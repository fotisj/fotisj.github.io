---
layout: post
title: Extracting Wikipedia texts
---

There are many contexts in which we want to work with wikipedia, which has become one of the largest 
language and knowledge resources in almost every language. Until recently I used the 
[WikiExtractor](https://github.com/attardi/wikiextractor), which worked really fine, but now it seems to 
be broken. I and some other users have problems running it, because of error related to encoding. 

Therefore I went looking for alternatives and found the [script segment_wiki ](https://radimrehurek.com/gensim/scripts/segment_wiki.html), 
which is part of the well-known gensim package. 

The workflow they proposed and which worked nicely for me is this:
First extract the wiki dump into a plain text file, which contains one json dict per line:

````python -m gensim.scripts.segment_wiki -i -f dewiki-latest-pages-articles.xml.bz2 -o dewiki-latest.json.gz````

Now iterate over the text file and read in a line and cast it to a dictionary, which you can process:

    from gensim import utils
    import json
    with utils.open('dewiki-latest.json.gz', 'rb') as f:
        for line in f:
            article = json.loads(line)
            do_sth_with_article(article)

(if you unpacked the resulting gz file, you can just read the file like this:
    
    import json
    with open('dewiki-lastest.json') as fin:
        for line in fin:
            article = json.loads(line)
            do_sth_with_article(article)

Its useful to know the structure of an article. Each has 4 keys: 

    'title', 'section_titles', 'section_texts', 'interlinks'

If you are mainly interested in lots of raw text, you may want to iterate over section_texts, 
but be aware that the last sections very often contain references and many articles can contain 
different sections at the end, like web links, references, published works and other lists., 
which are not helpful for training a language model. So you may want to consider filtering them out.
This is not trivial, because the section titles are not normed, so I put the section titles of the 
first 100.000 articles into a Counter. This is the manually filtered list containing only those
section titles which refer (to my knowledge) to list like texts: 

* ('Weblinks', 72044),
* ('Einzelnachweise', 59203),  (references)
* ('Literatur', 46900),
* ('Siehe auch', 24976),    (see also)
* ('Diskografie', 1485),
* ('Sonstiges', 2254)
* ('Schriften', 1131),
* ('Söhne und Töchter der Stadt', 1117),
* ('Städtepartnerschaften', 928),
* ('Wappen', 922),
* ('Fußnoten', 913),
* ('Filmografie', 821),
* ('Filmografie (Auswahl)', 719)
* ('Veröffentlichungen', 602),
* ('Technische Daten', 449),
* ('Söhne und Töchter der Stadt', 1117),
* ('Wappen', 922),
* ('Bevölkerungsentwicklung', 659),
* ('Bilder', 553)
* ('Galerie', 550)
* ('Ehrungen', 1616)

And there is much more you would want to exclude like 'Verbindungen' (compounds) in chemical elements. 
If you have any idee how to do this in a more organized way, please let me know.

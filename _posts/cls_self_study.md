---
layout: post
title: Computational Literary Studies: self study
---

As many others sometimes I am asked about good resources for people who are interested in learning  <i>computational literary studies</i>. Many of them cannot rely on courses at their local university and are interested in resources for self-studying. Here are some books, videos and online courses I found quite useful. 

In my opinion Computational Literary Studies can be seen as a specialized form of data science, and the competences it is based on can be described using the well-known Venn diagram with the three disciplines Computer Science, Statistics and Literary Studies. Let us first describe the fields and subfields and then the resources. Obviously each of them even is a research field on its own, so usually we are talking about a solid understanding of the basics. An usually the aim is not to implement an algorithm in one of these fields but to use a library, which implements it, competently. For practical reasons the following list is not a taxonomy and contains many overlaps, for example is word2vec using a shallow network which can be best understood after reading some material about Deep Learning where word embeddings are also very often used. 

As I don't work with R, my examples are usually taken from the Python eco-system.

## Mathematics for programmers:
* a refresher for your high school math
* Linear Algebra
* Calculus (just enough to understand Gradient Descent)
* Graph Theory
* Information Theory


## Computer Science
* Programming basics (in a script language like Python or R)
* Data collection and preparation
	* Regular expressions
* Data visualization and exploration
* Machine Learning (basic concepts and a library which allows you to apply them)
	* Dimesionality Reduction (PCA, t-sne, Umap)
	* Deep Learning
		* Convolutional Networks, Recurrent Networks, Transformer, Attention

## Natural Language Processing 
* Tokenization, lemmatization, part-of-speech tagging, named entity recognition, coreference resolution, morphological analysis, chunking, sentence parsing, semantic role labeling, language models
* domain adaption 
* sentiment analysis
* LDA aka Topic Modeling
* Word Embeddings (from word2vec to Bert)

## Statistics
* Descriptive Statistics
* Basics of Inference Statistics
* Comparing two corpora and other concepts from corpus linguistics


## Computational Literary Studies
* Corpus Linguistics
* Stylometry
* Text complexity (readibility, vocabulary richness, etc.)
* Character networks



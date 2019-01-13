---
layout: post
title: Mathematical formulas in markdown 
---
In order to render mathematical formulas in markdown, for example in Jupyter notebooks or Github pages, we can use the same solution: [MathJax](https://www.mathjax.org/). 
In Jupyter notebooks the support of MathJax works out of the box. In Github pages the standard markdown processor , kramdown, handles MathJax without any problems. MathJax converts 
TeX/LaTeX expressions - only the math-mode macros -  to an internal representation, MathML and renders them in HTML using even its own font for mathematical symbols. 

For Github pages: In order to use MathJax you have to import it in your webpage like this:

``
<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>
``

Then you can use inline or block expression: 

An expression like $$\forall x \in R^{200}$$ can be used inline. 

Here the Markdown/Latex to produce this:

``
An expression like $$\forall x \in R^{200}$$ can be used inline. 
``

Or as a block:

$$
y = \sum_1^n \frac{1}{x_n}
$$

Here the Markdown/Latex to produce this:

```
$$
y = \sum_1^n \frac{1}{x_n}
$$

```

The [wikibooks on Latex](https://en.wikibooks.org/wiki/LaTeX) has an extensive chapter on 
[Mathematics](https://en.wikibooks.org/wiki/LaTeX/Mathematics). Here a more complex example from the book:

$$
A_{m,n} = 
 \begin{pmatrix}
  a_{1,1} & a_{1,2} & \cdots & a_{1,n} \\
  a_{2,1} & a_{2,2} & \cdots & a_{2,n} \\
  \vdots  & \vdots  & \ddots & \vdots  \\
  a_{m,1} & a_{m,2} & \cdots & a_{m,n} 
 \end{pmatrix}
 $$

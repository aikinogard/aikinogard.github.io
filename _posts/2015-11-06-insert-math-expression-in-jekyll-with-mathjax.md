---
layout: post
title: "Insert math expression in Jekyll with MathJax"
description: ""
category: 
tags: [jekyll, MathJax]
---
{% include JB/setup %}

Here is a simple solution to put math equation in jekyll website.

First put the following javascript in ``_layouts/post.html``

{% highlight javascript %}
<script type="text/javascript"
    src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
</script>
{% endhighlight %}

Then try
	$$a^2 + b^2 = c^2$$
display a math expression.

Use ``\\( ... \\)`` like ``\\( sin(x^2) \\)`` to create inline equation \\( sin(x^2) \\).

I hope this is useful.

Reference: [MathJax with Jekyll](http://gastonsanchez.com/blog/opinion/2014/02/16/Mathjax-with-jekyll.html)
---
layout: post
title: "glob in python, Unix style pathname pattern expansion"
description: ""
category: 
tags: [python, glob]
---
{% include JB/setup %}

Just know a new module in Python standard library called ```glob```. This module helps you get files in your desired pattern. ```*``` matches any characters, ```?```matches single character, ```[]``` matches a character in square brackets range.

For example, if you have files

	12abc.pdf
	ut.bmp
	051.txt
	uc.pdf
	
Here is some examples of ```glob.glob(pathname)```:
	
{% highlight python %}
import glob
glob.glob("*.*")
{% endhighlight %}

```['051.txt', '12abc.pdf', 'uc.pdf', 'ut.bmp']```

{% highlight python %}
glob.glob("[0-9]*.*")
{% endhighlight %}

```['051.txt', '12abc.pdf']```

{% highlight python %}
glob.glob("[0-9]*.pdf")
{% endhighlight %}

```['12abc.pdf']```

{% highlight python %}
glob.glob("[0-9].pdf")
{% endhighlight %}

```[]```

{% highlight python %}
glob.glob("?.*")
glob.glob("?.pdf")
glob.glob("??.pdf")
{% endhighlight %}

```
[]
[]
['uc.pdf']
```

There is another function ```glob.iglob(pathname)``` which return yields the same values as ```glob()``` as an iterator.

The official documents can be find [here](https://docs.python.org/2/library/glob.html)
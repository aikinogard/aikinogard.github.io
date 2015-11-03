---
layout: post
title: "turtle in python"
description: ""
category: coding
tags: [python]
---
{% include JB/setup %}

I just found there is a module called ``turtle`` in python.

Try this out:

	import turtle

	def tree(branchLen,t):
	    if branchLen > 5:
	        t.forward(branchLen)
	        t.right(20)
	        tree(branchLen-15,t)
	        t.left(40)
	        tree(branchLen-15,t)
	        t.right(20)
	        t.backward(branchLen)

	def main():
	    t = turtle.Turtle()
	    myWin = turtle.Screen()
	    t.left(90)
	    t.up()
	    t.backward(100)
	    t.down()
	    t.color("green")
	    tree(75,t)
	    myWin.exitonclick()

	main()

I hope this is interesting.

Reference: [Problem Solving with Algorithms and Data Structures](http://interactivepython.org/runestone/static/pythonds/Recursion/pythondsintro-VisualizingRecursion.html)
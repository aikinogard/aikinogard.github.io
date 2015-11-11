---
layout: post
title: "heap in Python"
description: ""
category: 
tags: [python, algorithm]
---
{% include JB/setup %}

Heap is a data structure which is usually used to implement a priority queue, allowing us both enqueue and dequeue items in \\(O(\log n) \\).

This can be easily implemented in python.

You can find it at [Binary Heap Implementation](http://interactivepython.org/runestone/static/pythonds/Trees/BinaryHeapImplementation.html)

{% highlight python linenos%}
class BinHeap:
    def __init__(self):
        self.heapList = [0]
        self.currentSize = 0

	def percUp(self,i):
		while i // 2 > 0:
			if self.heapList[i] < self.heapList[i // 2]:
				tmp = self.heapList[i // 2]
				self.heapList[i // 2] = self.heapList[i]
				self.heapList[i] = tmp
			i = i // 2
			
	def percDown(self,i):
	    while (i * 2) <= self.currentSize:
	        mc = self.minChild(i)
    	    if self.heapList[i] > self.heapList[mc]:
        	    tmp = self.heapList[i]
            	self.heapList[i] = self.heapList[mc]
            	self.heapList[mc] = tmp
        	i = mc

	def minChild(self,i):
	    if i * 2 + 1 > self.currentSize:
	        return i * 2
	    else:
	    	if self.heapList[i*2] < self.heapList[i*2+1]:
	        	return i * 2
        	else:
        		return i * 2 + 1

	def insert(self,k):
	    self.heapList.append(k)
	    self.currentSize = self.currentSize + 1
	    self.percUp(self.currentSize)    
	
	def delMin(self):
    	retval = self.heapList[1]
    	self.heapList[1] = self.heapList[self.currentSize]
    	self.currentSize = self.currentSize - 1
    	self.heapList.pop()
    	self.percDown(1)
    	return retval
    	
	def buildHeap(self,alist):
    	i = len(alist) // 2
    	self.currentSize = len(alist)
    	self.heapList = [0] + alist[:]
    	while (i > 0):
        	self.percDown(i)
        	i = i - 1 		  		
{% endhighlight%}

It is good to understand what happened above. But for quick application of min heap, python already provides a build-in module ```heapq```. see [here](https://docs.python.org/2/library/heapq.html).

You can get start from:

* ```heapq.heapify(x)``` create a heap from list ```x``` in place. ```x``` becomes a min heap.
* ```heapq.headpush(heap, item)``` push ```item``` into ```heap```.
* ```heapq.headpop(heap, item)``` pop ```item``` out from ```heap```.




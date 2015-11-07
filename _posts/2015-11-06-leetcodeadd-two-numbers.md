---
layout: post
title: "Leetcode:Add Two Numbers"
description: ""
category: LeetCode
tags: [algorithms, LeetCode, python]
---
{% include JB/setup %}

>You are given two linked lists representing two non-negative numbers. The digits are stored in reverse order and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.
>
>``Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)``
>
>``Output: 7 -> 0 -> 8``

This problem is marked as Medium.

{% highlight python linenos %}
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def addTwoNumbers(self, l1, l2):
        """
        :type l1: ListNode
        :type l2: ListNode
        :rtype: ListNode
        """
        output = ListNode(0)
        p = output
        
        while l1 or l2:
            v1 = l1.val if l1 else 0
            v2 = l2.val if l2 else 0
            s = v1 + v2 + p.val
            digit = s % 10
            rem = s // 10
            p.val = digit
            l1 = l1.next if l1 else l1
            l2 = l2.next if l2 else l2
            if l1 or l2 or rem > 0:
                p.next = ListNode(rem)
                p = p.next
        return output
 {% endhighlight %}
---
layout: post
title: "LeetCode: Two Sum"
description: ""
category: LeetCode
tags: [algorithms, LeetCode, python]
---
{% include JB/setup %}

>Given an array of integers, find two numbers such that they add up to a specific target number.
>
>The function twoSum should return indices of the two numbers such that they add up to the target, where index1 must be less than index2. Please note that your returned answers (both index1 and index2) are not zero-based.
>
>You may assume that each input would have exactly one solution.
>
>``Input: numbers={2, 7, 11, 15}, target=9``
>
>``Output: index1=1, index2=2``

This is the first problem in LeetCode. The difficulty is Medium. It is not hard to solve this problem with brute force. However, an improvement of complexity can be implemented by hash table.

{% highlight python linenos %}
class Solution(object):
    def twoSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        buff_dict = {}
        for i, num in enumerate(nums):
            if num in buff_dict.keys():
                return [buff_dict[num], i + 1]
            else:
                buff_dict[target - num] = i + 1
{% endhighlight %}

The basic idea is to record the index of the "partner" of the encounter number into a python dictionary. Because python ``dict`` use hash table, the complexity of search in ``dict`` is \\(O(1) \\). So the overall complexity (consider the ``for`` loop) is \\(O(n) \\) instead of \\(O(n^2) \\).


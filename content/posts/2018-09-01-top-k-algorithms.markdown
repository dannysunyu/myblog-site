---
layout: post
title: "top k algorithms"
date: 2018-09-01 18:46:00 +0800
comments: true
categories: algorithms
---

##背景

去年面试Facebook时，被问到了一道Top K的问题，这类的问题解法往往具有共通性。今天在LeetCode上又遇到了一道[类似的问题](https://leetcode.com/problems/top-k-frequent-words/description/)，于是网上搜了一下[解题思路](https://www.programcreek.com/2014/05/leetcode-top-k-frequent-elements-java/)，摘录留下备用。

JDK里有一个强大的集合类 -- *PriorityQueue*，掌握了它的用法便能迎刃而解这类问题。

值得注意的是*PriorityQueue*没有继承自*List*，不具有随机访问第i个元素的方法。
```java
E get(int index);
```

>Given a non-empty array of integers, return the k most frequent elements.


```java
class Pair {
    int num;
    int count;

    Pair(int num, int count) {
        this.num=num;
        this.count=count;
    }
}

public class Solution {
    public List<Integer> topKFrequent(int[] nums, int k) {
        //count the frequency for each element
        HashMap<Integer, Integer> map = new HashMap<Integer, Integer>();
        for(int num: nums){
            if (map.containsKey(num)) {
                map.put(num, map.get(num)+1);
            } else {
                map.put(num, 1);
            }
        }

        // create a min heap
        PriorityQueue<Pair> queue = new PriorityQueue<>(new Comparator<Pair>() {
            public int compare(Pair a, Pair b) {
                return a.count - b.count;
            }
        });

        //maintain a heap of size k.
        for (Map.Entry<Integer, Integer> entry: map.entrySet()) {
            Pair p = new Pair(entry.getKey(), entry.getValue());
            queue.offer(p);
            if(queue.size() > k) {
                queue.poll();
            }
        }

        //get all elements from the heap
        List<Integer> result = new ArrayList<Integer>();
        while(queue.size() > 0) {
            result.add(queue.poll().num);
        }
        //reverse the order
        Collections.reverse(result);

        return result;
    }
}
```

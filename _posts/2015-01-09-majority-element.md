---
layout: post
title: Majority Element
---
'''
Given an array of size n, find the majority element. The majority element is the element that appears more than ⌊ n/2 ⌋ times.
'''

This problem can be solved in Linear time using [Majority Vote Algorithm](http://www.cs.utexas.edu/~moore/best-ideas/mjrty/). 

- Time Complexity - O(n)
- Space Complexity - O(1)

``` java
public class Solution {
    public int majorityElement(int[] num) {
       int cur=0;
       int counter=0;
     for(int i=0;i<num.length;i++)
     {
     	if(counter==0){cur=num[i]; counter=1;}
     	else if(counter!=00 && cur==num[i]) {counter++;}
     	else {counter--;}
     }
     if(counter!=0) return cur;
     else return -1;
        
    }
}
```

---
layout: post
title: Merge Sorted Array 
---
>Given two sorted integer arrays A and B, merge B into A as one sorted array.
>
>**Note:**
>
>You may assume that A has enough space (size that is greater or equal to m + n) to hold additional elements from B. The number of elements initialized in A and B are m and n respectively.

``` java 
public class MergeTwoSortedArrays{
    public void merge(int A[], int m, int B[], int n) {
        int len;
        len = m+n;
        int aindex = m-1;
        int bindex = n-1;
        int i=len-1;
        while(i>=0)
        {
            if(aindex<0)
            {
                A[i--]=B[bindex--];
            }
            else if(bindex<0)
            {
                A[i--]=A[aindex--];
            }
            else if(A[aindex]>B[bindex])
            {
                A[i--]=A[aindex--];
            }
            else if(A[aindex]<B[bindex])
            {
                A[i--]=B[bindex--];
            }
            else if(A[aindex]==B[bindex])
            {
                A[i--]=A[aindex--];
                A[i--]=B[bindex--];
            }
            
        }
        
        
    }
}

```

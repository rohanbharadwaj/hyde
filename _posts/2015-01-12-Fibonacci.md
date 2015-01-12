---
layout: post
title: Merge Sorted Array 
---
>
>The Fibonacci Sequence is the series of numbers:
>
>0, 1, 1, 2, 3, 5, 8, 13, 21, 34, ...
>
>The next number is found by adding up the two numbers before it.
>
>The 2 is found by adding the two numbers before it (1+1)
>Similarly, the 3 is found by adding the two numbers before it (1+2),
>And the 5 is (2+3),
>and so on!
>


```
The Rule is  F(n) =  F(n-1) +  F(n-2)
```

A recurive function for calculating nth Fibo can be given by the following code.

``` java
  fib(int n)
	{
		if(n==0) return 0L;
		if(n==1) return 1L;
		return fib(n-1)+fib(n-2);
		
	}
```

The recursion tree is given below, here we can see that there are lot of values which are computed multiple times.
Thus this approach has multiple duplicate calculations. We can remember previously computed values and use them 
instead of recomputing them. 

                             F(n)
                            /    \
                        F(n-1)   F(n-2)
                        /   \     /      \
                    F(n-2) F(n-3) F(n-3)  F(n-4)
                   /    \
                 F(n-3) F(n-4)
                 

One approach to remmeber the values is by storing them in HashMap and use them for later use because the lookup is 
O(1). 


``` java
import java.util.*;
public class Fibo{
	public static Long fibWithMemo(int n)
	{
		HashMap<Integer,Long> data = new HashMap<Integer,Long>();
		Long prev =  0L;
		Long cur = 1L;
		data.put(0,prev);
		data.put(1,cur);
		for(int i=2;i<=n;i++)
			data.put(i,data.get(i-1)+data.get(i-2));
	return data.get(n);
	}

	public static Long fib(int n)
	{
		if(n==0) return 0L;
		if(n==1) return 1L;
		return fib(n-1)+fib(n-2);
		
	}

	public static void main(String args[])
	{
		long start,elapsedTime;
		start = System.nanoTime();
		System.out.println(fibWithMemo(40));
		elapsedTime = System.nanoTime()-start;
		System.out.println("Time for fibWithMemo "+elapsedTime);
		start = System.nanoTime();
		System.out.println(fib(40));
		elapsedTime = System.nanoTime()-start;
		System.out.println("Time for fib "+elapsedTime);

	}

}

```

The ouput of the above program is :

```
rohan@rohan-Inspiron-1545:~/Algorithms$ java Fibo
102334155
Time for fibWithMemo 3462173
102334155
Time for fib 2981581808

```

---
layout: post
title: Recursion
---
Recursion is powerful tool to solve many problems with simple and elegant code, but it is often tricky to imagine how the
function calls are being made. I will try to take a problem and explain the flow of recursive calls.

>Given a positive integer, return its corresponding column title as appear in an Excel sheet.
>
>For example:
> ```
      1 -> A
      2 -> B
      3 -> C
      ...
      26 -> Z
      27 -> AA
      28 -> AB 
  ```    
>

This problem can be solved using a recursive function and it turns out to be a single line of code. 

``` java
public class ExcelTitle {
    public static String convertToTitle(int n) {
        return n == 0 ? "" : convertToTitle(--n / 26) + (char)('A' + (n % 26));
        
    }
    
    public static void main(String args[])
    {
    	System.out.println(convertToTitle(27));
    	

    }
}
```


The explanation is shown in the screenshot below:
![My helpful screenshot]({{ site.url }}/assets/recursion.jpg)

The output of the call `convertToTitle(27)` is AA.

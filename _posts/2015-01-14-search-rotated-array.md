---
layout: post
title: Searching in an sorted and rotated array
---

This can be done in `O(logN)` using a slightly modified binary search.

The interesting property of a sorted + rotated array is that when you divide it into two halves, 
atleast one of the two halves will always be sorted.

```
Let input array arr = [4,5,6,7,8,9,1,2,3]
number of elements  = 9
mid index = (0+8)/2 = 4

[4,5,6,7,8,9,1,2,3]
         ^
 left   mid  right
```
as seem right sub-array is not sorted while left sub-array is sorted.

If mid happens to be the point of rotation them both left and right sub-arrays will be sorted.

```
[6,7,8,9,1,2,3,4,5]
         ^
```

But in any case one half(sub-array) must be sorted.

We can easily know which half is sorted by comparing start and end element of each half.

Once we find which half is sorted we can see if the key is present in that half - simple comparison 
with the extremes.

If the key is present in that half we recursively call the function on that half 
else we recursively call our search on the other half.

We are discarding one half of the array in each call which makes this algorithm O(logN).

``` java
/*
 * This Program is used to search for a key in a sorted array which is 
 * rotated. It works fine even if there are duplicates.
 */
public class RotatedArray {
	public static int search(int[] arr, int key, int low, int high) {

		int mid = (low + high) / 2;

		if (arr[mid] == key)
			return mid;
		while (low <= high) {
			// if the left half is sorted.
			if (arr[low] < arr[mid]) {

				// if key is in the left half
				if (arr[low] <= key && key <= arr[mid])
					// search the left half
					return search(arr, key, low, mid - 1);
				else
					// search the right half
					return search(arr, key, mid + 1, high);
			}

			// if the right half is sorted.
			else if (arr[mid] < arr[low]) {
				// if the key is in the right half.
				if (arr[mid] <= key && arr[high] >= key)
					return search(arr, key, mid + 1, high);
				else
					return search(arr, key, low, mid - 1);
			}

			else if (arr[mid] == arr[low]) {

				if (arr[mid] != arr[high])
					// Then elements in left half must be identical.
					// Because if not, then it's impossible to have either
					// arr[mid] < arr[high] or arr[mid] > arr[high]
					// Then we only need to search the right half.
					return search(arr, key, mid + 1, high);
				else {
					// arr[low] = arr[mid] = arr[high], we have to search both
					// halves.
					int result = search(arr, key, low, mid - 1);
					if (result == -1)
						return search(arr, key, mid + 1, high);
					else
						return result;
				}
			}
		}
		return -1;
	}

	public static void main(String args[]) {
		int[] arr = { 2, 2, 2, 2, 2, 3, 1 };
		int high = arr.length;
		int res = search(arr, 3, 0, high - 1);
		System.out.println(res);
	}
}
```
[Reference](http://stackoverflow.com/questions/4773807/searching-in-an-sorted-and-rotated-array)

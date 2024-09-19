---
layout: post
title: Data Structure(1) - Array
date: 2024-09-18 15:50 -0400
category: [Study, Data Structure]
tags: [C#, Data Structure, Array]
---

> While preparing coding test, I realized I didn't learn about data structure in school.
> So, this post and the following posts are to study about data structure including I already learn in school.

## What is Array?
---
Array is a data structure that saves the same type of elements in the continuous memory. Array has a fixed size.
When an array is defined with the size, the size will not be modified. We can access to elements in array with index and the index starts with 0.

## How to Declare and Initialize an Array?
---
To declare an array, we need to use below format.   
`{type}[] {array_name};`

For example, I can declare like this
```shell
// int array
int[] IntArray;

// string array
string[] StringArray;
```

Now we need to initialize this array. There are a few ways to initialize it.
```shell
// The array size is 5.
IntArray = new int[5];
StringArray = new string[5]

// Or we can declare and initialize together.
int[] intArray2 = new int[5];
string[] stringArray2 = new string[5];

// If you already know elements that you want to add into array, you can do
int[] intArray3 = new int[] {1, 2, 3, 4, 5};

// or you want do it without 'new'
int[] intArray4 = {1, 2, 3, 4, 5};
```

## How to Access the Element in the Array?
---
We can access each element in the array using index.
```shell
int element1 = intArray4[2]; // 3

// if you want to edit the element value then,
intArray4[3] = 5; // intArray = {1, 2, 3, 5, 5}
```

## Length of Array
---
If you want to know the array length, you can use `Length` and `Count()`.
```shell
int len1 = intArray4.Length;
int len2 = intArray4.Count();
```
It is because `Length` is one of properties of array and `Count()` is LINQ Method. So Length is faster than Count().

## Loop of Array
---
We can use `for` statement and `foreach` statement to print element.
```shell
// using for loop
for(int i = 0; i < intArray4.Length; i++) {
    Console.WriteLine(intArray4[i]);
}

// using foreach loop
foreach(int i in intArray4) {
    Console.WriteLine(i);
}
```

## Multidimensional Arrays
---
```shell
// Declare and initialize
string[,] 2dArray = new string[2,2]; // 2 * 2 array

// Assign values
2dArray[0,1] = "hello"
```

## Example Problem
Let's solve [Intersection of Two Arrays II](https://leetcode.com/problems/intersection-of-two-arrays-ii/)!

**Problem Description:**   
Given two integer arrays nums1 and nums2, return an array of their intersection. Each element in the result must appear as many times as it shows in both arrays and you may return the result in any order.

Example 1:   
Input: nums1 = [1,2,2,1], nums2 = [2,2]   
Output: [2,2]

Example 2:   
Input: nums1 = [4,9,5], nums2 = [9,4,9,8,4]   
Output: [4,9]   
Explanation: [9,4] is also accepted.
 
Constraints:   
1 <= nums1.length, nums2.length <= 1000   
0 <= nums1[i], nums2[i] <= 1000


```shell
public class Solution {
    public int[] Intersect(int[] nums1, int[] nums2) {
        // List Declaring - To be posted
        List<int> result = new List<int>();

        // Declare a new array to save nums1
        int[] nums3 = nums1;
        
        // this for loop will compare elements nums3 and nums2
        foreach(int i in nums2) {
            // save index of element
            // if nums3 doesn't have i, then i will return -1
            int index = Array.IndexOf(nums3, i);

            // if nums3 include i, add the element into result list
            if(index > -1) {
                result.Add(nums3[index]);
                // to avoid duplicate I modifed the element value
                nums3[index] = -1;
            }
        }
        
        // this method needs int array to return. so convert list to array.
        return result.ToArray();
    }
}
```
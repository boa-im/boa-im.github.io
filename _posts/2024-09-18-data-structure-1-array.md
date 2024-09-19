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
---
Let's solve [Fizz Buzz](https://leetcode.com/problems/fizz-buzz/description/)!

**Problem Description:**   
Given an integer n, return a string array answer (1-indexed) where:   
answer[i] == "FizzBuzz" if i is divisible by 3 and 5.   
answer[i] == "Fizz" if i is divisible by 3.   
answer[i] == "Buzz" if i is divisible by 5.   
answer[i] == i (as a string) if none of the above conditions are true.
 
Example 1:   
Input: n = 3 .  
Output: ["1","2","Fizz"]

Example 2:   
Input: n = 5   
Output: ["1","2","Fizz","4","Buzz"]

Example 3:   
Input: n = 15   
Output: ["1","2","Fizz","4","Buzz","Fizz","7","8","Fizz","Buzz","11","Fizz","13","14","FizzBuzz"]

Constraints:   
1 <= n <= 104

```shell
public class Solution {
    public IList<string> FizzBuzz(int n) {
        // Declare a string List to return
        List<string> result = new List<string>();

        for(int i = 1; i <= n; i++) {
            // If i can be divisible by 3, isDivisibleByThree will be true
            bool isDivisibleByThree = i % 3 == 0;
            // If i can be divisible by 5, isDivisibleByFive will be true
            bool isDivisibleByFive = i % 5 == 0;

            // i can be divisible by only 3
            if(isDivisibleByThree && !isDivisibleByFive) {
                result.Add("Fizz");
            }
            // i can be divisible by only 5
            else if(!isDivisibleByThree && isDivisibleByFive) {
                result.Add("Buzz");
            }
            // i can be divisible by 3 and 5
            else if(isDivisibleByThree && isDivisibleByFive) {
                result.Add("FizzBuzz");
            }
            // i cannot be divisible by 3 or 5
            else {
                // i % 3 != 0 && i % 5 != 0
                result.Add(i.ToString());
            }
        }

        return result;
    }
}
```
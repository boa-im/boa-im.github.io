---
layout: post
title: "#167. Two Sum II - Input Array Is Sorted"
date: 2024-11-01 10:34 -0400
category: [Study, Leetcode]
tags: [Array, Two Pointers, Binary Search, Medium]
---

## Description
---
Given a **1-indexed** array of integers `numbers` that is already ***sorted in non-decreasing order***, find two numbers such that they add up to a specific `target` number. Let these two numbers be `numbers[index1]` and `numbers[index2]` where `1 <= index1 < index2 <= numbers.length`.

Return the indices of the two numbers, `index1` and `index2`, ***added by one*** as an integer array `[index1, index2]` of length 2.

The tests are generated such that there is **exactly one solution**. You **may not** use the same element twice.

Your solution must use only constant extra space.

**Example 1:**
> Input: numbers = [2,7,11,15], target = 9   
> Output: [1,2]   
> Explanation: The sum of 2 and 7 is 9. Therefore, index1 = 1, index2 = 2. We return [1, 2].

**Example 2:**
> Input: numbers = [2,3,4], target = 6   
> Output: [1,3]   
> Explanation: The sum of 2 and 4 is 6. Therefore index1 = 1, index2 = 3. We return [1, 3].

**Example 3:**
> Input: numbers = [-1,0], target = -1   
> Output: [1,2]   
> Explanation: The sum of -1 and 0 is -1. Therefore index1 = 1, index2 = 2. We return [1, 2].
 
**Constraints:**
- 2 <= numbers.length <= 3 * 104
- -1000 <= numbers[i] <= 1000
- numbers is sorted in non-decreasing order.
- -1000 <= target <= 1000
- The tests are generated such that there is exactly one solution.

## My Solution
---
```shell
public class Solution {
    public int[] TwoSum(int[] numbers, int target) {
        for(int i = 0; i < numbers.Length - 1; i++) {
            for(int j = i + 1; j < numbers.Length; j++) {
                if(numbers[i] + numbers[j] == target) {
                    return [i + 1, j + 1];
                }
            }
        }

        return [];
    }
}
```

#### Runtime
**343** ms / Beats **6.39%**

#### Memory
**49.59** MB / Beats **92.65%**

#### Big O Notation
Time complexity: **O(n^2)**   
Space complexity: **O(1)**

## Best Solution
---
```shell
public class Solution {
    public int[] TwoSum(int[] numbers, int target) {
        int left = 0;
        int right = numbers.Length - 1;

        while (left < right) {
            int total = numbers[left] + numbers[right];

            if (total == target) {
                return [left + 1, right + 1];
            } else if (total > target) {
                right--;
            } else {
                left++;
            }
        }

        return [];
    }
}
```

#### Runtime
**0** ms / Beats **100%**

#### Memory
**49.81** MB / Beats **54.73%**

#### Big O Notation
Time complexity: **O(n)**   
Space complexity: **O(1)**
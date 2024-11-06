---
layout: post
title: "#11. Container With Most Water"
date: 2024-11-06 11:04 -0500
category: [Study, Leetcode]
tags: [Array, Two Pointers, Greedy, Medium]
---

- [ ] Solved

## Description
---
You are given an integer array `height` of length `n`. There are `n` vertical lines drawn such that the two endpoints of the `ith` line are `(i, 0)` and `(i, height[i])`.

Find two lines that together with the x-axis form a container, such that the container contains the most water.

Return the maximum amount of water a container can store.

**Notice** that you may not slant the container.

**Example 1:**   
![example](assets/img/leetcode/question_11.jpg)   
> Input: height = [1,8,6,2,5,4,8,3,7]   
> Output: 49   
> Explanation: The above vertical lines are represented by array [1,8,6,2,5,4,8,3,7]. In this case, the max area of water (blue section) the container can contain is 49.

**Example 2:**   
> Input: height = [1,1]
> Output: 1

**Constraints:**
- n == height.length
- 2 <= n <= 105
- 0 <= height[i] <= 104

## My Solution
---
```shell
public class Solution {
    public int MaxArea(int[] height) {
        int max = 0;

        for(int i = 0; i < height.Length - 1; i++) {
            for (int j = i + 1; j < height.Length; j++) {
                int width = j - i;
                int length = Math.Min(height[i], height[j]);

                max = Math.Max(width * length, max);
            }
        }

        return max;
    }
}
```

#### Runtime
Time Limit Exceeded

#### Memory
Time Limit Exceeded

#### Big O Notation
Time complexity: **O(n^2)**   
Space complexity: **O(1)**

## Best Solution
---
```shell
public class Solution {
    public int MaxArea(int[] height) {
        int max = 0;
        int left = 0;
        int right = height.Length - 1;

        while(left < right) {
            max = Math.Max((right - left) * Math.Min(height[left], height[right]), max);

            if(height[left] > height[right]) {
                right--;
            }
            else {
                left++;
            }
        }

        return max;
    }
}
```

#### Runtime
**1** ms / Beats **98.94%**

#### Memory
**61.87** MB / Beats **75.86%**

#### Big O Notation
Time complexity: **O(n)**   
Space complexity: **O(1)**
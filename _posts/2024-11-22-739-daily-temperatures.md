---
layout: post
title: "#739. Daily Temperatures"
date: 2024-11-22 11:19 -0500
category: [Study, Leetcode]
tags: [Array, Stack, Monotonic Stack, Medium]
---

- [x] Solved

## Description
---
Given an array of integers `temperatures` represents the daily temperatures, return an array answer such that `answer[i]` is the number of days you have to wait after the `ith` day to get a warmer temperature. If there is no future day for which this is possible, keep `answer[i] == 0` instead.

**Example 1:**   
> Input: temperatures = [73,74,75,71,69,72,76,73]   
> Output: [1,1,4,2,1,1,0,0]

**Example 2:**   
> Input: temperatures = [30,40,50,60]   
> Output: [1,1,1,0]

**Example 3:**   
> Input: temperatures = [30,60,90]   
> Output: [1,1,0]
 
**Constraints:**
- 1 <= temperatures.length <= 105
- 30 <= temperatures[i] <= 100

## My Solution
---
```shell
public class Solution {
    public int[] DailyTemperatures(int[] temperatures) {
        int[] result = new int[temperatures.Length];
        result[temperatures.Length - 1] = 0;

        for(int i = 0; i < temperatures.Length-1; i++) {
            for(int j = i + 1; j < temperatures.Length; j++) {
                if(temperatures[i] < temperatures[j]) {
                    result[i] = j - i;
                    break;
                }
            }
        }

        return result;
    }
}
```

#### Runtime
**2164** ms / Beats **5.10%**

#### Memory
**73.16** MB / Beats **80.29%**

#### Big O Notation
Time complexity: **O(n^2)**   
Space complexity: **O(n)**

## Best Solution
---
```shell
public class Solution {
    public int[] DailyTemperatures(int[] temps) {
        int[] result = new int[temps.Length];
        Stack<int> stack = new Stack<int>();
        
        for (int i = 0; i < temps.Length; i++) {
            while (stack.Count > 0 && temps[stack.Peek()] < temps[i]) {
                int index = stack.Pop();
                result[index] = i - index;
            }
            stack.Push(i);
        }

        return result;
    }
}
```

#### Runtime
**10** ms / Beats **65.31%**

#### Memory
**76.22** MB / Beats **65.78%**

#### Big O Notation
Time complexity: **O(n)**   
Space complexity: **O(n)**
---
layout: post
title: "#150. Evaluate Reverse Polish Notation"
date: 2024-11-14 09:53 -0500
category: [Study, Leetcode]
tags: [Array, Math, Stack, Medium]
---

- [x] Solved

## Description
---
You are given an array of strings `tokens` that represents an arithmetic expression in a Reverse Polish Notation.

Evaluate the expression. Return *an integer that represents the value of the expression*.

**Note** that:
- The valid operators are `'+'`, `'-'`, `'*'`, and `'/'`.
- Each operand may be an integer or another expression.
- The division between two integers always **truncates toward zero**.
- There will not be any division by zero.
- The input represents a valid arithmetic expression in a reverse polish notation.
- The answer and all the intermediate calculations can be represented in a **32-bit** integer.
 

**Example 1:**   
> Input: tokens = ["2","1","+","3","*"]   
> Output: 9   
> Explanation: ((2 + 1) * 3) = 9

**Example 2:**   
> Input: tokens = ["4","13","5","/","+"]   
> Output: 6   
> Explanation: (4 + (13 / 5)) = 6

**Example 3:**   
> Input: tokens = ["10","6","9","3","+","-11","*","/","*","17","+","5","+"]   
> Output: 22   
> Explanation: ((10 * (6 / ((9 + 3) * -11))) + 17) + 5   
> = ((10 * (6 / (12 * -11))) + 17) + 5   
> = ((10 * (6 / -132)) + 17) + 5   
> = ((10 * 0) + 17) + 5   
> = (0 + 17) + 5   
> = 17 + 5   
> = 22
 
**Constraints:**
- 1 <= tokens.length <= 104
- tokens[i] is either an operator: "+", "-", "*", or "/", or an integer in the range [-200, 200].

## My Solution = Best Solution
---
```shell
public class Solution {
    public int EvalRPN(string[] tokens) {
        Stack<int> expression = new Stack<int>();

        for(int i = 0; i < tokens.Length; i++) {
            if(tokens[i] == "+") {
                expression.Push(expression.Pop() + expression.Pop());
            }else if(tokens[i] == "-") {
                int first = expression.Pop();
                int second = expression.Pop();
                expression.Push(second - first);
            }else if(tokens[i] == "*") {
                expression.Push(expression.Pop() * expression.Pop());
            }else if(tokens[i] == "/") {
                int first = expression.Pop();
                int second = expression.Pop();
                expression.Push(second / first);
            }else {
                expression.Push(Convert.ToInt32(tokens[i]));
            }
        }

        return expression.Pop();
    }
}
```

#### Runtime
**12** ms / Beats **56.28%**

#### Memory
**43.80** MB / Beats **27.01%**

#### Big O Notation
Time complexity: **O(n)**   
Space complexity: **O(n)**
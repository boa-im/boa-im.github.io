---
layout: post
title: Data Structure(7) - Stack
date: 2024-09-27 09:52 -0400
category: [Study, Data Structure]
tags: [C#, Data Structure, Stack]
---

## What is Stack?
---
As oppsed to Queue, which is a First-In-First-Out(FIFO) structure, Stack is Last-In-First-Out(LIFO) structure.
Let's think about brackets. If we open 2 brackets like `{(`. `{` this curly bracket was entered first but we need to close this bracket using `)` this first like `)}`. This is stack! Stack is also in System.Collections.Generic namespace.

## How to Declare Stack?
Using a stack, we need to know what type we want to add into stack
```shell
Stack<int> stack = new Stack<int>();
```

## Methods
---
#### Push
To add an element into stack, we can use `Push()` method.
```shell
stack.Push(1);
stack.Push(2);
stack.Push(3);
```

#### Contains
`Contains()` method is to check if the element is in the stack.
```shell
stack.Contains(2); // true
stack.Contains(4); // false
```

#### Pop
`Pop()` is used when we want to remove the last item. And, Like Dequeue method in Queue, we can get the removing value.
```shell
stack.Pop(); // stack = {1, 2}
Console.WriteLine(stack.Pop()); // Console: 2, stack = {1}
```

#### Peek
If you use `Peek()` method, You can get the last value in Stack without deleting.
```shell
Console.WriteLine(stack.Peek()); // 1
```

#### Clear
To remove all the elements in stack, we can use `Clear()` method.
```shell
stack.Clear();
```

## Example Problem
---
Let's solve [Implement Stack using Queues](https://leetcode.com/problems/implement-stack-using-queues/description/)!

**Problem Description:**  
Implement a last-in-first-out (LIFO) stack using only two queues. The implemented stack should support all the functions of a normal stack (push, top, pop, and empty).

Implement the MyStack class:   
void push(int x) Pushes element x to the top of the stack.   
int pop() Removes the element on the top of the stack and returns it.   
int top() Returns the element on the top of the stack.   
boolean empty() Returns true if the stack is empty, false otherwise.

Notes:   
You must use only standard operations of a queue, which means that only push to back, peek/pop from front, size and is empty operations are valid.   
Depending on your language, the queue may not be supported natively. You may simulate a queue using a list or deque (double-ended queue) as long as you use only a queue's standard operations.
 
Example 1:   
Input   
["MyStack", "push", "push", "top", "pop", "empty"]   
[[], [1], [2], [], [], []]

Output   
[null, null, null, 2, 2, false]

Explanation   
MyStack myStack = new MyStack();   
myStack.push(1);   
myStack.push(2);   
myStack.top(); // return 2   
myStack.pop(); // return 2   
myStack.empty(); // return False

Constraints:   
1 <= x <= 9   
At most 100 calls will be made to push, pop, top, and empty.   
All the calls to pop and top are valid.

```shell
public class MyStack {
    // save a queue as a global variable
    private Queue<int> stack;

    public MyStack() {
        // once a stack created, create a new queue to stack
        stack = new Queue<int>();
    }
    
    public void Push(int x) {
        // enqueue the param into queue
        stack.Enqueue(x);
        for (int i = 0; i < stack.Count - 1; i++) {
            // re-enqueue all elements in stack to back
            stack.Enqueue(stack.Dequeue());
            // input = 1, 2, 3
            // stack will be changed like:
            // {1} -> {1, 2} -> {2, 1} -> {2, 1, 3} -> {1, 3, 2} -> {3, 2, 1}
        }
    }
    
    public int Pop() {
        return stack.Dequeue();
    }
    
    public int Top() {
        return stack.Peek();
    }
    
    public bool Empty() {
        // return true or false;
        return stack.Count() == 0;
    }
}

/**
 * Your MyStack object will be instantiated and called as such:
 * MyStack obj = new MyStack();
 * obj.Push(x);
 * int param_2 = obj.Pop();
 * int param_3 = obj.Top();
 * bool param_4 = obj.Empty();
 */
 ```
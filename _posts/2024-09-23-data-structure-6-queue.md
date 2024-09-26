---
layout: post
title: Data Structure(6) - Queue
date: 2024-09-23 15:21 -0400
category: [Study, Data Structure]
tags: [C#, Data Structure, Queue]
---

## What is Queue?
---
Queue is based on First-In-First-Out(FIFO). Let's imagine we are a worker who works at a box office and there is a line for buying tickets. In this moment, we need to sell tickets to the first person and go to the next person. In Queue, order is really important to handle data.

## How to Declare Queue?
---
It is similar with other lists. Queue is in _System.Collections.Generic_ namespace. So, we need to set the type of data to declare a queue.
```shell
Queue<int> queue = new List<int>();
```

## How to Add or Delete a data in Queue?
---
When we add items into queue, the items' order will be saved as well. And, as I explained, if we need to delete a item in Queue, the first item needs to be deleted. This mean we don't have to put the item's value in delete method unlike other lists To add or delete item, we can use `Enqueue()` or `Dequeue()`. Let's see the example!
```shell
queue.Enqueue(1);
queue.Enqueue(2);
queue.Enqueue(3);
// queue = {1, 2, 3}

queue.Dequeue();
// queue = {2, 3}
queue.Dequeue();
// queue = {3}
```

## Methods
---
#### Contains
Do you want to check if the queue has a item? You can use `Contains()`!
```shell
queue.Contains(3); // True
queue.Contains(4); // False
```

#### Clear
In the situation we imagined, if the tickets are sold out so we can't sell more tickets, we need to let the remain customers go. We can use `Clear()` method for this case.
```shell
queue.Clear();
```

#### Peek
If we need to know what the first element is in queue, we can use `Peek()` to get the information of the first element.
```shell
Queue<string> q2 = new Queue<string>();
q2.Enqueue("first");
q2.Enqueue("second");
q2.Enqueue("third");

Console.WriteLine(q2.Peek()); // first

q2.Dequeue();
Console.WirteLine(q2.Peek()); // second
q2.Dequeue();
Console.WirteLine(q2.Peek()); // third
```

## Example Problem
---
Let's solve [Time Needed to Buy Tickets](https://leetcode.com/problems/time-needed-to-buy-tickets/description/)!

**Problem Description:**  
There are n people in a line queuing to buy tickets, where the 0th person is at the front of the line and the (n - 1)th person is at the back of the line.

You are given a 0-indexed integer array tickets of length n where the number of tickets that the ith person would like to buy is tickets[i].

Each person takes exactly 1 second to buy a ticket. A person can only buy 1 ticket at a time and has to go back to the end of the line (which happens instantaneously) in order to buy more tickets. If a person does not have any tickets left to buy, the person will leave the line.

Return the time taken for the person initially at position k (0-indexed) to finish buying tickets.

Example 1:   
Input: tickets = [2,3,2], k = 2   
Output: 6   
Explanation:   
The queue starts as [2,3,2], where the kth person is underlined.   
After the person at the front has bought a ticket, the queue becomes [3,2,1] at 1 second.   
Continuing this process, the queue becomes [2,1,2] at 2 seconds.   
Continuing this process, the queue becomes [1,2,1] at 3 seconds.   
Continuing this process, the queue becomes [2,1] at 4 seconds.    
Note: the person at the front left the queue.   
Continuing this process, the queue becomes [1,1] at 5 seconds.   
Continuing this process, the queue becomes [1] at 6 seconds. The kth person has bought all their tickets, so return 6.

Example 2:   
Input: tickets = [5,1,1,1], k = 0   
Output: 8   
Explanation:   
The queue starts as [5,1,1,1], where the kth person is underlined.   
After the person at the front has bought a ticket, the queue becomes [1,1,1,4] at 1 second.   
Continuing this process for 3 seconds, the queue becomes [4] at 4 seconds.   
Continuing this process for 4 seconds, the queue becomes [] at 8 seconds. The kth person has bought all their tickets, so return 8.
 
Constraints:   
n == tickets.length   
1 <= n <= 100   
1 <= tickets[i] <= 100   
0 <= k < n   

```shell
public class Solution {
    public int TimeRequiredToBuy(int[] tickets, int k) {
        Queue<int> queue = new Queue<int>(tickets);
        int time = 0;
        // if queue.Count() == 0, then time = 0 will be return.
        
        while(queue.Count() > 0) {
            // get how many tickets the first person wants to buy
            int current = queue.Dequeue();
            
            // first person bought a ticket
            // -> takes 1 second and remain tickets need to be decreased by 1
            current--;
            time++;
            
            // if the remaning tickets are over 0,
            // they can be bought next turn
            if (current > 0) {
                queue.Enqueue(current);
            }
            
            // if the person we need to know the time to buy all tickets,
            // this means k = 0 and current = 0
            // so we can return time
            if (k == 0 && current == 0) {
                return time;
            }

            // if k is 3, after the front person bought a ticket,
            // this person has to go one step forward to 2
            k--;

            // if k was 0 then because of `k--` it will make k -1,
            // this means k needs to go back
            if (k == -1) {
                k = queue.Count()-1;
            }
        }

        return time;
    }
}
```
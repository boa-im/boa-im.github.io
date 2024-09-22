---
layout: post
title: Data Structure(4) - HashSet
date: 2024-09-20 23:47 -0400
category: [Study, Data Structure]
tags: [C#, Data Structure, HashSet]
---

## What is HashSet?
---
To know about HashSet, we need to understand what the `Hash` and `Set` are.
Hash
: Hash is a way to save and search data quickly using hash function. When users input some data, hash function calculate the hash code and save proper location. And when users search that data, system use the hash code to search quickly.
Set
: Set is a collection of non-duplicate elements. Whenever users try to enter same value to set, it won't be saved to Set.
HashSet
: HashSet can be use to prevent duplicate values and to save or search fast.

## How to declare a HashSet?
---
Same as other dynamic arrays, we can declare a HashSet like below.
```shell
HashSet<int> list1 = new HashSet<int>();
HashSet<string> list2 = new HashSet<string>();
```

## Methods
---
Let's see the methods that common used for HashSet!
#### Add
We can use `Add()` method for 2 situation.
1. To add a new element into a HashSet.
2. To check if the element with a value already in HashSet.

If there is no element with the value, `Add()` method will add the element into HashSet and return **True**. If not, it will return **False**
```shell
HashSet<int> list = new HashSet<int>();
Console.WriteLine(list.Add(1)); // True
Console.WriteLine(list.Add(1)); // False
Console.WriteLine(list.Add(2));

foreach(int item in list) {
    Console.WriteLine(item);
}
// 1
// 2
```

#### Remove
To remove a element with value, we can use `Remove()` method.
```shell
HashSet<int> list = new HashSet<int>();
Console.WriteLine(list.Add(1));
Console.WriteLine(list.Add(2));
Console.WriteLine(list.Add(3));
Console.WriteLine(list.Add(4));
Console.WriteLine(list.Add(5));

list.Remove(5); // list = {1, 2, 3, 4}
```

#### Clear
If you want to delete all elements in the HashSet, you can go with `Clear()` method.
```shell
HashSet<int> list = new HashSet<int>();
Console.WriteLine(list.Add(1));
Console.WriteLine(list.Add(2));
Console.WriteLine(list.Add(3));
Console.WriteLine(list.Add(4));
Console.WriteLine(list.Add(5));
// list = {1, 2, 3, 4, 5}

list.Clear();
// list = {}
```

#### Contains
Of course you can check if the element is already in HashSet using `Add()` method, but Add method will add the element into the hashset if the element is not in the HashSet although you don't want to add. For this case, when you just want to check if the elements are in the HashSet, you can use `Contains()` method.
```shell
HashSet<int> list = new HashSet<int>();
Console.WriteLine(list.Add(1));
Console.WriteLine(list.Add(2));
Console.WriteLine(list.Add(3));
Console.WriteLine(list.Add(4));
Console.WriteLine(list.Add(5));

Console.WriteLine(list.Contains(1)); // True
Console.WriteLine(list.Contains(6)); // False - you don't want to add 6 into HashSet.
```

## Example Problem
---
Let's solve [Valid Sudoku](https://leetcode.com/problems/valid-sudoku/description/)!

**Problem Description:**  
Determine if a 9 x 9 Sudoku board is valid. Only the filled cells need to be validated according to the following rules:   
Each row must contain the digits 1-9 without repetition.   
Each column must contain the digits 1-9 without repetition.   
Each of the nine 3 x 3 sub-boxes of the grid must contain the digits 1-9 without repetition.

Note:   
A Sudoku board (partially filled) could be valid but is not necessarily solvable.   
Only the filled cells need to be validated according to the mentioned rules.    

Example 1:   
![example_image](assets/img/data-structure-4/example1.jpg)   
Input: board =    
[["5","3",".",".","7",".",".",".","."]   
,["6",".",".","1","9","5",".",".","."]   
,[".","9","8",".",".",".",".","6","."]   
,["8",".",".",".","6",".",".",".","3"]   
,["4",".",".","8",".","3",".",".","1"]   
,["7",".",".",".","2",".",".",".","6"]   
,[".","6",".",".",".",".","2","8","."]   
,[".",".",".","4","1","9",".",".","5"]   
,[".",".",".",".","8",".",".","7","9"]]   
Output: true

Example 2:   
Input: board =    
[["8","3",".",".","7",".",".",".","."]   
,["6",".",".","1","9","5",".",".","."]   
,[".","9","8",".",".",".",".","6","."]   
,["8",".",".",".","6",".",".",".","3"]   
,["4",".",".","8",".","3",".",".","1"]   
,["7",".",".",".","2",".",".",".","6"]   
,[".","6",".",".",".",".","2","8","."]   
,[".",".",".","4","1","9",".",".","5"]   
,[".",".",".",".","8",".",".","7","9"]]   
Output: false   
Explanation: Same as Example 1, except with the 5 in the top left corner being modified to 8. Since there are two 8's in the top left 3x3 sub-box, it is invalid.
 
Constraints:   
board.length == 9   
board[i].length == 9   
board[i][j] is a digit 1-9 or '.'.

```shell
public class Solution {
    public bool IsValidSudoku(char[][] board) {
        // Set HashSet Array with length 9 for each row, column, and box.
        var row = new HashSet<char>[9];
        var col = new HashSet<char>[9];
        var box = new HashSet<char>[9];

        // declare 27 hashset into each array
        for(int i = 0; i < 9; i++) {
            row[i] = new HashSet<char>();
            col[i] = new HashSet<char>();
            box[i] = new HashSet<char>();
        }
        
        for(int i = 0; i < 9; i++) {
            for(int j = 0; j < 9; j++) {
                // if the value in board is `.` just continue the loop
                if(board[i][j] == '.') {
                    continue;
                }

                // this is for checking each row or col
                // if the value of board[i][j] is already in the HashSet,
                // Add method will return False then this IsValidSudoku return false
                if(!row[i].Add(board[i][j]) || !col[j].Add(board[i][j])) {
                    return false;
                }

                // in this case the first box is [0,0] - [2,2]: boxIndex = 0
                // the second box is [0,3] - [2, 5]: boxIndex = 1
                // this means there are 9 boxes total
                if(!box[j/3 + i/3*3].Add(board[i][j])) {
                    return false;
                }
            }
        }
        return true;
    }
}
```
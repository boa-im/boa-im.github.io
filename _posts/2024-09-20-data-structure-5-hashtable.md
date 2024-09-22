---
layout: post
title: Data Structure(5) - HashTable
date: 2024-09-20 23:48 -0400
category: [Study, Data Structure]
tags: [C#, Data Structure, HashTable, DictionaryEntry, Dictionary, KeyValuePair, SortedList]
---

## What is HashTable?
---
I already talked about what the Hash is in the previous post.
To understand table, I can draw a table.

| Key | Value |
|:-:|:-:|
| 1 | One |
| 2 | Two |
| 3 | Three |

As you can see this table, each value has the own key. We can access each value easily using Key. Unlike usual list has auto-incresement index, table's advantage is that we can use our own key like student number, employee number or bank account number.

## HashTable, Dictionary
---
HashTable is in _System.Collections_ namespace like ArrayList. This means HashTable also can save multiple type for key and value because HashTable saves a element as an object. So when we try to save key with int number to int variable, we have to cast it to int from object. To access each object in HashTable, we need to use `DictionaryEntry`.

And Dictinary is in _System.Collections.Generic_ namespace like List. This means we need to set the data type for key and value. To access each object in Dictionary, we need to use `KeyValuePair`.

Let's see the example code!

```shell
// HashTable Example
HashTable table1 = new HashTable();

// We can use multiple type of key and value
table1.Add(1, "One");           // int key, string value
table1.Add("Two", 2);           // string key, int value
table1.Add(3.14, "Pi");         // double key, string value
table1.Add("Version", 1.0);     // string key, double value

HashTable table2 = new HashTable();
table2.Add(1, "One");
table2.Add(2, "Two");
table2.Add(3, "Three");
// table2.Add(3, "Four"); - gives an error because key is duplicated.

// way to use DictionaryEntry type - you can do var instead of it
foreach(DictionaryEntry entry in table2) {
    // casting key to int type
    int key = (int) entry.Key;
    Console.WriteLine(key);
}


// Dictionary Example
Dictionary<int, string> dict = new Dictionary<int, string>();

// we need to follow the type for key and value
dict.Add(1, "One");
dict.Add(2, "Two");
dict.Add(3, "Three");

// way to use KeyValuePair type - you can do var instead of it
foreach(KeyValuePair<int, string> pair in dict) {
    // don't have to cast key to int type
    int key = pair.Key;
    Console.WriteLine(key);
}
```

## SortedList
---
SortedList is really similar with Dictionary. The only thing is different with Dictionary is that SortedList sorts the keys automatically regardless of the order in which the elements added in. SortedList is also in _System.Collections.Generic_ namespace. To access each object in SortedList, we also can use `KeyValuePair`.

```shell
SortedList<int, string> list = new SortedList<int, string>();

list.Add(3, "Three");
list.Add(1, "One");
list.Add(2, "Two");

foreach(KeyValuePair<int, string> pair in list) {
    Console.WriteLine(pair);
}
// Console
// [1, One]
// [2, Two]
// [3, Three]
```

## Methods
---
#### Remove
To remove an element in HashTable, Dictionary or SortedList, you need to know the **Key** to use `Remove()` method.
```shell
table2.Remove(1);
dict.Remove(1);
list.Remove(1);
```

#### Clear
We can use `Clear()` method to remove all element.
```shell
table2.Clear();
dict.Clear();
list.Clear();
```

#### ContainsKey, ContainsValue
When we need to check if there is a Key or a Value, we can use `ContainsKey()` or `ContainsValue()` method.
```shell
// HashTable.ContainsKey()
Console.WriteLine(table2.ContainsKey(1)); // true
Console.WriteLine(table2.ContainsKey(4)); // false

// HashTable.ContainsValue()
Console.WriteLine(table2.ContainsValue("One")); // true
Console.WriteLine(table2.ContainsValue("Four")); // false

// Dictionary.ContainsKey()
Console.WriteLine(dict.ContainsKey(1)); // true
Console.WriteLine(dict.ContainsKey(4)); // false

// Dictionary.ContainsValue()
Console.WriteLine(dict.ContainsValue("One")); // true
Console.WriteLine(dict.ContainsValue("Four")); // false

// SortedList.ContainsKey()
Console.WriteLine(list.ContainsKey(1)); // true
Console.WriteLine(list.ContainsKey(4)); // false

// SortedList.ContainsValue()
Console.WriteLine(list.ContainsValue("One")); // true
Console.WriteLine(list.ContainsValue("Four")); // false
```

## Example Problem
---
Let's solve [Group Anagrams](https://leetcode.com/problems/group-anagrams/description/)!

**Problem Description:**  
Given an array of strings strs, group the anagrams together. You can return the answer in any order.

Example 1:   
Input: strs = ["eat","tea","tan","ate","nat","bat"]   
Output: [["bat"],["nat","tan"],["ate","eat","tea"]]   
Explanation:   
There is no string in strs that can be rearranged to form "bat".   
The strings "nat" and "tan" are anagrams as they can be rearranged to form each other.   
The strings "ate", "eat", and "tea" are anagrams as they can be rearranged to form each other.

Example 2:   
Input: strs = [""]   
Output: [[""]]

Example 3:   
Input: strs = ["a"]   
Output: [["a"]]

Constraints:   
1 <= strs.length <= 104   
0 <= strs[i].length <= 100   
strs[i] consists of lowercase English letters.

```shell
public class Solution {
    public IList<IList<string>> GroupAnagrams(string[] strs) {
        // to use the sorted string as a key, set a dictionary
        // each key has many value. So I use a List as a Value
        Dictionary<string, List<string>> result = new Dictionary<string, List<string>>();

        // check the items in strs
        foreach(string a in strs) {
            // To sort string, convert string to char array
            char[] keyChars = a.ToCharArray();
            Array.Sort(keyChars);
            
            // save the sorted string as a key
            string key = new string(keyChars);

            // if Dictionary does not contains key with value of the string key,
            // create a new key and add a new list as a value
            if(!result.ContainsKey(key))
                result[key] = new List<string>();

            // add the original value into the list
            result[key].Add(a);
        }

        // return the values in dictionary
        return new List<IList<string>>(result.Values);
    }
}
```
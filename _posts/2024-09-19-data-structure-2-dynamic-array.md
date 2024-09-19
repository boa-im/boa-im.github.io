---
layout: post
title: Data Structure(2) - Dynamic Array
date: 2024-09-19 15:26 -0400
category: [Study, Data Structure]
tags: [C#, Data Structure, Dynamic Array]
---

## What is Dynamic Array?
---
We already studied about the array in my previous post. We only can use array when we already know the size of the array or we don't have to add more elements into array. But sometimes we might not know the array size or we might want to add elements.   
To solve this problem, we can use dynamic array. In this post, I'll introduce `ArrayList` and `List`.

## ArrayList, List
---
ArrayList
: ArrayList can save many data types in one ArrayList because ArrayList saves element as a _object_.
That means every time we need to access to the element, we need to cast it. Let me give an example.

```shell
ArrayList arrayList = new ArrayList(); // we don't have to define a data type

arrayList.Add(100);
arrayList.Add("Hello, World!"); // arrayList can saves multiple data type

int firstVal = (int) arrayList[0] // casting to int from object
string secondVal = (string) arrayList[1] // casting to int from object
```

List
: If you already know that you only need to use one data type, then you can use List. 
We need to define the data type for a List.

```shell
List<int> list = new List<int>();

list.Add(1);
list.Add(100); // based on the defiend data type, we only can add int type value
list.AddRange(new int[] {2, 3, 4}); // add multiple values in one line
```

## Methods
---
ArrayList and List have common methods. Let's see how they are used!

#### Add
We can use `Add()` to add new element.
```shell
ArrayList arrayList = new ArrayList();
List<int> list = new List<int>();

arrayList.Add(1);
list.Add(1);
```

#### Insert
If there is a list that already has 4 elements and you want to insert a element in the middle, you just need to use `Insert()` with index.
```shell
ArrayList arrayList = new ArrayList();
List<int> list = new List<int>();

arrayList.AddRange(new int[] {1, 2, 3, 5});
list.AddRange(new int[] {2, 3, 4, 5});

arrayList.Insert(3, 4); // {1, 2, 3, 4, 5}
list.Insert(0, 1); // {1, 2, 3, 4, 5}
```

#### Remove
If you want to delete a element from ArrayList or List, you can use `Remove()`.
```shell
ArrayList arrayList = new ArrayList();
List<int> list = new List<int>();

arrayList.Add(1);
list.Add(1);

arrayList.Remove(1);
list.Remove(1);
```

#### RemoveAt
If you only know the element's index to delete, you can use `RemoveAt()`.
```shell
ArrayList arrayList = new ArrayList();
List<int> list = new List<int>();

arrayList.Add(1);
list.Add(1);

arrayList.RemoveAt(0);
list.RemoveAt(0);
```

#### Clear
To remove all the elements in the ArrayList or List, we need to use `Clear()` method.
```shell
ArrayList arrayList = new ArrayList();
List<int> list = new List<int>();

arrayList.Add(1);
list.Add(1);

arrayList.Remove(1);
list.Remove(1);
```

#### Sort
To sort the elements by ascending, we can use `Sort()` method.
```shell
ArrayList arrayList = new ArrayList();
List<int> list = new List<int>();

arrayList.AddRange(new int[] {2, 1, 5, 3, 4});
list.AddRange(new int[] {3, 4, 5, 1, 2});

arrayList.Sort(); // {1, 2, 3, 4, 5}
list.Sort(); // {1, 2, 3, 4, 5}
```

#### Contains
Do you want to check a value is in ArrayList or List? You can use `Contains()`!
```shell
ArrayList arrayList = new ArrayList();
List<int> list = new List<int>();

arrayList.AddRange(new int[] {2, 1, 5, 3, 4});
list.AddRange(new int[] {3, 4, 5, 1, 2});

Console.WriteLine(arrayList.Contains(1)); // True
Console.WriteLine(list.Contains(6)); // False
```
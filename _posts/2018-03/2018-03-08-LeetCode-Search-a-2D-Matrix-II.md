---
layout: post
title: LeetCode - Search a 2D Matrix II
categories:
    - LeetCode(Second)
tags:
    - LeetCode(Second)
    - Medium
    - Binary Search
excerpt_separator: "<!--more-->"
---

### Question Definition
Write an efficient algorithm that searches for a value in an m x n matrix. This matrix has the following properties:

* Integers in each row are sorted in ascending from left to right.
* Integers in each column are sorted in ascending from top to bottom.
<!--more-->

For example,

Consider the following matrix:
```
[
  [1,   4,  7, 11, 15],
  [2,   5,  8, 12, 19],
  [3,   6,  9, 16, 22],
  [10, 13, 14, 17, 24],
  [18, 21, 23, 26, 30]
]
```
Given target = 5, return true.

Given target = 20, return false.
### Java Solution
```java
public boolean searchMatrix(int[][] matrix, int target) {
    if(matrix.length == 0 || matrix[0].length == 0 || target < matrix[0][0])
        return false;
    int i = 0;
    int j = 0;
    while(i < matrix.length){
        while(j < matrix[i].length){
            if(matrix[i][j] == target) return true;
            if(matrix[i][j] > target) break;
            j++;
        }
        i++;
        j = 0;
    }
    return false;
}
```
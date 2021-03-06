---
layout: post
title: LeetCode - Integer Replacement
categories:
    - LeetCode
tags:
    - LeetCode
    - Medium
    - Math
    - Dynamic Programming
excerpt_separator: "<!--more-->"
---

### Question Definition

Given a positive integer n and you can do operations as follow:

If n is even, replace n with n/2.
If n is odd, you can replace n with either n + 1 or n - 1.
What is the minimum number of replacements needed for n to become 1?
<!--more-->

**Example 1:**
```
Input:
8

Output:
3

Explanation:
8 -> 4 -> 2 -> 1
```
**Example 2:**
```
Input:
7

Output:
4

Explanation:
7 -> 8 -> 4 -> 2 -> 1
or
7 -> 6 -> 3 -> 2 -> 1
```
### Java Solution
```java
public int integerReplacement(long n) {
    if(n <= 1)
        return 0;
    int result = 0;
    if(n % 2 == 0){
        while(n % 2 == 0){
            n = n / 2;
            result++;
        }
        result = integerReplacement(n) + result;
    }else{
        result = Math.min(integerReplacement(n + 1), integerReplacement(n - 1)) + 1;
    }
    return result;
}
```
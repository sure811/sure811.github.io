---
layout: post
title: LeetCode - Next Permutation
categories:
    - LeetCode
tags:
    - LeetCode
    - Medium
    - Array
excerpt_separator: "<!--more-->"
---

### Question Definition

Implement next permutation, which rearranges numbers into the lexicographically next greater permutation of numbers.

If such arrangement is not possible, it must rearrange it as the lowest possible order (ie, sorted in ascending order).

The replacement must be in-place, do not allocate extra memory.
<!--more-->

Here are some examples. Inputs are in the left-hand column and its corresponding outputs are in the right-hand column.
```
1,2,3 → 1,3,2
3,2,1 → 1,2,3
1,1,5 → 1,5,1
```

### Java Solution
```java
public void nextPermutation(int[] nums) {
    if(nums.length <= 1)
        return;
    int start = nums.length - 2;
    while(start >= 0 && nums[start] >= nums[start + 1])
        start--;
    if(start > -1){
        int end = nums.length - 1;
        while(end > start && nums[end] <= nums[start])
            end--;
        int temp = nums[start];
        nums[start] = nums[end];
        nums[end] = temp;

    }
    revert(nums, start + 1, nums.length - 1);
}

private void revert(int[] nums, int start, int end){
    while(start < end){
        int temp = nums[start];
        nums[start] = nums[end];
        nums[end] = temp;
        start++;
        end--;
    }
}
```

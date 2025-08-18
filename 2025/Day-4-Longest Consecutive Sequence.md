# [4] Longest Consecutive Sequence

**Date**: 2025-08-15

**Difficulty**: Medium

**Link**: [LeetCode Problem](https://leetcode.com/problems/longest-consecutive-sequence/description/?envType=study-plan-v2&envId=top-interview-150)

## Problem Statement

Given an unsorted array of integers nums, return the length of the longest consecutive elements sequence.

You must write an algorithm that runs in O(n) time.

 

Example 1:

Input: nums = [100,4,200,1,3,2]
Output: 4
Explanation: The longest consecutive elements sequence is [1, 2, 3, 4]. Therefore its length is 4.
Example 2:

Input: nums = [0,3,7,2,5,8,4,6,0,1]
Output: 9
Example 3:

Input: nums = [1,0,1,2]
Output: 3
 

Constraints:

0 <= nums.length <= 105
-109 <= nums[i] <= 109

## Solution

```python
class Solution:
    def longestConsecutive(self, nums: List[int]) -> int:
        num = set(nums)
        longest = 0
        for n in num:
            if n - 1 not in num:
                length = 1
                while n + length in num:
                    length+=1
                longest = max(longest, length)
        return longest
```

## Notes

- Time complexity: O(n)
- Space complexity: O(n)
- Ý tưởng:
    + Dùng set
    + Chỉ bắt đầu đếm tại những số là đầu dãy liên tiếp (không có num-1 trong set). Khi đã là đầu dãy, ta đếm tiếp num+1, num+2, ... cho đến khi dừng
- Ví dụ: 
```
nums = [100, 4, 200, 1, 3, 2]
set = {100, 4, 200, 1, 3, 2}
```

+ 100: 99 không có → là đầu dãy. Đếm: 100 (1), 101 không có → dừng. longest = 1.
+ 4: có 3 trong set → không là đầu dãy → bỏ qua.
+ 200: 199 không có → đầu dãy. Đếm: 200 (1), 201 không → dừng. longest = 1.
+ 1: 0 không có → đầu dãy. Đếm: 1(1), 2(2), 3(3), 4(4), 5 không → dừng. longest = 4.
+ 3, 2: đều có 2, 1 phía trước → không phải đầu dãy → bỏ qua.

=> return longest = 4
---
**Time**: 15 minutes  
**Status**: ✅ Solved 
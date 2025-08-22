# [8] Nth Digit

**Date**: 2025-08-21

**Difficulty**: Medium

**Link**: [LeetCode Problem](https://leetcode.com/problems/nth-digit/description/)

## Problem Statement

Given an integer n, return the nth digit of the infinite integer sequence [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, ...].

 

Example 1:

Input: n = 3
Output: 3
Example 2:

Input: n = 11
Output: 0
Explanation: The 11th digit of the sequence 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, ... is a 0, which is part of the number 10.
 

Constraints:

1 <= n <= 231 - 1

## Solution

```python
class Solution:
    def findNthDigit(self, n: int) -> int:
        d = 1        
        count = 9    
        start = 1
        while n > d * count:
            n -= d * count
            d *= 1
            d += 1
            count *= 10
            start *= 10

        num = start + (n - 1) // d
        idx = (n - 1) % d 

        return (num // (10 ** (d - 1 - idx))) % 10
```

## Notes

- Figure out what digit length (d) numbers we’re in.
- Digits of length 1: 1–9 → 9 numbers → 9 digits
- Digits of length 2: 10–99 → 90 numbers → 180 digits
- Digits of length 3: 100–999 → 900 numbers → 2700 digits
- Subtract blocks until we land in the right digit-length range.
- Find the actual number containing the digit.
- Extract the digit from that number.
- Time complexity: O(logn)
- Space complexity: O(1)
---
**Time**: 50 minutes  
**Status**: ✅ Solved 
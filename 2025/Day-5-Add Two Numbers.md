# [5] Add Two Numbers

**Date**: 2025-08-18

**Difficulty**: Medium

**Link**: [LeetCode Problem](https://leetcode.com/problems/add-two-numbers/description/?envType=problem-list-v2&envId=linked-list)

## Problem Statement

You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

 

Example 1:


Input: l1 = [2,4,3], l2 = [5,6,4]
Output: [7,0,8]
Explanation: 342 + 465 = 807.
Example 2:

Input: l1 = [0], l2 = [0]
Output: [0]
Example 3:

Input: l1 = [9,9,9,9,9,9,9], l2 = [9,9,9,9]
Output: [8,9,9,9,0,0,0,1]
 

Constraints:

The number of nodes in each linked list is in the range [1, 100].
0 <= Node.val <= 9
It is guaranteed that the list represents a number that does not have leading zeros.

## Solution

```python
class Solution:
    def addTwoNumbers(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
        dummy = ListNode()
        tail = dummy
        remain = 0
        while l1 or l2 or remain:
            x = l1.val if l1 else 0
            y = l2.val if l2 else 0
            sum = x + y + remain
            remain = sum // 10
            digit = sum % 10

            tail.next = ListNode(digit)
            tail = tail.next
            l1 = l1.next if l1 else None
            l2 = l2.next if l2 else None
        return dummy.next
```

## Notes

- Time complexity: O(n+m)
- Space complexity: O(1)
---
**Time**: 15 minutes  
**Status**: ✅ Solved 
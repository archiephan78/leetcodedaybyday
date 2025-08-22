# [7] Merge k Sorted Lists

**Date**: 2025-08-20

**Difficulty**: Medium

**Link**: [LeetCode Problem](https://leetcode.com/problems/merge-k-sorted-lists/description/)

## Problem Statement

You are given an array of k linked-lists lists, each linked-list is sorted in ascending order.

Merge all the linked-lists into one sorted linked-list and return it.

 

Example 1:

Input: lists = [[1,4,5],[1,3,4],[2,6]]
Output: [1,1,2,3,4,4,5,6]
Explanation: The linked-lists are:
[
  1->4->5,
  1->3->4,
  2->6
]
merging them into one sorted linked list:
1->1->2->3->4->4->5->6
Example 2:

Input: lists = []
Output: []
Example 3:

Input: lists = [[]]
Output: []
 

Constraints:

k == lists.length
0 <= k <= 104
0 <= lists[i].length <= 500
-104 <= lists[i][j] <= 104
lists[i] is sorted in ascending order.
The sum of lists[i].length will not exceed 104.

## Solution

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def mergeKLists(self, lists: List[Optional[ListNode]]) -> Optional[ListNode]:
        hq = []
        for l in lists:
            while l:
                heapq.heappush(hq, l.val)
                l = l.next
                print("=====")
                print(l)
        result = None
        print("====1")
        print(hq)
        while hq:
            #get minium
            val = heapq.heappop(hq)
            print(val)
            if not l:
                l = ListNode(val)
                result = l
                print("====2")
                print(result)
            else:
                l.next = ListNode(val)
                l = l.next
        return result
```

## Notes

- Using heap queue algorithm
- Time complexity: O(n log n)
- Space complexity: O(n)
---
**Time**: 30 minutes  
**Status**: ✅ Solved 
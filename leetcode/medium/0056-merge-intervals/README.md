# Merge Intervals

![Difficulty](https://img.shields.io/badge/Difficulty-Medium-yellow)

## Problem

Given an array of `intervals` where `intervals[i] = [starti, endi]`, merge all overlapping intervals, and return  *an array of the non-overlapping intervals that cover all the intervals in the input*.

 

 **Example 1:** 

```
Input: intervals = [[1,3],[2,6],[8,10],[15,18]]
Output: [[1,6],[8,10],[15,18]]
Explanation: Since intervals [1,3] and [2,6] overlap, merge them into [1,6].

```

 **Example 2:** 

```
Input: intervals = [[1,4],[4,5]]
Output: [[1,5]]
Explanation: Intervals [1,4] and [4,5] are considered overlapping.

```

 **Example 3:** 

```
Input: intervals = [[4,7],[1,4]]
Output: [[1,7]]
Explanation: Intervals [1,4] and [4,7] are considered overlapping.

```

 

 **Constraints:** 

- 1 <= intervals.length <= 104
- intervals[i].length == 2
- 0 <= starti <= endi <= 104

## Solution

**Language:** Java  
**Runtime:** 9 ms (beats 33.42%)  
**Memory:** 49.1 MB (beats 60.20%)  
**Submitted:** 2026-10-14T15:07:37.035Z  

```java

import java.util.*;

class Solution {
    public int[][] merge(int[][] intervals) {
        Arrays.sort(intervals, (a, b) -> Integer.compare(a[0], b[0]));

        List<int[]> ans = new ArrayList<>();

        for (int[] curr : intervals) {
            if (ans.isEmpty() ||
                ans.get(ans.size() - 1)[1] < curr[0]) {
                ans.add(curr);
            } else {
                ans.get(ans.size() - 1)[1] =
                    Math.max(ans.get(ans.size() - 1)[1], curr[1]);
            }
        }

        return ans.toArray(new int[ans.size()][]);
    }
}

```

---

[View on LeetCode](https://leetcode.com/problems/merge-intervals/)
# 4Sum

![Difficulty](https://img.shields.io/badge/Difficulty-Medium-yellow)

## Problem

Given an array `nums` of `n` integers, return  *an array of all the  **unique**  quadruplets*  `[nums[a], nums[b], nums[c], nums[d]]` such that:

- 0 <= a, b, c, d < n
- a, b, c, and d are distinct.
- nums[a] + nums[b] + nums[c] + nums[d] == target

You may return the answer in  **any order**.

 

 **Example 1:** 

```
Input: nums = [1,0,-1,0,-2,2], target = 0
Output: [[-2,-1,1,2],[-2,0,0,2],[-1,0,0,1]]

```

 **Example 2:** 

```
Input: nums = [2,2,2,2,2], target = 8
Output: [[2,2,2,2]]

```

 

 **Constraints:** 

- 1 <= nums.length <= 200
- -109 <= nums[i] <= 109
- -109 <= target <= 109

## Solution

**Language:** Java  
**Runtime:** 167 ms (beats 5.55%)  
**Memory:** 47.6 MB (beats 6.71%)  
**Submitted:** 2026-10-09T14:25:09.045Z  

```java
class Solution {
    public List<List<Integer>> fourSum(int[] nums, int target) {
         if(nums==null || nums.length<4){
            return new ArrayList<>();
        }
        Arrays.sort(nums);
        Set<List<Integer>> result =new HashSet<>(); 
        for(int i=0;i<nums.length-3;i++){
            for(int j=i+1;j<nums.length-2;j++){
            int left=j+1;
            int right=nums.length-1;
            while(left<right){
                long sum=(long) nums[i]+nums[j]+nums[left]+nums[right];
                if(sum==target){

                result.add(Arrays.asList(nums[i],nums[j],nums[left],nums[right]));
                left++;
                right--;
                }
            
            else if(sum<target){
                left++;
            }
            else{
                right--;
            
            }


            }
            }
        }
        return new ArrayList<>(result);
    }
}
```

---

[View on LeetCode](https://leetcode.com/problems/4sum/)
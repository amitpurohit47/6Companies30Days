# Minimum Size Subarray Sum

[![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/minimum-size-subarray-sum)

Given an array of positive integers nums and a positive integer target, return the minimal length of a contiguous subarray [numsl, numsl+1, ..., numsr-1, numsr] of which the sum is greater than or equal to target. If there is no such subarray, return 0 instead.

### Example 1

```
Input: target = 7, nums = [2,3,1,2,4,3]
Output: 2
```

### Example 2

```
Input: target = 4, nums = [1,4,4]
Output: 1
```

### Solution

```cpp
class Solution {
public:
    int minSubArrayLen(int target, vector<int>& nums) {

        int n,i,sum,ans,j;

        n=nums.size();
        sum = 0;
        i=0;
        j=0;
        ans=INT_MAX;

        while(j<n){
            sum+=nums[j];

            while(sum>=target && i<=j){
                ans = min(ans,j-i+1);
                sum-=nums[i];
                i++;
            }

            j++;

        }

        if(ans==INT_MAX) return 0;
        return ans;

    }
};
```

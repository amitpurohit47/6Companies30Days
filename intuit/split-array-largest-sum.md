# Split Array Largest Sum

[![Problem Link](../assets/lc.svg)](https://leetcode.com/problems/split-array-largest-sum)

Given an array nums which consists of non-negative integers and an integer m, you can split the array into m non-empty continuous subarrays.

Write an algorithm to minimize the largest sum among these m subarrays.

### Example 1
```
Input: nums = [7,2,5,10,8], m = 2
Output: 18
```

### Example 2
```
Input: nums = [1,2,3,4,5], m = 2
Output: 9
```

### Solution
```cpp
class Solution {
public:
    
    int canIPlace(vector<int>& v, int m, int mid){
        int j=0,sum=0;
        for(auto g:v){
            sum+=g;
            if(j==m) break;
            if(sum>mid){
                sum=g;
                j++;
            }
        }
        j++;
        return j<=m;
    }
    
    int splitArray(vector<int>& v, int m) {
        int mx = *max_element(v.begin(),v.end()),lo = mx,hi = accumulate(v.begin(),v.end(),0),ans=INT_MAX;
        while(lo<=hi){
            int mid = lo + (hi-lo)/2;
            if(canIPlace(v,m,mid)) hi = mid - 1,ans=min(ans,mid);
            else lo = mid + 1;
        }
        return ans;
    }
};
```


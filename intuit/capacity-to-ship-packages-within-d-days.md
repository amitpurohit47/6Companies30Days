# Capacity To Ship Packages Within D Days

[![Problem Link](../assets/lc.svg)](https://leetcode.com/problems/capacity-to-ship-packages-within-d-days/)

A conveyor belt has packages that must be shipped from one port to another within days days.

The ith package on the conveyor belt has a weight of weights[i]. Each day, we load the ship with packages on the conveyor belt (in the order given by weights). We may not load more weight than the maximum weight capacity of the ship.

Return the least weight capacity of the ship that will result in all the packages on the conveyor belt being shipped within days days.

### Example 1
```
Input: weights = [1,2,3,4,5,6,7,8,9,10], days = 5
Output: 15
```

### Example 2
```
Input: weights = [3,2,2,4,1,4], days = 3
Output: 6
```

### Solution
```cpp
class Solution {
public:
    
    bool canIPlace(vector<int>& nums, int mid, int m){
        int i,j=0,sum=0,n=nums.size();
        for(i=0;i<n;i++){
            if(j>m) return false;
            if(nums[i]>mid) return false;
            if(sum+nums[i]<=mid) sum+=nums[i];
            else sum=nums[i],j++;
        }
        j++;
        return j<=m;
    }
    
    int shipWithinDays(vector<int>& weights, int days) {
        int mx=-1,sum=0;
        for(auto g:weights) mx=max(mx,g),sum+=g;
        int lo = mx,hi=sum;
        while(lo<=hi){
            int mid = lo + (hi-lo)/2;
            // cout<<mid<<"\n";
            if(canIPlace(weights,mid,days)) hi = mid - 1;
            else lo = mid + 1;
        }
        return lo;
    }
};
```

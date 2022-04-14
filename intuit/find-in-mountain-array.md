# Find in Mountain Array

[![Problem Link](../assets/lc.svg)](https://leetcode.com/problems/find-in-mountain-array/)

Given a mountain array mountainArr, return the minimum index such that mountainArr.get(index) == target. If such an index does not exist, return -1.

### Example 1
```
Input: array = [1,2,3,4,5,3,1], target = 3
Output: 2
```

### Example 2
```
Input: array = [0,1,2,4,2,1], target = 3
Output: -1
```

### Solution
```cpp
class Solution {
public:
    int findInMountainArray(int target, MountainArray &mountainArr) {
        int lo=0,hi=mountainArr.length()-1,peak;
        while(lo<hi){
            int mid = lo + (hi-lo)/2;
            if(mountainArr.get(mid) < mountainArr.get(mid+1)) lo = mid + 1;
            else hi = mid;
        }
        peak = lo;
        lo = 0;
        hi = peak;
        while(lo<=hi){
            int mid = lo + (hi-lo)/2;
            int b = mountainArr.get(mid);
            if(b == target) return mid;
            else if(b<target) lo = mid + 1;
            else hi = mid - 1;
        }
        lo = peak;
        hi=mountainArr.length()-1;
        while(lo<=hi){
            int mid = lo + (hi-lo)/2;
            int b = mountainArr.get(mid);
            if(b == target) return mid;
            else if(b>target) lo = mid + 1;
            else hi = mid - 1;
        }
        return -1;
    }
};
```


# Array Pair Sum Divisibility Problem

[![Problem Link](https://img.shields.io/badge/GeeksforGeeks-298D46?style=for-the-badge&logo=geeksforgeeks&logoColor=white)](https://practice.geeksforgeeks.org/problems/array-pair-sum-divisibility-problem3257/1#)

Given an array of integers and a number k, write a function that returns true if given array can be divided into pairs such that sum of every pair is divisible by k.

### Sample Input

```
4 6
9 7 5 3
```

### Sample Output

```
True
```

### Solution

```cpp
class Solution {
  public:
    bool canPair(vector<int> nums, int k) {
        // Code here.
        if(nums.size()%2) return false;
        map<int,int> mp;
        for(int i=0;i<nums.size();i++){
            nums[i] = nums[i]%k;
            mp[nums[i]]++;
        }
        if(mp[0]%2) return false;
        for(int i=0;i<nums.size();i++){
            if(nums[i] && mp[nums[i]] != mp[k-nums[i]]) return false;
        }
        return true;
    }
};
```


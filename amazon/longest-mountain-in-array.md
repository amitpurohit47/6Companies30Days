# Longest Mountain in Array

[![Problem Link](../assets/lc.svg)](https://leetcode.com/problems/longest-mountain-in-array/)

You may recall that an array arr is a mountain array if and only if:

- arr.length >= 3
- There exists some index i (0-indexed) with 0 < i < arr.length - 1 such that:
  - arr[0] < arr[1] < ... < arr[i - 1] < arr[i]
  - arr[i] > arr[i + 1] > ... > arr[arr.length - 1]

Given an integer array arr, return the length of the longest subarray, which is a mountain. Return 0 if there is no mountain subarray.

### Example 1

```
Input: arr = [2,1,4,7,3,2,5]
Output: 5
```

### Example 2

```
Input: arr = [2,2,2]
Output: 0
```

### Solution

```cpp
class Solution {
public:
    int longestMountain(vector<int>& arr) {
        if(arr.size()<3) return 0;

        int i,n,j,ans=0;

        i=1;
        n=arr.size();


        while(i<n){
            while(i<n && arr[i]<=arr[i-1]) i++;
            j=i-1;
            while(i<n && arr[i]>arr[i-1]) i++;
            if(i==n) return ans;
            if(arr[i]==arr[i-1]){
                while(i<n && arr[i]==arr[i-1]) i++;
                while(i<n && arr[i]<=arr[i-1]) i++;
                j=i-1;
                continue;
            }
            while(i<n && arr[i]<arr[i-1]) i++;
            ans=max(ans,i-j);
            j=i-1;
        }

        return ans;
    }
};
```

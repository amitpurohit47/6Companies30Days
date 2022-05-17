# Sorted subsequence of size 3

[![Problem Link](../assets/gfg.svg)](https://practice.geeksforgeeks.org/problems/sorted-subsequence-of-size-3/1/#)

Given an array A of N integers, find any 3 elements in it such that A[i] < A[j] < A[k] and i < j < k.

### Sample Input
```
5
1 2 1 1 3
```
### Sample Output
```
1 2 3
```

### Solution
```cpp
class Solution{
  public:
    vector<int> find3Numbers(vector<int> arr, int n) {
        // Your code here
        vector<int> v;
        if(n<3) return v;
        vector<int> mx(n),mi(n);
        mi[0] = arr[0];
        mx[n-1] = arr[n-1];
        for(int i=1;i<n;i++) mi[i] = min(mi[i-1],arr[i]);
        for(int i=n-2;i>=0;i--) mx[i] = max(mx[i+1],arr[i]);
        for(int i=1;i<n-1;i++){
            if(mi[i-1]<arr[i] && arr[i]<mx[i+1]){
                v.push_back(mi[i-1]);
                v.push_back(arr[i]);
                v.push_back(mx[i+1]);
                return v;
            }
        }
        return v;
    }
};
```


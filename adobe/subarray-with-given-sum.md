# Subarray with given sum

[![Problem Link](../assets/gfg.svg)](https://practice.geeksforgeeks.org/problems/subarray-with-given-sum-1587115621/1#)

Given an unsorted array A of size N that contains only non-negative integers, find a continuous sub-array which adds to a given number S.

### Sample Input
```
5 12
1 2 3 7 5
```
### Sample Output
```
2 4
```

### Solution
```cpp
#define ll long long

class Solution
{
    public:
    //Function to find a continuous sub-array which adds up to a given number.
    vector<int> subarraySum(int arr[], int n, ll s)
    {
        // Your code here
        ll i=0,j=0,sum=0;
        while(1){
            while(sum<s && j<n){
                sum+=arr[j];
                j++;
            }
            while(sum>s && i<=j){
                sum-=arr[i];
                i++;
            }
            if(sum==s) return {i+1,j};
            if(j==n) break;
        }
        return {-1};
    }
};
```


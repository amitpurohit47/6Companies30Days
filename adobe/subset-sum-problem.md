# Partition Equal Subset Sum

[![Problem Link](../assets/gfg.svg)](https://practice.geeksforgeeks.org/problems/subset-sum-problem2014/1#)

Given an array arr[] of size N, check if it can be partitioned into two parts such that the sum of elements in both parts is the same.

### Sample Input
```
4
1 5 11 5
```

### Sample Output
```
YES
```

### Solution
```cpp
class Solution{
public:
    int equalPartition(int n, int arr[])
    {
        // code here
        int sum=0,i,j;
        for(i=0;i<n;i++) sum+=arr[i];
        if(sum%2) return 0;
        int dp[n+1][sum/2+1];
        for(i=0;i<=n;i++) dp[i][0] = 1;
        for(i=1;i<=(sum/2);i++) dp[0][i] = 0;
        for(i=1;i<=n;i++){
            for(j=1;j<=sum/2;j++){
                dp[i][j] = dp[i-1][j];
                if(j-arr[i-1]>=0) dp[i][j] = dp[i][j] || dp[i-1][j-arr[i-1]];
            }
        }
        return dp[n][sum/2];
    }
};
```



# Minimum sum partition

[![Problem Link](../assets/gfg.svg)](https://practice.geeksforgeeks.org/problems/minimum-sum-partition3317/1/#)

Given an integer array arr of size N, the task is to divide it into two sets S1 and S2 such that the absolute difference between their sums is minimum and find the minimum difference

### DP Table

![image](https://user-images.githubusercontent.com/44930179/148940265-8eb4f3ab-2a6e-413d-94d6-2b5b7e3a83a8.png)

### Sample Input

```
8
5 6 6 5 7 4 7 6
```

### Sample Output

```
0
```

### Solution

```cpp
class Solution{

  public:
	int minDifference(int arr[], int n)  {
	    // Your code goes here
	    int i,j,sum=0;
	    for(i=0;i<n;i++) sum+=arr[i];
	    int dp[n+1][sum+1];
        for(i=0;i<=sum;i++) dp[0][i] = 0;
        for(i=0;i<=n;i++) dp[i][0] = 1;
        for(i=1;i<=n;i++){
            for(j=1;j<=sum;j++){
                dp[i][j] = dp[i-1][j];
                if(j-arr[i-1]>=0) dp[i][j] = dp[i][j] || dp[i-1][j-arr[i-1]];
            }
        }
        int mi = INT_MAX;
        for(i=0;i<=sum;i++) if(dp[n][i]) mi=min(mi,abs((sum-i)-i));
        return mi;
	}
};

```

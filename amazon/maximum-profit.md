# Maximum Profit

[![Problem Link](../assets/gfg.svg)](https://practice.geeksforgeeks.org/problems/maximum-profit4657/1#)

In the stock market, a person buys a stock and sells it on some future date. Given the stock prices of N days in an array A[ ] and a positive integer K, find out the maximum profit a person can make in at-most K transactions. A transaction is equivalent to (buying + selling) of a stock and new transaction can start only when the previous transaction has been completed.

### DP Table (Hint)

![Hint Table](https://user-images.githubusercontent.com/44930179/148659858-dd45a472-54b3-4561-8bda-b7c35b2df318.png)

### Sample Input

```
2
6
10 22 5 75 65 80
```

### Sample Output

```
87
```

### Solution

```cpp
class Solution {
  public:
    int maxProfit(int k, int n, int a[]) {
        // code here
        int i,j,t,dp[k+1][n];
        for(i=0;i<n;i++) dp[0][i] = 0;
        for(i=0;i<=k;i++) dp[i][0] = 0;
        for(i=1;i<=k;i++){
            int mx=dp[i-1][0] - a[0];
            for(j=1;j<n;j++){
                dp[i][j] = max(dp[i][j-1],mx+a[j]);
                mx = max(mx,dp[i-1][j]-a[j]);
            }
        }
        return dp[k][n-1];
    }
};
```

# Express as sum of power of natural numbers

[![Problem Link](../assets/gfg.svg)](https://practice.geeksforgeeks.org/problems/express-as-sum-of-power-of-natural-numbers5647/1#)

Given two numbers n and x, find out the total number of ways n can be expressed as sum of xth power of unique natural numbers.As total number of ways can be very large ,so return the number of ways modulo 10<sup>9</sup> + 7.

### Sample Input
```
1
10 2
```

### Sample Output
```
1
```

### Solution
```cpp
#define mod 1000000007

class Solution{
    public:
    int numOfWays(int s, int x)
    {
        // code here
        vector<int> pows;
        int cur=1,i=1;
        while(cur<=s){
            pows.push_back(cur);
            i++;
            cur=pow(i,x);
        }
        int n=pows.size(),j;
        vector<vector<int>> dp(n+1,vector<int> (s+1,0));
        for(i=1;i<=s;i++) dp[0][i] = 0;
        dp[0][0] = 1;
        for(i=1;i<=n;i++){
            for(j=0;j<=s;j++){
                if(pows[i-1]>j) dp[i][j] = dp[i-1][j];
                else dp[i][j] = (dp[i-1][j]%mod + dp[i-1][j-pows[i-1]]%mod)%mod;
            }
        }
        return dp[n][s]%mod;
    }
};
```


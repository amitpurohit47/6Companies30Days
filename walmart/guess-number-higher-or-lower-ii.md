# Guess Number Higher or Lower II

[![Problem Link](../assets/lc.svg)](https://leetcode.com/problems/guess-number-higher-or-lower-ii/)


### Example 1
```
Input: n = 10
Output: 16
```

### Example 2
```
Input: n = 1
Output: 0
```

### Solution
```cpp
class Solution {
public:
    
    
    int dp(int i,int j,vector<vector<int>> &mp){
        if(i>=j) return 0;
        if(mp[i][j]!=-1) return mp[i][j];
        int res=INT_MAX;
        for(int k=i;k<=j;k++){
            int t = k + max(dp(i,k-1,mp),dp(k+1,j,mp));
            res = min(res,t);
        }
        return mp[i][j] = res;
    }
    
    int getMoneyAmount(int n) {
        vector<vector<int>> mp(n+1,vector<int> (n+1,-1));
        return dp(1,n,mp);
    }
};
```
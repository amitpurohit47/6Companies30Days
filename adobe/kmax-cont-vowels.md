# Number of distict Words with k maximum contiguous vowels

[![Problem Link](../assets/gfg.svg)](https://practice.geeksforgeeks.org/problems/7b9d245852bd8caf8a27d6d3961429f0a2b245f1/1/#)

Find the number of unique words consisting of lowercase alphabets only of length N that can be formed with at-most K contiguous vowels. 

### Hint
![image](https://user-images.githubusercontent.com/44930179/150683170-7a2c810c-8971-4f6f-b595-0b63763364f5.png)


### Sample Input
```
384 71
```
### Sample Output
```
233867288
```

### Solution
```cpp
#define mod 1000000007
#define ll long long

class Solution
{
  public:
  
    ll calc(int n,int k,int remVow,vector<vector<ll>> &dp){
        if(n==0) return 1;
        
        if(dp[n][remVow] != -1) return dp[n][remVow];
        
        ll choice1=0,choice2;
        if(remVow>0){
            choice1 = (5 * calc(n-1,k,remVow-1,dp))%mod;
        }
        choice2 = (21 * calc(n-1,k,k,dp))%mod;
        return dp[n][remVow] = (choice1%mod + choice2%mod)%mod;
    }
    
    int kvowelwords(int n, int k) {
        // Write Your Code here
        vector<vector<ll>> dp(n+1,vector<ll> (k+1,-1));
        return (int)calc(n,k,k,dp)%mod;
    }
};
```


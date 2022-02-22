# Count ways to N'th Stair(Order does not matter)

[![Problem Link](../assets/gfg.svg)](https://practice.geeksforgeeks.org/problems/count-ways-to-nth-stairorder-does-not-matter1322/1/#)

There are N stairs, and a person standing at the bottom wants to reach the top. The person can climb either 1 stair or 2 stairs at a time. Count the number of ways, the person can reach the top (order does not matter).

**Note:** Order does not matter means for n=4 {1 2 1},{2 1 1},{1 1 2} are considered same.

### Sample Input

```
4
```

### Sample Output

```
3
```

### Math Solution

```cpp
#define ll long long

class Solution
{
    public:
    ll countWays(int m)
    {
        return m/2 + 1;
    }
};
```

### DP Solution

```cpp
#define ll long long
#define mod 1000000007

class Solution
{
    public:
    ll countWays(int m)
    {
        ll dp[m+1];
        dp[0] = 1;
        dp[1] = 1;
        for(int i=2;i<=m;i++) dp[i] = (dp[i-2] + 1)%mod;
        return dp[m];
    }
};
```

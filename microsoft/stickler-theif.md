# Stickler Thief

[![Problem Link](../assets/gfg.svg)](https://practice.geeksforgeeks.org/problems/stickler-theif-1587115621/1/#)

Stickler the thief wants to loot money from a society having n houses in a single line. He is a weird person and follows a certain rule when looting the houses. According to the rule, he will never loot two consecutive houses. At the same time, he wants to maximize the amount he loots. The thief knows which house has what amount of money but is unable to come up with an optimal looting strategy. He asks for your help to find the maximum money he can get if he strictly follows the rule. Each house has a[i]amount of money present in it.

### Sample Input

```
6
5 5 10 100 10 5
```

### Sample Output

```
110
```

### Solution

```cpp
class Solution
{
    public:
    //Function to find the maximum money the thief can get.
    int FindMaxSum(int arr[], int n)
    {
        // Your code here
        int dp[n+1];
        dp[0] = 0;
        dp[1] = arr[0];
        for(int i=2;i<=n;i++){
            dp[i] = max(dp[i-1],arr[i-1]+dp[i-2]);
        }
        return dp[n];
    }
};
```

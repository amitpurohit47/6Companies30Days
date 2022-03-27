# Pots of Gold Game

[![Problem Link](../assets/gfg.svg)](https://practice.geeksforgeeks.org/problems/pots-of-gold-game/1/#)

Two players X and Y are playing a game in which there are pots of gold arranged in a line, each containing some gold coins. They get alternating turns in which the player can pick a pot from one of the ends of the line. The winner is the player who has a higher number of coins at the end. The objective is to maximize the number of coins collected by X, assuming Y also plays optimally.

Return the maximum coins X could get while playing the game. Initially, X starts the game.

### Sample Input
```
4
8 15 3 7
```

### Sample Output
```
22
```

### Solution
```cpp
class Solution {
public:

    int rec(int i,int j,vector<int>&A, map<pair<int,int>,int> &dp){
        if(i>j){
            return 0;
        }
        if(dp[{i,j}]) return dp[{i,j}];
        int ch1 = A[i] + min(rec(i+2,j,A,dp),rec(i+1,j-1,A,dp));
        int ch2 = A[j] + min(rec(i,j-2,A,dp),rec(i+1,j-1,A,dp));
        return dp[{i,j}] = max(ch1,ch2);
    }

    int maxCoins(vector<int>&A,int n)
    {
	    //Write your code here
	    int ans=0;
	    if(n==1) return A[0];
	    vector<vector<int>> dp(n,vector<int> (n));
	    int i,j,g;
	    for(g=0;g<n;g++){
	        for(i=0,j=g;j<n;i++,j++){
	            if(g==0) dp[i][j] = A[i];
	            else if(g==1) dp[i][j] = max(dp[i+1][j],dp[i][j-1]);
	            else{
	                int ch1 = A[i] + min(dp[i+2][j],dp[i+1][j-1]);
	                int ch2 = A[j] + min(dp[i][j-2],dp[i+1][j-1]);
	                dp[i][j] = max(ch1,ch2);
	            }
	        }
	    }
	    return dp[0][n-1];
    }
};
```

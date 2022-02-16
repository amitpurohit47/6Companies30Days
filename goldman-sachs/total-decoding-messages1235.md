# Total Decoding Messages

[![Problem Link](https://img.shields.io/badge/GeeksforGeeks-298D46?style=for-the-badge&logo=geeksforgeeks&logoColor=white)](https://practice.geeksforgeeks.org/problems/total-decoding-messages1235/1/#)

A top secret message containing letters from A-Z is being encoded to numbers using the following mapping:

```
'A' -> 1
'B' -> 2
 .
 .
'Z' -> 26
```

You are an FBI agent. You have to determine the total number of ways that message can be decoded, as the answer can be large return the answer modulo 109 + 7.

**Note:** An empty digit sequence is considered to have one decoding. It may be assumed that the input contains valid digits from 0 to 9 and If there are leading 0’s, extra trailing 0’s and two or more consecutive 0’s then it is an invalid string.

### Sample Input

```
123
```

### Sample Output

```
3
```

### Solution

```cpp
#define mod 1000000007

class Solution {
	public:
	int CountWays(string str){
	    if(str[0]=='0') return 0;
	    int n=str.length(),i,dp[n+1];
	    dp[1]=1;
	    dp[0]=1;
	    for(i=1;i<n;i++){
	        int temp = (str[i-1]-48)*10 + (str[i]-48);
	        if(temp==0) return 0;
	        if(str[i]=='0' && temp>26) return 0;
	        if(str[i]=='0') dp[i+1] = dp[i-1];
	        else if(str[i-1]=='0') dp[i+1] = dp[i];
	        else if(temp<=26 && temp>0) dp[i+1] = (dp[i]%mod+dp[i-1]%mod)%mod;
	        else dp[i+1] = dp[i];
	    }
	    return dp[n];
	}
};
```

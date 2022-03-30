# Minimum operations to convert array A to B

[![Problem Link](../assets/gfg.svg)](https://practice.geeksforgeeks.org/problems/minimum-insertions-to-make-two-arrays-equal/1/#)

Given two Arrays **A[]** and **B[]** of length **N** and **M** respectively. Find the minimum number of **insertions** and **deletions** on the array A[], required to make both the arrays identical.

**Note:** Array B[] is sorted and all its elements are distinct, operations can be performed at any index not necessarily at end. 

### Sample Input
```
1
5 3
1 2 5 3 1
1 3 5
```

### Sample Output
```
4
```

### Solution
```cpp
class Solution {
  public:
  
    int lis(vector<int> a){
        vector<int> dp;
        int i,j,k=1,n=a.size();
        if(n==0) return 0;
        for(i=0;i<n;i++){
            auto lb = lower_bound(dp.begin(),dp.end(),a[i]);
            if(lb!=dp.end()){
                *lb = min(*lb,a[i]);
            }else{
                dp.push_back(a[i]);
            }
        }
        return dp.size();
    }
  
    int minInsAndDel(int a[], int b[], int n, int m) {
        // code here
        int i,j,k=0,ans=0;
        unordered_set<int> st;
        for(i=0;i<m;i++) st.insert(b[i]);
        vector<int> c;
        for(i=0;i<n;i++){
            if(st.find(a[i])!=st.end()) c.push_back(a[i]);
            else ans++;
        }
        return ans+m-2*lis(c)+c.size();
    }
};
```

### 2D - DP (Memory Limit Exceeded)
```cpp
class Solution {
  public:
    int minInsAndDel(int a[], int b[], int n, int m) {
        // code here
        int i,j,dp[n+1][m+1];
        for(i=0;i<=n;i++) dp[i][0] = 0;
        for(i=0;i<=m;i++) dp[0][i] = 0;
        for(i=1;i<=n;i++){
            for(j=1;j<=m;j++){
                if(a[i-1]==b[j-1]){
                    dp[i][j] = dp[i-1][j-1] + 1;
                }else{
                    dp[i][j] = max(dp[i-1][j],dp[i][j-1]);
                }
            }
        }
        int ans = n - dp[n][m];
        ans+=(m-dp[n][m]);
        return ans;
    }
};
```



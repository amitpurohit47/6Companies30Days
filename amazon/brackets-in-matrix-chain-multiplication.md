# Brackets in Matrix Chain Multiplication

[![Problem Link](../assets/gfg.svg)](https://practice.geeksforgeeks.org/problems/brackets-in-matrix-chain-multiplication1024/1/#)

Given an array p[] of length n used to denote the dimensions of a series of matrices such that dimension of i'th matrix is p[i] \* p[i+1]. There are a total of n-1 matrices. Find the most efficient way to multiply these matrices together.
The problem is not actually to perform the multiplications, but merely to decide in which order to perform the multiplications such that you need to perform minimum number of multiplications. There are many options to multiply a chain of matrices because matrix multiplication is associative i.e. no matter how one parenthesize the product, the result will be the same.

### Sample Input

```
5
1 2 3 4 5
```

### Sample Output

```
(((AB)C)D)
```

### Memoization Solution

```cpp
class Solution{
public:

    int minmuls(vector<pair<int,int>> &v,
                int l,int r,
                map<pair<int,int>,int> &mp,
                map<pair<int,int>,string> &mp1)
    {
        if(l==r) {
            string s="";
            s+=(l+'A');
            mp1[{l,r}] = s;
            return 0;
        }
        if(mp[{l,r}]) return mp[{l,r}];
        int ans=INT_MAX,i;
        for(i=l;i<r;i++){
            int temp = v[l].first * v[r].second * v[i].second +
            minmuls(v,l,i,mp,mp1) +
            minmuls(v,i+1,r,mp,mp1);
            if(temp < ans){
                ans = temp;
                mp[{l,r}] = ans;
                string str = '(' + mp1[{l,i}] + mp1[{i+1,r}] + ')';
                mp1[{l,r}] = str;
            }
        }
        return ans;
    }

    string matrixChainOrder(int p[], int n){
        // code here
        vector<pair<int,int>> v;
        map<pair<int,int>,int> mp;
        map<pair<int,int>,string> mp1;
        v.reserve(n-1);
        for(int i=1;i<n;i++) v.push_back({p[i-1],p[i]});
        int a = minmuls(v,0,n-2,mp,mp1);
        return mp1[{0,n-2}];
    }
};
```

### DP Solution
```cpp
class Solution{
public:
    
    string matrixChainOrder(int p[], int n){
        // code here
        vector<pair<int,int>> v;
        map<pair<int,int>,string> mp1;
        int dp[n-1][n-1],i,j,k,g;
        v.reserve(n-1);
        for(i=1;i<n;i++) v.push_back({p[i-1],p[i]});
        for(i=0;i<n-1;i++) {
            dp[i][i] = 0;
            string s="";
            s+=(i+'A');
            mp1[{i,i}] = s;
        }
        for(g=1;g<n-1;g++){
            for(i=0,j=g;j<n-1;i++,j++){
                dp[i][j] = INT_MAX;
                for(k=i;k<j;k++){
                    int cost = v[i].first * v[k].second * v[j].second +
                                dp[i][k] + dp[k+1][j];
                    if(cost < dp[i][j]){
                        dp[i][j] = cost;
                        mp1[{i,j}] = '(' + mp1[{i,k}] + mp1[{k+1,j}] + ')';
                    }
                }
            }
        }
        return mp1[{0,n-2}];
    }
};
```
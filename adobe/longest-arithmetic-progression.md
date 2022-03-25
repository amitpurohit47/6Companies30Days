# Longest Arithmetic Progression

[![Problem Link](../assets/gfg.svg)](https://practice.geeksforgeeks.org/problems/longest-arithmetic-progression1019/1/#)

Given an array called A[] of sorted integers having no duplicates, find the length of the Longest Arithmetic Progression (LLAP) in it.

### Sample Input
```
6
1 7 10 13 14 19
```

### Sample Output
```
4
```

### Solution
```cpp
class Solution{   
public:
    int lengthOfLongestAP(int arr[], int n) {
        // code here
        int i,j,k,ans=1,len;
        vector<vector<int>> dp(n,vector<int> (4002,0));
        for(i=0;i<n;i++){
            for(j=i+1;j<n;j++){
                int d=arr[j]-arr[i];
                dp[j][d] = max(2,dp[i][d]+1);
                ans=max(ans,dp[j][d]);
            }
        }
        return ans;
    }
};
```
### Naive (TLE)
```cpp
class Solution{   
public:
    int lengthOfLongestAP(int arr[], int n) {
        // code here
        int i,j,k,ans=1,len;
        for(i=0;i<n;i++){
            for(j=i+1;j<n;j++){
                int d=arr[j]-arr[i];
                int lastval=arr[j];
                int len=2;
                for(k=j+1;k<n;k++){
                    if(arr[k]-lastval==d){
                        len++;
                        lastval=arr[k];
                    }
                }
                ans=max(len,ans);
            }
        }
        return ans;
    }
};
```

### Accepted

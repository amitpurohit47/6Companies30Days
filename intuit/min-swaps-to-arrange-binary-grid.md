# Minimum Swaps to Arrange a Binary Grid

[![Problem Link](../assets/lc.svg)](https://leetcode.com/problems/minimum-swaps-to-arrange-a-binary-grid/)

Given an n x n binary grid, in one step you can choose two adjacent rows of the grid and swap them.

A grid is said to be valid if all the cells above the main diagonal are zeros.

Return the minimum number of steps needed to make the grid valid, or -1 if the grid cannot be valid.

The main diagonal of a grid is the diagonal that starts at cell (1, 1) and ends at cell (n, n).

### Example 1
```
Input: grid = [[0,0,1],[1,1,0],[1,0,0]]
Output: 3
```

### Example 2
```
Input: grid = [[0,1,1,0],[0,1,1,0],[0,1,1,0],[0,1,1,0]]
Output: -1
```

### Solution
```cpp
class Solution {
public:
    int minSwaps(vector<vector<int>>& grid) {
        int n = grid.size(),ans=0;
        vector<int> v(n);
        
        for(int i=0;i<n;i++){
            int cnt=0,j=n-1;
            while(j>=0 && grid[i][j] == 0) cnt++,j--;
            v[i] = cnt;
        }
        
        for(auto g:v) cout<<g<<" ";
        
        for(int i=0;i<n;i++){
            int j = i,req=n-i-1;
            while(j<n && v[j]<req) j++;
            if(j==n) return -1;
            ans+=(j-i);
            while(j>i){
                v[j] = v[j-1];
                j--;
            }
        }
        
        return ans;
    }
};
```


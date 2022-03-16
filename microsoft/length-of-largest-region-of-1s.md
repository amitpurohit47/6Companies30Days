# Unit Area of largest region of 1's

[![Problem Link](../assets/gfg.svg)](https://practice.geeksforgeeks.org/problems/length-of-largest-region-of-1s-1587115620/1/#)

Given a grid of dimension nxm containing 0s and 1s. Find the unit area of the largest region of 1s.

Region of 1's is a group of 1's connected 8-directionally (horizontally, vertically, diagonally).

### Sample Input

```
3 4
1 1 1 0
0 0 1 0
0 0 0 1
```

### Sample Output

```
5
```

### Solution

```cpp
class Solution
{
    public:

    int dfs(vector<vector<int>>& grid,vector<vector<int>>& vis,int i,int j,int n,int m){
        vis[i][j] = 1;
        int ans = 1;
        if(i>0 && grid[i-1][j]==1 && !vis[i-1][j]) ans+=dfs(grid,vis,i-1,j,n,m);
        if(i<n-1 && grid[i+1][j]==1 && !vis[i+1][j]) ans+=dfs(grid,vis,i+1,j,n,m);
        if(j>0 && grid[i][j-1]==1 && !vis[i][j-1]) ans+=dfs(grid,vis,i,j-1,n,m);
        if(j<m-1 && grid[i][j+1]==1 && !vis[i][j+1]) ans+=dfs(grid,vis,i,j+1,n,m);
        if(i>0 && j>0 && grid[i-1][j-1]==1 && !vis[i-1][j-1]) ans+=dfs(grid,vis,i-1,j-1,n,m);
        if(i>0 && j<m-1 && grid[i-1][j+1]==1 && !vis[i-1][j+1]) ans+=dfs(grid,vis,i-1,j+1,n,m);
        if(i<n-1 && j>0 && grid[i+1][j-1]==1 && !vis[i+1][j-1]) ans+=dfs(grid,vis,i+1,j-1,n,m);
        if(i<n-1 && j<m-1 && grid[i+1][j+1]==1 && !vis[i+1][j+1]) ans+=dfs(grid,vis,i+1,j+1,n,m);
        return ans;
    }

    //Function to find unit area of the largest region of 1s.
    int findMaxArea(vector<vector<int>>& grid) {
        // Code here
        int n=grid.size(),m=grid[0].size(),i,j,ans=INT_MIN;
        vector<vector<int>> vis(n,vector<int> (m,0));
        for(i=0;i<n;i++){
            for(j=0;j<m;j++){
                if(grid[i][j]==1 && !vis[i][j]){
                    ans=max(ans,dfs(grid,vis,i,j,n,m));
                }
            }
        }
        return ans;
    }
};
```

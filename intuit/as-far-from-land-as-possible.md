# As Far from Land as Possible

[![Problem Link](../assets/lc.svg)](https://leetcode.com/problems/as-far-from-land-as-possible/)

Given an n x n grid containing only values 0 and 1, where 0 represents water and 1 represents land, find a water cell such that its distance to the nearest land cell is maximized, and return the distance. If no land or water exists in the grid, return -1.

The distance used in this problem is the Manhattan distance: the distance between two cells (x0, y0) and (x1, y1) is |x0 - x1| + |y0 - y1|.

### Example 1
```
Input: grid = [[1,0,1],[0,0,0],[1,0,1]]
Output: 2
```

### Example 2
```
Input: grid = [[1,0,0],[0,0,0],[0,0,0]]
Output: 4
```

### Solution
```cpp
class Solution {
public:
    
    int maxDistance(vector<vector<int>>& grid) {
        int n=grid.size(),m=grid[0].size();
        queue<pair<int,int>> q,q1;
        for(int i=0;i<n;i++) {
            for(int j=0;j<m;j++) {
                if(grid[i][j] == 1){
                    q.push({i+1,j});
                    q.push({i,j-1});
                    q.push({i,j+1});
                    q.push({i-1,j});
                }
            }
        }
        int ans=0;
        while(!q.empty()){
            ans++;
            while(!q.empty()){
                int i=q.front().first,j=q.front().second;
                q.pop();
                if(i>=0 && j>=0 && i<grid.size() && j<grid[0].size() && grid[i][j] == 0){
                    grid[i][j] = ans;
                    q1.push({i+1,j});
                    q1.push({i,j-1});
                    q1.push({i,j+1});
                    q1.push({i-1,j});
                }
            }
            swap(q,q1);
        }
        return ans == 1 ? -1 : ans-1;
        
    }
};
```

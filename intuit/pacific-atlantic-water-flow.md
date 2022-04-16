# Pacific Atlantic Water Flow

[![Problem Link](../assets/lc.svg)](https://leetcode.com/problems/pacific-atlantic-water-flow/)

There is an m x n rectangular island that borders both the Pacific Ocean and Atlantic Ocean. The Pacific Ocean touches the island's left and top edges, and the Atlantic Ocean touches the island's right and bottom edges.

The island is partitioned into a grid of square cells. You are given an m x n integer matrix heights where heights[r][c] represents the height above sea level of the cell at coordinate (r, c).

The island receives a lot of rain, and the rain water can flow to neighboring cells directly north, south, east, and west if the neighboring cell's height is less than or equal to the current cell's height. Water can flow from any cell adjacent to an ocean into the ocean.

Return a 2D list of grid coordinates result where result[i] = [ri, ci] denotes that rain water can flow from cell (ri, ci) to both the Pacific and Atlantic oceans.

### Example 1
```
Input: heights = [[1,2,2,3,5],[3,2,3,4,4],[2,4,5,3,1],[6,7,1,4,5],[5,1,1,2,4]]
Output: [[0,4],[1,3],[1,4],[2,2],[3,0],[3,1],[4,0]]
```

### Example 2
```
Input: heights = [[2,1],[1,2]]
Output: [[0,0],[0,1],[1,0],[1,1]]
```

### Solution
```cpp
class Solution {
public:
    
    void dfs(vector<vector<int>>& heights,int i,int j,vector<vector<int>>& ocean,int prev){
        if(i<0 or j<0 or i>=heights.size() or j>=heights[0].size()) return;
        if(heights[i][j] < prev or ocean[i][j]) return;
        ocean[i][j] = 1;
        dfs(heights,i+1,j,ocean,heights[i][j]);
        dfs(heights,i,j+1,ocean,heights[i][j]);
        dfs(heights,i,j-1,ocean,heights[i][j]);
        dfs(heights,i-1,j,ocean,heights[i][j]);
    }
    
    vector<vector<int>> pacificAtlantic(vector<vector<int>>& heights) {
        int i,j,n=heights.size(),m=heights[0].size();
        vector<vector<int>> pac(n,vector<int> (m,0)),atl(n,vector<int> (m,0)),ans;
        
        for(i=0;i<m;i++){
            dfs(heights,0,i,pac,INT_MIN);
            dfs(heights,n-1,i,atl,INT_MIN);
        }
        
        for(i=0;i<n;i++){
            dfs(heights,i,0,pac,INT_MIN);
            dfs(heights,i,m-1,atl,INT_MIN);
        }
        
        for(i=0;i<n;i++){
            for(j=0;j<m;j++){
                if(pac[i][j] && atl[i][j]){
                    vector<int> v(2);
                    v[0] = i;
                    v[1] = j;
                    ans.push_back(v);
                }
            }
        }
        
        return ans;
    }
};
```

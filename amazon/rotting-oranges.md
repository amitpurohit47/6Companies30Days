# Rotting Oranges

[![Problem Link](../assets/lc.svg)](https://leetcode.com/problems/rotting-oranges/)

You are given an `m x n` grid where each cell can have one of three values:

- `0` representing an empty cell,
- `1` representing a fresh orange, or
- `2` representing a rotten orange.

Every minute, any fresh orange that is **4-directionally adjacent** to a rotten orange becomes rotten.

Return the minimum number of minutes that must elapse until no cell has a fresh orange. If this is impossible, return `-1`.

### Example 1

```
Input: grid = [[2,1,1],[1,1,0],[0,1,1]]
Output: 4
```

### Example 2

```
Input: grid = [[2,1,1],[0,1,1],[1,0,1]]
Output: -1
```

### Solution

```cpp
class Solution {
public:
    int cnt;

    Solution(){
        cnt=0;
    }

    void rec(vector<vector<int>>& grid,vector<pair<int,int> > v,int n,int m){
        if(v.size()==0) return;

        int temp = v.size();
        for(int i=0;i<v.size();i++){
            pair<int,int> t = v[i];
            if(t.first+1<n && grid[t.first+1][t.second]) grid[t.first+1][t.second] = 2;
            if(t.first>0 && grid[t.first-1][t.second]) grid[t.first-1][t.second] = 2;
            if(t.second+1<m && grid[t.first][t.second+1]) grid[t.first][t.second+1] = 2;
            if(t.second>0 && grid[t.first][t.second-1]) grid[t.first][t.second-1] = 2;
        }
        v.clear();
        for(int i=0;i<n;i++){
            for(int j=0;j<m;j++){
                if(grid[i][j]==2)  v.push_back({i,j});
            }
        }
        if(v.size() == temp) return;
        cnt++;
        rec(grid,v,n,m);
    }

    int orangesRotting(vector<vector<int>>& grid) {
        int n = grid.size(),m=grid[0].size(),i,j,cnt1=0;
        vector<pair<int,int> > v;
        for(i=0;i<n;i++){
            for(j=0;j<m;j++){
                if(grid[i][j]==1) cnt1++;
                if(grid[i][j]==2){
                    v.push_back({i,j});
                }
            }
        }

        if(v.size()==0 && cnt1) return -1;


        rec(grid,v,n,m);

        for(i=0;i<n;i++){
            for(j=0;j<m;j++){
                if(grid[i][j]==1) return -1;
            }
        }
        return cnt;
    }
};
```

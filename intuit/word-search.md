# Word Search

[![Problem Link](../assets/gfg.svg)](https://practice.geeksforgeeks.org/problems/word-search/1/#)

Given a 2D board of letters and a word. Check if the word exists in the board. The word can be constructed from letters of adjacent cells only. ie - horizontal or vertical neighbors. The same letter cell can not be used more than once.

### Sample Input
```
1
3 4 
a g b c 
q e e l 
g b k s 
geeks
```
### Sample Output
```
1
```

### Solution
```cpp
class Solution {
public:

    bool dfs(vector<vector<char>>& grid, string word,int i,int j,int k){
        if(k==word.length()) return true;
        if(i<0 or
        j<0 or 
        i>=grid.size() or 
        j>=grid[0].size() or 
        grid[i][j]!=word[k]) return false;
        char ch = grid[i][j];
        grid[i][j] = '*';
        bool ans = dfs(grid,word,i-1,j,k+1);
        ans |= dfs(grid,word,i+1,j,k+1);
        ans |= dfs(grid,word,i,j-1,k+1);
        ans |= dfs(grid,word,i,j+1,k+1);
        grid[i][j] = ch;
        return ans;
        
    }

    bool isWordExist(vector<vector<char>>& grid, string word) {
        // Code here
        int n=grid.size(),m=grid[0].size();
        for(int i=0;i<n;i++){
            for(int j=0;j<m;j++){
                if(grid[i][j] == word[0] && dfs(grid,word,i,j,0))  return true;
            }
        }
        return false;
    }
};
```


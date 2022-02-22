# Is Sudoku Valid

[![Problem Link](../assets/gfg.svg)](https://practice.geeksforgeeks.org/problems/is-sudoku-valid4820/1/#)

Given an incomplete Sudoku configuration in terms of a 9x9 2-D square matrix(mat[][]) the task to check if the current configuration is valid or not where a 0 represents an empty block.

**Note:** Current valid configuration does not ensure validity of the final solved sudoku.

Refer to this : https://en.wikipedia.org/wiki/Sudoku

### Sample Input

```
3 0 6 5 0 8 4 0 0
5 2 0 0 0 0 0 0 0
0 8 7 0 0 0 0 3 1
0 0 3 0 1 0 0 8 0
9 0 0 8 6 3 0 0 5
0 5 0 0 9 0 6 0 0
1 3 0 0 0 0 2 5 0
0 0 0 0 0 0 0 7 4
0 0 5 2 0 6 3 0 0
```

### Sample Output

```
1
```

### Solution

```cpp
class Solution{
public:
    int isValid(vector<vector<int>> mat){
        // code here
        int i,j,k,m;
        for(i=0;i<9;i++){
            vector<int> mp(10,0);
            for(j=0;j<9;j++){
                if(mat[i][j]==0) continue;
                else if(mp[mat[i][j]]!=0) return 0;
                else mp[mat[i][j]]++;
            }
        }
        for(i=0;i<9;i++){
            vector<int> mp(10,0);
            for(j=0;j<9;j++){
                if(mat[j][i]==0) continue;
                else if(mp[mat[j][i]]!=0) return 0;
                else mp[mat[j][i]]++;
            }
        }
        for(i=0;i<9;i+=3){
            for(j=0;j<9;j+=3){
                vector<int> mp(10,0);
                for(k=i;k<i+3;k++){
                    for(m=j;m<j+3;m++){
                        if(mat[k][m]==0) continue;
                        else if(mp[mat[k][m]]!=0) return 0;
                        else mp[mat[k][m]]++;
                    }
                }
            }
        }
        return 1;
    }
};
```

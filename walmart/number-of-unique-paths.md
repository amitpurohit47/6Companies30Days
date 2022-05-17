# Number of Unique Paths

[![Problem Link](../assets/gfg.svg)](https://practice.geeksforgeeks.org/problems/number-of-unique-paths5339/1/#)

Given a A X B matrix with your initial position at the top-left cell, find the number of possible unique paths to reach the bottom-right cell of the matrix from the initial position.

**Note:** Possible moves can be either down or right at any point in time, i.e., we can move to matrix[i+1][j] or matrix[i][j+1] from matrix[i][j].

### Sample Input
```
4 4
```

### Sample Output
```
20
```

### Solution
```cpp
class Solution
{
    public:
    //Function to find total number of unique paths.
    int NumberOfPath(int a, int b)
    {
        //code here
        vector<vector<int>> v(a,vector<int> (b));
        v[a-1][b-1] = 1;
        for(int i=a-1;i>=0;i--){
            for(int j=b-1;j>=0;j--){
                if(i<a-1) v[i][j] = v[i+1][j];
                if(j<b-1) v[i][j] += v[i][j+1];
            }
        }
        return v[0][0];
    }
};

```

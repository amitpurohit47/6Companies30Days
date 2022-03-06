# Spirally traversing a matrix

[![Problem Link](../assets/gfg.svg)](https://practice.geeksforgeeks.org/problems/spirally-traversing-a-matrix-1587115621/1/#)

Given a matrix of size r\*c. Traverse the matrix in spiral form.

### Sample Input

```
4 4
1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16
```

### Sample Output

```
1 2 3 4 8 12 16 15 14 13 9 5 6 7 11 10
```

### Solution

```cpp
class Solution
{
    public:
    //Function to return a list of integers denoting spiral traversal of matrix.
    vector<int> spirallyTraverse(vector<vector<int> > matrix, int r, int c)
    {
        // code here
        int top=0,down=r-1,right=c-1,left=0,dir=0;
        vector<int> ans;
        while(top<=down && left<=right){
            if(dir==0){
                for(int i=left;i<=right;i++){
                    ans.push_back(matrix[top][i]);
                }
                top++;
                dir=1;
            }else if(dir==1){
                for(int i=top;i<=down;i++){
                    ans.push_back(matrix[i][right]);
                }
                right--;
                dir=2;
            }else if(dir==2){
                for(int i=right;i>=left;i--){
                    ans.push_back(matrix[down][i]);
                }
                down--;
                dir=3;
            }else{
                for(int i=down;i>=top;i--){
                    ans.push_back(matrix[i][left]);
                }
                left++;
                dir=0;
            }
        }
        return ans;
    }
};
```

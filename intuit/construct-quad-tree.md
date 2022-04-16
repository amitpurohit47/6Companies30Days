# Construct Quad Tree

[![Problem Link](../assets/lc.svg)](https://leetcode.com/problems/construct-quad-tree/)

Given a n * n matrix grid of 0's and 1's only. We want to represent the grid with a Quad-Tree.

Return the root of the Quad-Tree representing the grid.

Notice that you can assign the value of a node to True or False when isLeaf is False, and both are accepted in the answer.

### Example 1
```
Input: grid = [[0,1],[1,0]]
Output: [[0,1],[1,0],[1,1],[1,1],[1,0]]
```

### Solution
```cpp
class Solution {
public:
    Node* construct(vector<vector<int>>& grid) {
        int n = grid.size(),cnt=0,i,j;
        for(auto g:grid) for(auto p:g) if(p) cnt++;
        Node* root;
        if(cnt==n*n){
            root = new Node(1,1);
        }else if(cnt==0){
            root = new Node(0,1);
        }else{
            vector<vector<int>> m(n/2,vector<int> (n/2));
            for(i=0;i<n/2;i++) for(j=0;j<n/2;j++) m[i][j] = grid[i][j];
            Node* tl = construct(m);
            for(i=0;i<n/2;i++) for(j=n/2;j<n;j++) m[i][j-n/2] = grid[i][j];
            Node* tr = construct(m);
            for(i=n/2;i<n;i++) for(j=0;j<n/2;j++) m[i-n/2][j] = grid[i][j];
            Node* bl = construct(m);
            for(i=n/2;i<n;i++) for(j=n/2;j<n;j++) m[i-n/2][j-n/2] = grid[i][j];
            Node* br = construct(m);
            root = new Node(1,0,tl,tr,bl,br);
        }
        return root;
    }
};
```


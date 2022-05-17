# Transform to Sum Tree 

[![Problem Link](../assets/gfg.svg)](https://practice.geeksforgeeks.org/problems/transform-to-sum-tree/1/#)

Given a Binary Tree of size N , where each node can have positive or negative values. Convert this to a tree where each node contains the sum of the left and right sub trees of the original tree. The values of leaf nodes are changed to 0.

### Sample Input
```
         10
      /      \
    -2        6
   /   \     /  \
 8     -4   7    5
```

### Sample Output
```
        20
      /    \
    4        12
   /  \     /  \
 0     0   0    0
```

### Solution
```cpp
class Solution {
  public:
  
    // Convert a given tree to a tree where every node contains sum of values of
    // nodes in left and right subtrees in the original tree
    
    int rec(Node* root){
        if(root==NULL) return 0;
        int a = root->data;
        root->data = rec(root->left);
        root->data += rec(root->right);
        return a+root->data;
    }
    
    void toSumTree(Node *root)
    {
        // Your code here
        int a = rec(root);
    }
};
```


# Count Number of SubTrees having given Sum

[![Problem Link](../assets/gfg.svg)](https://practice.geeksforgeeks.org/problems/count-number-of-subtrees-having-given-sum/1/#)

Given a binary tree and an integer `x`. Your task is to complete the function `countSubtreesWithSumX()` that returns the count of the number of subtress having total node’s data sum equal to the value `x`.

Example: For the tree given below:

```
        5
     /    \
  -10      3
  / \     / \
 9   8  -4   7
```

Subtree with sum 7:

```
   -10
  /   \
 9     8
```

and one node 7.

### Sample Input

```
5 -10 3 9 8 -4 7
7
```

### Sample Output

```
2
```

### Solution

```cpp
int rec(Node* root, int X,int &ans){
    if(root==NULL) return 0;
    int lsum = rec(root->left,X,ans);
	int rsum = rec(root->right,X,ans);
	if(lsum+rsum+root->data==X) ans++;
	return lsum+rsum+root->data;
}

int countSubtreesWithSumX(Node* root, int X)
{
	// Code here
	if(root==NULL) return 0;
	int ans=0;
	rec(root,X,ans);
	return ans;

}
```

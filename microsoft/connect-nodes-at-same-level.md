# Connect Nodes at Same Level

[![Problem Link](../assets/gfg.svg)](https://practice.geeksforgeeks.org/problems/connect-nodes-at-same-level/1/#)

Given a binary tree, connect the nodes that are at same level. You'll be given an addition nextRight pointer for the same.

Initially, all the nextRight pointers point to garbage values. Your function should set these pointers to point next right for each node.

```
       10             10-->NULL
      / \            / \
     3   5    =>    3-->5-->NULL
    / \   \        / \   \
   4   1   2      4-->1-->2-->NULL
```

### Sample Input

```
3 1 2
```

### Sample Output

```
3 1 2
1 3 2
```

### Solution

```cpp
class Solution
{
    public:
    //Function to connect nodes at same level.
    void connect(Node *root)
    {
       // Your Code Here
       if(root==NULL) return;
       queue<vector<Node*>> q;
       vector<Node*> v;
       v.push_back(root);
       q.push(v);
       while(!q.empty()){
           vector<Node*> temp = q.front();
           q.pop();
           int i;
           for(i=0;i<temp.size()-1;i++){
               temp[i]->nextRight = temp[i+1];
           }
           temp[i]->nextRight = NULL;
           vector<Node*> vtemp;
           for(auto g:temp){
               if(g->left!=NULL){
                   vtemp.push_back(g->left);
               }
               if(g->right!=NULL){
                   vtemp.push_back(g->right);
               }
           }
           if(!vtemp.empty()) q.push(vtemp);
       }
    }

};
```

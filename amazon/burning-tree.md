# Burning Tree

[![Problem Link](../assets/gfg.svg)](https://practice.geeksforgeeks.org/problems/burning-tree/1/#)

Given a binary tree and a node called target. Find the minimum time required to burn the complete binary tree if the target is set on fire. It is known that in 1 second all nodes connected to a given node get burned. That is its left child, right child, and parent.

### Sample Input

```
1 2 3 4 5 N 6 N N 7 8 N 9 N N N N N 10
8
```

### Sample Output

```
7
```

### Solution

```cpp
class Solution {
  public:



    int minTime(Node* root, int target)
    {
        // Your code goes here
        map<Node*,Node*> mp;
        map<Node*,int> vis;
        queue<Node*> q;
        q.push(root);
        while(!q.empty()){
            Node* temp = q.front();
            q.pop();
            if(temp->left!=NULL){
                q.push(temp->left);
                mp[temp->left] = temp;
            }
            if(temp->right!=NULL){
                q.push(temp->right);
                mp[temp->right] = temp;
            }
        }

        Node* cur;

        if(root->data==target) cur = root;
        else{
            for(auto g:mp){
                if(g.first->data==target){
                    cur = g.first;
                    break;
                }
            }
        }


        // cout<<cur->data<<"\n";

        queue<vector<Node*>> qp;
        vector<Node*> v1;
        v1.push_back(cur);
        qp.push(v1);
        int ans=0;
        while(!qp.empty()){
            vector<Node*> vtemp = qp.front(),v2;
            qp.pop();
            for(auto g:vtemp){
                if(mp[g]!=NULL && !vis[mp[g]]){
                    vis[mp[g]]++;
                    v2.push_back(mp[g]);
                }
                if(g->left!=NULL && !vis[g->left]){
                    vis[g->left]++;
                    v2.push_back(g->left);
                }
                if(g->right!=NULL && !vis[g->right]){
                    vis[g->right]++;
                    v2.push_back(g->right);
                }
            }
            if(!v2.empty()){
                ans++;
                qp.push(v2);
            }
        }

        return ans;
    }
};
```

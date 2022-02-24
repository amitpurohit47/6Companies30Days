# Serialize and Deserialize a Binary Tree

[![Problem Link](../assets/gfg.svg)](https://practice.geeksforgeeks.org/problems/serialize-and-deserialize-a-binary-tree/1#)

Serialization is to store a tree in an array so that it can be later restored and Deserialization is reading tree back from the array. Now your task is to complete the function serialize which stores the tree into an array A[ ] and deSerialize which deserializes the array to the tree and returns it.

**Note:** The structure of the tree must be maintained. Multiple nodes can have the same data.

### Sample Input

```
1 2 3
```

### Sample Output

```
2 1 3
```

### Solution

```cpp
class Solution
{
    public:
    //Function to serialize a tree and return a list containing nodes of tree.

    void rec1(Node* root,vector<int> &ans){
        if(root==NULL) return;
        queue<Node*> q;
        q.push(root);
        ans.push_back(root->data);
        while(!q.empty()){
            Node* temp = q.front();
            q.pop();
            if(temp->left!=NULL){
                ans.push_back(temp->left->data);
                q.push(temp->left);
            }else{
                ans.push_back(-1);
            }
            if(temp->right!=NULL){
                ans.push_back(temp->right->data);
                q.push(temp->right);
            }else{
                ans.push_back(-1);
            }
        }
    }

    vector<int> serialize(Node *root)
    {
        //Your code here
        vector<int> ans;
        rec1(root,ans);
        return ans;
    }

    //Function to deserialize a list and construct the tree.
    Node * deSerialize(vector<int> &A)
    {
       //Your code here
       if(A.size()==0) return NULL;
       Node* root=new Node(A[0]);
       queue<Node*> q;
       q.push(root);
       int i=2;
       while(!q.empty()){
           Node* temp = q.front();
           q.pop();
           if(A[i-1]!=-1){
               temp->left = new Node(A[i-1]);
               q.push(temp->left);
           }
           if(A[i]!=-1){
               temp->right = new Node(A[i]);
               q.push(temp->right);
           }
           i+=2;
       }
       return root;
    }
};
```

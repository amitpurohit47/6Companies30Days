# Alien Dictionary

[![Problem Link](../assets/gfg.svg)](https://practice.geeksforgeeks.org/problems/alien-dictionary/1/#)

Given a sorted dictionary of an alien language having N words and k starting alphabets of standard dictionary. Find the order of characters in the alien language.

**Note:** Many orders may be possible for a particular test case, thus you may return any valid order and output will be 1 if the order of string returned by the function is correct else 0 denoting incorrect string returned.

### Sample Input
```
6 3
cb ca bb ba ab aa
```
### Sample Output
```
cba
```

### Solution
```cpp
class Solution{
    public:
    
    void dfs(vector<int> adj[],int u,vector<int> &vis,stack<int> &st){
        if(!vis[u]){
            vis[u] = 1;
            for(auto g:adj[u]) if(!vis[g]) dfs(adj,g,vis,st);
            st.push(u);
        }
    }
    
    void topoSort(vector<int> adj[],int V,string &ans){
        vector<int> vis(V,0);
        stack<int> st;
        for(int i=0;i<V;i++) dfs(adj,i,vis,st);
        while(!st.empty()){
            ans+=(st.top()+'a');
            st.pop();
        }
    }
    
    string findOrder(string dict[], int n, int k) {
        //code here
        vector<int> adj[k],vis(k,0);
        for(int i=0;i<n-1;i++){
            string a=dict[i],b=dict[i+1];
            int j=0;
            while(j<a.length() && j<b.length() && a[j]==b[j]) j++;
            if(j<a.length() && j<b.length()) adj[a[j]-'a'].push_back(b[j]-'a');
        }
        string ans="";
        topoSort(adj,k,ans);
        return ans;
    }
};
```


# Bridge edge in a graph

[![Problem Link](../assets/gfg.svg)](https://practice.geeksforgeeks.org/problems/bridge-edge-in-graph/1#)

Given a Graph of V vertices and E edges and another edge(c - d), the task is to find if the given edge is a Bridge. i.e., removing the edge disconnects the graph.

### Sample Input
```
4 4
0 1
1 2
2 3
1 3
1 2
```
### Sample Output
```
0
```

### Solution
```cpp
class Solution
{
	public:
    void dfs(int u,vector<int> &vis,vector<int> adj[]){
        if(!vis[u]){
            vis[u]=1;
            for(auto g:adj[u]) if(!vis[g]) dfs(g,vis,adj);
        }
    }
    int isBridge(int V, vector<int> adj[], int c, int d) 
    {
        if(c==d) return 0;
        adj[c].erase(remove(adj[c].begin(),adj[c].end(),d));
        adj[d].erase(remove(adj[d].begin(),adj[d].end(),c));
        vector<int> vis(V,0);
        dfs(c,vis,adj);
        return !vis[d];
    }
};
```

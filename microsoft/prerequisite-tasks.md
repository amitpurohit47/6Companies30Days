# Prerequisite Tasks

[![Problem Link](../assets/gfg.svg)](https://practice.geeksforgeeks.org/problems/prerequisite-tasks/1/#)

There are a total of N tasks, labeled from 0 to N-1. Some tasks may have prerequisites, for example to do task 0 you have to first complete task 1, which is expressed as a pair: [0, 1]

Given the total number of tasks N and a list of prerequisite pairs P, find if it is possible to finish all tasks.

### Sample Input

```
4
3
1 0
2 1
3 2
```

### Sample Output

```
Yes
```

### Solution

```cpp
class Solution {
public:

    bool rec(int u,vector<vector<int>> &adj,vector<int> &vis,vector<int> &dvis){
        if(!vis[u]){
            vis[u] = 1;
            dvis[u] = 1;
            for(auto g:adj[u]){
                if(dvis[g]){
                    return true;
                }
                if(rec(g,adj,vis,dvis)) return true;
            }
            dvis[u] = 0;
        }
        return false;

    }

	bool isPossible(int n, vector<pair<int, int> >& pre) {
	    // Code here
	    vector<vector<int>> adj(n);
	    for(auto g:pre){
	        adj[g.second].push_back(g.first);
	    }
	    vector<int> vis(n,0),dvis(n,0);

	    for(int i=0;i<n;i++){
	        if(rec(i,adj,vis,dvis)) return false;
	    }

	    return true;
	}
};
```

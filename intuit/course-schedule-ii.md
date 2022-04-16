# Course Schedule II

[![Problem Link](../assets/lc.svg)](https://leetcode.com/problems/course-schedule-ii/)

There are a total of numCourses courses you have to take, labeled from 0 to numCourses - 1. You are given an array prerequisites where prerequisites[i] = [ai, bi] indicates that you must take course bi first if you want to take course ai.

- For example, the pair [0, 1], indicates that to take course 0 you have to first take course 1.

Return the ordering of courses you should take to finish all courses. If there are many valid answers, return any of them. If it is impossible to finish all courses, return an empty array.

### Example 1
```
Input: numCourses = 2, prerequisites = [[1,0]]
Output: [0,1]
```

### Example 2
```
Input: numCourses = 4, prerequisites = [[1,0],[2,0],[3,1],[3,2]]
Output: [0,2,1,3]
```

### Solution
```cpp
class Solution {
public:
    
    bool dfs(vector<vector<int>> &g,int u,vector<int> &vis,vector<int> &dvis){
        if(dvis[u]) return true;
        vis[u] = 1;
        dvis[u] = 1;
        for(auto v:g[u]) if(dfs(g,v,vis,dvis)) return true;
        dvis[u] = 0;
        return false;
    }
    
    void dfs1(vector<vector<int>> &g,int u,vector<int> &vis,stack<int> &st){
        if(!vis[u]){
            vis[u] = 1;
            for(auto v:g[u]) if(!vis[v]) dfs1(g,v,vis,st);
            st.push(u);
        }
    }
    
    bool isCyclic(vector<vector<int>> &g,int n){
        vector<int> vis(n,0),dvis(n,0);
        
        for(int i=0;i<n;i++){
            if(!vis[i] &&  dfs(g,i,vis,dvis)) return true;
        }
        return false;
    }
    
    vector<int> findOrder(int n, vector<vector<int>>& pre) {
        vector<vector<int>> g(n);
        for(auto v:pre) g[v[1]].push_back(v[0]);
        vector<int> ans;
        if(!isCyclic(g,n)){
            
            stack<int> st;
            vector<int> vis(n,0);
            for(int i=0;i<n;i++){
                if(!vis[i]) dfs1(g,i,vis,st);
            }
            while(!st.empty()){
                ans.push_back(st.top());
                st.pop();
            }
        }
        return ans;
    }
};
```


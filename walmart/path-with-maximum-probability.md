# Path with Maximum Probability

[![Problem Link](../assets/lc.svg)](https://leetcode.com/problems/path-with-maximum-probability/)

You are given an undirected weighted graph of n nodes (0-indexed), represented by an edge list where edges[i] = [a, b] is an undirected edge connecting the nodes a and b with a probability of success of traversing that edge succProb[i].

Given two nodes start and end, find the path with the maximum probability of success to go from start to end and return its success probability.

If there is no path from start to end, return 0. Your answer will be accepted if it differs from the correct answer by at most 1e-5.

### Example 1
```
Input: n = 3, edges = [[0,1],[1,2],[0,2]], succProb = [0.5,0.5,0.2], start = 0, end = 2
Output: 0.25000
```

### Example 2
```
Input: n = 3, edges = [[0,1],[1,2],[0,2]], succProb = [0.5,0.5,0.3], start = 0, end = 2
Output: 0.30000
```

### Solution
```cpp
class Solution {
public:
    
    double maxProbability(int n, vector<vector<int>>& edges, vector<double>& succProb, int start, int end) {
        vector<double> dist(n,0);
        dist[start] = 1.0;
        vector<vector<pair<int,double>>> g(n);
        for(int i=0;i<edges.size();i++){
            g[edges[i][0]].push_back({edges[i][1],succProb[i]});
            g[edges[i][1]].push_back({edges[i][0],succProb[i]});
        }
        priority_queue<pair<double,int>> pq;
        pq.push({1.0,start});
        while(!pq.empty()){
            double d = pq.top().first;
            int u = pq.top().second;
            pq.pop();
            for(auto v:g[u]){
                if(d * v.second > dist[v.first]){
                    dist[v.first] = d * v.second;
                    pq.push({dist[v.first],v.first});
                }
            }
        }
        return dist[end];
    }
};
```



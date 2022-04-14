# Number of Boomerangs

[![Problem Link](../assets/lc.svg)](https://leetcode.com/problems/number-of-boomerangs/)

You are given n points in the plane that are all distinct, where points[i] = [xi, yi]. A boomerang is a tuple of points (i, j, k) such that the distance between i and j equals the distance between i and k (the order of the tuple matters).

Return the number of boomerangs.

### Example 1
```
Input: points = [[0,0],[1,0],[2,0]]
Output: 2
```

### Example 2
```
Input: points = [[1,1],[2,2],[3,3]]
Output: 2
```

### Solution
```cpp
class Solution {
public:
    
    int getDist(vector<int> v1,vector<int> v2){
        int x = v1[0] - v2[0];
        int y = v1[1] - v2[1];
        return x*x+y*y;
    }
    
    int numberOfBoomerangs(vector<vector<int>>& points) {
        int ans=0;
        unordered_map<int,int> mp;
        for(int i=0;i<points.size();i++){
            for(int j=0;j<points.size();j++){
                if(i == j) continue;
                mp[getDist(points[i],points[j])]++;
            }
            for(auto g:mp) ans+=(g.second*(g.second-1));
            mp.clear();
        }
        return ans;
    }
};
```

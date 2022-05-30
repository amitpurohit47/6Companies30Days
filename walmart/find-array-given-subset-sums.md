# Find Array Given Subset Sums

[![Problem Link](../assets/lc.svg)](https://leetcode.com/problems/find-array-given-subset-sums/)

You are given an integer n representing the length of an unknown array that you are trying to recover. You are also given an array sums containing the values of all 2n subset sums of the unknown array (in no particular order).

Return the array ans of length n representing the unknown array. If multiple answers exist, return any of them.

An array sub is a subset of an array arr if sub can be obtained from arr by deleting some (possibly zero or all) elements of arr. The sum of the elements in sub is one possible subset sum of arr. The sum of an empty array is considered to be 0.

**Note:** Test cases are generated such that there will always be at least one correct answer.

### Example 1
```
Input: n = 3, sums = [-3,-2,-1,0,0,1,2,3]
Output: [1,2,-3]
```

### Example 2
```
Input: n = 2, sums = [0,0,0,0]
Output: [0,0]
```

### Solution
```cpp
class Solution {
public:
    
    map<int,int> count(vector<int>& sums){
        map<int,int> mp;
        for(auto g:sums) mp[g]++;
        return mp;
    }
    
    vector<int> recoverArray(int n, vector<int>& sums) {
        vector<int> ans;
        sort(sums.begin(),sums.end());
        while(sums.size() > 1){
            vector<int> exc, inc;
            map<int,int> mp = count(sums);
            int dif = sums[sums.size() - 1] - sums[sums.size() - 2];
            for(auto g : sums){
                if(mp[g]){
                    exc.push_back(g);
                    inc.push_back(g + dif);
                    mp[g]--;
                    mp[g + dif]--;
                }
            }
            if(binary_search(exc.begin(),exc.end(),0)){
                swap(sums, exc);
                ans.push_back(dif);
            }else{
                swap(inc, sums);
                ans.push_back(-dif);
            }
        }
        return ans;
    }
};
```


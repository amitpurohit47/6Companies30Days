# Maximum Performance of a Team

[![Problem Link](../assets/lc.svg)](https://leetcode.com/problems/maximum-performance-of-a-team/)

You are given two integers n and k and two integer arrays speed and efficiency both of length n. There are n engineers numbered from 1 to n. speed[i] and efficiency[i] represent the speed and efficiency of the ith engineer respectively.

Choose at most k different engineers out of the n engineers to form a team with the maximum performance.

The performance of a team is the sum of their engineers' speeds multiplied by the minimum efficiency among their engineers.

Return the maximum performance of this team. Since the answer can be a huge number, return it modulo 10<sup>9</sup> + 7.

### Example 1
```
Input: n = 6, speed = [2,10,3,1,5,8], efficiency = [5,4,3,9,7,2], k = 2
Output: 60
```

### Example 2
```
Input: n = 6, speed = [2,10,3,1,5,8], efficiency = [5,4,3,9,7,2], k = 3
Output: 68
```

### Solution
```cpp
#define mod 1000000007
#define ll long long

class Solution {
public:
    int maxPerformance(int n, vector<int>& speed, vector<int>& efficiency, int k) {
        vector<pair<int,int>> v;
        ll sum = 0, ans = 0;
        for(int i = 0; i < n; i++){
            v.push_back( { efficiency[i], speed[i] } );
        }
        sort( v.rbegin(), v.rend() );
        priority_queue<int, vector<int>, greater<int>>  pq;
        for(auto g : v){
            int e = g.first;
            int s = g.second;
            pq.push(s);
            sum += s;
            if( pq.size() > k){
                sum -= pq.top();
                pq.pop();
            }
            ans = max( ans, sum * e );
        }
        return ans % mod;
    }
};
```

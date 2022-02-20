# IPL 2021 - Match Day 2

[![Problem Link](../assets/gfg.svg)](https://practice.geeksforgeeks.org/problems/deee0e8cf9910e7219f663c18d6d640ea0b87f87/1/#)

Due to the rise of covid-19 cases in India, this year BCCI decided to organize knock-out matches in IPL rather than a league.

Today is matchday 2 and it is between the most loved team Chennai Super Kings and the most underrated team - Punjab Kings. Stephen Fleming, the head coach of CSK, analyzing the batting stats of Punjab. He has stats of runs scored by all N players in the previous season and he wants to find the maximum score for each and every contiguous sub-list of size K to strategize for the game.

### Sample Input

```
9 3
1 2 3 1 4 5 2 3 6
```

### Sample Output

```
3 3 4 5 5 5 6
```

### Solution

```cpp
class Solution {
  public:
    vector<int> max_of_subarrays(vector<int> arr, int n, int k) {
        // your code here
        vector<int> ans;
        deque<int> q;
        int i;
        for(i=0;i<k;i++){
            while(!q.empty() && arr[q.back()]<=arr[i]) q.pop_back();
            q.push_back(i);
        }
        for(;i<n;i++){
            ans.push_back(arr[q.front()]);
            while(!q.empty() && q.front()+k<=i) q.pop_front();
            while(!q.empty() && arr[q.back()]<=arr[i]) q.pop_back();
            q.push_back(i);
        }
        ans.push_back(arr[q.front()]);
        return ans;
    }
};
```

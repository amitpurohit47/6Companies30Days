# Winner of an election

[![Problem Link](../assets/gfg.svg)](...problem...)

Given an array of names (consisting of lowercase characters) of candidates in an election. A candidate name in array represents a vote casted to the candidate. Print the name of candidate that received Max votes. If there is tie, print lexicographically smaller name.

### Sample Input
```
13
john johnny jackie johnny john jackie jamie jamie john johnny jamie johnny john
```
### Sample Output
```
john 4
```

### Solution
```cpp
class Solution{
  public:
  
    //Function to return the name of candidate that received maximum votes.
    vector<string> winner(string arr[],int n)
    {
        // Your code here
        // Return the string containing the name and an integer
        // representing the number of votes the winning candidate got
        map<string,int> mp;
        for(int i=0;i<n;i++){
            mp[arr[i]]++;
        }
        int mx=INT_MIN;
        for(auto g:mp){
            mx=max(mx,g.second);
        }
        set<string> st;
        for(auto g:mp){
            if(g.second == mx) st.insert(g.first);
        }
        vector<string> ans(2);
        ans[0] = *(st.begin());
        ans[1] = to_string(mx);
        return ans;
    }
};
```



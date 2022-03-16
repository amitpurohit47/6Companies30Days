# Find All Four Sum Numbers

[![Problem Link](../assets/gfg.svg)](https://practice.geeksforgeeks.org/problems/find-all-four-sum-numbers1732/1#)

Given an array of integers and another number. Find all the unique quadruple from the given array that sums up to the given number.

### Sample Input

```
5 3
0 0 2 1 1
```

### Sample Output

```
0 0 1 2 $
```

### Solution

```cpp
class Solution{
    public:
    // arr[] : int input array of integers
    // k : the quadruple sum required
    vector<vector<int> > fourSum(vector<int> &arr, int s) {
        // Your code goes here
        vector<vector<int>> ans;
        map<vector<int>,int> mp;
        int i,j,k,l,n=arr.size();
        sort(arr.begin(),arr.end());
        for(i=0;i<n-3;i++){
            for(j=i+1;j<n-2;j++){
                k=j+1;
                l=n-1;
                while(k<l){
                    if(arr[i]+arr[j]+arr[k]+arr[l]==s){
                        vector<int> t;
                        t.push_back(arr[i]);
                        t.push_back(arr[j]);
                        t.push_back(arr[k]);
                        t.push_back(arr[l]);
                        if(!mp[t]) ans.push_back(t);
                        mp[t]++;
                    }
                    if(arr[i]+arr[j]+arr[k]+arr[l]<s) k++;
                    else l--;
                }
            }
        }
        return ans;
    }
};
```

# Leaders in an array

[![Problem Link](../assets/gfg.svg)](https://practice.geeksforgeeks.org/problems/leaders-in-an-array-1587115620/1/#)

Given an array A of positive integers. Your task is to find the leaders in the array. An element of array is leader if it is greater than or equal to all the elements to its right side. The rightmost element is always a leader. 

### Sample Input
```
6
16 17 4 3 5 2
```
### Sample Output
```
17 5 2
```

### Solution
```cpp
class Solution{
    //Function to find the leaders in the array.
    public:
    vector<int> leaders(int a[], int n){
        // Code here
        int lead=a[n-1],i;
        vector<int> ans;
        ans.push_back(lead);
        for(i=n-2;i>=0;i--){
            if(a[i]>=lead){
                lead = a[i];
                ans.push_back(lead);
            }
        }
        reverse(ans.begin(),ans.end());
        return ans;
    }
};
```


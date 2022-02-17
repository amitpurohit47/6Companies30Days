# Max 10 numbers in a list having 10M entries (K largest elements)

[![Problem Link](https://img.shields.io/badge/GeeksforGeeks-298D46?style=for-the-badge&logo=geeksforgeeks&logoColor=white)](https://practice.geeksforgeeks.org/problems/k-largest-elements3736/1)

Given an array of N positive integers, print k largest elements from the array.

### Sample Input

```
5 2
12 5 787 1 23
```

### Sample Output

```
787 23
```

### Solution

```cpp
class Solution
{
    public:
    //Function to return k largest elements from an array.
    vector<int> kLargest(int arr[], int n, int k)
    {
        // code here
        priority_queue<int,vector<int>,greater<int>> pq;
        vector<int> ans;
        for(int i=0;i<k;i++) pq.push(arr[i]);
        for(int i=k;i<n;i++) {
            if(arr[i]>=pq.top()){
                pq.pop();
                pq.push(arr[i]);
            }
        }
        while(!pq.empty()){
            ans.push_back(pq.top());
            pq.pop();
        }
        reverse(ans.begin(),ans.end());
        return ans;
    }
};
```


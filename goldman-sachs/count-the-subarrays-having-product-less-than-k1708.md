# Count the subarrays having product less than k

[![Problem Link](https://img.shields.io/badge/GeeksforGeeks-298D46?style=for-the-badge&logo=geeksforgeeks&logoColor=white)](https://practice.geeksforgeeks.org/problems/count-the-subarrays-having-product-less-than-k1708/1/)

Given an array of positive numbers, the task is to find the number of possible contiguous subarrays having product less than a given number k.

### Sample Input
```
4 10
1 2 3 4
```
### Sample Output
```
7
```

### Naive Solution
```cpp
#define ll long long

class Solution{
  public:
    int countSubArrayProductLessThanK(const vector<int>& a, int n, ll k) {
        int ans = 0,i,j;
        for(i=0;i<n;i++){
            ll prod = 1;
            for(j=i;j<n;j++){
                prod*=a[j];
                if(prod<k) ans++;
            }
        }
        return ans;
    }
};

```

### Solution (Sliding Window)
```cpp
#define ll long long

class Solution{
  public:
    int countSubArrayProductLessThanK(const vector<int>& a, int n, ll k) {
        int ans = 0,i=0,j=0;
        ll prod = 1;
        while(j < n){
            prod*=a[j];
            while(prod>=k){
                prod/=a[i];
                i++;
            }
            ans+=(j-i+1);
            j++;
        }
        return ans;
    }
};
```



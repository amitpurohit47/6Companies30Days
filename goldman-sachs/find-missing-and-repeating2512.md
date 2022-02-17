# Find Missing And Repeating

[![Problem Link](https://img.shields.io/badge/GeeksforGeeks-298D46?style=for-the-badge&logo=geeksforgeeks&logoColor=white)](https://practice.geeksforgeeks.org/problems/find-missing-and-repeating2512/1/#)

Given an unsorted array Arr of size N of positive integers. One number 'A' from set {1, 2, …N} is missing and one number 'B' occurs twice in array. Find these two numbers.

### Sample Input

```
2
2 2
```

### Sample Output

```
2 1
```

### Solution

> Time: O(N), Space: O(1)

```cpp
class Solution{
public:
    int *findTwoElement(int *arr, int n) {
        // code here
        int *ans = new int[2];
        int xor1=0,xor2=0,temp,a=(1<<31),i,t1=0,t2=0,j;
        for(i=0;i<n;i++){
            xor1 = xor1^arr[i];
            xor2 = xor2^(i+1);
        }
        temp = xor1 xor xor2;
        for(j=31;j>=0;j--){
            if(a&temp) break;
            a = a >> 1;
        }
        for(i=1;i<=n;i++){
            if((1 << j) & i) t1^=i;
            else t2^=i;
        }
        for(i=0;i<n;i++){
            if((1 << j) & arr[i]) t1^=arr[i];
            else t2^=arr[i];
        }
        for(i=0;i<n;i++){
            if(t1==arr[i]){
                ans[0] = t1;
                ans[1] = t2;
                return ans;
            }
        }
        ans[0] = t2;
        ans[1] = t1;

        return ans;
    }
};
```

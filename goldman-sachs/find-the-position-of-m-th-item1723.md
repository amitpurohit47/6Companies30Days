# Find the position of M-th item

[![Problem Link](https://img.shields.io/badge/GeeksforGeeks-298D46?style=for-the-badge&logo=geeksforgeeks&logoColor=white)](https://practice.geeksforgeeks.org/problems/find-the-position-of-m-th-item1723/1#)

M items are to be delivered in a circle of size N. Find the position where the M-th item will be delivered if we start from a given position K. Note that items are distributed at adjacent positions starting from K.

### Sample Input

```
5 8 2
```

### Sample Output

```
4
```

### Solution

```cpp
class Solution {
  public:
    int findPosition(int n , int m , int k) {
        // code here
        if(m%n==0){
            if(k==1) return n;
            else return k-1;
        }
        m=m%n;
        if(m-(n-k+1)>0) m-=(n-k+1);
        else m=k+m-1;
        return m;
    }
};
```


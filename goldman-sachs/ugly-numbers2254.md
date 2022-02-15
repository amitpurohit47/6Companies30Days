# Ugly Numbers

[![Problem Link](https://img.shields.io/badge/GeeksforGeeks-298D46?style=for-the-badge&logo=geeksforgeeks&logoColor=white)](https://practice.geeksforgeeks.org/problems/ugly-numbers2254/1/)

Ugly numbers are numbers whose only prime factors are 2, 3 or 5. The sequence 1, 2, 3, 4, 5, 6, 8, 9, 10, 12, 15, … shows the first 11 ugly numbers. By convention, 1 is included. Write a program to find Nth Ugly Number.

### Sample Input

```
10
```

### Sample Output

```
12
```

### Solution

```cpp
class Solution{
public:
	// #define ull unsigned long long
	/* Function to get the nth ugly number*/
	ull getNthUglyNo(int n) {
	    // code here
	    ull ans = 1,i,j;
	    set<ull> st;
	    st.insert(1);
	    for(i=1;i<n;i++){
	        ans = *st.begin();
	        st.erase(st.begin());
	        st.insert(ans*2);
	        st.insert(ans*3);
	        st.insert(ans*5);

	    }
	    return *st.begin();
	}
};
```

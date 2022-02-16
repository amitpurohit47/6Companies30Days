# Number following a pattern

[![Problem Link](https://img.shields.io/badge/GeeksforGeeks-298D46?style=for-the-badge&logo=geeksforgeeks&logoColor=white)](https://practice.geeksforgeeks.org/problems/number-following-a-pattern3126/1#)

Given a pattern containing only I's and D's. I for increasing and D for decreasing.

Devise an algorithm to print the minimum number following that pattern.

Digits from 1-9 and digits can't repeat.

### Sample Input

```
D
```

### Sample Output

```
21
```

### Solution

```cpp
class Solution{
public:
    string printMinNumberForPattern(string s){
        // code here
        int cnt=1,i,n=s.length(),k=0;
        string s1="";
        stack<int> st;
        for(i=0;i<n;i++){
            if(s[i]=='D'){
                st.push(cnt);
                cnt++;
            }else{
                st.push(cnt);
                while(!st.empty()){
                    s1+=(st.top()+48);
                    st.pop();
                }
                cnt++;
            }
        }
        st.push(cnt);
        while(!st.empty()){
            s1+=(st.top()+48);
            st.pop();
        }
        return s1;
    }
};
```

### Accepted

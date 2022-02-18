# Decode the string

[![Problem Link](../assets/gfg.svg)](https://practice.geeksforgeeks.org/problems/decode-the-string2444/1#)

An encoded string (s) is given, the task is to decode it. The pattern in which the strings were encoded were as follows

**original string:** abbbababbbababbbab

**encoded string:** 3[a3[b]1[ab]]

### Sample Input

```
3[b2[ca]]
```

### Sample Output

```
bcacabcacabcaca
```

### Solution

```cpp
string decodedString(string s){
        stack<string> st;
        stack<int> st1;
        string res = "";
        int i = 0;
        while(i<s.length()){
            if(s[i]>='0' && s[i]<='9'){
                int cnt = 0;
                while(s[i]>='0' && s[i]<='9'){
                    cnt = cnt*10 + (s[i]-'0');
                    i++;
                }
                st1.push(cnt);
            }else if(s[i]=='['){
                st.push(res);
                res = "";
                i++;
            }else if(s[i]==']'){
                string temp = st.top();
                int a = st1.top();
                st.pop();
                st1.pop();
                while(a--) temp += res;
                res = temp;
                i++;
            }else{
                res += s[i];
                i++;
            }
        }
        return res;
    }
```

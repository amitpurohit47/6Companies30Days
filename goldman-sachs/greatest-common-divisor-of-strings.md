# Greatest Common Divisor of Strings

[![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/greatest-common-divisor-of-strings/)

For two strings s and t, we say "t divides s" if and only if s = t + ... + t (i.e., t is concatenated with itself one or more times).

Given two strings str1 and str2, return the largest string x such that x divides both str1 and str2.

### Example 1

```
Input: str1 = "ABCABC", str2 = "ABC"
Output: "ABC"
```

### Example 2

```
Input: str1 = "LEET", str2 = "CODE"
Output: ""
```

### Solution

```cpp
class Solution {
public:
    string gcdOfStrings(string s1, string s2) {
        if(s1==s2) return s1;
        if(s1.find(s2)!=string::npos && s2.find(s1)!=string::npos) return "";
        if(s1.length()<s2.length()) swap(s1,s2);
        int n1 = s1.length(),i,j;
        for(i=s2.length()-1;i>=0;i--){
            int len = i+1;
            string s="",S=s2.substr(0,len),S1="";
            for(j=0;j<n1/len;j++) s+=S;
            for(j=0;j<s2.length()/len;j++) S1+=S;
            if(s==s1 && S1==s2) return S;
        }
        return "";
    }
};
```

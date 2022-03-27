# Generate Parentheses

[![Problem Link](../assets/gfg.svg)](https://practice.geeksforgeeks.org/problems/generate-all-possible-parentheses/1/#)

Given an integer N representing the number of pairs of parentheses, the task is to generate all combinations of well-formed(balanced) parentheses.

### Sample Input

```
3
```

### Sample Output

```
((()))
(()())
(())()
()(())
()()()
```

### Solution

```cpp
class Solution
{
    public:


    void rec(string s,int o,int c,int n,vector<string> &ans){
        if(o==n && c==n){
            ans.push_back(s);
            return;
        }
        if(o<n){
            rec(s+'(',o+1,c,n,ans);
        }
        if(c<o){
            rec(s+')',o,c+1,n,ans);
        }

    }

    vector<string> AllParenthesis(int n)
    {
        // Your code goes here
        vector<string> ans;
        string s="";
        rec(s,0,0,n,ans);
        return ans;
    }
};
```

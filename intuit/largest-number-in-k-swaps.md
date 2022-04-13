# Largest number in K swaps

[![Problem Link](../assets/gfg.svg)](https://practice.geeksforgeeks.org/problems/largest-number-in-k-swaps-1587115620/1#)

Given a number K and string str of digits denoting a positive integer, build the largest number possible by performing swap operations on the digits of str at most K times.

### Sample Input
```
1
3
6278134320804246
```

### Sample Output
```
8876634320204241
```

### Solution
```cpp
class Solution
{
    public:
    void rec(string str, int k, int a, string &ans){
        ans=max(ans,str);
        if(k==0) return;
        for(int i=a;i<str.length()-1;i++){
            for(int j=i+1;j<str.length();j++){
                if(str[j]>str[i]){
                    swap(str[i],str[j]);
                    rec(str,k-1,i+1,ans);
                    swap(str[i],str[j]);
                }
            }
        }
    }
    
    string findMaximumNum(string str, int k)
    {
       // code here.
       string ans=str;
       rec(str,k,0,ans);
       return ans;
    }
};
```


# Largest number in K swaps

[![Problem Link](../assets/gfg.svg)](https://practice.geeksforgeeks.org/problems/largest-number-in-k-swaps-1587115620/1#)

Given a number K and string str of digits denoting a positive integer, build the largest number possible by performing swap operations on the digits of str at most K times.

### Sample Input
```
4
1234567
```

### Sample Output
```
7654321
```

### Solution
```cpp
class Solution
{
    public:
    
    string ans = "";
    //Function to find the largest number after k swaps.
    
    void rec(string s, int i, int k){
        ans = max(ans, s);
        if(k == 0 or i == s.length()) return;
        for(int j = i + 1; j < s.length(); j++){
            if( s[i] < s[j] ){
                swap(s[i], s[j]);
                rec(s, i + 1, k - 1);
                swap(s[i], s[j]);
            }
        }
        rec(s, i + 1, k);
    }
    
    string findMaximumNum(string str, int k)
    {
       rec(str, 0, k);
       return ans;
    }
};
```


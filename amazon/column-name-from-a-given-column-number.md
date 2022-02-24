# Column name from a given column number

[![Problem Link](../assets/gfg.svg)](https://practice.geeksforgeeks.org/problems/column-name-from-a-given-column-number4244/1/#)

Given a positive integer, return its corresponding column title as appear in an Excel sheet.

Excel columns has a pattern like A, B, C, … ,Z, AA, AB, AC,…. ,AZ, BA, BB, … ZZ, AAA, AAB ….. etc. In other words, column 1 is named as “A”, column 2 as “B”, column 27 as “AA” and so on.

### Sample Input

```
28
```

### Sample Output

```
AB
```

### Solution

```cpp
#define ll long long

class Solution{
    public:
    string colName (ll n)
    {
        // your code here
        string s="";
        int flag = 0;
        while(n!=0){
            if((n-flag)%26==0){
                s='Z'+s;
                flag = 1;
            }else{
                char a = ((n-flag)%26 - 1) + 'A';
                s = a + s;
                flag=0;
            }
            n/=26;
        }
        return s;
    }
};
```

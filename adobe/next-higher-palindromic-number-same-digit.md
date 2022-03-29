# Next higher palindromic number using the same set of digits

Given a palindromic number N in the form of string. The task is to find the smallest palindromic number greater than N using the same set of digits as in N.

[![Problem Link](../assets/gfg.svg)](https://practice.geeksforgeeks.org/problems/next-higher-palindromic-number-using-the-same-set-of-digits5859/1/#)

### Sample Input
```
1
454121454
```

### Sample Output
```
514424415
```

### Solution
```cpp
class Solution{
  public:
    string nextPalin(string s) { 
        //complete the function here
        int n = s.length(),j=-1;
        string ans,s1="";
        for(int i=0;i<n/2;i++) s1+=s[i];
        char c = 'a';
        for(int i=n/2-1;i>=1;i--){
            if(s1[i]>s1[i-1]){
                for(int k=i;k<n/2;k++){
                    if(s1[k]<c && s1[k]>s1[i-1]){
                        j=k;
                        c=s1[k];
                    }
                }
                swap(s1[i-1],s1[j]);
                sort(s1.begin()+i,s1.end());
                break;
            }
        }
        if(j==-1){
            return "-1";
        }
        ans=s1;
        if(n%2) ans+=s[n/2];
        reverse(s1.begin(),s1.end());
        ans+=s1;
        return ans;
    }
};
```

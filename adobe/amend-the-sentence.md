# Amend The Sentence

[![Problem Link](../assets/gfg.svg)](https://practice.geeksforgeeks.org/problems/amend-the-sentence3235/1#)

Given a string which is basically a sentence without spaces between words. However the first letter of every word is in uppercase. You need to print this sentence after following amendments:

1. Put a single space between these words
2. Convert the uppercase letters to lowercase.

**Note:** The first character of the string can be both uppercase/lowercase.


### Sample Input
```
BruceWayneIsBatman
```
### Sample Output
```
bruce wayne is batman
```

### Solution
```cpp
class Solution{
    public:
    string amendSentence (string s)
    {
        // your code here
        int i;
        string ans="";
        for(i=0;i<s.length();i++){
            if(s[i]>='A' && s[i]<='Z'){
                ans+=' ';
                ans+=(s[i]+32);
            }else{
                ans+=s[i];
            }
        }
        if(ans[0]==' '){
            ans.erase(0,1);
        }
        return ans;
    }
};
```



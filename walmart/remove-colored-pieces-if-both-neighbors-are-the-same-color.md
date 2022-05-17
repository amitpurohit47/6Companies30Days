# Remove Colored Pieces if Both Neighbors are the Same Color

[![Problem Link](../assets/lc.svg)](link)

### Example 1
```
Input: colors = "AAABABB"
Output: true
```

### Example 2
```
Input: colors = "AA"
Output: false
```

### Solution
```cpp
class Solution {
public:
    bool winnerOfGame(string colors) {
        if(colors.length()<3) return false;
        int a=0,b=0,n=colors.length();
        for(int i=0;i<n-2;i++){
            int t=1;
            for(int j=i;j<i+3;j++){
                if(colors[j]!='A'){
                    t=0;
                    break;
                }
            }
            if(t) a++;
        }
        for(int i=0;i<n-2;i++){
            int t=1;
            for(int j=i;j<i+3;j++){
                if(colors[j]!='B'){
                    t=0;
                    break;
                }
            }
            if(t) b++;
        }
        if(a>b) return true;
        return false;
    }
};
```

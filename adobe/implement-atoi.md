# Implement Atoi

[![Problem Link](../assets/gfg.svg)](https://practice.geeksforgeeks.org/problems/implement-atoi/1/#)

Your task  is to implement the function atoi. The function takes a string(str) as argument and converts it to an integer and returns it.

**Note:** You are not allowed to use inbuilt function.

### Sample Input
```
123
```

### Sample Output
```
123
```

### Solution
```cpp
class Solution{
  public:
    /*You are required to complete this method */
    int atoi(string str) {
        //Your code here
        int sum=0,i;
        for(i=0;i<str.length();i++){
            if(i==0 && str[i]=='-') continue;
            if(str[i]>'9' || str[i]<'0') return -1;
            sum = sum*10 + (str[i]-'0');
        }
        return str[0]=='-' ? -sum : sum;
    }
};
```


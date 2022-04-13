# Find the missing no in string

[![Problem Link](../assets/gfg.svg)](https://practice.geeksforgeeks.org/problems/find-the-missing-no-in-string/1/#)

Given a string consisting of some numbers, not separated by any separator. The numbers are positive integers and the sequence increases by one at each number except the missing number. The task is to complete the function missingNumber which return's the missing number. The numbers will have no more than six digits. Print -1 if input sequence is not valid.

**Note:** Its is guaranteed that if the string is valid, then it is sure that atleast one number would be missing from the string.

### Sample Input
```
1
1234567810111213141516
```

### Sample Output
```
9
```

### Solution
```cpp
int missingNumber(const string& str)
{
    // Code here
    string s="";
    for(int i=0;i<str.length() && i<6;i++){
        s+=str[i];
        size_t j=i+1;
        string s1 = s,s2;
        int f=0;
        while(j<str.length()){
            s1 = to_string(stoi(s1)+1);
            size_t k = str.find(s1,j);
            if(k!=string::npos && j==k){
                j=j+s1.length();
            }else{
                if(f) break;
                f=1;
                s2=s1;
            }
        }
        if(f && j>=str.length()) return stoi(s2);
    }
    return -1;
}
```


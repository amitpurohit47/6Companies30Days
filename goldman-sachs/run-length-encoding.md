# Run Length Encoding

[![Problem Link](https://img.shields.io/badge/GeeksforGeeks-298D46?style=for-the-badge&logo=geeksforgeeks&logoColor=white)](https://practice.geeksforgeeks.org/problems/run-length-encoding/1/)

Given a string, Your task is to complete the function `encode` that returns the run length encoded string for the given string.
eg if the input string is “wwwwaaadexxxxxx”, then the function should return “w4a3d1e1x6″.
You are required to complete the function `encode` that takes only one argument the string which is to be encoded and returns the encoded string.

### Sample Input

```
aaaabbbccc
```

### Sample Output

```
a4b3c3
```

### Solution

```cpp
string encode(string src)
{
  //Your code here
  int n=src.length(),i,cnt=1;
  string s="";
  s+=src[0];
  for(i=1;i<n;i++){
      if(src[i]!=src[i-1]){
          char a = cnt+48;
          s+=a;
          cnt=1;
          s+=src[i];
      }else cnt++;
  }
  char a = cnt+48;
  s+=a;
  return s;
}

```

### Accepted

# Generate Binary Numbers

[![Problem Link](../assets/gfg.svg)](https://practice.geeksforgeeks.org/problems/generate-binary-numbers-1587115620/1/#)

Given a number N. The task is to generate and print all binary numbers with decimal values from 1 to N.

### Sample Input

```
2
```

### Sample Output

```
1
10
```

### Solution

```cpp
vector<string> generate(int n)
{
	// Your code here
	vector<string> v;
	int i,m;
	for(i=1;i<=n;i++){
	    m=i;
	    string s="";
	    while(m){
	        if(m%2) s='1'+s;
	        else s='0'+s;
	        m/=2;
	    }
	    v.push_back(s);
	}
	return v;
}
```

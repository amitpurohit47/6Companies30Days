# Power Of Numbers 

[![Problem Link](../assets/gfg.svg)](https://practice.geeksforgeeks.org/problems/power-of-numbers-1587115620/1/#)

Given a number and its reverse. Find that number raised to the power of its own reverse.

**Note:** As answers can be very large, print the result modulo 109 + 7.

### Sample Input
```
2
```
### Sample Output
```
4
```

### Solution
```cpp
#define MOD 1000000007

class Solution{
    public:
    //You need to complete this fucntion
    
    long long power(int n,int r)
    {
       //Your code here
       long long ans;
        if(r==0) ans = 1;
        else if(r%2){
            ans = ((n%MOD) * (power(n,r-1)%MOD))%MOD;
        }else{
            ans = power(n,r/2)%MOD;
            ans = ((ans%MOD) * (ans%MOD))%MOD;
        }
        return ans;
    }

};
```

# Divide Two Integers

[![Problem Link](../assets/lc.svg)](https://leetcode.com/problems/divide-two-integers/)

Given two integers dividend and divisor, divide two integers without using multiplication, division, and mod operator.

The integer division should truncate toward zero, which means losing its fractional part. For example, 8.345 would be truncated to 8, and -2.7335 would be truncated to -2.

Return the quotient after dividing dividend by divisor.

**Note:** Assume we are dealing with an environment that could only store integers within the 32-bit signed integer range: [−231, 231 − 1]. For this problem, if the quotient is strictly greater than 231 - 1, then return 231 - 1, and if the quotient is strictly less than -231, then return -231.

### Example 1
```
Input: dividend = 10, divisor = 3
Output: 3
```

### Example 2
```
Input: dividend = 7, divisor = -3
Output: -2
```

### Solution
```cpp
class Solution {
public:
    int divide(int dividend, int divisor) {
        if(dividend == INT_MIN && divisor == 1) return INT_MIN;
        if(dividend == INT_MIN && divisor == -1) return INT_MAX;
        if(dividend == INT_MIN){
            if(divisor < 0){
                return divide(dividend - divisor, divisor) + 1;
            }else{
                return divide(dividend + divisor, divisor) - 1;
            }
        }
        if(divisor == INT_MIN) return 0;
        bool sign = (dividend < 0 && divisor < 0) || (dividend > 0 && divisor > 0);
        dividend = abs(dividend);
        divisor = abs(divisor);
        int ans = 0;
        while(dividend >= divisor){
            int x;
            for(x = 0; x < 31 && (divisor << x) > 0; x++){
                if((divisor << x) > dividend) break;
            }
            x--;
            ans += (1 << x);
            dividend -= (divisor << x);
        }
        return sign ? ans : -ans;
    }
};
```


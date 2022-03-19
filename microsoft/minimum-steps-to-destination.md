# Minimum steps to destination

[![Problem Link](../assets/gfg.svg)](https://practice.geeksforgeeks.org/problems/minimum-number-of-steps-to-reach-a-given-number5234/1/#)

Given an infinite number line. You start at 0 and can go either to the left or to the right. The condition is that in the ith move, youmust take i steps. Given a destination D , find the minimum number of steps required to reach that destination.

### Sample Input
```
5
```
### Sample Output
```
5
```

### Naive Solution
```cpp
class Solution{
public:

    int steps(int v,int i,int D){
        if(abs(v)>D) return INT_MAX;
        if(v==D) return i;
        int pos = steps(v+i+1,i+1,D);
        int neg = steps(v-i-1,i+1,D);
        return min(pos,neg);
    }

    int minSteps(int D){
        // code here
        if(D==0) return 0;
        
        return steps(0,0,D);
    }
};
```

### Solution
```cpp

class Solution{
public:

    int minSteps(int D){
        // code here
        int step=0,sum=0;
        while(sum<D || (sum-D)%2!=0){
            step++;
            sum+=step;
        }
        return step;
    }
};
```


# Nuts and Bolts Problem

[![Problem Link](../assets/gfg.svg)](https://practice.geeksforgeeks.org/problems/nuts-and-bolts-problem0431/1#)

Given a set of N nuts of different sizes and N bolts of different sizes. There is a one-one mapping between nuts and bolts. Match nuts and bolts efficiently.

Comparison of a nut to another nut or a bolt to another bolt is not allowed. It means nut can only be compared with bolt and bolt can only be compared with nut to see which one is bigger/smaller.

The elements should follow the following order ! # $ % & \* @ ^ ~ .

### Sample Input

```
5
@ % $ # ^
% @ # $ ^
```

### Sample Output

```
# $ % @ ^
# $ % @ ^
```

### Solution

```cpp
class Solution{
public:

    int partition(char nuts[],int l,int r,int pivot){
        int i,j=l;
        for(i=l;i<r;i++){
            if(nuts[i]<pivot){
                swap(nuts[j],nuts[i]);
                j++;
            }else if(nuts[i]==pivot){
                swap(nuts[i],nuts[r]);
                i--;
            }
        }
        swap(nuts[j],nuts[r]);
        return j;
    }

    void quicksort(char nuts[], char bolts[],int l,int r){
        if(l<r){
            int pivot = partition(nuts,l,r,bolts[r]);
            partition(bolts,l,r,nuts[pivot]);
            quicksort(nuts,bolts,l,pivot-1);
            quicksort(nuts,bolts,pivot+1,r);
        }
    }

	void matchPairs(char nuts[], char bolts[], int n) {
	    // code here
	    quicksort(nuts,bolts,0,n-1);
	}
};
```

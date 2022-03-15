# Stock span problem

[![Problem Link](../assets/gfg.svg)](https://practice.geeksforgeeks.org/problems/stock-span-problem-1587115621/1#)

The stock span problem is a financial problem where we have a series of n daily price quotes for a stock and we need to calculate the span of stock’s price for all n days.

The span Si of the stock’s price on a given day i is defined as the maximum number of consecutive days just before the given day, for which the price of the stock on the current day is less than or equal to its price on the given day.

For example, if an array of 7 days prices is given as {100, 80, 60, 70, 60, 75, 85}, then the span values for corresponding 7 days are {1, 1, 1, 2, 1, 4, 6}.

### Sample Input

```
7
100 80 60 70 60 75 85
```

### Sample Output

```
1 1 1 2 1 4 6
```

### Solution

```cpp
class Solution
{
    public:
    //Function to calculate the span of stockâ€™s price for all n days.
    vector <int> calculateSpan(int price[], int n)
    {
       // Your code here
       vector<int> ans(n);
       ans[0] = 1;
       stack<int> st;
       st.push(0);
       for(int i=1;i<n;i++){
           while(!st.empty() && price[st.top()]<=price[i]) st.pop();
           if(st.empty()) ans[i] = i+1;
           else ans[i] = i-st.top();
           st.push(i);
       }
       return ans;
    }
};
```

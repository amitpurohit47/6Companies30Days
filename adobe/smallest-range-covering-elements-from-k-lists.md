# Smallest range in K lists

[![Problem Link](../assets/gfg.svg)](https://practice.geeksforgeeks.org/problems/find-smallest-range-containing-elements-from-k-lists/1/#)

Given K sorted lists of integers, KSortedArray[] of size N each. The task is to find the smallest range that includes at least one element from each of the K lists. If more than one such range's are found, return the first such range found.

### Sample Input
```
5 3
1 3 5 7 9
0 2 4 6 8
2 3 5 7 11
```

### Sample Output
```
1 2
```

### Solution
```cpp
class Node{
    public:
    int val,r,c;
};

bool Compare(Node a, Node b){
    return a.val > b.val;
}

class Solution{
    public:
    
    pair<int,int> findSmallestRange(int arr[][N], int n, int k)
    {
        //code here
        vector<vector<Node>> v(k,vector<Node> (n));
        int i,j,mx=INT_MIN;
        for(i=0;i<k;i++){
            for(j=0;j<n;j++){
                v[i][j].val = arr[i][j];
                v[i][j].r = i;
                v[i][j].c = j;
            }
        }
        priority_queue<Node,vector<Node>,bool (*)(Node, Node)> pq(Compare);
        pair<int,int> ans;
        ans = {0,100000};
        for(i=0;i<k;i++){
            pq.push(v[i][0]);
            mx=max(mx,arr[i][0]);
        }
        while(1){
            Node t = pq.top();
            pq.pop();
            if(ans.second-ans.first>mx-t.val){
                ans = {t.val,mx};
            }
            if(t.c==n-1) break;
            mx = max(mx,arr[t.r][t.c+1]);
            pq.push(v[t.r][t.c+1]);
        }
        return ans;
    }
};
```


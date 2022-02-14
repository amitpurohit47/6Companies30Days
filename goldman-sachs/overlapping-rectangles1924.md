# Overlapping Rectangles

[![Problem Link](https://img.shields.io/badge/GeeksforGeeks-298D46?style=for-the-badge&logo=geeksforgeeks&logoColor=white)](https://practice.geeksforgeeks.org/problems/overlapping-rectangles1924/1/)

Given two rectangles, find if the given two rectangles overlap or not. A rectangle is denoted by providing the x and y coordinates of two points: the left top corner and the right bottom corner of the rectangle. Two rectangles sharing a side are considered overlapping. (L1 and R1 are the extreme points of the first rectangle and L2 and R2 are the extreme points of the second rectangle).

**Note:** It may be assumed that the rectangles are parallel to the coordinate axis.
![image](https://user-images.githubusercontent.com/44930179/147873497-c32af86c-7ec6-414a-9b17-96cd24f0485d.png)

### Sample Input
```
0 10 10 0 5 5 15 0
```
### Sample Output
```
1
```

### Solution
```cpp
class Solution {
  public:
    int doOverlap(int l1[], int r1[], int l2[], int r2[]) {
        // code here
        if(r1[0]<l2[0] || l1[0]>r2[0] || r2[1]>l1[1] || r1[1]>l2[1]) return 0;
        return 1;
    }
};
```


# Generate Random Point in a Circle

[![Problem Link](../assets/lc.svg)](https://leetcode.com/problems/generate-random-point-in-a-circle/)

Given the radius and the position of the center of a circle, implement the function randPoint which generates a uniform random point inside the circle.

Implement the Solution class:

- `Solution(double radius, double x_center, double y_center)` initializes the object with the radius of the circle radius and the position of the center (x_center, y_center).
- `randPoint()` returns a random point inside the circle. A point on the circumference of the circle is considered to be in the circle. The answer is returned as an array [x, y].
 

### Example
```
Input
["Solution", "randPoint", "randPoint", "randPoint"]
[[1.0, 0.0, 0.0], [], [], []]
Output
[null, [-0.02493, -0.38077], [0.82314, 0.38945], [0.36572, 0.17248]]
```

### Solution
```cpp
class Solution {
public:
    double rad,xc,yc;
    Solution(double radius, double x_center, double y_center) {
        rad = radius;
        xc = x_center;
        yc = y_center;
        srand(time(0));
    }
    
    double random(){
        double res = (1.0 * rand()) / RAND_MAX;
        return res;
    }
    
    vector<double> randPoint() {
        double len = rad * sqrt(random()), deg = 2 * M_PI * random();
        double x = xc + len * cos(deg);
        double y = yc + len * sin(deg);
        vector<double> v = {x,y};
        return v;
    }
};
```


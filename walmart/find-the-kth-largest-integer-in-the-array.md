# Find the Kth Largest Integer in the Array

[![Problem Link](../assets/lc.svg)](https://leetcode.com/problems/find-the-kth-largest-integer-in-the-array/)

You are given an array of strings nums and an integer k. Each string in nums represents an integer without leading zeros.

Return the string that represents the kth largest integer in nums.

**Note:** Duplicate numbers should be counted distinctly. For example, if nums is ["1","2","2"], "2" is the first largest integer, "2" is the second-largest integer, and "1" is the third-largest integer.

### Example 1
```
Input: nums = ["3","6","7","10"], k = 4
Output: "3"
```

### Example 2
```
Input: nums = ["2","21","12","1"], k = 3
Output: "2"
```

### Solution
```cpp
class Solution {
public:
    
    class Compare{
      public:
      bool operator()(string a,string b){
          if(b.length()>a.length()) return false;
          if(a.length()>b.length()) return true;
          return b < a;
      }
    };
    
    bool checkGreater(string a,string b){
        if(b.length()>a.length()) return true;
        if(b.length()<a.length()) return false;
        return b > a;
    }
    
    string kthLargestNumber(vector<string>& nums, int k) {
        priority_queue<string,vector<string>,Compare> pq;
        for(int i=0;i<k && i<nums.size();i++) pq.push(nums[i]);
        for(int i=k;i<nums.size();i++){
            if(checkGreater(pq.top(),nums[i])){
                pq.pop();
                pq.push(nums[i]);
            }
        }
        return pq.top();
    }
};
```


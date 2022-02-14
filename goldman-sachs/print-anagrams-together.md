# Print Anagrams Together

[![Problem Link](https://img.shields.io/badge/GeeksforGeeks-298D46?style=for-the-badge&logo=geeksforgeeks&logoColor=white)](https://practice.geeksforgeeks.org/problems/print-anagrams-together/1/#)

Given an array of strings, return all groups of strings that are anagrams. The groups must be created in order of their appearance in the original array. Look at the sample case for clarification.

### Sample Input
```
5
act god cat dog tac
```
### Sample Output
```
act cat tac 
god dog 
```

### Solution
```cpp
class Solution{
  public:
    vector<vector<string> > Anagrams(vector<string>& string_list) {

        unordered_map<string, vector<string>> ans_map;

        for(string &s: string_list) {
            string copy = s;
            sort(copy.begin(), copy.end());
            ans_map[copy].push_back(s);
        }

        vector< vector<string> > ans;

        for(auto v: ans_map) {
            ans.push_back(v.second);
        }

        return ans;
    }
};
```

### Accepted
[![image](https://user-images.githubusercontent.com/44930179/147873107-6516b2e3-9430-4e8d-af6c-a95529eef3b2.png)](https://practice.geeksforgeeks.org/viewSol.php?subId=6f74ea054ab4a7ac183196a83fd4b454&pid=701966&user=jhasuraj)

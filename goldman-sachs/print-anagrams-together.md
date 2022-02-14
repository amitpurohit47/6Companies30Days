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
        //code here
        vector<string> v;
        for(auto g:string_list){
            string s = g;
            sort(s.begin(),s.end());
            v.push_back(s);
        }
        map<string,int> mp;
        map<string,bool> mp1;
        int k=0,n=string_list.size();
        for(auto g:v){
            if(!mp1[g]){
                mp1[g] = true;
                mp[g] = k++;
            }
        }
        vector<vector<string> > ans(mp.size());
        for(int i=0;i<n;i++){
            ans[mp[v[i]]].push_back(string_list[i]);
        }
        return ans;
    }
};
```

# First non-repeating character in a stream

[![Problem Link](../assets/gfg.svg)](https://practice.geeksforgeeks.org/problems/first-non-repeating-character-in-a-stream1216/1#)

Given an input stream of A of n characters consisting only of lower case alphabets. The task is to find the first non repeating character, each time a character is inserted to the stream. If there is no such character then append '#' to the answer.

### Sample Input

```
zzabbc
```

### Sample Output

```
z#aaaa
```

### Solution

```cpp
class Solution {
	public:
		string FirstNonRepeating(string A){
		    // Code here
		    map<char,int> mp;
		    list<int> li;
		    string s="";
		    int i=1,n=A.length();
		    li.push_back(A[0]);
		    mp[A[0]]++;
		    s+=A[0];
		    while(i<n){
		        if(!mp[A[i]]) {
		            li.push_back(A[i]);
		            mp[A[i]]++;
		        }else{
		            for(auto itr = li.begin();itr!=li.end();++itr){
		                if(*itr == A[i]) {
		                    li.erase(itr);
		                    break;
		                }
		            }
		        }
		        if(li.empty()) s+='#';
		        else s+=li.front();
		        i++;
		    }
		    return s;
		}

};
```

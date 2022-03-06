# Possible Words From Phone Digits

[![Problem Link](../assets/gfg.svg)](https://practice.geeksforgeeks.org/problems/possible-words-from-phone-digits-1587115620/1/#)

Given a keypad as shown in the diagram, and an N digit number which is represented by array `a[]`, the task is to list all words which are possible by pressing these numbers.

![image](https://user-images.githubusercontent.com/44930179/149143296-16eeecc9-79d2-40ac-b091-8206ecd5e5d1.png)

### Sample Input

```
3
2 3 4
```

### Sample Output

```
adg adh adi aeg aeh aei afg afh afi bdg bdh bdi beg beh bei bfg bfh bfi cdg cdh cdi ceg ceh cei cfg cfh cfi
```

### Solution

```cpp
class Solution
{
    public:
    //Function to find list of all words possible by pressing given numbers.

    void rec(int* arr,int n,string s,int i,vector<string> &ans,map<int,string> mp){
        if(i==n){
            ans.push_back(s);
            return;
        }
        for(int j=0;j<mp[arr[i]].length();j++){
            rec(arr,n,s+mp[arr[i]][j],i+1,ans,mp);
        }
    }

    vector<string> possibleWords(int arr[], int n)
    {
        //Your code here
        vector<string> ans;
        int cnt=0,t=2;
        map<int,string> mp;
        string s="";
        for(char a='a';a<='r';a++){
            if(cnt==3){
                cnt=1;
                mp[t] = s;
                t++;
                s="";
                s+=a;
            }else{
                s+=a;
                cnt++;
            }
        }
        s+='s';
        mp[t] = s;
        cnt=0;
        s="";
        t++;
        for(char a='t';a<='y';a++){
            if(cnt==3){
                cnt=1;
                mp[t] = s;
                t++;
                s="";
                s+=a;
            }else{
                s+=a;
                cnt++;
            }
        }
        s+='z';
        mp[t] = s;
        rec(arr,n,"",0,ans,mp);
        return ans;
    }
};
```

# Phone directory

[![Problem Link](https://img.shields.io/badge/GeeksforGeeks-298D46?style=for-the-badge&logo=geeksforgeeks&logoColor=white)](https://practice.geeksforgeeks.org/problems/phone-directory4628/1/#)

Given a list of contacts contact[] of length n where each contact is a string which exist in a phone directory and a query string s. The task is to implement a search query for the phone directory. Run a search query for each prefix p of the query string s (i.e. from index 1 to |s|) that prints all the distinct contacts which have the same prefix as p in lexicographical increasing order. Please refer the explanation part for better understanding.

**Note:** If there is no match between query and contacts, print "0".

### Sample Input

```
3
geeikistest geeksforgeeks geeksfortest
geeips
```

### Sample Output

```
geeikistest geeksforgeeks geeksfortest
geeikistest geeksforgeeks geeksfortest
geeikistest geeksforgeeks geeksfortest
geeikistest
0
0
```

### Solution

```cpp
struct TrieNode
{
    unordered_map<char,TrieNode*> child;
    bool isLast;

    TrieNode()
    {
        for (char i = 'a'; i <= 'z'; i++)
            child[i] = NULL;

        isLast = false;
    }
};

class Trie{
    TrieNode* root;
    public:
    Trie(){
        root = new TrieNode();
    }
    void insert(string s)
    {
        int len = s.length();

        TrieNode *itr = root;
        for (int i = 0; i < len; i++)
        {
            TrieNode *nextNode = itr->child[s[i]];
            if (nextNode == NULL)
            {
                nextNode = new TrieNode();

                itr->child[s[i]] = nextNode;
            }

            itr = nextNode;

            if (i == len - 1)
                itr->isLast = true;
        }
    }

    void displayContactsUtil(TrieNode *curNode, string prefix,vector<string> &v)
    {
        if (curNode->isLast)
            v.push_back(prefix);

        for (char i = 'a'; i <= 'z'; i++)
        {
            TrieNode *nextNode = curNode->child[i];
            if (nextNode != NULL)
                displayContactsUtil(nextNode, prefix + (char)i,v);
        }
    }

    void displayContacts(string str,vector<vector<string>> &ans)
    {
        TrieNode *prevNode = root;

        string prefix = "";
        int len = str.length();

        int i;
        for (i=0; i<len; i++)
        {
            prefix += (char)str[i];

            char lastChar = prefix[i];

            TrieNode *curNode = prevNode->child[lastChar];
            vector<string> temp;
            if (curNode == NULL)
            {
                string s1="";
                s1+='0';
                temp.push_back(s1);
                ans.push_back(temp);
                i++;
                break;
            }


            displayContactsUtil(curNode, prefix,temp);
            ans.push_back(temp);
            prevNode = curNode;
        }
        for (; i<len; i++)
        {
            vector<string> temp;
            string s1="";
            s1+='0';
            temp.push_back(s1);
            ans.push_back(temp);
        }
    }
};

class Solution{
public:
    vector<vector<string>> displayContacts(int n, string contact[], string s)
    {
        // code here
        Trie t;
        for(int i=0;i<n;i++) t.insert(contact[i]);
        vector<vector<string>> ans;
        t.displayContacts(s,ans);
        return ans;
    }
};

```

Given two strings s and t, return true if t is an anagram of s, and false otherwise.

Example 1:
```
Input: s = "anagram", t = "nagaram"
Output: true
```
Example 2:
```
Input: s = "rat", t = "car"
Output: false
```

Constraints:
- `1 <= s.length, t.length <= 5 * 10**4`
- `s` and `t` consist of lowercase English letters.
### Your Solution:
```
class Solution 
{
public:
    bool isAnagram(string s, string t) 
    {
        std::unordered_map<char, int> dict1;
        std::unordered_map<char, int> dict2;
        if(s.length() != t.length())
            return false;
        for(int i=0;i<s.length();i++)
        {     
            dict1[s[i]]++;    
        }
        for(int i=0;i<t.length();i++)
        {  
            dict2[t[i]]++;
        }
        if(dict1==dict2)
        {
            return true;
        }
        else
        {
            return false;
        }       
    }
};
```
### Learning
- How to define and use a map (which is an equivalent to dictionary in python).
- To add new keys and alter their values. Out of curiosity I even learnt how to delete a key using `.erase(key)`.
- Operations that we can perform using two maps.

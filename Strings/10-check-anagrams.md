# Valid Anagram

Practice [Link](https://leetcode.com/problems/valid-anagram/description/)


Given two strings s and t, return true if t is an anagram of s, and false otherwise

An `anagram` is a word or phrase formed by rearranging the letters of a different word or phrase, using all the original letters exactly once.

## Brute Force

```cpp
bool isAnagram(string s, string t) {
    if (s.size() != t.size()) return false;
    
    sort(s.begin(), s.end());
    sort(t.begin(), t.end());
    
    return s == t;
}
```
> Time Complexity: O(nlogn), (where n-> size of strings)
>
> Space Complexity: O(1)

## Hash Map

```cpp
class Solution {
public:
    bool isAnagram(string s, string t) {
        if(s.size() != t.size())
            return false;

        

        unordered_map<char,int> hashMap;
        for(auto c: s)
            hashMap[c] += 1;

        int sz = hashMap.size();
        for(auto c: t)
        {
            hashMap[c]--;
            if(hashMap[c]==0)
                sz--;
        }
        return sz==0;
    }
};
```

> Time Complexity: O(n), (where n-> size of strings)
>
> Space Complexity: O(1)


# Selecting Approach

| Approach               | Time Complexity | Space Complexity | Use Case                                 |
| ---------------------- | --------------- | ---------------- | ---------------------------------------- |
| **Brute Force (Sort)** | O(n log n)      | O(1)             | Small inputs, quick prototyping          |
| **Hash Map Count**     | O(n)            | O(1)             | Handles all characters (Unicode-safe)    |

# Longest Common Prefix


## Horizontal Scanning

```cpp
class Solution {
public:
    string longestCommonPrefix(vector<string>& strs) {
        if(strs.empty())
            return "";
        
        string prefix = strs[0];
        for(int i=1;i<strs.size();i++)
        {
            while(strs[i].find(prefix) != 0){
                prefix = prefix.substr(0, prefix.size()-1);
                if(prefix.empty())
                    return "";
            }
        }
        return prefix;

        
    }
};
```

> Time Complexity: O(S) (S = sum of all chars in all strings)	
>
> Space Complexity: O(1) or O(m) (for prefix)


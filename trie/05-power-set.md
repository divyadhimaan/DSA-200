# Power Set

Practice [Link](https://www.geeksforgeeks.org/problems/power-set4302/1#)

Given a string s of length n, find all the possible non-empty subsequences of the string s in lexicographically-sorted order.

## Brute Force Approach

Create every possible subsequence using recursion and backtracking.

```cpp
class Solution{
	public:
	
	    void solve(string s, vector<string> &res, int idx, string f)
	    {
	        if(idx >= s.length())
	        {
	            if(f.length() > 0)
	                res.push_back(f);
	            return;
	        }
	        
	        f += s[idx];
	        
	        solve(s, res, idx+1, f);
	        f.pop_back();
	        solve(s,res,idx+1, f);
	            
	    }
	
		vector<string> AllPossibleStrings(string s){
		    vector<string> res;
		    
		    solve(s, res,0, "");
		    sort(res.begin(), res.end());
		    return res;
		}
};
```

> Time Complexity: `O(2^n) + O(2^n log(2^n))` -> Sorting
>
> Space Complexity: `O(2^n) + O(n)` ->  recursion stack
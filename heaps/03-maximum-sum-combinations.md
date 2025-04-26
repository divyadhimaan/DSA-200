# Maximum Sum Combination

Practice [Link](https://www.geeksforgeeks.org/problems/maximum-sum-combination/0)

Given two integer array A and B of size N each.
A sum combination is made by adding one element from array A and another element of array B.
Return the maximum K valid sum combinations from all the possible sum combinations.

Note : Output array must be sorted in non-increasing order.


## Naive Approach

```cpp
class Solution {
  public:
    vector<int> maxCombinations(int N, int K, vector<int> &A, vector<int> &B) {
        vector<int> sums;
        
        for(int i=0;i<N;i++)
        {
            for(int j=0;j<N;j++)
            {
                sums.push_back(A[i]+B[j]);
            }
        }
        
        sort(sums.begin(), sums.end(), greater<int>());
        
        vector<int> res(sums.begin(), sums.begin()+K);
        return res;
    }
};
```


> Time Complexity: O(n^2)
>
> Space Complexity: O(n)

## Better Approach


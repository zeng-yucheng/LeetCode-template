# [Count Number of Teams](https://leetcode.com/problems/count-number-of-teams/)

## Method 1: Enumerate Middle Point

```python
class Solution:
    def numTeams(self, rating: List[int]) -> int:
        ans = 0
        for j in range(1, len(rating) - 1):
            ans += sum([1 for i in rating[:j] if i < rating[j]]) *\
                   sum([1 for k in rating[j + 1:] if k > rating[j]])
            ans += sum([1 for i in rating[:j] if i > rating[j]]) *\
                   sum([1 for k in rating[j + 1:] if k < rating[j]])
        return ans
```

Complexity:
* Time: *O(N<sup>2</sup>)*
* Memory: *O(1)*
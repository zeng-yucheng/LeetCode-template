# [Count Number of Teams](https://leetcode.com/problems/count-number-of-teams/)

## Method 1: Enumerate Middle Point

**Code:**

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

**Complexity:**
* Time: *O(N<sup>2</sup>)*
* Memory: *O(1)*


## Method 2: Binary Indexed Tree

**Code:**

```python
class Solution:
    def numTeams(self, rating: List[int]) -> int:
        
        def lowbit(x):
            return x & -x

        def add(i, delta):
            while i < len(tree):
                tree[i] += delta
                i += lowbit(i)

        def query(i):
            presum = 0
            while i > 0:
                presum += tree[i]
                i -= lowbit(i)
            return presum
        
        uniques = sorted(rating)
        rank_map = {v: i + 1 for i,v in enumerate(uniques)}
        
        tree = [0 for i in range(len(rank_map) + 1)]


        ans = 0
        n = len(rating)
        add(rank_map[rating[0]], 1)
        for i in range(1, n-1):
            rank = rank_map[rating[i]]
            s1 = query(rank-1)
            l1 = i - s1
            s2 = rank - 1 - s1
            l2 = n - 1 - i - s2
            
            add(rank, 1)

            ans += s1 * l2 + s2 * l1
        
        return ans
```

**Complexity:**
* Time: *O(N \* logN)*
* Memory: *O(N)*
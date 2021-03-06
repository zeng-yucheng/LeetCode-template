# Binary Search Template

## Steps:

1. Special cases
2. Define two pointers
3. Iteration
    1. Mid
    2. Target
    3. Re-calculate pointers 
4. Return

## Template:

```python
def func():
    # deal with special cases
    if ... : return ...

    # define left and right pointer
    left, right = ..., ...

    # define iteration coditions
    while left <= right:
        # calculate mid
        mid = (left + right) // 2

        # achieve target
        if ...: return ...

        # re-calculate left and right
        if mid ...: right = mid - 1
        else: left = mid + 1
    
    # return target
    return ...
```

## Problems:
[69. Sqrt(x)](https://leetcode.com/problems/sqrtx/)

## Note:
* `left <= right`
* `target = mid or mid - 1`

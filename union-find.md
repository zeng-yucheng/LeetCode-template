# Union Find Template

## Steps:

1. Initiate `parents[]` and `size[]` array
2. Define `root()` function
    1. Calculate `father`
    2. Compress path
3. Define `union()` function
    1. Compare `size`
    2. Update `size`
    3. Union
4. Main function

## Template:

```python
def func():
    # Initiate
    parents, size = ..., ...
    
    # define root()
    def root(x):
        father = parents[x]
        if father != x:
            father = root(father)
        parents[x] = father
        return father
    
    # define union()
    def union(a, b):
        a, b = root(a), root(b)
        if a != b:
            # compare size
            if size(a) >= size(b):
                parents[b] = a
                if size(a) == size(b):
                    size(a) += 1
            else:
                parents[a] = b
    
    # define main()
```

## Problems:

## Note:
* `size(a) >= size(b)`
* `size(a) += 1`
* `if father != x: father = root(father)`
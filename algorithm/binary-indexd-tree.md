# Binary Indexed Tree

## **Introduction:**

A Fenwick tree or binary indexed tree is a data structure that can efficiently update elements and calculate prefix sums in a table of numbers.

Assuming 1-indexed below.

### 1. `lowbit()` function

Mathematical expression:
$$lowbit(x) = x \wedge (-x)$$

Example table:

<div align="center">

Integer | Binary | lowbit
:--- | :--- | :---
1 | 000**1** | 1
2 | 00**10** | 2
3 | 001**1** | 1
4 | 0**100** | 4
5 | 010**1** | 1
6 | 01**10** | 2
7 | 011**1** | 1
8 | **1000** | 8
</div>


### 2. Structure

Element in orange block can manege the elements in grey block
<div align="center"><img src="../pic/binary-indexed-tree-1.png" width="75%"></div>

Let $A$ be the original array:
$$
tree[i]=\sum_{j=i-lowbit(i)+1}^{i}{A[j]}
$$

### 3. Presum

Let $presum[i]$ be the presum of $i$:
$$
presum[i]=\sum_{i; i=i-lowbit(i) \wedge i>0}{tree[i]}
$$


### 4. Element Update

Need only *O(logN)* time.

## **Code**
`lowbit()` function:
```python
def lowbit(x):
    return x & -x
```

Calculate presum:
```python
def presum(i):
    sum = 0
    while i > 0:
        sum += tree[i]
        i -= lowbit(i)
    return sum
```

Update tree:
```python
def add(i, delta):
    while i <= len(A):
        tree[i] += delta
        i += lowbit(i)
```
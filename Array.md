# Linear Search

Linear Search is a searching algorithm that checks elements one by one until the target element is found.

---

## Algorithm

1. Start from index `0`
2. Compare each element with target element `x`
3. If element matches, return index
4. If element is not found, return `-1`

---

## Pseudo Code

```text
START

FOR each element in array

    IF element == target
        RETURN index

END FOR

RETURN -1

END
```

---

## Example

### Input
```text
arr = [10, 12, 14, 13, 20]
x = 13
```

### Output
```text
3
```

---

## Time Complexity

| Case | Complexity |
|------|------------|
| Best Case | O(1) |
| Worst Case | O(n) |

---

## Space Complexity

```text
O(1)
```

---

## Advantages
- Simple to understand
- Works on unsorted arrays

---

## Disadvantages
- Slow for large datasets

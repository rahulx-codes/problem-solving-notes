# Array

<div align="center">

## 📘 Concepts

</div>

---

<div align="center">

## 💻 Questions

</div>

- Search an Element (Linear Search)
- Largest in Array

---

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

---

# Find Largest Element in Array

## Concept

- Largest element means maximum value in array
- Assume first element as largest
- Traverse array from index `1`
- If current element is greater than `max`
  → update `max`

---

## Pseudo Code

```text
Take max = first element

Loop from index 1 to n-1
    If current element > max
        Update max

Return max
```

---

## ⏱ Complexity

| Type | Complexity |
|---|---|
| Time | O(n) |
| Space | O(1) |

---

## ⚠ Important Point

Array should not be empty because:

```java
arr[0]
```

can cause error.


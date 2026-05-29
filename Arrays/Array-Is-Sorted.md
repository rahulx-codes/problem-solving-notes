# Check if Array is Sorted

## Problem Statement

Given an array `arr[]`, check whether it is sorted in **non-decreasing order**.

Return:

- `true` → if the array is sorted.
- `false` → otherwise.

---

## Examples

### Example 1

```text
Input:
arr = [10, 20, 30, 40, 50]

Output:
true

Explanation:
Every element is greater than or equal to the previous element.
```

### Example 2

```text
Input:
arr = [90, 80, 100, 70, 40, 30]

Output:
false

Explanation:
80 < 90, so the array is not sorted.
```

---

## Constraints

```text
1 <= arr.size <= 10^6
-10^9 <= arr[i] <= 10^9
```

---

# Understanding Non-Decreasing Order

An array is said to be in **non-decreasing order** if:

```text
arr[i] >= arr[i - 1]
```

for every valid index `i`.

### Valid Examples

```text
[10, 20, 30, 40]
[5, 5, 5, 5]
[1, 2, 2, 3, 4]
```

### Invalid Examples

```text
[10, 20, 15, 30]
[5, 4, 3, 2]
```

---

# Approach 1: Brute Force

## Idea

1. Create a copy of the array.
2. Sort the copied array.
3. Compare original and sorted arrays.
4. If both are identical, the array was already sorted.

---

## Algorithm

```text
1. Create a copy of the array.
2. Sort the copied array.
3. Traverse both arrays.
4. If any element differs:
      return false
5. Otherwise:
      return true
```

---

## Dry Run

### Input

```text
[10, 20, 30, 40]
```

### Copy

```text
[10, 20, 30, 40]
```

### After Sorting

```text
[10, 20, 30, 40]
```

Both arrays are same.

```text
Answer = true
```

---

## Java Code

```java
import java.util.Arrays;

class Solution {

    public boolean isSorted(int[] arr) {

        int[] temp = arr.clone();

        Arrays.sort(temp);

        for (int i = 0; i < arr.length; i++) {
            if (arr[i] != temp[i]) {
                return false;
            }
        }

        return true;
    }
}
```

---

## Complexity Analysis

### Time Complexity

```text
Sorting = O(N log N)

Comparison = O(N)

Total = O(N log N)
```

### Space Complexity

```text
O(N)
```

because of copied array.

---

# Approach 2: Optimal Approach

## Observation

For a sorted array:

```text
arr[i] >= arr[i - 1]
```

must be true for every index.

If even one element violates this condition:

```text
arr[i] < arr[i - 1]
```

the array is not sorted.

---

## Algorithm

```text
1. Start from index 1.
2. Compare current element with previous element.
3. If current < previous:
       return false
4. Continue until end.
5. If no violation found:
       return true
```

---

## Dry Run 1

### Input

```text
[10, 20, 30, 40, 50]
```

| i | Previous | Current | Check |
|---|----------|----------|--------|
| 1 | 10 | 20 | ✓ |
| 2 | 20 | 30 | ✓ |
| 3 | 30 | 40 | ✓ |
| 4 | 40 | 50 | ✓ |

No violation found.

```text
Answer = true
```

---

## Dry Run 2

### Input

```text
[10, 20, 15, 30]
```

| i | Previous | Current | Check |
|---|----------|----------|--------|
| 1 | 10 | 20 | ✓ |
| 2 | 20 | 15 | ✗ |

Since:

```text
15 < 20
```

Return:

```text
false
```

---

## Java Code

```java
class Solution {

    public boolean isSorted(int[] arr) {

        for (int i = 1; i < arr.length; i++) {

            if (arr[i] < arr[i - 1]) {
                return false;
            }

        }

        return true;
    }
}
```

---

# Why Start From Index 1?

Index `0` has no previous element.

```text
Index : 0 1 2 3
Array : 5 8 9 10
```

Comparisons are:

```text
arr[1] vs arr[0]
arr[2] vs arr[1]
arr[3] vs arr[2]
```

Therefore traversal starts from index `1`.

---

# Edge Cases

## Single Element

```text
[10]
```

Output:

```text
true
```

Reason:

A single element is always sorted.

---

## Duplicate Elements

```text
[5, 5, 5, 5]
```

Output:

```text
true
```

Reason:

Equal elements are allowed in non-decreasing order.

---

## Negative Numbers

```text
[-10, -5, 0, 4]
```

Output:

```text
true
```

---

## Descending Order

```text
[50, 40, 30, 20]
```

Output:

```text
false
```

---

## Empty Array

```text
[]
```

Output:

```text
true
```

---

# Pseudocode

```text
function isSorted(arr)

    for i = 1 to arr.length - 1

        if arr[i] < arr[i - 1]
            return false

    return true
```

---

# Complexity Comparison

| Approach | Time Complexity | Space Complexity |
|-----------|----------------|------------------|
| Brute Force | O(N log N) | O(N) |
| Optimal | O(N) | O(1) |

---

# Interview Explanation

"I traverse the array once from left to right. For every element, I compare it with its previous element. If I find any element smaller than its previous element, I immediately return false because the sorted order is violated. If the entire traversal completes without finding any violation, I return true. This solution runs in O(N) time and O(1) extra space."

---

# Key Takeaways

Non-decreasing means:

```text
arr[i] >= arr[i - 1]
```

Equal elements are allowed.

Best solution uses one traversal.

Time Complexity:

```text
O(N)
```

Space Complexity:

```text
O(1)
```

This is the most optimal solution for checking whether an array is sorted.

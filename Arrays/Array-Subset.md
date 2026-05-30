# Array Subset

## Problem Statement

Given two arrays `a[]` and `b[]`, determine whether `b[]` is a subset of `a[]`.

A subset means every element present in `b[]` must also be present in `a[]`.

Return:

```text
true  -> if b[] is a subset of a[]
false -> otherwise
```

---

# Examples

## Example 1

Input:

```text
a[] = [11, 7, 1, 13, 21, 3, 7, 3]
b[] = [11, 3, 7, 1, 7]
```

Output:

```text
true
```

Explanation:

```text
All elements of b[] are present in a[].
```

---

## Example 2

Input:

```text
a[] = [1, 2, 3, 4, 4, 5, 6]
b[] = [1, 2, 4]
```

Output:

```text
true
```

Explanation:

```text
All elements of b[] are present in a[].
```

---

## Example 3

Input:

```text
a[] = [10, 5, 2, 23, 19]
b[] = [19, 5, 3]
```

Output:

```text
false
```

Explanation:

```text
3 is not present in a[].
Therefore b[] is not a subset of a[].
```

---

# Understanding the Concept

Think of:

```text
a[] = Parent Array
b[] = Child Array
```

To be a subset:

```text
Every element of b[]
must exist in a[]
```

If even one element is missing:

```text
Not a Subset
```

---

# Approach 1 : Brute Force

## Idea

For every element in `b[]`, search the entire `a[]`.

If any element is not found:

```text
Return false
```

Otherwise:

```text
Return true
```

---

# Pseudo Code

```text
function isSubset(a[], b[])

    for each element x in b[]

        found = false

        for each element y in a[]

            if x == y
                found = true
                break

        if found == false
            return false

    return true
```

---

# Dry Run

```text
a[] = [1,2,3,4,5]
b[] = [2,4]
```

Check:

```text
2 -> Found
4 -> Found
```

All elements found.

```text
Return true
```

---

# Java Code

```java
class Solution {
    public boolean isSubset(int a[], int b[]) {

        for (int i = 0; i < b.length; i++) {

            boolean found = false;

            for (int j = 0; j < a.length; j++) {

                if (b[i] == a[j]) {
                    found = true;
                    break;
                }
            }

            if (!found) {
                return false;
            }
        }

        return true;
    }
}
```

---

# Complexity Analysis

```text
Time Complexity  : O(n × m)

Space Complexity : O(1)
```

Where:

```text
n = size of a[]
m = size of b[]
```

---

# Approach 2 : Sorting + Two Pointers (Best Without HashSet)

## Why This Approach?

Brute Force repeatedly searches the array.

Instead:

```text
1. Sort both arrays
2. Use two pointers
3. Match elements efficiently
```

This significantly improves performance.

---

# Core Idea

Before Sorting:

```text
a[] = [11,7,1,13,21,3,7,3]
b[] = [11,3,7,1,7]
```

After Sorting:

```text
a[] = [1,3,3,7,7,11,13,21]
b[] = [1,3,7,7,11]
```

Use:

```text
i -> a[]
j -> b[]
```

---

# Pointer Rules

## Case 1

```text
a[i] == b[j]
```

Element matched.

Move both pointers.

```text
i++
j++
```

---

## Case 2

```text
a[i] < b[j]
```

Current element in `a[]` is smaller.

Move `i`.

```text
i++
```

---

## Case 3

```text
a[i] > b[j]
```

Required element is missing.

```text
Return false
```

---

# Pseudo Code

```text
function isSubset(a[], b[])

    sort(a)
    sort(b)

    i = 0
    j = 0

    while i < length(a) AND j < length(b)

        if a[i] < b[j]
            i++

        else if a[i] == b[j]
            i++
            j++

        else
            return false

    if j == length(b)
        return true

    return false
```

---

# Visual Dry Run

```text
a[] = [1,3,3,7,7,11,13,21]
b[] = [1,3,7,7,11]
```

Initial:

```text
i = 0
j = 0
```

Step 1

```text
1 == 1
```

Move both.

```text
i = 1
j = 1
```

---

Step 2

```text
3 == 3
```

Move both.

```text
i = 2
j = 2
```

---

Step 3

```text
3 < 7
```

Move `i`.

```text
i = 3
```

---

Step 4

```text
7 == 7
```

Move both.

```text
i = 4
j = 3
```

---

Step 5

```text
7 == 7
```

Move both.

```text
i = 5
j = 4
```

---

Step 6

```text
11 == 11
```

Move both.

```text
i = 6
j = 5
```

Since:

```text
j == b.length
```

All elements matched.

```text
Return true
```

---

# Optimized Java Solution

```java
import java.util.Arrays;

class Solution {
    public boolean isSubset(int a[], int b[]) {

        Arrays.sort(a);
        Arrays.sort(b);

        int i = 0;
        int j = 0;

        while (i < a.length && j < b.length) {

            if (a[i] < b[j]) {
                i++;
            }
            else if (a[i] == b[j]) {
                i++;
                j++;
            }
            else {
                return false;
            }
        }

        return j == b.length;
    }
}
```

---

# Complexity Analysis

## Sorting

```text
O(n log n) + O(m log m)
```

## Traversal

```text
O(n + m)
```

## Total

```text
Time Complexity:

O(n log n + m log m)
```

```text
Space Complexity:

O(1)
```

(ignoring internal sorting space)

---

# Comparison Table

| Approach               | Time Complexity      | Space Complexity |
| ---------------------- | -------------------- | ---------------- |
| Brute Force            | O(n × m)             | O(1)             |
| Sorting + Two Pointers | O(n log n + m log m) | O(1)             |

---

# Interview Explanation

If HashSet is not allowed:

```text
1. Sort both arrays.
2. Use two pointers.
3. Compare elements one by one.
4. Match every element of b[].
5. If all elements are matched,
   b[] is a subset of a[].
```

---

# Key Observation

```text
Subset means:

Every element of b[]
must exist in a[]
```

---

# Memory Trick

```text
Sort -> Compare -> Match
```

```text
a[i] < b[j]
Move i

a[i] == b[j]
Move both

a[i] > b[j]
Not a Subset
```

---

# Final Takeaway

```text
HashSet Allowed?
    Use HashSet

HashSet Not Allowed?
    Use Sorting + Two Pointers
```

```text
Best Without HashSet:

Time Complexity  : O(n log n + m log m)

Space Complexity : O(1)
```

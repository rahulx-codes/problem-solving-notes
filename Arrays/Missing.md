# Missing Number in Array

## Problem Statement

You are given an array `arr[]` of size `n - 1` that contains distinct integers in the range from `1 to n`.

The array represents a permutation of numbers from `1 to n` with one number missing.

Your task is to find the missing number.

---

# Example

## Example 1

### Input

```text
arr = [1, 2, 3, 5]
```

### Output

```text
4
```

### Explanation

All numbers from `1 to 5` are present except `4`.

---

## Example 2

### Input

```text
arr = [8, 2, 4, 5, 3, 7, 1]
```

### Output

```text
6
```

### Explanation

All numbers from `1 to 8` are present except `6`.

---

# Concept

Instead of checking every number manually, we use a mathematical formula.

The sum of numbers from `1 to n` is:

```text
n × (n + 1) / 2
```

We calculate:

- Expected sum of numbers from `1 to n`
- Actual sum of array elements

Then subtract both sums.

```text
Missing Number = Total Sum - Array Sum
```

---

# Step-by-Step Dry Run

## Input

```text
arr = [1, 2, 3, 5]
```

---

## Step 1: Find n

Array size is `4`.

So:

```text
n = arr.length + 1
n = 5
```

---

## Step 2: Calculate Total Expected Sum

Formula:

```text
n × (n + 1) / 2
```

Calculation:

```text
5 × 6 / 2 = 15
```

---

## Step 3: Calculate Array Sum

```text
1 + 2 + 3 + 5 = 11
```

---

## Step 4: Find Missing Number

```text
15 - 11 = 4
```

So the missing number is:

```text
4
```

---

# Optimized Java Code

```java
class Solution {

    int missingNum(int arr[]) {

        long n = arr.length + 1;

        long totalSum = n * (n + 1) / 2;

        long arrSum = 0;

        for (int num : arr) {
            arrSum += num;
        }

        return (int)(totalSum - arrSum);
    }
}
```

---

# Why We Use `long`

For large test cases:

```text
n * (n + 1)
```

can exceed the range of `int`.

Java `int` range:

```text
-2147483648 to 2147483647
```

If overflow happens, the answer becomes incorrect.

So we use `long` to safely store large values.

---

# Algorithm

1. Find `n`
2. Calculate expected sum using formula
3. Find array sum
4. Return the difference

---

# Pseudocode

```text
function missingNum(arr):

    n = arr.length + 1

    totalSum = n * (n + 1) / 2

    arrSum = 0

    for each number in arr:
        arrSum += number

    return totalSum - arrSum
```

---

# Time Complexity

| Operation | Complexity |
|---|---|
| Traversing Array | O(n) |

### Final Complexity

```text
O(n)
```

---

# Space Complexity

No extra data structure is used.

```text
O(1)
```

---

# Why This Approach is Good

- Efficient
- Simple logic
- No sorting needed
- No extra array needed
- Works in one traversal

---

# Interview Points

## Brute Force Approach

- Check every number from `1 to n`
- Time Complexity: `O(n²)`

Not efficient.

---

## Better Approach (Current Solution)

Uses mathematics.

### Advantages

- Faster
- Cleaner code
- Constant space
- Single traversal

---

# Key Learning

This problem teaches:

- Mathematical optimization
- Array traversal
- Overflow handling using `long`
- Time and space optimization

---

# Final Output

```text
Input  : [1, 2, 3, 5]
Output : 4
```

---

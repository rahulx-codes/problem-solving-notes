# Missing Number

## Problem Statement

Given an array `nums` containing `n` distinct numbers in the range `[0, n]`, return the only number in the range that is missing from the array.

---

# Example 1

```java
Input: nums = [3,0,1]

Output: 2
```

### Explanation

Array length is `3`.

So numbers should be:

```java
0 1 2 3
```

But array contains:

```java
3 0 1
```

Missing number is:

```java
2
```

---

# Example 2

```java
Input: nums = [0,1]

Output: 2
```

### Explanation

Array length is `2`.

Numbers should be:

```java
0 1 2
```

But array contains:

```java
0 1
```

Missing number is:

```java
2
```

---

# Understanding the Core Concept

If array size is `n`, then numbers should exist from:

```java
0 → n
```

But one number is missing.

We need to find that missing number.

---

# Best Approach → Sum Formula

## Main Idea

We know:

* Expected sum from `0 → n`
* Actual sum of array elements

Difference between them gives the missing number.

---

# Formula

Expected Sum:

```math
n(n+1)/2
```

Missing Number:

```java
missing = expectedSum - actualSum
```

---

# Why This Works

Suppose:

```java
nums = [3,0,1]
```

## Step 1 → Find Expected Sum

Array length:

```java
n = 3
```

Numbers should be:

```java
0 1 2 3
```

Expected sum:

```java
0 + 1 + 2 + 3 = 6
```

Using formula:

```java
3 * (3 + 1) / 2
= 3 * 4 / 2
= 6
```

---

## Step 2 → Find Actual Sum

Actual array:

```java
[3,0,1]
```

Actual sum:

```java
3 + 0 + 1 = 4
```

---

## Step 3 → Subtract

```java
missing = expectedSum - actualSum

missing = 6 - 4

missing = 2
```

Answer:

```java
2
```

---

# Step-by-Step Algorithm

## Algorithm

### Step 1

Find array length `n`.

### Step 2

Find expected sum using formula:

```java
n * (n + 1) / 2
```

### Step 3

Traverse array and calculate actual sum.

### Step 4

Return:

```java
expectedSum - actualSum
```

---

# Pseudo Code

```text
START

Find n = length of array

Find expectedSum using:
n * (n + 1) / 2

Initialize actualSum = 0

Loop through array:
    Add each element to actualSum

Return expectedSum - actualSum

END
```

---

# Java Solution

```java
class Solution {

    public int missingNumber(int[] nums) {

        int n = nums.length;

        // Expected sum from 0 to n
        int expectedSum = n * (n + 1) / 2;

        // Actual array sum
        int actualSum = 0;

        // Traverse array
        for(int num : nums) {
            actualSum += num;
        }

        // Missing number
        return expectedSum - actualSum;
    }
}
```

---

# Dry Run

## Input

```java
nums = [0,1,3]
```

---

## Step 1

```java
n = 3
```

---

## Step 2 → Expected Sum

```java
expectedSum = 3 * 4 / 2
            = 6
```

---

## Step 3 → Actual Sum

```java
actualSum = 0 + 1 + 3
          = 4
```

---

## Step 4 → Missing Number

```java
missing = 6 - 4
         = 2
```

Output:

```java
2
```

---

# Time Complexity

## Loop runs once

```java
O(n)
```

---

# Space Complexity

No extra space used.

```java
O(1)
```

---

# Why This is a Good Approach

✅ Easy to understand
✅ Easy to explain in interview
✅ Optimal solution
✅ No extra array needed
✅ Efficient

---

# Alternative Approaches

## 1. Brute Force

Check every number one by one.

### Complexity

```java
O(n²)
```

---

## 2. Sorting

Sort array and compare indexes.

### Complexity

```java
O(n log n)
```

---

## 3. XOR Approach (Advanced)

Uses XOR operator to find missing number.

Also optimal:

```java
O(n)
```

But harder for beginners.

---

# Interview Tip

In interviews:

1. First explain brute force
2. Then give optimized solution
3. Explain why optimized is better

This shows strong problem-solving skills.

---

# Key Learning from This Problem

After solving this problem you learn:

* Array traversal
* Sum formula usage
* Mathematical optimization
* Difference between expected and actual values
* Time complexity optimization

---

# Final Summary

If array size is `n`:

* Numbers should exist from `0 → n`
* One number is missing
* Find:

  * Expected sum
  * Actual sum
* Difference gives missing number

Final Formula:

```java
missing = expectedSum - actualSum
```

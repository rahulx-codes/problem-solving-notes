# Majority Element — Boyer Moore Voting Algorithm

## Problem Statement

Given an integer array `nums`, find the element that appears more than `n / 2` times.

If no such element exists, return `-1`.

---

# Example

Input:

```text
nums = [1, 1, 2, 1, 3, 5, 1]
```

Output:

```text
1
```

Explanation:

```text
1 appears 4 times
Array size = 7

7 / 2 = 3

4 > 3
```

So `1` is the majority element.

---

# Algorithm Used

```text
Boyer Moore Voting Algorithm
```

This is the optimal solution for Majority Element problem.

---

# Core Idea

Different elements cancel each other.

The majority element survives because its frequency is greater than all other elements combined.

---

# Algorithm Steps

1. Find a possible candidate
2. Verify candidate frequency
3. Return candidate if frequency > n/2
4. Otherwise return -1

---

# Candidate Selection Logic

We maintain:

```java
candidate
count
```

Rules:

- If count becomes 0 → choose new candidate
- Same element → count++
- Different element → count--

---

# Pseudocode

```text
SET candidate = 0
SET count = 0

FOR each number in array

    IF count == 0
        candidate = current number

    IF current number == candidate
        count++
    ELSE
        count--

SET freq = 0

FOR each number in array

    IF number == candidate
        freq++

IF freq > n/2
    RETURN candidate
ELSE
    RETURN -1
```

---

# Java Code

```java
public class MajorityElement {

    public static int findMajorityElement(int[] nums) {

        int candidate = 0;
        int count = 0;

        // Step 1: Find Candidate
        for (int num : nums) {

            if (count == 0) {
                candidate = num;
            }

            count += (num == candidate) ? 1 : -1;
        }

        // Step 2: Verify Candidate
        int freq = 0;

        for (int num : nums) {

            if (num == candidate) {
                freq++;
            }
        }

        return freq > nums.length / 2 ? candidate : -1;
    }

    public static void main(String[] args) {

        int[] arr1 = {1, 1, 2, 1, 3, 5, 1};
        int[] arr2 = {7};
        int[] arr3 = {2, 13};

        System.out.println(findMajorityElement(arr1));
        System.out.println(findMajorityElement(arr2));
        System.out.println(findMajorityElement(arr3));
    }
}
```

---

# Dry Run

Array:

```text
[1, 1, 2, 1, 3, 5, 1]
```

| Current Number | Candidate | Count |
|---|---|---|
| 1 | 1 | 1 |
| 1 | 1 | 2 |
| 2 | 1 | 1 |
| 1 | 1 | 2 |
| 3 | 1 | 1 |
| 5 | 1 | 0 |
| 1 | 1 | 1 |

Final Candidate:

```text
1
```

Verification:

```text
1 appears 4 times
```

Return:

```text
1
```

---

# Time Complexity

Candidate Selection:

```text
O(n)
```

Verification:

```text
O(n)
```

Total:

```text
O(n)
```

---

# Space Complexity

Only variables are used.

```text
O(1)
```

---

# Why This Algorithm is Best?

| Approach | Time | Space |
|---|---|---|
| Brute Force | O(n²) | O(1) |
| HashMap | O(n) | O(n) |
| Boyer Moore | O(n) | O(1) |

---

# Advantages

- Optimal solution
- No extra memory
- Fast execution
- Interview favorite algorithm

---

# Edge Cases

## Single Element

```text
[7]
```

Output:

```text
7
```

---

## No Majority Element

```text
[2, 13]
```

Output:

```text
-1
```

---

## All Elements Same

```text
[5, 5, 5, 5]
```

Output:

```text
5
```

---

# Final Conclusion

Boyer Moore Voting Algorithm solves the Majority Element problem using:

```text
Candidate Selection
+
Cancellation Logic
+
Verification
```

Final Complexity:

```text
Time  → O(n)
Space → O(1)
```

This makes it the optimal solution.

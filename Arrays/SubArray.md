# What is a SubArray?

A **SubArray** is a **continuous part** of an array.

## Important Rules

* Elements must be continuous
* Order cannot change
* Skipping elements is not allowed

---

# Example

```java
int[] arr = {1, 2, 3};
```

Possible SubArrays:

```text
[1]
[1,2]
[1,2,3]
[2]
[2,3]
[3]
```

Invalid SubArray:

```text
[1,3]
```

Because elements are not continuous.

---

# SubArray vs Subsequence

| Feature          | SubArray | Subsequence |
| ---------------- | -------- | ----------- |
| Continuous       | ✅ Yes    | ❌ No        |
| Order Matters    | ✅ Yes    | ✅ Yes       |
| Skipping Allowed | ❌ No     | ✅ Yes       |

---

# Visual Understanding

```text
Index : 0  1  2  3
Array : 1  2  3  4
```

SubArrays:

```text
[1]
[1,2]
[1,2,3]
[1,2,3,4]
[2]
[2,3]
[2,3,4]
[3]
[3,4]
[4]
```

---

# Total Number of SubArrays

## Formula

```text
n(n + 1) / 2
```

Where:

* n = size of array

---

# Example

```text
n = 4

4 × 5 / 2
= 10
```

Total SubArrays = 10

---

# Why Formula Works

```text
Index 0 → 4 subarrays
Index 1 → 3 subarrays
Index 2 → 2 subarrays
Index 3 → 1 subarray
```

Total:

```text
4 + 3 + 2 + 1 = 10
```

---

# Basic Logic of SubArray

To generate subarrays we need:

* Start index
* End index

Then print all elements between them.

---

# Algorithm — Print All SubArrays

## Step-by-Step Algorithm

```text
STEP 1: Start

STEP 2: Take array input

STEP 3: Run loop from start = 0 to n-1

STEP 4: Run another loop from end = start to n-1

STEP 5: Run third loop from i = start to end

STEP 6: Print arr[i]

STEP 7: Print new line after every subarray

STEP 8: Repeat until all subarrays printed

STEP 9: Stop
```

---

# Pseudocode — Print All SubArrays

```text
FUNCTION printSubArrays(arr)

    FOR start = 0 TO length-1

        FOR end = start TO length-1

            FOR i = start TO end

                PRINT arr[i]

            PRINT new line
```

---

# Dry Run

## Array

```text
[1,2,3]
```

---

## Execution

### start = 0

```text
end = 0 → [1]
end = 1 → [1,2]
end = 2 → [1,2,3]
```

### start = 1

```text
end = 1 → [2]
end = 2 → [2,3]
```

### start = 2

```text
end = 2 → [3]
```

---

# Java Code — Print All SubArrays

```java
public class SubArray {

    public static void printSubArrays(int[] arr) {

        int total = 0;

        for (int start = 0; start < arr.length; start++) {

            for (int end = start; end < arr.length; end++) {

                // Print one subarray
                for (int i = start; i <= end; i++) {

                    System.out.print(arr[i] + " ");
                }

                total++;
                System.out.println();
            }
        }

        System.out.println("Total SubArrays = " + total);
    }

    public static void main(String[] args) {

        int[] arr = {1, 2, 3};

        printSubArrays(arr);
    }
}
```

---

# Output

```text
1
1 2
1 2 3
2
2 3
3

Total SubArrays = 6
```

---

# Time Complexity

## Outer Loop

```text
O(n)
```

## Second Loop

```text
O(n)
```

## Third Loop

```text
O(n)
```

## Total Complexity

```text
O(n³)
```

---

# Space Complexity

```text
O(1)
```

No extra space used.

---

# Maximum SubArray Sum

## Problem

Find the subarray having maximum sum.

---

# Example

```text
Array:
[-2,1,-3,4,-1,2,1,-5,4]
```

Maximum Sum SubArray:

```text
[4,-1,2,1]
```

Sum:

```text
6
```

---

# Approaches

| Approach         | Complexity |
| ---------------- | ---------- |
| Brute Force      | O(n³)      |
| Prefix Sum       | O(n²)      |
| Kadane Algorithm | O(n)       |

---

# Brute Force Approach

## Main Idea

* Generate every subarray
* Calculate each sum
* Store maximum sum

---

# Algorithm — Maximum SubArray Sum

```text
STEP 1: Start

STEP 2: Initialize maxSum = -∞

STEP 3: Run loop for start index

STEP 4: Run loop for end index

STEP 5: Initialize currentSum = 0

STEP 6: Traverse subarray from start to end

STEP 7: Add all elements into currentSum

STEP 8: Compare currentSum with maxSum

STEP 9: Update maxSum if needed

STEP 10: Repeat for all subarrays

STEP 11: Print maxSum

STEP 12: Stop
```

---

# Pseudocode — Maximum SubArray Sum

```text
FUNCTION maxSubArray(arr)

    maxSum = -infinity

    FOR start = 0 TO n-1

        FOR end = start TO n-1

            currentSum = 0

            FOR i = start TO end

                currentSum += arr[i]

            IF currentSum > maxSum

                maxSum = currentSum

    PRINT maxSum
```

---

# Java Code — Brute Force Maximum Sum

```java
public class MaxSubArray {

    public static void maxSubArraySum(int[] arr) {

        int maxSum = Integer.MIN_VALUE;

        for (int start = 0; start < arr.length; start++) {

            for (int end = start; end < arr.length; end++) {

                int currentSum = 0;

                for (int i = start; i <= end; i++) {

                    currentSum += arr[i];
                }

                maxSum = Math.max(maxSum, currentSum);
            }
        }

        System.out.println("Maximum Sum = " + maxSum);
    }

    public static void main(String[] args) {

        int[] arr = {1, -2, 6, -1, 3};

        maxSubArraySum(arr);
    }
}
```

---

# Prefix Sum Concept

## What is Prefix Sum?

Prefix Sum stores cumulative sums.

---

# Example

```text
arr = [1,2,3,4]

prefix = [1,3,6,10]
```

Meaning:

```text
1
1+2
1+2+3
1+2+3+4
```

---

# Prefix Sum Formula

```text
SubArray Sum =
prefix[end] - prefix[start - 1]
```

If start = 0:

```text
SubArray Sum = prefix[end]
```

---

# Algorithm — Prefix Sum

```text
STEP 1: Create prefix array

STEP 2: Store cumulative sums

STEP 3: Run loops for start and end

STEP 4: Find subarray sum using formula

STEP 5: Compare with maxSum

STEP 6: Print maximum sum
```

---

# Pseudocode — Prefix Sum

```text
FUNCTION prefixSum(arr)

    CREATE prefix[]

    prefix[0] = arr[0]

    FOR i = 1 TO n-1

        prefix[i] =
        prefix[i-1] + arr[i]

    maxSum = -infinity

    FOR start = 0 TO n-1

        FOR end = start TO n-1

            IF start == 0

                currentSum = prefix[end]

            ELSE

                currentSum =
                prefix[end] -
                prefix[start-1]

            maxSum =
            maximum(maxSum, currentSum)

    PRINT maxSum
```

---

# Java Code — Prefix Sum

```java
public class PrefixSum {

    public static void maxSubArray(int[] arr) {

        int[] prefix = new int[arr.length];

        prefix[0] = arr[0];

        // Create prefix array
        for (int i = 1; i < arr.length; i++) {

            prefix[i] = prefix[i - 1] + arr[i];
        }

        int maxSum = Integer.MIN_VALUE;

        for (int start = 0; start < arr.length; start++) {

            for (int end = start; end < arr.length; end++) {

                int currentSum;

                if (start == 0) {

                    currentSum = prefix[end];

                } else {

                    currentSum =
                    prefix[end] - prefix[start - 1];
                }

                maxSum = Math.max(maxSum, currentSum);
            }
        }

        System.out.println("Maximum Sum = " + maxSum);
    }

    public static void main(String[] args) {

        int[] arr = {1, -2, 6, -1, 3};

        maxSubArray(arr);
    }
}
```

---

# Kadane’s Algorithm

# Best Optimized Approach

Time Complexity:

```text
O(n)
```

---

# Main Idea

If current sum becomes negative:

* Reset it to 0

Because negative sum decreases future sum.

---

# Algorithm — Kadane’s Algorithm

```text
STEP 1: Start

STEP 2: Initialize:

         currentSum = 0
         maxSum = -∞

STEP 3: Traverse array

STEP 4: Add current element into currentSum

STEP 5: Compare currentSum with maxSum

STEP 6: Update maxSum

STEP 7: If currentSum < 0
         set currentSum = 0

STEP 8: Repeat for all elements

STEP 9: Print maxSum

STEP 10: Stop
```

---

# Pseudocode — Kadane Algorithm

```text
FUNCTION kadane(arr)

    currentSum = 0
    maxSum = -infinity

    FOR each element

        currentSum += element

        IF currentSum > maxSum

            maxSum = currentSum

        IF currentSum < 0

            currentSum = 0

    PRINT maxSum
```

---

# Java Code — Kadane Algorithm

```java
public class KadaneAlgorithm {

    public static void kadane(int[] arr) {

        int maxSum = Integer.MIN_VALUE;
        int currentSum = 0;

        for (int i = 0; i < arr.length; i++) {

            currentSum += arr[i];

            maxSum = Math.max(maxSum, currentSum);

            if (currentSum < 0) {

                currentSum = 0;
            }
        }

        System.out.println("Maximum Sum = " + maxSum);
    }

    public static void main(String[] args) {

        int[] arr = {-2,1,-3,4,-1,2,1,-5,4};

        kadane(arr);
    }
}
```

---

# Kadane Dry Run

```text
Array:
[-2,1,-3,4,-1,2,1]
```

| Element | Current Sum | Max Sum |
| ------- | ----------- | ------- |
| -2      | -2 → 0      | -2      |
| 1       | 1           | 1       |
| -3      | -2 → 0      | 1       |
| 4       | 4           | 4       |
| -1      | 3           | 4       |
| 2       | 5           | 5       |
| 1       | 6           | 6       |

Final Answer:

```text
6
```

---

# Complexity Comparison

| Approach            | Time Complexity | Space Complexity |
| ------------------- | --------------- | ---------------- |
| Print All SubArrays | O(n³)           | O(1)             |
| Brute Force Max Sum | O(n³)           | O(1)             |
| Prefix Sum          | O(n²)           | O(n)             |
| Kadane Algorithm    | O(n)            | O(1)             |

---

# Important Interview Questions

## Easy

* Print all subarrays
* Count total subarrays
* Find smallest subarray

## Medium

* Maximum subarray sum
* Minimum subarray sum
* Subarray with given sum

## Hard

* Kadane variations
* Circular subarray sum
* Sliding window problems

---

# Final Revision Notes

| Topic             | Key Point               |
| ----------------- | ----------------------- |
| SubArray          | Continuous elements     |
| Formula           | n(n+1)/2                |
| Brute Force       | 3 loops                 |
| Prefix Sum        | Fast sum calculation    |
| Kadane            | Best optimized approach |
| Kadane Complexity | O(n)                    |

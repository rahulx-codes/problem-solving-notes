# First Occurrence of an Element (Sorted & Unsorted Array)

## Problem Statement

Given an array `arr[]` and a target element `k`, find the **first occurrence** (smallest index) of `k`.

If the element does not exist in the array, return `-1`.

---

## Example 1 (Unsorted Array)

```text
Input:
arr = [5, 9, 3, 7, 3, 8]
k = 3

Output:
2
```

### Explanation

```text
Index : 0 1 2 3 4 5
Array : 5 9 3 7 3 8
```

The first occurrence of `3` is at index `2`.

---

## Example 2 (Sorted Array)

```text
Input:
arr = [1, 2, 4, 4, 4, 7, 9]
k = 4

Output:
2
```

### Explanation

```text
Index : 0 1 2 3 4 5 6
Array : 1 2 4 4 4 7 9
```

The first occurrence of `4` is at index `2`.

---

# Approach 1: Unsorted Array (Linear Search)

## Intuition

Since the array is not sorted, Binary Search cannot be applied.

The simplest approach is:

- Start from index `0`
- Traverse the array
- Return the first index where target is found

---

## Algorithm

1. Traverse the array from left to right.
2. Compare every element with target.
3. If target is found, return the current index.
4. If traversal completes, return `-1`.

---

## Pseudocode

```text
FUNCTION FirstOccurrenceUnsorted(arr, k)

    FOR i = 0 TO arr.length - 1

        IF arr[i] == k
            RETURN i

    END FOR

    RETURN -1

END FUNCTION
```

---

## Dry Run

```text
arr = [5, 9, 3, 7, 3, 8]
k = 3
```

### Iteration 1

```text
i = 0
arr[0] = 5
```

Not Found

---

### Iteration 2

```text
i = 1
arr[1] = 9
```

Not Found

---

### Iteration 3

```text
i = 2
arr[2] = 3
```

Found

```text
Return 2
```

---

## Java Code

```java
class Solution {

    public int firstOccurrence(int[] arr, int k) {

        for (int i = 0; i < arr.length; i++) {

            if (arr[i] == k) {
                return i;
            }
        }

        return -1;
    }
}
```

---

## Complexity Analysis

### Time Complexity

```text
O(n)
```

Worst case: Element is at the end or not present.

### Space Complexity

```text
O(1)
```

---

# Approach 2: Sorted Array (Binary Search)

## Intuition

Since the array is sorted, Binary Search can be used.

However, normal Binary Search is not enough.

### Normal Binary Search

```text
Target Found
↓
Return Immediately
```

### First Occurrence Binary Search

```text
Target Found
↓
Store Answer
↓
Move Left
```

Because there may be another occurrence on the left side.

---

## Core Logic

Whenever target is found:

```java
ans = mid;
high = mid - 1;
```

Why?

Because we are searching for an earlier occurrence.

---

## Algorithm

1. Initialize:

```java
low = 0;
high = n - 1;
ans = -1;
```

2. While `low <= high`

- Calculate mid.
- If target found:
  - Store answer.
  - Move left.
- If target is greater:
  - Move right.
- If target is smaller:
  - Move left.

3. Return answer.

---

## Pseudocode

```text
FUNCTION FirstOccurrenceSorted(arr, k)

    low = 0
    high = arr.length - 1
    ans = -1

    WHILE low <= high

        mid = low + (high - low) / 2

        IF arr[mid] == k

            ans = mid
            high = mid - 1

        ELSE IF arr[mid] < k

            low = mid + 1

        ELSE

            high = mid - 1

        END IF

    END WHILE

    RETURN ans

END FUNCTION
```

---

## Dry Run

```text
arr = [1, 2, 4, 4, 4, 7, 9]
k = 4
```

### Iteration 1

```text
low = 0
high = 6

mid = 3
arr[3] = 4
```

Target Found

```text
ans = 3
high = 2
```

Move Left

---

### Iteration 2

```text
low = 0
high = 2

mid = 1
arr[1] = 2
```

Target is larger

```text
low = 2
```

---

### Iteration 3

```text
low = 2
high = 2

mid = 2
arr[2] = 4
```

Target Found

```text
ans = 2
high = 1
```

Loop Ends

Return:

```text
2
```

---

## Visualization

```text
Index : 0 1 2 3 4 5 6
Array : 1 2 4 4 4 7 9
                ↑
              mid
```

Found target.

Store answer:

```text
ans = 3
```

Move left:

```text
high = mid - 1
```

Search again.

```text
Index : 0 1 2
Array : 1 2 4
              ↑
```

Found earlier occurrence.

```text
ans = 2
```

Final Answer:

```text
2
```

---

## Java Code

```java
class Solution {

    public int firstSearch(int[] arr, int k) {

        int low = 0;
        int high = arr.length - 1;

        int ans = -1;

        while (low <= high) {

            int mid = low + (high - low) / 2;

            if (arr[mid] == k) {

                ans = mid;
                high = mid - 1;

            } else if (arr[mid] < k) {

                low = mid + 1;

            } else {

                high = mid - 1;
            }
        }

        return ans;
    }
}
```

---

# Last Occurrence (Follow-Up)

## Pseudocode

```text
FUNCTION LastOccurrence(arr, k)

    low = 0
    high = arr.length - 1
    ans = -1

    WHILE low <= high

        mid = low + (high - low) / 2

        IF arr[mid] == k

            ans = mid
            low = mid + 1

        ELSE IF arr[mid] < k

            low = mid + 1

        ELSE

            high = mid - 1

        END IF

    END WHILE

    RETURN ans

END FUNCTION
```

---

## Code Logic

### First Occurrence

```java
if(arr[mid] == k){
    ans = mid;
    high = mid - 1;
}
```

Move Left.

---

### Last Occurrence

```java
if(arr[mid] == k){
    ans = mid;
    low = mid + 1;
}
```

Move Right.

---

# Complexity Comparison

| Approach | Array Type | Time Complexity | Space Complexity |
|-----------|------------|----------------|------------------|
| Linear Search | Unsorted | O(n) | O(1) |
| Binary Search | Sorted | O(log n) | O(1) |

---

# Interview Notes

### When Array is Unsorted

```text
Use Linear Search
```

Reason:

```text
No ordering exists.
Binary Search cannot work.
```

---

### When Array is Sorted

```text
Use Binary Search
```

Reason:

```text
Search space can be reduced by half.
```

---

### Most Important Rule

```text
First Occurrence
↓
Store Answer
↓
Move Left
```

```text
high = mid - 1
```

---

### Last Occurrence

```text
Store Answer
↓
Move Right
```

```text
low = mid + 1
```

---

# Memory Trick

```text
FOUND TARGET

Normal Binary Search
↓
Return

First Occurrence
↓
Store Answer
↓
Go Left

Last Occurrence
↓
Store Answer
↓
Go Right
```

---

# Key Takeaway

Normal Binary Search stops immediately after finding the target.

For First Occurrence:

```text
Found Target
↓
Store Index
↓
Search Left
```

For Last Occurrence:

```text
Found Target
↓
Store Index
↓
Search Right
```

This pattern is one of the most important Binary Search interview questions and is frequently asked in coding rounds, placements, and DSA interviews.

# Third Largest Element

## Problem Statement

Given an array of integers, find the third largest element.

Return `-1` if the third largest element does not exist.

---

# Example

Input:

```text
[2, 4, 1, 3, 5]
```

Output:

```text
3
```

Explanation:

```text
Largest   = 5
2nd Large = 4
3rd Large = 3
```

---

# Concept

We use three variables:

```text
first
second
third
```

These variables store:

```text
1st largest element
2nd largest element
3rd largest element
```

While traversing the array:

- If a bigger element is found:
  - Shift previous values
- Update first, second, and third accordingly

This avoids sorting and gives better performance.

---

# Algorithm

1. Initialize:

```text
first = -∞
second = -∞
third = -∞
```

2. Traverse the array.

3. For every element:

- If element > first
  - Shift:
    - third = second
    - second = first
    - first = element

- Else if element > second
  - Shift:
    - third = second
    - second = element

- Else if element > third
  - third = element

4. Return third.

---

# Pseudocode

```text
Initialize first, second, third as minimum value

For each element in array:

    If element > first:
        third = second
        second = first
        first = element

    Else if element > second:
        third = second
        second = element

    Else if element > third:
        third = element

Return third
```

---

# Java Code

```java
public class ThirdLargest {

    public static int thirdLargest(int[] arr) {

        // Check if array has less than 3 elements
        if (arr.length < 3) {
            return -1;
        }

        int first = Integer.MIN_VALUE;
        int second = Integer.MIN_VALUE;
        int third = Integer.MIN_VALUE;

        for (int num : arr) {

            // Update first largest
            if (num > first) {
                third = second;
                second = first;
                first = num;
            }

            // Update second largest
            else if (num > second) {
                third = second;
                second = num;
            }

            // Update third largest
            else if (num > third) {
                third = num;
            }
        }

        return third;
    }

    public static void main(String[] args) {

        int[] arr = {2, 4, 1, 3, 5};

        System.out.println(thirdLargest(arr));
    }
}
```

---

# Dry Run

Array:

```text
[2, 4, 1, 3, 5]
```

Final values:

```text
first  = 5
second = 4
third  = 3
```

Answer:

```text
3
```

---

# Time Complexity

```text
O(n)
```

Because the array is traversed only once.

---

# Space Complexity

```text
O(1)
```

Because only 3 extra variables are used.

---

# Key Interview Point

## Sorting Approach

```text
O(n log n)
```

## Optimized Approach

```text
O(n)
```

Using three variables is the optimized solution.

---

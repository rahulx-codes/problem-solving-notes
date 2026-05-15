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
- Find the second largest in Array

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

## Algorithm

1. Start
2. Take first element as `max`
3. Traverse array from index `1`
4. Compare current element with `max`
5. If current element is greater
   → update `max`
6. Repeat until array ends
7. Return `max`
8. End

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

## Complexity

| Type | Complexity |
|---|---|
| Time | O(n) |
| Space | O(1) |

---

## Important Point

Array should not be empty because:

```java
arr[0]
```

can cause error.

---



# Find Second Largest Element in Array

---

# Concept

The second largest element is the element that is smaller than the largest element but greater than all other elements in the array.

Instead of sorting the array, we use two variables:

- Largest
- Second Largest

This helps us solve the problem in a single traversal.

---

# Core Logic

Whenever a new larger element is found:

```text
Old largest → becomes second largest
New element → becomes largest
```

---

# Algorithm

1. Initialize:
   - largest = minimum possible value
   - secondLargest = minimum possible value

2. Traverse the array.

3. If current element is greater than largest:
   - Move largest into secondLargest
   - Update largest

4. Else if current element is:
   - greater than secondLargest
   - and not equal to largest
   
   then update secondLargest.

5. Return secondLargest.

---

#  Pseudocode

```text
START

largest = -∞
secondLargest = -∞

FOR each element in array

    IF element > largest

        secondLargest = largest
        largest = element

    ELSE IF element > secondLargest
            AND element != largest

        secondLargest = element

IF secondLargest == -∞

    RETURN -1

ELSE

RETURN secondLargest

END
```

---

#  Time Complexity

```text
O(n)
```

Because the array is traversed only once.

---

# Space Complexity

```text
O(1)
```

No extra data structure is used.

---

# Advantages

- No sorting required
- Single traversal solution
- Optimized approach
- Faster than sorting
- Handles duplicate largest values correctly

---

# Sorting vs Optimized Approach

| Approach | Time Complexity |
|---|---|
| Sorting | O(n log n) |
| Single Traversal | O(n) |

The single traversal approach is more optimized.

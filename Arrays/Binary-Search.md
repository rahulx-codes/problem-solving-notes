# Binary Search in Java

Binary Search is a fast and efficient searching algorithm used on **sorted arrays**.

It works by repeatedly dividing the search space into half.

Instead of checking every element one by one, Binary Search directly moves toward the target element.

---

# Condition

Binary Search works only when the array is:

```text
Sorted
```

Example:

```text
[1, 3, 5, 7, 9, 11]
```

---

# Core Concept

1. Find the middle element
2. Compare middle element with target
3. If target is greater → move right
4. If target is smaller → move left
5. Repeat until element is found

---

# Visualization

Target = 9

```text
[1, 3, 5, 7, 9, 11]

mid = 5
9 > 5
Move Right

[7, 9, 11]

mid = 9
Found
```

---

# Algorithm

1. Initialize:
   - start = 0
   - end = arr.length - 1

2. Run loop until:
   - start <= end

3. Find middle:
   - mid = start + (end - start) / 2

4. Compare:
   - If arr[mid] == target → return true
   - If arr[mid] < target → move right
   - Else → move left

5. If loop ends:
   - Element not found

---

# Optimized Java Code

```java
public class BinarySearch {

    public static boolean binarySearch(int[] arr, int target) {

        int start = 0;
        int end = arr.length - 1;

        while (start <= end) {

            int mid = start + (end - start) / 2;

            if (arr[mid] == target) {
                return true;
            }

            if (arr[mid] < target) {
                start = mid + 1;
            } else {
                end = mid - 1;
            }
        }

        return false;
    }

    public static void main(String[] args) {

        int[] arr = {1, 3, 5, 7, 9, 11};

        int target = 9;

        boolean result = binarySearch(arr, target);

        System.out.println(result);
    }
}
```

---

# Dry Run

Array:

```text
[1, 3, 5, 7, 9, 11]
```

Target:

```text
9
```

---

## Iteration 1

| start | end | mid | arr[mid] |
|------|------|------|------|
| 0 | 5 | 2 | 5 |

```text
9 > 5
Move Right
```

New:

```text
start = 3
```

---

## Iteration 2

| start | end | mid | arr[mid] |
|------|------|------|------|
| 3 | 5 | 4 | 9 |

```text
Found
```

---

# Important Mid Formula

## Wrong Way

```java
int mid = (start + end) / 2;
```

Problem:

```text
Integer Overflow
```

---

## Correct Optimized Way

```java
int mid = start + (end - start) / 2;
```

This approach is safer and optimized.

---

# Time Complexity

```text
O(log n)
```

Because:

```text
Every iteration removes half of the array
```

---

# Space Complexity

```text
O(1)
```

No extra space is used.

---

# Binary Search vs Linear Search

| Feature | Linear Search | Binary Search |
|------|------|------|
| Array Type | Sorted/Unsorted | Sorted Only |
| Time Complexity | O(n) | O(log n) |
| Speed | Slow | Fast |
| Large Data | Inefficient | Efficient |

---

# Common Mistakes

## 1. Using Unsorted Array

Binary Search only works on sorted arrays.

---

## 2. Wrong While Condition

Wrong:

```java
while(end <= start)
```

Correct:

```java
while(start <= end)
```

---

## 3. Wrong Pointer Movement

Correct Rules:

| Condition | Move |
|------|------|
| arr[mid] < target | start = mid + 1 |
| arr[mid] > target | end = mid - 1 |

---

## 4. Infinite Loop

Wrong pointer updates can cause infinite loops.

---

# Recursive Binary Search

Binary Search can also be implemented recursively.

But iterative approach is usually better because:

- Less memory usage
- Faster execution
- No recursion stack overhead

---

# Real Life Example

Dictionary Search:

You do not search every page one by one.

You open the middle section first.

That is exactly how Binary Search works.

---

# Interview Important Points

- Works only on sorted arrays
- Uses Divide and Conquer technique
- Faster than Linear Search
- Common interview question
- Used in databases and search systems

---

# Applications of Binary Search

- Searching in sorted arrays
- Databases
- Search engines
- Competitive programming
- Large datasets
- System design

---

# Pseudocode

```text
BinarySearch(arr, target)

start = 0
end = arr.length - 1

while(start <= end)

    mid = start + (end - start) / 2

    if(arr[mid] == target)
        return true

    if(arr[mid] < target)
        start = mid + 1

    else
        end = mid - 1

return false
```

---

# Final Summary

Binary Search is:

- Fast
- Efficient
- Optimized
- Based on Divide and Conquer
- Best for sorted data

---

# Complexity Summary

| Complexity Type | Value |
|------|------|
| Time Complexity | O(log n) |
| Space Complexity | O(1) |

---

# Key Takeaways

- Array must be sorted
- Always calculate mid carefully
- Use correct pointer movement
- Much faster than Linear Search
- One of the most important DSA algorithms

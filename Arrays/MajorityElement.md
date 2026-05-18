# Majority Element

## Problem Statement

Given an integer array `nums`, find the element that appears more than `n / 2` times.

If no such element exists, return `-1`.

---

# Example

Input:

```text
nums = [2, 2, 1, 2, 3, 2, 2]
```

Output:

```text
2
```

Explanation:

```text
2 appears 5 times
Array size = 7

7 / 2 = 3

5 > 3
```

So `2` is the majority element.

---

# Brute Force Idea

For every element:

- Count how many times it appears
- Check if frequency is greater than `n / 2`

If yes:

```text
Return that element
```

Otherwise:

```text
Return -1
```

---

# Algorithm

1. Traverse array using outer loop
2. For every element, count frequency using inner loop
3. If frequency > n/2
4. Return element
5. If no majority found, return -1

---

# Pseudocode

```text
FOR each element i

    count = 0

    FOR each element j

        IF arr[i] == arr[j]
            count++

    IF count > n/2
        RETURN arr[i]

RETURN -1
```

---

# Dry Run

Array:

```text
[2, 2, 1, 2, 3, 2, 2]
```

---

## Step 1

Current element:

```text
2
```

Count occurrences:

```text
2 → 5 times
```

Check:

```text
5 > 7/2
5 > 3
```

True.

Return:

```text
2
```

---

# Java Code

```java
public class MajorityElement {

    public static int solution(int[] nums) {

        for (int i = 0; i < nums.length; i++) {

            int count = 0;

            for (int j = 0; j < nums.length; j++) {

                if (nums[i] == nums[j]) {
                    count++;
                }
            }

            if (count > nums.length / 2) {
                return nums[i];
            }
        }

        return -1;
    }

    public static void main(String[] args) {

        int[] nums = {2, 2, 1, 2, 3, 2, 2};

        System.out.println(solution(nums));
    }
}
```

---

# Time Complexity

Outer loop:

```text
O(n)
```

Inner loop:

```text
O(n)
```

Total:

```text
O(n²)
```

---

# Space Complexity

Only variables are used.

```text
O(1)
```

---

# Advantages

- Easy to understand
- Beginner friendly
- Simple logic

---

# Disadvantages

- Slow for large arrays
- Uses nested loops
- Not optimal for interviews

---

# Final Conclusion

The Brute Force approach checks frequency of every element using nested loops.

Complexity:

```text
Time  → O(n²)
Space → O(1)
```

Good for learning basic array logic before optimized approaches like HashMap and Boyer Moore Voting Algorithm.

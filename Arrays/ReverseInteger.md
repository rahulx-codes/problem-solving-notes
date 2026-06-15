# Reverse Integer in Java

# What is Reverse Integer?

Reverse Integer means reversing the digits of a number.

## Example

```java
1234 -> 4321
567  -> 765
120  -> 21
-123 -> -321
```

---

# Main Concept

We take digits from the END of the number one by one.

Two very important operations:

| Operation | Meaning           |
| --------- | ----------------- |
| `% 10`    | Get last digit    |
| `/ 10`    | Remove last digit |

---

# Understanding `% 10`

```java
123 % 10 = 3
```

Why?

Because `3` is the last digit.

---

# Understanding `/ 10`

```java
123 / 10 = 12
```

Why?

Because integer division removes the last digit.

---

# Main Reverse Formula

```java
reversed = reversed * 10 + digit;
```

## Why `* 10`?

Suppose:

```java
reversed = 32
digit = 1
```

We want:

```java
321
```

So first shift digits left:

```java
32 * 10 = 320
```

Then add digit:

```java
320 + 1 = 321
```

---

# Algorithm

1. Start loop until number becomes `0`
2. Extract last digit using `% 10`
3. Add digit into reversed number
4. Remove last digit using `/ 10`
5. Repeat

---

# Pseudo Code

```text
START

num = 4526
reversed = 0

WHILE num is not 0

    digit = num % 10

    reversed = reversed * 10 + digit

    num = num / 10

END WHILE

PRINT reversed

END
```

---

# Simple Reverse Program

```java
public class SimpleReverse {

    public static void main(String[] args) {

        int num = 4526;
        int reversed = 0;

        while (num != 0) {

            int digit = num % 10;

            reversed = reversed * 10 + digit;

            num /= 10;
        }

        System.out.println("Reversed Number: " + reversed);
    }
}
```

---

# Dry Run

## Input

```java
num = 4526
```

---

## Iteration 1

```java
digit = 4526 % 10 = 6

reversed = 0 * 10 + 6
reversed = 6

num = 4526 / 10
num = 452
```

---

## Iteration 2

```java
digit = 452 % 10 = 2

reversed = 6 * 10 + 2
reversed = 62

num = 45
```

---

## Iteration 3

```java
digit = 45 % 10 = 5

reversed = 62 * 10 + 5
reversed = 625

num = 4
```

---

## Iteration 4

```java
digit = 4 % 10 = 4

reversed = 625 * 10 + 4
reversed = 6254

num = 0
```

Loop stops.

---

# Output

```java
6254
```

---

# Time Complexity

| Complexity | Value      |
| ---------- | ---------- |
| Time       | O(log10 n) |
| Space      | O(1)       |

---

# Important Pattern

This concept is used in:

* Reverse Integer
* Palindrome Number
* Armstrong Number
* Sum of Digits
* Count Digits

Very important DSA pattern.

---

# LeetCode Question 7 — Reverse Integer

## Problem

Reverse digits of a signed 32-bit integer.

If reversed number goes outside int range:

```java
-2147483648 to 2147483647
```

Return:

```java
0
```

---

# Important Difference

In normal reverse program:

```java
int reversed
```

works fine.

But in LeetCode Question 7:

reverse can become VERY BIG.

Example:

```java
1534236469
```

Reverse:

```java
9646324351
```

This is bigger than int range.

So we use:

```java
long reversed
```

to safely store large values temporarily.

---

# LeetCode 7 Algorithm

1. Extract last digit
2. Build reverse number
3. Remove last digit
4. After loop check overflow
5. If outside int range return 0

---

# Pseudo Code

```text
START

reversed = 0

WHILE x is not 0

    digit = x % 10

    reversed = reversed * 10 + digit

    x = x / 10

END WHILE

IF reversed exceeds int range

    RETURN 0

RETURN reversed

END
```

---

# LeetCode 7 Code

```java
public class ReverseInteger {

    public static int reverse(int x) {

        long reversed = 0;

        while (x != 0) {

            int remainder = x % 10;

            reversed = reversed * 10 + remainder;

            x /= 10;
        }

        // Overflow Check
        if (reversed > Integer.MAX_VALUE ||
            reversed < Integer.MIN_VALUE) {

            return 0;
        }

        return (int) reversed;
    }

    public static void main(String[] args) {

        System.out.println(reverse(1234));

        System.out.println(reverse(-567));

        System.out.println(reverse(1534236469));
    }
}
```

---

# Understanding Overflow

## Integer.MAX_VALUE

```java
2147483647
```

## Integer.MIN_VALUE

```java
-2147483648
```

If reversed number becomes bigger or smaller than this range:

```java
return 0;
```

---

# Example

## Input

```java
1534236469
```

## Reverse

```java
9646324351
```

Too large for int.

So output:

```java
0
```

---

# Why This Approach is Beginner Friendly

Instead of predicting overflow before operation:

```java
Use long
Reverse safely
Check range at end
```

Easy to understand and clean.

---

# Final Notes

## Core Formula

```java
reversed = reversed * 10 + digit;
```

## Core Operations

```java
% 10  -> extract last digit

/ 10  -> remove last digit
```

These operations are extremely important in DSA and interviews.

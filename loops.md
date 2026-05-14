# Loops All Question 

---


# Find Next Prime Number

## Concept

A prime number is a number that is divisible only by:

- `1`
- itself

### Example

```text
2 3 5 7 11 13 17
```

---

# Algorithm

1. Start checking from `n + 1`
2. Skip even numbers
3. Check if number is prime
4. If not prime
   → move to next odd number
5. Repeat until prime number found
6. Return the prime number

---

# Pseudocode

## Find Next Prime

```text
FUNCTION checkNextPrime(n)

    num = n + 1

    IF num is even
        num = num + 1

    WHILE num is not prime
        num = num + 2

    RETURN num
```

---

## Prime Checking

```text
FUNCTION isPrime(n)

    IF n <= 1
        RETURN false

    IF n == 2
        RETURN true

    IF n is even
        RETURN false

    FOR i = 3 to √n step by 2

        IF n % i == 0
            RETURN false

    RETURN true
```

---

# Optimization Used

## 1. Skip Even Numbers

All even numbers are non-prime except `2`.

Instead of:

```text
21 → 22 → 23 → 24
```

we check:

```text
21 → 23 → 25
```

---

## 2. Check Till Square Root

Instead of checking till `n`, check till:

:contentReference[oaicite:0]{index=0}

Because factors repeat after square root.

---

# Main Logic

```java
while (!isPrime(num)) {
    num += 2;
}
```

Meaning:

- Keep checking numbers
- If number is not prime
  → move to next odd number
- Stop when prime number is found

---

# Dry Run

## Input

```text
n = 20
```

## Flow

```text
21 → not prime
23 → prime
```

## Output

```text
23
```

---

# ⏱ Time Complexity

```text
O(√n)
```

# 🚀 Functions in Java

> A function (method in Java) is a reusable block of code used to perform a specific task.

---

# 📚 Table of Contents

- [Basic Function Syntax](#-basic-function-syntax)
- [Function Calling](#-function-calling)
- [Function with Parameters](#-function-with-parameters)
- [Return Type Function](#-return-type-function)
- [Void Function](#-void-function)
- [Parameters vs Arguments](#-parameters-vs-arguments)
- [Method Overloading](#-method-overloading)
- [Recursion](#-recursion)
- [Call Stack](#-call-stack)
- [StackOverflowError](#-stackoverflowerror)
- [Local Variable](#-local-variable)
- [Static Method](#-static-method)
- [Non-Static Method](#-non-static-method)
- [Built-in Methods](#-built-in-methods)
- [Pass by Value](#-pass-by-value)
- [Quick Revision](#-quick-revision)

---

# 📌 Basic Function Syntax

```java
returnType functionName() {

}
```

### ✅ Example

```java
static void hello() {
    System.out.println("Hello");
}
```

---

# ▶️ Function Calling

```java
hello();
```

> Function only runs when it is called.

---

# 📥 Function with Parameters

```java
static void greet(String name) {
    System.out.println("Hello " + name);
}
```

### ✅ Calling

```java
greet("Rahul");
```

---

# 🔁 Return Type Function

> Return type defines what value a function sends back.

### 📌 Common Return Types

- `int`
- `double`
- `String`
- `boolean`

### ✅ Example

```java
static int add(int a, int b) {
    return a + b;
}
```

### ✅ Calling

```java
int sum = add(2, 3);
System.out.println(sum);
```

---

# ❌ Void Function

> A void function does not return any value.

### 📌 Used When

- Only printing output
- Performing task without returning data

### ✅ Example

```java
static void print() {
    System.out.println("Hi");
}
```

---

# 📦 Parameters vs Arguments

## 📌 Parameters

Parameters are variables written inside the function definition.

### ✅ Important Points

- Used to receive input
- Work like placeholders
- Defined during function creation

---

## 📌 Arguments

Arguments are actual values passed during function calling.

### ✅ Important Points

- Real data sent to function
- Passed while calling method
- Stored inside parameters

---

## ✅ Example

```java
static void greet(String name)
```

- `name` → Parameter

```java
greet("Rahul");
```

- `"Rahul"` → Argument

---

# 🧠 Method Overloading

> Same method name with different parameters.

### ✅ Example

```java
static int sum(int a, int b) {
    return a + b;
}

static int sum(int a, int b, int c) {
    return a + b + c;
}
```

### 📌 Java Checks

- Number of parameters
- Type of parameters

### 🎯 Benefits

- Improves readability
- Makes code cleaner
- Reduces confusion

---

# ♻️ Recursion

> A function calling itself.

### ✅ Example

```java
static void test() {
    test();
}
```

### 📌 Used In

- Factorial
- Trees
- Backtracking
- DSA Problems

### ⚠️ Important

Recursion must have a stopping condition.

---

# 📚 Call Stack

> Call stack is a memory structure used to store function calls.

### 📌 Flow

```text
main()
first()
second()
third()
```

### 📌 Rule

```text
LIFO → Last In First Out
```

### ⚙️ Working

- Function added when called
- Removed after execution completes

### 📌 Used In

- Recursion
- Memory management
- Debugging

---

# ⚠️ StackOverflowError

Occurs when:

- Function calls never stop
- Stack memory becomes full

Mostly caused by infinite recursion.

### ✅ Example

```java
static void loop() {
    loop();
}
```

---

# 📍 Local Variable

> A variable declared inside a function.

### ✅ Example

```java
static void test() {
    int x = 10;
}
```

`x` only works inside `test()`.

### 📌 Important Points

- Accessible only inside that function
- Destroyed after function execution ends

---

# 🔐 Static Method

> Static methods belong to class.

### ✅ Example

```java
static void hello() {

}
```

### ✅ Calling

```java
hello();
```

### 📌 Features

- Can be called without object
- Uses less memory
- Commonly used in utility methods

---

# 👤 Non-Static Method

> Non-static methods belong to objects.

### ✅ Example

```java
void hello() {

}
```

### ✅ Calling

```java
Main obj = new Main();
obj.hello();
```

### 📌 Features

- Requires object creation
- Can access object data directly

---

# 📦 Built-in Methods

> Methods already provided by Java.

### 📌 Examples

- Math methods
- String methods
- Array methods

```java
Math.sqrt(25);
```

```java
str.length();
```

---

# 🧪 Pass by Value

> Java uses pass by value.

### ✅ Meaning

- Copy of variable is passed
- Original value remains unchanged

### ✅ Example

```java
static void change(int x) {
    x = 100;
}
```

---

# 📋 Quick Revision

| Concept | Meaning |
|---|---|
| Function | Reusable code block |
| Parameter | Placeholder variable |
| Argument | Actual value |
| Return Type | Sends value back |
| Void | Returns nothing |
| Overloading | Same name, different parameters |
| Recursion | Function calls itself |
| Call Stack | Stores function calls |
| Static Method | Called without object |
| Local Variable | Variable inside function |

---

# ⭐ Important Tips

- Keep functions small and focused
- Use meaningful function names
- Avoid repeated code
- Practice recursion slowly
- Understand parameters clearly
- Focus on logic before syntax

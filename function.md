## Function 
> A function (method in Java) is a resuble bolck of code that preform a specific task.
---

# Basic Function Syntax
```
returnType function()
//code
{
```

### Example
```
static void hello(){
  System.out.println("Hello");
}
```
# function Calling
```
hello();
```
> Function only runs when it is called.

---

# function with Parameters
```
static void greet(String name){
  System.out.println("hello " + name);
}
```
### Calling
```
greet("Rahul");
```
---

# Return Type Function 

```
static int add(int a, int b){
  return a + b;
}
```

### Calling
```
int sum = add(2, 3);
System.out.println(sum);
```

---

# Parameters

Parameters are variables written inside the function definition.

### Important Points
- Used to receive input
- Work like placeholders
- Defined during function creation


#  Arguments

Arguments are actual values passed during function calling.

### Important Points
- Real data sent to function
- Passed while calling method
- Stored inside parameters



### Example of Parameter and Argument

```java
static void greet(String name)
```

- `name` → parameter

```java
greet("Rahul");
```

- `"Rahul"` → argument

---


















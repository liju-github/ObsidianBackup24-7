**Recursion** is a programming technique where a function calls itself to solve smaller instances of the same problem. This process continues until the problem becomes simple enough to solve directly, referred to as the **base case**.

---

### **How Recursion Works**

1. ***Base Case:***  
    The condition where the function stops calling itself. Without this, recursion would go on indefinitely, leading to a **stack overflow**.
    
2. ***Recursive Case:***  
    The condition where the function calls itself with modified input to reduce the problem size, aiming to reach the base case.
    
3. ***Call Stack:***  
    Each recursive call is pushed onto a **call stack**, which stores the function’s parameters, local variables, and return addresses. When the base case is reached, the stack unwinds, resolving the computations step by step.
    

---

### **Execution Flow of Recursion**

1. **Recursive Call:**
    - The function calls itself repeatedly, breaking the problem into smaller subproblems.
2. **Base Case Reached:**
    - Once the simplest version of the problem (base case) is reached, the recursion stops.
3. **Stack Unwinding:**
    - Results are returned to previous function calls, step by step, until the final result is computed.

---

### **Example: Factorial Calculation**


**Factorial Formula:**  
n!=n×(n−1)×(n−2)⋯×1n! = n \times (n-1) \times (n-2) \dots \times 1  
For example:  
5!=5×4×3×2×1=1205! = 5 \times 4 \times 3 \times 2 \times 1 = 120

#### Recursive Implementation (Go Code):

```go
func factorial(n int) int {
    if n == 0 { // Base Case
        return 1
    }
    return n * factorial(n-1) // Recursive Case
}
```

---

### **Execution Visualization**

#### _Example: `factorial(3)`_

1. **Initial Call:**  
    factorial(3)=3×factorial(2)factorial(3) = 3 \times factorial(2)
2. **Second Call:**  
    factorial(2)=2×factorial(1)factorial(2) = 2 \times factorial(1)
3. **Third Call:**  
    factorial(1)=1×factorial(0)factorial(1) = 1 \times factorial(0)
4. **Base Case Reached:**  
    factorial(0)=1factorial(0) = 1
5. **Stack Unwinding:**
    - factorial(1)=1×1=1factorial(1) = 1 \times 1 = 1
    - factorial(2)=2×1=2factorial(2) = 2 \times 1 = 2
    - factorial(3)=3×2=6factorial(3) = 3 \times 2 = 6

---

### **Call Stack Representation**

At each step, the call stack grows:

|Function Call|Returned Value|
|---|---|
|`factorial(3)`|Waiting|
|`factorial(2)`|Waiting|
|`factorial(1)`|Waiting|
|`factorial(0)`|1|

When unwinding, values are returned step by step:

|Function Call|Returned Value|
|---|---|
|`factorial(3)`|6|
|`factorial(2)`|2|
|`factorial(1)`|1|

---

### **Diagram Representation**

#### _**Recursive Call Flow:**_

```
factorial(3)  
  ↳ factorial(2)  
      ↳ factorial(1)  
          ↳ factorial(0) → 1 (Base Case)
```

#### _Stack Unwinding:_

```
factorial(0) → 1  
factorial(1) → 1 × 1 = 1  
factorial(2) → 2 × 1 = 2  
factorial(3) → 3 × 2 = 6  
```

---

### **Example: Fibonacci Series**

**Fibonacci Formula:**  
F(0)=0, F(1)=1F(0) = 0, \, F(1) = 1  
F(n)=F(n−1)+F(n−2)for n≥2F(n) = F(n-1) + F(n-2) \quad \text{for } n \geq 2

#### Recursive Implementation (Go Code):

```go
func fibonacci(n int) int {
    if n == 0 { // Base Case 1
        return 0
    }
    if n == 1 { // Base Case 2
        return 1
    }
    return fibonacci(n-1) + fibonacci(n-2) // Recursive Case
}
```

---

### **Execution Visualization**

#### _Example: `fibonacci(4)`_

1. **Initial Call:**  
    fibonacci(4)=fibonacci(3)+fibonacci(2)fibonacci(4) = fibonacci(3) + fibonacci(2)
2. **Second Call:**  
    fibonacci(3)=fibonacci(2)+fibonacci(1)fibonacci(3) = fibonacci(2) + fibonacci(1)
3. **Third Call:**  
    fibonacci(2)=fibonacci(1)+fibonacci(0)fibonacci(2) = fibonacci(1) + fibonacci(0)

**Base Cases Reached:**

- fibonacci(0)=0fibonacci(0) = 0
- fibonacci(1)=1fibonacci(1) = 1

4. **Stack Unwinding:**
    - fibonacci(2)=1+0=1fibonacci(2) = 1 + 0 = 1
    - fibonacci(3)=1+1=2fibonacci(3) = 1 + 1 = 2
    - fibonacci(4)=2+1=3fibonacci(4) = 2 + 1 = 3

---

### **Call Stack Representation**

|Function Call|Returned Value|
|---|---|
|`fibonacci(4)`|Waiting|
|`fibonacci(3)`|Waiting|
|`fibonacci(2)`|Waiting|
|`fibonacci(1)`|1|
|`fibonacci(0)`|0|

When unwinding:

|Function Call|Returned Value|
|---|---|
|`fibonacci(4)`|3|
|`fibonacci(3)`|2|
|`fibonacci(2)`|1|

---

### **Diagram Representation**

#### _**Recursive Call Flow:**_

```
fibonacci(4)  
  ↳ fibonacci(3)  
      ↳ fibonacci(2)  
          ↳ fibonacci(1) → 1  
          ↳ fibonacci(0) → 0  
      ↳ fibonacci(1) → 1  
  ↳ fibonacci(2)  
      ↳ fibonacci(1) → 1  
      ↳ fibonacci(0) → 0  
```

#### _Stack Unwinding:_

```
fibonacci(0) → 0  
fibonacci(1) → 1  
fibonacci(2) → 1  
fibonacci(3) → 2  
fibonacci(4) → 3  
```

---

### **Example: Sum of Natural Numbers**

**Sum Formula:**  
S(n)=1+2+3+⋯+n=n+S(n−1)S(n) = 1 + 2 + 3 + \dots + n = n + S(n-1)  
S(0)=0S(0) = 0

#### Recursive Implementation (Go Code):

```go
func sumOfNaturalNumbers(n int) int {
    if n == 0 { // Base Case
        return 0
    }
    return n + sumOfNaturalNumbers(n-1) // Recursive Case
}
```

---

### **Execution Visualization**

#### _Example: `sumOfNaturalNumbers(4)`_

1. **Initial Call:**  
    S(4)=4+S(3)S(4) = 4 + S(3)
2. **Second Call:**  
    S(3)=3+S(2)S(3) = 3 + S(2)
3. **Third Call:**  
    S(2)=2+S(1)S(2) = 2 + S(1)
4. **Fourth Call:**  
    S(1)=1+S(0)S(1) = 1 + S(0)
5. **Base Case Reached:**  
    S(0)=0S(0) = 0

**Stack Unwinding:**

- S(1)=1S(1) = 1
- S(2)=2+1=3S(2) = 2 + 1 = 3
- S(3)=3+3=6S(3) = 3 + 3 = 6
- S(4)=4+6=10S(4) = 4 + 6 = 10

---

### **Call Stack Representation**

|Function Call|Returned Value|
|---|---|
|`sumOfNaturalNumbers(4)`|Waiting|
|`sumOfNaturalNumbers(3)`|Waiting|
|`sumOfNaturalNumbers(2)`|Waiting|
|`sumOfNaturalNumbers(1)`|Waiting|
|`sumOfNaturalNumbers(0)`|0|

When unwinding:

|Function Call|Returned Value|
|---|---|
|`sumOfNaturalNumbers(4)`|10|
|`sumOfNaturalNumbers(3)`|6|
|`sumOfNaturalNumbers(2)`|3|

---

### **Diagram Representation**

#### _**Recursive Call Flow:**_

```
S(4)  
  ↳ S(3)  
      ↳ S(2)  
          ↳ S(1)  
              ↳ S(0) → 0  
```

#### _Stack Unwinding:_

```
S(0) → 0  
S(1) → 1 + 0 = 1  
S(2) → 2 + 1 = 3  
S(3) → 3 + 3 = 6  
S(4) → 4 + 6 = 10  
```

---```

---

### **Key Points to Remember:**

1. **Base Case:** Always define one to prevent infinite recursion.
2. **Recursive Case:** Simplify the problem towards the base case.
3. **Call Stack:** Understand its role and how recursion utilizes it.
4. **Efficiency:** Recursion can be inefficient for large problems; iterative solutions or optimizations like **memoization** may be better.

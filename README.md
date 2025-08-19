# Pointer Operations in C++

## Overview
Pointers are one of the most important features of C++.  
A **pointer** is a variable that stores the memory address of another variable.  
Using pointers, we can directly access and manipulate memory, perform dynamic memory allocation, and optimize performance.

---

## Theory

### Declaration and Initialization
- Syntax:  
  ```cpp
  int *ptr;       // declaration
  int x = 10;
  ptr = &x;       // ptr stores the address of x
  ```

* is used for dereferencing (accessing the value at the address).

& is the address-of operator (gives the memory address of a variable).


# Accessing Values Using Pointers in C++

## Overview
Pointers not only store the memory address of a variable but also allow us to **access and manipulate the actual value** stored at that address.  
This is done using the **dereference operator (`*`)**.

---

## Theory
- The **address-of operator (`&`)** is used to get the memory address of a variable.  
- The **dereference operator (`*`)** is used to access or modify the value stored at the memory address.

Example:
```cpp
int x = 10;
int *ptr = &x;   // ptr stores the address of x
cout << *ptr;    // outputs 10 (value of x)
```

Here:

&x → gives the address of variable x.

*ptr → accesses the value stored at that address.


# Pointer Arithmetic in C++

---

## Rules of Pointer Arithmetic
1. **Increment (ptr++)**
   - Moves the pointer to the next memory location of its data type.
   - For example, if `ptr` is an `int*` and each int is 4 bytes, `ptr++` increases the address by 4.

2. **Decrement (ptr--)**
   - Moves the pointer to the previous memory location of its data type.

3. **Addition (ptr + n)**
   - Moves the pointer forward by `n` memory locations.

4. **Subtraction (ptr - n)**
   - Moves the pointer backward by `n` memory locations.

---

# Null Pointers in C++

## Overview
A **null pointer** is a special type of pointer that does not point to any valid memory location.  
It is often used to represent the **absence of an object** or to indicate that a pointer has not yet been assigned a valid address.

---

## Characteristics of Null Pointers
- A null pointer **does not store a valid memory address**.
- It is commonly used for **error handling** and **safety checks** in programs.
- In C++, the constant `NULL` or the keyword `nullptr` can be assigned to a pointer.
- Accessing or dereferencing a null pointer leads to **undefined behavior** (usually program crash).

---

## Declaring a Null Pointer
```cpp
int *ptr = NULL;     // Old C-style null pointer
int *ptr2 = nullptr; // Modern C++11 and later (preferred)
```

# Pointers to Pointers in C++

## Overview
A **pointer to a pointer** is a type of pointer that stores the address of another pointer.  
This allows multiple levels of indirection and is useful when dealing with **dynamic memory, arrays, and function arguments**.

---

## Syntax
```cpp
datatype **ptr;
```

The first * indicates that ptr is a pointer.

The second * indicates that it points to another pointer.

# Dynamic Memory Allocation in C++

## Overview
Dynamic Memory Allocation allows programs to request memory at **runtime** instead of compile-time.  
In C++, this is achieved using the `new` and `delete` operators.  
It provides flexibility to create variables, arrays, and objects when their size is not known in advance.

---

## Why Dynamic Memory Allocation?
- Useful when the required memory size cannot be determined before execution.
- Prevents memory wastage by allocating only as much as needed.
- Commonly used in:
  - Arrays with variable sizes
  - Linked lists, trees, and graphs
  - Real-time memory management

---

## Syntax
```cpp
datatype* pointer = new datatype;      // allocate single variable
datatype* array = new datatype[size];  // allocate array
delete pointer;                        // free single variable
delete[] array;                        // free array
```

# Function Pointers in C++

##  Overview
A **function pointer** is a pointer that stores the **address of a function**.  
Using function pointers, we can call functions indirectly, pass functions as arguments, and implement callback mechanisms.

---

##  Why Use Function Pointers?
- To pass a function as an argument to another function.
- To create **callback functions**.
- To implement **tables of functions** (useful in menu-driven programs).
- Provides flexibility in **runtime function selection**.

---

##  Syntax
```cpp
returnType (*pointerName)(parameterTypes) = functionName;
returnType → the return type of the function.
```

parameterTypes → the list of parameters the function accepts.

functionName → the function whose address is stored.

# 1. Swap Function using Call by Value

##  Theory
This program demonstrates the concept of **call by value** in C++.  
- When a function is called by value, copies of the actual arguments are passed to the function.  
- In this program, the function `swap(int x, int y)` swaps only the local copies of `x` and `y`.  
- The original variables `a` and `b` in `main()` remain unchanged.  

Thus, **call by value does not affect the actual variables**.

---

##  Algorithm
1. Start the program.  
2. Define a function `swap(int x, int y)`:
   - Store `x` in a temporary variable `temp`.  
   - Assign `y` to `x`.  
   - Assign `temp` to `y`.  
3. In the `main()` function:
   - Declare two integers `a = 5` and `b = 10`.  
   - Call `swap(a, b)`.  
   - Since the function is called by value, only copies are swapped.  
4. Print the values of `a` and `b`.  
5. End the program.  

---

# 2. Swap Function using Call by Reference

##  Theory
This program demonstrates the concept of **call by reference** in C++.  
- In call by reference, the function receives the **actual memory addresses** of the variables.  
- Any changes made inside the function directly affect the original variables.  
- Here, the `swap(int &x, int &y)` function swaps the actual values of `a` and `b`.  

Thus, **the values of `a` and `b` are exchanged successfully**.

---

##  Algorithm
1. Start the program.  
2. Define a function `swap(int &x, int &y)`:
   - Store `x` in a temporary variable `temp`.  
   - Assign `y` to `x`.  
   - Assign `temp` to `y`.  
3. In the `main()` function:
   - Declare two integers `a = 5` and `b = 10`.  
   - Call `swap(a, b)`.  
   - Since the function is called by reference, the actual variables are swapped.  
4. Print the new values of `a` and `b`.  
5. End the program.  

---

# 3. Swap Function using Pointers

##  Theory
This program demonstrates the concept of **call by pointer** in C++.  
- In this method, the function receives the **addresses of the variables** using pointers.  
- The dereference operator (`*`) is used to access and modify the actual values stored at those addresses.  
- As a result, the swap is performed directly on the original variables.

Thus, the values of `a` and `b` are successfully exchanged.

---

##  Algorithm
1. Start the program.  
2. Define a function `swap(int *x, int *y)`:
   - Store the value at `*x` in a temporary variable `temp`.  
   - Assign the value at `*y` to `*x`.  
   - Assign `temp` to `*y`.  
3. In the `main()` function:  
   - Declare two integers `a = 5` and `b = 10`.  
   - Display their values **before swapping**.  
   - Call `swap(&a, &b)` and pass the addresses of `a` and `b`.  
   - Display the values of `a` and `b` **after swapping**.  
4. End the program.  

---

# 4. Modify Array using Function with Array and Reference Parameter

##  Theory
This program demonstrates:
- **Passing arrays to functions:** In C++, when an array is passed to a function, its base address is passed. This allows the function to modify the original array directly.  
- **Pass by reference (`&`):** The variable `num` is passed by reference, so any change to it inside the function affects the original variable.  
- In this program, the array is updated with consecutive values starting from `num`, and at the same time, the value of `num` is incremented.

---

##  Algorithm
1. Start the program.  
2. Initialize an array `a[5] = {10, 20, 30, 40, 50}` and declare an integer `num`.  
3. Take input from the user for `num`.  
4. Display the array **before update**.  
5. Call the function `modifiedArray(a, num)`:
   - Traverse through the array using a loop.  
   - Assign the current value of `num` to each element of the array.  
   - Increment `num` after each assignment.  
6. Display the array **after update**.  
7. End the program.  

---

# 5. Salary Increment Eligibility Program

##  Theory
This program checks if an employee is eligible for a salary increment based on the following **four conditions**:
1. The employee has at least one research project.  
2. The employee has at least one research publication.  
3. The profit generated is greater than ₹1,00,000.  
4. There are new projects in the pipeline.  

- If **at least three conditions** are satisfied, the salary is **incremented by 20%**.  
- Otherwise, the salary remains the same.  

This program demonstrates:
- Use of **functions** with multiple parameters.  
- Conditional statements (`if`) to evaluate rules.  
- Passing values and returning updated results.  

---

##  Algorithm
1. Start the program.  
2. Input the following details:  
   - Number of research projects.  
   - Number of research publications.  
   - Profit.  
   - Number of new projects in pipeline.  
   - Current salary.  
3. Call the function `checkEligibilityAndIncrement()`.  
   - Initialize `conditionsSatisfied = 0`.  
   - Check each of the four conditions:  
     - If satisfied, increment `conditionsSatisfied`.  
   - If `conditionsSatisfied >= 3`:  
     - Increase salary by 20%.  
   - Otherwise, keep the salary unchanged.  
   - Display updated salary or message.  
4. Return the final salary to the main program.  
5. Display the final salary.  
6. End.  

---

# 6.Salary Increment Eligibility Program (Pass by Reference)

##  Theory
This program determines whether an employee is eligible for a **20% salary increment** based on specific conditions. The program uses **pass by reference** (`double& salary`) to directly modify the salary inside the function.

### Conditions Checked:
1. At least one research project.  
2. At least one research publication.  
3. Profit greater than ₹1,00,000.  
4. At least one new project in the pipeline.  

- If **3 or more conditions** are satisfied, salary is incremented by **20%**.  
- Otherwise, salary remains unchanged.  

---

##  Algorithm
1. Start.  
2. Input values:  
   - Number of research projects.  
   - Number of research publications.  
   - Profit.  
   - Number of new projects in pipeline.  
   - Current salary.  
3. Call function `checkEligibilityAndIncrement(salary, researchProjects, researchPublications, profit, newProjectsInPipeline)`.  
   - Initialize counter `conditionsSatisfied = 0`.  
   - Check each condition and increment the counter if true.  
   - If `conditionsSatisfied >= 3`:  
     - Update salary by `salary * 1.2`.  
     - Print incremented salary.  
   - Else:  
     - Print that conditions are not met.  
4. Back in `main()`, display the final salary.  
5. End.  

---

#  Conclusion: Pointer Operations in C++

Pointer operations are fundamental in C++ as they provide direct access and manipulation of memory.  
By using pointers, programmers can:

- **Access values** stored in memory through the dereference (`*`) operator.  
- **Navigate memory** using pointer arithmetic (increment, decrement, addition, subtraction).  
- **Ensure safety** with null pointers, preventing accidental access to invalid memory.  
- **Work with multiple levels of indirection** through pointers to pointers.  
- **Manage memory efficiently** using dynamic allocation (`new` and `delete`).  
- **Enable flexibility** with function pointers, allowing dynamic function execution and callbacks.  

---

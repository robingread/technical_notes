tags: #cpp

# Pointers
A pointer in C++ is a variable that holds the *address* of another variable in memory.

```c++
int x = 1;
int *ip = &x;
```

In doing this, the variable `ip` now holds the address of the variable `x`.

De-referencing
```c++
int y;
y = *ip;
```

The variable `y` now holds the value stored at the address that `ip` points to, which should be `1`.

# References
- Once assigned, you cannot change the value of the reference.
- Think of a reference as an *alias* for another variable.
- References are not variables themselves.

```c++
int x = 0;
int y = 1;
int &z = x;

// z = 0;
z = 10;
// x = 10 and z = 10
x = 20;
// x = 20 and z = 20
```

> [!tip]
> A good rule of thumb is to create references as `const` so that you reduce the likelihood that you accidentally change another value unknowingly.
> 
> ```c++
> int x = 0;
> int &z = x;
> z = 42;   // This also changes x, but may not be so obvious!
> ```




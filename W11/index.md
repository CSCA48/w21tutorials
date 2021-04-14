---
title: Week 10 Tutorial
sidebar: 11
sidebar-title: Week 10
---


<p align="center"> <a href="https://www.youtube.com/watch?v=dQw4w9WgXcQ"> Additional A3 Walkthrough </a> </p>

---

# How to write a recursive algorithm

---
Assume you have a problem of some type:

1. Break down the problem into a smaller (easier) problem(s) of the same type
2. Recursively solve that smaller problem(s)
3. Use the solution of the 'easier' problem to solve the original problem 

---

# Recursion Examples

---

## Find the Largest number in an array

We have solved this problem in a non-recursive way multiple times before. There are multiple ways we can solve it using recursion too. Sometimes using a helper can be useful, especially if you need to add more parameters to a function.

### Exercise:

Implement the largest function using loops, and once you find a working solution, implement it using recursion.

```c
#include <stdio.h>

int main() {
    int array[] = {33, 12, 45, 9, 24};
    int n = 5;

    // Implement the large function!
    int largest_element = largest(array, n);

    printf("The largest number of the list is: %d\n", largest_element);
}
```
---

## Find if a string is a palindrome or not

A palindrome is a word or phrase that reads the same backward as forward. Implement a recursive function to find if a word is a palindrome or not.

### Exercise:

Implement the isPalindrome function using loops, and once you find a working solution, implement it using recursion.

```c
#include <stdio.h>
#include <string.h>
// Not necessary!
// #include <stdbool.h>

#define MAX_LENGTH 1024

int main() {
    char word [MAX_LENGTH] = "racecar";

    // Implement the isPalindrome function!
    if (isPalindrome(word)){
        printf("The word %s is a palindrome", word);
    } else{
        printf("The word %s is not a palindrome", word);
    }
}
```
---

## Find the factorial of the number

A factorial is when you multiply a number by all the numbers below it. Implement a recursive function to calculate the factorial of a number.

### Exercise:

Implement the factorial function using loops, and once you find a working solution, implement it using recursion.

```c
#include <stdio.h>
#include <string.h>

int main() {
  int number = 6;
  int result = 0;

  // Implement the factorial function!
  result = factorial(number);

  printf("Number = %d\n", number);
  printf("Factorial = %d\n", result);  
  
  return 0;
}
```

---
title: Week 11 Tutorial
sidebar: 12
sidebar-title: Week 11
---

# More Recursion Examples !

---
## Find the power of a number

Create a function to find the power of a number using recursion. Try it yourself first and compare your solution with your classmates :)

```c
#include<stdio.h>

int main(){
   int base, power, result;
   printf("Enter the base and power: ");
   scanf("%d %d",&base, &power);
   // base ^ power
   result = pow_recursive(base, power);
   printf("%d to the power of %d is %d\n", base, power, result);
   return 0;
}
```
---

## Can you find the right password?

Let's say there is a _secret_ function to validate a password. 

```c
#include <stdio.h>
#include <string.h>

/**
 * Assumes `password` is exactly 6 characters long.
 * `password` only contains lowercase letters a-z
 *
 * Returns 1 if password is correct, 0 otherwise
 */
int check_password(char *password) {
  int hash[7] = {2876, 2832, 3196, 2908, 2712, 2988};
  for (int i = 0; i < 6; i++)
    if ((password[i] ^ (password[5 - i] * 29)) != hash[i])
      return 0;
  return 1;
}
```

Implement a function that returns the secret password. That is, you want to create a function that will use ```check_password``` to find the 6-char secret password.

*Hint:* Try solving it using loops first!

---
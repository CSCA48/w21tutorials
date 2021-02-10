---
title: Week 4 Tutorial
sidebar: 5
sidebar-title: Week 4
---


---


<p align="center"> <a href="https://www.youtube.com/playlist?list=PLlTc---1rMDXdCiTq-5gmNbjEMgNTCXrO"> Recorded videos (courtesy of Willy) </a> </p>

---

# Compound Data Types (CDTs)

Compound Data Types (CDTs) are useful to represent information about entites that have multiple properties. For instance, if you want to represent a student record which needs to have different fields like name, student number, age, etc.

We want to keep all these information together and bundle it up in a single package, instead of having multiple variables floating around.

---

## How do we define CDTs?

---

```c
typedef struct struct_name {
    int field1;
    char field2[1024];
    // More fields
} new_type_name;
```

In the first line, we start declaring a new compound data type, the composite name will be ```struct_name```. Inside the declaration, we will list all the components of the CDT, also called as fields, which can be from any data type. Once we are done, we will name our new compound data type ```new_type_name```.

Let's refer back to our example about a student record.

```c
typedef struct Uoft_student {
    char name[1024];
    int studentNumber;
    int age;
    struct UofT_student *teammate;
    // And we can keep going...
} Student;
```
---

## How do we use CDTs?

---

Once we have defined our new data type, we can do everything that we would do with another regular data type: declare it, acccess it, pass/return from a function.

To **declare** a variable:

```c
// Generalized
new_type_name v;
// In our example
Student angela;
```

To **access** a field:

```c
// Generalized
v.field1 = 3;
// In our example
strcpy(angela.name, "Angela Zavaleta");
```

To **pass** or **return** them from a function:

```c
// Generalized
new_type_name random_function(new_type_name v, int value){
    // Implementation
}
// In our example
// We want to duplicate the Student record but with a different id
Student duplicate_student(Student s, int new_id){
    // Implementation
}
```

---

## How does it look in memory?

---

A variable of a CDT will get one locker box only! It will divide that box into smaller sections to store the data of its fields. When we pass or return a CDT, a copy will be created.

Similar to other variables, we can use them with pointers!

```c
// We can initialize the pointers exactly as we saw last week
new_type_name v;
new_type_name *vp;
vp = &v;
// We can use an arrow to get the field!
vp->field1 = 9;
```

Let's show this using our student example:

```c
Student willy;
Student *willy_pointer;
willy_pointer = &willy;
strcpy(willy_pointer->name, "Willy Song");
willy_pointer->teammate = &angela;

Student charles;
Student *charles_pointer;
charles_pointer = &charles;
strcpy(charles_pointer->name, "Charles Xu");
angela_pointer->teammate = &charles;
```

---

## Exercise

---

Use a CDT to store an array of 3 restaurants reviews. Each review should contain the restaurant name, the reviewer's name and the review score.

```c
#include <stdio.h>

______ ______ Restaurant_Review {
    // TODO
} Review;

int main() {
    _______ reviews[3];

    // Declare the reviews and store them in the array


    // Now let's print the reviews to check they were done properly
    for (int i = 0; i < 3; i++){
        printf("Review %d:\n", i);
        printf("Name of Restaurant: %s\n", _______);
        printf("Name of Reviewer: %s\n", _______);
        printf("Score %d:\n", _______);
    }
}
```

---

# Assignment 1 !

Assignment 1 was posted this week and as we always say, it's important for you to start it early enough so we can answer any questions ahead of time. Make sure you read the handout and the starter code. However, it is okay if you do not fully undertand what you need to do as you are just learning some of the material. A1 makes you implement a program that can read instructions and draw out images (inspired by [Logo](https://en.wikipedia.org/wiki/Logo_(programming_language))). 

The general idea is that you have a turtle that starts off at the top-left of the screen, and follows all the instructions given to move around, drawing a line along the path it takes. Let's take a simple example:

```
penup
forward 100
right
forward 100
pendown
forward 300
left
forward 300
left
forward 300
left
forward 300
left

```
<details> 
  <summary>What do you think this draws onto the screen? </summary>
   - A square 300 x 300 where the top left corner is located at 100, 100.
</details>


Of course, we're also programmers so we hate repetitive instructions! In the assignment you'll also implement support for a loop structure that lets you do something like:

```
penup
forward 100
right
forward 100
pendown
loop 4
  forward 300
  left
```

Once you are done the assignment, don't forget to test <a href="https://github.com/CSCA48/w21tutorials/raw/master/W5/angelas-surprise.txt" download>this file</a> which has the turtle instructions to Angela's favorite drawing 😃 (Right click, Save link as...). Give it a few seconds, its a LOT of instructions.

If you want to create fun instructions for your pictures, you can generate them using our tool <a href="https://csca48.github.io/w21tutorials/img2turtle/">img2turtle</a>.

---

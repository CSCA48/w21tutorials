---
title: Week 6 Tutorial
sidebar: 7
sidebar-title: Week 6
---

---


<p align="center"> <a href="https://youtu.be/94Y_a6DcrL8"> Last week's videos (Thanks Willy!) </a> </p>

---

# Linked Lists Recap

Linked Lists are one of the simplest implementations of the Lists ADT (Abstract Data Type). It is formed by a set of nodes, that are arranged in such a way that each node *points to* the next node. Each node will contain a value and a pointer to the next node.

---

## How do we define a Linked List?

---

Let's define a generic node:

```c
typedef struct list_node {
   int val;                 // Data stored
   struct list_node *next   // Pointer to the next list of nodes
} node;
```

---

# Exercise: Cupcake delivery

Before attempting each of these exercises, discuss your implementation with your peers and discuss various ways of solving the questions. After solving the questions, there are some extra discussion prompts at the end and a **crunchy** version of the exercise.

Angela found a TikTok recipe of <span style="color:mediumpurple">**purple cupcakes**</span> so she decided to bake some for her A48 TA friends! She will deliver these cupcakes in a first-come first-serve basis. Her plan was to bake 3 cupcakes per TA, but some TAs asked for more...

---

## Task 1: Cupcake Delivery list

Define the the structs ```Delivery``` and ```Delivery_List_Node```. The ```Delivery``` struct represents the CDT that contains the name of the recepient (TA) and the number of cupcakes they want. The ```Delivery_List_Node``` struct contains a ```Delivery``` and a pointer to the next ```Delivery_List_Node```.

---

## Task 2: New Delivery

Create a function ```new_Delivery_Node``` that will initialize a new ```Delivery_List_Node``` given a name and the number of cupcakes. 

---

## Task 3: Inserting Deliveries

Create a function ```insert_delivery``` to insert the deliveries from TAs into the ```Delivery_List_Node``` called ```cupcake_delivery_list```. Remember the delivery is first-come first-serve.

---

## Task 3: Inserting Priority Deliveries

Brian, Paco and Abbas found out that Angela is giving cupcakes to the other TAs and now they want to try some too. However, they want their orders before than everyone else!

Create a function ```insert_priority_delivery``` to insert special deliveries to the beginning of the ```Delivery_List_Node``` called ```cupcake_delivery_list```.

---

This is an example of how you would call the functions from main with some discussion prompts about the implementation.

```c
int main(){
    // Task 1 and 2:
    Delivery_List_Node *cupcake_delivery_list = NULL;
    // -> Why am I not allocating memory in the previous line?
    cupcake_delivery_list = new_Delivery_Node("Mustafa", 12);

    // Task 3:
    insert_delivery(cupcake_delivery_list, "Willy", 36);
    insert_delivery(cupcake_delivery_list, "Charles", 6);
    insert_delivery(cupcake_delivery_list, "Maduvan", 6);
    insert_delivery(cupcake_delivery_list, "Andrew", 1);
    insert_delivery(cupcake_delivery_list, "Kasra", 12);
    insert_delivery(cupcake_delivery_list, "Yara", 3);
    insert_delivery(cupcake_delivery_list, "Clara", 3);
    insert_delivery(cupcake_delivery_list, "Katrina", 6);
    insert_delivery(cupcake_delivery_list, "Benjamin", 12);
    insert_delivery(cupcake_delivery_list, "River", 3);
    insert_delivery(cupcake_delivery_list, "Sam", 3);
    insert_delivery(cupcake_delivery_list, "Keshavaa", 3);
    insert_delivery(cupcake_delivery_list, "Derick", 3);
    insert_delivery(cupcake_delivery_list, "Alon", 3);

    // -> This insert function is not returning anything, do you
    // think that's a good idea?

    // Task 4:
    cupcake_delivery_list = insert_priority_delivery(cupcake_delivery_list, "Paco", 12);
    cupcake_delivery_list = insert_priority_delivery(cupcake_delivery_list, "Abbas", 12);
    cupcake_delivery_list = insert_priority_delivery(cupcake_delivery_list, "Brian", 36);

    // -> This new insert function is returning a delivery list pointer,
    // is it better from our previous implementation? could you implement
    // this function without returning a pointer?

    // Print to test!
    Delivery_List_Node *currentNode = cupcake_delivery_list;

    for(int i = 0; i< 18; i++){
        printf("Order #%d: %s --- %d cupcake(s)\n", i+1,currentNode->order.name, currentNode->order.numOfCupcakes);
        currentNode = currentNode->next;
    }

    return 0;
}
```
---

## Crunchy version

The first-come first-serve order might not be the best in this scenario because some people may live close to each other and Angela is scared of taking the highway so we need to reduce the amount of driving.

Re-implement all the previous tasks adding a new field for ```Delivery``` called distance, which represents the distance from Angela's house to the receipient's. For Task 3, we want to insert the orders in order of distance (closer ones to Angela's should be delivered first). For Task 4, we want to still insert the orders at the front, so you might want to update their distance to -1.

*Note: I know that technically the distances might be in opposite directions, but this is just an exercise so pretend distance is an accurate way of sorting :)*

---
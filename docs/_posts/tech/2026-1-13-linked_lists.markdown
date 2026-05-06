---
layout: post
title:  "Building Linked Lists in C From Scratch with an Interactive Colab"
date:   2026-1-13 06:25:17 -0800
categories: jekyll update technology
---
<a target="_blank" href="https://colab.research.google.com/github/jordan-hay/jordan-hay.github.io/blob/main/docs/assets/Building_Linked_Lists_in_C_From_Scratch_with_an_Interactive_Colab.ipynb
">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/>
</a>

# Introduction

If pointers in C feel abstract, linked lists are where they finally become real.

A linked list is one of the first data structures where you stop thinking about variables as isolated boxes and start thinking about memory as connected pieces.

This walkthrough builds linked lists step-by-step — from the smallest C program all the way to traversing and joining lists — using simple examples.

---

# 1. The Smallest Possible C Program

Everything starts with a tiny executable:

```c
#include <stdio.h>

int main() {
    printf("hello from C\n");
    return 0;
}
```

Key ideas:

- `main()` is the entry point
    
- `printf()` prints text
    
- `return 0` means success
    

Compile and run:

```bash
gcc main.c -o main
./main
```

---

# 2. Creating a Struct

A linked list node is just a struct with data and a pointer.

Start simple:

```c
struct point {
    int x;
    int y;
};
```

Now you can create variables that group multiple fields together:

```c
struct point p;

p.x = 3;
p.y = 4;
```

Think of structs as custom types.

---

# 3. Using typedef

Typing `struct point` repeatedly gets annoying.

So we use:

```c
typedef struct point {
    int x;
    int y;
} point;
```

Now you can write:

```c
point p;
```

instead of:

```c
struct point p;
```

Cleaner and more readable.

---

# 4. Pointers to Structs and the `->` Operator

Pointers become much easier once they’re attached to structs.

```c
point *ptr = &p;
```

Access fields with:

```c
ptr->x = 7;
ptr->y = 9;
```

This is shorthand for:

```c
(*ptr).x
```

The arrow operator is everywhere in linked lists.

---

# 5. Dynamic Memory with malloc

Now memory moves from the stack to the heap.

```c
point *p = malloc(sizeof(point));
```

This allocates memory while the program is running.

Then:

```c
p->x = 1;
p->y = 2;
```

And finally:

```c
free(p);
```

Rule:

- `malloc` allocates memory
    
- `free` releases memory
    

Forget `free`, and memory leaks.

---

# 6. Your First Linked List Node

Now combine everything:

```c
typedef struct ll_text {
    char *text;
    struct ll_text *next;
} ll_text;
```

This is the core linked list idea.

A node contains:

1. Data
    
2. A pointer to another node
    

The magic is:

```c
struct ll_text *next;
```

The struct points to another version of itself.

That creates the chain.

---

# 7. Creating One Node

```c
ll_text *node = malloc(sizeof(ll_text));

node->text = strdup("hello");
node->next = NULL;
```

Important:

```c
node->next = NULL;
```

`NULL` means:

> “This is the end of the list.”

Without it, traversal becomes unsafe.

---

# 8. Connecting Two Nodes

Now create links:

```c
a->next = b;
```

Visual model:

```text
A --> B --> NULL
```

Example:

```c
printf("%s -> %s -> NULL\n", a->text, a->next->text);
```

You are literally walking pointers through memory.

---

# 9. Traversing a Linked List

Traversal is the core operation.

```c
ll_text *curr = a;

while (curr != NULL) {
    printf("%s -> ", curr->text);
    curr = curr->next;
}
```

This loop means:

1. Use current node
    
2. Move to next node
    
3. Stop at `NULL`
    

Visual flow:

```text
curr
 ↓
A -> B -> C -> NULL
```

Then:

```text
A printed
curr moves to B

B printed
curr moves to C

C printed
curr moves to NULL
```

Loop ends.

---

# 10. Writing a Node Constructor

Instead of repeating allocation logic:

```c
ll_text *make_node(char *word) {
    ll_text *node = malloc(sizeof(ll_text));

    node->text = strdup(word);
    node->next = NULL;

    return node;
}
```

Now you can do:

```c
ll_text *node = make_node("hello");
```

This pattern appears constantly in systems programming.

---

# 11. Joining Lists

Here’s an important example:

```c
ll_text *join_lists(ll_text *list1, ll_text *list2) {
    ll_text *newlist = malloc(sizeof(ll_text));

    newlist->text = strdup(list1->text);
    newlist->next = list2;

    return newlist;
}
```

This is subtle.

It only copies:

- ONE node from `list1`
    

Then connects it to `list2`.

It does NOT clone the full first list.

That distinction matters heavily on exams and interviews.

---

# 12. Appending Lists Properly

A more realistic append operation:

```c
while (curr->next != NULL) {
    curr = curr->next;
}

curr->next = list2;
```

This walks to the end of `list1` and attaches `list2`.

Visual result:

```text
A -> B -> X -> NULL
```

This is true list concatenation.

---

# 13. The Most Common Linked List Bug

Forgetting:

```c
node->next = NULL;
```

Uninitialized pointers contain garbage memory.

Traversal may:

- crash
    
- loop forever
    
- corrupt memory
    

Always terminate lists explicitly.

---

# 14. The Mental Model That Makes Linked Lists Click

A linked list node contains:

```text
[data] + [pointer to next node]
```

Traversal always follows the same pattern:

```c
curr = head;

while (curr != NULL) {
    use curr
    curr = curr->next
}
```

Core memory concepts involved:

- structs
    
- pointers
    
- heap allocation
    
- dynamic memory
    
- self-referential types
    

Linked lists are less about the data structure itself and more about learning how memory actually works in C.

Once this clicks, trees, graphs, stacks, queues, and operating systems become much easier to understand.
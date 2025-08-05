# Data Structures and Their Control Flow Inversions: A Tri-Language Perspective

Written by Deepseek R1

In programming, data structures and control flow are two sides of the same coin. By examining three fundamental data primitives—product types, sum types, and fixed points—we can derive their corresponding control flow mechanisms through inversion. We illustrate this relationship with examples in **C**, **Standard ML (SML)**, and **Java**.

---

## 1. Product Types (A **AND** B): Bundle and Destructure

**Data Structure**: A product type bundles multiple values (e.g., a `struct` in C, a tuple in SML, or a class in Java).  
**Control Flow Inversion**: Destructuring the bundle to operate on individual components (e.g., getters/setters, pattern matching).

### Examples:
#### **C** (Structs)
```c
typedef struct { int x; int y; } Point;

// Inversion: Destructure and operate
int sum_point(Point p) {
    return p.x + p.y; // Access fields directly
}
```

#### **SML** (Tuples)
```sml
type Point = int * int;

(* Inversion: Pattern matching *)
fun sum_point (x, y) = x + y;
```

#### **Java** (Classes)
```java
class Point {
    int x, y;
    int sum() { return x + y; } // Method operates on bundled data
}
```

---

## 2. Sum Types (A **OR** B): Branch and Match

**Data Structure**: A sum type represents a choice between alternatives (e.g., a tagged union in C, an SML `datatype`, or Java polymorphism).  
**Control Flow Inversion**: Branching based on the active variant (e.g., `switch`, pattern matching, or the visitor pattern).

### Examples:
#### **C** (Tagged Union)
```c
typedef enum { INT, FLOAT } Tag;
typedef struct {
    Tag tag;
    union { int i; float f; };
} Value;

// Inversion: Switch on tag
void print_value(Value v) {
    switch(v.tag) {
        case INT: printf("%d\n", v.i); break;
        case FLOAT: printf("%f\n", v.f); break;
    }
}
```

#### **SML** (Datatype)
```sml
datatype Value = Int of int | Float of real;

(* Inversion: Pattern matching *)
fun print_value (Int i) = print (Int.toString i)
  | print_value (Float f) = print (Real.toString f);
```

#### **Java** (Visitor Pattern)
```java
interface Value {
    <T> T accept(Visitor<T> visitor);
}

class Int implements Value {
    int i;
    public <T> T accept(Visitor<T> visitor) { return visitor.visit(this); }
}

class Float implements Value {
    float f;
    public <T> T accept(Visitor<T> visitor) { return visitor.visit(this); }
}

interface Visitor<T> {
    T visit(Int i);
    T visit(Float f);
}
```

---

## 3. Fixed Points: Recursion and Iteration

**Data Structure**: A fixed point allows recursive data structures (e.g., linked lists, trees).  
**Control Flow Inversion**: Recursive traversal or iteration (e.g., `map`, loops).

### Examples:
#### **C** (Linked List)
```c
typedef struct Node {
    int data;
    struct Node* next;
} Node;

// Inversion: Apply function recursively
void map(Node* list, int (*f)(int)) {
    if (list == NULL) return;
    list->data = f(list->data);
    map(list->next, f);
}
```

#### **SML** (Recursive List)
```sml
datatype IntList = Nil | Cons of int * IntList;

(* Inversion: Recursive map *)
fun map _ Nil = Nil
  | map f (Cons(x, xs)) = Cons(f x, map f xs);
```

#### **Java** (Iterator)
```java
class Node {
    int data;
    Node next;
    void forEach(Consumer<Integer> f) {
        f.accept(data);
        if (next != null) next.forEach(f);
    }
}
```

---

## Conclusion

By inverting data structure primitives, we derive fundamental control flow mechanisms:
1. **Product types** invert to field access/mutation.  
2. **Sum types** invert to branching logic.  
3. **Fixed points** invert to recursion/iteration.  

This duality underpins how languages manage complexity: data defines *what is*, and control flow defines *what to do*. Whether in low-level C, expressive SML, or object-oriented Java, this relationship remains universal.

# Python Senior Backend Interview Revision

## Goal

Complete Python revision required for:

- Senior Backend Engineer
- Team Lead
- Engineering Manager (technical rounds)

Focus:

- Python Internals
- OOP
- Concurrency
- Design Patterns Foundation
- Interview Questions
- Production-level Understanding

---

# 1. Python Internals

## Memory Management

### Reference Counting

- Every object keeps track of references.
- Object removed when reference count becomes 0.

Example:

```python
a = [1, 2, 3]
b = a
```

Both point to same object.

---

### Garbage Collection

Handles circular references.

```python
a.ref = b
b.ref = a
```

Reference counting alone cannot clean this.

Python GC handles it.

---

### Mutable vs Immutable

Mutable:

- list
- dict
- set

Immutable:

- str
- tuple
- int
- float

---

### Identity vs Equality

```python
is
```

Checks memory identity.

```python
==
```

Checks value equality.

---

### Object Interning

Python reuses objects for:

- Small integers
- Some strings

Example:

```python
a = 100
b = 100
```

May share same memory.

---

## Shallow Copy vs Deep Copy

### Shallow Copy

Copies outer object.

Nested objects shared.

```python
copy.copy()
```

---

### Deep Copy

Copies everything recursively.

```python
copy.deepcopy()
```

---

## Mutable Default Arguments

Bad:

```python
def func(items=[]):
    items.append(1)
```

Shared across calls.

Good:

```python
def func(items=None):
    items = items or []
```

---

# 2. Iterators & Generators

## Iterator Protocol

Methods:

```python
__iter__()
__next__()
```

---

## Generator

Uses:

```python
yield
```

Produces values lazily.

Benefits:

- Memory efficient
- Streaming large datasets

---

## Generator vs List

Generator:

- Lazy evaluation
- Lower memory

List:

- Eager evaluation
- Higher memory

---

# 3. Closures & Decorators

## Closure

Inner function remembers outer variables.

```python
def outer():
    x = 10

    def inner():
        return x
```

---

## Late Binding

Closures capture variables not values.

Common interview topic.

---

## Decorators

Wrap function behavior.

Structure:

```python
decorator
    wrapper
        function
```

Common Uses:

- Logging
- Authentication
- Retry
- Metrics

---

# 4. Context Managers

Methods:

```python
__enter__()
__exit__()
```

Used by:

```python
with
```

Purpose:

- Resource management
- Cleanup

Examples:

- Files
- Database Connections
- Locks

---

# 5. Concurrency

## GIL

Global Interpreter Lock

Allows:

- One thread executes Python bytecode at a time.

Does NOT make code thread-safe.

---

## Threading

Best for:

- I/O Bound Work

Examples:

- APIs
- Network Calls
- Databases

---

## Multiprocessing

Best for:

- CPU Bound Work

Examples:

- Image Processing
- ML Computation
- Heavy Calculations

Advantages:

- Separate processes
- Separate memory
- Bypasses GIL

---

## AsyncIO

Uses:

```python
async
await
```

Single thread.

Cooperative multitasking.

Best for:

- Thousands of concurrent I/O operations.

---

## Race Conditions

Example:

```python
counter += 1
```

Not atomic.

Can lose updates.

---

## Synchronization

### Lock

Single acquisition.

### RLock

Reentrant lock.

Same thread can acquire multiple times.

### Semaphore

Limit concurrent access.

### Queue

Thread-safe communication.

---

# 6. OOP

## Encapsulation

Hide internal data.

Example:

```python
__salary
```

---

## Abstraction

Hide implementation complexity.

Example:

```python
Payment.pay()
```

without exposing internal details.

---

## Inheritance

IS-A relationship.

Example:

```python
Dog -> Animal
```

---

## Composition

HAS-A relationship.

Preferred over inheritance.

Example:

```python
Car has Engine
```

---

## Polymorphism

Same interface.

Different implementations.

Example:

```python
payment.pay()
```

---

## Duck Typing

Python only checks behavior.

Not type hierarchy.

Example:

```python
obj.speak()
```

If it exists, it works.

---

# 7. ABC (Abstract Base Classes)

Used for contracts.

```python
@abstractmethod
```

Forces implementation.

Benefits:

- Prevent incomplete classes.
- Catch bugs early.

---

# 8. MRO

Method Resolution Order.

Determines lookup order.

Example:

```python
D -> B -> C -> A -> object
```

Inspect:

```python
D.mro()
D.__mro__
```

Python uses:

C3 Linearization

---

# 9. Mixins

Reusable behavior.

Example:

```python
LoggerMixin
SerializableMixin
```

Not domain models.

---

# 10. Monkey Patching

Modify runtime behavior.

Example:

```python
Dog.speak = new_speak
```

Danger:

- Hard debugging
- Unexpected side effects

---

# 11. Descriptors

Methods:

```python
__get__()
__set__()
__delete__()
```

Power:

- property
- classmethod
- staticmethod

---

# 12. __slots__

Reduces memory.

Removes:

```python
__dict__
```

Benefits:

- Lower memory usage
- Faster attribute access

Tradeoff:

Cannot create arbitrary attributes.

---

# 13. Dunder Methods

## __str__

Human-readable representation.

---

## __repr__

Developer/debug representation.

---

## __eq__

Defines:

```python
==
```

---

## __call__

Makes object callable.

---

# 14. Dataclasses

Removes boilerplate.

Auto-generates:

- __init__
- __repr__
- __eq__

Example:

```python
@dataclass
class User:
    name: str
```

---

# 15. Metaclasses

Classes are objects.

Created by:

```python
type
```

Example:

```python
type(Employee)
```

Output:

```python
<class 'type'>
```

Used heavily by:

- Django ORM
- SQLAlchemy
- Pydantic

---

# Interview Hot Topics

Must Know:

- GIL
- AsyncIO vs Threading
- Multiprocessing
- Decorators
- Context Managers
- Closures
- Mutable Default Arguments
- Deep vs Shallow Copy
- Composition vs Inheritance
- Polymorphism
- Duck Typing
- MRO
- Mixins
- Descriptors
- __slots__
- Dataclasses
- Metaclasses

---

# Status

Python Revision Completed

Next:

- SOLID Principles
- Design Patterns
- LLD
- HLD
- System Design
- Backend Architecture

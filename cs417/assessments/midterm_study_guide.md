# CS 417 — Midterm Study Guide

The midterm covers material from **Weeks 1–7**. It emphasizes conceptual understanding over syntax recall. The format is multiple choice, fill-in-the-blank, and short answer (including algorithm tracing and writing code).

**Where to focus your study time:** The majority of the exam covers material from **after Quiz 1** — recursion, searching, hashing, and sorting (Weeks 5–7). These topics carry the most weight. Earlier material (OOP, Big-O, stacks/queues, Unicode) appears but in smaller proportion. If your study time is limited, prioritize Weeks 5–7 first, then review earlier concepts.

This guide is organized by topic. For each topic: what you should know, what to focus on, and practice problems.

---

## 1. Object-Oriented Programming (Weeks 1–2)

### Key Concepts
- **Class vs. Object**: A class is a blueprint; an object is a specific instance created from that class
- **Encapsulation**: Bundling data and methods together, restricting direct access to internal components
- **Abstraction**: Exposing only essential features while hiding implementation details
- **Inheritance**: A class can inherit methods and attributes from a parent class (`class Cat(Animal):`)
- **Polymorphism**: Different classes can be treated through a common interface, each implementing it differently
- **`self`**: Refers to the current instance — how an object accesses its own attributes and methods
- **`__init__`**: The constructor — runs automatically when a new object is created
- **`__str__`**: Defines the custom string representation used by `print()` and `str()`

### What to Focus On
- Understand what each OOP concept *means*, not just definitions — be able to recognize examples
- Know how a class definition translates to object creation and method calls

### Practice
- Given a class definition, predict what method calls will output
- Identify which OOP principle (encapsulation, abstraction, inheritance, polymorphism) a code example demonstrates

---

## 2. Character Encoding & Unicode (Week 4)

### Key Concepts
- **ASCII**: Original 7-bit encoding — 128 characters (English letters, digits, punctuation, control characters)
- **Unicode**: A universal standard that assigns a unique **code point** to every character across all writing systems (Latin, Chinese, Arabic, emoji, etc.)
- **UTF-8**: A variable-width encoding for Unicode — uses 1 byte for ASCII characters, up to 4 bytes for others. It's backward-compatible with ASCII.
- **`ord()`**: Returns the Unicode code point (integer) of a character — e.g., `ord('A')` returns `65`
- **`chr()`**: Returns the character for a given code point — e.g., `chr(65)` returns `'A'`
- **Python 3 strings are Unicode by default** — every string is a sequence of Unicode characters

### What to Focus On
- Know *why* Unicode exists — ASCII only covers English; Unicode covers the world's writing systems
- Understand that UTF-8 is an *encoding* of Unicode (how code points are stored as bytes), not a separate standard
- Be able to use `ord()` and `chr()` conceptually

### Practice
- What is `ord('a')`? What is `chr(90)`?
- Why can't ASCII represent Chinese characters?
- What's the relationship between ASCII, Unicode, and UTF-8?

---

## 3. Abstract Data Types — Stacks & Queues (Week 4)

### Key Concepts
- **ADT**: A specification defined by its operations and behavior, independent of implementation
- **Stack**: Last-In, First-Out (LIFO)
  - Operations: `push(item)`, `pop()`, `peek()`, `is_empty()`, `size()`
  - Real-world analogy: browser back button, undo functionality, call stack
- **Queue**: First-In, First-Out (FIFO)
  - Operations: `enqueue(item)`, `dequeue()`, `peek()`, `is_empty()`, `size()`
  - Real-world analogy: customer service line, print queue

### What to Focus On
- Know the difference between LIFO and FIFO and when to use each
- Be able to *use* a stack or queue (call the operations) to solve a problem — you won't need to implement one from scratch
- Understand that the call stack is how Python manages recursive function calls

### Practice
- Given a sequence of push/pop or enqueue/dequeue operations, determine the final state
- "Which data structure?" questions — match a real-world scenario to stack or queue

---

## 4. Big-O Complexity Analysis (Week 2)

### Key Concepts

| Complexity | Name | Example |
|-----------|------|---------|
| O(1) | Constant | Accessing a list element by index |
| O(log n) | Logarithmic | Binary search |
| O(n) | Linear | Sequential search, single loop through a list |
| O(n log n) | Linearithmic | Merge sort, quicksort (average case) |
| O(n²) | Quadratic | Nested loops, bubble/selection/insertion sort (worst case) |

### What to Focus On
- **Read code and determine Big-O** — count loops, nesting, and whether input size affects work done
- A single loop over n items → O(n)
- A nested loop (both over n) → O(n²)
- No loops, just arithmetic or index access → O(1)
- Cutting the problem in half each step → O(log n)
- Know the growth rate ranking: O(1) < O(log n) < O(n) < O(n log n) < O(n²)

### Practice
- Given 3–4 short Python functions, state the Big-O of each with a one-sentence justification
- "Which is fastest for large inputs?" ranking questions

---

## 5. Recursion (Week 5)

### Key Concepts
- Every recursive function needs two things:
  1. **Base case** — the condition that stops recursion (e.g., empty list, n == 0)
  2. **Recursive case** — the function calls itself with a smaller/simpler input
- Without a base case → infinite recursion → `RecursionError` (stack overflow)
- Python uses the **call stack** to manage recursive calls — each call gets its own local variables
- The call stack unwinds when the base case is reached, returning values back up

### What to Focus On
- **Tracing**: Given a recursive function and an input, trace through each call and return value
- **Writing**: Given a problem, write a recursive function with a clear base case and recursive case
- **Identifying**: What does this recursive function compute? (factorial, sum, fibonacci, etc.)

### Practice
- Trace `factorial(5)` step by step — show each call and each return
- Write a recursive function to sum a list, reverse a string, or count items
- What happens if you remove the base case?

---

## 6. Searching (Weeks 5-6)

### Key Concepts

| Algorithm | How it Works | Time Complexity | Requires |
|-----------|-------------|----------------|----------|
| **Sequential search** | Check each item one by one from the beginning | O(n) | Nothing — works on any list |
| **Binary search** | Compare with middle, eliminate half each step | O(log n) | List must be **sorted** |

### What to Focus On
- Binary search: know the precondition (sorted data) and why it's O(log n)
- Be able to trace binary search — given a sorted list and a target, show which elements are compared at each step
- Understand the tradeoff: binary search is faster but requires sorted data

### Practice
- Trace binary search on `[3, 8, 15, 22, 33, 41, 56, 70]` looking for 41. How many comparisons?
- When would you choose sequential over binary search?

---

## 7. Hashing (Weeks 5-6)

### Key Concepts
- **Hash function**: Maps a key to a table index (commonly `key % table_size`)
- **Collision**: When two different keys hash to the same slot
- **Linear probing**: On collision, check the next slot sequentially (wrap around if needed)
- **Clustering**: A buildup of items in consecutive slots — degrades performance, caused by linear probing
- Best case: O(1) lookup. Worst case (many collisions): O(n)
- **Load factor**: ratio of filled slots to total slots — higher load factor = more collisions

### What to Focus On
- **Build a hash table by hand**: given a hash function, a table size, and a list of keys, insert them one by one using linear probing
- Know how to identify and explain collisions
- Understand why clustering is a problem

### Practice
- Insert keys [44, 22, 33, 55, 11] into a table of size 11 using `key % 11` with linear probing. Show the final table and identify all collisions.
- What happens to performance as the table fills up? Why?

---

## 8. Sorting (Weeks 6-7) — *Heaviest topic on the midterm*

### O(n²) Sorts — Know the Mechanism

| Algorithm | Mechanism | Best Case | Worst Case | Key Trait |
|-----------|-----------|-----------|------------|-----------|
| **Bubble sort** | Repeatedly swap adjacent elements; largest bubbles to the end each pass | O(n) — already sorted | O(n²) | Simple but slow; can detect sorted early with no-swap optimization |
| **Selection sort** | Find the largest (or smallest) remaining, place it in final position | O(n²) | O(n²) | Always O(n²) — no early exit; fewer swaps than bubble sort |
| **Insertion sort** | Insert each element into its correct position in the growing sorted portion | O(n) — already sorted | O(n²) | Excellent for nearly sorted data; adaptive |

### Shell Sort — The Bridge

- Improves insertion sort by sorting **sublists defined by a gap**
- Gap decreases over time — starts with large gaps (moves elements far), finishes with gap=1 (regular insertion sort)
- The early passes reduce disorder so the final insertion sort pass does very little work
- Complexity depends on gap sequence — generally between O(n) and O(n²)

### O(n log n) Sorts — Know the Strategy

| Algorithm | Strategy | Best Case | Worst Case | Key Trait |
|-----------|----------|-----------|------------|-----------|
| **Merge sort** | Divide list in half recursively, merge sorted halves | O(n log n) | O(n log n) | **Guaranteed** O(n log n); uses extra memory for merging |
| **Quicksort** | Choose pivot, partition into less-than/greater-than, recurse | O(n log n) | O(n²) | Usually fast in practice; worst case when pivot is always min/max |

### What to Focus On
- **Trace bubble sort**: Show the list after each complete pass
- **Trace merge sort**: Show the splitting and merging phases
- Know *why* each algorithm has its complexity — don't just memorize the Big-O
- Understand the **divide and conquer** strategy shared by merge sort and quicksort
- Know when quicksort degrades (sorted input + bad pivot choice) and why merge sort doesn't
- For large datasets, why O(n log n) matters vs O(n²)

### Practice
- Bubble sort trace: Start with `[29, 10, 14, 37, 13]` — show the list after each pass
- Merge sort trace: Start with `[38, 27, 43, 3, 9, 82, 10]` — show splitting and merging
- "Which algorithm?" questions: match a description of behavior to the correct sort
- Compare: When might insertion sort beat quicksort? (Small or nearly sorted data)

---

## 9. Software Engineering Fundamentals (Week 3)

### Key Concepts
- **Unit testing**: Testing a small, isolated piece of functionality (a single function or method)
- **pytest**: Python testing library — write functions starting with `test_`, use `assert`
- **Good coding practices**: Meaningful names, consistent formatting, appropriate comments, modular design
- **Project structure**: Organizing code into modules, separating concerns

### What to Focus On
- Know *what* a unit test is and *why* we write them — not pytest syntax details
- Understand that `assert a == b` checks that two values are equal

---

## Exam Tips

1. **For algorithm tracing**: Work carefully, one step at a time. Show your work — partial credit is available for correct process even if the final answer has a small error.

2. **For "which data structure/algorithm?"**: Think about the *properties* — LIFO vs FIFO, sorted vs unsorted requirement, time complexity needs.

3. **For Big-O questions**: Count the loops. One loop = O(n). Nested loops = O(n²). Halving = O(log n). No loops = O(1).

4. **For recursion**: Always identify the base case first. Then check: does each recursive call move toward the base case?

5. **For sorting comparisons**: Know the complexity table, but more importantly know *why* — what does each algorithm actually do that makes it fast or slow?

---

*Good luck!*

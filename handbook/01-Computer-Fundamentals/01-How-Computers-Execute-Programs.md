# 01 - How Computers Execute Programs

> Version: 1.0  
> Module: Computer Fundamentals  
> Last Updated: 2026-07-05
> Difficulty: 🟢 Beginner → 🟡 Intermediate  
> Estimated Reading Time: 35–45 Minutes

---

# Why This Chapter Exists

Before learning Node.js, Express, PostgreSQL, Prisma, Docker, or System Design, it is important to understand **how a computer actually runs a program**.

Almost every backend technology eventually relies on the operating system, memory, CPU, storage, and networking.

If you understand **how a computer executes a program**, many topics later in this handbook become much easier to understand:

- Why Node.js is single-threaded
- Why `fs.readFile()` is asynchronous
- Why databases store data on disk
- Why RAM is faster than SSD
- Why Docker containers start processes
- Why Express receives HTTP requests
- Why PostgreSQL executes SQL queries

This chapter builds the foundation for everything that follows.

---

# Learning Objectives

After completing this chapter, you should be able to explain:

- Why computers only understand binary
- What machine instructions are
- What happens when you double-click a program
- How an operating system loads a program
- Why RAM is required before execution
- How the CPU executes instructions
- The difference between source code and machine code
- The role of compilers and interpreters
- Where Node.js fits into this entire process

---

# Prerequisites

There are no prerequisites.

This is the first technical chapter of the handbook.

---

# Quick Review

| Concept           | Summary                                       |
| ----------------- | --------------------------------------------- |
| Program           | A set of instructions written by a programmer |
| Compiler          | Converts source code into machine code        |
| Interpreter       | Executes source code step by step             |
| Operating System  | Loads and manages programs                    |
| RAM               | Temporary memory used while programs run      |
| CPU               | Executes machine instructions                 |
| Storage (SSD/HDD) | Permanently stores programs and data          |

---

# Big Picture

Understanding how programs execute is easier if we first look at the complete journey.

```

               Programmer
                    │
                    ▼
         Writes Source Code
                    │
                    ▼
       Compiler / Interpreter
                    │
                    ▼
           Machine Instructions
                    │
                    ▼
           Operating System
                    │
                    ▼
        Loads Program into RAM
                    │
                    ▼
              CPU Executes
                    │
                    ▼
              Program Output

```

Everything you will study later—Node.js, PostgreSQL, Express, MongoDB—follows this same execution path.

---

# A Simple Question

Suppose you open **Visual Studio Code**.

You double-click the application icon.

Within a second, the editor appears on your screen.

Have you ever wondered what happened during that one second?

Thousands of operations occurred behind the scenes.

The operating system:

- Found the executable file
- Loaded it into memory
- Allocated resources
- Started a process
- Assigned CPU time
- Created threads
- Initialized libraries
- Rendered the user interface

All of this happens before you even type a single line of code.

Understanding this process makes backend development much easier.

---

# What Is a Computer?

A computer is simply a machine that executes instructions.

It does **not** understand JavaScript.

It does **not** understand Python.

It does **not** understand TypeScript.

It does **not** understand English.

It only understands one thing:

> Machine Instructions

Every programming language eventually becomes machine instructions.

---

# What Is a Program?

A program is nothing more than a collection of instructions.

Example:

```text
Open calculator

↓

Wait for user input

↓

Read numbers

↓

Add numbers

↓

Display result
```

Those instructions may be written in:

- JavaScript
- TypeScript
- C
- C++
- Rust
- Go
- Java

The language does not matter.

Eventually every program becomes machine instructions.

---

# Humans vs Computers

Humans prefer readable languages.

Example:

```ts
const sum = 10 + 20

console.log(sum)
```

This is easy for humans.

The CPU cannot understand this.

Instead, it understands instructions closer to:

```text
LOAD R1, MEMORY_ADDRESS

LOAD R2, MEMORY_ADDRESS

ADD R1, R2

STORE RESULT

PRINT
```

Even this is still a simplified representation.

The actual CPU executes binary instructions.

---

# Why Can't CPUs Understand JavaScript?

A CPU is an electronic circuit.

Inside the processor are billions of tiny transistors.

Each transistor has only two electrical states:

- ON
- OFF

These two states are represented as:

```
1
0
```

Everything a computer does—playing music, running Node.js, rendering a website, storing database records—is ultimately represented using combinations of **0s and 1s**.

This representation is called **binary**.

---

# Mental Model

Think of a CPU as someone who speaks only one language.

Imagine this conversation.

```
You: Hello!

CPU: ❌ I don't understand.

You: console.log("Hello")

CPU: ❌ I don't understand.

You: 010101100110...

CPU: ✅ Finally!
```

Obviously, real CPUs do not literally read long binary strings written by humans, but the analogy is useful:

**The CPU only executes machine instructions encoded in binary.**

---

# Real-World Example

Suppose you write:

```ts
function add(a: number, b: number) {
  return a + b
}

console.log(add(10, 20))
```

This code is designed for humans.

Before the CPU can execute it, several transformations occur.

```
TypeScript

↓

JavaScript

↓

Machine Instructions

↓

CPU

↓

Output
```

This transformation is one of the central ideas of modern software development.

Later in this handbook, you'll learn how tools such as the TypeScript compiler, Node.js runtime, and JavaScript engine participate in this process.

---

# Important Takeaways

Before moving to the next section, make sure these ideas are clear:

✅ A computer executes instructions.

✅ CPUs do not understand JavaScript directly.

✅ Programming languages are designed for humans.

✅ Every program eventually becomes machine instructions.

✅ The operating system is responsible for loading programs before the CPU can execute them.

---

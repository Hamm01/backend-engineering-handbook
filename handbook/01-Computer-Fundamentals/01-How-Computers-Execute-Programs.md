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

# What's Next

Now that we understand **why programming languages must be translated**, the next section explores:

- Binary
- Machine Language
- Assembly Language
- Compilers
- Interpreters

These concepts explain **how human-readable code becomes something a CPU can execute.**

---

# From Human Language to Machine Language

Imagine you are visiting a country where nobody speaks your language.

You speak English.

The local people understand only Japanese.

No matter how intelligent you are, communication cannot happen until both sides understand the same language.

Programming languages work in exactly the same way.

---

## Mental Model

Imagine this conversation.

```

Human

↓

English

↓

Translator

↓

Japanese

↓

Local Person

```

Programming follows the same idea.

```

Programmer

↓

TypeScript

↓

Compiler / Runtime

↓

Machine Code

↓

CPU

```

The CPU is not "smart."

It simply understands a very small language called **Machine Language**.

Everything else must eventually be translated.

---

# Why Do Programming Languages Exist?

This is one of the most misunderstood questions among beginners.

Many people think JavaScript exists because computers need JavaScript.

That is completely backwards.

JavaScript exists because **humans need JavaScript.**

Computers would actually prefer if we wrote everything directly in machine instructions.

Humans would never be productive doing that.

Programming languages are designed for **human readability**, not for computers.

---

# Machine Language

Machine Language is the only language the CPU executes directly.

A machine instruction is simply a binary instruction telling the processor to perform one operation.

Examples include:

- Load data into a register
- Add two numbers
- Move memory
- Compare values
- Jump to another instruction

A real machine instruction looks something like this:

```text
10110000 01100001
```

Thankfully, developers almost never write machine code manually.

---

# Why Binary?

Computers are built using billions of tiny electronic switches called **transistors**.

Each transistor has only two stable electrical states.

```
ON

OFF
```

These states naturally become

```
1

0
```

Everything inside your computer is represented using these two values.

For example,

```
Number

↓

Binary

↓

Electrical Signals

↓

CPU
```

When you type the number

```text
25
```

the processor eventually stores it as

```text
11001
```

When you type

```text
A
```

the computer eventually stores it as

```text
01000001
```

Everything becomes binary.

---

# What About Images?

People often think binary only represents numbers.

Actually, binary represents **everything.**

```
Images

↓

Pixels

↓

Numbers

↓

Binary
```

---

Music

```
Sound

↓

Samples

↓

Numbers

↓

Binary
```

---

Videos

```
Frames

↓

Pixels

↓

Numbers

↓

Binary
```

---

Even this Markdown file eventually becomes binary before being stored on your SSD.

---

# Machine Instructions

A CPU performs only extremely small operations.

For example,

```
Load value

↓

Add value

↓

Store result

↓

Jump

↓

Compare

↓

Repeat
```

Suppose we write

```ts
const answer = 10 + 20
```

You probably imagine one operation.

The processor does not.

Internally it performs several tiny instructions.

A simplified view:

```
Load 10

↓

Load 20

↓

Add

↓

Store Result

↓

Continue
```

Millions or billions of these tiny operations occur every second.

Modern CPUs execute billions of instructions every second.

---

# Why Can't We Just Program in Binary?

Technically...

we can.

Historically, programmers actually did.

Imagine writing an application like this:

```text
101101010101010001011001010101001001010101...
```

Finding one mistake would be nearly impossible.

Adding a new feature would be a nightmare.

Maintaining millions of binary digits is simply unrealistic.

Higher-level programming languages were created to solve this exact problem.

---

# Levels of Programming Languages

As computers evolved, programming languages also evolved.

```
Machine Language

↓

Assembly

↓

C

↓

C++

↓

Java

↓

JavaScript

↓

TypeScript
```

Notice something interesting.

As we move upward,

programming becomes easier for humans,

but another translation step becomes necessary before the CPU can execute the program.

---

# Quick Comparison

| Language   | Human Friendly | CPU Friendly |
| ---------- | -------------- | ------------ |
| Binary     | ❌             | ✅           |
| Assembly   | ⚠️             | ✅           |
| C          | ✅             | ❌           |
| JavaScript | ✅✅           | ❌           |
| TypeScript | ✅✅           | ❌           |

The easier a language becomes for humans,

the more work is required behind the scenes before the CPU can execute it.

---

# Production Perspective

When you run:

```bash
node app.js
```

Node.js does **not** send your JavaScript directly to the CPU.

Instead,

```
JavaScript

↓

V8 JavaScript Engine

↓

Machine Instructions

↓

CPU
```

We'll study V8 in detail later in the Node.js Internals module.

For now, remember one key idea:

> The CPU never executes JavaScript directly.

---

# Common Misconceptions

❌ "The CPU understands JavaScript."

No.

The CPU executes machine instructions.

---

❌ "Binary is only used for numbers."

No.

Binary represents every kind of digital information.

---

❌ "Programming languages exist for computers."

No.

Programming languages exist primarily for humans.

---

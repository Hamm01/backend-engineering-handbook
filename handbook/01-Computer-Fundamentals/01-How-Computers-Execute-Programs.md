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

# Interview Questions

### Question 1

Why can't a CPU execute JavaScript directly?

---

### Question 2

Why does every programming language eventually become machine instructions?

---

### Question 3

Why is binary used instead of decimal?

---

### Question 4

Why are higher-level programming languages easier to maintain?

---

# Summary

In this section you learned:

- Why CPUs only understand machine language
- Why binary exists
- Why programming languages exist
- Why every program must eventually be translated
- Why humans don't write binary directly

These ideas form the basis for understanding compilers, interpreters, Node.js, and JavaScript engines.

The next section explains **Assembly Language, Compilers, and Interpreters**, where we'll follow the complete journey from TypeScript source code to executable machine instructions.

# Assembly Language, Compilers, and Interpreters

## Why We Need Programming Languages

Imagine you are talking to someone who only understands Chinese.

You only know English.

Communication becomes impossible.

You need a translator.

Exactly the same thing happens between developers and CPUs.

A CPU understands only one language:

```text
Machine Code

10110000
00000001
11101010
...
```

Humans cannot realistically write millions of binary instructions.

Imagine writing Google Chrome entirely like this:

```text
10101010
00101111
11100001
01010100
...
```

Even writing a calculator would become nearly impossible.

So computer scientists introduced layers of abstraction.

Instead of writing binary directly, programmers write instructions that are easier for humans to understand.

---

## Evolution of Programming Languages

Programming languages evolved in multiple stages.

```text
Human Thinking
        │
        ▼
High-Level Languages
(TypeScript, JavaScript, Go, Rust, C++)
        │
        ▼
Compiler / Interpreter
        │
        ▼
Assembly Language
        │
        ▼
Assembler
        │
        ▼
Machine Code
(Binary)
        │
        ▼
CPU Executes
```

Each layer hides more complexity from the programmer.

As hardware became more powerful, programming languages became more expressive.

---

# Machine Language

Machine language is the only language a processor can execute directly.

Example (illustrative only):

```text
10110000 01100001
10110001 00000001
00000001 11000001
```

To us this looks meaningless.

To the CPU, every bit has a predefined meaning.

Each instruction tells the processor something like:

- Load a value
- Move data
- Add numbers
- Jump somewhere
- Compare values
- Read memory

Machine code is therefore nothing more than instructions encoded as binary.

---

# The Problem With Machine Code

Although machine code is fast, it has major disadvantages.

Imagine accidentally changing

```text
10110000
```

to

```text
10110001
```

One single bit changed.

The entire instruction now means something different.

Finding bugs would be almost impossible.

Some additional problems:

- extremely difficult to read
- impossible for large projects
- processor-specific
- difficult to debug
- impossible to remember instruction encodings

Developers needed something more human-friendly.

---

# Assembly Language

Assembly language is the human-readable representation of machine code.

Instead of writing

```text
10110000 01100001
```

we can write

```asm
MOV AL, 97
```

Instead of

```text
00000001 11000001
```

we write

```asm
ADD AX, BX
```

These instructions are much easier for humans to understand.

The processor still cannot execute assembly directly.

Assembly must first be translated into machine code.

That translation is performed by an **assembler**.

---

## Machine Code vs Assembly

| Machine Code | Assembly |
| ------------ | -------- |
| 10110000     | MOV      |
| 00000001     | ADD      |
| 11101010     | JMP      |
| 00111001     | CMP      |

The two represent exactly the same instructions.

Assembly simply replaces binary numbers with readable names called **mnemonics**.

---

# Assembly Mnemonics

Assembly instructions usually have short names.

Some common ones are:

| Mnemonic | Meaning              |
| -------- | -------------------- |
| MOV      | Move data            |
| ADD      | Add                  |
| SUB      | Subtract             |
| MUL      | Multiply             |
| DIV      | Divide               |
| JMP      | Jump                 |
| CMP      | Compare              |
| PUSH     | Push onto stack      |
| POP      | Remove from stack    |
| CALL     | Call function        |
| RET      | Return from function |

Even modern CPUs ultimately execute versions of these low-level operations.

---

# Example: Adding Two Numbers

Suppose we want to calculate

```text
5 + 3
```

Machine code might look like

```text
10110000
00000101

10110001
00000011

00000001
11000001
```

Assembly becomes much easier.

```asm
MOV AX, 5
MOV BX, 3
ADD AX, BX
```

Even someone unfamiliar with assembly can roughly understand what is happening.

---

# Assembly Still Has Problems

Assembly is far easier than binary.

But it still has major limitations.

Imagine writing a web server entirely in assembly.

You would have to manually:

- allocate memory
- manage CPU registers
- control every jump
- handle every function call
- work directly with processor instructions

Even printing text requires many instructions.

A simple loop becomes dozens of assembly instructions.

Large software would contain millions of lines.

Productivity would be extremely low.

---

# High-Level Languages

To solve this problem, high-level programming languages were created.

Instead of telling the CPU _how_ to do every tiny operation, we describe _what_ we want.

Example in TypeScript:

```ts
const a = 5
const b = 3

const sum = a + b

console.log(sum)
```

This is readable by almost every developer.

The compiler or interpreter handles the complicated translation.

---

# Levels of Abstraction

Notice how each level hides more details.

```text
Machine Code
↓

Assembly
↓

C
↓

C++

↓

Java

↓

TypeScript
```

As we move upward:

- readability increases
- development becomes faster
- portability improves
- hardware details become hidden

The tradeoff is that more translation is required before execution.

---

# What Is a Compiler?

A compiler is a program that translates source code into another language before the program runs.

Most commonly:

```text
Source Code
↓

Compiler
↓

Machine Code
↓

Executable File
```

Examples:

```text
C
↓

gcc

↓

calculator.exe
```

```text
Rust
↓

rustc

↓

server.exe
```

Once compiled, the executable can run without the compiler.

---

## Real-Life Analogy

Imagine writing a book in English.

A professional translator converts it into Japanese.

After translation, the Japanese book can be distributed independently.

The translator is no longer needed.

A compiler works in the same way.

---

# Compiler Workflow

```text
Developer
     │
writes code
     │
     ▼
Source Code
     │
     ▼
Compiler
     │
     ▼
Machine Code
     │
     ▼
Executable Program
     │
     ▼
CPU Executes
```

Compilation happens before execution.

---

# What Is an Interpreter?

An interpreter works differently.

Instead of translating the whole program at once, it reads the program piece by piece while it is running.

```text
Source Code
↓

Interpreter

↓

Execute Instruction

↓

Next Instruction

↓

Execute Again
```

No standalone executable is produced.

The interpreter stays involved for the lifetime of the program.

---

## Interpreter Analogy

Imagine attending an international conference.

A speaker talks one sentence.

An interpreter immediately translates it.

The audience hears the translated sentence.

The speaker continues.

Translation happens continuously.

This is exactly how interpreters operate.

---

# Compiler vs Interpreter

```text
Compiler

Entire Program
        │
        ▼
Translation
        │
        ▼
Executable
        │
        ▼
Run
```

```text
Interpreter

Instruction
      │
      ▼
Translate
      │
      ▼
Execute
      │
      ▼
Next Instruction
```

The key difference is **when** translation happens.

---

# Common Examples

| Language   | Typical Execution Model                 |
| ---------- | --------------------------------------- |
| C          | Compiled                                |
| C++        | Compiled                                |
| Rust       | Compiled                                |
| Go         | Compiled                                |
| Python     | Interpreted (bytecode + VM)             |
| JavaScript | Interpreted with JIT compilation        |
| TypeScript | Transpiled to JavaScript                |
| Java       | Compiled to bytecode, then JIT compiled |

Modern language runtimes often combine compilation and interpretation techniques for better performance.

---

# Where Does TypeScript Fit?

Many beginners assume TypeScript runs directly on the CPU.

It does not.

The CPU has absolutely no understanding of TypeScript syntax.

When you write:

```ts
const age: number = 25
```

the type annotation (`: number`) is useful only during development.

The **TypeScript compiler (`tsc`)** removes type information and converts the code into plain JavaScript.

```text
TypeScript
      │
      ▼
TypeScript Compiler (tsc)
      │
      ▼
JavaScript
```

At this stage, we still do **not** have machine code.

We only have JavaScript, another programming language.

---

# Where Does Node.js Fit?

Node.js is **not a compiler**.

It is **not an operating system**.

It is a **JavaScript runtime**.

When you execute:

```bash
node app.js
```

Node.js reads your JavaScript source code and passes it to the **V8 JavaScript Engine**.

V8 parses the JavaScript, converts it into an internal representation, interprets it, and then uses **Just-In-Time (JIT) compilation** to translate frequently executed code into optimized machine code while the program is running.

This allows JavaScript to achieve performance much closer to traditionally compiled languages for many workloads.

We'll explore the internals of V8, bytecode, and JIT compilation in dedicated chapters later in this handbook.

---

# Complete Journey of a Backend Program

Let's connect everything you've learned so far.

Suppose you write this TypeScript code:

```ts
console.log('Hello Backend')
```

The execution journey looks like this:

```text
TypeScript Source Code
          │
          ▼
TypeScript Compiler (tsc)
          │
          ▼
JavaScript
          │
          ▼
Node.js Runtime
          │
          ▼
V8 Engine
          │
          ▼
Bytecode
          │
          ▼
JIT Compiler
          │
          ▼
Machine Code
          │
          ▼
CPU Executes Instructions
          │
          ▼
Output Appears on Screen
```

Every backend application you build with Node.js follows this pipeline, although many of these stages are optimized and happen so quickly that they are invisible to the developer.

---

# Key Takeaways

- CPUs execute only machine code.
- Machine code is represented as binary instructions.
- Assembly language provides human-readable mnemonics for machine instructions.
- An assembler converts assembly into machine code.
- High-level languages improve productivity by hiding hardware complexity.
- A compiler translates an entire program before execution.
- An interpreter translates and executes code during runtime.
- TypeScript is transpiled into JavaScript.
- Node.js executes JavaScript using the V8 engine.
- V8 ultimately produces machine instructions that the CPU can execute.

---

# Common Mistakes

1. **"The CPU understands TypeScript."**  
   False. The CPU only executes machine instructions.

2. **"Node.js compiles TypeScript."**  
   No. TypeScript is transpiled by `tsc` (or another build tool) before Node.js runs the resulting JavaScript.

3. **"JavaScript is purely interpreted."**  
   Modern JavaScript engines, including V8, use a combination of interpretation and JIT compilation.

4. **"Assembly runs directly on the CPU."**  
   Assembly source code must first be translated into machine code by an assembler.

---

# Interview Questions

1. Why can't a CPU execute TypeScript directly?
2. What is the difference between assembly language and machine code?
3. What role does an assembler play?
4. How does a compiler differ from an interpreter?
5. Why is TypeScript called a transpiled language?
6. What happens after `tsc` generates JavaScript?
7. What is the role of the V8 engine inside Node.js?
8. Why do modern JavaScript engines use JIT compilation instead of only interpretation?

---

# Exercises

1. Draw the complete execution pipeline from TypeScript source code to CPU execution without referring to the handbook.
2. Research three common assembly mnemonics (`MOV`, `CMP`, and `JMP`) and describe their purpose.
3. Compile a simple TypeScript file using `tsc` and compare the generated JavaScript with the original source.
4. Write a short paragraph explaining, in your own words, why high-level programming languages dramatically improve developer productivity.

---

# Next Chapter

Now that we understand **how source code eventually becomes machine instructions**, the next chapter explores **how the Operating System loads and starts a program**, including executable files, process creation, virtual memory, and how your Node.js application actually begins running after you type:

```bash
node app.js
```

From there, we'll follow the program all the way from the operating system into the first line of your JavaScript code.

# How the Operating System Starts a Program

## Introduction

In the previous chapter, we learned how high-level source code eventually becomes machine instructions that a CPU can execute.

However, one important question still remains.

Suppose you open a terminal and type:

```bash
node app.js
```

Almost instantly, your JavaScript program begins running.

You see logs printed to the terminal.

Files can be opened.

HTTP servers start listening.

Database connections are established.

But how did all of that begin?

Who loaded the `node` executable into memory?

Who created memory for your application?

Who decided where the program should run?

Who gave it access to the CPU?

Who cleaned everything up when the program exited?

The answer is the **Operating System**.

In this chapter, we'll follow the complete journey that begins the moment you press the **Enter** key after typing:

```bash
node app.js
```

By the end of this chapter, you'll understand how a backend application goes from being a file stored on disk to becoming a running process executing JavaScript code inside your computer.

---

# What Really Happens?

Imagine your computer is currently idle.

Nothing related to your application exists.

There is:

- no JavaScript running
- no Node.js process
- no allocated memory
- no CPU instructions being executed
- no network ports open

Only two files exist on your storage device.

```text
Disk

├── node.exe
└── app.js
```

These are simply files.

They are not running.

They are not using CPU time.

They are not occupying RAM.

They're just bytes stored on your SSD.

---

# Step 1 — You Press Enter

When you press **Enter**, something happens before Node.js is even involved.

The terminal (PowerShell, CMD, Bash, or another shell) receives your command.

```text
Keyboard
     │
     ▼
Terminal
     │
     ▼
node app.js
```

The terminal now needs someone to execute this command.

It cannot execute programs itself.

Instead, it asks the operating system.

```text
Terminal
     │
Request:
"Please start this executable."
     │
     ▼
Operating System
```

---

# Step 2 — The Operating System Searches for Node.js

At this point, the operating system receives a request to execute the command:

```bash
node app.js
```

However, the operating system cannot execute the word `node`.

It must first determine **where the executable file actually exists**.

To do this, the operating system searches through a list of directories stored in the **PATH environment variable**.

For example:

```text
PATH

C:\Program Files\nodejs\
C:\Windows\System32\
C:\Windows\
...
```

On Linux and macOS, the PATH might look like:

```text
/usr/local/bin
/usr/bin
/bin
...
```

The operating system checks each directory until it finds the executable.

```text
Terminal
      │
      ▼
node
      │
      ▼
Operating System
      │
      ▼
Search PATH
      │
      ▼
Found node executable
```

If the executable cannot be found, you'll see an error similar to:

```text
'node' is not recognized as an internal or external command
```

or

```text
command not found: node
```

Once the executable is found, the operating system prepares to start it.

---

# Step 3 — Program vs Process

This is one of the most important distinctions in computer science.

Many developers use the words **program** and **process** interchangeably.

They are **not** the same thing.

A **program** is a passive file stored on disk.

Examples include:

- `node.exe`
- `app.js`
- `chrome.exe`

A **process** is a program that is currently running.

Think of it this way:

```text
Program
      │
(Double-click or Execute)
      ▼
Process
```

Another analogy is a recipe and a meal.

```text
Recipe
    │
Cook It
    ▼
Prepared Meal
```

The recipe is just instructions.

The meal is the result of executing those instructions.

Similarly:

```text
Program = Instructions stored on disk

Process = Instructions currently executing
```

When you type:

```bash
node app.js
```

The operating system creates a **new process** for the Node.js executable.

---

# Step 4 — The Executable Loader

Finding the executable is not enough.

The operating system must now load it into memory.

This job is performed by a component known as the **Executable Loader**.

Its responsibilities include:

- Reading the executable file from disk
- Creating a new process
- Allocating virtual memory
- Loading executable code into memory
- Preparing the stack
- Preparing the heap
- Initializing registers
- Setting up command-line arguments
- Preparing environment variables

The process looks like this:

```text
Disk

↓

Executable File

↓

Executable Loader

↓

Memory

↓

Running Process
```

Only after these steps can the CPU begin executing instructions.

---

# Step 5 — The Scheduler Gives CPU Time

Once the process has been created, it is ready to run.

However, your computer is probably running hundreds of other processes.

Examples include:

- Browser
- Music Player
- Antivirus
- VS Code
- File Explorer

The CPU can only execute a small number of instructions at any given moment.

The operating system's **scheduler** decides which process gets CPU time.

```text
Ready Processes

Browser

Node.js

VS Code

Spotify

↓

CPU Scheduler

↓

CPU
```

Your Node.js process waits until the scheduler assigns it CPU time.

When that happens, execution begins.

---

# Step 6 — Node.js Starts

Now the CPU begins executing the machine instructions inside the Node.js executable.

At this point:

- Node.js runtime initializes
- Internal libraries are loaded
- V8 JavaScript Engine is initialized
- Command-line arguments are processed

Node.js then opens the JavaScript file you specified:

```bash
node app.js
```

It reads:

```text
app.js
```

from disk.

---

# Step 7 — V8 Executes JavaScript

The JavaScript source code is handed to the V8 engine.

V8 performs several stages internally:

- Parse JavaScript
- Generate an Abstract Syntax Tree (AST)
- Produce bytecode
- Interpret the bytecode
- JIT compile frequently executed code into optimized machine code

Eventually, machine instructions are generated.

The CPU executes those instructions.

Your JavaScript program is now running.

---

# The Complete Journey

Putting everything together:

```text
node app.js

↓

Keyboard

↓

Terminal

↓

Operating System

↓

Search PATH

↓

Find node executable

↓

Executable Loader

↓

Create Process

↓

Allocate Virtual Memory

↓

Initialize Stack

↓

Initialize Heap

↓

Load Executable

↓

CPU Scheduler

↓

CPU Starts Executing Node.js

↓

Initialize Node.js Runtime

↓

Initialize V8

↓

Read app.js

↓

Parse JavaScript

↓

Generate Bytecode

↓

JIT Compile Hot Code

↓

Machine Instructions

↓

CPU Executes

↓

console.log("Hello World")
```

This is the complete journey from pressing the **Enter** key to executing the first line of your JavaScript program.

Although this entire process usually takes only a fraction of a second, dozens of operating system components work together behind the scenes to make it possible.

In the following chapters, we'll examine each stage in much greater detail, starting with the difference between **programs and processes**, followed by **virtual memory**, **process memory layout**, **threads**, **system calls**, and eventually the internals of **Node.js** and the **V8 JavaScript engine**.

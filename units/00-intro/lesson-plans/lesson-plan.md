# Lesson Plan

This unit covers a lot of shallow ground by introducing Typescript within an XP framework. 
This first week has a lot of shallow ground to cover, starting with XP and key practices. Please review the [unit plan on the shared drive](https://docs.google.com/document/d/1mUDnKEH063gkWQMWIiXrJU7oKQRwftckSHRdr6y05l4/edit).

## Overview

The goal is to ensure learners can write basic typescript to use it for developing Angular applications. 

**XP Goals**
- Test Cycle
- Collaboration with pair programming
- Unit tests and fakes (basics)

**Typescript Goals**
- Static types and syntax 
- Modules and imports/exports
- Classes and accessors

**Tools**
- Getting VS Code setup 
- Using the debugger
- Browser tools 

## XP and Typescript Fundamentals 

A good part of this week will focus on getting learners comfortable with: 

* Typescript 
* XP: pair programming and tdd 
* Dev Tools: browser and VS Code/Webstorm

The exercises laid out for this week wiill combine with one of the above topics each day to set a strong foundation for their expected workflow the following week. Habits established here set instructor expectations of how learners should perform throughout the course. 

## Exercises

Below are some recommended exercises to achieve this weeks goals. All of them rely on pair programming, where pairs are shuffled at least weekly.

* Shopping Cart: Intro to the test cycle.
* Vending Machine: Great introduction to using the DOM, tying TS and HTML/CSS together.
* Mortgage Lender: Very good as an assessment of basic TDD.
* Data Structures: Good intro to pair programming, but short. Fix failing tests. 
* Bowling Kata: Provide tests and the challenge is to implement the code.
* JS TDD Katas: to fill out the time for exercises that are shorter than expected.

Stretch goals should be added to each unit along with reading and A/V materials for independent study.

### Shoppping Cart (Law I) 

Exercise the first law: write a failing test. Practice writing a reasonable test.
Good ole shopping cart! This is the first opportunity to write their own tests and learn a strong workflow for the test cycle.

Keys: 
- Typescript fundamentals (write it, compile it, run it)
- Pair programming 
- Applying AAA 

### Data Structures (Law II)

Exercise the second law of TDD: get to green as fast as you can.  Data structures are fairly straight forward, so the challenge lies in writing good tests and getting to green quickly.

Tests are provided and learners must implement the code to make them pass. The primary goal is to practice pair programming by setting them in context and encouraging collaboration. Exercise is very short and should be immediately followed up with a discussion and sharing of everyones work. **This can be a morning or afternoon exercise taking approximately 2 hours.**

Keys: 
- Typescript practice 
- Pair programming practice 
- Writing a good test

### Mortgage Lender (Law III)

Exercise the third law: refactoring. Learners will focus on writing tests that can remain unchanged while the their code implementation evolves. They will spend a lot of time thinking about how the program should work and writing white box style tests.

Once the tests are done, learners should find the code basically writes itself. They are expected to use more features of Typescript to arrive at a loosely coupled solution.

Keys: 
- Typescript: apis/interfaces and enums 
- TDD  

### Vending Machine

This is a longer lesson that should take up approximately 1 full day of instruction. Learners must implement HTML, CSS and Javascript to build an interactive vending machine. Altogether there are 3 parts: 

1. The typescript app code by following the stories/AC. 
2. The UI (HTML/CSS)
3. A simple script to connect the UI with the app (DOM).

The exercise starts with the app, using TDD to create the core functionality. This can be followed up by next implementing the UI. The goal is simple: if their orginal app really works, then it can be used to display the data on the DOM. 

Keys:
- Typescript compilation and configuration
- The DOM 
- Ancillary lessons: interfaces, classes, SOLID

### Bowling Kata

Tests are provided, but there's no code! Their challenge is to implement the app without changing the tests. Learners should start to understand and appreciate the 'Refactor' step of the test cycle.

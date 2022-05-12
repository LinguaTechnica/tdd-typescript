# Lesson Plan

Use this section to provide guides, examples and resources to support the current lessons and exercises. 

## Overview

Now that learners have been introduced to Typescript, TDD and pair programming, this lesson plan should focus on tying together how frontend development works. Goals: 

- Ts compilation and configuration
- The DOM 
- Tools: browser and debugger 

The burning questions right now are: whats an app, how does compilation and bundling work and why?  We want to aim for a fundamental understanding of frameworks at their most basic level so that understanding its component parts can lead to a practical understanding of what Angular does later.

## Vending Machine 

This is a longer lesson that should take approximately 2-3 days of instruction. Learners must implement HTML, CSS and Javascript to build an interactive vending machine. Altogether there are 3 parts: 

1. The typescript app code by following the stories/AC. 
2. The UI (HTML/CSS)
3. A simple script to connect the UI with the app (DOM).

The exercise starts with the app, using TDD to create the core functionality. This can be followed up by next implementing the UI. The goal is simple: if their orginal app really works, then it can be used to display the data on the DOM. 

The practical distinction between an app and a normal JS script is the server aspect of applications. As leaners will see next week, Angular is first compiled, then bundled and then imported into `index.html`. This is their chance to manually do these steps with this handson lesson. 

Keys:
- Typescript compilation and configuration
- The DOM 
- Ancillary lessons: interfaces, classes, SOLID

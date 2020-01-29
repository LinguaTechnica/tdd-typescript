# Vocabulary

* Test Driven Development (TDD): An approach to software development where no code is written without writing tests first. First, developers write failing tests for the functionality they plan to implement, then they write the simplest code possible to make those tests pass, then they refactor their code into high-quality production code.

* Pure function: a function that accepts an input and returns a value without modifying any data outside its scope (has no side effects). Its output or return value must depend on the input/argument, and pure functions must return a value.
  
        function pure(arg) {
            return arg * 4
        }

* Impure function: a function that mutates variables/state/data outside of it's lexical scope (has side effects), doesn't depend on the arguments, or doesn't have a return value.

* NZOMBIES Analysis: (Null, Zero, One, Many, Boundaries, Interface, Exceptions, Simple) an analysis tool where developers experiment with common inputs into a program and guidelines for how to write high quality code.

* Red > Green > Refactor: Red (Only write code in response to a failing test), Green (make tests pass with the simplest code possible), Refactor (refactor your code).

* Unit Test: The smallest testable part of your code, meant to test a single "unit" of code, such as a function. It should have as few inputs and prerequisites as possible.

* Integration Test: The purpose of this of integration testing is to expose faults in the interaction between integrated units. This could be as simple as two objects interacting with each other or as complex as testing multiple systems together.

* End-to-End (E2E) Testing: The process of testing an entire system flow, including external resource usage. The name comes from the process of testing software from back to front or start to finish. For example: creating a test where a button is clicked and the software is allowed to go through the entire process for that button click. This could include making external requests, creating elements, rendering results, etc. The test in this can would verify the ending state of the page is correct. A high level test that verifies the entire flow of the button click action.
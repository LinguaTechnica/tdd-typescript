# Vending Machine
<!--BEGIN CHALLENGE-->

### !challenge

* type: project
* id: <!--unique-id (command-option-u)-->
* title: Submit Your Work
* points: 1
* topics: typescript, tdd

##### !question

Build a simple Vending Machine app. 

## Instructions

1. Fork [this repository](https://github.com/gSchool/vending-machine-ts).
1. Share the repo with your group. Each person should submit the same link!
1. Submit your work below.

It's good practice to commit your code after each green test. Make sure you add a brief, but informative commit message.

**Tips**

- Write the **simplest** code needed to make the test pass. 
- Refactor: 
    - Are any methods more than 5 or 10 lines of code?
    - Is it obvious what each section of code does? If not, how could you make it obvious?
- Commits should have informative messages
- [Typescript Handbook](https://www.typescriptlang.org/docs/handbook)
- [Javascript MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/get)


### User Stories and Acceptance Criteria

Below are a list of simple stories. Collaborate with your group to implement them as best you can.

As a customer, I want to see that the vending machine has items, so that I can purchase them.
- Given that I approach the vending machine
- when I look at it,
- then I see items inside that I can buy along with their price:

As a customer, I want to know how much money I have deposited, so that I know what I can purchase.
- Given I am using the vending machine, 
- when I insert money, 
- then I see a message with the total I have deposited.
- The machine should accept bills in these amounts: `10, 20, 50, 100, 500`

As a customer, I want to add additional money, so that I can use the denominations I have to purchase an item.
- Given I have deposited money in the vending machine,
- when I deposit additional money,
- then I see the new total on a screen. 

As a customer, I want to see a message if my item is unavailable, so that I can make another choice.
- Given I am using the vending machine, 
- when I enter a code for an item that is unavailable, 
- then I see a message that the item is unavailable.

As a customer, I want to see a message if my deposit is insufficient, so that I know to add more money.
- Given I have made a choice, 
- when I have not deposited enough money for that item, 
- then I see a message telling me how much more to deposit.

As a customer, I want to receive change, so that I don’t pay more than the item costs.
- Given I have made a selection, 
- when the item is delivered, 
- then I receive correct change (in correct monetary units)

As a customer, I want to receive my money back when I push the cancel button, so that I can change my mind.
- Given that I have deposited money,
- When I push the cancel button,
- Then I receive my money back

As a customer, I want to know if the vending machine can make change, so that I can cancel my choice if it can't make change.
- Given I have deposited money and selected a choice, 
- when the machine does not have correct change, 
- then I see a message to choose again or cancel the transaction


## Submit Your Work 

##### !end-question

##### !placeholder

Your repo link goes here!

##### !end-placeholder

<!--optional-->
##### !hint

##### !end-hint

<!--optional, checkpoints only-->
##### !rubric

##### !end-rubric

<!--optional-->
##### !explanation

##### !end-explanation

### !end-challenge

<!--END CHALLENGE-->
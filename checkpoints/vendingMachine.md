# Vending Machine
<!--BEGIN CHALLENGE-->

### !challenge

* type: project
* id: aad7fc63-50ef-4ed0-ba6a-b4363ee70441
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

Below are a list of simple stories. Collaborate with your group to implement them as best you can. **Money is valued in Rupees (Rs)! NOT dollars ($)**

1 As a customer, I want to see that the vending machine has items, so that I can purchase them.
- when view the machine,
- then I see items inside which I can buy, along with their price.

2 As a customer, I want to know how much money I have deposited, so that I know what I can purchase.
- Given a vending machine with items, 
- when I insert money, 
- then I see a message with the total I have deposited.

3 As a customer, I want to add additional money, so that I can increase my purchase power.
- Given I have deposited money in the vending machine,
- when I deposit additional money,
- then I see the new total on a screen. 

4 As a customer, I want to see a message if my item is unavailable, so that I can make another choice.
- Given I have selected an item, 
- when it's unavailable, 
- then I see a message that the item is unavailable.

5 As a customer, I want to see a message if my deposit is insufficient, so that I know to add more money.
- Given I have made a selection, 
- when I have not deposited enough money for that item, 
- then I see a message telling me how much more to deposit.

6 As a customer, I want to receive change, so that I don’t pay more than the item costs.
- Given I have deposited <deposit>, 
- when the item costs <price> 
- then I receive <change> (in correct monetary units)

Examples:
|  deposit |  price | change |
| -------- | ------ | ------ |
|    100   |   80   |   20   | 
|    500   |   200  |   300  | 

7 As a customer, I want to receive my money back when I cancel the transaction.
- Given that I have deposited money,
- When I push the cancel button,
- Then I receive my money back

8 As a customer, I want to know if the vending machine can make change, so that I can cancel my choice if it can't make change.
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
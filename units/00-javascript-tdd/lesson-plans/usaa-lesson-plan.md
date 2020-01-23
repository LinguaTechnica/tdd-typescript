# JavaScript TDD (USAA)

This lesson plan can be used when teaching this unit to USAA cohorts.

## Introduction

XP emphasizes baby steps and feedback loops

In this lesson we will demonstrate these values, principles by:

-  Using compile errors as our first test failures (baby step)
-  Writing tests first so that we know when our code is working (feedback loop)

### TDD
- Slides https://docs.google.com/presentation/d/1zLUC0LkYz2T0EjpT-AExiLgPKivpWR2wtafk9mLGGYE/edit#slide=id.g2187950ca4_0_165

## Live Demonstration
- USE THE ZOOM TOOL

**Strong Voice** During this phase of the lesson:

- Do not type along with me
- Pay close attention to what I am saying
- Take good notes so you can do this on your own later
- Feel free to interrupt at any point if you have questions

We will go through all of this again, together, after this.

`git clone https://github.com/gSchool/tdd-vending-machine`

`cd tdd-vending-machine && npm i`

`npm test` (this should run and fail because there is no test)

Let's do an nzombies analysis on this.  Let's start with constructing the vending machine and looking at it's contents with a method called `seeSelections()`.

```
Write nzombies on whiteboard, then fill out acronym
			| Params 		| Return
Null		|				|
Zero		|				|
One			|				|
___________________________________________
Many		|				|
Boundries	|				|
Inteface	|				|
Exceptions	|				|
Simple		|				|
```

For our params, `seeSelections()` never accepts params, so we can basically skip NZOMBIES analysis for the params. Let's do an NZOMBIES analysis for the return values.

Can it return null? Yes, I will never let that happen, so that is untestable.
Can it return zero? Yes, a new vending machine would be empty, so let's write that test.

in `test/Machine.test.js`

```js
const Machine = require('../src/Machine')

describe('the vending machine', () => {
  it('can be initialized without items', () => {
    const vendingMachine = new Machine()

    expect(vendingMachine.seeSelections()).toEqual([])
  })
})
```

`npm test`

Our goal is not to pass the test, but rather to pass the error in front of us until we pass the test.
Red > Red I'm looking for > Green > Refactor

`mkdir src`

`touch src/Machine.js`

in `src/Machine.test.js`

```js
class Machine {
  constructor() {

  }
}

module.exports = Machine
```

`npm test`

in `src/Machine.js`

```js
class Machine {
  constructor() {

  }

  seeSelections() {
    return []
  }
}

module.exports = Machine
```

`git add -p`

`git commit -m "feat(machine): adds Machine and seeSelections"`

Now in order to see stock, I need to stock the machine.  This is probably a new method, let's call it `stock()`.
Stock is different than seeSelections, as it will take params, but it won't return anything. So we will perform a NZOMBIES analysis on the params.

Can it accept null? Sure, but I can't write that test right now, as it would pass.  Can it accept zero?  Yes, but we can't write that test either right now because it would also pass. These two tests would pass because calling `seeSelections()` currently returns `[]` in both cases. So let's start with one.

in `test/Machine.test.js`

```js
it('can stock one snack', () => {
  //setup
  const vendingMachine = new Machine()
  const snack = {
    name: 'pringles',
    price: 100
  }

  //execution
  vendingMachine.stock([snack])

  //assertion
  expect(vendingMachine.seeSelections()).toEqual([snack])
})
```

`npm test`

in `src/Machine.js` add method

```js
stock() {

}
```

`npm test`

in `src/Machine.js` add method

```js
class Machine {
  constructor() {
    this.snacks = []
  }

  seeSelections() {
    return this.snacks
  }

  stock(snacks) {
    this.snacks = snacks
  }
}
```

`git add -p`

`git commit -m "feat(machine): adds stock"`

Now that I've completed one, I can complete null.  This is a design decision that says be generous with what you accept.  One could decided to throw here based on the philosophy of fail early, it's a tradeoff, welcome to being a developer.

in `test/Machine.test.js`

```js
it('stocks nothing if called with null', () => {
  //setup
  const vendingMachine = new Machine()

  //execution
  vendingMachine.stock() // discuss undefined vs null?

  //assertion
  expect(vendingMachine.seeSelections()).toEqual([])
})
```

in `src/Machine.js`

```js
stock(snacks = []) {
 this.snacks = snacks
}
```

Optional Throw Exception Implementation

in `test/Machine.test.js`

```js
it('throws exception if stock is called with null', () => {
  //setup
  const vendingMachine = new Machine()
  const expectedMsg = "Cannot stock vending machine without snacks";

  //execution + assertion
  expect(() => {
    vendingMachine.stock()
  }).toThrow(expectedMsg);
})
```

in `src/Machine.js`

```js
stock(snacks) {
 if (!snacks) {
    throw Error('Cannot stock vending machine without snacks');
  }
}
```

`git add -p`

`git commit -m "feat(machine): add null stock handling"`

Now that I am able to stock my machine with a snack, I want to be able to purchase that snack.  In order to do that I need to be able to deposit money, and have that tell me how much total money I have deposited.

in `test/Machine.test.js`

```js
it('allows me to deposit money and informs me of my balance', () => {
  //setup
  const vendingMachine = new Machine()
  const amount = 100
  const expected = `You have deposited $${amount}`

  //execution
  const actual = vendingMachine.deposit(amount)

  //assertion
  expect(actual).toEqual(expected)
})
```

`npm test`

in `src/Machine.js` add method

```js
deposit() {

}
```

`npm test`

in `src/Machine.js`
```js
deposit(amount) {
  return `You have deposited $${amount}`
}
```

`git add -p`

`git commit -m "feat(machine): adds deposit"`

Now that I can deposit money, I need to be able to spend it.  This will take a lot more setup.

in `test/Machine.test.js`

```js
it('allows me to buy a stocked item and tells me my remaining balance', () => {
  //setup
  const vendingMachine = new Machine()
  const price = 1
  const deposit = 100
  const snack = {
    name: 'pringles',
    price
  }

  vendingMachine.stock([snack])
  vendingMachine.deposit(deposit)

  const expected = `You have purchased ${snack.name}, and have $${deposit - price}`

  //execution
  const actual = vendingMachine.buy(snack.name)

  //assertion
  expect(actual).toEqual(expected)
})
```

`npm test`

in `src/Machine.js` add method

```js
buy() {

}
```

`npm test`

in `src/Machine.js`

```js
class Machine {
  constructor() {
    this.snacks = []
    this.balance = 0
  }

  seeSelections() {
    return this.snacks
  }

  stock(snacks = []) {
    this.snacks = snacks
  }

  deposit(amount) {
    this.balance = amount
    return `You have deposited $${this.balance}`
  }

  buy(snackName) {
    const snack = this.snacks.find(snack => snack.name === snackName)

    return `You have purchased ${snack.name}, and have $${this.balance - snack.price}`
  }
}
```

## We Do

**Strong Voice** During this phase of the lesson:

- We do this work together
- I will wait to move on until everyone is ready
- If you know what to do next, you can work ahead of me
- Feel free to interrupt at any point if you have questions
- Please pay attention to questions asked by your fellow students

Now that we have the ability to buy, let's work together to implement many and our boundry cases.

in `test/Machine.test.js`

```js
it('can stock multiple snacks', () => {
    // setup
    const vendingMachine = new Machine()
    const cheetos = {name: 'cheetos', price: 3};
    const snicker = {name: 'snicker', price: 2};
    const twizzlers = {name: 'twizzlers', price: 1};

    //exercise
    vendingMachine.stock([cheetos, snicker])
    vendingMachine.stock([twizzlers]);

    // assert
    expect(vendingMachine.seeSelections()).toEqual([cheetos, snicker, twizzlers]);
});
```

in `src/Machine.js` add method

```js
  stock(snacks = []){
    this.snacks = this.snacks.concat(snacks);
  }
```

## You Do

**Strong Voice** During this phase of the lesson you will:
- Work together as pairs
- [TBD]

...

- TDD Shopping Cart - https://prodgitlab.usaa.com/grp-galvanize-class/tdd-shopping-cart

### Stretch Goal
Assuming students worked on solutions to the N-Queens problem during a previous day, have students attempt using their new toolset of NZOMBIES analysis and TDD to drive their solution: https://github.com/gSchool/n-queens-javascript

## Stand down

> Address mis-understandings you observed during class work

### Review Questions
- TBD

## Exit Ticket

> Hand out printed exit-tickets

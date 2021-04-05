# Mocking in JavaScript (USAA)

This lesson plan can be used when teaching this unit to USAA cohorts.

## Prerequisites

- Can TDD pure functions in JS

## Objectives

- Identify pure and impure functions
- Write tests using jest mocks
- Inject test mocks using constructor injection

## Introduction

XP emphasizes quality, in order to write code that is easy to change we need to use dependency injection to decouple functionality.

In this lesson we will demonstrate this principle by writing code that is unit tested even though it has external dependencies.


## Live Demonstration

**Strong Voice** During this part of the lesson:

- Do not type along with me
- Pay close attention to what I am saying
- Take good notes so you can do this on your own later
- Feel free to interrupt at any point if you have questions

We will go through all of this again, together, after this.

### Pure Functions

**On your whiteboard** Define a pure function.

>	- return value solely depends on its arguments
>	- No side effects (like net­work, print, or data­base calls)
>	- Does not mod­ify the argu­ments which are passed to them

Pure functions are easy to test because the output is determined by the parameters.
Every test is some form of given `X` expect `Y` to be returned.

### New Project
First thing I need to do is create an npm project:

`mkdir mocking-lesson && cd mocking-lesson`

`npm init -y`

- review package.json with the students
	- dependency
	- devDependency
	- peerDependency
	- scripts

- package.json definition (via NodeJS): All npm packages contain a file, usually in the project root, called package.json - this file holds various metadata relevant to the project. This file is used to give information to npm that allows it to identify the project as well as handle the project's dependencies. It can also contain other metadata such as a project description, the version of the project in a particular distribution, license information, even configuration data - all of which can be vital to both npm and to the end users of the package. The package.json file is normally located at the root directory of a Node.js project.

**Post in Slack** See `https://docs.npmjs.com/files/package.json` for more information about `package.json`

Now that I have a project, I will start including project dependecies.

### Your first Jest Test

This lesson is about mocking, so I will not be doing `N-ZOMBIES` analysis during this lesson. I will focus on the concept of mocking. After today, all of your tests should be driven by your `N-ZOMBIES` analysis.

In this case, we want `jest`, a unit testing library for JavaScript.

`npm i -D jest`

`touch Dependency.js`

modify package.json test script to be `"test": "jest"`

So lets say we have a dependency that is super expensive, maybe it has to make an HTTP call that takes a long time to return.

We will create a class that simulates doing this, imagine this is an actual call to an API.

We wouldn't want to __actually__ call that API every time we ran the test.

- In `Dependency.js`

```JavaScript
class Dependency {
    constructor() {
        this.data = []
    }

    expensiveFunction() {
        const start = new Date().getTime()
        while (new Date().getTime() < start + 10000) {
        } // Block for 10 seconds
        return 42
    }
}

module.exports = Dependency
```

**cold call** is `expensiveFunction` pure?
> Yes! It takes no parameters and always returns `42`

For the purposes of this lesson, just imagine that dependency was already created and tested.
Also note that in order to show different types of mocking, we won't be doing strict TDD here, we want to show how mocking works.

So now we want to test a class that uses this dependency.

`touch CodeUnderTest.spec.js`

The first thing I'm going to do is make sure my test suite is wired up

- In `CodeUnderTest.spec.js`

```JavaScript
describe('CodeUnderTest', () => {
    it('jest works', () => {
        expect(true).toEqual(false)
    })
})
```

`npm test`


Great, now that we are sure everything is working, let's write our first test without mocking anything.

And, just to be clear, a mock is an object that you can configure with its expected method calls and parameters.

For example, if I create a mock email service, I'll tell it to expect the method call with "sendEmail()" to this address with this content and then the mock object tells you whether or not it recieves that call.

If the mock object recieves a different method call, it'll fail the test. It verifies those method calls itself.

(source: https://www.youtube.com/watch?v=tVCSKsMtXn0)

- In `CodeUnderTest.spec.js`

```JavaScript
const CodeUnderTest = require('./CodeUnderTest')
const Dependency = require('./Dependency')

describe('CodeUnderTest', () => {
    it('should return 1764 (42 * 42)', () => {
        //Setup
        const dependency = new Dependency()
        const codeUnderTest = new CodeUnderTest(dependency)
        const expected = 1764

        //Exercise
        const actual = codeUnderTest.getResult()

        //assert
        expect(actual).toEqual(expected)

        // Teardown
    })
})
```

`npm test`

Great, our test runs! Let's get this thing wired up

`touch CodeUnderTest.js`

- In `CodeUnderTest.js`

```JavaScript
class CodeUnderTest {
  constructor(dependency) {
    this.dependency = dependency
  }

  getResult() {
    return this.dependency.expensiveFunction() * 42
  }
}

module.exports = CodeUnderTest
```

`npm test`

Great the test passes as expected, but look at how long it takes, over 11 seconds!

If this was an API, we would also be hitting it every time,
and we could get rate limited or just use resources for no reason.

Instead we want to use something called a stub.

Stubs are responsible for returning values in a test, that's their whole job. You create a stub object, and they're responsible for handling those indirect inputs into your application. So, if I'm using an object that uses some dependency of my application, I will want to create a stub of that dependency that I can use in my test class.

Stubs don't return anything that isn't specfified, and they don't record the number of interactions they recieve, they're a type of mock that just returns data. Let's fix our test to use a stub.

- In `CodeUnderTest.spec.js`

```JavaScript

const CodeUnderTest = require('./CodeUnderTest')
const Dependency = require('./Dependency')

describe('CodeUnderTest', () => {
    it('return 42 * 42', () => {
        //Setup
        const mockDependency = {
            expensiveFunction: () => 42
        }
        const codeUnderTest = new CodeUnderTest(mockDependency)
        const expected = 1764

        //Exercise
        const actual = codeUnderTest.getResult()

        //assert
        expect(actual).toEqual(expected)
    })
})
```

All I'm doing here is basically saying "When this function is called, just return me 42",
which we can only do effectively because we are injecting our dependency.

This could be rewritten using jest's built in mocks,
which have some nice functionality that we will use later

- In `CodeUnderTest.spec.js` change the mock

```
const mockDependency = {
  expensiveFunction: jest.fn().mockReturnValue(42)
}
```

`npm test`

There we go, we're still passing.

**cold call** What technique are we using to make the `CodeUnderTest` easier to test?
> Dependency Injection

**cold call** Other than testing, what are some other advantages of `Dependency Injection`?
> Change behavior at run time
> Easier to `compose` simple objects into more complex objects.


### Person DAO

Now let's switch to a something a little closer to the real world.

We will write a `DAO` that accesses a database.

Frist, let's create the database. This project is using `SlowDatabase`

- In `SlowDatabase.js` add a constructor and a save method

```JavaScript
class SlowDatabase {
    constructor() {
        this.data = []
    }

    save(newData) {
        const start = new Date().getTime()
        while (new Date().getTime() < start + 5000) {
        } // Block for 5 seconds
        this.data.push(newData)
    }
}

module.exports = SlowDatabase
```

**Cold Call** Is `save` pure?  
> No! So it's going to be harder to test than a pure function.

So let's write the first test.

- In `PersonDAO.spec.js` add a test case

```JavaScript
const SlowDatabase = require('./SlowDatabase')
const PersonDAO = require('./PersonDAO')

it('save Alan Turing', () => {
    //setup
    const database = new SlowDatabase()
    const personDao = new PersonDAO(database)
    const expected = {givenName: 'Alan', familyName: 'Turing'}

    // exercise
    personDao.saveToDatabase(expected);

    // assert
    // **Cold Call** personDao.saveToDatabase and database.save do not return anything. How can I get this test fail?

    // This is a bit strange but for now this is how we know the datbase was called
    expect(database.data[0]).toEqual(expected);
})
```

`npm test` <== Fail

Now make this pass by implementing the saveToDatabase method

- Create `PersonDAO.js ` and add method save
```
class PersonDAO {
  constructor(database) {
    this.database = database
  }

  saveToDatabase(person) {
    this.database.save(person)
  }
}

module.exports = PersonDAO
```

`npm test`

Now we're passing, but it takes a long time and would actually write to the DB.

Let's remove this implementation and drive it out using a `spy`.

- In `PersonDAO.js ` add method save

```
saveToDatabase(person) {

}
```

A spy is sort of a combination of a mock and a stub. A spy allows you to configure what type of data you want to return and it also records your method calls for you. The main difference is that spies do not only record the method calls, they typically record other information too.

Spies also allow you to verify method calls and parameters.

So for example, if you have a spy email service - inside your test you want to tell it that you should send 10 emails with this email service when this thing happens, instead of adding 10 verify calls where you sepearately verify that these emails were sent, the spy gives you access to say Hey, verify that 10 emails were sent and that they were sent to these emails addresses. It just makes it easier to verify that data instead of having to declare everything in order.

A spy is a mock that records what it is called with, this way we can define how we want to use the dependency.

Let's rewrite this test.

- In `PersonDAO.spec.js` change the test case
```
it('save Alan Turing, () => {
    //setup
    const mockSave = jest.fn();
    const mockDatabase = {save: mockSave}
    const personDAO = new PersonDAO(mockDatabase)
    const expected = {givenName: 'Alan', familyName: 'Turing'}

    // exercise
    personDAO.saveToDatabase(expected);

    // assert
    expect(mockSave).toHaveBeenCalledWith(expected);
})
```

`npm test` <== Fail

Now that I have a failing test I can write the implementation

- In `PersonDAO.js ` add method save
```
saveToDatabase(person) {
  this.database.save(person)
}
```

`npm test` <== pass


Let's say we wanted to save a person in our application, other code could directly call the DB writer, but we don't want to do this because then when we change our DB, we have to change it everywhere in the app.

By using dependency injection, not only can we test it better, but it means the code is decoupled, so if we want to change the DB, all we need to do is change one line of code.

## We Do

## You Do

**Strong Voice** During this phase of the lesson you will:
- Work together as pairs
- Solve this according to the directions provided

**Post in slack** https://github.com/gSchool/populatron_javascript

## Stand down

> Address mis-understandings you observed during class work

## Exit Ticket

> Hand out printed exit-tickets

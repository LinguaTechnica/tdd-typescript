# Shopping Cart


<!--BEGIN CHALLENGE-->

### !challenge

* type: project
* id: 0ce9c4d9-c962-485d-ba3b-9a533369616f
* title: Submit Your Work

##### !question

Time to practice your new Typescript skills. Use tests to build a simple Shopping Cart application.

## Instructions

1. Fork [this repository](https://github.com/gSchool/tdd-shopping-cart-ts).
1. Share the repo with your group. Each person should submit the same link!
1. Submit your work.

At the end of today you'll have an opportunity to discuss and share your code with the rest of the class.

### Stories and Acceptance Criteria

Ali Snobba has given you the following criteria to determine completeness of your project. Note that there are no code implementation details. So you must collaborate with your partner on how best to implement the application.

`Story: As a shopper, I want to have a shopping cart, so I can store items until I am ready to checkout.`

1. Given that I'm new shopper, when I begin shopping, then I expect my cart to be empty.
1. Given I have an empty cart, when I add an Item, then I expect the price to reflect the sum of all the Items in my cart.
1. Given I have an empty cart, when I add items, then I expect it to see an itemized list of the items along with their price and quantity.
1. Given I have cart with one item, when I add more of that item, then I expect to see its quantity updated on the itemized list.
1. Given I have a cart with items, when I remove an item, then I expect the cart to display the updated itemized list.
1. Given I have one item in my cart with a quantity of 3, when I remove one, then I expect the cart to have 2 of that item.

### Stretch Goals (OPTIONAL)

A coupon is an object that has an item name and a price. The price on a coupon is deducted from the price of the item.

`Story: As a customer, I want to apply a coupon to my order, so I can take advantage of current sales.`

* Given I have a cart with items, when there are 2 of the same item in the cart, then those items are discounted as 2 for the price of 1.
* Given I have a cart of items, when an item is on sale, then it receives a 25% discount.
* Given I have multiple coupons, when any items match the coupon, then the coupon discounts can be applied multiple times to the same items.
* Given I have a coupon for my cart, when no item matches the coupon, then the coupon discount is not applied.

### Tips

- Use [es6 getters](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/get) to simplify your task.
- Use [es6 template literals](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals) instead of String concatenation
- Use [map, filter, and reduce](https://danmartensen.svbtle.com/javascripts-map-reduce-and-filter) to avoid looping

### Resources

- [Typescript Handbook](https://www.typescriptlang.org/docs/handbook/2)

## Submit Your Work 

##### !end-question

##### !placeholder

Link to your repository

##### !end-placeholder

##### !rubric

See the [Language rubric in the Student Worksheet](https://docs.google.com/spreadsheets/d/1XMK4CVC7OFgpD8jvt6M85TiUF0-feOZcpDUU1QsFOoU/edit?usp=sharing) if scoring is being applied.

Otherwise, a point is assigned for submitting the work. Instructors can review the code.

##### !end-rubric

### !end-challenge

<!--END CHALLENGE-->
# Mortgage Lender

Every day, potential buyers are looking for a lender to finance their new home. Let's build an app to simulate a
potential (and grossly over-simplified) process for lenders to qualify and approve loan applicants. The process can be summarized:

An applicant submits an application for a loan. The lender will then check that the applicant qualifies before approving the application. If the application is approved, the lender offers a loan amount for which the candidate qualifies. For example, if an applicant applies for $100,000, the lender may decide that the applicant only qualifies for $75,000 and send them an offer for that amount. The applicant must then decide to accept or reject the loan offered. Once an offer is accepted, the lender gives the money to the candidate to purchase their new home.

<!--BEGIN CHALLENGE-->

### !challenge

* type: project
* id: 6c59d25d-4251-4123-9793-ec1026752429
* title: Submit Your Work
* points: 3
* topics: typescript, tdd

##### !question

## Instructions

1. Fork [this repository](https://github.com/gSchool/mortgage-lender-ts).
1. Share the repo with your group. Each person should submit the same link!
1. Submit your work.

### Objectives

Use what you've learned about pair programming, the test cycle, and OOP to fulfill the acceptance criteria.

Your final code should have:

1. No compile errors.
2. No failing tests.
3. Descriptive commit messages.
4. Multiple commits.
5. Meet acceptance criteria.

**Tips**

Apply what you've learned so far.

- Write tests first
- Use AAA to guide you
- Use red green refactor

### Stories and Acceptance Criteria

As a lender, I want to be able to check my available funds, so that I know how much money I can offer for loans.

```gherkin
When I check my available funds
Then I should see how much funds I currently have
```

As a lender, I want to add money to my available funds, so that I can offer loans to potential home buyers.

```gherkin
Given I have <current_amount> available funds
When I add <deposit_amount>
Then my available funds should be <total>

Examples:
| current_amount | deposit_amount |   total  |
|     100,000    |      50,000    | 150,000  |
|     200,000    |      30,000    | 230,000  |
```

As a lender, I want to approve or deny loans base on available funds, so that I don't go bankrupt.

```gherkin
Given I have <available funds> in available funds
When a qualified applicant applies for <loan amount> loan
Then the loan is <loan status>

Example:
| loan amount | available funds | loan status |
|   125,000   |    100,000      |    denied   |
|   125,000   |    200,000      |  approved   |
|   125,000   |    125,000      |  approved   |
```

As a lender, I want to qualify loan applications, so that I can ensure I get my money back.

```gherkin
Rule: Qualifying candidates must have debt-to-income (DTI) less than 36%, 
      credit score above 620 and savings worth 25% of requested loan amount.

Given a loan applicant with <dti> DTI, <credit score> credit score, and <savings> savings
When they apply for a loan
Then their qualification is <qualification>

Example:
|  loan amount  |   dti  |  credit score  |  savings  |  qualification |
|    250,000    |   21   |       700      | 100,000   |      true      |
|    250,000    |   37   |       700      | 100,000   |     false      |
|    250,000    |   30   |       600      | 100,000   |     false      |
|    250,000    |   30   |       700      |  20,000   |     false      |
```

As a lender, I want to keep pending loan amounts in a separate account, so I don't extend too many offers and bankrupt myself.

```gherkin
Given I have approved a loan
When a loan offer is sent
Then the requested loan amount is moved from available funds to pending funds
And the loan status is marked as pending
```

As a lender, I want to receive response for loan offers, so that I can update the status of pending loans.

```gherkin
Given I have sent a loan offer to a qualified applicant
When the applicant accepts my loan offer
Then the loan amount is removed from the pending funds
And the loan status is marked as accepted

Given I have sent a loan offer to a qualified applicant
When the applicant rejects my loan offer
Then the loan amount is moved from the pending funds back to available funds
And the loan status is marked as rejected
```

As a lender, I want to set an expiration date of 3 days on all loan contracts, so that I can manage my time and money wisely.

```gherkin
Given I have sent a loan offer to a qualified applicant,
When the applicant does not accept my loan contract within 3 days,
Then the loan amount is move from the pending funds back to available funds
And the loan status is marked as expired
```

##### !end-question

##### !placeholder

Link to your repo goes here.

##### !end-placeholder

##### !rubric

See the [Language rubric in the Student Worksheet](https://docs.google.com/spreadsheets/d/1XMK4CVC7OFgpD8jvt6M85TiUF0-feOZcpDUU1QsFOoU/edit?usp=sharing) if scoring is being applied.

Otherwise, a point is assigned for submitting the work. Instructors can review the code.
##### !end-rubric

### !end-challenge

<!--END CHALLENGE-->
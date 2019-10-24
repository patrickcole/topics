# Code Procedures

## Clean Code

### Everyone will benefit

- having clean, readable code will help everyone understand your intent, including you!

### In the future

- think about the future when you or someone else has to come back and read/interpret your code

### Bad Code will duplicate if not fixed

- bad code habits breed more bad code habits
- if something looks bad and you have the luxury of time, spend the time to refactor it, you'll thank yourself later
- messy code will be harder to clean up later on, possibly when crunch time hits

### Better Code = Better Procedures

- having good procedures for good, clean code will help in future procedures/decisions for code
- review some common comment styles/syntaxes to get an idea of what are best practices, start using them

### Write DRY Code

- don't overdo it, don't abstract too far where it's not readable
- having DRY code will make things easier to understand and follow later on
- less confusion if things are not repeated, for example naming something `ArrayOfUnreadMessages()` and another `UnreadArray()` causes confusion of which one is the intent/standard

### Get The Satisfaction

- by writing good code, you'll be more satisfied with yourself
- it gives you positive reinforcement that you are doing a great job

[source](https://dev.to/paulasantamaria/clean-code-why-bother-21lo)

---

## More Advantages to Good Code Practices

### Single Responsibility Principle

- don't have code that does multiple things, create functions that perform singular operations
- this way, logic and process is easier to follow
- less "side-effects" if functions are performing single actions

### Reviewing Code for Pull Requests is Easier

- those reviewing your important pull request will be able to understand why it's soo important if code is done well
- messy/bad code just complicates the process

### Resolve Bugs Quicker

- easy to follow, well-formed code will be easier to debug than messy code
- reiterating the single-responsibility principle; by having functions that handle one action will make following the execution process much smoother when something goes wrong

### Remember That Best Practices Can Change

- be open to new changes when they are announced
- remember that we are always learning and evolving our methods to write code (i.e. hooks in React now instead of life cycle methods)

[source](https://dev.to/paulasantamaria/clean-code-why-bother-part-2-1eme)

---

## Things to Remember

### Standardize code formatting

- use jslint, eslint or some other code guide like airbnb
- prettier can help format code to follow rules on save/export

### Don't get too deep in DRY

- don't abstract so much that it's unreadable
- apply "the rule of three" if you see the same thing repeated more than 2x, DRY it up

### Debug via logs instead of via console

- provide log files without debug outputs
- good for comparison over time to see code progression
- do not clutter logs with simple "here" logs in production

### Beware of premature code optimizations

- always perform an audit of your code before you make the decision to optimize it
- sometimes the changes you could imagine might be negligible in the long run and you've spent time on them instead of more features

### Don't complicate codebase with unnecessary features

- only implement what is in the requirements
- provide the features called for first, then suggest new features before implementing them
- unexpected features can confuse and complicate code execution

### Setup testing environment early in development cycle

- fail fast! test often!
- have the system in place to perform tests right away
- each new implementation of code will solve tests and solidify code base

[source](https://dev.to/mohanarpit/coding-practices-your-future-self-will-love-you-for-ohe)

---

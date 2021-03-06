# Advanced Class: Unit Testing and OO Design

<br/>

>This is a summary of the Advanced Session taught on March 29, as part of the accelaration program at [Codaisseur](https://codaisseur.com/). The **learning goals** of the day are: 
>
>* Understand basic concepts OO Design
>* Understand basic concepts of good Unit Testing
>* Get some experience with Unit Testing
>* Practice  Pair Programming

<br/>

## Types of tests
![Types of test](https://pbs.twimg.com/media/CevWKfrW4AAeJjK.jpg:large)
_1) **Manual/Exploratory tests** (Manual test technique, can't be automated)_

_2) **End to end tests** (The whole system from one end to another end)_

_3) **Integration tests** (Realy calls the db, test multiple components)_

_4) **Components tests** (Testing multiple units)_

_5) **Unit tests** (Smallest test possible)_

### The V-model
![The V model](https://thumb7.shutterstock.com/display_pic_with_logo/4082620/427973527/stock-vector-v-model-software-development-427973527.jpg)

_The higher you get, the slower your tests are_

### Contemporary ways of testing
![UI/Service/Unit](https://martinfowler.com/bliki/images/testPyramid/test-pyramid.png)


<br><br>

## Unit Testing
### What is unit testing?
* Testing the **smallest testable part** of a system (Could be method, a class, a module, etc.) in isolation.

### Why?
* It is about **verifying expectations** - does this do what I expect it does?
* Unit testing helps not only to reduce bugs, but also **reduce bug-fix-time**.

### How does it work?
1) You have a **test runner** (such as Jest, Enzyme, JRuby) which has a
2) **Test framework** (with some helper methods such as `expect`)
3) The test runner runs your **test class** (test code) which verifies your **production code**.

### How to use it:
#### How To Fix A Bug
1) Reproduce it with a (new) unit tests(s). (The test should fail)
2) Fix your production code.
3) Run all your tests. All should pass.

#### How to commit your code
1) (Code should compile/build)
2) Run all Unit Tests
3) If all tests pass: Commit. Else, fix code to make test pass.

### What to test:
* **Boundaries** (min, max, exactly)
* **Error-conditions**
* **Happy Path**
* **Dependencies**
* ( **Properties** (such as get/set) - _topic of debate_)

### How to structure your test:
1) You set up an environment (**Arrange**)
2) You perform a certain action (**Action**)
3) You verify your expectation (**Assert**)

_Use only one Assert per test!_

<br/><br/>

## Fakes

Fakes are tools to write (UNIT) tests, to manage dependencies, to not let good design interfere with your testability.

### Fake Object
* Always returns a constant
```
when object.doSomething(anyArgument) then 
  return "Foo"
```
### Stubs
* Returns default (or predefined) output

```
when object.doSomething("Foo" ) then 
  return "Bar"
```

### Mocks
* Verify interactions
```
when object.doSomething("Barz") then
  return "Has been clicked"
```

<br/><br/>

## SOLID Principles

![Solid Explanation](https://devscopeninjas.azurewebsites.net/wp-content/uploads/2017/04/Solid-1024x283-1024x283.jpg)

### Single Responsibility Principle
* Anything (function, model, class, etc.) should only have **one reason to change**.
* Closely connected to the idea of **separation of concerns**.

### Dependency Inversion Principle
* **Dependency injection** is an implementation of this principle
* **Low level modules should depend on high level modules**, not the other way round.
* **Abstractions should not depend upon details**, details should depend upon abstractions.
* Definition of bad design: **Rigidity** (hard to change), **Fragility** (other stuff breaks if change something), **Immobility** (Can it be reused or is it hard to disentangle from another application)
* You are looking for **one way dependencies**:

  _A service namespace might depend on a model and parsers, the parsers on a model, but the model shouldn't also depend on the service or parsers!_

* **Regression**: you introduce something new and code you wrote before fails

<br/><br/>

## Separation of concerns
Given are two structures: 

  * Presentation Layer
  * Logic layer
  * Data Access layer

  and:

  * Service Interface Layer
  * Logic Layer
  * Data Access Layer

They are both **connected vertically** in terms of dependencies.

Imagine the first would be a `mail` module and the second an `auth` module, you could also **connect them horizontally** - the Micro Services SetUp.

<br/><br/>

## Dynamically vs Statically Typed

* **Dynamically typed** - types are checked _in run time_.
  * Duck typing: if it quacks like a duck and it looks like duck it probably is duck, but we are not going to check.
* **Statically typed** - types are checked _in compiler time_.

<br/><br/>

## Interesting Sources


* [The Clean Code Talks: Unit Testing](https://www.youtube.com/watch?v=wEhu57pih5w)
* [Solid Cheat Sheets](https://www.monterail.com/blog/solid-principles-cheatsheet-printable)

> _This Repository is created by Mimi Magusin. Her personal profile can be found [here](https://github.com/MimiMagusin), her Codaisseur Profile can be found [here](https://github.com/MimiMag)._

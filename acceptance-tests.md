- [Acceptance Tests](#acceptance-tests)
  - [How to implement acceptance tests](#how-to-implement-acceptance-tests)
    - [Four layers of acceptance tests](#four-layers-of-acceptance-tests)
  - [Example: Buying a book from a store](#example-buying-a-book-from-a-store)
    - [What are the steps?](#what-are-the-steps)
      - [Gherkin](#gherkin)
  - [Test Cases](#test-cases)
  - [DSL](#dsl)
    - [Custom DSL](#custom-dsl)
      - [Custom DSL example](#custom-dsl-example)
    - [Cucumber](#cucumber)
  - [Protocol driver](#protocol-driver)
    - [Using various drivers](#using-various-drivers)
  - [System under test](#system-under-test)

# Acceptance Tests

[How to Write Acceptance Tests](https://www.youtube.com/watch?v=JDD5EEJgpHU)

[Github example](https://github.com/davef77/acceptance-testing/tree/master)

* Define the behaviour that we want from our system
* Act as an executable specification that guides development and verifies that the system meeets the specification
* Meant to test general behaviour of the system, not every single input. Avoid overtesting in BDD scenarios.
* Work best in combination with other forms of automated testing. Test tiny differences in unit tests.

How do you know if you have your specifications right? Ask yourself, can you imagine your spec working as an example in the documentation of your system?

## How to implement acceptance tests

Each scenario should validate a single outcome.

### Four layers of acceptance tests

Test Case -> DSL -> Protocol Driver -> System Under Test

* **test cases**: executable specification in the language of the problem domain only talking about what the system needs to do
* **dsl**: set of shared-actions run by the test layer
* **protocol driver**: translate from the language of the problem domain into the language of the system and the first layer to know how to interact with the system
* **system under test**: running in a prod-like environment

## Example: Buying a book from a store

User story: I can buy a book and pay with my credit card.

### What are the steps?
1. Go to the store.
2. Search for a book.
3. Put the book in the shopping cart.
4. Go to the checkout.
5. Pay for the book.

User stories should be written in text and committed to the repository. One commonly-used DSL for writing stories is Gherkin.

#### Gherkin

Plain-text, DSL used for describing the behavior of software systems in a structured and human-readable format. Designed to be easy to understand by both technical and non-technical team members. It uses a specific syntax that includes keywords such as Given, When, Then, And, and But to create feature files that outline the expected behavior of a system.

```
Feature: Buying a Book with a Credit Card

  Scenario: Purchase a Book using a Credit Card
    Given the user goes to the online store
    When they search for a book with the title "Continuous Delivery"
    And they select a book by the author "David Farley"
    And they add the selected book to their shopping basket
    And they proceed to check out with the item "Continuous Delivery"
    Then they should see a successful purchase confirmation for the item "Continuous Delivery"

```

## Test Cases

* Written from the perspective of an external user of the system. 
* Written before development to help drive development.
* Say what the system does, not how it does it.


## DSL

### Custom DSL

* Written in code using the language of the problem domain.
* Designed to make it easy to create test cases.
* Simple to read.
* Provides a set of actions required for test cases which are shared between test cases so we get reuse.
* Actions are repeatable and deterministic.

**Goal with a DSL is to make it easy to write test cases.**

#### Custom DSL example

```java
@Test
public void shouldBuyBookWithCreditCard() {
	shopping.goToStore();
	
	shopping.searchForBook("title: Continuous Delivery");
	shopping.selectBook("author: David Farley");
	
	shopping.addSelectedItemToShoppingBasket();
	
	shopping.checkOut("item: Ciontinuous Delivery");
	
	shopping.assertItemPurchase("item: ContinuousDelivery);
}
```

**Example of a checkout implementation**
```java
public void checkOut(String… args) {
	Params params = new Params(args);
	String item = params.Optional("item", "Continuous Delivery");
	String price = params.Optional("price", 12.24);
	Card card = parseCard(params.Optional("card" …);
	
	driver.checkout(item, price, card);
}	
```

### Cucumber

Testing framework that works with Gherkin to enable BDD practices. Cucumber allows teams to write automated tests in a way that aligns with Gherkin's plain-text format. These tests are known as "step definitions."

Cucumber acts as an intermediary between the plain-text Gherkin scenarios and the actual code that performs the testing. It interprets the Gherkin statements and maps them to the corresponding step definitions in code.

Cucumber takes the steps defined by the annotations and runs them in order as defined by the Cucumber scenarios. This means steps can be reused. Also, the internals of the test can use a custom DSL.

**Example using Cucumber and custom DSL**
```java
public class ShoppingSteps {

    @Given("the user goes to the online store")
    public void goToStore() {
		shopping.goToStore();
    }

    @When("they search for a book with the title {string}")
    public void searchForBook(String title) {
		shopping.searchForBook("title: Continuous Delivery");
    }

    @And("they select a book by the author {string}")
    public void selectBook(String author) {
       shopping.selectBook("author: David Farley");
    }

    @And("they add the selected book to their shopping basket")
    public void addSelectedItemToShoppingBasket() {
        shopping.addSelectedItemToShoppingBasket();
    }

    @And("they proceed to check out with the item {string}")
    public void checkOut(String item) {
        shopping.checkOut("item: Ciontinuous Delivery");
    }

    @Then("they should see a successful purchase confirmation for the item {string}")
    public void assertItemPurchase(String item) {
        shopping.assertItemPurchase("itemL ContinuousDelivery);
    }
}
```

## Protocol driver

Still uses the abstract language of the problem domain, but it's job is to translate this language to real interactions with the system under test.

It's the only part of the test infrastructure that understandds "how". For example, if you're testing the UI, you might use Selenium to drive the test.

These details are hidden from higher levels. In the test case you don't say things like "search for this box" or "click on this button", you say "buy a book." The protocol driver knows what it should do.

**Example**

```java
@Overrid
public void addSelectedItemToShoppingBasket() {
	WebElement buyButton = driver().findElement(…
	
	butButton.click();
}
```

### Using various drivers

It can be effective to "plug-in" different drivers. For example, if you have a Web site and an API, you can test `placeOrder` via both Ui and API drivers.

* Web
* API
* External system stub

## System under test

Deployed in a production-like environment. It could be software, but it could even be a real store using, for example, a robot to perform the actions. The abstractions at the upper layers allow us to separate what we are testing from how we are testing it.

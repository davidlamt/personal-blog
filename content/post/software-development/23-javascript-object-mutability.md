---
title: "JavaScript Object Mutability"
date: 2017-09-14T06:37:08-07:00
publishdate: 2017-10-01
draft: false
slug: "javascript-object-mutability"
categories: ["Software Development"]
---

In a [previous post](/var-vs-let-vs-const), I discussed how declaring variables (and functions) with `const` helps prevent state changes.

**Unexpected state changes are one of the most common causes for bugs**. As a result, it is desirable to prevent unexpected state changes from occuring in the first place.

One method is to declare variables using `const` as that makes the variable *constant*. However, as stated in the previous post, `const` declarations do not make JavaScript objects immutable.

## JavaScript Objects

Let's run some experiments on a JavaScript object declared with the `const` keyword.

```js
const person = {
    name: 'David',
    age: 23,
    awesomeness: 10
};

person = {
    name: 'Josh'
};
/*
 * "TypeError: Assignment to constant variable."
 *
 * A const object cannot be redefined - good.
 */

person.awesomeness = 0;

console.log(person);
/*
 * {
 *     name: 'David',
 *     age: 23,
 *     awesomeness: 0
 * }
 *
 * What the? This cannot be true. I am truly awesome.
 * Plus, why the heck can I change a variable declared as const?
 */

person.sucks = true;

console.log(person);
/*
 * {
 *     name: 'David',
 *     age: 23,
 *     awesomeness: 0,
 *     sucks: true
 * }
 *
 * No no NO! I do not suck!
 * And I should not be able to add another property to a const definition!
 */
```

Apparently, `const` objects **can have existing properties redefined and be assigned new properties**.

Well, at least, the variable cannot be redefined.

What if you want an object to be immutable? For instance, a pseudo-enumeration variable.

```js
const DRINKING_AGE = {
    CALIFORNIA: 21,
    PUERTO_RICO: 18,
    // ...
};
```

## Immutable Objects

The `Object.freeze()` method **prevents existing properties from being modified and new properties from being added**.

Let's see an example!

```js
const DRINKING_AGE = Object.freeze({
    CALIFORNIA: 21,
    PUERTO_RICO: 18,
    // ...
});

DRINKING_AGE.CALIFORNIA = 15;

console.log(DRINKING_AGE);
/*
 * {
 *     CALIFNORIA: 21,
 *     PUERTO_RICO: 18
 * }
 *
 * Perfect, we cannot modifiy an existing property.
 * Nice try, minor!
 */

DRINKING_AGE.UTAH = 15;

console.log(DRINKING_AGE);
/*
 * {
 *     CALIFNORIA: 21,
 *     PUERTO_RICO: 18
 * }
 *
 * There we go, no new properties can be added.
 * Valiant effort but you are getting quite annoying.
 */
```
---
title: Vue Directives
Date created: 2024-06-11 11:13
Aliases:
tags: 
  - Public
---

Directives are special attributes provided by Vue to apply special reactive behaviour to the rendered DOM. Directives are prefixed with `v-`.

[List of built-in directives in Vue](https://vuejs.org/api/built-in-directives.html#v-html)

Directives have single [[JavaScript Expression]] attribute (with exception of `v-for`, `v-on` and `v-slot`) ant they reactively apply updates to the DOM when the expression value changes

![[Pasted image 20240611123245.png]]

## Arguments

Arguments are denoted by a colon after directive name and can be used to specify a HTML attribute

```html
<a v-bind:href="url"> ... </a>

<!-- shorthand -->
<a :href="url"> ... </a>
```

### Dynamic Arguments

Expressions can be used as a directive arguments by wrapping with square brackets

```html
<a v-on:[eventName]="doSomething"> ... </a>

<!-- shorthand -->
<a @[eventName]="doSomething"> ... </a>
```

Dynamic arguments are expected to evaluate to either a string or `null`. If the value will be `null` the binding is removed

### Constraints
- Certain characters such as spaces and quotes are invalid inside HTML attribute names
- For **in-DOM** templates uppercase characters will be forced into lowercase, breaking the code

## Modifiers
Modifiers are postfixes indicating that the directive should be bound in a special way 
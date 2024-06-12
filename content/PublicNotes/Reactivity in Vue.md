---
title: Reactivity in Vue
Date created: 2024-06-11 12:36
Aliases:
tags: 
  - Public
---

(Examples use [[Vue.js#API options|Composition API]])

To achieve [[Reactive Programming|reactivity]] Vue uses a dependency tracking system. When a component is rendered Vue tracks `ref`s that were used during the render, when one of them is mutated  it will trigger a re-render.

Because there's no way to detect access or mutation of plain variables in JavaScript, [[Ref Object|Ref Objects]] are used to intercept get and set operations and track used values or trigger changes to the DOM.

Refs can also be passed into functions, while retaining access to the latest value and reactivity connection.

## Deep Reactivity and Shallow Refs

Refs make their values deeply reactive, meaning that changes will be detected even when mutating nested objects or arrays. 

To opt-out of deep reactivity, you can use [[Shallow Ref|Shallow Refs]] for which only `.value` access is tracked for reactivity. This can optimize performance or be useful when inner state is managed externally.

## DOM Update Timing
Mutating reactive state changes [[DOM]] automatically, it is however asynchronous, waiting for the update cycle. To wait for completed DOM update after state change use `nextTick()` global API

```js
import { nextTick } from 'vue'

async function increment() {
  count.value++
  await nextTick()
  // Now the DOM is updated
}
```

## `reactive()` API

As an alternative to the `ref()` function wrapping a value in a special object, `reactive()` function makes an object itself reactive by creating a [[JavaScript Proxy]] object intercepting the access and mutation of all properties.

Similar to `ref()` it is deeply reactive and can be opted-out of with `shallowReactive()`

Because the API returns a proxy, the returned value is **not** equal to the original object, and only the **proxy** is reactive - changes to the original object will not trigger updates. It is recommended to **exclusively use the proxied versions of your state**

Calling `reactive()` on the same object always returns the same proxy, and calling it on an existing proxy also returns that proxy.

### Limitations
- Limited value types - only works for object types, doesn't work for primitive types
- Inability to replace - because of the need to keep the reference, we can't replace a reactive object
- Not destructure-friendly - when destructuring reactive object's primitive property into local variable or pass it into a function we loose reactivity connection
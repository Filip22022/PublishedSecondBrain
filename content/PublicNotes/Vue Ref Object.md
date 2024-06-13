---
title: Vue Ref Object
Date created: 2024-06-11 12:56
Aliases:
tags: 
  - Public
---

Ref Objects are wrappers for values in [[Vue.js]] that track the changes to a variable to make it reactive

see also [[Vue Template Refs]]
## Declaring a Reactive State
Declaring is done using the `ref()` function which wraps the argument within a ref object with a `.value` property
```js
import { ref } from 'vue'

const count = ref(0)

console.log(count) // { value: 0 }
console.log(count.value) // 0

count.value++
console.log(count.value) // 1
```

Accessing refs in a component's template is done by returning refs from a `setup()` function and referencing in the template
```js
import { ref } from 'vue'

export default {
  // `setup` is a special hook for the Composition API.
  setup() {
    const count = ref(0)

    // expose the ref to the template
    return {
      count
    }
  }
}
```

```html
<div>{{ count }}</div>
```

>[!Tip] Unwrapping
> There's no need to use `.value` when using the ref in the template. For convenience refs are automatically unwrapped in the templates
> >[!Warning] 
> Ref unwrapping only applies if the ref is a top-level property in template render context
> for:
> 	const count = ref(0)
> 	const object = { id: ref(1) }
> 	
> 	{{ count + 1 }} //works
> 	{{ object.id + 1 }} //doesn't work


## Mutating Refs

Mutating can be done directly in event handlers:
```html
<button @click="count++">
  {{ count }}
</button>
```

alternatively for more complex logic, we can define functions, expose them and use as event handlers

```js
import { ref } from 'vue'

export default {
  setup() {
    const count = ref(0)

    function increment() {
      // .value is needed in JavaScript
      count.value++
    }

    // don't forget to expose the function as well.
    return {
      count,
      increment
    }
  }
}
```

```html
<button @click="increment">
  {{ count }}
</button>
```



## Exposing State and Methods

To avoid verbose exposing via `setup()` in [[Single-File Components]] we can simplify the usage with `<script setup>`

Top-level imports, variables and functions declared are automatically usable in template of the same component
---
title: Vue Template Refs
Date created: 2024-06-12 16:42
Aliases:
tags: 
  - Public
---
see also [[Vue Ref Object]]

In cases where we need direct access to the [[DOM]] elements we can use the `ref` *attribute* that allows us to get a direct reference to a specific element. 

```html
<input ref="input">
```

To obtain the reference declare a ref that matches the attribute name
```vue
<script setup>
import { ref, onMounted } from 'vue'

// declare a ref to hold the element reference
// the name must match template ref value
const input = ref(null)

onMounted(() => {
  input.value.focus()
})
</script>

<template>
  <input ref="input" />
</template>
```

If watching the changes of a ref in a template expression make sure to account for the `null` value, since the element only exists after the first render.

```js
watchEffect(() => {
  if (input.value) {
    input.value.focus()
  } else {
    // not mounted yet, or the element was unmounted (e.g. by v-if)
  }
})
```

## `v-for`
To access a ref attribute from a `v-for` [[Vue Directives|directive]] the script ref should contain an Array value. 
The ref array **does not guarantee** the same order as the source array.

```vue
<script setup>
import { ref, onMounted } from 'vue'

const list = ref([
  /* ... */
])

const itemRefs = ref([])

onMounted(() => console.log(itemRefs.value))
</script>

<template>
  <ul>
    <li v-for="item in list" ref="itemRefs">
      {{ item }}
    </li>
  </ul>
</template>
```

## Function Refs
Instead of using a string key, the `ref` attribute can also be bound to a function, which will be called on each component update. The function receives the element reference as first argument.

```html
<input :ref="(el) => { /* assign el to a property or ref */ }">
```
Here a dynamic `:ref` binding is used. When the element is unmounted the value will be null. A method can also be used instead of an inline function

## Component Refs

The attribute can also be used on a child component. The reference in this case will be of component instance. 
When using `<script setup>` the component is private by default, so the reference won't be able to access anything unless the child component exposes a public interface using `defineExpose`

```vue
<script setup>
import { ref } from 'vue'

const a = 1
const b = ref(2)

// Compiler macros, such as defineExpose, don't need to be imported
defineExpose({
  a,
  b
})
</script>
```
The instance of this component via template refs will be `{ a:number, b:number}` as refs are automatically unwrapped
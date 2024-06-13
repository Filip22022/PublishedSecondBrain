---
title: Single-File Components
Date created: 2024-06-12 09:19
Aliases: SFC
tags: 
  - Public
---

Single-File Components (abbreviated as SFC, with `*.vue` extension) are a file format encapsulating template, logic and styling of a [[Vue Components|Vue Component]] in a single file.

These files are a defining feature of the framework and the recommended approach. They do, however, require a build step in exchange for their optimisation so they may not be appropriate for all scenarios.

## Example
```vue
<script setup>
import { ref } from 'vue'
const greeting = ref('Hello World!')
</script>

<template>
  <p class="greeting">{{ greeting }}</p>
</template>

<style>
.greeting {
  color: red;
  font-weight: bold;
}
</style>
```

The SFC files compile into standard JavaScript module, and with proper build setup should allow components to be imported like the following:

```js
import MyComponent from './MyComponent.vue'

export default {
  components: {
    MyComponent
  }
}
```


## Syntax

Each `*.vue` file consists of three types of top-level language blocks:
### `<template>`
The html template of the component, the contents will be pre-compiled by `@vue/compiler-dom` into JS render functions and attached to the component as it's `render` option
### `<script>`
A JS script executed as a module, with the default export being Vue component options object
### `<script setup>`
An additional script allowed with `setup` attribute exposing the top-level bindings to the template. It's pre-processed for the component's `setup()` function and is executed for **each instance** of the component
### `<style>`
A `*.vue` file can contain multiple `<style>` tags, which define the css styles for the component

### Custom Blocks
Custom blocks such as `<query>` or `<docs>` can be added

## Comments
In SFC files comments should be made using the language of the block they are in. For top-level comments use HTML syntax
`<!-- comment contents here -->`
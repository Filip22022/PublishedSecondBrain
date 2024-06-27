---
title: Vue Components
Date created: 2024-06-12 09:42
Aliases:
tags: 
  - Public
---

Components are independent reusable UI pieces in [[Vue.js]]. An app is commonly organised into a tree of nested components, similarly to how native HTML elements are nested but with encapsulated logic in each component.

## Defining a Component
Vue components are typically defined in a [[Single-File Components|Single-File Component]] with a `*.vue` extension, but can also be defined as plain JavaScript object containing Vue-specific options:
```js
import { ref } from 'vue'

export default {
  setup() {
    const count = ref(0)
    return { count }
  },
  template: `
    <button @click="count++">
      You clicked me {{ count }} times.
    </button>`
  // Can also target an in-DOM template:
  // template: '#my-template-element'
}
```
 But the SFC's are the way recommended by the framework

## Using a Component

To use a component we need to import it in the parent component.
```vue
<script setup>
import MyComponent from './MyComponent.vue'
</script>

<template>
  <h1>Here is a child component!</h1>
  <MyComponent />
</template>
```

The component is automatically available to the template because of the use of `<script setup>`. Alternatively it's possible to globally register a component.

If not using in-DOM templates, it's recommended to use `PascalCalse` tag names for components, and using `/>` to close a tag is possible.

## Content Distribution
To pass content to a component in the following fashion:
```vue
<AlertBox>
  Something bad happened.
</AlertBox>
```

use Vue's `<slot>` element:
```vue
<!-- AlertBox.vue -->
<template>
  <div class="alert-box">
    <strong>This is an Error for Demo Purposes</strong>
    <slot />
  </div>
</template>

<style scoped>
.alert-box {
  /* ... */
}
</style>
```

`<slot />` is a placeholder where the content will be inserted

see also [[Vue Slots]]
## Dynamic Component
To dynamically switch between components, for example in a tabbed interface, use `<component>` element with `is` attribute
```vue
<!-- Component changes when currentTab changes -->
<component :is="tabs[currentTab]"></component>
```

the value based to `:is` can be either of:
- name string of a registered component
- imported component object

The `is` attribute can also be used to create regular HTML elements.

If the component we switch from and unmount should stay "alive" we can use `<KeepAlive>` component

## Props
To pass custom values to a component, use [[Vue Props]]

## Events
 When we need to communicate a message to the parent, we can use [[Vue Events]]

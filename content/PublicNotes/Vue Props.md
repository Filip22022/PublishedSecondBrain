---
title: Vue Props
Date created: 2024-06-12 12:15
Aliases:
tags: 
  - Public
---

Props are custom attributes registered on a component by declaring it in the list of props a component accepts:

```vue
<!-- MyComponent.vue -->
<script setup>
defineProps(['title'])
</script>

<template>
  <h4>{{ title }}</h4>
</template>
```

`defineProps` is only available inside `<script setup>`, and the declared props are automatically exposed to the template.
We can also access those props in code:
```js
const props = defineProps(['title'])
console.log(props.title)
```

Passing the data to a registered prop is done through a custom attribute:

```html
<MyComponent title="My journey with Vue" />
<MyComponent title="Blogging with Vue" />
<MyComponent title="Why Vue is so fun" />
```

You can also render a component for each of the props in an array:

```js
const posts = ref([
  { id: 1, title: 'My journey with Vue' },
  { id: 2, title: 'Blogging with Vue' },
  { id: 3, title: 'Why Vue is so fun' }
])
```

```html
<MyComponent
  v-for="post in posts"
  :key="post.id"
  :title="post.title"
 />
```
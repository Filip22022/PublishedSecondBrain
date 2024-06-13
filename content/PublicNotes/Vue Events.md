---
title: Vue Events
Date created: 2024-06-12 12:19
Aliases:
tags: 
  - Public
---

Events are used to communicate from a child component back to a parent component.

To listen to any event on a child component instance use `v-on` directive, or the shorthand `@`
```vue
<BlogPost
  ...
  @enlarge-text="postFontSize += 0.1"
 />
 ```
the child component can emit an event on itself by calling the built-in `$emit` method:
```vue
<!-- BlogPost.vue, omitting <script> -->
<template>
  <div class="blog-post">
    <h4>{{ title }}</h4>
    <button @click="$emit('enlarge-text')">Enlarge text</button>
  </div>
</template>
```


## `defineEmits`
Optionally emitted events can be declared using `defineEmits` macro that documents all emitted events and can validate them.
It is sonly usable in `<script setup>` and returns an emit function that is the equivalent of `$emit` but can be used in `<script setup>`

```vue
<script setup>
const emit = defineEmits(['enlarge-text'])

emit('enlarge-text')
</script>
```
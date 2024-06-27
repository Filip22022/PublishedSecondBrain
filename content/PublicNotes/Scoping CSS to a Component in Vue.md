---
title: Scoping CSS to a Component in Vue
Date created: 2024-06-13 10:34
Aliases:
tags: 
  - Public
---

By default the css inside the `<style>` tags applies to a global scope affecting other elements than the component it's in. To prevent that and apply the css to the elements of current component only add `scoped` attribute
```html
<style scoped>
...
</style>
```

Both `scoped` and global styles can exist in the same component
```vue
<style>
/* global styles */
</style>

<style scoped>
/* local styles */
</style>
```

>[!info] 
>Using classes and id's is faster than scoped styles

### Child Components
When using `scoped`, the parent's style will not affect child components, but a child's root node will be affected by both parent's scoped css and child's scoped css.

If you want a `scoped` selector style to affect child components, use `:deep()` pseudo-class
```vue
<style scoped>
.a :deep(.b) {
  /* ... */
}
</style>
```

### Slot Selectors
Content rendered by `<slot/>` is not affected by `scoped` style, due to being owned by the parent component that passed it in. To target slot content use `:slotted` pseudo-class

```vue
<style scoped>
:slotted(div) {
  color: red;
}
</style>
```

### Global Selectors
To escape the scope and apply a rule globally use `:global` pseudo-class

```vue
<style scoped>
:global(.red) {
  color: red;
}
</style>
```
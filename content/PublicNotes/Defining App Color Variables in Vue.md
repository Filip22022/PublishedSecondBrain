---
title: Defining App Color Variables in Vue
Date created: 2024-06-17 19:05
Aliases:
tags: 
  - Public
---

To have a set of css variables accessible form vue components, create a `variables.css` file in the assets folder

```css
root {
  --font-family: "Roboto", "Helvetica", "Arial", sans-serif;
  --primary-color: #333a4b;
}
```

import the styles in `App.vue`

```vue
<style>
  @import './assets/styles/variables.css';
</style>
```

then use in components

```vue
<style scoped>
  #something {
    font-family: var(--font-family);
    color: var(--primary-color);
  }
</style>
```
---
title: Binding Inline Styles in Vue
Date created: 2024-06-13 15:03
aliases: 
tags:
  - Public
---

Binding and manipulating `class` and `style` attributes of an element is a common need, so Vue provides enhancements to using `v-bind` with those attributes to avoid having to generate them with string concatenations.

see also [[Binding html Classes in Vue]]

## Binding Inline Styles

### Binding to Objects
`:style` attribute can bind js object values corresponding to an HTML element `style` property

```js
const activeColor = ref('red')
const fontSize = ref(30)
```

```vue
<div :style="{ color: activeColor, fontSize: fontSize + 'px' }"></div>
```

Both `camelCase` (recommended) and `kebab-case` css property keys are supported 

Binding a style object directly is often the cleaner solution, and often used together with computed properties (similar to [[Binding html Classes in Vue]])
```js
const styleObject = reactive({
  color: 'red',
  fontSize: '30px'
})
```
\
```vue
<div :style="styleObject"></div>
```

### Binding to Arrays
`:style` can be bound to an array of multiple style objects, which will be merged and applied to the same element

```vue
<div :style="[baseStyles, overridingStyles]"></div>
```

### Auto Prefixing
When using a CSS property requiring a [[Vendor Prefix]] vue will add it automatically

### Multiple Values
Multiple prefixed values can be provided to a style property, which will render the last value supported by the browser
```vue
<div :style="{ display: ['-webkit-box', '-ms-flexbox', 'flex'] }"></div>
```

This will render `display:flex` for browsers supporting the version of flexbox without prefix 
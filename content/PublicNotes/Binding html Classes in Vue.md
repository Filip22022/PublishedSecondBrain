---
title: Binding html Classes in Vue
Date created: 2024-06-13 12:37
Aliases:
tags: 
  - Public
---

Binding and manipulating `class` and `style` attributes of an element is a common need, so Vue provides enhancements to using `v-bind` with those attributes to avoid having to generate them with string concatenations.

see also [[Binding Inline Styles in Vue]]

## Binding the `class` Attribute

### Binding to Objects
Passing an object to `:class` (`v-bind:class`) can be used to dynamically change classes based on boolean values

```html
<div :class="{ active: isActive }"></div>
```

Multiple classes can be toggled together in this way by having more fields in the object.

```js
const isActive = ref(true)
const hasError = ref(false)
```

```html
<div
  :class="{ active: isActive, 'text-danger': hasError }"
></div>
```

The `:class` directive can also coexist with standard `class` attribute:
```html
<div
  class="static"
  :class="{ active: isActive }"
></div>
```

### Computed Property Binding
Class can be bound to a computed property that returns an object

```js
const isActive = ref(true)
const error = ref(null)

const classObject = computed(() => ({
  active: isActive.value && !error.value,
  'text-danger': error.value && error.value.type === 'fatal'
}))
```

```html
<div :class="classObject"></div>
```

### Binding to Arrays
Binding `:class` to an array to apply multiple classes at the same time

```js
const activeClass = ref('active')
const errorClass = ref('text-danger')
```

```html
<div :class="[activeClass, errorClass]"></div>
```

It can also be chained with [[Ternary Operator]] 
```html
<div :class="[isActive ? activeClass : '', errorClass]"></div>
```
 where `errorClass` will be always applied, while `activeClass` will be only applied when `isActive` is [[Truthy and Falsy Values|truthy]]

To shorten the code the object syntax is also usable inside the array syntax:
```html
<div :class="[{ activeClass: isActive }, errorClass]"></div>
```

### Binding with Components

When `class` attribute is used on a component with only one root element in the template, the classes will be automatically added to the component's root element, and the same is true for class bindings.

When the component has multiple root elements, we need to define the element receiving the class with `$attrs` component property

```vue
<!-- MyComponent template using $attrs -->
<p :class="$attrs.class">Hi!</p>
<span>This is a child component</span>
```

```vue
<MyComponent class="baz" />
```

which will render
```html
<p class="baz">Hi!</p>
<span>This is a child component</span>
```


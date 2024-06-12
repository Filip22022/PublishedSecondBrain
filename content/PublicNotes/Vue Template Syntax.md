---
title: Vue Template Syntax
Date created: 2024-06-11 11:03
Aliases:
tags: 
  - Public
---

Vue uses HTML-based templates to bind [[DOM]] to the underlying component's data. When the app state changes Vue figures the minimal number of DOM manipulations and number of components to re-render

## Binding the Data

### Text Interpolation
Using the double curly braces (moustaches) will replace the tag with *corresponding component's instance* property value, and will be updated whenever the property changes

Example:
```html
<span>Message: {{ msg }}</span>
```

### Raw HTML
Because the curly brace tags are interpreted as plain text, to output HTML we need to use the `v-html` [[Vue Directives|directive]]
```html
<p>Using text interpolation: {{ rawHtml }}</p>
<p>Using v-html directive: <span v-html="rawHtml"></span></p>****
```

### Attribute Bindings
Curly braces syntax cannot be used inside HTML attributes, use `v-bind` directive instead.  If the bound value is `null` or `undefined` the attribute will be removed from the rendered element

```html
<div v-bind:id="dynamicId"></div>
```

Because it's very common in Vue, it has a shorthand syntax:
```html
<div :id="dynamicId"></div>
```

if the attribute has identical name to the bound JavaScript value, it can be shortened even further:
```html
<!-- same as :id="id" -->
<div :id></div>

<!-- this also works -->
<div v-bind:id></div>
```

### Boolean Attribute
`v-bind` works differently with boolean attributes
```html
<button :disabled="isButtonDisabled">Button</button>
```
The attribute will only be included if the bound value is [[Truthy Values|thruthy]] or is an empty string.

### Multiple Attributes
Multiple attributes can be bound using one directive without an argument:
```js
const objectOfAttrs = {
  id: 'container',
  class: 'wrapper',
  style: 'background-color:green'
}
```

```html
<div v-bind="objectOfAttrs"></div>
```

## Using JS Expressions
Vue supports full JavaScript expressions inside it's data bindings. These expressions are evaluated as JavaScript in the data scope of *current component instance*. They can be used inside [[Vue Template Syntax#Text Interpolation|Text Interpolations]] or in the attribute value of any of the [[Vue Directives]] 

examples:
```html
{{ number + 1 }}

{{ ok ? 'YES' : 'NO' }}

{{ message.split('').reverse().join('') }}

<div :id="`list-${id}`"></div>
```

Each binding can contain only a **single** [[JavaScript Expression|expression]]

### Calling Functions
It's possible to call a component-exposed method inside a binding expression

```html
<time :title="toTitleDate(date)" :datetime="date">
  {{ formatDate(date) }}
</time>
```

Functions called inside binding expressions are called **every time** the component is updated, so they shouldn't have any side effects, like changing data or triggering asynchronous operations

### Restricted Access
Template expressions have access to a restricted list of globals that exposes commonly used built-in globals. User attached properties and other not included globals will not be accessible in template expressions unless you add them to `app.config.globalProperties`

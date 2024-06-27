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
\
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


### `defineEmits`
Optionally emitted events can be declared using `defineEmits` macro that documents all emitted events and can validate them.
It is sonly usable in `<script setup>` and returns an emit function that is the equivalent of `$emit` but can be used in `<script setup>`

```vue
<script setup>
const emit = defineEmits(['enlarge-text'])

emit('enlarge-text')
</script>
```


## Event Handler Types
### Inline Event Handlers

For simple cases, the code for handling the event can be placed directly in the directive
```js
const count = ref(0)
```

```vue
<button @click="count++">Add 1</button>
<p>Count is: {{ count }}</p>
```

### Method Event Handlers

For more complex cases the `v-on` directive can take name or path of a component method


```js
const name = ref('Vue.js')

function greet(event) {
  alert(`Hello ${name.value}!`)
}
```

```vue
<!-- `greet` is the name of the method defined above -->
<button @click="greet">Greet</button>
```


To be treated as method handler need to be in one of the forms `foo`, `foo.bar` or `foo['bar']`. As `foo()` would be treated as an inline handler

### Calling Methods in Inline Handlers

Methods can also be called in an inline handler, allowing us to pass custom arguments instead of native events

```js
function say(message) {
	alert(message)
}
```

```vue
<button @clisk="say('hello')">Say hello</button>
```

## Accessing the DOM Event

Sometimes we need access to the original DOM event .

### Method Handlers
Method handlers automatically receive the event object:
```js
const name = ref('Vue.js')

function greet(event) {
  alert(`Hello ${name.value}!`)
  // `event` is the native DOM event
  if (event) {
    alert(event.target.tagName)
  }
}
```

```vue
<!-- `greet` is the name of the method defined above -->
<button @click="greet">Greet</button>
```

Where the `event.target` is the native DOM event object triggering the handler.

### Inline Handlers
In inline handlers we can pass the event with a special `$event` variable, or by using an inline arrow function
```vue
<!-- using $event special variable -->
<button @click="warn('Form cannot be submitted yet.', $event)">
  Submit
</button>

<!-- using inline arrow function -->
<button @click="(event) => warn('Form cannot be submitted yet.', event)">
  Submit
</button>
```

```js
function warn(message, event) {
  // now we have access to the native event
  if (event) {
    event.preventDefault()
  }
  alert(message)
}
```

## Event Modifiers

To access functionality like `event.preventDefault()` or `event.stopPropagation()` inside event handlers without having to deal with DOM event details Vue provides *event modifiers*

The available modifiers are:
- `.stop`
- `.prevent`
- `.self`
- `.capture`
- `.once`
- `.passive`

### Examples
```vue
<!-- the click event's propagation will be stopped -->
<a @click.stop="doThis"></a>

<!-- the submit event will no longer reload the page -->
<form @submit.prevent="onSubmit"></form>

<!-- modifiers can be chained -->
<a @click.stop.prevent="doThat"></a>

<!-- just the modifier -->
<form @submit.prevent></form>

<!-- only trigger handler if event.target is the element itself -->
<!-- i.e. not from a child element -->
<div @click.self="doThat">...</div>

<!-- use capture mode when adding the event listener     -->
<!-- i.e. an event targeting an inner element is handled -->
<!-- here before being handled by that element           -->
<div @click.capture="doThis">...</div>

<!-- the click event will be triggered at most once -->
<a @click.once="doThis"></a>

<!-- the scroll event's default behavior (scrolling) will happen -->
<!-- immediately, instead of waiting for `onScroll` to complete  -->
<!-- in case it contains `event.preventDefault()`                -->
<div @scroll.passive="onScroll">...</div>
```

>[!tip] Order Matters
>The code generated from the modifiers follows the same order as the modifiers themselves, so `@click.prevent.self` will **prevent click's default action on the element and it's children** while `@click.self.prevent` will **prevent click's action on _only_ the element itself **

## Key Modifiers
Checking for specific keyboard events can be done by adding key modifiers to the `v-on` directive 

for example:
```vue
<!-- only call `submit` when the `key` is `Enter` -->
<input @keyup.enter="submit" />
```

Any valid key names exposed via `KeyboardEvent.key` can be used as modifiers when converted to `kebab-case`, but Vue also provides aliases for the commonly used keys:
- `.enter`
- `.tab`
- `.delete` (captures both "Delete" and "Backspace" keys)
- `.esc`
- `.space`
- `.up`
- `.down`
- `.left`
- `.right`

### System Modifier Keys
The following modifiers cause mouse or keyboard events to only be triggered when the modifier key is pressed:\
- `.ctrl`
- `.alt`
- `.shift`
- `.meta`

for example:
```vue
<!-- Alt + Enter -->
<input @keyup.alt.enter="clear" />

<!-- Ctrl + Click -->
<div @click.ctrl="doSomething">Do something</div>
```

>[!Warning] The modifier keys work differently from regular keys and only emit `keyup` events when another key is released while holding down the modifier key

### `.exact` Modifier
This modifier allows to control the exact combination of system modifiers needed to trigger an event:
```vue
<!-- this will fire even if Alt or Shift is also pressed -->
<button @click.ctrl="onClick">A</button>

<!-- this will only fire when Ctrl and no other keys are pressed -->
<button @click.ctrl.exact="onCtrlClick">A</button>

<!-- this will only fire when no system modifiers are pressed -->
<button @click.exact="onClick">A</button>
```

## Mouse Button Modifiers
The mouse button modifiers are:
- `.left`
- `.right`
- `.middle`
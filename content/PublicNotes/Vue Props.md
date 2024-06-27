---
title: Vue Props
Date created: 2024-06-12 12:15
Aliases:
tags: 
  - Public
---

Props are custom attributes passed from the parent to a child component. 

## Naming
Long prop names should use `camelCase` when declaring, and `kebab-case` when passing props to a child component

```js
defineProps({
  greetingMessage: String
})
```

```html
<span>{{ greetingMessage }}</span>
```

```html
<MyComponent greeting-message="hello" />
```

## Declaring Props
Props need to be registered on a component by declaring it in the list of props a component accepts. 

Using `<script setup>` it can be done using  `defineProps` with an array of strings or object syntax
```vue
<!-- MyComponent.vue -->
<script setup>
defineProps(['title'])
</script>

<template>
  <h4>{{ title }}</h4>
</template>
```
or the (style guide preferred):
```vue
<script setup>
	defineProps({
	  title: String,
	  likes: Number
	})
</script>	
```
In the object declaration syntax, they key is the name of the prop, and the value should be of the expected type.

`defineProps` is only available inside `<script setup>`, and the declared props are automatically exposed to the template.

## Accessing
We can access props in code:
```js
const props = defineProps(['title'])
console.log(props.title)
```

```vue
<template>
	<div title=><div/>
<template/>
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

## Dynamic Props

Props with static values use strings
```html
<MyComponent title="My journey with Vue" />
```

But they can also be assigned dynamically with `v-bind`/`:` shortcut

```html
<!-- Dynamically assign the value of a variable -->
<BlogPost :title="post.title" />

<!-- Dynamically assign the value of a complex expression -->
<BlogPost :title="post.title + ' by ' + post.author.name" />
```

Doing it this way allows us to use other value types than strings to props. Using the binding causes the prop to be interpreted as a JavaScript expression rather than a string. 

This would be a numerical value: 44
```html
<BlogPost :likes="42+2" />
```

This would be a string: "42+2"
```html
<BlogPost likes="42+2" />
```

### Passing Different Value Types
- Number
```html
<BlogPost :likes="42" />

<!-- Dynamically assign to the value of a variable. -->
<BlogPost :likes="post.likes" />
```
- Boolean
```html
<!-- Including the prop with no value will imply `true`. -->
<BlogPost is-published />

<!-- this is a JavaScript expression rather than a string.          -->
<BlogPost :is-published="false" />

<!-- Dynamically assign to the value of a variable. -->
<BlogPost :is-published="post.isPublished" />
```
- Array
```html
<BlogPost :comment-ids="[234, 266, 273]" />

<!-- Dynamically assign to the value of a variable. -->
<BlogPost :comment-ids="post.commentIds" />
```
- Object
```html
<BlogPost
  :author="{
    name: 'Veronica',
    company: 'Veridian Dynamics'
  }"
 />

<!-- Dynamically assign to the value of a variable. -->
<BlogPost :author="post.author" />
```

### Binding All Properties of an Object

To pass all object properties as props use `v-bind` without an argument

for an object
```js
const post = {
  id: 1,
  title: 'My Journey with Vue'
}
```

```html
<BlogPost v-bind="post" />
```
is equivalent to
```html
<BlogPost :id="post.id" :title="post.title" />
```

### Mutating Props

Props form a one-way-down data binding between the child property and the parent, meaning when the parent property updates, it will update the child, but not the other way around.

>[!Warning] Props should not be mutated inside a child component

There are two cases where you might need to mutate a value of a prop:

1. The prop is an initial value for a local data property
		In this case define the local data property separately and use prop as initial value
	```js
	const props = defineProps(['initialCounter'])
	// counter only uses props.initialCounter as the initial value;
	// it is disconnected from future prop updates.
	const counter = ref(props.initialCounter)
	```
2. The prop is a raw value that needs to be transformed
		In this case define a computed property with the prop's value
	```js
	const props = defineProps(['size'])
	
	// computed property that auto-updates when the prop changes
	const normalizedSize = computed(() => props.size.trim().toLowerCase())
	```

#### Mutating Object/Array Props
Child components are able to mutate object's/array's nested properties due to being passed by reference in js, but this could cause problems with reasoning about data flow.

>[!warning] Children should not mutate object/array props, instead they should emit an event to let the parent perform the mutation

## Prop Validation

[[Prop Validation in Vue]]
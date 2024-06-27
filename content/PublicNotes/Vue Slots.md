---
title: Vue Slots
Date created: 2024-06-13 16:53
Aliases:
tags: 
  - Public
---

Slots are used to pass custom templates into component to make them more reusable.

To pass a template into a component use the following:
```vue
<MyComponent>
	<SomeTemplate/>
	SomeText
</MyComponent>
```

```vue
<button class="fancy-btn">
  <slot></slot> <!-- slot outlet -->
</button>
```

The *slot outlet* being a `<slot/>` element indicates to a parent where a content passed into the custom component should be rendered.

## Scope

Because slot content is defined in a parent component and passed into a child component from there, it has access to data from the parent component, but does **not** have access to data from the child component

To share data from child's scope with the slot content, attributes can be passed to a slot outlet in the same way as [[Vue Props|props]]
```vue
<!-- <MyComponent> template -->
<div>
  <slot :text="greetingMessage" :count="1"></slot>
</div>
```

### Receiving Data in Default Slot
To receive data in an **only** slot use the `v-slot` directly on a child component tag. If using the default slot **with** named slots, use the named slots method for all slots.
```vue
<MyComponent v-slot="slotProps">
  {{ slotProps.text }} {{ slotProps.count }}
</MyComponent>
```

we can also use destructuring
```vue
<MyComponent v-slot="{ text, count }">
  {{ text }} {{ count }}
</MyComponent>
```


### Receiving Data in Named Slots
To receive the data in a named slot, add an argument with the slots name, or use the shorthand
```vue
<MyComponent>
  <template #header="headerProps">
    {{ headerProps }}
  </template>

  <template #default="defaultProps">
    {{ defaultProps }}
  </template>

  <template #footer="footerProps">
    {{ footerProps }}
  </template>
</MyComponent>
```

Passing props
```vue
<slot name="header" message="hello"></slot>
```
where the `headerProps` would be `{message: 'hello'}` because the `name` is reserved.

## Default Content
Default or Fallback Content can be provided to the slot, it will be rendered when the component is used without passing in any slot content

```vue
<button type="submit">
  <slot>
    Submit <!-- fallback content -->
  </slot>
</button>
```

## Named Slots

Named slots allow us to have multiple slot outlets in a single component

```vue
<div class="container">
  <header>
    <slot name="header"></slot>
  </header>
  <main>
    <slot></slot>
  </main>
  <footer>
    <slot name="footer"></slot>
  </footer>
</div>
```
This template has a default slot, and two additional named slots

to pass content into a named slot use `<template>` element with `v-slot` directive in the form `<template v-slot:slotname>` or the dedicated shorthand `<template #header>`
```vue
<BaseLayout>
  <template v-slot:header>
    <!-- content for the header slot -->
  </template>
</BaseLayout>
```

All top level non-`<template>` nodes are treated as content for the default slot, and the default slot can also be targeted with `#default`

### Dynamic Names

`v-slot` works with dynamic directive arguments

```vue
<base-layout>
  <template v-slot:[dynamicSlotName]>
    ...
  </template>

  <!-- with shorthand -->
  <template #[dynamicSlotName]>
    ...
  </template>
</base-layout>
```

## Conditional Slots

To render something based on whether a slot is present use `v-if` directive with `$slots` property
```vue
<template>
  <div class="card">
    <div v-if="$slots.header" class="card-header">
      <slot name="header" />
    </div>
    
    <div v-if="$slots.default" class="card-content">
      <slot />
    </div>
    
    <div v-if="$slots.footer" class="card-footer">
      <slot name="footer" />
    </div>
  </div>
</template>
```


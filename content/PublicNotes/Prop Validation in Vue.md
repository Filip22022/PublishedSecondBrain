---
title: Prop Validation in Vue
Date created: 2024-06-13 12:21
Aliases:
tags: 
  - Public
---

Components can specify requirements for their props, if they are not met, Vue will trigger a warning in the browsers JavaScript console

## Example

```js
defineProps({
  // Basic type check
  //  (`null` and `undefined` values will allow any type)
  propA: Number,
  // Multiple possible types
  propB: [String, Number],
  // Required string
  propC: {
    type: String,
    required: true
  },
  // Required but nullable string
  propD: {
    type: [String, null],
    required: true
  },
  // Number with a default value
  propE: {
    type: Number,
    default: 100
  },
  // Object with a default value
  propF: {
    type: Object,
    // Object or array defaults must be returned from
    // a factory function. The function receives the raw
    // props received by the component as the argument.
    default(rawProps) {
      return { message: 'hello' }
    }
  },
  // Custom validator function
  // full props passed as 2nd argument in 3.4+
  propG: {
    validator(value, props) {
      // The value must match one of these strings
      return ['success', 'warning', 'danger'].includes(value)
    }
  },
  // Function with a default value
  propH: {
    type: Function,
    // Unlike object or array default, this is not a factory
    // function - this is a function to serve as a default value
    default() {
      return 'Default function'
    }
  }
})
```

## Specifying Requirements

We can specify prop validations by providing an object with validation requirements to the `defineProps()`

### Details
- All props are optional by default unless `required: true` is specified
- An absent optional Boolean will be `false`, which can be changed with `default` i.e.:`default:undefined
- All other types of absent optional props will have `undefined` value
- if `default` is specified, it will be used if prop value would be `undefined`, even when explicit `undefined` value is passed

## Available Runtime Type Checks

The type can be one of the following native constructors:
- `String`
- `Number`
- `Boolean`
- `Array`
- `Object`
- `Date`
- `Function`
- `Symbol`
- `Error`

Of a custom class/constructor function. The assertion in that case will be made with `instanceof` check.

for exapmple:
```js
class Person {
  constructor(firstName, lastName) {
    this.firstName = firstName
    this.lastName = lastName
  }
}
```

```js
defineProps({
  author: Person
})
```

### Nullable Types
if the type is required, but could be `null`, use the following array syntax:
```js
defineProps({
  id: {
    type: [String, null],
    required: true
  }
})
```

## Boolean Casting
`Boolean` type props have special casting rules. The following prop in `MyComponent`:
```js
defineProps({
  disabled: Boolean
})
```

can be used like this:
```html
<!-- equivalent of passing :disabled="true" -->
<MyComponent disabled />

<!-- equivalent of passing :disabled="false" -->
<MyComponent />
```

If the prop can have multiple types the casting rules will also applied. A special behaviour occurs when both `String` and `Boolean` are allowed:
```js
// disabled will be casted to true
defineProps({
  disabled: [Boolean, Number]
})

// disabled will be casted to true
defineProps({
  disabled: [Boolean, String]
})

// disabled will be casted to true
defineProps({
  disabled: [Number, Boolean]
})

// disabled will be parsed as an empty string (disabled="")
defineProps({
  disabled: [String, Boolean]
})
```
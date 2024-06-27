---
title: Vue.js
Date created: 2024-06-05 22:17
Aliases: Vue
tags: 
  - Public
---

Vue.js is a component-based declarative framework for building user interfaces built on top of HTML, CSS nad JavaScript.

### [[Single-File Components]]
Most vue projects use components built with HTML-like files called Single-File Components (SFC) with the `*.vue` extension. Those files encapsulate components logic, template, and styles in one file, and they are a defining feature of the framework

### API Options
Vue components can use one of two API styles: Options API and Composition API. 

Options API is centred around a "component instance", abstracting away the reactivity details and enforcing more organisation via option groups. 
Composition API is focused on declaring [[Reactive Programming|reactive]] state variables. It's doesn't impose limitations, but requires more understanding about reactivity and the framework, offering flexibility and reusable logic in return.

On the [Vue.js website](https://vuejs.org/guide/) the authors recommend going with Options for low-complexity scenarios and Composition for full Applications (in production use)

## Notes
[Official Docs](https://vuejs.org/guide/)

>Using composition API and `<script setup>` in the notes
### Guides
[[Creating a Vue Application]]
[[Vue Template Syntax]]
[[Vue Useful Commands]]
[[Vue Naming Guide]]
[[Defining App Color Variables in Vue]]
#### CSS
[[Scoping CSS to a Component in Vue]]
[[Creating a Global Stylesheet in Vue]]
[[Binding html Classes in Vue]]
[[Binding Inline Styles in Vue]] 

### General
[[Reactivity in Vue]]
[[Vue Components]]
[[Single-File Components]]
[[Vue Template Refs]]
[[Vue Props]]
[[Vue Events]]
[[Vue Slots]]
[[Vue Directives]]
[[Vue Router]]
---
title: Creating a Vue Application
Date created: 2024-06-11 09:38
Aliases:
tags: 
  - Public
---

Note on [[Scaffolding]] a Vue Single Page Application

## Building

>Prerequisites: up-to-date [[Node.js]] version

To create the empty vue application run 
```
npm create vue@latest
```
and chose appropriate options when prompted.

This will create an application structure, for more details see [[Vue Scaffolding Structure]]

then install the dependencies and start the dev server with
```
cd <your-project-name>
npm install
npm run dev
```

This will allow you to have the project running in development mode.  To ship the app to production run
```
npm run build
```
which will create a production build in the `./dist` folder

### CDN
To create a vue application directly from a Content Delivery Network follow the [docs](https://vuejs.org/guide/quick-start.html)

## Root Component

Every app requires a root component that can contain other components as it's children. This component is passed to `createApp` function to create an application instance
```js
import { createApp } from 'vue'

const app = createApp({
  /* root component options */
})
```

If using Single-File Components the root component is typically imported from another file:
```js
import { createApp } from 'vue'
// import the root component App from a single-file component.
import App from './App.vue'

const app = createApp(App)
```

## Mounting

For the application to render the `.mount()` method needs to be called. It needs "container" argument which can be a [[DOM]] element or selector string

```html
<div id="app"></div>
```

```js
app.mount('#app')
```

The `app`'s root component will be rendered inside the container element, which itself is not considered a part of the app.

The `.mount()` method should be called **after** all app configurations and asset registrations. It's return value is the *root component* instance

> For using vue without a build setup (CDN) it's possible to provide a template by writing it directly inside the mount container

## Configuration
Application instance exposes a `.config` object which is used to configure options on the app-level, like defining an error handler that captures errors from all descendant components

```js
app.config.errorHandler = (err) => {
  /* handle error */
}
```

The instance also allows registering app-scoped assets, for example components:
```js
app.component('TodoDeleteButton', TodoDeleteButton)
```
Which will make the `TodoDeleteButton` available for use anywhere in the app

## Multiple Instances
Multiple vue applications can co-exist on the same page, it can be useful for mounting separate small application instances on the elements of a bigger page they are responsible for.
---
title: Vue Router
Date created: 2024-06-14 19:14
Aliases:
tags: 
  - Public
---

Vue Router is an officially-supported library suited for building single page application

[Vue Router Documentation](https://router.vuejs.org/installation.html)

## Basic Usage

### Creating a Router Instance

The router instance takes in a list of possible paths, and the components that should be returned from them.
```js
import { createWebHistory, createRouter } from 'vue-router'

import HomeView from './HomeView.vue'
import AboutView from './AboutView.vue'

const routes = [
  { path: '/', component: HomeView },
  { path: '/about', component: AboutView },
]

const router = createRouter({
  history: createWebHistory(),
  routes,
})

  
export default router
```

It needs to be added to the app, and call `use()` to register it as a plugin

```js
createApp(App)
  .use(router)
  .mount('#app')
```

### Adding the Router to the Application
Vue Router uses the `<RouterLink>` and `<RouterView>` tags to place page links and the associated component inside the application
```vue
<template>
  <h1>Hello App!</h1>
  <nav>
    <RouterLink to="/">Go to Home</RouterLink>
    <RouterLink to="/about">Go to About</RouterLink>
  </nav>
  <main>
    <RouterView />
  </main>
</template>
```

### Accessing the Router
 In Composition API the router and the route can be accessed by using the following methods
```js
const router = useRouter()
const route = useRoute() 
```

### Catch All Route
When using `createWebHistory()` in the router, directly accessing an internal url will not work, so creating a catch all route to redirect all incorrect routes might be preferable.

To do that we create a regexp param matching
```js
const routes = [
  // will match everything and put it under `route.params.pathMatch`
  { path: '/:pathMatch(.*)*', name: 'NotFound', component: NotFound },
  // will match anything starting with `/user-` and put it under `route.params.afterUser`
  { path: '/user-:afterUser(.*)', component: UserGeneric },
]
```
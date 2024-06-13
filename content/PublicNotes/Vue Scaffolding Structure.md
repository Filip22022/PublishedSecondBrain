---
title: Vue Scaffolding Structure
Date created: 2024-06-12 15:48
Aliases:
tags: 
  - Public
---

The structure of a newly generated Vue application using Vite:

```
/node-modules
/public
	...
/src
	/assets
	/components
	-App.vue
	-main.js
-index.html
...
-vite.config.js
-package.json
-package-lock.json
...
```

- **index.html** is the main file where the Single Page Application will be mounted
- **App.vue** is the root component of the application that will house the rest of the website
- **main.js** is the script creating and mounting the vue application
- **/src** is where the source files will be located
- **/public** is a folder for all the static assets directly served by the web server without being processed
- **/src/assets** is a folder for all assets that need to be processed first
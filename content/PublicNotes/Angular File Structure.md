---
title: Angular File Structure
Date created: 2024-04-18 19:03
Aliases:
tags: 
  - Public
---

The suggested folder and file structure from [Angular Style Guide](https://angular.io/guide/styleguide) following [[LIFT Principle]] 

The goal behind this way of structuring the application is to start small, but keep a long term vision in mind.

## Structure
```
<root>
	src/
		app/
			core/
				- exception.service.ts|spec.ts
				- user-profile.service.ts|spec.ts
			heroes/
				hero/
					- hero.component.ts|html|css|spec.ts
				hero-list/
					- hero-list.component.ts|html|css|spec.ts
				shared/
					- hero-button.component.ts|html|css|spec.ts
					- hero.model.ts
					- hero.service.ts|spec.ts
				- heroes.component.ts|html|css|spec.ts
				- heroes.module.ts
				- heroes-routing.module.ts
			shared/
				- shared.module.ts
				- init-caps.pipe.ts|spec.ts
				- filter-text.component.ts|spec.ts
				- filter-text.service.ts|spec.ts
			villains/
				villain/
					…
				villain-list/
					…
				shared/
					…
				- villains.component.ts|html|css|spec.ts
				- villains.module.ts
				- villains-routing.module.ts
			- app.component.ts|html|css|spec.ts
			- app.module.ts
			- app-routing.module.ts
		- main.ts
		- index.html
		…
	node_modules/…
	…
```

## Guidelines

- Create folders named for their feature area
- Create an NgModule for each feature area
- Create app NgModule in the application's root folder 
- Create an NgModule for all distinct features in an application and place them in the same named folder as the feature area
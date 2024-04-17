---
title: SASS vs LESS
Date created: 2024-04-16 15:50
Aliases:
tags: 
  - Public
---

SASS and LESS are [[CSS]] preprocessors - extensions of CSS that add additional functionality, including variables and functions. Those preprocessors function like scripting languages that are compiled into standard CSS

## SASS vs SCSS
Despite the distinction found in some places, what is usually called SASS and SCSS are two different syntax options of the same preprocesor - SASS.

SASS is the indented syntax, while SCSS uses standard CSS syntax with brackets and semicolons

### SASS example
```css
$primary-color: #007bff 
.btn 
	background-color: 
	$primary-color color: 
	#fff padding: 10px 20px
```
### SCSS example
```scss
$primary-color: #007bff;

.btn {
    background-color: $primary-color;
    color: #fff;
    padding: 10px 20px;
}
```

## SASS vs LESS
Sass and Less are two different preprocessors for CSS, and have some syntactic differences like variable declaration and mixins:

- Sass
	```scss
	$primary-color: #007bff;

	.button {  
		@include rounded-corners(5px);  
	}  
	  
	@mixin rounded-corners($radius) {  
		border-radius: $radius;  
	}	
	```
- Less
	```less
	@primary-color: #007bff;

	.button {  
		.rounded-corners(5px);  
	}  
  
	.rounded-corners(@radius) {  
		border-radius: @radius;  
	}
	```

Additionally Sass uses Ruby, while Less uses JavaScript which might be important while installing on a machine without access to Ruby or Node.js
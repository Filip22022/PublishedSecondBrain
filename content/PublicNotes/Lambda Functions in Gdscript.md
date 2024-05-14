---
title: Lambda Functions in Gdscript
Date created: 2024-04-27 12:52
Aliases:
tags: 
  - Public
---

[[Lambda Functions]] in gdscript can be put in place of a `Callable`. They are custom `Callables` that are not associated with `Object` instance, but they can be named

```gdscript
var my_lambda = func(msg):
	print(message)

my_lambda.call("Hello")
```

```gdscript
button_pressed.connect(func(): print("Button Pressed!"))
```
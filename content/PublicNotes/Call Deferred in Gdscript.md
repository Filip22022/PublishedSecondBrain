---
title: Call Deferred in Gdscript
Date created: 2024-04-29 20:41
Aliases:
tags: 
  - Public
---

In Gdscript the `call_deferred` is used to delay the execution of the function until idle time.

According to [this thread](https://www.reddit.com/r/godot/comments/165n0dl/when_are_call_deferred_calls_actually_handled/) it's an oversimplification in the documentation for the sake of understanding and under the hood, the function starts a new call stack after the current one.

## Syntax

### On an Object

`<object>.call_deferred("<method_name>", <arguments>)`

### On a Callable

`<callable>.call_deferred()`

> [!Warning]
> Returns `null` not the method's result

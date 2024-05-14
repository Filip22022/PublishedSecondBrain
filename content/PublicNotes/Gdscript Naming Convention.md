---
title: Gdscript Naming Convention
Date created: 2024-05-01 14:12
Aliases:
tags: 
  - Public
---
Naming convention for gdscript from the [style guide](https://docs.godotengine.org/en/stable/tutorials/scripting/gdscript/gdscript_styleguide.html) 

|              Type               | Rules                                     | Example                              |
| :-----------------------------: | ----------------------------------------- | ------------------------------------ |
|              File               | snake_case                                | my_file                              |
|              Class              | PascaCase                                 | CharacterBody, var Body = preload... |
|     Functions and Variables     | snake_case                                | function, my_variable                |
| Private Functions and Variables | snake\_case, prefixed with `_` underscore | \_private_variable                   |
|             Signal              | snake\_case, past tense                   | door_opened                          |
|            Constant             | UPPERCASE, UNSERSORE_SEPARATED            | MY_CONSTANT                          |
---
title: Setting Property as Required in Godot
Tags: Public
Aliases:
Date created: 2024-03-25 21:33
---

As of now (25/3/2024) there's no way to make a property required in a strict sense.

A workaround has been proposed to set a configuration warning:
```
func _get_configuration_warning() -> String:
    if some_exported_value == 0:
        return "some_exported_value needs a value different than 0."

    return ""
```
But I haven't had much luck with it myself.
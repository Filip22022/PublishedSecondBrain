---
title: Type Hints in Python
Date created: 2024-04-22 14:58
Aliases:
tags: 
  - Public
---

Type annotations are optional in Python, but they can be used by type checkers or linters, and are useful for making the code purpose clearer

## Types

### Basic
```python
int
float
bool
str
```
### Collections
```python
list[int/x/./...
set[x]
dict[x,y]
```

## Annotating
### Variables
```python
variable: type = value
name: string = "Bob"
```
### Functions
```python
def some_function(param: int = default_value) -> str:
	...
```

---
[mypy typing cheatsheet](https://mypy.readthedocs.io/en/stable/cheat_sheet_py3.html)
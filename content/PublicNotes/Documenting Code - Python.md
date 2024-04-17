---
title: Documenting Code - Python
Tags: Public
Aliases:
Date created: 2024-03-01 09:07
---

## Syntax

### Inline Comments
Inline comments are created with `#` sign.
My personal preference is starting with a space and capital letter without period, but those are just choices.

`# A comment`

### Type Hinting
In line with the idea of self-documenting code, you can include type hints in python to make it clear what input or output is expected.

```
def hello_name(name: str) -> str:
    return(f"Hello {name}")
```

### Docstrings
Accessed by `help()` function, set by creating a multiline comment `""" x """` directly under the declaration of documented object.

```
def say_hello(name):
    """A simple function that says hello"""
    return(f"Hello {name}")
```

#### Docstring Structure
- """
- one-line summary
- blank line
- elaboration
- """
- blank line

```
""" Short sumary

Elaboration of the description
can be multiline
"""

some_code
```

#### Package Docstring
Should be placed at the top of package's `__init__.py` file

#### Module Docstring
Should be placed on top of the file, before imports

#### Script Docstrings 
Should be placed at the top of the script file

## Content
### Docstring Content

#### Class Docstring
- Summary of purpose and behaviour
- public methods with description
- class properties
- anything related to the interface

#### Class `__init__` Method
- Constructor parameters

#### Methods
- Brief description
- Any arguments (include information about being optional and/or default values)
- Side effects of executing the method
- Raised exceptions
- Restrictions on when the method can be called

#### Package
- modules 
- sub-packages

#### Module
- brief description 
- list of classes, exceptions, functions and any other exported objects

#### Module Function
- description 
- arguments
- side effects
- exceptions 
- restrictions on execution

#### Script
Should contain enough information for a user to be able to use the script. Should be usable for the `usage` message for the script
- description
- parameters
- custom/third-party imports

## Formats

### Epytext
```
"""
This is a javadoc style.

@param param1: this is a first param
@param param2: this is a second param
@return: this is a description of what is returned
@raise keyError: raises an exception
"""
```

### reStructuredText (Sphinx)
Default PyCharm docstring
```
"""
This is a reST style.

:param param1: this is a first param
:param param2: this is a second param
:returns: this is a description of what is returned
:raises keyError: raises an exception
"""
```
### Google
```
"""
This is an example of Google style.

Args:
    param1: This is the first param.
    param2: This is a second param.

Returns:
    This is a description of what is returned.

Raises:
    KeyError: Raises an exception.
"""
```

### Numpydoc
```

"""
My numpydoc description of a kind
of very exhautive numpydoc format docstring.

Parameters
----------
first : array_like
    the 1st param name `first`
second :
    the 2nd param
third : {'value', 'other'}, optional
    the 3rd param, by default 'value'

Returns
-------
string
    a value in a string

Raises
------
KeyError
    when a key error
OtherError
    when an other error
"""
```
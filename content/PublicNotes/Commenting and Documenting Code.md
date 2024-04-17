---
title: Commenting and Documenting Code
Tags: Public
Aliases:
Date created: 2024-03-01 09:12
---

## Why Document the Code?
Anyone using your code - be it yourself, or other developers need to be able to quickly understand what it does and how it works. If your code is lacking documentation no one will want to use it even if it's good.

### Inline Comments Controversy
There is a discourse in the community about the importance of comments, and their role.
I'm closer to the opinion that they are a necessary part of codebases, and can make understanding code much easier. They shouldn't however be overused nor repeat code

### Documentation
Documentation is a high level description explaining how the code us used, and how it connects with other parts. It's the main source of knowledge when trying to use a piece of code and should contain all the information necessary to do so.

## Comments
While best code is self-explainatory, that's not always possible. Comments are useful to explain it

### Writing Good Comments
- Don't repeat code
- Keep them simple
- Explain unconventional code
- if it's hard to explain, fix the code

### Consistency
Whether following widely accepted style of commenting or one of your own, keeping it consistent and coherent is very important.

## Documentation

### Project Level
The need for documentation is different for projects of different levels

#### Private projects
Don't need much documentation, as you'll be the only user. Should only include information that will help you in the future

#### Shared projects
Projects for few people. Should include some more information to help other contributors understand everything.

should include:
- Readme
- Examples of use
- How to contribute

#### Public/Open Source Projects
Are intended to be shared with a large group and can have large development team. The documentation should be high priority.

should have:
- Readme
- How to contribute 
- Code of conduct
- License
- docs
	- tutorials
	- how-to-guides
	- references
	- explanations

### Structure
Code should be documented at different levels.
- README file - structure, file names, dependencies
- Header Comments - Module/component name, purpose, interface
- Docstrings  - function's name parameters, return value nad behaviour

### Create a manual
Create a guide for building/installing your module/component with description of configuration and deployment.

### API reference
Describe dependencies, methods, properties and events. You can also include examples of code and tests.

### Popular Tools
- Markdown on GitHub - good lightweight
- JSDoc - for JavaScript
- Javadoc - for Java
- Sphinx 
- Pydoc - for python
- Doxygen

## By Language
[[Documenting Code - Python]] 
---
title: SOLID Principles
Tags: Public
Aliases:
Date created: 2023-06-26 19:19
---

SOLID is a mnemonic acronym for five object-oriented designs

S - Single responsibility principle
O - Open-closed principle
L - Liskov substitution principle
I - Interface segregation principle 
D - Dependency inversion principle 

---

#### Single Responsibility
"A class should have one, and only one, reason to change" - Robert C. Martin

In other words a class should have only one responsibility - that ensures that separate responsibilities stay independent from each other

#### Open-closed Principle
>"Software principles should be open for extension but closed for modification"         
>\- *Bertrand Meyer, 'Object Oriented Software Construction'*

You should be able to add new functionality to existing code without changing the existing code

Implementing the rule through inheritance leads to tight coupling, and if you don't want your implementations to share code it's better implemented with interfaces, where interfaces are closed for implementation.

#### Liskov Substitution Principle
>"Let _Φ(x)_ be a property provable about objects _x_ of type _T_. Then _Φ(y)_ should be true for objects _y_ of type _S_ where _S_ is a subtype of _T_." 
>\-*Barbara Liskov*

In simpler terms objects of superclass must be replaceable with objects of their subclasses without breaking the application

#### Interface Segregation Principle
>“Clients should not be forced to depend upon interfaces that they do not use.”         
> \-*Robert C. Martin*

Code should not be forced to implement interfaces(and methods) it doesn't need. That is achieving by splitting interfaces into smaller, more specific ones so that clients only have to know about the methods that are of interest to them

It aims to reduce side effects of changes in codebase, by splitting software into multiple, independent parts.

#### Dependency Inversion

1. High-level modules should not import anything from low-level modules. Both should depend on abstractions (e.g., interfaces).
2. Abstractions should not depend on details. Details (concrete implementations) should depend on abstractions.

It is important that both high and low level modules depend on abstraction, splitting them with a layer of abstraction placed between them



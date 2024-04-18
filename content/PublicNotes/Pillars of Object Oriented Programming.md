---
title: Pillars of Object Oriented Programming
tags:  Public
Aliases: Abstraction, Encapsulation, Inheritance, Polymorphism
Date created: 2023-06-26 17:59
---

### Abstraction
---
To abstract something is to hide it away behind a layer of simplicity. It means that you create a facade that you can use, that keeps part of the technical implementation out of sight. ^06f6e9

It's necessary to improve the readability of code, as it lets you interact with it at a higher level. It also helps with reusability, as you ran reuse abstracted parts of code more easily.

### Encapsulation
---
Encapsulation is bundling data and methods operating on said data into one unit, and restricting access to that data from outside. It usually involves hiding a part or all the data in the object by having its fields private, and only accessible through public methods.

Allows creating an interface independent of it's internal implementation, decoupling parts of the code, meaning they can also be more easily adapted to changes.

### Inheritance
---
Inheritance is the mechanism allowing to create subclasses or child-classes that have all the characteristics of base- or parent-class.

It can be used to easily make several different objects that are similar, by inheriting the similarities from a parent-class, and only implementing the differences specifically. 

It allows for convenient code reuse, and prevents repetition across different classes. Moreover allows for instances of child-classes to be counted as instances of parent-class.

-> [[Composition over Inheritance]]

### Polymorphism
---
Polymorphism is the idea that an entity in the code can have more than one form.  It allows a function or class to be used with different implementation depending on the circumstances.

  - static polymorphism (compile time) - overloading methods with a different number of parameters
  - dynamic polymorphism (runtime) - letting a child class have it's own definition of a method belonging to a parent class 

Can be implemented through interfaces, inheritance or virtual methods.
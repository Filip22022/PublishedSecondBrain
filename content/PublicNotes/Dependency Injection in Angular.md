---
title: Dependency Injection in Angular
Date created: 2024-04-19 21:04
Aliases:
tags: 
  - Public
---

[[Angular]] provides the ability to [[Dependency Injection|inject]] a service into a component

## Creating an Injectable Service

```ts
@Injectable({providedIn: 'root'})
export class HeroService {
```

```ts
constructor(private service: HeroService) { }
```

The necessary dependencies are inferred automatically based on component's constructor parameter types.  Angular injector then provides or creates the service.

## Registering Providers
A service must have at least one registered provider. It can be declared in the `@Injectable` metadata, or in the `@Component` metadata

By default `ng generate service` registers a provider with the root injector.
```ts
@Injectable({providedIn: 'root'})
export class HeroService {
```
This allows Angular to create single, shared instance of the service for all classes that require it, and perform [[Tree-Shaking]] 

When registering a service at the component level, you get a new service instance with each new component instance 
```ts
@Component({
  standalone: true,
  selector:    'app-hero-list',
  templateUrl: './hero-list.component.html',
  imports:     [ NgFor, NgIf, HeroDetailComponent ],
  providers:  [ HeroService ]
})
```
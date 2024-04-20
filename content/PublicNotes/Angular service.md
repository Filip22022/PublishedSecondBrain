---
title: Angular service
Date created: 2024-04-19 09:53
Aliases:
tags: 
  - Public
---

Services are values, functions or features in an application, that are unrelated to the UI. They are the _model_  layer of the application

## Guidelines
- Use services as singletons with [[Dependency Injection]]
- Create services with single responsibility
- Use `@Injectable()` class decorator instead of `@Inject` parameter decorator when using types as tokens 
- Provide a service with application root injector in `@Injectable` decorator
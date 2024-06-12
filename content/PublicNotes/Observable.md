---
title: Observable
Date created: 2024-06-08 18:09
Aliases:
tags: 
  - Public
---
A Rx library implementation of [[Data Streams]] 

Observables are collections of values that can be subscribed to by Observers and will notify them with new data. They work in Push system, meaning that *data producer* decides when to send data to the *data consumer*

They can be be viewed as generalization of functions with zero arguments, but multiple values. In that way subscribing to an observable is akin to calling a function.


## Synchronicity
Subscribing to an observable is a synchronous operation, but unlike functions observables can 'return' multiple values over time

```js
import { Observable } from 'rxjs';

const foo = new Observable((subscriber) => {
  console.log('Hello');
  subscriber.next(42);
  subscriber.next(100); // "return" another value
  subscriber.next(200); // "return" yet another
});
```

And the values can be returned asynchronously
```js
import { Observable } from 'rxjs';

const foo = new Observable((subscriber) => {
  console.log('Hello');
  subscriber.next(42);
  subscriber.next(100);
  subscriber.next(200);
  setTimeout(() => {
    subscriber.next(300); // happens asynchronously
  }, 1000);
});
```

Unlike calling a function with returns **one value synchronously**, subscribing to an observable returns **any amount of values either synchronously or asynchronously**

## Using Observables

### Creation
The constructor of an observable takes one argument, which is the `subscribe` function

```js
import { Observable } from 'rxjs';

const observable = new Observable(subscriber => {
  subscriber.next('Hello');
  subscriber.next('World');
  subscriber.complete();
});

observable.subscribe({
  next(value) { console.log('Received value:', value); },
  error(err) { console.error('Error occurred:', err); },
  complete() { console.log('Stream complete'); }
});
```

They can also be created using special creation functions

- `const observable = of(<values>);` creates observable emitting sequence of values
- `const observable = from([array/promise/iterable]);` converts the array/promise/iterable
- `const observable = fromEvent(button, 'click');` converts DOM event
- `const observable = interval(<miliseconds>);` emits sequence of numbers starting at 0 every specified interval

### Subscribing

```js
observable.subscribe((x) => console.log(x));
```

"Subscribing to an observable is like calling function, providing callbacks where the data will be delivered to"

`observable.subscribe` returns an object - the `Subscription`, which represents ongoing execution

### Execution
The code inside Observable `subscribe` function represents Observable execution - a lazy computation happening for each observer that subscribes, producing multiple values.

Three possible types of values:
- `next` notification (sends a value)
- `error` notification (sends a js error or exception)
- `complete` notification (doesn't send a value)

>The `error` and `complete` notifications can be only delivered once, and nothing else can be delivered afterwards

### Disposal

Disposing the observable execution is handy, when we want to cancel the execution before it completes, and particularly for aborting infinite execution in finite time.

To cancel the execution call `unsubscribe()` method on a `Subscription` object

#### Example
```js
import { Observable } from 'rxjs';

const observable = new Observable(function subscribe(subscriber) {
  // Keep track of the interval resource
  const intervalId = setInterval(() => {
    subscriber.next('hi');
  }, 1000);

  // Provide a way of canceling and disposing the interval resource
  return function unsubscribe() {
    clearInterval(intervalId);
  };
});
```
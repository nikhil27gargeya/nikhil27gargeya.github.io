# Asynchronous Programming

Synchronous:
```
const name = "Jim";
const greeting = `Hello, my name is ${name}`;
console.log(greeting);

function makeGreeting(name) {
  return `Hello, my name is ${name}!`;
}
```
With synchronous programming, the program steps through each line of code in the order written and is unresponsive while a function is running due to its single threaded nature.

Callback vs Promise vs Async Await:
Callback: is a function passed to another function and is invoked after the function completes. issue is nesting callbacks is (callback hell)
Promise: object that defers some asynchronous event while something else is done.
Async Await: cleaner syntax because asynchronous wrapper and it looks like synchronous code, no need to nest promises. Good for writing multiple async functions so promises don't need to be nested.

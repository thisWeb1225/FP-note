# Do everything with function

program === functions

比起問程式需要怎麼做，應該要問自己，我的程序需要包含甚麼，以及他會吐出什麼

### Imperative

**Imperative is How to do**

```jsx
let userName = 'Jack';
let greeting = 'Hi';

console.log(`${greeting}, ${userName}!`);

greeting = 'hollo';
console.log(`${greeting}, ${userName}!`)
```

### Functional

**Declarative is What should do**

```jsx
function greet(greeting, userName) {
  return `${greeting}, ${userName}`;
}

greet('Hi', 'Jack');
greet('Hello', 'Jack');
```
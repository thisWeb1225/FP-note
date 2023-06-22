# Recursion

## Iteration vs Recursion

Iteration: imperative、looping、stateful

Recursion : functional、self-referential、stateless

Iteration 的情況是，每一個 loop 的值都會改變，所以我們可能要思考每次的值是什麼。

而 Recursion 只在乎每次的輸入和輸出，用一種無狀態的方式去循環。

```tsx
// Iteration
function sum (numbers: Array<number>) {
  let total = 0;
  for (let i = 0; i < numbers.length; i++) {
    total += i;
  }
  return total;
}

sum([1, 2, 3, 4, 5]) // 10

// Recursion
function sum (numbers: Array<number>) {
  if (numbers.length === 1) {
    return numbers[0];
  } else {
    return numbers[0] + sum(numbers.slice(1));
  }
}

sum([1, 2, 3, 4, 5]) // 10
```

## Exercise

1. **階層 Factorial**

```tsx
// Iteration
function iterativeFactorial(n) {
  let product = 1;
  while (n > 0) {
    product *= n;
    n--;
  }
  return product;
}

// Recursion
function recursiveFactorial(n) {
	if ( n === 0 ) return 1;
	return n * resursiveFactorail(n - 1)
}
```

1. **Fibonacci Number**

`fibonacci(n) = fibonacci(n-1) + fibonacci(n-2)`. By convention, the first two numbers are fixed: `fibonacci(0) = 0` and `fibonacci(1) = 1`.

```tsx
// Iteration
function iterativeFibonacci(n) {
	if (n === 0) return 0;
	if (n === 1) return 1;
	
	let previous = 0;
	let current = 1;
	for (let i = 1; i < n; i++) {
		let next = previous + current; // f(n) = f(n-1) + f(n-2)
		previous = current;
		current = next; 
	}

	return current;
}

// Recursion
function recursiveFibonacci(n) {
	if (n === 0) return 0;
  if (n === 1) return 1;
  return recursiveFibonacci(n - 2) + recursiveFibonacci(n - 1);
}
```
Functional Programming & Higher Order Functions 💡

🔴 Functional Programming is a programming paradigm where you mostly construct and structure your code using functions. These functions take input as arguments and return the output based on the inputs provided. It doesn’t allow any mutation nor shared state.

One of the most powerful concepts of functional programming is higher-order functions 👇

🔺 Higher order function is a function that takes another function as an argument or returns a function or both. map(), filter(), forEach() are some built in higher-order functions.

🔻 One of the great advantages of using higher-order functions is that we can create smaller functions that only take care of one piece of logic. Then, we compose more complex functions by using different smaller functions. This helps to reduce bugs and makes our code easier to read and understand.

Checkout the example below 🔽

In this example, using higher-order functions, sqrt logic is moved to a new function and provided as a callback in the main function. This makes the code concise and even we can reuse the same function for different logic. (This is just a simple example for better understanding)

const values = [1,4,9];

// before
const calculateSqrt = function(arr, callback) {
const output = [];
for (let i = 0; i < arr.length; i++) {
output.push(Math.sqrt(arr[i]))
}
return output;
}

console.log(calculateSqrt(values))

// After
const findSqrt = (value) => {
return Math.sqrt(value);
}

const calculate = function(arr, callback) {
const output = [];
for (let i = 0; i < arr.length; i++) {
output.push(callback(arr[i]))
}
return output;
}

console.log(calculate(values, findSqrt))

# Topic 2: Functions 🎯

## 1️⃣ Why Does This Exist?

Imagine you're a restaurant. Every time someone orders food, you don't create a completely new process. Instead, you follow the same steps:
1. Take the order
2. Cook the food
3. Plate it
4. Serve it

Functions are the same. They're reusable blocks of code that perform a specific task. Instead of writing the same code over and over, you write it once and reuse it many times.

## 2️⃣ Mental Model

Think of a function like a **kitchen recipe**:

```
┌─────────────────┐
│ Recipe: Cookies │
├─────────────────┤
│ Input (ingredients):
│  - Flour
│  - Butter
│  - Sugar
│
│ Instructions (steps):
│  1. Mix ingredients
│  2. Bake 15 mins
│
│ Output (result):
│  - Delicious cookies
└─────────────────┘
```

- **Input**: What you need to provide (ingredients)
- **Process**: What the function does (recipe steps)
- **Output**: What you get back (cookies)

## 3️⃣ Real-World Analogy

A function is like a **vending machine**:

```
Put in: $2 and press "Soda"
       ↓
[VENDING MACHINE]
       ↓
Get out: A cold soda

The vending machine doesn't care if you use it once or a million times.
You always put in money, and you get out a drink. Same process, every time.
```

## 4️⃣ The Three Ways to Create Functions

### Method 1: Function Declaration
```javascript
function greet(name) {
  return `Hello, ${name}!`;
}

greet("Alice");  // "Hello, Alice!"
```

### Method 2: Function Expression
```javascript
const greet = function(name) {
  return `Hello, ${name}!`;
};

greet("Bob");  // "Hello, Bob!"
```

### Method 3: Arrow Function (Modern & Preferred)
```javascript
const greet = (name) => {
  return `Hello, ${name}!`;
};

greet("Charlie");  // "Hello, Charlie!"

// Short form (if only one line)
const greet = (name) => `Hello, ${name}!`;
```

## 5️⃣ Anatomy of a Function

```javascript
const add = (a, b) => {
  //  ↑   ↑ ↑  ↑  ↑
  //  |   | |  |  └─ Body (code that runs)
  //  |   | |  └──── Parameters (inputs)
  //  |   | └─────── Arrow function syntax
  //  |   └───────── Function name
  //  └───────────── Keyword (const)

  const result = a + b;
  return result;
  // ↑ Return (what you get back)
};

add(2, 3);  // Call the function with arguments
//  ↑  ↑ ↑
//  |  └ Arguments (actual values passed in)
//  └──── Function call
```

## 6️⃣ Parameters vs Arguments

**Parameters**: The variable names in the function definition
**Arguments**: The actual values passed when calling the function

```javascript
// Define function with PARAMETERS
const multiply = (a, b) => {  // a and b are parameters
  return a * b;
};

// Call function with ARGUMENTS
multiply(5, 3);  // 5 and 3 are arguments
// Result: 15
```

## 7️⃣ Return Values

Functions can send data back to you:

```javascript
// With return
const square = (num) => {
  return num * num;
};

const result = square(5);
console.log(result);  // 25

// Without return (implicitly returns undefined)
const logMessage = (msg) => {
  console.log(msg);
  // No return statement = returns undefined
};

const x = logMessage("Hi");  // Prints "Hi"
console.log(x);  // undefined
```

## 8️⃣ Beginner Examples

### Example 1: Simple Addition Function
```javascript
const add = (num1, num2) => {
  return num1 + num2;
};

console.log(add(5, 3));      // 8
console.log(add(10, 20));    // 30
console.log(add(-5, 5));     // 0
```

### Example 2: Function That Checks Age
```javascript
const isAdult = (age) => {
  return age >= 18;
};

console.log(isAdult(25));    // true
console.log(isAdult(15));    // false
console.log(isAdult(18));    // true
```

### Example 3: Function With Multiple Lines
```javascript
const getUserGreeting = (firstName, lastName) => {
  const fullName = `${firstName} ${lastName}`;
  const greeting = `Welcome, ${fullName}!`;
  return greeting;
};

console.log(getUserGreeting("John", "Doe"));
// "Welcome, John Doe!"
```

### Example 4: Function That Doesn't Return Anything
```javascript
const printProfile = (name, age) => {
  console.log(`Name: ${name}`);
  console.log(`Age: ${age}`);
  // No return statement
};

printProfile("Alice", 28);
// Prints:
// Name: Alice
// Age: 28
```

## 9️⃣ Real-World Example: Todo App Functions

```javascript
// Function 1: Create a new todo
const createTodo = (id, title, completed = false) => {
  return {
    id: id,
    title: title,
    completed: completed,
    createdAt: new Date()
  };
};

// Function 2: Check if todo is done
const isTodoDone = (todo) => {
  return todo.completed === true;
};

// Function 3: Mark todo as complete
const completeTodo = (todo) => {
  todo.completed = true;
  return todo;
};

// Function 4: Get all incomplete todos
const getIncompleteTodos = (todos) => {
  const incomplete = [];
  for (let i = 0; i < todos.length; i++) {
    if (!todos[i].completed) {
      incomplete.push(todos[i]);
    }
  }
  return incomplete;
};

// Usage
const todo1 = createTodo(1, "Buy groceries");
const todo2 = createTodo(2, "Clean room");
const todo3 = createTodo(3, "Study React", true);

const allTodos = [todo1, todo2, todo3];

console.log(isTodoDone(todo1));         // false
console.log(isTodoDone(todo3));         // true

completeTodo(todo1);
console.log(todo1.completed);           // true

const incomplete = getIncompleteTodos(allTodos);
console.log(incomplete.length);         // 1 (only todo2)
```

## 🔟 Arrow Function Shorthand

Arrow functions have a special short syntax when there's only one line:

```javascript
// Full version
const double = (x) => {
  return x * 2;
};

// Short version (one-liner)
const double = (x) => x * 2;

// No parameters? Need empty parentheses
const getRandom = () => Math.random();

// Single parameter? Can skip parentheses
const square = x => x * x;

// But it's clearer to use parentheses anyway
const square = (x) => x * x;
```

## 1️⃣1️⃣ Default Parameters

Provide default values if no argument is passed:

```javascript
const greet = (name = "Friend") => {
  return `Hello, ${name}!`;
};

console.log(greet("Alice"));     // "Hello, Alice!"
console.log(greet());            // "Hello, Friend!"

// Real-world example
const createUser = (name, role = "user", active = true) => {
  return { name, role, active };
};

console.log(createUser("John"));
// { name: "John", role: "user", active: true }

console.log(createUser("Jane", "admin"));
// { name: "Jane", role: "admin", active: true }

console.log(createUser("Bob", "moderator", false));
// { name: "Bob", role: "moderator", active: false }
```

## 1️⃣2️⃣ Common Mistakes to Avoid

### ❌ Mistake 1: Forgetting to return
```javascript
// ❌ No return
const add = (a, b) => {
  a + b;  // Just calculates, doesn't return
};

console.log(add(2, 3));  // undefined ❌

// ✅ With return
const add = (a, b) => {
  return a + b;
};

console.log(add(2, 3));  // 5 ✅
```

### ❌ Mistake 2: Code after return
```javascript
const calculate = (x) => {
  return x * 2;
  console.log("This never runs!");  // ❌ Dead code
};
```

### ❌ Mistake 3: Calling function without parentheses
```javascript
const greet = () => "Hello";

console.log(greet);      // ❌ Prints the function itself
console.log(greet());    // ✅ Prints "Hello"
```

### ❌ Mistake 4: Parameters vs Arguments confusion
```javascript
const add = (a, b) => a + b;  // a, b are parameters

add(2);           // ❌ Missing argument, b is undefined
add(2, 3, 4);     // ❌ Extra argument 4 is ignored

add(2, 3);        // ✅ Correct
```

### ❌ Mistake 5: Arrow function with curly braces but no return
```javascript
// ❌ Forgot return
const double = (x) => {
  x * 2;
};
console.log(double(5));  // undefined

// ✅ Add return
const double = (x) => {
  return x * 2;
};
console.log(double(5));  // 10

// ✅ Or use short syntax
const double = (x) => x * 2;
console.log(double(5));  // 10
```

## 1️⃣3️⃣ Best Practices

### ✅ Best Practice 1: Use arrow functions for most cases
```javascript
// ❌ Old style (function declaration)
function calculate(a, b) {
  return a + b;
}

// ✅ Modern style (arrow function)
const calculate = (a, b) => a + b;
```

### ✅ Best Practice 2: Function names should describe what they do
```javascript
// ❌ Vague names
const f = (x) => x * 2;
const calc = (a, b) => a + b;

// ✅ Clear names
const doubleNumber = (x) => x * 2;
const addNumbers = (a, b) => a + b;
const getUserAge = (user) => user.age;
```

### ✅ Best Practice 3: Use one responsibility per function
```javascript
// ❌ Doing too much
const processUser = (user) => {
  user.verified = true;
  user.lastLogin = new Date();
  sendEmail(user.email);
  updateDatabase(user);
  console.log("Done!");
};

// ✅ Split into focused functions
const verifyUser = (user) => {
  user.verified = true;
};

const updateLastLogin = (user) => {
  user.lastLogin = new Date();
};

const notifyUser = (user) => {
  sendEmail(user.email);
};
```

### ✅ Best Practice 4: Keep functions small and readable
```javascript
// ❌ Too complex
const process = (arr) => {
  const result = [];
  for (let i = 0; i < arr.length; i++) {
    if (arr[i] > 0) {
      result.push(arr[i] * 2);
    }
  }
  return result;
};

// ✅ Clear and simple
const filterPositive = (numbers) => numbers.filter(n => n > 0);
const doubleNumbers = (numbers) => numbers.map(n => n * 2);
const processNumbers = (numbers) => {
  return doubleNumbers(filterPositive(numbers));
};
```

## 1️⃣4️⃣ Mini Challenge

### Challenge 1: Create a temperature converter
Create functions that convert temperatures:

```javascript
// Create these functions:
// 1. celsiusToFahrenheit(c) - Formula: (c × 9/5) + 32
// 2. fahrenheitToCelsius(f) - Formula: (f - 32) × 5/9

// Test:
console.log(celsiusToFahrenheit(0));    // 32
console.log(celsiusToFahrenheit(100));  // 212
console.log(fahrenheitToCelsius(32));   // 0
console.log(fahrenheitToCelsius(212));  // 100
```

<details>
<summary>Solution</summary>

```javascript
const celsiusToFahrenheit = (c) => (c * 9/5) + 32;
const fahrenheitToCelsius = (f) => (f - 32) * 5/9;

console.log(celsiusToFahrenheit(0));    // 32
console.log(celsiusToFahrenheit(100));  // 212
console.log(fahrenheitToCelsius(32));   // 0
console.log(fahrenheitToCelsius(212));  // 100
```
</details>

### Challenge 2: Create a password validator
Create a function that checks if a password is strong enough:
- At least 8 characters
- Contains at least one letter
- Contains at least one number

```javascript
const isStrongPassword = (password) => {
  // Your code here
};

console.log(isStrongPassword("abc123"));      // false (too short)
console.log(isStrongPassword("abcdefgh"));    // false (no number)
console.log(isStrongPassword("12345678"));    // false (no letter)
console.log(isStrongPassword("abcde1234"));   // true
```

<details>
<summary>Solution</summary>

```javascript
const isStrongPassword = (password) => {
  const hasMinLength = password.length >= 8;
  const hasLetter = /[a-zA-Z]/.test(password);
  const hasNumber = /[0-9]/.test(password);
  
  return hasMinLength && hasLetter && hasNumber;
};

console.log(isStrongPassword("abc123"));      // false (too short)
console.log(isStrongPassword("abcdefgh"));    // false (no number)
console.log(isStrongPassword("12345678"));    // false (no letter)
console.log(isStrongPassword("abcde1234"));   // true
```
</details>

## 1️⃣5️⃣ Mini Project: Calculator Functions

Create a simple calculator with multiple functions:

```javascript
// Basic operations
const add = (a, b) => a + b;
const subtract = (a, b) => a - b;
const multiply = (a, b) => a * b;
const divide = (a, b) => {
  if (b === 0) {
    return "Error: Cannot divide by zero";
  }
  return a / b;
};

// Batch operations
const sum = (numbers) => {
  let total = 0;
  for (let i = 0; i < numbers.length; i++) {
    total += numbers[i];
  }
  return total;
};

const average = (numbers) => {
  if (numbers.length === 0) return 0;
  return sum(numbers) / numbers.length;
};

const findMax = (numbers) => {
  let max = numbers[0];
  for (let i = 1; i < numbers.length; i++) {
    if (numbers[i] > max) {
      max = numbers[i];
    }
  }
  return max;
};

// Usage
console.log(add(10, 5));           // 15
console.log(subtract(10, 5));      // 5
console.log(multiply(10, 5));      // 50
console.log(divide(10, 5));        // 2
console.log(divide(10, 0));        // "Error: Cannot divide by zero"

const scores = [85, 90, 78, 92, 88];
console.log(sum(scores));          // 433
console.log(average(scores));      // 86.6
console.log(findMax(scores));      // 92
```

## 1️⃣6️⃣ Interview Questions

### Q1: What's the difference between function declaration and arrow function?

**Answer:**
```javascript
// Function declaration
function greet(name) {
  return `Hello, ${name}`;
}

// Arrow function
const greet = (name) => `Hello, ${name}`;
```

Key differences:
- Arrow functions are more concise
- `this` keyword behaves differently (advanced topic)
- Function declarations are hoisted (can call before defining)

### Q2: Can a function return another function?

**Answer:**
Yes! This is called a **higher-order function**:

```javascript
const multiplier = (factor) => {
  return (number) => number * factor;
};

const double = multiplier(2);
console.log(double(5));  // 10

const triple = multiplier(3);
console.log(triple(5));  // 15
```

### Q3: What's the difference between parameters and arguments?

**Answer:**
- **Parameters**: Variable names in the function definition
- **Arguments**: Actual values passed when calling the function

```javascript
const add = (a, b) => a + b;  // a, b are parameters
add(5, 3);                     // 5, 3 are arguments
```

### Q4: What does "return early" mean?

**Answer:**
It means exiting a function early instead of running all the code:

```javascript
const getDiscount = (age) => {
  if (age < 0) return null;           // Return early ✅
  if (age < 13) return 0.5;           // Return early ✅
  if (age < 65) return 0;
  return 0.3;
};
```

### Q5: When would you use default parameters?

**Answer:**
When you want to provide a fallback value if no argument is passed:

```javascript
const createMessage = (greeting = "Hello", name = "Friend") => {
  return `${greeting}, ${name}!`;
};

console.log(createMessage("Hi", "Alice"));   // "Hi, Alice!"
console.log(createMessage("Hi"));            // "Hi, Friend!"
console.log(createMessage());                // "Hello, Friend!"
```

## 🎓 Summary

| Concept | Usage |
|---------|-------|
| **Function** | Reusable code block that performs a task |
| **Parameters** | Input variables in function definition |
| **Arguments** | Actual values passed to function |
| **Return** | Value sent back from function |
| **Arrow function** | Modern, concise syntax with `=>` |
| **Default parameters** | Fallback values if no argument passed |

---

## 📚 Next Topic

Ready to learn about **Arrays & Objects**? Go to `03_Arrays_and_Objects.md`

## 💡 Quick Reference

```javascript
// Function declaration
function add(a, b) {
  return a + b;
}

// Arrow function (full)
const add = (a, b) => {
  return a + b;
};

// Arrow function (short)
const add = (a, b) => a + b;

// With default parameter
const greet = (name = "Friend") => `Hello, ${name}!`;

// No parameters
const getRandom = () => Math.random();

// Single parameter (parentheses optional)
const double = x => x * 2;
```

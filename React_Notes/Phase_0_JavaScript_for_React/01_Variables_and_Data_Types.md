# Topic 1: Variables & Data Types 🎯

## 1️⃣ Why Does This Exist?

Every program stores information. Whether you're building a video game, a web app, or a calculator, you need to remember things:
- What is the user's name?
- How many points do they have?
- Is the user logged in?
- What's in their shopping cart?

Variables are containers that hold this information. Without variables, you'd have no way to store and retrieve data.

## 2️⃣ Mental Model

Think of a variable like a **labeled box**:

```
┌─────────────────────┐
│  name: "John"       │  ← Variable name (label)
│  value: "John"      │  ← What's inside the box
└─────────────────────┘
```

- The **label** is the variable name (e.g., `name`, `age`, `isLoggedIn`)
- The **contents** are the value (e.g., `"John"`, `25`, `true`)
- You can put different things in the box and change what's inside

## 3️⃣ Real-World Analogy

Imagine a post office:
- Each mailbox has a **label** (variable name): Box #42
- Inside the mailbox is **mail** (the value): a letter from your mom
- You can take out the old mail and put in new mail
- The label stays the same, but the contents change

## 4️⃣ Syntax Breakdown

### The Three Ways to Declare Variables

```javascript
// ❌ OLD WAY (avoid in modern JavaScript)
var age = 25;

// ✅ MODERN WAY - Use const by default
const name = "John";

// ✅ ALTERNATIVE - Use let if you need to reassign
let score = 0;
score = 100;  // This is allowed with let
```

### Why Three Keywords?

| Keyword | Reassignable | Scope | When to Use |
|---------|--------------|-------|-------------|
| `const` | ❌ No | Block | **Default choice** - prevents accidental changes |
| `let` | ✅ Yes | Block | When you need to change the value later |
| `var` | ✅ Yes | Function | **Avoid** - old syntax with confusing rules |

## 5️⃣ Primitive Data Types

JavaScript has several basic data types:

### String (text)
```javascript
const name = "Alice";
const greeting = 'Hello, World!';
const multiline = `This is
a multiline
string`;
```

### Number (integers and decimals)
```javascript
const age = 25;
const price = 19.99;
const temperature = -5;
```

### Boolean (true or false)
```javascript
const isLoggedIn = true;
const hasPermission = false;
```

### Null (intentional emptiness)
```javascript
const data = null;  // You set it to null on purpose
```

### Undefined (unintentional emptiness)
```javascript
let x;
console.log(x);  // undefined (nothing assigned yet)
```

### Symbol & BigInt (advanced, skip for now)

## 6️⃣ Object Data Types

Objects store multiple related values together:

```javascript
const person = {
  name: "John",
  age: 30,
  city: "New York",
  isStudent: false
};

// Access values with dot notation
console.log(person.name);     // "John"
console.log(person.age);      // 30

// Or with bracket notation
console.log(person["city"]);  // "New York"
```

## 7️⃣ Array Data Type

Arrays store lists of values:

```javascript
const fruits = ["apple", "banana", "orange"];

// Access by position (index starts at 0)
console.log(fruits[0]);    // "apple"
console.log(fruits[1]);    // "banana"
console.log(fruits.length);  // 3
```

## 8️⃣ Beginner Examples

### Example 1: Simple Variables
```javascript
// Declare a variable
const city = "London";

// Use the variable
console.log(city);  // "London"

// You can't reassign const (this causes an error)
// city = "Paris";  // ❌ TypeError

// But with let, you can
let count = 0;
count = 5;  // ✅ OK
console.log(count);  // 5
```

### Example 2: Different Data Types
```javascript
const title = "My App";           // String
const numberOfUsers = 1000;       // Number
const version = 2.5;              // Number
const isDarkMode = true;          // Boolean
const emptyValue = null;          // Null
let user;                          // Undefined
```

### Example 3: Objects and Arrays
```javascript
// A student object
const student = {
  name: "Maria",
  grade: "A",
  courses: ["Math", "Science", "English"]
};

// Access the data
console.log(student.name);              // "Maria"
console.log(student.courses[0]);        // "Math"
console.log(student.courses.length);    // 3
```

## 9️⃣ Real-World Example: Building a Todo App

```javascript
// Variables for a todo item
const todoItem = {
  id: 1,
  title: "Buy groceries",
  description: "Milk, eggs, bread",
  completed: false,
  dueDate: "2024-06-22",
  priority: "high"
};

// Access and display
console.log(`Task: ${todoItem.title}`);
console.log(`Priority: ${todoItem.priority}`);
console.log(`Done? ${todoItem.completed}`);

// Create a list of todos
const todos = [
  { id: 1, title: "Buy groceries", completed: false },
  { id: 2, title: "Clean room", completed: true },
  { id: 3, title: "Study React", completed: false }
];

// Count incomplete todos
let incompleteCount = 0;
for (let i = 0; i < todos.length; i++) {
  if (!todos[i].completed) {
    incompleteCount++;
  }
}
console.log(`You have ${incompleteCount} incomplete tasks`);  // 2
```

## 🔟 Common Mistakes to Avoid

### ❌ Mistake 1: Using `var` (old habit)
```javascript
// ❌ Don't do this
var name = "John";

// ✅ Do this instead
const name = "John";
```

### ❌ Mistake 2: Trying to reassign `const`
```javascript
const age = 25;
age = 26;  // ❌ TypeError: Assignment to constant variable

// ✅ Use let if you need to reassign
let age = 25;
age = 26;  // ✅ OK
```

### ❌ Mistake 3: Confusing null and undefined
```javascript
// undefined = "I never assigned this"
let x;
console.log(x);  // undefined

// null = "I purposely set this to nothing"
let y = null;
console.log(y);  // null
```

### ❌ Mistake 4: Forgetting that arrays are 0-indexed
```javascript
const colors = ["red", "green", "blue"];
console.log(colors[0]);  // "red" (not "blue"!)
console.log(colors[3]);  // undefined (doesn't exist!)
```

### ❌ Mistake 5: Mutating objects unintentionally
```javascript
const person = { name: "John", age: 25 };

// This modifies the original object!
person.age = 26;  // Object content changed, but reference is same

console.log(person.age);  // 26 ✅ This is OK actually

// But be careful:
const person2 = person;  // Both point to same object
person2.age = 30;
console.log(person.age);  // 30 (person changed too!)
```

## 1️⃣1️⃣ Best Practices

### ✅ Best Practice 1: Use `const` by default
```javascript
// Start with const
const name = "John";
const age = 25;
const isStudent = true;
```

### ✅ Best Practice 2: Use `let` only when you need to reassign
```javascript
let count = 0;
count++;  // Need to change? Use let
```

### ✅ Best Practice 3: Use meaningful variable names
```javascript
// ❌ Bad
const x = 25;
const p = "John";

// ✅ Good
const userAge = 25;
const userName = "John";
const totalPrice = 99.99;
```

### ✅ Best Practice 4: Use camelCase for variable names
```javascript
// ❌ Bad (snake_case)
const user_name = "John";
const user_age = 25;

// ✅ Good (camelCase)
const userName = "John";
const userAge = 25;
```

### ✅ Best Practice 5: Group related variables in objects
```javascript
// ❌ Many separate variables
const firstName = "John";
const lastName = "Doe";
const userAge = 25;
const userEmail = "john@example.com";

// ✅ Grouped in an object
const user = {
  firstName: "John",
  lastName: "Doe",
  age: 25,
  email: "john@example.com"
};
```

## 1️⃣2️⃣ Mini Challenge

Try to solve these without looking at the solutions:

### Challenge 1: Create a book object
Create a variable called `book` that contains:
- title: "The Great Gatsby"
- author: "F. Scott Fitzgerald"
- pages: 180
- isClassic: true
- genres: ["Fiction", "Romance"]

Then log: `"The Great Gatsby by F. Scott Fitzgerald has 180 pages"`

<details>
<summary>Solution</summary>

```javascript
const book = {
  title: "The Great Gatsby",
  author: "F. Scott Fitzgerald",
  pages: 180,
  isClassic: true,
  genres: ["Fiction", "Romance"]
};

console.log(`${book.title} by ${book.author} has ${book.pages} pages`);
// "The Great Gatsby by F. Scott Fitzgerald has 180 pages"
```
</details>

### Challenge 2: Fix the errors
What's wrong with this code?

```javascript
var userName = "Alice";
userName = "Bob";

const userAge = 30;
userAge = 31;

const user = {
  name: "Charlie",
  email: "charlie@email.com"
};

user.name = "David";
console.log(user.name);
```

<details>
<summary>Solution</summary>

```javascript
// Line 1-2: ✅ OK - var is allowed but discouraged
// Line 4-5: ❌ ERROR - Can't reassign const
// Solution: Use let if you need to reassign
let userAge = 30;
userAge = 31;  // ✅ Now OK

// Line 7-11: ✅ OK - Objects can have their properties changed
// const means the reference can't change, but properties inside can
const user = {
  name: "Charlie",
  email: "charlie@email.com"
};

user.name = "David";  // ✅ This is allowed
console.log(user.name);  // "David"
```
</details>

## 1️⃣3️⃣ Mini Project: User Profile Manager

Create a simple program that manages a user's profile:

```javascript
// Create a user object with properties
const user = {
  username: "alex_dev",
  email: "alex@email.com",
  age: 24,
  isActive: true,
  joinDate: "2023-01-15",
  preferences: {
    darkMode: true,
    notifications: true,
    language: "English"
  },
  skills: ["JavaScript", "React", "CSS"]
};

// 1. Log a welcome message
console.log(`Welcome, ${user.username}!`);

// 2. Show user profile
console.log(`Email: ${user.email}`);
console.log(`Age: ${user.age}`);

// 3. Show first skill
console.log(`Primary skill: ${user.skills[0]}`);

// 4. Check if user is active
if (user.isActive) {
  console.log("User is active ✅");
} else {
  console.log("User is offline ❌");
}

// 5. Update a preference
user.preferences.darkMode = false;
console.log(`Dark mode: ${user.preferences.darkMode}`);
```

## 1️⃣4️⃣ Interview Questions

### Q1: What's the difference between `let`, `const`, and `var`?

**Answer:**
- `const`: Can't be reassigned, block-scoped, preferred for most variables
- `let`: Can be reassigned, block-scoped, used when value changes
- `var`: Can be reassigned, function-scoped, old syntax (avoid)

### Q2: When would you use `null` vs `undefined`?

**Answer:**
- `undefined`: JavaScript automatically assigns this when nothing is defined (forgot to assign)
- `null`: You explicitly set it to nothing on purpose

### Q3: Can you modify the contents of a `const` object?

**Answer:**
Yes! `const` prevents reassigning the variable itself, but you can modify properties inside:

```javascript
const user = { name: "John" };
user.name = "Alice";  // ✅ OK - modifying property
user = {};           // ❌ ERROR - can't reassign
```

### Q4: What's the difference between objects and arrays?

**Answer:**
- **Objects**: Store key-value pairs, use named keys
- **Arrays**: Store ordered values, use numeric indices

```javascript
const obj = { name: "John", age: 25 };      // Objects
const arr = ["John", 25, true];              // Arrays
```

### Q5: How do you access nested data?

**Answer:**
Use dot notation or bracket notation:

```javascript
const user = {
  name: "John",
  address: {
    city: "New York",
    zip: "10001"
  },
  hobbies: ["reading", "coding"]
};

console.log(user.address.city);      // "New York"
console.log(user.hobbies[0]);        // "reading"
```

## 🎓 Summary

| Concept | Key Point |
|---------|----------|
| `const` | Default choice - immutable variable reference |
| `let` | Use when you need to reassign |
| `var` | Avoid - old syntax |
| **Primitives** | string, number, boolean, null, undefined |
| **Objects** | Collections of key-value pairs |
| **Arrays** | Collections of values with numeric indices |

---

## 📚 Next Topic

Ready to learn about **Functions**? Go to `02_Functions.md`

## 💡 Quick Reference

```javascript
// Declaration
const name = "John";              // String
const age = 25;                   // Number
const isStudent = true;           // Boolean

// Objects
const person = { name: "John", age: 25 };
person.age = 26;                  // ✅ OK

// Arrays
const fruits = ["apple", "banana"];
console.log(fruits[0]);           // "apple"
fruits[1] = "orange";             // ✅ OK
```
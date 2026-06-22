# Topic 3: Arrays & Objects 🎯

## 1️⃣ Why Do These Exist?

Imagine you're building a student management system. You have thousands of students. If you created a separate variable for each student, you'd go crazy:

```javascript
// ❌ This is insane!
const student1 = "John";
const student2 = "Alice";
const student3 = "Bob";
// ... thousands more
```

Instead, you organize related data into **Arrays** and **Objects**. They let you store multiple values in one place.

## 2️⃣ Mental Models

### Arrays: An Ordered List 📋
Think of arrays like a **shopping list**:
```
┌───────────────────────┐
│ 0: Milk               │
│ 1: Bread              │
│ 2: Eggs               │
│ 3: Cheese             │
└───────────────────────┘
```

Each item has a **position** (index), starting from 0.

### Objects: A Dictionary 📖
Think of objects like a **real dictionary**:
```
┌──────────────────────┐
│ name    → "John"     │
│ age     → 25         │
│ email   → "j@m.com"  │
│ verified→ true       │
└──────────────────────┘
```

Each item has a **key** (name) and a **value**.

## 3️⃣ Real-World Analogy

**Arrays**: Like a **cinema seat map**
- Row 1, Seat 1
- Row 1, Seat 2
- Row 1, Seat 3
- Access by position: "Which seat is empty?"

**Objects**: Like a **person's ID card**
- Name: John
- Age: 25
- Address: 123 Main St
- Access by key: "What's their address?"

## 4️⃣ Creating Arrays

### Method 1: Array Literal (Preferred)
```javascript
const fruits = ["apple", "banana", "orange"];
const numbers = [1, 2, 3, 4, 5];
const mixed = [1, "hello", true, null, { name: "John" }];
const empty = [];
```

### Method 2: Array Constructor (Avoid)
```javascript
const numbers = new Array(1, 2, 3);  // Same as [1, 2, 3]
```

## 5️⃣ Accessing Array Elements

```javascript
const fruits = ["apple", "banana", "orange"];

// Access by index (starts at 0)
console.log(fruits[0]);         // "apple"
console.log(fruits[1]);         // "banana"
console.log(fruits[2]);         // "orange"
console.log(fruits[3]);         // undefined (doesn't exist)

// Get length
console.log(fruits.length);     // 3

// Get last element
console.log(fruits[fruits.length - 1]);  // "orange"
```

## 6️⃣ Modifying Arrays

```javascript
const fruits = ["apple", "banana"];

// Add to end
fruits.push("orange");
console.log(fruits);  // ["apple", "banana", "orange"]

// Remove from end
fruits.pop();
console.log(fruits);  // ["apple", "banana"]

// Add to beginning
fruits.unshift("mango");
console.log(fruits);  // ["mango", "apple", "banana"]

// Remove from beginning
fruits.shift();
console.log(fruits);  // ["apple", "banana"]

// Replace element
fruits[0] = "pear";
console.log(fruits);  // ["pear", "banana"]

// Insert in middle
fruits.splice(1, 0, "grape");  // Insert "grape" at index 1
console.log(fruits);  // ["pear", "grape", "banana"]
```

## 7️⃣ Creating Objects

### Method 1: Object Literal (Preferred)
```javascript
const person = {
  name: "John",
  age: 25,
  email: "john@example.com",
  isStudent: true
};
```

### Method 2: Empty Object, Then Add Properties
```javascript
const person = {};
person.name = "John";
person.age = 25;
person.email = "john@example.com";
```

### Method 3: Object Constructor (Avoid)
```javascript
const person = new Object();
person.name = "John";
```

## 8️⃣ Accessing Object Properties

```javascript
const person = {
  name: "John",
  age: 25,
  email: "john@example.com"
};

// Dot notation (preferred)
console.log(person.name);      // "John"
console.log(person.age);       // 25

// Bracket notation (when key has spaces or special characters)
console.log(person["name"]);   // "John"

// Using variable as key
const key = "email";
console.log(person[key]);      // "john@example.com"
```

## 9️⃣ Modifying Objects

```javascript
const person = {
  name: "John",
  age: 25
};

// Update property
person.age = 26;
console.log(person.age);      // 26

// Add new property
person.email = "john@example.com";
console.log(person);          // { name: "John", age: 26, email: "john@example.com" }

// Delete property
delete person.email;
console.log(person);          // { name: "John", age: 26 }

// Using bracket notation
person["phone"] = "555-1234";
console.log(person.phone);    // "555-1234"
```

## 1️⃣0️⃣ Beginner Examples

### Example 1: Array of Numbers
```javascript
const scores = [85, 90, 78, 92, 88];

console.log(scores[0]);        // 85
console.log(scores.length);    // 5

// Add a new score
scores.push(95);
console.log(scores);           // [85, 90, 78, 92, 88, 95]

// Update a score
scores[2] = 80;
console.log(scores);           // [85, 90, 80, 92, 88, 95]
```

### Example 2: Array of Objects
```javascript
const students = [
  { name: "John", grade: "A" },
  { name: "Alice", grade: "B" },
  { name: "Bob", grade: "A" }
];

console.log(students[0].name);     // "John"
console.log(students[1].grade);    // "B"
console.log(students.length);      // 3

// Add new student
students.push({ name: "Charlie", grade: "C" });
console.log(students.length);      // 4
```

### Example 3: Nested Objects
```javascript
const user = {
  name: "John",
  age: 25,
  address: {
    street: "123 Main St",
    city: "New York",
    zip: "10001"
  },
  hobbies: ["reading", "coding", "gaming"]
};

console.log(user.name);                // "John"
console.log(user.address.city);        // "New York"
console.log(user.address.zip);         // "10001"
console.log(user.hobbies[0]);          // "reading"
console.log(user.hobbies.length);      // 3
```

### Example 4: Mixed Operations
```javascript
const book = {
  title: "JavaScript Mastery",
  author: "Alex Dev",
  pages: 450,
  available: true,
  ratings: [4.5, 4.8, 4.2, 5.0],
  reviews: [
    { reviewer: "John", rating: 4.5 },
    { reviewer: "Alice", rating: 5.0 }
  ]
};

console.log(book.title);                    // "JavaScript Mastery"
console.log(book.ratings[0]);               // 4.5
console.log(book.reviews[0].reviewer);      // "John"
console.log(book.reviews[1].rating);        // 5.0
```

## 1️⃣1️⃣ Real-World Example: Todo App Data

```javascript
// Array of todo objects
const todos = [
  {
    id: 1,
    title: "Buy groceries",
    completed: false,
    priority: "high",
    dueDate: "2024-06-22",
    tags: ["shopping", "urgent"]
  },
  {
    id: 2,
    title: "Study React",
    completed: false,
    priority: "high",
    dueDate: "2024-06-25",
    tags: ["learning", "coding"]
  },
  {
    id: 3,
    title: "Call mom",
    completed: true,
    priority: "medium",
    dueDate: "2024-06-20",
    tags: ["personal"]
  }
];

// Access data
console.log(todos.length);                    // 3
console.log(todos[0].title);                  // "Buy groceries"
console.log(todos[0].priority);               // "high"
console.log(todos[0].tags[0]);                // "shopping"
console.log(todos[2].completed);              // true

// Add new todo
todos.push({
  id: 4,
  title: "Finish project",
  completed: false,
  priority: "high",
  dueDate: "2024-06-23",
  tags: ["work", "coding"]
});

// Update a todo
todos[1].completed = true;

// Get number of incomplete todos
let incomplete = 0;
for (let i = 0; i < todos.length; i++) {
  if (!todos[i].completed) {
    incomplete++;
  }
}
console.log(`${incomplete} incomplete todos`);  // "2 incomplete todos"
```

## 1️⃣2️⃣ Common Array Operations

```javascript
const numbers = [1, 2, 3, 4, 5];

// Check if value exists
const hasThree = numbers.includes(3);  // true

// Find index
const index = numbers.indexOf(4);       // 3

// Combine arrays
const more = [6, 7, 8];
const combined = numbers.concat(more);
// [1, 2, 3, 4, 5, 6, 7, 8]

// Slice (doesn't modify original)
const slice = numbers.slice(1, 4);
// [2, 3, 4]

// Reverse
const reversed = numbers.reverse();
// [5, 4, 3, 2, 1]

// Note: reverse() modifies the original!
console.log(numbers);  // [5, 4, 3, 2, 1]
```

## 1️⃣3️⃣ Common Object Operations

```javascript
const person = {
  name: "John",
  age: 25,
  email: "john@example.com"
};

// Get all keys
const keys = Object.keys(person);
// ["name", "age", "email"]

// Get all values
const values = Object.values(person);
// ["John", 25, "john@example.com"]

// Get key-value pairs
const entries = Object.entries(person);
// [["name", "John"], ["age", 25], ["email", "john@example.com"]]

// Check if property exists
const hasName = "name" in person;  // true
const hasPhone = "phone" in person;  // false

// Copy object (shallow)
const copy = Object.assign({}, person);
// { name: "John", age: 25, email: "john@example.com" }
```

## 1️⃣4️⃣ Common Mistakes to Avoid

### ❌ Mistake 1: Arrays are 0-indexed
```javascript
const colors = ["red", "green", "blue"];

console.log(colors[0]);  // "red" (not colors[1])
console.log(colors[1]);  // "green"
console.log(colors[3]);  // undefined (doesn't exist)
```

### ❌ Mistake 2: Confusing length property
```javascript
const fruits = ["apple", "banana", "orange"];

console.log(fruits.length);              // 3
console.log(fruits[fruits.length - 1]);  // "orange" (last item)
console.log(fruits[fruits.length]);      // undefined
```

### ❌ Mistake 3: Modifying array while looping
```javascript
// ❌ Don't do this
const arr = [1, 2, 3, 4, 5];
for (let i = 0; i < arr.length; i++) {
  if (arr[i] === 3) {
    arr.splice(i, 1);  // Messes up loop!
  }
}

// ✅ Use filter instead
const filtered = arr.filter(num => num !== 3);
```

### ❌ Mistake 4: Using undefined key
```javascript
const person = { name: "John" };

console.log(person.age);  // undefined (property doesn't exist)

// ✅ Check first
if (person.age !== undefined) {
  console.log(person.age);
}

// Or use optional chaining (advanced)
console.log(person?.age);  // undefined (no error)
```

### ❌ Mistake 5: Confusing reference vs value
```javascript
// Arrays and objects are references
const original = { name: "John" };
const copy = original;  // Both point to same object!

copy.name = "Alice";
console.log(original.name);  // "Alice" (original changed too!)

// ✅ Use Object.assign or spread
const trueCopy = Object.assign({}, original);
trueCopy.name = "Bob";
console.log(original.name);  // "Alice" (original unchanged)
```

## 1️⃣5️⃣ Best Practices

### ✅ Best Practice 1: Use const for arrays and objects
```javascript
// ✅ Good
const person = { name: "John" };
person.age = 25;  // OK to modify contents

const fruits = ["apple"];
fruits.push("banana");  // OK to modify contents

// ❌ Avoid
let person = { name: "John" };
var fruits = ["apple"];
```

### ✅ Best Practice 2: Use meaningful property names
```javascript
// ❌ Bad
const obj = {
  x: 25,
  y: "j@email.com",
  z: true
};

// ✅ Good
const person = {
  age: 25,
  email: "j@email.com",
  isActive: true
};
```

### ✅ Best Practice 3: Keep related data together in objects
```javascript
// ❌ Scattered variables
const firstName = "John";
const lastName = "Doe";
const userAge = 25;
const userEmail = "john@example.com";

// ✅ Grouped in object
const user = {
  firstName: "John",
  lastName: "Doe",
  age: 25,
  email: "john@example.com"
};
```

### ✅ Best Practice 4: Use dot notation when possible
```javascript
// ✅ Preferred
console.log(person.name);

// ✅ Use brackets only when necessary
console.log(person["first-name"]);  // key with hyphen
```

### ✅ Best Practice 5: Check if property exists before using
```javascript
const person = { name: "John" };

// ✅ Check first
if (person.email) {
  console.log(person.email);
} else {
  console.log("No email provided");
}

// ✅ Or use optional chaining
console.log(person?.email ?? "No email");
```

## 1️⃣6️⃣ Mini Challenges

### Challenge 1: Array Operations
```javascript
const numbers = [1, 2, 3, 4, 5];

// 1. Add 6 to the end
// 2. Remove 1 from the beginning
// 3. Check if 3 exists
// 4. Find index of 4
// 5. Print the length

// Expected console output:
// true
// 3
// 4
```

<details>
<summary>Solution</summary>

```javascript
const numbers = [1, 2, 3, 4, 5];

numbers.push(6);           // [1, 2, 3, 4, 5, 6]
numbers.shift();           // [2, 3, 4, 5, 6]
console.log(numbers.includes(3));    // true
console.log(numbers.indexOf(4));     // 2 (new index after shift)
console.log(numbers.length);         // 5
```
</details>

### Challenge 2: Object Creation
Create an object representing a book with properties:
- title: "The Great Gatsby"
- author: "F. Scott Fitzgerald"
- pages: 180
- year: 1925
- genre: "Fiction"

Then access and print:
- Book title by author
- Total pages
- Publication year

<details>
<summary>Solution</summary>

```javascript
const book = {
  title: "The Great Gatsby",
  author: "F. Scott Fitzgerald",
  pages: 180,
  year: 1925,
  genre: "Fiction"
};

console.log(`${book.title} by ${book.author}`);
console.log(`Pages: ${book.pages}`);
console.log(`Year: ${book.year}`);
```
</details>

### Challenge 3: Array of Objects
Create an array of 3 students with their names, ages, and grades:

```javascript
const students = [
  // Add students here
];

// Print each student's name and grade
// Expected output:
// John: A
// Alice: B
// Bob: A+
```

<details>
<summary>Solution</summary>

```javascript
const students = [
  { name: "John", age: 20, grade: "A" },
  { name: "Alice", age: 21, grade: "B" },
  { name: "Bob", age: 19, grade: "A+" }
];

for (let i = 0; i < students.length; i++) {
  console.log(`${students[i].name}: ${students[i].grade}`);
}
```
</details>

## 1️⃣7️⃣ Mini Project: Contact Manager

Create a contact management system:

```javascript
// Array of contacts (objects)
const contacts = [
  {
    id: 1,
    name: "John Doe",
    email: "john@example.com",
    phone: "555-1234",
    tags: ["friend", "work"]
  },
  {
    id: 2,
    name: "Alice Smith",
    email: "alice@example.com",
    phone: "555-5678",
    tags: ["family"]
  }
];

// Function to add contact
const addContact = (name, email, phone, tags = []) => {
  const newContact = {
    id: contacts.length + 1,
    name: name,
    email: email,
    phone: phone,
    tags: tags
  };
  contacts.push(newContact);
  return newContact;
};

// Function to find contact by name
const findContact = (name) => {
  for (let i = 0; i < contacts.length; i++) {
    if (contacts[i].name === name) {
      return contacts[i];
    }
  }
  return null;
};

// Function to display all contacts
const displayContacts = () => {
  for (let i = 0; i < contacts.length; i++) {
    console.log(`${contacts[i].name}: ${contacts[i].email}`);
  }
};

// Usage
console.log("All contacts:");
displayContacts();

console.log("\nAdding new contact...");
addContact("Bob Johnson", "bob@example.com", "555-9012", ["work"]);

console.log("\nAll contacts:");
displayContacts();

console.log("\nFinding contact...");
const found = findContact("Alice Smith");
console.log(found);
// { id: 2, name: "Alice Smith", email: "alice@example.com", phone: "555-5678", tags: ["family"] }
```

## 1️⃣8️⃣ Interview Questions

### Q1: What's the difference between arrays and objects?

**Answer:**
- **Arrays**: Ordered collections, accessed by numeric index, best for lists
- **Objects**: Unordered collections, accessed by key names, best for structured data

```javascript
const array = [1, 2, 3];        // Use index: array[0]
const object = { a: 1, b: 2 };  // Use key: object.a
```

### Q2: Are arrays a type of object?

**Answer:**
Yes! In JavaScript, arrays are special objects. They have numeric keys and extra array methods.

```javascript
const arr = [1, 2, 3];
console.log(typeof arr);  // "object"
console.log(Array.isArray(arr));  // true
```

### Q3: How do you copy an array or object?

**Answer:**
```javascript
// Shallow copy
const original = { name: "John", age: 25 };
const copy = Object.assign({}, original);
// or
const copy = { ...original };

// For arrays
const originalArr = [1, 2, 3];
const copyArr = [...originalArr];
```

### Q4: What happens if you access an index that doesn't exist?

**Answer:**
```javascript
const arr = [1, 2, 3];
console.log(arr[10]);  // undefined (no error, just undefined)
```

### Q5: Can arrays contain different data types?

**Answer:**
Yes! JavaScript arrays are flexible:

```javascript
const mixed = [
  1,                      // number
  "hello",                // string
  true,                   // boolean
  { name: "John" },       // object
  ["a", "b"],             // array
  null,                   // null
  undefined               // undefined
];
```

## 🎓 Summary

| Concept | Usage |
|---------|-------|
| **Array** | Ordered list, accessed by index (0, 1, 2...) |
| **Object** | Unordered collection, accessed by keys |
| **push()** | Add to end of array |
| **pop()** | Remove from end of array |
| **length** | Number of elements in array |
| **Dot notation** | Access object properties with period |
| **Bracket notation** | Access with square brackets |

---

## 📚 Next Topic

Ready to learn about **Array Methods**? Go to `04_Array_Methods.md`

## 💡 Quick Reference

```javascript
// Arrays
const arr = [1, 2, 3];
arr.push(4);               // [1, 2, 3, 4]
arr.pop();                 // [1, 2, 3]
arr[0];                    // 1
arr.length;                // 3

// Objects
const obj = { name: "John", age: 25 };
obj.name;                  // "John"
obj["age"];                // 25
obj.email = "j@mail.com";  // Add property
delete obj.email;          // Remove property
```
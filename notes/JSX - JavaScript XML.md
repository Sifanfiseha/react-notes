# 📝 JSX - JavaScript XML

## What is JSX?

JSX stands for **JavaScript XML**. It is a syntax extension for JavaScript that allows you to write HTML-like code inside JavaScript. JSX makes it easier to create React elements and components.

### Why Use JSX?

- It makes your code more readable and expressive.
- It allows you to write HTML and JavaScript together in the same file.
- JSX is compiled into regular JavaScript by tools like Babel.

---

## JSX Syntax and Rules

### 1. Basic Syntax

JSX allows you to write HTML-like code inside JavaScript. For example:

```jsx
const element = <h1>Hello, world!</h1>;
```

This JSX code is transformed into:

```javascript
const element = React.createElement('h1', null, 'Hello, world!');
```

---

### 2. Embedding Expressions

You can embed JavaScript expressions inside JSX using curly braces `{}`.

```jsx
const name = "John";
const element = <h1>Hello, {name}!</h1>;
```

---

### 3. Attributes in JSX

JSX attributes are similar to HTML attributes but use camelCase for naming. For example:

```jsx
const element = <img src="image.jpg" alt="Description" />;
```

---

### 4. Nesting Elements

You can nest elements inside other elements.

```jsx
const element = (
  <div>
    <h1>Hello, world!</h1>
    <p>This is a paragraph.</p>
  </div>
);
```

---

### 5. Return a Single Root Element

JSX must return a single root element. If you need to return multiple elements, wrap them in a parent tag like `<div>` or a React fragment (`<>`).

**Correct:**

```jsx
function App() {
  return (
    <>
      <h1>Hello</h1>
      <p>Welcome to React!</p>
    </>
  );
}
```

**Incorrect:**

```jsx
function App() {
  return (
    <h1>Hello</h1>
    <p>Welcome to React!</p>
  );
}
```

**Difference:** The correct example wraps all elements in a single parent (`<>`), while the incorrect example does not.

---

### 6. Close All Tags

In JSX, all tags must be explicitly closed, even self-closing ones.

**Correct:**

```jsx
function App() {
  return (
    <>
      <img src="logo.png" alt="Logo" />
      <br />
    </>
  );
}
```

**Incorrect:**

```jsx
function App() {
  return (
    <>
      <img src="logo.png" alt="Logo">
      <br>
    </>
  );
}
```

**Difference:** The correct example explicitly closes all tags (`<img />`, `<br />`), while the incorrect example leaves them unclosed.

---

### 7. Use camelCase for Attributes

JSX attributes must use camelCase. For example, `class` becomes `className`, and `onclick` becomes `onClick`.

**Correct:**

```jsx
function App() {
  return <button className="btn" onClick={() => alert("Clicked!")}>Click Me</button>;
}
```

**Incorrect:**

```jsx
function App() {
  return <button class="btn" onclick="alert('Clicked!')">Click Me</button>;
}
```

**Difference:** The correct example uses camelCase attributes (`className`, `onClick`), while the incorrect example uses invalid HTML-style attributes (`class`, `onclick`).

---

## JSX in Functions

JSX can be returned from functions to create React components.

```jsx
function Greeting() {
  return <h1>Hello, world!</h1>;
}
```

---

## JSX and JavaScript

You can use JavaScript logic inside JSX by embedding expressions or calling functions.

```jsx
function formatName(user) {
  return `${user.firstName} ${user.lastName}`;
}

const user = { firstName: "John", lastName: "Doe" };
const element = <h1>Hello, {formatName(user)}!</h1>;
```

---

## Summary

- **What is JSX?**: JSX is a syntax extension for JavaScript that allows you to write HTML-like code inside JavaScript. It simplifies creating React elements and components.
- **Why Use JSX?**: JSX makes code more readable, combines logic and markup, and provides better error messages.
- **JSX Syntax and Rules**:
  1. Embed JavaScript expressions using `{}`.
  2. Use camelCase for attributes (e.g., `className`, `onClick`).
  3. Close all tags, including self-closing ones.
  4. Always return a single root element.
- **JSX in Functions**: JSX can be returned from functions to create React components.
- **JSX and JavaScript**: You can embed JavaScript logic and expressions directly into JSX.

---

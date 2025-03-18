## Introduction

Styled Components is a popular library for writing CSS in JavaScript within React applications. It enables scoped styles, dynamic styling, and component-based styling using tagged template literals.

## Installation

To use Styled Components, install the package:

```sh
npm install styled-components
```

Or using Yarn:

```sh
yarn add styled-components
```

## Creating Styled Components

Styled Components allow defining styles directly in JavaScript.

### Example: Creating a Button Component

```jsx
import styled from 'styled-components';

const Button = styled.button`
  background-color: blue;
  color: white;
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  &:hover {
    background-color: darkblue;
  }
`;

function App() {
  return <Button>Click Me</Button>;
}

export default App;
```

## Benefits of Styled Components

- **Scoped Styles:** Avoids global CSS conflicts.
- **Dynamic Styling:** Allows passing props to modify styles.
- **No External Stylesheets:** Styles live within the component.
- **Better Theming Support:** Easily integrates with theme providers.

## Dynamic Styling with Props

You can modify styles dynamically using props.

```jsx
const Button = styled.button`
  background-color: ${(props) => (props.primary ? 'blue' : 'gray')};
  color: white;
`;

function App() {
  return <Button primary>Primary Button</Button>;
}
```

## Theming with Styled Components

Styled Components support a **ThemeProvider** to manage themes globally.

1. **Define a Theme:**

```jsx
import { ThemeProvider } from 'styled-components';

const theme = {
  primaryColor: 'blue',
  secondaryColor: 'gray',
};
```

2. **Use Theme in Components:**

```jsx
const Button = styled.button`
  background-color: ${(props) => props.theme.primaryColor};
  color: white;
`;
```

3. **Wrap the App in ThemeProvider:**

```jsx
function App() {
  return (
    <ThemeProvider theme={theme}>
      <Button>Click Me</Button>
    </ThemeProvider>
  );
}
```

## Global Styles with Styled Components

Use `createGlobalStyle` to define global styles.

```jsx
import { createGlobalStyle } from 'styled-components';

const GlobalStyle = createGlobalStyle`
  body {
    margin: 0;
    font-family: Arial, sans-serif;
  }
`;

function App() {
  return (
    <>
      <GlobalStyle />
      <Button>Click Me</Button>
    </>
  );
}
```

## Summary

- **Styled Components** allow writing CSS inside JavaScript using template literals.
- They support **scoped styles**, **dynamic props**, **theming**, and **global styles**.
- Works well with modern React applications.

Styled Components provide a powerful alternative to traditional CSS or CSS Modules by keeping styles component-specific and enhancing maintainability.
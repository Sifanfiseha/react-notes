# 🔄 useEffect - Managing Side Effects in React

## What is `useEffect`?

The `useEffect` hook is a React hook that lets you run **side effects** in functional components. Side effects are actions that happen outside of rendering the UI, such as fetching data, setting up subscriptions, or updating the DOM.

---

## Why Use `useEffect`?

- To perform actions after rendering (e.g., fetching data or updating the UI).
- To clean up resources (e.g., removing event listeners or stopping timers).
- To synchronize state with external systems (e.g., APIs or WebSocket connections).

---

## How Does `useEffect` Work?

### Syntax

```jsx
useEffect(() => {
  // Side effect logic here

  return () => {
    // Cleanup logic here (optional)
  };
}, [dependencies]);
```

---

## Examples

### 1. Fetching Data

```jsx
import React, { useState, useEffect } from "react";

function FetchData() {
  const [data, setData] = useState(null); // State to store fetched data

  useEffect(() => {
    // Fetch data from the API when the component mounts
    fetch("https://api.example.com/data")
      .then((res) => res.json())
      .then((result) => setData(result)); // Update state with fetched data
  }, []); // Empty dependency array ensures this runs only once

  return <div>{data ? data.message : "Loading..."}</div>; // Display data or loading message
}
```

---

### 2. Timer with Cleanup

```jsx
import React, { useState, useEffect } from "react";

function Timer() {
  const [count, setCount] = useState(0); // State to store the timer count

  useEffect(() => {
    // Start a timer that increments the count every second
    const interval = setInterval(() => setCount((c) => c + 1), 1000);

    // Cleanup function to stop the timer when the component unmounts
    return () => clearInterval(interval);
  }, []); // Empty dependency array ensures this runs only once

  return <h1>{count}</h1>; // Display the timer count
}
```

---

### 3. Online/Offline Status

```jsx
import React, { useState, useEffect } from "react";

function OnlineStatus() {
  const [isOnline, setIsOnline] = useState(navigator.onLine); // State to track online status

  useEffect(() => {
    // Function to update the online status
    const updateStatus = () => setIsOnline(navigator.onLine);

    // Add event listeners for online and offline events
    window.addEventListener("online", updateStatus);
    window.addEventListener("offline", updateStatus);

    // Cleanup function to remove event listeners when the component unmounts
    return () => {
      window.removeEventListener("online", updateStatus);
      window.removeEventListener("offline", updateStatus);
    };
  }, []); // Empty dependency array ensures this runs only once

  return <h1>{isOnline ? "Online" : "Offline"}</h1>; // Display online/offline status
}
```

---

## Summary

- **What is `useEffect`?**: A hook to manage side effects in React components.
- **Why Use It?**: Simplifies lifecycle management and ensures clean, efficient code.
- **Key Features**:
  - **Effect Function**: Runs the side effect logic.
  - **Cleanup Function**: Frees up resources when the component is removed.
  - **Dependency Array**: Controls when the effect runs.
- **Best Practices**:
  1. Avoid excessive API calls by debouncing or throttling.
  2. Always clean up side effects to prevent memory leaks.

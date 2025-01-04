# Incorrect Object Comparison in React's useEffect Hook

This repository demonstrates a common error in React's `useEffect` hook: incorrectly comparing objects, leading to unintended infinite loops or unexpected behavior.  The `useEffect` hook, when used improperly, can trigger unexpected re-renders.

## Problem
The provided `MyComponent` function uses `useState` to manage a count.  The `useEffect` hook attempts to log a message whenever the count changes.  However, the comparison `prevCount !== count`  is flawed because it compares objects using strict equality. When state updates in a way that causes the object to be different, even with the same value, the comparison will always be true resulting in an infinite loop and potentially crashing the application. 

## Solution
The solution involves using a more appropriate object comparison method or avoiding object comparisons within the useEffect dependency array completely. In cases where direct object comparison is necessary, consider using JSON.stringify to compare the string representation of objects.  However, this approach can be computationally expensive for large objects.  Often, using a library like Lodash's `isEqual` or crafting a custom comparison function is more efficient and readable.  Another better solution would be refactoring the useEffect's dependencies to only depend on the count value instead of the entire state object.

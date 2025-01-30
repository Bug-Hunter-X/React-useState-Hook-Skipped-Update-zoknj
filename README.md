# React useState Hook Skipped Update

This repository demonstrates a subtle bug in React's `useState` hook where an update is skipped due to multiple calls to `setCount` within a single render cycle.

## Bug Description:

The `MyComponent` component utilizes the `useState` hook to manage a counter.  The `handleClick` function attempts to increment the counter by two by calling `setCount` twice. However, due to React's batching of state updates, only the final update (count + 2) is applied. The intermediate state (count + 1) is skipped.

## Solution:

To prevent this issue, use functional updates provided by `useState` to ensure updates are based on the previous state:

```javascript
setCount(prevCount => prevCount + 1);
```
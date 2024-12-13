# React Memory Leak: Unclosed setInterval in useEffect

This repository demonstrates a common React bug: a memory leak caused by the improper use of `setInterval` within a `useEffect` hook.  The example showcases the incorrect implementation and provides a corrected version.

## Bug Description
The `MyComponent` component uses `setInterval` to update a counter every second.  However, the cleanup function returned by `setInterval` (which should stop the interval) is missing, leading to multiple intervals running concurrently and causing a memory leak.

## Solution
The solution involves using the returned cleanup function from `setInterval` within the `useEffect` hook to properly clear the interval when the component unmounts or when dependencies change. This prevents additional intervals from running, thus fixing the memory leak.
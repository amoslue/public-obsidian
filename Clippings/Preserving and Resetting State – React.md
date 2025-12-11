---
title: "Preserving and Resetting State – React"
source: "https://react.dev/learn/preserving-and-resetting-state"
tags:
  - "clippings"
---
Every time you click the button, the input state disappears! This is because a *different* `MyTextField` function is created for every render of `MyComponent`. You’re rendering a *different* component in the same position, so React resets all state below. This leads to bugs and performance problems. To avoid this problem, **always declare component functions at the top level, and don’t nest their definitions.**
---
title: "Queueing a Series of State Updates – React"
source: "https://react.dev/learn/queueing-a-series-of-state-updates"
tags:
  - "clippings"
---
Here, `n => n + 1` is called an **updater function.** When you pass it to a state setter:

React queues this function to be processed after all the other code in the event handler has run.

During the next render, React goes through the queue and gives you the final updated state.

setNumber(n \=> n + 1);  

setNumber(n \=> n + 1);  

setNumber(n \=> n + 1);

  

  

Here’s how React works through these lines of code while executing the event handler:

`setNumber(n => n + 1)`: `n => n + 1` is a function. React adds it to a queue.

`setNumber(n => n + 1)`: `n => n + 1` is a function. React adds it to a queue.

`setNumber(n => n + 1)`: `n => n + 1` is a function. React adds it to a queue.

When you call `useState` during the next render, React goes through the queue. The previous `number` state was `0`, so that’s what React passes to the first updater function as the `n` argument. Then React takes the return value of your previous updater function and passes it to the next updater as `n`, and so on:

queued update`n`returns`n => n + 1``0``0 + 1 = 1``n => n + 1``1``1 + 1 = 2``n => n + 1``2``2 + 1 = 3`

React stores `3` as the final result and returns it from `useState`.

This is why clicking “+3” in the above example correctly increments the value by 3.
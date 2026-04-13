---
title: "Python's asyncio: A Hands-On Walkthrough"
source: https://realpython.com/async-io-python/#a-first-look-at-async-io
tags:
  - clippings
  - "#asyncio"
  - "#corotine"
---
## Questions I had
What does await do?
==await== pauses the current coroutine and gives control back to the event loop.**  i.e. NOT TO DO SOMETHING UNTILL XXX TASK IS DONE

==ayncio.create_task== will schedule the task in event loop. and when the code hit await xxx, it gives back control to event loop to pick up a ready task to run.

==asyncio.to_thread== can make something non-sync to be awaitable

==asyncio.gather== If you pass **coroutines** to `asyncio.gather`, it will **automatically wrap them into tasks and schedule them** on the event loop.

==asyncio.run()== creates a new event loop, runs the given coroutine until completion, and then closes the loop.
==asyncio.TaskGroup()== it fails or succeeds together. and ==asyncio.gather(task, return_exceptions=true)== will continues even some of the tasks fails.

```python
async with asyncio.TaskGroup() as tg:
	task = [
	tg.asyncio.create_task(asyncio.to_thread(xxx))
```

	

then how does event loop decide which task to continue when there are multiple tasks ready?
Answer is: 
By default
- ❌ No priority scheduling
- ❌ No shortest-job-first
- ❌ No fairness guarantees
It’s:  
👉 **“Whoever is ready, in queue order”**


## Original page

Async I/O may seem counterintuitive and paradoxical at first. How does something that facilitates concurrent code use a single thread in a single CPU core? Miguel Grinberg’s [PyCon](https://realpython.com/pycon-guide/) talk explains everything quite beautifully:

> Chess master Judit Polgár hosts a chess exhibition in which she plays multiple amateur players. She has two ways of conducting the exhibition: *synchronously* and *asynchronously*.
> 
> Assumptions:
> 
> - 24 opponents
> - Judit makes each chess move in 5 seconds
> - Opponents each take 55 seconds to make a move
> - Games average 30 pair-moves (60 moves total)
> 
> **Synchronous version**: Judit plays one game at a time, never two at the same time, until the game is complete. Each game takes *(55 + 5) \* 30 == 1800* seconds, or 30 minutes. The entire exhibition takes *24 \* 30 == 720* minutes, or **12 hours**.
> 
> **Asynchronous version**: Judit moves from table to table, making one move at each table. She leaves the table and lets the opponent make their next move during the wait time. One move on all 24 games takes Judit *24 \* 5 == 120* seconds, or 2 minutes. The entire exhibition is now cut down to *120 \* 30 == 3600* seconds, or just **1 hour**. ([Source](https://youtu.be/iG6fr81xHKA?t=4m29s))


At the heart of async I/O is the concept of a [**coroutine**](https://realpython.com/ref/glossary/coroutine/), which is an object that can suspend its execution and resume it later. In the meantime, it can pass the control to an event loop, which can execute another coroutine. Coroutine objects result from calling a [**coroutine function**](https://realpython.com/ref/glossary/coroutine-function/), also known as an **asynchronous function**. You define one with the `async def` construct.

``` python
import asyncio

async def count():
    print("One")
    await asyncio.sleep(1)
    print("Two")
    await asyncio.sleep(1)

async def main():
    await asyncio.gather(count(), count(), count())

if __name__ == "__main__":
    import time

    start = time.perf_counter()
    asyncio.run(main())
    elapsed = time.perf_counter() - start
    print(f"{__file__} executed in {elapsed:0.2f} seconds.")
```
The `main()` function is another coroutine function that uses [`asyncio.gather()`](https://realpython.com/async-io-python/#other-asyncio-tools) to run three instances of `count()` concurrently. You use the `asyncio.run()` function to launch the [event loop](https://realpython.com/async-io-python/#the-async-io-event-loop) and execute `main()`.
# What the event loop actually does

It repeatedly performs this cycle:

while tasks exist:  
    pick a task that is ready  
    run it until it hits "await"  
    suspend it  
    run another ready task

This switching is called **cooperative multitasking**.

Tasks **voluntarily give up control** when they `await`.
           ┌──────────────┐
Task A ───►│              │
Task B ───►│  Event Loop  │──► CPU
Task C ───►│              │
           └──────────────┘

``` python
async def g():
    result = await f()  # Pause and come back to g() when f() returns
    return result
```
 To call a coroutine function, you must either `await` it to get its result or run it directly in an event loop.
 
``` python
async def f(x):
    y = await z(x)  # Okay - `await` and `return` allowed in coroutines
    return y

async def g(x):
    yield x  # Okay - this is an async generator

async def m(x):
    yield from gen(x)  # No - SyntaxError

def n(x):
    y = await z(x)  # No - SyntaxError (no `async def` here)
    return y
```

 The recommended way to start an event loop in modern Python is to use [`asyncio.run()`](https://docs.python.org/3/library/asyncio-runner.html#asyncio.run). This function is responsible for getting the event loop, running tasks until they complete, and closing the loop. You can’t call this function when another async event loop is running in the same code.
- **Coroutines don’t do much on their own until they’re tied to the event loop.**
- By default, an async event loop runs in a single thread and on a single CPU core. In most `asyncio` applications, there will be only one event loop, typically in the main thread. Running multiple event loops in different threads is technically possible, but not commonly needed or recommended.
- Event loops are pluggable. You can write your own implementation and have it run tasks just like the event loops provided in `asyncio`.

## Common Async I/O Programming Patterns
### chain
import asyncio
import random
import time

async def main():
    user_ids = [1, 2, 3]
    start = time.perf_counter()
    await asyncio.gather(
        *(get_user_with_posts(user_id) for user_id in user_ids)
    )
    end = time.perf_counter()
    print(f"\n==> Total time: {end - start:.2f} seconds")

async def get_user_with_posts(user_id):
    user = await fetch_user(user_id)
    await fetch_posts(user)

async def fetch_user(user_id):
    delay = random.uniform(0.5, 2.0)
    print(f"User coro: fetching user by {user_id=}...")
    await asyncio.sleep(delay)
    user = {"id": user_id, "name": f"User{user_id}"}
    print(f"User coro: fetched user with {user_id=} (done in {delay:.1f}s).")
    return user

async def fetch_posts(user):
    delay = random.uniform(0.5, 2.0)
    print(f"Post coro: retrieving posts for {user['name']}...")
    await asyncio.sleep(delay)
    posts = [f"Post {i} by {user['name']}" for i in range(1, 3)]
    print(
        f"Post coro: got {len(posts)} posts by {user['name']}"
        f" (done in {delay:.1f}s):"
    )
    for post in posts:
        print(f" - {post}")

if __name__ == "__main__":
    random.seed(444)
    asyncio.run(main())
### Queue-based
import asyncio
import random
import time

async def main():
    queue = asyncio.Queue()
    user_ids = [1, 2, 3]

    start = time.perf_counter()
    await asyncio.gather(
        producer(queue, user_ids),
        *(consumer(queue) for _ in user_ids),
    )
    end = time.perf_counter()
    print(f"\n==> Total time: {end - start:.2f} seconds")

async def producer(queue, user_ids):
    async def fetch_user(user_id):
        delay = random.uniform(0.5, 2.0)
        print(f"Producer: fetching user by {user_id=}...")
        await asyncio.sleep(delay)
        user = {"id": user_id, "name": f"User{user_id}"}
        print(f"Producer: fetched user with {user_id=} (done in {delay:.1f}s)")
        await queue.put(user)

    await asyncio.gather(*(fetch_user(uid) for uid in user_ids))
    for _ in range(len(user_ids)):
        await queue.put(None)  # Sentinels for consumers to terminate

async def consumer(queue):
    while True:
        user = await queue.get()
        if user is None:
            break
        delay = random.uniform(0.5, 2.0)
        print(f"Consumer: retrieving posts for {user['name']}...")
        await asyncio.sleep(delay)
        posts = [f"Post {i} by {user['name']}" for i in range(1, 3)]
        print(
            f"Consumer: got {len(posts)} posts by {user['name']}"
            f" (done in {delay:.1f}s):"
        )
        for post in posts:
            print(f"  - {post}")

if __name__ == "__main__":
    random.seed(444)
    asyncio.run(main())


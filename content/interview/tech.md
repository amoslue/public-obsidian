1. **Class and Object**: The core of OOP is the division of tasks into objects (which are instances of classes) and classes (which define objects). A class serves as a blueprint for creating objects.
    
2. **Encapsulation**: This is about bundling the data (attributes) and the methods that operate on the data into a single unit or class. It also involves restricting direct access to some of an object’s components, which is a means of preventing accidental interference and misuse of the methods and data.
    
3. **Inheritance**: This is a mechanism wherein a new class is derived from an existing class. The new class, known as a subclass, inherits attributes and methods of the existing class, known as a superclass. This allows for reusing existing code and improving software modularity.
    
4. **Polymorphism**: It refers to the ability of a variable, function, or object to take on multiple forms. The most common use of polymorphism in OOP occurs when a parent class is used to refer to a child class object. Any Java object that can pass more than one IS-A test is considered to be polymorphic.
    
5. **Abstraction**: This concept involves hiding complex implementation details and showing only the necessary features of the object. In other words, it deals with the outside view of an object (interface).

what is generic?
- "generic" refers to a feature that allows classes, interfaces, methods, or functions to be written with placeholders for types. These placeholders can then be specified and replaced with actual types when the generic is used. Generics are primarily used to create data structures or algorithms that can operate on multiple types of data, improving code reusability, type safety, and readability.
#oop

When to use Influx DB and Prometheus? #systemDesign
- **Choose InfluxDB if**:
    
    - You need a general-purpose time-series database.
    - You have high write loads and need efficient querying for time-series data.
    - You need to manage retention policies and downsampling of historical data.
    - You require a SQL-like query language for interacting with time-series data.
- **Choose Prometheus if**:
    
    - Your primary goal is monitoring and alerting.
    - You prefer a pull-based model for collecting metrics.
    - You need a flexible and powerful query language for time-series data (PromQL).
    - You want built-in support for alerting and integrating with alert management systems.
    - You are looking for a standalone, self-contained monitoring solution.

## What is the difference between concurrency and parallelism?
#### **Concurrency**

- **Definition**: Concurrency is about **managing multiple tasks at the same time**, but not necessarily executing them simultaneously. It focuses on structuring a program to handle multiple tasks in overlapping time periods.
    
- **How it works**: Concurrency is achieved by **interleaving tasks**—switching between them quickly to give the illusion of simultaneous execution. This can be done using techniques like **threading**, **asynchronous programming**, or **event loops**.
    
- **Goal**: Improve responsiveness and efficiency, especially in **I/O-bound tasks** (e.g., waiting for network responses, file I/O, or user input).
    
- **Example**: A web server handling multiple client requests concurrently. While one request is waiting for a database query, the server can process another request.
    

---

#### **Parallelism**

- **Definition**: Parallelism is about **executing multiple tasks simultaneously**, typically by leveraging multiple CPU cores or processors.
    
- **How it works**: Parallelism requires hardware support (e.g., multi-core CPUs or distributed systems). Tasks are divided into subtasks that run in parallel on different cores or machines.
    
- **Goal**: Improve performance and speed, especially in **CPU-bound tasks** (e.g., mathematical computations, image processing, or data analysis).
    
- **Example**: Rendering a video by splitting the frames across multiple CPU cores or GPUs.
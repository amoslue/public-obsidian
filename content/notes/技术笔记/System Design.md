Steps of system design:

non-functional requirement: 
	- latency
	- reliability
	- consistency

QPS:
	- Total user * 10% = Daily Active User (DAU)
	- Concurrent user = DAU * 10%
	- Calculate update time T
	- QPS = Concurrent user / T

![[Pasted image 20240529185708.png]] 

### Q: which to use as application layer? RESTful API or WebSocket?

**WebSocket**:
- **Use**: Used to establish **long-lived connections** for **full-duplex** communication. It is ideal for **real-time** data transmission and **low-latency** applications, such as instant messaging, real-time gaming, stock tickers, etc.
- **Characteristics**: Once a connection is established, both the client and server can send data to each other at any time without reopening the connection.

**RESTful API**:
- **Use**: Used to implement a **client-server** communication model based on request/response. It is suitable for **resource-oriented** operations, such as fetching, creating, updating, and deleting data (CRUD operations).
- **Characteristics**: Each client request is sent via the HTTP protocol, and after the server responds, the connection is closed. The requests are stateless, meaning each request is independent and does not rely on previous interactions.
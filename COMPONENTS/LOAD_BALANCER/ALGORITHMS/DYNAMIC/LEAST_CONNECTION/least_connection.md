# 🔄 Least Connection Load Balancing Algorithm

## 📘 Overview

**Least Connection** is a dynamic load balancing algorithm that forwards incoming client requests to the server with the fewest number of active connections. It ensures better load distribution, especially in systems where requests are long-lived or resource-intensive.

## ⚙️ How It Works

1. **Connection Tracking**  
   The load balancer monitors and logs all incoming and outgoing connections to each backend server.

2. **Dynamic Decision Making**  
   Each new request is routed to the server with the **least number of current active connections**.

3. **Real-Time Updates**  
   The active connection count is updated:
   - ➕ When a new request is routed to a server.
   - ➖ When the request is completed or the client disconnects.

4. **Tie-Breaking**  
   If multiple servers have the same number of active connections, the load balancer may use a round-robin or random strategy to break the tie.

## 🔧 How it Works (Step-by-step)

Let's say we have 4 backend servers: S1, S2, S3, S4

1. **Monitor Active Connections:**
   The load balancer keeps track of how many active (live) connections each server is currently handling.

2. **Incoming Request:**
   A new request comes in.

3. **Choose Server:**
   The load balancer chooses the server with the least number of active connections.
   
   Example:
   ```
   Active Connections:
   S1: 5
   S2: 2
   S3: 3
   S4: 2
   
   New request → goes to S2 (or S4, if tie-breaking rule is round-robin/random).
   ```

4. **Update State:**
   The chosen server's active connection count increases by one.

5. **When a request completes:**
   Once the client disconnects, the server's active connection count decreases by one.

## 📈 Real-World Example

Imagine a video conferencing app with backend servers handling user streams.
Some users may stay in a session for 2 minutes, others for 2 hours.

➡️ Using Round Robin, one server might end up with several long sessions.
❌ This can cause unbalanced load and server crashes.

➡️ Using Least Connection, each new user is more likely to go to a less-loaded server, balancing the system in real-time.
✅ Better performance, fewer timeouts.

## 🧠 How Does the Load Balancer Track Connections?

1. **Load Balancer Acts as a Gatekeeper**
   - Every request first hits the load balancer before reaching any server
   - It can see which server each connection is sent to
   - It tracks when connections are opened and closed

2. **Maintains an In-Memory Connection Table**
   ```json
   {
     "Server 1": 3,
     "Server 2": 5,
     "Server 3": 2
   }
   ```
   This is updated dynamically as connections open and close.

## ⏱️ When to Use Least Connection Load Balancing

- Ideal for applications where some requests take longer to process than others (e.g., video streaming or large file uploads)
- Useful when some connections stay active longer
- Great for systems with fluctuating traffic, as it balances based on real-time server load

## 📊 Benefits and Drawbacks

### Benefits
- **Balanced Load:** Distributes traffic to servers with the fewest active connections, preventing overloading
- **Dynamic:** Adapts to changing server workloads in real-time

### Limitations
- **Tracking Overhead:** Needs real-time monitoring of connection counts
- **Not Ideal for Stateless Systems:** If every request is short and stateless, round-robin might be simpler
- **Slow-Closing Connections:** Some connections staying open unnecessarily can skew the load count

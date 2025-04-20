# 🧠 Distributed Caching with Consistent Hashing

## 1. Distributed Cache

A **distributed cache** is a fast, temporary storage system spread across multiple nodes (servers) in a network.  
Instead of storing all cached data on a single server, the data is **divided and distributed** across several servers, also known as **nodes**.

---

## 2. Problem with Single Cache

Relying on a single cache server creates serious issues:

- ❌ **Overload risk:** One server can’t handle all requests at scale.
- ❌ **Single point of failure:** If the server crashes, the entire system suffers.

**Solution:** Spread the cache across multiple nodes to share the load and increase resilience.

---

## 3. Consistent Hashing

### 🔍 Why it's needed:
When data is spread across many nodes, we need a way to **decide which node stores which data**.  
This is where **consistent hashing** comes in.

### 🧮 What is Hashing?
Hashing is a method to convert data into a unique identifier (like a number).

### ✅ What is Consistent Hashing?
Consistent hashing ensures that when **nodes are added or removed**, only a small subset of the data needs to be reallocated.  
This keeps the system stable and efficient.

---

## 4. How It Works

Imagine you have **10 nodes** in your system.

- A **hash ring** (a circle of hash values) is created.
- Each node is assigned a **position** on this ring using a hash function.
- To store or retrieve data:
  - Hash the key (e.g., `"X"`)
  - Find the **closest node clockwise** on the ring
  - Store or fetch data from that node

🔄 This makes the system predictable and fault-tolerant.

---

## 5. Benefits of Using Consistent Hashing

- ⚡ **Efficient Routing:** Requests go directly to the responsible node (no broadcasting).
- 📈 **Scalability:** Easily add new nodes with minimal data movement.
- 🔁 **Resilience:** If a node fails, data can still be retrieved from the next available node in the ring.

---

> 🔐 Consistent hashing plays a key role in building reliable and scalable distributed systems, especially in large-scale caching and database solutions.

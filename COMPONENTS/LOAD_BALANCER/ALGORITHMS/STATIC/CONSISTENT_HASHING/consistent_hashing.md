# 📘 Consistent Hashing

## 🧠 What is Consistent Hashing?
Consistent Hashing is a powerful technique to distribute requests or data across servers in a dynamic system. It minimizes disruption when servers are added or removed, making it ideal for load balancers, distributed caches, and scalable systems.

---

## 🆚 Problem with Basic Hashing
- In traditional hashing, if the number of servers changes (e.g., from 5 to 4), most keys get remapped.
-  Example: If hash("User123") = 7, and we have 5 servers:
-   7 % 5 = 2 → Server 2 handles the request.

#### ❌ Problem: What if a Server is Removed?
Let’s say we remove 1 server → N changes from 5 to 4:

Now, 7 % 4 = 3 → The request goes to Server 3 instead.

But earlier it was going to Server 2.

So just by changing the number of servers, the mapping of almost every key changes.


### 🔑 Solution: Consistent Hashing
- Only a **small fraction of keys** get remapped when a server is added or removed.
- Achieves **minimal disruption**.

---

## 🔄 The Hash Ring Concept
### Imagine a Circle:
- A number line from `0` to a large value (e.g., `2^32 - 1`) in a circular layout (like a clock).

### 📌 How It Works:
1. **Hashing:**
   - Use a hash function (e.g., SHA-1 or MD5).
   - Hash the server IDs (e.g., `"ServerA" → 100`).
   - Hash the request keys (e.g., `"User123" → 200`).

2. **Placement on the Ring:**
   - Place each server and request at its corresponding hash value on the ring.

3. **Assignment Rule:**
   - Each request is assigned to the **next server clockwise** on the ring.
   - If no server is found clockwise (end of ring), wrap around to `0`.

---
![Consistent_hashing](https://media.geeksforgeeks.org/wp-content/uploads/20231214182509/Mapping-in-the-hashing-(1).jpg)
## 🧪 Example Setup
### Servers:
- Server A → 100
- Server B → 500
- Server C → 900

### Request:
- `"User123" → 200`
- It goes to the next server clockwise → **Server B (500)**

### Ranges:
- 0–100 → A      (0–99),
- 100–500 → B    (100–499),
- 500–900 → C    (500–899),
- 900–0 → A      (900–999), // considertotoal range 0-999

---

## 🔄 Server Changes
### ➕ Adding a Server
- Add Server D at 300
- Before: 100–500 → B
- After:
  - 100–300 → **D**
  - 300–500 → B
- ✅ Only requests in 100–300 remap

### ➖ Removing a Server
- Remove Server C (900)
- Before: 500–900 → C
- After: 500–100 → A
- ✅ Only requests in 500–900 remap

---

## ❗ Problem: Uneven Load Distribution
- Example ranges:
  - 100–500 → 400 units (B)
  - 500–900 → 400 units (C)
  - 900–100 → 200 units (A)
- Some servers get more traffic than others

---

## 💡 Solution: Virtual Nodes
### What Are They?
- Each server gets multiple "virtual" positions on the ring
- These virtual nodes are distributed using different hash values

### Example:
- Server A → 100, 250, 400
- Server B → 500, 650, 800
- Server C → 900, 1050, 1200

### Benefits:
- ✅ Even load distribution
- ✅ Better scalability
- ✅ Weighted load: stronger servers can get more virtual nodes

---

## ❓ Your Idea: Even Distribution Without Virtual Nodes
### Idea:
- Manually place servers at even points (e.g., 0, 333, 666)
- Distributes load evenly if keys are uniformly distributed

### Challenges:
- ❌ Not scalable (manual work)
- ❌ Not consistent hashing anymore
- ❌ Adding/removing servers remaps almost everything

### Verdict:
- ✅ Works for small static systems
- ❌ Not ideal for dynamic or large-scale setups

---

## ⚙️ Full Workflow in a Load Balancer
### Setup:
- Hash ring is prepared with or without virtual nodes

### Request Handling:
1. Hash request (e.g., URL → 200)
2. Find next server clockwise on the ring
3. Route request to that server

### Scaling:
- Add/remove server(s), update nearby ranges
- Cache locality is preserved → fewer misses

---

## 🚀 When to Use What?
### No Virtual Nodes:
- Small, fixed systems
- Simplicity is more important than perfect balance

### With Virtual Nodes:
- Large, dynamic systems
- Uniform load, high fault tolerance

### Manual Distribution (Even Without Virtual Nodes):
- Tiny, fixed system with few servers

---

## ✅ Summary
- Consistent Hashing is crucial for distributed systems
- It **minimizes disruption** when servers are added/removed
- Virtual nodes help in **balancing the load**
- Use cases: **CDNs, distributed caches, load balancers, databases**

---


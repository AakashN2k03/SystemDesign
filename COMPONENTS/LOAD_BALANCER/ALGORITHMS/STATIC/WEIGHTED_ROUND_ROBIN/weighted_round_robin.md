# ⚖️ Weighted Round Robin Load Balancing Algorithm

**Weighted Round Robin** is a static load balancing technique similar to standard Round Robin, but with one key difference: **each server is assigned a weight**. These weights influence how many requests a server will handle relative to others, enabling better resource utilization in environments with heterogeneous server capacities.

---

## 🔄 How It Works

- Servers with **higher weights receive more requests**
- Follows a **cyclic pattern**, like traditional Round Robin
- Request allocation is **proportional to server weight**
- If a server reaches its processing limit, it may **queue or reject** further requests based on its configuration

---

## 🍬 Simple Analogy

Imagine distributing candy to friends with different cravings. A friend who loves candy more gets more pieces. Similarly, Weighted Round Robin assigns **more tasks to powerful servers** that can handle more load.

---

## 🧮 Example Calculation

Assume we have three servers:

- **Server1 (weight 0.3)**
- **Server2 (weight 0.2)**
- **Server3 (weight 0.1)**

### Total Weight = 0.3 + 0.2 + 0.1 = 0.6

In one cycle of requests:
- **Server1** receives: `(0.3 / 0.6) = 50%`
- **Server2** receives: `(0.2 / 0.6) = 33.33%`
- **Server3** receives: `(0.1 / 0.6) = 16.67%`

---

## 🕐 When to Use Weighted Round Robin

- When servers have **different capacities or performance levels**
- In setups with **varied CPU, memory, or bandwidth**
- When aiming to **optimize usage of all available resources**
- To **prevent weaker servers from being overwhelmed**

---

## ✅ Benefits and ⚠️ Drawbacks

### ✅ Benefits
- **Capacity-Aware:** Assigns more load to powerful servers
- **Flexible:** Easily adjustable as server resources change
- **Efficient:** Ensures optimal use of available infrastructure

### ⚠️ Drawbacks
- **More Complex:** Implementation is more involved than basic Round Robin
- **Requires Maintenance:** Weights need regular updates to match current server performance

---

Weighted Round Robin is ideal for real-world deployments with a mix of strong and weak servers, helping achieve **balanced load distribution** and **efficient performance**.

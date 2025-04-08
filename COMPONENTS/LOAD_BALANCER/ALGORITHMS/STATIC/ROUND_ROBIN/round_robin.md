# 🔁 Round Robin Algorithm – Load Balancing Explained

**Round Robin** is one of the **simplest** and most commonly used algorithms for load balancing in system design.

- Distribute incoming requests **sequentially and cyclically** across the available servers — just like dealing cards in a circle.

---

## ✅ How It Works (Step-by-Step)

Assume we have **3 servers**:

-  Server A  
-  Server B  
-  Server C  

Incoming requests are handled like this:

- Request 1 → Server A  
- Request 2 → Server B  
- Request 3 → Server C  
- Request 4 → Server A (starts over again)  
- Request 5 → Server B  
- ... and so on.

> 🔁 It follows a circular sequence: A → B → C → A → B → C...

---

## ⚙️ Real-Life Analogy

Imagine you're with a group of friends and you want to share a bag of candies 🍬 equally.  
You give one candy to each friend in a circle and start over when you reach the last one.  
This is how Round Robin works — **ensuring everyone gets a fair share**.

---

## 🖥️ System Design Perspective

### 🎯 Components Involved

1. **Client** – A user/browser sending requests  
2. **Load Balancer** – Uses the Round Robin algorithm  
3. **Backend Servers** – Multiple app instances to handle the load  

![Round Robin Load Balancing](https://media.geeksforgeeks.org/wp-content/uploads/20240130183312/Round-Robin-(1).webp)

---

## 🧠 Advantages

✅ **Simple to implement**  
✅ **Fair distribution** (if all servers have equal capacity)  

---

## ⚠️ Disadvantages

❌ **Not efficient** if one server is slower or overloaded  
❌ **Unequal Capacities**: Treats all servers equally, regardless of power  
❌ **Predictability**: Can lead to performance issues in heterogeneous environments

---



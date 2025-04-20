# 🗄️ Application Server Cache

## 📘 What is Application Server Cache?

An **Application Server Cache** is a storage layer within an application server that temporarily holds frequently accessed data. This allows the data to be quickly retrieved without needing to go back to the main database each time.

This caching mechanism helps applications perform faster by:
- Reducing the load on the database.
- Speeding up response times for users.

---

## 💡 Real-World Example

When an app frequently needs certain data, like:
- User profiles
- Product lists

The **application server** can store this data in the cache. When users request it, the app can instantly provide the cached version instead of processing a full database query. This significantly improves performance by avoiding the overhead of database access.

---
![application_server_cache](https://media.geeksforgeeks.org/wp-content/uploads/20240212140144/Application-Server-Cache-(1).webp)
## ⚠️ Drawbacks of Application Server Cache

When you add multiple servers to handle a high volume of requests, a **load balancer** sends requests to different nodes (servers). However, each node only has its own cache and doesn’t know about the cached data on other nodes. 

This leads to the following issues:
- **Cache Misses** – Since each server has its own cache, the data may not be present on all nodes, leading to cache misses.
- **Frequent Data Fetching** – Cache misses mean that data has to be re-fetched from the database, slowing down response times.

---

## 🛠️ Solutions to Cache Inconsistency

To fix the above issues, there are two main options:

1. **Distributed Cache** – This approach uses a shared cache system accessible by all application servers, ensuring better cache utilization and consistency across nodes.
   
2. **Global Cache** – A centralized cache that serves as a single point for all application servers to access, ensuring synchronization and improved data consistency.

---


# Source IP Hash Load Balancing Algorithm

The Source IP Hash Load Balancing Algorithm is a load balancing technique used to distribute network traffic across multiple backend servers in a consistent and deterministic way. It works by hashing the client's source IP address to determine which backend server should handle the request.

## 🔧 How It Works (Step-by-Step)

1. **Extract Source IP**: When a client sends a request, the load balancer extracts the IP address of the client (source IP).
2. **Apply Hash Function**: A hash function (like CRC32, MD5, SHA-1, or a simple modulus-based function) is applied to the source IP address.
   - Example: `hash("192.168.1.5") = 4523`
3. **Map to Server**: The result of the hash is modulo-divided by the total number of backend servers:
   - `ServerIndex = hash(sourceIP) % NumberOfServers`
   - Example: `4523 % 5 = 3` → Choose Server 3
4. **Forward Request**: The load balancer forwards the request to the server determined by the index.

## Advantages

| Benefit | Explanation |
|---------|-------------|
| ✅ Session Persistence (Sticky Sessions) | Same client IP will always be routed to the same server. |
| ✅ Low Overhead | Simple to implement and computationally inexpensive. |
| ✅ No Need for External Session Storage | Since requests are always routed to the same server, session data can stay on that server. |

## Disadvantages

| Limitation | Explanation |
|------------|-------------|
| ❌ Uneven Load Distribution | Some IPs may be more active than others, causing server imbalance. |
| ❌ Scalability Issues | If the number of servers changes (e.g., one is added or removed), hash results shift, breaking persistence. |
| ❌ Not Effective for NAT Clients | If multiple users are behind a NAT (sharing same IP), they'll all be directed to the same server. |

## 📊 Use Case Example

Let's say we have 3 backend servers:
```
Servers: [Server A, Server B, Server C]
```

And clients with the following IPs:
```
192.168.1.1 → hash(192.168.1.1) % 3 = 0 → Server A
192.168.1.2 → hash(192.168.1.2) % 3 = 1 → Server B
192.168.1.3 → hash(192.168.1.3) % 3 = 2 → Server C
```

Every time the client with IP 192.168.1.2 makes a request, it will be routed to Server B consistently.

## Technical Deep Dive

### 🔐 Role of the Hash Function

The hash function is the core component of this algorithm. Its role is:
- To convert the source IP address (like 192.168.1.10) into a numeric value (a hash). This value helps decide which server to send the request to.
- Then, it uses: `server_index = hash(source_ip) % number_of_servers`

This ensures every IP address always maps to the same server (as long as the number of servers doesn't change).

### Understanding Load Imbalance

**📉 "Some IPs may be more active than others, causing server imbalance" – What it means?**

Imagine this: You have 5 clients (with 5 unique IPs) and 3 servers. But one of those clients is a very active user, sending thousands of requests per second, while others send only a few. Since that client's IP always hashes to the same server, that one server gets overloaded, while the others sit idle.

This is called traffic skew or load imbalance:

| Issue | Impact |
|-------|--------|
| 🧍 A few IPs are very active | That server becomes a bottleneck |
| 💤 Other servers are underused | Wastes resources |
| 💥 Server may crash | If overloaded by too much traffic |

### NAT Client Problem

**🌐 "Not Effective for NAT Clients" – What does it mean?**

NAT (Network Address Translation) is when multiple users share the same public IP address — like in:
- Schools
- Offices
- Internet cafes
- Mobile networks

**Problem**: If 100 users behind a NAT (like in an office) all access your system, they all appear to have the same source IP (e.g., 203.0.113.5). So when the hash function runs:

```
hash("203.0.113.5") % number_of_servers → Server 2
```

All 100 users get routed to Server 2! That one server gets overloaded — other servers remain underused.

# 🏗️ System Design Key Concepts

## 1. ⚡ **Performance**
* **Definition:** How fast the system responds and completes tasks. It's about **speed & efficiency**.
* **Why important:** Users leave if apps are slow.
* **Example:**
   * Google Search → returns billions of results in **<0.5 seconds**.
   * If it took 10 seconds, people would switch to Bing or Yahoo.

> 🎯 **Key Point:** Speed is everything - even 100ms delay can reduce conversion rates by 1%

---

## 2. 📈 **Scalability**
* **Definition:** The ability of a system to handle **increasing load** (more users, data, or requests).
* **Types:**
   * **🔺 Vertical Scaling (Scale-up):** Add more CPU/RAM to one server.
   * **🔄 Horizontal Scaling (Scale-out):** Add more servers and distribute load.
* **Example:**
   * WhatsApp → started with small servers, now supports **2B+ users** by scaling horizontally.
   * Netflix adds more servers across regions to handle traffic spikes.

> ⚠️ **Important:** Horizontal scaling is preferred for web applications - easier to scale and more cost-effective

---

## 3. 🕒 **Latency**
* **Definition:** The **time delay** between a user's action and the system's response.
* **Measured in:** milliseconds (ms).
* **Why important:** Directly affects user experience.
* **Example:**
   * Sending a WhatsApp message → should show "delivered" in **<1 second**.
   * High latency → takes 5 seconds, user gets frustrated.

> 📊 **Benchmark:** 
> - **Excellent:** <100ms
> - **Good:** 100-300ms  
> - **Poor:** >1000ms

---

## 4. 🚀 **Throughput**
* **Definition:** How many requests the system can **process per unit time** (usually requests/second).
* **Why important:** Ensures system can handle peak loads.
* **Example:**
   * Twitter handles **500,000+ tweets per minute** during big events.
   * Payment systems like Visa can handle **tens of thousands of transactions per second**.

> 💡 **Pro Tip:** Throughput and latency are often inversely related - optimize based on your use case

---

## 5. 🔄 **Consistency**
* **Definition:** Ensures users see the **same data everywhere**.
* **Models:**
   * **💪 Strong Consistency:** Data is updated everywhere instantly.
      * Example: Bank transactions – if ₹1000 is debited, balance updates everywhere at once.
   * **⏳ Eventual Consistency:** Data may take some time to sync, but will eventually be correct.
      * Example: Instagram likes – if you like a post, your friend may see it a few seconds later.

> 🔍 **Critical Decision:** Choose consistency model based on business requirements - financial systems need strong consistency, social media can use eventual consistency

---

## 6. ✅ **Availability**
* **Definition:** The system is **accessible and usable** when needed.
* **Measured in:** "Nines" (99.9%, 99.99% uptime).
* **Why important:** Downtime costs money & users.
* **Example:**
   * Gmail → targets **99.99% availability** (only ~50 minutes downtime per year).
   * If Gmail went down for hours, businesses worldwide would be stuck.

> 📈 **Availability Levels:**
> - **99%:** 3.65 days downtime/year
> - **99.9%:** 8.76 hours downtime/year  
> - **99.99%:** 52.56 minutes downtime/year
> - **99.999%:** 5.26 minutes downtime/year

---

## 🎯 **Quick Reference Table**

| Concept | Key Metric | Good Target | Critical For |
|---------|------------|-------------|--------------|
| Performance | Response Time | <100ms | User Experience |
| Scalability | Users/Load | Handle 10x growth | Business Growth |
| Latency | Delay Time | <300ms | Real-time Apps |
| Throughput | Requests/sec | Match peak load | High-traffic Systems |
| Consistency | Data Sync | Based on use case | Data Integrity |
| Availability | Uptime % | 99.9%+ | Business Continuity |

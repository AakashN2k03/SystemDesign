# 📘 Software Requirements Overview

## 🧠 What Are Software Requirements?

Software requirements define **what a system should do** and **how well it should do it**.

They are broadly categorized into:

- ✅ **Functional Requirements (FR)** – What the system does.
- 🚀 **Non-Functional Requirements (NFR)** – How the system performs under conditions.

---

## ✅ Functional Requirements (FR)

### 💡 Definition
Functional requirements describe the **specific behaviors or functions** of a system. These are the tasks or features the system must perform.

### 📦 Examples (Food Delivery App - e.g., Zomato)

| Feature              | Functional Requirement Example                                       |
|----------------------|----------------------------------------------------------------------|
| User Authentication  | Users must be able to sign up, log in, and log out.                 |
| Restaurant Search    | Users should be able to search restaurants by location/cuisine.     |
| Order Placement      | Users should be able to place, modify, and cancel orders.           |
| Payment Integration  | Support payment via UPI, card, or wallet.                           |
| Notification System  | Send SMS or in-app alerts when order is confirmed/delivered.        |

### 🧠 In Simple Words:
> “**Functional = What the system should do for the user.**”

---

## 🚀 Non-Functional Requirements (NFR)

### 💡 Definition
Non-functional requirements define **how well the system performs** its functions under various conditions.

### ⚙️ Categories of NFR

| NFR Type        | Description & Examples                                                                 |
|------------------|-----------------------------------------------------------------------------------------|
| Performance      | System must respond within 2 seconds to user queries.                                  |
| Scalability      | Should support up to 1 million concurrent users.                                       |
| Reliability      | 99.9% uptime required.                                                                 |
| Availability     | App should be available 24/7 with max 5 minutes downtime/month.                        |
| Security         | Data must be encrypted; only authenticated users can access the system.                |
| Maintainability  | Code should follow clean practices and be easy to update.                              |
| Usability        | Users should perform key actions with no more than 3 clicks.                           |
| Portability      | Should work on Android, iOS, and major web browsers.                                   |
| Compliance       | Must adhere to GDPR, HIPAA, or relevant legal guidelines.                              |

### 🧠 In Simple Words:
> “**Non-functional = How well the system works under pressure, scale, or constraints.**”

---

## 🔁 Quick Comparison Table

| Aspect              | Functional Requirement        | Non-Functional Requirement                |
|---------------------|-------------------------------|--------------------------------------------|
| Focus Area          | Features & functions          | Quality & performance                      |
| Type                | Mandatory behavior            | Optional but crucial for satisfaction      |
| Example             | User can reset password       | System responds to reset request in 2 sec  |
| Measured By         | Functionality (Pass/Fail)     | Metrics (Speed, Uptime, Load)              |
| Concerned With      | What the system should do     | How the system should do it                |

---

## 🛠️ Real-World Analogy

> Think of a car:

- 🚗 **Functional**: Start, stop, accelerate, turn left/right.
- 🏎️ **Non-functional**: Accelerates 0–100 km/h in 5s, fuel-efficient, safe, quiet.

---

## 🧩 Common Challenges in Defining Requirements

| Challenge                      | Description                                                                    |
|--------------------------------|--------------------------------------------------------------------------------|
| 🤷‍♂️ Vague or Incomplete        | Requirements like “fast app” are unclear.                                     |
| 🔁 Changing Requirements        | Business needs evolve frequently.                                             |
| 🤝 Miscommunication             | Different interpretations between clients, users, and devs.                   |
| 🎯 Conflicting Requirements     | Marketing demands more features; Engineering prefers performance.             |
| 📉 Lack of Stakeholder Input   | Excludes real user needs.                                                     |
| 📐 Measuring NFRs is Tough     | Usability, scalability, reliability are tricky to quantify.                   |
| ⌛ Time Constraints             | Teams rush into development without clarity.                                  |

---

## 🔍 How to Gather Functional and Non-Functional Requirements

### 🔹 Functional Requirements Gathering Techniques

| Technique                | Description                                                               |
|--------------------------|---------------------------------------------------------------------------|
| 📋 Stakeholder Interviews| Talk to product owners, users, and business leaders.                      |
| 🧠 Brainstorming         | Collaborate with PMs, devs, QA, and designers.                            |
| 📄 Use Cases/User Stories| “As a user, I want to…” format to define tasks.                           |
| 👀 Observation           | Watch users interact with existing systems.                              |
| 📊 Surveys/Questionnaires| Useful for collecting input from many users.                             |
| 🧪 Prototyping           | Build wireframes or mockups for feedback.                                 |

### 🔹 Non-Functional Requirements Gathering Techniques

| Technique                | Description                                                               |
|--------------------------|---------------------------------------------------------------------------|
| ✅ Performance Benchmarking | Check similar systems' performance metrics.                              |
| 💬 SLA Discussions       | Discuss uptime, latency, recovery with stakeholders.                     |
| 🧪 Load Testing          | Simulate traffic to test system stability.                                |
| 📚 Compliance Review     | Understand legal and security requirements.                              |
| 📈 Monitoring Needs      | Define what stakeholders want to track.                                   |

---



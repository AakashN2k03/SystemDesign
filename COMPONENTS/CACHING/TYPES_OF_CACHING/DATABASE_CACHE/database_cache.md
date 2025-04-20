🔍 What is Database Cache?
A Database Cache is a temporary storage layer that sits between your application and your database. It stores frequently accessed data in memory (RAM), so that when the same data is requested again, it can be delivered faster without querying the database every time.

💡 Why Use Database Cache?
Speed: Memory access is faster than disk/database access.

Reduce Load: Less pressure on the database server.

Cost-Efficient: Fewer database calls = reduced cloud/database usage cost.

Scalability: Helps handle more users without slowing down the app.

🔄 How It Works (Step-by-Step):
Example scenario:
Let’s say you have a website that shows a user profile by ID.

🔍 First time:

App asks database: “Give me data for user ID = 101”

DB returns data: {name: "Aakash", age: 22}

App stores this data in the cache for future use

🔁 Next time (same user):

App checks cache first → found the data

It skips the database and directly serves data from cache ➡️ faster response

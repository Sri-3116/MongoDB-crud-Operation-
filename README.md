# MongoDB Student Database Practice

## 📌 Project Overview

The objective of this project was to understand the fundamentals of **MongoDB** and practice database operations using **MongoDB Shell (mongosh)**.

In this project, I created a `studentDB` database and performed various operations on `students` and `books` collections. The practice includes database and collection creation, CRUD operations, query operators, update operations, and deletion of documents.

---

## 🎯 Objectives

* Understand MongoDB databases and collections.
* Create and manage collections using MongoDB Shell.
* Perform **CRUD operations**.
* Practice MongoDB **query operators**.
* Perform single and multiple document updates.
* Check whether a field exists using `$exists`.
* Work with multiple collections.
* Understand document deletion.

---

## 🛠️ Technologies Used

* **MongoDB**
* **MongoDB Shell (mongosh)**
* **MongoDB Compass** (optional)

---

# 📂 Database & Collection Setup

The database used in this project is:

```javascript
studentDB
```

Collections created:

```text
students
books
```

### Create / Switch Database

```javascript
use studentDB
```

### Create Students Collection

```javascript
db.createCollection("students")
```

### View Databases

```javascript
show dbs
```

### View Collections

```javascript
show collections
```

---

# ➕ Insert Operations

## Insert One Document

A single student document was inserted using `insertOne()`.

```javascript
db.students.insertOne({
    name: "Jayasri",
    age: 25,
    course: "MERN Stack",
    status: "Active"
})
```

## Insert Multiple Documents

Multiple student documents were inserted using `insertMany()`.

```javascript
db.students.insertMany([
    {
        name: "Arun",
        age: 23,
        course: "Java",
        status: "Active"
    },
    {
        name: "Priya",
        age: 24,
        course: "MERN Stack",
        status: "Completed"
    },
    {
        name: "Rahul",
        age: 22,
        course: "Python",
        status: "Active"
    },
    {
        name: "Divya",
        age: 26,
        course: "AEM",
        status: "Completed"
    }
])
```

---

# 🔍 Read Operations

## Fetch All Documents

```javascript
db.students.find()
```

## Find MERN Stack Students

```javascript
db.students.find({
    course: "MERN Stack"
})
```

This returns students whose course is **MERN Stack**.

---

# ✏️ Update Operations

## Update One Document

Jayasri's status was changed from `Active` to `Completed`.

```javascript
db.students.updateOne(
    { name: "Jayasri" },
    { $set: { status: "Completed" } }
)
```

## Update Multiple Documents

All students with `Active` status were changed to `Completed`.

```javascript
db.students.updateMany(
    { status: "Active" },
    { $set: { status: "Completed" } }
)
```

## Add an Email Field

An email field was added to Jayasri's document.

```javascript
db.students.updateOne(
    { name: "Jayasri" },
    { $set: { email: "jayasri@example.com" } }
)
```

---

# 🔎 MongoDB Query Operators

Query operators were used to filter documents based on specific conditions.

## `$gt` — Greater Than

Find students whose age is greater than 23.

```javascript
db.students.find({
    age: { $gt: 23 }
})
```

## `$lt` — Less Than

Find students whose age is less than 25.

```javascript
db.students.find({
    age: { $lt: 25 }
})
```

## `$in` — Match Multiple Values

Find students studying MERN Stack or AEM.

```javascript
db.students.find({
    course: { $in: ["MERN Stack", "AEM"] }
})
```

## `$and` — Match All Conditions

Find students who are older than 23 and have completed their course.

```javascript
db.students.find({
    $and: [
        { age: { $gt: 23 } },
        { status: "Completed" }
    ]
})
```

## `$or` — Match Any Condition

Find students studying Java or Python.

```javascript
db.students.find({
    $or: [
        { course: "Java" },
        { course: "Python" }
    ]
})
```

## `$exists` — Check Field Existence

Find students who have an email field.

```javascript
db.students.find({
    email: { $exists: true }
})
```

---

# 📚 Books Collection

A second collection called `books` was created to practice MongoDB operations with another type of data.

## Create Books Collection

```javascript
db.createCollection("books")
```

## Insert Multiple Books

```javascript
db.books.insertMany([
    {
        title: "The Alchemist",
        author: "Paulo Coelho",
        category: "Fiction",
        price: 350,
        available: true
    },
    {
        title: "Clean Code",
        author: "Robert C. Martin",
        category: "Programming",
        price: 600,
        available: true
    },
    {
        title: "JavaScript Guide",
        author: "David Flanagan",
        category: "Programming",
        price: 500,
        available: false
    }
])
```

## Find Programming Books

```javascript
db.books.find({
    category: "Programming"
})
```

## Update Book Availability

The availability of `Clean Code` was changed to `false`.

```javascript
db.books.updateOne(
    { title: "Clean Code" },
    { $set: { available: false } }
)
```

---

# 🗑️ Delete Operations

## Delete One Document

The student named Rahul was deleted.

```javascript
db.students.deleteOne({
    name: "Rahul"
})
```

## Delete All Documents

All documents from the `students` collection were deleted.

```javascript
db.students.deleteMany({})
```

After deletion:

```javascript
db.students.find()
```

The collection returned no student documents.

> **Note:** `deleteMany({})` deletes all documents in the selected collection. Use it carefully.

---

# 📖 MongoDB Operations Covered

| Operation                         | MongoDB Method       |
| --------------------------------- | -------------------- |
| Create database / switch database | `use`                |
| Create collection                 | `createCollection()` |
| View databases                    | `show dbs`           |
| View collections                  | `show collections`   |
| Insert one document               | `insertOne()`        |
| Insert multiple documents         | `insertMany()`       |
| Read documents                    | `find()`             |
| Update one document               | `updateOne()`        |
| Update multiple documents         | `updateMany()`       |
| Delete one document               | `deleteOne()`        |
| Delete multiple documents         | `deleteMany()`       |

### Query Operators Covered

| Operator  | Purpose                      |
| --------- | ---------------------------- |
| `$gt`     | Greater than                 |
| `$lt`     | Less than                    |
| `$in`     | Match any value from a list  |
| `$and`    | Match all conditions         |
| `$or`     | Match any condition          |
| `$exists` | Check whether a field exists |

---

# 💡 Key Learnings

Through this project, I learned how MongoDB stores data in a **document-oriented structure** and how databases are organized using collections and documents.

I practiced creating databases and collections, inserting documents, retrieving specific records, updating individual and multiple documents, filtering data using query operators, checking field existence, and deleting documents.

I also gained practical experience using **mongosh** to interact with MongoDB through the command line.

---

# 🚀 Conclusion

This project provided hands-on experience with the fundamental operations of MongoDB. It helped me understand how to manage collections and documents and how MongoDB query and update operators can be used to work with data efficiently.

The knowledge gained from this exercise provides a foundation for using MongoDB in **MERN Stack applications**, especially when working with **Node.js, Express.js, and Mongoose**.

---

## 👩‍💻 Author

**Jayasri**

GitHub: `Sri-3116`


# TP5 — Task Management System with GraphQL

![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)
![Express](https://img.shields.io/badge/Express.js-000000?style=for-the-badge&logo=express&logoColor=white)
![GraphQL](https://img.shields.io/badge/GraphQL-E10098?style=for-the-badge&logo=graphql&logoColor=white)
![Apollo](https://img.shields.io/badge/Apollo_Server-311C87?style=for-the-badge&logo=apollographql&logoColor=white)

> A RESTless Task Management API built with **GraphQL**, **Apollo Server**, and **Express.js** — supporting full CRUD operations via queries and mutations.

---

## 📌 Overview

This project is part of the **SOA & Microservices** course (A.U. 2025/2026).  
It demonstrates how to design and expose a GraphQL API for managing tasks, including creating, completing, updating, and deleting tasks — all through a strongly-typed schema.

---

## 🎯 Objectives

- Understand how to configure and use GraphQL with Node.js and Express
- Design a GraphQL schema with types, queries, and mutations
- Implement resolvers to handle business logic
- Interact with the API using Apollo Sandbox

---

## 🛠️ Tech Stack

| Technology       | Role                          |
|------------------|-------------------------------|
| Node.js          | JavaScript runtime            |
| Express.js       | HTTP server framework         |
| GraphQL          | Query language for the API    |
| Apollo Server    | GraphQL server implementation |
| @graphql-tools   | Schema + resolver binding     |

---

## 📁 Project Structure
tp-graphql/
│
├── index.js              # Entry point — Express + Apollo Server setup
├── taskSchema.gql        # GraphQL schema (types, queries, mutations)
├── taskSchema.js         # Schema loader using fs + buildSchema
├── taskResolver.js       # Resolvers for all queries and mutations
├── .gitignore            # Ignores node_modules
├── package.json          # Project metadata and dependencies
└── README.md             # Project documentation

---

## ⚙️ Installation & Setup

### 1. Clone the repository

```bash
git clone https://github.com/TonUsername/tp-graphql.git
cd tp-graphql
```

### 2. Install dependencies

```bash
npm install
```

### 3. Start the server

```bash
node index.js
```

### 4. Open Apollo Sandbox
http://localhost:5000/graphql

---

## 📐 GraphQL Schema

```graphql
type Task {
  id: ID!
  title: String!
  description: String!
  completed: Boolean!
  duration: Int
}

type Query {
  tasks: [Task]
  task(id: ID!): Task
}

type Mutation {
  addTask(title: String!, description: String!, completed: Boolean!, duration: Int): Task
  completeTask(id: ID!): Task
  changeDescription(id: ID!, description: String!): Task
  deleteTask(id: ID!): Task
}
```

---

## 🔍 Sample Queries & Mutations

### ▶ Get all tasks
```graphql
query {
  tasks {
    id
    title
    description
    completed
    duration
  }
}
```

### ▶ Get task by ID
```graphql
query {
  task(id: "1") {
    id
    title
    completed
  }
}
```

### ▶ Add a new task
```graphql
mutation {
  addTask(
    title: "New Task"
    description: "Task description here"
    completed: false
    duration: 5
  ) {
    id
    title
    duration
  }
}
```

### ▶ Mark task as completed
```graphql
mutation {
  completeTask(id: "1") {
    id
    title
    completed
  }
}
```

### ▶ Update task description
```graphql
mutation {
  changeDescription(id: "2", description: "Updated description") {
    id
    title
    description
  }
}
```

### ▶ Delete a task
```graphql
mutation {
  deleteTask(id: "3") {
    id
    title
  }
}
```

---

## 📦 Dependencies

```json
{
  "express": "^4.x",
  "@apollo/server": "^4.x",
  "@as-integrations/express5": "^1.x",
  "@graphql-tools/schema": "^10.x",
  "graphql": "^16.x"
}
```

---

## 👨‍💻 Author

| Field       | Info                          |
|-------------|-------------------------------|
| **Student** | Abdallah Omar                      |
| **Class**   | 4Info                         |
| **Course**  | SOA & Microservices           |
| **Teacher** | Dr. Salah Gontara             |
| **Year**    | 2026/2027                     |

---

## 📄 License

This project is for **educational purposes only** as part of university coursework.

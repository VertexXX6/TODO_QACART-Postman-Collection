# TODO_QACART Postman Collection

This repository contains a Postman collection (`TODO_QACART.postman_collection.json`) designed for testing the API endpoints of the TODO_QACART application. The collection includes requests for user authentication, task management, and database seeding, along with test scripts to validate responses.

## Table of Contents
- [Overview](#overview)
- [Prerequisites](#prerequisites)
- [Collection Structure](#collection-structure)
- [Setup Instructions](#setup-instructions)
- [Environment Variables](#environment-variables)
- [Requests](#requests)
  - [Login](#login)
  - [Register](#register)
  - [Add Todo](#add-todo)
  - [Mark Todo List as Completed](#mark-todo-list-as-completed)
  - [Delete Todo](#delete-todo)
  - [Seed](#seed)
- [Testing](#testing)
- [Contributing](#contributing)
- [License](#license)

## Overview
The `TODO_QACART` Postman collection provides a set of API requests to interact with the TODO_QACART application's RESTful API. It supports user authentication (login and registration), task management (create, update, and delete tasks), and a seeding endpoint for initializing the database. Each request includes test scripts to verify response status codes and data integrity.

## Prerequisites
To use this collection, ensure you have the following:
- [Postman](https://www.postman.com/downloads/) installed.
- Access to the TODO_QACART API at `https://todo.qacart.com`.
- Basic understanding of REST APIs and JSON.

## Collection Structure
The collection includes the following requests:
1. **Login**: Authenticate a user and retrieve an access token.
2. **Register**: Register a new user with randomized credentials.
3. **Add Todo**: Create a new todo item.
4. **Mark Todo List as Completed**: Update a todo item to mark it as completed.
5. **Delete Todo**: Delete a specific todo item.
6. **Seed**: Seed the database with initial data.

Each request is configured with pre-request scripts, test scripts, and appropriate HTTP methods (POST, PUT, DELETE, GET).

## Setup Instructions
1. **Import the Collection**:
   - Open Postman.
   - Click **Import** in the top left corner.
   - Select the `TODO_QACART.postman_collection.json` file or paste the collection link:
     ```
     https://rawan-4828560.postman.co/workspace/Rawan's-Workspace~34de6cf4-79fd-4929-871b-6f9c1338f207/collection/45850699-8b28a935-a87d-4be5-be0a-bd4cf21d6303?action=share&source=collection_link&creator=45850699
     ```

2. **Set Up Environment Variables**:
   - Create a new Postman environment (e.g., `TODO_QACART_Env`).
   - Configure the following variables (some are set dynamically by the collection):
     - `BaseURL`: `https://todo.qacart.com` (set automatically if not defined).
     - `email`: Randomized email (set by pre-request script in Register).
     - `password`: Randomized password (set by pre-request script in Register).
     - `firstName`: Randomized first name (set by pre-request script in Register).
     - `lastName`: Randomized last name (set by pre-request script in Register).
     - `access_token`: Set after successful Login or Register.
     - `id`: Todo item ID (set after Add Todo).
     - `item`: Todo item description (set after Add Todo).
     - `userID`: User ID (set after Add Todo).
     - `createdAt`: Creation timestamp (set after Add Todo).
     - `isCompleted`: Completion status (set after Add Todo).
     - `__v`: Version key (set after Add Todo).

3. **Run the Collection**:
   - Execute requests in sequence, starting with **Login** or **Register** to obtain an `access_token`.
   - Use the `access_token` for authenticated requests (Add Todo, Mark Todo List as Completed, Delete Todo, Seed).

## Environment Variables
The collection uses the following environment variables, some of which are set dynamically:

| Variable       | Description                              | Example Value                     |
|----------------|------------------------------------------|-----------------------------------|
| `BaseURL`      | Base URL for the API                    | `https://todo.qacart.com`         |
| `email`        | User email for registration/login       | `user{{random}}@example.com`      |
| `password`     | User password                           | Randomized password               |
| `firstName`    | User's first name                       | Randomized first name            |
| `lastName`     | User's last name                        | Randomized last name             |
| `access_token` | JWT token for authentication            | Set after Login/Register          |
| `id`           | Todo item ID                            | Set after Add Todo                |
| `item`         | Todo item description                   | `new hello new personallity`      |
| `userID`       | User ID associated with the todo        | Set after Add Todo                |
| `createdAt`    | Todo creation timestamp                 | Set after Add Todo                |
| `isCompleted`  | Todo completion status                  | `false` or `true`                 |
| `__v`          | Version key for the todo item           | `0`                               |

## 📌 Example Request: Add Todo
```http
POST {{BaseURL}}/api/v1/tasks
Authorization: Bearer {{access_token}}
Content-Type: application/json

{
  "item": "new hello new personality",
  "isCompleted": false
}

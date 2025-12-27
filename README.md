# API Documentation for Evangadi Forum

This documentation provides the details for the Evangadi Forum API endpoints, including authentication, questions, and answers.

---

## 🔐 Authentication Middleware

### Check User
Checks the current authenticated user's information.

* **Endpoint:** `/api/user/checkUser`
* **Method:** `GET`
* **Request Headers:** * `Authorization: Bearer <token>`
* **Success Response:**
    * **Code:** `200 OK`
    * **Content:**
        ```json
        {
          "message": "Valid user",
          "username": "Kebede",
          "userid": "123"
        }
        ```
* **Error Response:**
    * **Code:** `401 Unauthorized`
    * **Content:** `{ "error": "Unauthorized", "message": "Authentication invalid" }`

---

## 👤 User Endpoints

### Sign-up
Registers a new user.

* **Endpoint:** `/api/user/register`
* **Method:** `POST`
* **Request Body:**
    ```json
    {
      "username": "string",
      "first_name": "string",
      "last_name": "string",
      "email": "string",
      "password": "string"
    }
    ```
* **Success Response:** `201 Created`
                  ```json
                 {
                   "message": "User registered successfully"
                 }

                  ```
* **Error Responses:** * `400 Bad Request`: : Missing or invalid fields.
                ```json
              {
                 "error": "Bad Request",
                 "message": "Please provide all required fields"
              }
                ```
    * `409 Conflict`: User already exists.

### Login
Authenticates a user and returns a JWT token.

* **Endpoint:** `/api/user/login`
* **Method:** `POST`
* **Request Body:**
    ```json
    {
      "email": "string",
      "password": "string"
    }
    ```
* **Success Response:** `200 OK`
    ```json
    {
      "message": "User login successful",
      "token": "jwt_token"
    }
    ```

---

## ❓ Questions Endpoints

### Get All Questions
Fetches all questions.

* **Endpoint:** `/api/question`
* **Method:** `GET`
* **Success Response:** `200 OK`
    ```json
    {
      "questions": [
        {
          "question_id": 1,
          "title": "First Question",
          "content": "This is the first question.",
          "user_name": "Sisay",
          "created_at": "2023-06-30T12:00:00Z"
        }
      ]
    }
    ```

### Get Single Question
Retrieves details of a specific question.

* **Endpoint:** `/api/question/:question_id`
* **Method:** `GET`
* **URL Parameters:** `question_id` (integer)
* **Success Response:** `200 OK`

---

## 💬 Answers Endpoints

### Post Answer
Submits an answer for a specific question.

* **Endpoint:** `/api/answer`
* **Method:** `POST`
* **Request Body:**
    ```json
    {
      "questionid": 1,
      "answer": "string"
    }
    ```
* **Success Response:** `201 Created`

### Get Answers for a Question
Retrieves answers for a specific question.

* **Endpoint:** `/api/answer/:question_id`
* **Method:** `GET`
* **URL Parameters:** `question_id` (integer)
* **Success Response:** `200 OK`
    ```json
    {
      "answers": [
        {
          "answer_id": 1,
          "content": "This is an answer.",
          "user_name": "Abebe",
          "created_at": "2023-06-30T12:00:00Z"
        }
      ]
    }
    ```

---

## 🛠 Common Error Codes

| Status Code | Description |
| :--- | :--- |
| `400` | Bad Request (Missing or invalid fields) |
| `401` | Unauthorized (Invalid credentials) |
| `404` | Not Found (Resource does not exist) |
| `409` | Conflict (User already exists) |
| `500` | Internal Server Error (Unexpected error) |

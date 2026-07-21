# POST Method

## 1. What is POST?

`POST` is the HTTP method used to create new resources on a server.

Unlike GET, a POST request modifies the server by adding new information.

Examples:

```http
POST /users
POST /posts
POST /comments
```

---

## 2. Structure of a POST request

Example:

```http
POST https://jsonplaceholder.typicode.com/posts
```

A POST request usually contains:

- Base URL
- Endpoint
- Headers
- Request Body

---

## 3. Base URL

The Base URL is the common address of the API.

Example:

```text
https://jsonplaceholder.typicode.com
```

---

## 4. Endpoint

The endpoint identifies the resource where the new data will be created.

Example:

```http
POST /posts
```

---

## 5. Request Body

Unlike GET requests, POST requests usually send information to the server.

Example:

```json
{
  "title": "My first post",
  "body": "Learning API Testing",
  "userId": 1
}
```

---

## 6. Headers

POST requests commonly include headers.

Example:

```http
Content-Type: application/json
```

This header tells the server that the request body is JSON.

---

## 7. Typical Response

A successful POST request usually returns:

```http
201 Created
```

Example:

```json
{
  "id": 101,
  "title": "My first post",
  "body": "Learning API Testing",
  "userId": 1
}
```

---

## 8. Common Status Codes

### 201 Created

The resource was created successfully.

### 400 Bad Request

Invalid request.

### 401 Unauthorized

Authentication required.

### 403 Forbidden

Permission denied.

### 404 Not Found

Endpoint not found.

### 500 Internal Server Error

Unexpected server error.

---

## 9. What should a QA validate?

Possible validations include:

- Correct status code
- Resource created successfully
- Response body matches the request
- Mandatory fields are present
- Data types are correct
- Correct error messages
- Invalid data handling
- Missing required fields
- Duplicate data
- Response time
- Response headers

---

## 10. Positive Test Examples

### Create a valid resource

```http
POST /posts
```

Expected:

- `201 Created`
- New resource returned
- New ID generated

---

## 11. Negative Test Examples

### Empty Body

Expected:

- Validation error

---

### Missing required field

Expected:

- Validation error

---

### Invalid data type

Expected:

- Validation error

---

### Invalid endpoint

```http
POST /postss
```

Expected:

- `404 Not Found`

---

## 12. Practical Examples

(To be completed during the course.)

---

## 13. Key Concepts Learned

(To be completed after practicing POST.)
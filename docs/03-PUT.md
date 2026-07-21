# PUT Method

## 1. What is PUT?

`PUT` is the HTTP method used to completely update an existing resource on a server.

Unlike POST, PUT is generally used when the resource already exists.

Examples:

```http
PUT /users/1
PUT /posts/10
PUT /products/5
```

---

## 2. Structure of a PUT request

Example:

```http
PUT https://jsonplaceholder.typicode.com/posts/1
```

A PUT request usually contains:

- Base URL
- Endpoint
- Path Parameter
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

The endpoint identifies the resource to update.

Example:

```http
PUT /posts/1
```

The value `1` identifies the resource that will be replaced.

---

## 5. Path Parameter

PUT requests usually require a Path Parameter.

Example:

```http
PUT /posts/1
```

General format:

```http
PUT /resource/{id}
```

Meaning:

> Replace the resource whose ID is 1.

---

## 6. Request Body

PUT normally sends the complete resource.

Example:

```json
{
  "id": 1,
  "title": "Updated title",
  "body": "Updated content",
  "userId": 1
}
```

The server replaces the existing resource with the new one.

---

## 7. Headers

Most APIs require:

```http
Content-Type: application/json
```

This tells the server that the body is JSON.

---

## 8. Typical Response

A successful PUT request commonly returns:

```http
200 OK
```

Example:

```json
{
  "id": 1,
  "title": "Updated title",
  "body": "Updated content",
  "userId": 1
}
```

Some APIs may return:

```http
204 No Content
```

when no response body is needed.

---

## 9. PUT vs POST

| POST | PUT |
|------|-----|
| Creates a new resource | Replaces an existing resource |
| Usually no ID in URL | Usually includes an ID |
| Common response: 201 Created | Common response: 200 OK |

---

## 10. Common Status Codes

### 200 OK

Resource updated successfully.

### 204 No Content

Updated successfully without returning a body.

### 400 Bad Request

Invalid request.

### 401 Unauthorized

Authentication required.

### 403 Forbidden

Permission denied.

### 404 Not Found

The resource does not exist.

### 500 Internal Server Error

Unexpected server error.

---

## 11. What should a QA validate?

Possible validations include:

- Correct status code
- Correct resource updated
- Response body is correct
- Data types remain valid
- All fields updated correctly
- No unexpected fields changed
- Invalid IDs
- Invalid data
- Missing fields
- Response time
- Response headers

---

## 12. Positive Test Examples

### Update an existing resource

```http
PUT /posts/1
```

Expected:

- `200 OK`
- Resource updated
- Response body reflects the new values

---

## 13. Negative Test Examples

### Resource does not exist

```http
PUT /posts/999
```

Expected:

- Depends on the API
- Commonly `404 Not Found`

---

### Missing required fields

Expected:

- Validation error

---

### Invalid data type

Expected:

- Validation error

---

### Invalid endpoint

```http
PUT /postss/1
```

Expected:

- `404 Not Found`

---

## 14. Practical Examples

(To be completed during the course.)

---

## 15. Key Concepts Learned

(To be completed after practicing PUT.)
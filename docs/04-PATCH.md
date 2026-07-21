# PATCH Method

## 1. What is PATCH?

`PATCH` is the HTTP method used to partially update an existing resource on a server.

Unlike PUT, PATCH only modifies the fields included in the request body.

Examples:

```http
PATCH /users/1
PATCH /posts/10
PATCH /products/5
```

---

## 2. Structure of a PATCH request

Example:

```http
PATCH https://jsonplaceholder.typicode.com/posts/1
```

A PATCH request usually contains:

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
PATCH /posts/1
```

The value `1` identifies the resource that will be modified.

---

## 5. Path Parameter

PATCH requests usually require a Path Parameter.

Example:

```http
PATCH /posts/1
```

General format:

```http
PATCH /resource/{id}
```

Meaning:

> Partially update the resource whose ID is 1.

---

## 6. Request Body

PATCH only sends the fields that need to be updated.

Example:

```json
{
  "title": "Updated title"
}
```

Only the `title` field is modified.

The remaining fields keep their original values.

---

## 7. Headers

Most APIs require:

```http
Content-Type: application/json
```

This tells the server that the request body is JSON.

---

## 8. Typical Response

A successful PATCH request commonly returns:

```http
200 OK
```

Example:

```json
{
  "id": 1,
  "title": "Updated title",
  "body": "Original body",
  "userId": 1
}
```

Some APIs may return:

```http
204 No Content
```

when no response body is needed.

---

## 9. PATCH vs PUT

| PUT | PATCH |
|------|--------|
| Replaces the entire resource | Updates only selected fields |
| Usually sends the complete object | Sends only modified fields |
| Missing fields may be replaced | Missing fields remain unchanged |

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
- Only the expected fields changed
- Unmodified fields remain unchanged
- Correct response body
- Correct data types
- Invalid IDs
- Invalid request body
- Missing required fields
- Response time
- Response headers

---

## 12. Positive Test Examples

### Update one field

```http
PATCH /posts/1
```

Body:

```json
{
  "title": "New title"
}
```

Expected:

- `200 OK`
- Only the `title` field changes.

---

### Update multiple fields

```http
PATCH /posts/1
```

Body:

```json
{
  "title": "New title",
  "body": "New content"
}
```

Expected:

- `200 OK`
- Only the specified fields are updated.

---

## 13. Negative Test Examples

### Resource does not exist

```http
PATCH /posts/999
```

Expected:

- Depends on the API.
- Commonly `404 Not Found`.

---

### Invalid data type

Expected:

- Validation error.

---

### Invalid endpoint

```http
PATCH /postss/1
```

Expected:

- `404 Not Found`

---

### Empty request body

```http
PATCH /posts/1
```

Body:

```json
{}
```

Expected:

- Depends on the API.
- The resource may remain unchanged or return a validation error.

---

## 14. Practical Examples

(To be completed during the course.)

---

## 15. Key Concepts Learned

(To be completed after practicing PATCH.)
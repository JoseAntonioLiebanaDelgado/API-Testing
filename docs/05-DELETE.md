# DELETE Method

## 1. What is DELETE?

`DELETE` is the HTTP method used to remove an existing resource from a server.

Unlike GET, POST, PUT and PATCH, a DELETE request removes information instead of retrieving or modifying it.

Examples:

```http
DELETE /users/1
DELETE /posts/10
DELETE /products/5
```

---

## 2. Structure of a DELETE request

Example:

```http
DELETE https://jsonplaceholder.typicode.com/posts/1
```

A DELETE request usually contains:

- Base URL
- Endpoint
- Path Parameter
- Headers (if required)

Most DELETE requests do not require a Request Body.

---

## 3. Base URL

The Base URL is the common address of the API.

Example:

```text
https://jsonplaceholder.typicode.com
```

---

## 4. Endpoint

The endpoint identifies the resource to delete.

Example:

```http
DELETE /posts/1
```

The value `1` identifies the resource that will be removed.

---

## 5. Path Parameter

DELETE requests usually require a Path Parameter.

Example:

```http
DELETE /posts/1
```

General format:

```http
DELETE /resource/{id}
```

Meaning:

> Delete the resource whose ID is 1.

---

## 6. Request Body

Most DELETE requests do not require a request body.

Example:

```http
DELETE /posts/1
```

Some APIs may allow or require a body, but this is uncommon.

Always check the API documentation.

---

## 7. Headers

Some APIs require headers such as:

```http
Content-Type: application/json
```

or

```http
Authorization: Bearer <token>
```

Authentication is commonly required before deleting resources.

---

## 8. Typical Response

A successful DELETE request commonly returns:

```http
200 OK
```

or

```http
204 No Content
```

Example:

```json
{}
```

Some APIs return an empty body after a successful deletion.

---

## 9. Common Status Codes

### 200 OK

Resource deleted successfully.

### 202 Accepted

The deletion request has been accepted and will be processed asynchronously.

### 204 No Content

Resource deleted successfully without returning a response body.

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

## 10. What should a QA validate?

Possible validations include:

- Correct status code
- Correct resource deleted
- Resource is no longer available
- Correct response body
- Invalid IDs
- Attempt to delete an already deleted resource
- Authorization rules
- Response time
- Response headers

---

## 11. Positive Test Examples

### Delete an existing resource

```http
DELETE /posts/1
```

Expected:

- `200 OK` or `204 No Content`
- Resource deleted successfully.

---

### Verify deletion

Example:

```http
GET /posts/1
```

Expected:

- Depends on the API.
- Commonly `404 Not Found`.

---

## 12. Negative Test Examples

### Resource does not exist

```http
DELETE /posts/999
```

Expected:

- Commonly `404 Not Found`.

---

### Invalid endpoint

```http
DELETE /postss/1
```

Expected:

- `404 Not Found`

---

### Unauthorized deletion

Expected:

- `401 Unauthorized`

or

- `403 Forbidden`

depending on the API.

---

### Invalid ID

Example:

```http
DELETE /posts/abc
```

Expected:

- Depends on the API.
- Commonly `400 Bad Request`.

---

## 13. Practical Examples

(To be completed during the course.)

---

## 14. Key Concepts Learned

(To be completed after practicing DELETE.)
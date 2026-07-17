# GET Method

## 1. What is GET?

`GET` is an HTTP method used to retrieve information from a server.

A GET request should only read data. It should not create, modify or delete resources.

Examples:

```http
GET /users
GET /users/1
GET /posts
```

---

## 2. Structure of a GET request

Example:

```http
GET https://jsonplaceholder.typicode.com/users?username=Bret
```

This request contains:

```text
https://jsonplaceholder.typicode.com
```

Base URL: the common address of the API.

```text
/users
```

Endpoint: the resource being requested.

```text
?username=Bret
```

Query parameter: a filter applied to the request.

---

## 3. Base URL

The Base URL is the common part used by the endpoints of an API.

For JSONPlaceholder:

```text
https://jsonplaceholder.typicode.com
```

Different APIs have different Base URLs.

Examples:

```text
https://api.example.com
https://api.github.com
https://api.weather.com
```

---

## 4. Endpoint

An endpoint represents a resource or functionality exposed by an API.

Examples from JSONPlaceholder:

```http
/users
/posts
/comments
/albums
/photos
/todos
```

Examples:

```http
GET /users
```

Retrieves users.

```http
GET /posts
```

Retrieves posts.

---

## 5. Get a collection

Request:

```http
GET https://jsonplaceholder.typicode.com/users
```

Expected response:

- Status code: `200 OK`
- Response body: JSON array
- Contains all available users

Example:

```json
[
  {
    "id": 1,
    "name": "Leanne Graham"
  },
  {
    "id": 2,
    "name": "Ervin Howell"
  }
]
```

A JSON array begins and ends with:

```json
[]
```

An array represents a collection containing zero, one or multiple elements.

---

## 6. Get a specific resource

Request:

```http
GET https://jsonplaceholder.typicode.com/users/1
```

The value `1` identifies a specific user.

Expected response:

- Status code: `200 OK`
- Response body: JSON object
- Returned user has `id: 1`

Example:

```json
{
  "id": 1,
  "name": "Leanne Graham",
  "username": "Bret"
}
```

A JSON object begins and ends with:

```json
{}
```

---

## 7. Path parameters

A Path Parameter is part of the endpoint path and usually identifies a specific resource.

General format:

```http
GET /users/{id}
```

Example:

```http
GET /users/1
```

Here:

```text
users
```

is the resource.

```text
1
```

is the Path Parameter.

Meaning:

> Return the specific user whose ID is 1.

---

## 8. Query parameters

Query Parameters are used to search, filter or modify the results of a request.

They begin after the `?` symbol.

General format:

```http
GET /resource?key=value
```

Example:

```http
GET /users?username=Bret
```

Meaning:

> Search the users whose username equals Bret.

The Query Parameter contains:

```text
username
```

Parameter name.

```text
Bret
```

Parameter value.

---

## 9. Path Parameter vs Query Parameter

These two requests may appear similar, but they do not mean exactly the same thing.

### Specific resource

```http
GET /users/1
```

Meaning:

> Return the specific user with ID 1.

Typical response:

```json
{
  "id": 1
}
```

The response is normally one JSON object.

---

### Filtered collection

```http
GET /users?id=1
```

Meaning:

> Search the users whose ID equals 1.

Typical response:

```json
[
  {
    "id": 1
  }
]
```

The response is an array because the API is filtering a collection.

Even when only one result matches, the response can still be an array.

---

## 10. Search with no results

Request:

```http
GET /users?id=999
```

JSONPlaceholder returns:

```http
200 OK
```

Body:

```json
[]
```

This means:

- The request was valid.
- The search was executed correctly.
- No users matched the filter.

An empty search result is not necessarily an error.

---

## 11. Specific resource not found

Request:

```http
GET /users/999
```

JSONPlaceholder returns:

```http
404 Not Found
```

Body:

```json
{}
```

This means that the requested specific resource does not exist.

---

## 12. Important difference: 404 vs empty array

### Specific resource does not exist

```http
GET /users/999
```

Result:

```http
404 Not Found
```

The request asks for one concrete resource, but that resource does not exist.

---

### Search returns no matches

```http
GET /users?id=999
```

Result:

```http
200 OK
```

```json
[]
```

The search was valid, but it returned zero results.

Summary:

| Request | Meaning | Result when no match exists |
|---|---|---|
| `GET /users/999` | Return one specific user | `404 Not Found` |
| `GET /users?id=999` | Search users by ID | `200 OK` and `[]` |

This behaviour is used by JSONPlaceholder. Other APIs may define different behaviours, so the API documentation must always be checked.

---

## 13. Multiple query parameters

Multiple Query Parameters are separated using `&`.

Example:

```http
GET /users?id=1&username=Bret
```

Meaning:

> Search users whose ID is 1 and whose username is Bret.

Structure:

```text
?
```

Begins the Query Parameters.

```text
&
```

Separates one parameter from another.

General format:

```http
GET /resource?key1=value1&key2=value2
```

---

## 14. Query parameters in Postman

Postman allows Query Parameters to be added in two ways.

### Directly in the URL

```http
https://jsonplaceholder.typicode.com/users?username=Bret
```

### Using the Params table

| Key | Value |
|---|---|
| username | Bret |

Postman automatically synchronizes the URL and the Params table.

This is especially useful when a request contains multiple parameters.

---

## 15. JSON data types

API responses commonly contain several JSON data types.

### Integer

```json
"id": 1
```

### String

```json
"name": "Leanne Graham"
```

Text values are written between quotation marks.

### Object

```json
"address": {
  "city": "Gwenborough"
}
```

### Array

```json
"users": [
  {
    "id": 1
  }
]
```

### Boolean

```json
"active": true
```

### Null

```json
"phone": null
```

Important example:

```json
"lat": "-37.3159"
```

Although it looks like a number, it is a string because it is between quotation marks.

---

## 16. Main parts of an API response

After sending a request in Postman, the response normally contains:

### Status code

Example:

```http
200 OK
```

Indicates the result of the request.

### Response body

Contains the data returned by the server.

### Response time

Example:

```text
23 ms
```

Indicates how long the server took to respond.

### Response size

Example:

```text
2.93 KB
```

Indicates the size of the response.

### Response headers

Contain metadata about the response, such as the content type.

---

## 17. Common status codes used with GET

### 200 OK

The request was processed correctly.

Example:

```http
GET /users
```

### 400 Bad Request

The server cannot process the request because it is invalid.

### 401 Unauthorized

Authentication is required or invalid.

### 403 Forbidden

The client is authenticated but does not have permission.

### 404 Not Found

The requested endpoint or specific resource does not exist.

### 500 Internal Server Error

An unexpected error occurred on the server.

---

## 18. What should a QA validate in a GET request?

A QA should not only check that the request returns data.

Possible validations include:

- Correct status code
- Correct response structure
- Correct JSON data types
- Mandatory fields are present
- Values are correct
- IDs are unique
- Fields are not unexpectedly empty
- Correct behaviour when the resource does not exist
- Correct behaviour when a search has no results
- Correct response time
- Correct response headers
- No unexpected or sensitive data is returned

---

## 19. Positive test examples

### Get all users

```http
GET /users
```

Expected:

- `200 OK`
- JSON array
- Array contains users

### Get an existing user

```http
GET /users/1
```

Expected:

- `200 OK`
- JSON object
- `id` equals `1`

### Search by username

```http
GET /users?username=Bret
```

Expected:

- `200 OK`
- JSON array
- One matching user
- Returned username equals `Bret`

---

## 20. Negative and edge test examples

### Specific user does not exist

```http
GET /users/999
```

Expected in JSONPlaceholder:

- `404 Not Found`

### Search returns no results

```http
GET /users?username=NoExiste
```

Expected in JSONPlaceholder:

- `200 OK`
- Empty array `[]`

### Incorrect endpoint

```http
GET /user
```

Expected:

- Usually `404 Not Found`

### Invalid filter value

```http
GET /users?id=abc
```

The result depends on the API specification.

Possible outcomes include:

- `200 OK` with `[]`
- `400 Bad Request`
- Validation error response

---

## 21. Examples practiced

```http
GET https://jsonplaceholder.typicode.com/users
```

Retrieves all users.

```http
GET https://jsonplaceholder.typicode.com/users/1
```

Retrieves the specific user with ID 1.

```http
GET https://jsonplaceholder.typicode.com/users/999
```

Returns `404 Not Found` because the specific user does not exist.

```http
GET https://jsonplaceholder.typicode.com/users?username=Bret
```

Returns an array containing the matching user.

```http
GET https://jsonplaceholder.typicode.com/users?id=1
```

Returns an array containing the user with ID 1.

```http
GET https://jsonplaceholder.typicode.com/users?id=999
```

Returns `200 OK` with an empty array.

```http
GET https://jsonplaceholder.typicode.com/users?city=Gwenborough
```

Filters users using the city value supported by JSONPlaceholder.

---

## 22. Key concepts learned

- GET retrieves data.
- GET should not modify resources.
- The Base URL identifies the API.
- An endpoint identifies a resource.
- A Path Parameter usually identifies one specific resource.
- A Query Parameter filters or searches a collection.
- `?` begins the Query Parameters.
- `&` separates multiple Query Parameters.
- A collection is normally returned as a JSON array.
- A specific resource is normally returned as a JSON object.
- A valid search with no matches can return `200 OK` and `[]`.
- A specific resource that does not exist can return `404 Not Found`.
- The exact expected behaviour must always be checked against the API documentation.
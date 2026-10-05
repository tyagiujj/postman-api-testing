# Postman API Testing

A hands-on learning repository for **API testing with Postman**. I'm documenting my progress day by day: every collection, environment, and exercise I build while learning is committed here.

The practice APIs used are free public ones:

- [JSONPlaceholder](https://jsonplaceholder.typicode.com): a fake REST API for posts, comments, and users
- [Postman Echo](https://postman-echo.com): echoes back whatever you send, which is handy for inspecting headers, params, and bodies

---

## Repository Structure

```
postman-api-testing/
├── User Management API.postman_collection.json   # Main collection with all requests
├── Dev.postman_environment.json                  # Dev environment variables
├── QA.postman_environment.json                   # QA environment variables
└── README.md
```

---

## Getting Started

### Prerequisites

- [Postman](https://www.postman.com/downloads/) (desktop app or web)

### Import into Postman

1. Clone the repository:
   ```bash
   git clone <repo-url>
   ```
2. Open Postman and click **Import**.
3. Select `User Management API.postman_collection.json` and both environment files.
4. Choose the **Dev** or **QA** environment from the top-right dropdown.
5. Set the variable values (they are exported empty):

   | Variable  | Example value                          | Used in                      |
   |-----------|----------------------------------------|------------------------------|
   | `baseUrl` | `https://jsonplaceholder.typicode.com` | CRUD flow, Parameters        |
   | `userId`  | `1`                                    | Query parameter requests     |
   | `echoUrl` | `https://postman-echo.com`             | Echo practice (collection variable) |

6. Send any request.

---

## What's Covered So Far (Day 1 to 3)

### Day 1: Postman Basics and CRUD Operations

Folder: **CRUD flow**. It covers the five main HTTP methods against `/posts`:

| # | Request     | Method   | Endpoint             | Purpose                               |
|---|-------------|----------|----------------------|---------------------------------------|
| 1 | Create post | `POST`   | `{{baseUrl}}/posts`   | Create a new resource                 |
| 2 | Read post   | `GET`    | `{{baseUrl}}/posts/1` | Fetch a single resource               |
| 3 | Update post | `PUT`    | `{{baseUrl}}/posts/1` | Replace the whole resource            |
| 4 | Patch post  | `PATCH`  | `{{baseUrl}}/posts/1` | Update only some fields               |
| 5 | Delete post | `DELETE` | `{{baseUrl}}/posts/1` | Remove the resource                   |

**Key learnings:**
- The difference between `PUT` (full replace) and `PATCH` (partial update)
- Sending JSON request bodies with a `Content-Type: application/json` header
- Reading status codes such as `200 OK`, `201 Created`, and `404 Not Found`

### Day 2: Parameters, Headers, and Request Bodies

Folder: **Parameters**
- **Query parameters**: `/posts?userId={{userId}}`
- **Path variables**: `/posts/:id`
- **Nested resources**: `/posts/1/comments`

Folder: **Echo practice** (using Postman Echo)
- **URL encoding**: sending a value with spaces (`city=New Delhi`)
- **Custom headers**: sending `X-Student-Name` and checking that it comes back
- **Form data**: `multipart/form-data` with text fields and a file upload

### Day 3: Variables and Environments

- **Collection variables**: `baseUrl`, `userId`, `echoUrl`
- **Environments**: separate **Dev** and **QA** environments
- Swapping environments without editing any request
- Variable scope: global → collection → environment → data → local

### Homework

Folder: **HomeWork**
- Request for a non-existent resource (`/posts/9999`), which returns a `404`
- Filtering comments by `postId`
- Fetching all posts by a user (`/users/1/posts`)
- Posting a raw body to Postman Echo
- Combining several query parameters (`?userId=2&id=5`)

---

## Roadmap (Upcoming Topics)

- [x] Postman basics and HTTP methods (CRUD)
- [x] Query parameters, path variables, and headers
- [x] Request body types (raw JSON, form-data)
- [x] Variables and environments
- [ ] **Test scripts**: assertions with `pm.test()` and `pm.expect()` (status code, response time, body fields)
- [ ] **Pre-request scripts**: generating dynamic data and setting variables
- [ ] **Chaining requests**: saving a value from one response (such as an `id`) and using it in the next request
- [ ] **Dynamic variables**: `{{$randomEmail}}`, `{{$guid}}`, `{{$timestamp}}`
- [ ] **Authentication**: API Key, Basic Auth, Bearer Token, OAuth 2.0
- [ ] **JSON Schema validation** of responses
- [ ] **Collection Runner**: running the whole collection with iterations
- [ ] **Data-driven testing** with CSV and JSON data files
- [ ] **Negative and boundary testing**: invalid inputs, missing fields, error codes
- [ ] **Mock servers** and **API documentation** in Postman
- [ ] **Newman**: running collections from the command line
- [ ] **HTML reports** with `newman-reporter-htmlextra`
- [ ] **CI/CD integration**: running tests automatically with GitHub Actions
- [ ] **Final project**: an end-to-end API test suite for a complete application

---

## Running with Newman (Coming Soon)

Once test scripts are added, the collection can be run from the terminal:

```bash
npm install -g newman newman-reporter-htmlextra

newman run "User Management API.postman_collection.json" \
  -e Dev.postman_environment.json \
  -r cli,htmlextra
```

---

## Progress Log

| Day   | Topic                                   | Status       |
|-------|-----------------------------------------|--------------|
| Day 1 | Collections and CRUD requests           | ✅ Done       |
| Day 2 | Params, headers, and body types         | ✅ Done       |
| Day 3 | Variables and environments              | ✅ Done       |
| Day 4 | Test scripts and assertions             | ⏳ Upcoming   |
| Day 5 | Pre-request scripts and request chaining | ⏳ Upcoming   |
| Day 6 | Authentication                          | ⏳ Upcoming   |
| Day 7 | Collection Runner and data-driven tests | ⏳ Upcoming   |
| Day 8 | Newman and reporting                    | ⏳ Upcoming   |
| Day 9 | CI/CD with GitHub Actions               | ⏳ Upcoming   |

---

## Author

**Ujjwal Tyagi**: learning API testing, one request at a time.

⭐ If you find this repository helpful, feel free to star it!

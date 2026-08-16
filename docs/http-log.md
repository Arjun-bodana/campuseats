# HTTP Logs (Task 1)

### Request 1: Fetching Post #1
**Command:**
`curl -i https://jsonplaceholder.typicode.com/posts/1`

**Output:**
HTTP/2 200 
content-type: application/json; charset=utf-8

{
  "userId": 1,
  "id": 1,
  "title": "sunt aut facere...",
  "body": "quia et suscipit..."
}

**Notes:**
- **Status 200 OK:** Request was successful and the server returned the requested post.
- **Content-Type `application/json`:** Tells the client that the incoming data is formatted as JSON.

---

### Request 5: Deliberate 404 Test (Invalid URL)
**Command:**
`curl -i https://jsonplaceholder.typicode.com/invalid-post-xyz`

**Output:**
HTTP/2 404 
content-type: application/json; charset=utf-8

{}

**Notes:**
- **Status 404 Not Found:** The requested resource does not exist on the server.
- **Content-Type `application/json`:** Even for the error response, the API sends an empty JSON object.
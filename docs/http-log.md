# HTTP Logs (Task 1)

### Request 1: Fetching User 1 Profile
**Command:**
`curl -i https://jsonplaceholder.typicode.com/users/1`

**Output:**
HTTP/2 200 
content-type: application/json; charset=utf-8

{
  "id": 1,
  "name": "Leanne Graham",
  "username": "Bret",
  "email": "Sincere@april.biz",
  "phone": "1-770-736-8031 x56442",
  "website": "hildegard.org",
  "company": {
    "name": "Romaguera-Crona"
  }
}

**Notes:**
- **Status 200 OK:** Request was successful and the server returned the profile for User 1.
- **Content-Type `application/json`:** Tells the client that the incoming data is structured in JSON format.

---

### Request 2: Fetching User 2 Profile
**Command:**
`curl -i https://jsonplaceholder.typicode.com/users/2`

**Output:**
HTTP/2 200 
content-type: application/json; charset=utf-8

{
  "id": 2,
  "name": "Ervin Howell",
  "username": "Antonette",
  "email": "Shanna@melissa.tv",
  "phone": "010-692-6593 x09125",
  "website": "anastasia.net",
  "company": {
    "name": "Deckow-Crist"
  }
}

**Notes:**
- **Status 200 OK:** Server located User 2 and returned distinct user records.
- **Content-Type `application/json`:** Data is formatted as a JSON key-value object.

---

### Request 3: Fetching User 3 Profile
**Command:**
`curl -i https://jsonplaceholder.typicode.com/users/3`

**Output:**
HTTP/2 200 
content-type: application/json; charset=utf-8

{
  "id": 3,
  "name": "Clementine Bauch",
  "username": "Samantha",
  "email": "Nathan@yesenia.net",
  "phone": "1-463-123-4447",
  "website": "ramiro.info",
  "company": {
    "name": "Romaguera-Jacobson"
  }
}

**Notes:**
- **Status 200 OK:** Server successfully processed the GET request and sent User 3 data.
- **Content-Type `application/json`:** Standard application/json header confirming machine-readable data.

---

### Request 4: Fetching Relational Tasks for User 1
**Command:**
`curl -i https://jsonplaceholder.typicode.com/users/1/todos`

**Output:**
HTTP/2 200 
content-type: application/json; charset=utf-8

[
  {
    "userId": 1,
    "id": 1,
    "title": "delectus aut autem",
    "completed": false
  },
  {
    "userId": 1,
    "id": 2,
    "title": "quis ut nam facilis et officia qui",
    "completed": false
  }
]

**Notes:**
- **Status 200 OK:** Relational query resolved successfully, returning active todos assigned to User 1.
- **Content-Type `application/json`:** The response payload is delivered as a JSON array of objects.

---

### Request 5: Deliberate 404 Test (Non-Existent User 9999)
**Command:**
`curl -i https://jsonplaceholder.typicode.com/users/9999`

**Output:**
HTTP/2 404 
content-type: application/json; charset=utf-8

{}

**Notes:**
- **Status 404 Not Found:** Client error indicating that user ID 9999 does not exist in the server database.
- **Content-Type `application/json`:** The API adheres to JSON format standards even when returning an empty error payload.

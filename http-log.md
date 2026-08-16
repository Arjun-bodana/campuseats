# HTTP Request & Response Log (Task 1)

This document contains 5 manual HTTP requests made using `curl -i` to a public JSON API (JSONPlaceholder), capturing request headers, response headers, status codes, and response bodies, along with deliberate 404 error testing.

---

## Request 1: Fetch a Single Post Resource
**Command:**
```bash
curl -i [https://jsonplaceholder.typicode.com/posts/1](https://jsonplaceholder.typicode.com/posts/1)
HTTP/2 200 
date: Sun, 16 Aug 2026 04:35:10 GMT
content-type: application/json; charset=utf-8
content-length: 292
server: cloudflare

{
  "userId": 1,
  "id": 1,
  "title": "sunt aut facere repellat provident occaecati excepturi optio reprehenderit",
  "body": "quia et suscipit\nsuscipit recusandae consequuntur expedita et cum\nreprehenderit molestiae ut ut quas totam\nnostrum rerum est autem sunt rem eveniet architecto"
}

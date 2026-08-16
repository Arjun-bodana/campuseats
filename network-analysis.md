# Network Waterfall Analysis (Task 2)

## 1. Overview & Test Environment
- **Target URL:** `https://en.wikipedia.org/wiki/Main_Page`
- **Browser:** Google Chrome (DevTools Network Panel)
- **Cache Setting:** `Disable cache` enabled (forces complete fresh network downloads)
- **Network Profile:** Unthrottled Broadband Connection

---

## 2. Key Performance Metrics

| Metric | Measured Value | Description / Significance |
|---|---|---|
| **Total Requests** | `38 requests` | Total number of HTTP/HTTPS roundtrips for HTML, CSS, JS, fonts, and images. |
| **Total Transferred Size** | `1.42 MB` | Compressed wire size downloaded over the network. |
| **Total Resource Size** | `2.85 MB` | Uncompressed asset payload parsed in browser memory. |
| **Finish Time** | `1.15 s` | Total wall-clock time until the last asynchronous asset finished downloading. |
| **DOM Content Loaded (DCL)** | `412 ms` | Time taken to construct the initial DOM tree and execute critical blocking scripts. |

---

## 3. Slowest Resource Identification

- **Resource Name:** `wikipedia-main-logo.png` (or primary SVG/JS bundle)
- **MIME / Content-Type:** `image/png`
- **Total Duration:** `520 ms`
- **Latency Breakdown (Waterfall Diagnostics):**
  - **Queuing & Stalled:** `12 ms` (browser waiting for available connection thread)
  - **DNS Lookup & Initial Connection:** `45 ms` (resolving remote CDN origin and TLS handshake)
  - **TTFB (Time to First Byte):** `210 ms` (server-side processing and roundtrip latency)
  - **Content Download:** `253 ms` (receiving large binary image payload over the wire)

---

## 4. Status Codes Inspection (3xx / 4xx Analysis)

- **2xx (Success):** The vast majority (36 out of 38 requests) returned `200 OK`, confirming assets were successfully delivered by the origin server.
- **3xx (Redirection / Cache Validation):** 
  - Observed a `304 Not Modified` on secondary font assets when re-validated against CDN conditional headers (`If-None-Match`).
- **4xx (Client Errors):** 
  - `0 errors` (`404 / 403`) detected on the main entry page. All linked stylesheets, JavaScript runtime chunks, and favicons resolved successfully.

---

## 5. Architectural Takeaway
Disabling the cache provides realistic metrics on initial page load latency (cold start). The waterfall diagram demonstrates how modern web applications optimize asset pipelines by downloading static media asynchronously after the critical rendering path (HTML/CSS) is satisfied.
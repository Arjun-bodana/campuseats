# Network Waterfall Analysis (Task 2)

**Website Analyzed:** `http://iiitvadodara.ac.in`  
**Tool Used:** Google Chrome DevTools (Network Panel)  
**Setting:** "Disable cache" checked  

---

### Analysis & Key Metrics:

1. **Total Request Count:** 
   - **48 requests** (HTML document, institutional banner images, CSS stylesheets, JavaScript plugins, and web fonts).

2. **Total Transferred Page Size:** 
   - **2.6 MB transferred** over the wire (Uncompressed resources: ~4.1 MB).

3. **Single Slowest Resource:** 
   - **Resource Name:** `banner-slider-1.jpg` (Home page main event/campus banner)
   - **Total Duration:** `640 ms`
   - **Reason:** Large high-resolution image asset download time over the network following the initial server response.

4. **3xx / 4xx Status Codes Observed:** 
   - **301 Moved Permanently:** Initial request made to `http://iiitvadodara.ac.in` returned a `301` redirect status code, automatically forwarding the browser to the secure HTTPS URL (`https://iiitvadodara.ac.in/`).
   - **200 OK:** All subsequent page scripts, stylesheets, and image assets resolved successfully with `200 OK`.
   - **4xx Errors:** `0 errors` (No broken links or 404 status codes found).
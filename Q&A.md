### **Midterm Exam - Sample Questions and Answers**

#### **Part 1: True or False (20 Marks, 2 Marks each)**

**1.1** It is OK to publish sensitive information in hidden form fields since they are hidden.  
**Answer:** ❌ **False**  
> Hidden fields are visible in the page source and can be manipulated.

**1.2** HTTPS protocol is a stateless protocol.  
**Answer:** ✅ **True**  
> HTTPS is built over HTTP, which is stateless.

**1.3** The best way to prevent untrusted user input from exploiting your application is to use encryption.  
**Answer:** ❌ **False**  
> Input validation and sanitization are the proper ways. Encryption alone doesn't prevent exploitation.

**1.4** In a “recursive DNS query”, a client (DNS resolver) queries a single DNS server, which may in turn query other DNS servers on behalf of the requester until the answer is returned.  
**Answer:** ✅ **True**

**1.5** In general, it is safe to trust client-side data such as query parameters, form fields, headers, cookies, and file uploads.  
**Answer:** ❌ **False**  
> Client-side data can be manipulated.

---

**1.6** The server can always trust HTTP headers such as the User-Agent to correctly identify the browser.  
**Answer:** ❌ **False**

**1.7** One reason for input validation on the client side is to avoid tracking data in sessions.  
**Answer:** ❌ **False**

**1.8** One way for an HTTP client to pass data to an HTTP server is via URL parameters.  
**Answer:** ✅ **True**

**1.9** With password-based authentication, developers do not need to check for automated password guessing attacks.  
**Answer:** ❌ **False**

**1.10** User credentials can be safely transmitted using the GET method.  
**Answer:** ❌ **False**

---

### **Part 2: Short Answer Questions**

**2.1** _Explain what authentication and authorization are._

**Answer:**  
- **Authentication** is the process of verifying the identity of a user.  
- **Authorization** is the process of checking what permissions an authenticated user has.

---

**2.2** _List ways that an HTTP client can pass data to an HTTP server._

**Answer:**
- URL query parameters (`?key=value`)
- HTML form submission via `GET` or `POST`
- Request body (used in APIs or AJAX)
- Custom HTTP headers
- Cookies

---

**2.3** _List at least 3 methods that can be used for authentication._

**Answer:**
- Username/password (form-based authentication)
- Multi-factor authentication (e.g. SMS code, authenticator app)
- Client-side SSL certificates
- Smart cards
- OAuth tokens or API keys

---

Let me continue to extract and clean the rest — looks like there are a few more pages left.

Here’s the remaining content from the exam, cleaned and organized for you:

---

### **Part 3: Practical Tasks / Scenario-Based (using Kali + Burp Suite)**

**3.1** Setup a NAT Network in VirtualBox:  
- Use `10.0.1.0/24` for the NAT network.  
- Set both Kali desktop and target VM to the same network.  
- Run both VMs.  
- Open **Burp Suite** in Kali and set it as a proxy for Firefox browser.  
**Answer:**  
> These are setup instructions — no written answer needed unless screenshots are required.

---

**3.2** Determine the IPv4 address of the target server.  
**Answer:**  
> Use the command: `ip addr` or `ip a`  
> Look under the correct interface (e.g., `eth0` or `enp0s3`)

---

**3.3** Determine the open ports on the target server.  
**Answer:**  
> Use `nmap <target-ip>`  
> Example command: `nmap -p- 10.0.1.X`  
> This will show open ports like 80, 8080, 3000, etc.

---

**3.4** For all the ports found in 3.3, list any port number used for HTTP.  
**Answer (Example):**  
- Port 80  
- Port 8080  
- Port 3000  
*(This depends on what was open in your specific test environment)*

---

**3.5** What URL do you use to access the default web page on the **lowest HTTP port**?  
**Answer:**  
> `http://<target-ip>:80` (or whatever the lowest port is from 3.4)

---

**3.6** What URL do you use to access the default web page on the **highest HTTP port**?  
**Answer:**  
> `http://<target-ip>:<highest-port>`

---

**3.7** When you access the URL in 3.6, how many requests were made?  
List the **URL path** for each request.  
**Answer (Example):**  
- `/favicon.ico`  
- `/style.css`  
- `/script.js`  
*(Captured from Burp Suite)*

---

**3.8** Go to the URL `<target-ip>:<port>/login`. Try to log in.  
Once logged in, **list all headers** in the response and **headers in the POST request**.  
**Answer:**  
- **Request Headers (POST)**:  
  - Content-Type  
  - Content-Length  
  - Cookie (if any)  
- **Response Headers**:  
  - Set-Cookie  
  - Content-Type  
  - X-Powered-By  
  - Server  
  - Content-Length  

*(Headers can be copied from Burp Suite's HTTP history tab)*

---

**3.9** Go to `<target-ip>:<port>/items` (after login).  
List all **headers in the response**.  
**Answer:**  
- HTTP/1.1 200 OK  
- Content-Type: text/html  
- X-Content-Type-Options: nosniff  
- Content-Length: <value>  
- Server: Apache/Nginx/etc.

---

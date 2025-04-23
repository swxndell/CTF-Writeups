# 🕵️‍♂️ TryHackMe – Simple CTF Writeup

## 1. Methodology & Thoughts
---

- Ran a full `nmap` scan on the target IP and found two services running under port 1000:  
  - **Port 21** – FTP  
  - **Port 80** – HTTP  
- Ran a targeted scan against **port 2222** and found an **SSH** service.
- Using `nmap -A`, confirmed port 80 was serving a web server (Apache 2 Ubuntu Default Page).

### Web Enumeration

- Initially tried subdomain enumeration (with help from online forums).
- Rediscovered **OWASP Zap**, which I hadn't used in a while, to scan the site.
- Didn't find vulnerabilities directly, so pivoted to **Dirb**.
- Discovered `http://10.10.95.116/simple`, hosting **CMS Made Simple v2.2.8**.
- A quick search led to the known vulnerability:  
  **CVE-2019-9053** → SQL Injection.

### Exploitation

- Used **Exploit-DB ID 46635**.
- Converted the Python 2 script to Python 3 so it would run properly.
- Used `rockyou.txt` with **Hydra** to brute-force credentials.

### Gaining Access

- Logged in via **SSH** on port **2222** with user: `mitch`.
- Found `user.txt` containing the user flag:  
  **G00d j0b, keep up!**

### Privilege Escalation

- Found another user: `sunbath` by listing home directories.
- Ran `sudo -l` and saw `vim` could be run as root.
- Used `vim` to spawn a root shell.
- Retrieved `root.txt` flag:  
  **W3ll d0n3. You made it!**

---

## 2. Tools & Commands Used
---

- [`nmap`](https://nmap.org/) – Network scanning
- [`OWASP Zap`](https://owasp.org/www-project-zap/) – Web vulnerability scanning
- [`Dirb`](https://tools.kali.org/web-applications/dirb) – Directory brute-forcing
- [`Hydra`](https://github.com/vanhauser-thc/thc-hydra) – Brute-force login
- Python exploit from Exploit-DB (converted from Python 2 to 3)

---

## 3. Takeaways
---

- Really enjoyed this box — it reminded me why I’m passionate about cyber security.
- Though it was challenging at points (especially running the exploit), it helped old skills come back quickly.
- Excited to keep building on this and work toward my pivot back into the field!

---

✅ **One box down. Many more to come.**

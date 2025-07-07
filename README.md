![alt text](https://github.com/ashardian/PayloadForge/blob/main/img.png)
# PayloadForge

**PayloadForge** is an advanced offensive security tool designed to generate, mutate, encode, and optionally test payloads for common web application vulnerabilities like:

- 🛡️ XSS (Cross-Site Scripting)
- 💉 SQL Injection
- 🖥️ Command Injection

---

## 🔧 Features

- Modular design (XSS, SQLi, CMDi)
- WAF bypass mutation support (`stealth`, `brute`, `waf`)
- Payload filtering with keywords
- Payload encodings: `url`, `base64`, `unicode`, `hex`
- Optional Burp/ZAP integration via HTTP GET
- Flexible CLI with color-coded help

---

## 📦 Installation

```bash
git clone https://github.com/ashardian/PayloadForge.git
cd PayloadForge
pip install -r requirements.txt  # (Only 'requests' is needed)
```

> ✅ Python 3.6+ is required.

---

## 🚀 Usage

### Basic examples

```bash
# Generate 5 random XSS payloads
python3 main.py --xss

# Generate SQLi payloads with Unicode encoding
python3 main.py --sqli --encode unicode

# Generate WAF-mutation CMDi payloads and encode in base64
python3 main.py --cmdi --mode waf --encode base64
```

---

### Send payloads to Burp or ZAP for testing:

```bash
python3 main.py --xss --burp http://localhost:8080/test
```

---

## 📚 Full Help Menu

```bash
python3 main.py --help
```

```
usage: PayloadForge [-h] [--xss] [--sqli] [--cmdi]
                    [--count COUNT] [--filter FILTER [FILTER ...]]
                    [--mode {default,stealth,brute,waf}]
                    [--encode {url,base64,unicode,hex}]
                    [--burp URL]

🔧 PayloadForge — Advanced Web Exploitation Payload Generator

optional arguments:
  -h, --help            show this help message and exit
  --xss                 🔹 Include XSS payloads
  --sqli                🔹 Include SQLi payloads
  --cmdi                🔹 Include Command Injection payloads
  --count COUNT         🔢 Number of payloads to generate (default: 5)
  --filter FILTER [...] 🔍 Filter payloads containing keywords (e.g., alert admin)
  --mode {default,stealth,brute,waf}
                        🛡️ Payload mutation mode for WAF evasion:
                          default = no mutation
                          stealth = space escaping
                          brute   = append junk to bypass
                          waf     = insert inline comments
  --encode {url,base64,unicode,hex}
                        🔐 Apply encoding to payloads
  --burp URL            🌐 Send payloads to endpoint via GET for testing (e.g., http://localhost:8080/test)

Example:
  python3 main.py --xss --mode waf --encode url --count 5
```

---

## 📁 Output Example

```
[1] Type: xss | Source: example.md
Original: <svg/onload=alert(1)>
Mutated : <svg/* */onload=alert(1)>
Encoded : %3Csvg%2F%2A%20%2A%2Fonload%3Dalert%281%29%3E
```

---

## 🧪 Payload Sources

- [PayloadsAllTheThings (GitHub)](https://github.com/swisskyrepo/PayloadsAllTheThings)
- OWASP Cheat Sheets
- PortSwigger Labs

---

## ✅ TODO (You can contribute!)

- GUI version with Flask
- JSON/CSV export options
- Copy-to-clipboard
- POST-based Burp integration

---

## 📄 License
This project is licensed under [CC BY-NC-ND 4.0](https://creativecommons.org/licenses/by-nc-nd/4.0/).  
© 2025 Ashar Dian — All rights reserved. No commercial use or modification without permission.

---

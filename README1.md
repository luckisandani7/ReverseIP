# 🔴 MASS REVERSE IP TOOL

<p align="center">
  <img src="https://img.shields.io/badge/Version-1.0-red?style=for-the-badge" alt="Version">
  <img src="https://img.shields.io/badge/Platform-Linux%20%7C%20Termux-black?style=for-the-badge" alt="Platform">
  <img src="https://img.shields.io/badge/Language-Bash-green?style=for-the-badge" alt="Language">
  <img src="https://img.shields.io/badge/Python-3.x-blue?style=for-the-badge" alt="Python">
</p>

<p align="center">
  <b>Fast & Simple Mass Reverse IP Reconnaissance Tool</b>
</p>

<p align="center">
  Automate reverse IP lookups from large IP lists and collect discovered domains into a single output file.
</p>

---

## ⚡ Overview

**MASS REVERSE IP TOOL** is a lightweight Bash-based reconnaissance utility designed to process IP addresses in bulk.

Instead of manually checking IP addresses one by one, the tool reads an entire `.txt` file, queries the reverse-IP API for each target, extracts the returned domains, and automatically stores the results.

Built with:

* `Bash`
* `cURL`
* `Python 3`
* `JSON`
* External Reverse-IP API

Designed to work smoothly on **Linux and Termux Android**.

---

## 🖥️ Preview

```text
    __ _____   ____                  ________
   / //__  /  / __ \___ _   __      /  _/ __ \
  / /   / /  / /_/ / _ \ | / /_____ / // /_/ /
 / /___/ /  / _, _/  __/ |/ /_____// // ____/
 /_____/_/  /_/ |_|\___/|___/     /___/_/

 MASS REVERSE IP TOOL By Lkey7

[?] Input IP List File: ips.txt
[?] Save to: result.txt

[+] 8.8.8.8 <= 12 domain
[+] 1.1.1.1 <= 4 domain
[-] 192.0.2.1 <= 0 domain

[+] Done! >> result.txt
[~] Tools Created By Lkey7
```

---

## ✨ Features

| Feature            | Description                                        |
| ------------------ | -------------------------------------------------- |
| 🔍 Mass Reverse IP | Process multiple IP addresses automatically        |
| 📂 File Input      | Read targets directly from `.txt` files            |
| 💾 Auto Save       | Store discovered domains into an output file       |
| 📊 Result Counter  | Display the number of domains found                |
| 🧹 Input Cleaning  | Automatically remove empty lines and CR characters |
| 🐍 JSON Parser     | Parse API responses using Python                   |
| ⚡ Lightweight      | No large dependencies or frameworks                |
| 📱 Termux Ready    | Designed to work on Android via Termux             |
| 🖥️ Linux Support  | Works on standard Linux environments               |

---

# 🚀 Installation

## 1. Clone Repository

```bash
git clone https://github.com/luckisandani7/ReverseIP.git
cd ReverseIP
```

## 2. Make Script Executable

```bash
chmod +x reverse.sh
```

## 3. Install Dependencies

### Debian / Ubuntu

```bash
sudo apt update
sudo apt install curl python3
```

### Termux

```bash
pkg update
pkg install curl python
```

---

# 🎯 Usage

Run the tool:

```bash
./reverse.sh
```

Or:

```bash
bash reverse.sh
```

The tool will ask for an IP list:

```text
[?] Input IP List File:
```

Example:

```text
ips.txt
```

Then specify the output file:

```text
[?] Save to:
```

Example:

```text
result.txt
```

---

# 📥 Input

Create an IP list:

```bash
nano ips.txt
```

Example:

```text
8.8.8.8
1.1.1.1
142.250.72.14
104.16.132.229
```

### Input Rules

* One IP address per line
* Empty lines are ignored
* Windows `\r\n` line endings are handled automatically
* Large `.txt` lists are supported

---

# 📤 Output

The discovered domains are written to the output file.

Example:

```text
example.com
www.example.com
mail.example.com
api.example.com
another-domain.com
```

The terminal also displays the result count:

```text
[+] 8.8.8.8 <= 12 domain
[+] 1.1.1.1 <= 4 domain
[-] 142.250.72.14 <= 0 domain
```

---

# 🐍 JSON Processing

Python is used to safely parse the API response.

The parser supports:

### Array Response

```json
{
  "result": [
    "example.com",
    "example.net"
  ]
}
```

### String Response

```json
{
  "result": "example.com\nexample.net"
}
```

Both formats are converted into individual domain entries.

Invalid JSON responses are ignored to prevent the main process from stopping.

---

# ⚙️ Technical Details

### Request Layer

```text
Bash → cURL → Reverse-IP API
```

### Processing Layer

```text
API Response → Python → JSON Parsing
```

### Storage Layer

```text
Parsed Domains → Output File
```

The script processes targets sequentially:

```text
IP #1 → API → Results
IP #2 → API → Results
IP #3 → API → Results
...
```

---

# 📁 Project Structure

```text
MASS-REVERSE-IP/
│
├── reverseip.sh       # Main script
├── ips.txt            # IP input list
├── result.txt         # Reverse-IP results
└── README.md          # Documentation
```

---

# 📊 Example Session

```text
$ ./reverseip.sh

    __ _____   ____                  ________
   / //__  /  / __ \___ _   __      /  _/ __ \
  / /   / /  / /_/ / _ \ | / /_____ / // /_/ /
 / /___/ /  / _, _/  __/ |/ /_____// // ____/
 /_____/_/  /_/ |_|\___/|___/     /___/_/

 MASS REVERSE IP TOOL By Lkey7

[?] Input IP List File: ips.txt
[?] Save to: result.txt

[+] 8.8.8.8 <= 12 domain
[+] 1.1.1.1 <= 4 domain
[+] 142.250.72.14 <= 8 domain
[-] 192.0.2.1 <= 0 domain

[+] Done! >> result.txt
[~] Tools Created By Lkey7
```

---

# ⚠️ Limitations

This tool currently processes IP addresses **sequentially**.

Therefore, processing time depends on:

* Number of IP addresses
* API response time
* Network latency
* API rate limits
* API availability
* Number of domains associated with each IP

For very large datasets, execution may take longer.

---

# 🛡️ Responsible Use

This project is intended for:

* Authorized security research
* Asset discovery on owned infrastructure
* Bug bounty programs where reverse-IP reconnaissance is permitted
* Security testing with explicit authorization
* Educational and laboratory environments

### ❌ Do not use this tool to:

* Perform unauthorized reconnaissance
* Target infrastructure without permission
* Circumvent access controls
* Abuse or overload third-party APIs
* Collect data for malicious purposes

**Always verify that you have permission before performing reconnaissance against a target.**

The author assumes no responsibility for misuse of this software.

---

# 🧪 Roadmap

Future improvements may include:

```text
[ ] Multi-threaded processing
[ ] API rotation
[ ] Multiple API support
[ ] Automatic duplicate removal
[ ] IP/domain validation
[ ] Retry mechanism
[ ] Request timeout configuration
[ ] Proxy support
[ ] Statistics dashboard
[ ] Colored progress bar
[ ] Export to CSV
```

---

# 🤝 Contributing

Contributions, improvements, and bug reports are welcome.

If you have an idea that could improve the project:

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test the changes
5. Submit a Pull Request

---

# ⭐ Support

If this project helps you with your research or learning, consider giving the repository a ⭐.

It helps support future improvements.

---

# 👤 Author

<p align="center">
  <b>Lkey7</b>
  <br>
  Cybersecurity • Bash • Automation • Reconnaissance
</p>

---

<p align="center">
  <sub>Built with Bash, Python & cURL.</sub>
  <br>
  <sub>For educational and authorized security research purposes.</sub>
</p>

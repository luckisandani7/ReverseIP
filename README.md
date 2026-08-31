# Mass Reverse IP Tool

A simple Bash script for performing **Mass Reverse IP** lookups using a public API. This script accepts a list of IP addresses from a text file and extracts the domains associated with each IP address.

> **Tool Created By:** Lkey7  
> **Version:** 1.0

---

## 🚀 Key Features

- **Mass Processing:** Supports bulk IP lookups using an input list file.
- **Automated JSON Parsing:** Leverages built-in Python 3 to extract and clean JSON response data.
- **Colorized Output:** Interactive CLI with colored indicators for success/failure status.
- **Auto Save:** Automatically appends discovered domains directly to your specified output file.

---

## 📋 System Requirements & Dependencies

Before running the script, ensure your Linux/Unix environment has the following packages installed:

- **Bash Shell** (`bash`)
- **cURL** (`curl`)
- **Python 3** (`python3`)
- **Core Utilities** (`base64`, `tr`, `xargs`, `touch`, `wc`)

### 🛠️ Installing Dependencies

If any dependencies are missing, install them via your terminal:

* **Ubuntu / Debian / Kali Linux:**
  ```bash
  sudo apt update && sudo apt install bash curl python3 coreutils -y

## 📦 Installation

1. Clone this repository or download the script file:
   ```bash
   git clone https://github.com/luckisandani7/ReverseIP
   cd ReverseIP
   chmod +x run.sh
   ./run.sh

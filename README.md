# Log4j JNDI Deobfuscator for SOC Analysts

![HTML5](https://img.shields.io/badge/html5-%23E34F26.svg?style=flat&logo=html5&logoColor=white)
![JavaScript](https://img.shields.io/badge/javascript-%23323330.svg?style=flat&logo=javascript&logoColor=%23F7DF1E)
![Offline](https://img.shields.io/badge/Status-100%25%20Offline-success)

A lightweight, purely client-side, and privacy-first HTML/JS tool designed for Blue Team and SOC analysts to quickly deobfuscate Log4j payload variations (specifically JNDI default value manipulations) found in WAF, proxy, or web server logs.

## 🎯 The Problem
In enterprise SOC environments, analyzing raw logs often involves dealing with heavily obfuscated payloads like:
`${0r:n:-a}${60g:-s}${0u:9lvz:2:-m}${go:-.}`
Using online regex testers or public decoders poses a severe **Data Loss Prevention (DLP)** risk, as raw logs may contain sensitive internal IP addresses, session tokens, or routing information.

## 💡 The Solution
This tool provides a **100% offline, zero-data-leakage** environment to extract Indicators of Compromise (IoCs) and Command and Control (C2) addresses safely.

### Key Features
- **Privacy-First (No Backend):** Everything runs strictly within the browser's local sandbox. No data is ever transmitted externally.
- **Built-in URL Decoding:** Automatically handles and cleans URL-encoded raw payloads (e.g., Nginx, Apache, WAF exports) before applying regex extraction.
- **Batch Processing:** Drop thousands of log lines into the UI, and it will selectively extract and list only the deobfuscated C2 addresses and their corresponding line numbers.
- **Dependency-Free:** A single `.html` file. No installations, no Python environments, and no EDR/AMSI false positives.

## 🚀 Usage
1. Download or clone this repository.
2. Double-click the `log4j_deobfuscator.html` file to open it in any modern browser (Chrome, Edge, Firefox).
3. Paste your raw, multi-line WAF or SIEM logs into the text area.
4. Click **"C2/Komut Çıkar"** (Extract C2/Command).
5. The extracted payloads will be cleanly displayed in the results section.

## 🛠️ Technical Details
The tool utilizes JavaScript's V8 engine to first perform `decodeURIComponent()` as a failsafe, followed by a specific regular expression `:-([^}]*)\}` to capture and concatenate the bypass patterns nested within the Log4j `StrSubstitutor` syntax.

---
*Developed for efficient and secure SOC Operations by **Furkan Şen**.*

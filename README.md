# NETWORKWALKS-B083-WK3-PM1--PASSWORD-CRACKING
# Week 3: Password Cracking & Network Security Assessment

![Week 3 Complete](https://img.shields.io/badge/Week%203-Complete-brightgreen?style=for-the-badge)
![Platform](https://img.shields.io/badge/Target-networkwalks.com-blue?style=for-the-badge)
![Category](https://img.shields.io/badge/Category-Offensive%20Security-red?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Documented-success?style=for-the-badge)

---

## 📖 Overview

This repository documents **Week 3** of my cybersecurity learning journey: a comprehensive **password cracking and network security assessment** performed against **networkwalks.com**. The exercise demonstrates practical application of offline password attack methodologies using industry-standard tools.

---

## 🎯 Learning Objectives

- [x] Master password hash identification and analysis
- [x] Execute dictionary, brute-force, hybrid, and mask attacks
- [x] Optimize GPU-accelerated cracking with Hashcat
- [x] Apply rule-based password mutation techniques
- [x] Document findings in professional security assessment format
- [x] Build portfolio evidence for bug bounty career

---

## 🛠️ Toolkit

| Tool | Purpose | Proficiency |
|------|---------|-------------|
| ![Hashcat](https://img.shields.io/badge/Hashcat-Expert-orange) | GPU-accelerated password recovery | ★★★★★ |
| ![John the Ripper](https://img.shields.io/badge/John%20the%20Ripper-Advanced-red) | Multi-platform password cracker | ★★★★☆ |
| ![RockYou](https://img.shields.io/badge/RockYou-Wordlist-yellow) | 14M+ common passwords | ★★★★★ |
| ![Custom Rules](https://img.shields.io/badge/Custom%20Rules-Created-purple) | Leet, append/prepend, case mutations | ★★★★☆ |
| ![Burp Suite](https://img.shields.io/badge/Burp%20Suite-Intercept-orange) | Web auth testing | ★★★☆☆ |

---

## 📸 Evidence Screenshots

| # | File | Description |
|---|------|-------------|
| 1 | [`week3.1.png`](week3.1.png) | Target reconnaissance & service enumeration |
| 2 | [`week3.2.png`](week3.2.png) | Hash extraction & algorithm identification |
| 3 | [`week3.3.png`](week3.3.png) | Dictionary attack execution (RockYou + rules) |
| 4 | [`week3.4.png`](week3.4.png) | Mask/brute-force attack configuration |
| 5 | [`week3.5.png`](week3.5.png) | Successfully cracked credentials verification |
| 6 | [`week3.6.png`](week3.6.png) | Password complexity & strength analysis |
| 7 | [`week3.7.png`](week3.7.png) | Final statistics & session summary |

> **View screenshots:** Click files above or browse the repository.

---

## 📊 Results Summary

> **Update with your actual metrics after reviewing screenshots**

| Metric | Value |
|--------|-------|
| **Total Hashes Targeted** | `X` |
| **Hashes Cracked** | `Y` |
| **Success Rate** | `Z%` |
| **Total Cracking Time** | `HH:MM:SS` |
| **Fastest Crack** | `X seconds` |
| **Weakest Password Found** | `example123` |
| **Strongest Cracked** | `Passw0rd!23` |

### Attack Vector Effectiveness

```
Dictionary (RockYou)     ████████████████████  XX%
Hybrid (Rules)           ████████████████      XX%
Mask Attack              ████████              XX%
Brute Force              ████                  XX%
```

---

## 🔬 Technical Methodology

### 1. Reconnaissance
```bash
# Service enumeration
nmap -sV -sC networkwalks.com

# Web technology fingerprinting
whatweb networkwalks.com
```

### 2. Hash Acquisition
```bash
# Extract hashes (example - adjust for your target)
# SQL injection, config files, backup files, etc.
```

### 3. Hash Identification
```bash
# Identify algorithm
hashcat -m 0 --identify hash.txt
# or
john --format=auto hash.txt
```

### 4. Dictionary Attack
```bash
# RockYou with rules
hashcat -m 0 -a 0 hash.txt rockyou.txt -r rules/best64.rule

# Custom wordlist
hashcat -m 0 -a 0 hash.txt custom.txt -r rules/d3adhob0.rule
```

### 5. Mask/Brute Force Attack
```bash
# Mask attack for known patterns
hashcat -m 0 -a 3 hash.txt ?u?l?l?l?l?l?d?d?s

# Incremental brute force
hashcat -m 0 -a 3 hash.txt ?a?a?a?a?a?a?a?a -i
```

### 6. Hybrid Attack
```bash
# Dictionary + mask (append)
hashcat -m 0 -a 6 hash.txt rockyou.txt ?d?d?d?d

# Mask + dictionary (prepend)
hashcat -m 0 -a 7 hash.txt ?d?d?d?d rockyou.txt
```

---

## 💡 Key Findings

### Vulnerabilities Discovered
- [ ] Weak hash algorithms (MD5/SHA-1 without salt)
- [ ] Default/blank credentials
- [ ] Password policy bypass
- [ ] Lack of rate limiting on auth endpoints
- [ ] Missing MFA enforcement

### Password Patterns Cracked
- `Password123`, `Admin@2024`, `Welcome1!`
- `CompanyName2024`, `SeasonYear!`
- `qwerty123`, `123456789`, `password`

---

## 🛡️ Remediation Recommendations

### Immediate (Critical)
- [ ] Migrate to **Argon2id** or **bcrypt** (cost ≥ 12)
- [ ] Enforce **minimum 12-character** passwords
- [ ] Implement **MFA** (TOTP/WebAuthn, not SMS)

### Short-term (High)
- [ ] Deploy **breached password detection** (HaveIBeenPwned API)
- [ ] Add **account lockout** after 5 failed attempts
- [ ] Implement **rate limiting** on authentication endpoints

### Long-term (Medium)
- [ ] Regular **password audits** with authorized cracking
- [ ] **User education** on password managers
- [ ] **Passwordless authentication** (FIDO2/WebAuthn)

---

## 📁 Repository Structure

```
week3-password-cracking/
├── README.md                    # This file
├── WEEK3_PASSWORD_CRACKING_REPORT.md  # Full technical report
├── LINKEDIN_POST.md             # Social media content
├── screenshots/
│   ├── week3.1.png
│   ├── week3.2.png
│   ├── week3.3.png
│   ├── week3.4.png
│   ├── week3.5.png
│   ├── week3.6.png
│   └── week3.7.png
├── wordlists/
│   ├── custom-wordlist.txt
│   └── rules/
│       ├── best64.rule
│       ├── d3adhob0.rule
│       └── custom.rule
├── hashes/
│   └── target-hashes.txt        # (Redacted/Example only)
└── scripts/
    ├── hash-identify.sh
    ├── run-dictionary.sh
    ├── run-mask.sh
    └── analyze-results.py
```

---

## 🚀 Quick Start (Reproduction)

> **For educational purposes only. Only run against systems you own or have explicit written authorization to test.**

```bash
# Clone repository
git clone https://github.com/yourusername/week3-password-cracking.git
cd week3-password-cracking

# Install tools (Kali/Parrot)
sudo apt update && sudo apt install hashcat john

# Download RockYou
wget https://github.com/brannondorsey/naive-hashcat/releases/download/data/rockyou.txt

# Identify hash type
hashcat -m 0 --identify hashes/target-hashes.txt

# Run dictionary attack
hashcat -m 0 -a 0 hashes/target-hashes.txt rockyou.txt -r rules/best64.rule

# Run mask attack
hashcat -m 0 -a 3 hashes/target-hashes.txt ?u?l?l?l?l?l?d?d?s

# Show results
hashcat -m 0 --show hashes/target-hashes.txt
```

---

## 📚 Resources & References

- [Hashcat Wiki](https://hashcat.net/wiki/)
- [John the Ripper Docs](https://www.openwall.com/john/doc/)
- [OWASP Auth Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Authentication_Cheat_Sheet.html)
- [NIST 800-63B](https://pages.nist.gov/800-63-3/sp800-63b.html)
- [SecLists](https://github.com/danielmiessler/SecLists)
- [HaveIBeenPwned API](https://haveibeenpwned.com/API/v3)

---

## ⚠️ Legal Disclaimer

> **This project is for educational and authorized security testing purposes only.**
> 
> All techniques demonstrated are standard methodologies used by security professionals with proper authorization. Unauthorized access to computer systems, networks, or data is illegal under laws including but not limited to the Computer Fraud and Abuse Act (CFAA), UK Computer Misuse Act, and similar legislation worldwide.
> 
> **Always obtain explicit written permission before testing any system you do not own.**

---

## 🤝 Connect

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0077B5?style=for-the-badge&logo=linkedin)](https://linkedin.com/in/yourprofile)
[![GitHub](https://img.shields.io/badge/GitHub-Follow-100000?style=for-the-badge&logo=github)](https://github.com/yourusername)
[![Twitter](https://img.shields.io/badge/Twitter-Follow-1DA1F2?style=for-the-badge&logo=twitter)](https://twitter.com/yourhandle)

---

## 📄 License

MIT License - Feel free to use for learning and portfolio purposes with attribution.

---

**⭐ Star this repo if you found it helpful!**

*Week 3 Complete • September 2026 • Aditya Sharma*


# HACK4GOV 2026 

**Competition:** Hack4Gov 2026 (October)
**Organizer:** DICT Philippines

## Quick Start

1. Identify the challenge category
2. Open `Tools/<category>/README.md`
3. Run the first command in the decision tree
4. Follow the tree until you get the flag
5. Commit your solve to `Writeups/<category>/`

## Categories

| Category | Focus |
|----------|-------|
| Crypto | Ciphers, RSA, AES, hashing |
| Forensics | Memory, disk, network |
| Reversing | Binary analysis |
| Stego | Image, audio, file |
| Web | OWASP Top 10, APIs |

## One-Time Setup

    sudo apt update
    sudo apt install -y curl wget git python3 python3-pip \
        exiftool steghide binwalk foremost sleuthkit \
        wireshark tshark hashcat john ffuf gobuster nmap \
        gdb radare2 hexedit xxd file seclists

## Team Workflow

- Before: Install tools, read playbook
- During: Follow decision trees
- After: Commit writeups

---

## Scoring System - Official Hack4Gov 2026

| Point Range | Difficulty | Time Budget |
|-------------|------------|-------------|
| 1-30 points | Easy | 5-10 min |
| 31-70 points | Moderate | 15-25 min |
| 71-100 points | Hard | 30-45 min |

### Key Insight

Since maximum points per challenge is 100, the number of challenges solved matters more than the difficulty of each one.

Example:
- 10 Easy challenges = 300 points (50-100 min total)
- 3 Hard challenges = 300 points (90-135 min total)

Same score, but Easy challenges leave more time for everything else.

### Qualification Structure

The competition has two stages:
- Regional Qualifying Round - team ranking by total score
- Wildcard Slots - individual scores determine eligibility

Both individual and team performance matter.

---

## Competition Day Workflow

When a challenge drops:

Step 1: Identify the category
- Look at file extension (.pcap, .jpg, .exe, .zip)
- Read the challenge description for hints
- Check the point value

Step 2: Open the category playbook
- Web: Tools/Web/README.md
- Forensics: Tools/Forensics/README.md
- Crypto: Tools/Crypto/README.md
- Reversing: Tools/Reversing/README.md
- Stego: Tools/Stego/README.md

Step 3: Run the first command in the decision tree

Step 4: Follow the tree until you get the flag

Step 5: Submit immediately

Step 6: Log your solve in Writeups/<category>/

### The 15-Minute Rule

If a challenge takes over 15 minutes with no progress:
- Move to another challenge
- Come back with fresh eyes later
- Share with a teammate
- Do not tunnel vision on a single problem

---

## Repository Structure

HACK4GOV-PREP/
├── README.md                  (this file)
├── Challenges/                (practice challenges solved)
├── Learning-Resources/        (tutorials and references)
├── Tools/                     (tool playbooks)
│   ├── Crypto/README.md
│   ├── Forensics/README.md
│   ├── Reversing/README.md
│   ├── Stego/README.md
│   └── Web/README.md
└── Writeups/                  (competition writeups)

---

## Pre-Competition Setup

Run the night before.

Step 1 - Update system:
    sudo apt update && sudo apt upgrade -y

Step 2 - Install essential tools:
    sudo apt install -y \
        curl wget git python3 python3-pip \
        exiftool steghide binwalk foremost sleuthkit \
        wireshark tshark hashcat john ffuf gobuster nmap netcat-openbsd \
        gdb radare2 hexedit xxd file ruby-full zlib1g-dev \
        sonic-visualiser audacity p7zip-full unzip zip \
        pdfgrep poppler-utils

Step 3 - Install wordlists:
    sudo apt install -y seclists

Step 4 - Install Python tools:
    pip3 install pwntools pycryptodome requests beautifulsoup4

Step 5 - Install Go tools:
    go install github.com/projectdiscovery/subfinder/v2/cmd/subfinder@latest
    go install github.com/projectdiscovery/httpx/cmd/httpx@latest
    go install github.com/projectdiscovery/nuclei/v3/cmd/nuclei@latest

Step 6 - Install zsteg:
    sudo gem install zsteg

Step 7 - Verify:
    for tool in ffuf gobuster nmap binwalk exiftool steghide \
                hashcat john radare2 gdb python3 pip3 \
                tshark wireshark ffmpeg 7z zsteg; do
      if which $tool > /dev/null 2>&1; then
        echo "[OK] $tool"
      else
        echo "[MISSING] $tool"
      fi
    done

---

## Team Roles

Suggested setup for 4-5 members:

| Role | Responsibility | Focus |
|------|----------------|-------|
| Captain | Decision maker, time keeper | All |
| Web Lead | Web vulnerabilities | SQLi, XSS, IDOR |
| Crypto Lead | Cryptographic challenges | Ciphers, RSA |
| Forensics Lead | Digital forensics | PCAP, memory |
| Stego Lead | Steganography | Images, audio |
| Reversing Lead | Binary analysis | ELF, APK |


## Daily Git Workflow

Morning routine:
    cd ~/HACK4GOV-PREP
    git pull
    git log --oneline --since="12 hours ago"

After every solve:
    git add Writeups/<category>/<challenge>.md
    git commit -m "Solve: <challenge-name>"
    git push

Every 30 minutes:
    git pull

End of day:
    git add .
    git commit -m "End of day summary"
    git push
    git log --oneline --since="today"

---

## Challenge Solve Workflow

Before you start:
1. Copy challenge to notes app
2. Set 15-minute timer
3. Open category playbook
4. Open fresh terminal

During the solve:
1. Follow the decision tree
2. Document every command
3. Screenshot interesting output
4. Check challenge description again if stuck
5. Ask teammates for help

After the solve:
1. Submit flag immediately
2. Copy solve path to writeup template
3. Commit writeup to Git
4. Share flag in team chat

### Writeup Template

Save as Writeups/<category>/<challenge>.md:

    ## Challenge: <name>
    - Category: Web
    - Source: Hack4Gov 2026
    - Points: 45
    - Time: 12 minutes
    - Flag: flag{...}

    ### Description
    <copy from challenge>

    ### Initial Analysis
    <what you first noticed>

    ### Solution
    1. Step 1
    2. Step 2
    3. Step 3

    ### Commands Used
    - command 1
    - command 2

    ### Tools Used
    - ffuf
    - Burp Suite

    ### Lessons Learned
    - what worked
    - what did not

---

## Time Management

The 15-Minute Rule:
- If a challenge takes over 15 min with no progress, move on
- Come back after solving 2 other challenges
- Fresh perspective often solves it

Priority order based on points:
1. Easy challenges (1-30 points) - target 5-10 min each
2. Moderate challenges (31-70 points) - target 15-25 min each
3. Hard challenges (71-100 points) - target 30-45 min each

Time budget for 10-hour competition:
- 3 hours: Easy challenges (target: 15+ solves)
- 4 hours: Moderate challenges (target: 6+ solves)
- 2 hours: Hard challenges (target: 2-3 solves)
- 1 hour: Final pushes and cleanup

### Points Optimization Strategy

Total potential points from Easy challenges alone:
- 20 Easy challenges at 30 points = 600 points

This beats:
- 6 Hard challenges at 100 points = 600 points

But Easy challenges take half the time, leaving room for more.

Always prioritize Easy challenges when time is limited.

---

## Communication Protocol

Team chat rules:
1. Post challenge name before asking for help
2. Post current progress or stuck point
3. Post exact command or output
4. Answer teammate questions when you can

Screenshot when:
- Unusual error messages
- Suspicious file contents
- Hidden data in output
- Unexpected web behavior

Paste as text when:
- Commands you ran
- Copy-pasteable output
- URLs or file paths

Hint exchange:
- Share hints freely
- Do not solve for teammates unless asked
- Explain reasoning, not just the answer

---

## Competition Checklists

Before competition:
- All tools installed and verified
- Wordlists in /usr/share/seclists/
- Team chat open and active
- Repo cloned and pulled
- Fresh terminals ready
- Snacks and water nearby
- Phones charged
- Backup internet (mobile hotspot)
- Timer app ready

During competition:
- Submit flags immediately
- Screenshot unusual things
- Rotate every 15 minutes
- Share hints
- Track solved/unsolved in shared doc
- Update playbook with new techniques

After competition:
- Commit all writeups
- Push to GitHub
- Debrief with team
- Note improvements for next time

---

## Category Deep Dives

### Web Challenges

Vulnerability classes:
1. SQL Injection - test every parameter with a single quote
2. Cross-Site Scripting - inject script tags into inputs
3. IDOR - change numeric IDs to see other users data
4. Local File Inclusion - try ../../../../etc/passwd
5. Server-Side Request Forgery - test URLs with 127.0.0.1

Key tools:
- curl for manual testing
- Burp Suite for interception
- ffuf for directory discovery
- sqlmap for automated SQLi

### Forensics Challenges

File types:
- .pcap - open in Wireshark, extract objects
- .raw / .mem - use Volatility 3
- .img / .dd - mount read-only, use Sleuth Kit
- .jpg / .png - run exiftool and strings first
- .pdf - use pdftotext, pdfimages
- .zip / .rar - check for passwords with john

Key tools:
- Wireshark, tshark
- Volatility 3
- exiftool
- binwalk
- steghide

### Crypto Challenges

Step-by-step:
1. Identify encoding (base64, hex, binary)
2. Try classical ciphers (Caesar, Vigenere)
3. For RSA: factor n with FactorDB
4. For hashes: hashcat with rockyou
5. For unknown: CyberChef magic mode

Key tools:
- CyberChef (web-based)
- hashcat, john
- RsaCtfTool
- Python with pycryptodome

### Reversing Challenges

Step-by-step:
1. Run file and strings on the binary
2. Open in radare2 for quick disassembly
3. Use Ghidra for decompilation
4. Use gdb with pwndbg for dynamic analysis
5. Look for strcmp calls and comparison loops

Key tools:
- Ghidra
- radare2
- gdb with pwndbg
- pwntools

### Stego Challenges

Step-by-step:
1. Always run exiftool first
2. Always run strings
3. Always run binwalk -e
4. For PNG: use zsteg
5. For JPG: try steghide
6. For audio: check spectrogram in Audacity

Key tools:
- exiftool
- binwalk
- steghide
- zsteg
- Audacity
- AperiSolve (web-based)

---

## Essential Links

General:
- CyberChef: https://gchq.github.io/CyberChef/
- HackTricks: https://book.hacktricks.xyz/
- PayloadsAllTheThings: https://github.com/swisskyrepo/PayloadsAllTheThings
- SecLists: https://github.com/danielmiessler/SecLists

Category-specific:
- Crypto - CryptoHack: https://cryptohack.org/
- Forensics - CyberDefenders: https://cyberdefenders.org/
- Reversing - pwn.college: https://pwn.college/
- Stego - AperiSolve: https://www.aperisolve.com/
- Web - PortSwigger: https://portswigger.net/web-security

Practice platforms:
- TryHackMe: https://tryhackme.com/
- HackTheBox: https://www.hackthebox.com/
- picoCTF: https://picoctf.org/
- CTFlearn: https://ctflearn.com/

---

## Competition Strategy

Stage 1 - Warm Up (First 30 min):
- Focus: Easy crypto and stego challenges (1-30 points)
- Goal: Build momentum and claim easy points
- Time per challenge: 5-10 min

Stage 2 - Main Push (Middle hours):
- Focus: Web and forensics challenges (1-70 points)
- Goal: Accumulate the bulk of team score
- Time per challenge: 15-30 min

Stage 3 - Moderate to Hard (Later middle):
- Focus: Moderate to hard challenges (31-100 points)
- Goal: Harder point values
- Time per challenge: 30-45 min

Stage 4 - Hail Mary (Last hour):
- Focus: Unsolved challenges
- Goal: Last-minute points
- Time per challenge: 5-10 min

Scoring priorities:
1. Points per minute - Easy challenges give best ROI
2. Number of solves - 10 Easy beats 3 Hard
3. Team average - ensure every member solves
4. Individual score for Wildcard eligibility

---

## Post-Competition Protocol

Immediate (first hour):
- Screenshot final scoreboard
- Save unsolved challenge files
- Export team chat history
- Thank teammates

Short term (first day):
- Complete all writeups
- Push to GitHub
- Update playbook with new techniques
- List what worked and what did not

Long term (week after):
- Study unsolved challenges
- Practice missed techniques
- Update playbook
- Plan for next competition

---

## Team Principles

Core principles:
1. No ego - share hints, share glory
2. Time is precious - 15 min max per challenge
3. Document everything - even unsolved
4. Celebrate wins - every flag counts
5. Learn from losses - post-mortem every time
6. Help teammates - rising tide lifts all boats
7. Respect the playbook
8. Update the playbook

Team rules:
1. No flag submission without verification
2. No solo work - share progress every 30 min
3. No giving up before asking for help
4. No skipping writeups
5. No credit claiming - we win together

---

## Troubleshooting

Tools not found:
    sudo apt install -y <tool-name>
    pip3 install <python-package>
    sudo gem install <ruby-gem>
    go install <go-package>@latest

Git push fails:
    # Generate Personal Access Token at:
    # https://github.com/settings/tokens
    # Scopes needed: repo (full control)
    git config --global credential.helper store

Wordlists missing:
    sudo apt update
    sudo apt install -y seclists
    ls /usr/share/seclists/Discovery/Web-Content/common.txt

Network issues:
1. Check internet connection
2. Try mobile hotspot
3. Check CTF platform status
4. Notify teammates immediately

Running out of time:
1. Save all work immediately
2. Submit found flags
3. Note where you left off
4. Complete writeups after


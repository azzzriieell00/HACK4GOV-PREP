# HACK4GOV 2026 — RED TEAM PLAYBOOK


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

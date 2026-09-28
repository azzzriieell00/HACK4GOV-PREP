# Reversing Tools — Red Team Guide

## 60-Second Decision Tree

    ├── ELF binary → radare2, gdb, Ghidra
    ├── PE binary (.exe) → Ghidra
    ├── APK → apktool, jadx
    ├── .pyc → uncompyle6
    └── Just source code → Read it

## Basic Triage

    file binary
    readelf -h binary
    strings binary | grep -i "flag\|password"

## Static Analysis

    r2 binary
    # Inside r2: aaa, afl, s main, pdf, izz

## Dynamic Analysis

    gdb ./binary
    # Inside gdb: disas main, b main, run, ni, info registers
    strace ./binary
    ltrace ./binary

## APK Reversing

    apktool d app.apk
    jadx-gui app.apk
    grep -ri "flag\|password" output/

## Python Bytecode

    uncompyle6 binary.pyc > source.py

## Pwntools Template

    from pwn import *
    p = process('./binary')
    print(p.recvuntil(b'Enter:'))
    payload = b'A' * 64 + p64(0xdeadbeef)
    p.sendline(payload)
    p.interactive()

## Critical Tips
1. Run strings first
2. Run file first
3. Use Ghidra for complex binaries
4. Check for anti-debug (ptrace)

## Links
- Ghidra: https://ghidra-sre.org/
- radare2 book: https://book.rada.re/
- pwn.college: https://pwn.college/

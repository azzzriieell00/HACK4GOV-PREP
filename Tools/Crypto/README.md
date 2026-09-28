# Crypto Tools — Red Team Guide

## 60-Second Decision Tree

    ├── Letters only → Caesar / ROT
    ├── Base64-like → base64 -d
    ├── Very large numbers → RSA
    ├── Hex string → xxd -r -p
    └── Still stuck → CyberChef magic

## Encoding Identification

    echo "SGVsbG8=" | base64 -d
    echo "JBSWY3DP" | base32 -d
    echo "48656c6c6f" | xxd -r -p
    echo "Hello" | tr 'A-Za-z' 'N-ZA-Mn-za-m'

## RSA Attacks

    from Crypto.Util.number import inverse, long_to_bytes
    p = ...
    q = ...
    e = 65537
    c = ...
    n = p * q
    phi = (p-1) * (q-1)
    d = inverse(e, phi)
    m = pow(c, d, n)
    print(long_to_bytes(m))

## Hash Cracking

    hashcat -m 0 hash.txt /usr/share/wordlists/rockyou.txt
    john --wordlist=/usr/share/wordlists/rockyou.txt hash.txt

## Critical Tips
1. Try CyberChef first (Magic mode)
2. Base64 usually ends with =
3. For RSA: factor n with FactorDB
4. Rockyou.txt: /usr/share/wordlists/rockyou.txt

## Links
- CyberChef: https://gchq.github.io/CyberChef/
- dCode: https://www.dcode.fr/cipher-identifier
- FactorDB: http://factordb.com/
- RsaCtfTool: https://github.com/RsaCtfTool/RsaCtfTool

# Forensics Tools — Red Team Guide

## 60-Second Decision Tree

    ├── .pcap → tshark / Wireshark
    ├── .raw / .mem → Volatility
    ├── .img / .dd → Autopsy / Sleuth Kit
    ├── .pdf / .docx → exiftool, oletools
    ├── .jpg / .png → exiftool, strings, binwalk
    ├── .zip / .rar → john
    └── Unknown → file, strings, binwalk

## PCAP Analysis

    tshark -r capture.pcap -q -z io,phs
    tshark -r capture.pcap -Y "http.request" -T fields -e http.host -e http.request.uri
    tshark -r capture.pcap --export-objects http,extracted/

## Memory Analysis

    vol -f memory.raw windows.info
    vol -f memory.raw windows.pslist
    vol -f memory.raw windows.strings | grep -i "flag"

## Disk Images

    file disk.img
    mmls disk.img
    sudo mount -o ro,loop,offset=$((512*2048)) disk.img /mnt/forensics
    fls -r -p disk.img

## Image Analysis

    exiftool image.jpg
    strings image.jpg | grep -i flag
    binwalk -e image.jpg
    steghide extract -sf image.jpg

## PDF Analysis

    pdftotext document.pdf output.txt
    pdfgrep -i "flag" document.pdf
    exiftool document.pdf

## Critical Tips
1. Always run file first
2. Always check metadata with exiftool
3. Always run strings
4. Always try binwalk -e

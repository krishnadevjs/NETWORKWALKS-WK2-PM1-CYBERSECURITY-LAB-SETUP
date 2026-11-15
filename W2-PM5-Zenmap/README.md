# W2-PM5 — Zenmap Network Scanning

**Target:** `127.0.0.1` (local host)  
**Tool:** Zenmap / Nmap 7.98  
**Profile:** Intense scan  
**Status:** Evidence captured and documented

## Objective

Use Zenmap/Nmap to identify the state of ports and services on the local lab host, then interpret the results in context.

## Scan details

The saved Zenmap XML records the Intense scan profile and the arguments:

```bash
nmap -T4 -A -v 127.0.0.1
```

A separate service-version scan was saved with:

```bash
nmap -sV -oN results/localhost-scan.txt 127.0.0.1
```

## Recorded findings

- Host: up.
- TCP 631: open; service identified as IPP/CUPS 2.4.
- 999 other scanned TCP ports: closed.
- The Zenmap XML also reports the CUPS HTTP title as `Home - CUPS 2.4.16`.

## Evidence

- `results/localhost-scan.txt` — Nmap service-version output.
- `results/localhost-scan.xml` — Zenmap Intense scan XML.
- `screenshots/zenmap.png` — Zenmap GUI evidence.

## Scope and limitations

This was a scan of the local loopback host only. It does not represent a scan of `networkwalks.com`, another device, or the wider network. Service/version detection is based on Nmap probes and may not be a complete software inventory. No exploitation or service modification was performed.

See [../W2-PM-FINAL-Report/FINAL-REPORT.md](../W2-PM-FINAL-Report/FINAL-REPORT.md) for the consolidated analysis.

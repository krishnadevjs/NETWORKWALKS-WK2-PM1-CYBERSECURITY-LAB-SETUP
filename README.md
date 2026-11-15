# Networkwalks — Week 2 Cybersecurity Practical

> **Practical lab submission** · Footprinting · Network Scanning · Technical Reporting

This repository contains the selected Week 2 practical modules and their supporting raw outputs, screenshots, and final report.

## Project overview

Selected modules:
- **W2-PM1** — Footprinting with multiple tools (elective)
- **W2-PM5** — Zenmap-based network scanning (essential)
- **W2-PM-FINAL** — Consolidated report covering the selected practicals

## Module status

| Module | Practical | Status |
|---|---|---|
| W2-PM1 | Footprinting with six tools | Evidence committed |
| W2-PM5 | Zenmap / Nmap local-host scan | Evidence committed |
| W2-PM-FINAL | Detailed report | Draft published; student/course details to be completed |

## Repository structure

```text
.
├── README.md
├── .gitignore
├── W2-PM1-Footprinting/
│   ├── README.md
│   ├── results/
│   └── screenshots/
├── W2-PM5-Zenmap/
│   ├── README.md
│   ├── results/
│   └── screenshots/
└── W2-PM-FINAL-Report/
    └── FINAL-REPORT.md
```

## Practical scope

### W2-PM1 — Footprinting

The PM1 practical uses publicly observable information for `networkwalks.com`. Six tools were used: WHOIS, DIG, HOST, NSLOOKUP, WhatWeb and cURL. The report distinguishes raw observations from interpretation; technology fingerprints are not treated as proof of vulnerabilities.

### W2-PM5 — Zenmap network scanning

The PM5 practical scanned `127.0.0.1` (the local host). The recorded results identify TCP port 631 as IPP/CUPS 2.4 and report 999 other scanned TCP ports closed. This scan did not target `networkwalks.com` or an external network.

## Evidence and responsible-use notes

- Raw command output is retained under each module's `results/` directory.
- Screenshots are retained under each module's `screenshots/` directory.
- The captured cURL/WhatWeb cookie value is redacted in the committed text output.
- No credentials, API keys, access tokens or private keys should be committed.
- Activities are documented for coursework and authorised learning. Do not scan systems or networks without permission.

## Final report

See [W2-PM-FINAL-Report/FINAL-REPORT.md](W2-PM-FINAL-Report/FINAL-REPORT.md) for objectives, scope, methodology, findings, limitations, conclusion and evidence index.

**Submission note:** Replace the student/course placeholders in the final report and export it to PDF if required by the submission portal.

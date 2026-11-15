# Networkwalks — Week 2 Cybersecurity Practical

> **Practical lab submission** · Footprinting · Network Scanning · Technical Reporting

This repository documents the selected Week 2 cybersecurity practical modules. Each module is organised so its methodology, captured output, screenshots, and conclusions can be reviewed independently.

## Project overview

The selected work is **W2-PM1** (one elective), together with the essential **W2-PM5** practical and **W2-PM-FINAL** report. Only completed work and genuine evidence will be included.

### Module tracker

| Module | Practical | Status |
|---|---|---|
| **W2-PM1** | Footprinting with multiple Kali/Linux tools | In progress |
| **W2-PM5** | Network scanning using Zenmap | Practical run; evidence review pending |
| **W2-PM-FINAL** | Consolidated final report | Pending |

> Status is updated only after the practical work and its evidence are verified.

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
    └── REPORT-TEMPLATE.md
```

## Practical scope

### W2-PM1 — Footprinting with multiple tools

The practical uses publicly available information about the assignment domain, `networkwalks.com`, to demonstrate basic footprinting and technology identification.

Tools used/planned:

- WHOIS — domain registration information
- DIG — DNS record queries
- HOST — DNS lookups
- NSLOOKUP — DNS query verification
- WhatWeb — web technology identification
- [Add another tool only if it was actually used for this module]

The report will distinguish observed output from interpretation. Technology fingerprints and publicly visible records are **not** treated as proof of a vulnerability.

### W2-PM5 — Zenmap network scanning

The essential scanning practical uses Zenmap/Nmap to inspect the local host (`127.0.0.1`). Evidence includes the saved Zenmap scan and corresponding Nmap service-detection output. Findings are specific to this local test target and must not be interpreted as a scan of the assignment website or an external network.

### W2-PM-FINAL — Final report

The final report will cover the selected and completed modules and include:

1. Objective and scope
2. Lab environment and tools
3. Methodology and commands
4. Evidence and observations
5. Results and interpretation
6. Limitations
7. Conclusion and references

## Evidence and reporting standards

- Screenshots should clearly show the relevant tool, target, and result.
- Retain raw outputs where practical and pair them with readable explanations.
- Support findings with reproducible evidence.
- Describe failed, incomplete, or inconclusive steps honestly.
- Never commit credentials, API keys, access tokens, private keys, or unrelated personal data.
- Review screenshots and outputs for usernames, hostnames, private network details, and other information that is unnecessary for assessment.

## Responsible-use statement

All activities are intended for coursework and authorised learning. Footprinting is limited to publicly available information for the stated assignment domain. Network scanning is limited to the selected local lab target unless separate written authorisation is obtained. Do not use these procedures against systems or networks without permission.

## Submission status

This repository is a work in progress. It is ready for submission only after the evidence has been reviewed, module statuses have been verified, and the completed final report has been added.

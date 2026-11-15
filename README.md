# Networkwalks — Week 2 Cybersecurity Practical

> **Practical lab submission** · Footprinting · Network Scanning · Technical Reporting

This repository contains the documentation and evidence for the Week 2 cybersecurity practical exercises. It is organised by project module so that the methodology, command output, screenshots, and conclusions can be reviewed independently.

## Project overview

The Week 2 assignment requires the selected footprinting elective(s), the essential Zenmap network-scanning practical, and a consolidated final report. This repository will contain only work that was actually performed and evidence that was actually collected.

### Module tracker

| Module | Practical | Status |
|---|---|---|
| **W2-PM1** | Footprinting with multiple Kali/Linux tools | In progress |
| **W2-PM4** | Footprinting using theHarvester | In progress |
| **W2-PM5** | Network scanning using Zenmap | Practical run; evidence review pending |
| **W2-PM-FINAL** | Consolidated practical report | Pending |

> Status is updated as the practical work and evidence are verified. A module is not marked complete merely because its tools were installed.

## Repository structure

```text
.
├── README.md
├── W2-PM1-Footprinting/
│   ├── results/
│   └── screenshots/
├── W2-PM4-theHarvester/
│   ├── results/
│   └── screenshots/
├── W2-PM5-Zenmap/
│   ├── results/
│   └── screenshots/
└── W2-PM-FINAL-Report/
    └── (final report and supporting documents)
```

Directories and evidence files will be added as the corresponding work is reviewed and prepared for publication.

## Practical scope

### W2-PM1 — Footprinting with multiple tools

The practical uses publicly available information about the assignment domain, `networkwalks.com`, to demonstrate basic footprinting and technology identification.

Tools used/planned for the practical:

- WHOIS — domain registration information
- DIG — DNS record queries
- HOST — DNS lookups
- NSLOOKUP — DNS query verification
- WhatWeb — web technology identification
- theHarvester — passive public-source discovery

The report will distinguish observed output from interpretation. Technology fingerprints and publicly visible records are **not** treated as proof of a vulnerability.

### W2-PM4 — theHarvester

This elective documents passive information gathering with theHarvester. The report will identify the selected data source, command, observed results, and limitations. Only results actually obtained during the practical will be included.

### W2-PM5 — Zenmap network scanning

The essential scanning practical uses Zenmap/Nmap to inspect the local host (`127.0.0.1`). The evidence includes the saved Zenmap scan and corresponding Nmap service-detection output. Findings will be described in the context of this local test target; they must not be interpreted as a scan of the assignment website or an external network.

### W2-PM-FINAL — Final report

The final report will consolidate the selected and completed modules and include:

1. Objective and scope
2. Lab environment and tools
3. Methodology and commands
4. Evidence and observations
5. Results and interpretation
6. Limitations
7. Conclusion and references

## Evidence and reporting standards

- Screenshots should show the relevant tool, target, and result clearly.
- Raw outputs should be retained where practical and paired with readable explanations.
- Findings must be reproducible and supported by the included evidence.
- Failed, incomplete, or inconclusive steps must be described honestly.
- No credentials, API keys, access tokens, private keys, or unrelated personal data should be committed.
- Local machine details and network identifiers should be reviewed and redacted when they are not necessary for assessment.

## Responsible-use statement

All activities in this repository are intended for coursework and authorised learning. Footprinting is limited to publicly available information for the stated assignment domain. Network scanning is limited to the explicitly selected local lab target unless separate written authorisation is obtained. Do not use these procedures against systems or networks without permission.

## Lab environment

The practical work is being carried out on a Kali/Linux-style security lab environment. Exact tool versions, commands, and relevant configuration details will be recorded with the module evidence where available.

## Submission note

This repository is a work in progress. The final submission should be considered ready only after the practical evidence has been reviewed, the module statuses have been updated, and the final report has been added.

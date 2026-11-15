# W2-PM5 — Zenmap Network Scanning

**Target:** `127.0.0.1` (local host)
**Status:** Practical run; evidence review pending

## Objective
Use Zenmap/Nmap to identify the state of ports and services on the local lab host, then interpret the results in context.

## Evidence layout
- `results/` — Zenmap XML and Nmap text output.
- `screenshots/` — screenshots of the Zenmap interface and relevant scan output.

## Current recorded observation
The recorded service-detection output reported TCP port `631` open and identified the service as IPP/CUPS `2.4`. The scan also reported 999 closed TCP ports. Confirm these details against the saved output before final submission.

## Reporting
Include the scan profile/command, target, date, tool version, key findings, and limitations. This is a scan of the local host only; it does not represent the state of any external target or network.

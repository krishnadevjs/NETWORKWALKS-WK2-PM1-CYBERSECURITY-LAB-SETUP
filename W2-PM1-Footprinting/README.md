# W2-PM1 — Footprinting

## Objective
Perform passive and basic HTTP/DNS footprinting of `networkwalks.com` using six command-line tools.

## Tools Used
1. WHOIS — domain registration and registrar information.
2. DIG — A, NS and MX DNS records.
3. HOST — hostname and mail-exchange lookups.
4. NSLOOKUP — DNS name and address resolution.
5. WhatWeb — web technology fingerprinting.
6. cURL — HTTP response headers and status inspection.

## Key Observations
- The website returned HTTP `200 OK` during the checks.
- DNS lookups returned an A record, authoritative name servers and an MX record.
- WHOIS identified GoDaddy as the registrar and showed the domain registration dates and status codes.
- WhatWeb identified Apache and WordPress-related technologies.
- cURL confirmed the HTTP response and exposed response-header information.
- The WHOIS and DNS outputs showed different name-server values in different sources; this discrepancy is recorded rather than assumed to be an error.

## Evidence
- `results/` contains command output.
- `screenshots/` contains screenshots of the practical work.

## Scope and Limitations
The work was limited to the specified domain and publicly available information. Technology fingerprinting and exposed response headers are observations, not proof of vulnerabilities. No exploitation or intrusive testing was performed.

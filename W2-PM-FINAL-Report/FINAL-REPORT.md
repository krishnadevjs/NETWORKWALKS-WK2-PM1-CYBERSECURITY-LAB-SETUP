# Week 2 Cybersecurity Practical — Final Report

**Student:** [Enter your full name]  
**Course / Programme:** [Enter course or programme]  
**Practical date:** 15 November 2026  
**Repository:** https://github.com/krishnadevjs/NETWORKWALKS-WK2-PM1-CYBERSECURITY-LAB-SETUP

---

## Executive Summary

This report documents the selected Week 2 practical modules: **W2-PM1 — Footprinting with Multiple Tools** and **W2-PM5 — Zenmap Network Scanning**. Six command-line tools were used to collect publicly observable domain, DNS and HTTP information for `networkwalks.com`. Zenmap/Nmap was then used separately to scan the local lab host, `127.0.0.1`.

The footprinting checks observed an HTTP `200 OK` response, DNS A/NS/MX records, GoDaddy registrar information, and Apache/WordPress-related technology indicators. The local scan found TCP port 631 open and identified IPP/CUPS 2.4; 999 other scanned TCP ports were reported closed. These are observations from the captured outputs, not evidence that the external website is vulnerable.

## 1. Objectives

1. Practise passive and low-impact footprinting using multiple Kali/Linux tools.
2. Identify publicly visible domain-registration, DNS, HTTP and web-technology information.
3. Use Zenmap/Nmap to identify open ports and services on a controlled local target.
4. Preserve command output and screenshots so that the work can be reviewed and reproduced.

## 2. Scope, Rules and Authorisation Context

### W2-PM1 target
- Domain: `networkwalks.com`
- Activity: WHOIS, DNS queries, HTTP response-header inspection and technology fingerprinting.
- Scope: publicly observable information for the assignment domain.

### W2-PM5 target
- Host: `127.0.0.1` (the local machine).
- Activity: Zenmap Intense scan and a separate Nmap service-version scan.
- Scope: local loopback interface only. This scan did **not** scan `networkwalks.com`, another host, or an external network.

The practical evidence records the targets and actions performed. This report does not claim that a separate written authorisation letter was obtained. No exploitation, credential attacks, denial-of-service testing, or attempts to access restricted data were performed.

## 3. Lab Environment

| Component | Recorded detail |
|---|---|
| Operating system | Ubuntu 26.04.1 LTS |
| DNS utility | DiG 9.20.24-1ubuntu0.5-Ubuntu |
| Network scanner | Nmap 7.98 |
| GUI | Zenmap |
| Local scan target | 127.0.0.1 |
| External footprinting target | networkwalks.com |
| Practical evidence date | 15 November 2026 |

Only tool and environment details supported by the saved evidence or recorded lab context are included. Exact versions for WHOIS, HOST, NSLOOKUP, WhatWeb and cURL were not captured in the evidence set.

## 4. W2-PM1 — Footprinting with Multiple Tools

### 4.1 WHOIS

**Purpose:** Retrieve public domain-registration and registrar information.

**Target:** `networkwalks.com`

**Observed results:**
- Registrar: GoDaddy.com, LLC.
- Registry creation date: 6 November 2019.
- Registry expiry date: 6 November 2027.
- Domain status included clientDeleteProhibited, clientRenewProhibited, clientTransferProhibited and clientUpdateProhibited.
- DNSSEC was reported as unsigned.
- The registry output listed `NS6135.HOSTGATOR.COM` and `NS6136.HOSTGATOR.COM`.

The registrar WHOIS portion of the same saved output also listed `NS29.DOMAINCONTROL.COM` and `NS30.DOMAINCONTROL.COM`. This differs from the registry name-server list and from the DNS response captured during the practical. The discrepancy is reported as observed; this exercise did not establish its cause.

**Evidence:** `W2-PM1-Footprinting/results/whois.txt`; `screenshots/whois.png`.

### 4.2 DIG

**Purpose:** Query DNS records directly and inspect the returned answers.

**Queries performed:** A, NS and MX records for `networkwalks.com`.

| Record | Observed answer |
|---|---|
| A | `192.232.216.135` |
| NS | `ns6136.hostgator.com`, `ns6135.hostgator.com` |
| MX | Priority 0, `mail.networkwalks.com` |

All three saved DiG outputs reported `NOERROR`. The A record had a TTL of 14400 seconds; the NS records had a TTL of 21600 seconds; and the MX record had a TTL of 14400 seconds.

**Evidence:** `results/dns-a.txt`, `results/dns-ns.txt`, `results/dns-mx.txt`; `screenshots/dig.png`.

### 4.3 HOST

**Purpose:** Perform hostname and mail-exchange lookups as an additional DNS cross-check.

**Observed results:** The saved output returned the domain's address and the MX destination. The initial host lookup recorded a communication timeout to the local DNS stub resolver before returning a result; the separate MX lookup succeeded. This transient resolver behaviour is retained in the evidence rather than omitted.

**Evidence:** `results/host.txt`, `results/host-mx.txt`; `screenshots/host.png`.

### 4.4 NSLOOKUP

**Purpose:** Resolve the domain and query its name-server records using another DNS client.

**Observed results:** The saved output returned the domain address and name-server information, providing a second client-side view of DNS resolution.

**Evidence:** `results/nslookup.txt`, `results/nslookup-ns.txt`; `screenshots/nslookup.png`.

### 4.5 WhatWeb

**Purpose:** Identify web technologies from publicly visible HTTP responses and page characteristics.

**Observed results:**
- HTTP status: `200 OK`.
- Page title: `Networkwalks Academy`.
- Server indicator: Apache.
- Technology indicators included WordPress 7.1.4, WordPress Download Manager 3.3.76, Bootstrap 7.1.4, jQuery 3.7.1, HTML5 and Google Tag Manager.
- WhatWeb identified the `__wpdm_client` cookie and reported the HttpOnly attribute.
- The scan identified publicly visible contact and metadata information.

Technology versions reported by a fingerprinting tool are indicators derived from observable responses; they are not independently verified software inventory. A detected technology or version does not, by itself, establish a vulnerability. The cookie value has been redacted in the committed output.

**Evidence:** `results/whatweb.txt`; `screenshots/whatweb.png`.

### 4.6 cURL

**Purpose:** Inspect the HTTP response status and response headers without downloading the page body.

**Command recorded for the practical:**

```bash
curl -sS -D results/curl-headers.txt -o /dev/null https://networkwalks.com
```

**Observed results:**
- HTTP status: `200 OK`.
- Server header: Apache.
- Content type: `text/html; charset=UTF-8`.
- Headers included a WordPress REST API link, Referrer-Policy, X-Endurance-Cache-Level and X-nginx-cache.
- A `__wpdm_client` cookie was present; its value is redacted in the committed evidence.

These headers describe the response observed at the time of testing. They are not, without further validation, proof of a security weakness.

**Evidence:** `results/curl-headers.txt`; `screenshots/curl.png`.

### 4.7 W2-PM1 Interpretation

The six tools provided complementary views of registration data, DNS records, HTTP behaviour and technology indicators. The A, NS and MX records were returned successfully by DiG. WHOIS and DNS outputs did not show identical name-server lists, so the report preserves the discrepancy rather than assuming that one source is definitive. The HTTP checks returned `200 OK`, and WhatWeb identified Apache and WordPress-related components. No vulnerability was demonstrated by these footprinting observations.

## 5. W2-PM5 — Zenmap Network Scanning

### 5.1 Objective and target

Zenmap was used to run the **Intense scan** profile against `127.0.0.1`. The target was the local machine's loopback address.

### 5.2 Scan details

The saved Zenmap XML records the profile as `Intense scan` and the Nmap arguments as:

```bash
nmap -T4 -A -v 127.0.0.1
```

A separate service-version scan was also saved:

```bash
nmap -sV -oN results/localhost-scan.txt 127.0.0.1
```

The Nmap version recorded in the XML and text output was 7.98.

### 5.3 Results

| Port | State | Service | Version / identification |
|---|---|---|---|
| TCP 631 | Open | IPP | CUPS 2.4 |

The service scan reported 999 closed TCP ports among the 1000 scanned TCP ports. The Zenmap XML also recorded the CUPS HTTP title as `Home - CUPS 2.4.16` and the server header as `CUPS/2.4 IPP/2.1`.

### 5.4 Interpretation

The local host was reachable over loopback. TCP port 631 was accepting connections and was identified as the Internet Printing Protocol (IPP) service provided by CUPS. The other 999 scanned TCP ports were reported closed in the captured scan. This is a local machine observation; it must not be generalised to the external assignment domain or to other devices on the network.

If printing is not required on this machine, the CUPS service can be reviewed and disabled through normal system administration. No service changes were made as part of this practical.

**Evidence:** `W2-PM5-Zenmap/results/localhost-scan.txt`, `results/localhost-scan.xml`; `screenshots/zenmap.png`.

## 6. Consolidated Findings

| Module | Observation | Evidence | Interpretation |
|---|---|---|---|
| PM1 — WHOIS | GoDaddy registrar; registration dates and status codes returned | `results/whois.txt` | Public registration information was available; registrar and registry name-server lists differed |
| PM1 — DNS | A, NS and MX answers returned with NOERROR | `results/dns-*.txt` | Domain resolution information was observable |
| PM1 — HTTP | HTTP 200 OK; Apache response header | `results/curl-headers.txt` | The website responded successfully during the check |
| PM1 — Fingerprinting | Apache and WordPress-related indicators detected | `results/whatweb.txt` | Technology indicators only; not proof of vulnerabilities |
| PM5 — Local scan | TCP 631 open, IPP/CUPS 2.4; 999 TCP ports closed | `results/localhost-scan.*` | Local printing service was exposed on loopback during the scan |

## 7. Limitations and Data Quality

- Results are a point-in-time snapshot from 15 November 2026 and may change.
- DNS answers can vary with resolver, caching, delegation state and timing.
- The WHOIS output contains different name-server lists in its registry and registrar sections; the practical did not investigate the operational reason.
- The initial HOST lookup recorded a resolver communication timeout before returning data.
- WhatWeb technology and version identification is fingerprint-based and may be incomplete or inaccurate.
- The Zenmap/Nmap scan covered the local loopback host only. It does not describe the external website or the wider network.
- The evidence set does not include exact versions for every PM1 utility.
- No exploitation or vulnerability validation was conducted; therefore no confirmed vulnerability is claimed.

## 8. Conclusion

The selected Week 2 practicals demonstrated how multiple tools can be combined to collect and cross-check publicly visible domain, DNS and HTTP information, and how Zenmap/Nmap can identify services on a local host. PM1 produced registration, DNS, HTTP and technology-fingerprint observations for `networkwalks.com`. PM5 identified a local CUPS/IPP service on TCP port 631 at `127.0.0.1`.

The main learning outcome was the importance of interpreting tool output in context, retaining reproducible evidence, and distinguishing an observation from a confirmed security issue. The two practicals used different targets and their findings have been kept separate throughout this report.

## 9. References

- Week 2 project brief supplied for the practical: *WK2 - Week2 Projects* (module selection and final-report requirement).
- Nmap documentation: https://nmap.org/book/man.html
- WhatWeb project: https://github.com/urbanadventurer/WhatWeb
- DiG / BIND utilities documentation: https://bind9.readthedocs.io/
- cURL documentation: https://curl.se/docs/

## Appendix A — Evidence Index

### W2-PM1 — Footprinting

| Evidence path | Description |
|---|---|
| `results/whois.txt` | Domain registration and registrar output |
| `results/dns-a.txt` | DiG A-record response |
| `results/dns-ns.txt` | DiG NS-record response |
| `results/dns-mx.txt` | DiG MX-record response |
| `results/host.txt` | HOST lookup output |
| `results/host-mx.txt` | HOST MX lookup output |
| `results/nslookup.txt` | NSLOOKUP domain resolution |
| `results/nslookup-ns.txt` | NSLOOKUP name-server query |
| `results/whatweb.txt` | Web technology fingerprint output |
| `results/curl-headers.txt` | HTTP response headers (cookie value redacted) |
| `screenshots/whois.png` | WHOIS terminal evidence |
| `screenshots/dig.png` | DiG terminal evidence |
| `screenshots/host.png` | HOST terminal evidence |
| `screenshots/nslookup.png` | NSLOOKUP terminal evidence |
| `screenshots/whatweb.png` | WhatWeb terminal evidence |
| `screenshots/curl.png` | cURL terminal evidence |

### W2-PM5 — Zenmap

| Evidence path | Description |
|---|---|
| `results/localhost-scan.txt` | Nmap service-version scan output |
| `results/localhost-scan.xml` | Zenmap Intense scan XML output |
| `screenshots/zenmap.png` | Zenmap GUI scan evidence |

---

**Before submission:** Replace the student and course placeholders, confirm that the screenshots are legible, and export this Markdown report to PDF if the submission portal requires PDF format.

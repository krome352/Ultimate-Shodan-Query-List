# 🔎 Shodan Filter Masterlist

> A structured reference to Shodan search filters, query syntax, network metadata, HTTP, SSL/TLS, SSH, and defensive attack-surface discovery.

![Shodan](https://img.shields.io/badge/Shodan-Search%20Reference-1f6feb?style=for-the-badge)
![Markdown](https://img.shields.io/badge/Format-GitHub%20Markdown-181717?style=for-the-badge)
![Purpose](https://img.shields.io/badge/Focus-OSINT%20%26%20Asset%20Discovery-238636?style=for-the-badge)

---

## 📑 Table of Contents

- [Overview](#-overview)
- [Query Syntax](#-query-syntax)
- [General Filters](#-general-filters)
- [Network and Location Filters](#-network-and-location-filters)
- [Software and Vulnerability Filters](#-software-and-vulnerability-filters)
- [HTTP Filters](#-http-filters)
- [SSL/TLS Filters](#-ssltls-filters)
- [SSH Filters](#-ssh-filters)
- [Screenshot Filters](#-screenshot-filters)
- [Useful Search Queries](#-useful-search-queries)
- [Filter Discovery Through the API](#-filter-discovery-through-the-api)
- [Important Notes](#-important-notes)
- [Official Documentation](#-official-documentation)

---

## 📖 Overview

Shodan indexes information collected from internet-connected services. Its search engine lets you query service banners and associated metadata using filters.

A filter follows this general format:

```text
filter:value
```

Example:

```text
port:443 country:US
```

This query combines two conditions: port `443` and country code `US`.

**Important:** Shodan has multiple products and datasets. A filter available in Shodan Search may not be available in Shodan Trends. The reference below separates documented Trends filters from other commonly used Search filters.

---

## 🧠 Query Syntax

| Syntax | Example | Purpose |
|:---|:---|:---|
| `filter:value` | `port:443` | Filter by a specific property |
| `"..."` | `org:"Example Corporation"` | Quote values containing spaces |
| `,` | `product:Apache,nginx` | Match alternative values for a filter |
| `>` | `port:>1024` | Numeric greater-than comparison |
| `<` | `port:<1024` | Numeric less-than comparison |
| `>=` | `port:>=1024` | Numeric greater-than or equal comparison, where supported |
| `<=` | `port:<=1024` | Numeric less-than or equal comparison, where supported |

Multiple filters can be combined to narrow results:

```text
country:US port:443 product:nginx
```

Shodan's documented syntax supports comma-separated alternatives and numeric ranges. Check the official query guide for additional syntax details.

---

## 🌐 General Filters

| Filter | Example | Description |
|:---|:---|:---|
| `all` | `all:"example"` | Search across supported indexed fields |
| `asn` | `asn:AS15169` | Autonomous system number |
| `city` | `city:"Atlanta"` | City |
| `country` | `country:US` | Two-letter country code |
| `cpe` | `cpe:"cpe:/a:vendor:product"` | Common Platform Enumeration identifier |
| `has_ipv6` | `has_ipv6:true` | IPv6-related metadata |
| `hash` | `hash:123456789` | Service banner hash |
| `hostname` | `hostname:example.com` | Hostname |
| `ip` | `ip:203.0.113.10` | IP address |
| `isp` | `isp:"Example ISP"` | Internet service provider |
| `net` | `net:203.0.113.0/24` | Network range in CIDR notation |
| `org` | `org:"Example Organization"` | Organization |
| `os` | `os:Linux` | Identified operating system |
| `port` | `port:443` | Service port |
| `product` | `product:nginx` | Detected product |
| `region` | `region:"California"` | Region, where supported |
| `state` | `state:CA` | State metadata, where supported |
| `tag` | `tag:cloud` | Shodan tag |
| `version` | `version:1.2.3` | Detected software version |
| `has_ssl` | `has_ssl:true` | SSL-related metadata |
| `has_screenshot` | `has_screenshot:true` | Results with screenshot data |
| `vuln` | `vuln:CVE-2024-0000` | Match a specified vulnerability identifier, where supported |
| `has_vuln` | `has_vuln:true` | Vulnerability-related metadata |

---

## 📍 Network and Location Filters

| Filter | Example | Description |
|:---|:---|:---|
| `ip` | `ip:203.0.113.10` | Match an IP address |
| `net` | `net:203.0.113.0/24` | Match a CIDR range |
| `asn` | `asn:AS15169` | Match an autonomous system |
| `org` | `org:"Example Corporation"` | Match an organization |
| `isp` | `isp:"Example ISP"` | Match an ISP |
| `hostname` | `hostname:example.com` | Match a hostname |
| `country` | `country:GB` | Match a country code |
| `city` | `city:"London"` | Match a city |
| `state` | `state:NY` | Match state metadata |
| `region` | `region:"New York"` | Match region metadata |

### Common port reference

| Port | Common service |
|---:|:---|
| `21` | FTP |
| `22` | SSH |
| `25` | SMTP |
| `53` | DNS |
| `80` | HTTP |
| `110` | POP3 |
| `143` | IMAP |
| `443` | HTTPS |
| `445` | SMB |
| `587` | SMTP submission |
| `993` | IMAPS |
| `995` | POP3S |
| `1433` | Microsoft SQL Server |
| `3306` | MySQL |
| `3389` | RDP |
| `5432` | PostgreSQL |
| `5900` | VNC |
| `6379` | Redis |
| `8080` | Alternate HTTP |
| `8443` | Alternate HTTPS |
| `9200` | Elasticsearch, commonly |

> A port number alone does not prove which service is running. Validate the returned banner and protocol metadata.

---

## 🧩 Software and Vulnerability Filters

| Filter | Example | Description |
|:---|:---|:---|
| `product` | `product:OpenSSH` | Match a detected software product |
| `version` | `version:9.0` | Match a reported software version |
| `os` | `os:Linux` | Match operating-system metadata |
| `cpe` | `cpe:"cpe:/a:vendor:product"` | Match a CPE identifier |
| `vuln` | `vuln:CVE-2024-0000` | Search for vulnerability-related records |
| `has_vuln` | `has_vuln:true` | Match records with vulnerability metadata |

### Example queries

```text
product:nginx
```

```text
product:OpenSSH version:9.0
```

```text
cpe:"cpe:/a:vendor:product"
```

```text
has_vuln:true
```

**Interpretation note:** A reported version or vulnerability match is not proof that a device is exploitable. Confirm the software, configuration, patch status, and applicability before drawing conclusions.

---

## 🌍 HTTP Filters

| Filter | Example | Description |
|:---|:---|:---|
| `http.component` | `http.component:WordPress` | Detected web component |
| `http.component_category` | `http.component_category:CMS` | Web component category |
| `http.favicon.hash` | `http.favicon.hash:123456789` | Favicon hash |
| `http.html_hash` | `http.html_hash:123456789` | Indexed HTML hash |
| `http.robots_hash` | `http.robots_hash:123456789` | `robots.txt` hash |
| `http.securitytxt` | `http.securitytxt:true` | Security.txt-related metadata |
| `http.status` | `http.status:200` | HTTP status code |
| `http.title` | `http.title:"Login"` | Page title |
| `http.waf` | `http.waf:Cloudflare` | Detected web application firewall |

### Example queries

```text
http.title:"Login"
```

```text
http.status:403
```

```text
http.component:WordPress
```

```text
http.waf:Cloudflare
```

```text
http.securitytxt:true
```

---

## 🔐 SSL/TLS Filters

| Filter | Example | Description |
|:---|:---|:---|
| `ssl` | `ssl:example.com` | Search supported SSL/TLS fields |
| `ssl.alpn` | `ssl.alpn:h2` | Application-Layer Protocol Negotiation |
| `ssl.version` | `ssl.version:TLSv1.3` | Reported TLS version |
| `ssl.cert.fingerprint` | `ssl.cert.fingerprint:abcdef123456` | Certificate fingerprint |
| `ssl.cert.issuer.cn` | `ssl.cert.issuer.cn:"Example CA"` | Certificate issuer common name |
| `ssl.cert.subject.cn` | `ssl.cert.subject.cn:example.com` | Certificate subject common name |
| `ssl.cert.serial` | `ssl.cert.serial:123456789` | Certificate serial number |
| `ssl.jarm` | `ssl.jarm:examplehash` | JARM fingerprint |
| `ssl.ja3s` | `ssl.ja3s:examplehash` | JA3S fingerprint |

### Example queries

```text
ssl.cert.subject.cn:example.com
```

```text
ssl.cert.issuer.cn:"Example CA"
```

```text
ssl.version:TLSv1.3
```

```text
ssl.alpn:h2
```

> Certificate and fingerprint matching depends on indexed metadata and the exact filter implementation.

---

## 🔑 SSH Filters

| Filter | Example | Description |
|:---|:---|:---|
| `ssh.fingerprint` | `ssh.fingerprint:"SHA256:example"` | Match an SSH host-key fingerprint |

Example:

```text
ssh.fingerprint:"SHA256:example"
```

Use fingerprints for authorized asset correlation and inventory work. A fingerprint match alone does not establish the identity or trustworthiness of a host.

---

## 🖼️ Screenshot Filters

| Filter | Example | Description |
|:---|:---|:---|
| `has_screenshot` | `has_screenshot:true` | Find records with screenshot data |
| `screenshot.label` | `screenshot.label:desktop` | Match a screenshot classification label |

Example:

```text
has_screenshot:true
```

Screenshot availability and supported labels depend on the relevant Shodan product and dataset.

---

## 🔎 Useful Search Queries

The following are examples for learning query composition and conducting authorized inventory research. Replace example values with assets you own or are permitted to assess.

### 1. Search by hostname

```text
hostname:example.com
```

### 2. Search by domain

```text
domain:example.com
```

### 3. Search by organization

```text
org:"Example Organization"
```

### 4. Search HTTPS services

```text
port:443
```

### 5. Search for a web technology

```text
product:nginx
```

### 6. Search HTTP metadata

```text
http.title:"Dashboard"
```

### 7. Search certificate metadata

```text
ssl.cert.subject.cn:example.com
```

### 8. Combine multiple filters

```text
hostname:example.com port:443
```

### 9. Search screenshot-bearing records

```text
has_screenshot:true
```

### 10. Search vulnerability metadata

```text
has_vuln:true
```

---

## 🧰 Filter Discovery Through the API

**This is the authoritative way to obtain the live filter list for your account and the selected Shodan API product.**

Shodan documents the Search API endpoint:

```text
GET https://api.shodan.io/shodan/host/search/filters?key=YOUR_API_KEY
```

The Trends API has its own filter endpoint:

```text
GET https://trends.shodan.io/api/v1/search/filters?key=YOUR_API_KEY
```

These endpoints return filter names, not a complete tutorial for every filter. Use the corresponding product's documentation to learn each filter's supported values.

### Retrieve the main Search API filter list

Using `curl` with an API key stored in an environment variable:

```bash
curl -sS \
  "https://api.shodan.io/shodan/host/search/filters?key=${SHODAN_API_KEY}"
```

Set `SHODAN_API_KEY` in your local environment before running the command. Do not commit API keys to GitHub.

### Retrieve the Trends filter list

```bash
curl -sS \
  "https://trends.shodan.io/api/v1/search/filters?key=${SHODAN_API_KEY}"
```

> **Important:** The main Search API and Trends API expose different filter sets. Do not combine their results and label the combined list as universally supported.

---

## ⚠️ Important Notes

- Shodan indexes observed service information; results may be outdated.
- Filter availability can differ by product, dataset, and account permissions.
- A filter name appearing in one API does not guarantee that it works in every Shodan interface.
- Software version matches are not proof of vulnerability.
- Use Shodan responsibly for defensive research and authorized asset discovery.
- Never publish API keys, private tokens, or sensitive organization data in a public repository.

---

## 📚 Official Documentation

| Resource | Purpose |
|:---|:---|
| [Shodan Search Filters](https://www.shodan.io/search/filters) | Main search filter reference |
| [Search Query Fundamentals](https://help.shodan.io/the-basics/search-query-fundamentals) | Query syntax and filter behavior |
| [Shodan Book: Query Syntax](https://book.shodan.io/getting-started/query-syntax/) | Search syntax guide |
| [Shodan REST API](https://developer.shodan.io/api) | API endpoints and filter discovery |
| [Shodan Trends Filters](https://trends.shodan.io/search/filters) | Trends-specific filter reference |
| [Shodan Datapedia](https://datapedia.shodan.io/) | Banner fields and metadata |

---

<p align="center">
  <sub>Built for learning, OSINT, defensive security, and authorized attack-surface discovery.</sub>
</p>

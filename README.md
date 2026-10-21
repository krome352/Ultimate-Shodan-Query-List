⌕ Ultimate Shodan Query Reference
A Cybersecurity Reconnaissance Field Guide

A categorized reference to Shodan search queries for discovering internet-exposed services, identifying potentially vulnerable technologies, and investigating security misconfigurations.

Version: 1.2
Focus: Asset Discovery · Service Enumeration · Vulnerability Research · Exposure Analysis

Table of Contents
- 01 — Default Credentials & Authentication
- 02 — Web Servers & Applications
- 03 — Database Services
- 04 — Remote Access Services
- 05 — Internet of Things (IoT)
- 06 — Industrial Control Systems
- 07 — Cloud Services & API Exposure
- 08 — Network Services
- 09 — Known Vulnerabilities & CVEs
- 10 — Misconfigurations & Information Disclosure
- 11 — Directory Listings & Exposed Web Files
- 12 — Legacy Runtime & Framework Fingerprints
- 13 — Wireless & Network-Device Web Interfaces
- 14 — Combined Queries for More Specific Research
01 — Default Credentials & Authentication
Objective: Identify services that may expose authentication weaknesses or insecure access configurations.
#	Query	Purpose
01	default password	Search for banners mentioning default passwords
02	password:admin	Search for indexed authentication-related text
03	password:123456	Search for a commonly used weak password string
04	password:password	Search for the literal password string
05	authorization:Basic	Identify responses containing Basic authentication metadata
06	port:21 "anonymous"	Investigate FTP services mentioning anonymous access
07	port:23	Discover Telnet services
08	port:22 "password"	Search SSH banners or indexed text for password references
09	port:5900	Discover VNC services for authorized configuration auditing
10	port:27017	Discover MongoDB services for authentication and exposure checks


Analyst note: Search results containing password-related strings do not establish that valid credentials are present or that authentication can be bypassed.
02 — Web Servers & Applications
Objective: Discover web applications, administrative interfaces, development environments, and potential information-disclosure issues.
#	Query	Purpose
11	http.title:"Index of"	Find web pages that may expose directory listings
12	http.title:"admin"	Discover pages with admin-related titles
13	http.component:"phpMyAdmin"	Identify detected phpMyAdmin deployments
14	http.component:"WordPress"	Identify WordPress installations
15	http.component:"Joomla"	Identify Joomla installations
16	http.component:"Drupal"	Identify Drupal installations
17	http.vulnerability:*	Search for results associated with Shodan's vulnerability data
18	http.title:"error"	Find pages with error-related titles
19	http.title:"test"	Find pages potentially associated with test environments
20	http.title:"backup"	Find pages with backup-related titles
21	http.title:"index of" "password"	Find pages with backup-related titles


Analyst note: Titles and component fingerprints are clues, not vulnerability confirmations. Verify software versions, deployment context, and the presence of an actual security weakness.
03 — Database Services
Objective: Identify database technologies exposed to the public internet and assess whether their exposure is intentional.
#	Query	Service
21	port:27017	MongoDB
22	port:6379	Redis
23	port:9200	Elasticsearch
24	port:5984	CouchDB
25	port:11211	Memcached
26	port:3306	MySQL
27	port:5432	PostgreSQL
28	port:1521	Oracle Database
29	port:9042	Apache Cassandra native transport
30	port:7474	Neo4j HTTP interface


Analyst note: A reachable database is not necessarily misconfigured. Investigate authentication requirements, network restrictions, TLS, access controls, and whether the service is intended to be publicly reachable.
04 — Remote Access Services
Objective: Locate remote administration services and assess their exposure, configuration, and patch status.
#	Query	Purpose
31	port:3389	Remote Desktop Protocol (RDP)
32	port:5900	VNC remote desktop
33	TeamViewer	Search for TeamViewer-related service fingerprints
34	AnyDesk	Search for AnyDesk-related fingerprints
35	Ammyy	Search for Ammyy Admin references
36	port:22	SSH service discovery
37	port:23 "login"	Telnet login prompts
38	pcAnywhere	Search for pcAnywhere-related fingerprints
39	remote access	Search indexed banners for remote-access references
40	remote administration	Search for remote administration references


Analyst note: Product-name searches may be incomplete or imprecise. Confirm the protocol, product version, exposure, and patch level before classifying a finding as a vulnerability.
05 — Internet of Things (IoT)
Objective: Discover connected-device technologies and investigate unnecessary public exposure.
#	Query	Device category
41	webcam	Web cameras
42	camera	Security and network cameras
43	printer	Network printers
44	IoT	General Internet of Things references
45	smart home	Smart-home devices
46	router	Network routers
47	DVR	Digital video recorders
48	NVR	Network video recorders
49	baby monitor	Networked baby-monitor references
50	smart TV	Smart televisions


Analyst note: These are broad discovery terms. Results may include product descriptions, false positives, and unrelated banners. Restrict investigations to systems you own or are authorized to assess.
06 — Industrial Control Systems
Objective: Understand the external exposure of industrial, operational-technology, and building-automation infrastructure.
#	Query	Technology
51	SCADA	Supervisory Control and Data Acquisition
52	PLC	Programmable Logic Controllers
53	Modbus	Industrial communications protocol
54	BACnet	Building automation communications
55	Siemens	Siemens industrial technology
56	Schneider Electric	Schneider Electric equipment
57	Allen-Bradley	Rockwell Automation equipment
58	Honeywell	Honeywell industrial and automation systems
59	GE Fanuc	Legacy GE Fanuc control systems
60	Mitsubishi	Mitsubishi industrial technology


Analyst note: Industrial systems require extra caution. Do not probe, authenticate to, modify, or interact with live control systems without explicit authorization and a defined safety plan. Search results alone are sufficient for initial passive research.
07 — Cloud Services & API Exposure
Objective: Investigate possible cloud-storage exposure, leaked secrets, and publicly indexed API-related information.
#	Query	Purpose
61	Amazon S3	Search for S3-related references
62	Azure Blob Storage	Search for Azure storage references
63	Google Cloud	Search for Google Cloud references
64	api key	Search for API-key-related text
65	AWS secret	Search for AWS-secret-related references
66	private key	Search for private-key-related text
67	JWT	Search for JSON Web Token references
68	OAuth	Search for OAuth-related references
69	GitHub token	Search for GitHub-token-related text
70	Slack token	Search for Slack-token-related text


Analyst note: These terms do not guarantee that secrets are present, valid, or usable. Avoid collecting, testing, or using third-party credentials. For defensive audits, use authorized cloud inventory tools and secret-scanning tools against your own repositories and assets.
08 — Network Services
Objective: Discover commonly exposed network protocols and identify services that may need stronger access controls.
#	Query	Service
71	port:445	SMB
72	port:139	NetBIOS session service
73	port:389	LDAP
74	port:161	SNMP
75	port:21	FTP
76	port:69	TFTP
77	port:23	Telnet
78	port:514	Syslog or legacy remote-shell-related services, depending on configuration
79	rexec	Search for remote-execution service references
80	port:6000	X11-related services


Analyst note: Port numbers are useful starting points, not definitive service identification. Some protocols use different ports, and unrelated services can run on the same port. Confirm service fingerprints before drawing conclusions.
09 — Known Vulnerabilities & CVEs
Objective: Research known vulnerabilities and identify potentially affected software for authorized asset assessments.

A CVE (Common Vulnerabilities and Exposures) is an identifier assigned to a publicly disclosed vulnerability.
#	CVE	Vulnerability / affected technology
81	CVE-2017-0144	EternalBlue — Microsoft SMBv1
82	CVE-2019-0708	BlueKeep — Remote Desktop Services
83	CVE-2021-44228	Log4Shell — Apache Log4j
84	CVE-2020-1472	Zerologon — Netlogon
85	CVE-2019-11089	Verify the CVE identifier and affected product before using this entry
86	CVE-2020-0688	Microsoft Exchange Server
87	CVE-2017-10271	Oracle WebLogic Server
88	CVE-2016-10033	PHPMailer remote code execution vulnerability
89	CVE-2014-0160	Heartbleed — OpenSSL
90	CVE-2018-14340	Verify the identifier and product association before using this entry


Analyst note: A CVE identifier is not automatically a valid Shodan search filter. Check Shodan's current search syntax and vulnerability data support. Where supported, a query such as vuln:CVE-2021-44228 may be useful; verify the syntax in Shodan's documentation.

A detected vulnerability may be a false positive or may not apply to the installed version or configuration. Confirm affected versions using trusted advisories and your own authorized asset inventory.
10 — Misconfigurations & Information Disclosure
Objective: Find signs of exposed development infrastructure, configuration files, and potentially sensitive information.
#	Query	Purpose
91	debug	Search for debug-related references
92	test	Search for test-environment references
93	development	Search for development-environment references
94	staging	Search for staging-environment references
95	git	Search for Git-related references
96	.env	Search for environment-file references
97	.git	Search for Git metadata references
98	wp-config	Search for WordPress configuration references
99	database password	Search for database-password-related text
100	credentials	Search for credential-related references


Analyst note: Shodan indexes observable service data; a keyword match does not necessarily mean a file is publicly retrievable. Never attempt to access or download exposed secrets belonging to third parties.
11 — Directory Listings & Exposed Web Files
Objective: Passively identify web services that may expose directory indexes or accidentally publish configuration, backup, and log files.
11.1 — Directory Listings
http.title:"index of"
http.title:"directory listing"
http.title:"index of /"
http.title:"parent directory"
What these look for: Page titles commonly associated with directory-index pages. A match is only a lead, not proof that sensitive files are exposed.
11.2 — Potentially Sensitive Files
http.title:"index of" "config"
http.title:"index of" "password"
http.title:"index of" ".git"
http.title:"index of" ".env"
http.title:"index of" "backup"
http.title:"index of" "log"
What these look for: Directory-index pages whose indexed text mentions configuration, password, Git metadata, environment files, backups, or logs.
Analyst note: Shodan indexes observable HTTP metadata and content; it does not guarantee that a matching file is retrievable. Do not open, download, or use third-party secrets. Verify findings only within an authorized scope.

12 — Legacy Runtime & Framework Fingerprints
Objective: Find pages that appear to reference older runtimes or recognizable web frameworks. These text matches do not establish the server's installed version or vulnerability status.
http.html:"Python 2.6"
http.html:"Python 2.7"
http.html:"Dojo"
http.html:"Django 1."
http.html:"Flask"
What these look for: Indexed page content that mentions these runtime or framework names. A mention may be documentation or unrelated text rather than evidence the technology is running.
Analyst note: Confirm versions through authorized asset inventory, reliable fingerprints, or vendor documentation before assigning risk. A framework name alone is not a vulnerability.

13 — Wireless & Network-Device Web Interfaces
Objective: Discover web pages that may belong to wireless access points, controllers, or network-device administration interfaces.
http.title:"wireless"
http.title:"login" "wireless"
http.title:"access point"
http.title:"controller" "login"
What these look for: Page titles and indexed text associated with wireless devices, access-point management, or controller login pages.
Analyst note: These broad fingerprints can return unrelated pages. Do not attempt logins, default credentials, configuration changes, or active tests against devices you do not own or have explicit permission to assess.

14 — Combined Queries for More Specific Research
Objective: Combine multiple search terms to narrow passive discovery. More terms can reduce the number of results, but do not automatically make results more accurate.
http.title:"index of" "Python"
http.title:"directory listing" "config"
http.title:"index of" "password" "Python"
What these look for: Directory-index or listing pages that also mention a technology or keyword of interest.
Analyst note: Query behavior depends on Shodan's current syntax and indexed data. Treat matches as research leads, not confirmed findings, and keep verification within authorized scope.

Query Engineering — Improving Search Precision
Individual search terms are useful for exploration. Shodan filters can help narrow results when their syntax is supported for the relevant data type.
Filter	Example	Function
port:	port:443	Match a port
country:	country:US	Restrict results by country
city:	city:Atlanta	Narrow by city metadata
org:	org:"Example Organization"	Match organization metadata
product:	product:nginx	Match a detected product
http.title:	http.title:"Dashboard"	Match an HTTP page title
http.component:	http.component:"WordPress"	Match a detected web component
vuln:	vuln:CVE-2021-44228	Search vulnerability data where supported


Example — Authorized web-service inventory

port:443 country:US

Example — Narrowing a technology search

http.component:"WordPress" country:US

Example — Researching known vulnerability exposure

vuln:CVE-2021-44228
Filter availability, syntax, and matching behavior can change. Consult the official Shodan search documentation before relying on a query for an assessment.

Operational Workflow
1. Define scope. Identify the organization, IP ranges, domains, or assets you are authorized to investigate.
2. Discover. Search for services and technologies associated with that scope.
3. Classify. Distinguish ordinary exposure from a potential misconfiguration or known vulnerability.
4. Corroborate. Check software versions, vendor advisories, configuration records, and trusted vulnerability references.
5. Document. Record the query, timestamp, observed evidence, confidence level, and potential impact.
6. Remediate. Restrict unnecessary exposure, patch affected software, rotate exposed secrets, and improve access controls.
7. Reassess. Repeat the authorized inventory to confirm that the exposure has been addressed.
Important Notes
- Exposure ≠ vulnerability. A public service may be intentionally exposed and securely configured.
- Search results ≠ proof. Banners, titles, product fingerprints, and vulnerability detections can be incomplete or inaccurate.
- Protect sensitive data. Do not retrieve, disclose, or use third-party credentials, private keys, or other secrets.
- Respect authorization. Keep active verification within systems you own or have explicit permission to test.
- Validate the reference. Confirm CVE identifiers, product associations, and Shodan filter syntax against authoritative sources.
Primary reference: Shodan Search Query Fundamentals

Additional reference: Shodan Help Center
End of reference — Ultimate Shodan Query List

~ VantaSEC

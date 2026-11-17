# Week 2 Footprinting and Network Discovery

Author: Sifa Obedi Kamendu | Networkwalks B084

Footprinting and Network Discovery Report

Week 2  Networkwalks Cybersecurity Program

Sifa Obedi Kamendu  |  Batch B084
Evidence dates 13 and 17 November 2026
Public copy with sensitive identifiers removed

1 Liability Disclaimer

This report documents educational reconnaissance and host discovery. It does not establish permission for further testing. Any future activity must remain within the scope approved by the system or network owner. No exploitation or access to accounts is documented in the supplied evidence.

2 Introduction

I used Kali Linux to gather information about networkwalks.com and Zenmap on Windows to discover live hosts on my local LAN. The final scan reported 48 live hosts and displayed MAC addresses for 47 of them. The website checks identified public DNS information, HTTP headers, web technology fingerprints and a WAF fingerprint. These observations are not proof of exploitable vulnerabilities.

The report follows the supplied sample structure using my own findings. Addresses, device identifiers and cookie values are masked in the public evidence. Exact host records remain in the original assignment evidence for private submission.

3 Tools Used

4 Activities Performed

4 1 Footprinting and Reconnaissance

WHOIS

Command: whois networkwalks.com

The screenshot lists GoDaddy.com LLC as registrar, HostGator name servers and DNSSEC as unsigned. These are registration observations, not evidence that the domain can be compromised.

WhatWeb

Command: whatweb networkwalks.com

HTTP redirected to HTTPS and the HTTPS page returned 200 OK. WhatWeb reported Apache, WordPress 7.1.4, WordPress Download Manager 3.3.77 and jQuery 3.7.1. These are tool fingerprints, not independently verified installed versions. The Bootstrap version label is also unverified.

Nslookup

Command: nslookup networkwalks.com

The query returned an IPv4 address for the domain. The server address is masked in the public screenshots.

HTTP headers

Command: curl -I https://networkwalks.com

The response showed HTTP 200 OK, Server Apache, WordPress REST API links and a cookie with Secure and HttpOnly attributes. The cookie value is removed from the public image. This single response is not a complete header or application security assessment.

WAF detection

Command: wafw00f networkwalks.com

Wafw00f reported ModSecurity from SpiderLabs. A fingerprint does not establish whether the WAF blocks attacks effectively.

DNS enumeration

Command: dnsrecon -d networkwalks.com

The visible output contains SOA, NS, MX, A, TXT and autodiscover SRV information. It also reports no answer for a DNSSEC query. That message alone is not a validated DNS security weakness.

I saved terminal output as text using the command followed by | tee ~/Desktop/filename.txt. The screenshots show the captured responses; the report does not claim that every DNS record or website component was enumerated.

4 2 Network Scanning with Zenmap

I checked the active Wi-Fi adapter with ipconfig. Its subnet mask was 255.255.255.0, equivalent to /24. I selected this adapter rather than the disconnected or virtual adapters, then used the Zenmap Ping scan profile to discover live hosts. The screenshot shows nmap -sn followed by my LAN subnet.

My earlier scan showed fewer hosts. The final output in the uploaded report is the source for the count of 48. Host discovery results can vary between scans; the count describes that scan only. Live hosts are not necessarily all PCs. A topology view generated from discovery is not a verified map of physical switches or cabling.

5 Risk Analysis and Impact

No confirmed vulnerability or severity rating is assigned. The following observations identify areas for review rather than demonstrated security failures.

6 Recommendations

Verify actual CMS and plugin versions and maintain supported updates.

Review application headers and cookie settings across relevant responses.

Maintain only required DNS records and assess DNSSEC configuration separately.

Review WAF configuration and monitoring through approved testing.

Compare discovered devices with an approved inventory before investigating unexpected entries.

Keep complete evidence for private assessment and redact device identifiers and session values before public posting.

7 Conclusion

I practised collecting domain and website information, identifying the correct Windows subnet and documenting live host discovery. My final scan found 48 hosts with 47 MAC addresses shown. I learned to distinguish scan observations from confirmed vulnerabilities and to preserve useful evidence while removing sensitive details for public sharing.

8 Evidence Collected

The following images come from my uploaded findings and topology export. Black boxes conceal identifiers and values; scan counts, commands where practical and tool conclusions remain visible. Blank Zenmap setup screenshots were omitted because they do not show results.

01 Windows network configuration

Redacted evidence for public sharing. The original source is retained separately for private assignment review.

02 Zenmap live hosts

Redacted evidence for public sharing. The original source is retained separately for private assignment review.

03 WHOIS

Redacted evidence for public sharing. The original source is retained separately for private assignment review.

04 WhatWeb

Redacted evidence for public sharing. The original source is retained separately for private assignment review.

05 NSlookup

Redacted evidence for public sharing. The original source is retained separately for private assignment review.

06 HTTP headers

Redacted evidence for public sharing. The original source is retained separately for private assignment review.

07 WAF detection

Redacted evidence for public sharing. The original source is retained separately for private assignment review.

08 DNSRecon

Redacted evidence for public sharing. The original source is retained separately for private assignment review.

09 Topology 1

Redacted evidence for public sharing. The original source is retained separately for private assignment review.


## Screenshots

![01_Windows_network_configuration](images/01_Windows_network_configuration.png)

![02_Zenmap_live_hosts](images/02_Zenmap_live_hosts.png)

![03_WHOIS](images/03_WHOIS.png)

![04_WhatWeb](images/04_WhatWeb.png)

![05_NSlookup](images/05_NSlookup.png)

![06_HTTP_headers](images/06_HTTP_headers.png)

![07_WAF_detection](images/07_WAF_detection.png)

![08_DNSRecon](images/08_DNSRecon.png)

![09_Topology_1](images/09_Topology_1.png)

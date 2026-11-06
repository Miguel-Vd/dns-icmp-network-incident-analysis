# Network Incident Report: DNS and ICMP Traffic Analysis

**Incident Type:** DNS Resolution Failure  
**Affected Service:** Domain Name System (DNS)  
**Protocols Involved:** UDP and ICMP  
**Incident Time:** 13:24:32  
**Analysis Tool:** tcpdump  
**Environment:** Simulated Security Incident — Google Cybersecurity Professional Certificate

---

## Part 1: Summary of the Problem Found in DNS and ICMP Traffic

### The UDP protocol reveals that:

UDP packets sent from the client computer to the DNS server were unsuccessful. Instead of receiving a DNS response containing the website's IP address, the computer received ICMP error messages indicating that UDP port 53 was unreachable.

### The network analysis showed the following ICMP error message:

`udp port 53 unreachable`

This message indicates that the DNS queries could not be delivered to the intended service on UDP port 53.

### The port noted in the error message is used for:

Port 53 is used by the Domain Name System (DNS), which translates domain names into IP addresses. DNS commonly uses UDP port 53 for standard queries, although TCP port 53 is also supported.

### The most likely issue is:

The DNS service was unavailable or inaccessible through UDP port 53. This prevented the browser from resolving the domain name `www.yummyrecipesforme.com` into an IP address and accessing the website.

Possible explanations include a DNS service failure, incorrect server configuration, or firewall restrictions.

---

## Part 2: Incident Analysis and Possible Causes

### Time the Incident Occurred

The first recorded event occurred at **13:24:32**, according to the timestamp in the tcpdump log.

### How the IT Team Became Aware of the Incident

The IT team became aware of the issue after multiple customers reported that they could not access `www.yummyrecipesforme.com`.

Users experienced connection errors while attempting to load the website, receiving a "destination port unreachable" message.

### Actions Taken to Investigate the Incident

The security analyst initially attempted to access the website to reproduce the reported issue.

After encountering the same error, the analyst examined the network traffic using tcpdump.

The captured traffic showed DNS queries being sent through UDP to the DNS server. However, instead of receiving successful DNS responses, the client received ICMP destination-unreachable messages.

The analyst reviewed the timestamps, source and destination IP addresses, protocols, and destination port to identify the affected network service.

### Key Findings

The investigation identified the following information:

- **Client IP Address:** 192.51.100.15
- **DNS Server IP Address:** 203.0.113.2
- **Affected Protocols:** UDP and ICMP
- **Destination Port:** UDP 53
- **Affected Service:** DNS
- **ICMP Error:** `udp port 53 unreachable`

The client attempted to contact the DNS server three times, and each attempt resulted in the same ICMP error.

These findings indicate that the DNS queries could not reach an available service on UDP port 53.

Because DNS resolution was unsuccessful, the browser could not obtain the IP address required to establish the intended HTTPS connection.

### Possible Cause of the Incident

A likely explanation is that the DNS service was not running or was otherwise inaccessible on the destination server.

Other possible causes include:

- Firewall rules rejecting DNS traffic on UDP port 53.
- Incorrect DNS server configuration.
- A temporary DNS service or network failure.

A denial-of-service (DoS) attack could also be investigated as a potential cause of service disruption. However, the available tcpdump logs do not provide sufficient evidence to confirm that an attack occurred.

Further investigation would be required to determine the exact root cause.

---

## Conclusion

The network traffic analysis identified a DNS resolution failure involving UDP port 53.

The tcpdump logs showed repeated DNS queries followed by ICMP destination-unreachable messages, indicating that the DNS service was inaccessible.

The incident affected users' ability to resolve the website's domain name and access the requested web page.

The findings were documented and escalated to the security engineering team for further investigation and resolution.

---

## Skills Demonstrated

- Network traffic analysis
- tcpdump log interpretation
- DNS troubleshooting
- UDP and ICMP protocol analysis
- Identification of network service failures
- Incident documentation and reporting

---

*This report is based on a simulated incident provided as part of the Google Cybersecurity Professional Certificate. The investigation was performed using the network traffic information supplied in the exercise.*

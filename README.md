# DNS and ICMP Network Incident Analysis

## Overview

This project is part of the Google Cybersecurity Professional Certificate and focuses on investigating a simulated network incident using tcpdump logs.

The objective was to identify the network protocols affected, analyze the errors found in the captured traffic, and document possible causes of the incident.

## Incident Description

Multiple users reported being unable to access the website `www.yummyrecipesforme.com`, receiving a "destination port unreachable" error.

The network traffic logs showed that DNS queries sent through UDP were unsuccessful. Instead of receiving a DNS response, the computer received ICMP error messages indicating that UDP port 53 was unreachable.

## Investigation and Findings

The tcpdump logs provided the following information:

- **Source IP:** 192.51.100.15
- **DNS Server IP:** 203.0.113.2
- **Affected Protocols:** UDP and ICMP
- **Affected Service:** DNS
- **Affected Port:** UDP 53
- **Error Message:** `udp port 53 unreachable`
- **Incident Time:** 13:24:32

The same error occurred during three attempts to contact the DNS server, preventing successful domain name resolution.

## Possible Causes

Based on the available evidence, the issue may have been caused by:

- DNS service unavailability.
- Firewall rules blocking UDP port 53.
- Incorrect DNS server configuration.

A denial-of-service attack could also be considered, but the logs do not provide enough evidence to confirm one.

## Conclusion

The investigation identified a DNS communication failure involving UDP port 53. The ICMP error messages indicated that the DNS service was unreachable, preventing users from resolving the website's domain name.

The findings were documented for further investigation by the security engineering team.

## Skills Practiced

- Network traffic analysis
- DNS, UDP, and ICMP protocols
- tcpdump log interpretation
- Incident investigation
- Technical incident reporting

## Disclaimer

This project was completed as part of a simulated exercise in the Google Cybersecurity Professional Certificate.

## Documentation

- [Full Incident Report](reports/incident-report.md)

## Network Traffic Evidence

The tcpdump log contains three DNS queries sent over UDP
and three ICMP destination-unreachable responses.

The captured traffic indicates that the DNS service
was inaccessible through UDP port 53.

[View the original tcpdump log](evidence/tcpdump-log.txt)

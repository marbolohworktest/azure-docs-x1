---
title: Azure Firewall IDPS signature rule categories
description: Learn about Azure Firewall IDPS signature rule categories and their descriptions.
author: vhorne
ms.service: azure-firewall
services: firewall
ms.topic: overview
ms.date: 12/15/2021
ms.author: victorh
---

# Azure Firewall IDPS signature rule categories

Azure Firewall IDPS features over 50 categories that can be assigned to individual signatures. The following table is a list of definitions for each category.

## Categories

|Category |Description |
|---------|---------|
|3CORESec|This category is for signatures that are generated automatically from the 3CORESec team’s IP blocklists. These blocklists are generated by 3CORESec based on malicious activity from their Honeypots.|
|ActiveX|This category is for signatures that protect against attacks against Microsoft ActiveX controls and exploits targeting vulnerabilities in ActiveX controls.|
|Adware-PUP|This category is for signatures to identify software that is used for ad tracking or other types of spyware related activity.|
|Attack Response|This category is for signatures to identify responses indicative of intrusion—examples include but not limited to LMHost file download, presence of certain web banners and the detection of Metasploit Meterpreter kill command. These signatures are designed to catch the results of a successful attack. Things like *id=root*, or error messages that indicate a compromise may have happened.|
|Botcc (Bot Command and Control)|This category is for signatures that are autogenerated from several sources of known and confirmed active botnet and other Command and Control (C2) hosts. This category is updated daily. The category’s primary data source is `Shadowserver.org.`|
|Botcc Port grouped|This category is for signatures like those in the Botcc category but grouped by destination port. Rules grouped by port can offer higher fidelity than rules not grouped by port.|
|Chat|This category is for signatures that identify traffic related to many chat clients such as Internet Relay Chat (IRC). Chat traffic can be indicative of possible check-in activity by threat actors.|
|CIArmy|This category is for signatures that are generated using Collective Intelligence’s IP rules for blocking.|
|Coin mining|This category is for signatures with rules that detect malware, which does coin mining. These signatures can also detect some legitimate (though often undesirable) coin mining software.|
|Compromised|This category is for signatures based on a list of known compromised hosts. This list is confirmed and updated daily. The signatures in this category can vary from one to several hundred rules depending on the data sources. The data sources for this category come from several private but highly reliable data sources.|
|Current Events|This category is for signatures with rules developed in response to active and short-lived campaigns and high-profile items that are expected to be temporary. One example is fraud campaigns related to disasters. The rules in this category aren't intended to be kept in the ruleset for long, or that need to be further tested before they're considered for inclusion. Most often these will be simple signatures for the Storm binary URL of the day, signatures to catch CLSIDs of newly found vulnerable apps where we don’t have any detail on the exploit, and so on.|
|DNS (Domain Name Service)|This category is for signatures with rules for attacks and vulnerabilities regarding DNS. This category is also used for rules related to abuse of DNS such as tunneling.|
|DOS|This category is for signatures that detect Denial of Service (DoS) attempts. These rules are intended to catch inbound DoS activity, and provide indication of outbound DoS activity. <br><br>Note: All the signatures in this category are defined as “Alert Only”, therefore by default, traffic matching these signatures will not be blocked even though the IDPS mode is set to “Alert and Deny”. Customers may override this behavior by customizing these specific signatures to “Alert and Deny” mode.|
|Drop|This category is for signatures to block IP addresses on the Spamhaus DROP (Don’t Route or Peer) list. The rules in this category are updated daily.|
|Dshield|This category is for signatures based on attackers identified by Dshield. The rules in this category are updated daily from the DShield top attackers list, which is reliable.|
|Exploit|This category is for signatures that protect against direct exploits not otherwise covered in a specific service category. This category is where specific attacks against vulnerabilities such as against Microsoft Windows will be found. Attacks with their own category such as SQL injection have their own category.|
|Exploit-Kit|This category is for signatures to detect activity related to Exploit Kits their infrastructure, and delivery.|
|FTP|This category is for signatures related to attacks, exploits, and vulnerabilities associated with the File Transfer Protocol (FTP). This category also includes rules that detect non-malicious FTP activity such as logins for logging purposes.|
|Games|This category is for signatures that identify of gaming traffic and attacks against those games. The rules cover games such as World of Warcraft, Starcraft, and other popular online games. While the games and their traffic aren't malicious, they're often unwanted and prohibited by policy on corporate networks.|
|Hunting|This category is for signatures that provide indicators that when matched with other signatures can be useful for threat hunting in an environment. These rules can provide false positives on legitimate traffic and inhibit performance. They're only recommended for use when actively researching potential threats in the environment. <br><br>Note: All the signatures in this category are defined as “Alert Only”, therefore by default, traffic matching these signatures will not be blocked even though the IDPS mode is set to “Alert and Deny”. Customers may override this behavior by customizing these specific signatures to “Alert and Deny” mode.|
|ICMP|This category is for signatures related to attacks and vulnerabilities about Internet Control Message Protocol(ICMP).|
|ICMP_info|This category is for signatures related to ICMP protocol-specific events, typically associated with normal operations for logging purposes. <br><br>Note: All the signatures in this category are defined as “Alert Only”, therefore by default, traffic matching these signatures will not be blocked even though the IDPS mode is set to “Alert and Deny”. Customers may override this behavior by customizing these specific signatures to “Alert and Deny” mode.|
|IMAP|This category is for signatures related to attacks, exploits, and vulnerabilities about Internet Message Access Protocol (IMAP). This category also includes rules that detect nonmalicious IMAP activity for logging purposes.|
|Inappropriate|This category is for signatures to identify potentially activity related to sites that are pornographic or otherwise not appropriate for a work environment.<br><br>Warning: This category can have a significant performance impact and high rate of false positives.|
|Info|This category is for signatures to help provide audit level events that are useful for correlation and identifying interesting activity, which may not be inherently malicious but is often observed in malware and other threats. For example, downloading an Executable over HTTP by IP address rather than domain name. <br><br>Note: All the signatures in this category are defined as “Alert Only”, therefore by default, traffic matching these signatures will not be blocked even though the IDPS mode is set to “Alert and Deny”. Customers may override this behavior by customizing these specific signatures to “Alert and Deny” mode. |
|JA3|This category is for signatures to fingerprint malicious SSL certificates using JA3 hashes. These rules are based on parameters that are in the SSL handshake negotiation by both clients and servers. These rules can have a high false positive rate but can be useful for threat hunting or malware detonation environments.|
|Malware|This category is for signatures to detect malicious software. Rules in this category detect activity related to malicious software that is detected on the network including malware in transit, active malware, malware infections, malware attacks, and updating of malware. This is also a highly important category and it's highly recommended that you run it.|
|Misc|This category is for signatures not covered in other categories.|
|Mobile Malware|This category is for signatures that indicate malware that is associated with mobile and tablet-operating systems like Google Android, Apple iOS, and others. Malware that is detected and is associated with mobile operating systems will generally be placed in this category rather than the standard categories like Malware.|
NETBIOS|This category is for signatures related to attacks, exploits, and vulnerabilities associated with NetBIOS. This category also includes rules that detect non-malicious NetBIOS activity for logging purposes.|
|P2P|This category is for signatures for the identification of Peer-to-Peer (P2P) traffic and attacks against it. Identified P2P traffic includes torrents, edonkey, Bittorrent, Gnutella, and Limewire among others. P2P traffic isn't inherently malicious but is often of notable for enterprises. <br><br>Note: All the signatures in this category are defined as “Alert Only”, therefore by default, traffic matching these signatures will not be blocked even though the IDPS mode is set to “Alert and Deny”. Customers may override this behavior by customizing these specific signatures to “Alert and Deny” mode.|
|Phishing|This category is for signatures that detect credential-phishing activity. This includes landing pages displaying credential phishing and successful submission of credentials into credential-phishing sites.|
|Policy|This category is for signatures that may indicate violations to an organization’s policy. This can include protocols prone to abuse, and other application-level transactions, which may be of interest. <br><br>Note: All the signatures in this category are defined as “Alert Only”, therefore by default, traffic matching these signatures will not be blocked even though the IDPS mode is set to “Alert and Deny”. Customers may override this by customizing these specific signatures to “Alert and Deny” mode.|
|POP3|This category is for signatures related to attacks, exploits, and vulnerabilities associated with the Post Office Protocol 3.0 (POP3). This category also includes rules that detect nonmalicious POP3 activity for logging purposes.|
|RPC|This category is for signatures related to attacks, exploits, and vulnerabilities regarding Remote Procedure Call (RPC). This category also includes rules that detect non-malicious RPC activity for logging purposes.|
|SCADA|This category is for signatures related to attacks, exploits, and vulnerabilities associated with supervisory control and data acquisition (SCADA). This category also includes rules that detect non-malicious SCADA activity for logging purposes.|
|SCAN|This category is for signatures to detect reconnaissance and probing from tools such as Nessus, Nikto, and other port scanning, tools. This category can be useful for detecting early breach activity and post-infection lateral movement within an organization. <br><br>Note: All the signatures in this category are defined as “Alert Only”, therefore by default, traffic matching these signatures will not be blocked even though the IDPS mode is set to “Alert and Deny”. Customers may override this by customizing these specific signatures to “Alert and Deny” mode.|
|Shell code|This category is for signatures for remote shell code detection. Remote shell code is used when an attacker wants to target a vulnerable process running on another machine on a local network or intranet. If successfully executed, the shell code can provide the attacker access to the target machine across the network. Remote shell codes normally use standard TCP/IP socket connections to allow the attacker access to the shell on the target machine. Such shell code can be categorized based on how this connection is set up: if the shell code can establish this connection, it's called a “reverse shell” or a "connect back" shell code because the shell code connects back to the attacker’s machine.|
|SMTP|This category is for signatures related to attacks, exploits, and vulnerabilities associated with Simple Mail Transfer Protocol (SMTP). This category also includes rules that detect non-malicious SMTP activity for logging purposes.|
|SNMP|This category is for signatures related to attacks, exploits, and vulnerabilities associated with Simple Network Management Protocol (SNMP). This category also includes rules that detect non-malicious SNMP activity for logging purposes.|
|SQL|This category is for signatures related to attacks, exploits, and vulnerabilities associated with Structured Query Language (SQL). This category also includes rules that detect non-malicious SQL activity for logging purposes. <br><br>Note: All the signatures in this category are defined as “Alert Only”, therefore by default, traffic matching these signatures will not be blocked even though the IDPS mode is set to “Alert and Deny”. Customers may override this by customizing these specific signatures to “Alert and Deny” mode.|
|TELNET|This category is for signatures related to attacks, exploits, and vulnerabilities associated with TELNET. This category also includes rules that detect non-malicious TELNET activity for logging purposes.|
|TFTP|This category is for signatures related to attacks, exploits, and vulnerabilities associated with Trivial File Transport Protocol (TFTP). This category also includes rules that detect nonmalicious TFTP activity for logging purposes.|
|TOR|This category is for signatures for the identification of traffic to and from TOR exit nodes based on IP address. <br><br>Note: All the signatures in this category are defined as “Alert Only”, therefore by default, traffic matching these signatures will not be blocked even though the IDPS mode is set to “Alert and Deny”. Customers may override this behavior by customizing these specific signatures to “Alert and Deny” mode.|
|User Agents|This category is for signatures to detect suspicious and anomalous user agents. Known malicious user agents are placed in the Malware category.|
VOIP|This category is for signatures for attacks and vulnerabilities associated with Voice over IP (VOIP) including SIP, H.323, and RTP among others.|
|Web Client|This category is for signatures for attacks and vulnerabilities associated with web clients such as web browsers and also client-side applications like CURL, WGET, and others.|
|Web Server|This category is for signatures to detect attacks against web server infrastructure such as APACHE, TOMCAT, NGINX, Microsoft Internet Information Services (IIS), and other web server software.|
|Web Specific Apps|This category is for signatures to detect attacks and vulnerabilities in specific web applications.|
|WORM|This category is for signatures to detect malicious activity that automatically attempts to spread across the internet or within a network by exploiting a vulnerability are classified as the WORM category. While the actual exploit itself will typically be identified in the Exploit or given protocol category, another entry in this category may be made if the actual malware engaging in worm-like propagation can be identified as well.


## Next steps
- To learn more about Azure Firewall Premium features, see [Azure Firewall Premium features](premium-features.md).

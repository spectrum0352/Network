Port(s)	Protocol	Service	Risk	Impact	Mitigation
0	UDP	Reserved	Rarely used; may be exploited in certain attack scenarios	Potential for misuse in specific attacks	Block unless explicitly required
1	TCP/UDP	TCPMUX	Deprecated; can expose all services via a single port; associated with trojans like SocketsDeTroie	Service enumeration; bypass of access controls	Block; avoid enabling TCPMUX services
2–3	TCP/UDP	CompressNET	Obsolete; associated with the "Death" trojan	Remote access trojan exploitation	Block; not used in modern networks
5	TCP/UDP	Remote Job Entry (RJE)	Obsolete protocol	Potential for unauthorized job submissions	Block
7	TCP/UDP	Echo Protocol	Can be exploited for reflection/amplification attacks	Denial-of-Service (DoS) attacks	Block; use ICMP-based tools like ping for diagnostics
9	TCP/UDP	Discard Protocol / Wake-on-LAN	Discard service can be misused; Wake-on-LAN (WoL) over UDP port 9 can be exploited if not secured	Unauthorized system wake-ups; potential for DoS attacks	Block Discard service; for WoL, use secure methods like VPN tunnels
11	TCP/UDP	Active Users (systat)	Can reveal system user information	Information disclosure	Block
13	TCP/UDP	Daytime Protocol	Can be used for DoS attacks and system fingerprinting	Denial-of-Service; information leakage	Block
15	TCP/UDP	Netstat Service	Obsolete; can reveal network connections	Information disclosure	Block
17	TCP/UDP	Quote of the Day (QOTD)	Can be exploited for reflection/amplification attacks	Denial-of-Service attacks	Block
18	TCP/UDP	Message Send Protocol	Obsolete; minimal legitimate use	Potential for misuse	Block
19	TCP/UDP	Character Generator (CHARGEN)	Vulnerable to amplification attacks; associated with trojans	Denial-of-Service; remote code execution	Block
20–21	TCP	FTP Data Transfer / Control	Transmits data in plaintext; susceptible to interception and brute-force attacks	Credential theft; unauthorized data access	Use secure alternatives like SFTP or FTPS; restrict access
22	TCP/UDP	Secure Shell (SSH)	Brute-force attacks; potential for unauthorized access	System compromise	Implement strong authentication; restrict access by IP; monitor logs
23	TCP/UDP	Telnet	Transmits data in plaintext; associated with multiple trojans	Credential theft; unauthorized access	Replace with SSH; block Telnet
24	TCP/UDP	Priv-Mail	Obsolete; minimal legitimate use	Potential for misuse	Block
25	TCP	Simple Mail Transfer Protocol (SMTP)	Susceptible to spam and phishing if misconfigured	Spam distribution; phishing attacks	Implement proper authentication and spam filters; monitor usage
26	TCP/UDP	Encrypted SMTP	Rarely used; potential for misuse	Unauthorized email transmission	Block unless explicitly required
27	TCP/UDP	NSW User System FE	Obsolete; minimal legitimate use	Potential for misuse	Block
29	TCP/UDP	MSG ICP	Obsolete; minimal legitimate use	Potential for misuse	Block
33	TCP/UDP	Display Support Protocol	Obsolete; minimal legitimate use	Potential for misuse	Block
35	TCP/UDP	Private Printer Server Protocol	Obsolete; minimal legitimate use	Potential for misuse	Block
37	TCP/UDP	TIME Protocol	Can be used for DoS attacks and system fingerprinting	Denial-of-Service; information leakage	Block
39	TCP/UDP	Resource Location Protocol (RLP)	Obsolete; can reveal network resources	Information disclosure	Block
40	TCP/UDP	Unassigned	No standard assignment; potential for misuse	Varies depending on usage	Block unless explicitly required
42	TCP/UDP	WINS / ARPA Host Name Server	WINS is deprecated; vulnerable to spoofing	Incorrect name resolution; MITM attacks	Block unless legacy systems require; prefer DNS
43	TCP	WHOIS	Data mining, used for reconnaissance	Information disclosure	Allow only to trusted WHOIS servers; log usage
47	TCP/UDP	NI FTP	Obsolete	Likely unused; low business value	Block
49	TCP/UDP	TACACS	Susceptible to replay or MITM if not using TACACS+ with encryption	Credential theft	Use TACACS+ with encryption; prefer RADIUS with secure transport
50	TCP/UDP	Remote Mail Checking Protocol	Obsolete	Rarely used; unknown attack surface	Block
51	TCP/UDP	IMP Logical Address Maintenance	Obsolete	Legacy only	Block
52–58	TCP/UDP	XNS Protocol Suite	Obsolete Xerox protocols; rarely seen in modern networks	Minimal legitimate use; spoofing/misuse risk	Block
53	TCP/UDP	DNS	Targeted in amplification/reflection attacks; exfiltration channel	DNS spoofing, tunneling, data exfiltration	Allow only to internal or trusted external DNS; monitor queries
64	TCP/UDP	CI (Covia/Travelport)	Niche application; not common	Potential misuse if exposed	Block unless business-critical
67–68	UDP	DHCP (BOOTP) Server/Client	Can be abused for rogue DHCP server attacks	IP spoofing, MITM, denial of service	Use DHCP guard in Azure NSG; allow only trusted DHCP servers
69	UDP	TFTP	No authentication; used in malware and bootstrapping attacks	Remote code execution; info leakage	Block unless strictly required in isolated subnets
70	TCP	Gopher Protocol	Obsolete; historically vulnerable	Unused; minor risk	Block
71–74	TCP	NETRJS	Obsolete	Rarely used	Block
77	TCP/UDP	Remote Job Entry (RJE)	Obsolete	Risk of unauthorized execution	Block
79	TCP	Finger Protocol	Used for user enumeration	Information leakage	Block
80	TCP	HTTP	Widely used, but plaintext; target for web exploits, injection attacks	Session hijacking, XSS, injection	Use HTTPS (443); limit HTTP to redirect only; apply WAF filtering
80	UDP	QUIC (HTTP/3)	Relatively new; limited inspection options	Difficult to inspect traffic	Allow only if using modern web apps requiring HTTP/3; otherwise block
81	TCP	Torpark	Obscures traffic origins	Anonymized traffic, potential for data exfiltration	Block; monitor for TOR use
82	UDP	Torpark Control	Same as above	Control of anonymized traffic	Block
88	TCP/UDP	Kerberos	Authentication protocol; target for replay, pass-the-ticket, and downgrade attacks	Lateral movement, impersonation	Use AES encryption; enforce strong pre-authentication; monitor logs
90	TCP/UDP	DOD DNSIX / PointCast	Obsolete and/or commercial traffic	Limited legitimate use; abuse potential	Block
99	TCP	WIP Message Protocol	Unofficial; rare	Potential RAT/backdoor use	Block
100	UDP	CyberGate RAT	Known remote access trojan	Full remote control of infected host	Block, alert on detection; use EDR/AV to scan for indicators of compromise
Port(s)	Proto	Service	Risk	Impact	Mitigation
101	TCP	NIC Hostname Service	Rare use; low visibility	Potential info leakage	Block unless required
102	TCP	ISO-TSAP (DECnet)	Legacy protocol	Attack surface for legacy systems	Block unless used by specific legacy workloads
104	TCP/UDP	DICOM (medical imaging)	Data privacy, unauthorized image transfer	Exposure of sensitive medical images	Use over VPN or private endpoint; enforce TLS
105	TCP/UDP	CCSO Nameserver (Ph/Qi)	Obsolete directory service	Unused or internal service	Block
107	TCP	Remote Telnet Service	Cleartext authentication	Credential theft, MITM	Block; use SSH
108	TCP/UDP	SNA Gateway Access	Legacy IBM SNA systems	Rare; hard to inspect	Block unless business-justified
109–110	TCP	POP2 / POP3	Cleartext credentials and mail	Email credential theft	Use secure versions (e.g., POP3S over 995); block plaintext POP
111	TCP/UDP	ONC/Sun RPC	Used in DCOM, NFS; vulnerable to RCE	Exploitable across many protocols	Block or restrict to internal IPs; log and monitor
113	TCP/UDP	Ident Protocol	Used for IRC and service identification	Info disclosure	Block unless explicitly required
115	TCP	SFTP (Simple FTP, not SSH FTP)	Confused with SSH-SFTP; lacks security	Data leakage	Use SCP/SFTP over SSH; block port 115
117	TCP/UDP	UUCP Path	Obsolete	No business use	Block
118	TCP/UDP	SQL Services	Legacy; ambiguous	Data theft or misuse	Restrict to internal networks; use secure SQL implementations
119	TCP	NNTP (Usenet)	Rarely used; potential malware or spam	Abuse for C2 (command and control)	Block unless strictly required
123	UDP	NTP	Used in DDoS amplification, time manipulation attacks	Time-based attack on logs, auth tokens	Use internal NTP or trusted upstream only; block external NTP responses
126	TCP/UDP	NXEdit (Unisys)	Niche development service	Low use; potential niche risk	Block unless business-critical
135	TCP/UDP	EPMAP / DCE-RPC / MS-RPC	High-value target in Windows attacks	Remote code execution, lateral movement	Restrict to trusted IPs (domain controllers, management systems)
137–139	TCP/UDP	NetBIOS Services	SMBv1 traffic; targeted for LLMNR/NBT-NS spoofing	Lateral movement, credential harvesting	Block externally; limit to internal networks with controls
143	TCP	IMAP	If plaintext, vulnerable to sniffing	Email account compromise	Enforce IMAPS (993); block plaintext IMAP
152	TCP/UDP	BFTP	Obsolete	No known business use	Block
153	TCP/UDP	SGMP	Obsolete monitoring	SNMP spoofing	Block
156	TCP/UDP	SQL Service	Ambiguous use	Exfiltration or unauthorized DB access	Limit by ACL; monitor traffic
158	TCP/UDP	DMSP	Rare/unofficial	Unknown attacks	Block
161	UDP	SNMP	Enumerates network info; used in attacks	Reconnaissance, credential reuse	Allow only to/from known management IPs; use SNMPv3
162	TCP/UDP	SNMP Trap	Used by devices to send event alerts	Spoofed alerts or monitoring bypass	Restrict to SNMP managers only
170	TCP	Print-srv	Print service over network	Abuse for printer-based attacks	Restrict or block; prefer modern IPP printing
175	TCP	VMNET (IBM NJE)	Legacy IBM system	Not widely used	Block
177	TCP/UDP	XDMCP	Graphical login over network; unencrypted	Credential sniffing	Block; use SSH with X forwarding
179	TCP	BGP	Critical for routing; can be hijacked	Route injection, denial of service	Only allow on peering/edge firewalls; validate peer config
194	TCP/UDP	IRC	Used in malware and botnet C2 channels	Lateral movement, C2	Block unless used in internal comms testing
199	TCP/UDP	SMUX (SNMP Multiplexer)	Legacy SNMP multiplexing	May reveal SNMP data	Block unless strictly needed by management applications
Port(s)	Proto	Service	Risk	Impact	Mitigation
201	TCP/UDP	AppleTalk Routing Maintenance	Legacy, not used in modern networks	Potentially abused for tunneling	Block
209	TCP/UDP	Quick Mail Transfer Protocol	Obsolete	Cleartext mail traffic	Block
210	TCP/UDP	ANSI Z39.50 (library databases)	Low usage, possible DoS	Misuse in academic environments	Block unless required
213	TCP/UDP	IPX (Internetwork Packet Exchange)	Legacy protocol	Rarely used, potential tunneling	Block
218	TCP/UDP	Message Posting Protocol (MPP)	Obsolete	Rare use	Block
220	TCP/UDP	IMAP v3	Email over insecure protocol	Credential leakage	Use IMAPS (993); block plaintext IMAP
259	TCP/UDP	ESRO	Obsolete	Low risk	Block
264	TCP/UDP	BGMP (Border Gateway Multicast Protocol)	Rare, for multicast routing	BGP-like attacks	Block unless specifically used for multicast
280	TCP	http-mgmt	Admin via HTTP	Sensitive system exposure	Use HTTPS; block HTTP admin ports
300	TCP	ThinLinc Web Access	Remote access	Remote attack surface	Allow only via secure tunnel/VPN
308	TCP	Novastor Backup	Backup software exposure	Data compromise	Restrict to trusted IPs
311	TCP/UDP	macOS Admin	Management interface	Unauthorized access to macOS servers	Restrict access; prefer HTTPS admin
318	TCP	PKIX Time Stamp Protocol	Rarely used	Timestamper forgery	Block unless used
319–320	UDP	Precision Time Protocol (PTP)	DoS, timing manipulation	Time drift or authentication issues	Use internal NTP/PTP only
350–351	TCP/UDP	MATIP (Airline systems)	Industry-specific	Sensitive airline routing or booking data exposure	Block unless industry-required
366	TCP	ODMR (On-Demand Mail Relay)	Obsolete mail relay	Spam relay	Block
369	TCP/UDP	rpc2portmap	Used in RPC communications	RCE via misconfigured RPC	Restrict to internal IPs only
370	TCP/UDP	Coda authentication	Rare distributed FS protocol	Info disclosure	Block
371	TCP	ClearCase ALBD	Used in IBM Rational ClearCase	Could expose version control data	Restrict to internal developers
383	TCP	HP Data Alarm Manager	Monitoring software	Alert spoofing or flood	Restrict to known monitoring agents
384	TCP	Remote Network Server System	Rare/undocumented		
502	TCP/UDP	Modbus (Industrial Control)	SCADA/ICS exposure	Critical infrastructure tampering	Allow only if necessary; restrict to OT network and VPN
504	TCP/UDP	Citadel groupware	Legacy groupware; outdated encryption	Data leakage, C2 communication	Block unless explicitly needed
512	TCP	Rexec	Insecure remote command execution	Credential theft, command injection	Block; use SSH instead
512	UDP	comsat	Legacy notification	Minimal use	Block
513	TCP	rlogin	Insecure remote login	Credential reuse, sniffing	Block; replace with SSH
513	UDP	who	Info disclosure	Username enumeration	Block
514	TCP	rsh	Insecure remote shell	Command execution	Block
514	UDP	syslog	Unencrypted logs	Log spoofing, interception	Use TLS-encrypted syslog; restrict to known IPs
515	TCP	LPD (printer service)	Printer abuse, DDoS	Spool overflow, data exposure	Block or restrict to internal print servers
517–518	UDP	talk/ntalk	Obsolete user chat	Info disclosure	Block
520	TCP/UDP	EFS/RIP (Routing protocols)	Routing protocol manipulation	Network spoofing, route poisoning	Allow internally if required; block externally
521	UDP	RIPng	IPv6 route manipulation	Same as above	Same as above
524	TCP/UDP	NetWare Core Protocol	Legacy NetWare	Unauthorized file access	Block unless using legacy NetWare
525	UDP	Timed (Time server)	Insecure time source	Time drift, authentication issues	Use NTP securely
530	TCP/UDP	RPC	Broad use	RCE or lateral movement risks	Restrict to internal systems only
531	TCP/UDP	AOL Instant Messenger	Legacy messenger, potential for abuse	Exfiltration channel	Block
532	TCP	netnews	Obsolete	Spam or outdated feeds	Block
533	UDP	netwall	Emergency broadcasts	Spoofing	Block
540	TCP	UUCP (Unix copy)	Insecure file transfer	Remote execution or file manipulation	Block
542	TCP/UDP	Commerce apps	Undefined, potential legacy system	Data leakage	Block unless specifically required
543–544	TCP	Kerberos rlogin / shell	Kerberos-based remote access	Auth spoofing if misconfigured	Use modern Kerberos practices
545	TCP	OSISoft PI	OT/ICS software	Remote access to sensitive metrics	Restrict to internal OT networks only
546–547	TCP/UDP	DHCPv6 client/server	DHCP spoofing	Man-in-the-middle attacks	Allow only on trusted internal segments
548	TCP	Apple Filing Protocol	File sharing	File disclosure	Restrict or block unless used in Apple environments
550	TCP/UDP	new-who	Obsolete	Info disclosure	Block
554	TCP/UDP	RTSP (Streaming)	Video stream hijacking or abuse	C2 channel, surveillance	Block unless required for camera/media
556	TCP	Remotefs	Remote file system	Data leakage, DoS	Block
560–561	UDP	Remote monitor	Unauthenticated stats	Reconnaissance	Block
563	TCP/UDP	NNTPS	Obsolete, encrypted Usenet	Spam, C2	Block
587	TCP	SMTP submission	Legitimate mail use	Open relays or spoofing if misconfigured	Restrict to mail relays only
591	TCP	FileMaker HTTP alt port	Web server for FileMaker	Web exposure	Restrict to known clients
593	TCP/UDP	RPC over HTTP (DCOM)	Often targeted by malware	Lateral movement and privilege escalation	Allow only to known RPC servers, especially Exchange
604	TCP	BEEP tunnel	Uncommon tunneling	C2 and covert traffic	Block unless used by internal apps
623	UDP	ASF-RMCP (Remote Mgmt)	Unauthenticated remote mgmt	Full device control by attacker	Block externally
625	TCP	Open Directory Proxy	Apple directory proxy	Directory abuse	Restrict
631	TCP/UDP	IPP / CUPS printing	Printer abuse	Spool attacks, remote printing	Restrict to internal subnets
635	TCP/UDP	RLZ DBase	Unknown/obscure	Unknown	Block
636	TCP/UDP	LDAPS	Encrypted directory access	Safer alternative to 389	Allow only to internal domain controllers
639	TCP/UDP	MSDP	Multicast source discovery	Network abuse	Block unless multicast routing is used
641, 653	TCP/UDP	SupportSoft Remote Command	Remote control software	Full remote access	Block or tightly restrict
643	TCP/UDP	SANity	Storage diagnostics	Possible info leakage	Block unless explicitly required
646	TCP/UDP	LDP (MPLS routing)	Network rerouting	Service disruption	Block unless used in network core
647	TCP	DHCP Failover	Misuse can impact DHCP	IP exhaustion or address conflict	Allow only between trusted DHCP peers
648	TCP	RRP (Registrar Protocol)	Domain name manipulation	Domain hijacking	Block unless registrar infrastructure
651, 695	TCP/UDP	IEEE-MMS / over SSL	Smart grid / OT protocols	Critical systems compromise	Restrict to OT zones only
654	TCP	Media Management Protocol	Media system access	Streaming misuse	Block unless required
657	TCP/UDP	IBM RMC	Hardware partitioning (AIX)	VM/partition abuse	Restrict to HMC
660	TCP	macOS Server admin	Admin interface	Unauthorized access	Restrict to trusted subnets
666	TCP/UDP	Doom / Aircrack-ng	Hacking and gaming ports	Remote wireless attacks or misuse	Block
674	TCP	ACAP	Obsolete config protocol	Data manipulation	Block
688	TCP/UDP	ApplianceWare	Server management	Unauthorized config access	Block unless required
691	TCP	MS Exchange Routing	Exchange-specific	Misrouted mail or relay	Allow for Exchange servers only
694	TCP/UDP	Linux-HA (Heartbeat)	Cluster control abuse	Failover manipulation	Restrict to internal nodes
698	UDP	OLSR (Routing)	Mobile ad-hoc networks	Route injection	Block
700	TCP	EPP (Domain Registry)	Registrar protocol	Domain tampering	Block unless used in registrar systems
502	TCP/UDP	Modbus	Legacy ICS protocol, no auth	ICS device compromise	Restrict to trusted IPs; deep packet inspection
512–514	TCP/UDP	rexec, rlogin, rsh, syslog	Cleartext auth, command injection	Remote shell compromise, data leakage	Block or replace with SSH; use secure syslog (TLS)
515	TCP	LPD	Unauthenticated printing	Lateral movement, DoS	Disable if unused, use IPP with auth
520–521	UDP	RIP/RIPng	Route manipulation	Traffic redirection	Use modern routing protocols; firewall route ads
524	TCP/UDP	NCP	Weak auth, legacy	Credential theft	Limit to internal NetWare systems
530–545	TCP/UDP	RPC, Kerberos (variants), Kshell, Klogin	Legacy protocols	Privilege escalation, MITM	Use modern Kerberos (port 88), enable encryption
546–547	TCP/UDP	DHCPv6	Rogue DHCPv6	Network hijack	Use DHCP snooping
548	TCP	AFP	Weak auth (legacy)	Data theft	Require strong auth, encrypt
554	TCP/UDP	RTSP	Code execution via media streams	Malware delivery	Filter media types, use AV inspection
593	TCP/UDP	HTTP RPC	Remote code execution	Exchange server compromise	Patch Exchange; restrict RPC access
623	UDP	ASF-RMCP	Unauthenticated remote control	Out-of-band control abuse	Block externally; use TLS-authenticated IPMI
631	TCP/UDP	IPP/CUPS	Printer exposure	Lateral movement	Require TLS and auth
636	TCP/UDP	LDAPS	Improper cert validation	LDAP spoofing	Enforce strict cert checks
646	TCP/UDP	LDP (MPLS)	Route injection	Traffic rerouting	Only allow from trusted routers
860	TCP	iSCSI	Unencrypted storage access	Data theft	Use CHAP/iSCSI over VPN
873	TCP	rsync	Unauth access to file sync	Data exfiltration	Restrict to internal IPs, enable auth
902–904	TCP/UDP	VMware Mgmt	Remote console access	VM compromise	Restrict to mgmt IPs, enable strong auth
989–990	TCP/UDP	FTPS	Weak cipher usage	Credential leakage	Enforce modern TLS settings
991–995	TCP/UDP	NAS, IMAPS, POP3S	Known CVEs	Data theft via email	Patch, enforce strong TLS
700–749	TCP/UDP	Various (EPP, Kerberos admin, etc.)	Credential-related	Privilege escalation	Use modern, encrypted protocols
999	TCP	ScimoreDB	Rare, poorly supported	SQL injection, exposure	Block externally, patch or segment access
1002	TCP	Opsware agent (Cogbot)	Unofficial, potential agent compromise	Unauthorized control of systems	Restrict to known agents, monitor traffic
1010	TCP	ThinLinc Web Administration	Web admin interface exposure	Unauthorized admin access	Use strong auth, IP restriction, HTTPS
1023–1024	TCP/UDP	Reserved ports	Unused or system ports, potential exploitation	Denial of service, info leakage	Block unless specifically required
1025–1029	TCP	NFS, IIS, Teradata, Microsoft DCOM	Legacy services, remote code execution	Remote compromise, privilege escalation	Use latest patches, restrict access, network segmentation
1030	TCP	services.exe (Windows service)	Unofficial, may be exploited in attacks	Privilege escalation	Harden Windows, monitor unusual activity
1058–1059	TCP/UDP	IBM AIX Network Installation Manager (NIM)	Potential for unauthorized installs	Unauthorized system changes	Restrict to management subnet, enforce authentication
1064	TCP	lsass.exe-related (Windows Security)	Target for credential theft	Account compromise	Patch, enable MFA, monitor logs
1080	TCP	SOCKS proxy	Open proxy risk	Proxy abuse for anonymizing attacks	Restrict proxy use, authenticate users
1085	TCP/UDP	WebObjects (Apple)	Application vulnerabilities	Remote code execution	Patch, firewall restrictions
1098–1099	TCP/UDP	RMI Activation/Registry	Java RMI remote code execution	System takeover	Restrict Java RMI exposure, use firewall rules
1119	TCP/UDP	Blizzard games	Game server exploits, botnet risk	Service disruption	Restrict gaming traffic, monitor
1140	TCP/UDP	AutoNOC protocol	Network management exposure	Reconnaissance	Restrict management ports
1167	UDP	Conference calling	Audio interception, DoS	Privacy breach, service disruption	Encrypt, monitor unusual traffic
1176	TCP	Home automation server	IoT device exploitation	Network pivot	Use strong authentication, network segmentation
1194	TCP/UDP	OpenVPN	VPN vulnerabilities	Unauthorized network access	Use strong encryption, updated VPN software
1214	TCP	Kazaa (file sharing)	P2P network risks, malware	Data leakage, malware spread	Block P2P unless business justified
1234	TCP/UDP	Mercurial, Git, VLC media player	Code repository, media streaming exploits	Unauthorized code access, DoS	Restrict access, monitor data exfiltration
1241	TCP/UDP	Nessus Security Scanner	Scanner detected by attackers	Target for attackers	Use scanner within isolated environment
1270	TCP/UDP	Microsoft System Center Operations Manager	Unauthorized monitoring agent use	Reconnaissance, data leak	Restrict to trusted hosts, strong auth
1293	TCP/UDP	IPSec	VPN and encryption issues	Traffic interception, MITM	Strong keys, patch VPN endpoints
1301–1309	TCP	Various (OBDNet, Dell OpenManage, JTAGd)	Management interfaces exposed	Remote control, info leak	Restrict to management network
1337	TCP/UDP	Men and Mice DNS, WASTE file sharing	DNS poisoning, P2P abuse	Network disruption, data leakage	Restrict, monitor DNS and file-sharing traffic
1341–1344	TCP/UDP	Qubes MES, ICAP	Application-specific vulnerabilities	Data corruption, exposure	Patch, restrict usage
1352	TCP	IBM Lotus Notes/Domino RPC	Remote code execution	Email server compromise	Patch, limit exposure
1414	TCP	IBM WebSphere MQ	Messaging queue exposure	Data interception	Encrypt MQ traffic, restrict access
1433–1434	TCP/UDP	Microsoft SQL Server	SQL injection, brute force	Database compromise	Use firewalls, patch SQL Server, use strong auth
1470	TCP	SolarWinds Kiwi Log Server	Log server compromise	Loss of logs, data breach	Restrict access, monitor logs
1494	TCP/UDP	Citrix XenApp ICA Protocol	Remote desktop access risks	Unauthorized desktop access	Use MFA, patch Citrix, limit exposure
1500–1501	TCP/UDP	IBM Tivoli Storage Manager	Backup system exposure	Data loss, ransomware entry	Restrict access, secure backups
1512–1513	TCP/UDP	Windows WINS, Garena Gaming Client	Legacy name service risks, gaming client abuse	Network spoofing, DoS	Disable if unused, restrict gaming traffic
1521	TCP	Oracle Database Listener	SQL injection, brute force	Database compromise	Patch, use firewall, strong authentication
1524–1527	TCP/UDP	Ingres DB, Apache Derby	Database vulnerabilities	Data loss or corruption	Restrict access, patch
1533	TCP	IBM Sametime IM	Messaging vulnerabilities	Data leakage, account compromise	Use encrypted communication, patch
1547–1550	TCP/UDP	Laplink, Image Storage License Manager	Legacy protocol exploitation	Unauthorized access	Disable if unused, patch
1580–1583	TCP/UDP	IBM Tivoli Storage Manager web interface	Web UI vulnerabilities	Admin access compromise	Use HTTPS, restrict IPs, strong auth
1589	UDP	Cisco VLAN Query Protocol	VLAN spoofing	Network segmentation bypass	Use secure VLAN management
1590	TCP	GE Smallworld Datastore	Proprietary DB vulnerabilities	Data loss or corruption	Restrict access, patch
1627	TCP	iSketch (Unofficial)	Unknown/unofficial service	Unknown, possible unauthorized access	Block unless explicitly required
1628–1629	TCP/UDP	LonWorks Remote Network Interface (RNI) and IP tunneling (ANSI EIA/CEA-852)	Industrial control protocol exposure	ICS/SCADA network compromise	Isolate ICS networks, restrict access, monitor logs
1645	TCP/UDP	Old RADIUS authentication port (Legacy)	Authentication bypass if used instead of 1812	Unauthorized network access	Prefer port 1812; restrict legacy ports
1646	TCP/UDP	Old RADIUS accounting port (Legacy)	Unauthorized accounting info disclosure	Misuse of accounting info, network misuse	Prefer port 1813; restrict legacy ports
1666	TCP	Perforce (Unofficial)	Code repository exposure	Code theft or tampering	Restrict to trusted users, use authentication
1677	TCP/UDP	Novell GroupWise clients (Official)	Legacy messaging vulnerabilities	Email/data compromise	Patch, restrict exposure
1688	TCP	Microsoft Key Management Service (KMS) Windows Activation	Exploitable for license fraud or DoS	Service disruption, license abuse	Restrict to internal, authorized clients
1700	UDP	Cisco RADIUS Change of Authorization for TrustSec (Unofficial)	Unauthorized access/control risk	Network policy bypass	Restrict to Cisco TrustSec devices
1701	UDP	Layer 2 Forwarding Protocol (L2F) & Layer 2 Tunneling Protocol (L2TP) (Official)	VPN tunnel hijacking or interception	Unauthorized network access	Use strong encryption, updated VPN software
1707	TCP/UDP	Windward Studios, Romtoc Multiplayer Client (Unofficial)	Application vulnerabilities	Remote code execution, game server compromise	Restrict to trusted IPs, monitor traffic
1716	TCP	America’s Army MMO (Unofficial)	Gaming service abuse	DDoS or unauthorized access	Restrict unless gaming traffic is needed
1719–1720	UDP/TCP	H.323 Registration and Call signaling (Official)	VoIP protocol vulnerabilities	Call interception, DoS	Use encrypted signaling, restrict access
1723	TCP/UDP	Microsoft PPTP VPN protocol (Official)	Weak encryption (PPTP known vulnerabilities)	VPN compromise, unauthorized access	Use stronger VPN protocols (IKEv2, OpenVPN)
1725	UDP	Valve Steam Client (Unofficial)	Gaming client exploits	Malware, network misuse	Restrict gaming-related ports
1755	TCP/UDP	Microsoft Media Services (MMS streaming) (Official)	Media streaming abuse	Bandwidth exhaustion, content spoofing	Restrict access, monitor streaming traffic
1761–1762	TCP/UDP	cft-0, Novell Zenworks Remote Control (Unofficial)	Remote control vulnerabilities	Unauthorized remote control	Restrict to trusted hosts, enforce authentication
1768	TCP/UDP	cft-1 to cft-7 (Official)	Network monitoring protocol exposure	Reconnaissance, info leak	Restrict access, monitor traffic
1776	TCP/UDP	Federal Emergency Management Information System (Official)	Sensitive government system exposure	Data leak, system disruption	Restrict to authorized users and networks
1792	TCP/UDP	Moby (Unofficial)	Unknown/unofficial service	Unknown	Block unless required
1801	TCP/UDP	Microsoft Message Queuing (MSMQ) (Official)	Message queue spoofing, DoS	Message tampering or denial of service	Use encryption, authentication, restrict access
1812	TCP/UDP	RADIUS authentication (Official)	Credential interception	Unauthorized network access	Use secure shared secrets, restrict source IPs
1813	TCP/UDP	RADIUS accounting (Official)	Accounting data leakage	Network misuse, billing inaccuracies	Restrict access, encrypt accounting messages
1863	TCP	Microsoft Notification Protocol (MSNP) (Official)	Instant Messaging vulnerabilities	Phishing, malware distribution	Patch clients, restrict unnecessary IM traffic
1883	TCP/UDP	MQTT (Message Queue Telemetry Transport) (Official)	IoT message interception	IoT device compromise	Use TLS, strong auth, isolate IoT network
1886	TCP	Leonardo over IP (Unofficial)	Unknown/unofficial	Unknown	Block unless required
1900	UDP	Microsoft SSDP (UPnP discovery) (Official)	UPnP exploitation	Device discovery by attackers	Block from WAN, restrict internally
1920	TCP	IBM Tivoli monitoring console (Unofficial)	Monitoring data exposure	Reconnaissance, info leak	Restrict access, use VPN
1935	TCP	Adobe Flash RTMP streaming (Official)	Streaming protocol exploits	Data injection, DoS	Restrict, disable if not needed
1947	TCP/UDP	SentinelSRM, Aladdin HASP License Manager (Official)	License manager exposure	License theft, software tampering	Restrict access, monitor traffic
1967	UDP	Cisco IOS IP Service Level Agreements (Unofficial)	Network monitoring data exposure	Reconnaissance	Restrict access, monitor
1972	TCP/UDP	InterSystems Caché (Official)	Database access vulnerabilities	Data breach, privilege escalation	Use strong auth, restrict network exposure
1977	UDP	Cisco TCO (Documentation) (Official)	Documentation exposure	Info leakage	Restrict access
1984	TCP	Big Brother / Xymon Network Monitor (Official)	Monitoring system compromise	Reconnaissance, data tampering	Restrict access, patch
1985	UDP	Cisco HSRP (Hot Standby Router Protocol) (Official)	Network spoofing	Network disruption	Use secure HSRP configuration, restrict access
1992–1993	TCP/UDP	Bobwillneverdie Multiplayer (Unofficial)	Game server exploits	DDoS, unauthorized access	Restrict unless gaming required
1994	TCP/UDP	Cisco STUN-SDLC (Serial Tunneling) (Official)	Tunnel exploitation	Unauthorized data tunneling	Restrict access, monitor tunnels
1997	TCP	Chizmo Networks Transfer Tool (Unofficial)	Unknown/unofficial	Unknown	Block unless required
1998	TCP/UDP	Cisco X.25 over TCP (XOT) (Official)	Legacy protocol exposure	Reconnaissance, DoS	Restrict access, disable if unused
2000	TCP/UDP	Cisco SCCP (Skinny Client Control Protocol) (Official)	VoIP vulnerabilities	Call interception, unauthorized access	Use encryption, restrict access
2001	UDP	CAPTAN Test Stand System (Unofficial)	Unknown/unofficial service	Potential exploitation, info leakage	Block unless explicitly needed
2002	TCP	Secure Access Control Server (ACS) for Windows (Unofficial)	Access control system exposure	Unauthorized access to secure systems	Restrict to trusted IPs, use strong authentication
2008	TCP	Stylex Secured Server (Unofficial)	Unknown/unofficial service	Possible unauthorized access	Block unless required
2010	TCP	Artemis: Spaceship Bridge Simulator (Unofficial)	Game server vulnerabilities	DDoS, remote code execution	Restrict access to known users
2014	TCP	Remoticus (Unofficial)	Remote access tool, potential for abuse	Unauthorized remote control	Use VPN, strong authentication, restrict exposure
2030	TCP	Oracle Services for Microsoft Transaction Server (Unofficial)	Legacy/unofficial services exposure	Data leakage, unauthorized access	Restrict or block if unused
2031	TCP/UDP	Mobrien Chat (Official)	Chat service vulnerabilities	Data leakage, phishing	Monitor traffic, restrict access
2041	TCP	Mail.Ru Agent Communication Protocol (Unofficial)	Messaging service exploitation	Malware propagation, phishing	Restrict or block unless needed
2049	TCP/UDP	Network File System (NFS) (Official)	File sharing protocol vulnerabilities	Unauthorized file access, data exfiltration	Use strong auth, network segmentation
2053	TCP	knetd Kerberos De-multiplexor (Unofficial)	Kerberos-related exploits	Authentication bypass, unauthorized access	Use up-to-date Kerberos, restrict access
2055	TCP/UDP	Iliad-Odyssey Protocol (Official)	Unknown risks	Possible info leakage or DoS	Restrict if unused
2056	UDP	Civilization 4 Multiplayer (Unofficial)	Game server risks	DDoS, unauthorized game access	Restrict or block
2074	TCP/UDP	Vertel VMF SA (Official)	Voice or data service exposure	Eavesdropping, data injection	Restrict, monitor traffic
2080	TCP/UDP	Autodesk NLM (FLEXlm License Manager) (Official)	License server compromise	License theft, service disruption	Restrict to authorized users
2082–2083	TCP	CPanel Default and Secure Radius Service (Unofficial/Official)	Web hosting control panel exposure	Account takeover, unauthorized hosting changes	Use SSL, restrict IPs
2086–2087	TCP	GNUnet, WebHost Manager Default and SSL (Official/Unofficial)	Web hosting management vulnerabilities	Unauthorized control panel access	Strong passwords, 2FA, IP restrictions
2095–2096	TCP	CPanel Webmail Default and SSL (Unofficial)	Email access vulnerabilities	Email compromise	Use encrypted connections, monitor logs
2100	TCP	Warzone 2100 Multiplayer (Unofficial)	Gaming service vulnerabilities	DDoS, remote exploits	Restrict or block
2102–2105	TCP/UDP	Project Athena Zephyr Notification Services, IBM MiniPay, Kerberos Rlogin (Official/Unofficial)	Legacy protocols, remote login vulnerabilities	Unauthorized remote access	Disable if unused, strong authentication
2115	TCP/UDP	MIS Department (Unofficial)	Unknown/unofficial	Unknown	Block unless necessary
2121	TCP	FTP Proxy (Unofficial)	FTP vulnerabilities	Credential theft, data interception	Prefer secure FTP (SFTP), restrict access
2142	UDP	TDMoIP (RFC 5087) (Official)	Tunneling vulnerabilities	Data interception	Use encryption, restrict access
2144–2145	TCP	Iron Mountain LiveVault Agent (Unofficial)	Backup agent access risks	Data theft, ransomware	Restrict to backup systems, use authentication
2156	UDP	Talari Reliable Protocol (Official)	Voice/data protocol exposure	Eavesdropping, DoS	Restrict and monitor traffic
2160–2161	TCP	APC Agent (Official)	Power management vulnerabilities	Unauthorized device control	Restrict access, patch systems
2179	TCP	VMConnect to Hyper-V Hosts (Official)	Virtual machine management exposure	VM compromise	Restrict to trusted admins, use MFA
2181	TCP/UDP	EForward Document Transport System (Official)	Document transfer risks	Data leakage	Use encryption, restrict access
2190–2196	UDP/TCP	TiVoConnect Beacon, Apple Push Notification (Unofficial)	Notification service abuse	DoS, info leakage	Restrict exposure, monitor traffic
2200	UDP	Tuxanci Game Server (Unofficial)	Gaming-related vulnerabilities	DDoS, unauthorized access	Restrict or block
2210–2212	TCP/UDP	NOAAPORT Broadcast, MikroTik Remote/Secure Management, LeeCO POS Server	Broadcast and remote management vulnerabilities	Unauthorized device or system control	Use VPN, restrict IPs
2219–2223	TCP/UDP	NetIQ Protocols, ESET Antivirus Updates, DirectAdmin (Unofficial/Official)	Management protocol vulnerabilities	Remote compromise, malware update tampering	Use encryption, restrict access
2261–2262	TCP/UDP	CoMotion Master and Backup (Official)	Collaboration system exposure	Data loss or tampering	Restrict to trusted users
2301–2305	TCP/UDP	HP System Management, ArmA/Halo Multiplayer (Unofficial)	Legacy management and gaming ports	Unauthorized access, DDoS	Restrict to required users, block if unused
2323	TCP	Philips TVs JointSPACE (Unofficial)	IoT device exposure	Device compromise	Isolate IoT network
2345	TCP	Symon Communications (Unofficial)	Unknown/unofficial	Unknown	Block unless needed
2368–2370	TCP	Ghost Blogging Platform, BMC Control-M Server (Official)	Web service and control server vulnerabilities	Unauthorized control, data breach	Restrict, patch
2375–2376	TCP	Docker REST API (Plain & SSL) (Official)	Remote Docker API exposure	Container compromise	Use SSL (2376), restrict IPs, authentication
2379	TCP	KGS Go Server (Unofficial)	Unknown/unofficial	Unknown	Block unless needed
2381	TCP	HP Insight Manager Web Server (Unofficial)	Management interface exposure	Unauthorized system access	Restrict access
2399	TCP	FileMaker Data Access Layer (ODBC/JDBC)	Database access risks	Data exfiltration, SQL injection	Use encryption, restrict database access
2401	TCP	CVS version control system	Unauthorized source code access, information disclosure	Code leak, IP theft, intellectual property loss	Restrict access, require authentication, monitor logs
2404	TCP	IEC 60870-5-104 (electric power telecontrol)	Critical infrastructure protocol; DoS, spoofing	Disruption of power control, safety risks	VPN or isolated network, strict ACLs, continuous monitoring
2420	UDP	Westell Remote Access	Unauthorized remote access, potential exploitation	Compromise of remote systems, data theft	Limit IP ranges, strong authentication
2424	TCP	OrientDB binary client connections	DB injection, data leakage	Data breach, unauthorized DB access	Enforce encryption, authentication, firewall restrictions
2427	UDP	Cisco MGCP	VoIP intercept or abuse	Call interception, voice fraud	Restrict to known devices, monitor VoIP traffic
2447	TCP/UDP	OpenView NNM daemon	Network management service vulnerabilities	Network management disruption	Patch regularly, restrict access
2463	TCP/UDP	LSI RAID Management	Hardware management exploitation	RAID manipulation, data loss	Use internal networks only, secure credentials
2480	TCP	OrientDB HTTP client	Data exposure, injection attacks	Data breach, remote code execution	Authentication, HTTPS, firewall filtering
2483-2484	TCP/UDP	Oracle DB listener (2483 unsecured, 2484 SSL secured)	DB access compromise, data leakage	Data breach, DB takeover	Use only 2484 (SSL), strong authentication, patch DB
2500-2501	TCP	TheosMessenger client connections	Messaging interception or abuse	Data leakage, communication interception	Restrict IPs, encrypt traffic
2518	TCP/UDP	Willy	Unknown / legacy protocol risk	Potential unknown exploit	Restrict or disable if unused
2525	TCP	SMTP alternate port	Email relay abuse, spam, phishing	Spam campaigns, phishing attacks	Use email authentication (SPF, DKIM), limit source IPs
2535	TCP	MADCAP - Multicast Address Dynamic Client Allocation Protocol	Multicast attacks, amplification	Network congestion, DDoS amplification	Restrict multicast to trusted segments
2540-2541	TCP/UDP	LNS/OpenLNS remote server, LonTalk/IP	Remote access abuse, protocol exploits	Unauthorized access to network devices	VPN access, IP whitelisting
2546	TCP/UDP	EVault data protection services	Data loss, backup service attacks	Data destruction or theft	Secure backup networks, encrypt data
2593	TCP/UDP	RunUO – Ultima Online server	Game server abuse	Server compromise, cheating	Restrict access, monitor unusual traffic
2598	TCP	Citrix ICA with Session Reliability	Remote code execution, credential theft	Remote takeover of Citrix sessions	VPN-only access, patch Citrix servers
2599	TCP	SonicWALL anti-spam traffic	Traffic interception	Anti-spam system bypass or data interception	Restrict to known SonicWALL IPs
2610	TCP	TrackiT mobile device monitoring	Data leakage, unauthorized monitoring	Privacy breach, data theft	Secure endpoint communication
2612	TCP/UDP	QPasa from MQSoftware	Messaging interception	Data leakage, system compromise	Encrypted channels, authentication
2636	TCP	Solve Service	Service disruption, exploitation	Service downtime or abuse	Patch regularly, restrict access
2638	TCP	SQL Anywhere database server	DB compromise, data exfiltration	Data breach, database takeover	Strong auth, patch DB, restrict IP
2641-2642	TCP/UDP	HDL Server / Tragic	Unknown/legacy protocol risks	Potential unknown exploits	Disable if unused, restrict access
2698	TCP/UDP	Citel / MCK IVPIP	Telephony or VoIP protocol abuse	Call interception, fraud	Network segmentation, restrict access
2700-2800	TCP	P2P, spam detection, XBT Tracker	Malware spread, P2P abuse	Malware propagation, bandwidth abuse	Block P2P ports unless explicitly required
2735	TCP/UDP	NetIQ Monitor Console	Management console exploitation	Unauthorized admin access	Secure console access, restrict IPs
2809	TCP/UDP	CORBA iiop / IBM WebSphere default ports	Remote code execution, service abuse	Application compromise	Restrict access, patch software
2811	TCP	GridFTP specification gsi ftp	Data leakage, unauthorized file transfer	Data breach, data loss	Use encryption, restrict IPs
2827	TCP	I2P Basic Open Bridge API	Anonymity network abuse	Abuse for anonymized malicious traffic	Block or restrict to authorized users
2868	TCP/UDP	Norman Proprietary Event Protocol (NPEP)	Proprietary protocol abuse	System monitoring evasion	Restrict to trusted endpoints
2944-2945	UDP	Megaco H.248 protocol (text/binary)	VoIP signaling attacks	VoIP hijacking, call fraud	Secure VoIP infrastructure
2947	TCP	gpsd GPS daemon	Location data exposure	Privacy breach	Restrict access
2948-2949	TCP/UDP	WAP-push MMS & secure MMS	Mobile messaging abuse	Spam, malware distribution	Network segmentation
2967	TCP	Symantec AntiVirus Corporate Edition	AV management compromise	AV disablement, malware persistence	Patch, restrict management access
3000-3008	TCP/UDP	Development servers (Cloud9, Ruby on Rails, Miralix)	Dev environment exposure, code injection	Code compromise, lateral movement	Isolate dev environments, restrict to trusted IPs
3017	TCP	Miralix IVR and Voicemail	VoIP abuse	Call fraud, data theft	Network segmentation, patching
3020	TCP/UDP	CIFS / SMB	Lateral movement, data theft	Credential theft, lateral spread	Block externally, restrict internal access, monitor traffic
3025	TCP	netpd.org	Unknown / legacy risks	Unknown risk	Restrict/block if unused
3030	TCP/UDP	NetPanzer	Unknown P2P / gaming traffic	Bandwidth abuse, unknown	Restrict/block unless necessary
3040	TCP/UDP	GoLabs Update Port / Project Open Cannibal Update Port	Software update spoofing	Malware updates, supply chain attacks	Authenticate updates, restrict IPs
3050-3052	TCP/UDP	Interbase/Firebird DB, Galaxy Server, APC PowerChute	DB compromise, server abuse	Data breach, server control	Secure authentication, patch, network segmentation
3071	TCP/UDP	Call of Duty Black Ops game port	Game server abuse	Server hijack, DDoS	Restrict access to gaming servers only
3074	TCP/UDP	Xbox LIVE / Games for Windows – Live	DDoS, abuse	Service disruption, account compromise	Restrict to trusted gaming endpoints
3100	TCP	SMAUSA OpCon Scheduler (default listen port)	Unauthorized scheduler access, privilege escalation	Task scheduling compromise	Restrict to trusted IPs, enable authentication
3101	TCP	BlackBerry Enterprise Server communication	Data interception, man-in-the-middle (MITM)	Data leak, disruption	Use encryption, restrict access to authorized devices
3119	TCP	D2000 Entis/Actis Application Server	Application exploits, injection attacks	Application downtime, data breach	Apply patches, WAF, monitor unusual activity
3128	TCP	Squid proxy default port / Tatsoft client connection	Proxy misuse, open relay attacks	Data exfiltration, lateral movement	Limit to internal use, require authentication
3141	TCP	devpi Python package server	Package poisoning, unauthorized upload	Supply chain compromise	Authenticate users, scan packages for malware
3162	TCP/UDP	Standard Floating License Manager (SFLM)	License abuse, unauthorized access	License theft, service disruption	Limit access, monitor license usage
3225	TCP/UDP	FCIP (Fibre Channel over IP)	Storage network attacks, spoofing	Data corruption/loss	Use secure channels, isolate storage networks
3233 - 3235	TCP/UDP	WhiskerControl, Galaxy Network Service	Control protocol attacks, command injection	Network service compromise	Restrict to known hosts, enable authentication
3260	TCP	iSCSI target	Storage access attacks, data theft	Data breach, ransomware	Use CHAP authentication, restrict access
3268 - 3269	TCP/UDP	Microsoft Global Catalog (LDAP and LDAP over SSL)	LDAP injection, credential theft	AD compromise, privilege escalation	Enforce LDAP signing/encryption, limit access
3283	TCP	Apple Remote Desktop reporting	Remote access exploitation	Unauthorized remote control	Enable MFA, restrict network scope
3290	UDP	VATSIM voice communication	Voice traffic interception	Privacy breaches	Use encryption, limit to trusted endpoints
3305 - 3306	TCP/UDP	Odette FTP / MySQL Database	SQL injection, database compromise	Data loss, service disruption	Patch DB servers, use firewall rules, monitor queries
3333	TCP	Various: Eggdrop IRC bot, Network Caller ID, CruiseControl	Botnet control, unauthorized remote control	Network abuse	Restrict access, monitor connections
3389	TCP/UDP	Microsoft RDP (Remote Desktop Protocol)	Brute force attacks, credential theft	Full system compromise	Use Network Level Authentication, limit IPs, MFA
3478	TCP/UDP	STUN/TURN for NAT traversal	NAT traversal abuse, potential DoS	Service disruption	Restrict to needed apps, monitor usage
3535	TCP	SMTP alternate port	Spam relay, mail spoofing	Reputation damage, blacklisting	Use authenticated SMTP, monitor outbound traffic
3544	UDP	Teredo tunneling (IPv6 tunneling)	Tunnel abuse for bypassing firewall policies	Data exfiltration, bypass control	Block if not needed, monitor traffic
3632	TCP	Distributed compiler	Code injection, remote execution	Code compromise	Restrict access, authenticate users
3689	TCP	Digital Audio Access Protocol (DAAP)	Unauthorized media access	Data privacy breach	Restrict to trusted users and devices
3690	TCP/UDP	Subversion (SVN) version control	Repository tampering, unauthorized access	Source code compromise	Enforce strong authentication, audit logs
3724	TCP/UDP	Blizzard games communication	Service abuse, DoS	Service disruption	Restrict to gaming environments
3784 - 3785	TCP/UDP	VoIP services (Ventrilo)	Eavesdropping, VoIP abuse	Confidentiality breach	Use encryption, limit to authorized users
3899	TCP	Remote Administrator	Remote control abuse, unauthorized access	System compromise	Use strong auth, restrict access
4444	TCP/UDP	Oracle WebCenter Content / Metasploit default listener	Exploitation via Metasploit attacks	System takeover	Close if not used, monitor for unusual activity
4500	UDP	IPSec NAT Traversal	VPN tunneling abuse, bypassing firewall policies	Network intrusion	Use secure VPN configs, monitor traffic
4662	TCP/UDP	OrbitNet Message Service / eMule	P2P abuse, malware distribution	Bandwidth abuse, malware spread	Block or restrict P2P traffic
4899	TCP/UDP	Radmin remote administration tool	Unauthorized remote access	System compromise	Use strong authentication, restrict IP addresses



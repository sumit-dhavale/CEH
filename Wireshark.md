# ============================================================
# WIRESHARK QUICK REFERENCE
# Network Analysis • PCAP Analysis • Malware Analysis
# ============================================================

> Capture • Analyze • Filter • Extract • Investigate

---

# ============================================================
# OPENING PCAP FILE
# ============================================================

File
 ↓
Open
 ↓
Select .pcap / .pcapng

OR

Ctrl + O

---

# ============================================================
# ESSENTIAL DISPLAY FILTERS ⭐⭐⭐⭐⭐
# ============================================================

| Protocol | Filter |
|----------|--------|
| TCP | tcp |
| UDP | udp |
| HTTP | http |
| HTTPS / TLS | tls |
| DNS | dns |
| ICMP | icmp |
| ARP | arp |
| FTP | ftp |
| FTP-DATA | ftp-data |
| SMB | smb |
| SMB2 | smb2 |
| SSH | ssh |
| Telnet | telnet |
| DHCP | bootp |
| Kerberos | kerberos |
| LDAP | ldap |
| SMTP | smtp |
| POP3 | pop |
| IMAP | imap |
| SIP | sip |
| RTP | rtp |

---

# ============================================================
# PORT FILTERS
# ============================================================

| Service | Filter |
|----------|--------|
| FTP | tcp.port==21 |
| SSH | tcp.port==22 |
| Telnet | tcp.port==23 |
| SMTP | tcp.port==25 |
| DNS | tcp.port==53 or udp.port==53 |
| HTTP | tcp.port==80 |
| POP3 | tcp.port==110 |
| IMAP | tcp.port==143 |
| SNMP | udp.port==161 |
| LDAP | tcp.port==389 |
| HTTPS | tcp.port==443 |
| SMB | tcp.port==445 |
| RDP | tcp.port==3389 |
| VNC | tcp.port==5900 |

---

# ============================================================
# IP FILTERS
# ============================================================

Source IP

ip.src==192.168.1.10

Destination IP

ip.dst==192.168.1.20

Both

ip.addr==192.168.1.10

---

# ============================================================
# TCP FILTERS
# ============================================================

SYN

tcp.flags.syn==1

ACK

tcp.flags.ack==1

RST

tcp.flags.reset==1

FIN

tcp.flags.fin==1

PSH

tcp.flags.push==1

Retransmissions

tcp.analysis.retransmission

Lost Segments

tcp.analysis.lost_segment

---

# ============================================================
# HTTP ANALYSIS
# ============================================================

HTTP GET

http.request.method=="GET"

HTTP POST

http.request.method=="POST"

Host

http.host

URI

http.request.uri

Response

http.response

Status Code

http.response.code

User-Agent

http.user_agent

Cookies

http.cookie

Authorization Header

http.authorization

---

# ============================================================
# DNS ANALYSIS
# ============================================================

All DNS

dns

Queries

dns.qry.name

Responses

dns.resp.name

A Record

dns.a

AAAA Record

dns.aaaa

MX Record

dns.mx.mail_exchange

TXT Record

dns.txt

---

# ============================================================
# FTP ANALYSIS
# ============================================================

ftp

FTP Commands

ftp.request.command

FTP Username

USER

FTP Password

PASS

Right Click

↓

Follow TCP Stream

---

# ============================================================
# SMTP ANALYSIS
# ============================================================

smtp

AUTH LOGIN

MAIL FROM

RCPT TO

DATA

---

# ============================================================
# DHCP
# ============================================================

bootp

Look For

Discover

Offer

Request

ACK

---

# ============================================================
# ICMP
# ============================================================

All ICMP

icmp

Echo Request

icmp.type==8

Echo Reply

icmp.type==0

Destination Unreachable

icmp.type==3

Time Exceeded

icmp.type==11

---

# ============================================================
# ARP
# ============================================================

arp

Who Has

arp.opcode==1

Reply

arp.opcode==2

---

# ============================================================
# KERBEROS
# ============================================================

kerberos

Look For

AS-REQ

AS-REP

TGS-REQ

TGS-REP

---

# ============================================================
# SMB
# ============================================================

smb

smb2

Tree Connect

Session Setup

NTLM Authentication

---

# ============================================================
# TLS / HTTPS
# ============================================================

tls

Certificates

tls.handshake.certificate

Server Name (SNI)

tls.handshake.extensions_server_name

---

# ============================================================
# FOLLOW STREAM ⭐⭐⭐⭐⭐
# ============================================================

Right Click Packet

↓

Follow

↓

TCP Stream

OR

UDP Stream

Useful For

✔ HTTP Requests

✔ FTP Logins

✔ Telnet Sessions

✔ Chat Messages

✔ Plain Text Credentials

---

# ============================================================
# EXPORT OBJECTS ⭐⭐⭐⭐⭐
# ============================================================

File

↓

Export Objects

↓

HTTP

SMB

DICOM

TFTP

Useful For

✔ Images

✔ Documents

✔ Malware Samples

✔ ZIP Files

---

# ============================================================
# STATISTICS MENU ⭐⭐⭐⭐⭐
# ============================================================

Statistics

↓

Protocol Hierarchy

Shows

✔ HTTP

✔ TCP

✔ UDP

✔ SMB

✔ DNS

---

Statistics

↓

Conversations

Shows

✔ Source

✔ Destination

✔ Port

✔ Bytes

---

Statistics

↓

Endpoints

Shows

✔ IP Addresses

✔ MAC Addresses

---

Statistics

↓

IO Graph

Bandwidth Graph

---

# ============================================================
# SEARCHING
# ============================================================

Ctrl + F

Search By

✔ String

✔ Hex

✔ Packet Details

Useful Keywords

password

username

login

admin

token

cookie

Authorization

Basic

Bearer

secret

flag

---

# ============================================================
# CREDENTIAL HUNTING
# ============================================================

HTTP Login

http.request.method=="POST"

↓

Follow TCP Stream

Look For

username=

password=

---

FTP

ftp

↓

Follow TCP Stream

Look For

USER

PASS

---

SMTP

smtp

↓

AUTH LOGIN

---

Telnet

telnet

↓

Follow TCP Stream

---

POP3

pop

↓

USER

PASS

---

# ============================================================
# FILE DOWNLOADS
# ============================================================

HTTP Download

http.response

↓

Export Objects

↓

HTTP

---

SMB Download

smb

↓

Export Objects

↓

SMB

---

# ============================================================
# MALWARE ANALYSIS
# ============================================================

Look For

DNS Queries

HTTP Downloads

Executable Files

PowerShell Commands

Suspicious User-Agent

Large Data Transfers

Beaconing

---

# ============================================================
# USEFUL SHORTCUTS
# ============================================================

Ctrl + O   → Open Capture

Ctrl + E   → Start / Stop Capture

Ctrl + F   → Find

Ctrl + Shift + E → Export

Ctrl + M   → Mark Packet

Ctrl + G   → Go To Packet

---

# ============================================================
# COMMON ANALYSIS WORKFLOW
# ============================================================

Open PCAP

↓

Protocol Hierarchy

↓

Endpoints

↓

Conversations

↓

Apply Filters

↓

Follow TCP Stream

↓

Export Objects

↓

Search Credentials

↓

Answer Questions

---

# ============================================================
# MOST USED FILTERS ⭐⭐⭐⭐⭐
# ============================================================

tcp

udp

http

tls

dns

icmp

arp

ftp

smb

http.request.method=="POST"

http.request.method=="GET"

dns.qry.name

ip.addr==192.168.1.10

tcp.port==80

tcp.port==445

udp.port==53

tcp.analysis.retransmission

tls.handshake.certificate

http.user_agent

http.cookie

ftp

bootp

kerberos

---

# ============================================================
# QUICK REFERENCE
# ============================================================

Open PCAP
Ctrl + O

Find
Ctrl + F

HTTP Login
http.request.method=="POST"

DNS
dns

FTP
ftp

SMB
smb

HTTPS
tls

HTTP
http

ICMP
icmp

ARP
arp

Follow Stream
Right Click → Follow TCP Stream

Export Files
File → Export Objects

Top Talkers
Statistics → Conversations

Protocols
Statistics → Protocol Hierarchy

Hosts
Statistics → Endpoints

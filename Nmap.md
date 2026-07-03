# ============================================================
# NMAP - CEH PRACTICAL CHEAT SHEET
# ============================================================

# ------------------------------------------------------------
# 1. HOST DISCOVERY
# ------------------------------------------------------------

# Ping Scan (Find Live Hosts)
nmap -sn 192.168.1.0/24

# ARP Scan (Local Network)
sudo arp-scan -l

# No Ping
nmap -Pn 192.168.1.10


# ------------------------------------------------------------
# 2. BASIC SCANS
# ------------------------------------------------------------

# Default Scan
nmap 192.168.1.10

# Service Version
nmap -sV 192.168.1.10

# OS Detection (Root)
sudo nmap -O 192.168.1.10

# Aggressive Scan (Best for Single Host)
sudo nmap -A 192.168.1.10

# Save All Formats
nmap -A 192.168.1.10 -oA scan

# Save Normal Output
-oN result.txt

# Save XML
-oX result.xml

# Save Grepable
-oG result.gnmap


# ------------------------------------------------------------
# 3. PORT SCANNING
# ------------------------------------------------------------

# Top 1000 Ports
nmap 192.168.1.10

# All TCP Ports
nmap -p- 192.168.1.10

# Fast Full Scan
nmap -Pn -T4 -p- 192.168.1.10

# Service Detection on All Ports
nmap -Pn -p- -sV 192.168.1.10

# Specific Port
nmap -p 80 192.168.1.10

# Multiple Ports
nmap -p 21,22,80,445 192.168.1.10

# Port Range
nmap -p 1-1000 192.168.1.10


# ------------------------------------------------------------
# 4. UDP SCAN
# ------------------------------------------------------------

# Full UDP
nmap -sU 192.168.1.10

# Top 100 UDP
nmap -sU --top-ports 100 192.168.1.10

# SNMP
nmap -sU -p161 192.168.1.10

# DNS
nmap -sU -p53 192.168.1.10


# ------------------------------------------------------------
# 5. VERSION / OS
# ------------------------------------------------------------

# Version Detection
nmap -sV 192.168.1.10

# Aggressive Version Detection
nmap -sV --version-intensity 9 192.168.1.10

# OS Detection
sudo nmap -O 192.168.1.10

# Aggressive Scan
sudo nmap -A 192.168.1.10


# ------------------------------------------------------------
# 6. DEFAULT NSE
# ------------------------------------------------------------

# Default Scripts
nmap -sC 192.168.1.10

# Same As
nmap --script=default 192.168.1.10

# Vulnerability Scan
nmap --script vuln 192.168.1.10


# ============================================================
# IMPORTANT NSE SCRIPTS
# ============================================================

# ---------- SMB ----------
smb-enum-shares
smb-enum-users
smb-os-discovery
smb-security-mode
smb2-security-mode
smb-vuln*

Example
nmap --script smb-enum-shares -p445 IP


# ---------- FTP ----------
ftp-anon
ftp-syst
ftp-bounce
ftp-vsftpd-backdoor

Example
nmap --script ftp-anon -p21 IP


# ---------- HTTP ----------
http-title
http-headers
http-enum
http-methods
http-server-header
http-auth-finder
http-config-backup
http-default-accounts
http-vuln*

Example
nmap --script http-title -p80 IP


# ---------- HTTPS ----------
ssl-cert
ssl-enum-ciphers
ssl-heartbleed

Example
nmap --script ssl-cert -p443 IP


# ---------- SSH ----------
ssh-auth-methods
ssh2-enum-algos
ssh-hostkey

Example
nmap --script ssh-hostkey -p22 IP


# ---------- SMTP ----------
smtp-enum-users
smtp-open-relay
smtp-commands

Example
nmap --script smtp-enum-users -p25 IP


# ---------- DNS ----------
dns-brute
dns-recursion
dns-service-discovery

Example
nmap --script dns-brute IP


# ---------- SNMP ----------
snmp-info
snmp-processes
snmp-sysdescr
snmp-win32-users

Example
nmap --script snmp-info -p161 IP


# ---------- MYSQL ----------
mysql-info
mysql-users
mysql-empty-password

Example
nmap --script mysql-info -p3306 IP


# ---------- MSSQL ----------
ms-sql-info
ms-sql-empty-password

Example
nmap --script ms-sql-info -p1433 IP


# ---------- LDAP ----------
ldap-rootdse

Example
nmap --script ldap-rootdse -p389 IP


# ---------- RPC ----------
rpcinfo

Example
nmap --script rpcinfo IP


# ---------- RPCAP ----------
nmap -p2002 -sV IP


# ---------- RDP ----------
rdp-enum-encryption
rdp-ntlm-info

Example
nmap --script rdp-ntlm-info -p3389 IP


# ---------- VNC ----------
vnc-info

Example
nmap --script vnc-info -p5900 IP


# ---------- NFS ----------
nmap --script nfs-showmount IP


# ============================================================
# SEARCH NSE SCRIPTS
# ============================================================

ls /usr/share/nmap/scripts

grep ftp /usr/share/nmap/scripts/script.db

grep smb /usr/share/nmap/scripts/script.db

grep http /usr/share/nmap/scripts/script.db

locate *.nse


# ============================================================
# TIMING
# ============================================================

-T0  Paranoid
-T1  Sneaky
-T2  Polite
-T3  Normal
-T4  Fast   ⭐
-T5  Insane


# ============================================================
# MOST COMMON CEH QUESTIONS
# ============================================================

Find Live Hosts
nmap -sn 192.168.1.0/24

Find OS
sudo nmap -O IP

Find Version
nmap -sV IP

Aggressive Scan
sudo nmap -A IP

Find FTP Anonymous
nmap --script ftp-anon -p21 IP

Find SMB Shares
nmap --script smb-enum-shares -p445 IP

Find HTTP Title
nmap --script http-title -p80 IP

Find SSL Certificate
nmap --script ssl-cert -p443 IP

Find RPCAP
nmap -p2002 -sV IP

Find Vulnerabilities
nmap --script vuln IP

Find SNMP
nmap -sU -p161 IP

Find DNS
nmap --script dns-brute IP

Find MySQL
nmap --script mysql-info -p3306 IP

Find LDAP
nmap --script ldap-rootdse -p389 IP

Find RDP Encryption
nmap --script rdp-enum-encryption -p3389 IP

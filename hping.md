# ============================================================
# HPING3 QUICK REFERENCE
# CEH • Pentesting • Network Testing
# ============================================================

> Packet Crafting • Firewall Testing • Network Troubleshooting

---

# Quick Syntax

```bash
hping3 [OPTIONS] <TARGET>
```

---

# Common Protocol Modes

| Mode | Option | Protocol |
|------|--------|----------|
| TCP | *(Default)* | TCP |
| UDP | `-2` | UDP |
| ICMP | `-1` | ICMP |
| RAW IP | `-0` | Raw IP |

---

# Frequently Used Options

| Option | Description |
|---------|-------------|
| `-S` | SYN Flag |
| `-A` | ACK Flag |
| `-F` | FIN Flag |
| `-P` | PSH Flag |
| `-R` | RST Flag |
| `-U` | URG Flag |
| `-Y` | YMAS (ECN) |
| `-p` | Destination Port |
| `-s` | Source Port |
| `-c` | Packet Count |
| `-i u1000` | Interval (1000 µs) |
| `--flood` | Send packets as fast as possible (for lab environments only) |
| `--rand-source` | Random Source IP |
| `-a` | Spoof Source IP |
| `-t` | Set TTL |
| `-d` | Payload Size |
| `-E file` | Payload From File |
| `-V` | Verbose |
| `--traceroute` | Traceroute Mode |

---

# Basic Packet Tests

### TCP SYN

```bash
hping3 -S -p 80 192.168.1.10
```

### TCP ACK

```bash
hping3 -A -p 80 192.168.1.10
```

### TCP FIN

```bash
hping3 -F -p 80 192.168.1.10
```

### TCP RST

```bash
hping3 -R -p 80 192.168.1.10
```

### TCP PSH

```bash
hping3 -P -p 80 192.168.1.10
```

### TCP URG

```bash
hping3 -U -p 80 192.168.1.10
```

---

# ICMP

### Echo Request

```bash
hping3 -1 192.168.1.10
```

### Multiple ICMP Packets

```bash
hping3 -1 -c 5 192.168.1.10
```

---

# UDP

### UDP Probe

```bash
hping3 -2 -p 53 192.168.1.10
```

### SNMP

```bash
hping3 -2 -p 161 192.168.1.10
```

### DHCP

```bash
hping3 -2 -p 67 192.168.1.10
```

---

# Traceroute

```bash
hping3 --traceroute -S -p 80 192.168.1.10
```

---

# TTL Testing

```bash
hping3 -S -p 80 -t 64 192.168.1.10
```

---

# Source Port

```bash
hping3 -S -s 12345 -p 80 192.168.1.10
```

---

# Packet Count

```bash
hping3 -S -c 10 -p 80 192.168.1.10
```

---

# Payload Size

```bash
hping3 -S -p 80 -d 120 192.168.1.10
```

---

# Read Payload From File

```bash
hping3 -E payload.bin -p 80 192.168.1.10
```

---

# Verbose Output

```bash
hping3 -V -S -p 80 192.168.1.10
```

---

# Common Service Ports

| Service | Port |
|----------|-----:|
| FTP | 21 |
| SSH | 22 |
| Telnet | 23 |
| SMTP | 25 |
| DNS | 53 |
| HTTP | 80 |
| POP3 | 110 |
| IMAP | 143 |
| SNMP | 161 |
| LDAP | 389 |
| HTTPS | 443 |
| SMB | 445 |
| MySQL | 3306 |
| RDP | 3389 |
| VNC | 5900 |

---

# Common Response Types

| Response | Meaning |
|----------|---------|
| SYN-ACK | Port appears open |
| RST | Port closed |
| No Reply | Filtered or dropped |
| ICMP Unreachable | Host or port unreachable |
| ICMP Time Exceeded | TTL expired |

---

# TCP Flag Reference

| Flag | Meaning |
|------|---------|
| SYN | Start connection |
| ACK | Acknowledge packet |
| FIN | Graceful close |
| RST | Reset connection |
| PSH | Push data |
| URG | Urgent data |

---

# Useful Packet Tests

| Goal | Example |
|------|---------|
| Test HTTP | `hping3 -S -p80 TARGET` |
| Test HTTPS | `hping3 -S -p443 TARGET` |
| Test SSH | `hping3 -S -p22 TARGET` |
| Test FTP | `hping3 -S -p21 TARGET` |
| Test SMB | `hping3 -S -p445 TARGET` |
| Test DNS | `hping3 -2 -p53 TARGET` |
| Test RDP | `hping3 -S -p3389 TARGET` |

---

# Troubleshooting

| Issue | Check |
|-------|-------|
| No Replies | Firewall or host down |
| ICMP Unreachable | Port or host unreachable |
| RST Packets | Service not listening |
| SYN-ACK | TCP service responding |

---

# Practice Labs

### Lab 1
Send 5 TCP SYN packets to port 80.

### Lab 2
Check whether SSH (22) responds.

### Lab 3
Send a UDP packet to DNS (53).

### Lab 4
Run a TCP traceroute to HTTPS (443).

### Lab 5
Compare responses from ports 22, 80 and 443.

---

# Learning Notes

- TCP is the default protocol.
- ICMP mode uses `-1`.
- UDP mode uses `-2`.
- Use `-c` to limit packet count.
- `--traceroute` helps visualize the network path.
- Adjusting TTL (`-t`) is useful for understanding packet lifetimes.

# Recon-ng 

> Author: Personal Study Notes

---

# Install

## Kali / Parrot

```bash
sudo apt update
sudo apt install recon-ng
```

Verify

```bash
recon-ng
```

---

# Start

```bash
recon-ng
```

Exit

```bash
exit
```

Help

```bash
help
```

or

```bash
?
```

---

# Workspaces

Create

```bash
workspaces create ceh
```

List

```bash
workspaces list
```

Select

```bash
workspaces select ceh
```

Remove

```bash
workspaces remove ceh
```

---

# Marketplace

Search everything

```bash
marketplace search
```

Search WHOIS

```bash
marketplace search whois
```

Search DNS

```bash
marketplace search dns
```

Search Host

```bash
marketplace search hosts
```

Search Google

```bash
marketplace search google
```

Search Bing

```bash
marketplace search bing
```

Search Certificate

```bash
marketplace search certificate
```

Search BuiltWith

```bash
marketplace search builtwith
```

---

# Install Module

```bash
marketplace install MODULE
```

Example

```bash
marketplace install recon/domains-hosts/hackertarget
```

---

# Load Module

```bash
modules load MODULE
```

Example

```bash
modules load recon/domains-hosts/hackertarget
```

---

# Module Information

```bash
info
```

---

# Module Options

```bash
options list
```

---

# Set Target

```bash
options set SOURCE example.com
```

Verify

```bash
options list
```

---

# Run Module

```bash
run
```

---

# Go Back

```bash
back
```

---

# Show Database

Domains

```bash
show domains
```

Hosts

```bash
show hosts
```

Contacts

```bash
show contacts
```

Companies

```bash
show companies
```

Credentials

```bash
show credentials
```

Locations

```bash
show locations
```

Profiles

```bash
show profiles
```

Ports

```bash
show ports
```

Leaks

```bash
show leaks
```

---

# Database Commands

Schema

```bash
db schema
```

View hosts

```bash
db query SELECT * FROM hosts;
```

View contacts

```bash
db query SELECT * FROM contacts;
```

View domains

```bash
db query SELECT * FROM domains;
```

View companies

```bash
db query SELECT * FROM companies;
```

---

# API Keys

List Keys

```bash
keys list
```

Add Key

```bash
keys add shodan_api YOUR_API_KEY
```

Delete Key

```bash
keys remove shodan_api
```

---

# Useful Modules

## WHOIS Contacts

```
recon/domains-contacts/whois_pocs
```

Purpose

- Contact Email
- Abuse Email
- Registrar Contacts

---

## Certificate Transparency

```
recon/domains-hosts/certificate_transparency
```

Purpose

- Subdomains

---

## HackerTarget

```
recon/domains-hosts/hackertarget
```

Purpose

- DNS
- Hosts
- Subdomains

---

## BuiltWith

```
recon/domains-hosts/builtwith
```

Purpose

- CMS
- Framework
- Web Technologies

---

## Google Search

```
recon/domains-hosts/google_site_web
```

Purpose

- Indexed Hosts

---

## Bing Search

```
recon/domains-hosts/bing_domain_web
```

Purpose

- Subdomains
- Hosts

---

# Common Workflow

```
Create Workspace

↓

Search Marketplace

↓

Install Module

↓

Load Module

↓

Info

↓

Options List

↓

Set SOURCE

↓

Run

↓

Show Results

↓

Back
```

---

# CEH Style Labs

## Contact Email

```bash
modules load recon/domains-contacts/whois_pocs

options set SOURCE tesla.com

run

show contacts
```

Expected Answer

```
admin@example.com
```

---

## Discover Subdomains

```bash
modules load recon/domains-hosts/certificate_transparency

options set SOURCE tesla.com

run

show hosts
```

Expected Answer

```
vpn.tesla.com
```

---

## Registrar

```bash
modules load recon/domains-contacts/whois_pocs

options set SOURCE tesla.com

run
```

or

```bash
whois tesla.com
```

Look for

```
Registrar
```

---

## Hosting Provider

```bash
host tesla.com
```

or

```bash
dig tesla.com
```

Then

```bash
whois <IP_ADDRESS>
```

Look for

```
Organization
OrgName
NetName
descr
```

---

## Web Technologies

```bash
modules load recon/domains-hosts/builtwith

options set SOURCE tesla.com

run
```

Possible Results

```
Apache
Nginx
WordPress
Drupal
PHP
Cloudflare
```

---

# Alternative Commands

Resolve Domain

```bash
host example.com
```

A Record

```bash
dig example.com A
```

MX

```bash
dig example.com MX
```

NS

```bash
dig example.com NS
```

TXT

```bash
dig example.com TXT
```

WHOIS

```bash
whois example.com
```

Reverse Lookup

```bash
dig -x IP
```

---

# Most Useful Commands

```bash
recon-ng

help

workspaces create ceh

workspaces list

workspaces select ceh

marketplace search

marketplace install MODULE

modules load MODULE

info

options list

options set SOURCE example.com

run

show hosts

show contacts

show domains

show companies

show ports

db schema

db query SELECT * FROM hosts;

back

exit
```

---

# Expected CEH Questions

✅ Find Contact Email

✅ Discover Subdomain

✅ Find Registrar

✅ Find Hosting Provider

✅ Find Company Name

✅ Find DNS Information

✅ Find MX Record

✅ Find Name Server

✅ Identify CMS

✅ Identify Web Server

✅ Identify Technologies

✅ Find SSL Information

---

# Important Notes

- Always run `info` before using a module.
- Check `options list` to see required parameters.
- Most modules require `SOURCE`.
- Results are stored in the workspace database.
- Use `show` commands or SQL queries to review collected information.
- If a module requires an API key, add it with `keys add`.

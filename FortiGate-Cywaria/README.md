# FortiGate Security Gateways (Cywaria Final Exam)
**Date:** March 27, 2024  
**Type:** Solo project

## Summary
This project is a full FortiGate perimeter and remote access configuration, completed in an exam-style lab environment (Cywaria).  
The firewall was configured end-to-end: management, routing, NAT, VPN, identity integration, access control, and monitoring.

The final deliverable included both screenshots (evidence for each task) and an exported FortiGate configuration.

---

## What Was Configured

### 1. Device Hardening
- Set the firewall hostname to my name.
- Upgraded firmware.
- Created additional admin accounts.
- Restricted admin login to specific trusted hosts.
- Enabled logging on implicit deny rules.

### 2. Network & Interfaces
- Assigned interface roles (WAN/LAN).
- Enabled DHCP on internal-facing interfaces.
- Disabled automatic default gateway pull where not appropriate.
- Configured static routes where needed for management access from outside networks.

### 3. NAT and Firewall Policies
- Outbound internet access allowed via NAT.
- Inbound management access restricted to a controlled jump box.
- Destination NAT for an internal Windows web server (external IP mapped to internal IP).
- Port forwarding set up and validated.
- Additional supporting firewall rules created and tested.

### 4. Web / FTP / Logging Policies
- Separate security policies for HTTP/HTTPS.
- Separate security policy for FTP.
- Verified that traffic hits the intended firewall policy and generates logs.
- Confirmed the policies show up properly in FortiView.

### 5. Active Directory Integration
- Integrated the FortiGate with Active Directory using LDAP bind.
- Created and added remote user groups for auth-based policy control.
- Created and tested a new user account against that auth path.
- Verified authentication results in logs.

### 6. SSL VPN
- Created user/group entries for SSL VPN users.
- Configured an SSL VPN portal.
- Configured SSL VPN settings and firewall policies.
- Connected with FortiClient, browsed the internet in Web-Only mode through the VPN.
- Captured FortiView logs confirming a successful SSL VPN session.

### 7. IPsec VPN
- Set up an IPsec VPN tunnel.
- Tested successful tunnel establishment and documented it.

---

## Skills Demonstrated
- Firewall rule design (inbound vs outbound, service-specific policies).
- NAT and port forwarding for internal services.
- AAA / identity integration: LDAP binding and AD-backed authentication groups.
- SSL VPN and IPsec VPN configuration and verification.
- Traffic visibility using FortiView and logging.
- Secure admin posture: named admin accounts + trusted host restrictions.

---

## Why This Matters
This project shows practical understanding of FortiGate configuration and policy design:

- Used DNAT and firewall rules to securely expose internal services.  
- Configured VPN access based on user identity instead of IP.  
- Enabled logging and traffic visibility through FortiView.  
- Applied the principle of least privilege in rule and policy creation.

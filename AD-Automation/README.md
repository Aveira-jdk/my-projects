# Active Directory Enterprise Environment Automation
**Date:** March 7, 2024  
**Type:** Solo project

## Objective
Simulate a realistic enterprise-scale Microsoft Active Directory environment:
- High user/computer count
- Departmental OU structure
- Core infrastructure services
- Meaningful security policies (GPOs)

All of this was done automatically using Python and PowerShell.

---

## Scale of the Environment
- **Total number of users:** 20,547  
- **Total number of computers:** 15,029  
- **Total number of servers:** 27  
- **Total number of OUs:** 52  
- **Departments modeled:** 15 (each with Users + Computers sub-OUs)

Servers included roles like:
- Domain Controller
- DNS
- DHCP
- Web Server (IIS)
- File Server
- Simple Mail Server

All running Windows Server 2019 in a lab environment.

---

## Automation Process
### 1. User and Computer Generation
- Used Python (with Faker-style data generation) to create realistic user data at scale.
- Generated CSVs for 20,000+ user accounts and 12,000+ computer objects (including simulated "server" objects).
- Imported them into AD via PowerShell in bulk.

### 2. OU Structure
- Built an OU hierarchy that mirrors a real enterprise:
  - A top-level `Departments` container
  - Per-department OUs
  - Each department OU has `Users` and `Computers` sub-OUs

### 3. Group Policy Objects (GPOs)
Deployed and linked multiple GPOs to apply security and operational controls. Examples:

- **Wallpaper Block**  
  Forces a controlled wallpaper for standardization / awareness across `Departments`.

- **Restrict SOFT Install**  
  Restricts unauthorized software installs.

- **noCMD**  
  Disables Command Prompt in specific high-risk OUs  
  (linked to `CustomerService`, `Legal`).

- **ControlPanel Restrict**  
  Restricts Control Panel access for `Medical`, `HR`, `Legal`, `QA`.

- **USB Block**  
  Disables/removes USB storage access for `HR` and `CustomerService`.

- **noREGEDIT**  
  Blocks Registry Editor in `Marketing` and `Finance`.

- **Printer PDF / Default Printing Policy**  
  Ensures standard corporate printing behavior and logging.

- **StartUpMessage**  
  Displays a startup banner to all departments.

- **Default Domain Policy / Default Domain Controllers Policy**  
  Baseline security settings for the domain and the DCs.

All GPOs were applied with `AllSettingsEnabled`, and OU linking was validated.

---

## Skills Demonstrated
- Mass provisioning in Active Directory
- PowerShell automation and bulk import
- Organizational Unit planning at scale
- GPO hardening for usability, data loss prevention, and restriction of risky tools (CMD, REGEDIT, USB)
- Core Windows services configuration (AD DS, DNS, DHCP, IIS, File services, Mail)

---

## Why This Matters
This project demonstrates understanding of large-scale Active Directory configuration:  
- Includes realistic numbers of users, computers, and OUs.  
- Uses departmental structure for access and policy management.  
- Applies GPOs that reflect common administrative and security needs.  

It shows practical experience with automation and directory design similar to enterprise environments.

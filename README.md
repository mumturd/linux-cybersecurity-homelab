# Linux Cybersecurity Homelab

## Project Overview

This project documents the creation and security assessment of a virtual Linux server using Ubuntu Server and UTM on macOS.

The purpose of this homelab was to gain hands-on experience with Linux administration, network security, vulnerability assessment, authentication monitoring, and system auditing.

I configured a virtual server, examined its network services, reviewed security logs, and used security auditing tools to evaluate its configuration.

## Lab Environment

| Component | Configuration |
|---|---|
| Host Operating System | macOS (Apple Silicon) |
| Virtualization Software | UTM |
| Guest Operating System | Ubuntu Server 24.04.5 LTS (ARM64) |
| VM Memory | 2 GB |
| VM CPU | 2 cores |
| Virtual Disk | 30 GB |
| Network | UTM Shared Network |

## Tools and Technologies

- **Ubuntu Server:** Linux system administration and security configuration.
- **UTM:** Virtualization of the Ubuntu Server environment.
- **OpenSSH:** Remote administration and public-key authentication.
- **UFW:** Host-based firewall configuration.
- **Nmap:** Network scanning and service identification.
- **Lynis:** Linux security configuration assessment.
- **Auditd:** Security event auditing and file monitoring.
- **Journalctl:** Authentication log investigation.

## 1. Virtual Machine Deployment

Created an Ubuntu Server virtual machine using UTM on an Apple Silicon Mac.

Configured virtual hardware, storage, and shared networking, then installed the operating system and applied available system updates.

The environment was designed to provide a lightweight Linux server for cybersecurity practice.

## 2. SSH Remote Administration

Installed and configured OpenSSH to remotely administer the Ubuntu server from macOS Terminal.

Created an ED25519 SSH key pair and successfully authenticated to the server using the private key stored on the host machine.

Password-based SSH authentication was retained during this project.

**Skills practiced:**
- Remote Linux administration
- SSH configuration
- Public-key authentication
- Secure access management

## 3. Firewall Configuration

Configured UFW to control network connections to the Ubuntu server.

Applied a default-deny policy for incoming connections while allowing outgoing traffic and authorized SSH access on TCP port 22.

Verified that SSH remained accessible after enabling the firewall.

## 4. Network Assessment

Used Nmap and Linux networking commands to examine the server's network services.

Identified OpenSSH listening on TCP port 22 and examined local DNS and DHCP-related services.

Used `ss -tulnp` to inspect listening sockets and the processes associated with them.

The assessment did not identify obvious unnecessary externally listening services in the reviewed output.

## 5. Security Log Analysis

Investigated SSH authentication activity using `journalctl`.

Reviewed successful password and public-key authentication events, session activity, and source IP addresses.

Searched available SSH logs for failed authentication attempts.

No matching failed authentication events were found in the available records during the investigation.

## 6. Lynis Security Audit

Installed Lynis and conducted a baseline Linux security assessment.

**Baseline results:**
- Hardening index: 62/100
- Tests performed: 255
- Firewall detected
- Security repository warning reported

Investigated the repository warning by reviewing Ubuntu's APT configuration and confirming that the `noble-security` repository was configured.

This suggested a possible false-positive finding that required manual validation.

Also verified that unattended upgrades were installed and configured for automatic package list updates and unattended upgrades.

After these checks and installing Auditd, a subsequent Lynis assessment still reported a hardening index of 62/100.

## 7. Security Auditing with Auditd

Installed and enabled Auditd to practice Linux security event monitoring.

Created a temporary audit rule to monitor a test file for writes and attribute changes.

Used `ausearch` to retrieve records associated with the custom audit key.

The retrieved records demonstrated audit event collection, including a record associated with configuring the audit rule.

## Key Findings

| Finding | Result |
|---|---|
| SSH remote access | Operational |
| SSH key authentication | Successfully tested |
| UFW firewall | Enabled |
| Network service enumeration | Completed |
| SSH authentication log analysis | Completed |
| Lynis baseline hardening index | 62/100 |
| Automatic updates | Configured |
| Auditd | Installed and running |

## Lessons Learned

This project helped me understand how Linux security controls work together.

I gained experience administering a remote server, configuring a firewall, examining network services, reviewing authentication logs, and investigating security assessment findings.

One important lesson was that security scanner warnings must be verified before making configuration changes. A hardening score alone does not determine whether a system is secure.

## Future Improvements

- Add more detailed Auditd monitoring rules.
- Perform additional security configuration assessments.
- Explore SSH hardening and authentication policies.
- Build a second isolated virtual machine for network testing.
- Document verified remediation changes with before-and-after evidence.
- Expand the lab with additional security monitoring tools.

## Project Purpose

This homelab was developed as a hands-on cybersecurity learning project to strengthen practical technical skills and demonstrate familiarity with Linux system security and administration.

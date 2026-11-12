# Cybersecurity Homelab Security Report

## 1. Project Overview

For this project, I created a virtual Ubuntu Server on my Mac using UTM. I used different cybersecurity tools to check my server's security and learn how to protect a Linux system.

The main goal was to practice basic cybersecurity skills and learn how security tools work.

## 2. Network Security

I used Nmap to scan my Ubuntu Server and see which ports were open.

I found that port 22 was open for SSH. This is the service I use to connect to Ubuntu from my Mac.

I also used UFW to set up a firewall. The firewall blocks unwanted incoming connections while still allowing SSH.

## 3. SSH Security

I set up SSH so I could access my Ubuntu Server through my Mac's Terminal.

I also created an SSH key to make logging in more secure.

I tested the key and was able to connect successfully. I kept password login enabled for now.

## 4. Security Scan with Lynis

I installed Lynis to check my Ubuntu Server for possible security problems.

**My results:**
- Hardening score: 62/100
- Tests completed: 255
- Firewall detected and enabled
- Automatic security updates configured

Lynis gave me a warning about my security update repository. I checked Ubuntu's settings and found that the security repository was already configured.

My score stayed at 62 after running another scan.

## 5. Security Logs

I used `journalctl` to look at SSH login activity.

I was able to see successful logins using passwords and SSH keys.

I also searched for failed login attempts, but none appeared in the available logs.

## 6. Auditd Monitoring

I installed Auditd to learn how Linux records security events.

I created a rule to monitor a test file and used `ausearch` to look for activity.

I was able to find audit records related to my monitoring rule.

## 7. What I Learned

This project helped me understand how to:

- Set up and manage a Linux server.
- Use SSH to connect remotely.
- Scan a network using Nmap.
- Configure a firewall.
- Check for security problems using Lynis.
- Look at login activity and system logs.
- Use Auditd to monitor system activity.

## 8. Conclusion

This homelab helped me gain hands-on cybersecurity experience. I learned how to use different security tools and understand the results they provide.

I plan to continue improving the homelab by adding more security tools and practicing new cybersecurity skills.

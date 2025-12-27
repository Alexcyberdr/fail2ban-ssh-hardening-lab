# Fail2Ban SSH Hardening Lab

## Objective
Simulate, detect, and mitigate an SSH brute-force attack using Fail2Ban on an Ubuntu VPS, documenting the full incident lifecycle as evidence of SOC Tier 1 skills.

## Environment
- OS: Ubuntu 22.04 LTS
- Service: OpenSSH
- Security Tool: Fail2Ban
- Attacker Host: Kali Linux
- VPS Provider: IONOS

## Attack Simulation
Multiple failed SSH authentication attempts were generated from an external host to simulate a brute-force attack against the SSH service.

## Detection
Authentication failures were identified in:
- `/var/log/auth.log`

Fail2Ban actively monitored these logs and tracked failed login attempts.

## Mitigation
After reaching the configured threshold (5 failed attempts within 10 minutes), Fail2Ban automatically banned the attacker IP using the `sshd` jail.

## Validation
- SSH access from the attacker host was blocked
- Ban action was logged in `/var/log/fail2ban.log`
- Access was restored after manual unban for validation purposes

## Key Commands Used
```bash
grep "Failed password" /var/log/auth.log
fail2ban-client status
fail2ban-client status sshd
grep "Ban" /var/log/fail2ban.log
fail2ban-client set sshd unbanip 73.68.xxx.xxx

Evidence

All screenshots and logs are stored in the evidence/ directory.

Lessons Learned
	•	Automated log monitoring is critical for early detection
	•	Fail2Ban effectively mitigates brute-force SSH attacks
	•	Proper thresholds balance security and availability

Future Improvements
	•	Disable root SSH login
	•	Enforce SSH key-only authentication
	•	Implement UFW firewall rules
	•	Integrate with SIEM (Wazuh)

## Step-by-Step Lab Execution

1. Baseline system validation
2. SSH service verification
3. Brute-force simulation (failed SSH attempts)
4. Detection via auth.log and Fail2Ban
5. **Automated IP ban triggered by Fail2Ban**
6. Access validation (SSH blocked)
7. Manual unban for validation


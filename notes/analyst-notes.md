# Analyst notes

The saved OpenSSH excerpt contains two failed password entries for root from the same masked address. The source ports differ, which is consistent with separate connections. I generated the attempts during a controlled lab exercise.

The Fail2Ban excerpt records a ban by the SSH jail. After I manually removed the ban and reconnected from the test host, the jail status showed five total failures, one total ban, and zero currently banned addresses. This check verified recovery from the test source. I did not measure the full automatic ban duration or investigate host-wide compromise in this exercise.

[Authentication sample](../evidence/logs/failed_password_sample.txt) · [Ban sample](../evidence/logs/fail2ban_ban_samples.txt) · [Recovery screenshot](../evidence/screenshots/06_access_retored.png)

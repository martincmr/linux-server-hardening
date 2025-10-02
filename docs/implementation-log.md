# Implementation Log

## Phase 1: Initial Assessment
- Date: 2025-09-30
- Lynis Score: 61/100
- Key findings: No firewall, default SSH config, no IPS

## Phase 2: Network Security
- Implemented UFW with deny-by-default
- Configured allow rules for SSH (2222)

## Phase 3: SSH Hardening
- Changed port to 2222
- Disabled root login
- Enforced key-based auth

## Phase 4: Intrusion Prevention
- Installed and configured Fail2ban
- Set maxretry=3, bantime=3600

## Phase 5: System Hardening & Lynis Remediation
- Date: 2025-10-01
- Disabled unnecessary services
- Applied kernel hardening via sysctl (KRNL-5820)
- Configured auditd
- Implemented specific Lynis suggestions:
  - **AUTH-9262:** Configured account locking after failed login attempts.
  - **AUTH-9286:** Enforced minimum password complexity requirements.
  - **AUTH-9328:** Set a maximum password age.
  - **ACCT-9628:** Implemented stricter PAM password policies.
  - **SSH-7408:** Strengthened SSH configuration disabling weak algorithms.
  - **BOOT-5122:** Hardened GRUB bootloader configuration.
  - **NETW-3200:** Reviewed and hardened network interface settings.
  - **PKGS-7370 & PKGS-7394:** Removed unnecessary software packages.
  - **MAIL-8818:** Secured local mail spool permissions.

## Phase 6: Validation
- Date: 2025-10-01
- Final Lynis score: 75/100
- All critical controls verified functional.
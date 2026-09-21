# Changes to SUSE16-CIS-Audit

# Based on CIS SUSE Linux Enterprise 16 Benchmark v1.0.0

## September 2026

- 1.3.1.1 title no longer renders the whole vars map; the audit failed to parse
- 5.2.4 NOPASSWD entries for suse16cis_sudoers_exclude_nopasswd_list users accepted
- 6.2.1.3, 6.2.1.4 grub config checks accept the setting as the first token
- 6.2.1.4 audit_backlog_limit regex accepts every value from 8192
- sshd -T checks case-insensitive: 1.7.9, 5.1.7-5.1.11, 5.1.13, 5.1.14, 5.1.18, 5.1.23, 5.1.24
- 5.1.24 catches the [::] listen form
- 1.2.1.2 fails only on gpgcheck off or invalid values
- 2.1.21 inet_interfaces checked via postconf; passes without postfix
- 4.1.1 firewalld package checked; nftables mask assertion removed
- 4.1.4 checks active zones only, excluding lo and virbr
- 5.1.1 checks sshd_config.d *.conf files only, stdout negation now a pattern list
- 5.1.3 public key permission mask /133
- 6.2.3.1 accepts dir=/etc/sudoers.d with or without the trailing slash
- 6.3.2 cron file path no longer doubled
- 7.1.13 reports SUID/SGID files for review without failing
- 7.2.8 reads /etc/passwd instead of 59000 getent lookups

## August 2026 - QA findings remediation

- section 2.1: controls 2.1.11 to 2.1.22 carried the previous control's package and gate,
  every file remapped and 2.1.22 added
- section 1.8: all 7 files rewritten, bodies were one control out of step with the titles
- 1.8.3 contained a pattern and its own negation, so it could never pass
- 1.8.5 and 1.8.7 patterns were not /-delimited and matched as literal text
- 1.8.4 and 1.8.6 used an unescaped [org/...] character class
- 1.7.4, 1.7.5 and 1.7.6 rewritten, all three checked the wrong file
- 1.1.1.1/.3/.4/.5/.6 looked for "unblacklist", which modprobe never emits
- 1.2.1.2 had no stdout assertion, the command always exited 0
- 1.6.6 and 1.6.7 regexes were unterminated and matched as literal substrings
- 2.4.1.7 and 2.4.1.8 both pointed at /etc/cron.d
- 2.4.3.1 and 2.4.3.2 put find's expression before its paths
- 2.1.13 rsync socket test was indented into the service test
- 2.1.21 gate polarity was inverted and the postfix file is main.cf, not main.conf
- 2.3.1.1 now checks the chrony time source and OPTIONS=-u chrony
- 4.1.1 asserted iptables enabled and running in the nftables branch
- 4.1.4 grep -v passed whenever any zone was not ACCEPT
- 4.1.6 ipv6 test was indented into the ipv4 test, duplicating its keys
- 4.1.7 and 1.1.1.10 asserted /.+/ on output that is never empty
- 5.1.3 assigned keysperm and echoed keyperms
- 5.1.7 to 5.1.22 now read sshd -T, they checked sshd_config while the role writes drop-ins
- 5.4.1.6 compared dates as strings
- 5.4.2.2 used a substring and a character class, both always true
- 5.4.2.5 pattern matched a backslash, not a "." PATH entry
- 6.1.3.1 checked /var/log/apt on a zypper distribution
- 6.2.4.1 audited /var/log permissions instead of the audit log directory mode
- 6.3.3 aide.conf path is now a variable, autrace dropped
- 7.2.4 to 7.2.7 uniq -d had no sort, non-adjacent duplicates were missed
- toggles 1.2.1.5, 5.1.24, 6.1.2.9 and 6.3.3 enabled to match remediation
- suse16cis_desktop_required removed
- README and run_audit.sh typos

## August 2026 - Profile alignment and GDM gating

- 1.8.2 to 1.8.7 desktop_required gate removed, remediation gates on suse16cis_gui alone
- level gates and meta server/workstation aligned to the benchmark across 19 controls
  - lowered to level 1: 1.3.1.4, 1.8.1, 3.2.1-3.2.6
  - raised to level 2: 1.8.7, 2.1.20, 2.2.2, 5.3.2.1.3, 5.4.1.2, 6.2.4.1
  - workstation set to NA: 2.1.11, 2.1.20, 3.1.2
  - meta only, gate unchanged: 1.8.4, 1.8.6, 3.1.1
- 1.1.1.2, 1.8.4, 2.1.1, 2.1.2, 3.1.3 held at level_1, split-profile controls, do not re-raise
- CONTRIBUTING.md and README Contributing section added
- goss documentation links point at the krameff fork

## June 2026 - QA pass fixes

- Added CONTRIBUTING.md
- Updated .gitignore with full standard Lockdown pattern set

## v1.0.0 - 2026-06-10

- Initial SUSE16-CIS-Audit role based on CIS SUSE Linux Enterprise 16 Benchmark v1.0.0

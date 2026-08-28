# Changes to SUSE16-CIS-Audit

# Based on CIS SUSE Linux Enterprise 16 Benchmark v1.0.0

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

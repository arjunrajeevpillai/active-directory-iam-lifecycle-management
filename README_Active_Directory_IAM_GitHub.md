# Active Directory-Based Identity & Access Management Lab

A hands-on **Active Directory IAM foundation lab** built with Windows Server 2019 and Oracle VirtualBox for the fictional organization TechSecure Solutions.

## Project overview

The lab demonstrates core on-premises identity administration: AD DS domain setup, DNS configuration, directory organization, user and security-group administration, department shared folders, NTFS permissions, and domain connectivity validation.

> **Scope accuracy:** This repository documents a foundation lab. It does not claim completed automated Joiner-Mover-Leaver (JML) workflows, PowerShell lifecycle automation, GPO baselines, formal access reviews, cloud IAM, MFA/SSO, or successful Kali Linux domain integration.

## Environment

| Component | Configuration |
|---|---|
| Server OS | Windows Server 2019 |
| Virtualization | Oracle VirtualBox |
| Domain | `corp.local` |
| NetBIOS | `CORP` |
| Domain controller | `DC01` |
| DC address | `192.168.0.10/24` |
| Lab network | VirtualBox Host-only, `192.168.0.0/24` |
| Host adapter | `192.168.0.1/24` |

## Implemented components

- AD DS forest and `corp.local` domain
- DNS configuration and domain-controller discovery validation
- Organizational units, user accounts, and security groups
- Department folders: HR, IT, Finance, Security, Management
- SMB share and department-level NTFS permission configuration
- Windows host domain-join and connectivity tests

## Issues and troubleshooting

- Migrated from an initial NAT network (`10.0.2.0/24`) to a Host-only network (`192.168.0.0/24`).
- Resolved domain-controller discovery error 1355 by correcting DNS configuration.
- Corrected the SMB share path from `C:` to `C:\DepartmentShares`.
- Kali Linux was explored but not domain-joined. Screenshots show Linux command syntax mistakes (`ifconfig /all`, `iproute`) and a network configuration from the earlier NAT subnet. These are included as troubleshooting evidence, not successful integration.

## Architecture

See `docs/architecture.png` for the logical lab diagram.

## Repository structure (recommended)

```text
active-directory-iam-lab/
├── README.md
├── report/
│   ├── Active_Directory_IAM_Professional_Report.pdf
│   └── Active_Directory_IAM_Professional_Report.docx
├── docs/
│   └── architecture.png
├── screenshots/
│   ├── ad-ds-dns/
│   ├── users-groups/
│   ├── shares-permissions/
│   └── troubleshooting-kali/
└── scripts/
    └── (add tested IAM automation scripts as they are developed)
```

## Future enhancements

1. Build a dedicated Windows 11 Pro `CLIENT01` VM and join it to the domain.
2. Implement and test Joiner-Mover-Leaver workflows.
3. Add PowerShell provisioning, group assignment, transfer, and deprovisioning scripts.
4. Implement Group Policy security baselines.
5. Conduct periodic access reviews and generate audit reports.
6. Explore Microsoft Entra ID, MFA, SSO, and hybrid identity.

## Security and publication notes

- Do not commit passwords, DSRM credentials, recovery keys, or secrets.
- Sanitize screenshots to remove personal usernames, host identifiers, and sensitive network details.
- Use synthetic identities and lab-only credentials.
- Verify all scripts in an isolated test environment before using them elsewhere.

## Author

Arjun R. Pillai

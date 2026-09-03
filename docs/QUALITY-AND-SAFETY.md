# Quality and Safety

> This is the historical 0.1.1 document. Current SSH behavior, update scheduling,
> and 0.1.x release gates are described in [README](../README.md),
> [Support](../SUPPORT.md), and [Security](../SECURITY.md). The older Actions
> deferral or validation status is not evidence for the current version.

This document describes the verification model and safety boundaries for PCssak Gongyu 0.1.1
Free Early Access. It is evidence and operating guidance, not a guarantee that the software is
defect-free or compatible with every computer.

[한국어](QUALITY-AND-SAFETY.ko.md)

## User-directed system changes

PCssak Gongyu starts as the current user. Read-only checks and per-user features do not require a
permanently elevated process. A backend operation that changes machine-wide Windows state verifies
administrator privileges again and refuses the change when the required token is absent.

The app separates these scopes:

- automatic SMB preparation and its recorded recovery state;
- user-created shares, mapped drives and stored credentials;
- short-lived share pairing on TCP 19763; and
- separately consented OpenSSH Server, `sshd` and TCP 22 setup.

Automatic SMB preparation does not silently enable SSH. MSRA screen sharing and mouse control are
disabled in 0.1.1 and are not the same as SSH shell, command or SFTP access.

## Ownership and fail-closed behavior

The app treats a share as PCSSAK-managed only when its name, path and random management token match
both the Windows share description and the machine ownership record. An external or legacy share
without that evidence is shown read-only for destructive management actions.

Sensitive Windows, Program Files, ProgramData, drive-root and user-profile locations are rejected
by the backend for managed-share removal and pairing ACL changes. A UI validation cannot bypass
that backend check.

Machine-wide changes use a global single-instance mutex and an operation journal. A second Windows
or RDP session cannot start another instance while the first is active. An interrupted or uncertain
operation is reported as incomplete and must not be presented as success.

## Firewall and LAN boundary

SMB and NetBIOS rules created by automatic setup are limited to Domain and Private profiles and
Windows `LocalSubnet`. A rule with a matching name but a broader remote scope is not accepted as a
safe result.

SSH is a separate explicit opt-in. Version 0.1.1 supports only a host PC on a trusted physical
Ethernet or Wi-Fi connection using a Private or Domain profile on the same router and LAN. The
PCSSAK-owned inbound rule is bound to the real Windows `System32\OpenSSH\sshd.exe`, TCP 22, Lan or
Wireless interface types, and the exact local IPv4/on-link scope present when SSH is enabled.

Any active Public profile, addressed VPN or tunnel, or a failed adapter or firewall query blocks
SSH enablement. VPN access, direct Internet access and router port forwarding are unsupported.
Changing the physical network or DHCP address requires SSH to be turned off and enabled again only
after the new LAN is trusted.

A local-ready result verifies the service, firewall contract and local listener. It does not prove
a remote login or SFTP transfer. A two-PC same-LAN test and independent server host-key fingerprint
check remain necessary.

## Pairing and credential handling

Share pairing uses an 8-digit, five-minute, single-use code. The current protocol uses RFC 9807
OPAQUE with Argon2id and sends SMB credentials only after authentication inside an AES-256-GCM
protected response derived from the OPAQUE session key. The raw code and a simple code hash are not
logged or sent over TCP 19763. Rate limits reduce online guessing but do not make a short code safe
to disclose publicly.

Stored SMB passwords use current-user Windows DPAPI. A user can separately choose Windows
Credential Manager. Passwords, pairing codes and private keys must never be posted to a public
Issue or copied into a full diagnostic log.

## Recovery and uninstall

Before changing Windows state, the app records the evidence needed for its supported recovery path.
Recovery only changes items that ownership and previous-state records identify. It does not claim
unknown shares, rules or accounts as its own.

Normal “Turn SSH access off” does not remove OpenSSH Server; it closes the allow rule and stops and
disables `sshd`. The separate “Fully reset the SSH environment” restores PCSSAK-recorded changes
and removes OpenSSH only when PCSSAK originally installed it. General recovery and NSIS uninstall
do not automatically remove every user-created share, mapping, credential, local app file, startup
entry, or user-installed OpenSSH feature. Review the in-app state and
[Known Limitations](KNOWN-LIMITATIONS.md) before uninstalling. A recovery failure can stop uninstall
so the recovery tool is not removed first.

## Local-first privacy boundary

The app has no PCSSAK telemetry, advertising, online account, automatic crash upload or license
server. The updater checks the public GitHub Release once per launch and never installs without
user approval. Local files, paths, network identifiers, settings, journals and logs are not
automatically uploaded to PCSSAK.

Local-first does not mean offline-only. User-requested LAN, SMB, Wake-on-LAN, pairing and SSH
operations communicate with selected network devices. OpenSSH Server installation can contact
Windows Update, WSUS or an organization-configured source. See [PRIVACY.md](../PRIVACY.md).

## Release integrity

The 0.1.1 public build uses one x64 NSIS installer. It is not Authenticode-signed, so Windows can
show Unknown publisher or SmartScreen and users must not disable Windows security products. The
Tauri/Minisign updater signature verifies installer integrity but is not a Windows publisher
identity.

The version-pinned `v0.1.1` release must contain exactly the nine assets defined in
[RELEASE-ASSET-CONTRACT.md](RELEASE-ASSET-CONTRACT.md). `SHA256SUMS.txt` covers the other eight
assets, and the exact MPL-2.0 source archive is published with the installer. `latest.json` is the
Tauri-only updater manifest; human and website metadata is kept in `DOWNLOAD-METADATA.json`. Public
0.1.0 users must manually install the official 0.1.1 build once; signed in-app updates become
available after that transition.

## Verification layers

The 0.1.1 source and candidate must pass local locked Rust tests and strict Clippy for x64 and i686,
UI, locale and static checks, dependency auditing, reproducible third-party notice and MPL source
generation, both Minisign signatures, and exact nine-asset assembly verification. Exact counts,
hashes and exclusions are fixed in the build evidence and release record for that source commit;
this document does not infer them.

Those results do not replace hands-on installation, elevation, reboot, recovery, update, uninstall,
antimalware and same-LAN two-PC testing on the exact release bytes. Version 0.1.1 defers final
external legal review, the full Windows 10/11 Home/Pro x64 VM and LAN matrix, independent
supply-chain approvals, and GitHub Actions to 0.1.2. Missing evidence remains a known limitation,
not a validation pass. Fixed v0.1.1 assets are not replaced; a correction is published as a higher
version.

## Compatibility claims

Windows 11 Home/Pro x64 and Windows 10 22H2 Home/Pro x64 are validation targets for 0.1.1. They are
not a claim that every target has completed hands-on validation. Windows 10 general servicing has
ended and users must verify ESU or LTSC status separately. Native ARM64, Windows S mode, Windows
Server, macOS and Linux are not supported release targets. An x86 build or compile result is not a
public x86 installer claim.

Only a release note that identifies the exact installer hash and completed environment may be used
as release-specific hands-on evidence.

## What users should do

- Download only from the official version-pinned PCSSAK release or product page.
- Compare the installer SHA-256 with `SHA256SUMS.txt`.
- Do not disable SmartScreen, Microsoft Defender or a firewall.
- Begin with a non-sensitive test folder and maintain an independent backup.
- Use sharing and SSH only on systems and networks you are authorized to administer.
- Verify the host-key fingerprint and actual login from the second PC before relying on SSH.
- Remove personal, credential and network details before requesting support.

Report a normal defect through the structured Issue form. Report an exploitable security problem
privately under [SECURITY.md](../SECURITY.md).

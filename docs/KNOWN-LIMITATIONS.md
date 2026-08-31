# Known Limitations

[한국어](KNOWN-LIMITATIONS.ko.md)

This document describes the public PCssak Gongyu 0.1.1 Free Early Access boundary. Availability
is determined only by the version-pinned
[`v0.1.1` release](https://github.com/pcssakinc/pcssak-gongyu-releases/releases/tag/v0.1.1)
and its exact nine assets. If the installer or any fixed asset is missing, the official 0.1.1
publication is not complete.

## Early Access and installer

- Version 0.1.1 is below 1.0 and can contain unknown defects or changing behavior.
- The public 0.1.1 release contains one x64 NSIS per-machine installer. It requires administrator
  elevation.
- No x86 installer is published. An i686 compile or test result is not a support claim.
- The installer is not Authenticode-signed and can show Unknown publisher or SmartScreen.
- Do not disable SmartScreen, Microsoft Defender, a firewall or another security product.
- The public 0.1.0 build has no in-app updater. Existing users must manually install the official
  0.1.1 installer once; signed in-app updates become available after that transition.
- `latest.json` is the Tauri-only updater manifest; human and website metadata is kept in
  `DOWNLOAD-METADATA.json`. The two update signatures are not Windows publisher identity
  signatures.
- The installer uses the WebView2 download bootstrapper. A PC without the Runtime can require a
  Microsoft download during setup; later maintenance follows Windows and organizational policy.

## Windows compatibility

- Windows 11 Home/Pro x64 and Windows 10 22H2 Home/Pro x64 are validation targets, not completed
  support claims for every edition, build and device.
- Windows 10 general servicing has ended. PCSSAK support cannot replace Microsoft security updates,
  ESU eligibility or LTSC lifecycle requirements.
- Native ARM64, Windows S mode, Windows Server, macOS and Linux are unsupported release targets.
- Domain GPO, endpoint security, custom firewall and optional-feature source policy can override or
  block an otherwise valid operation.
- Hardware, language pack, VPN, EDR and managed-network combinations are not exhaustively tested.

## Same-LAN scope

- Sharing, mapping, pairing and SSH are intended for computers on the same trusted router and LAN.
- An SSH host must use a Private or Domain profile on physical Ethernet or Wi-Fi.
- Any active Public profile, addressed VPN or tunnel, or failed adapter/firewall query blocks SSH
  enablement.
- Public networks, VPNs or tunnels, direct Internet access and router port forwarding are
  unsupported. Do not expose TCP 22 to the Internet.
- A DHCP address or physical network change can make the recorded SSH scope stale. Turn SSH off,
  verify the new LAN and enable it again.
- Routed subnets, VLANs and enterprise firewall policy can require administrator review and are not
  automatically broadened by the app.

## SSH is not screen-sharing remote support

- SSH setup, remote shell, command execution and SFTP are core 0.1.1 functions for the same LAN.
- MSRA screen sharing and mouse control are disabled and are not silently provided through SSH.
- “Locally ready” checks the host service, firewall and listener; it does not prove another PC can
  log in or transfer a file.
- The app does not modify `%ProgramData%\ssh\sshd_config`, configure key-only authentication,
  create `AllowUsers` policy, distribute a trusted host-key fingerprint or automate an IP allowlist.
- First connection requires an independent host-key fingerprint check. Account authentication and
  authorization remain Windows and OpenSSH policy.
- Normal “Turn SSH access off” does not remove OpenSSH Server. It closes the PCSSAK allow rule,
  verifies protective blocking, and stops and disables `sshd`, so the next enable does not require
  reinstallation.
- The separate “Fully reset the SSH environment” restores PCSSAK-recorded service and firewall
  changes and removes OpenSSH Server only when PCSSAK originally installed it. A user-installed
  feature is preserved.

## SMB sharing, pairing and mapping

- The app manages only shares whose ownership evidence matches both Windows and the PCSSAK record.
  External and unverifiable legacy shares remain read-only for destructive actions.
- Existing shares are not silently imported. A matching name or path alone does not establish
  ownership.
- Sensitive system and profile locations are blocked, but these checks do not replace backups.
- Pairing uses an 8-digit, five-minute, single-use code. Rate limits reduce but do not eliminate
  online guessing. Protect the code from screenshots, clipboard history and observation.
- A pairing response can be uncertain after the final client message; issue a new code rather than
  reusing the old one.
- Drive mappings and Windows Credential Manager state can differ by Windows user, elevation token
  and session. Existing conflicting credentials may require manual review.

## Recovery and uninstall

- Recovery depends on valid ownership and previous-state records. Missing or conflicting evidence
  causes a refusal rather than a guessed destructive action.
- Running services are not always stopped when their startup types are restored, because another
  Windows feature may use them.
- User-created shares, mapped drives, Windows credentials, local app data, WebView2 data, startup
  entries and a user-installed OpenSSH Server can remain after uninstall.
- A failed recovery can stop uninstall to preserve the recovery tool.
- Recovery and rollback are safety conveniences, not a full system backup.

## Local data and privacy

- Logs can contain IP addresses, hostnames, share names, paths and Windows errors. They are not
  automatically uploaded, but users must redact them before support submission.
- Local JSON, DPAPI credentials, WebView2 storage and journals can remain until the user removes
  them. PCSSAK cannot remotely delete data that was never centrally collected.
- Email, GitHub, Cloudflare, Google and Microsoft services process information under their own
  policies when the user chooses to use them.
- The Korean EULA and Privacy Policy are authoritative to the extent permitted by applicable law;
  English is a reference translation. No global legal-compliance certification is claimed.

## Verification boundary

Local automated tests, static checks and dependency audits do not replace hands-on testing of the
exact published bytes. Version 0.1.1 defers final external legal review, the full Windows 10/11
Home/Pro x64 VM and LAN matrix, independent supply-chain approvals, and GitHub Actions to 0.1.2.
That deferral must not be described as completed compatibility or legal review; release notes may
claim evidence only for the exact file and environment that actually completed it.

Report a reproducible non-security problem through the Issue form. For a vulnerability or possible
credential exposure, follow [SECURITY.md](../SECURITY.md) and report privately.

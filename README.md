# PCssak Gongyu Releases

[한국어 안내](README.ko.md)

> **0.3.5 known issues, reported after publication:** SSH enabling was reported to succeed.
> Disabling can report an incomplete result even when the service is stopped and automatic
> startup is disabled, because restoration of older external firewall records fails.
> Full restoration can also fail with `SSH-FW/IDENTITY-MATCH-TARGET`.
> These issues are recorded for 0.3.6; they are **not fixed in 0.3.5**.
> See the [publication verification and known issues](docs/RELEASE-v0.3.5-VERIFICATION.md).

> This directory is the public repository contract for PCssak Gongyu `v0.3.5`
> Free Early Access. The version-pinned GitHub release and its nine verified
> assets are the publication record.

PCssak Gongyu is a Windows utility for user-directed SMB shared-folder setup,
LAN checks, network-drive management, and separately consented SSH setup.
Version `0.3.5` is **Free Early Access**; this describes product maturity and
does not promise that future versions will remain free.

## Release and verification requirements

Version 0.3.5 is Free Early Access that, after public version 0.3.4, retires the contract under which enabling SSH temporarily disabled other programs' and Windows' own firewall allow rules and replaces it with a LAN shield, a block rule for sources outside the approved LAN. Version 0.3.4 was published as a GitHub release on 2026-09-17; versions 0.2.9, 0.3.0 and 0.3.1 were unpublished test builds. Availability is established by the version-pinned GitHub release and its nine verified assets; the website must identify the same version and file hashes. Publication requires final-source validation, installer verification, both update signatures and all nine assets, followed by public read-back. Automated checks are separate from installation, recovery and SSH access on real PCs; this document alone does not establish publication or successful real-device testing.

## Official download and Latest update

After verified publication, use only the
[official v0.3.5 release](https://github.com/pcssakinc/pcssak-gongyu-releases/releases/tag/v0.3.5)
or a version-pinned page on [pcssak.com](https://pcssak.com/). The release title
states Free Early Access, while GitHub uses `draft=false`, `prerelease=false`,
and Latest so the application can check this stable endpoint:

`https://github.com/pcssakinc/pcssak-gongyu-releases/releases/latest/download/latest.json`

**Users on 0.2.0, 0.2.1, 0.2.2, 0.2.3, 0.2.4, 0.2.5, 0.2.6, 0.2.7, 0.2.8, 0.3.2, 0.3.3, 0.3.4, or an unpublished 0.2.9, 0.3.0 or 0.3.1 build with valid legal-consent records can check for 0.3.5 after its verified publication in the app,
download and verify it, then approve installation.** The legal documents and updater
public key are unchanged in this patch. Users on 0.1.9 run the official installer
interactively to review the current legal documents. Users on 0.1.8 or earlier also
need a one-time manual installation because of the previous updater-key transition.

For 0.1.1 through 0.3.4, do not uninstall first or delete settings, sharing records,
SSH configuration, or interrupted-operation records. Protected replacement preserves
user settings without launching the old uninstaller. If the app was already removed,
use the new installer without manually deleting Windows recovery records. Only
0.1.0 requires removal before installing the official release. Missing consent or
damaged installation records require the interactive installation path.

Version 0.3.5 no longer temporarily disables other programs' or Windows' own firewall allow rules when SSH is enabled; instead it creates, before the PCSSAK allow rule, five PCSSAK-owned inbound block rules, the LAN shield. Each rule negates one condition of the 0.3.4 allow contract: sshd.exe with a remote address outside the approved physical LAN IPv4 subnets (as start-end ranges) or any IPv6 address; sshd.exe on the Public profile; sshd.exe arriving over VPN or remote-access interfaces; sshd.exe arriving on a local address that is not the approved physical IPv4; and any program on TCP 22 from outside the LAN. Where local policy applies and authentication bypass and excluded interfaces have been ruled out, the shield uses explicit inbound-block precedence; verification re-reads the rules and compares addresses as range sets rather than display strings, and enable succeeds only when each of the five rules exists exactly once with no extra constraints (specific interfaces, remote ports, packages or users). Allow rules carrying IPsec authentication conditions can be evaluated before blocks and are conservatively reported as rules the shield cannot cover; unreadable conditions are not accepted as safe, and organization-policy effects and actual packet blocking require separate verification. The legacy V4 firewall-record matching check and the four-rule limit on conflicting external allow rules are no longer enable gates, an approved recovery still being applied continues to defer enable and the other safety gates remain, the presence of a legacy record is read by the status query to show the legacy recovery card, and enabling SSH and adding the shield preserve existing external rule states and records. They do not run legacy restoration, which remains a separate recovery action so that enabling does not repeat slow legacy comparisons or reactivate bypass rules after verification. A PC enabled by 0.3.4 or earlier is not short-circuited as already on: when the service, automatic start, allow rule and baseline match the current contract and only the shield is missing, the app adds the shield alone without the full block rule, a network transition or service changes, and reverts only that shield if the step fails. Disable removes the shield only after the full block rule is verified or the service is stopped with start type Disabled, reporting an unverified removal as a notice only; full restoration removes the shield and then the full block rule after every other verification. Uninstalling keeps the SSH service, the PCSSAK rules and the five shield rules, so run full SSH restoration first if SSH is no longer needed. Legacy firewall-record recovery no longer stops at the first mismatched group: undecidable groups are left unresolved (unchanged) while the rest are matched and restored, with per-reason counts shown as fixed codes; a physical-LAN detection failure at the 84% firewall step is reported with a network diagnostic key while keeping its stage code. After enabling, the app connects to this PC's own approved LAN IPv4 on port 22 and reports whether the sshd banner answered; this is not a verification of access from another PC or of the firewall path, and a failed probe is not an error. Four address-property acceptance cases on transient COM objects passed; actual rule registration, packet blocking, real-PC enabling, two-PC SSH/SFTP and persistence across reboot remain unverified.

In 0.3.5, the shield verdict is limited to verified local-policy applicability, no detected authentication bypass, and no excluded interfaces. Unknown policy, authentication or interface state is not treated as safe, and the app does not claim unconditional precedence over organization policy. The external-rule list uses its safe appearance only when both the shield and the overall safety verdict are true. A completed recovery card is hidden only when the protected completed record, archive, public finalization and all four current journal locations agree; unresolved originals remain protected. Four address-property acceptance cases on transient COM objects have been checked, but actual rule registration, packet blocking, and current-PC or two-PC connection trials remain NOT_RUN.

A restart pending after OpenSSH installation no longer displays overall 100%, all stages complete or connection success. It identifies installation as finished but SSH setup as incomplete, with the remaining setup completed by running SSH enable again after restart. After removing a protective block rule, only confirmed absence counts as complete; query errors or remaining rules are not reported as successful removal. Development validation of these changes is separate from successful restart, recovery or connection on a real PC.
See the [release notes](docs/RELEASE-NOTES-v0.3.5.md) for details.
This document and automated tests do not establish successful SSH connections,
installation, or reboot persistence on every PC. Existing immutable assets are
preserved. The full Windows and two-PC SSH matrices remain incomplete.

The public installer targets Windows x64 only:

- `PCssak-Gongyu-0.3.5-Windows-x64-Setup.exe`

Windows x86 is not published until its separate Windows 10 x86 Home/Pro
hands-on evidence gate passes.

Versions from 0.1.2 through 0.4.9, inclusive, are free Early Access
releases intended to obtain real-world measurements. Final external legal
review, the full Windows 10/11 Home/Pro x64 VM and physical-LAN SSH/SFTP matrix,
independent supply-chain review, and Windows-trusted Authenticode signing are
not complete and are disclosed while post-release testing continues. Each release still
requires final-source verification through GitHub Actions or the approved local
Windows verification process, Tauri updater signing, independent Minisign signing,
SHA-256 checks, and the exact nine-asset contract. The local alternative is limited
to versions from 0.1.2 through 0.4.9, inclusive. It records actual commands,
tool and log hashes, and results; a skipped or failed Actions run is not called a success.
Early Access does not guarantee defect-free operation across every Windows and
security-product combination; test on a recoverable system with a backup before
using it on an important PC.

## Verify before running

Compare the installer SHA-256 with `SHA256SUMS.txt` from the same release:

```powershell
Get-FileHash -Algorithm SHA256 '.\PCssak-Gongyu-0.3.5-Windows-x64-Setup.exe'
```

The release also contains `PCssak-Gongyu-0.3.5-Windows-x64-Setup.exe.sig`.
PCssak Gongyu verifies updater artifacts with its embedded Gongyu-specific
Minisign public key. `UPDATE-RELEASE.json.sig` separately binds the product,
version, source commit, installer hash, installer byte size, embedded EULA and
privacy-policy hashes, canonical URL, and approved release notes. These signatures
are not a Windows publisher identity.

Public Early Access installers from 0.1.2 through 0.4.9, inclusive,
and their bundled executables do not carry an Authenticode publisher signature.
Windows or security products may therefore warn about or block the file. Do not
disable SmartScreen, Microsoft Defender, a firewall, or another security product
to install it. Stop if a hash or signature differs.

Windows 11 Smart App Control (SAC) blocking is separate from the application's
PIN lock and installer behavior. The app never disables SAC or other security controls automatically.
Microsoft's [SAC FAQ](https://support.microsoft.com/en-us/Windows/Security/threat-malware-protection/smart-app-control-frequently-asked-questions)
describes re-enablement improvements in recent updates, but we do not promise that
every Windows build or device state allows turning it off and immediately back on.
SAC does not offer a per-app exception. Keep protection enabled when installation
or execution is blocked. If only the unsigned uninstaller is blocked and the user
chooses a temporary SAC pause, this is limited to devices whose re-enablement support
has been confirmed in advance; uninstall and immediately re-enable it. Follow the
[conditional removal guidance](SECURITY.md); do not pause SAC when eligibility is unclear.

## Nine release assets

Every release contains exactly the set documented in
[`docs/RELEASE-ASSET-CONTRACT.md`](docs/RELEASE-ASSET-CONTRACT.md):

- the x64 installer and its Tauri/Minisign `.sig`;
- Tauri `latest.json`;
- signed `UPDATE-RELEASE.json` and its `.sig`;
- human/website `DOWNLOAD-METADATA.json`;
- `SHA256SUMS.txt`, `THIRD-PARTY-NOTICES.txt`, and the exact-version MPL source
  archive.

`latest.json` is exclusively the Tauri static updater manifest validated by
[`latest.schema.json`](latest.schema.json). Human-facing download data is kept
separately in `DOWNLOAD-METADATA.json`, validated by
[`download-metadata.schema.json`](download-metadata.schema.json).
The signed release contract is fixed by
[`update-release.schema.json`](update-release.schema.json).

## Security and support

Read [`SECURITY.md`](SECURITY.md) before reporting a vulnerability. For normal
support, contact `support@pcssak.com`. Never attach passwords, private keys,
recovery codes, access tokens, personal documents, or an unredacted network
configuration to a public issue.

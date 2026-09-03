# PCssak Gongyu Releases

[한국어 안내](README.ko.md)

> This directory is the public repository contract for PCssak Gongyu `v0.1.6`
> Free Early Access. The version-pinned GitHub release and its nine verified
> assets are the publication record.

PCssak Gongyu is a Windows utility for user-directed SMB shared-folder setup,
LAN checks, network-drive management, and separately consented SSH setup.
Version `0.1.6` is **Free Early Access**; this describes product maturity and
does not promise that future versions will remain free.

## Official download and Latest update

Use only the
[official v0.1.6 release](https://github.com/pcssakinc/pcssak-gongyu-releases/releases/tag/v0.1.6)
or a version-pinned page on [pcssak.com](https://pcssak.com/). The release title
states Free Early Access, while GitHub uses `draft=false`, `prerelease=false`,
and Latest so the application can check this stable endpoint:

`https://github.com/pcssakinc/pcssak-gongyu-releases/releases/latest/download/latest.json`

The public `0.1.0` build has no in-app updater, so those users must manually
install the official `0.1.6` installer once. Version `0.1.1` users may need the
official interactive installer to accept changed legal documents. Version
`0.1.3`, `0.1.4`, and trial-installed `0.1.5` users with valid legal-consent records use the in-app path
to check, download, verify the signature, and approve installation of the update.
The legal documents and updater public key are unchanged.

Version `0.1.6` improves existing Microsoft OpenSSH reuse and rollback-identity
binding. A company test PC successfully upgraded from
`0.1.3` to `0.1.5`, but an existing OpenSSH path/identity compatibility failure was
then found, so `0.1.5` was not published. Latest was kept at `0.1.3` during repair;
immutable assets are preserved. The approved local enable, disable, re-enable,
and restore trial passed with the original installation, configuration and host keys preserved.
The complete Windows and two-PC SSH matrices remain incomplete.
See the [release notes](docs/RELEASE-NOTES-v0.1.6.md). This document
is not evidence that the new version has been published.

The planned public installer targets Windows x64 only:

- `PCssak-Gongyu-0.1.6-Windows-x64-Setup.exe`

Windows x86 is not published until its separate Windows 10 x86 Home/Pro
hands-on evidence gate passes.

Versions from 0.1.2 up to, but not including, 0.2.0 are free Early Access
releases intended to obtain real-world measurements. Final external legal
review, the full Windows 10/11 Home/Pro x64 VM and physical-LAN SSH/SFTP matrix,
independent supply-chain review, and Windows-trusted Authenticode signing are
not complete and return as mandatory gates before 0.2.0. Final-source GitHub
Actions, Tauri updater signing, independent Minisign signing, SHA-256 checks,
and the exact nine-asset contract remain mandatory for every 0.1.x release.
Early Access does not guarantee defect-free operation across every Windows and
security-product combination; test on a recoverable system with a backup before
using it on an important PC.

## Verify before running

Compare the installer SHA-256 with `SHA256SUMS.txt` from the same release:

```powershell
Get-FileHash -Algorithm SHA256 '.\PCssak-Gongyu-0.1.6-Windows-x64-Setup.exe'
```

The release also contains `PCssak-Gongyu-0.1.6-Windows-x64-Setup.exe.sig`.
PCssak Gongyu verifies updater artifacts with its embedded Gongyu-specific
Minisign public key. `UPDATE-RELEASE.json.sig` separately binds the product,
version, source commit, installer hash, installer byte size, embedded EULA and
privacy-policy hashes, canonical URL, and approved release notes. These signatures
are not a Windows publisher identity.

Public 0.1.x Early Access installers from 0.1.2 up to, but not including, 0.2.0
and their bundled executables do not carry an Authenticode publisher signature.
Windows or security products may therefore warn about or block the file. Do not
disable SmartScreen, Microsoft Defender, a firewall, or another security product
to install it. Stop if a hash or signature differs.

Windows 11 Smart App Control (SAC) blocking is separate from this installer-directory
defect. The app never disables SAC or other security controls automatically.
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

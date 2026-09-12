# PCssak Gongyu Releases

[한국어 안내](README.ko.md)

> This directory is the public repository contract for PCssak Gongyu `v0.2.0`
> Free Early Access. The version-pinned GitHub release and its nine verified
> assets are the publication record.

PCssak Gongyu is a Windows utility for user-directed SMB shared-folder setup,
LAN checks, network-drive management, and separately consented SSH setup.
Version `0.2.0` is **Free Early Access**; this describes product maturity and
does not promise that future versions will remain free.

## Official download and Latest update

Use only the
[official v0.2.0 release](https://github.com/pcssakinc/pcssak-gongyu-releases/releases/tag/v0.2.0)
or a version-pinned page on [pcssak.com](https://pcssak.com/). The release title
states Free Early Access, while GitHub uses `draft=false`, `prerelease=false`,
and Latest so the application can check this stable endpoint:

`https://github.com/pcssakinc/pcssak-gongyu-releases/releases/latest/download/latest.json`

The updater signing key has changed. **All users on 0.1.8 or earlier must run the
official 0.2.0 installer manually once.** Older apps do not contain the new public
key and may show a generic signature error before displaying migration guidance.
For 0.1.1 through 0.1.9, install over the existing app without deleting settings,
sharing records, SSH configuration, or interrupted-operation records. Version 0.1.0
supports neither in-app updating nor an in-place upgrade: uninstall that version
before installing the official release. **Users on 0.1.9 also need interactive
installation for 0.2.0 because the legal-document scope and effective date changed.**
The installer presents the new documents for consent and preserves user settings.
Protected replacement does not launch the older uninstaller. Later updates may use
the verified in-app installation path when the accepted legal documents are unchanged.

Version `0.2.0` tightens SSH automatic-start and applied-configuration checks, prevents
overlapping setup actions and stale SSH permission responses, and protects application
files from partial removal when bundled files are locked. It retains the 0.1.9 fixes
for equivalent firewall-rule snapshots, personal/team sharing, member approval, SMB
preparation, administrator resumption, and exact-scope interrupted-operation recovery.
SSH disable verifies stopped/disabled state without uninstalling OpenSSH.
This does not claim completed real Windows changes, reboot tests, or two-PC connection tests.
See the [release notes](docs/RELEASE-NOTES-v0.2.0.md) for changes and known limitations.
The version-pinned release and its verified assets determine download availability;
this document alone is not a publication record. Previously published immutable
assets are preserved. The complete Windows and two-PC SSH matrices remain incomplete.

The public installer targets Windows x64 only:

- `PCssak-Gongyu-0.2.0-Windows-x64-Setup.exe`

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
Get-FileHash -Algorithm SHA256 '.\PCssak-Gongyu-0.2.0-Windows-x64-Setup.exe'
```

The release also contains `PCssak-Gongyu-0.2.0-Windows-x64-Setup.exe.sig`.
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

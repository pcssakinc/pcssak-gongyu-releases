# PCssak Gongyu Releases

[한국어 안내](README.ko.md)

> This directory is the public repository contract for PCssak Gongyu `v0.2.4`
> Free Early Access. The version-pinned GitHub release and its nine verified
> assets are the publication record.

PCssak Gongyu is a Windows utility for user-directed SMB shared-folder setup,
LAN checks, network-drive management, and separately consented SSH setup.
Version `0.2.4` is **Free Early Access**; this describes product maturity and
does not promise that future versions will remain free.

## Official download and Latest update

Use only the
[official v0.2.4 release](https://github.com/pcssakinc/pcssak-gongyu-releases/releases/tag/v0.2.4)
or a version-pinned page on [pcssak.com](https://pcssak.com/). The release title
states Free Early Access, while GitHub uses `draft=false`, `prerelease=false`,
and Latest so the application can check this stable endpoint:

`https://github.com/pcssakinc/pcssak-gongyu-releases/releases/latest/download/latest.json`

**Users on 0.2.0, 0.2.1, 0.2.2, or 0.2.3 with valid legal-consent records can check for 0.2.4 in the app,
download and verify it, then approve installation.** The legal documents and updater
public key are unchanged in this patch. Users on 0.1.9 run the official installer
interactively to review the current legal documents. Users on 0.1.8 or earlier also
need a one-time manual installation because of the previous updater-key transition.

For 0.1.1 through 0.2.3, do not uninstall first or delete settings, sharing records,
SSH configuration, or interrupted-operation records. Protected replacement preserves
user settings without launching the old uninstaller. If the app was already removed,
use the new installer without manually deleting Windows recovery records. Only
0.1.0 requires removal before installing the official release. Missing consent or
damaged installation records require the interactive installation path.

Version 0.2.4 fixes the root cause that made Enable SSH fail: inbound allow rules that
belong to Windows Store apps were classified as risky TCP 22 rules. Effective policies
and the Store-app policy store are checked together. A rule is excluded only when the
observed counts, enabled states, and programs match and every matching rule is
package-only with no program. Conflicting external allow rules are inspected read-only
before protective rules, baseline records, or OpenSSH installation. A consented
Public-to-Private physical-LAN transition may occur first; if the temporary-disable
limit is exceeded, SSH changes do not start and restoration of that transition is
attempted. Unverified restoration retains the failure and recovery records.
The blocking rule count and sample names are shown in the app. A safe-stop request never
cuts work off: rollback is attempted at a safe point, and cancellation is recorded only
after that rollback is verified. Unverified rollback retains interrupted-work recovery
guidance. OpenSSH installation must finish first; disable and full reset can stop only
before their first change, and final verification may complete. Interrupted-operation
records are checked read-only, and only a fully-off or
fully-completed state releases the block; partial states keep the existing confirmation
path. Protected replacement now includes 0.2.3 in all four installer entry paths.
SSH disable verifies stopped/disabled state without uninstalling OpenSSH.
See the [release notes](docs/RELEASE-NOTES-v0.2.4.md) for the changes and verification
scope. The version-pinned release and its nine verified assets determine availability.
This document and automated tests do not establish successful SSH connections,
installation, or reboot persistence on every PC. Existing immutable assets are
preserved. The full Windows and two-PC SSH matrices remain incomplete.

The public installer targets Windows x64 only:

- `PCssak-Gongyu-0.2.4-Windows-x64-Setup.exe`

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
Get-FileHash -Algorithm SHA256 '.\PCssak-Gongyu-0.2.4-Windows-x64-Setup.exe'
```

The release also contains `PCssak-Gongyu-0.2.4-Windows-x64-Setup.exe.sig`.
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

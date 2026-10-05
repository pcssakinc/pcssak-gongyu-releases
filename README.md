# PCssak Gongyu Releases

[한국어 안내](README.ko.md)

> This directory is the public repository contract for PCssak Gongyu v0.4.2 Free Early Access.
> Publication is established by the actual immutable release and nine verified assets.

PCssak Gongyu is a Windows utility for user-directed SMB sharing, LAN checks,
network-drive management and separately consented SSH setup. Free Early Access
describes the maturity of this version, not a promise about future pricing.

## What changed in 0.4.2

The PCSSAK cream/navy palette with small mint accents, wordmark, appearance and
large-text settings are unified. Button boundaries and high-contrast focus are
improved. Automatic setup assesses readiness on the same physical-LAN basis as
its approved changes and adds bounded retries for temporary inspection delays.
Auxiliary WMI reads compare bulk results with official individual reads and
fall back on mismatch. Exact-ID restoration and regular SSH controls keep their
existing checks: this does not resolve historical firewall restoration or make
all SSH operations 22 times faster. The current manual and protected replacement
from 0.4.1 are updated.

The following connection and recovery safeguards from 0.4.1 remain.

Sharing connection checks preserve seven underlying failure reasons and bind the
approved network identity and returned scope to the same observation. Recovery
cards in Settings separate status, actions and explanations. Physical-LAN checks,
verification before and after changes, and user confirmation remain required.
VPN and virtual adapters are not trusted automatically. The reported remote
server's exact environment and failure remain unconfirmed; this release does not
claim expanded Windows Server or virtual-LAN support or hands-on success.

The regular SSH controls and Settings categories introduced in 0.4.0 remain.
Retired legacy firewall-recovery screens are not reopened, and protected records
are not deleted. Restore, overwrite and deletion confirmations remain, as does
the possible need to re-enter passwords on another PC or Windows account.

The protected partial-restoration limits introduced in 0.3.9 remain. App-owned
settings may be cleaned only when protected records and exact non-overlapping
targets establish independent external recovery. Original service restoration,
OpenSSH removal, Public-profile restoration and release of protective blocking
may remain deferred. Damaged, overlapping or unreadable state is not success.
The LAN-shield verdict remains limited to verified policy, authentication and
interface state, without guaranteeing precedence over organization policy.
Other programs' and Windows' allow rules are not arbitrarily changed. Stopping
the service does not prove that all authenticated SSH sessions have ended.

Hands-on 0.4.2 installation, upgrade, removal, reboot persistence, two-PC SSH/SFTP
and full restoration are NOT_RUN. Experience with one PC on an earlier release
is not evidence for this installer. The full Windows Home/Pro matrix, external
legal review, independent supply-chain review and Authenticode remain incomplete.
Development tests, final-source verification, both update signatures, nine assets
and public read-back are separate gates. See the [release notes](docs/RELEASE-NOTES-v0.4.2.md).

## Official download and Latest update

After verified publication, use only the
[official v0.4.2 release](https://github.com/pcssakinc/pcssak-gongyu-releases/releases/tag/v0.4.2)
or a version-pinned page on [pcssak.com](https://pcssak.com/). The title states
Free Early Access; GitHub uses `draft=false`, `prerelease=false` and Latest.
The application's fixed update endpoint is:

`https://github.com/pcssakinc/pcssak-gongyu-releases/releases/latest/download/latest.json`

The legal documents and **0.3.9 updater public key** are unchanged. **0.3.9, 0.4.0 and 0.4.1 users
with valid legal-consent records can download, verify and approve the update in
the app after verified 0.4.2 publication. Users on 0.3.8 or earlier lack the current
key and must download the official installer once, compare its SHA-256 with the
published list and run it interactively.** Do not bypass signature errors.

For 0.1.1 through 0.4.1, use protected replacement without uninstalling first or
deleting settings, sharing records, SSH configuration or interrupted-operation
records. The old uninstaller is not launched. Even after prior removal, do not
manually delete Windows recovery records. Only 0.1.0 requires removal before
installing the official release. Missing consent or damaged records require
interactive installation. Hands-on replacement and removal are NOT_RUN.
Do not force a downgrade during interrupted recovery.

An OpenSSH installation awaiting reboot is not successful access or overall
completion; run SSH enable after reboot to finish setup. Updating does not turn
on SSH or complete legacy firewall recovery. The public installer is x64 only:

- `PCssak-Gongyu-0.4.2-Windows-x64-Setup.exe`

Windows x86 is not published before separate Windows 10 x86 Home/Pro hands-on
evidence passes. Versions from 0.1.2 through 0.4.9 are free Early Access. Final-source
verification, Tauri/Minisign signing, SHA-256 and the exact nine assets remain
required. The approved local Windows alternative records actual commands, tool
and log hashes and results; failed Actions are not called successful. Use a
recoverable test PC, current backup and active security software.

## Verify before running

Compare the installer SHA-256 with `SHA256SUMS.txt` from the same release:

```powershell
Get-FileHash -Algorithm SHA256 '.\PCssak-Gongyu-0.4.2-Windows-x64-Setup.exe'
```

The release also contains `PCssak-Gongyu-0.4.2-Windows-x64-Setup.exe.sig`.
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

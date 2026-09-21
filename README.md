# PCssak Gongyu Releases

**Languages:** English · [한국어](README.ko.md)

> This directory is the public repository contract for PCssak Gongyu `v0.3.8`
> Free Early Access. Publication is established by the actual release assets and verification record.
> The version-pinned GitHub release and its nine verified
> assets are the publication record.

PCssak Gongyu is a Windows utility for user-directed SMB shared-folder setup,
LAN checks, network-drive management, and separately consented SSH setup.
Version `0.3.8` is **Free Early Access**; this describes product maturity and
does not promise that future versions will remain free.

## Release and verification requirements

Version 0.3.8 addresses repeated legacy firewall recovery blocks and lost responses
from slow reads reported with public 0.3.7. The first 0.3.8 candidate failed a real-PC
trial with long waits and blocked window closing; that failure remains part of the
record. The subsequent implementation also fixes recovery finalization and cancelled
preparation responses. Hands-on installation, upgrade, SSH enable, disable, re-enable
and reboot testing of this revision is **NOT_RUN**. Development tests are distinct
from final-source validation, the installer, both update signatures, all nine assets
and public read-back. Versions 0.2.9, 0.3.0 and 0.3.1 were unpublished test builds;
earlier automated results do not establish that this revision solves the real-PC problem.

The main SSH button reuses an existing OpenSSH service, including a user-installed
service. Enable sets it to Automatic and Running; disable stops it and sets Disabled.
Original installation ownership, settings, keys and the first recorded service state
remain preserved. A new installation without pending recovery follows the normal
installation path. These implemented service settings do not establish successful
reboot persistence on the reporting PC.

An independent legacy recovery can remain pending while normal enable or disable
proceeds only when the SSH service and current SSH settings already exist, its
protected approval and progress records validate, and its targets do not overlap
the currently managed SSH rules. This preserves the original recovery without
completing or deleting it; explicit recovery remains available in Details. Missing
or damaged evidence, pending exact-ID recovery, overlapping targets, old settings
alone, or no installed SSH service prevent this separation. The button does not
repeatedly force full legacy recovery when these conditions fail. Interrupted SSH
setup or restoration itself still requires recovery of the same parent operation;
completing a child recovery does not finalize that parent.
The exception does not remove recovery gates for sharing, full restoration or removal.

Recovery comparison separates the originally approved targets from observation-only
candidates. Only after proving an original retained rule ID is absent can a new
handoff record pass that original ID to V5 archiving while preserving the original
journal, approval digest and completed list. A current rule with the same name is
not a replacement; restoration duties for surviving targets remain. Recovery handoff
schema 3 and operation journal version 3 are separate compatibility boundaries.
After writing these records, use the same updated application line to resume;
do not delete records or downgrade to bypass a block.

If protected recovery completed but its operation did not finalize, explicit recovery
checks the same operation, approved plan, current exact targets and archived originals
before retrying finalization. Older unbound records require separate confirmation and
are recorded as manually confirmed, not as proof of past successful restoration.
Startup and button reads share one actual response, including a late final result.
Cancellation, app lock, another operation or a changed plan stops preparation; an
obsolete response cannot overwrite newer state. A slow display-only read after a
completed mutation no longer holds that completed action open. The next preparation
verifies current state. A safe stop waits for the current Windows call and the
item's restore, verification and progress recording to finish; it is not forced
termination or proof that full restoration succeeded.

## Official download and Latest update

After verified publication, use only the
[official v0.3.8 release](https://github.com/pcssakinc/pcssak-gongyu-releases/releases/tag/v0.3.8)
or a version-pinned page on [pcssak.com](https://pcssak.com/). The release title
states Free Early Access, while GitHub uses `draft=false`, `prerelease=false`,
and Latest so the application can check this stable endpoint:

`https://github.com/pcssakinc/pcssak-gongyu-releases/releases/latest/download/latest.json`

**Users on 0.2.0, 0.2.1, 0.2.2, 0.2.3, 0.2.4, 0.2.5, 0.2.6, 0.2.7, 0.2.8, 0.3.2, 0.3.3, 0.3.4, 0.3.5, 0.3.6, 0.3.7, or an unpublished 0.2.9, 0.3.0 or 0.3.1 build with valid legal-consent records can check for 0.3.8 after its verified publication in the app,
download and verify it, then approve installation.** The legal documents and updater
public key are unchanged in this patch. Users on 0.1.9 run the official installer
interactively to review the current legal documents. Users on 0.1.8 or earlier also
need a one-time manual installation because of the previous updater-key transition.

The 0.3.7-to-0.3.8 protected replacement path and interrupted-replacement regressions
are implemented. Hands-on replacement and removal with the final installer are NOT_RUN.
For 0.1.1 through 0.3.7, do not uninstall first or delete settings, sharing records,
SSH configuration, or interrupted-operation records. Protected replacement preserves
user settings without launching the old uninstaller. If the app was already removed,
use the new installer without manually deleting Windows recovery records. Only
0.1.0 requires removal before installing the official release. Missing consent or
damaged installation records require the interactive installation path.

Quick disable is judged by removal of the PCSSAK allow rule, verification that the service is stopped with start type Disabled, and verified blocking. It does not restore legacy external rules: original journals are preserved and pending restoration is shown separately. If full restoration cannot verify external recovery, it defers restarting the original service, restoring automatic start, removing the OpenSSH capability and releasing protective blocking. Only a partial result with reverified safety can proceed through an ordinary retry; unverified safety still requires interrupted-operation recovery. Stopping the service does not prove that every already authenticated SSH session has ended. Exact SCM STOPPED state is required instead of treating starting, stopping or paused services as fully stopped. Quick disable, partial restoration, V5 archiving and unresolved outcomes have distinct guidance in all ten languages.

The V5 flow verifies an exact rule ID is absent twice, then archives the original in administrator-protected storage only after explicit user approval matching the preview digest. Existing targets, policy changes, duplicate matches and query failures are not treated as missing rules; their originals are preserved. Interrupted archiving resumes from the existing record, and concurrent changes after approval stop the operation. Archiving neither changes or recreates a Windows firewall rule nor completes full restoration. Older interrupted records lead to the next recovery step appropriate to their operation; journal deletion, firewall resets and disabling security software are not bypasses.

The five PCSSAK-owned LAN-shield block rules introduced in 0.3.5 remain in place. Enable and quick disable do not arbitrarily modify other programs' or Windows' own allow rules. Safety is limited to verified policy applicability, no authentication bypass and no excluded interfaces; organization-policy effects are not guaranteed. Existing user-installed OpenSSH and settings remain preserved. Service registration is distinct from capability installation, and a pending installation reboot is neither overall 100% completion nor successful access: run SSH enable again after reboot. A local sshd banner response does not verify another PC's access or packet filtering.

The existing LAN-shield verdict is limited to verified local-policy applicability, no detected authentication bypass, and no excluded interfaces. Unknown policy, authentication or interface state is not treated as safe, and the app does not claim unconditional precedence over organization policy. The external-rule list uses its safe appearance only when both the shield and the overall safety verdict are true. A completed recovery card is hidden only when the protected completed record, archive, public finalization and all four current journal locations agree; unresolved originals remain protected. Earlier address-property tests on transient COM objects do not establish this revision's actual rule registration, packet blocking or successful access. Final recovery and access on the reporting PC and the full two-PC matrix remain unverified.

A restart pending after OpenSSH installation no longer displays overall 100%, all stages complete or connection success. It identifies installation as finished but SSH setup as incomplete, with the remaining setup completed by running SSH enable again after restart. After removing a protective block rule, only confirmed absence counts as complete; query errors or remaining rules are not reported as successful removal. Development validation of these changes is separate from successful restart, recovery or connection on a real PC.
See the [release notes](docs/RELEASE-NOTES-v0.3.8.md) for details.
This document and automated tests do not establish successful SSH connections,
installation, or reboot persistence on every PC. Existing immutable assets are
preserved. The full Windows and two-PC SSH matrices remain incomplete.

The public installer targets Windows x64 only:

- `PCssak-Gongyu-0.3.8-Windows-x64-Setup.exe`

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
Get-FileHash -Algorithm SHA256 '.\PCssak-Gongyu-0.3.8-Windows-x64-Setup.exe'
```

The release also contains `PCssak-Gongyu-0.3.8-Windows-x64-Setup.exe.sig`.
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

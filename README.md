# PCssak Gongyu - Official Windows Downloads

[한국어 안내](README.ko.md)

PCssak Gongyu is a Windows utility for user-directed SMB shared-folder setup, LAN checks, network
drive management, short-lived share pairing, and separately consented OpenSSH Server setup. It is
part of PCSSAK's focused Windows tool family.

The first public channel is **PCssak Gongyu 0.1.0 Free Early Access**. Availability is determined
only by the version-pinned
[`v0.1.0` GitHub release](https://github.com/pcssakinc/pcssak-gongyu-releases/releases/tag/v0.1.0).
If that page does not contain the installer and the complete fixed asset set, no official public
0.1.0 installer is available.

## Download

After publication, use only the version-pinned release above or the official
[PCssak Gongyu product page](https://pcssak.com/gongyu). The planned first release contains one
Windows x64 installer:

- `PCssak-Gongyu-Beta-Windows-x64-Setup.exe`

Do not use an x86 file, an unknown mirror, a messenger attachment or a repackaged installer. Before
running the installer, compare its SHA-256 with `SHA256SUMS.txt` from the same release.

```powershell
Get-FileHash -Algorithm SHA256 '.\PCssak-Gongyu-Beta-Windows-x64-Setup.exe'
```

The result must match the value beside the exact filename character for character. Stop if the
source, filename, size or hash differs.

## First installation

1. Confirm the official source, filename and SHA-256.
2. Start the x64 NSIS installer and choose one of the installation languages offered by that exact
   release.
3. Review the Korean authoritative EULA and its English reference translation. Cancel if you do
   not agree.
4. Approve Windows administrator elevation only after confirming the app name is **PCssak Gongyu**.
5. Finish installation, open the app and choose the preferred app language in Settings if needed.
6. Begin with a non-sensitive test folder and keep an independent backup.

The app interface supports Korean, English, Japanese, Simplified Chinese, Traditional Chinese,
French, German, Russian, Brazilian Portuguese and Turkish. The exact installer-language list and
first-launch handoff must be verified on the final installer bytes and will be stated in the
version-specific release notes; the app-language list alone is not proof of installer localization.

## Unsigned Early Access boundary

The 0.1.0 installer is **not Windows Authenticode-signed** and the app has no automatic updater.
No detached Tauri updater `.sig` is published. Windows can show **Unknown publisher** or a
Microsoft Defender SmartScreen reputation warning.

Do not disable SmartScreen, Microsoft Defender, a firewall or another security product. An updater
signature, SHA-256 or official filename would not replace Authenticode publisher identity. For
0.1.0, authenticity depends on the official version-pinned source and the matching published hash.

## Same-LAN sharing and SSH

PCssak Gongyu is for computers on the same trusted router and LAN. It can assist with:

- SMB preparation and recovery with Domain/Private `LocalSubnet` firewall rules;
- PCSSAK-owned shared folders and permission evidence;
- mapped network drives and user-selected credential storage;
- an 8-digit, five-minute, single-use share-pairing flow; and
- separately consented OpenSSH Server, `sshd` and TCP 22 setup.

SSH is a **core 0.1.0 feature**, not a removed remote function. The host PC must be on physical
Ethernet or Wi-Fi using a **Private or Domain** network profile on the same LAN. The PCSSAK-owned
rule is bound to the real Windows `sshd.exe` and the exact local IPv4/on-link range present when SSH
is enabled.

**Public networks, VPNs or tunnels, direct Internet access and router port forwarding are not
supported.** Do not broaden the firewall rule to every remote address or expose TCP 22 to the
Internet. A network or DHCP-address change requires SSH to be turned off, the new trusted LAN to be
verified, and SSH to be enabled again.

“Locally ready” checks the host service, firewall and listener. It does not prove that another PC
can log in or use SFTP. On first connection, verify the server host-key fingerprint through a
separate path.

MSRA screen sharing and mouse control are disabled in 0.1.0. They are separate from same-LAN SSH
shell, command and SFTP access.

## Release files

The public `v0.1.0` prerelease must contain exactly these five assets:

1. `PCssak-Gongyu-Beta-Windows-x64-Setup.exe`
2. `PCssak-Gongyu-0.1.0-MPL-Sources.zip`
3. `THIRD-PARTY-NOTICES.txt`
4. `latest.json`
5. `SHA256SUMS.txt`

The release must use GitHub's machine-readable `prerelease=true` state, not only the words “Early
Access” in its title. GitHub `/releases/latest` excludes prereleases, so all product and download
links use the exact `v0.1.0` tag.

`latest.json` is PCSSAK download metadata validated by [`latest.schema.json`](latest.schema.json).
It is not a Tauri updater manifest and must not be described as a signed automatic-update channel.
See the complete [release asset contract](docs/RELEASE-ASSET-CONTRACT.md).

## Compatibility status

- Validation targets: Windows 11 Home/Pro x64 and Windows 10 22H2 Home/Pro x64
- Public architecture: x64 only
- Not published: Windows x86
- Unsupported release targets: native ARM64, Windows S mode, Windows Server, macOS and Linux

These are boundaries and targets, not a statement that every environment has completed hands-on
testing. Windows 10 general servicing has ended; users must verify ESU or LTSC lifecycle status
separately. Read [Known Limitations](docs/KNOWN-LIMITATIONS.md).

## Local processing and recovery

The app has no PCSSAK telemetry, advertising, online account, automatic crash upload, license
server or automatic updater. Local settings, network identifiers, paths, journals and credentials
are not automatically uploaded to PCSSAK.

User-requested LAN, SMB, Wake-on-LAN, pairing and SSH operations still communicate with chosen
local devices. OpenSSH Server installation can contact Windows Update, WSUS or an
organization-configured source.

Recovery and uninstall do not automatically remove every user-created share, mapping, Windows
credential, local app file, startup entry or separately enabled OpenSSH/SSH state. Review the app
state and documentation before removal.

## Help improve Early Access

- Use the [bug report form](https://github.com/pcssakinc/pcssak-gongyu-releases/issues/new?template=bug-report.yml) for a reproducible,
  non-security defect.
- Use the [feature request form](https://github.com/pcssakinc/pcssak-gongyu-releases/issues/new?template=feature-request.yml) for a recurring user
  problem and its safety impact.
- Follow [SECURITY.md](SECURITY.md) for an exploitable vulnerability or possible credential
  exposure.
- General support: `support@pcssak.com`
- Privacy requests: `privacy@pcssak.com`

Never post passwords, private keys, pairing codes, real usernames, exact internal IP addresses,
share names, full paths, directory listings, customer files, complete network configurations or raw
logs in a public Issue.

## Documentation

- [Korean release guide](README.ko.md)
- [End User License Agreement](EULA.md) and [installer text](EULA.txt)
- [Privacy Policy](PRIVACY.md)
- [Support](SUPPORT.md)
- [Quality and Safety](docs/QUALITY-AND-SAFETY.md)
- [Known Limitations](docs/KNOWN-LIMITATIONS.md)
- [Third-Party Notices](THIRD-PARTY-NOTICES.txt)
- [MPL source information](docs/THIRD-PARTY-SOURCE.md)
- [Prepared v0.1.0 release notes](docs/RELEASE-NOTES-v0.1.0.md)
- [Release asset contract](docs/RELEASE-ASSET-CONTRACT.md)
- [Issue and contribution guidelines](CONTRIBUTING.md)

## Development and responsibility

PCssak Gongyu is independently directed and maintained under the PCSSAK name. AI tools can assist
with research, implementation, review, testing and documentation, but final requirements,
technical decisions, release approval and maintenance remain under human control.

This public repository distributes release binaries, documentation, third-party notices and the
required MPL source packages. The original application source remains private proprietary software
except for separately identified third-party components.

The Korean EULA and Privacy Policy are authoritative to the extent permitted by applicable law;
English is a reference translation. PCSSAK does not claim that these documents certify compliance
with every country or jurisdiction.

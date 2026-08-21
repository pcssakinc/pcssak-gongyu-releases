# PCssak Gongyu Releases

[한국어 안내](README.ko.md)

> This directory is a local publication template for the future
> `pcssakinc/pcssak-gongyu-releases` repository. It does not mean that a public
> release already exists. Do not publish it until every gate in
> [`docs/RELEASE-ASSET-CONTRACT.md`](docs/RELEASE-ASSET-CONTRACT.md) passes.

PCssak Gongyu is a Windows utility for user-directed SMB shared-folder setup,
LAN checks, network-drive management, and separately consented SSH setup. The
first public build is planned as **Free Early Access**. Features and supported
environments can change before a stable paid version.

## Official download contract

After publication, use only the
[official v0.1.0 Early Access release](https://github.com/pcssakinc/pcssak-gongyu-releases/releases/tag/v0.1.0)
or the Korean/English download pages on [pcssak.com](https://pcssak.com/).
The first release exposes one Windows x64 installer:

- `PCssak-Gongyu-Beta-Windows-x64-Setup.exe`

Windows x86 is not published until its separate Windows 10 x86 Home/Pro
hands-on evidence gate passes. A filename alone is not proof of authenticity.
Before running the installer, compare its SHA-256 with `SHA256SUMS.txt` from
the same versioned release.

```powershell
Get-FileHash -Algorithm SHA256 '.\PCssak-Gongyu-Beta-Windows-x64-Setup.exe'
```

The output must match the line for the same filename character for character.
Do not run a file whose source, filename, size, or hash differs.

## Unsigned Early Access boundary

The first Early Access installer has **no Authenticode code signature** and no
detached Tauri updater `.sig` file. Windows can therefore display **Unknown
publisher** or a Microsoft Defender SmartScreen reputation warning. This is an
honest distribution limitation, not a request to weaken Windows security.

Do **not** disable SmartScreen, Microsoft Defender, your firewall, or another
security product to install PCssak Gongyu. If Windows blocks the file or the
hash differs, stop and report it to `support@pcssak.com`.

## Release files

Each public release must contain exactly the fixed asset set documented in
[`docs/RELEASE-ASSET-CONTRACT.md`](docs/RELEASE-ASSET-CONTRACT.md), including:

- the x64 installer;
- `SHA256SUMS.txt`;
- the distribution metadata `latest.json`;
- `THIRD-PARTY-NOTICES.txt`; and
- the exact-version MPL-2.0 component source archive.

`latest.json` is PCSSAK download metadata validated by
[`latest.schema.json`](latest.schema.json). It is **not** a Tauri updater
manifest and must not be presented as a signed automatic-update channel.

## Security and support

Read [`SECURITY.md`](SECURITY.md) before reporting a vulnerability. For normal
support, contact `support@pcssak.com`. Never attach passwords, private keys,
recovery codes, access tokens, personal documents, or an unredacted network
configuration to a public issue.

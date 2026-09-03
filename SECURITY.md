# Security Policy / 보안 정책

## English

Security reports are evaluated against the latest publicly available PCssak
Gongyu Free Early Access release. Early Access can contain undiscovered defects;
this policy is a reporting and response boundary, not a guarantee that defects
do not exist.

Versions from 0.1.2 up to, but not including, 0.2.0 are public Early Access.
External legal review, the complete Windows Home/Pro and physical-LAN SSH/SFTP
matrices, independent supply-chain review, and Authenticode are not complete.
GitHub Actions, Tauri/Minisign signatures, SHA-256 and the exact release assets
remain required. Prefer a recoverable test system and a current backup.

### Report privately

After the public repository is created, use its GitHub private vulnerability
reporting channel when available. Otherwise email `support@pcssak.com` with:

- the affected PCssak Gongyu version and Windows edition/build;
- x64 architecture and whether the process was elevated;
- the smallest reproducible steps, expected result, and actual result;
- security impact and whether the issue is already public; and
- sanitized logs or a synthetic proof of concept.

Do not send passwords, private keys, tokens, recovery codes, personal documents,
or another person's data. Do not test against systems or accounts you do not own
or have explicit permission to assess. Allow reasonable remediation time before
public disclosure.

### Verify downloads

Download only from `pcssakinc/pcssak-gongyu-releases` or a version-pinned link on
`pcssak.com`. Compare the installer SHA-256 with `SHA256SUMS.txt` from the same
release. The Tauri updater verifies the published `.sig` with the Gongyu-specific
Minisign public key, and the independently signed `UPDATE-RELEASE.json` binds
release identity, installer hash and byte size, and the canonical installer URL.
The public 0.1.0 build has no in-app updater, so install the official 0.1.6 build
manually once before using cryptographically verified in-app updates. Public
0.1.x Early Access installers from 0.1.2 up to, but not including, 0.2.0 do not
carry an Authenticode publisher signature. Windows or security products may
therefore warn about or block the file. The Tauri updater signature, independent
Minisign signature, and SHA-256 checks remain mandatory, but they do not prove a
Windows publisher identity. Do not disable SmartScreen, Microsoft Defender, a
firewall, or another security product to bypass a warning.

### Smart App Control is a separate boundary

The 0.1.6 OpenSSH compatibility work does not remove Windows 11 Smart App
Control (SAC) blocking or add an Authenticode signature. The application never
turns off SAC, Defender, SmartScreen, a firewall, or an organization's application
control policy. Updater signatures verify release integrity, not Windows publisher
trust or permission to execute.

Microsoft's [current SAC FAQ](https://support.microsoft.com/en-us/Windows/Security/threat-malware-protection/smart-app-control-frequently-asked-questions)
says recent updates improve re-enablement without a clean installation and that
SAC has no per-app exception. Availability still depends on the Windows environment;
do not assume disabling it is immediately reversible. The [KB5074105 change log](https://support.microsoft.com/en-us/servicing/os/windows-11/2026/01/january-29-2026-kb5074105-os-builds-26200-7705-and-26100-7705-preview)
also records removal of its earlier SAC toggle announcement on February 11, 2026.
Do not infer support for every device from a preview build number. Keep protection
enabled when installation or execution is blocked. We do not bypass the policy or
guarantee that a signed future release will never show a warning.

If SAC blocks only the unsigned uninstaller and the user chooses to remove the app,
a temporary pause is an optional, user-performed exception only when re-enablement
without resetting Windows has been confirmed for that exact environment in advance.
Check the applicable official Windows support and the device's Windows Security
warnings first. If support is unclear, resetting/reinstalling Windows is required,
or the device is organization-managed, do not pause SAC; contact support or the
administrator instead. On a confirmed eligible personal device, the user may pause
SAC manually, run the official uninstaller, and immediately turn SAC back on and
confirm that it is on. If it cannot be restored, stop further testing and seek support.
This does not authorize disabling Defender, SmartScreen, a firewall, or organizational
policy. The app never changes those controls or SAC automatically.

## 한국어

보안 제보는 공개된 최신 PCssak Gongyu 무료 Early Access 버전을 기준으로 검토합니다.
Early Access에는 발견되지 않은 결함이 남아 있을 수 있으며, 이 정책은 제보와 대응 범위를
정하는 문서이지 결함이 없다는 보증이 아닙니다.

0.1.2 이상 0.2.0 미만의 0.1.x는 공개 무료 Early Access입니다. 법률 전문가 최종 외부 검토,
Windows 10/11 Home·Pro x64 전체 VM·물리 LAN SSH/SFTP 실기 행렬, 독립 공급망 검토와
Windows 신뢰 Authenticode 서명은 아직 완료되지 않았으며 0.2.0 공개 전 필수 게이트로
복원합니다. GitHub Actions 최종 소스 검증, Tauri 업데이트 서명, 독립 Minisign 서명,
SHA-256과 정확한 9개 자산 검증은 0.1.x에서도 생략하지 않습니다. 복구 가능한 시험 환경과
최신 백업을 우선하세요.

### 비공개 제보

공개 저장소를 만든 뒤 GitHub 비공개 취약점 제보 기능을 사용할 수 있으면 그 채널을
우선합니다. 사용할 수 없으면 `support@pcssak.com`으로 다음 내용을 보내 주세요.

- 영향을 받는 PCssak Gongyu 버전과 Windows 에디션·빌드
- x64 아키텍처와 관리자 권한 실행 여부
- 최소 재현 절차, 기대 결과와 실제 결과
- 보안 영향과 이미 공개된 문제인지 여부
- 개인정보를 제거한 로그 또는 합성한 최소 재현 자료

암호, 개인키, 토큰, 복구 코드, 개인 문서나 다른 사람의 정보를 보내지 마세요. 소유하거나
명시적으로 허가받지 않은 시스템·계정은 시험하지 말고, 공개 전에 합리적인 수정 시간을
주세요.

### 다운로드 확인

`pcssakinc/pcssak-gongyu-releases` 또는 `pcssak.com`의 버전 고정 링크에서만 받고 같은
릴리스의 `SHA256SUMS.txt`와 설치 파일 SHA-256을 비교하세요. Tauri Updater는 공개한
`.sig`를 Gongyu 전용 Minisign 공개키로 검증하며, 별도로 서명한 `UPDATE-RELEASE.json`이
릴리스 신원·설치본 해시·바이트 크기와 정규 설치본 URL을 묶습니다. 공개 0.1.0에는 앱 내
updater가 없으므로 공식 0.1.6를 한 번 수동 설치한 뒤부터 암호학적으로 검증되는 앱 내 업데이트를
사용하세요. 0.1.2 이상 0.2.0 미만의 공개 0.1.x Early Access 설치 파일에는 Authenticode
게시자 서명이 없습니다. 따라서 Windows나 보안 제품이 경고하거나 실행을 차단할 수 있습니다.
Tauri 업데이트 서명, 독립 Minisign 서명과 SHA-256 검증은 유지되지만 Windows 게시자 신원을
보증하지는 않습니다.
경고를 우회하려고 SmartScreen, Microsoft Defender, 방화벽 또는 다른 보안 제품을 끄지 마세요.

### Smart App Control은 별도의 보안 경계입니다

0.1.6의 OpenSSH 호환성 수정은 Windows 11 Smart App Control(SAC) 차단 해제나
Authenticode 서명 추가가 아닙니다. 앱은 SAC·Defender·SmartScreen·방화벽·조직의 앱 실행
정책을 자동 해제하지 않습니다. 업데이트 서명은 배포 파일의 무결성을 검증하며 Windows
게시자 신뢰나 실행 허가를 대신하지 않습니다.

Microsoft의 [최신 SAC FAQ](https://support.microsoft.com/en-us/Windows/Security/threat-malware-protection/smart-app-control-frequently-asked-questions)는
최근 업데이트에서 재설치 없는 재활성화가 개선됐고 개별 앱 예외는 없다고 설명합니다.
실제 제공 여부는 Windows 환경에 따라 다르므로 해제 후 즉시 원상복귀할 수 있다고
가정하지 마세요. [KB5074105 변경 이력](https://support.microsoft.com/en-us/servicing/os/windows-11/2026/01/january-29-2026-kb5074105-os-builds-26200-7705-and-26100-7705-preview)에도
2026-02-11에 기존 SAC 전환 기능 안내를 철회한 기록이 있으므로 미리보기 빌드 번호 하나로
모든 PC의 지원을 판단하지 않습니다. 설치·실행이 SAC에 차단되면 보호 기능을 유지하고
해당 환경의 시험을 보류하세요. 정책을 우회하지 않으며 향후 서명본도 경고가 절대 없다고
보장하지 않습니다.

무서명 제거기만 SAC에 차단되고 사용자가 직접 앱 제거를 선택한 경우에는 해당 환경에서
Windows 초기화 없이 재활성화가 가능하다고 사전에 확인했을 때만 선택적으로 잠시 중지할
수 있습니다. 적용되는 공식 Windows 지원 정보와 해당 PC의 Windows 보안 사전 경고를
먼저 확인하세요. 지원이 불명확하거나 초기화·재설치가 필요하거나 조직 관리 PC이면 SAC
중지를 안내하지 않으며 지원 또는 관리자에게 문의합니다. 조건이 확인된 개인 PC에서만
사용자가 직접 SAC 일시 중지 → 공식 제거기 실행 → 즉시 SAC 재활성화 및 켜짐 확인 순서로
진행합니다. 다시 켤 수 없다면 추가 시험을 중단하고 지원을 요청하세요. 이는 Defender·
SmartScreen·방화벽·조직 정책의 해제를 허용하지 않으며 앱은 어떤 보안 기능도 자동 변경하지
않습니다.

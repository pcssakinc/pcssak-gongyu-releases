# Security Policy / 보안 정책

## English

Security reports are evaluated against the latest publicly available PCssak
Gongyu Free Early Access release. Early Access can contain undiscovered defects;
this policy is a reporting and response boundary, not a guarantee that defects
do not exist.

Versions from 0.1.2 through 0.4.9, inclusive, are public Early Access.
External legal review, the complete Windows Home/Pro and physical-LAN SSH/SFTP
matrices, independent supply-chain review, and Authenticode are not complete.
Final-source verification through GitHub Actions or the approved local Windows
verification process, Tauri/Minisign signatures, SHA-256, and the exact release
assets remain required. The local alternative is available only from 0.1.2 through
0.4.9, inclusive; it binds actual commands, tool and log hashes, and results
to the final source. Skipped or failed Actions runs are not recorded as successful.
Neither path replaces hands-on Windows or two-PC SSH/SFTP testing. Prefer a
recoverable test system and a current backup.

### Report privately

Use the public repository's GitHub private vulnerability reporting channel when
available. Otherwise email `support@pcssak.com` with:

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
Version 0.2.4 keeps the 0.2.0 legal documents and updater key. Validly consented
0.2.0, 0.2.1, 0.2.2, and 0.2.3 installations can use verified in-app updating with user approval. Users on
0.1.9 still need interactive installation to review the current legal documents;
0.1.8 or earlier also need the previously announced updater-key migration. For
0.1.1 through 0.2.3, use protected replacement without first uninstalling the app
or deleting settings or Windows recovery records. Only 0.1.0 requires removal first.
Public Early Access installers from 0.1.2 through 0.4.9, inclusive, do not
carry an Authenticode publisher signature. Windows or security products may
therefore warn about or block the file. The Tauri updater signature, independent
Minisign signature, and SHA-256 checks remain mandatory, but they do not prove a
Windows publisher identity. Do not disable SmartScreen, Microsoft Defender, a
firewall, or another security product to bypass a warning.

Version 0.2.4 resolves package binding for inbound allow rules using effective policies
and the Store-app network-isolation store together. A rule is excluded only when the
observed counts, enabled states, and programs match and every matching rule is
package-only with no program. Unmatched, unreadable, or mixed ordinary-program rules
retain conservative blocking. Only the writable store is modified. External allow
rules needing temporary disabling are inspected read-only before any protective rule,
baseline record, or feature installation. A consented Public-to-Private physical-LAN
transition may occur first; exceeding the limit prevents SSH changes and attempts to
restore that transition. Unverified restoration retains the failure and recovery
records. The same limit is re-checked immediately before writing, so Windows default
rules are never disabled in bulk. A safe stop is cooperative: the signal never
terminates work. Rollback is attempted at a safe point and is recorded as cancelled
only when verified; unverified rollback retains interrupted-work recovery guidance.
Interrupted-operation self-checks are
read-only and release the block only for a fully-off or contract-complete state;
partial, unreadable, or pending-external-rule states keep manual confirmation, and
machine-scope releases still require administrator rights. Final network identity,
policy, ownership, and rollback checks remain required. No firewall reset, journal
deletion, or security-policy bypass is used.

### Smart App Control is a separate boundary

The 0.1.7 application-lock (PIN) work does not remove Windows 11 Smart App
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

0.1.2 이상 0.4.9 이하 버전은 공개 무료 Early Access입니다. 법률 전문가 최종 외부 검토,
Windows 10/11 Home·Pro x64 전체 VM·물리 LAN SSH/SFTP 실기 행렬, 독립 공급망 검토와
Windows 신뢰 Authenticode 서명은 아직 완료되지 않았습니다. 이 상태를 고지하고 배포 후
실측을 진행합니다. GitHub Actions 또는 승인된 로컬 Windows 경로의 최종 소스 검증, Tauri 업데이트 서명, 독립 Minisign 서명,
SHA-256과 정확한 9개 자산 검증은 공개 Early Access에서도 생략하지 않습니다. 복구 가능한 시험 환경과
최신 백업을 우선하세요.
로컬 대체는 `0.1.2 <= 버전 <= 0.4.9`에서만 허용하며 실제 명령·도구·로그 해시와 결과를 최종
소스에 결속합니다. 건너뛰거나 실패한 Actions를 성공으로 기록하지 않으며 어느 경로도 실제
Windows·두 PC SSH/SFTP 실기를 대신하지 않습니다.

### 비공개 제보

공개 저장소에서 GitHub 비공개 취약점 제보 기능을 사용할 수 있으면 그 채널을
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
릴리스 신원·설치본 해시·바이트 크기와 정규 설치본 URL을 묶습니다. 0.2.4는 0.2.0의 법률
정본·업데이트 키를 유지하므로 정상 동의 기록이 있는 0.2.0·0.2.1·0.2.2·0.2.3은 앱 안에서 검증·사용자 승인 후
업데이트할 수 있습니다. 0.1.9는 현행 법률 문서를 확인하는 대화형 설치가 필요하며 0.1.8
이하는 앞서 고지한 키 전환도 적용됩니다. 0.1.1~0.2.3은 앱을 먼저 제거하거나 사용자 설정·
Windows 복구 기록을 지우지 않고 보호 교체합니다. 0.1.0만 별도 제거 후 설치합니다.
0.1.2 이상 0.4.9 이하의 공개 Early Access 설치 파일에는 Authenticode
게시자 서명이 없습니다. 따라서 Windows나 보안 제품이 경고하거나 실행을 차단할 수 있습니다.
Tauri 업데이트 서명, 독립 Minisign 서명과 SHA-256 검증은 유지되지만 Windows 게시자 신원을
보증하지는 않습니다.
경고를 우회하려고 SmartScreen, Microsoft Defender, 방화벽 또는 다른 보안 제품을 끄지 마세요.

0.2.4는 수신 허용 규칙의 패키지 결속을 실제 적용 중인 정책과 스토어 앱의 네트워크 격리
저장소에서 함께 읽습니다. 관측한 규칙 개수·활성 상태·프로그램이 모두 대응하며 모든 대응
규칙이 프로그램 없는 패키지 전용일 때만 감사에서 제외합니다. 대응 없음·판독 실패·일반
프로그램 규칙 혼합은 보수적 차단을 유지합니다. 변경은 계속 변경 가능한 저장소에만 적용합니다.
보호 차단 규칙·기준선 기록·기능 설치 전에 임시 비활성화가 필요한 외부 허용 규칙의 규모를
읽기 전용으로 확인합니다. 공용 물리 LAN에서는 필요한 신뢰 동의와 개인 네트워크 전환 뒤
점검하며, 상한을 넘으면 SSH 변경을 시작하지 않고 전환 원복을 시도합니다. 원복이 검증되지
않으면 실패와 복구 기록을 유지합니다. 쓰기 직전에도 같은 상한을 다시 검사해 Windows 기본
규칙을 대량으로 끄지 않습니다. 안전 중지는 협조적이며 작업을 강제 종료하지 않고 안전한
지점에서 기존 원복 경로로 되돌리기를 시도합니다. 되돌림을 검증한 경우에만 취소로 기록하며,
검증하지 못하면 중단 복구 안내를 유지합니다. 중단 기록의 자동 점검은 읽기 전용이고 완전히
꺼진 상태나 계약대로 완료된
상태만 차단을 해제하며, 부분 상태·판정 불가·외부 규칙 원복 대기는 수동 확인을 유지하고
머신 범위 해제는 관리자 권한을 계속 요구합니다. 현재 네트워크 신원·정책·소유권·원복의
최종 검증은 그대로 요구하며 방화벽 일괄 초기화, 장부 삭제나 보안 정책 우회로 오류를
숨기지 않습니다.

### Smart App Control은 별도의 보안 경계입니다

0.1.7의 앱 잠금(PIN) 추가는 Windows 11 Smart App Control(SAC) 차단 해제나
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

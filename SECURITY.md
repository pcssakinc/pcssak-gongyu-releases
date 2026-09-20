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
Version 0.3.6 keeps the 0.2.0 legal documents and updater key. Validly consented
public 0.2.0 through 0.2.8 and 0.3.2 through 0.3.5, plus unpublished 0.2.9, 0.3.0 and 0.3.1 installations can use verified in-app updating with user approval after publication. Users on
0.1.9 still need interactive installation to review the current legal documents;
0.1.8 or earlier also need the previously announced updater-key migration. For
0.1.1 through 0.3.5, use protected replacement without first uninstalling the app
or deleting settings or Windows recovery records. Only 0.1.0 requires removal first.
Public Early Access installers from 0.1.2 through 0.4.9, inclusive, do not
carry an Authenticode publisher signature. Windows or security products may
therefore warn about or block the file. The Tauri updater signature, independent
Minisign signature, and SHA-256 checks remain mandatory, but they do not prove a
Windows publisher identity. Do not disable SmartScreen, Microsoft Defender, a
firewall, or another security product to bypass a warning.

Version 0.2.5 resolves package binding for inbound allow rules using effective policies
and the Store-app network-isolation store together. A rule is excluded only when the
observed counts, enabled states, and programs match and every matching rule is
package-only with no program. Unmatched, unreadable, or mixed ordinary-program rules
retain conservative blocking. In 0.3.6, enabling SSH preserves external rules and existing journals; there is no external-rule
disable limit. Five PCSSAK-owned block rules precede the allow rule and complete safety read-back.
Legacy restoration is a separate explicit action. Unknown policy, authentication-bypass or
excluded-interface state is not accepted as safe. A safe stop is cooperative: the signal never
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
릴리스 신원·설치본 해시·바이트 크기와 정규 설치본 URL을 묶습니다. 이번 0.3.6 버전은 0.2.0의 법률
정본·업데이트 키를 유지하므로 정상 동의 기록이 있는 공개 0.2.0~0.2.8·0.3.2~0.3.5 및 비공개
0.2.9·0.3.0·0.3.1 사용자는 실제 공개 후 앱 안에서 검증·사용자 승인 뒤 업데이트할 수 있습니다.
0.1.9는 현행 법률 문서를 확인하는 대화형 설치가 필요하며 0.1.8
이하는 앞서 고지한 키 전환도 적용됩니다. 0.1.1~0.3.5 사용자는 앱을 먼저 제거하거나 사용자 설정·
Windows 복구 기록을 지우지 않고 보호 교체합니다. 0.1.0만 별도 제거 후 설치합니다.
0.1.2 이상 0.4.9 이하의 공개 Early Access 설치 파일에는 Authenticode
게시자 서명이 없습니다. 따라서 Windows나 보안 제품이 경고하거나 실행을 차단할 수 있습니다.
Tauri 업데이트 서명, 독립 Minisign 서명과 SHA-256 검증은 유지되지만 Windows 게시자 신원을
보증하지는 않습니다.
경고를 우회하려고 SmartScreen, Microsoft Defender, 방화벽 또는 다른 보안 제품을 끄지 마세요.

0.2.5는 수신 허용 규칙의 패키지 결속을 실제 적용 중인 정책과 스토어 앱의 네트워크 격리
저장소에서 함께 읽습니다. 관측한 규칙 개수·활성 상태·프로그램이 모두 대응하며 모든 대응
규칙이 프로그램 없는 패키지 전용일 때만 감사에서 제외합니다. 대응 없음·판독 실패·일반
프로그램 규칙 혼합은 보수적 차단을 유지합니다. 변경은 계속 변경 가능한 저장소에만 적용합니다.
0.3.6 켜기는 외부 규칙·장부를 보존하며 외부 규칙 비활성화 상한을 사용하지 않습니다.
소유 차단 규칙 다섯 건 뒤 허용 규칙을 구성하고 전체 안전을 다시 확인합니다. 이전 외부
규칙은 별도 명시적 복구 동작에서 처리합니다. 안전 중지는 협조적이며 작업을 강제 종료하지 않고 안전한
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

## 0.2.5 기존 SSH 보존과 조회 오류 수정 — 당시 버전 기록

Version 0.2.5 fixes a firewall query error that could misclassify Store-app rules and
block starting an already installed SSH server. Preflight and application use the
same exact rule-identity plan while retaining the temporary-change limit and recovery
verification. An existing SSH installation with no PCSSAK management footprint uses
separate service-only start/stop controls. Installation, firewall rules, SSH settings,
and the startup policy are preserved; its existing network exposure is not described
as PCSSAK same-LAN protection. Recovery buttons and rule-list guidance are also fixed.

0.2.5는 이미 설치된 SSH를 다시 켤 때 스토어 앱 규칙을 충돌로 오판하던 조회 오류를 수정합니다.
방화벽 사전 점검과 실제 적용이 같은 고유 규칙 ID 계획을 사용하며, 기존 임시 변경 상한과
원복 검증을 유지합니다. PCSSAK 관리 흔적이 없는 기존 SSH는 별도 서비스 시작·중지로
다루며 설치·방화벽·SSH 설정·자동 시작 유형을 보존합니다. 기존 설정의 네트워크 노출 범위를
PCSSAK의 같은 LAN 보호로 표시하지 않습니다. 중단 복구 버튼과 오류 목록 안내도 수정합니다.

외부 서비스 전용 제어는 자동 시작 유형을 바꾸지 않습니다. 기존 사용 안 함 정책이면 시작을 거부하고, 기존 설치·인증·방화벽을 초기화하지 않습니다. 네트워크 원복 기록이나 PCSSAK 관리 흔적이 남으면 기존 관리·복구 경로를 유지합니다.

## 0.2.6 변경 전 기록과 구형 기록 호환성 — 당시 버전 기록

0.2.6은 구형 SSH 방화벽 복구 기록의 사전 검사 호환성을 수정합니다. 구형 원문과 이번
호출 전 상태를 보존하여 이후 실패의 원복에도 사용합니다. 자동 설정은 원래 상태 기록을
확인한 뒤 변경하며 새 네트워크 전환은 GUID로 기록합니다. 이전 작업 이력은 최대 32건·128KiB로
보존하고 첫 단계의 세부 진행과 진단 코드를 구분합니다. 기존 사용자 SSH 설치·설정 보존과
규칙 변경 상한은 유지합니다. 제보 PC의 실제 접속 성공은 아직 확인하지 못했습니다.

신규 자동 네트워크 전환은 GUID와 원래 상태를 기록·재조회한 뒤 적용합니다. 기록 부재와
판독 실패를 구분하며 손상된 원복 기록은 성공으로 지우지 않습니다. 과거 종료 이력은
참고용이며 현재 복구 권한이나 안전 상태를 추정하는 근거로 사용하지 않습니다.

0.1.1~0.2.5는 먼저 제거하지 않고 0.2.6 설치기의 보호 교체를 사용합니다. 정상 법률 동의
기록이 있는 0.2.0~0.2.5는 검증과 사용자 승인 후 앱 내 업데이트를 사용할 수 있습니다.

Version 0.2.6 restores preflight compatibility with older SSH firewall recovery records.
It preserves the old record and the verified state before the current call for later rollback.
Automatic setup verifies original-state records before changes and records new network transitions
by GUID. Prior terminal history is retained within 32 entries and 128 KiB, with more specific early
progress and diagnostic codes. Existing user SSH settings and rule-change limits remain protected.
Successful SSH access on the reporting PC has not yet been verified.

## 0.3.6 검증 기준과 기존 SSH 보존

0.3.6은 공개 0.3.5에서 확인한 빠른 끄기와 과거 외부 규칙 복구의 혼동을 바로잡는 무료 Early Access입니다. 개발 구현·자동 시험과 최종 소스 검증·설치본·두 업데이트 서명·9자산·공개 판독은 구분합니다. 공개 여부와 최종 검증은 해당 버전의 고정 GitHub 릴리스·공개 자산·마감 기록으로 확인하며, 홈페이지도 같은 버전·파일 해시를 가리켜야 합니다. 0.2.9·0.3.0·0.3.1은 비공개 시험본이었습니다. 자동 시험 통과는 실제 PC의 복구·접속 성공을 뜻하지 않습니다.

Version 0.3.6 is Free Early Access addressing the confusion between quick SSH disable and restoration of legacy external firewall rules observed in public 0.3.5. Development implementation and automated tests are distinct from final-source validation, the installer, both update signatures, all nine assets and public read-back. Check the version-pinned GitHub release, public assets and closeout records for publication and final verification; the website must identify the same version and file hashes. Versions 0.2.9, 0.3.0 and 0.3.1 were unpublished test builds. Automated test success does not establish successful recovery or access on a real PC.

빠른 끄기는 PCSSAK 허용 규칙 제거, 서비스 중지·시작 유형 사용 안 함과 차단 상태를 검증해 판정하며, 과거 외부 규칙을 복구하지 않습니다. 원본 장부는 보존하고 남은 복구는 별도 대기로 안내합니다. 완전 원복에서 외부 복구를 확인하지 못하면 원래 서비스 재시작·자동 시작 복원·기능 제거와 보호 차단 해제를 보류합니다. 안전 상태를 다시 확인한 부분 결과만 일반 재시도로 이어지며, 안전을 확인하지 못한 실패는 중단 복구 검증이 필요합니다. 서비스 중지는 이미 인증된 모든 SSH 세션의 종료를 보장하지 않습니다. Windows 서비스가 시작·중지 중이거나 일시 중지된 상태를 「중지 완료」로 오인하지 않도록 SCM의 정확한 STOPPED 상태를 확인합니다. 빠른 끄기·부분 원복·V5 보관과 미해결 안내는 10개 언어로 구분합니다.

V5 기록의 정확한 ID가 없음을 이중 확인하고, 미리보기의 승인 해시와 일치하는 명시적 사용자 승인 뒤 원본을 관리자 보호 저장소에 보관합니다. 현재 존재하는 대상, 정책 변경, 중복 대응과 조회 실패는 누락으로 처리하지 않고 원본을 보존합니다. 중단된 보관은 기존 기록으로 재개하며, 승인 이후 동시 변경이 발견되면 진행하지 않습니다. 보관은 실제 방화벽 규칙의 변경·재생성이나 완전 원복 완료가 아닙니다. 구형 중단 기록은 종류에 맞는 다음 복구 단계로 연결하고, 장부 삭제·방화벽 초기화·보안 해제로 우회하지 않습니다.

0.3.5부터 사용한 PCSSAK 소유 차단 규칙 다섯 건의 LAN 보호막은 유지합니다. 켜기와 빠른 끄기는 다른 프로그램·Windows 기본 허용 규칙을 임의로 바꾸지 않습니다. 정책 적용 가능성·인증 우회 없음·제외 인터페이스 없음을 확인한 범위만 안전으로 판단하고 조직 정책 전체의 효과를 보장하지 않습니다. 기존 사용자 설치 OpenSSH와 설정은 보존하며, 서비스 등록은 Windows 기능 설치 여부와 구분합니다. 설치 재부팅 대기는 전체 100%나 접속 성공이 아니며, 재부팅 뒤 SSH 켜기를 다시 실행해야 합니다. 이 PC의 sshd 배너 응답은 다른 PC의 접속·패킷 차단 검증이 아닙니다.

0.3.6의 보호막 판정은 로컬 방화벽 정책이 적용 가능하고, 인증 우회가 확인되지 않으며, 제외된 인터페이스가 없음을 확인한 범위에 한합니다. 정책·인증 조건·인터페이스 판독이 불명확하면 안전하다고 표시하지 않으며 조직 정책보다 무조건 우선한다고 보장하지 않습니다. 외부 규칙 목록의 안전 색상은 보호막과 전체 안전 판정이 모두 참일 때만 표시합니다. 복구 완료 원문·보관본·공개 마감 상태와 네 위치의 현재 장부가 일치할 때만 완료된 복구 카드를 숨기며, 미해결 원본은 보호 기록에 보존합니다. 임시 COM 객체의 주소 속성 수용 4사례는 확인했지만 실제 규칙 등록·패킷 차단·현재 PC와 두 PC의 접속 실기는 NOT_RUN입니다.

OpenSSH 설치 후 재부팅을 기다리는 상태는 전체 100%·모든 단계 완료·접속 성공으로 표시하지 않습니다. 설치 단계 종료와 SSH 설정 미완료를 알리고 재부팅 뒤 SSH 켜기를 다시 실행해 나머지 설정을 마무리하도록 안내합니다. 보호 차단 규칙 삭제 뒤에도 정확한 부재만 완료로 인정하며 조회 오류나 남은 규칙을 삭제 성공으로 바꾸지 않습니다. 두 변경의 개발 검증은 실제 재부팅·복구·접속 성공과 구분합니다.

숫자 포트 구간의 순서·중복·겹침, 경로 구분자와 실제 Windows 루트의 검증된 별칭,
전체 프로필 표기를 비교할 때만 통일합니다. 다른 프로그램·다른 포트나 불명확한 별칭을
같다고 추측하지 않습니다. 실제 OS 식별자와 원본 정책 해시를 사용한 변경·원복 검증,
패키지 결속·중복·조회 실패 차단은 유지합니다. 외부 규칙의 임시 변경 상한은 0.3.6 켜기에서 사용하지 않습니다.

기존 수동 SSH는 사용 안 함 시작 유형을 바꾸지 않습니다. 공유 관리 계정이 있는 경우에는
기존 SSH 차단 설정을 확인하고 서비스 시작이 끝날 때까지 해당 파일의 보호를 유지합니다.
계정 조회 실패를 계정 없음으로 취급하지 않습니다. 기존 관리·복구 기록이 있으면 기존
PCSSAK 관리 경로를 사용하며, 단순 존재 분류로 설정의 안전성을 보증하지 않습니다.

0.1.1~0.3.5는 먼저 제거하지 않고 0.3.6 설치기의 보호 교체를 사용합니다. 정상 법률 동의
기록이 있는 공개 0.2.0~0.2.8·0.3.2~0.3.5 및 비공개 0.2.9·0.3.0·0.3.1은 실제 공개 후 검증·사용자 승인 후 앱 내 업데이트를 사용할 수 있습니다.
법률 정본·업데이트 공개키는 유지합니다. 실기·게시자 서명 미완료 고지도 유지합니다.

In 0.3.6, the shield verdict is limited to verified local-policy applicability, no detected authentication bypass, and no excluded interfaces. Unknown policy, authentication or interface state is not treated as safe, and the app does not claim unconditional precedence over organization policy. The external-rule list uses its safe appearance only when both the shield and the overall safety verdict are true. A completed recovery card is hidden only when the protected completed record, archive, public finalization and all four current journal locations agree; unresolved originals remain protected. Four address-property acceptance cases on transient COM objects have been checked, but actual rule registration, packet blocking, and current-PC or two-PC connection trials remain NOT_RUN.

Quick disable is judged by removal of the PCSSAK allow rule, verification that the service is stopped with start type Disabled, and verified blocking. It does not restore legacy external rules: original journals are preserved and pending restoration is shown separately. If full restoration cannot verify external recovery, it defers restarting the original service, restoring automatic start, removing the OpenSSH capability and releasing protective blocking. Only a partial result with reverified safety can proceed through an ordinary retry; unverified safety still requires interrupted-operation recovery. Stopping the service does not prove that every already authenticated SSH session has ended. Exact SCM STOPPED state is required instead of treating starting, stopping or paused services as fully stopped. Quick disable, partial restoration, V5 archiving and unresolved outcomes have distinct guidance in all ten languages.

The V5 flow verifies an exact rule ID is absent twice, then archives the original in administrator-protected storage only after explicit user approval matching the preview digest. Existing targets, policy changes, duplicate matches and query failures are not treated as missing rules; their originals are preserved. Interrupted archiving resumes from the existing record, and concurrent changes after approval stop the operation. Archiving neither changes or recreates a Windows firewall rule nor completes full restoration. Older interrupted records lead to the next recovery step appropriate to their operation; journal deletion, firewall resets and disabling security software are not bypasses.

The five PCSSAK-owned LAN-shield block rules introduced in 0.3.5 remain in place. Enable and quick disable do not arbitrarily modify other programs' or Windows' own allow rules. Safety is limited to verified policy applicability, no authentication bypass and no excluded interfaces; organization-policy effects are not guaranteed. Existing user-installed OpenSSH and settings remain preserved. Service registration is distinct from capability installation, and a pending installation reboot is neither overall 100% completion nor successful access: run SSH enable again after reboot. A local sshd banner response does not verify another PC's access or packet filtering.

A restart pending after OpenSSH installation no longer displays overall 100%, all stages complete or connection success. It identifies installation as finished but SSH setup as incomplete, with the remaining setup completed by running SSH enable again after restart. After removing a protective block rule, only confirmed absence counts as complete; query errors or remaining rules are not reported as successful removal. Development validation of these changes is separate from successful restart, recovery or connection on a real PC.

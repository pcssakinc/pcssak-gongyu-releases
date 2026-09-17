# Support / 고객지원

PCssak Gongyu 0.1.2 through 0.4.9 is Free Early Access. Support has no guaranteed response or fix deadline.
Reports are prioritized by safety impact, affected users and reproducibility.

PCssak Gongyu 0.1.2~0.4.9는 무료 Early Access입니다. 답변·수정 기한을 보장하는 지원 SLA는 없으며,
안전 영향·영향받는 사용자·재현 가능성을 기준으로 우선순위를 정합니다.

0.3.4는 기존 복구 기록을 보존하는 비교 개선, COM 열거 누락 차단, 제공자 단계 관측을
보완합니다. 실제 제공 여부는 [일반 최신 릴리스](https://github.com/pcssakinc/pcssak-gongyu-releases/releases/latest)와
버전 고정 9자산으로 확인하세요. 이 안내와 [0.3.4 변경일기](docs/RELEASE-NOTES-v0.3.4.md)는
게시·실제 PC 복구 성공의 증거가 아닙니다. 0.2.9·0.3.0·0.3.1은 비공개 시험본이었습니다.

자동 검사, 공개 파일 검증, 실제 설치·복구·SSH/SFTP 접속은 서로 다른 검증입니다.
0.3.4의 실제 설치·복구·두 PC 접속·재부팅 시험은 `NOT_RUN`이며 아래 실패 이력은 유지합니다.
반복 실패 시 버전·마지막 단계·짧은 진단 코드만 문의하고 원본 로그·주소·계정·경로는 보내지 마세요.
앱·설정·복구 기록을 보존하고 방화벽 초기화나 보안 해제로 우회하지 마세요.

## 0.3.3 공개와 검증 범위 / 0.3.3 publication and verification scope

[0.3.3 공식 릴리스](https://github.com/pcssakinc/pcssak-gongyu-releases/releases/tag/v0.3.3)는
2026-09-15 13:46:27 UTC에 공개했습니다. 최종 소스 `33cf1849`의 로컬 14단계는
Rust x64·i686 각각 956개·UI 436개를 포함해 통과했고, 공개 후 인증 없는 재다운로드에서
9자산·두 서명·세 스키마·MPL 원본과 이전 0.3.2 보존을 확인했습니다.
[0.3.3 변경일기](docs/RELEASE-NOTES-v0.3.3.md)의 실제 PC 검증 범위는 읽기 전용
관측까지입니다. 설치·SSH 전환·접속은 `NOT_RUN`이며 공개가 해당 PC의 복구 성공을
뜻하지 않습니다. 홈페이지 운영 검증은 별도이며 최종 결과는 후속 날짜별 기록에서
확인합니다. 아래 0.3.2 실패 기록도 유지합니다.

The [official 0.3.3 release](https://github.com/pcssakinc/pcssak-gongyu-releases/releases/tag/v0.3.3)
was published on 2026-09-15 at 13:46:27 UTC. Final source `33cf1849` passed 14 local steps,
including 956 Rust tests on each of x64/i686 and 436 UI tests. Anonymous public readback
verified nine assets, two signatures, three schemas, MPL originals and preservation of 0.3.2.
The [0.3.3 notes](docs/RELEASE-NOTES-v0.3.3.md) record read-only PC observation; installation,
live SSH transitions and access are `NOT_RUN`. Publication does not establish recovery on
the affected PC. Website operational validation is separate; its final result belongs in
the dated follow-up records. The 0.3.2
failure and record-preservation guidance below remain available.

## Reported 0.3.2 SSH issue / 0.3.2에서 확인한 SSH 문제

On 2026-09-15 at 21:02 KST, a user test recognized an existing SSH installation,
then failed at 84% during firewall-rule processing with `native_method_output_null`
and `HRESULT=0`. Rollback verification remained incomplete, and the next enable
attempt stopped at 2% with `LEGACY-RECOVERY`. This is an observed failure, not a
successful rollback. Version 0.3.3 adds checked read-back and address-comparison fixes;
recovery on the affected PC has not been verified. Passing automated
tests and public asset checks does not resolve this hands-on report.

For this symptom, stop repeated enable or recovery attempts and keep the app,
settings and recovery records intact while waiting for verified support guidance.
Do not delete journals, manually reset firewall rules, mix installation files or
disable Windows security controls. Contact `support@pcssak.com` with the version,
stage and the short error identifiers above; do not send raw logs or private paths,
accounts or network details. The 0.3.2 homepage rollout was paused with the homepage
kept on 0.2.8 at that time. This does not establish that downgrading would repair the state.

2026-09-15 21:02 KST 사용자 실기에서는 기존 SSH 설치를 인식한 뒤 방화벽 규칙 처리
84%에서 `native_method_output_null`, `HRESULT=0`으로 실패했습니다. 실패 후 원복 검증은
미완료이며 다음 켜기는 2%에서 `LEGACY-RECOVERY`로 중단됐습니다. 관측한 실패를 알리는
것이며 원복 성공을 확정한 내용이 아닙니다. 0.3.3에 결과 재조회·주소 비교 보완을 넣었지만
해당 PC의 복구는 검증하지 못했습니다. 자동 시험·공개 자산 검증은 실기 해결의 증거가 아닙니다.

이 증상이 있으면 켜기·복구를 반복하지 말고 앱·설정·복구 기록을 보존한 채 검증된 지원
안내를 기다리세요. 장부 삭제·방화벽 규칙 수동 초기화·설치 파일 혼용·Windows 보안 해제로
우회하지 마세요. `support@pcssak.com`에는 버전·발생 단계·위의 짧은 오류 식별자만 먼저
전달하고 원본 로그·개인 경로·계정·네트워크 정보를 보내지 마세요. 홈페이지의 0.3.2
전환은 당시 보류하고 기존 0.2.8을 유지했습니다. 구버전 설치로 복구된다는 뜻이 아닙니다.

아래 일반 재개 안내보다 이 문제의 현재 보류 안내를 우선합니다. 기존 불변 릴리스·태그·
다운로드 자산·승인 노트는 보존합니다. 0.3.3의 검증·공개는 위 절과
[공개 마감 기록](WORKLOG_2026-09-15_V0.3.3_PUBLIC_CLOSEOUT.md)에서 확인합니다.
For this issue, the current pause guidance takes precedence over the general resume
guidance below. Immutable releases, tags, assets and approved notes are preserved;
the 0.3.3 verification and publication are recorded above and in the
[publication closeout](WORKLOG_2026-09-15_V0.3.3_PUBLIC_CLOSEOUT.md).

## Before reporting

1. Confirm the exact app version and that the installer came from the official version-pinned
   GitHub release or `pcssak.com`.
2. Compare the installer SHA-256 with `SHA256SUMS.txt` from the same release.
3. Record the Windows edition, build and x64 architecture without including a device or account
   name.
4. State whether the affected PC is the host or connecting PC, whether administrator elevation was
   used, and whether the host network profile is Private, Domain or Public.
5. Identify the affected step: installation, startup, signed in-app update, automatic setup,
   sharing, mapping, pairing, PCSSAK-managed SSH setup/enable/disable/full restore, existing SSH
   service start/stop, SSH login, SFTP, recovery or
   uninstall.
6. Reproduce only with a small synthetic folder, account and filename. Do not repeat a step that
   could expand access or damage data.

Use the GitHub [bug report form](https://github.com/pcssakinc/pcssak-gongyu-releases/issues/new?template=bug-report.yml) for a reproducible
non-security defect and the [feature request form](https://github.com/pcssakinc/pcssak-gongyu-releases/issues/new?template=feature-request.yml)
for a recurring user problem. General help is available at `support@pcssak.com`.

Do not post passwords, private keys, pairing codes, real usernames, exact internal IP addresses,
share names, full paths, directory listings, customer files, complete network configurations or
raw logs. Replace them with synthetic values and a short sanitized excerpt.

For an exploitable vulnerability, privilege escalation, unintended access expansion or credential
exposure, do not open a public Issue. Follow [SECURITY.md](SECURITY.md).

## Support boundary

- Public free Early Access through 0.4.9 uses an x64 NSIS installer for Windows.
  An x86 installer is not published.
- Each official release contains exactly the nine files in
  [the release asset contract](docs/RELEASE-ASSET-CONTRACT.md). Stop if any asset is missing or its
  SHA-256 differs.
- Windows 11 Home/Pro x64 and Windows 10 22H2 Home/Pro x64 are validation targets, not a claim that
  every edition, build, device or organizational policy has completed hands-on validation.
- Native ARM64, Windows S mode, Windows Server, macOS and Linux are not supported release targets.
- PCSSAK-managed SSH setup uses the exact trusted physical Ethernet/Wi-Fi LAN. An identified Public LAN
  requires explicit trust consent before the app changes that network to Private. VPN software
  may remain connected, but VPN/tunnel/virtual paths are excluded from SSH access scope. Direct
  Internet access and router port forwarding remain unsupported; organizational policy is not bypassed.
- For PCSSAK-managed SSH, “Locally ready” verifies the host service, firewall and listener;
  it does not prove that another PC can log in or use SFTP.
- A verified existing SSH installation managed outside PCSSAK has separate service start/stop
  controls. Startup type, firewall, SSH configuration and installation are preserved. Existing
  network exposure remains; same-LAN-only protection is not applied or guaranteed. The original
  startup setting applies after reboot, so an automatic service may start again. Stopping the
  service does not establish that every existing session ended. For an Automatic or Manual
  installation before its first start, a missing sshd_config alone is accepted only when no
  PCSSAK-managed sharing account exists. A Disabled startup policy is not changed. Starting the service
  is blocked if its startup type is Disabled or required protection for PCSSAK-managed accounts
  cannot be verified. An unreadable management
  mode blocks service changes. Existing settings are not taken over or reset. Once a short service request starts, wait for
  final verification; it does not offer the managed installation progress or safe-stop controls.
- MSRA screen sharing and mouse control are not included. They are not the same as SSH.
- The installer is not Authenticode-signed and can show Unknown publisher or SmartScreen. Do not
  disable Windows security products to install it.
- Version 0.3.3 keeps the 0.2.0 legal documents and updater key. Users on public 0.2.0 through
  0.2.8, public 0.3.2 or unpublished 0.2.9, 0.3.0, and 0.3.1 with valid legal consent can check,
  download, verify, and approve the published 0.3.3 update in the app. Users on 0.1.9 still need
  interactive installation to review the current legal documents. Users on 0.1.8 or earlier also
  need the previously announced updater-key migration. Run the official 0.3.3 installer once for
  those manual transitions; do not bypass an old app's signature error.
- For 0.1.1 through 0.3.2, install over the existing app without first uninstalling it or deleting
  settings, sharing records, SSH configuration, or interrupted-operation records. Only 0.1.0
  requires separate removal before installation. Do not delete recovery records or mix version files
  to repair an already damaged installation; contact support instead. If the app was already
  removed, use the official installer without manually deleting retained Windows recovery records.
- For an interrupted operation, open the recovery card in Settings. Where available, automatic
  inspection reads the actual state and releases the block only after verifying a consistent
  completed or fully off state. Otherwise keep the records and use the matching SSH resume,
  retry, or administrator guidance. Reinstalling does not justify deleting recovery records.
- The dedicated older firewall-record recovery keeps original records, unresolved entries, and
  partial progress, and resumes only the plan the user approved. Ordinary SSH enable or automatic
  inspection does not complete this recovery. Screen cancellation or its 610-second wait limit
  does not cancel the actual worker. Stage n/m counts are not an overall success percentage.
  Duplicate requests remain blocked through the follow-up SSH status read; recovery does not
  automatically start SSH. An error may follow a partial change, so keep the records.
- Uninstall sharing cleanup removes tracked sharing, member connections, and recorded SMB settings
  while preserving SSH, network profiles, and their recovery records. User files are not deleted;
  local app-data removal is a separate choice. Save open files first. On failure, preserve the app
  and records and resume the same cleanup choice; full SSH restoration is a separate operation.
- Safe stop during an active PCSSAK-managed SSH change sends a cooperative request. It does not
  force Windows operations to terminate. DISM installation can finish before the next safe checkpoint;
  cancellation is reported only after rollback is verified. An operation already in final
  verification may still complete. Cancelling preparation does not cancel a Windows change
  already started.
- Later updates may be checked, downloaded, verified, and installed after approval in the app when
  the accepted legal documents are unchanged and the consent record is valid. New legal documents
  require renewed consent through interactive installation. See [the 0.3.3 notes](docs/RELEASE-NOTES-v0.3.3.md).
  The version-pinned release and its nine verified assets establish availability.
- The 0.1.5 correction targets the existing-folder preparation failure reported during 0.1.4
  installation. This does not remove SAC blocking or establish completion of the hands-on test matrix.
  Do not install older intermediate versions or disable security controls to work around this error.
  See [the correction notes](docs/RELEASE-NOTES-v0.1.5.md) and [SAC guidance](SECURITY.md).

## 이슈 등록 전 확인

1. 앱의 정확한 버전과 설치 파일이 공식 버전 고정 GitHub 릴리스 또는 `pcssak.com`에서
   내려받은 것인지 확인합니다.
2. 같은 릴리스의 `SHA256SUMS.txt`와 설치 파일 SHA-256을 비교합니다.
3. 기기명·계정명을 제외하고 Windows 에디션·빌드·x64 여부를 기록합니다.
4. 문제가 생긴 PC가 호스트인지 접속 PC인지, 관리자 승격 여부와 호스트 프로필이 Private·
   Domain·Public 중 무엇인지 기록합니다.
5. 설치·시작·서명된 앱 내 업데이트·자동 설정·공유·매핑·페어링·SSH 처음 설정/켜기/끄기/
   완전 원복, 기존 SSH 서비스 시작·중지, 로그인·SFTP·원복·제거 중 문제가 생긴 단계를 구분합니다.
6. 작은 합성 폴더·계정·파일명으로만 재현하고 접근 범위 확대나 데이터 손상 가능성이 있는
   단계는 반복하지 않습니다.

재현 가능한 일반 오류는 [버그 제보 양식](https://github.com/pcssakinc/pcssak-gongyu-releases/issues/new?template=bug-report.yml), 반복되는
사용자 문제는 [기능 제안 양식](https://github.com/pcssakinc/pcssak-gongyu-releases/issues/new?template=feature-request.yml)을 사용하세요.
일반 문의는 `support@pcssak.com`으로 받을 수 있습니다.

비밀번호·개인키·페어링 코드·실제 사용자명·정확한 내부 IP·공유명·전체 경로·폴더 목록·고객
파일·전체 네트워크 구성·원본 로그를 공개하지 마세요. 합성 값과 민감정보를 제거한 짧은 구간으로
바꾸세요. 악용 가능한 취약점·권한 상승·접근 범위 확대·자격증명 노출은 공개 Issue 대신
[보안 정책](SECURITY.md)을 따르세요.

## 지원 범위

- 0.4.9까지의 공개 무료 Early Access 설치 파일은 Windows x64 NSIS이며 x86 설치 파일은
  게시하지 않습니다.
- 각 공식 릴리스는 [릴리스 자산 계약](docs/RELEASE-ASSET-CONTRACT.md)의 정확한 9개 파일만
  포함합니다. 하나라도 없거나 SHA-256이 다르면 중단하세요.
- Windows 11 Home/Pro x64와 Windows 10 22H2 Home/Pro x64는 검증 목표이며, 모든 에디션·
  빌드·장치·조직 정책의 실기 완료를 의미하지 않습니다.
- ARM64 네이티브, Windows S 모드, Windows Server, macOS와 Linux는 지원 배포 대상이 아닙니다.
- PCSSAK 관리형 SSH는 정확히 확인한 신뢰 물리 Ethernet·Wi-Fi LAN을 사용합니다. 식별된 Public LAN은
  명시적 신뢰 동의 뒤 해당 네트워크만 Private으로 전환합니다. VPN 연결은 유지할 수 있으나
  VPN·터널·가상 경로는 SSH 허용 범위에서 제외합니다. 인터넷 직접 접속·포트포워딩은
  지원하지 않으며 조직 정책을 우회하지 않습니다.
- PCSSAK 관리형 SSH의 “로컬 준비 완료”는 호스트 서비스·방화벽·리스너 확인이며 다른 PC의
  로그인·SFTP 성공 증거가 아닙니다.
- PCSSAK 밖에서 관리하는 검증된 기존 SSH에는 별도 서비스 시작·중지를 제공합니다. 자동
  시작 유형·방화벽·SSH 설정·설치는 보존합니다. 기존 네트워크 노출 범위가 유지되며 같은
  LAN 전용 보호를 적용하거나 보장하지 않습니다. 재부팅에는 원래 시작 설정이 적용되어
  자동 시작 서비스가 다시 켜질 수 있습니다. 중지는 기존 세션 전체의 종료를 보증하지
  않습니다. 자동/수동 시작형 설치의 최초 실행 전에는 PCSSAK 관리 공유 계정이 없는 경우에만
  sshd_config 부재를 허용합니다. 사용 안 함 정책은 해제하지 않습니다.
  시작 유형이 사용 안 함이거나 PCSSAK 관리 계정에 필요한 보호를 확인하지 못하면 서비스 시작을
  중단하며, 관리 구분을 읽지 못하면 서비스 변경을 중단합니다. 기존 설정을 인수하거나
  초기화하지 않습니다. 짧은 서비스 요청이 시작되면 최종
  검증을 기다리며 관리형 설치 단계표나 안전 중지 버튼은 제공하지 않습니다.
- 화면 공유·마우스 제어용 MSRA는 포함되지 않으며 SSH와 다른 기능입니다.
- 설치 파일은 Authenticode 미서명이라 알 수 없는 게시자나 SmartScreen이 나타날 수 있습니다.
  설치를 위해 Windows 보안 기능을 끄지 마세요.
- 이번 0.3.3 버전은 0.2.0의 법률 정본·업데이트 키를 유지합니다. 정상 법률 동의 기록이 있는
  공개 0.2.0~0.2.8·0.3.2와 비공개 0.2.9·0.3.0·0.3.1 사용자는 공개된 0.3.3 자산을
  앱에서 확인·다운로드·검증·사용자 승인 후 업데이트할 수 있습니다. 0.1.9는 현행 문서를
  확인하는 대화형 설치가 필요하며, 0.1.8 이하는 앞서 고지한 업데이트 키 전환도 필요합니다.
  이 수동 전환 대상은 공식 0.3.3 설치본을 한 번 직접 실행하고 구형 앱의 서명 오류를 우회하지 마세요.
- 0.1.1~0.3.2 사용자는 기존 앱을 먼저 제거하거나 설정·공유 장부·SSH 설정·중단 기록을 지우지
  않고 덮어 설치합니다. 0.1.0만 별도 제거 후 설치합니다. 이미 손상된 설치를 복구하려고
  기록을 임의 삭제하거나 서로 다른 버전의 파일을 섞지 말고 지원에 문의하세요. 이미 앱을
  제거했다면 남은 Windows 복구 기록을 임의 삭제하지 않고 공식 설치본을 사용하세요.
- 중단 기록은 설정 복구 카드에서 확인하세요. 자동 점검이 제공되는 경우 실제 상태를 읽고
  일관된 완료 또는 완전히 꺼진 상태가 검증된 경우에만 차단을 해제합니다. 그 밖에는 기록을
  보존하고 해당 SSH 재개·재조회·관리자 안내를 따르세요. 재설치했다고 복구 기록을 지우지 마세요.
- 전용 「이전 방화벽 기록 복구」는 원문·미해결 항목·부분 진행을 보존하고 사용자가 승인한
  계획만 이어갑니다. 일반 SSH 켜기나 자동 점검으로 이 복구를 완료 처리하지 않습니다.
  조회 화면 취소나 610초 대기 상한은 실제 작업 취소가 아니며 단계 n/m은 전체 성공률이
  아닙니다. 후속 SSH 상태 판독까지 중복 요청을 막고 복구 후 SSH를 자동으로 켜지 않습니다.
  일부 변경 뒤 오류가 날 수도 있으므로 기록을 보존하세요.
- 제거의 공유 정리는 추적한 공유·회원 연결·기록된 SMB 설정을 정리하면서 SSH·네트워크
  프로필과 해당 원복 기록을 보존합니다. 사용자 파일은 삭제하지 않으며 로컬 앱 데이터
  삭제는 별도 선택입니다. 열린 파일을 먼저 저장하세요. 실패하면 앱과 기록을 보존하고
  같은 정리 선택으로 이어가며 SSH 완전 원복은 별도 기능입니다.
- PCSSAK 관리형 SSH 변경 중 안전 중지는 협조적 요청이며 Windows 작업을 강제 종료하지 않습니다. DISM
  설치는 끝난 뒤 다음 안전 지점에서 중지를 반영하고, 원복이 검증된 경우에만 취소로 표시합니다.
  마지막 검증 단계에서는 그대로 완료될 수도 있습니다. 준비 취소를 이미 시작한 Windows
  변경의 취소로 해석하지 않습니다.
- 후속 업데이트는 동의한 법률 정본이 그대로이고 동의 기록이 유효하면 앱에서 확인·다운로드·
  검증하고 사용자 승인 뒤 설치합니다. 법률 정본이 바뀌면 다시 대화형 설치에서 동의합니다.
  [0.3.3 안내](docs/RELEASE-NOTES-v0.3.3.md)를 함께 확인하세요. 실제 제공 여부는
  버전 고정 릴리스와 검증된 9자산으로 판단합니다.
- 0.1.5는 0.1.4 설치 때 보고된 기존 폴더 준비 오류의 수정 버전이며 SAC 차단 해제나
  전체 실측 완료를 뜻하지 않습니다. 오류를 피하려고 중간 구버전을 먼저 설치하거나 보안
  기능을 끄지 마세요. [수정 안내](docs/RELEASE-NOTES-v0.1.5.md)와 [SAC 안내](SECURITY.md)를
  함께 확인하세요.

## 0.3.3 공개 후 이행 계약

서명 자산이 공개됐으며 정상 법률 동의가 있는 공개 0.2.0~0.2.8·0.3.2 및
비공개 0.2.9·0.3.0·0.3.1에서 앱 업데이트를 확인할 수 있습니다. 0.1.1~0.3.2는
설정·공유·SSH·중단 기록을 보존하는 보호 교체 대상입니다. 0.1.9의 법률 문서 확인,
0.1.8 이하의 공개키 전환, 0.1.0의 별도 제거 예외는 위 기존 안내와 같습니다.
현재 문제를 해결하려고 시험본을 혼용하거나 기존 앱·복구 기록을 먼저 지우지 마세요.

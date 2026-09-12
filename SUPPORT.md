# Support / 고객지원

PCssak Gongyu 0.1.2 through 0.4.9 is Free Early Access. Support has no guaranteed response or fix deadline.
Reports are prioritized by safety impact, affected users and reproducibility.

PCssak Gongyu 0.1.2~0.4.9는 무료 Early Access입니다. 답변·수정 기한을 보장하는 지원 SLA는 없으며,
안전 영향·영향받는 사용자·재현 가능성을 기준으로 우선순위를 정합니다.

## Before reporting

1. Confirm the exact app version and that the installer came from the official version-pinned
   GitHub release or `pcssak.com`.
2. Compare the installer SHA-256 with `SHA256SUMS.txt` from the same release.
3. Record the Windows edition, build and x64 architecture without including a device or account
   name.
4. State whether the affected PC is the host or connecting PC, whether administrator elevation was
   used, and whether the host network profile is Private, Domain or Public.
5. Identify the affected step: installation, startup, signed in-app update, automatic setup,
   sharing, mapping, pairing, SSH setup/enable/disable/full reset, SSH login, SFTP, recovery or
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
- SSH setup uses the exact trusted physical Ethernet/Wi-Fi LAN. A reliably identified Public LAN
  requires explicit trust consent before the app changes that network to Private. VPN software
  may remain connected, but VPN/tunnel/virtual paths are excluded from SSH access scope. Direct
  Internet access and router port forwarding remain unsupported; organizational policy is not bypassed.
- “Locally ready” verifies the host service, firewall and listener; it does not prove that another
  PC can log in or use SFTP.
- MSRA screen sharing and mouse control are not included. They are not the same as SSH.
- The installer is not Authenticode-signed and can show Unknown publisher or SmartScreen. Do not
  disable Windows security products to install it.
- Version 0.2.3 keeps the 0.2.0 legal documents and updater key. Users on 0.2.0, 0.2.1, or 0.2.2 with valid legal
  consent can check, download, verify, and approve the update in the app. Users on 0.1.9 still need
  interactive installation to review the current legal documents. Users on 0.1.8 or earlier also
  need the previously announced updater-key migration. Run the official 0.2.3 installer once for
  those manual transitions; do not bypass an old app's signature error.
- For 0.1.1 through 0.2.2, install over the existing app without first uninstalling it or deleting
  settings, sharing records, SSH configuration, or interrupted-operation records. Only 0.1.0
  requires separate removal before installation. Do not delete recovery records or mix version files
  to repair an already damaged installation; contact support instead. If the app was already
  removed, use the official installer without manually deleting retained Windows recovery records.
- For an interrupted SSH operation, open the recovery card in Settings and use its matching
  resume button. If status cannot be read, keep the records and use the retry or administrator
  guidance shown there. Cancelling preparation does not cancel a Windows change already started.
- Later updates may be checked, downloaded, verified, and installed after approval in the app when
  the accepted legal documents are unchanged and the consent record is valid. New legal documents
  require renewed consent through interactive installation. See [the 0.2.3 notes](docs/RELEASE-NOTES-v0.2.3.md).
  The version-pinned release and its nine verified assets, not this preparation document, establish availability.
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
   완전 원복·로그인·SFTP·원복·제거 중 문제가 생긴 단계를 구분합니다.
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
- SSH는 정확히 확인한 신뢰 물리 Ethernet·Wi-Fi LAN을 사용합니다. 식별된 Public LAN은
  명시적 신뢰 동의 뒤 해당 네트워크만 Private으로 전환합니다. VPN 연결은 유지할 수 있으나
  VPN·터널·가상 경로는 SSH 허용 범위에서 제외합니다. 인터넷 직접 접속·포트포워딩은
  지원하지 않으며 조직 정책을 우회하지 않습니다.
- “로컬 준비 완료”는 호스트 서비스·방화벽·리스너 확인이며 다른 PC의 로그인·SFTP 성공 증거가
  아닙니다.
- 화면 공유·마우스 제어용 MSRA는 포함되지 않으며 SSH와 다른 기능입니다.
- 설치 파일은 Authenticode 미서명이라 알 수 없는 게시자나 SmartScreen이 나타날 수 있습니다.
  설치를 위해 Windows 보안 기능을 끄지 마세요.
- 0.2.3은 0.2.0의 법률 정본·업데이트 키를 유지합니다. 정상 법률 동의 기록이 있는 0.2.0·0.2.1·0.2.2는
  앱에서 확인·다운로드·검증·사용자 승인 후 업데이트할 수 있습니다. 0.1.9는 현행 문서를
  확인하는 대화형 설치가 필요하며, 0.1.8 이하는 앞서 고지한 업데이트 키 전환도 필요합니다.
  이 수동 전환 대상은 공식 0.2.3 설치본을 한 번 직접 실행하고 구형 앱의 서명 오류를 우회하지 마세요.
- 0.1.1~0.2.2는 기존 앱을 먼저 제거하거나 설정·공유 장부·SSH 설정·중단 기록을 지우지
  않고 덮어 설치합니다. 0.1.0만 별도 제거 후 설치합니다. 이미 손상된 설치를 복구하려고
  기록을 임의 삭제하거나 서로 다른 버전의 파일을 섞지 말고 지원에 문의하세요. 이미 앱을
  제거했다면 남은 Windows 복구 기록을 임의 삭제하지 않고 공식 설치본을 사용하세요.
- SSH 중단은 설정 복구 카드에서 해당 종류의 재개 버튼을 사용하세요. 상태를 읽지 못하면
  기록을 보존하고 카드의 재조회·관리자 안내를 따르세요. 준비 취소를 이미 시작한 Windows
  변경의 취소로 해석하지 않습니다.
- 후속 업데이트는 동의한 법률 정본이 그대로이고 동의 기록이 유효하면 앱에서 확인·다운로드·
  검증하고 사용자 승인 뒤 설치합니다. 법률 정본이 바뀌면 다시 대화형 설치에서 동의합니다.
  [0.2.3 안내](docs/RELEASE-NOTES-v0.2.3.md)를 함께 확인하세요. 실제 제공 여부는 이 준비 문서가
  아니라 버전 고정 릴리스와 검증된 9자산으로 판단합니다.
- 0.1.5는 0.1.4 설치 때 보고된 기존 폴더 준비 오류의 수정 버전이며 SAC 차단 해제나
  전체 실측 완료를 뜻하지 않습니다. 오류를 피하려고 중간 구버전을 먼저 설치하거나 보안
  기능을 끄지 마세요. [수정 안내](docs/RELEASE-NOTES-v0.1.5.md)와 [SAC 안내](SECURITY.md)를
  함께 확인하세요.

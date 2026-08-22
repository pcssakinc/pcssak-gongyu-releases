# Support / 고객지원

PCssak Gongyu 0.1.0 is Free Early Access. Support has no guaranteed response or fix deadline.
Reports are prioritized by safety impact, affected users and reproducibility.

PCssak Gongyu 0.1.0은 무료 Early Access입니다. 답변·수정 기한을 보장하는 지원 SLA는 없으며,
안전 영향·영향받는 사용자·재현 가능성을 기준으로 우선순위를 정합니다.

## Before reporting

1. Confirm the exact app version and that the installer came from the official version-pinned
   GitHub release or `pcssak.com`.
2. Compare the installer SHA-256 with `SHA256SUMS.txt` from the same release.
3. Record the Windows edition, build and x64 architecture without including a device or account
   name.
4. State whether the affected PC is the host or connecting PC, whether administrator elevation was
   used, and whether the host network profile is Private, Domain or Public.
5. Identify the affected step: installation, startup, automatic setup, sharing, mapping, pairing,
   SSH enable/status/disable, SSH login, SFTP, recovery or uninstall.
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

- The planned public installer is x64 NSIS for Windows. An x86 installer is not published.
- Windows 11 Home/Pro x64 and Windows 10 22H2 Home/Pro x64 are validation targets, not a claim that
  every edition, build, device or organizational policy has completed hands-on validation.
- Native ARM64, Windows S mode, Windows Server, macOS and Linux are not supported release targets.
- SSH setup is a core feature for a host PC on the same trusted LAN using a Private or Domain
  profile. Public networks, VPNs or tunnels, direct Internet access and router port forwarding are
  unsupported.
- “Locally ready” verifies the host service, firewall and listener; it does not prove that another
  PC can log in or use SFTP.
- MSRA screen sharing and mouse control are not included in 0.1.0. They are not the same as SSH.
- The installer is not Authenticode-signed and can show Unknown publisher or SmartScreen. Do not
  disable Windows security products to install it.
- The app has no automatic updater. Obtain later versions only from an official version-pinned
  release.

## 이슈 등록 전 확인

1. 앱의 정확한 버전과 설치 파일이 공식 버전 고정 GitHub 릴리스 또는 `pcssak.com`에서
   내려받은 것인지 확인합니다.
2. 같은 릴리스의 `SHA256SUMS.txt`와 설치 파일 SHA-256을 비교합니다.
3. 기기명·계정명을 제외하고 Windows 에디션·빌드·x64 여부를 기록합니다.
4. 문제가 생긴 PC가 호스트인지 접속 PC인지, 관리자 승격 여부와 호스트 프로필이 Private·
   Domain·Public 중 무엇인지 기록합니다.
5. 설치·시작·자동 설정·공유·매핑·페어링·SSH 켜기/상태/끄기·로그인·SFTP·원복·제거 중
   문제가 생긴 단계를 구분합니다.
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

- 공개 예정 설치 파일은 Windows x64 NSIS이며 x86 설치 파일은 게시하지 않습니다.
- Windows 11 Home/Pro x64와 Windows 10 22H2 Home/Pro x64는 검증 목표이며, 모든 에디션·
  빌드·장치·조직 정책의 실기 완료를 의미하지 않습니다.
- ARM64 네이티브, Windows S 모드, Windows Server, macOS와 Linux는 지원 배포 대상이 아닙니다.
- SSH는 같은 신뢰 LAN의 Private·Domain 호스트를 위한 핵심 기능입니다. Public·VPN·터널·
  인터넷 직접 접속·라우터 포트포워딩은 지원하지 않습니다.
- “로컬 준비 완료”는 호스트 서비스·방화벽·리스너 확인이며 다른 PC의 로그인·SFTP 성공 증거가
  아닙니다.
- 화면 공유·마우스 제어용 MSRA는 0.1.0에 포함되지 않으며 SSH와 다른 기능입니다.
- 설치 파일은 Authenticode 미서명이라 알 수 없는 게시자나 SmartScreen이 나타날 수 있습니다.
  설치를 위해 Windows 보안 기능을 끄지 마세요.
- 앱은 자동 업데이트를 제공하지 않습니다. 이후 버전도 공식 버전 고정 릴리스에서 확인하세요.

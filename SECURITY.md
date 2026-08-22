# Security Policy / 보안 정책

## English

Security reports are evaluated against the latest publicly available PCssak
Gongyu Free Early Access release. Early Access can contain undiscovered defects;
this policy is a reporting and response boundary, not a guarantee that defects
do not exist.

### Report privately

Use the repository's GitHub private vulnerability reporting channel when it is
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

### Network exposure boundary

Version 0.1.0 treats SSH as a separate, user-approved core feature for a host on
the same trusted LAN using a Private or Domain profile. The PCSSAK-owned inbound
rule is limited to the real Windows `sshd.exe`, TCP 22, physical Ethernet or Wi-Fi,
and the exact local IPv4/on-link scope present when SSH is enabled. Public networks,
VPNs or tunnels, direct Internet access and router port forwarding are unsupported.
Do not broaden the rule to all remote addresses or expose TCP 22 to the Internet.

A locally ready status does not prove a remote login. Verify the server host-key
fingerprint through a separate path and test the actual SSH/SFTP connection from
the second PC. MSRA screen sharing and mouse control are disabled and are not the
same as SSH.

### Verify downloads

Download only from `pcssakinc/pcssak-gongyu-releases` or a version-pinned link on
`pcssak.com`. Compare the installer SHA-256 with `SHA256SUMS.txt` from the same
release. The Early Access installer is not Authenticode-signed and no detached
Tauri updater `.sig` is published. Do not disable SmartScreen, Microsoft
Defender, a firewall, or another security product to bypass a warning.

## 한국어

보안 제보는 공개된 최신 PCssak Gongyu 무료 Early Access 버전을 기준으로 검토합니다.
Early Access에는 발견되지 않은 결함이 남아 있을 수 있으며, 이 정책은 제보와 대응 범위를
정하는 문서이지 결함이 없다는 보증이 아닙니다.

### 비공개 제보

GitHub 비공개 취약점 제보 기능을 사용할 수 있으면 그 채널을 우선합니다. 사용할 수 없으면
`support@pcssak.com`으로 다음 내용을 보내 주세요.

- 영향을 받는 PCssak Gongyu 버전과 Windows 에디션·빌드
- x64 아키텍처와 관리자 권한 실행 여부
- 최소 재현 절차, 기대 결과와 실제 결과
- 보안 영향과 이미 공개된 문제인지 여부
- 개인정보를 제거한 로그 또는 합성한 최소 재현 자료

암호, 개인키, 토큰, 복구 코드, 개인 문서나 다른 사람의 정보를 보내지 마세요. 소유하거나
명시적으로 허가받지 않은 시스템·계정은 시험하지 말고, 공개 전에 합리적인 수정 시간을
주세요.

### 네트워크 노출 경계

0.1.0의 SSH는 같은 신뢰 LAN에서 Private 또는 Domain 프로필을 사용하는 호스트의 별도 핵심
기능입니다. PCSSAK 소유 인바운드 규칙은 실제 Windows `sshd.exe`, TCP 22, 물리 Ethernet·
Wi-Fi와 SSH를 켠 순간의 정확한 로컬 IPv4·온링크 범위로 제한합니다. Public, VPN·터널,
인터넷 직접 접속과 라우터 포트포워딩은 지원하지 않습니다. 규칙을 모든 원격 주소로 넓히거나
TCP 22를 인터넷에 노출하지 마세요.

로컬 준비 상태는 원격 로그인을 증명하지 않습니다. 별도 경로로 서버 호스트 키 지문을 확인하고
두 번째 PC에서 실제 SSH/SFTP를 시험하세요. 화면 공유·마우스 제어용 MSRA는 비활성화되며
SSH와 같은 기능이 아닙니다.

### 다운로드 확인

`pcssakinc/pcssak-gongyu-releases` 또는 `pcssak.com`의 버전 고정 링크에서만 받고 같은
릴리스의 `SHA256SUMS.txt`와 설치 파일 SHA-256을 비교하세요. Early Access 설치 파일에는
Authenticode 서명이 없고 Tauri 업데이트용 분리 `.sig`도 게시하지 않습니다. 경고를
우회하려고 SmartScreen, Microsoft Defender, 방화벽 또는 다른 보안 제품을 끄지 마세요.

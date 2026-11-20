# PCssak Gongyu 0.4.9 · 무료 수동 설치판 / Free manual download

Windows x64 · 20,716,953 bytes

SHA-256: `4e19e0fcc61cdfe162143fa8837eeefc148ab69a4910d23b590b164e9939ee26`

## 한국어

Windows 10·11 x64에서 폴더 공유와 네트워크 드라이브를 관리하고, 필요할 때 같은 LAN의 SSH 접속을 설정하는 무료 사전 공개판입니다. 계정, 결제, 제품 키 없이 사용할 수 있습니다. 이번 버전은 직접 내려받아 설치합니다.

1. 이 릴리스의 `PCssak-Gongyu-0.4.9-Windows-x64-Setup.exe`와 `SHA256SUMS.txt`를 내려받으세요.
2. PowerShell에서 `Get-FileHash .\PCssak-Gongyu-0.4.9-Windows-x64-Setup.exe -Algorithm SHA256`을 실행하고 설치 파일의 해시가 목록과 일치하는지 확인하세요.
3. 설치 파일을 실행해 안내를 따르세요. Windows 게시자 서명(Authenticode)이 없어 경고나 조직 정책에 따른 차단이 생길 수 있습니다. Windows 보안 기능을 켠 상태로 사용하세요.

0.4.2 사용자는 설치본을 직접 실행해 기존 설치를 업데이트합니다. 0.1.1~0.4.8에는 기존 설정과 공유 기록을 보존하는 덮어 설치 경로가 있습니다. 0.1.0은 제거 후 설치하세요. 기존 앱의 자동 업데이트 채널은 0.4.2입니다.

0.4.2 이후의 변경에는 SSH 로그인을 허용할 로컬 계정 선택, 최근 24시간 로그인 실패 횟수 표시, 업그레이드 뒤 다시 적용할 SSH 보안 설정 안내가 포함됩니다. PC가 여러 네트워크를 오갈 때는 연결된 망부터 설정을 복원할 수 있습니다. Windows의 네트워크 프로필을 확인하지 못했을 때의 진단도 개선했습니다.

0.4.9 설치본의 실제 설치·업그레이드·제거·재부팅, 물리 PC 두 대 사이의 SSH/SFTP 연결, Windows 10/11 Home·Pro 전체 조합, Windows Server 2019 문제 장비에서의 복구는 현장 확인이 남아 있습니다. 외부 법률·공급망 검토도 미완료입니다. Windows 보호 기능을 유지하고 복구 가능한 PC에서 먼저 사용하세요. 설치본에 해당하는 MPL 소스와 제3자 고지를 같은 릴리스에서 받을 수 있습니다.

## English

PCssak Gongyu helps you share folders and map drives on a trusted LAN, with optional SSH setup. This free Early Access build is for Windows 10/11 x64. No account, payment or product key is required.

Download `PCssak-Gongyu-0.4.9-Windows-x64-Setup.exe` and `SHA256SUMS.txt` from this release. Compare the installer’s SHA-256 using the PowerShell command above, then run it interactively. Windows may warn about the unknown publisher or your organization may block installation. Keep Windows security protections enabled.

Install manually over versions 0.1.1–0.4.8 to use the protected replacement path. Uninstall 0.1.0 before installing. Existing apps continue to use 0.4.2 on their signed update channel. Version 0.4.9 adds SSH account selection, failed-login counts, guidance on reapplying security settings after an upgrade, per-network restoration, and improved network-profile diagnostics.

Hands-on installation, upgrades, removal and reboot tests, two-PC SSH/SFTP, the full Windows Home/Pro matrix and recovery on the affected Windows Server 2019 machine remain unverified. External legal and independent supply-chain reviews are outstanding. Start on a recoverable PC. The matching MPL source archive and third-party notices are included with the download.

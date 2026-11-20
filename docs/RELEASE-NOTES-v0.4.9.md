# PCssak Gongyu 0.4.9 — Free Early Access 변경일기

0.4.2 이후 자동 공유와 SSH가 Windows 업데이트·방화벽 변경·망 변경 뒤에도 지금 PC의 실제 상태로 동작하는지, 그리고 이 앱이 여는 문(SSH·파일 공유·페어링)이 외부 공격의 통로가 되지 않는지를 집중해서 다듬었습니다. 0.4.3부터 0.4.8까지는 내부 시험판으로만 만들었고 공개하지 않았으므로, 0.4.2를 쓰던 분께는 이번 0.4.9가 그 변경을 모두 담은 첫 공개판입니다. 아래는 0.4.9에서 새로 바뀐 점과 0.4.2 이후 누적된 변경입니다.

0.4.9는 누구나 계정·결제·제품 키 없이 내려받을 수 있는 Windows x64 무료 사전 공개판입니다.

## SSH 로그인 허용 계정을 앱 안에서 관리

0.4.8부터 SSH는 전용 로컬 그룹 `pcssak-ssh-users`에 있는 계정만 로그인할 수 있고, 켤 때 지금 로그인한 Windows 계정만 넣었습니다. 다른 계정은 관리자 명령 프롬프트에서 직접 추가해야 했습니다.

0.4.9는 SSH 카드에 「SSH 로그인 허용 계정」을 추가했습니다. 펼치면 현재 구성원과 지금 로그인한 계정을 보여 주고, 이 PC의 사용 가능한 일반 계정을 골라 추가하거나 뺄 수 있습니다.

- 추가는 이 PC의 사용 가능한 일반 로컬 계정만 받습니다. 앱이 목록을 다시 읽어 정확히 같은 이름일 때만 추가합니다. 공유 전용 계정·사용 안 함 계정·도메인 형식 이름은 거부합니다.
- 빼기는 현재 구성원 목록에서 고른 항목만, 그 계정의 보안 식별자(SID)로 지웁니다. 마지막 구성원을 뺄 때는 아무도 SSH로 로그인할 수 없게 된다는 확인을 한 번 더 받습니다.
- 그룹이 없으면(SSH를 아직 켜지 않음) 새로 만들지 않고 「SSH 사용하기」를 먼저 안내합니다.
- 변경은 다음 로그인부터 적용되며 sshd를 다시 시작하지 않습니다. 이미 연결된 세션은 끊지 않습니다. 추가·빼기에는 관리자 권한이 필요하고, 로그에는 계정 이름 대신 건수만 남깁니다.

## 이전 버전에서 켠 SSH의 보안 설정 미적용 표시

0.4.7 이하에서 SSH를 켠 뒤 업데이트한 PC는 접속은 되지만 0.4.8의 `sshd_config` 관리 보안 블록(비밀번호 반복 실패 차단·허용 계정 제한·LAN 밖 로그인 거부)이 없습니다. 0.4.8까지 상태 화면은 이런 PC를 「준비 완료」로만 보여 줬습니다.

0.4.9는 앱이 관리하는 SSH가 실행 중인데 관리 보안 블록이 없거나 옛 판이면 「보안 설정 미적용 — 「SSH 사용하기」를 다시 누르면 적용」을 표시합니다. 판독은 읽기 전용이며, 설정 파일을 읽지 못하면 미적용으로 단정하지 않고 확인 불가로 둡니다. 계약 밖 허용 규칙이 따로 있으면 위험 표시가 우선합니다.

같은 점검에서 0.4.8의 망 변경 안내가 실제 버튼(「SSH 사용하기」)과 다른 이름을 가리키던 문구를 10개 언어 모두 실제 버튼 이름으로 고쳤습니다.

## 최근 SSH 로그인 실패 수

대시보드 「보안 점검」 카드에 최근 24시간의 SSH 비밀번호 로그인 실패 기록 수를 표시합니다. Windows용 OpenSSH가 기본으로 남기는 `OpenSSH/Operational` 이벤트 기록에서 개수만 셉니다. 계정 이름·출발 주소·원문은 화면에 보이지도, 앱 로그에 남지도 않습니다.

- 0회는 확인 표시, 1회 이상은 주의와 함께 「모두 닫기」·허용 계정 확인을 안내합니다. 검사 상한(5,000건)에 걸리면 비밀번호를 대입하는 중일 수 있다고 강하게 알립니다.
- 기록을 읽지 못하면(관리자 권한 필요·OpenSSH 이벤트 기록 꺼짐) 0회가 아니라 확인 불가로 표시합니다.
- 사용자가 `sshd_config`의 기록 수준을 낮췄거나 파일 기록을 쓰면 실패가 이 채널에 남지 않습니다. 0회는 "기록된 실패 없음"이며 공격이 없었다는 보증이 아닙니다.

## 공인 IP 전용 안내

공유기 없이 공인 IP나 통신사(CGNAT) IP를 직접 받은 PC는 0.4.8부터 SSH·파일 공유 허용 범위를 만들지 않았습니다. 다만 안내는 일반적인 "주소 범위 미지원" 문구에 한 문장을 덧붙인 형태였습니다.

0.4.9는 거부 원인이 공인·통신사 IP 직결뿐일 때 SSH와 파일 공유에 각각 전용 안내를 보여 줍니다. 사설 IP(예: 192.168.x.x)를 주는 공유기에 연결하라는 해결 방법을 함께 안내합니다. 환경 진단도 "물리 LAN 미확인" 대신 공인 IP 직결 경고를 냅니다. 다른 미지원 주소가 섞여 있으면 원인을 하나로 단정하지 않고 기존 일반 안내를 유지합니다.

## 자동 설정·SSH의 "네트워크 프로필 확인 실패" 조사와 보완

0.4.5를 Windows Server 2019에서 실행했을 때 자동 설정과 SSH가 모두 "네트워크 프로필을 확인하지 못했다"로 멈춘 사용자 보고가 있었습니다. 해당 서버의 실제 상태는 아직 확보하지 못해 원인을 하나로 확정하지 않았습니다. 대신 이 안내가 나오는 경로를 코드에서 모두 추적해, 고칠 수 있는 결함은 고치고 다음 실행에서 원인이 바로 드러나도록 보완했습니다.

- 이 안내는 유선·Wi-Fi 물리 NIC와 IPv4 주소는 찾았지만, Windows 네트워크 목록 관리자(NLM)에서 그 NIC의 연결된 네트워크나 범주(도메인·개인·공용)를 확인하지 못했을 때만 나옵니다.
- 결함 수정: 보완 조회는 PC에 저장된 오래된 비연결 네트워크까지 훑습니다. 그중 하나가 응답하지 않으면 보완 조회 전체가 중단됐습니다. 서버처럼 저장된 네트워크가 많은 PC에서 현재 LAN이 정상이어도 실패할 수 있던 경로라, 응답하지 않는 항목만 건너뛰도록 고쳤습니다. 최종 채택은 여전히 요청한 NIC와 정확히 결속된 네트워크만 하므로 안전 기준은 그대로입니다.
- 진단 보완: 「보안 점검」의 「진단 정보 복사」에 실패 세부 코드(예: 결속 누락·범주 미확인)와 네트워크 위치 인식(NlaSvc)·네트워크 목록(netprofm) 서비스 상태를 넣었습니다. 세부 코드는 영문 고정 코드만 담고 주소·식별자는 담지 않습니다.
- 서버 OS 실측: 허브의 Windows Server 2025(빌드 26100)에서 같은 판정 경로를 읽기 전용으로 실행했습니다. NlaSvc가 수동·정지 상태인데도 네트워크 목록 서비스(netprofm)만으로 프로필 판정이 정상이었습니다. 그래서 최신 Windows에서는 NlaSvc 정지를 문제로 보지 않습니다.
- 안내 보완: NlaSvc가 자동 시작인데 멈췄을 때, 또는 실제로 프로필 판정이 실패했고 NlaSvc가 실행 중이 아닐 때만 보안 점검에 경고를 띄웁니다. netprofm이 사용 안 함이면 경고합니다. 프로필 확인 실패 안내에는 진단 정보 전달 방법과, Windows Server 2019 같은 이전 Windows의 NlaSvc 확인을 덧붙였습니다. 앱이 서비스를 직접 켜지는 않습니다.
- 진단 결함 수정: 0.4.8의 환경 진단은 공용(Public) 프로필의 정상 LAN을 "물리 LAN 미확인"으로 잘못 표시했습니다(실측에서 확인). 이제 자동 설정·SSH와 같은 사전 판정을 써서 공용 프로필이면 그 사실만 기록하고 경고하지 않습니다.

## 완전 원복이 끝나지 않던 문제 수정

SSH를 켜면서 공용(Public) 네트워크를 개인(Private)으로 바꾼 기록이 여러 네트워크에 걸쳐 있으면, 0.4.8까지 완전 원복은 기록된 **모든** 네트워크에 동시에 연결돼 있어야만 끝났습니다. 예를 들어 집과 사무실을 오가는 노트북은 집에서는 집 네트워크만, 사무실에서는 사무실 네트워크만 되돌릴 수 있어 원복이 영원히 완료되지 않았습니다.

0.4.9는 네트워크별로 결과를 나눕니다. 지금 연결된 상태에서 공용 복원이 확인된 네트워크만 기록에서 빼고, 연결되지 않은 네트워크는 추측해 바꾸지 않고 기록에 남깁니다. 원복 결과에는 남은 네트워크 수와 함께 "그 네트워크에 다시 연결한 뒤 「우리 SSH 설정 원복」을 한 번 더"라는 안내가 나옵니다. 남은 네트워크가 있는 동안 SSH 보호 차단 규칙은 그대로 유지됩니다.

SSH 켜기 실패 뒤의 되돌리기와 공유 설정의 네트워크 원복은 지금처럼 모든 네트워크가 확인돼야 성공으로 처리합니다. 공유 원복이 새 결과를 확인하지 않고 기록을 지울 수 있던 회귀는 개발 중에 발견해 막았습니다.

## 0.4.2 이후 누적된 변경(0.4.3~0.4.8, 공개하지 않은 내부 시험판)

**SSH 보안 경계.** SSH를 켜면 `sshd_config`에 앱 관리 블록을 둡니다. 기존 설정은 보존하고 `sshd -t` 설정 검사를 통과한 후보만 원자 교체합니다.

- 비밀번호 반복 실패 차단: `MaxAuthTries 4`, `LoginGraceTime 60`, `MaxStartups 10:30:60`.
- 허용 계정 제한: 전용 그룹 `pcssak-ssh-users`에 켤 때 로그인한 Windows 계정만 넣고 `AllowGroups`로 제한합니다. 다른 관리자로 UAC를 승인해도 그 관리자는 자동으로 들어가지 않습니다.
- LAN 밖 로그인 거부: 파일 끝의 `Match Address` 블록이 승인한 현재 물리 LAN 대역 밖의 로그인을 sshd 단계에서 거부합니다. 방화벽이 꺼져도 유지됩니다.
- 공유기 없이 공인·통신사(CGNAT) IP를 직접 받은 PC는 SSH·파일 공유 허용 범위를 만들지 않습니다.
- 완전 원복은 관리 블록을 지우고, 이 앱이 만든 경우에만 전용 그룹을 지웁니다.

**자동 공유와 페어링.**

- 자동 설정은 FDResPub·fdPHost·LanmanServer·LanmanWorkstation·Dnscache 다섯 서비스만 자동 시작으로 바꿉니다. UPnP 계열(SSDPSRV·UPnPHost)은 더 이상 켜지 않으며, 「설정 원복」은 과거에 켠 기록도 계속 되돌립니다.
- 공유 페어링 수신 규칙(19763)은 LocalSubnet 대신 현재 물리 LAN의 주소·인터페이스·프로필과 실행 파일 경로에 묶습니다. 같은 PC(루프백·자기 주소)에서 온 연결은 거부합니다.
- 가입 승인 목록은 요청자가 고른 표시 이름과 별도로 실제 연결의 출발 IP를 보여 줍니다.
- LAN 스캔은 모든 PC의 공유 목록을 현재 자격 증명으로 자동 조회하지 않고, 고른 PC에만 「공유 목록 보기」로 조회합니다.
- 관리자 권한으로 다시 실행한 뒤 공유 생성·초대 발급을 자동 실행하지 않고 다시 확인을 받습니다. 시작 직후 `WEBVIEW2_*` 환경변수를 지웁니다.

**환경 적응.**

- 자동 설정과 SSH는 과거 복구 기록이 아니라 지금 확인한 서비스·물리 네트워크·방화벽 상태로 동작합니다. 현재 주소와 인터페이스가 같은 실제 직접 경로로 허용 범위를 계산합니다.
- 물리 랜카드별로 주소·이름·프로필을 묶어, 프로필을 확인하지 못한 보조 랜카드가 정상 연결의 설정을 막지 않게 했습니다. 서버의 NIC 팀(LBFO)은 하위가 모두 물리 NIC일 때 인정합니다.
- SSH 켜기는 지금 연결된 망만 확인해, 과거에 다른 LAN에서 동의한 기록 때문에 막히지 않습니다. IP·서브넷이 바뀌면 상태 화면이 「다시 켜기로 재조정」을 안내합니다.
- Windows 업데이트 뒤 OpenSSH 실행 파일과 DLL이 맞지 않는 경우, 「SSH 사용하기」 안에서 앱에 동봉한 공식 Microsoft OpenSSH 10.4.0.0p1-Preview 묶음으로 자동 설치·복구합니다. Windows의 OpenSSH 폴더·DLL·PATH를 덮어쓰지 않고 키·설정을 보존합니다. 공식 미리 보기 판이며 운영 준비 완료 판으로 표시되지 않았습니다.
- 대시보드 「보안 점검 — 이 PC가 열어 둔 문」이 SSH(22)·파일 공유(445/139)·페어링(19763)의 열림 상태와 환경 위험(방화벽 꺼짐·타사 방화벽·그룹 정책·계정 잠금 꺼짐 등)을 보여 주고, 「모두 닫기」로 SSH 끄기·페어링 중지·이 앱이 만든 파일 공유 방화벽 규칙 제거를 한 번에 실행합니다. 「진단 정보 복사」는 개인정보 없는 진단 JSON을 복사합니다.

## 설치와 업데이트

1. 이 릴리스의 `PCssak-Gongyu-0.4.9-Windows-x64-Setup.exe`와 `SHA256SUMS.txt`를 내려받으세요.
2. PowerShell에서 `Get-FileHash .\PCssak-Gongyu-0.4.9-Windows-x64-Setup.exe -Algorithm SHA256`을 실행하고 설치 파일의 해시가 목록과 일치하는지 확인하세요.
3. 설치 파일을 실행해 안내를 따르세요. Windows 게시자 서명(Authenticode)이 없어 경고나 조직 정책에 따른 차단이 생길 수 있습니다. Windows 보안 기능을 켠 상태로 사용하세요.

0.4.2 사용자는 설치본을 직접 실행해 기존 설치를 업데이트합니다. 0.1.1~0.4.8에는 기존 설정과 공유 기록을 보존하는 덮어 설치 경로가 있습니다. 0.1.0은 제거 후 설치하세요. 기존 앱의 자동 업데이트 채널은 0.4.2입니다.

설치 파일은 20,716,953바이트이며 SHA-256은 `4e19e0fcc61cdfe162143fa8837eeefc148ab69a4910d23b590b164e9939ee26`입니다. 설치 파일에 대응하는 MPL 원본과 제3자 고지도 같은 릴리스에서 받을 수 있습니다.

## 확인한 것과 아직 확인하지 못한 것

Windows CI와 보안 검사를 통과했습니다. Windows x64 설치 파일을 풀어 안에 든 실행 파일의 버전과 빌드 결과를 대조했습니다. 공개 링크에서 로그인 없이 설치 파일을 다시 내려받아 크기와 SHA-256이 게시한 값과 일치하는 것도 확인했습니다.

0.4.9 설치본의 실제 설치·업그레이드·제거·재부팅, 물리 PC 두 대 사이의 SSH/SFTP 연결, Windows 10/11 Home·Pro 전체 조합, Windows Server 2019 문제 장비에서의 복구는 현장 확인이 남아 있습니다. 외부 법률·공급망 검토도 미완료입니다. Windows 보호 기능을 유지하고 복구 가능한 PC에서 먼저 사용하세요. 설치본에 해당하는 MPL 소스와 제3자 고지를 같은 릴리스에서 받을 수 있습니다.

## English

PCssak Gongyu helps you share folders and map drives on a trusted LAN, with optional SSH setup. This free Early Access build is for Windows 10/11 x64. No account, payment or product key is required.

Download `PCssak-Gongyu-0.4.9-Windows-x64-Setup.exe` and `SHA256SUMS.txt` from this release. Compare the installer’s SHA-256 using the PowerShell command above, then run it interactively. Windows may warn about the unknown publisher or your organization may block installation. Keep Windows security protections enabled.

Install manually over versions 0.1.1–0.4.8 to use the protected replacement path. Uninstall 0.1.0 before installing. Existing apps continue to use 0.4.2 on their signed update channel. Version 0.4.9 adds SSH account selection, failed-login counts, guidance on reapplying security settings after an upgrade, per-network restoration, and improved network-profile diagnostics.

Hands-on installation, upgrades, removal and reboot tests, two-PC SSH/SFTP, the full Windows Home/Pro matrix and recovery on the affected Windows Server 2019 machine remain unverified. External legal and independent supply-chain reviews are outstanding. Start on a recoverable PC. The matching MPL source archive and third-party notices are included with the download.

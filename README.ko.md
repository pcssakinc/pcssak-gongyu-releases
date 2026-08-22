# PCssak Gongyu - 공식 Windows 다운로드

**언어:** [English](README.md) · 한국어

PCssak Gongyu는 사용자가 지시하는 Windows SMB 공유 폴더 설정, LAN 점검, 네트워크 드라이브
관리, 짧은 공유 페어링과 별도로 동의한 OpenSSH Server 설정을 돕는 PCSSAK Windows 도구입니다.

첫 공개 채널은 **PCssak Gongyu 0.1.0 무료 Early Access**입니다. 실제 제공 여부는 버전 고정
[`v0.1.0` GitHub 릴리스](https://github.com/pcssakinc/pcssak-gongyu-releases/releases/tag/v0.1.0)로만
판단합니다. 해당 페이지에 설치 파일과 고정 자산 전체가 없으면 공식 공개 0.1.0 설치 파일도
없습니다.

## 다운로드

위 버전 고정 릴리스 또는 [PCssak Gongyu 공식 제품 페이지](https://pcssak.co.kr/gongyu)만
사용하세요. 공개 0.1.0에는 Windows x64 설치 파일 하나만 포함합니다.

- `PCssak-Gongyu-Beta-Windows-x64-Setup.exe`

x86 파일, 출처 불명 미러, 메신저 첨부와 재포장 설치 파일을 사용하지 마세요. 실행 전에 같은
릴리스의 `SHA256SUMS.txt`와 설치 파일 SHA-256을 비교하세요.

```powershell
Get-FileHash -Algorithm SHA256 '.\PCssak-Gongyu-Beta-Windows-x64-Setup.exe'
```

출력값이 정확한 파일명 옆의 값과 한 글자도 빠짐없이 일치해야 합니다. 출처·파일명·크기·해시 중
하나라도 다르면 실행하지 마세요.

## 처음 설치할 때

1. 공식 출처, 파일명과 SHA-256을 확인합니다.
2. x64 NSIS 설치 파일을 실행하고 해당 릴리스가 실제 제공하는 설치 언어 중 하나를 선택합니다.
3. 국문 정본 EULA와 영문 참고 번역을 읽고 동의하지 않으면 취소합니다.
4. 앱 이름이 **PCssak Gongyu**인지 확인한 뒤에만 Windows 관리자 승격을 승인합니다.
5. 설치를 마치고 앱을 연 뒤 필요하면 설정에서 원하는 앱 언어를 선택합니다.
6. 민감하지 않은 시험 폴더부터 시작하고 독립된 백업을 유지합니다.

설치기와 앱은 한국어, 영어, 일본어, 중국어 간체·번체, 프랑스어, 독일어, 러시아어, 브라질
포르투갈어와 튀르키예어 10개로 구성했습니다. 언어 선택과 첫 실행 전달은 자동검사했지만,
Windows 언어별 전체 실기 행렬은 이번 무료 Early Access 공개 전에 완료하지 않았습니다.

## 미서명 Early Access 경계

0.1.0 설치 파일에는 **Windows Authenticode 서명이 없고**, 앱에는 자동 업데이트 기능이
없습니다. Tauri 업데이트용 분리 `.sig`도 게시하지 않습니다. Windows에 **알 수 없는 게시자**
또는 Microsoft Defender SmartScreen 평판 안내가 나타날 수 있습니다.

SmartScreen, Microsoft Defender, 방화벽과 다른 보안 제품을 끄지 마세요. 업데이트 서명,
SHA-256 또는 공식 파일명이 Authenticode 게시자 신원을 대신하지 않습니다. 0.1.0의 진본 확인은
공식 버전 고정 출처와 공개 해시 일치에 의존합니다.

## 같은 LAN 공유와 SSH

PCssak Gongyu는 같은 신뢰 공유기와 LAN의 PC를 대상으로 합니다.

- Domain·Private `LocalSubnet` 방화벽 규칙을 사용하는 SMB 준비와 원복
- PCSSAK 소유권 증거가 있는 공유 폴더와 권한
- 네트워크 드라이브와 사용자가 선택한 자격증명 저장
- 8자리·5분·1회용 공유 페어링
- 별도로 동의한 OpenSSH Server·`sshd`·TCP 22 설정

SSH는 제거된 원격 기능이 아니라 **0.1.0 핵심 기능**입니다. 호스트 PC는 같은 LAN의 물리
Ethernet·Wi-Fi에서 **Private 또는 Domain** 프로필을 사용해야 합니다. PCSSAK 소유 규칙은 실제
Windows `sshd.exe`와 SSH를 켠 순간의 정확한 로컬 IPv4·온링크 범위에 결속됩니다.

**Public 네트워크, VPN·터널, 인터넷 직접 접속과 라우터 포트포워딩은 지원하지 않습니다.**
방화벽 규칙을 모든 원격 주소로 넓히거나 TCP 22를 인터넷에 노출하지 마세요. 네트워크나 DHCP
주소가 바뀌면 SSH를 끄고 새 LAN을 신뢰할 수 있는지 확인한 뒤 다시 켜야 합니다.

“로컬 준비 완료”는 호스트 서비스·방화벽·리스너를 확인한 결과이며 다른 PC의 실제 로그인·
SFTP 성공을 증명하지 않습니다. 첫 접속은 별도 경로로 서버 호스트 키 지문을 확인하세요.

화면 공유·마우스 제어용 MSRA는 0.1.0에서 비활성화됩니다. 같은 LAN SSH 원격 셸·명령 실행·
SFTP와는 다른 기능입니다.

## 릴리스 파일

공개 `v0.1.0` prerelease에는 아래 다섯 자산만 정확히 포함해야 합니다.

1. `PCssak-Gongyu-Beta-Windows-x64-Setup.exe`
2. `PCssak-Gongyu-0.1.0-MPL-Sources.zip`
3. `THIRD-PARTY-NOTICES.txt`
4. `latest.json`
5. `SHA256SUMS.txt`

릴리스 제목에 Early Access라고 쓰는 것만으로는 부족하며 GitHub 기계 판독 상태도
`prerelease=true`여야 합니다. GitHub `/releases/latest`는 prerelease를 제외하므로 제품·다운로드
링크는 정확한 `v0.1.0` 태그를 사용합니다.

`latest.json`은 [`latest.schema.json`](latest.schema.json)으로 검증하는 PCSSAK 다운로드
메타데이터입니다. Tauri 업데이트 매니페스트가 아니며 서명된 자동 업데이트 채널처럼 표시하면
안 됩니다. 전체 기준은 [릴리스 자산 계약](docs/RELEASE-ASSET-CONTRACT.md)을 확인하세요.

## 호환성 상태

- 검증 목표: Windows 11 Home/Pro x64, Windows 10 22H2 Home/Pro x64
- 공개 아키텍처: x64만
- 미게시: Windows x86
- 미지원 배포 대상: ARM64 네이티브, Windows S 모드, Windows Server, macOS, Linux

이는 범위와 목표이며 모든 환경의 실기가 완료됐다는 뜻이 아닙니다. Windows 10 일반 지원은
종료됐으므로 ESU·LTSC 수명주기를 별도로 확인하세요. [알려진 한계](docs/KNOWN-LIMITATIONS.ko.md)를
읽어 주세요.

## 로컬 처리와 원복

앱에는 PCSSAK 텔레메트리, 광고, 온라인 계정, 자동 오류 업로드, 라이선스 서버 또는 자동
업데이트가 없습니다. 로컬 설정·네트워크 식별자·경로·저널·자격증명을 PCSSAK으로 자동
업로드하지 않습니다.

사용자가 실행한 LAN·SMB·Wake-on-LAN·페어링·SSH는 선택한 로컬 장치와 통신합니다. OpenSSH
Server 설치는 Windows Update·WSUS 또는 조직이 정한 원본과 통신할 수 있습니다.

원복과 제거는 사용자가 만든 모든 공유·매핑·Windows 자격증명·로컬 앱 데이터·자동 시작·
별도로 켠 OpenSSH/SSH를 자동 삭제하지 않습니다. 제거 전에 앱 상태와 문서를 확인하세요.

## Early Access 개선에 참여하기

- 재현 가능한 일반 오류는 [버그 제보 양식](https://github.com/pcssakinc/pcssak-gongyu-releases/issues/new?template=bug-report.yml)을 사용합니다.
- 반복되는 사용자 문제와 안전 영향은 [기능 제안 양식](https://github.com/pcssakinc/pcssak-gongyu-releases/issues/new?template=feature-request.yml)에
  적습니다.
- 악용 가능한 취약점·자격증명 노출 가능성은 [SECURITY.md](SECURITY.md)를 따릅니다.
- 일반 지원: `support@pcssak.com`
- 개인정보 권리 요청: `privacy@pcssak.com`

비밀번호·개인키·페어링 코드·실제 사용자명·정확한 내부 IP·공유명·전체 경로·폴더 목록·고객
파일·전체 네트워크 구성·원본 로그를 공개 Issue에 올리지 마세요.

## 문서

- [English release guide](README.md)
- [최종 사용자 이용약관](EULA.md)과 [설치기용 텍스트](EULA.txt)
- [개인정보 처리방침](PRIVACY.md)
- [고객지원](SUPPORT.md)
- [품질과 안전](docs/QUALITY-AND-SAFETY.ko.md)
- [알려진 한계](docs/KNOWN-LIMITATIONS.ko.md)
- [제3자 소프트웨어 고지](THIRD-PARTY-NOTICES.txt)
- [MPL 원본 안내](docs/THIRD-PARTY-SOURCE.md)
- [v0.1.0 릴리스 노트](docs/RELEASE-NOTES-v0.1.0.md)
- [릴리스 자산 계약](docs/RELEASE-ASSET-CONTRACT.md)
- [Issue·기여 원칙](CONTRIBUTING.md)

## 개발과 책임

PCssak Gongyu는 PCSSAK 명칭 아래 독립적으로 지휘·관리합니다. AI 도구는 조사·구현·검토·시험·
문서화를 보조할 수 있지만 최종 요구사항·기술 결정·출시 승인·유지보수는 사람이 통제합니다.

이 공개 저장소는 릴리스 설치 파일, 문서, 제3자 고지와 필요한 MPL 원본 묶음을 배포합니다.
별도로 식별한 제3자 구성요소를 제외한 자체 애플리케이션 소스는 비공개 독점 소프트웨어로
유지합니다.

적용 법률이 허용하는 범위에서 국문 EULA·개인정보 처리방침이 기준이며 영문은 참고 번역입니다.
PCSSAK은 이 문서가 모든 국가·지역의 법률 준수를 인증한다고 주장하지 않습니다.

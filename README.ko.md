# PCssak Gongyu 릴리스

[English](README.md)

> 이 디렉터리는 PCssak Gongyu v0.4.0 무료 Early Access의 공개 저장소 계약입니다.
> 게시 완료는 불변 릴리스와 검증된 아홉 자산의 실제 공개 기록으로 판단합니다.

PCssak Gongyu는 사용자가 지시한 Windows SMB 공유, LAN 점검, 네트워크 드라이브
관리와 별도 동의를 받은 SSH 설정을 돕습니다. 무료 Early Access는 이번 버전의
성숙도를 표시하며 이후 모든 버전의 무료 제공 약속은 아닙니다.

## 0.4.0에서 바뀐 점

일반 SSH 화면을 켜기·끄기·우리 SSH 설정 원복으로 정리했습니다. 과거 기록의 조회·
복구 버튼, 설정에서 해당 화면으로 가는 경로와 일반 조작 전 구형 V4·V5 복구를 자동
실행하던 화면 경로를 제거합니다. 관련 명령 다섯 개의 WebView 권한도 퇴역합니다.
현재 LAN 규칙의 소유권·서비스 상태·우리 설정 원복의 보호 기록은 보존하며 기록을
지우거나 과거 복구를 완료했다고 표시하지 않습니다.

설정 상단에는 언어·Windows 자동 실행·테마·업데이트·앱 잠금을 배치하고 데이터 관리·
문제 해결·고급 설정을 펼쳐 볼 수 있게 했습니다. 중단된 작업 안내는 접힌 영역 밖에
유지합니다. 다른 PC나 Windows 계정에서는 백업의 비밀번호를 다시 입력해야 할 수
있다는 제한과 복원·덮어쓰기·삭제 확인은 유지합니다. 화면 안내는 10개 언어를 지원합니다.

0.3.9의 보호된 부분 원복 한계는 유지합니다. 과거 타사 규칙 복구가 독립적이며 보호
원문과 대상 비중첩을 확인할 때만 앱 소유 설정을 정리합니다. 외부 복구와 보호 차단은
보존하고 원래 서비스 상태·OpenSSH 기능 제거·Public 프로필 원복·차단 해제는 보류될
수 있습니다. 손상되거나 겹치거나 읽을 수 없는 상태를 성공으로 바꾸지 않습니다.
현재 LAN 보호막도 검증된 정책·인증·인터페이스 범위의 판정이며 조직 정책 전체를 보장하지
않습니다. 다른 프로그램과 Windows 기본 허용 규칙을 임의로 바꾸지 않습니다. 서비스
중지는 이미 인증된 모든 SSH 세션의 종료를 보장하지 않습니다.

0.4.0 설치·업그레이드·제거·재부팅·두 PC SSH/SFTP·완전 원복 연속 실기는 NOT_RUN입니다.
기존 버전 한 PC의 켜기·끄기 경험을 이번 설치본의 성공으로 간주하지 않습니다. 전체
Windows Home·Pro 행렬·외부 법률 검토·독립 공급망 검토·Authenticode 게시자 서명도
미완료입니다. 개발 시험, 최종 소스 검증, 두 업데이트 서명, 아홉 자산과 공개 판독은
각각 별도 배포 관문입니다. 상세는 [릴리스 노트](docs/RELEASE-NOTES-v0.4.0.md)를 따릅니다.

## 공식 다운로드와 자동 업데이트

공개 후에는 [GitHub v0.4.0 공식 릴리스](https://github.com/pcssakinc/pcssak-gongyu-releases/releases/tag/v0.4.0)
또는 [pcssak.com](https://pcssak.com/)의 버전 고정 다운로드 페이지만 사용합니다. 제목에는
Free Early Access를 유지하며 GitHub 상태는 `draft=false`, `prerelease=false`, Latest로 게시합니다.
앱의 고정 업데이트 확인 주소는 다음과 같습니다.

`https://github.com/pcssakinc/pcssak-gongyu-releases/releases/latest/download/latest.json`

법률 정본과 **0.3.9의 업데이트 공개키**를 유지합니다. 정상 법률 동의 기록이 남은
**0.3.9 사용자는 실제 0.4.0 공개 후 앱에서 다운로드·서명 검증·사용자 승인으로 업데이트**할
수 있습니다. **0.3.8 이하는 현행 공개키가 없으므로 공식 설치본을 한 번 직접 내려받아
SHA-256을 공개 목록과 대조한 뒤 대화형으로 설치**해야 합니다. 서명 오류를 우회하지 마세요.

0.1.1~0.3.9는 먼저 앱을 제거하거나 설정·공유 장부·SSH 설정·중단 기록을 지우지 않고
보호 덮어 설치합니다. 구 제거기는 실행하지 않습니다. 이미 제거했어도 남은 Windows
복구 기록을 임의로 지우지 마세요. 0.1.0만 구 버전을 제거한 뒤 공식 설치본을 직접 설치합니다.
동의나 기록을 확인할 수 없으면 대화형 설치로 안내합니다. 실제 최종 설치본의 보호
교체·제거 시험은 NOT_RUN입니다. 중단 복구 도중 구버전으로 강제 복귀하지 마세요.

OpenSSH 설치 뒤 재부팅 대기는 접속 성공이나 전체 완료가 아닙니다. 재부팅 후 SSH
켜기를 다시 실행해 나머지 설정을 마무리합니다. 업데이트 자체가 SSH를 켜거나 과거
방화벽 복구를 완료하지 않습니다. 공개 설치본 대상은 Windows x64 하나입니다.

- `PCssak-Gongyu-0.4.0-Windows-x64-Setup.exe`

Windows x86은 별도 Windows 10 x86 Home·Pro 실기 증거 게이트 전에는 공개하지 않습니다.
0.1.2 이상 0.4.9 이하 버전은 무료 Early Access입니다. 최종 소스 검증·Tauri/Minisign
서명·SHA-256·정확한 9자산 검증은 생략하지 않습니다. 승인된 로컬 Windows 대체 경로도
실제 명령·도구·로그 해시와 결과를 기록하며 실패한 Actions를 성공으로 표시하지 않습니다.
복구 가능한 시험 PC와 최신 백업에서 먼저 확인하고 보안 제품을 유지하세요.

## 실행 전 무결성 확인

같은 릴리스의 `SHA256SUMS.txt`와 설치본 SHA-256을 비교하세요.

```powershell
Get-FileHash -Algorithm SHA256 '.\PCssak-Gongyu-0.4.0-Windows-x64-Setup.exe'
```

릴리스에는 설치본 `PCssak-Gongyu-0.4.0-Windows-x64-Setup.exe.sig`도 포함됩니다. 앱은
내장한 Gongyu 전용 Minisign 공개키로 업데이트 설치본을 검증합니다. 별도의
`UPDATE-RELEASE.json.sig`는 제품·버전·소스 커밋·설치본 해시·바이트 크기·내장 EULA·PRIVACY
정본 해시·정규 URL·승인 릴리스 노트를 한 묶음으로 검증합니다.

위 서명은 Windows 게시자 신원을 보증하는 Authenticode와 다릅니다. 0.1.2 이상 0.4.9 이하의
공개 Early Access 설치본과 내부 실행 파일에는 Authenticode 게시자 서명이 없습니다.
따라서 Microsoft Defender SmartScreen이나 다른 보안 제품이 경고하거나 실행을 차단할 수
있습니다. 설치를 위해 SmartScreen, Microsoft Defender, 방화벽 또는 다른 보안 제품을 끄지
마세요. 해시나 서명이 다르면 중단하세요.

Windows 11의 Smart App Control(SAC) 차단은 앱의 PIN 잠금·설치 동작과 별개입니다. 앱은 SAC나
다른 보안 기능을 자동 해제하지 않습니다. Microsoft의 [SAC 공식 FAQ](https://support.microsoft.com/en-us/Windows/Security/threat-malware-protection/smart-app-control-frequently-asked-questions)는
최근 업데이트의 재활성화 개선을 설명하지만 모든 Windows 빌드·기기 상태에서 해제 후 바로
다시 켤 수 있다고 보장하지 않습니다. 개별 앱만 허용하는 SAC 예외도 없습니다. 설치·실행
차단은 보안을 유지한 채 시험을 보류합니다. 무서명 제거기만 SAC에 차단되고 사용자가 직접
해제를 선택하는 경우에는 재활성화 지원이 사전에 확인된 기기에 한해 일시 중지·제거·즉시
재활성화하는 [조건부 제거 안내](SECURITY.md)를 따릅니다. 조건이 불명확하면 중지하지 않습니다.

## 릴리스 자산 9종

각 릴리스에는 [`docs/RELEASE-ASSET-CONTRACT.md`](docs/RELEASE-ASSET-CONTRACT.md)에 고정한
다음 종류만 정확히 포함합니다.

- x64 설치본과 Tauri/Minisign `.sig`
- Tauri 전용 `latest.json`
- 서명된 `UPDATE-RELEASE.json`과 `.sig`
- 사람·홈페이지용 `DOWNLOAD-METADATA.json`
- `SHA256SUMS.txt`, `THIRD-PARTY-NOTICES.txt`, 정확한 버전의 MPL 원본 ZIP

`latest.json`은 [`latest.schema.json`](latest.schema.json)을 따르는 Tauri 정적 업데이트
매니페스트입니다. 사람용 다운로드 정보는
[`download-metadata.schema.json`](download-metadata.schema.json)을 따르는
`DOWNLOAD-METADATA.json`으로 분리했습니다.
서명된 배포 계약은 [`update-release.schema.json`](update-release.schema.json)으로 고정합니다.

## 보안과 지원

보안 취약점은 먼저 [`SECURITY.md`](SECURITY.md)를 확인하세요. 일반 문의는
`support@pcssak.com`으로 받습니다. 공개 이슈에 암호, 개인키, 복구 코드, 접근 토큰,
개인 문서 또는 가리지 않은 네트워크 설정을 첨부하지 마세요.

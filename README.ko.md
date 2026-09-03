# PCssak Gongyu 릴리스

[English](README.md)

> 이 디렉터리는 PCssak Gongyu `v0.1.6` 무료 Early Access의 공개 저장소 계약입니다.
> 버전 고정 GitHub 릴리스와 검증된 자산 9종을 실제 게시 기록으로 봅니다.

PCssak Gongyu는 사용자가 지시한 Windows SMB 공유 폴더 설정, LAN 점검, 네트워크 드라이브
관리와 별도로 동의한 SSH 설정을 돕습니다. `0.1.6`는 **무료 Early Access**이며, 이는 제품
성숙도를 정직하게 표시하는 이름이지 이후 버전도 계속 무료라는 약속은 아닙니다.

## 공식 다운로드와 자동 업데이트

공개 후에는 [GitHub v0.1.6 공식 릴리스](https://github.com/pcssakinc/pcssak-gongyu-releases/releases/tag/v0.1.6)
또는 [pcssak.com](https://pcssak.com/)의 버전 고정 다운로드 페이지만 사용합니다. 제목에는
Free Early Access를 명확히 유지하되 앱의 자동 업데이트가 동작하도록 GitHub 상태는
`draft=false`, `prerelease=false`, Latest로 게시합니다.

앱이 확인하는 주소는 다음 하나입니다.

`https://github.com/pcssakinc/pcssak-gongyu-releases/releases/latest/download/latest.json`

공개 `0.1.0`에는 앱 내 자동 업데이트가 없습니다. 해당 사용자는 위 공식 `0.1.6` 설치본을
한 번 수동으로 내려받아 직접 설치해야 합니다. `0.1.1` 사용자는 법률 정본 변경 때문에
공식 대화형 설치기에서 새 동의가 필요할 수 있습니다. `0.1.3`·`0.1.4`·시험 설치 `0.1.5` 사용자는 정상 법률
동의 기록이 남아 있으면 앱에서 새 버전을 확인하고 다운로드·서명 검증·사용자 승인 후
업데이트하는 경로를 사용합니다. 법률 정본과 업데이트 공개키는 바꾸지 않습니다.

`0.1.6`은 기존 Microsoft OpenSSH 재사용과 원복 정보 결속을 수정하기 위한 **공개 전 준비 중**
버전입니다. 회사 PC의 `0.1.3`→`0.1.5` 설치 실측은 성공했지만 이후 기존 OpenSSH의
경로·신원 호환성 문제가 확인돼 `0.1.5`는 공개하지 않았습니다. Latest는 `0.1.3`을 유지하며
기존 불변 자산은 교체하지 않습니다. `0.1.6`의 SSH 구현·회귀시험·실측·배포는 진행 중이고
전체 Windows·두 PC SSH 실기는 미완료입니다. [준비 안내](docs/RELEASE-NOTES-v0.1.6.md)를
확인하세요. 이 문서 자체가 새 버전의 게시 증거는 아닙니다.

공개할 설치본 대상은 Windows x64 하나입니다.

- `PCssak-Gongyu-0.1.6-Windows-x64-Setup.exe`

Windows x86은 별도의 Windows 10 x86 Home·Pro 실기 증거 게이트를 통과하기 전에는
공개하지 않습니다.

0.1.2 이상 0.2.0 미만의 0.1.x는 기능을 먼저 실측하기 위한 무료 Early Access입니다.
법률 전문가 최종 외부 검토, Windows 10/11 Home·Pro x64 전체 VM·물리 LAN SSH/SFTP 실기
행렬, 독립 공급망 검토와 Windows 신뢰 Authenticode 서명은 아직 완료되지 않았으며 0.2.0
공개 전 필수 게이트로 복원합니다. GitHub Actions 최종 소스 검증, Tauri 업데이트 서명,
독립 Minisign 서명, SHA-256과 정확한 9개 자산 검증은 0.1.x에서도 생략하지 않습니다.
Early Access는 모든 Windows·보안 제품 조합의 무결함을 보증하지 않으므로 중요한 PC보다
복구 가능한 시험 환경과 백업에서 먼저 사용하세요.

## 실행 전 무결성 확인

같은 릴리스의 `SHA256SUMS.txt`와 설치본 SHA-256을 비교하세요.

```powershell
Get-FileHash -Algorithm SHA256 '.\PCssak-Gongyu-0.1.6-Windows-x64-Setup.exe'
```

릴리스에는 설치본 `PCssak-Gongyu-0.1.6-Windows-x64-Setup.exe.sig`도 포함됩니다. 앱은
내장한 Gongyu 전용 Minisign 공개키로 업데이트 설치본을 검증합니다. 별도의
`UPDATE-RELEASE.json.sig`는 제품·버전·소스 커밋·설치본 해시·바이트 크기·내장 EULA·PRIVACY
정본 해시·정규 URL·승인 릴리스 노트를 한 묶음으로 검증합니다.

위 서명은 Windows 게시자 신원을 보증하는 Authenticode와 다릅니다. 0.1.2 이상 0.2.0 미만의
공개 0.1.x Early Access 설치본과 내부 실행 파일에는 Authenticode 게시자 서명이 없습니다.
따라서 Microsoft Defender SmartScreen이나 다른 보안 제품이 경고하거나 실행을 차단할 수
있습니다. 설치를 위해 SmartScreen, Microsoft Defender, 방화벽 또는 다른 보안 제품을 끄지
마세요. 해시나 서명이 다르면 중단하세요.

Windows 11의 Smart App Control(SAC) 차단은 이번 설치 폴더 오류와 별개입니다. 앱은 SAC나
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

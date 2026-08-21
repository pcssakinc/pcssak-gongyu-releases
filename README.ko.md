# PCssak Gongyu 릴리스

[English](README.md)

> 이 디렉터리는 앞으로 만들 `pcssakinc/pcssak-gongyu-releases` 공개 저장소의 로컬
> 배포 템플릿입니다. 현재 공개 릴리스가 존재한다는 뜻이 아닙니다.
> [`docs/RELEASE-ASSET-CONTRACT.md`](docs/RELEASE-ASSET-CONTRACT.md)의 모든 게이트가
> 통과하기 전에는 게시하지 않습니다.

PCssak Gongyu는 사용자가 지시한 Windows SMB 공유 폴더 설정, LAN 점검, 네트워크
드라이브 관리와 별도로 동의한 SSH 설정을 돕는 도구입니다. 첫 공개 버전은 **무료 Early
Access**로 계획하며, 안정 유료 버전 전에는 기능과 지원 환경이 바뀔 수 있습니다.

## 공식 다운로드 계약

공개 후에는 [GitHub v0.1.0 공식 얼리액세스 릴리스](https://github.com/pcssakinc/pcssak-gongyu-releases/releases/tag/v0.1.0)
또는 [pcssak.com](https://pcssak.com/)의 한국어·영어 다운로드 페이지만 사용합니다.
첫 릴리스는 아래 Windows x64 설치 파일 하나만 공개합니다.

- `PCssak-Gongyu-Beta-Windows-x64-Setup.exe`

Windows x86은 별도의 Windows 10 x86 Home·Pro 실기 증거 게이트를 통과하기 전에는
공개하지 않습니다. 파일 이름만으로는 진본임을 증명할 수 없습니다. 실행 전에 같은 버전
릴리스의 `SHA256SUMS.txt`와 설치 파일 SHA-256을 비교하세요.

```powershell
Get-FileHash -Algorithm SHA256 '.\PCssak-Gongyu-Beta-Windows-x64-Setup.exe'
```

출력값이 같은 파일명 옆의 값과 한 글자도 빠짐없이 일치해야 합니다. 출처·파일명·크기·해시
중 하나라도 다르면 실행하지 마세요.

## 미서명 Early Access 한계

첫 Early Access 설치 파일에는 **Authenticode 코드 서명이 없으며**, Tauri 업데이트용
분리 `.sig` 파일도 없습니다. 따라서 Windows에 **알 수 없는 게시자** 또는 Microsoft
Defender SmartScreen 평판 경고가 나타날 수 있습니다. 이는 정직하게 공개하는 배포 한계이며
Windows 보안을 약화하라는 뜻이 아닙니다.

설치를 위해 SmartScreen, Microsoft Defender, 방화벽 또는 다른 보안 제품을 **끄지
마세요**. Windows가 차단하거나 해시가 다르면 중단하고 `support@pcssak.com`으로
알려 주세요.

## 릴리스 파일

각 공개 릴리스에는 [`docs/RELEASE-ASSET-CONTRACT.md`](docs/RELEASE-ASSET-CONTRACT.md)에
정한 고정 자산만 정확히 포함합니다.

- x64 설치 파일
- `SHA256SUMS.txt`
- 배포 메타데이터 `latest.json`
- `THIRD-PARTY-NOTICES.txt`
- 정확한 버전의 MPL-2.0 구성요소 원본 소스 묶음

`latest.json`은 [`latest.schema.json`](latest.schema.json)으로 검증하는 PCSSAK 다운로드
메타데이터입니다. **Tauri 업데이트 매니페스트가 아니며**, 서명된 자동 업데이트 채널처럼
표현하면 안 됩니다.

## 보안과 지원

보안 취약점은 먼저 [`SECURITY.md`](SECURITY.md)를 확인하세요. 일반 문의는
`support@pcssak.com`으로 받습니다. 공개 이슈에 암호, 개인키, 복구 코드, 접근 토큰,
개인 문서 또는 가리지 않은 네트워크 설정을 첨부하지 마세요.

# PCssak Gongyu 공개 릴리스 자산 계약

이 문서는 `pcssakinc/pcssak-gongyu-releases`에 게시하는 자산 이름과 공개 조건을 고정한다.
0.1.0은 실기 미완료와 무서명 위험을 숨기지 않는 무료 Early Access로 공개 승인을 받았다.
자산 무결성·법률 정본·오픈소스 의무는 완화하지 않으며, 실기 미완료 항목은 공개 고지와 후속
버전 개선 대상으로 관리한다.

## 1. GitHub 릴리스 상태

무료 Early Access의 의미를 GitHub의 기계 판독 상태와 릴리스 제목·본문,
`latest.json`의 `channel`에 모두 동일하게 표시한다. GitHub 릴리스는 다음 상태로
게시해야 한다.

- 태그: 제품 메타데이터와 같은 `v0.1.0` 형식
- `draft=false`
- `prerelease=true`
- 제목: `PCssak Gongyu 0.1.0 — Free Early Access` 형식

GitHub의 `/releases/latest`는 prerelease를 제외하므로 Gongyu 다운로드에는 사용하지 않는다.
홈페이지, README와 `latest.json`은 모두 검증한 정확한 버전 태그 URL을 사용한다.

## 2. 고정 자산 집합

버전 `0.1.0`의 첫 공개 릴리스에는 아래 다섯 파일만 정확히 올린다.

1. `PCssak-Gongyu-0.1.0-MPL-Sources.zip`
2. `PCssak-Gongyu-Beta-Windows-x64-Setup.exe`
3. `THIRD-PARTY-NOTICES.txt`
4. `latest.json`
5. `SHA256SUMS.txt`

제품 버전이 바뀌면 첫 번째 파일명과 태그·`latest.json`의 버전만 같은 값으로 바꾼다.
설치 파일명은 홈페이지의 고정 다운로드 계약 때문에 바꾸지 않는다. Windows x86 설치
파일은 Windows 10 x86 Home·Pro 실기 증거 게이트가 별도로 통과하기 전까지 추가하지 않는다.

Authenticode 서명과 Tauri 업데이트용 분리 서명을 이번 Early Access에는 만들지 않는다.
따라서 `.sig`, `.msi`, 인증서 또는 개인키 파일은 릴리스 자산에 포함하면 안 된다.

## 3. `latest.json` 계약

`latest.json`은 `latest.schema.json`을 만족하는 PCSSAK 다운로드 메타데이터다. Tauri
업데이트 매니페스트가 아니며 앱이 이를 서명된 자동 업데이트 정보로 처리해서는 안 된다.

- `manifestKind`: `pcssak-download-metadata`
- `channel`: `early-access`
- `release.draft`: `false`
- `release.prerelease`: `true`
- 설치 파일 `authenticode`: `not-signed`
- 설치 파일 `detachedSignature`: `null`
- 모든 자산 URL: `releases/download/v<정확한 버전>/...` 버전 고정 URL
- 홈페이지·README에서 매니페스트 자체를 찾는 URL도
  `releases/download/v<정확한 버전>/latest.json` 사용

JSON Schema만으로 `version`과 파일명·URL 속 버전이 서로 같은지 완전히 표현할 수 없으므로
`scripts/verify-public-release-template.ps1`과 릴리스 자동화에서 교차 검증해야 한다.

## 4. SHA-256 계약

최종 이름으로 복사한 파일에서 SHA-256을 다시 계산한다. `SHA256SUMS.txt`는 소문자 64자리
해시, ASCII 공백 두 개, 정확한 파일명과 LF 줄바꿈을 사용하고 다음 네 파일만 정렬해 담는다.

1. `PCssak-Gongyu-0.1.0-MPL-Sources.zip`
2. `PCssak-Gongyu-Beta-Windows-x64-Setup.exe`
3. `THIRD-PARTY-NOTICES.txt`
4. `latest.json`

`SHA256SUMS.txt`가 자기 자신을 해시하게 만들면 순환 의존이 생기므로 자체 해시는 넣지 않는다.
`latest.json`도 같은 이유로 `SHA256SUMS.txt`의 해시를 담지 않고 버전 고정 URL만 담는다.

생성 순서는 다음과 같이 고정한다.

1. 설치 파일, MPL ZIP, 고지문을 최종 파일명으로 복사하고 각각의 SHA-256을 계산한다.
2. 그 세 해시와 버전 고정 URL로 `latest.json`을 만들고 스키마·교차 버전을 검증한다.
3. 최종 `latest.json` SHA-256을 계산한다.
4. 위 네 파일의 해시를 정해진 순서로 `SHA256SUMS.txt`에 기록한다.
5. 업로드 직전 다섯 파일을 다시 읽어 이름·크기·해시를 확인한다.

## 5. MPL-2.0 원본 계약

`scripts/create-mpl-source-archive.ps1`이 현재 `Cargo.lock`, x64/i686 잠금 그래프와
`THIRD-PARTY-NOTICES.txt`를 교차 검증하고 로컬 Cargo 레지스트리 캐시의 정확한 `.crate`
원본으로 ZIP을 만든다. 네트워크에서 임의로 찾은 브랜치·태그·소스 저장소 ZIP으로
대체하면 안 된다. ZIP에는 해시 기준인 `Cargo.lock`과 전체 라이선스 본문이 있는
`THIRD-PARTY-NOTICES.txt`도 함께 넣는다. 현재 잠금 그래프의 MPL-2.0 구성요소는 다음
다섯 개다.

- `cssparser 0.36.0`
- `cssparser-macros 0.6.1`
- `dtoa-short 0.3.5`
- `option-ext 0.2.0`
- `selectors 0.36.1`

버전이 달라지면 이 목록을 손으로 추정하지 말고 생성기와 고지 생성 결과를 다시 검증한다.

## 6. 공개 필수 조건과 승인된 Early Access 위험

### 6.1 완화할 수 없는 게시 조건

다음 중 하나라도 남으면 사용자 승인 여부와 관계없이 저장소 공개 전환·자산 업로드·릴리스
게시를 중단한다.

- EULA·개인정보 문서의 미확정 표시, 개인 실명·물리 주소·사업자·법인 지위를 추정하는 표현,
  또는 `PCSSAK` 제공자·운영자, `PCSSAK 개인정보 보호 담당 부서`, `support@pcssak.com`,
  `privacy@pcssak.com` 계약 불일치
- `EULA.md`와 설치기용 `EULA.txt`, 프로그램에 포함한 법률 문서와 공개 저장소 원본 불일치
- 공개 README·지원·품질·알려진 한계·보안·제3자 원본·Issue 양식의 링크 또는 SSH 범위 불일치
- 공개 설치 파일이 x64 후보가 아니거나 제품 버전·파일명·EULA·고지의 대상이 서로 다름
- 설치 파일, `latest.json`, `SHA256SUMS.txt` 또는 MPL 원본 ZIP 해시 불일치
- GitHub 자산 이름과 홈페이지의 버전 고정 다운로드 이름 불일치
- 정확히 다섯 자산 중 하나라도 누락되거나 MPL 원본 묶음·제3자 고지를 설치 파일과 동시에
  제공하지 않음
- 보안 제품 비활성화를 요구하는 설치 안내

### 6.2 0.1.0에서 공개 승인한 미완료 항목

PCSSAK은 다음 항목을 검증 완료로 오인시키지 않고 릴리스 노트·README·알려진 한계·홈페이지에
명시하는 조건으로 0.1.0 무료 Early Access 공개를 승인했다.

- 지원 후보 Windows Home·Pro 전체의 신규 설치·업데이트·제거·재부팅 실기 미완료
- 같은 LAN 두 PC의 SMB·매핑·페어링·SSH 로그인·명령·SFTP·SSH 끄기 실기 미완료
- Authenticode 코드 서명과 Tauri 자동 업데이트 서명 부재
- GitHub 호스팅 Actions 미실행. 로컬 자동검사 결과만 존재하며 이를 CI 통과로 표시하지 않음
- 도메인 메일의 발신·답장·외부 공급자 헤더와 DMARC 운영 검증 미완료

공개 문서는 위 항목을 호환성 또는 안전성 통과로 표현하면 안 된다. 사용자는 민감하지 않은 시험
환경과 별도 백업을 먼저 사용하도록 안내한다. 0.1.0에서 발견한 결함은 같은 태그의 자산을 바꾸지
않고 새 `0.1.1` 이상 태그와 새 다섯 자산으로 수정한다. 심각한 보안 결함이 확인되면 다운로드를
즉시 중단하고 새 후보가 준비될 때까지 해당 버전을 제공하지 않는다.

## 7. 공개 저장소 루트 법률 문서 정본

GitHub Release에 올리는 위 다섯 자산과 공개 릴리스 저장소 루트의 법률 문서는 서로 다른
집합이다. 다음 두 문서는 Release 자산 수에 추가하지 않지만 공개 저장소 루트에 반드시 둔다.

- 소스 저장소 루트 `LICENSE.txt`가 EULA의 유일한 정본이며, 공개 릴리스 저장소 루트
  `EULA.txt`는 그 파일의 바이트 동일 복사본이어야 한다.
- 소스 저장소 루트 `PRIVACY.md`가 개인정보 처리방침의 유일한 정본이며, 공개 릴리스 저장소
  루트 `PRIVACY.md`는 그 파일의 바이트 동일 복사본이어야 한다.

복사 과정에서 줄바꿈, BOM, 공백, 제목 또는 번역을 다시 만들지 않는다. 소스 정본이 바뀌면
공개 저장소의 두 복사본도 같은 변경에서 다시 복사하고 아래 읽기 전용 검증을 통과해야 한다.

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File `
  .\scripts\verify-release-repo-legal-copies.ps1 `
  -ReleaseRepositoryRoot <공개-릴리스-저장소-루트>
```

두 파일 중 하나라도 없거나 한 바이트라도 다르면 공개 저장소 PR 병합과 Release 게시를
차단한다. 이 계약은 GitHub Release의 정확한 다섯 자산 계약을 여섯·일곱 자산으로 늘리지 않는다.

`EULA.md`는 `EULA.txt`로 안내하는 고정 포인터만 허용한다. 별도의 약관 본문, 요약, 번역 또는
수정본을 `EULA.md`에 두면 EULA가 둘로 갈라지므로 게시를 차단한다.

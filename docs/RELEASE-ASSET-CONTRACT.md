# PCssak Gongyu 공개 릴리스·자동 업데이트 자산 계약

이 문서는 `pcssakinc/pcssak-gongyu-releases`의 무료 `v0.1.4` Early Access에 쓰는
공개 자산, Tauri 자동 업데이트, 서명과 GitHub Release 상태를 하나의 계약으로 고정한다.
현재 디렉터리는 공개 저장소용 소스 템플릿이며, 실제 게시 완료 여부는 GitHub의 버전 고정
릴리스와 Latest 엔드포인트를 각각 재검증해 판단한다.

## 1. GitHub 릴리스 상태

`v0.1.4`는 제품 성숙도를 숨기지 않도록 제목과 본문에서 **Free Early Access**라고
표시한다. 다만 Tauri가 고정 주소에서 최신 버전을 찾게 하려면 GitHub가 프리릴리스를
`/releases/latest`에서 제외하는 동작을 피해야 한다. 따라서 게시 상태는 다음과 같다.

- 태그: `v0.1.4`
- 제목: `PCssak Gongyu 0.1.4 — Free Early Access`
- `draft=false`
- `prerelease=false`
- GitHub Latest 지정: `true`

Early Access라는 제품 채널과 GitHub의 `prerelease` 플래그는 같은 개념이 아니다. 홈페이지와
사람용 다운로드는 버전 고정 URL을 사용하고, 앱의 업데이트 확인만 다음 고정 Latest 주소를
사용한다.

`https://github.com/pcssakinc/pcssak-gongyu-releases/releases/latest/download/latest.json`

공개 `0.1.0`에는 앱 내 updater가 없으므로 해당 사용자는 공식 `0.1.4` 설치본을 한 번 수동으로
내려받아 직접 설치해야 한다. `0.1.1` 사용자는 법률 정본 변경 때문에 대화형 설치기에서 새 동의가
필요할 수 있다. `0.1.3` 사용자는 정상 법률 동의 기록이 남아 있으면 앱 안에서 서명된 업데이트를
사용할 수 있다. 법률 정본과 업데이트 공개키는 그대로 유지한다. 홈페이지와 릴리스 노트도
이 전환 조건을 같은 문구로 고지한다.

같은 태그의 게시 자산은 사후 교체하지 않는다. 코드·법률·설치본 중 하나라도 바뀌면 더 높은
새 버전으로 다시 빌드·서명·게시한다.

## 2. 정확한 공개 자산 9종

`v0.1.4` Release에는 아래 아홉 파일만 정확히 올린다.

1. `DOWNLOAD-METADATA.json`
2. `PCssak-Gongyu-0.1.4-MPL-Sources.zip`
3. `PCssak-Gongyu-0.1.4-Windows-x64-Setup.exe`
4. `PCssak-Gongyu-0.1.4-Windows-x64-Setup.exe.sig`
5. `THIRD-PARTY-NOTICES.txt`
6. `UPDATE-RELEASE.json`
7. `UPDATE-RELEASE.json.sig`
8. `latest.json`
9. `SHA256SUMS.txt`

Windows x86 설치 파일은 Windows 10 x86 Home·Pro 실기 증거 게이트가 별도로 통과하기 전에는
추가하지 않는다. `.msi`, 인증서, 공개키 백업, 개인키, 암호, 빌드 임시 파일도 Release 자산에
포함하지 않는다.

## 3. 두 서명과 신뢰 경계

Tauri가 만든 `.sig`는 Minisign 서명 파일 전체를 Base64로 표현한 텍스트다. 설치본과
`UPDATE-RELEASE.json`은 서로 다른 목적의 같은 Gongyu 전용 업데이트 키로 각각 서명한다.
조립·게시 검증은 Minisign 0.12의 `-H`를 항상 사용해 현대 prehashed 서명만 허용하고 레거시
서명은 같은 공개키로 유효하더라도 거부한다.

- 설치본 `.sig`: Tauri Updater가 내려받은 설치본 바이트를 검증한다.
- `UPDATE-RELEASE.json.sig`: 제품·버전·소스 커밋·설치본 해시·설치본 바이트 크기·내장 EULA·
  PRIVACY 정본 해시·정규 URL·승인 릴리스 노트가 한 묶음이라는 사실을 검증하여 오래된
  메타데이터 재사용, 법률 정본 자기불일치, 과대 다운로드, 다른 URL로의 유도를 차단한다.

조립기는 `src-tauri/tauri.conf.json`에 실제로 내장되는 Gongyu 공개키를 읽고, 공개키가
Minisign `.pub` 본문을 정확히 한 번 Base64한 형식인지 확인한다. 이어서 신뢰한 실제
`minisign.exe` CLI로 설치본과 `UPDATE-RELEASE.json`의 서명을 모두 암호학적으로 검증한다.
문자열 모양만 확인하거나 다른 제품 공개키, 이중 Base64 공개키, 과거 키의 서명을 허용하지
않는다.

Minisign 0.12 x64와 7-Zip 26.02 x64의 `7z.exe`·`7z.dll` SHA-256은 검토한 공식 배포물 값으로
조립기 코드에 고정한다. 호출자가 경로와 임의 해시를 함께 제출해도 고정값과 다르면 실행 전에
거부한다. 공식 Windows `7za.exe`는 NSIS를 지원하지 않고 `7z.exe`는 인접
`Codecs`·`Formats`를 자동 로드하므로, 기본 정식 승인 경로에서는 사용자 쓰기 가능한 호출자
폴더나 TEMP 격리 복사본을 실행하지 않는다. 정확한 `C:\Program Files\7-Zip\7z.exe`
machine-wide 설치만 허용하고 Program Files·7-Zip 디렉터리를 `OPEN_REPARSE_POINT` 핸들로 연다. 같은 핸들의 최종
경로·VolumeSerial/FileId·소유자·DACL을 확인하며, 현재 비관리자 토큰의 사용자 SID와 활성 그룹
SID 어느 것에도 파일·하위 디렉터리 추가·삭제·DACL/소유자 변경 Allow 권한이 없어야 한다.
`Codecs`·`Formats` 부재와 공식 26.02 루트 항목 집합을 실행 전후에 재검증한다. `7z.exe`와
`7z.dll`은 쓰기·교체·삭제를 허용하지 않는 읽기 공유 핸들로 실행 종료까지 잠그며, 같은 핸들의
해시·최종 경로·파일 ID를 재검증한다. 내부 앱은 x64 `0x8664`여야 한다. Tauri가 NSIS 조립 전에
공식적으로 적용하는 단일 `UNK→NSS` 3바이트 패치 외에는 같은 실행의 Tauri x64 빌드 앱과 전체
바이트가 같아야 한다.

Minisign 검증은 호출자가 제공한 공개키 경로나 임시 서명 경로를 그대로 신뢰하지 않는다. 매
검증마다 재분석 지점이 아닌 새 GUID 데이터 디렉터리에 코드 고정 공개키와 승인 `.sig`에서
해제한 서명, 잠근 원본 대상의 바이트 복사본만 기록하고 `target.bin`·`updater.pub`·
`target.minisig` 정확히 세 일반 파일인지 확인한다. 공개키·디코딩 서명·격리 검증 대상·원본
대상·원본 `.sig`는 읽기 공유 핸들로, 각 부모 데이터/입력 디렉터리는
rename/delete 차단 핸들로 실행 완료까지 고정한다. 잠근 바이트가 승인 해시와 같은지 Minisign
실행 직전과 직후에 다시 확인해 같은 사용자 프로세스의 공개키·서명·대상 교체를 실패 폐쇄한다.
디렉터리 핸들은 `OPEN_REPARSE_POINT`로 열고 같은 핸들의 `FileAttributeTagInfo`에서 실제
디렉터리이며 재분석 지점이 아님을 확인한다. GUID 최상위에서 중간·leaf 순서로 자식 생성 전에
잠금을 취득해 junction 자체를 다른 대상으로 재지정하는 경합도 차단한다. 7-Zip에는 잠근 원본
NSIS에서 만든 GUID 입력 스냅샷만 전달하고, `UseShellExecute=false`·보호된 작업 디렉터리·최소
환경으로 고정한 승인 실행 파일을 직접 시작한다.

제품 개인키는 조립기·템플릿·공개 저장소가 생성하거나 읽지 않는다. 키 생성과 서명은 분리된
승인 절차에서 끝나야 하며 조립기는 공개키 검증만 수행한다.

이 Tauri/Minisign 서명은 Windows 게시자 신원을 확인하는 Authenticode와 목적이 다르다.
`-PublicEarlyAccess`로 공개하는 0.1.2 이상 0.2.0 미만의 정확한 3요소 0.1.x 버전은 설치기와
실제 NSIS에서 추출한 `pcssak-gongyu.exe`가 **둘 다 정확히** `Authenticode: not-signed`인
경우에만 조립·게시할 수 있다. 한쪽만 서명됐거나 `UnknownError` 등 다른 상태면 혼합 후보로
간주해 원격 호출 전에 차단한다. 릴리스 노트에는 게시자 서명 부재와 Windows·보안 제품이
경고하거나 실행을 차단할 수 있음을 명시한다. 이 유예는 0.2.0에서 자동 만료한다.

`-PublicEarlyAccess`가 없는 엄격 경로와 0.2.0 이상에서는 설치본과 내부 앱이 Windows 신뢰
정책에서 `Valid`이고 Code Signing EKU가 있으며, Windows가 확인하는 타임스탬프 인증서와
Time Stamping EKU를 모두 가져야 한다. 두 파일의 signer leaf thumbprint·subject·issuer가
정확히 같고, 저장소 밖 후보별 `candidate-leaf` 승인 JSON과 별도 승인 SHA-256에도 일치해야
한다. 승인 증거가 없거나 값이 다르면 GitHub 원격 호출 전에 차단한다. Microsoft Artifact
Signing처럼 후보마다 단기 leaf가 바뀌는 서비스의 thumbprint를 장기 제품 신원으로 오인하지
않는다. durable identity 지원은 별도 스키마와 검증기가 생기기 전에는 허용하지 않는다.

로컬 `Get-AuthenticodeSignature`가 직접 확인하는 범위는 위 Windows 신뢰 상태와 인증서/EKU
존재까지이며 타임스탬프 프로토콜이 RFC 3161인지 판별하지 않는다. RFC 3161 사용 자체가 서명
절차의 요구사항이면 SignTool `/tr` 또는 서명 서비스가 만든 외부 로그/provenance를 별도로
검토·보존한다. 새로 서명한 파일도 Microsoft Defender SmartScreen 평판 경고가 처음에는 표시될
수 있으며, 경고가 없다고 보장하지 않는다. 설치를 위해 SmartScreen, Microsoft Defender,
방화벽 또는 다른 보안 제품을 끄라고 안내하지 않는다.

## 4. `latest.json`: Tauri 전용 정적 업데이트 매니페스트

`latest.json`은 더 이상 사람·홈페이지용 다운로드 정보가 아니다. Tauri 공식 정적 JSON
형식만 정확히 담으며 `latest.schema.json`으로 구조를 고정한다.

- `version`: `0.1.4`
- `notes`: 사람이 승인한 릴리스 노트 원문
- `pub_date`: 이번 조립 실행의 UTC `Z` 시각
- `platforms.windows-x86_64.url`: 버전 고정 설치본 정규 URL
- `platforms.windows-x86_64.signature`: 검증한 설치본 `.sig`의 한 줄 Base64 본문

`latest.json`은 GitHub Latest 주소에서 제공하지만 그 안의 설치본 URL은 반드시
`releases/download/v0.1.4/...`처럼 버전이 고정되어야 한다. Windows x86 또는 계약 밖
플랫폼 키는 허용하지 않는다.

## 5. 서명된 `UPDATE-RELEASE.json`

매니페스트는 `update-release.schema.json`에 고정한 아래 열세 속성만 정확히 가진다.

- `schema`: `pcssak.update-release/v1`
- `product`: `PCssak Gongyu`
- `version`: `0.1.4`
- `tag`: `v0.1.4`
- `source_commit`: 승인한 소스의 소문자 40자리 Git SHA
- `installer`: `PCssak-Gongyu-0.1.4-Windows-x64-Setup.exe`
- `installer_sha256`: 실제 설치본 SHA-256
- `installer_size`: 실제 설치본 바이트 수인 양의 정수, 최대 536,870,912바이트(512 MiB)
- `eula_sha256`: 이 버전 소스 `LICENSE.txt` 정본의 정확한 바이트 SHA-256
- `privacy_sha256`: 이 버전 소스 `PRIVACY.md` 정본의 정확한 바이트 SHA-256
- `download_url`: 같은 태그의 버전 고정 정규 설치본 URL
- `notes`: 사람이 승인한 릴리스 노트 원문
- `notes_sha256`: 위 노트 문자열 UTF-8 바이트의 SHA-256

조립기는 매니페스트 서명을 먼저 검증한 뒤 모든 필드를 실제 입력·승인값과 교차 검증한다.
필드가 하나라도 더 있거나 빠진 경우, 대소문자·해시·크기·URL·커밋·노트가 다른 경우에는
출력 디렉터리를 만들기 전에 실패한다. 앱은 이 서명된 `installer_size`로 HTTP
`Content-Length`와 실제 스트림 누적 크기를 모두 제한한다. 앱에 내장된 법률 정본 바이트가
서명된 두 법률 해시와 다르면 앱 내 설치를 실패 폐쇄하고 공식 수동 NSIS 설치만 안내한다.

## 6. `DOWNLOAD-METADATA.json`: 사람·홈페이지용 정보

기존 `latest.json`의 사람용 역할은 `DOWNLOAD-METADATA.json`으로 분리한다.
`download-metadata.schema.json` 스키마 버전 2를 사용하며 다음을 제공한다.

- Free Early Access 채널, 버전, 소스 커밋, 게시 시각과 한·영 안내
- `draft=false`, `prerelease=false`, `latest=true`, 릴리스 제목과 버전 고정 페이지
- 설치본·설치본 서명·Tauri 매니페스트·서명된 배포 매니페스트의 이름·정규 URL·SHA-256과
  설치본 바이트 크기
- `SHA256SUMS.txt`, 제3자 고지와 정확한 MPL 원본 ZIP의 위치·SHA-256

이 파일은 Tauri Updater 프로토콜로 해석하지 않는다. 홈페이지는 자동 업데이트용
`latest.json`을 다운로드 카드 데이터로 재사용하지 않는다.

## 7. SHA-256과 순환 참조 방지

`SHA256SUMS.txt`는 소문자 64자리 해시, ASCII 공백 두 개, 정확한 파일명, 파일명 오름차순,
LF 줄바꿈을 사용한다. 자기 자신을 제외한 나머지 여덟 자산을 모두 담는다. 따라서
`latest.json`, 설치본 `.sig`, `UPDATE-RELEASE.json.sig`, `DOWNLOAD-METADATA.json`의 해시도
반드시 포함된다.

`SHA256SUMS.txt` 자체 해시는 사람의 최종 승인·게시 명령 입력으로 별도 기록할 수 있지만
파일 안에는 넣지 않는다. `DOWNLOAD-METADATA.json`도 `SHA256SUMS.txt`의 해시나 자기 자신의
해시를 넣지 않는다. 이 규칙으로 순환 참조를 만들지 않는다.

생성 순서는 다음과 같이 고정한다.

1. 설치본·두 `.sig`·`UPDATE-RELEASE.json`·MPL ZIP·고지문 입력의 해시와 신규성을 확인한다.
2. `BUILD-EVIDENCE.json`의 clean x64 빌드 증거와 NSIS 3.12 공식 ZIP·441개 공식 파일
   매니페스트·두 `makensis.exe`·`nsis_tauri_utils.dll` 고정 크기/해시를 정확 스키마로 검증한다.
   PATH Git은 금지하며 Program Files의 승인 Git for Windows 2.54.0.windows.1 x86_64에 대해
   고정 실행 파일 크기·SHA-256·빌드 커밋·Authenticode 상태·인증서 지문과 핸들 기반
   소유자/DACL·비재분석점·최종 경로·파일 ID를 검증한 `git_*` 8필드를 함께 요구한다.
3. 엄격 경로에서는 스크립트 자체의 사전/사후 검사로 완결할 수 없는 세 공급망 경계와 후보별
   Authenticode signer leaf 신원을 저장소 밖의 별도 승인 JSON과 승인 SHA-256으로 검증하며,
   없으면 실패 폐쇄한다. 0.1.x `-PublicEarlyAccess` 경로에서는 이 외부 증거를 완료로 가장하지
   않고 0.2.0 전 필수 작업으로 기록하며 입력 자체를 허용하지 않는다.
   - `pcssak.build-isolation-approval/v1`: 관리자 보호 읽기 전용 승인 commit snapshot,
     활성 토큰 비신뢰 쓰기 거부, NSIS 도구 트리 신규 child 생성 차단·매니페스트 잠금,
     네트워크 격리, 비릴리스 프로세스 차단
   - `pcssak.toolchain-provenance-approval/v1`: cargo·rustc·rustup·cargo-tauri의 버전,
     경로 계약, 크기, SHA-256, 서명 상태/지문, 공식 출처 참조, 빌드 중 읽기 전용
   - `pcssak.assembly-input-lock-approval/v1`: 실제 14입력 해시 매니페스트,
     FileShare.Read, 동일 핸들 hash/parse/copy, FileId, reparse 거부, 조립 프로세스 격리
   세 증거는 모두 실제 source commit과 별도 승인 `BUILD-EVIDENCE.json` SHA-256에 결속하고
   `decision=approved`, 모든 보안 불리언 `true`, 개인정보 없음이어야 한다. 조립기와 게시기는
   이를 생성하거나 추정하지 않으며 누락·false·해시 불일치면 출력/Draft 전에 중단한다.
4. 제품 내장 공개키와 실제 Minisign CLI로 두 서명을 검증한다.
5. 검증된 설치본 서명과 승인 노트로 `latest.json`을 만들고 해시한다.
6. 앞선 해시로 `DOWNLOAD-METADATA.json`을 만들고 해시한다.
7. 자기 자신을 제외한 여덟 자산을 `SHA256SUMS.txt`에 정렬 기록한다.
8. 최종 출력 9종의 이름·대소문자·크기·재분석 지점·해시와 두 서명을 다시 검증한다.

### 0.1.x 공개 Early Access 간소화 정책

관리자 승인에 따라 0.1.2 이상 0.2.0 미만의 정확한 3요소 0.1.x 버전은 기능 실측을 위한 공개
무료 Early Access 경로를 사용한다. 최종 소스 GitHub Actions, Tauri 업데이트 서명, 독립
Minisign 서명, SHA-256, MPL 원본, 법률 정본 결속과 정확한 9개 자산 검증은 생략하지 않는다.
대한민국 적격 전문가의 최종 법률 외부 검토, Windows 10/11 Home·Pro x64 전체 VM·실제 물리
LAN SSH/SFTP 실기, 세 공급망 독립 검토와 Windows 신뢰 Authenticode 서명은 미완료임을 공개
고지하고 0.2.0 공개 전에 엄격 게이트로 복원한다. 스크립트는 0.2.0 이상에서 이 경로를 자동
거부하며, 조립기나 게시기가 미완료 항목을 승인으로 바꾸지 않는다.

반복 배포는 같은 최종 소스 커밋·파이프라인 파일 해시·산출물 해시에 결속한 외부 상태 파일로
재개한다. 검증이 끝난 동일 바이트를 다시 빌드하거나 재서명하지 않고, GitHub Actions는 최종
소스가 확정된 뒤 그 SHA에 대해 한 번만 디스패치한다. 응답이 불확실하면 같은 SHA의 기존 실행을
조회하며 무조건 재디스패치하지 않는다.

## 8. MPL-2.0 원본 계약

`scripts/create-mpl-source-archive.ps1`이 현재 `Cargo.lock`, x64/i686 잠금 그래프와
`THIRD-PARTY-NOTICES.txt`를 교차 검증하고 로컬 Cargo 레지스트리 캐시의 정확한 `.crate`
원본으로 ZIP을 만든다. 임의의 브랜치·태그·소스 저장소 ZIP으로 대체하지 않는다. ZIP에는
해시 기준인 `Cargo.lock`, 전체 고지문, 생성 매니페스트도 함께 둔다. 구성요소 목록은
잠금 파일이 바뀔 수 있으므로 문서에서 손으로 고정하지 않고 생성기 결과를 기준으로 한다.

## 9. GitHub 원격 Draft-first 불변 게시 게이트

실제 게시는 GitHub Actions 할당량과 무관한 `scripts/publish-public-release.ps1`로만 수행한다.
스크립트가 Immutable Releases 설정을 켜지는 않는다. 관리자가 공개 저장소 설정에서 먼저 켠
뒤 읽기 전용 API가 `enabled=true`를 반환해야 다음 단계로 간다.

1. 공식 GitHub CLI 2.96.0의 고정 SHA-256, `GitHub, Inc.` Valid Authenticode와 인증·고정
   저장소를 확인한다. 모든 저장소 명령은 `github.com/pcssakinc/pcssak-gongyu-releases`, 모든
   REST 명령은 `--hostname github.com`에 고정하고, 자식 프로세스의 `GH_HOST`·`GH_REPO`도 같은
   값으로 제한하며 프롬프트와 Enterprise 토큰 값, debug·강제 TTY·외부 pager·프록시·사용자
   지정 TLS 인증서 환경을 차단한다.
   GitHub CLI 구성의 `http_unix_socket`도 비어 있어야 한다. 조립 결과의 별도 승인
   `Sha256SumsSha256`, 원격 `main` SHA 및 그 커밋의 EULA·개인정보 처리방침 바이트를 확인한다.
   승인 릴리스 노트는 원본을 잠근 상태에서 GUID 격리본으로 복사하고 파일·디렉터리 잠금과 승인
   해시를 공개 전환까지 유지한 경로만 GitHub CLI에 전달한다.
   엄격 경로에서는 원격 API를 호출하기 전에 저장소 밖의 대한민국 적격 전문가 최종 승인 JSON과
   Windows 10/11 Home·Pro x64 일회용 VM 실기 JSON을 각각 별도 승인 SHA-256으로 검증한다.
   법률 증거는 승인 소스·EULA·PRIVACY 해시에, VM 증거는 최종 설치본 SHA-256·크기 및 설치
   언어/EULA·HKLM seed·신규/복구/업그레이드·제거 양쪽 선택·원복 실패 중단 시나리오에 결속한다.
   0.1.x `-PublicEarlyAccess`에서는 이 두 증거가 미완료임을 승인 노트에 고지하고 해당 인수를
   받지 않는다. 게시기는 실제 승인 증거를 생성하거나 완료로 추정하지 않는다.
2. 태그와 Release가 모두 없으면 `v0.1.4`를 `draft=true`, `prerelease=false`, Free Early
   Access 제목으로 만든다. 둘 다 있으면 태그 target, Release ID·태그·제목·본문·target 및 기존
   자산 각각의 이름·`uploaded` 상태·크기·`sha256:` digest가 현재 승인 입력과 정확히 같은 Draft만
   재개한다. 태그/Release 중 하나만 있거나 승인 밖·중복·불일치 자산이 있으면 원격을 자동 변경하지
   않는다. 이미 정확히 공개된 9자산 Release라면 새 공개 요청 없이 최종 read-back부터 재개한다.
3. 정확한 9자산을 GUID 격리 승인 스냅샷으로 복사하고 파일·디렉터리 잠금을 유지한 경로만
   사용한다. 새 Draft 또는 검증한 부분 Draft에서 없는 자산만 하나씩 업로드하고, 각 호출의 종료
   코드와 무관하게 원격 파일명·`uploaded` 상태·크기·`sha256:` digest를 확인한 뒤 다음 자산으로
   간다. 기존 자산에 `--clobber`, 삭제 또는 태그 이동을 사용하지 않는다.
4. Draft 9자산을 새 임시 디렉터리에 다시 내려받아 모든 해시와 두 Minisign 서명을 재검증한다.
   각 검증의 공개키·서명·대상 파일과 데이터/입력 디렉터리는 실행이 끝날 때까지 잠그고 전후
   해시와 정확한 파일 집합을 다시 확인한다.
5. 공개 직전에 Immutable Releases 활성화, 원격 `main`·법률 정본, 태그 target 및 정확한 Draft
   9자산 digest를 다시 확인한다. 엄격 경로에서는 메모리에 고정한 법률·VM 승인 계약도 확인하고,
   두 경로 모두 단일 `gh release edit`
   명령으로만 `draft=false`, `prerelease=false`, Latest로 전환한다. 명령 응답이 실패하거나
   끊겨도 성공·실패를 추정하지 않고 고정 Release ID를 반복 read-back한다. 정확한 9자산의
   `draft=false`가 확인된 경우에만 공개 성공으로, 마지막 read-back이 정확한 `draft=true`이면
   안전 재개 가능한 실패로 판정하며, 읽을 수 없거나 계약이 다르면 원격 상태 불명 사고로 중단한다.
6. 공개 뒤 `immutable=true`, `gh release verify`, 각 자산의 `gh release verify-asset`, 정확한
   Latest 하나, `/releases/latest`와 `/releases/latest/download/latest.json` read-back을
   재검증한다.

Draft 검증 실패 시 자동 삭제하지 않는다. 원격 Draft가 현재 승인 입력과 정확히 일치하면 같은
입력으로 누락 자산부터 재개하고, 다르거나 상태를 확인할 수 없으면 조사한다. 불변 공개 전환 뒤
검증이 실패하면 자산 삭제·교체·태그 이동·자동 롤백을 시도하지 않고 배포 사고로 중단한다. 수정은
더 높은 새 버전으로만 수행한다.

## 10. 실패 폐쇄 조건

다음 중 하나라도 발견되면 게시를 중단한다.

- `draft=false`, `prerelease=false`, `Latest=true`, `v0.1.4` 또는 정확한 9자산 불일치
- `/releases/latest/download/latest.json`이 다른 버전·프리릴리스를 가리킴
- Gongyu 공개키 불일치·이중 인코딩·Minisign 검증 실패·다른 키 또는 과거 키의 서명
- Minisign 검증 중 공개키·서명·대상 바이트 또는 격리 데이터 디렉터리의 정확한 파일 집합 변경
- 설치본, 두 `.sig`, 두 매니페스트, 고지문, MPL ZIP 또는 `SHA256SUMS.txt` 해시 불일치
- 서명된 배포 매니페스트의 제품·버전·커밋·설치본 이름·해시·크기·정규 URL·승인 노트 불일치
- 고정하지 않은 Minisign/7-Zip, 7-Zip 격리 디렉터리의 추가 파일·재분석 지점 또는 NSIS 내부
  x64 앱과 같은 빌드 산출물의 해시 불일치
- 조립 결과에서 별도 승인한 `Sha256SumsSha256` 불일치, 고정하지 않은 GitHub CLI 버전·해시,
  `GitHub, Inc.`가 아닌 Authenticode 서명 또는 공개 직전 원격 상태 변경
- 설치본·MPL·서명 입력의 PE 형식 또는 재분석 지점 검증 실패, 엄격 경로의 Authenticode
  Valid·Code Signing EKU·타임스탬프 계약 실패, 0.1.x `-PublicEarlyAccess` 경로에서 설치기와
  내부 앱의 정확한 `not-signed` 쌍 불일치
- EULA·개인정보 처리방침 정본 바이트 불일치, 개인 Gmail·개인키·암호·인증서 노출
- 검증되지 않은 x86 설치본이나 계약에 없는 추가 Release 자산 포함
- 보안 제품 비활성화를 요구하는 설치 안내

엄격 x64 공개 전에는 최종 설치본의 SHA-256·크기와 소스 커밋에 결속된
`pcssak.x64-nsis-release-validation/v1` 승인 증거가 반드시 있어야 한다. Windows 10/11
Home·Pro x64 정확히 네 일회용 VM에서 설치 언어·EULA·HKLM 첫 실행 seed, 신규 설치·동일 버전
복구·상위 버전 업그레이드, 제거 [예]/[아니오], 원복 실패 중단과 별도 정리 안내를 모두 통과하지
못하면 원격 API를 호출하기 전에 공개를 차단한다. 0.1.x `-PublicEarlyAccess`에서는 이 행렬이
미완료임을 릴리스 노트에 공개하고 0.2.0 전 필수 작업으로 남긴다. 어느 경로에서도 모든 백신·
EDR·조직 정책과 도메인 이메일 발신·회신 조합까지 지원 완료로 표시하지 않으며, 미검증 조합은
알려진 Early Access 제한으로 계속 고지한다.

## 11. 공개 저장소 루트 법률 문서 정본

GitHub Release의 위 9자산과 공개 저장소 루트 법률 문서는 서로 다른 집합이다.

- 소스 저장소 `LICENSE.txt`가 EULA의 유일한 정본이며 공개 저장소 `EULA.txt`는 바이트 동일
  복사본이어야 한다.
- 소스 저장소 `PRIVACY.md`가 개인정보 처리방침의 유일한 정본이며 공개 저장소
  `PRIVACY.md`는 바이트 동일 복사본이어야 한다.

복사 과정에서 줄바꿈, BOM, 공백, 제목 또는 번역을 다시 만들지 않는다. 아래 읽기 전용
검증을 통과하지 못하면 공개 저장소 병합과 Release 게시를 차단한다.

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File `
  .\scripts\verify-release-repo-legal-copies.ps1 `
  -ReleaseRepositoryRoot <공개-릴리스-저장소-루트>
```

`EULA.md`를 유지한다면 `LICENSE.txt`의 바이트 동일 복사본 또는 검증기에 고정한
`fixed-pointer-to-EULA.txt` 포인터만 허용한다.

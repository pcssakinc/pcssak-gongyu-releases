# Security Policy / 보안 정책

## English

Security reports are evaluated against the latest publicly available PCssak
Gongyu Free Early Access release. Early Access can contain undiscovered defects;
this policy is a reporting and response boundary, not a guarantee that defects
do not exist.

For version 0.1.1 only, final external legal review and the full Windows 10/11
Home/Pro x64 VM/LAN matrix are deferred to 0.1.2. Cryptographic update signatures,
hashes, the fixed nine assets, and immutable-release verification remain in place,
but 0.1.1 is not a completed compatibility or legal-review claim. Prefer a
recoverable test system and a current backup.

### Report privately

After the public repository is created, use its GitHub private vulnerability
reporting channel when available. Otherwise email `support@pcssak.com` with:

- the affected PCssak Gongyu version and Windows edition/build;
- x64 architecture and whether the process was elevated;
- the smallest reproducible steps, expected result, and actual result;
- security impact and whether the issue is already public; and
- sanitized logs or a synthetic proof of concept.

Do not send passwords, private keys, tokens, recovery codes, personal documents,
or another person's data. Do not test against systems or accounts you do not own
or have explicit permission to assess. Allow reasonable remediation time before
public disclosure.

### Verify downloads

Download only from `pcssakinc/pcssak-gongyu-releases` or a version-pinned link on
`pcssak.com`. Compare the installer SHA-256 with `SHA256SUMS.txt` from the same
release. The Tauri updater verifies the published `.sig` with the Gongyu-specific
Minisign public key, and the independently signed `UPDATE-RELEASE.json` binds
release identity, installer hash and byte size, and the canonical installer URL.
The public 0.1.0 build has no in-app updater, so install the official 0.1.1 build
manually once before using signed in-app updates. The Early Access installer is
still not Authenticode-signed. Do not disable SmartScreen, Microsoft Defender,
a firewall, or another security product to bypass a warning.

## 한국어

보안 제보는 공개된 최신 PCssak Gongyu 무료 Early Access 버전을 기준으로 검토합니다.
Early Access에는 발견되지 않은 결함이 남아 있을 수 있으며, 이 정책은 제보와 대응 범위를
정하는 문서이지 결함이 없다는 보증이 아닙니다.

0.1.1에 한해 법률 전문가 최종 외부 검토와 Windows 10/11 Home·Pro x64 전체 VM·LAN 실기
행렬을 0.1.2로 유예했습니다. 업데이트 서명·해시·고정된 9개 자산·불변 릴리스 검증은
유지하지만, 0.1.1은 호환성 또는 법률 검토 완료를 뜻하지 않습니다. 복구 가능한 시험 환경과
최신 백업을 우선하세요.

### 비공개 제보

공개 저장소를 만든 뒤 GitHub 비공개 취약점 제보 기능을 사용할 수 있으면 그 채널을
우선합니다. 사용할 수 없으면 `support@pcssak.com`으로 다음 내용을 보내 주세요.

- 영향을 받는 PCssak Gongyu 버전과 Windows 에디션·빌드
- x64 아키텍처와 관리자 권한 실행 여부
- 최소 재현 절차, 기대 결과와 실제 결과
- 보안 영향과 이미 공개된 문제인지 여부
- 개인정보를 제거한 로그 또는 합성한 최소 재현 자료

암호, 개인키, 토큰, 복구 코드, 개인 문서나 다른 사람의 정보를 보내지 마세요. 소유하거나
명시적으로 허가받지 않은 시스템·계정은 시험하지 말고, 공개 전에 합리적인 수정 시간을
주세요.

### 다운로드 확인

`pcssakinc/pcssak-gongyu-releases` 또는 `pcssak.com`의 버전 고정 링크에서만 받고 같은
릴리스의 `SHA256SUMS.txt`와 설치 파일 SHA-256을 비교하세요. Tauri Updater는 공개한
`.sig`를 Gongyu 전용 Minisign 공개키로 검증하며, 별도로 서명한 `UPDATE-RELEASE.json`이
릴리스 신원·설치본 해시·바이트 크기와 정규 설치본 URL을 묶습니다. 공개 0.1.0에는 앱 내
updater가 없으므로 공식 0.1.1을 이번 한 번 수동 설치한 뒤부터 서명된 앱 내 업데이트를
사용하세요. Early Access 설치 파일에는 여전히 Authenticode 서명이 없습니다. 경고를
우회하려고 SmartScreen, Microsoft Defender, 방화벽 또는 다른 보안 제품을 끄지 마세요.

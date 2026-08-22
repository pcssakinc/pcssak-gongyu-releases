# MPL-2.0 구성요소 원본 소스 / MPL-2.0 Component Source

PCssak Gongyu 0.1.0은 수정하지 않은 MPL-2.0 적용 구성요소를 바이너리 형태로 포함합니다.
정확한 원본은 설치 파일과 같은 버전 고정 GitHub 릴리스의
[`PCssak-Gongyu-0.1.0-MPL-Sources.zip`](https://github.com/pcssakinc/pcssak-gongyu-releases/releases/download/v0.1.0/PCssak-Gongyu-0.1.0-MPL-Sources.zip)으로
제공합니다.

위 파일은 [`v0.1.0` 릴리스](https://github.com/pcssakinc/pcssak-gongyu-releases/releases/tag/v0.1.0)에
설치 파일과 고정 자산 전체가 실제로 게시된 경우에만 공식 제공물입니다. 링크에 파일이 없으면
아직 공개된 원본 묶음도 없습니다.

0.1.0 잠금 그래프에서 원본 묶음 대상은 다음과 같습니다.

- `cssparser 0.36.0`
- `cssparser-macros 0.6.1`
- `dtoa-short 0.3.5`
- `option-ext 0.2.0`
- `selectors 0.36.1`

묶음은 현재 `Cargo.lock`, Windows x64·i686 잠금 그래프와
[`THIRD-PARTY-NOTICES.txt`](../THIRD-PARTY-NOTICES.txt)를 교차 검증한 정확한 Cargo `.crate`
원본으로 생성합니다. 임의의 저장소 브랜치나 태그 ZIP으로 바꾸지 않습니다. 실제 릴리스의
`SHA256SUMS.txt`에서 원본 묶음 SHA-256을 확인하세요.

설치 프로그램은 전체 제3자 고지를 설치 경로의 `legal` 폴더에도 배치합니다. 링크가 작동하지
않거나 특정 MPL 구성요소의 원본 사본이 필요하면 제품 버전과 구성요소 이름만
`support@pcssak.com`으로 보내 주세요. 자격증명·개인 파일·로그는 필요하지 않습니다.

---

PCssak Gongyu 0.1.0 includes unmodified MPL-2.0-covered components in binary form. Their exact
source is provided with the installer in the same version-pinned GitHub release as
[`PCssak-Gongyu-0.1.0-MPL-Sources.zip`](https://github.com/pcssakinc/pcssak-gongyu-releases/releases/download/v0.1.0/PCssak-Gongyu-0.1.0-MPL-Sources.zip).

The file is an official distribution asset only when the
[`v0.1.0` release](https://github.com/pcssakinc/pcssak-gongyu-releases/releases/tag/v0.1.0)
actually publishes the installer and complete fixed asset set. If the asset is absent, no public
source bundle has been published yet.

The 0.1.0 lock graph identifies these source-bundle components:

- `cssparser 0.36.0`
- `cssparser-macros 0.6.1`
- `dtoa-short 0.3.5`
- `option-ext 0.2.0`
- `selectors 0.36.1`

The archive is generated from the exact Cargo `.crate` sources cross-checked against the current
`Cargo.lock`, Windows x64 and i686 lock graphs, and
[`THIRD-PARTY-NOTICES.txt`](../THIRD-PARTY-NOTICES.txt). It must not be replaced by an arbitrary
repository branch or tag archive. Verify its SHA-256 in `SHA256SUMS.txt` from the same release.

The installer also places the complete third-party notice in its `legal` directory. If the source
link is unavailable or a particular MPL component copy is needed, email `support@pcssak.com` with
only the product version and component name. Credentials, personal files and logs are unnecessary.

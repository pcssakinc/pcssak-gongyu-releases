# 공유 공개 배포 현재 상태

## 2026-09-13 — 0.2.7 GitHub 공개 검증 완료

[0.2.7](https://github.com/pcssakinc/pcssak-gongyu-releases/releases/tag/v0.2.7)은
2026-09-13 20:02:03 KST에 무료 Early Access의 불변 일반 릴리스로 공개됐다.
Release ID는 `387871856`이며 일반 Latest와 정확한 9자산의 익명 판독 검증을 마쳤다.

- 빌드 소스: `4353ea19de134329c38116eab360a943df20e5fa`
- 공개 태그 대상: `0086541d964a70139412f8ec242681fd4d781827`
- 설치본: `PCssak-Gongyu-0.2.7-Windows-x64-Setup.exe`, 3,696,906바이트
- 설치본 SHA-256: `dd7eba3622569915ed5655f02f5d7b35cadf20124eff6d313d5df13fb766e85a`
- 로컬 14단계 통과: Rust x64·i686 각각 856개 통과·실패 0·제외 13개, UI 374개 통과.
- 공개 검증: 9파일·스키마 3개·업데이트 서명 2개·MPL 원본 5개·법률·노트·소스·
  Latest 및 이전 0.2.6 공개 보존 통과. GitHub Actions는 미실행이다.

홈페이지도 [PR #125](https://github.com/pcssakinc/homepage/pull/125)의 운영 코드
`a38ce910606367a38ccc1fccc1a06ede3fe6c74c`로 배포와 검증을 완료했다.
Cloudflare Build `0ba38440-a03e-4de9-aa13-dbc261a92a59`, Worker
`3332307e-80d1-42e4-8ad5-5d646b3f3ce5`는 2026-09-13T11:18:17Z에 성공했다.
양 공식 도메인의 다운로드·가이드 네 페이지는 4 GET·HTTP 200으로 버전·고정 링크·해시·
보안 헤더를 확인했으며, 결과 SHA-256은
`4ba5f73ea7441879ab812efc7299219df57b46f63884223264887710830cd2c5`다.
운영 전체 검사는 20:18:52.765~20:23:20.866 KST에 최초 1회·종료 0·320/400 요청으로
통과했다. fresh/baseline은 false이며 결과 SHA-256은
`2f3c978a614e0723fdfae8025ad5313912bcc140b3bd6baf2f6486dcb916d267`다.
한국어 운영 다운로드의 대표 데스크톱 화면도 확인했다. 전체 스크롤·모바일 검증과 구분한다.

제보 PC의 실제 설치·SSH 켜기/끄기·SFTP·재부팅과 전체 Windows 실기, 외부 법률·독립
공급망 검토는 미완료이며 Authenticode 게시자 서명이 없다. 무료 Early Access 공개
완료와 실제 기기 문제 해결 완료를 구분한다.

근거 해시와 정확한 범위는 [배포 마감 일지](../WORKLOG_2026-09-13_V0.2.7_PUBLIC_RELEASE_CLOSEOUT.md),
기능·제약은 [승인 릴리스 노트](RELEASE-NOTES-v0.2.7.md)를 따른다.
다음 작업은 승인된 시험 PC에서 기존 환경 보존·연결·중단 복구를 확인하는 것이다.
마감 일지의 홈페이지 진행 중 문장은 당시 기록으로 보존한다. 이 후속 문서 마감으로
앱 빌드 소스·공개 태그·자산을 변경하지 않는다.

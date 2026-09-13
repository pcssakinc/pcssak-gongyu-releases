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

홈페이지 연결·배포·운영 검증은 이 기록 시점에 별도 작업으로 진행 중이다.
제보 PC의 실제 설치·SSH 켜기/끄기·SFTP·재부팅과 전체 Windows 실기, 외부 법률·독립
공급망 검토는 미완료이며 Authenticode 게시자 서명이 없다. 무료 Early Access 공개
완료와 실제 기기 문제 해결 완료를 구분한다.

근거 해시와 정확한 범위는 [배포 마감 일지](../WORKLOG_2026-09-13_V0.2.7_PUBLIC_RELEASE_CLOSEOUT.md),
기능·제약은 [승인 릴리스 노트](RELEASE-NOTES-v0.2.7.md)를 따른다.
다음 작업은 홈페이지 운영 검증 완료와 승인된 시험 PC에서 기존 환경 보존·연결·중단
복구를 확인하는 것이다. 문서 마감으로 공개 태그나 자산을 변경하지 않는다.

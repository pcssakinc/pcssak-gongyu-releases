# PCssak Gongyu 개인정보 처리방침

| 항목 | 내용 |
|---|---|
| 제품 | PCssak Gongyu 0.1.0 Early Access |
| 제품 식별자 | `com.pcssak.gongyu` |
| 브랜드 | PCSSAK |
| 법적 개인정보처리자 | PCSSAK |
| 개인정보 보호 담당 부서 | PCSSAK 개인정보 보호 담당 부서 |
| 개인정보 보호 문의 | privacy@pcssak.com |
| 시행일 | 2026-08-15 |

PCSSAK는 이 방침에서 사용하는 개인정보처리자명 겸 브랜드명입니다. 이 표시는 PCSSAK가
법인 또는 등록 사업자임을 주장하거나 대표자 실명·주소·사업자등록번호를 공시하는 문구가
아닙니다.

## 1. 핵심 요약

앱에는 PCSSAK가 운영하는 텔레메트리, 광고, 온라인 계정, 자동 업데이트, 원격 구성 또는
라이선스 인증 서버가 없습니다. 앱 설정과 자격증명은 사용자의 Windows PC에 저장됩니다.

다만 “아무 네트워크 통신도 없다”는 뜻은 아닙니다. 사용자가 요청한 LAN 검색, SMB 공유,
네트워크 드라이브, Wake-on-LAN, 공유 페어링 및 SSH는 사용자의 PC와 지정한 네트워크
대상 사이에서 통신합니다. OpenSSH Server 온라인 설치를 선택하면 Windows가 Microsoft,
Windows Update, WSUS 또는 조직이 설정한 기능 원본에 접속할 수 있습니다.

## 2. 적용 범위

이 방침은 PCssak Gongyu 앱이 로컬에서 다루는 정보와 사용자가 지원 이메일을 보낼 때의
처리를 설명합니다. 다음 서비스의 처리는 별도 방침과 설정을 확인해야 합니다.

- `pcssak.com` 웹사이트와 Cloudflare가 처리하는 접속 기록·쿠키
- GitHub 저장소와 Releases의 접속·다운로드 기록
- Microsoft Windows, WebView2 Runtime, OpenSSH Server, Windows Update 및 WSUS
- 사용자가 연결한 다른 PC, 파일 서버, 라우터 또는 조직의 네트워크

위 서비스의 실제 배포 구성과 처리방침이 함께 확정되지 않으면 웹사이트 또는 다운로드에
이 방침만을 공통 방침으로 표시해서는 안 됩니다.

## 3. 앱에서 로컬로 처리하는 정보

| 정보 | 목적 | 저장 위치 또는 처리 방식 | PCSSAK 서버 전송 |
|---|---|---|---|
| IP 주소, 호스트명, MAC 주소, 네트워크 어댑터 정보 | LAN 검색, 장치 식별, Wake-on-LAN, 접속 대상 표시 | 화면, 메모리, 즐겨찾기 및 진단 로그 | 없음 |
| 공유 이름, 로컬 폴더 경로, UNC 경로, 드라이브 문자 | 공유 생성·표시, 매핑, 소유권 검증 | 로컬 파일, Windows 공유 설정, 레지스트리, 로그 | 없음 |
| SMB 사용자명과 비밀번호 | 공유 인증과 선택적 자동 마운트 | DPAPI로 보호한 `vault.dat` 및 사용자가 선택한 경우 Windows 자격 증명 관리자 | 없음 |
| 페어링 계정명, 공유명, 생성 시각, 관리 토큰 | 앱이 만든 계정·공유·권한만 안전하게 관리 | `paired_accounts.json`, Windows 계정/ACL, `HKLM\SOFTWARE\PCSSAK\Gongyu` | 없음 |
| 즐겨찾기와 UI 설정 | 사용 편의와 화면 상태 복원 | `favorites.json`, WebView2 `localStorage` | 없음 |
| 앱이 만든 매핑 기록 | 앱 소유 매핑과 외부 매핑을 구분 | `managed_mounts.json` | 없음 |
| 진행 중 작업 기록 | 중복·충돌 작업 방지와 비정상 종료 후 안내 | 사용자 작업은 로컬 `operation_journal.json`, PC 전체 작업은 `%ProgramData%\PCSSAK-Gongyu\operation_journal.json` | 없음 |
| 오류·동작 로그 | 문제 진단과 원복 결과 확인 | `pcssak-gongyu.log`, `pcssak-gongyu.log.1`~`pcssak-gongyu.log.3` | 없음 |
| 현재 SMB 세션 사용자명 | 내 PC 공유의 접속자 표시 | 화면에 일시 표시 | 없음 |

위 파일은 기본적으로 `%LOCALAPPDATA%\PCSSAK\Gongyu\` 아래에 저장됩니다. 손상된
JSON 파일은 복구를 위해 같은 폴더의 `.corrupt-*` 보존본으로 이동될 수 있습니다.
예외적으로 PC 전체 작업 저널은 모든 Windows 사용자 세션에서 같은 중단 상태를 확인하기 위해
`%ProgramData%\PCSSAK-Gongyu\operation_journal.json`에 저장됩니다. 이 저널에는 작업 종류,
단계, 시작 시각과 복구 상태만 기록하며 경로·계정명·비밀번호·페어링 코드 같은 자유 형식 값은
기록하지 않습니다. 인증된 사용자는 상태를 읽을 수 있고 Administrators와 SYSTEM만 변경할 수
있습니다. 다른 PCSSAK 제품의 `%ProgramData%\PCSSAK` 공유 루트는 사용하거나 변경하지 않습니다.

0.1.0 이전 개발판의 로컬 폴더에만 같은 이름의 파일이 있으면 현행 파일을 덮어쓰지 않는
안전 복사 방식으로 한 번 이전합니다. 현행 파일이 이미 있으면 현행 파일을 유지하며, 구 파일은
어느 경우에도 자동 삭제하지 않습니다. JSON 데이터 이전이 실패하면 빈 저장소로 계속 진행하지
않고 오류를 표시합니다. 구 로그 복사만 실패한 경우에는 구 로그를 보존하고 새 위치에서 로깅을
계속합니다.

로그에는 작업 시각, IP·호스트·공유·경로, Windows 오류 코드와 실패 단계가 포함될 수
있습니다. 비밀번호와 페어링 코드는 로그에 기록하지 않도록 설계했지만, 사용자는 지원을
요청할 때 로그를 그대로 보내기 전에 불필요한 식별정보가 없는지 확인해야 합니다.

## 4. 앱이 의도적으로 수집하지 않는 정보

앱에는 PCSSAK 서버로 다음 정보를 업로드하는 코드가 없습니다.

- 사용 통계, 광고 식별자, 분석 이벤트 또는 충돌 보고서
- 온라인 PCSSAK 계정, 결제 정보 또는 라이선스 키
- 공유 폴더 안의 파일 내용, 화면 녹화, 키 입력 또는 브라우저 기록

앱은 공유와 접근 권한을 구성합니다. 사용자가 탐색기나 다른 프로그램으로 공유 파일을
열면 Windows SMB가 그 파일을 네트워크로 전송할 수 있으며, 이는 앱 서버로 보내는 것이
아닙니다.

## 5. 네트워크 통신

| 기능 | 대상과 범위 | 사용 시점 |
|---|---|---|
| LAN 검색·호스트 확인 | 사용자의 로컬 네트워크 주소 | 사용자가 검색을 시작한 때 |
| SMB 공유·매핑 | 사용자가 지정한 Windows PC 또는 파일 서버 | 공유 조회·접속·매핑 때 |
| Wake-on-LAN | 사용자가 선택한 네트워크의 브로드캐스트 | 사용자가 깨우기를 실행한 때 |
| 공유 페어링 | 사용자가 지정한 LAN 호스트의 TCP 19763 | 일회용 페어링 세션 동안 |
| SSH | 지정한 LAN 호스트의 TCP 22, 또는 내 PC의 SSH 수신 | 사용자가 별도 동의로 SSH를 켜거나 접속할 때 |
| OpenSSH Server 설치 | Windows Update, WSUS 또는 사용자가 지정한 오프라인 원본 | SSH 켜기에서 기능이 없고 설치 원본을 선택한 때 |

8자리 페어링 코드는 사용자가 확인할 수 있도록 화면에 표시되고, 입력한 코드는 WebView와 로컬
Tauri IPC 메모리를 잠시 통과합니다. JavaScript 문자열의 확정적인 메모리 소거까지 보장하지는
않으므로 화면 캡처, 화면 공유, 클립보드 기록과 주변 노출에 주의해야 합니다. 백엔드는 코드와
OPAQUE 비밀 상태를 작업 수명 동안만 메모리에서 처리하고, OPAQUE 등록 자료를 디스크에 저장하지
않습니다. 코드 원문과 코드의 단순 해시는 로그나 TCP 19763 패킷에 기록·전송하지 않습니다.

LAN에는 [RFC 9807 OPAQUE](https://www.rfc-editor.org/rfc/rfc9807.html)의 공개 KE1·KE2·KE3
메시지가 오갑니다. 인증이 끝난 뒤 SMB 사용자명·비밀번호는 OPAQUE 세션 키에서 파생한 키로
AES-256-GCM 암호화·인증한 응답 안에서만 전송합니다. 코드는 5분·1회용이고 새 코드를 발급하면
이전 코드는 즉시 무효화됩니다. 페어링 시도는 같은 IP에서 1분에 6회, 호스트 전체에서 1분에
12회로 제한합니다.

SMB·SSH 방화벽 규칙은 로컬 서브넷으로 제한하도록 설계되어 있습니다. 라우터, VPN,
도메인 정책 또는 사용자의 수동 설정에 따라 실제 도달 범위가 달라질 수 있으므로 조직
관리자는 Windows Defender 방화벽의 최종 규칙을 확인해야 합니다.

NSIS 설치본은 Microsoft WebView2 Evergreen 독립 실행형 설치 관리자를 포함하는
`offlineInstaller` 방식을 사용합니다. 설치 파일 자체는 WebView2를 받기 위한 인터넷 연결이
필요하지 않지만, 설치된 Evergreen Runtime의 유지·업데이트 정책은 Microsoft와 조직의
Windows 정책에 따릅니다.

## 6. 보관 기간과 삭제

앱의 로컬 데이터는 사용자가 삭제하거나 Windows 계정·PC를 정리할 때까지 남습니다. 앱에는
보관 기간이 지난 로컬 파일을 PCSSAK 서버에서 지우는 절차가 없습니다. 중앙 서버로 수집하지
않기 때문입니다.

프로그램 제거는 실행 파일과 설치 파일을 제거하지만 다음 항목을 모두 자동으로 지운다고
보장하지 않습니다.

- `%LOCALAPPDATA%\PCSSAK\Gongyu\`의 로컬 데이터와 로그
- HKCU 자동 시작 값과 WebView2 사용자 데이터
- 사용자가 만든 공유, 매핑, 계정, ACL 또는 Windows 자격 증명
- 별도로 켠 OpenSSH Server, `sshd` 서비스·설정 및 SSH 방화벽 상태

제거 전에 앱의 설정 원복, 페어링 계정 삭제, 공유 해제, SSH 끄기 및 자동 시작 끄기를 각각
확인하십시오. 정확한 제거 범위와 실패 시 동작은 `SECURITY.md`에 설명합니다.

## 7. 보호 조치와 사용자의 선택

- SMB 비밀번호는 Windows DPAPI의 현재 사용자 범위로 보호하며 평문으로 파일에 저장하지
  않습니다. 다른 Windows 사용자나 다른 PC로 파일만 복사하면 복호화되지 않습니다.
- 앱이 직접 만든 공유와 매핑은 별도 소유권 기록으로 외부 항목과 구분합니다. 기록과 Windows
  상태가 함께 검증되지 않으면 파괴적 관리 작업을 거부합니다.
- 민감한 시스템 경로는 공유 페어링 ACL 추가와 앱의 공유 해제 대상에서 백엔드가 차단합니다.
- 비밀번호나 보안 코드는 클립보드·화면에 일시 표시될 수 있으므로 주변 노출과 클립보드 기록에
  주의하십시오.
- 조직 PC에서는 관리자, 보안 정책, 백신·EDR 및 백업 정책을 먼저 확인하십시오.

## 8. 지원 이메일

사용자가 `support@pcssak.com` 또는 `privacy@pcssak.com`으로 문의하면 발신 이메일 주소와
표시 이름, 제목, 본문, 첨부파일, 메시지 ID와 전달 결과 같은 메일 메타데이터를 문의 접수,
답변, 보안 신고 확인 및 개인정보 권리행사 처리 목적으로 사용합니다. 비밀번호, 개인키,
전체 자격증명, 불필요한 개인정보 또는 공유 파일을 보내지 마십시오.

두 도메인 주소는 Cloudflare Email Routing을 거쳐 운영자의 Gmail 받은편지함으로 전달되도록
구성됩니다. 공개 문서와 화면에는 전달 대상인 개인 Gmail 주소를 표시하지 않습니다.
Cloudflare의 라우팅 분석에는 발신자·수신자·제목·메시지 ID·처리 결과가 최근 31일 동안
보관될 수 있고, 최종 수신·검색·보관은 Gmail에서 처리됩니다.

문의 메일은 처리 중 보관하고 문의가 종료된 날부터 1년 동안 후속 확인과 분쟁 대응을 위해
보관한 뒤 삭제합니다. 운영자는 매월 종료일을 확인하여 보관기간이 지난 메일과 첨부파일을
삭제합니다. 법령상 보존 의무, 진행 중인 분쟁 또는 보안 사고 조사를 위해 더 오래 보관해야
하면 해당 자료를 다른 문의와 구분하고 그 목적이 끝난 뒤 지체 없이 삭제합니다. Gmail에서
삭제한 자료가 서비스 제공자의 백업에서 완전히 소거되는 시점은 Google의 실제 보존·삭제
정책을 따릅니다.

Cloudflare Email Routing은 수신 전달 서비스입니다. 도메인 주소를 사용한 발신·회신과
SPF·DKIM·DMARC, 외부 Gmail·Outlook·Naver에서의 수신·회신 헤더는 아직 실측하지 않았습니다.
개인 Gmail 주소가 발신자나 반송 정보에 노출되지 않는다는 실측이 끝나기 전에는 공개 배포와
고객 회신을 시작하지 않습니다.

- Cloudflare Email Routing 안내: https://developers.cloudflare.com/email-service/get-started/route-emails/
- Cloudflare 라우팅 분석 데이터 안내: https://developers.cloudflare.com/email-service/observability/metrics-analytics/
- Google 개인정보처리방침: https://policies.google.com/privacy?hl=ko

- 문의 메일 보관 기간: 문의 종료일부터 1년, 이후 월 1회 점검하여 삭제
- 권리행사 처리 기간: 본인 확인이 끝난 정당한 요청은 접수일부터 10일 이내 결과 안내
- 외부 처리 서비스: Cloudflare Email Routing과 Google Gmail
- 이전되는 정보: 발신자·수신자 주소, 표시 이름, 제목, 본문, 첨부파일, 메시지 ID 및 처리 결과
- 이전 목적과 방법: 이메일 전달·보관·검색·답변을 위한 인터넷 전송
- 이전 시점: 사용자가 도메인 주소로 메일을 보내거나 운영자가 문의를 처리할 때
- 거부 방법과 영향: 이메일 전송을 하지 않을 수 있으며 앱의 로컬 기능 사용에는 영향이 없지만,
  개인별 지원·보안 신고 회신·이메일을 통한 권리행사는 제공하기 어렵습니다.
- 국외 처리 주체와 국가·지역: Cloudflare 계정 서비스 주체인 Cloudflare, Inc.(미국)가
  이메일 전달·라우팅 분석을 처리하며, Cloudflare는 정보를 주로 미국과 유럽경제지역에
  저장하고 글로벌 운영 지역에서 이전·접근할 수 있다고 고지합니다. Gmail 서비스 계약
  주체는 Google LLC(미국)이며, Google은 미국을 포함해 이용자의 거주국 밖에 있는 전 세계
  서버에서 정보를 처리할 수 있다고 고지합니다. 제공자의 실제 인프라 위치는 서비스 운영에
  따라 달라질 수 있으므로 최신 공식 방침을 함께 확인하며 중요한 변경은 이 방침에 반영합니다.

## 9. 정보주체의 권리와 연락처

앱 내부 데이터는 사용자가 자신의 PC에서 직접 열람·정정·삭제할 수 있습니다. 지원 이메일로
보낸 정보의 열람, 정정, 삭제, 처리정지 또는 동의 철회를 요청하려면 아래 연락처를 이용할 수
있습니다. 요청자 본인 또는 적법한 대리인인지 확인하기 위해 필요한 최소 정보만 추가로 요청할
수 있습니다. 본인 확인이 끝난 정당한 요청은 접수일부터 10일 이내에 조치 결과를 안내합니다.
법령상 제한 또는 보존 의무 때문에 전부 이행할 수 없으면 그 범위, 이유와 이의제기 방법을 같은
기간 안에 안내합니다.

- 개인정보 보호 담당 부서: PCSSAK 개인정보 보호 담당 부서
- 이메일: privacy@pcssak.com

## 10. 아동, 변경과 언어

프로그램은 아동을 대상으로 한 온라인 서비스가 아니며 생년월일을 수집하지 않습니다. 이
방침을 변경하면 시행 전에 변경 내용과 시행일을 배포 페이지 또는 새 설치본에 표시합니다.
중요한 변경에 별도 동의가 필요한 경우 새 동의를 받습니다.

한국어 방침이 정본입니다. 영어 사용자에게는 같은 처리 사실을 담은 번역을 함께 제공해야
하며, 번역과 한국어가 다르면 강행법규가 허용하는 범위에서 한국어 방침을 따릅니다.

무료 얼리액세스 공개는 모든 국가·지역의 개인정보 보호 법령 준수를 보증하지 않습니다.
이용자의 지역에서 배제할 수 없는 법령은 그대로 적용됩니다. 유료 제공을 시작하거나 사업자
등록 및 실제 거래·처리 구조가 확정되기 전에는 개인정보처리자 표시, 권리행사 창구, 처리위탁·
국외 이전, 보유 기간과 지역별 고지를 다시 검토하여 이 방침을 개정합니다.

## English reference translation

PCssak Gongyu 0.1.0 Early Access has no PCSSAK telemetry, advertising, online
account, automatic updater or license server. Local settings and credentials stay
on the user's Windows PC. User-selected LAN, SMB, Wake-on-LAN, pairing and SSH
operations still communicate with devices chosen by the user. Online installation
of the Windows OpenSSH optional feature may contact Microsoft, Windows Update,
WSUS or another source configured by the organization.

The 8-digit pairing code is briefly present in the UI and local IPC memory, but the
backend does not persist its OPAQUE registration state. Neither the raw code nor a
simple code hash is logged or sent over TCP 19763. The LAN exchange uses RFC 9807
OPAQUE messages; SMB credentials are returned only inside an AES-256-GCM protected
response derived from the authenticated OPAQUE session key.

Local files under `%LOCALAPPDATA%\PCSSAK\Gongyu\`, Windows credentials,
shares, accounts, ACLs, startup settings and OpenSSH state are not necessarily
deleted by uninstall. Review `SECURITY.md` before removal. Support email sent to
`support@pcssak.com` or `privacy@pcssak.com` is routed through Cloudflare Email Routing
to the operator's Gmail inbox. Cloudflare routing analytics may display sender,
recipient, subject, message ID and delivery-result data for the most recent 31 days.
The private destination address is not published. A message is retained while its
inquiry is active and for one year after closure, then reviewed and deleted monthly,
subject to a documented legal, dispute or security-investigation exception. A verified
request for access, correction, deletion or restriction is answered within 10 days.
Messages must not contain unnecessary passwords, private keys or personal information.

Cloudflare Email Routing provides inbound forwarding only. Domain sending, reply
headers, SPF, DKIM and DMARC have not yet passed end-to-end tests. Email routing is
handled by Cloudflare, Inc. in the United States; Cloudflare states that information is
stored primarily in the United States and the EEA and may be transferred or accessed
globally. Gmail is provided under the operator's account by Google LLC in the United
States, and Google states that information may be processed on servers outside the
user's country worldwide. Provider infrastructure can change, so current official
policies remain part of the notice and material changes must be reflected here.

If a pre-0.1.0 development file exists only in the legacy local folder, the app
copies it once without overwriting a current file and does not delete the legacy
source. A JSON migration failure stops that store from opening as empty; a log
copy failure preserves the old log and continues logging in the current folder.

The controller is PCSSAK, and privacy requests are handled by the PCSSAK Privacy
Protection Department at privacy@pcssak.com. PCSSAK is both the controller name and
brand name used in this notice. This does not represent that PCSSAK is incorporated
or registered as a business, and it does not publish a representative's personal name,
a physical address, or a business registration number. The Korean notice is
authoritative and this English text is a reference translation.

Free Early Access distribution does not guarantee compliance with every country or
region. Mandatory local law remains unaffected. Before paid distribution begins or a
business registration and actual transaction or processing structure are established,
the controller identity, rights channel, processors and international transfers,
retention, and local notices must be reviewed again. Until separate domain outbound
mail passes end-to-end tests, the operator must not reply from the private Gmail
destination address.

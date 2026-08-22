# PCssak Gongyu 0.1.0 — Free Early Access

> **Free Early Access publication notice / 무료 Early Access 공개 안내:** PCSSAK은 Windows x64
> 설치·제거 환경 전체와 같은 LAN 두 PC의 SMB·SSH 실기를 완료하지 않은 상태를 공개적으로
> 고지하고 0.1.0 배포를 승인했습니다. 로컬 자동검사 통과는 모든 PC에서의 호환성·안전성 보증이
> 아닙니다. 이 릴리스는 **Windows x64 전용**, **Authenticode 미서명**, **자동 업데이트 없음**
> 상태입니다. 중요한 환경보다 민감하지 않은 시험 폴더에서 먼저 사용하고 별도 백업을 유지하세요.
> 발견한 문제는 고정된 `v0.1.0` 자산을 교체하지 않고 후속 `0.1.1` 이상 버전에서 수정합니다.
>
> PCSSAK has approved 0.1.0 for public Free Early Access with the incomplete hands-on Windows x64
> matrix and same-LAN two-PC SMB/SSH validation explicitly disclosed. Passing local automated checks
> is not a guarantee of compatibility or safety on every PC. This release is **Windows x64 only**,
> **not Authenticode-signed**, and has **no automatic updater**. Start with a non-sensitive test
> folder and keep an independent backup. Reported defects will be addressed in a new `0.1.1` or
> later release; the fixed `v0.1.0` assets will not be replaced in place.

These localized summaries describe the same product and safety boundary. They do not prove that
the installer itself offers every language below.

## English

PCssak Gongyu 0.1.0 is a **free Early Access** release for **Windows x64**. On PCs connected to the
same trusted LAN, its core scope covers SMB shared-folder setup, network-drive connection and
management, and SSH remote commands and SFTP. The host PC must use a **Private or Domain** Windows
network profile. Public-network profiles, VPNs or tunnels, direct Internet access, and router port
forwarding are not supported.
The SSH boundary is the real Windows OpenSSH Server process (`sshd.exe`) on TCP 22, limited to the
host's active local IPv4 on-link CIDR; both PCs must share the same router and on-link LAN.

The installer is **not Authenticode-signed**, so Windows may show **Unknown publisher** or a
SmartScreen reputation warning. Download only from the official version-pinned Release and verify
the installer's SHA-256 against `SHA256SUMS.txt`; do not disable Windows security features. Windows
x86 and MSRA screen sharing or mouse control are not provided in 0.1.0.

- Support: `support@pcssak.com`
- Privacy requests: `privacy@pcssak.com`

## 한국어

PCssak Gongyu 0.1.0은 **Windows x64**용 **무료 Early Access** 버전입니다. 같은 신뢰 LAN에
연결한 PC에서 SMB 공유 폴더 설정, 네트워크 드라이브 연결·관리, SSH 원격 명령과 SFTP를 핵심
범위로 제공합니다. 호스트 PC의 Windows 네트워크 프로필은 **Private 또는 Domain**이어야
합니다. Public 네트워크 프로필, VPN·터널, 인터넷 직접 접속과 라우터 포트포워딩은 지원하지
않습니다.
SSH 허용 대상은 TCP 22에서 동작하는 실제 Windows OpenSSH Server 프로세스(`sshd.exe`)이며,
호스트의 활성 로컬 IPv4 온링크 CIDR로만 제한됩니다. 두 PC는 같은 공유기와 같은 온링크 LAN에
있어야 합니다.

설치 파일은 **Authenticode 미서명**이므로 Windows에 **알 수 없는 게시자(Unknown publisher)**
또는 SmartScreen 평판 경고가 나타날 수 있습니다. 공식 버전 고정 릴리스에서만 내려받고
`SHA256SUMS.txt`와 설치 파일의 SHA-256을 확인하세요. Windows 보안 기능을 끄지 마세요.
Windows x86과 MSRA 화면 공유·마우스 제어는 0.1.0에서 제공하지 않습니다.

- 지원: `support@pcssak.com`
- 개인정보 요청: `privacy@pcssak.com`

## 日本語

PCssak Gongyu 0.1.0 は、**Windows x64** 向けの**無料 Early Access** 版です。同じ信頼できる
LAN 上の PC を対象に、SMB 共有フォルダーの設定、ネットワークドライブの接続・管理、SSH
リモートコマンドおよび SFTP を主要機能として提供します。ホスト PC の Windows
ネットワークプロファイルは **Private または Domain** である必要があります。Public
ネットワーク、VPN・トンネル、インターネットからの直接接続、ルーターのポートフォワーディング
には対応していません。
SSH の許可対象は TCP 22 で動作する実際の Windows OpenSSH Server プロセス（`sshd.exe`）で、
ホストの有効なローカル IPv4 オンリンク CIDR のみに制限されます。2 台の PC は同じルーターと
同じオンリンク LAN に接続されている必要があります。

インストーラーは **Authenticode で署名されていない**ため、Windows に **Unknown
publisher（不明な発行元）**または SmartScreen の評価警告が表示される場合があります。
公式のバージョン固定 Release からのみダウンロードし、`SHA256SUMS.txt` と照合して
インストーラーの SHA-256 を確認してください。Windows のセキュリティ機能を無効にしないで
ください。Windows x86 および MSRA の画面共有・マウス操作は 0.1.0 では提供されません。

- サポート: `support@pcssak.com`
- プライバシーに関する依頼: `privacy@pcssak.com`

## 简体中文

PCssak Gongyu 0.1.0 是面向 **Windows x64** 的**免费 Early Access** 版本。在同一可信 LAN
内的电脑之间，核心功能包括 SMB 共享文件夹设置、网络驱动器连接与管理，以及 SSH 远程命令和
SFTP。主机的 Windows 网络配置文件必须为 **Private（专用）或 Domain（域）**。不支持 Public
（公用）网络、VPN 或隧道、从互联网直接访问以及路由器端口转发。
SSH 仅允许通过 TCP 22 访问实际的 Windows OpenSSH Server 进程（`sshd.exe`），并限制在主机
当前活动的本地 IPv4 on-link CIDR。两台电脑必须连接同一台路由器并位于同一 on-link LAN。

安装程序**未经过 Authenticode 签名**，因此 Windows 可能显示 **Unknown publisher（未知
发布者）**或 SmartScreen 信誉警告。请仅从绑定具体版本的官方 Release 下载，并根据
`SHA256SUMS.txt` 验证安装程序的 SHA-256；请勿关闭 Windows 安全功能。0.1.0 不提供 Windows
x86 版本，也不提供 MSRA 屏幕共享或鼠标控制。

- 支持：`support@pcssak.com`
- 隐私请求：`privacy@pcssak.com`

## 繁體中文

PCssak Gongyu 0.1.0 是適用於 **Windows x64** 的**免費 Early Access** 版本。在同一個受信任
LAN 內的電腦之間，核心功能包括 SMB 共用資料夾設定、網路磁碟機連線與管理，以及 SSH
遠端命令和 SFTP。主機的 Windows 網路設定檔必須為 **Private（私人）或 Domain（網域）**。不支援
Public（公用）網路、VPN 或通道、從網際網路直接存取，以及路由器連接埠轉送。
SSH 只允許透過 TCP 22 存取實際的 Windows OpenSSH Server 處理程序（`sshd.exe`），並限制於
主機目前啟用的本機 IPv4 on-link CIDR。兩部電腦必須連接同一部路由器並位於同一 on-link LAN。

安裝程式**未經 Authenticode 簽署**，因此 Windows 可能顯示 **Unknown publisher（未知的
發行者）**或 SmartScreen 信譽警告。請只從綁定特定版本的官方 Release 下載，並依照
`SHA256SUMS.txt` 驗證安裝程式的 SHA-256；請勿停用 Windows 安全性功能。0.1.0 不提供
Windows x86 版本，也不提供 MSRA 畫面共用或滑鼠控制。

- 支援：`support@pcssak.com`
- 隱私權要求：`privacy@pcssak.com`

## Français

PCssak Gongyu 0.1.0 est une version **Early Access gratuite** pour **Windows x64**. Sur des PC
reliés au même réseau local de confiance, ses fonctions principales couvrent la configuration des
dossiers partagés SMB, la connexion et la gestion des lecteurs réseau, ainsi que les commandes à
distance SSH et SFTP. Le PC hôte doit utiliser un profil réseau Windows **Privé ou Domaine**. Les
réseaux publics, les VPN ou tunnels, l'accès direct depuis Internet et la redirection de ports du
routeur ne sont pas pris en charge.
La limite SSH vise le véritable processus Windows OpenSSH Server (`sshd.exe`) sur le port TCP 22 et
se restreint au CIDR IPv4 local on-link actif de l'hôte ; les deux PC doivent partager le même
routeur et le même LAN on-link.

Le programme d'installation **n'est pas signé avec Authenticode** ; Windows peut donc afficher
**Unknown publisher (Éditeur inconnu)** ou un avertissement de réputation SmartScreen.
Téléchargez-le uniquement depuis la Release officielle liée à cette version et vérifiez son
SHA-256 avec `SHA256SUMS.txt` ; ne désactivez pas les fonctions de sécurité Windows. Windows x86 et
le partage d'écran ou le contrôle de la souris via MSRA ne sont pas proposés dans la version 0.1.0.

- Assistance : `support@pcssak.com`
- Demandes relatives à la vie privée : `privacy@pcssak.com`

## Deutsch

PCssak Gongyu 0.1.0 ist eine **kostenlose Early-Access-Version** für **Windows x64**. Auf PCs im
selben vertrauenswürdigen LAN gehören die Einrichtung von SMB-Freigaben, das Verbinden und
Verwalten von Netzlaufwerken sowie SSH-Fernbefehle und SFTP zum Kernumfang. Der Host-PC muss ein
Windows-Netzwerkprofil vom Typ **Privat oder Domäne** verwenden. Öffentliche Netzwerke, VPNs oder
Tunnel, direkter Zugriff aus dem Internet und Router-Portweiterleitungen werden nicht unterstützt.
Die SSH-Grenze gilt für den tatsächlichen Windows-OpenSSH-Serverprozess (`sshd.exe`) auf TCP 22 und
ist auf das aktive lokale IPv4-On-Link-CIDR des Hosts beschränkt; beide PCs müssen denselben Router
und dasselbe On-Link-LAN verwenden.

Das Installationsprogramm ist **nicht mit Authenticode signiert**. Windows kann daher **Unknown
publisher (Unbekannter Herausgeber)** oder eine SmartScreen-Reputationswarnung anzeigen. Laden Sie
es nur vom offiziellen, versionsgebundenen Release herunter und prüfen Sie den SHA-256-Wert anhand
von `SHA256SUMS.txt`; deaktivieren Sie keine Windows-Sicherheitsfunktionen. Windows x86 sowie
MSRA-Bildschirmfreigabe oder Maussteuerung werden in 0.1.0 nicht angeboten.

- Support: `support@pcssak.com`
- Datenschutzanfragen: `privacy@pcssak.com`

## Русский

PCssak Gongyu 0.1.0 — это **бесплатная версия раннего доступа (Early Access)** для **Windows x64**.
Основные возможности для компьютеров в одной доверенной локальной сети включают настройку общих
папок SMB, подключение и управление сетевыми дисками, а также удалённые команды по SSH и SFTP.
На компьютере-хосте должен использоваться профиль сети Windows **Частная или Доменная**. Публичные
сети, VPN или туннели, прямой доступ из Интернета и перенаправление портов на роутере не
поддерживаются.
Граница SSH относится к реальному процессу Windows OpenSSH Server (`sshd.exe`) на TCP-порту 22 и
ограничена активным локальным IPv4 on-link CIDR хоста; оба компьютера должны находиться за одним
маршрутизатором и в одной on-link LAN.

Установщик **не подписан с помощью Authenticode**, поэтому Windows может показать **Unknown
publisher (Неизвестный издатель)** или предупреждение о репутации SmartScreen. Загружайте его
только из официального выпуска с фиксированной версией и сверяйте SHA-256 с файлом
`SHA256SUMS.txt`; не отключайте функции безопасности Windows. Версия для Windows x86, а также
демонстрация экрана или управление мышью через MSRA в 0.1.0 не предоставляются.

- Поддержка: `support@pcssak.com`
- Запросы по вопросам конфиденциальности: `privacy@pcssak.com`

## Português (Brasil)

O PCssak Gongyu 0.1.0 é uma versão **Early Access gratuita** para **Windows x64**. Em PCs
conectados à mesma LAN confiável, o escopo principal inclui a configuração de pastas compartilhadas
SMB, a conexão e o gerenciamento de unidades de rede, além de comandos remotos por SSH e SFTP. O
PC host deve usar um perfil de rede do Windows **Privado ou Domínio**. Redes públicas, VPNs ou
túneis, acesso direto pela Internet e encaminhamento de portas no roteador não são compatíveis.
O limite de SSH se aplica ao processo real do Windows OpenSSH Server (`sshd.exe`) na porta TCP 22 e
fica restrito ao CIDR IPv4 local on-link ativo do host; os dois PCs devem usar o mesmo roteador e a
mesma LAN on-link.

O instalador **não possui assinatura Authenticode**, portanto o Windows pode exibir **Unknown
publisher (Editor desconhecido)** ou um aviso de reputação do SmartScreen. Baixe-o somente da
Release oficial vinculada à versão e verifique o SHA-256 com `SHA256SUMS.txt`; não desative os
recursos de segurança do Windows. O Windows x86 e o compartilhamento de tela ou controle do mouse
via MSRA não são oferecidos na versão 0.1.0.

- Suporte: `support@pcssak.com`
- Solicitações de privacidade: `privacy@pcssak.com`

## Türkçe

PCssak Gongyu 0.1.0, **Windows x64** için **ücretsiz bir Early Access** sürümüdür. Aynı güvenilir
LAN'a bağlı bilgisayarlarda temel kapsam; SMB paylaşımlı klasör kurulumu, ağ sürücüsü bağlantısı ve
yönetimi ile SSH üzerinden uzaktan komutları ve SFTP'yi içerir. Ana bilgisayarın Windows ağ profili
**Özel veya Etki Alanı** olmalıdır. Genel ağlar, VPN'ler veya tüneller, İnternet'ten doğrudan erişim
ve yönlendirici bağlantı noktası yönlendirmesi desteklenmez.
SSH sınırı, TCP 22 üzerinde çalışan gerçek Windows OpenSSH Server işlemi (`sshd.exe`) için geçerlidir
ve ana bilgisayarın etkin yerel IPv4 on-link CIDR'ı ile sınırlıdır; iki bilgisayar aynı yönlendiriciyi
ve aynı on-link LAN'ı kullanmalıdır.

Yükleyici **Authenticode ile imzalanmamıştır**; bu nedenle Windows, **Unknown publisher (Bilinmeyen
yayımcı)** veya SmartScreen itibar uyarısı gösterebilir. Yalnızca sürüme sabitlenmiş resmî Release
sayfasından indirin ve yükleyicinin SHA-256 değerini `SHA256SUMS.txt` ile doğrulayın; Windows güvenlik
özelliklerini devre dışı bırakmayın. Windows x86 ile MSRA ekran paylaşımı veya fare denetimi 0.1.0'da
sunulmaz.

- Destek: `support@pcssak.com`
- Gizlilik talepleri: `privacy@pcssak.com`

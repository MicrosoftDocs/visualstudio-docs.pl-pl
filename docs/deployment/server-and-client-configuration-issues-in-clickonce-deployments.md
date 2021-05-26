---
title: Problemy z konfiguracją serwera/klienta (ClickOnce)
description: Dowiedz się więcej o problemach z konfiguracją serwera i klienta, które mogą mieć wpływ na wdrożenie aplikacji ClickOnce.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications, ClickOnce
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
- Windows applications, ClickOnce deployments
ms.assetid: 929e5fcc-dd56-409c-bb57-00bd9549b20b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8040fb8028666d0dd551369b6b7f782de09058ca
ms.sourcegitcommit: 18e7300d4878f2fcd0263a4aff31a755ae8fc289
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/25/2021
ms.locfileid: "110449945"
---
# <a name="server-and-client-configuration-issues-in-clickonce-deployments"></a>Problemy konfiguracji serwera i klienta we wdrożeniach technologii ClickOnce
Jeśli używasz programu Internet Information Services (IIS) w systemie Windows Server, a wdrożenie zawiera typ pliku, który nie jest rozpoznany przez system Windows, taki jak plik programu Microsoft Word, usługi IIS odmówią przekazania tego pliku, a wdrożenie nie powiedzie się.

 Ponadto niektóre serwery internetowe i oprogramowanie aplikacji internetowych, takie jak , zawierają listę plików i typów plików, których [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] nie można pobrać. Na przykład [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] program uniemożliwia pobieranie wszystkich *Web.config* plików. Te pliki mogą zawierać poufne informacje, takie jak nazwy użytkowników i hasła.

 Chociaż to ograniczenie nie powinno powodować problemów z pobieraniem podstawowych plików, takich jak manifesty i zestawy, to ograniczenie może uniemożliwić pobieranie plików danych dołączonych [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji. W programie ten błąd można usunąć, usuwając program obsługi, który zabrania pobierania takich plików [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] z menedżera konfiguracji usług IIS. Aby uzyskać dodatkowe informacje, zobacz dokumentację serwera usług IIS.

 Niektóre serwery internetowe mogą blokować pliki z rozszerzeniami, takimi jak *dll,* *config* i *mdf.* Aplikacje oparte na systemie Windows zwykle zawierają pliki z niektórymi z tych rozszerzeń. Jeśli użytkownik spróbuje uruchomić aplikację, która uzyskuje dostęp do zablokowanego pliku na serwerze sieci Web, wystąpi [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] błąd. Zamiast odblokowywać wszystkie rozszerzenia plików, program domyślnie publikuje każdy plik aplikacji z rozszerzeniem [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] *.deploy.* W związku z tym administrator musi tylko skonfigurować serwer sieci Web, aby odblokować następujące trzy rozszerzenia plików:

- *.application*

- *Manifest*

- *.deploy*

  Tę opcję można jednak wyłączyć, czyszcząc opcję Użyj rozszerzenia pliku **".deploy"** w oknie dialogowym Opcje publikowania [.](/previous-versions/visualstudio/visual-studio-2010/7z83t16a(v=vs.100))W takim przypadku należy skonfigurować serwer sieci Web w celu odblokowania wszystkich rozszerzeń plików używanych w aplikacji.

  Musisz skonfigurować manifest *,* *.application* i *.deploy,* na przykład jeśli używasz usług IIS, w których nie zainstalowano programu .NET Framework, lub jeśli używasz innego serwera sieci Web (na przykład Apache).

## <a name="clickonce-and-secure-sockets-layer-ssl"></a>ClickOnce i Secure Sockets Layer (SSL)
 Aplikacja będzie działać prawidłowo za pośrednictwem protokołu SSL, z wyjątkiem [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Internet Explorer zgłasza monit o certyfikat SSL. Monit może zostać wyświetlony, gdy istnieje problem z certyfikatem, na przykład gdy nazwy lokacji nie są zgodne lub certyfikat wygasł. Aby wykonać pracę za pośrednictwem połączenia SSL, upewnij się, że certyfikat jest aktualny i że dane certyfikatu są zgodne [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] z danymi lokacji.

## <a name="clickonce-and-proxy-authentication"></a>ClickOnce i uwierzytelnianie serwera proxy
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Zapewnia obsługę zintegrowanego uwierzytelniania serwera proxy systemu Windows, począwszy od wersji .NET Framework 3.5. Nie są machine.config określone dyrektywy. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nie zapewnia obsługi innych protokołów uwierzytelniania, takich jak Podstawowe lub Szyfrowane.

 Aby włączyć tę funkcję, można również zastosować poprawkę do .NET Framework 2.0. Aby uzyskać więcej informacji, zobacz FIX: Komunikat o błędzie podczas próby zainstalowania aplikacji ClickOnce utworzonej w programie [.NET Framework 2.0](https://support.microsoft.com/help/917952/fix-error-message-when-you-try-to-install-a-clickonce-application-that)na komputerze klienckim skonfigurowanym do używania serwera proxy: "Wymagane jest uwierzytelnianie serwera proxy".

 Aby uzyskać więcej informacji, [ \<defaultProxy> zobacz element (ustawienia sieci)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings).

## <a name="clickonce-and-web-browser-compatibility"></a>Zgodność z usługą ClickOnce i przeglądarką sieci Web
 Obecnie instalacje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] będą uruchamiane tylko wtedy, gdy adres URL manifestu wdrożenia zostanie otwarty przy użyciu Internet Explorer. Wdrożenie, którego adres URL jest uruchamiany z innej aplikacji, takiej jak Microsoft Office Outlook, zostanie pomyślnie uruchomione tylko wtedy, Internet Explorer zostanie ustawiona jako domyślna przeglądarka sieci Web.

> [!NOTE]
> Mozilla Firefox jest obsługiwana, jeśli dostawca wdrażania nie jest pusty lub Microsoft .NET jest zainstalowane rozszerzenie Asystenta struktury. To rozszerzenie jest spakowane z .NET Framework 3.5 SP1. W przypadku obsługi XBAP wtyczka NPWPF jest aktywowana w razie potrzeby.

## <a name="activate-clickonce-applications-through-browser-scripting"></a>Aktywowanie aplikacji ClickOnce za pomocą skryptów przeglądarki
 Jeśli opracowano niestandardową stronę internetową, która uruchamia aplikację przy użyciu aktywnych skryptów, może się okazać, że aplikacja nie zostanie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uruchamiana na niektórych komputerach. Internet Explorer zawiera ustawienie o nazwie **Automatyczne monitowanie** o pobieranie plików , które ma wpływ na to zachowanie. To ustawienie jest dostępne na **karcie Zabezpieczenia** w **menu** Opcje, które ma wpływ na to zachowanie. Nosi ona nazwę **Automatyczne monitowanie o pobieranie plików** i jest wymieniona poniżej kategorii Pliki **do** pobrania. Właściwość jest domyślnie ustawiona na **wartość Włącz** dla intranetowych stron sieci Web i wartość **Wyłącz** domyślnie dla internetowych stron sieci Web. Jeśli to ustawienie jest ustawione na wartość **Wyłącz**, każda próba programowego aktywowania aplikacji (na przykład przez przypisanie jej adresu URL do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `document.location` właściwości) zostanie zablokowana. W takim przypadku użytkownicy mogą uruchamiać aplikacje tylko za pośrednictwem pobierania zainicjowanego przez użytkownika, na przykład przez kliknięcie hiperlinku ustawionego na adres URL aplikacji.

## <a name="additional-server-configuration-issues"></a>Dodatkowe problemy z konfiguracją serwera

##### <a name="administrator-permissions-required"></a>Wymagane uprawnienia administratora
 Jeśli publikujesz za pomocą protokołu HTTP, musisz mieć uprawnienia administratora na serwerze docelowym. Usługi IIS wymagają tego poziomu uprawnień. Jeśli nie publikujesz przy użyciu protokołu HTTP, potrzebujesz tylko uprawnienia do zapisu w ścieżce docelowej.

##### <a name="server-authentication-issues"></a>Problemy z uwierzytelnianiem serwera
 Po opublikowaniu na serwerze zdalnym, który ma wyłączony dostęp anonimowy, zostanie wyświetlony następujące ostrzeżenie:

```
"The files could not be downloaded from http://<remoteserver>/<myapplication>/.  The remote server returned an error: (401) Unauthorized."
```

> [!NOTE]
> Uwierzytelnianie NTLM (NT challenge-response) może działać, jeśli witryna wyświetli monit o poświadczenia inne niż poświadczenia domyślne, a w oknie dialogowym zabezpieczeń kliknij przycisk **OK** po wyświetleniu monitu, jeśli chcesz zapisać podane poświadczenia dla przyszłych sesji. Jednak to obejście nie będzie działać w przypadku uwierzytelniania podstawowego.

## <a name="use-third-party-web-servers"></a>Korzystanie z serwerów sieci Web innych firm
 W przypadku wdrażania aplikacji z serwera sieci Web innego niż usługi IIS może wystąpić problem, jeśli serwer zwraca nieprawidłowy typ zawartości dla plików kluczy, takich jak manifest wdrożenia i [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest aplikacji. Aby rozwiązać ten problem, zapoznaj się z dokumentacją pomocy serwera sieci Web dotyczącą dodawania nowych typów zawartości do serwera i upewnij się, że wszystkie mapowania rozszerzeń nazw plików wymienione w poniższej tabeli zostały podane.

|Rozszerzenie nazwy pliku|Typ zawartości|
|-------------------------|------------------|
|`.application`|`application/x-ms-application`|
|`.manifest`|`application/x-ms-manifest`|
|`.deploy`|`application/octet-stream`|
|`.msu`|`application/octet-stream`|
|`.msp`|`application/octet-stream`|

## <a name="clickonce-and-mapped-drives"></a>ClickOnce i zamapowane dyski
 Jeśli używasz Visual Studio do publikowania aplikacji ClickOnce, nie możesz określić zamapowany dysk jako lokalizację instalacji. Można jednak zmodyfikować aplikację ClickOnce, aby zainstalować ją z dysku zmapowanych przy użyciu generatora manifestu i edytora (Mage.exe i MageUI.exe). Aby uzyskać więcej informacji, [zobaczMage.exe (Narzędzie tworzenia i edycji manifestów)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool) i [MageUI.exe (Narzędzie tworzenia i edycji manifestów, Graphical Client).](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)

## <a name="ftp-protocol-not-supported-for-installing-applications"></a>Protokół FTP nie jest obsługiwany w przypadku instalowania aplikacji
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Obsługuje instalowanie aplikacji z dowolnego serwera sieci Web lub serwera plików HTTP 1.1. Protokół FTP, protokół transferu plików, nie jest obsługiwany w przypadku instalowania aplikacji. Za pomocą protokołu FTP można publikować tylko aplikacje. W poniższej tabeli podsumowano te różnice:

| Typ adresu URL | Opis |
|----------| - |
| ftp:// | Aplikację można [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] opublikować przy użyciu tego protokołu. |
| http:// | Aplikację można zainstalować [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] przy użyciu tego protokołu. |
| https:// | Aplikację można zainstalować [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] przy użyciu tego protokołu. |
| File:// | Aplikację można zainstalować [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] przy użyciu tego protokołu. |

## <a name="windows-xp-sp2-windows-firewall"></a>Windows XP z dodatkiem SP2: Zapora systemu Windows
 Domyślnie system Windows XP z dodatkiem SP2 włącza Zaporę systemu Windows. W przypadku tworzenia aplikacji na komputerze z zainstalowanym systemem Windows XP nadal można publikować i uruchamiać aplikacje z serwera lokalnego z uruchomionymi [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] usługami IIS. Nie można jednak uzyskać dostępu do tego serwera z uruchomionymi usługami IIS z innego komputera, chyba że zostanie otwarta Zapora systemu Windows. Aby uzyskać instrukcje dotyczące zarządzania Zaporą systemu Windows, zobacz Pomoc systemu Windows.

## <a name="windows-server-enable-frontpage-server-extensions"></a>Windows Server: włączanie rozszerzeń serwera FrontPage
 rozszerzenia FrontPage Server Extensions firmy Microsoft jest wymagany do publikowania aplikacji na serwerze sieci Web z systemem Windows, który używa protokołu HTTP.

 Domyślnie system Windows Server nie ma zainstalowanych rozszerzenia FrontPage Server Extensions instalacji. Jeśli chcesz użyć funkcji do publikowania na serwerze sieci Web z systemem Windows Server, który używa protokołu HTTP z rozszerzenia FrontPage Server Extensions, musisz najpierw [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozszerzenia FrontPage Server Extensions. Instalację można przeprowadzić przy użyciu narzędzia do zarządzania serwerem w systemie Windows Server.

## <a name="windows-server-locked-down-content-types"></a>Windows Server: zablokowane typy zawartości
 W usługach IIS wszystkie typy plików są blokowane z wyjątkiem niektórych znanych typów zawartości (na przykład [!INCLUDE[WinXPSvr](../debugger/includes/winxpsvr_md.md)] *htm,* *html,* *txt* itd.). Aby umożliwić wdrażanie aplikacji przy użyciu tego serwera, należy zmienić ustawienia usług IIS, aby umożliwić pobieranie plików typu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] *.application,* *.manifest* i innych typów plików niestandardowych używanych przez aplikację.

 W przypadku wdrażania przy użyciu serwera usług IIS uruchom *inetmgr.exe* i dodaj nowe typy plików dla domyślnej strony sieci Web:

- W przypadku *rozszerzeń .application* *i .manifest* typ MIME powinien być "application/x-ms-application". W przypadku innych typów plików typem MIME powinien być "application/octet-stream".

- Jeśli utworzysz typ MIME z rozszerzeniem "" i typem MIME "application/octet-stream", umożliwi to pobranie plików o niezablokowanych \<em> typach. (Jednak nie można pobrać zablokowanych typów plików, takich jak *\* aspx* i *\* asmx).*

  Aby uzyskać szczegółowe instrukcje dotyczące konfigurowania typów MIME w systemie Windows Server, zobacz Jak dodać typ [MIME](/iis/configuration/system.webserver/staticcontent/mimemap#how-to-add-a-mime-type-to-a-web-site-or-application)do witryny sieci Web lub aplikacji .

## <a name="content-type-mappings"></a>Mapowania typów zawartości
 Podczas publikowania za pośrednictwem protokołu HTTP typ zawartości (znany także jako typ MIME) dla pliku *.application* powinien być "application/x-ms-application". Jeśli zainstalowano .NET Framework 2.0 na serwerze, zostanie on ustawiony automatycznie. Jeśli ta aplikacja nie jest zainstalowana, należy utworzyć skojarzenie typu MIME dla wirtualnego serwera aplikacji [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] (lub całego serwera).

 W przypadku wdrażania przy użyciu serwera usług IIS uruchom <em>program inetmgr.</em> i dodaj nowy typ zawartości "application/x-ms-application" dla *rozszerzenia .application.*

## <a name="http-compression-issues"></a>Problemy z kompresją HTTP
 W programie można wykonywać pobieranie, które korzysta z kompresji HTTP, czyli technologii serwera sieci Web, która kompresuje strumień danych przy użyciu algorytmu GZIP przed wysłaniem strumienia [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] do klienta. Klient — w tym przypadku [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] — dekompresuje strumień przed odczytaniem plików.

 Jeśli używasz usług IIS, możesz łatwo włączyć kompresję HTTP. Jednak po włączeniu kompresji HTTP jest ona włączona tylko dla niektórych typów plików — czyli plików HTML i tekstowych. Aby włączyć kompresję zestawów *(dll),* XML *(xml),* manifestów wdrażania (*.application*) i manifestów aplikacji *(manifest*), należy dodać te typy plików do listy typów dla usług IIS do skompresowania. Do momentu dodania typów plików do wdrożenia tylko pliki tekstowe i HTML będą kompresowane.

 Aby uzyskać szczegółowe instrukcje dotyczące usług IIS, zobacz [Jak określić dodatkowe typy dokumentów](/troubleshoot/iis/content-types-http-compression.md)dla kompresji HTTP .

## <a name="see-also"></a>Zobacz też
- [Rozwiązywanie problemów z wdrożeniami technologii ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)
- [Wybieranie strategii wdrażania technologii ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)
- [Wstępnie wymagane składniki wdrażania aplikacji](../deployment/application-deployment-prerequisites.md)

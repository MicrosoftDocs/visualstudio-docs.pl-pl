---
title: Problemy z konfiguracją serwera/klienta we wdrożeniach ClickOnce
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 794b53a71a0a8215ae6bc9af47f9fe2a0ff911b5
ms.sourcegitcommit: 8589d85cc10710ef87e6363a2effa5ee5610d46a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/23/2019
ms.locfileid: "72806878"
---
# <a name="server-and-client-configuration-issues-in-clickonce-deployments"></a>Problemy konfiguracji serwera i klienta we wdrożeniach technologii ClickOnce
Jeśli używasz programu Internet Information Services (IIS) w systemie Windows Server, a wdrożenie zawiera typ pliku, który nie jest rozpoznawany przez system Windows, na przykład plik programu Microsoft Word, usługi IIS będą odrzucać przesłanie tego pliku, a wdrożenie nie powiedzie się.

 Ponadto niektóre serwery sieci Web i oprogramowanie aplikacji sieci Web, takie jak [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], zawierają listę plików i typów plików, których nie można pobrać. Na przykład [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] uniemożliwia pobieranie wszystkich plików *Web. config* . Te pliki mogą zawierać informacje poufne, takie jak nazwy użytkowników i hasła.

 Chociaż to ograniczenie nie powinno być przyczyną problemów z pobieraniem plików podstawowych [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], takich jak manifesty i zestawy, to ograniczenie może uniemożliwić pobranie plików danych zawartych jako część aplikacji [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. W [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]można rozwiązać ten problem, usuwając program obsługi, który uniemożliwia pobieranie takich plików z Menedżera konfiguracji usług IIS. Dodatkowe szczegóły można znaleźć w dokumentacji serwera IIS.

 Niektóre serwery sieci Web mogą blokować pliki z rozszerzeniami, takimi jak *dll*, *config*i *MDF*. Aplikacje oparte na systemie Windows zazwyczaj obejmują pliki z niektórymi z tych rozszerzeń. Jeśli użytkownik spróbuje uruchomić aplikację [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], która uzyskuje dostęp do zablokowanego pliku na serwerze sieci Web, zostanie zwrócony błąd. Zamiast odblokowywania wszystkich rozszerzeń plików, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] domyślnie publikuje każdy plik aplikacji z rozszerzeniem *. deploy* . W związku z tym administrator musi tylko skonfigurować serwer sieci Web, aby odblokować następujące trzy rozszerzenia plików:

- *. aplikacja*

- *. manifest*

- *. deploy*

  Można jednak wyłączyć tę opcję, czyszcząc opcję **Użyj rozszerzenia pliku ". deploy"** w [oknie dialogowym Opcje publikowania](/previous-versions/visualstudio/visual-studio-2010/7z83t16a(v=vs.100)), w takim przypadku należy skonfigurować serwer sieci Web tak, aby odblokował wszystkie rozszerzenia plików używane w aplikacji.

  Należy skonfigurować *. manifest*, *. Application*i *. deploy*, na przykład jeśli używasz usług IIS, w których nie zainstalowano .NET Framework, lub jeśli używasz innego serwera sieci Web (na przykład Apache).

## <a name="clickonce-and-secure-sockets-layer-ssl"></a>ClickOnce i SSL (SSL)
 Aplikacja [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] będzie działała za pośrednictwem protokołu SSL, z tą różnicą, że program Internet Explorer zgłasza monit dotyczący certyfikatu protokołu SSL. Monit można wypróbować, jeśli wystąpił problem z certyfikatem, na przykład jeśli nazwy lokacji nie są zgodne lub certyfikat wygasł. Aby [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pracy za pośrednictwem połączenia SSL, upewnij się, że certyfikat jest aktualny i że dane certyfikatu są zgodne z danymi lokacji.

## <a name="clickonce-and-proxy-authentication"></a>Uwierzytelnianie ClickOnce i serwer proxy
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] zapewnia obsługę uwierzytelniania zintegrowanego serwera proxy systemu Windows, począwszy od .NET Framework 3,5. Nie są wymagane żadne określone dyrektywy Machine. config. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nie zapewnia obsługi innych protokołów uwierzytelniania, takich jak Basic lub Digest.

 Aby włączyć tę funkcję, można również zastosować poprawkę do .NET Framework 2,0. Aby uzyskać więcej informacji, zobacz http://go.microsoft.com/fwlink/?LinkId=158730.

 Aby uzyskać więcej informacji, zobacz [\<defaultProxy > elementu (Ustawienia sieci)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings).

## <a name="clickonce-and-web-browser-compatibility"></a>Zgodność z programem ClickOnce i przeglądarką sieci Web
 Obecnie instalacje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] zostaną uruchomione tylko wtedy, gdy adres URL do manifestu wdrażania zostanie otwarty przy użyciu programu Internet Explorer. Wdrożenie, którego adres URL jest uruchamiany z innej aplikacji, takiej jak Microsoft Office Outlook, zostanie uruchomione pomyślnie tylko wtedy, gdy program Internet Explorer jest ustawiony jako domyślna przeglądarka sieci Web.

> [!NOTE]
> Mozilla Firefox jest obsługiwana, jeśli dostawca wdrożenia nie jest pusty lub zainstalowano rozszerzenie asystenta programu Microsoft .NET Framework. To rozszerzenie jest spakowane w .NET Framework 3,5 z dodatkiem SP1. W przypadku obsługi aplikacji XBAP wtyczka NPWPF jest uaktywniana w razie potrzeby.

## <a name="activate-clickonce-applications-through-browser-scripting"></a>Aktywuj aplikacje ClickOnce za pomocą skryptów przeglądarki
 Jeśli opracowano niestandardową stronę sieci Web, która uruchamia [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikację korzystającą z aktywnych skryptów, może się okazać, że aplikacja nie zostanie uruchomiona na niektórych komputerach. Program Internet Explorer zawiera ustawienie o nazwie **Automatyczne monitowanie dotyczące pobierania plików**, które ma wpływ na to zachowanie. To ustawienie jest dostępne na karcie **zabezpieczenia** w menu **Opcje** , która ma wpływ na to zachowanie. Jest on nazywany **automatycznym monitem o pliki do pobrania**i znajduje się na liście poniżej kategorii **pliki do pobrania** . Właściwość jest domyślnie **włączona** dla intranetowych stron sieci Web i domyślnie **wyłączona** dla internetowych stron sieci Web. Gdy to ustawienie jest **wyłączone**, każda próba aktywacji aplikacji [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] programowo (na przykład przez przypisanie jej adresu URL do właściwości `document.location`) zostanie zablokowana. W takim przypadku użytkownicy mogą uruchamiać aplikacje tylko za pomocą pobranego przez użytkownika pobrania, na przykład klikając hiperłącze ustawione na adres URL aplikacji.

## <a name="additional-server-configuration-issues"></a>Dodatkowe problemy z konfiguracją serwera

##### <a name="administrator-permissions-required"></a>Wymagane są uprawnienia administratora
 Jeśli publikujesz przy użyciu protokołu HTTP, musisz mieć uprawnienia administratora na serwerze docelowym. Usługi IIS wymagają tego poziomu uprawnień. Jeśli nie publikujesz przy użyciu protokołu HTTP, potrzebujesz uprawnienia do zapisu w ścieżce docelowej.

##### <a name="server-authentication-issues"></a>Problemy z uwierzytelnianiem serwera
 Po opublikowaniu na serwerze zdalnym, który ma wyłączony dostęp anonimowy, zostanie wyświetlone następujące ostrzeżenie:

```
"The files could not be downloaded from http://<remoteserver>/<myapplication>/.  The remote server returned an error: (401) Unauthorized."
```

> [!NOTE]
> Uwierzytelnianie NTLM (NT Challenge-Response) można wykonać, Jeśli lokacja monituje o poświadczenia inne niż poświadczenia domyślne, a następnie w oknie dialogowym Zabezpieczenia kliknij przycisk **OK** po wyświetleniu monitu, jeśli chcesz zapisać podane poświadczenia dla przyszłe sesje. To obejście nie będzie jednak działało w przypadku uwierzytelniania podstawowego.

## <a name="use-third-party-web-servers"></a>Korzystanie z serwerów sieci Web innych firm
 Jeśli wdrażasz aplikację [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] z serwera sieci Web innego niż IIS, może wystąpić problem, jeśli serwer zwraca nieprawidłowy typ zawartości dla plików [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Key, takich jak manifest wdrożenia i manifest aplikacji. Aby rozwiązać ten problem, zapoznaj się z dokumentacją pomocy serwera sieci Web dotyczącą sposobu dodawania nowych typów zawartości do serwera i upewnij się, że wszystkie mapowania rozszerzeń nazw plików wymienione w poniższej tabeli są stosowane.

|Rozszerzenie nazwy pliku|Typ zawartości|
|-------------------------|------------------|
|`.application`|`application/x-ms-application`|
|`.manifest`|`application/x-ms-manifest`|
|`.deploy`|`application/octet-stream`|
|`.msu`|`application/octet-stream`|
|`.msp`|`application/octet-stream`|

## <a name="clickonce-and-mapped-drives"></a>Technologia ClickOnce i zamapowane dyski
 Jeśli używasz programu Visual Studio do publikowania aplikacji ClickOnce, nie można określić dysku zamapowanego jako lokalizacji instalacji. Można jednak zmodyfikować aplikację ClickOnce, aby zainstalować ją z dysku zamapowanego przy użyciu generatora manifestu i edytora (Mage. exe i MageUI. exe). Aby uzyskać więcej informacji, zobacz temat [Mage. exe (narzędzie tworzenia i edycji manifestów)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool) i [MageUI. exe (narzędzie tworzenia i edycji manifestów, klient graficzny)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client).

## <a name="ftp-protocol-not-supported-for-installing-applications"></a>Protokół FTP nie jest obsługiwany w przypadku instalowania aplikacji
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] obsługuje instalowanie aplikacji z dowolnego serwera sieci Web lub serwera plików HTTP 1,1. FTP, protokół transferu plików nie jest obsługiwana w przypadku instalowania aplikacji. Za pomocą protokołu FTP można publikować tylko aplikacje. W poniższej tabeli zestawiono te różnice:

| Typ adresu URL | Opis |
|----------| - |
| ftp:// | Aplikację [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] można opublikować przy użyciu tego protokołu. |
| http:// | Możesz zainstalować aplikację [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] przy użyciu tego protokołu. |
| https:// | Możesz zainstalować aplikację [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] przy użyciu tego protokołu. |
| file:// | Możesz zainstalować aplikację [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] przy użyciu tego protokołu. |

## <a name="windows-xp-sp2-windows-firewall"></a>Windows XP z dodatkiem SP2: Zapora systemu Windows
 Domyślnie system Windows XP z dodatkiem SP2 włącza zaporę systemu Windows. W przypadku tworzenia aplikacji na komputerze z zainstalowanym systemem Windows XP nadal można publikować i uruchamiać [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacje z serwera lokalnego z uruchomionymi usługami IIS. Nie można jednak uzyskać dostępu do tego serwera z uruchomionymi usługami IIS z innego komputera, chyba że zostanie otwarta Zapora systemu Windows. Aby uzyskać instrukcje dotyczące zarządzania Zaporą systemu Windows, zobacz Pomoc systemu Windows.

## <a name="windows-server-enable-frontpage-server-extensions"></a>Windows Server: Włącz rozszerzenia serwera FrontPage
 Rozszerzenia FrontPage Server Extensions firmy Microsoft jest wymagana do publikowania aplikacji na serwerze sieci Web systemu Windows, który używa protokołu HTTP.

 Domyślnie system Windows Server nie ma zainstalowanych rozszerzenia FrontPage Server Extensions. Jeśli chcesz użyć [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] do opublikowania na serwerze sieci Web z systemem Windows Server, który używa protokołu HTTP z rozszerzenia FrontPage Server Extensions, musisz najpierw zainstalować rozszerzenia FrontPage Server Extensions. Instalację można przeprowadzić za pomocą narzędzia Zarządzanie serwerem administrowania w systemie Windows Server.

## <a name="windows-server-locked-down-content-types"></a>Windows Server: zablokowane typy zawartości
 Usługi IIS w [!INCLUDE[WinXPSvr](../debugger/includes/winxpsvr_md.md)] zablokują wszystkie typy plików z wyjątkiem pewnych znanych typów zawartości (na przykład *. htm*, *. html*, *. txt*itd.). Aby włączyć wdrażanie aplikacji [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] przy użyciu tego serwera, należy zmienić ustawienia usług IIS, aby zezwalały na pobieranie plików typu *. Application*, *manifest*i inne niestandardowe typy plików używane przez aplikację.

 W przypadku wdrażania przy użyciu serwera IIS Uruchom polecenie *inetmgr. exe* i Dodaj nowe typy plików dla domyślnej strony sieci Web:

- Dla rozszerzeń *. Application* i *. manifest* typ MIME powinien mieć wartość "application/x-MS-Application". W przypadku innych typów plików typ MIME powinien mieć wartość "application/octet-stream".

- W przypadku utworzenia typu MIME z rozszerzeniem "<em>" i typu MIME "application/octet-stream" zezwala na pobranie plików odblokowywanego typu plików. (Nie można jednak pobrać zablokowanych typów plików, takich jak *. aspx</em> i *. asmx* ).

  Aby uzyskać szczegółowe instrukcje dotyczące konfigurowania typów MIME w systemie Windows Server, zobacz artykuł KB326965 w bazie wiedzy Microsoft Knowledge Base "Usługa IIS 6,0 nie obsługuje nieznanych typów MIME" w [http://support.microsoft.com/default.aspx?scid=kb; en-us; 326965](http://support.microsoft.com/default.aspx?scid=kb;en-us;326965).

## <a name="content-type-mappings"></a>Mapowania typu zawartości
 Podczas publikowania przy użyciu protokołu HTTP typ zawartości (znany również jako typ MIME) dla pliku *. Application* powinien mieć wartość "application/x-MS-Application". Jeśli na serwerze jest zainstalowana .NET Framework 2,0, zostanie ona automatycznie ustawiona dla użytkownika. Jeśli nie jest zainstalowany, należy utworzyć skojarzenie typu MIME dla wirtualnego katalogu aplikacji [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] (lub całego serwera).

 W przypadku wdrażania przy użyciu serwera IIS Uruchom polecenie <em>inetmgr.</em> exe i Dodaj nowy typ zawartości "application/x-MS-Application" dla rozszerzenia *aplikacji* .

## <a name="http-compression-issues"></a>Problemy z kompresją HTTP
 Za pomocą [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]można wykonać pobieranie, które używają kompresji HTTP, technologii serwera sieci Web, która używa algorytmu GZIP do kompresowania strumienia danych przed wysłaniem strumienia do klienta. Klient — w tym przypadku [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]— dekompresuje strumień przed odczytaniem plików.

 W przypadku korzystania z usług IIS można łatwo włączyć kompresję HTTP. Jednak włączenie kompresji HTTP jest możliwe tylko dla niektórych typów plików — czyli plików HTML i tekstowych. Aby włączyć kompresję zestawów ( *. dll*), XML (*XML*), manifestów wdrożenia (*aplikacji*) i manifestów aplikacji ( *. manifest*), należy dodać te typy plików do listy typów dla usług IIS do skompresowania. Do momentu dodania typów plików do wdrożenia zostaną skompresowane tylko pliki tekstowe i HTML.

 Aby uzyskać szczegółowe instrukcje dotyczące usług IIS, zobacz [jak określić dodatkowe typy dokumentów dla kompresji http](https://support.microsoft.com/help/234497).

## <a name="see-also"></a>Zobacz także
- [Rozwiązywanie problemów z wdrożeniami ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)
- [Wybierz strategię wdrażania ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)
- [Wstępnie wymagane składniki wdrażania aplikacji](../deployment/application-deployment-prerequisites.md)
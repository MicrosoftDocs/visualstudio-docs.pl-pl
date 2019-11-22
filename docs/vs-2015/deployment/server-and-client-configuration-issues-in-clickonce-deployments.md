---
title: Problemy z konfiguracją serwera i klienta we wdrożeniach ClickOnce | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 35
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5a78fab1986c7fae50bbb4c8149e8f2c89ec4873
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295214"
---
# <a name="server-and-client-configuration-issues-in-clickonce-deployments"></a>Problemy konfiguracji serwera i klienta we wdrożeniach ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli używasz programu Internet Information Services (IIS) w systemie Windows Server, a wdrożenie zawiera typ pliku, który nie jest rozpoznawany przez system Windows, na przykład plik programu Microsoft Word, usługi IIS będą odrzucać przesłanie tego pliku, a wdrożenie nie powiedzie się.  
  
 Ponadto niektóre serwery sieci Web i oprogramowanie aplikacji sieci Web, takie jak [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], zawierają listę plików i typów plików, których nie można pobrać. Na przykład [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] uniemożliwia pobieranie wszystkich plików Web. config. Te pliki mogą zawierać informacje poufne, takie jak nazwy użytkowników i hasła.  
  
 Chociaż to ograniczenie nie powinno być przyczyną problemów z pobieraniem plików podstawowych [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], takich jak manifesty i zestawy, to ograniczenie może uniemożliwić pobranie plików danych zawartych jako część aplikacji [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]. W [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]można rozwiązać ten problem, usuwając program obsługi, który uniemożliwia pobieranie takich plików z Menedżera konfiguracji usług IIS. Dodatkowe szczegóły można znaleźć w dokumentacji serwera IIS.  
  
 Niektóre serwery sieci Web mogą blokować pliki z rozszerzeniami, takimi jak dll, config i MDF. Aplikacje oparte na systemie Windows zazwyczaj obejmują pliki z niektórymi z tych rozszerzeń. Jeśli użytkownik spróbuje uruchomić aplikację [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], która uzyskuje dostęp do zablokowanego pliku na serwerze sieci Web, zostanie zwrócony błąd. Zamiast odblokowywania wszystkich rozszerzeń plików, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] domyślnie publikuje każdy plik aplikacji z rozszerzeniem ". deploy". W związku z tym administrator musi tylko skonfigurować serwer sieci Web, aby odblokować następujące trzy rozszerzenia plików:  
  
- . aplikacja  
  
- . manifest  
  
- . deploy  
  
  Można jednak wyłączyć tę opcję, czyszcząc opcję **Użyj rozszerzenia pliku ". deploy"** w [oknie dialogowym Opcje publikowania](https://msdn.microsoft.com/fd9baa1b-7311-4f9e-8ffb-ae50cf110592), w takim przypadku należy skonfigurować serwer sieci Web tak, aby odblokował wszystkie rozszerzenia plików używane w aplikacji.  
  
  Należy skonfigurować. manifest,. Application i. Deploy, na przykład jeśli używasz usług IIS, w których nie zainstalowano [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], lub jeśli używasz innego serwera sieci Web (na przykład Apache).  
  
## <a name="clickonce-and-secure-sockets-layer-ssl"></a>ClickOnce i SSL (SSL)  
 Aplikacja [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] będzie działała za pośrednictwem protokołu SSL, z tą różnicą, że program Internet Explorer zgłasza monit dotyczący certyfikatu protokołu SSL. Monit można wypróbować, jeśli wystąpił problem z certyfikatem, na przykład jeśli nazwy lokacji nie są zgodne lub certyfikat wygasł. Aby [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] pracy za pośrednictwem połączenia SSL, upewnij się, że certyfikat jest aktualny i że dane certyfikatu są zgodne z danymi lokacji.  
  
## <a name="clickonce-and-proxy-authentication"></a>Uwierzytelnianie ClickOnce i serwer proxy  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] zapewnia obsługę uwierzytelniania zintegrowanego serwera proxy systemu Windows, począwszy od .NET Framework 3,5. Nie są wymagane żadne określone dyrektywy Machine. config. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nie zapewnia obsługi innych protokołów uwierzytelniania, takich jak Basic lub Digest.  
  
 Aby włączyć tę funkcję, można również zastosować poprawkę do .NET Framework 2,0. Aby uzyskać więcej informacji, zobacz https://go.microsoft.com/fwlink/?LinkId=158730.  
  
 Aby uzyskać więcej informacji, zobacz [\<defaultProxy > elementu (Ustawienia sieci)](https://msdn.microsoft.com/library/9d663c4b-07b4-4f6f-9b12-efbd3630354f).  
  
## <a name="clickonce-and-web-browser-compatibility"></a>Zgodność z programem ClickOnce i przeglądarką sieci Web  
 Obecnie instalacje [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] zostaną uruchomione tylko wtedy, gdy adres URL do manifestu wdrażania zostanie otwarty przy użyciu programu Internet Explorer. Wdrożenie, którego adres URL jest uruchamiany z innej aplikacji, takiej jak Microsoft Office Outlook, zostanie uruchomione pomyślnie tylko wtedy, gdy program Internet Explorer jest ustawiony jako domyślna przeglądarka sieci Web.  
  
> [!NOTE]
> Mozilla Firefox jest obsługiwana, jeśli dostawca wdrożenia nie jest pusty lub zainstalowano rozszerzenie asystenta programu Microsoft .NET Framework. To rozszerzenie jest spakowane w .NET Framework 3,5 z dodatkiem SP1. W przypadku obsługi aplikacji XBAP wtyczka NPWPF jest uaktywniana w razie potrzeby.  
  
## <a name="activating-clickonce-applications-through-browser-scripting"></a>Aktywowanie aplikacji ClickOnce za pomocą skryptów przeglądarki  
 Jeśli opracowano niestandardową stronę sieci Web, która uruchamia [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikację korzystającą z aktywnych skryptów, może się okazać, że aplikacja nie zostanie uruchomiona na niektórych komputerach. Program Internet Explorer zawiera ustawienie o nazwie **Automatyczne monitowanie dotyczące pobierania plików**, które ma wpływ na to zachowanie. To ustawienie jest dostępne na karcie **zabezpieczenia** w menu **Opcje** , która ma wpływ na to zachowanie. Jest on nazywany **automatycznym monitem o pliki do pobrania**i znajduje się na liście poniżej kategorii **pliki do pobrania** . Właściwość jest domyślnie **włączona** dla intranetowych stron sieci Web i domyślnie **wyłączona** dla internetowych stron sieci Web. Gdy to ustawienie jest **wyłączone**, każda próba aktywacji aplikacji [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] programowo (na przykład przez przypisanie jej adresu URL do właściwości `document.location`) zostanie zablokowana. W takim przypadku użytkownicy mogą uruchamiać aplikacje tylko za pomocą pobranego przez użytkownika pobrania, na przykład klikając hiperłącze ustawione na adres URL aplikacji.  
  
## <a name="additional-server-configuration-issues"></a>Dodatkowe problemy z konfiguracją serwera  
  
##### <a name="administrator-permissions-required"></a>Wymagane są uprawnienia administratora  
 Jeśli publikujesz przy użyciu protokołu HTTP, musisz mieć uprawnienia administratora na serwerze docelowym. Usługi IIS wymagają tego poziomu uprawnień. Jeśli nie publikujesz przy użyciu protokołu HTTP, potrzebujesz uprawnienia do zapisu w ścieżce docelowej.  
  
##### <a name="server-authentication-issues"></a>Problemy z uwierzytelnianiem serwera  
 Po opublikowaniu na serwerze zdalnym, który ma wyłączony dostęp anonimowy, zostanie wyświetlone następujące ostrzeżenie:  
  
```  
"The files could not be downloaded from http://<remoteserver>/<myapplication>/.  The remote server returned an error: (401) Unauthorized."  
```  
  
> [!NOTE]
> Uwierzytelnianie NTLM (NT Challenge-Response) można wykonać, Jeśli lokacja monituje o poświadczenia inne niż poświadczenia domyślne, a następnie w oknie dialogowym Zabezpieczenia kliknij przycisk **OK** po wyświetleniu monitu, jeśli chcesz zapisać podane poświadczenia dla przyszłych sesji. To obejście nie będzie jednak działało w przypadku uwierzytelniania podstawowego.  
  
## <a name="using-third-party-web-servers"></a>Korzystanie z serwerów sieci Web innych firm  
 Jeśli wdrażasz aplikację [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] z serwera sieci Web innego niż IIS, może wystąpić problem, jeśli serwer zwraca nieprawidłowy typ zawartości dla plików [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Key, takich jak manifest wdrożenia i manifest aplikacji. Aby rozwiązać ten problem, zapoznaj się z dokumentacją pomocy serwera sieci Web dotyczącą sposobu dodawania nowych typów zawartości do serwera i upewnij się, że wszystkie mapowania rozszerzeń nazw plików wymienione w poniższej tabeli są stosowane.  
  
|Rozszerzenie nazwy pliku|Typ zawartości|  
|-------------------------|------------------|  
|`.application`|`application/x-ms-application`|  
|`.manifest`|`application/x-ms-manifest`|  
|`.deploy`|`application/octet-stream`|  
|`.msu`|`application/octet-stream`|  
|`.msp`|`application/octet-stream`|  
  
## <a name="clickonce-and-mapped-drives"></a>Technologia ClickOnce i zamapowane dyski  
 Jeśli używasz programu Visual Studio do publikowania aplikacji ClickOnce, nie można określić dysku zamapowanego jako lokalizacji instalacji. Można jednak zmodyfikować aplikację ClickOnce, aby zainstalować ją z dysku zamapowanego przy użyciu generatora manifestu i edytora (Mage. exe i MageUI. exe). Aby uzyskać więcej informacji, zobacz temat [Mage. exe (narzędzie tworzenia i edycji manifestów)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1) i [MageUI. exe (narzędzie tworzenia i edycji manifestów, klient graficzny)](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14).  
  
## <a name="ftp-protocol-not-supported-for-installing-applications"></a>Protokół FTP nie jest obsługiwany w przypadku instalowania aplikacji  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] obsługuje instalowanie aplikacji z dowolnego serwera sieci Web lub serwera plików HTTP 1,1. FTP, protokół transferu plików nie jest obsługiwana w przypadku instalowania aplikacji. Za pomocą protokołu FTP można publikować tylko aplikacje. W poniższej tabeli zestawiono te różnice:  
  
|Typ adresu URL|Opis|  
|--------------|-----------------|  
|ftp://|Aplikację [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] można opublikować przy użyciu tego protokołu.|  
|http://|Możesz zainstalować aplikację [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] przy użyciu tego protokołu.|  
|https://|Możesz zainstalować aplikację [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] przy użyciu tego protokołu.|  
|file://|Możesz zainstalować aplikację [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] przy użyciu tego protokołu.|  
  
## <a name="windows-xp-sp2-windows-firewall"></a>Windows XP z dodatkiem SP2: Zapora systemu Windows  
 Domyślnie system Windows XP z dodatkiem SP2 włącza zaporę systemu Windows. W przypadku tworzenia aplikacji na komputerze z zainstalowanym systemem Windows XP nadal można publikować i uruchamiać [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacje z serwera lokalnego z uruchomionymi usługami IIS. Nie można jednak uzyskać dostępu do tego serwera z uruchomionymi usługami IIS z innego komputera, chyba że zostanie otwarta Zapora systemu Windows. Aby uzyskać instrukcje dotyczące zarządzania Zaporą systemu Windows, zobacz Pomoc systemu Windows.  
  
## <a name="windows-server-enable-frontpage-server-extensions"></a>Windows Server: Włącz rozszerzenia serwera FrontPage  
 Rozszerzenia FrontPage Server Extensions firmy Microsoft jest wymagana do publikowania aplikacji na serwerze sieci Web systemu Windows, który używa protokołu HTTP.  
  
 Domyślnie system Windows Server nie ma zainstalowanych rozszerzenia FrontPage Server Extensions. Jeśli chcesz użyć [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] do opublikowania na serwerze sieci Web z systemem Windows Server, który używa protokołu HTTP z rozszerzenia FrontPage Server Extensions, musisz najpierw zainstalować rozszerzenia FrontPage Server Extensions. Instalację można przeprowadzić za pomocą narzędzia Zarządzanie serwerem administrowania w systemie Windows Server.  
  
## <a name="windows-server-locked-down-content-types"></a>Windows Server: zablokowane typy zawartości  
 Usługi IIS w [!INCLUDE[WinXPSvr](../includes/winxpsvr-md.md)] zablokują wszystkie typy plików z wyjątkiem pewnych znanych typów zawartości (na przykład. htm,. html,. txt itd.). Aby włączyć wdrażanie aplikacji [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] przy użyciu tego serwera, należy zmienić ustawienia usług IIS, aby zezwalały na pobieranie plików typu. Application, manifest i inne niestandardowe typy plików używane przez aplikację.  
  
 W przypadku wdrażania przy użyciu serwera IIS Uruchom polecenie inetmgr. exe i Dodaj nowe typy plików dla domyślnej strony sieci Web:  
  
- Dla rozszerzeń. Application i. manifest typ MIME powinien mieć wartość "application/x-MS-Application". W przypadku innych typów plików typ MIME powinien mieć wartość "application/octet-stream".  
  
- W przypadku utworzenia typu MIME z rozszerzeniem "*" i typu MIME "application/octet-stream" będzie można pobrać pliki niezablokowanego typu plików. (Nie można jednak pobrać zablokowanych typów plików, takich jak. aspx i. asmx).  
  
  Aby uzyskać szczegółowe instrukcje dotyczące konfigurowania typów MIME w systemie Windows Server, zobacz artykuł KB326965 w bazie wiedzy Microsoft Knowledge Base "Usługa IIS 6,0 nie obsługuje nieznanych typów MIME" w [https://support.microsoft.com/default.aspx?scid=kb; en-us; 326965](https://support.microsoft.com/default.aspx?scid=kb;en-us;326965).  
  
## <a name="content-type-mappings"></a>Mapowania typu zawartości  
 Podczas publikowania przy użyciu protokołu HTTP typ zawartości (znany również jako typ MIME) dla pliku. Application powinien mieć wartość "application/x-MS-Application". Jeśli na serwerze zainstalowano [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)], zostanie ono automatycznie skonfigurowane. Jeśli nie jest zainstalowany, należy utworzyć skojarzenie typu MIME dla wirtualnego katalogu aplikacji [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] (lub całego serwera).  
  
 W przypadku wdrażania przy użyciu serwera IIS Uruchom polecenie inetmgr. exe i Dodaj nowy typ zawartości "application/x-MS-Application" dla rozszerzenia aplikacji.  
  
## <a name="http-compression-issues"></a>Problemy z kompresją HTTP  
 Za pomocą [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]można wykonać pobieranie, które używają kompresji HTTP, technologii serwera sieci Web, która używa algorytmu GZIP do kompresowania strumienia danych przed wysłaniem strumienia do klienta. Klient — w tym przypadku [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]— dekompresuje strumień przed odczytaniem plików.  
  
 W przypadku korzystania z usług IIS można łatwo włączyć kompresję HTTP. Jednak włączenie kompresji HTTP jest możliwe tylko dla niektórych typów plików — czyli plików HTML i tekstowych. Aby włączyć kompresję zestawów (. dll), XML (XML), manifestów wdrożenia (aplikacji) i manifestów aplikacji (. manifest), należy dodać te typy plików do listy typów dla usług IIS do skompresowania. Do momentu dodania typów plików do wdrożenia zostaną skompresowane tylko pliki tekstowe i HTML.  
  
 Aby uzyskać szczegółowe instrukcje dotyczące usług IIS, zobacz [jak określić dodatkowe typy dokumentów dla kompresji http](https://go.microsoft.com/fwlink/?LinkId=178459).  
  
## <a name="see-also"></a>Zobacz też  
 [Rozwiązywanie problemów z wdrożeniami ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)   
 [Wybieranie strategii wdrażania ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [Wstępnie wymagane składniki wdrażania aplikacji](../deployment/application-deployment-prerequisites.md)

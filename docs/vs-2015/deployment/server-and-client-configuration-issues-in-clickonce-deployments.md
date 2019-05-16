---
title: Serwer i problemy z konfiguracją klienta we wdrożeniach ClickOnce | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 8b8f81f22ffe566524e45a62330bc95c8ce00016
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65686379"
---
# <a name="server-and-client-configuration-issues-in-clickonce-deployments"></a>Problemy konfiguracji serwera i klienta we wdrożeniach ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli używasz usług Internet Information Services (IIS) w systemie Windows Server, a wdrożenie zawiera typ pliku, który nie rozpoznaje Windows, takich jak plik programu Microsoft Word, usługi IIS będą odrzucać do przekazywania pliku, a wdrożenie zakończy się niepowodzeniem.  
  
 Ponadto niektóre serwery i sieci Web aplikacji, takich jak [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], zawiera listę plików i typy, których nie można pobrać plików. Na przykład [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] uniemożliwia pobieranie wszystkich plików w pliku Web.config. Te pliki mogą zawierać poufne informacje, takie jak nazwy użytkowników i hasła.  
  
 Mimo że to ograniczenie nie powinny powodować żadnych problemów w przypadku pobierania core [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] plików, takich jak manifesty i zestawy, to ograniczenie może uniemożliwić pobieranie plików danych dołączone jako część Twojego [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji. W [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], możesz rozwiązać ten problem, usuwając program obsługi, który uniemożliwia pobieranie tych plików z Menedżera konfiguracji usług IIS. Zobacz dokumentację serwera usług IIS, aby uzyskać więcej informacji.  
  
 Niektóre serwery internetowe mogą blokować pliki z rozszerzeniem .dll, config i .mdf. Aplikacje systemu Windows obejmują zazwyczaj pliki z niektórymi z tych rozszerzeń. Jeśli użytkownik podejmie próbę uruchomienia [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji, która uzyskuje dostęp do zablokowanych plików na serwerze sieci Web, spowoduje zgłoszenie błędu. Zamiast odblokowywania wszystkich rozszerzeń plików [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] publikuje każdy plik aplikacji z rozszerzeniem pliku ".deploy" domyślnie. W związku z tym administrator musi tylko skonfigurować serwer sieci Web, aby odblokować następujące trzy rozszerzenia:  
  
- .Application  
  
- Manifest  
  
- .deploy  
  
  Jednak tę opcję można wyłączyć, usuwając zaznaczenie **rozszerzenie pliku ".deploy"** opcja [okno dialogowe Opcje publikowania](https://msdn.microsoft.com/fd9baa1b-7311-4f9e-8ffb-ae50cf110592), w którym to przypadku należy skonfigurować serwer sieci Web, aby odblokować wszystkie rozszerzenia plików używane w aplikacji.  
  
  Trzeba będzie skonfigurować manifest, .application i .deploy, na przykład korzystania z usług IIS, w którym nie zainstalowano [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], lub jeśli używasz innego serwera sieci Web (np. Apache).  
  
## <a name="clickonce-and-secure-sockets-layer-ssl"></a>ClickOnce i protokołu Secure Sockets Layer (SSL)  
 A [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacja będzie działać prawidłowo za pośrednictwem protokołu SSL, z wyjątkiem sytuacji, gdy program Internet Explorer zgłasza monit o certyfikat SSL. Monit może być wywoływane, gdy ma się, że wystąpił problem z certyfikatem, takie jak kiedy nazwy lokacji nie są zgodne lub certyfikat wygasł. Zapewnienie [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] działa za pośrednictwem połączenia SSL, upewnij się, że certyfikat jest aktualny i że dane certyfikatu są zgodne dane lokacji.  
  
## <a name="clickonce-and-proxy-authentication"></a>ClickOnce i uwierzytelnianie serwera Proxy  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] zapewnia obsługę Windows zintegrowanego uwierzytelniania serwera proxy, począwszy od programu .NET Framework 3.5. Nie dyrektywy określonych machine.config nie są wymagane. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nie zapewnia obsługi innych protokołów uwierzytelniania, takich jak podstawowe lub szyfrowane.  
  
 Można również zastosować poprawkę do .NET Framework 2.0, aby włączyć tę funkcję. Aby uzyskać więcej informacji, zobacz http://go.microsoft.com/fwlink/?LinkId=158730.  
  
 Aby uzyskać więcej informacji, zobacz [ \<defaultProxy >, Element (ustawienia sieci)](https://msdn.microsoft.com/library/9d663c4b-07b4-4f6f-9b12-efbd3630354f).  
  
## <a name="clickonce-and-web-browser-compatibility"></a>ClickOnce i zgodności z przeglądarką sieci Web  
 Obecnie [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] instalacje będą uruchamiane tylko wtedy, gdy adres URL do manifestu wdrażania jest otwierane przy użyciu programu Internet Explorer. Wdrożenia, którego adres URL jest uruchamiane w innej aplikacji, takich jak Microsoft Office Outlook, zostanie uruchomiony pomyślnie tylko wtedy, gdy program Internet Explorer jest ustawiony jako domyślnej przeglądarki sieci Web.  
  
> [!NOTE]
> Mozilla Firefox jest obsługiwana, gdy dostawca wdrożenia nie jest pusty lub zainstalowaniu rozszerzenia Asystenta ustawień programu Microsoft .NET Framework. To rozszerzenie jest dostarczana z .NET Framework 3.5 SP1. Do obsługi XBAP NPWPF wtyczki jest uaktywniany w razie potrzeby.  
  
## <a name="activating-clickonce-applications-through-browser-scripting"></a>Aktywacja aplikacji ClickOnce za pomocą skryptów w przeglądarce  
 Jeśli projektujesz niestandardowy strona internetowa, która uruchamia [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji przy użyciu wykonywanie aktywnych skryptów może się okazać, że aplikacja nie uruchomi się na niektórych maszynach. Program Internet Explorer zawiera ustawienia o nazwie **automatycznego monitowania do pobierania plików**, co ma wpływ na to zachowanie. To ustawienie jest dostępne na **zabezpieczeń** karcie jego **opcje** menu, który wpływa na to zachowanie. Jest on nazywany **automatycznego monitowania do pobierania plików**, i znajduje się poniżej **pliki do pobrania** kategorii. Właściwość jest ustawiona na **Włącz** domyślnie dla stron sieci Web w sieci intranet i **wyłączyć** domyślnie dla stron sieci Web. Jeśli to ustawienie jest równa **wyłączyć**, próby aktywacji [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji programowo (na przykład, przypisując jej adres URL do `document.location` właściwość) zostanie zablokowane. W takiej sytuacji użytkownicy mogą uruchamiać aplikacje wyłącznie za pośrednictwem pobierania zainicjowanego przez użytkownika, na przykład, klikając hiperłącze Ustaw adres URL aplikacji.  
  
## <a name="additional-server-configuration-issues"></a>Problemy z konfiguracją dodatkowy serwer  
  
##### <a name="administrator-permissions-required"></a>Uprawnienia administratora niezbędne  
 W przypadku publikowania za pośrednictwem protokołu HTTP, musi mieć uprawnienia administratora na serwerze docelowym. Usługi IIS wymaga tego poziomu uprawnień. Jeśli nie jest publikowany, przy użyciu protokołu HTTP, musisz tylko mieć uprawnienia zapisu w ścieżce docelowej.  
  
##### <a name="server-authentication-issues"></a>Problemy z uwierzytelnianiem serwera  
 Podczas publikowania na serwerze zdalnym, który ma wyłączone "anonimowy dostęp", otrzymasz następujące ostrzeżenie:  
  
```  
"The files could not be downloaded from http://<remoteserver>/<myapplication>/.  The remote server returned an error: (401) Unauthorized."  
```  
  
> [!NOTE]
> Aby włączyć uwierzytelnianie NTLM (NT żądanie odpowiedź) działać, jeśli witryna monituje o podanie poświadczeń innych niż poświadczenia domyślne, a w oknie dialogowym Zabezpieczenia, kliknij **OK** po wyświetleniu monitu, jeśli chcesz zapisać podane poświadczenia na potrzeby przyszłych sesji. To rozwiązanie nie będzie działać dla uwierzytelniania podstawowego.  
  
## <a name="using-third-party-web-servers"></a>Korzystanie z serwerów sieci Web innych firm  
 Jeżeli wdrażasz [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji z serwera sieci Web innej niż IIS, problem może występować, jeśli serwer zwraca nieprawidłowy typ zawartości dla klucza [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] plików, takich jak manifesty wdrożenia i manifest aplikacji. Aby rozwiązać ten problem, zobacz Pomoc dla serwera sieci Web, dokumentację, jak dodać nowe typy zawartości do serwera i upewnij się, że wszystkie plik rozszerzenia mapowania nazw są wymienione w poniższej tabeli znajdują się w miejscu.  
  
|Rozszerzenie nazwy pliku|Typ zawartości|  
|-------------------------|------------------|  
|`.application`|`application/x-ms-application`|  
|`.manifest`|`application/x-ms-manifest`|  
|`.deploy`|`application/octet-stream`|  
|`.msu`|`application/octet-stream`|  
|`.msp`|`application/octet-stream`|  
  
## <a name="clickonce-and-mapped-drives"></a>ClickOnce i zamapowanego dysków  
 Jeśli publikowanie aplikacji ClickOnce przy użyciu programu Visual Studio, nie można określić zamapowanego dysku jako lokalizację instalacji. Jednak można modyfikować aplikacji ClickOnce, aby zainstalować z dysku zmapowanego przy użyciu generatora manifestu i Edytor (Mage.exe i MageUI.exe). Aby uzyskać więcej informacji, zobacz [Mage.exe (Manifest Generation i narzędzia do edytowania)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1) i [MageUI.exe (Manifest Generation i graficzny klient Editing Tool)](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14).  
  
## <a name="ftp-protocol-not-supported-for-installing-applications"></a>Protokół FTP nieobsługiwane w przypadku instalowania aplikacji  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] obsługuje instalowanie aplikacji z dowolnego serwera HTTP 1.1 w sieci Web lub serwera plików. FTP, protokół transferu plików, nie jest obsługiwana dla instalacji aplikacji. FTP umożliwia publikowanie tylko aplikacji. Poniższa tabela zawiera podsumowanie tych różnic:  
  
|Typ adresu URL|Opis|  
|--------------|-----------------|  
|ftp://|Możesz opublikować [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji przy użyciu tego protokołu.|  
|http://|Możesz zainstalować [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji przy użyciu tego protokołu.|  
|https://|Możesz zainstalować [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji przy użyciu tego protokołu.|  
|file://|Możesz zainstalować [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji przy użyciu tego protokołu.|  
  
## <a name="windows-xp-sp2-windows-firewall"></a>Windows XP z dodatkiem SP2: Zapora systemu Windows  
 Domyślnie Windows XP z dodatkiem SP2, powoduje włączenie zapory Windows. Jeśli tworzysz aplikację na komputerze, na którym zainstalowano Windows XP zainstalowane jesteś nadal można opublikować, a następnie uruchom [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji z lokalnego serwera, na którym działa program IIS. Jednak nie można uzyskać dostęp do tego serwera, na którym działa program IIS z innego komputera, chyba że Otwórz zaporę Windows. Aby uzyskać instrukcje dotyczące zarządzania zaporą Windows, zapoznaj się z pomocą Windows.  
  
## <a name="windows-server-enable-frontpage-server-extensions"></a>Windows Server: Włączanie rozszerzenia serwera FrontPage  
 Rozszerzenia serwera FrontPage firmy Microsoft jest wymagana do publikowania aplikacji na serwerze sieci Windows Web, która korzysta z protokołu HTTP.  
  
 Domyślnie system Windows Server nie ma zainstalowanych rozszerzeń serwera FrontPage. Jeśli chcesz używać [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] do publikowania na serwerze sieci Web usługi Windows Server, który korzysta z protokołu HTTP przy użyciu rozszerzenia serwera FrontPage, należy zainstalować rozszerzenia serwera FrontPage najpierw. Instalację można wykonać za pomocą narzędzia administracyjnego Zarządzanie serwerem w systemie Windows Server.  
  
## <a name="windows-server-locked-down-content-types"></a>Windows Server: Typy zawartości w trybie blokady  
 Usługi IIS na [!INCLUDE[WinXPSvr](../includes/winxpsvr-md.md)] zablokuje wszystkich typów plików, z wyjątkiem niektórych znanych typów zawartości (na przykład htm, HTML, txt i tak dalej). Aby włączyć wdrażanie [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji za pomocą tego serwera, musisz zmienić ustawienia programu IIS, aby zezwolić na pobieranie plików typu .application, manifest i wszelkie inne niestandardowe typy plików używanych przez aplikację.  
  
 W przypadku wdrożenia przy użyciu serwera usług IIS, uruchom inetmgr.exe, a następnie dodaj nowe typy plików dla domyślnej strony sieci Web:  
  
- .Application i .manifest rozszerzeń typu MIME powinien być "application/x-ms aplikacji." Dla pozostałych typów plików w typie MIME powinien być "application/octet-stream".  
  
- W przypadku utworzenia typu MIME rozszerzenia "*" i typ MIME "application/octet-stream" umożliwi plików odblokowany typu do pobrania. (Jednak zablokowane plików, których nie można pobrać typów, takie jak aspx i .asmx).  
  
  Aby uzyskać szczegółowe instrukcje dotyczące konfigurowania typy MIME w systemie Windows Server, zapoznaj się do artykułu bazy wiedzy Microsoft Knowledge Base KB326965, "Usług IIS 6.0 jest nie obsługiwać nieznane typy MIME" w [ http://support.microsoft.com/default.aspx?scid=kb; en-us; 326965](http://support.microsoft.com/default.aspx?scid=kb;en-us;326965).  
  
## <a name="content-type-mappings"></a>Mapowanie typu zawartości  
 Podczas publikowania, za pośrednictwem protokołu HTTP, typu zawartości (znany także jako typ MIME) dla pliku .application powinien być "application/x-ms aplikacji." Jeśli masz [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] zainstalowane na serwerze, to zostanie ustawiona dla Ciebie automatycznie. Jeśli to nie jest zainstalowany, a następnie należy utworzyć skojarzenia typu MIME dla [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] katalog główny aplikacji (lub cały serwer).  
  
 W przypadku wdrożenia przy użyciu serwera usług IIS, uruchom inetmgr.exe, a następnie dodaj nowy typ zawartości "application/x-ms-aplikacji" dla rozszerzenie .application.  
  
## <a name="http-compression-issues"></a>Problemy z kompresji HTTP  
 Za pomocą [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], można wykonać pliki do pobrania, które używają kompresji HTTP, technologia serwera sieci Web, która za pomocą algorytmu GZIP kompresowania strumienia danych przed wysłaniem strumienia do klienta. Klient — w tym przypadku [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]— dekompresuje strumienia przed odczytaniem plików.  
  
 Jeśli używasz usług IIS, można łatwo włączyć kompresję HTTP. Jednak włączenie kompresji HTTP obejmującej go jest włączona tylko dla niektórych typów plików — to znaczy, pliki HTML i tekst. Aby włączyć kompresję dla zestawów (.dll), XML (.xml), manifesty wdrożenia (.application) i manifesty aplikacji (manifest), należy dodać następujące typy plików do listy typów dla usługi IIS mają skompresować. Do momentu dodania typy plików do wdrożenia, będą kompresowane tylko tekst i pliki HTML.  
  
 Aby uzyskać szczegółowe instrukcje dotyczące usług IIS, zobacz [sposobu określania typów dokumentów dodatkowe kompresji HTTP](http://go.microsoft.com/fwlink/?LinkId=178459).  
  
## <a name="see-also"></a>Zobacz też  
 [Rozwiązywanie problemów z wdrożeniami ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)   
 [Wybieranie strategii wdrażania ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [Wstępnie wymagane składniki wdrażania aplikacji](../deployment/application-deployment-prerequisites.md)

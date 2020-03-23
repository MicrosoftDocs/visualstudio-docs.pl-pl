---
title: Instalowanie i używanie za zaporą lub serwerem proxy
description: Przejrzyj adresy URL, porty i protokoły domeny, które możesz dodać do listy dozwolonych lub otworzyć, jeśli organizacja używa zapory lub serwera proxy
ms.date: 02/01/2020
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
- list of domains, locations, URLs
ms.assetid: ''
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 44ffc778d398c2f9a1cfaf026d2364ee1dc27f9b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79303009"
---
# <a name="install-and-use-visual-studio-and-azure-services-behind-a-firewall-or-proxy-server"></a>Instalowanie i używanie programów Visual Studio i usług Platformy Azure za zaporą lub serwerem proxy

Jeśli ty lub Twoja organizacja używa środków bezpieczeństwa, takich jak zapora lub serwer proxy, istnieją adresy URL domen, które można dodać do "listy dozwolonych" oraz porty i protokoły, które można otworzyć, aby uzyskać najlepsze wrażenia podczas instalacji i używania Visual Studio i usługi platformy Azure.

* **[Zainstaluj program Visual Studio:](#install-visual-studio)** Te tabele zawierają adresy URL domeny, które należy dodać do listy dozwolonych, dzięki czemu masz dostęp do wszystkich składników i obciążeń, które chcesz.

* **[Użyj programu Visual Studio i usług platformy Azure:](#use-visual-studio-and-azure-services)** Ta tabela zawiera adresy URL domeny, aby dodać do listy dozwolonych i porty i protokoły, aby otworzyć, dzięki czemu masz dostęp do wszystkich funkcji i usług, które chcesz.

> [!NOTE]
> Ten artykuł został napisany dla programu Visual Studio w systemie Windows, ale niektóre informacje dotyczą również [instalowania programu Visual Studio dla komputerów Mac](/visualstudio/mac/install-behind-a-firewall-or-proxy-server) za zaporą lub serwerem proxy.

## <a name="install-visual-studio"></a>Instalacja programu Visual Studio

### <a name="urls-to-add-to-an-allow-list"></a>Adresy URL do dodania do listy dozwolonych

Ponieważ Instalator programu Visual Studio pobiera pliki z różnych domen i ich serwerów pobierania, oto adresy URL domen, które można dodać do listy dozwolonych jako zaufane w interfejsie użytkownika lub w skryptach wdrażania.

#### <a name="microsoft-domains"></a>Domeny firmy Microsoft

| Domain | Przeznaczenie |
| - | - |
| go.microsoft.com | Rozpoznawanie adresu URL instalatora |
| aka.ms | Rozpoznawanie adresu URL instalatora |
| download.visualstudio.microsoft.com | Lokalizacja pobierania pakietów instalacyjnych |
| download.microsoft.com | Lokalizacja pobierania pakietów instalacyjnych |
| download.visualstudio.com | Lokalizacja pobierania pakietów instalacyjnych |
| dl.xamarin.com | Lokalizacja pobierania pakietów instalacyjnych |
| xamarin-downloads.azureedge.net | Android SDK pakiety pobieranie lokalizacji listy |
| marketplace.visualstudio.com | Lokalizacja pobierania rozszerzeń programu Visual Studio |
| \*gallerycdn.vsassets.io .  | Lokalizacja pobierania rozszerzeń programu Visual Studio |
| visualstudio.microsoft.com | Lokalizacja dokumentacji |
| docs.microsoft.com | Lokalizacja dokumentacji |
| msdn.microsoft.com | Lokalizacja dokumentacji |
| www\.microsoft.com | Lokalizacja dokumentacji |
| \*.windows.net | Lokalizacja logowania |
| \*.microsoftonline.com | Lokalizacja logowania |
| \*.live.com | Lokalizacja logowania |
| | |

#### <a name="non-microsoft-domains"></a>Domeny inne niż Microsoft

| Domain | Instaluje te obciążenia |
| - | - |
| archive.apache.org | Rozwój urządzeń mobilnych z JavaScript (Cordova) |
| cocos2d-x.org | Tworzenie gier z C++ (Cocos) |
| download.epicgames.com | Tworzenie gier z C++ (Unreal Engine) |
| download.oracle.com | Rozwój urządzeń mobilnych z JavaScript (Java SDK) <br /><br />Rozwój urządzeń mobilnych z programem .NET (Java SDK) |
| download.unity3d.com | Tworzenie gry z Unity (Unity) |
| netstorage.unity3d.com | Tworzenie gry z Unity (Unity) |
| dl.google.com | Rozwój urządzeń mobilnych z JavaScript (Android SDK i NDK, Emulator) <br /><br />Rozwój urządzeń mobilnych z .NET (Android SDK i NDK, emulator) |
| www\.incredibuild.com | Tworzenie gier z C++ (IncrediBuild) |
| incredibuildvs2017i.azureedge.net | Tworzenie gier z C++ (IncrediBuild) |
| www\.python.org | Rozwój Pythona (Python) <br /><br />Analityka danych i aplikacje analityczne (Python) |
| developerservices2.apple.com | Inicjowanie obsługi administracyjnej systemu Xamarin.iOS |
| developer.apple.com | Inicjowanie obsługi administracyjnej systemu Xamarin.iOS |
| appstoreconnect.apple.com | Inicjowanie obsługi administracyjnej systemu Xamarin.iOS |
| idmsa.apple.com | Inicjowanie obsługi administracyjnej systemu Xamarin.iOS |
| | |

## <a name="use-visual-studio-and-azure-services"></a>Korzystanie z programu Visual Studio i usług platformy Azure

### <a name="urls-to-add-to-an-allow-list-and-ports-and-protocols-to-open"></a>Adresy URL do dodania do listy dozwolonych oraz portów i protokołów do otwarcia

Aby upewnić się, że masz dostęp do wszystkiego, co chcesz, gdy używasz programu Visual Studio lub usługi Azure za zaporą lub serwerem proxy, oto adresy URL, które należy dodać do listy dozwolonych oraz porty i protokoły, które można otworzyć.

| Usługa lub scenariusz | Punkt końcowy DNS | Protocol (Protokół)<br/>/Port | Opis |
| - | - | -: | - | - |
| Adres URL<br>rozwiązanie | go.microsoft.com<br><br>aka.ms | | Służy do skracania adresów URL, które następnie rozwiązują się z dłuższymi adresami URL |
| Strona początkowa | vsstartpage.blob.core.windows.net | 443 | Służy do wyświetlania aktualności deweloperów wyświetlanych na stronie początkowej (tylko visual studio 2017) |
| Docelowe<br> Powiadomienie <br>Usługa | targetednotifications-tm.trafficmanager.net <br><br>www.research.net | 443<br><br>443 | Służy do filtrowania globalnej listy powiadomień do listy, która ma zastosowanie tylko do określonych typów maszyn/scenariuszy użycia |
| Wewnętrzny <br>sprawdzanie aktualizacji | marketplace.visualstudio.com<br><br>&#42;.windows.net <br>witryna &#42;.microsoftonline.com <br>&#42;.live.com | 443 | Służy do dostarczania powiadomień, gdy zainstalowane rozszerzenie ma dostępną aktualizację <br><br> Używane jako miejsce logowania |
| Projekt SI <br>Integracja | az861674.vo.msecnd.net | 443<br> | Służy do konfigurowania nowych projektów do wysyłania danych użycia do zarejestrowanego konta usługi Application Insights |
| Soczewka kodu | codelensprodscus1su0.app.<br>codelens.visualstudio.com | 443 | Służy do dostarczania informacji w edytorze o tym, kiedy plik był ostatnio aktualizowany, oś czasu zmian, elementy robocze, które zmiany są skojarzone z, autorzy i więcej |
| Eksperymentalne <br>funkcja włączania | visualstudio-devdiv-c2s.msedge.net | 80 | Służy do aktywowania nowych eksperymentalnych funkcji lub zmian funkcji |
| Identyfikator "plakietka" <br>(nazwa użytkownika i awatar)<br>i <br>Ustawienia roamingu | app.vssps.visualstudio.com <br><br>app.vsspsext.visualstudio.com<br><br>app.vssps.visualstudio.com<br><br> ns-sb2-prod-ch1-002.cloudapp.net <br><br>az700632.vo.msecnd.net<br><br>api.vstsusers.visualstudio.com/profiles/* | 443 | Służy do wyświetlania nazwy użytkownika i awatara w IDE <br><br> Służy do upewnienia się, że zmiany ustawień przemieszczają się z jednego komputera na drugi |
| Ustawienia zdalne | az700632.vo.msecnd.net | 443 | Służy do wyłączania rozszerzeń, o których wiadomo, że powodują problemy w programie Visual Studio |
| Narzędzia systemu Windows | developer.microsoft.com <br><br>dev.windows.com  <br><br>appdev.microsoft.com | https/443 | Używane w scenariuszach ze sklepu z aplikacjami systemu Windows |
| Schemat JSON <br>Odnajdywanie <br><br>Schemat JSON <br>Definicja<br><br>Schemat JSON <br>Wsparcie dla <br>Zasoby platformy Azure | json.schemastore.org <br>schemastoreorg.azurewebsites.net<br><br>json-schema.org<br><br>schema.management.azure.com | http/80<br>https/443<br><br>http/80<br><br>https/443 | Służy do odnajdowania i pobierania schematów JSON, których użytkownik może używać podczas edytowania dokumentów JSON <br><br>Służy do uzyskiwania schematu metaweryfikacji dla JSON<br><br>Służy do uzyskiwania bieżącego schematu szablonów wdrażania usługi Azure Resource Manager |
| Pakiet NPM <br>odnajdywanie | Skimdb.npmjs.com <br><br>Registry.npmjs.org <br><br>Api.npms.io | https/443<br><br>http/80 &<br> https/443<br>https/443 | Wymagane do wyszukiwania pakietów NPM i używane do instalacji pakietu skryptów po stronie klienta w projektach internetowych |
| Pakiet Bower<br> ikony<br><br>Pakiet Bower <br>search | Bower.io <br><br>bowercache.azurewebsites.net <br>go.microsoft.com <br>Registry.bower.io | http/80<br><br>https/443<br>http/80<br>https/443 | Udostępnia domyślną ikonę pakietu altana  <br><br>Umożliwia wyszukiwanie pakietów Bower |
| NuGet<br><br>Pakiet NuGet<br> odnajdywanie | api.nuget.org <br>www.nuget.org <br>nuget.org <br>azuresearch-usnc.nuget.org <br>azuresearch-ussc.nuget.org <br>licenses.nuget.org <br>nuget.cdn.azure.cn <br>azuresearch-ea.nuget.org <br>azuresearch-sea.nuget.org <br><br>crl3.digicert.com <br>crl4.digicert.com <br>ocsp.digicert.com <br>cacerts.digicert.com | https/443<br><br>http/80 &<br>https/443<br> | Służy do weryfikacji podpisanych pakietów NuGet.<br><br>Wymagane do wyszukiwania pakietów i wersji NuGet |
| Informacje o repozytorium GitHub | api.github.com | https/443 | Wymagane do uzyskania dodatkowych informacji o pakietach bower |
| Web Linters | Eslint.org<br><br>www.Bing.com <br><br>www.coffeelint.org | http/80 | |
| Cookiecutter (wychyłka cookiecut<br>Szablon Eksploratora<br>odnajdywanie <br><br>Cookiecutter (wychyłka cookiecut <br>Projekt Eksploratora<br> tworzenie | api.github.com <br>raw.githubusercontent.com <br>go.microsoft.com<br><br>pypi.org <br> pypi.python.org | https/443<br> | Służy do odkrywania szablonów online z naszego zalecanego pliku danych i z repozytoriów GitHub <br><br>Służy do tworzenia projektu na podstawie szablonu cookiecutter, który wymaga jednorazowej instalacji na żądanie pakietu Pythona typu cookiecutter z indeksu pakietów Języka Python (PyPI) |
| Pakiet Pythona <br>odnajdywanie<br><br>Pakiet Pythona <br>zarządzanie<br><br>Nowa <br>Python <br> projekt <br>szablonów | pypi.org<br> <br>pypi.python.org <br>bootstrap.pypa.io<br><br>go.microsoft.com | https/443 | Umożliwia wyszukiwanie pakietów pipsów<br><br>Służy do automatycznego instalowania pip, jeśli jej brakuje <br><br>Służy do rozwiązywania następujących nowych szablonów projektów języka Python do adresów URL szablonów cookiecutter:<br> - Projekt klasyfikatora<br>- Projekt klastrowania <br> - Projekt regresji <br> - PyGame za pomocą PyKinect <br> - Projekt Pyvot |
| Sieć Web pakietu Office <br>dodatek <br> Manifest <br>Weryfikacja <br>Usługa | verificationservice.osi.office.net | https/443 | Służy do sprawdzania poprawności manifestów dla dodatków sieci Web pakietu Office |
| Program SharePoint i <br>Dodatki pakietu Office | sharepoint.com<br> office365.com<br> microsoftonline.com <br> outlook.com | https/443 | Używane do publikowania i testowania dodatków programu SharePoint i pakietu Office w usłudze SharePoint Online i usłudze Office 365 |
| Menedżer przepływu pracy <br>Usługa testowa<br> Host | | http/12292 | Reguła zapory utworzona automatycznie do testowania dodatków programu SharePoint za pomocą przepływów pracy |
| Automatyczne zbierane <br>statystyki niezawodności <br>i inne <br>Obsługa klienta <br>Programy poprawy (CEIP)<br> dla platformy Azure SDK i <br>dla narzędzi SQL <br><br> | vortex.data.microsoft.com<br> <br>dc.services.visualstudio.com | https/443 | Służy do wysyłania statystyk niezawodności (dane awarii/zawieszenia) od użytkownika do firmy Microsoft. Rzeczywiste zrzuty awarii/zawieszenia będą nadal przekazywane, jeśli jest włączone raportowanie błędów systemu Windows; tylko informacje statystyczne zostaną pominięte; <br>Służy do ujawniania wzorców użycia anonimowych dla rozszerzenia zestawu SDK narzędzi azure do programu Visual Studio oraz wzorców użycia dla narzędzi SQL do programu Visual Studio |
| Visual Studio <br> Obsługa klienta <br>Program poprawy (CEIP) <br><br>Plik PerfWatson.exe | vortex.data.microsoft.com<br>dc.services.visualstudio.com<br>visualstudio-devdiv-c2s.msedge.net<br>az667904.vo.msecnd.net <br>scus-breeziest-in.cloudapp.net<br> | https/443 | Służy do zbierania anonimowych wzorców użycia i dzienników błędów <br><br>Służy do śledzenia problemów z zawieszaniem interfejsu użytkownika |
| Tworzenie i<br>Zarządzanie <br>Zasoby platformy Azure | management.azure.com <br>management.core.windows.net | https/443 | Służy do tworzenia witryn sieci Web platformy Azure lub innych zasobów do obsługi publikowania aplikacji sieci Web, funkcji platformy Azure lub WebJobs |
| Zaktualizowane narzędzia publikowania w internecie <br>kontrole i rozszerzenie <br>zalecenia | marketplace.visualstudio.com | https/443 | Służy do sprawdzania dostępności zaktualizowanych narzędzi publikowania. Jeśli jest wyłączona, potencjalne zalecane rozszerzenie do publikowania w sieci web może nie być wyświetlane |
| Zaktualizowany zasób platformy Azure <br>Informacje o punkcie końcowym tworzenia | \*.blob.core.windows.net | https/443 | Służy do aktualizowania punktów końcowych używanych do tworzenia zasobów platformy Azure dla niektórych usług platformy Azure. Jeśli jest wyłączona, zamiast tego używane są ostatnio pobrane lub wbudowane lokalizacje punktów końcowych |
| Zdalne debugowanie i <br>Zdalne profilowanie <br>Witryny sieci Web platformy Azure | &#42;.cloudapp.net <br> &#42;.azurewebsites.net | 4022 | Służy do dołączania zdalnego debugera do witryn sieci Web platformy Azure. Jeśli opcja jest wyłączona, dołączanie zdalnego debugera do witryn sieci Web platformy Azure nie będzie działać |
| Usługa Active Directory <br>Graph | graph.windows.net | https/443 | Służy do inicjowania obsługi administracyjnej nowych aplikacji usługi Azure Active Directory. Używany również przez dostawcę usług połączonych z usługą Office 365 MSGraph |
| Azure Functions <br>Aktualizacja interfejsu wiersza polecenia <br>Zaznacz | functionscdn.azureedge.net | https/443 | Służy do sprawdzania zaktualizowanych wersji interfejsu wiersza polecenia usług Azure Functions. Jeśli ta opcja jest wyłączona, zamiast tego zostanie użyta kopia buforowana (lub kopia przenoszona przez składnik Usługi Azure Functions) interfejsu wiersza polecenia |
| Cordova | npmjs.org<br>gradle.org | http/80 &<br/>https/443 | HTTP jest używany do pobierania Gradle podczas kompilacji; Https służy do włączania wtyczek Cordova w projektach |
| Eksplorator chmury | 1. &#60;&#62; punktowy klastra <br>Service Fabric <br>2. &#60;&#62; punktu końcowego zarządzania<br>Ogólny exp chmury <br>3.&#62; punktu końcowego wykresu &#60;<br>Ogólny exp chmury<br>4. &#60;&#62; punktu końcowego konta magazynu<br>Węzły magazynu <br>5. &#60;adresy URL portalu Azure&#62;<br>Ogólny exp chmury <br>6. &#60;punkty końcowe magazynu kluczy&#62; <br>Węzły maszyn wirtualnych usługi Azure Resource Manager<br>7. &#60;PublicIPAddressOfCluster&#62;<br>Zdalne debugowanie sieci szkieletowej usług i ślady ETW | <br>1.https/19080<br>2. https/443<br>3. https/443<br>4. https/443<br>5. https/443<br>6. https/443<br>7.tcp/dynamiczny | 1. Przykład: test12.eastus.cloudapp.com<br>2. Pobiera subskrypcje i pobiera/zarządza zasobami platformy Azure<br>3. Pobiera subskrypcje usługi Azure Stack<br>4. Zarządza zasobami pamięci masowej (np. mystorageaccount.blob.core.windows.net)<br>5. Opcja menu kontekstowego "Otwórz w portalu" (otwiera zasób w witrynie Azure portal)<br>6. Tworzy i używa magazynów kluczy do debugowania maszyn wirtualnych (przykład: myvault.vault.azure.net) <br><br>7. Dynamicznie przydziela blok portów na podstawie liczby węzłów w klastrze i dostępnych portów. <br><br>Blok portu spróbuje uzyskać trzykrotnie więcej węzłów przy co najmniej 10 portach.<br><br>W przypadku śledzenia przesyłania strumieniowego podejmowana jest próba uzyskania bloku portu z 810. Jeśli którykolwiek z tego bloku portu jest już używany, a następnie podejmowana jest próba uzyskania następnego bloku i tak dalej. (To moduł równoważenia obciążenia jest pusty, a następnie porty z 810 są najprawdopodobniej używane) <br><br>Podobnie do debugowania, cztery zestawy bloków portów są zarezerwowane: <br>- connectorPort: 30398, <br>- forwarderPort: 31398, <br>- spedycarzPortx86: 31399,<br>- plikUploadPort: 32398<br> |
| Cloud Services | 1. PROW<br><br>2. core.windows.net <br><br>3. management.azure.com<br> management.core.windows.net <br><br>4. &#42;.blob.core.windows.net <br>&#42;.queue.core.windows.net<br>&#42;.table.core.windows.net <br><br>5. portal.azure.com <br><br>6. usługa &#60;użytkownika w chmurze&#62;.cloudapp.net <br> &#60;region maszyny wirtualnej&#62;.&#60;użytkownika&#62;.azure.com | 1. rdp/3389 <br><br> 2. https/443 <br><br> 3. https/443 <br><br> 4. https/443 <br><br> 5. https/443 <br><br>6. tcp <br>a) 30398 <br>b) 30400 <br>c) 31398 <br>d) 31400 <br>e) 32398 <br>f) 32400 | 1. Maszyna wirtualna usług pulpitu zdalnego do usługi w chmurze <br><br> 2. Składnik konta magazynu konfiguracji diagnostyki prywatnej <br><br> 3. Portal platformy Azure <br><br> 4. Eksplorator serwerów — usługa Azure Storage &#42; jest kontem magazynu o nazwie klient  <br><br> 5. Linki do otwierania portalu &#47; Pobierz certyfikat subskrypcji &#47; plik ustawień publikowania <br><br>6. a) Złącze portu lokalnego do zdalnego debugowania usługi w chmurze i maszyny wirtualnej<br> 6. b) Złącze publicznego portu do zdalnego debugowania usługi w chmurze i maszyny wirtualnej <br> 6. c) Port lokalny przesyłania dalej do zdalnego debugowania usługi w chmurze i maszyny wirtualnej <br> 6. d) Port publiczny przesyłania dalej do zdalnego debugowania usługi w chmurze i maszyny wirtualnej  <br> 6. e) Port lokalny przesyłający pliki do zdalnego debugowania usługi w chmurze i maszyny wirtualnej <br> 6. f) Port publiczny przesyłający pliki do zdalnego debugowania usługi w chmurze i maszyny wirtualnej |
| Service Fabric | 1. <br>Ocs. Microsoft.com<br>aka.ms <br>go.microsoft.com <br><br>2. <br>vssftools.blob.core.windows.net <br>Vault.azure.com <br>Portal.azure.com <br><br> 3. &#42; vault.azure.net<br><br> 4. <br>app.vsaex.visualstudio.com<br>&#42; .vsspsext.visualstudio.com<br>clouds.vsrm.visualstudio.com <br>clouds.visualstudio.com<br>app.vssps.visualstudio.com <br>&#42; .visualstudio.com | https/443 | 1. Dokumentacja <br><br> 2. Tworzenie funkcji klastra <br><br>3. &#42; jest nazwa magazynu kluczy platformy Azure (przykład:- test11220180112110108.vault.azure.net  <br><br>  4. &#42; jest dynamiczny (przykład: vsspsextprodch1su1.vsspsext.visualstudio.com) |
| Snapshot <br>Debuger | 1. go.microsoft.com <br>2. management.azure.com <br> 3. &#42;.azurewebsites.net <br> 4. &#42;.scm.azurewebsites.net<br>5. api.nuget.org/v3/index.json <br>6. Zdalna usługa /adres IP serwerów/ FQDN | 1. https/443 <br>2. https/443  <br>3. http/80 <br>4. https/443 <br>5. https/443 <br>6. Zgoda/<br> 4022 (zależna od wersji programu Visual Studio) | 1. Zapytanie .json plik dla rozmiaru jednostki SKU usługi aplikacji <br>2. Różne wywołania usługi Azure RM <br>3. Rozgrzewka witryny za pośrednictwem  <br>4. Docelowy punkt końcowy Usługi aplikacji Klienta Kudu <br>5. Wersja rozszerzenia witryny kwerendy opublikowana w nuget.org <br>6. [Zdalne debugowanie](../debugger/remote-debugging.md) |
| Azure Stream Analytics <br><br>HDInsight | Management.azure.com | https/443 | Służy do wyświetlania, przesyłania, uruchamiania i zarządzania zadaniami ASA <br><br> Służy do przeglądania klastrów HDI oraz przesyłania, diagnozowania i debugowania zadań HDI |
| Azure Data Lake | &#42;.azuredatalakestore.net <br>&#42;.azuredatalakeanalytics.net | https/443 | Służy do kompilowania, przesyłania, wyświetlania, diagnozowania i debugowania zadań; używane do przeglądania plików ADLS; służy do przesyłania i pobierania plików |
| Usługi pakowania | [konto].visualstudio.com <br/> [konto]. \*visualstudio.com .visualstudio.com <br/> \*.blob.core.windows.net <br/> registry.npmjs.org </br> nodejs.org <br/> dist.nuget.org <br/> nuget.org | https/443 | .npmjs.org, \* \*.nuget.org i \*.nodejs.org są wymagane tylko dla niektórych scenariuszy zadań kompilacji (na przykład: Instalator narzędzi NuGet, Instalator narzędzi węzłów) lub jeśli zamierzasz używać publicznych nadrzędnych danych z źródłami danych. Pozostałe trzy domeny są wymagane dla podstawowej funkcjonalności usługi Pakowanie. |
| Usługa Azure DevOps Services | \*vsassets.io .vsassets.io <br/> static2.sharepointonline.com <br/> dev.azure.com | | Używane do łączenia się z usługami DevOps platformy Azure |
| Społeczność deweloperów | sendvsfeedback2.azurewebsites.net/api | https/443 | Używane do wywoływania interfejsów API narzędzia opinii społeczności programistów (moje problemy, wyszukiwanie, głosowanie, komentowanie, przesyłanie, przesyłanie, życiorysy) |
| Intellicode | \*intellicode.vsengsaas.visualstudio.com .intellicode.vsengsaas.visualstudio.com | https/443 | Używane do wywoływania interfejsów API intellicode |
| Live Share | \*liveshare.vsengsaas.visualstudio.com .| https/443 | Używane do wywoływania interfejsów API udostępniania na żywo |
| Visual Studio Online | \*online.visualstudio.com .online.visualstudio.com | https/443 | Używane do wywoływania interfejsów API usługi Visual Studio Online |
| Automatyczne pozyskiwanie typów JavaScript | registry.npmjs.org | https/443 | Służy do instalowania definicji typów TypeScript w celu zapewnienia intellisense dla popularnych bibliotek JavaScript |
| Usługa licencjonowania subskrypcji programu Visual Studio | app.vssps.visualstudio.com/apis/<br/>Licencjonowanie/Prawa klienta | https/443 | Licencjonowanie aktywacji online |
| Debuger | 1. <br>vsdebugger.blob.core.windows.net <br>vsdebugger.azureedge.net <br><br>2. <br>download.visualstudio.com/\*/<br/>onecore.msvsmon. \*.zip (plik błyskawiczny)<br><br> 3. referencesource.microsoft.com/symbols <br><br> 4. <br>symbols.nuget.org/download/symbols<br><br> 5. visualstudio.com<br><br>6. msdl.microsoft.com/download/symbols | https/443 | 1. <br>Służy do pobierania bitów debugera do debugowania .NET Core na unix / macOS przez SSH <br><br>2. <br>Służy do pobierania bitów debugera do zdalnego debugowania kontenera platformy Windows<br><br> 3. Używany do stepping źródła .NET framework <br><br> 4. <br>(Jeśli użytkownik wyrazi na to zgodę) Służy do pobierania symboli opublikowanych na serwerze nuget.org symboli.<br><br> 5. (Jeśli użytkownik zdecyduje się) Używany do pobierania symboli MS i plików binarnych, może być również potrzebne do debugowania kodu zarządzanego w zrzutach |
| Visual Studio Online| \*online.visualstudio.com .online.visualstudio.com | https/443 | Używane do wywoływania interfejsów API usługi Visual Studio Online |
| Publikowanie aplikacji systemu Android platformy Xamarin | \*googleapis.com .googleapis.com <br/> play.google.com <br/>accounts.google.com | https/443 | Służy do interakcji z usługą Sklepu Google Play do publikowania/przekazywania aplikacji systemu Android platformy Xamarin bezpośrednio z programu Visual Studio. |
| Azure Container Registry | *.azurecr.io | https/443 | Rejestry kontenerów dostępu hostowane na platformie Azure w celu konfiguracji potoków CICD |
| | | | |

## <a name="troubleshoot-network-related-errors"></a>Rozwiązywanie problemów z błędami związanymi z siecią

Czasami podczas instalowania lub używania programu Visual Studio za zaporą lub serwerem proxy można uruchomić błędy związane z siecią lub serwerem proxy. Aby uzyskać więcej informacji na temat rozwiązań dla takich komunikatów o [błędach, zobacz rozwiązywanie problemów z błędami związanymi z siecią podczas instalowania lub używania](troubleshooting-network-related-errors-in-visual-studio.md) strony programu Visual Studio.

## <a name="get-support"></a>Uzyskiwanie pomocy technicznej

Oferujemy opcję pomocy technicznej [**na czacie na żywo**](https://visualstudio.microsoft.com/vs/support/#talktous) (tylko w języku angielskim) w przypadku problemów związanych z instalacją.

Oto kilka innych opcji pomocy technicznej:

* Zgłoś nam problemy z produktem za pomocą narzędzia [Zgłoś problem,](../ide/how-to-report-a-problem-with-visual-studio.md) które pojawia się zarówno w Instalatorze programu Visual Studio, jak i w środowiskach IDE programu Visual Studio.
* Zasugeruj funkcję, śledź problemy z produktem i znajdź odpowiedzi w [społeczności deweloperów programu Visual Studio](https://developercommunity.visualstudio.com/).
* Użyj swojego konta [GitHub,](https://github.com/) aby porozmawiać z nami i innymi deweloperami programu Visual Studio w [konwersacji programu Visual Studio w społeczności Gitter.](https://gitter.im/Microsoft/VisualStudio)

## <a name="see-also"></a>Zobacz też

* [Wymagania dotyczące łączności dla rozszerzenia Live Share](/visualstudio/liveshare/reference/connectivity/)
* [Tworzenie instalacji sieciowej programu Visual Studio](create-a-network-installation-of-visual-studio.md)
* [Rozwiązywanie problemów z błędami związanymi z siecią w programie Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md)
* [Przewodnik dla administratora programu Visual Studio](visual-studio-administrator-guide.md)
* [Instalowanie za zaporą lub serwerem proxy (Visual Studio dla komputerów Mac)](/visualstudio/mac/install-behind-a-firewall-or-proxy-server)

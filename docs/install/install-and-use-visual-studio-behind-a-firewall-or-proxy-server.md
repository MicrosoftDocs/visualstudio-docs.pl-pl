---
title: Instalowanie i używanie za zaporą lub serwerem proxy
description: Przejrzyj adresy URL domeny, porty i protokoły, które możesz chcieć dodać do listy dozwolonych, lub Otwórz, jeśli Twoja organizacja używa zapory lub serwera proxy
ms.date: 05/22/2019
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
ms.openlocfilehash: d74cb5b1594c0e4d347e2f8a4e1924cf68d64eed
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114937"
---
# <a name="install-and-use-visual-studio-and-azure-services-behind-a-firewall-or-proxy-server"></a>Instalowanie i używanie programu Visual Studio i usług platformy Azure za serwerem zapory lub serwera proxy

Jeśli ty lub Twoja organizacja korzysta z środków zabezpieczeń, takich jak zapora lub serwer proxy, istnieją adresy URL domeny, które można dodać do listy "Lista dozwolonych" oraz portów i protokołów, które mogą być otwierane, aby zapewnić najlepsze środowisko podczas instalowania i używania  Visual Studio i usługi platformy Azure.

* **[Zainstaluj program Visual Studio](#install-visual-studio)** : te tabele zawierają adresy URL domeny, które mają zostać dodane do listy dozwolonych, dzięki czemu masz dostęp do wszystkich składników i obciążeń, które chcesz.

* **[Użyj programu Visual Studio i usług platformy Azure](#use-visual-studio-and-azure-services)** : Ta tabela zawiera adresy URL domeny, które mają zostać dodane do listy dozwolonych, oraz porty i protokoły do otwarcia, aby mieć dostęp do wszystkich żądanych funkcji i usług.

> [!NOTE]
> W tym artykule został napisany dla programu Visual Studio w Windows, ale ma również zastosowanie do niektórych informacji [instalowania programu Visual Studio dla komputerów Mac](/visualstudio/mac/install-behind-a-firewall-or-proxy-server) za serwerem zapory lub serwera proxy.

## <a name="install-visual-studio"></a>Zainstaluj program Visual Studio

### <a name="urls-to-add-to-an-allow-list"></a>Adresy URL do dodania do listy dozwolonych

Ponieważ Instalator programu Visual Studio pobiera pliki z różnych domen i ich serwerów pobierania, poniżej znajdują się adresy URL domeny, które mogą zostać dodane do listy dozwolonych jako zaufane w interfejsie użytkownika lub w skryptach wdrożenia.

#### <a name="microsoft-domains"></a>Microsoft domains

| Domena | Cel |
| - | - |
| go.microsoft.com | Rozpoznawanie adresu URL instalacji |
| aka.MS | Rozpoznawanie adresu URL instalacji |
| download.visualstudio.microsoft.com | Konfigurowanie lokalizacji pobierania pakietów |
| download.microsoft.com | Konfigurowanie lokalizacji pobierania pakietów |
| download.visualstudio.com | Konfigurowanie lokalizacji pobierania pakietów |
| dl.xamarin.com | Konfigurowanie lokalizacji pobierania pakietów |
| xamarin-downloads.azureedge.net | Lokalizacja listy pobierania pakietów Android SDK |
| marketplace.visualstudio.com | Lokalizacja pobierania rozszerzenia programu Visual Studio |
| visualstudio.microsoft.com | Lokalizacja dokumentacji |
| docs.microsoft.com | Lokalizacja dokumentacji |
| msdn.microsoft.com | Lokalizacja dokumentacji |
| www\.microsoft.com | Lokalizacja dokumentacji |
| \*. windows.net | Lokalizacja logowania |
| \*. microsoftonline.com | Lokalizacja logowania |
| \*. live.com | Lokalizacja logowania |
| | |

#### <a name="non-microsoft-domains"></a>Domeny inne niż firmy Microsoft

| Domena | Instaluje te obciążenia |
| - | - |
| archive.apache.org | Tworzenie aplikacji mobilnych za pomocą języka JavaScript (Cordova) |
| cocos2d-x.org | Tworzenie gier przy użyciu języka C++ (Cocos) |
| download.epicgames.com | Tworzenie gier przy użyciu języka C++ (Unreal Engine) |
| download.oracle.com | Tworzenie aplikacji mobilnych za pomocą języka JavaScript (zestaw SDK języka Java) <br /><br />Tworzenie aplikacji mobilnych przy użyciu platformy .NET (Java SDK) |
| download.unity3d.com | Programowanie gier za pomocą aparatu Unity (Unity) |
| netstorage.unity3d.com | Programowanie gier za pomocą aparatu Unity (Unity) |
| dl.google.com | Tworzenie aplikacji mobilnych za pomocą języka JavaScript (zestaw Android SDK i zestawu NDK, emulatora) <br /><br />Tworzenie aplikacji mobilnych przy użyciu platformy .NET (zestaw Android SDK i zestawu NDK, emulatora) |
| www\.incredibuild.com | Tworzenie gier przy użyciu języka C++ (IncrediBuild) |
| incredibuildvs2017i.azureedge.net | Tworzenie gier przy użyciu języka C++ (IncrediBuild) |
| www\.python.org | Programowanie w języku Python (Python) <br /><br />Dane aplikacji analizy i przetwarzania (Python) |
| | |

## <a name="use-visual-studio-and-azure-services"></a>Używanie programu Visual Studio i usług platformy Azure

### <a name="urls-to-add-to-an-allow-list-and-ports-and-protocols-to-open"></a>Adresy URL do dodania do listy dozwolonych i portów i protokołów do otwarcia

Aby mieć pewność, że masz dostęp do wszystkiego, czego potrzebujesz w przypadku korzystania z programu Visual Studio lub usług platformy Azure za zaporą lub serwerem proxy, poniżej znajdują się adresy URL, które należy dodać do listy dozwolonych, oraz portów i protokołów, które mogą być otwierane.

| Usługa lub scenariusza | Punkt końcowy DNS | Protokół | Port | Opis |
| - | - | - | - | - |
| {1&gt;URL&lt;1}<br>rozwiązanie | go.microsoft.com<br><br>aka.MS | | | Mające na celu skrócenie adresów URL, które następnie rozwiąż problem na dłużej adresów URL |
| Strona początkowa | vsstartpage.blob.core.windows.net | | 443 | Służy do wyświetlania wiadomości dla deweloperów wyświetlanych na stronie startowej (tylko w programie Visual Studio 2017) |
| Docelowe<br> Powiadomienia <br>NDES | targetednotifications.azurewebsites.net <br><br>www.research.net | | 80<br><br>443 | Używane do filtrowania globalną listę powiadomień do listy, która ma zastosowanie tylko do określonych rodzajów scenariusze maszyn/użycia |
| Rozszerzenie <br>sprawdzenie dostępności aktualizacji | marketplace.visualstudio.com<br><br>&#42;.windows.net <br>&#42;.microsoftonline.com <br>&#42;.live.com | | 443 | Używane do udostępniania powiadomień, gdy zainstalowane rozszerzenie ma dostępną aktualizację <br><br> Używana jako lokalizacja logowania |
| Projekt sztucznej Inteligencji <br>Integracja | az861674.vo.msecnd.net | | 443<br> | Używane do konfigurowania nowych projektów, aby wysłać dane użycia do swoje zarejestrowane konto w usłudze Application Insights |
| Funkcji Code Lens | codelensprodscus1su0.app.<br>codelens.visualstudio.com | | 443 | Można uzyskać informacje dotyczące po ostatniej aktualizacji pliku, oś czasu zmiany, elementy robocze, które są skojarzone zmiany, autorów i więcej w edytorze |
| Eksperymentalne <br>Włączanie funkcji | visualstudio-devdiv-c2s.msedge.net | | 80 | Umożliwia uaktywnianie eksperymentalne nowe funkcje i zmiany funkcji |
| Tożsamość "badge" <br>(nazwa użytkownika i awatara)<br>and <br>Ustawienia roamingu | app.vssps.visualstudio.com <br><br>app.vsspsext.visualstudio.com<br><br>app.vssps.visualstudio.com<br><br> ns-sb2-prod-ch1-002.cloudapp.net <br><br>az700632.vo.msecnd.net | | 443 | Umożliwia wyświetlenie nazwy użytkownika i awatara w środowisku IDE <br><br> Używany do sprawdzenia, czy zmiany ustawień są przekazywane z jednego komputera na inny |
| Ustawienia zdalnego | az700632.vo.msecnd.net | | 443 | Używane do wyłączania rozszerzeń, które są znane spowodować problemy w programie Visual Studio |
| Narzędzia Windows | developer.microsoft.com <br><br>dev.windows.com  <br><br>appdev.microsoft.com | https | 443 | Używany w scenariuszach magazynu aplikacji Windows |
| Schemat JSON <br>Odnajdywanie <br><br>Schemat JSON <br>Definicja<br><br>Schemat JSON <br>Obsługa programu <br>Zasoby platformy Azure | json.schemastore.org <br>schemastoreorg.azurewebsites.net<br><br>json-schema.org<br><br>schema.management.azure.com | http<br>https<br><br>http<br><br>https | 80<br>443 <br><br> 443<br><br>443 | Używana do odnajdowania i Pobierz schematów JSON, które użytkownik może użyć podczas edycji dokumentów JSON <br><br>Używany do uzyskiwania schematu sprawdzania poprawności metadanych dla formatu JSON<br><br>Używany do uzyskiwania bieżącego schematu dla szablonów wdrażania usługi Azure Resource Manager |
| Pakiet NPM <br>odnajdywanie | Skimdb.npmjs.com <br><br>Registry.npmjs.org <br><br>Api.npms.io | https<br><br>HTTP/HTTPS<br><br>https | 443<br><br>80/443<br><br>443 | Wymagane do wyszukiwania dla pakietów NPM i używane do instalacji pakietu skryptu po stronie klienta w projektach sieci web |
| Pakietów bower<br> ikony<br><br>Pakietów bower <br>search | Bower.IO <br><br>bowercache.azurewebsites.net <br>go.microsoft.com <br>Registry.bower.io | http<br><br>https<br>http<br>https | 80<br><br>443<br>80<br>443 | Udostępnia domyślną ikonę pakietu bower  <br><br>Umożliwia wyszukiwanie pakietów Bower |
| NuGet<br><br>Pakiet NuGet<br> odnajdywanie | Api.nuget.org <br>www.nuget.org <br>Nuget.org<br><br>crl3.digicert.com <br>crl4.digicert.com <br>ocsp.digicert.com <br>cacerts.digicert.com | https<br><br>HTTP/HTTPS | 443<br><br>80/443<br> | Używane do weryfikowania podpisanych pakietów NuGet.<br><br>Wymagane dla wyszukiwanie pakietów NuGet i wersje |
| Informacje o repozytorium GitHub | api.github.com | https | 443 | Wymagane w celu uzyskania dodatkowych informacji na temat pakietów bower |
| Linterów sieci Web | Eslint.org<br><br>www.Bing.com <br><br>www.coffeelint.org | http | 80 | |
| Cookiecutter<br>Eksplorator szablonu<br>odnajdywanie <br><br>Cookiecutter <br>Eksplorator projektu<br> Tworzenie | api.github.com <br>raw.githubusercontent.com <br>go.microsoft.com<br><br>pypi.org <br> pypi.python.org | https | 443<br> | Służy do odnajdywania szablonów online z naszych zalecanych kanałów informacyjnych i repozytoriów GitHub <br><br>Umożliwia tworzenie projektu z szablonu narzędzia cookiecutter, który wymaga jednorazowe instalacji na żądanie pakietu języka Python cookiecutter na podstawie indeksu pakietów języka Python (PyPI) |
| Pakiet języka Python <br>odnajdywanie<br><br>Pakiet języka Python <br>Zarządzanie przy użyciu usługi<br><br>New <br>Python <br> projekt <br>szablony | pypi.org<br> <br>pypi.python.org <br>bootstrap.pypa.io<br><br>go.microsoft.com | https | 443 | Zapewnia możliwość wyszukiwania pakiety pip<br><br>Używane do automatycznego instalowania narzędzia pip, jeżeli brakuje <br><br>Służy do rozwiązywania następujących nowych szablonów projektów języka Python do adresów URL szablonów cookiecutter:<br> -Projekt klasifikace<br>-Projekt clusteringu <br> -Projekt regrese <br> -PyGame przy użyciu PyKinect <br> -Projekt Pyvot |
| Sieci web pakietu Office <br>Dodatek <br> Manifest <br>Weryfikacja <br>NDES | verificationservice.osi.office.net | https | 443 | Służy do sprawdzania manifesty dla dodatki pakietu Office sieci web |
| Program SharePoint i <br>Dodatki pakietu Office | sharepoint.com | https | 443 | Używany do publikowania i przetestować dodatków pakietu Office do usługi SharePoint Online i SharePoint |
| Usługa Workflow Manager <br>Testowanie usługi<br> Host | | http | 12292 | Reguły zapory, która jest tworzona automatycznie do dodatków programu SharePoint przy użyciu przepływów pracy testowania |
| Zbierane automatycznie <br>statystyki niezawodności <br>i innych <br>Komfort <br>Programów poprawy jakości obsługi (klienta CEIP)<br> dla zestawu Azure SDK i <br>Aby uzyskać narzędzia SQL <br><br> | vortex.data.microsoft.com<br> <br>dc.services.visualstudio.com | https | 443 | Umożliwia wysyłanie statystyki niezawodności (dane o awariach/zawieszenia) od użytkownika do firmy Microsoft. Zrzuty rzeczywistej awarii/zawieszenia nadal zostanie przekazany, jeśli raportowanie błędów Windows jest włączona; tylko informacje statystyczne będą pomijane; <br>Używane do ujawniania wzorców anonimowe użycie rozszerzenia Azure Tools SDK programu Visual Studio i wzorców użycia dla programu SQL, narzędzia programu Visual Studio |
| {1&gt;Visual Studio&lt;1} <br> Komfort <br>Program poprawy jakości obsługi (klienta CEIP) <br><br>PerfWatson.exe | vortex.data.microsoft.com<br>dc.services.visualstudio.com<br>visualstudio-devdiv-c2s.msedge.net<br>az667904.vo.msecnd.net <br>scus-breeziest-in.cloudapp.net<br> | https | 443 | Używane do zbierania anonimowe użycie wzorce i dzienniki błędów <br><br>Używane do śledzenia problemów blokowanie interfejsu użytkownika |
| Tworzenie i<br>Zarządzanie <br>Zasoby platformy Azure | management.azure.com <br>management.core.windows.net | https | 443 | Używane do tworzenia witryn sieci Web platformy Azure lub inne zasoby do obsługi podczas publikowania aplikacji sieci web, usługi Azure Functions i WebJobs |
| Zaktualizowano web publikowanie narzędzi <br>Sprawdzanie i rozszerzenia <br>Zalecenia | marketplace.visualstudio.com | https | 443 | Używany do sprawdzania dostępności aktualizacji narzędzia publikowania. Wyłączenie tej opcji, mogą nie być wyświetlane potencjalny zalecane rozszerzenia na potrzeby publikowania w sieci web |
| Zaktualizowano zasobów platformy Azure <br>Informacje o tworzeniu punktu końcowego | \*.blob.core.windows.net | https | 443 | Użyć do zaktualizowania punktów końcowych używanych do tworzenia zasobów platformy Azure dla niektórych usług platformy Azure. Wyłączenie ostatniego pobrany lub wbudowane w punkcie końcowym lokalizacje są używane zamiast tego |
| Zdalne debugowanie i <br>Zdalne profilowanie <br>Usługa Azure Websites | &#42;.cloudapp.net <br> &#42;.azurewebsites.net | | 4022 | Używany do dołączania debugera zdalnego do witryn sieci Web platformy Azure. Wyłączenie dołączanie debugera zdalnego do witryn sieci Web platformy Azure nie będzie działać |
| Usługa Active Directory <br>Graph | graph.windows.net | https | 443 | Używane do obsługi administracyjnej nowych aplikacji usługi Azure Active Directory. Również używany przez dostawcę podłączoną usługę Office 365 MSGraph- |
| Azure Functions <br>Aktualizacja interfejsu wiersza polecenia <br>Sprawdź | functionscdn.azureedge.net | https | 443 | Używany do sprawdzania pod kątem zaktualizowanych wersji interfejsu wiersza polecenia usługi Azure Functions. Wyłączenie pamięci podręcznej kopię (lub kopiowania przez składnik usługi Azure Functions) interfejsu wiersza polecenia w zamian zostanie użyta |
| Cordova | npmjs.org<br>gradle.org | HTTP/HTTPS | 80/443 | Protokół HTTP jest używany do pobierania narzędzia Gradle w czasie kompilacji. Protokół HTTPS jest używana do włączenia wtyczki Cordova w projektach |
| Eksplorator chmury | 1. &#60;clusterendpoint&#62; <br>Usługa Service Fabric <br>2. &#60;punkt końcowy zarządzania&#62;<br>Exp chmury ogólne <br>3. &#60;punkt końcowy programu graph&#62;<br>Exp chmury ogólne<br>4. &#60;punktu końcowego konta magazynu&#62;<br>Węzły usługi Storage <br>5. &#60;witryny azure portal adresów URL&#62;<br>Exp chmury ogólne <br>6. &#60;punkty końcowe magazynu kluczy&#62; <br>Węzły maszyny Wirtualnej na platformie Azure Resource Manager<br>7. &#60;PublicIPAddressOfCluster&#62;<br>Usługa Service Fabric zdalne debugowanie i śladów funkcji ETW | <br>1. protokół https<br>2. protokół https<br>3. protokół https<br>4. protokół https<br>5. protokół https<br>6. protokół https<br>7: tcp | 1. 19080<br>2. 443 <br>3. 443 <br>4. 443 <br>5. 443 <br>6. 443 <br>7. dynamiczne | 1. przykład: test12.eastus.cloudapp.com<br>2. pobiera subskrypcje i pobiera/zarządza zasobami platformy Azure<br>3. pobiera Azure Stack subskrypcje<br>4. zarządza zasobami magazynu (przykład: mystorageaccount.blob.core.windows.net)<br>5. opcja menu kontekstowego "Otwórz w portalu" (otwiera zasób w Azure Portal)<br>6. tworzy i używa magazynów kluczy na potrzeby debugowania maszyn wirtualnych (przykład: myvault.vault.azure.net) <br><br>7. dynamicznie przydziela blok portów na podstawie liczby węzłów w klastrze i dostępnych portów. <br><br>Blok portu spróbuje uzyskać trzy razy liczba węzłów z co najmniej 10 portów.<br><br>Dla śladów przesyłania strumieniowego podejmowana jest próba pobrania bloku portu z 810. Jeśli dowolny z tego bloku port jest już używana, aby uzyskać kolejnego bloku i tak dalej zostanie podjęta próba. (Moduł równoważenia obciążenia jest pusta, portów z 810 będą prawdopodobnie używane) <br><br>Podobnie do debugowania, cztery zestawy blokuje porty są zarezerwowane: <br>-connectorPort: 30398, <br>-forwarderPort: 31398, <br>-forwarderPortx86: 31399,<br>-fileUploadPort: 32398<br> |
| Usługi w chmurze | 1. RDP<br><br>2. core.windows.net <br><br>3.  management.azure.com<br> management.core.windows.net <br><br>4. &#42;.blob.core.windows.net <br>&#42;.queue.core.windows.net<br>&#42;.table.core.windows.net <br><br>5. portal.azure.com <br><br>6. &#60;usługi w chmurze użytkownika&#62;. cloudapp.net <br> &#60;user's VM&#62;.&#60;region&#62;.azure.com | 1. protokołu rdp <br><br> 2. protokół https <br><br> 3. protokół https <br><br> 4. protokół https <br><br> 5. protokół https <br><br>6. tcp | 1. 3389 <br><br> 2. 443 <br><br> 3. 443 <br><br>4. 443 <br><br>5. 443 <br><br> 6.) 30398 <br> 6. b) 30400 <br> 6. c) 31398 <br> 6. d) 31400 <br> 6. e) 32398 <br> 6. f) 32400 | 1. Pulpit zdalny do Cloud Services maszyny wirtualnej <br><br> 2. składnik konta magazynu prywatnej konfiguracji diagnostyki <br><br> 3. Azure Portal <br><br> 4. Eksplorator serwera — usługa Azure &#42; Storage to konto magazynu o nazwie klient  <br><br> 5. linki do otwierania portalu &#47; pobieranie pliku ustawień publikowania certyfikatu &#47; subskrypcji <br><br>6.) port lokalny łącznik dla debugowania zdalnego dla usługi w chmurze i maszyn wirtualnych<br> 6. b) port publiczny łącznika dla debugowania zdalnego dla usługi w chmurze i maszyn wirtualnych <br> port lokalny 6. c) usługi przesyłania dalej dla debugowania zdalnego dla usługi w chmurze i maszyn wirtualnych <br> 6. d) port publiczny usługi przesyłania dalej dla debugowania zdalnego dla usługi w chmurze i maszyn wirtualnych  <br> 6. e) pliku obiektu przekazującego port lokalny do zdalnego debugowania dla usługi w chmurze i maszyn wirtualnych <br> 6. f) pliku obiektu przekazującego portu publicznego do zdalnego debugowania dla usługi w chmurze i maszyn wirtualnych |
| Usługa Service Fabric | 1. <br>ocs.Microsoft.com<br>aka.MS <br>go.microsoft.com <br><br>2. <br>vssftools.blob.core.windows.net <br>Vault.azure.com <br>Portal.azure.com <br><br> 3. &#42; vault.azure.net<br><br> 4. <br>app.vsaex.visualstudio.com<br>&#42; .vsspsext.visualstudio.com<br>clouds.vsrm.visualstudio.com <br>clouds.visualstudio.com<br>app.vssps.visualstudio.com <br>&#42; .visualstudio.com | https | 443 | 1. Dokumentacja <br><br> 2. Utwórz funkcję klastra <br><br>3. &#42; nazwa magazynu kluczy platformy Azure (przykład:-test11220180112110108.Vault.Azure.NET  <br><br>  4. &#42; jest to dynamiczny (przykład: vsspsextprodch1su1.vsspsext.VisualStudio.com) |
| Migawka <br>Debuger | 1. go.microsoft.com <br>2. management.azure.com <br> 3. &#42;azurewebsites.net <br> 4. &#42;scm.azurewebsites.net<br>5. api.nuget.org/v3/index.json <br>6. msvsmon (. exe) | 1. protokół https <br>2. protokół https  <br>3. http <br>4. protokół https <br>5. protokół https <br>6. Concord <br> | 1. 443<br> 2. 443<br>3. 80  <br>4. 443<br> 5. 443<br> 6. 4022 (zależne wersji programu visual Studio) | 1. plik Query. JSON dla rozmiaru jednostki SKU usługi App Service <br>2. różne wywołania usługi Azure RM <br>3. wywołanie rozgrzewania lokacji za pośrednictwem  <br>4. dla klienta App Service kudu punkt końcowy <br>5. zapytanie o wersję rozszerzenia witryny opublikowaną w nuget.org <br>6. kanał debugowania zdalnego |
| Azure Stream Analytics <br><br>HDInsight | Management.azure.com | https | 443 | Umożliwia wyświetlanie, Prześlij, uruchamianie i zarządzanie nimi zadania usługi ASA <br><br> Używane w celu przeglądania klastrach HDI i przesyłanie, diagnozowanie i debugowanie zadań usługi HDI |
| Azure Data Lake | &#42;.azuredatalakestore.net <br>&#42;.azuredatalakeanalytics.net | https | 443 | Używane do kompilowania, Prześlij, wyświetlanie, diagnozowanie i debugowanie zadań; używane do przeglądania plików ADLS. używany do przekazywania i pobierania plików |
| Usługi pakietu | [account].visualstudio.com <br/> [konto]. \*. visualstudio.com <br/> \*.blob.core.windows.net <br/> registry.npmjs.org </br> nodejs.org <br/> dist.nuget.org <br/> nuget.org | https | 443 | \*. Npmjs.org, \*. nuget.org, i \*. nodejs.org są tylko wymagane dla wybranych kompilacji scenariuszy zadań (na przykład: Instalator narzędzia NuGet, węzeł Tool Installer) lub jeśli zamierzasz używać upstreams publicznej przy użyciu źródła danych. Trzy domeny są wymagane do podstawowych funkcji tworzenia pakietów usługi. |
| Azure DevOps Services | \*. vsassets.io <br/> static2.sharepointonline.com <br/> dev.azure.com | | | Używane do łączenia się z usługami DevOps platformy Azure |
| | | | | |

## <a name="troubleshoot-network-related-errors"></a>Rozwiązywanie problemów związanych z siecią

Czasami może być wystąpiły błędy związane z siecią lub serwera proxy podczas instalowania lub użyć programu Visual Studio za zaporą lub serwerem proxy. Aby uzyskać więcej informacji na temat rozwiązania dla takich komunikatów o błędach, zobacz [Rozwiązywanie problemów z błędami związanych z siecią, podczas instalowania lub użyć programu Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md) strony.

## <a name="get-support"></a>Uzyskaj pomoc techniczną

Firma Microsoft oferuje [ **Czat na żywo** ](https://visualstudio.microsoft.com/vs/support/#talktous) opcję pomocy technicznej (tylko język angielski) w przypadku problemów związanych z instalacją.

Poniżej przedstawiono kilka więcej opcji pomocy technicznej:

* Zgłoś problemy produktu z nami za pośrednictwem [Zgłoś Problem](../ide/how-to-report-a-problem-with-visual-studio.md) narzędzia, która pojawia się zarówno w Instalatorze programu Visual Studio, jak i w środowisku IDE programu Visual Studio.
* Zaproponuj funkcję śledzenia problemów produktu i Szukaj odpowiedzi w [społeczności deweloperów programu Visual Studio](https://developercommunity.visualstudio.com/).
* Użyj swojej [GitHub](https://github.com/) konto, aby komunikować się z USA i innych deweloperów programu Visual Studio w [konwersacji programu Visual Studio community dotyczącym oprogramowania Gitter](https://gitter.im/Microsoft/VisualStudio).

## <a name="see-also"></a>Zobacz także

* [Wymagania dotyczące łączności dla rozszerzenia Live Share](/visualstudio/liveshare/reference/connectivity/)
* [Tworzenie instalacji sieciowej programu Visual Studio](create-a-network-installation-of-visual-studio.md)
* [Rozwiązywanie problemów dotyczących sieci w programie Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md)
* [Podręcznik administratora w usłudze Visual Studio](visual-studio-administrator-guide.md)
* [Instalowanie za serwerem zapory lub serwera proxy (Visual Studio dla komputerów Mac)](/visualstudio/mac/install-behind-a-firewall-or-proxy-server)

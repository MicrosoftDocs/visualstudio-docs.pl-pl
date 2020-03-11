---
title: Instalowanie i używanie za zaporą lub serwerem proxy
description: Przejrzyj adresy URL domeny, porty i protokoły, które możesz chcieć dodać do listy dozwolonych, lub Otwórz, jeśli Twoja organizacja używa zapory lub serwera proxy
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
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409523"
---
# <a name="install-and-use-visual-studio-and-azure-services-behind-a-firewall-or-proxy-server"></a>Instalowanie i używanie programu Visual Studio i usług platformy Azure za serwerem zapory lub serwera proxy

Jeśli ty lub Twoja organizacja korzysta z środków zabezpieczeń, takich jak zapora lub serwer proxy, istnieją adresy URL domeny, które można dodać do listy "Lista dozwolonych" oraz portów i protokołów, które mogą być otwierane, aby zapewnić najlepsze środowisko podczas instalowania i używania  Visual Studio i usługi platformy Azure.

* **[Zainstaluj program Visual Studio](#install-visual-studio)** : te tabele zawierają adresy URL domeny, które mają zostać dodane do listy dozwolonych, dzięki czemu masz dostęp do wszystkich składników i obciążeń, które chcesz.

* **[Użyj programu Visual Studio i usług platformy Azure](#use-visual-studio-and-azure-services)** : Ta tabela zawiera adresy URL domeny, które mają zostać dodane do listy dozwolonych, oraz porty i protokoły do otwarcia, aby mieć dostęp do wszystkich żądanych funkcji i usług.

> [!NOTE]
> Ten artykuł został zapisany dla programu Visual Studio w systemie Windows, ale pewne informacje dotyczą również [instalowania Visual Studio dla komputerów Mac](/visualstudio/mac/install-behind-a-firewall-or-proxy-server) za zaporą lub serwerem proxy.

## <a name="install-visual-studio"></a>Instalacja programu Visual Studio

### <a name="urls-to-add-to-an-allow-list"></a>Adresy URL do dodania do listy dozwolonych

Ponieważ Instalator programu Visual Studio pobiera pliki z różnych domen i ich serwerów pobierania, poniżej znajdują się adresy URL domeny, które mogą zostać dodane do listy dozwolonych jako zaufane w interfejsie użytkownika lub w skryptach wdrożenia.

#### <a name="microsoft-domains"></a>Microsoft domains

| Domain | Przeznaczenie |
| - | - |
| go.microsoft.com | Rozpoznawanie adresu URL instalacji |
| aka.MS | Rozpoznawanie adresu URL instalacji |
| download.visualstudio.microsoft.com | Konfigurowanie lokalizacji pobierania pakietów |
| download.microsoft.com | Konfigurowanie lokalizacji pobierania pakietów |
| download.visualstudio.com | Konfigurowanie lokalizacji pobierania pakietów |
| dl.xamarin.com | Konfigurowanie lokalizacji pobierania pakietów |
| xamarin-downloads.azureedge.net | Lokalizacja listy pobierania pakietów Android SDK |
| marketplace.visualstudio.com | Lokalizacja pobierania rozszerzenia programu Visual Studio |
| \*. gallerycdn.vsassets.io  | Lokalizacja pobierania rozszerzenia programu Visual Studio |
| visualstudio.microsoft.com | Lokalizacja dokumentacji |
| docs.microsoft.com | Lokalizacja dokumentacji |
| msdn.microsoft.com | Lokalizacja dokumentacji |
| microsoft.com www\. | Lokalizacja dokumentacji |
| \*.windows.net | Lokalizacja logowania |
| \*.microsoftonline.com | Lokalizacja logowania |
| \*.live.com | Lokalizacja logowania |
| | |

#### <a name="non-microsoft-domains"></a>Domeny inne niż firmy Microsoft

| Domain | Instaluje te obciążenia |
| - | - |
| archive.apache.org | Tworzenie aplikacji mobilnych za pomocą języka JavaScript (Cordova) |
| cocos2d-x.org | Tworzenie gier przy użyciu języka C++ (Cocos) |
| download.epicgames.com | Tworzenie gier przy użyciu języka C++ (Unreal Engine) |
| download.oracle.com | Tworzenie aplikacji mobilnych za pomocą języka JavaScript (zestaw SDK języka Java) <br /><br />Tworzenie aplikacji mobilnych przy użyciu platformy .NET (Java SDK) |
| download.unity3d.com | Programowanie gier za pomocą aparatu Unity (Unity) |
| netstorage.unity3d.com | Programowanie gier za pomocą aparatu Unity (Unity) |
| dl.google.com | Tworzenie aplikacji mobilnych za pomocą języka JavaScript (zestaw Android SDK i zestawu NDK, emulatora) <br /><br />Tworzenie aplikacji mobilnych przy użyciu platformy .NET (zestaw Android SDK i zestawu NDK, emulatora) |
| incredibuild.com www\. | Tworzenie gier przy użyciu języka C++ (IncrediBuild) |
| incredibuildvs2017i.azureedge.net | Tworzenie gier przy użyciu języka C++ (IncrediBuild) |
| python.org www\. | Programowanie w języku Python (Python) <br /><br />Dane aplikacji analizy i przetwarzania (Python) |
| developerservices2.apple.com | Inicjowanie obsługi platformy Xamarin. iOS |
| developer.apple.com | Inicjowanie obsługi platformy Xamarin. iOS |
| appstoreconnect.apple.com | Inicjowanie obsługi platformy Xamarin. iOS |
| idmsa.apple.com | Inicjowanie obsługi platformy Xamarin. iOS |
| | |

## <a name="use-visual-studio-and-azure-services"></a>Używanie programu Visual Studio i usług platformy Azure

### <a name="urls-to-add-to-an-allow-list-and-ports-and-protocols-to-open"></a>Adresy URL do dodania do listy dozwolonych i portów i protokołów do otwarcia

Aby mieć pewność, że masz dostęp do wszystkiego, czego potrzebujesz, gdy korzystasz z programu Visual Studio lub usług platformy Azure za zaporą lub serwerem proxy, poniżej znajdują się adresy URL, które należy dodać do listy dozwolonych, i portów i protokołów, które mogą być otwierane.

| Usługa lub scenariusza | Punkt końcowy DNS | Protokół<br/>/Port | Opis |
| - | - | -: | - | - |
| Adres URL<br>rozwiązanie | go.microsoft.com<br><br>aka.MS | | Mające na celu skrócenie adresów URL, które następnie rozwiąż problem na dłużej adresów URL |
| Strona początkowa | vsstartpage.blob.core.windows.net | 443 | Służy do wyświetlania wiadomości dla deweloperów wyświetlanych na stronie startowej (tylko w programie Visual Studio 2017) |
| Docelowe<br> Powiadomienie <br>Usługa | targetednotifications-tm.trafficmanager.net <br><br>www.research.net | 443<br><br>443 | Używane do filtrowania globalną listę powiadomień do listy, która ma zastosowanie tylko do określonych rodzajów scenariusze maszyn/użycia |
| Wewnętrzny <br>sprawdzenie dostępności aktualizacji | marketplace.visualstudio.com<br><br>&#42;.windows.net <br>&#42;.microsoftonline.com <br>&#42;.live.com | 443 | Używane do udostępniania powiadomień, gdy zainstalowane rozszerzenie ma dostępną aktualizację <br><br> Używana jako lokalizacja logowania |
| Projekt sztucznej Inteligencji <br>Integracja | az861674.vo.msecnd.net | 443<br> | Używane do konfigurowania nowych projektów, aby wysłać dane użycia do swoje zarejestrowane konto w usłudze Application Insights |
| Funkcji Code Lens | codelensprodscus1su0.app.<br>codelens.visualstudio.com | 443 | Można uzyskać informacje dotyczące po ostatniej aktualizacji pliku, oś czasu zmiany, elementy robocze, które są skojarzone zmiany, autorów i więcej w edytorze |
| Eksperymentalne <br>Włączanie funkcji | visualstudio-devdiv-c2s.msedge.net | 80 | Umożliwia uaktywnianie eksperymentalne nowe funkcje i zmiany funkcji |
| Tożsamość "badge" <br>(nazwa użytkownika i awatara)<br>i <br>Ustawienia roamingu | app.vssps.visualstudio.com <br><br>app.vsspsext.visualstudio.com<br><br>app.vssps.visualstudio.com<br><br> ns-sb2-prod-ch1-002.cloudapp.net <br><br>az700632.vo.msecnd.net<br><br>api.vstsusers.visualstudio.com/profiles/* | 443 | Umożliwia wyświetlenie nazwy użytkownika i awatara w środowisku IDE <br><br> Używany do sprawdzenia, czy zmiany ustawień są przekazywane z jednego komputera na inny |
| Ustawienia zdalnego | az700632.vo.msecnd.net | 443 | Używane do wyłączania rozszerzeń, które są znane spowodować problemy w programie Visual Studio |
| Narzędzia Windows | developer.microsoft.com <br><br>dev.windows.com  <br><br>appdev.microsoft.com | https/443 | Używany w scenariuszach magazynu aplikacji Windows |
| Schemat JSON <br>Odnajdywanie <br><br>Schemat JSON <br>Definicja<br><br>Schemat JSON <br>Obsługa <br>Zasoby platformy Azure | json.schemastore.org <br>schemastoreorg.azurewebsites.net<br><br>json-schema.org<br><br>schema.management.azure.com | protokół http/80<br>https/443<br><br>protokół http/80<br><br>https/443 | Używana do odnajdowania i Pobierz schematów JSON, które użytkownik może użyć podczas edycji dokumentów JSON <br><br>Używany do uzyskiwania schematu sprawdzania poprawności metadanych dla formatu JSON<br><br>Używany do uzyskiwania bieżącego schematu dla szablonów wdrażania usługi Azure Resource Manager |
| Pakiet NPM <br>odnajdywanie | Skimdb.npmjs.com <br><br>Registry.npmjs.org <br><br>Api.npms.io | https/443<br><br>& http/80<br> https/443<br>https/443 | Wymagane do wyszukiwania dla pakietów NPM i używane do instalacji pakietu skryptu po stronie klienta w projektach sieci web |
| Pakietów bower<br> ikony<br><br>Pakietów bower <br>search | Bower.IO <br><br>bowercache.azurewebsites.net <br>go.microsoft.com <br>Registry.bower.io | protokół http/80<br><br>https/443<br>protokół http/80<br>https/443 | Udostępnia domyślną ikonę pakietu bower  <br><br>Umożliwia wyszukiwanie pakietów Bower |
| NuGet<br><br>Pakiet NuGet<br> odnajdywanie | api.nuget.org <br>www.nuget.org <br>nuget.org <br>azuresearch-usnc.nuget.org <br>azuresearch-ussc.nuget.org <br>licenses.nuget.org <br>nuget.cdn.azure.cn <br>azuresearch-ea.nuget.org <br>azuresearch-sea.nuget.org <br><br>crl3.digicert.com <br>crl4.digicert.com <br>ocsp.digicert.com <br>cacerts.digicert.com | https/443<br><br>& http/80<br>https/443<br> | Używane do weryfikowania podpisanych pakietów NuGet.<br><br>Wymagane dla wyszukiwanie pakietów NuGet i wersje |
| Informacje o repozytorium GitHub | api.github.com | https/443 | Wymagane w celu uzyskania dodatkowych informacji na temat pakietów bower |
| Linterów sieci Web | Eslint.org<br><br>www.Bing.com <br><br>www.coffeelint.org | protokół http/80 | |
| Cookiecutter<br>Eksplorator szablonu<br>odnajdywanie <br><br>Cookiecutter <br>Eksplorator projektu<br> Tworzenie | api.github.com <br>raw.githubusercontent.com <br>go.microsoft.com<br><br>pypi.org <br> pypi.python.org | https/443<br> | Służy do odnajdywania szablonów online z naszych zalecanych kanałów informacyjnych i repozytoriów GitHub <br><br>Umożliwia tworzenie projektu z szablonu narzędzia cookiecutter, który wymaga jednorazowe instalacji na żądanie pakietu języka Python cookiecutter na podstawie indeksu pakietów języka Python (PyPI) |
| Pakiet języka Python <br>odnajdywanie<br><br>Pakiet języka Python <br>zarządzanie<br><br>Nowa <br>Python <br> projekt <br>szablonów | pypi.org<br> <br>pypi.python.org <br>bootstrap.pypa.io<br><br>go.microsoft.com | https/443 | Zapewnia możliwość wyszukiwania pakiety pip<br><br>Używane do automatycznego instalowania narzędzia pip, jeżeli brakuje <br><br>Służy do rozwiązywania następujących nowych szablonów projektów języka Python do adresów URL szablonów cookiecutter:<br> -Projekt klasifikace<br>-Projekt clusteringu <br> -Projekt regrese <br> -PyGame przy użyciu PyKinect <br> -Projekt Pyvot |
| Sieci web pakietu Office <br>Dodatek <br> Manifest <br>Weryfikacja <br>Usługa | verificationservice.osi.office.net | https/443 | Służy do sprawdzania manifesty dla dodatki pakietu Office sieci web |
| Program SharePoint i <br>Dodatki pakietu Office | sharepoint.com<br> office365.com<br> microsoftonline.com <br> outlook.com | https/443 | Służy do publikowania i testowania dodatków programu SharePoint i pakietu Office do usługi SharePoint Online i pakietu Office 365 |
| Usługa Workflow Manager <br>Testowanie usługi<br> Host | | http/12292 | Reguły zapory, która jest tworzona automatycznie do dodatków programu SharePoint przy użyciu przepływów pracy testowania |
| Zbierane automatycznie <br>statystyki niezawodności <br>i innych <br>Komfort <br>Programów poprawy jakości obsługi (klienta CEIP)<br> dla zestawu Azure SDK i <br>Aby uzyskać narzędzia SQL <br><br> | vortex.data.microsoft.com<br> <br>dc.services.visualstudio.com | https/443 | Umożliwia wysyłanie statystyki niezawodności (dane o awariach/zawieszenia) od użytkownika do firmy Microsoft. Zrzuty rzeczywistej awarii/zawieszenia nadal zostanie przekazany, jeśli raportowanie błędów Windows jest włączona; tylko informacje statystyczne będą pomijane; <br>Używane do ujawniania wzorców anonimowe użycie rozszerzenia Azure Tools SDK programu Visual Studio i wzorców użycia dla programu SQL, narzędzia programu Visual Studio |
| Visual Studio <br> Komfort <br>Program poprawy jakości obsługi (klienta CEIP) <br><br>PerfWatson.exe | vortex.data.microsoft.com<br>dc.services.visualstudio.com<br>visualstudio-devdiv-c2s.msedge.net<br>az667904.vo.msecnd.net <br>scus-breeziest-in.cloudapp.net<br> | https/443 | Używane do zbierania anonimowe użycie wzorce i dzienniki błędów <br><br>Używane do śledzenia problemów blokowanie interfejsu użytkownika |
| Tworzenie i<br>Zarządzanie <br>Zasoby platformy Azure | management.azure.com <br>management.core.windows.net | https/443 | Używane do tworzenia witryn sieci Web platformy Azure lub inne zasoby do obsługi podczas publikowania aplikacji sieci web, usługi Azure Functions i WebJobs |
| Zaktualizowano web publikowanie narzędzi <br>Sprawdzanie i rozszerzenia <br>Zalecenia | marketplace.visualstudio.com | https/443 | Używany do sprawdzania dostępności aktualizacji narzędzia publikowania. Wyłączenie tej opcji, mogą nie być wyświetlane potencjalny zalecane rozszerzenia na potrzeby publikowania w sieci web |
| Zaktualizowano zasobów platformy Azure <br>Informacje o tworzeniu punktu końcowego | \*.blob.core.windows.net | https/443 | Użyć do zaktualizowania punktów końcowych używanych do tworzenia zasobów platformy Azure dla niektórych usług platformy Azure. Wyłączenie ostatniego pobrany lub wbudowane w punkcie końcowym lokalizacje są używane zamiast tego |
| Zdalne debugowanie i <br>Zdalne profilowanie <br>Usługa Azure Websites | &#42;.cloudapp.net <br> &#42;.azurewebsites.net | 4022 | Używany do dołączania debugera zdalnego do witryn sieci Web platformy Azure. Wyłączenie dołączanie debugera zdalnego do witryn sieci Web platformy Azure nie będzie działać |
| Usługa Active Directory <br>Graph | graph.windows.net | https/443 | Używane do obsługi administracyjnej nowych aplikacji usługi Azure Active Directory. Również używany przez dostawcę podłączoną usługę Office 365 MSGraph- |
| Azure Functions <br>Aktualizacja interfejsu wiersza polecenia <br>Zaznacz | functionscdn.azureedge.net | https/443 | Używany do sprawdzania pod kątem zaktualizowanych wersji interfejsu wiersza polecenia usługi Azure Functions. Wyłączenie pamięci podręcznej kopię (lub kopiowania przez składnik usługi Azure Functions) interfejsu wiersza polecenia w zamian zostanie użyta |
| Cordova | npmjs.org<br>gradle.org | & http/80<br/>https/443 | Protokół HTTP jest używany do pobierania narzędzia Gradle w czasie kompilacji. Protokół HTTPS jest używana do włączenia wtyczki Cordova w projektach |
| Eksplorator chmury | 1. &#60;clusterendpoint&#62; <br>Service Fabric <br>2. &#60;punkt końcowy zarządzania&#62;<br>Exp chmury ogólne <br>3. &#60;punkt końcowy programu graph&#62;<br>Exp chmury ogólne<br>4. &#60;punktu końcowego konta magazynu&#62;<br>Węzły usługi Storage <br>5. &#60;witryny azure portal adresów URL&#62;<br>Exp chmury ogólne <br>6. &#60;punkty końcowe magazynu kluczy&#62; <br>Węzły maszyny Wirtualnej na platformie Azure Resource Manager<br>7. &#60;PublicIPAddressOfCluster&#62;<br>Usługa Service Fabric zdalne debugowanie i śladów funkcji ETW | <br>1. https/19080<br>2. https/443<br>3. https/443<br>4. https/443<br>5. https/443<br>6. https/443<br>7. TCP/dynamiczny | 1. przykład: test12.eastus.cloudapp.com<br>2. pobiera subskrypcje i pobiera/zarządza zasobami platformy Azure<br>3. pobiera Azure Stack subskrypcje<br>4. zarządza zasobami magazynu (przykład: mystorageaccount.blob.core.windows.net)<br>5. opcja menu kontekstowego "Otwórz w portalu" (otwiera zasób w Azure Portal)<br>6. tworzy i używa magazynów kluczy na potrzeby debugowania maszyn wirtualnych (przykład: myvault.vault.azure.net) <br><br>7. dynamicznie przydziela blok portów na podstawie liczby węzłów w klastrze i dostępnych portów. <br><br>Blok portu spróbuje uzyskać trzy razy liczba węzłów z co najmniej 10 portów.<br><br>Dla śladów przesyłania strumieniowego podejmowana jest próba pobrania bloku portu z 810. Jeśli dowolny z tego bloku port jest już używana, aby uzyskać kolejnego bloku i tak dalej zostanie podjęta próba. (Moduł równoważenia obciążenia jest pusta, portów z 810 będą prawdopodobnie używane) <br><br>Podobnie do debugowania, cztery zestawy blokuje porty są zarezerwowane: <br>-connectorPort: 30398, <br>-forwarderPort: 31398, <br>-forwarderPortx86: 31399,<br>-fileUploadPort: 32398<br> |
| Cloud Services | 1. RDP<br><br>2. core.windows.net <br><br>3.  management.azure.com<br> management.core.windows.net <br><br>4. &#42;.blob.core.windows.net <br>&#42;.queue.core.windows.net<br>&#42;.table.core.windows.net <br><br>5. portal.azure.com <br><br>6. &#60;usługi w chmurze użytkownika&#62;. cloudapp.net <br> &#60;user's VM&#62;.&#60;region&#62;.azure.com | 1. rdp/3389 <br><br> 2. https/443 <br><br> 3. https/443 <br><br> 4. https/443 <br><br> 5. https/443 <br><br>6. tcp <br>a) 30398 <br>b) 30400 <br>c) 31398 <br>d) 31400 <br>e) 32398 <br>f) 32400 | 1. Pulpit zdalny do Cloud Services maszyny wirtualnej <br><br> 2. składnik konta magazynu prywatnej konfiguracji diagnostyki <br><br> 3. Azure Portal <br><br> 4. Eksplorator serwera — usługa Azure &#42; Storage to konto magazynu o nazwie klient  <br><br> 5. linki do otwierania portalu &#47; pobieranie pliku ustawień publikowania certyfikatu &#47; subskrypcji <br><br>6.) port lokalny łącznik dla debugowania zdalnego dla usługi w chmurze i maszyn wirtualnych<br> 6. b) port publiczny łącznika dla debugowania zdalnego dla usługi w chmurze i maszyn wirtualnych <br> port lokalny 6. c) usługi przesyłania dalej dla debugowania zdalnego dla usługi w chmurze i maszyn wirtualnych <br> 6. d) port publiczny usługi przesyłania dalej dla debugowania zdalnego dla usługi w chmurze i maszyn wirtualnych  <br> 6. e) pliku obiektu przekazującego port lokalny do zdalnego debugowania dla usługi w chmurze i maszyn wirtualnych <br> 6. f) pliku obiektu przekazującego portu publicznego do zdalnego debugowania dla usługi w chmurze i maszyn wirtualnych |
| Service Fabric | 1. <br>ocs.Microsoft.com<br>aka.MS <br>go.microsoft.com <br><br>2. <br>vssftools.blob.core.windows.net <br>Vault.azure.com <br>Portal.azure.com <br><br> 3. &#42; vault.azure.net<br><br> 4. <br>app.vsaex.visualstudio.com<br>&#42; .vsspsext.visualstudio.com<br>clouds.vsrm.visualstudio.com <br>clouds.visualstudio.com<br>app.vssps.visualstudio.com <br>&#42; .visualstudio.com | https/443 | 1. Dokumentacja <br><br> 2. Utwórz funkcję klastra <br><br>3. &#42; nazwa magazynu kluczy platformy Azure (przykład:-test11220180112110108.Vault.Azure.NET  <br><br>  4. &#42; jest to dynamiczny (przykład: vsspsextprodch1su1.vsspsext.VisualStudio.com) |
| Snapshot <br>Debuger | 1. go.microsoft.com <br>2. management.azure.com <br> 3. &#42;. azurewebsites.NET <br> 4. &#42;. SCM.azurewebsites.NET<br>5. api.nuget.org/v3/index.json <br>6. Usługa zdalna/adres IP serwerów/nazwa FQDN | 1. https/443 <br>2. https/443  <br>3. http/80 <br>4. https/443 <br>5. https/443 <br>6. Concord/<br> 4022 (zależna wersja programu Visual Studio) | 1. plik Query. JSON dla rozmiaru jednostki SKU usługi App Service <br>2. różne wywołania usługi Azure RM <br>3. wywołanie rozgrzewania lokacji za pośrednictwem  <br>4. dla klienta App Service kudu punkt końcowy <br>5. zapytanie o wersję rozszerzenia witryny opublikowaną w nuget.org <br>6. [debugowanie zdalne](../debugger/remote-debugging.md) |
| Usługa Azure Stream Analytics <br><br>HDInsight | Management.azure.com | https/443 | Umożliwia wyświetlanie, Prześlij, uruchamianie i zarządzanie nimi zadania usługi ASA <br><br> Używane w celu przeglądania klastrach HDI i przesyłanie, diagnozowanie i debugowanie zadań usługi HDI |
| Azure Data Lake | &#42;.azuredatalakestore.net <br>&#42;.azuredatalakeanalytics.net | https/443 | Używane do kompilowania, Prześlij, wyświetlanie, diagnozowanie i debugowanie zadań; używane do przeglądania plików ADLS. używany do przekazywania i pobierania plików |
| Usługi pakietu | [account].visualstudio.com <br/> [Account].\*. visualstudio.com <br/> \*.blob.core.windows.net <br/> registry.npmjs.org </br> nodejs.org <br/> dist.nuget.org <br/> nuget.org | https/443 | \*. npmjs.org, \*. nuget.org i \*. nodejs.org są wymagane tylko w przypadku niektórych scenariuszy zadań kompilacji (na przykład Instalatora narzędzia NuGet, Instalatora narzędzia węzła) lub jeśli zamierzasz używać publicznego przesyłania strumieniowego ze źródłami danych. Trzy domeny są wymagane do podstawowych funkcji tworzenia pakietów usługi. |
| Usługa Azure DevOps Services | \*. vsassets.io <br/> static2.sharepointonline.com <br/> dev.azure.com | | Używane do łączenia się z usługami DevOps platformy Azure |
| Społeczność deweloperów | sendvsfeedback2.azurewebsites.net/api | https/443 | Służy do wywoływania interfejsów API narzędzia do oceny społeczności deweloperów (moje problemy, wyszukiwanie, głosowanie, komentarz, przesyłanie, przekazywanie, wznawianie) |
| Rozszerzenia intellicode | \*. intellicode.vsengsaas.visualstudio.com | https/443 | Używane do wywoływania interfejsów API rozszerzenia intellicode |
| Live Share | \*. liveshare.vsengsaas.visualstudio.com| https/443 | Używane do wywoływania Live Share interfejsów API |
| Visual Studio Online | \*. online.visualstudio.com | https/443 | Używane do wywoływania interfejsów API usługi Visual Studio Online |
| Automatyczne pobieranie typu JavaScript | registry.npmjs.org | https/443 | Służy do instalowania definicji typów TypeScript w celu zapewnienia funkcji IntelliSense dla popularnych bibliotek JavaScript |
| Usługa licencjonowania subskrypcji programu Visual Studio | app.vssps.visualstudio.com/apis/<br/>Licencjonowanie/ClientRights | https/443 | Licencjonowanie aktywacji w trybie online |
| Debuger | 1. <br>vsdebugger.blob.core.windows.net <br>vsdebugger.azureedge.net <br><br>2. <br>download.visualstudio.com/\*/<br/>OneCore. msvsmon.\*. zip<br><br> 3. referencesource.microsoft.com/symbols <br><br> 4. <br>symbols.nuget.org/download/symbols<br><br> 5. visualstudio.com<br><br>6. msdl.microsoft.com/download/symbols | https/443 | 1. <br>Służy do pobierania BITS debugera dla debugowania .NET Core w systemie UNIX/macOS za pośrednictwem protokołu SSH <br><br>2. <br>Służy do pobierania BITS debugera dla zdalnego debugowania kontenerów platformy Docker systemu Windows<br><br> 3. używane do wykonywania kroków źródłowych programu .NET Framework <br><br> 4. <br>(Jeśli założenia użytkownika) Służy do pobierania symboli publikowanych na serwerze symboli nuget.org.<br><br> 5. (Jeśli użytkownik zdecyduje się na) służący do pobierania symboli i plików binarnych firmy Microsoft, może być również wymagany do debugowania kodu zarządzanego w zrzutach |
| Visual Studio Online| \*. online.visualstudio.com | https/443 | Używane do wywoływania interfejsów API usługi Visual Studio Online |
| Publikowanie aplikacji platformy Xamarin dla systemu Android | \*. googleapis.com <br/> play.google.com <br/>accounts.google.com | https/443 | Służy do współpracy z usługą Sklep Google Play do publikowania/przekazywania aplikacji platformy Xamarin Android bezpośrednio z programu Visual Studio. |
| Azure Container Registry | *. azurecr.io | https/443 | Dostęp do rejestrów kontenerów hostowanych na platformie Azure w celu skonfigurowania potoków CICD |
| | | | |

## <a name="troubleshoot-network-related-errors"></a>Rozwiązywanie problemów związanych z siecią

Czasami może być wystąpiły błędy związane z siecią lub serwera proxy podczas instalowania lub użyć programu Visual Studio za zaporą lub serwerem proxy. Aby uzyskać więcej informacji o rozwiązaniach takich komunikatów o błędach, zobacz [Rozwiązywanie problemów związanych z siecią podczas instalowania lub używania strony programu Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md) .

## <a name="get-support"></a>Uzyskiwanie pomocy technicznej

Oferujemy opcję obsługi [**rozmowy na żywo**](https://visualstudio.microsoft.com/vs/support/#talktous) (tylko w języku angielskim) dla problemów związanych z instalacją.

Poniżej przedstawiono kilka więcej opcji pomocy technicznej:

* Zgłoś problemy dotyczące produktów w firmie Microsoft za pomocą narzędzia [Zgłoś problem](../ide/how-to-report-a-problem-with-visual-studio.md) , które pojawia się zarówno w Instalator programu Visual Studio, jak i w środowisku IDE programu Visual Studio.
* Zaproponuj funkcję, śledź problemy dotyczące produktów i Znajdź odpowiedzi w [społeczności deweloperów programu Visual Studio](https://developercommunity.visualstudio.com/).
* Użyj swojego konta w usłudze [GitHub](https://github.com/) , aby komunikować się z nami i innych deweloperów programu Visual Studio w [konwersacji programu Visual Studio w społeczności warunkom](https://gitter.im/Microsoft/VisualStudio).

## <a name="see-also"></a>Zobacz też

* [Wymagania dotyczące łączności dla rozszerzenia Live Share](/visualstudio/liveshare/reference/connectivity/)
* [Tworzenie instalacji sieciowej programu Visual Studio](create-a-network-installation-of-visual-studio.md)
* [Rozwiązywanie problemów związanych z siecią w programie Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md)
* [Przewodnik administratora programu Visual Studio](visual-studio-administrator-guide.md)
* [Instalowanie za zaporą lub serwerem proxy (Visual Studio dla komputerów Mac)](/visualstudio/mac/install-behind-a-firewall-or-proxy-server)

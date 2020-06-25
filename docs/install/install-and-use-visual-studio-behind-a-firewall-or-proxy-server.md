---
title: Instalowanie i używanie za zaporą lub serwerem proxy
description: Przejrzyj adresy URL domeny, porty i protokoły, które możesz chcieć dodać do listy dozwolonych, lub Otwórz, jeśli Twoja organizacja używa zapory lub serwera proxy
ms.date: 06/17/2020
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
ms.openlocfilehash: 09340940796e20f679c3c9bbad3d55880b25ab7a
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85283479"
---
# <a name="install-and-use-visual-studio-and-azure-services-behind-a-firewall-or-proxy-server"></a>Instalowanie i używanie programu Visual Studio i usług platformy Azure za zaporą lub serwerem proxy

Jeśli ty lub Twoja organizacja korzysta z środków zabezpieczeń, takich jak zapora lub serwer proxy, istnieją adresy URL domeny, które można dodać do listy "Lista dozwolonych" oraz portów i protokołów, które mogą być otwierane, aby zapewnić najlepsze środowisko podczas instalowania i używania usług Visual Studio i Azure.

* **[Zainstaluj program Visual Studio](#install-visual-studio)**: te tabele zawierają adresy URL domeny, które mają zostać dodane do listy dozwolonych, dzięki czemu masz dostęp do wszystkich składników i obciążeń, które chcesz.

* **[Użyj programu Visual Studio i usług platformy Azure](#use-visual-studio-and-azure-services)**: Ta tabela zawiera adresy URL domeny, które mają zostać dodane do listy dozwolonych, oraz porty i protokoły do otwarcia, aby mieć dostęp do wszystkich żądanych funkcji i usług.

> [!NOTE]
> Ten artykuł został zapisany dla programu Visual Studio w systemie Windows, ale pewne informacje dotyczą również [instalowania Visual Studio dla komputerów Mac](/visualstudio/mac/install-behind-a-firewall-or-proxy-server) za zaporą lub serwerem proxy.

## <a name="install-visual-studio"></a>Instalowanie programu Visual Studio

### <a name="urls-to-add-to-an-allow-list"></a>Adresy URL do dodania do listy dozwolonych

Ponieważ Instalator programu Visual Studio pobiera pliki z różnych domen i ich serwerów pobierania, poniżej znajdują się adresy URL domeny, które mogą zostać dodane do listy dozwolonych jako zaufane w interfejsie użytkownika lub w skryptach wdrożenia.

#### <a name="microsoft-domains"></a>Domeny firmy Microsoft

| Domain | Przeznaczenie |
| - | - |
| go.microsoft.com | Rozwiązywanie problemów z adresem URL |
| aka.ms | Rozwiązywanie problemów z adresem URL |
| download.visualstudio.microsoft.com | Lokalizacja pobierania pakietów instalacyjnych |
| download.microsoft.com | Lokalizacja pobierania pakietów instalacyjnych |
| download.visualstudio.com | Lokalizacja pobierania pakietów instalacyjnych |
| dl.xamarin.com | Lokalizacja pobierania pakietów instalacyjnych |
| xamarin-downloads.azureedge.net | Lokalizacja listy pobierania pakietów Android SDK |
| marketplace.visualstudio.com | Lokalizacja pobierania rozszerzeń programu Visual Studio |
| \*. gallerycdn.vsassets.io  | Lokalizacja pobierania rozszerzeń programu Visual Studio |
| visualstudio.microsoft.com | Lokalizacja dokumentacji |
| docs.microsoft.com | Lokalizacja dokumentacji |
| msdn.microsoft.com | Lokalizacja dokumentacji |
| \.Microsoft.com www | Lokalizacja dokumentacji |
| \*.windows.net | Lokalizacja logowania |
| \*.microsoftonline.com | Lokalizacja logowania |
| \*.live.com | Lokalizacja logowania |
| | |

#### <a name="non-microsoft-domains"></a>Domeny inne niż firmy Microsoft

| Domain | Instaluje te obciążenia |
| - | - |
| archive.apache.org | Programowanie aplikacji mobilnych za pomocą języka JavaScript (Cordova) |
| cocos2d-x.org | Programowanie gier za pomocą języka C++ (Wyspy Kokosowe) |
| download.epicgames.com | Programowanie gier za pomocą języka C++ (aparat Unreal) |
| download.oracle.com | Programowanie aplikacji mobilnych za pomocą języka JavaScript (Java SDK) <br /><br />Programowanie aplikacji mobilnych przy użyciu platformy .NET (SDK Java) |
| download.unity3d.com | Programowanie gier za pomocą aparatu Unity (Unity) |
| netstorage.unity3d.com | Programowanie gier za pomocą aparatu Unity (Unity) |
| dl.google.com | Programowanie aplikacji mobilnych za pomocą języka JavaScript (Android SDK i NDK, Emulator) <br /><br />Programowanie aplikacji mobilnych przy użyciu platformy .NET (Android SDK i NDK, Emulator) |
| \.incredibuild.com www | Programowanie gier za pomocą języka C++ (IncrediBuild) |
| incredibuildvs2017i.azureedge.net | Programowanie gier za pomocą języka C++ (IncrediBuild) |
| \.Python.org www | Programowanie w języku Python (Python) <br /><br />Aplikacje do analizy i przetwarzania danych (Python) |
| developerservices2.apple.com | Inicjowanie obsługi platformy Xamarin. iOS |
| developer.apple.com | Inicjowanie obsługi platformy Xamarin. iOS |
| appstoreconnect.apple.com | Inicjowanie obsługi platformy Xamarin. iOS |
| idmsa.apple.com | Inicjowanie obsługi platformy Xamarin. iOS |
| | |

## <a name="use-visual-studio-and-azure-services"></a>Korzystanie z programu Visual Studio i usług platformy Azure

### <a name="urls-to-add-to-an-allow-list-and-ports-and-protocols-to-open"></a>Adresy URL do dodania do listy dozwolonych i portów i protokołów do otwarcia

Aby mieć pewność, że masz dostęp do wszystkiego, czego potrzebujesz, gdy korzystasz z programu Visual Studio lub usług platformy Azure za zaporą lub serwerem proxy, poniżej znajdują się adresy URL, które należy dodać do listy dozwolonych, i portów i protokołów, które mogą być otwierane.

| Usługa lub scenariusz | Punkt końcowy usługi DNS | Protokół<br/>/Port | Opis |
| - | - | -: | - | - |
| Adres URL<br>rozwiązanie | go.microsoft.com<br><br>aka.ms | | Służy do skracania adresów URL, które następnie są rozpoznawane jako dłuższe adresy URL |
| Strona początkowa | vsstartpage.blob.core.windows.net | 443 | Służy do wyświetlania wiadomości dla deweloperów wyświetlanych na stronie startowej (tylko w programie Visual Studio 2017) |
| Docelowe<br> Powiadomienie <br>Usługa | targetednotifications-tm.trafficmanager.net <br><br>www.research.net | 443<br><br>443 | Służy do filtrowania globalnej listy powiadomień do listy, która ma zastosowanie tylko do określonych typów maszyn/scenariuszy użycia |
| Wewnętrzny <br>sprawdzenie aktualizacji | marketplace.visualstudio.com<br><br>&#42;. windows.net <br>&#42;. microsoftonline.com <br>&#42;. live.com | 443 | Służy do dostarczania powiadomień, gdy dostępne jest aktualizacje z zainstalowanym rozszerzeniem <br><br> Używane jako lokalizacja logowania |
| Projekt AI <br>Integracja | az861674.vo.msecnd.net | 443<br> | Służy do konfigurowania nowych projektów w celu wysyłania danych użycia do zarejestrowanego konta Application Insights |
| Soczewki kodu | codelensprodscus1su0. app.<br>codelens.visualstudio.com | 443 | Służy do przekazywania informacji w edytorze o momencie ostatniej aktualizacji pliku, osi czasu zmian, elementów roboczych, do których te zmiany są skojarzone, autorów itd. |
| Eksperymentalne <br>Włączanie funkcji | visualstudio-devdiv-c2s.msedge.net | 80 | Służy do uaktywniania eksperymentalnych nowych funkcji lub zmian funkcji |
| Tożsamość "znaczek" <br>(nazwa użytkownika i awatar)<br>oraz <br>Ustawienia roamingu | app.vssps.visualstudio.com <br><br>app.vsspsext.visualstudio.com<br><br>app.vssps.visualstudio.com<br><br> ns-sb2-prod-ch1-002.cloudapp.net <br><br>az700632.vo.msecnd.net<br><br>api.vstsusers.visualstudio.com/profiles/* | 443 | Służy do wyświetlania nazwy i awatara w środowisku IDE <br><br> Służy do upewnienia się, że ustawienie zmienia dostęp z jednego komputera do drugiego |
| Ustawienia zdalne | az700632.vo.msecnd.net | 443 | Służy do wyłączania rozszerzeń, które są znane, aby spowodować problemy w programie Visual Studio |
| Narzędzia systemu Windows | developer.microsoft.com <br><br>dev.windows.com  <br><br>appdev.microsoft.com | https/443 | Używany w scenariuszach sklepu Windows App Store |
| Schemat JSON <br>Odnajdywanie <br><br>Schemat JSON <br>Definicja<br><br>Schemat JSON <br>Obsługa <br>Zasoby platformy Azure | json.schemastore.org <br>schemastoreorg.azurewebsites.net<br><br>json-schema.org<br><br>schema.management.azure.com | protokół http/80<br>https/443<br><br>protokół http/80<br><br>https/443 | Służy do odnajdywania i pobierania schematów JSON, których użytkownik może używać podczas edytowania dokumentów JSON <br><br>Służy do uzyskiwania schematu meta-walidacji dla JSON<br><br>Służy do uzyskiwania bieżącego schematu dla szablonów wdrażania Azure Resource Manager |
| Pakiet NPM <br>odnajdywanie | Skimdb.npmjs.com <br><br>Registry.npmjs.org <br><br>Api.npms.io | https/443<br><br>& http/80<br> https/443<br>https/443 | Wymagane do wyszukiwania pakietów NPM i używanych do instalacji pakietu skryptu po stronie klienta w projektach sieci Web |
| Pakiet Bower<br> ikony<br><br>Pakiet Bower <br>search | Bower.io <br><br>bowercache.azurewebsites.net <br>go.microsoft.com <br>Registry.bower.io | protokół http/80<br><br>https/443<br>protokół http/80<br>https/443 | Udostępnia domyślną ikonę pakietu Bower  <br><br>Zapewnia możliwość wyszukiwania pakietów Bower |
| NuGet<br><br>Pakiet NuGet<br> odnajdywanie | api.nuget.org <br>www.nuget.org <br>nuget.org <br>azuresearch-usnc.nuget.org <br>azuresearch-ussc.nuget.org <br>licenses.nuget.org <br>nuget.cdn.azure.cn <br>azuresearch-ea.nuget.org <br>azuresearch-sea.nuget.org <br><br>crl3.digicert.com <br>crl4.digicert.com <br>ocsp.digicert.com <br>cacerts.digicert.com | https/443<br><br>& http/80<br>https/443<br> | Służy do weryfikowania podpisanych pakietów NuGet.<br><br>Wymagane do wyszukiwania pakietów NuGet i wersji |
| Informacje o repozytorium GitHub | api.github.com | https/443 | Wymagane do uzyskania dodatkowych informacji na temat pakietów Bower |
| Linterów sieci Web | Eslint.org<br><br>www.Bing.com <br><br>www.coffeelint.org | protokół http/80 | |
| Cookiecutter<br>Szablon Eksploratora<br>odnajdywanie <br><br>Cookiecutter <br>Projekt Eksploratora<br> tworzenie | api.github.com <br>raw.githubusercontent.com <br>go.microsoft.com<br><br>pypi.org <br> pypi.python.org | https/443<br> | Służy do odnajdywania szablonów online z naszych zalecanych kanałów informacyjnych i repozytoriów GitHub <br><br>Służy do tworzenia projektu na podstawie szablonu cookiecutter, który wymaga jednokrotnej instalacji pakietu języka Python cookiecutter z poziomu indeksu pakietu języka Python (PyPI) |
| Pakiet języka Python <br>odnajdywanie<br><br>Pakiet języka Python <br>zarządzanie<br><br>Nowa <br>Python <br> projekt <br>szablonów | pypi.org<br> <br>pypi.python.org <br>bootstrap.pypa.io<br><br>go.microsoft.com | https/443 | Zapewnia możliwość wyszukiwania pakietów PIP<br><br>Używane do automatycznego instalowania PIP, jeśli brakuje <br><br>Służy do rozwiązywania następujących nowych szablonów projektów języka Python do adresów URL szablonów cookiecutter:<br> -Projekt klasyfikatora<br>— Projekt klastrowania <br> — Projekt regresji <br> -PyGame przy użyciu PyKinect <br> -Pyvot projekt |
| Sieć Web pakietu Office <br>dodatek <br> Manifest <br>Weryfikacja <br>Usługa | verificationservice.osi.office.net | https/443 | Służy do sprawdzania poprawności manifestów dla dodatków sieci Web pakietu Office |
| SharePoint i <br>Dodatki pakietu Office | sharepoint.com<br> office365.com<br> microsoftonline.com <br> outlook.com | https/443 | Służy do publikowania i testowania dodatków programu SharePoint i pakietu Office do usługi SharePoint Online i pakietu Office 365 |
| Menedżer przepływów pracy <br>Usługa testowa<br> Host | | http/12292 | Reguła zapory, która jest tworzona automatycznie dla testowania dodatków programu SharePoint przy użyciu przepływów pracy |
| Zbierane automatycznie <br>Statystyka niezawodności <br>i inne <br>Obsługa klienta <br>Programy poprawy jakości obsługi klienta (CEIP)<br> dla zestawu Azure SDK i <br>dla narzędzi SQL <br><br> | vortex.data.microsoft.com<br> <br>dc.services.visualstudio.com | https/443 | Służy do wysyłania statystyk dotyczących niezawodności (danych awarii/zawieszenia) od użytkownika do firmy Microsoft. Rzeczywiste zrzuty awarii/zawieszenia będą nadal przekazywane, Jeśli Raportowanie błędów systemu Windows jest włączona; tylko informacje statystyczne zostaną pominięte; <br>Służy do ujawniania anonimowych wzorców użycia rozszerzenia zestawu SDK narzędzi platformy Azure do programu Visual Studio oraz dla wzorców użycia narzędzi SQL dla programu Visual Studio |
| Visual Studio <br> Obsługa klienta <br>Program poprawy jakości obsługi klienta (CEIP) <br><br>PerfWatson.exe | vortex.data.microsoft.com<br>dc.services.visualstudio.com<br>visualstudio-devdiv-c2s.msedge.net<br>az667904.vo.msecnd.net <br>scus-breeziest-in.cloudapp.net<br> | https/443 | Służy do zbierania anonimowych wzorców użycia i dzienników błędów <br><br>Służy do śledzenia problemów z blokowaniem interfejsu użytkownika |
| Tworzenie i<br>Zarządzanie <br>Zasoby platformy Azure | management.azure.com <br>management.core.windows.net | https/443 | Służy do tworzenia usługi Azure Websites lub innych zasobów w celu obsługi publikowania aplikacji sieci Web, Azure Functions lub zadań WebJob |
| Zaktualizowano narzędzia do publikacji w sieci Web <br>sprawdzenia i rozszerzenie <br>zalecenia | marketplace.visualstudio.com | https/443 | Służy do sprawdzania dostępności zaktualizowanych narzędzi publikacji. Jeśli ta wartość jest wyłączona, możliwe jest, że zalecane rozszerzenie publikacji w sieci Web nie może być wyświetlane |
| Zaktualizowano zasób platformy Azure <br>Informacje o punkcie końcowym tworzenia | \*.blob.core.windows.net | https/443 | Służy do aktualizowania punktów końcowych używanych do tworzenia zasobów platformy Azure dla niektórych usług platformy Azure. Jeśli ta wartość jest wyłączona, zamiast tego są używane ostatnio pobierane lub wbudowane lokalizacje punktów końcowych |
| Debugowanie zdalne i <br>Zdalne profilowanie <br>Azure Websites | &#42;. cloudapp.net <br> &#42;. azurewebsites.net | 4022 | Służy do dołączania zdalnego debugera do usługi Azure Websites. Po wyłączeniu dołączenie zdalnego debugera do usługi Azure Websites nie będzie działało |
| Usługa Active Directory <br>Graph | graph.windows.net | https/443 | Używane do aprowizacji nowych aplikacji Azure Active Directory. Używany także przez dostawcę usługi połączonej z pakietem Office 365 MSGraph |
| Azure Functions <br>Aktualizacja interfejsu wiersza polecenia <br>Zaznacz | functionscdn.azureedge.net | https/443 | Służy do sprawdzania dostępności zaktualizowanych wersji interfejsu wiersza polecenia Azure Functions. Jeśli ta wartość jest wyłączona, zamiast tego zostanie użyty buforowana kopia (lub kopia wykonywana przez składnik Azure Functions) interfejsu wiersza polecenia |
| Cordova | npmjs.org<br>gradle.org | & http/80<br/>https/443 | Protokół HTTP jest używany do pobierania Gradle podczas kompilacji; Protokół HTTPS jest używany do dołączania wtyczek Cordova do projektów |
| Eksplorator chmury | 1. &#60;clusterendpoint&#62; <br>Service Fabric <br>2. &#60;punkt końcowy zarządzania&#62;<br>Ogólna usługa wydatków w chmurze <br>3. &#60;punkt końcowy programu Graph&#62;<br>Ogólna usługa wydatków w chmurze<br>4. &#60;punktu końcowego konta magazynu&#62;<br>Węzły magazynu <br>5. &#60;adresy URL Azure Portal&#62;<br>Ogólna usługa wydatków w chmurze <br>6. &#60;punkty końcowe magazynu kluczy&#62; <br>Azure Resource Manager węzły maszyny wirtualnej<br>7. &#60;PublicIPAddressOfCluster&#62;<br>Service Fabric debugowanie zdalne i śledzenie ETW | <br>1. https/19080<br>2. https/443<br>3. https/443<br>4. https/443<br>5. https/443<br>6. https/443<br>7. TCP/dynamiczny | 1. przykład: test12.eastus.cloudapp.com<br>2. pobiera subskrypcje i pobiera/zarządza zasobami platformy Azure<br>3. pobiera Azure Stack subskrypcje<br>4. zarządza zasobami magazynu (przykład: mystorageaccount.blob.core.windows.net)<br>5. opcja menu kontekstowego "Otwórz w portalu" (otwiera zasób w Azure Portal)<br>6. tworzy i używa magazynów kluczy na potrzeby debugowania maszyn wirtualnych (przykład: myvault.vault.azure.net) <br><br>7. dynamicznie przydziela blok portów na podstawie liczby węzłów w klastrze i dostępnych portów. <br><br>Blok portu spróbuje uzyskać trzykrotnie liczbę węzłów z co najmniej 10 portami.<br><br>W przypadku śladów przesyłania strumieniowego jest podejmowana próba pobrania bloku portu z 810. Jeśli którykolwiek z tych bloków portu jest już używany, podejmowana jest próba pobrania następnego bloku i tak dalej. (Moduł równoważenia obciążenia jest pusty, a następnie porty z 810 są najprawdopodobniej używane) <br><br>Podobnie w przypadku debugowania są zarezerwowane cztery zestawy bloków portów: <br>-connectorPort: 30398, <br>-forwarderPort: 31398, <br>-forwarderPortx86:31399,<br>-fileUploadPort: 32398<br> |
| Cloud Services | 1. RDP<br><br>2. core.windows.net <br><br>3. management.azure.com<br> management.core.windows.net <br><br>4. &#42;. blob.core.windows.net <br>&#42;.queue.core.windows.net<br>&#42;.table.core.windows.net <br><br>5. portal.azure.com <br><br>6. &#60;w usłudze w chmurze użytkownika&#62;. cloudapp.net <br> &#60;&#62; maszyny wirtualnej użytkownika. &#60;regionu&#62;. azure.com | 1. rdp/3389 <br><br> 2. https/443 <br><br> 3. https/443 <br><br> 4. https/443 <br><br> 5. https/443 <br><br>6. TCP <br>a) 30398 <br>b) 30400 <br>c) 31398 <br>d) 31400 <br>e) 32398 <br>f) 32400 | 1. Pulpit zdalny do Cloud Services maszyny wirtualnej <br><br> 2. składnik konta magazynu prywatnej konfiguracji diagnostyki <br><br> 3. Azure Portal <br><br> 4. Eksplorator serwera — &#42; usługi Azure Storage to konto magazynu o nazwie klient  <br><br> 5. linki do otwierania portalu &#47; pobierania certyfikatu subskrypcji &#47; pliku ustawień publikowania <br><br>6. a) lokalny port łącznika dla zdalnego debugowania dla usługi w chmurze i maszyny wirtualnej<br> 6. b) port publiczny łącznika dla zdalnego debugowania dla usługi w chmurze i maszyny wirtualnej <br> 6. c) port lokalny usługi przesyłania dalej na potrzeby debugowania zdalnego dla usług w chmurze i maszyn wirtualnych <br> 6. d) port publiczny usługi przesyłania dalej dla zdalnego debugowania dla usługi w chmurze i maszyny wirtualnej  <br> 6. e) lokalny port obiektu przekazującego pliku na potrzeby debugowania zdalnego dla usługi w chmurze i maszyny wirtualnej <br> 6. f) obiektu przekazującego Publiczny port dla zdalnego debugowania dla usługi w chmurze i maszyny wirtualnej |
| Service Fabric | 1. <br>Licencja. Microsoft.com<br>aka.ms <br>go.microsoft.com <br><br>2. <br>vssftools.blob.core.windows.net <br>Vault.azure.com <br>Portal.azure.com <br><br> 3. &#42; vault.azure.net<br><br> 4. <br>app.vsaex.visualstudio.com<br>&#42;. vsspsext.visualstudio.com<br>clouds.vsrm.visualstudio.com <br>clouds.visualstudio.com<br>app.vssps.visualstudio.com <br>&#42;. visualstudio.com | https/443 | 1. Dokumentacja <br><br> 2. Utwórz funkcję klastra <br><br>3. &#42; to nazwa magazynu kluczy platformy Azure (przykład:-test11220180112110108.vault.azure.net  <br><br>  4. &#42; jest dynamiczna (przykład: vsspsextprodch1su1.vsspsext.visualstudio.com) |
| Snapshot <br>Debuger | 1. go.microsoft.com <br>2. management.azure.com <br> 3. &#42;. azurewebsites.net <br> 4. &#42;. scm.azurewebsites.net<br>5. api.nuget.org/v3/index.jsna <br>6. Usługa zdalna/adres IP serwerów/nazwa FQDN | 1. https/443 <br>2. https/443  <br>3. http/80 <br>4. https/443 <br>5. https/443 <br>6. Concord/<br> 4022 (zależna wersja programu Visual Studio) | 1. plik Query. JSON dla rozmiaru jednostki SKU usługi App Service <br>2. różne wywołania usługi Azure RM <br>3. wywołanie rozgrzewania lokacji za pośrednictwem  <br>4. dla klienta App Service kudu punkt końcowy <br>5. zapytanie o wersję rozszerzenia witryny opublikowaną w nuget.org <br>6. [debugowanie zdalne](../debugger/remote-debugging.md) |
| Usługa Azure Stream Analytics <br><br>HDInsight | Management.azure.com | https/443 | Służy do wyświetlania, przesyłania i uruchamiania zadań ASA oraz zarządzania nimi <br><br> Służy do przeglądania klastrów HDI oraz do przesyłania, diagnozowania i debugowania zadań HDI |
| Azure Data Lake | &#42;. azuredatalakestore.net <br>&#42;. azuredatalakeanalytics.net | https/443 | Służy do kompilowania, przesyłania, wyświetlania, diagnozowania i debugowania zadań; służy do przeglądania plików ADLS; służy do przekazywania i pobierania plików |
| Usługa tworzenia pakietów | [Account]. VisualStudio. com <br/> [konto]. \* . visualstudio.com <br/> \*.blob.core.windows.net <br/> registry.npmjs.org </br> nodejs.org <br/> dist.nuget.org <br/> nuget.org | https/443 | Klasy \* . npmjs.org, \* . NuGet.org i \* . NodeJS.org są wymagane tylko w przypadku niektórych scenariuszy zadań kompilacji (na przykład: Instalatora narzędzia NuGet, Instalatora narzędzia węzła) lub jeśli zamierzasz używać publicznego przesyłania strumieniowego ze źródłami danych. Pozostałe trzy domeny są wymagane do podstawowej funkcjonalności usługi pakowania. |
| Usługa Azure DevOps Services | \*. vsassets.io <br/> static2.sharepointonline.com <br/> dev.azure.com | | Używane do nawiązywania połączenia z Azure DevOps Services |
| Azure Service Bus | \*.servicebus.windows.net | ampq/5671 i 5672, </br> sbmp/9350-9354, </br> http/80, </br> https/443 | Służy do tworzenia kolejek, tematów i subskrypcji. </br> Służy również do wysyłania i odbierania komunikatów do/z Service Busch kolejek i tematów. |
| Azure Cosmos DB | \*. documents.azure.com | https/443 | Służy do wywoływania podstawowych interfejsów API bazy danych dokumentów. |
| Społeczność deweloperów | sendvsfeedback2.azurewebsites.net/api | https/443 | Służy do wywoływania interfejsów API narzędzia do oceny społeczności deweloperów (moje problemy, wyszukiwanie, głosowanie, komentarz, przesyłanie, przekazywanie, wznawianie) |
| Rozszerzenia intellicode | \*. intellicode.vsengsaas.visualstudio.com | https/443 | Używane do wywoływania interfejsów API rozszerzenia intellicode |
| Live Share | \*. liveshare.vsengsaas.visualstudio.com| https/443 | Używane do wywoływania Live Share interfejsów API |
| Visual Studio Codespaces | \*. online.visualstudio.com | https/443 | Używane do wywoływania interfejsów API programu Visual Studio Codespaces |
| Automatyczne pobieranie typu JavaScript | registry.npmjs.org | https/443 | Służy do instalowania definicji typów TypeScript w celu zapewnienia funkcji IntelliSense dla popularnych bibliotek JavaScript |
| Usługa licencjonowania subskrypcji programu Visual Studio | app.vssps.visualstudio.com/apis/<br/>Licencjonowanie/ClientRights | https/443 | Licencjonowanie aktywacji w trybie online |
| Debuger | 1. <br>vsdebugger.blob.core.windows.net <br>vsdebugger.azureedge.net <br><br>2. <br>download.visualstudio.com/\*/<br/>OneCore. msvsmon. \* .. kodu<br><br> 3. referencesource.microsoft.com/symbols <br><br> 4. <br>symbols.nuget.org/download/symbols<br><br> 5. visualstudio.com<br><br>6. msdl.microsoft.com/download/symbols | https/443 | 1. <br>Służy do pobierania BITS debugera dla debugowania .NET Core w systemie UNIX/macOS za pośrednictwem protokołu SSH <br><br>2. <br>Służy do pobierania BITS debugera dla zdalnego debugowania kontenerów platformy Docker systemu Windows<br><br> 3. używane do wykonywania kroków źródłowych programu .NET Framework <br><br> 4. <br>(Jeśli założenia użytkownika) Służy do pobierania symboli publikowanych na serwerze symboli nuget.org.<br><br> 5. (Jeśli użytkownik zdecyduje się na) służący do pobierania symboli i plików binarnych firmy Microsoft, może być również wymagany do debugowania kodu zarządzanego w zrzutach |
| Visual Studio Codespaces| \*. online.visualstudio.com | https/443 | Używane do wywoływania interfejsów API programu Visual Studio Codespaces |
| Publikowanie aplikacji platformy Xamarin dla systemu Android | \*. googleapis.com <br/> play.google.com <br/>accounts.google.com | https/443 | Służy do współpracy z usługą Sklep Google Play do publikowania/przekazywania aplikacji platformy Xamarin Android bezpośrednio z programu Visual Studio. |
| Azure Container Registry | *. azurecr.io | https/443 | Dostęp do rejestrów kontenerów hostowanych na platformie Azure w celu skonfigurowania potoków CICD |
| | | | |

## <a name="troubleshoot-network-related-errors"></a>Rozwiązywanie problemów związanych z siecią

Czasami może wystąpić błąd związany z siecią lub serwerem proxy podczas instalowania programu Visual Studio lub korzystania z niego za zaporą lub serwer proxy. Aby uzyskać więcej informacji o rozwiązaniach takich komunikatów o błędach, zobacz [Rozwiązywanie problemów związanych z siecią podczas instalowania lub używania strony programu Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md) .

## <a name="get-support"></a>Uzyskiwanie pomocy technicznej

Oferujemy opcję obsługi programu [**Chat**](https://visualstudio.microsoft.com/vs/support/#talktous) (tylko w języku angielskim) dla problemów związanych z instalacją.

Oto kilka dodatkowych opcji pomocy technicznej:

* Zgłoś problemy dotyczące produktów w firmie Microsoft za pomocą narzędzia [Zgłoś problem](../ide/how-to-report-a-problem-with-visual-studio.md) , które pojawia się zarówno w Instalator programu Visual Studio, jak i w środowisku IDE programu Visual Studio.
* Zaproponuj funkcję, śledź problemy dotyczące produktów i Znajdź odpowiedzi w [społeczności deweloperów programu Visual Studio](https://developercommunity.visualstudio.com/).
* Użyj swojego konta w usłudze [GitHub](https://github.com/) , aby komunikować się z nami i innych deweloperów programu Visual Studio w [konwersacji programu Visual Studio w społeczności warunkom](https://gitter.im/Microsoft/VisualStudio).

## <a name="see-also"></a>Zobacz też

* [Wymagania dotyczące łączności dla rozszerzenia Live Share](/visualstudio/liveshare/reference/connectivity/)
* [Tworzenie instalacji sieciowej programu Visual Studio](create-a-network-installation-of-visual-studio.md)
* [Rozwiązywanie problemów związanych z siecią w programie Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md)
* [Podręcznik administratora programu Visual Studio](visual-studio-administrator-guide.md)
* [Instalowanie za zaporą lub serwerem proxy (Visual Studio dla komputerów Mac)](/visualstudio/mac/install-behind-a-firewall-or-proxy-server)

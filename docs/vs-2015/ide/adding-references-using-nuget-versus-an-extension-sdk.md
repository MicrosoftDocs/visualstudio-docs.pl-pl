---
title: Dodawanie odwołań przy użyciu narzędzia NuGet w porównaniu z zestawem SDK | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.toolsoptionspages.nuget_package_manager.general
- vs.toolsoptionspages.nuget_package_manager.package_sources
ms.assetid: 2175581e-83cb-444c-bb52-cc1fca8ea196
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 95927385ce3218d73ba6b94819429163178bb65b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75917344"
---
# <a name="adding-references-using-nuget-versus-an-extension-sdk"></a>Różnice pomiędzy dodawaniem odwołań za pomocą NuGet a Extension SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz udostępnić pakiet do użycia w projektach programu Visual Studio, używając rozszerzenia NuGet do programu Visual Studio lub zestawu SDK (Software Development Kit). Opisując podobieństwa i różnice między tymi dwoma mechanizmami, ten temat może pomóc wybrać najlepszy dla zadania.

- NuGet to system zarządzania pakietami typu open source, który upraszcza proces dołączania bibliotek do rozwiązania projektu. Aby uzyskać więcej informacji, zobacz [Omówienie narzędzia NuGet](/nuget/what-is-nuget).

- Zestaw SDK to zbiór plików, które program Visual Studio traktuje jako pojedynczy element odniesienia. W oknie dialogowym **Menedżer odwołań** są wyświetlane wszystkie zestawy SDK, które są istotne dla projektu, który jest otwarty podczas wyświetlania tego okna dialogowego. Po dodaniu zestawu SDK do projektu możesz uzyskać dostęp do całej zawartości tego zestawu SDK za pomocą funkcji IntelliSense, **przybornika**, projektantów, **Przeglądarka obiektów**, MSBuild, wdrażania, debugowania i pakowania. Aby uzyskać więcej informacji na temat zestawów SDK, zobacz [Tworzenie zestawu Software Development Kit](../extensibility/creating-a-software-development-kit.md).

## <a name="which-mechanism-should-i-use"></a>Którego mechanizmu należy używać?
 Poniższa tabela zawiera porównanie funkcji odwołujących się do zestawu SDK z przywołującymi się do nich funkcjami programu NuGet.

|Cechy|Obsługa zestawu SDK|Uwagi dotyczące zestawu SDK|Obsługa NuGet|Uwagi dotyczące narzędzia NuGet|
|-------------|-----------------|---------------|-------------------|-----------------|
|Mechanizm odwołuje się do jednej jednostki, a następnie wszystkie pliki i funkcje są dostępne.|Y|Zestaw SDK można dodać przy użyciu okna dialogowego **Menedżer odwołań** , a wszystkie pliki i funkcje są dostępne podczas pracy deweloperskiej.|Y||
|Program MSBuild automatycznie korzysta z zestawów i plików metadanych systemu Windows (WinMD).|Y|Odwołania w zestawie SDK są automatycznie przenoszone do kompilatora.|Y||
|Program MSBuild automatycznie korzysta z plików. h lub. lib.|Y|Plik *SDKName*. props informuje program Visual Studio, jak skonfigurować katalog Visual C++ i tak dalej, aby umożliwić użycie plików. h lub. lib.|N||
|Program MSBuild automatycznie wykorzystuje pliki JS lub CSS.|Y|W **Eksplorator rozwiązań**można rozwinąć węzeł odwołania zestawu SDK języka JavaScript w celu wyświetlenia pojedynczych plików JS lub CSS, a następnie wygenerować `<source include/>` Tagi, przeciągając te pliki do plików źródłowych. Zestaw SDK obsługuje ustawienia F5 i Automatic Package.|Y||
|Program MSBuild automatycznie dodaje formant w **przyborniku**.|Y|**Przybornik** może korzystać z zestawów SDK i wyświetlać kontrolki na kartach, które określisz.|N||
|Mechanizm obsługuje Instalator programu Visual Studio rozszerzenia (VSIX).|Y|VSIX ma specjalny manifest i logikę do tworzenia pakietów SDK|Y|VSIX można osadzić w innym programie instalacyjnym.|
|**Przeglądarka obiektów** wylicza odwołania.|Y|**Przeglądarka obiektów** automatycznie pobiera listę odwołań w zestawach SDK i wylicza je.|N||
|Pliki i linki są automatycznie dodawane do okna dialogowego **Menedżer odwołań** (linki pomocy itd.)|Y|W oknie dialogowym **Menedżer odwołań** są automatycznie wyliczane zestawy SDK oraz linki pomocy i lista zależności zestawu SDK.|N|Pakiet NuGet udostępnia swoje własne okno dialogowe **Manage NuGet Packages** .|
|Mechanizm obsługuje wiele architektur.|Y|Zestawy SDK mogą dostarczać wiele konfiguracji. MSBuild korzysta z odpowiednich plików dla każdej konfiguracji projektu.|N||
|Mechanizm obsługuje wiele konfiguracji.|Y|Zestawy SDK mogą dostarczać wiele konfiguracji. W zależności od architektury projektu MSBuild korzysta z odpowiednich plików dla każdej architektury projektu.|N||
|Mechanizm może określić "nie do kopiowania".|Y|W zależności od tego, czy pliki są porzucane w folderze \redist lub \DesignTime, można kontrolować, które pliki mają być kopiowane do pakietu aplikacji zużywanej.|N|Należy zadeklarować pliki do skopiowania w manifeście pakietu.|
|Zawartość pojawia się w zlokalizowanych plikach.|Y|Zlokalizowane dokumenty XML w zestawach SDK są automatycznie dołączane w celu lepszego środowiska projektowania.|N||
|Program MSBuild obsługuje jednocześnie używanie wielu wersji zestawu SDK.|Y|Zestaw SDK obsługuje jednocześnie używanie wielu wersji.|N|Nie odwołuje się do niego. W projekcie nie można jednocześnie korzystać z więcej niż jednej wersji plików NuGet.|
|Mechanizm obsługuje określanie odpowiednich platform docelowych, wersji programu Visual Studio i typów projektów.|Y|W oknie dialogowym **Menedżer odwołań** i **przyborniku** są wyświetlane tylko zestawy SDK, które mają zastosowanie do projektu, dzięki czemu użytkownicy mogą łatwiej wybierać odpowiednie zestawy SDK.|T (częściowa)|Pivot jest platformą docelową. Nie istnieje filtrowanie w interfejsie użytkownika. Podczas instalacji może zostać zwrócony błąd.|
|Mechanizm obsługuje określanie informacji rejestracyjnych dla natywnych WinMD.|Y|Można określić korelację między plikiem. winmd a plikiem DLL w SDKManifest.xml.|N||
|Mechanizm obsługuje określanie zależności od innych zestawów SDK.|Y|Zestaw SDK powiadamia tylko użytkownika; Użytkownik musi je nadal zainstalować i ręcznie odwoływać się do nich.|Y|Pakiet NuGet pobiera je automatycznie; Użytkownik nie ma powiadomienia.|
|Mechanizm integruje się z  [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)] pojęciami, takimi jak manifest aplikacji i identyfikator struktury.|Y|Zestaw SDK musi przekazać koncepcje, które są specyficzne dla programu, [!INCLUDE[win8_appstore_short](../includes/win8-appstore-short-md.md)] Aby pakowanie i F5 działały poprawnie z zestawami SDK, które są dostępne w [!INCLUDE[win8_appstore_short](../includes/win8-appstore-short-md.md)] .|N||
|Mechanizm integruje się z potokiem debugowania aplikacji dla [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikacji.|Y|Zestaw SDK musi przekazywać [!INCLUDE[win8_appstore_short](../includes/win8-appstore-short-md.md)] konkretne koncepcje, aby pakowanie i F5 działały poprawnie z zestawami SDK dostępnymi w programie [!INCLUDE[win8_appstore_short](../includes/win8-appstore-short-md.md)] .|Y|Zawartość NuGet jest częścią projektu. Nie jest wymagana żadna Specjalna uwaga.|
|Mechanizm integruje się z manifestami aplikacji.|Y|Zestaw SDK musi przekazywać [!INCLUDE[win8_appstore_short](../includes/win8-appstore-short-md.md)] konkretne koncepcje, aby pakowanie i F5 działały poprawnie z zestawami SDK dostępnymi w programie [!INCLUDE[win8_appstore_short](../includes/win8-appstore-short-md.md)] .|Y|Zawartość NuGet jest częścią projektu. Nie jest wymagana żadna Specjalna uwaga.|
|Mechanizm wdraża pliki niebędące odwołaniami (na przykład wdrożenie środowiska testowego, na którym mają być uruchamiane testy [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikacji).|Y|Pliki w folderze \redist są wdrażane automatycznie.|Y||
|Mechanizm automatycznie dodaje zestawy SDK platformy w środowisku IDE programu Visual Studio.|Y|W przypadku porzucenia [!INCLUDE[win8](../includes/win8-md.md)] zestawu SDK lub zestawu Windows Phone SDK w określonej lokalizacji z określonym układem zestaw SDK zostanie automatycznie zintegrowany ze wszystkimi funkcjami programu Visual Studio.|N||
|Mechanizm obsługuje czystą maszynę dewelopera. (Oznacza to, że instalacja nie jest wymagana, a proste pobieranie z kontroli kodu źródłowego będzie działało).|N|Ponieważ odwołanie do zestawu SDK, należy najpierw zaewidencjonować rozwiązanie i zestaw SDK. Zestaw SDK można zaewidencjonować z poziomu dwóch domyślnych lokalizacji niezwiązanych z rejestrem, z których MSBuild iteruje zestawy SDK (Aby uzyskać szczegółowe informacje, zobacz [Tworzenie zestawu Software Development Kit](../extensibility/creating-a-software-development-kit.md)). Alternatywnie, jeśli lokalizacja niestandardowa składa się z zestawów SDK, można określić następujący kod w pliku projektu:<br /><br /> `<PropertyGroup>    <SDKReferenceDirectoryRoot>C:\MySDKs</SDKReferenceDirectoryRoot>   </PropertyGroup>`<br /><br /> Następnie sprawdź zestawy SDK w tej lokalizacji.|Y|Możesz wyewidencjonować rozwiązanie, a program Visual Studio natychmiast rozpoznaje pliki i działa z nich.|
|Możesz dołączyć do dużej istniejącej społeczności autorów pakietów.|Brak|Społeczność jest nowością.|Y||
|Możesz dołączyć do dużej istniejącej społeczności odbiorców pakietu.|Brak|Społeczność jest nowością.|Y||
|Możesz dołączyć do ekosystemu partnerów (galerii niestandardowych, repozytoriów itd.).|Brak|Dostępne repozytoria obejmują galerię programu Visual Studio, centrum pobierania Microsoft i [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)] .|Y||
|Mechanizm integruje się z serwerami kompilacji ciągłej integracji na potrzeby tworzenia i używania pakietów.|Y|Zestaw SDK musi przekazać zaznaczoną lokalizację (Właściwość SDKReferenceDirectoryRoot) w wierszu polecenia do programu MSBuild.|Y||
|Mechanizm obsługuje zarówno wersje stabilne, jak i w wersji wstępnej.|Y|Zestaw SDK obsługuje Dodawanie odwołań do wielu wersji.|Y||
|Mechanizm obsługuje funkcję autoaktualizowania zainstalowanych pakietów.|Y|Jeśli jest dostarczany jako VSIX lub część aktualizacji automatycznych programu Visual Studio, zestaw SDK udostępnia automatyczne powiadomienia.|Y||
|Mechanizm zawiera autonomiczny plik. exe do tworzenia i zużywania pakietów.|Y|Zestaw SDK zawiera MSBuild.exe.|Y||
|Pakiety mogą być zaewidencjonowane do kontroli wersji.|Y|Nie można zaewidencjonować niczego poza węzłem dokumentów, co oznacza, że zestawy SDK rozszerzeń mogą nie zostać zaewidencjonowane. Rozmiar rozszerzenia SDK może być duży.|Y||
|Za pomocą interfejsu programu PowerShell można tworzyć pakiety i korzystać z nich.|T (zużycie), N (Tworzenie)|Brak narzędzi do tworzenia zestawu SDK. Użycie wykonuje MSBuild w wierszu polecenia.|Y||
|Możesz użyć pakietu symboli do obsługi debugowania.|Y|Jeśli porzucasz pliki. pdb w zestawie SDK, pliki zostaną automatycznie pobrane.|Y||
|Mechanizm obsługuje aktualizacje za pomocą Menedżera pakietów.|Brak|Zestaw SDK jest aktualizowany przy użyciu programu MSBuild.|Y||
|Mechanizm obsługuje uproszczony format manifestu.|Y|SDKManifest.xml obsługuje wiele atrybutów, ale zazwyczaj niezbędny jest mały podzbiór.|Y||
|Mechanizm jest dostępny dla wszystkich wersji programu Visual Studio.|Y|Zestaw SDK obsługuje wszystkie wersje programu Visual Studio, od Visual Studio Express za pośrednictwem programu [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] .|Y|Pakiet NuGet obsługuje wszystkie wersje programu Visual Studio [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] .|
|Mechanizm jest dostępny dla wszystkich typów projektów.|N|Zestaw SDK obsługuje aplikacje, które są [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] uruchamiane w systemie [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] .|N|Możesz przejrzeć listę dozwolonych projektów.|

## <a name="see-also"></a>Zobacz też
 [Zarządzanie odwołaniami w projekcie](../ide/managing-references-in-a-project.md)

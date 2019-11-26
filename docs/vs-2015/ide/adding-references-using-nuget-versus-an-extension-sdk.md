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
ms.openlocfilehash: 63d9e6694fab400b1f29ed5e2706bb788a760357
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301268"
---
# <a name="adding-references-using-nuget-versus-an-extension-sdk"></a>Różnice pomiędzy dodawaniem odwołań za pomocą NuGet a Extension SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz udostępnić pakiet do użycia w projektach programu Visual Studio, używając rozszerzenia NuGet do programu Visual Studio lub zestawu SDK (Software Development Kit). Opisując podobieństwa i różnice między tymi dwoma mechanizmami, ten temat może pomóc wybrać najlepszy dla zadania.

- NuGet to system zarządzania pakietami typu open source, który upraszcza proces dołączania bibliotek do rozwiązania projektu. Aby uzyskać więcej informacji, zobacz [Omówienie narzędzia NuGet](https://go.microsoft.com/fwlink/?LinkId=254877).

- Zestaw SDK to zbiór plików, które program Visual Studio traktuje jako pojedynczy element odniesienia. W oknie dialogowym **Menedżer odwołań** są wyświetlane wszystkie zestawy SDK, które są istotne dla projektu, który jest otwarty podczas wyświetlania tego okna dialogowego. Po dodaniu zestawu SDK do projektu możesz uzyskać dostęp do całej zawartości tego zestawu SDK za pomocą funkcji IntelliSense, **przybornika**, projektantów, **Przeglądarka obiektów**, MSBuild, wdrażania, debugowania i pakowania. Aby uzyskać więcej informacji na temat zestawów SDK, zobacz [Tworzenie zestawu Software Development Kit](../extensibility/creating-a-software-development-kit.md).

## <a name="which-mechanism-should-i-use"></a>Którego mechanizmu należy używać?
 Poniższa tabela zawiera porównanie funkcji odwołujących się do zestawu SDK z przywołującymi się do nich funkcjami programu NuGet.

|Funkcja|Obsługa zestawu SDK|Uwagi dotyczące zestawu SDK|Obsługa NuGet|Uwagi dotyczące narzędzia NuGet|
|-------------|-----------------|---------------|-------------------|-----------------|
|Mechanizm odwołuje się do jednej jednostki, a następnie wszystkie pliki i funkcje są dostępne.|T|Zestaw SDK można dodać przy użyciu okna dialogowego **Menedżer odwołań** , a wszystkie pliki i funkcje są dostępne podczas pracy deweloperskiej.|T||
|Program MSBuild automatycznie korzysta z zestawów i plików metadanych systemu Windows (WinMD).|T|Odwołania w zestawie SDK są automatycznie przenoszone do kompilatora.|T||
|Program MSBuild automatycznie korzysta z plików. h lub. lib.|T|Plik *SDKName*. props informuje program Visual Studio, jak skonfigurować katalog wizualny C++ i tak dalej, aby umożliwić użycie plików. h lub. lib.|N||
|Program MSBuild automatycznie wykorzystuje pliki JS lub CSS.|T|W **Eksplorator rozwiązań**można rozwinąć węzeł odwołania zestawu SDK języka JavaScript w celu wyświetlenia pojedynczych plików JS lub CSS, a następnie wygenerować Tagi `<source include/>`, przeciągając te pliki do plików źródłowych. Zestaw SDK obsługuje ustawienia F5 i Automatic Package.|T||
|Program MSBuild automatycznie dodaje formant w **przyborniku**.|T|**Przybornik** może korzystać z zestawów SDK i wyświetlać kontrolki na kartach, które określisz.|N||
|Mechanizm obsługuje Instalator programu Visual Studio rozszerzenia (VSIX).|T|VSIX ma specjalny manifest i logikę do tworzenia pakietów SDK|T|VSIX można osadzić w innym programie instalacyjnym.|
|**Przeglądarka obiektów** wylicza odwołania.|T|**Przeglądarka obiektów** automatycznie pobiera listę odwołań w zestawach SDK i wylicza je.|N||
|Pliki i linki są automatycznie dodawane do okna dialogowego **Menedżer odwołań** (linki pomocy itd.)|T|W oknie dialogowym **Menedżer odwołań** są automatycznie wyliczane zestawy SDK oraz linki pomocy i lista zależności zestawu SDK.|N|Pakiet NuGet udostępnia swoje własne okno dialogowe **Manage NuGet Packages** .|
|Mechanizm obsługuje wiele architektur.|T|Zestawy SDK mogą dostarczać wiele konfiguracji. MSBuild korzysta z odpowiednich plików dla każdej konfiguracji projektu.|N||
|Mechanizm obsługuje wiele konfiguracji.|T|Zestawy SDK mogą dostarczać wiele konfiguracji. W zależności od architektury projektu MSBuild korzysta z odpowiednich plików dla każdej architektury projektu.|N||
|Mechanizm może określić "nie do kopiowania".|T|W zależności od tego, czy pliki są porzucane w folderze \redist lub \DesignTime, można kontrolować, które pliki mają być kopiowane do pakietu aplikacji zużywanej.|N|Należy zadeklarować pliki do skopiowania w manifeście pakietu.|
|Zawartość pojawia się w zlokalizowanych plikach.|T|Zlokalizowane dokumenty XML w zestawach SDK są automatycznie dołączane w celu lepszego środowiska projektowania.|N||
|Program MSBuild obsługuje jednocześnie używanie wielu wersji zestawu SDK.|T|Zestaw SDK obsługuje jednocześnie używanie wielu wersji.|N|Nie odwołuje się do niego. W projekcie nie można jednocześnie korzystać z więcej niż jednej wersji plików NuGet.|
|Mechanizm obsługuje określanie odpowiednich platform docelowych, wersji programu Visual Studio i typów projektów.|T|W oknie dialogowym **Menedżer odwołań** i **przyborniku** są wyświetlane tylko zestawy SDK, które mają zastosowanie do projektu, dzięki czemu użytkownicy mogą łatwiej wybierać odpowiednie zestawy SDK.|T (częściowa)|Pivot jest platformą docelową. Nie istnieje filtrowanie w interfejsie użytkownika. Podczas instalacji może zostać zwrócony błąd.|
|Mechanizm obsługuje określanie informacji rejestracyjnych dla natywnych WinMD.|T|Można określić korelację między plikiem. winmd a plikiem DLL w SDKManifest. XML.|N||
|Mechanizm obsługuje określanie zależności od innych zestawów SDK.|T|Zestaw SDK powiadamia tylko użytkownika; Użytkownik musi je nadal zainstalować i ręcznie odwoływać się do nich.|T|Pakiet NuGet pobiera je automatycznie; Użytkownik nie ma powiadomienia.|
|Mechanizm integruje się z pojęciami [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)], takimi jak manifest aplikacji i identyfikator struktury.|T|Zestaw SDK musi przekazać koncepcje charakterystyczne dla [!INCLUDE[win8_appstore_short](../includes/win8-appstore-short-md.md)] tak, aby pakowanie i F5 działały poprawnie z zestawami SDK, które są dostępne w[!INCLUDE[win8_appstore_short](../includes/win8-appstore-short-md.md)].|N||
|Mechanizm integruje się z potokiem debugowania aplikacji dla [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikacji.|T|Zestaw SDK musi przekazać koncepcje zależne od [!INCLUDE[win8_appstore_short](../includes/win8-appstore-short-md.md)], aby pakowanie i F5 działały poprawnie z zestawami SDK dostępnymi w [!INCLUDE[win8_appstore_short](../includes/win8-appstore-short-md.md)].|T|Zawartość NuGet jest częścią projektu. Nie jest wymagana żadna Specjalna uwaga.|
|Mechanizm integruje się z manifestami aplikacji.|T|Zestaw SDK musi przekazać koncepcje zależne od [!INCLUDE[win8_appstore_short](../includes/win8-appstore-short-md.md)], aby pakowanie i F5 działały poprawnie z zestawami SDK dostępnymi w [!INCLUDE[win8_appstore_short](../includes/win8-appstore-short-md.md)].|T|Zawartość NuGet jest częścią projektu. Nie jest wymagana żadna Specjalna uwaga.|
|Mechanizm wdraża pliki niebędące odwołaniami (na przykład wdrożenie środowiska testowego, na którym mają być uruchamiane testy aplikacji [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]).|T|Pliki w folderze \redist są wdrażane automatycznie.|T||
|Mechanizm automatycznie dodaje zestawy SDK platformy w środowisku IDE programu Visual Studio.|T|W przypadku porzucenia zestawu SDK [!INCLUDE[win8](../includes/win8-md.md)] lub zestawu Windows Phone SDK w określonej lokalizacji z określonym układem zestaw SDK zostanie automatycznie zintegrowany ze wszystkimi funkcjami programu Visual Studio.|N||
|Mechanizm obsługuje czystą maszynę dewelopera. (Oznacza to, że instalacja nie jest wymagana, a proste pobieranie z kontroli kodu źródłowego będzie działało).|N|Ponieważ odwołanie do zestawu SDK, należy najpierw zaewidencjonować rozwiązanie i zestaw SDK. Zestaw SDK można zaewidencjonować z poziomu dwóch domyślnych lokalizacji niezwiązanych z rejestrem, z których MSBuild iteruje zestawy SDK (Aby uzyskać szczegółowe informacje, zobacz [Tworzenie zestawu Software Development Kit](../extensibility/creating-a-software-development-kit.md)). Alternatywnie, jeśli lokalizacja niestandardowa składa się z zestawów SDK, można określić następujący kod w pliku projektu:<br /><br /> `<PropertyGroup>    <SDKReferenceDirectoryRoot>C:\MySDKs</SDKReferenceDirectoryRoot>   </PropertyGroup>`<br /><br /> Następnie sprawdź zestawy SDK w tej lokalizacji.|T|Możesz wyewidencjonować rozwiązanie, a program Visual Studio natychmiast rozpoznaje pliki i działa z nich.|
|Możesz dołączyć do dużej istniejącej społeczności autorów pakietów.|N/D|Społeczność jest nowością.|T||
|Możesz dołączyć do dużej istniejącej społeczności odbiorców pakietu.|N/D|Społeczność jest nowością.|T||
|Możesz dołączyć do ekosystemu partnerów (galerii niestandardowych, repozytoriów itd.).|N/D|Dostępne repozytoria obejmują galerię programu Visual Studio, centrum pobierania Microsoft i [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)].|T||
|Mechanizm integruje się z serwerami kompilacji ciągłej integracji na potrzeby tworzenia i używania pakietów.|T|Zestaw SDK musi przekazać zaznaczoną lokalizację (Właściwość SDKReferenceDirectoryRoot) w wierszu polecenia do programu MSBuild.|T||
|Mechanizm obsługuje zarówno wersje stabilne, jak i w wersji wstępnej.|T|Zestaw SDK obsługuje Dodawanie odwołań do wielu wersji.|T||
|Mechanizm obsługuje funkcję autoaktualizowania zainstalowanych pakietów.|T|Jeśli jest dostarczany jako VSIX lub część aktualizacji automatycznych programu Visual Studio, zestaw SDK udostępnia automatyczne powiadomienia.|T||
|Mechanizm zawiera autonomiczny plik. exe do tworzenia i zużywania pakietów.|T|Zestaw SDK zawiera program MSBuild. exe.|T||
|Pakiety mogą być zaewidencjonowane do kontroli wersji.|T|Nie można zaewidencjonować niczego poza węzłem dokumentów, co oznacza, że zestawy SDK rozszerzeń mogą nie zostać zaewidencjonowane. Rozmiar rozszerzenia SDK może być duży.|T||
|Za pomocą interfejsu programu PowerShell można tworzyć pakiety i korzystać z nich.|T (zużycie), N (Tworzenie)|Brak narzędzi do tworzenia zestawu SDK. Użycie wykonuje MSBuild w wierszu polecenia.|T||
|Możesz użyć pakietu symboli do obsługi debugowania.|T|Jeśli porzucasz pliki. pdb w zestawie SDK, pliki zostaną automatycznie pobrane.|T||
|Mechanizm obsługuje aktualizacje za pomocą Menedżera pakietów.|N/D|Zestaw SDK jest aktualizowany przy użyciu programu MSBuild.|T||
|Mechanizm obsługuje uproszczony format manifestu.|T|SDKManifest. XML obsługuje wiele atrybutów, ale zazwyczaj niezbędny jest mały podzbiór.|T||
|Mechanizm jest dostępny dla wszystkich wersji programu Visual Studio.|T|Zestaw SDK obsługuje wszystkie wersje programu Visual Studio, od Visual Studio Express do [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)].|T|Pakiet NuGet obsługuje wszystkie wersje programu Visual Studio, w tym [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)].|
|Mechanizm jest dostępny dla wszystkich typów projektów.|N|Zestaw SDK obsługuje aplikacje [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)], począwszy od [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].|N|Możesz przejrzeć listę dozwolonych projektów.|

## <a name="see-also"></a>Zobacz też
 [Zarządzanie odwołaniami w projekcie](../ide/managing-references-in-a-project.md)

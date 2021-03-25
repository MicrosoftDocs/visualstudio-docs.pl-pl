---
title: Różnice pomiędzy dodawaniem odwołań za pomocą NuGet a Extension SDK
description: Dowiedz się więcej o różnicach między oprogramowaniem pakietu jako pakietem NuGet lub zestawem SDK, gdy istnieje odwołanie w projekcie programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 08/02/2019
ms.topic: conceptual
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 74dd27db6372fa8b3712216f9efca6300dbc6d7d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090606"
---
# <a name="nuget-versus-sdk-as-a-project-reference"></a>Pakiet NuGet a zestaw SDK jako odwołanie do projektu

Ten artykuł został zaprojektowany, aby pomóc deweloperom w wyborze, czy spakować swoje oprogramowanie jako pakiet NuGet, czy jako zestaw SDK (Software Development Kit). W tym celu omawia różnice między tymi dwoma, gdy są one przywoływane w projekcie programu Visual Studio.

- [NuGet](/nuget) to system zarządzania pakietami typu "open source", który upraszcza proces dołączania bibliotek do projektu. W przypadku platformy .NET (w tym .NET Core) pakiet NuGet jest mechanizmem obsługiwanym przez firmę Microsoft w celu udostępniania kodu. Pakiet NuGet definiuje sposób tworzenia, obsługiwania i używania pakietów dla platformy .NET oraz udostępnia narzędzia dla każdej z tych ról. W programie Visual Studio Dodaj pakiety NuGet do projektu za pomocą interfejsu użytkownika [Menedżera pakietów](/nuget/consume-packages/install-use-packages-visual-studio) .

- [Zestaw SDK](../extensibility/creating-a-software-development-kit.md) to zbiór plików, które program Visual Studio traktuje jako pojedynczy element odniesienia. W oknie dialogowym Menedżer odwołań w programie Visual Studio są wyświetlane wszystkie zestawy SDK, które są istotne dla bieżącego projektu, gdy wybierzesz pozycję **Dodaj odwołanie**. Po dodaniu zestawu SDK do projektu możesz uzyskać dostęp do całej zawartości tego zestawu SDK za pomocą funkcji IntelliSense, okna przybornika, projektantów, Przeglądarka obiektów, MSBuild, wdrażania, debugowania i pakowania.

## <a name="which-mechanism-should-i-use"></a>Którego mechanizmu należy używać?

Poniższa tabela zawiera porównanie funkcji odwołujących się do zestawu SDK z przywołującymi się do nich funkcjami programu NuGet.

| Cecha | Obsługa zestawu SDK | Uwagi dotyczące zestawu SDK | Obsługa NuGet | Uwagi dotyczące narzędzia NuGet |
| - | - | - |---------------| - |
| Mechanizm odwołuje się do jednej jednostki, a następnie wszystkie pliki i funkcje są dostępne. | Y | Zestaw SDK można dodać przy użyciu okna dialogowego **Menedżer odwołań** , a wszystkie pliki i funkcje są dostępne podczas pracy deweloperskiej. | Y | |
| Program MSBuild automatycznie korzysta z zestawów i plików metadanych systemu Windows (*winmd*). | Y | Odwołania w zestawie SDK są automatycznie przenoszone do kompilatora. | Y | |
| Program MSBuild automatycznie korzysta z plików. h lub. lib. | Y | Plik *SDKName. props* informuje program Visual Studio, jak skonfigurować katalog Visual C++ i tak dalej, aby umożliwić użycie plików *. h* lub *. lib* . | N | |
| Program MSBuild automatycznie wykorzystuje pliki  *js* lub *CSS* . | Y | W **Eksplorator rozwiązań** można rozwinąć węzeł odwołania zestawu SDK języka JavaScript w celu wyświetlenia pojedynczych plików *js* lub *CSS* , a następnie wygenerować `<source include/>` Tagi, przeciągając te pliki do plików źródłowych. Zestaw SDK obsługuje ustawienia F5 i Automatic Package. | Y | |
| Program MSBuild automatycznie dodaje formant w **przyborniku**. | Y | **Przybornik** może korzystać z zestawów SDK i wyświetlać kontrolki na kartach, które określisz. | N | |
| Mechanizm obsługuje Instalator programu Visual Studio rozszerzenia (VSIX). | Y | VSIX ma specjalny manifest i logikę do tworzenia pakietów SDK | Y | VSIX można osadzić w innym programie instalacyjnym. |
| **Przeglądarka obiektów** wylicza odwołania. | Y | **Przeglądarka obiektów** automatycznie pobiera listę odwołań w zestawach SDK i wylicza je. | N | |
| Pliki i linki są automatycznie dodawane do okna dialogowego **Menedżer odwołań** (linki pomocy itd.) | Y | W oknie dialogowym **Menedżer odwołań** są automatycznie wyliczane zestawy SDK oraz linki pomocy i lista zależności zestawu SDK. | N | Pakiet NuGet udostępnia swoje własne okno dialogowe **Manage NuGet Packages** . |
| Mechanizm obsługuje wiele architektur. | Y | Zestawy SDK mogą dostarczać wiele konfiguracji. MSBuild korzysta z odpowiednich plików dla każdej konfiguracji projektu. | N | |
| Mechanizm obsługuje wiele konfiguracji. | Y | Zestawy SDK mogą dostarczać wiele konfiguracji. W zależności od architektury projektu MSBuild korzysta z odpowiednich plików dla każdej architektury projektu. | N | |
| Mechanizm może określić "nie do kopiowania". | Y | W zależności od tego, czy pliki są porzucane w folderze *\redist* lub *\DesignTime* , można kontrolować, które pliki mają być kopiowane do pakietu aplikacji zużywanej. | N | Należy zadeklarować pliki do skopiowania w manifeście pakietu. |
| Zawartość pojawia się w zlokalizowanych plikach. | Y | Zlokalizowane dokumenty XML w zestawach SDK są automatycznie dołączane w celu lepszego środowiska projektowania. | N | |
| Program MSBuild obsługuje jednocześnie używanie wielu wersji zestawu SDK. | Y | Zestaw SDK obsługuje jednocześnie używanie wielu wersji. | N | Nie odwołuje się do niego. W projekcie nie można jednocześnie korzystać z więcej niż jednej wersji plików NuGet. |
| Mechanizm obsługuje określanie odpowiednich platform docelowych, wersji programu Visual Studio i typów projektów. | Y | W oknie dialogowym **Menedżer odwołań** i **przyborniku** są wyświetlane tylko zestawy SDK, które mają zastosowanie do projektu, dzięki czemu użytkownicy mogą łatwiej wybierać odpowiednie zestawy SDK. | T (częściowa) | Pivot jest platformą docelową. Nie istnieje filtrowanie w interfejsie użytkownika. Podczas instalacji może zostać zwrócony błąd. |
| Mechanizm obsługuje określanie informacji rejestracyjnych dla natywnych WinMD. | Y | Można określić korelację między plikiem. winmd a plikiem DLL w *SDKManifest.xml*. | N | |
| Mechanizm obsługuje określanie zależności od innych zestawów SDK. | Y | Zestaw SDK powiadamia tylko użytkownika; Użytkownik musi je nadal zainstalować i ręcznie odwoływać się do nich. | Y | Pakiet NuGet pobiera je automatycznie; Użytkownik nie ma powiadomienia. |
| Mechanizm integruje się z  [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)] pojęciami, takimi jak manifest aplikacji i identyfikator struktury. | Y | Zestaw SDK musi przekazać koncepcje, które są specyficzne dla programu, [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] Aby pakowanie i F5 działały poprawnie z zestawami SDK, które są dostępne w [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] . | N | |
| Mechanizm integruje się z potokiem debugowania aplikacji dla [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplikacji. | Y | Zestaw SDK musi przekazywać [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] konkretne koncepcje, aby pakowanie i F5 działały poprawnie z zestawami SDK dostępnymi w programie [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] . | Y | Zawartość NuGet jest częścią projektu. Nie jest wymagana żadna Specjalna uwaga. |
| Mechanizm integruje się z manifestami aplikacji. | Y | Zestaw SDK musi przekazywać [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] konkretne koncepcje, aby pakowanie i F5 działały poprawnie z zestawami SDK dostępnymi w programie [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] . | Y | Zawartość NuGet jest częścią projektu. Nie jest wymagana żadna Specjalna uwaga. |
| Mechanizm wdraża pliki niebędące odwołaniami (na przykład wdrożenie środowiska testowego, na którym mają być uruchamiane testy [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplikacji). | Y | Pliki w folderze *\redist* są wdrażane automatycznie. | Y | |
| Mechanizm automatycznie dodaje zestawy SDK platformy w środowisku IDE programu Visual Studio. | Y | W przypadku porzucenia [!INCLUDE[win8](../debugger/includes/win8_md.md)] zestawu SDK lub zestawu Windows Phone SDK w określonej lokalizacji z określonym układem zestaw SDK zostanie automatycznie zintegrowany ze wszystkimi funkcjami programu Visual Studio. | N | |
| Mechanizm obsługuje czystą maszynę dewelopera. (Oznacza to, że instalacja nie jest wymagana, a proste pobieranie z kontroli kodu źródłowego będzie działało). | N | Ponieważ odwołanie do zestawu SDK, należy najpierw zaewidencjonować rozwiązanie i zestaw SDK. Zestaw SDK można zaewidencjonować z poziomu dwóch domyślnych lokalizacji niezwiązanych z rejestrem, z których MSBuild iteruje zestawy SDK (Aby uzyskać szczegółowe informacje, zobacz [Tworzenie zestawu Software Development Kit](../extensibility/creating-a-software-development-kit.md)). Alternatywnie, jeśli lokalizacja niestandardowa składa się z zestawów SDK, można określić następujący kod w pliku projektu:<br /><br />`<PropertyGroup>`<br />&nbsp;&nbsp;`<SDKReferenceDirectoryRoot>`<br />&nbsp;&nbsp;`C:\MySDKs`<br />&nbsp;&nbsp;`</SDKReferenceDirectoryRoot>`<br />`</PropertyGroup>`<br /><br /> Następnie sprawdź zestawy SDK w tej lokalizacji. | Y | Możesz wyewidencjonować rozwiązanie, a program Visual Studio natychmiast rozpoznaje pliki i działa z nich. |
| Możesz dołączyć do dużej istniejącej społeczności autorów pakietów. | Nie dotyczy | Społeczność jest nowością. | Y | |
| Możesz dołączyć do dużej istniejącej społeczności odbiorców pakietu. | Nie dotyczy | Społeczność jest nowością. | Y | |
| Możesz dołączyć do ekosystemu partnerów (galerii niestandardowych, repozytoriów itd.). | Nie dotyczy | Dostępne repozytoria obejmują Visual Studio Marketplace, centrum pobierania Microsoft i [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)] . | Y | |
| Mechanizm integruje się z serwerami kompilacji ciągłej integracji na potrzeby tworzenia i używania pakietów. | Y | Zestaw SDK musi przekazać zaznaczoną lokalizację (Właściwość SDKReferenceDirectoryRoot) w wierszu polecenia do programu MSBuild. | Y | |
| Mechanizm obsługuje zarówno wersje stabilne, jak i w wersji wstępnej. | Y | Zestaw SDK obsługuje Dodawanie odwołań do wielu wersji. | Y | |
| Mechanizm obsługuje funkcję autoaktualizowania zainstalowanych pakietów. | Y | Jeśli jest dostarczany jako VSIX lub część aktualizacji automatycznych programu Visual Studio, zestaw SDK udostępnia automatyczne powiadomienia. | Y | |
| Mechanizm zawiera autonomiczny plik *. exe* do tworzenia i zużywania pakietów. | Y | Zestaw SDK zawiera *MSBuild.exe*. | Y | |
| Pakiety mogą być zaewidencjonowane do kontroli wersji. | Y | Nie można zaewidencjonować niczego poza węzłem dokumentów, co oznacza, że zestawy SDK rozszerzeń mogą nie zostać zaewidencjonowane. Rozmiar rozszerzenia SDK może być duży. | Y | |
| Za pomocą interfejsu programu PowerShell można tworzyć pakiety i korzystać z nich. | T (zużycie), N (Tworzenie) | Brak narzędzi do tworzenia zestawu SDK. Użycie wykonuje MSBuild w wierszu polecenia. | Y | |
| Możesz użyć pakietu symboli do obsługi debugowania. | Y | Jeśli porzucasz pliki *. pdb* w zestawie SDK, pliki zostaną automatycznie pobrane. | Y | |
| Mechanizm obsługuje aktualizacje za pomocą Menedżera pakietów. | Nie dotyczy | Zestaw SDK jest aktualizowany przy użyciu programu MSBuild. | Y | |
| Mechanizm obsługuje uproszczony format manifestu. | Y | *SDKManifest.xml* obsługuje wiele atrybutów, ale zazwyczaj niezbędny jest mały podzbiór. | Y | |
| Mechanizm jest dostępny dla wszystkich wersji programu Visual Studio. | Y | Zestaw SDK obsługuje wszystkie wersje programu Visual Studio. | Y | Pakiet NuGet obsługuje wszystkie wersje programu Visual Studio. |

## <a name="see-also"></a>Zobacz też

- [Zarządzanie odwołaniami w projekcie](../ide/managing-references-in-a-project.md)
- [Zarządzanie odwołaniami w projekcie (Visual Studio dla komputerów Mac)](/visualstudio/mac/managing-references-in-a-project)

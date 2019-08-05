---
title: Różnice pomiędzy dodawaniem odwołań za pomocą NuGet a Extension SDK
ms.date: 08/02/2019
ms.topic: conceptual
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 372e82f9bb032ac5a81362017d2062ecf0d44e3f
ms.sourcegitcommit: a124076dfd6b4e5aecda4d01984fee7b0c034745
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/05/2019
ms.locfileid: "68795083"
---
# <a name="nuget-versus-sdk-as-a-project-reference"></a>Pakiet NuGet a zestaw SDK jako odwołanie do projektu

Ten artykuł został zaprojektowany, aby pomóc deweloperom w wyborze, czy spakować swoje oprogramowanie jako pakiet NuGet, czy jako zestaw SDK (Software Development Kit). W tym celu omawia różnice między tymi dwoma, gdy są one przywoływane w projekcie programu Visual Studio.

- [NuGet](/nuget) to system zarządzania pakietami typu "open source", który upraszcza proces dołączania bibliotek do projektu. W przypadku platformy .NET (w tym .NET Core) pakiet NuGet jest mechanizmem obsługiwanym przez firmę Microsoft w celu udostępniania kodu. Pakiet NuGet definiuje sposób tworzenia, obsługiwania i używania pakietów dla platformy .NET oraz udostępnia narzędzia dla każdej z tych ról. W programie Visual Studio Dodaj pakiety NuGet do projektu za pomocą interfejsu użytkownika [Menedżera pakietów](/nuget/consume-packages/install-use-packages-visual-studio) .

- [Zestaw SDK](../extensibility/creating-a-software-development-kit.md) to zbiór plików, które program Visual Studio traktuje jako pojedynczy element odniesienia. W oknie dialogowym Menedżer odwołań w programie Visual Studio są wyświetlane wszystkie zestawy SDK, które są istotne dla bieżącego projektu, gdy wybierzesz pozycję **Dodaj odwołanie**. Po dodaniu zestawu SDK do projektu możesz uzyskać dostęp do całej zawartości tego zestawu SDK za pomocą funkcji IntelliSense, okna przybornika, projektantów, Przeglądarka obiektów, MSBuild, wdrażania, debugowania i pakowania.

## <a name="which-mechanism-should-i-use"></a>Którego mechanizmu należy używać?

Poniższa tabela zawiera porównanie funkcji odwołujących się do zestawu SDK z przywołującymi się do nich funkcjami programu NuGet.

| Funkcja | Obsługa zestawu SDK | Uwagi dotyczące zestawu SDK | Obsługa NuGet | Uwagi dotyczące narzędzia NuGet |
| - | - | - |---------------| - |
| Mechanizm odwołuje się do jednej jednostki, a następnie wszystkie pliki i funkcje są dostępne. | T | Zestaw SDK można dodać przy użyciu okna dialogowego **Menedżer odwołań** , a wszystkie pliki i funkcje są dostępne podczas pracy deweloperskiej. | T | |
| Program MSBuild automatycznie korzysta z zestawów i plików metadanych systemu Windows (*winmd*). | T | Odwołania w zestawie SDK są automatycznie przenoszone do kompilatora. | T | |
| Program MSBuild automatycznie korzysta z plików. h lub. lib. | T | Plik *SDKName. props* informuje program Visual Studio, jak skonfigurować katalog wizualny C++ i tak dalej, aby umożliwić użycie plików *. h* lub *. lib* . | N | |
| Program MSBuild automatycznie wykorzystuje pliki *js* lub *CSS* . | T | W **Eksplorator rozwiązań**można rozwinąć węzeł odwołania zestawu SDK języka JavaScript w celu wyświetlenia pojedynczych plików *js* lub *CSS* , a następnie wygenerować `<source include/>` Tagi, przeciągając te pliki do plików źródłowych. Zestaw SDK obsługuje ustawienia F5 i Automatic Package. | T | |
| Program MSBuild automatycznie dodaje formant w **przyborniku**. | T | **Przybornik** może korzystać z zestawów SDK i wyświetlać kontrolki na kartach, które określisz. | N | |
| Mechanizm obsługuje Instalator programu Visual Studio rozszerzenia (VSIX). | T | VSIX ma specjalny manifest i logikę do tworzenia pakietów SDK | T | VSIX można osadzić w innym programie instalacyjnym. |
| **Przeglądarka obiektów** wylicza odwołania. | T | **Przeglądarka obiektów** automatycznie pobiera listę odwołań w zestawach SDK i wylicza je. | N | |
| Pliki i linki są automatycznie dodawane do okna dialogowego **Menedżer odwołań** (linki pomocy itd.) | T | W oknie dialogowym **Menedżer odwołań** są automatycznie wyliczane zestawy SDK oraz linki pomocy i lista zależności zestawu SDK. | N | Pakiet NuGet udostępnia swoje własne okno dialogowe **Manage NuGet Packages** . |
| Mechanizm obsługuje wiele architektur. | T | Zestawy SDK mogą dostarczać wiele konfiguracji. MSBuild korzysta z odpowiednich plików dla każdej konfiguracji projektu. | N | |
| Mechanizm obsługuje wiele konfiguracji. | T | Zestawy SDK mogą dostarczać wiele konfiguracji. W zależności od architektury projektu MSBuild korzysta z odpowiednich plików dla każdej architektury projektu. | N | |
| Mechanizm może określić "nie do kopiowania". | T | W zależności od tego, czy pliki są porzucane w folderze *\redist* lub *\DesignTime* , można kontrolować, które pliki mają być kopiowane do pakietu aplikacji zużywanej. | N | Należy zadeklarować pliki do skopiowania w manifeście pakietu. |
| Zawartość pojawia się w zlokalizowanych plikach. | T | Zlokalizowane dokumenty XML w zestawach SDK są automatycznie dołączane w celu lepszego środowiska projektowania. | N | |
| Program MSBuild obsługuje jednocześnie używanie wielu wersji zestawu SDK. | T | Zestaw SDK obsługuje jednocześnie używanie wielu wersji. | N | Nie odwołuje się do niego. W projekcie nie można jednocześnie korzystać z więcej niż jednej wersji plików NuGet. |
| Mechanizm obsługuje określanie odpowiednich platform docelowych, wersji programu Visual Studio i typów projektów. | T | W oknie dialogowym **Menedżer odwołań** i **przyborniku** są wyświetlane tylko zestawy SDK, które mają zastosowanie do projektu, dzięki czemu użytkownicy mogą łatwiej wybierać odpowiednie zestawy SDK. | T (częściowa) | Pivot jest platformą docelową. Nie istnieje filtrowanie w interfejsie użytkownika. Podczas instalacji może zostać zwrócony błąd. |
| Mechanizm obsługuje określanie informacji rejestracyjnych dla natywnych WinMD. | T | Można określić korelację między plikiem. winmd a plikiem DLL w *SDKManifest. XML*. | N | |
| Mechanizm obsługuje określanie zależności od innych zestawów SDK. | T | Zestaw SDK powiadamia tylko użytkownika; Użytkownik musi je nadal zainstalować i ręcznie odwoływać się do nich. | T | Pakiet NuGet pobiera je automatycznie; Użytkownik nie ma powiadomienia. |
| Mechanizm integruje się z [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)] pojęciami, takimi jak manifest aplikacji i identyfikator struktury. | T | Zestaw SDK musi przekazać koncepcje, które są specyficzne [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] dla programu, aby pakowanie i F5 działały poprawnie z zestawami SDK[!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)], które są dostępne w. | N | |
| Mechanizm integruje się z potokiem debugowania aplikacji dla [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplikacji. | T | Zestaw SDK musi przekazywać [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)]konkretne koncepcje, aby pakowanie i F5 działały poprawnie z zestawami SDK dostępnymi [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)]w programie. | T | Zawartość NuGet jest częścią projektu. Nie jest wymagana żadna Specjalna uwaga. |
| Mechanizm integruje się z manifestami aplikacji. | T | Zestaw SDK musi przekazywać [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)]konkretne koncepcje, aby pakowanie i F5 działały poprawnie z zestawami SDK dostępnymi [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)]w programie. | T | Zawartość NuGet jest częścią projektu. Nie jest wymagana żadna Specjalna uwaga. |
| Mechanizm wdraża pliki niebędące odwołaniami (na przykład wdrożenie środowiska testowego, na którym mają być uruchamiane [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] testy aplikacji). | T | Pliki w folderze *\redist* są wdrażane automatycznie. | T | |
| Mechanizm automatycznie dodaje zestawy SDK platformy w środowisku IDE programu Visual Studio. | T | W przypadku porzucenia [!INCLUDE[win8](../debugger/includes/win8_md.md)] zestawu SDK lub zestawu Windows Phone SDK w określonej lokalizacji z określonym układem zestaw SDK zostanie automatycznie zintegrowany ze wszystkimi funkcjami programu Visual Studio. | N | |
| Mechanizm obsługuje czystą maszynę dewelopera. (Oznacza to, że instalacja nie jest wymagana, a proste pobieranie z kontroli kodu źródłowego będzie działało). | N | Ponieważ odwołanie do zestawu SDK, należy najpierw zaewidencjonować rozwiązanie i zestaw SDK. Zestaw SDK można zaewidencjonować z poziomu dwóch domyślnych lokalizacji niezwiązanych z rejestrem, z których MSBuild iteruje zestawy SDK (Aby uzyskać szczegółowe informacje, zobacz [Tworzenie zestawu Software Development Kit](../extensibility/creating-a-software-development-kit.md)). Alternatywnie, jeśli lokalizacja niestandardowa składa się z zestawów SDK, można określić następujący kod w pliku projektu:<br /><br />`<PropertyGroup>`<br />&nbsp;&nbsp;`<SDKReferenceDirectoryRoot>`<br />&nbsp;&nbsp;`C:\MySDKs`<br />&nbsp;&nbsp;`</SDKReferenceDirectoryRoot>`<br />`</PropertyGroup>`<br /><br /> Następnie sprawdź zestawy SDK w tej lokalizacji. | T | Możesz wyewidencjonować rozwiązanie, a program Visual Studio natychmiast rozpoznaje pliki i działa z nich. |
| Możesz dołączyć do dużej istniejącej społeczności autorów pakietów. | Brak | Społeczność jest nowością. | T | |
| Możesz dołączyć do dużej istniejącej społeczności odbiorców pakietu. | Brak | Społeczność jest nowością. | T | |
| Możesz dołączyć do ekosystemu partnerów (galerii niestandardowych, repozytoriów itd.). | Brak | Dostępne repozytoria obejmują Visual Studio Marketplace, centrum pobierania Microsoft i [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)]. | T | |
| Mechanizm integruje się z serwerami kompilacji ciągłej integracji na potrzeby tworzenia i używania pakietów. | T | Zestaw SDK musi przekazać zaznaczoną lokalizację (Właściwość SDKReferenceDirectoryRoot) w wierszu polecenia do programu MSBuild. | T | |
| Mechanizm obsługuje zarówno wersje stabilne, jak i w wersji wstępnej. | T | Zestaw SDK obsługuje Dodawanie odwołań do wielu wersji. | T | |
| Mechanizm obsługuje funkcję autoaktualizowania zainstalowanych pakietów. | T | Jeśli jest dostarczany jako VSIX lub część aktualizacji automatycznych programu Visual Studio, zestaw SDK udostępnia automatyczne powiadomienia. | T | |
| Mechanizm zawiera autonomiczny plik *. exe* do tworzenia i zużywania pakietów. | T | Zestaw SDK zawiera program *MSBuild. exe*. | T | |
| Pakiety mogą być zaewidencjonowane do kontroli wersji. | T | Nie można zaewidencjonować niczego poza węzłem dokumentów, co oznacza, że zestawy SDK rozszerzeń mogą nie zostać zaewidencjonowane. Rozmiar rozszerzenia SDK może być duży. | T | |
| Za pomocą interfejsu programu PowerShell można tworzyć pakiety i korzystać z nich. | T (zużycie), N (Tworzenie) | Brak narzędzi do tworzenia zestawu SDK. Użycie wykonuje MSBuild w wierszu polecenia. | T | |
| Możesz użyć pakietu symboli do obsługi debugowania. | T | Jeśli porzucasz pliki *. pdb* w zestawie SDK, pliki zostaną automatycznie pobrane. | T | |
| Mechanizm obsługuje aktualizacje za pomocą Menedżera pakietów. | Brak | Zestaw SDK jest aktualizowany przy użyciu programu MSBuild. | T | |
| Mechanizm obsługuje uproszczony format manifestu. | T | *SDKManifest. XML* obsługuje wiele atrybutów, ale zazwyczaj niezbędny jest mały podzbiór. | T | |
| Mechanizm jest dostępny dla wszystkich wersji programu Visual Studio. | T | Zestaw SDK obsługuje wszystkie wersje programu Visual Studio. | T | Pakiet NuGet obsługuje wszystkie wersje programu Visual Studio. |

## <a name="see-also"></a>Zobacz także

- [Zarządzanie odwołaniami w projekcie](../ide/managing-references-in-a-project.md)
- [Zarządzanie odwołaniami w projekcie (Visual Studio dla komputerów Mac)](/visualstudio/mac/managing-references-in-a-project)
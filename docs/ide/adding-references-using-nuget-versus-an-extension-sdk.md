---
title: Różnice pomiędzy dodawaniem odwołań za pomocą NuGet a Extension SDK
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 857cb1757919925c8ca28e3b07904450b1264277
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62975754"
---
# <a name="adding-references-using-nuget-versus-an-extension-sdk"></a>Dodawaniem odwołań za pomocą NuGet a extension SDK

Możesz podać pakiet do użycia w ramach projektów programu Visual Studio za pomocą NuGet lub zestaw software development kit (SDK). Poprzez opisanie podobieństwa i różnice między dwa mechanizmy, w tym artykule może pomóc wybrać najlepszy dla zadania.

- NuGet jest systemem zarządzania pakietami open source, który upraszcza dołączanie biblioteki do rozwiązania projektu. Aby uzyskać więcej informacji, zobacz [dokumentacja programu NuGet](/nuget).

- Zestaw SDK to zbiór plików, które program Visual Studio traktuje jako element jedno odwołanie. **Menadżer odwołań** okno dialogowe wyświetla listę wszystkich zestawów SDK, które są istotne dla projektu, który został otwarty podczas tego okna dialogowego. Po dodaniu zestawu SDK do projektu, możesz uzyskać dostęp do wszystkich zawartość tego zestawu SDK za pomocą funkcji IntelliSense, **przybornika**, projektantów oraz **przeglądarki obiektów**, MSBuild, wdrażania, debugowaniu i pakowaniu. Aby uzyskać więcej informacji na temat zestawów SDK, zobacz [tworzenia Software Development Kit](../extensibility/creating-a-software-development-kit.md).

## <a name="which-mechanism-should-i-use"></a>Jakie działania należy używać?

Poniższa tabela ułatwia porównanie odwołujący się funkcji odwołujący się funkcje pakietu nuget zestawu SDK.

| Funkcja | Obsługa zestawu SDK | Informacje o zestawu SDK | Obsługę pakietów NuGet | Informacje o NuGet |
| - | - | - |---------------| - |
| Mechanizm odwołuje się do jednej jednostki, a następnie wszystkie pliki i funkcje są dostępne. | T | Dodawanie zestawu SDK przy użyciu **Menadżer odwołań** okno dialogowe, a wszystkie pliki i funkcje są dostępne podczas tworzenia przepływu pracy. | T | |
| Program MSBuild automatycznie wykorzystuje zestawach i Windows metadanych (*winmd*) plików. | T | Odwołania do zestawu SDK są automatycznie przekazywane do kompilator. | T | |
| Program MSBuild używa automatycznie pliki .h lub lib. | T | *SDKName.props* plik informuje program Visual Studio, sposobu konfigurowania katalogu Visual C++ i tak dalej, aby uzyskać automatyczne *.h* lub *.lib* pliku zużycia. | N | |
| Automatycznie wykorzystuje MSBuild *js* lub *.css* plików. | T | W **Eksploratora rozwiązań**, można rozwinąć węzeł odniesienia zestaw SDK języka JavaScript, aby wyświetlić poszczególne *js* lub *.css* pliki, a następnie wygenerować `<source include/>` tagów, przeciągając te pliki do ich plików źródłowych. Zestaw SDK obsługuje klawisza F5 i automatyczne pakiet Instalatora. | T | |
| Program MSBuild automatycznie doda do formantu w **przybornika**. | T | **Przybornika** można używać zestawów SDK i pokazać kontrolki na kartach, które określisz. | N | |
| Ten mechanizm obsługuje Instalatora programu Visual Studio rozszerzenia (VSIX). | T | VSIX ma specjalne manifestu i logiki, aby utworzyć pakiety zestawu SDK | T | VSIX może być osadzony w inny program instalacyjny. |
| **Przeglądarki obiektów** wylicza odwołania. | T | **Przeglądarki obiektów** pobiera listę odwołań do zestawów SDK i wylicza je automatycznie. | N | |
| Pliki i łącza automatycznie dodane do **Menadżer odwołań** okno dialogowe (łącza pomocy i tak dalej automatycznego wypełniania) | T | **Menadżer odwołań** okno dialogowe automatycznie wylicza zestawy SDK, oraz łącza pomocy i Lista składników zależnych zestawu SDK. | N | NuGet udostępnia swoje własne **Zarządzaj pakietami NuGet** okno dialogowe. |
| Ten mechanizm obsługuje wielu architektur. | T | Zestawy SDK może wysłać wiele konfiguracji. Program MSBuild używa odpowiednich plików dla każdej konfiguracji projektu. | N | |
| Ten mechanizm obsługuje wiele konfiguracji. | T | Zestawy SDK może wysłać wiele konfiguracji. W zależności od architektury projektu MSBuild zużywa odpowiednie pliki dla każdej architektury projektu. | N | |
| Mechanizm określić, czy "nie kopia." | T | W zależności od tego, czy pliki są usuwane *\redist* lub *\designtime* folderu, można kontrolować, które pliki do skopiowania do pakietu aplikacja odbierająca komunikaty. | N | Możesz deklarować plików do skopiowania w manifeście pakietu. |
| Zawartość jest wyświetlana w zlokalizowanych plików. | T | Zlokalizowane dokumenty XML w zestawy SDK są automatycznie dołączane do lepszego środowiska czasu projektowania. | N | |
| Program MSBuild obsługuje jednoczesnego używania wielu wersji zestawu SDK. | T | Zestaw SDK obsługuje jednoczesnego używania wielu wersji. | N | To nie odwołuje się do. W czasie, nie może mieć więcej niż jedna wersja plików NuGet w projekcie. |
| Ten mechanizm obsługuje określenie odpowiednich docelowych struktur, wersji programu Visual Studio i typów projektów. | T | **Menadżer odwołań** okno dialogowe i **przybornika** Pokaż tylko zestawy SDK, które mają zastosowanie do projektu tak, aby użytkownicy mogą łatwiej wybrać odpowiednich zestawów SDK. | T (częściowa Obsługa) | Element przestawny jest platformę docelową. Nie ma żadnych filtrowania w interfejsie użytkownika. W trakcie instalacji może zwrócić błąd. |
| Mechanizm obsługuje określanie informacje o rejestracji Winmd natywnych. | T | Można określić korelacji między plikiem winmd i plik .dll w *SDKManifest.xml*. | N | |
| Ten mechanizm obsługuje określanie zależności od innych zestawów SDK. | T | Zestaw SDK powiadomi tylko użytkownika; Użytkownik nadal należy je zainstalować i odwoływać się do nich ręcznie. | T | NuGet pobiera je automatycznie. użytkownik nie jest powiadamiany. |
| Mechanizm integruje się z usługą [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)] pojęć, takich jak manifest aplikacji i identyfikator Framework. | T | Zestaw SDK musi pomyślnie przejść pojęcia, które są specyficzne dla [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] pakowania i F5 poprawnie pracować przy użyciu zestawów SDK, które są dostępne w[!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)]. | N | |
| Mechanizm integruje się z potoku na potrzeby debugowania aplikacji [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplikacji. | T | Zestaw SDK musi pomyślnie przejść [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)]-określonych tak, aby tworzenie pakietów i F5 działać poprawnie, przez zestawy SDK dostępne w [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)]. | T | Zawartość NuGet staje się częścią projektu. Nie szczególną ostrożność F5 jest wymagana. |
| Mechanizm integruje się z manifesty aplikacji. | T | Zestaw SDK musi pomyślnie przejść [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)]-określonych tak, aby tworzenie pakietów i F5 działać poprawnie, przez zestawy SDK dostępne w [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)]. | T | Zawartość NuGet staje się częścią projektu. Nie szczególną ostrożność F5 jest wymagana. |
| Mechanizm wdraża pliki-reference (na przykład wdrożyć struktury testowej, na których można uruchomić testy z [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplikacji). | T | Jeśli usuniesz pliki *\redist* folderów, pliki są automatycznie wdrażane. | T | |
| Mechanizm automatycznie dodaje zestawów SDK dla platformy w programie Visual Studio IDE. | T | Jeśli usuniesz [!INCLUDE[win8](../debugger/includes/win8_md.md)] zestawu SDK lub SDK Windows Phone w określonej lokalizacji przy użyciu określonego układu, zestaw SDK automatycznie jest zintegrowany ze wszystkimi funkcjami programu Visual Studio. | N | |
| Ten mechanizm obsługuje maszyny dewelopera czyste. (Oznacza to, że instalacja nie jest wymagana i będzie działać proste pobieranie z kontroli kodu źródłowego.) | N | Ponieważ można odwoływać się do zestawu SDK, należy zaewidencjonować rozwiązanie i zestawu SDK oddzielnie. Możesz sprawdzić w zestawie SDK z dwóch lokalizacji rejestru innego niż domyślny, z których program MSBuild wykonuje iteracje zestawów SDK (Aby uzyskać więcej informacji, zobacz [tworzenia Software Development Kit](../extensibility/creating-a-software-development-kit.md)). Alternatywnie Jeśli niestandardowej lokalizacji składa się z zestawów SDK, można określić następujący kod w pliku projektu:<br /><br />`<PropertyGroup>`<br />&nbsp;&nbsp;`<SDKReferenceDirectoryRoot>`<br />&nbsp;&nbsp;`C:\MySDKs`<br />&nbsp;&nbsp;`</SDKReferenceDirectoryRoot>`<br />`</PropertyGroup>`<br /><br /> Następnie sprawdź zestawy SDK do tej lokalizacji. | T | Można wyewidencjonować rozwiązania, a program Visual Studio od razu rozpoznaje i działa na plikach. |
| Możesz dołączyć dużą społeczność istniejących autorom pakietów. | Brak | Społeczność jest nowa. | T | |
| Możesz dołączyć dużą społeczność istniejących konsumentów pakietu. | Brak | Społeczność jest nowa. | T | |
| Możesz dołączyć ekosystemem partnerów (galerie niestandardowe, repozytoriów i tak dalej). | Brak | Dostępne repozytoriów obejmują Visual Studio Marketplace, Microsoft Download Center, i [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)]. | T | |
| Mechanizm integruje się z serwerów kompilacji ciągłej integracji, zarówno dla operacji tworzenia pakietu i użycia. | T | Zestaw SDK musi pomyślnie przejść zaewidencjonowanej w lokalizacji (właściwość SDKReferenceDirectoryRoot) w wierszu polecenia do programu MSBuild. | T | |
| Ten mechanizm obsługuje obie wersje pakietu stabilne i wersji wstępnej. | T | Zestaw SDK obsługuje dodawanie odwołania do wielu wersji. | T | |
| Ten mechanizm obsługuje automatyczne aktualizowanie zainstalowanych pakietów. | T | Jeśli dostarczane jako VSIX lub jej część automatyczne aktualizacje programu Visual Studio, zestaw SDK zapewnia automatyczne powiadomienia. | T | |
| Mechanizm zawiera autonomicznego *.exe* plik do tworzenia i używania pakietów. | T | Zestaw SDK zawiera *MSBuild.exe*. | T | |
| Pakietów można sprawdzić w taki sposób, w ramach kontroli wersji. | T | Nie można zaewidencjonować niczego poza węzeł dokumentów, co oznacza, że zestawów SDK rozszerzeń mogą nie zostać zaewidencjonowane. Rozmiar zestawu SDK rozszerzeń, może być duża. | T | |
| Interfejs programu PowerShell umożliwia tworzenie i korzystanie z pakietów. | T (zużycie), N (Tworzenie) | Nie narzędzia do tworzenia zestawu SDK. Użycie jest wykonywanie programu MSBuild w wierszu polecenia. | T | |
| Pakiet symboli służy do obsługi debugowania. | T | Jeśli usuniesz *.pdb* plików w zestawie SDK, pliki Pobierz pobierane automatycznie. | T | |
| Ten mechanizm obsługuje pakiet manager jest aktualizowany automatycznie. | Brak | Zestaw SDK pobiera zmian za pomocą narzędzia MSBuild. | T | |
| Ten mechanizm obsługuje lekki format manifestu. | T | *SDKManifest.xml* obsługuje wiele atrybutów, ale zazwyczaj konieczne jest niewielki ułamek. | T | |
| Ten mechanizm jest dostępna dla wszystkich wersji programu Visual Studio. | T | Zestaw SDK obsługuje wszystkich wersji programu Visual Studio. | T | NuGet obsługiwane są wszystkie wersje programu Visual Studio. |
| Ten mechanizm jest dostępna dla wszystkich typów projektów. | N | Zestaw SDK obsługuje [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplikacje, począwszy od [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]. | N | Możesz przejrzeć listę dozwolonych projektów. |

## <a name="see-also"></a>Zobacz także

- [Zarządzanie odwołaniami w projekcie](../ide/managing-references-in-a-project.md)
- [Zarządzanie odwołaniami w projekcie (Visual Studio dla komputerów Mac)](/visualstudio/mac/managing-references-in-a-project)
---
title: Różnice pomiędzy dodawaniem odwołań za pomocą NuGet a Extension SDK
ms.date: 08/02/2019
ms.topic: conceptual
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ad7fc9132647988aee46a2bb07e992505109d33c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702430"
---
# <a name="nuget-versus-sdk-as-a-project-reference"></a>NuGet kontra SDK jako odwołanie do projektu

Ten artykuł ma na celu pomóc deweloperom wybrać, czy pakiet ich oprogramowania jako pakiet NuGet lub jako zestaw do tworzenia oprogramowania (SDK). W szczególności omówiono różnice między tymi dwoma, gdy są one odwoływane w projekcie programu Visual Studio.

- [NuGet](/nuget) to system zarządzania pakietami typu open source, który upraszcza proces włączania bibliotek do projektu. Dla platformy .NET (w tym .NET Core) NuGet jest obsługiwanym przez firmę Microsoft mechanizmem udostępniania kodu. NuGet definiuje sposób tworzenia, hostowania i zużywania pakietów dla platformy .NET oraz narzędzia dla każdej z tych ról. W programie Visual Studio można dodać pakiety NuGet do projektu przy użyciu interfejsu użytkownika [Menedżera pakietów.](/nuget/consume-packages/install-use-packages-visual-studio)

- [SDK](../extensibility/creating-a-software-development-kit.md) jest zbiorem plików, które visual studio traktuje jako pojedynczy element odniesienia. Okno dialogowe Menedżer odwołań w programie Visual Studio zawiera listę wszystkich zestawienia SDK, które są istotne dla bieżącego projektu po **wybraniu**opcji Dodaj odwołanie . Po dodaniu zestawu SDK do projektu można uzyskać dostęp do całej zawartości tego zestawu SDK za pośrednictwem intellisense, okna przybornika, projektantów, przeglądarki obiektów, MSBuild, wdrożenia, debugowania i pakowania.

## <a name="which-mechanism-should-i-use"></a>Którego mechanizmu należy użyć?

Poniższa tabela ułatwia porównanie funkcji odwołujących się do sdk z funkcjami odwołującymi się do NuGet.

| Funkcja | Obsługa SDK | Uwagi dotyczące SDK | Pomoc techniczna nuget | Notatki NuGet |
| - | - | - |---------------| - |
| Mechanizm odwołuje się do jednej jednostki, a następnie wszystkie pliki i funkcje są dostępne. | Tak | Dodaj SDK za pomocą okna dialogowego **Menedżer odwołań,** a wszystkie pliki i funkcje są dostępne podczas tworzenia przepływu pracy. | Tak | |
| MSBuild automatycznie zużywa zestawy i pliki metadanych systemu Windows (*.winmd).* | Tak | Odwołania w zestawie SDK są automatycznie przekazywane do kompilatora. | Tak | |
| MSBuild automatycznie zużywa pliki .h lub .lib. | Tak | Plik *SDKName.props* informuje program Visual Studio, jak skonfigurować katalog Visual C++ itd. *.h* *.lib* | Nie | |
| MSBuild automatycznie zużywa pliki *.js* lub *css.* | Tak | W **Eksploratorze rozwiązań**można rozwinąć węzeł odwołania javascript SDK, aby `<source include/>` wyświetlić poszczególne pliki *.js* lub *css,* a następnie wygenerować znaczniki, przeciągając te pliki do ich plików źródłowych. Zestaw SDK obsługuje f5 i automatyczną konfigurację pakietów. | Tak | |
| MSBuild automatycznie dodaje formant w **przyborniku**. | Tak | **Przybornik** może korzystać z zestawów SDK i wyświetlać formanty na określonych kartach. | Nie | |
| Mechanizm obsługuje Instalator programu Visual Studio dla rozszerzeń (VSIX). | Tak | VSIX ma specjalny manifest i logikę do tworzenia pakietów SDK | Tak | VSIX może być osadzony w innym programie instalacyjnym. |
| **Przeglądarka obiektów** wylicza odwołania. | Tak | Przeglądarka **obiektów** automatycznie pobiera listę odwołań w SDK i wylicza je. | Nie | |
| Pliki i łącza są automatycznie dodawane do okna dialogowego **Menedżera odwołań** (łącza pomocy i tak dalej automatyczne wypełnianie) | Tak | Okno dialogowe **Menedżer odwołań** automatycznie wylicza pakiety SDK wraz z łączami pomocy i listą zależności SDK. | Nie | NuGet udostępnia własne okno dialogowe **Zarządzanie pakietami NuGet.** |
| Mechanizm obsługuje wiele architektur. | Tak | ZestawY SDK mogą wysyłać wiele konfiguracji. MSBuild zużywa odpowiednie pliki dla każdej konfiguracji projektu. | Nie | |
| Mechanizm obsługuje wiele konfiguracji. | Tak | ZestawY SDK mogą wysyłać wiele konfiguracji. W zależności od architektury projektu MSBuild zużywa odpowiednie pliki dla każdej architektury projektu. | Nie | |
| Mechanizm można określić "nie do kopiowania." | Tak | W zależności od tego, czy pliki są usuwane w folderze *\redist* czy *\designtime,* można kontrolować, które pliki mają być kopiowane do pakietu aplikacji zużywającej. | Nie | Deklarujesz, które pliki mają być kopiowane w manifeście pakietu. |
| Zawartość jest wyświetlana w zlokalizowanych plikach. | Tak | Zlokalizowane dokumenty XML w skusie SDK są automatycznie uwzględniane w celu uzyskania lepszego środowiska w czasie projektowania. | Nie | |
| MSBuild obsługuje jednoczesne korzystanie z wielu wersji zestawu SDK. | Tak | Zestaw SDK obsługuje jednoczesne korzystanie z wielu wersji. | Nie | To nie jest odniesienie. Nie można mieć więcej niż jedną wersję plików NuGet w projekcie w czasie. |
| Mechanizm obsługuje określanie odpowiednich struktur docelowych, wersji programu Visual Studio i typów projektów. | Tak | Okno dialogowe **Menedżer odwołań** i **przybornik pokazuje** tylko zestawy SDK, które mają zastosowanie do projektu, dzięki czemu użytkownicy mogą łatwiej wybrać odpowiednie zestawy SDK. | Y (częściowy) | Pivot jest platformą docelową. Nie ma filtrowania w interfejsie użytkownika. W czasie instalacji może zwrócić błąd. |
| Mechanizm obsługuje określanie informacji o rejestracji dla natywnych identyfikatorów WAMI. | Tak | Można określić korelację między plikiem .winmd a plikiem .dll w pliku *SDKManifest.xml*. | Nie | |
| Mechanizm obsługuje określanie zależności od innych zestawów SDK. | Tak | SDK tylko powiadamia użytkownika; użytkownik musi je zainstalować i odwoływać się do nich ręcznie. | Tak | NuGet ściąga je automatycznie; użytkownik nie jest powiadamiany. |
| Mechanizm integruje [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)] się z pojęć, takich jak manifest aplikacji i identyfikator framework. | Tak | SDK musi przejść pojęcia, które [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] są specyficzne dla tak, aby opakowanie i F5[!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)]działały poprawnie z SDK, które są dostępne w . | Nie | |
| Mechanizm integruje się z potoku [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] debugowania aplikacji dla aplikacji. | Tak | SDK musi [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)]przejść -specyficzne pojęcia tak, aby opakowanie i F5 działał [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)]poprawnie z SDK dostępne w . | Tak | Zawartość NuGet staje się częścią projektu. Nie jest wymagana żadna szczególna uwaga F5. |
| Mechanizm integruje się z manifestów aplikacji. | Tak | SDK musi [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)]przejść -specyficzne pojęcia tak, aby opakowanie i F5 działał [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)]poprawnie z SDK dostępne w . | Tak | Zawartość NuGet staje się częścią projektu. Nie jest wymagana żadna szczególna uwaga F5. |
| Mechanizm wdraża pliki nieskładkowe (na przykład wdrożyć [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] struktury testów, na których można uruchomić testy aplikacji). | Tak | Jeśli upuścisz pliki w folderze *\redist,* pliki zostaną automatycznie wdrożone. | Tak | |
| Mechanizm automatycznie dodaje platformy SDK w programie Visual Studio IDE. | Tak | Jeśli upuścisz [!INCLUDE[win8](../debugger/includes/win8_md.md)] SDK lub Windows Phone SDK w określonej lokalizacji z określonym układem, SDK zostanie automatycznie zintegrowany ze wszystkimi funkcjami programu Visual Studio. | Nie | |
| Mechanizm obsługuje czystą maszynę dewelopera. (Oznacza to, że instalacja nie jest wymagana, a proste pobieranie z kontroli kodu źródłowego będzie działać.) | Nie | Ponieważ odwołujesz się do SDK, należy zaewidencjonować rozwiązanie i SDK oddzielnie. Zestaw SDK można sprawdzić z dwóch domyślnych lokalizacji niebędących rejestrami, z których program MSBuild iteruje zestawy SDK (szczegółowe informacje można znaleźć w temacie [Tworzenie zestawu programistycznego).](../extensibility/creating-a-software-development-kit.md) Alternatywnie, jeśli lokalizacja niestandardowa składa się z SDK, można określić następujący kod w pliku projektu:<br /><br />`<PropertyGroup>`<br />&nbsp;&nbsp;`<SDKReferenceDirectoryRoot>`<br />&nbsp;&nbsp;`C:\MySDKs`<br />&nbsp;&nbsp;`</SDKReferenceDirectoryRoot>`<br />`</PropertyGroup>`<br /><br /> Następnie sprawdź sdk w tej lokalizacji. | Tak | Można wyewidencjonować rozwiązanie i Visual Studio natychmiast rozpoznaje i działa na pliki. |
| Możesz dołączyć do dużej istniejącej społeczności autorów pakietów. | Nie dotyczy | Społeczność jest nowa. | Tak | |
| Możesz dołączyć do dużej istniejącej społeczności konsumentów pakietów. | Nie dotyczy | Społeczność jest nowa. | Tak | |
| Możesz dołączyć do ekosystemu partnerów (niestandardowe galerie, repozytoria itd.). | Nie dotyczy | Dostępne repozytoria obejmują visual studio marketplace, Microsoft [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)]Download Center i . | Tak | |
| Mechanizm integruje się z serwerami kompilacji ciągłej integracji zarówno do tworzenia pakietów, jak i zużycia. | Tak | SDK musi przekazać lokalizację zaewidencjonowania (właściwość SDKReferenceDirectoryRoot) w wierszu polecenia do usługi MSBuild. | Tak | |
| Mechanizm obsługuje zarówno wersje pakietów stabilnych, jak i wersji wstępnej. | Tak | Zestaw SDK obsługuje dodawanie odwołań do wielu wersji. | Tak | |
| Mechanizm obsługuje automatyczną aktualizację zainstalowanych pakietów. | Tak | Jeśli są dostarczane jako VSIX lub część visual studio aktualizacji automatycznych, SDK zapewnia automatyczne powiadomienia. | Tak | |
| Mechanizm zawiera autonomiczny plik *exe* do tworzenia i korzystania z pakietów. | Tak | Plik SDK zawiera *plik MSBuild.exe*. | Tak | |
| Pakiety można sprawdzić w kontroli wersji. | Tak | Nie można zaewidencjonować niczego poza węzłem Dokumenty, co oznacza, że skomuny SDK rozszerzeń mogą nie zostać zaewidencjonowane. Rozmiar SDK rozszerzenia może być duży. | Tak | |
| Za pomocą interfejsu programu PowerShell można tworzyć i używać pakietów. | Y (zużycie), N (tworzenie) | Brak narzędzi do tworzenia zestawu SDK. Zużycie jest wykonywanie MSBuild w wierszu polecenia. | Tak | |
| Można użyć pakietu Symbol do debugowania obsługi. | Tak | Jeśli usuniesz pliki *pdb* w SDK, pliki będą pobierane automatycznie. | Tak | |
| Mechanizm obsługuje automatyczne aktualizacje menedżera pakietów. | Nie dotyczy | SDK zostanie poprawiony za pomocą MSBuild. | Tak | |
| Mechanizm obsługuje lekki format manifestu. | Tak | *SDKManifest.xml* obsługuje wiele atrybutów, ale mały podzbiór jest zwykle konieczne. | Tak | |
| Mechanizm jest dostępny dla wszystkich wersji programu Visual Studio. | Tak | Zestaw SDK obsługuje wszystkie wersje programu Visual Studio. | Tak | NuGet obsługuje wszystkie wersje programu Visual Studio. |

## <a name="see-also"></a>Zobacz też

- [Zarządzanie odwołaniami w projekcie](../ide/managing-references-in-a-project.md)
- [Zarządzanie odwołaniami w projekcie (Visual Studio dla komputerów Mac)](/visualstudio/mac/managing-references-in-a-project)

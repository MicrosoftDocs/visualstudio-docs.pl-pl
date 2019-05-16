---
title: Projektowanie XAML
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 288e2415-9fcf-408e-bc35-9848315e14fd
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 437c6cc7af2b0337b362e14db19deb9584a3d412
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65695538"
---
# <a name="designing-xaml-in-visual-studio"></a>Projektowanie XAML w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Program Visual Studio i Blend for Visual Studio udostępniają narzędzia wizualne dla kompilowania interesujące interfejsy użytkownika i rozbudowane treści multimedialne środowisk dla komputerów opartych na XAML Windows, sieci web, [Windows Phone](https://msdn.microsoft.com/library/windowsphone/develop/jj683071.aspx), i [Windows Store](https://msdn.microsoft.com/library/windows/apps/jj129478.aspx)aplikacji. Zarówno korzystają ze wspólnego zestawu, projektowania i okien narzędzi i Edytor XAML, ale program Blend for Visual Studio udostępnia narzędzia do projektowania dodatkowe dla bardziej zaawansowanych zadań, takich jak animacji i zachowania.

## <a name="choosing-the-right-tool"></a>Wybór właściwego narzędzia
 Ulubionego narzędzia projektowania jest w dużym stopniu zależy od zestawu umiejętności. Jeśli jesteś bardziej zorientowane na kod, można napisać kod XAML w programie Visual Studio do wykonywania zadań projektowania nawet Zaawansowane. Jeśli jesteś bardziej zorientowane na projekt, program Blend for Visual Studio umożliwia wykonywanie zaawansowanych zadań bez konieczności pisania kodu.

 Możesz przełączać się i z powrotem między Visual Studio i Blend for Visual Studio, a nawet może mieć tego samego projektu, otworzyć zarówno w tym samym czasie. Zmiany wprowadzone do plików XAML w jednym środowisku IDE można zastosować za pomocą automatyczne przeładowanie po przełączeniu się do innego środowiska IDE. Można kontrolować zachowanie Załaduj ponownie za pomocą opcji w **narzędzia**, **opcje** okno dialogowe, w dowolnym środowisku IDE.

### <a name="shared-capabilities"></a>Współdzielone możliwości
 Dla najbardziej podstawowe zadania środowisko IDE programu Visual Studio i Blend for Visual Studio udostępnianie tego samego zestawu windows oraz funkcje, pewne niewielkie różnice. Najważniejsze funkcje obejmują:

- **Spójny interfejs użytkownika:** Można zaprojektować aplikacje w ramach znanego interfejsu użytkownika programu Visual Studio, co sprawia, że przełączanie między środowiskami IDE użytkownikom przyjemny i bardziej produktywne. Blend dla Visual Studio używa programu Visual Studio ciemny motyw, który pomoże Ci skupić się na zawartość, którą projektujesz, skracając kontrast między treścią użytkownika a interfejsem użytkownika. Zobacz [Tworzenie interfejsu użytkownika przy użyciu projektanta XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

     ![Program Blend for Visual Studio IDE](../designers/media/blendide.png "BlendIDE")

- **Funkcja XAML IntelliSense:** Oba środowiska IDE obsługuje wszystkie typowe funkcje, których można oczekiwać od uzupełniania instrukcji, obsługa typowych operacji edytora, takich jak komentowania i formatowanie kodu i nawigacji do zasobów, powiązania i kodu w tym funkcji IntelliSense.

- **Podstawowe możliwości debugowania:** Można teraz debugować w programie Blend, w tym ustawianie punktów przerwania w kodzie, aby debugować uruchomionej aplikacji. Aby zapewnić spójne środowisko debugowania w programie Visual Studio, program Blend for Visual Studio zawiera większość debugowania systemu windows i paski narzędzi programu Visual Studio. Zaawansowane możliwości debugowania, takie jak dane diagnostyczne i analiza kodu są dostępne tylko w programie Visual Studio. Zobacz [debugowania w programie Visual Studio](../debugger/debugging-in-visual-studio.md).

- **Środowisko ponownego ładowania pliku:** Edytowanie plików XAML w każdej Blend for Visual Studio lub Visual Studio i mieć edytowanych plików podczas przełączania między nimi Załaduj ponownie. Aby zminimalizować przestoje przepływu pracy, można teraz ustawić pliku preferencji Załaduj ponownie w oknie dialogowym ponowne załadowanie pliku.

     ![Środowisko ponownego ładowania pliku](../designers/media/blendfilereload.png "BlendFileReload")

- **Synchronizowane układy i ustawienia:** Układy niestandardowe umożliwiają zapisać i zastosować dostosowania układu okna narzędzia. Program Visual Studio zsynchronizuje te dostosowania i preferencje dotyczące programu Visual Studio i Blend for Visual Studio na maszynach po zalogowaniu się przy użyciu tego samego konta Microsoft. Zobacz [Dostosowywanie ustawień środowiska deweloperskiego w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

- **Typowe Eksploratora rozwiązań:** Eksplorator rozwiązań pozwala zorganizowany widok projektów i ich pliki, a także uzyskać dostęp do poleceń związanych z nimi. Za pomocą Eksploratora rozwiązań łatwiej jest pracować z projektami dużych przedsiębiorstw. Zobacz [rozwiązania i projekty](../ide/solutions-and-projects-in-visual-studio.md).

- **Team Explorer:** Za pomocą programu Team Explorer można zarządzać projektów z repozytoriami GIT lub TFS, ułatwiające współpracę zespołową. Zobacz [pracy w programie Team Explorer](https://msdn.microsoft.com/library/fd7a5cf7-7916-4fa0-b5e6-5a83cf377a02).

- **Pakiet NuGet:** Możesz zarządzać pakietami NuGet w programie Visual Studio i Blend for Visual Studio. NuGet to Menedżer pakietów dla platformy .NET Framework, która upraszcza instalacji i usuwania pakietów za pomocą rozwiązania.

## <a name="advanced-capabilities-in-blend-for-visual-studio"></a>Zaawansowane funkcje w programie Blend for Visual Studio
 Aby zwiększyć wydajność, należy wziąć pod uwagę przy użyciu Blend dla programu Visual Studio w celu uwzględnienia poniższych zadań. Są to obszary, w której program Blend for Visual Studio oferuje więcej szybkość i funkcjonalności niż Projektant programu Visual Studio lub kod samodzielnie.

|Zadanie|Visual Studio|Blend for Visual Studio|Więcej informacji|
|--------|-------------------|-----------------------------|----------------------|
|**Tworzenie animacji**|Brak narzędzia do projektowania nie animacje; należy utworzyć je programowo. Ta migracja wymaga zrozumienia Animacja i system chronometrażu w WPF i obszerną wiedzę kodowania.|Wizualne Tworzenie animacji i można przeglądać je w programie Blend for Visual Studio. Jest większa szybkość i dokładność niż Tworzenie animacji w kodzie. Możesz dodać wyzwalacze do obsługi interakcji z użytkownikiem i możesz przełączyć się do kodu w celu dodania obsługi zdarzeń i inne funkcje.|[Animowanie obiektów](../designers/animate-objects-in-xaml-designer.md)|
|**Przekształcając ścieżki do manipulowania łatwiejsze kształty i tekst**|Nieobsługiwane.|Po przekonwertowaniu ich na ścieżki, które zapewniają kontrolę lepiej edycji ułatwia subtelne lub znaczne zmiany do kształtów zewnętrznych (takich jak prostokąty i elipsy).  Możesz zmienić kształt lub łączenia ścieżek i utworzyć ścieżki złożone z wielu kształtów.<br /><br /> Można również przeprowadzić konwersję bloki tekstu do ścieżki do manipulowania nimi jako obrazy wektorowe.|[Rysowanie kształtów i ścieżek](../designers/draw-shapes-and-paths.md)|
|**Stosowanie interakcyjności w projekty interfejsu użytkownika**|Wymaga kodu C#, Visual Basic lub C++.|Przeciągnij i upuść zachowań na kontrolki, aby dodać interakcję do statyczne projekty. Zachowania są fragmenty kodu gotowych do użycia, które hermetyzują funkcje, takie jak przeciągania i upuszczania, powiększania i zmiany stanu wizualnego. Istnieje coraz większego zestawu zachowania, które możesz wybrać spośród i możesz utworzyć swój własny.<br /><br /> Każde działanie można następnie dostosować, zmieniając jego właściwości w programie Blend for Visual Studio lub przez dodanie obsługi zdarzeń w kodzie.|[Wstawianie kontrolek i modyfikowanie ich zachowania](../designers/insert-controls-and-modify-their-behavior-in-xaml-designer.md)|
|**Użyj kompozycji Adobe**|Nieobsługiwane.|Importuj Adobe FXG oraz PhotoShop, Illustrator kompozycji i implementują interfejs użytkownika w programie Blend for Visual Studio.|[Wstawianie obrazów, klipów wideo i klipów audio](../designers/insert-images-videos-and-audio-clips-in-xaml-designer.md)|
|**Edytuj formanty, szablony i style**|Wymaga kodowania i wiedzy na temat WPF — style i szablony.|Włącz obrazów w formancie.<br /><br /> Szablon narzędzi edycji Aby wprowadzić zmiany do kontrolek, stylów i szablonów za pomocą zaledwie kilkoma kliknięciami.<br /><br /> Na przykład można użyć programu Blend dla programu Visual Studio zasoby stylów, implementować wspólnych formantów WPF (takie jak przyciski, pola listy, paski przewijania, menu itd.) oraz zmieniać ich kolor, styl lub podstawowego szablonu bezpośrednio w programie Blend for Visual Studio. Można następnie przełączyć kod poprawek, jeśli chcesz.|[Modyfikowanie stylu obiektów](../designers/modify-the-style-of-objects-in-blend.md)|
|**Interfejs użytkownika łączą się z danymi**|Można utworzyć źródło danych z zasobów, takich jak bazy danych programu SQL Server, usługi WCF lub usług sieci web, obiektów lub listy programu SharePoint i powiązać źródła danych z formantów interfejsu użytkownika.<br /><br /> Dane w czasie projektowania musi zostać utworzony ręcznie dla środowisko interaktywne projektu.|Tworzenie danych przykładowych, łatwe do tworzenia prototypów i testowania aplikacji. Przełącz, aby dane na żywo, gdy wszystko będzie gotowe.<br /><br /> Blend dla możliwości istnieją zaległe Generowanie danych programu Visual Studio (można dodać nazwy, liczby, adresy URL zdjęcia w prosty sposób na bieżąco) i zaoszczędzić dużo czasu.<br /><br /> W przypadku danych na żywo można powiązać formantów interfejsu użytkownika do pliku XML lub do dowolnego źródła danych środowiska CLR.|[Wyświetlanie danych](../designers/display-data-in-blend.md)|

 Aby uzyskać więcej informacji na temat Zaawansowana konstrukcja XAML Zobacz. [Tworzenie interfejsu użytkownika przy użyciu programu Blend for Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)

---
title: Projektowanie XAML w programie Visual Studio
ms.date: 07/17/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 288e2415-9fcf-408e-bc35-9848315e14fd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: c23a73302e5d4771b3372b8f4534b42806156da0
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389620"
---
# <a name="design-xaml-in-visual-studio"></a>Projektowanie XAML w programie Visual Studio

Program Visual Studio i Blend for Visual Studio zapewnia narzędzia graficzne do kompilowania interesujące interfejsy użytkownika, i rozbudowane treści multimedialne możliwości pracy z XAML dla różnych typów aplikacji. Oba narzędzia korzystają ze wspólnego zestawu w funkcji w tym to edytor wizualny XAML, ale program Blend for Visual Studio udostępnia narzędzia do projektowania dodatkowe dla bardziej zaawansowanych zadań, takich jak animacji i zachowania.

Proces projektowania aplikacji zależy od tego, narzędzia, które wybierzesz i docelowej platformy. W tym artykule porównano narzędzia do projektowania XAML w programie Visual Studio i Blend for Visual Studio. Aby uzyskać bardziej szczegółowe wskazówki dotyczące korzystania z narzędzi zobacz następujące tematy:

- [Tworzenie interfejsu użytkownika przy użyciu projektanta XAML w programie Visual Studio](creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
- [Tworzenie interfejsu użytkownika przy użyciu programu Blend for Visual Studio](creating-a-ui-by-using-blend-for-visual-studio.md)

## <a name="choose-the-right-tool"></a>Wybierz odpowiednie narzędzie

Ulubionego narzędzia projektowania jest w dużym stopniu zależy od zestawu umiejętności. Jeśli jesteś bardziej zorientowane na kod, można napisać kod XAML w programie Visual Studio do wykonywania zadań Zaawansowana konstrukcja. Jeśli jesteś bardziej zorientowane na projekt, program Blend for Visual Studio umożliwia wykonywanie zaawansowanych zadań bez konieczności pisania kodu.

Możesz przełączać się i z powrotem między Visual Studio i Blend for Visual Studio, a nawet może mieć tego samego projektu, otworzyć zarówno w tym samym czasie. Zmiany wprowadzone do plików XAML w jednym środowisku IDE można zastosować za pomocą automatyczne przeładowanie po przełączeniu się do innego środowiska IDE. Można kontrolować zachowanie Załaduj ponownie za pomocą opcji w **narzędzia** > **opcje** okno dialogowe, w dowolnym środowisku IDE.

### <a name="shared-capabilities"></a>Współdzielone możliwości

Dla najbardziej podstawowe zadania środowisko IDE programu Visual Studio i Blend for Visual Studio udostępnianie tego samego zestawu windows oraz funkcje, pewne niewielkie różnice. Najważniejsze funkcje obejmują:

- **Spójny interfejs użytkownika:** można zaprojektować aplikacje w ramach znanego interfejsu użytkownika programu Visual Studio, co sprawia, że przełączanie między środowiskami IDE użytkownikom przyjemny i bardziej produktywne. Blend dla Visual Studio używa programu Visual Studio ciemny motyw, który pomoże Ci skupić się na zawartość, którą projektujesz, skracając kontrast między treścią użytkownika a interfejsem użytkownika. Zobacz [Tworzenie interfejsu użytkownika przy użyciu projektanta XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

     ![Program Blend for Visual Studio IDE](../designers/media/blendide.png)

- **Funkcja XAML IntelliSense:** obie obsługują IDE, wszystkie typowe funkcje można oczekiwać od uzupełniania instrukcji, obsługa typowych operacji edytora, takich jak komentowania i formatowanie kodu i nawigacji do zasobów, w tym funkcji IntelliSense powiązanie i kodu.

- **Podstawowe możliwości debugowania:** można teraz debugować w programie Blend, w tym ustawiania punktów przerwania w kodzie, aby debugować uruchomionej aplikacji. Aby zapewnić spójne środowisko debugowania w programie Visual Studio, program Blend for Visual Studio zawiera większość debugowania systemu windows i paski narzędzi programu Visual Studio. Zaawansowane możliwości debugowania, takie jak dane diagnostyczne i analiza kodu są dostępne tylko w programie Visual Studio. Zobacz [debugowania w programie Visual Studio](../debugger/debugging-in-visual-studio.md).

- **Środowisko ponownego ładowania pliku:** można edytować plików XAML w każdej Blend for Visual Studio lub Visual Studio i mieć edytowanych plików ponownie załadować automatycznie jak przełączać się między nimi. Aby zminimalizować przestoje przepływu pracy, można teraz ustawić pliku preferencji Załaduj ponownie w oknie dialogowym ponowne załadowanie pliku.

     ![Środowisko ponownego ładowania pliku](../designers/media/blendfilereload.png)

- **Synchronizowane układy i ustawienia:** układy niestandardowe umożliwiają zapisać i zastosować dostosowania układu okna narzędzia. Visual Studio zsynchronizuje te dostosowania i preferencje dotyczące programu Visual Studio i Blend for Visual Studio na maszynach po zalogowaniu się przy użyciu tego samego konta Microsoft. Zobacz [synchronizować ustawienia na wielu komputerach](../ide/synchronized-settings-in-visual-studio.md).

- **Typowe Eksploratora rozwiązań:** **Eksploratora rozwiązań** zapewnia zorganizowany widok projektów i ich pliki, a także uzyskać dostęp do poleceń związanych z nimi. Za pomocą Eksploratora rozwiązań łatwiej jest pracować z projektami dużych przedsiębiorstw. Zobacz [rozwiązania i projekty](../ide/solutions-and-projects-in-visual-studio.md).

- **Team Explorer:** za pomocą programu Team Explorer można zarządzać projektów z repozytoriami GIT lub TFS, ułatwiające współpracę zespołową. Zobacz [pracy w programie Team Explorer](/azure/devops/user-guide/work-team-explorer).

- **Pakiet NuGet:** można zarządzać pakietami NuGet w programie Visual Studio i Blend for Visual Studio. NuGet to Menedżer pakietów dla platformy .NET Framework, która upraszcza instalacji i usuwania pakietów za pomocą rozwiązania.

## <a name="advanced-capabilities-in-blend-for-visual-studio"></a>Zaawansowane funkcje w programie Blend for Visual Studio

Aby zwiększyć wydajność, należy wziąć pod uwagę przy użyciu Blend dla programu Visual Studio w celu uwzględnienia poniższych zadań. Są to obszary, w której program Blend for Visual Studio oferuje więcej szybkość i funkcjonalności niż Projektant programu Visual Studio lub kod samodzielnie.

|Zadanie|Visual Studio|Blend for Visual Studio|Więcej informacji|
|--------|-------------------| - | - |
|**Tworzenie animacji**|Brak narzędzia do projektowania nie animacje; należy utworzyć je programowo. Ta migracja wymaga zrozumienia Animacja i system chronometrażu w WPF i obszerną wiedzę kodowania.|Wizualne Tworzenie animacji i można przeglądać je w programie Blend for Visual Studio. Jest większa szybkość i dokładność niż Tworzenie animacji w kodzie. Możesz dodać wyzwalacze do obsługi interakcji z użytkownikiem i możesz przełączyć się do kodu w celu dodania obsługi zdarzeń i inne funkcje.|[Animowanie obiektów](../designers/animate-objects-in-xaml-designer.md)|
|**Przekształcając ścieżki do manipulowania łatwiejsze kształty i tekst**|Nieobsługiwane.|Po przekonwertowaniu ich na ścieżki, które zapewniają kontrolę lepiej edycji ułatwia subtelne lub znaczne zmiany do kształtów zewnętrznych (takich jak prostokąty i elipsy). Możesz zmienić kształt lub łączenia ścieżek i utworzyć ścieżki złożone z wielu kształtów.<br /><br /> Można również przeprowadzić konwersję bloki tekstu do ścieżki do manipulowania nimi jako obrazy wektorowe.|[Rysowanie kształtów i ścieżek](../designers/draw-shapes-and-paths.md)|
|**Stosowanie interakcyjności w projekty interfejsu użytkownika**|Wymaga kodu C#, Visual Basic lub C++.|Przeciągnij i upuść zachowań na kontrolki, aby dodać interakcję do statyczne projekty. Zachowania są fragmenty kodu gotowych do użycia, które hermetyzują funkcje, takie jak przeciągania i upuszczania, powiększania i zmiany stanu wizualnego. Istnieje coraz większego zestawu zachowania, z których można wybrać i utworzyć własny.<br /><br /> Każde działanie można następnie dostosować, zmieniając jego właściwości w programie Blend for Visual Studio lub przez dodanie obsługi zdarzeń w kodzie.|[Wstawianie kontrolek i modyfikowanie ich zachowania](../designers/insert-controls-and-modify-their-behavior-in-xaml-designer.md)|
|**Użyj kompozycji Adobe**|Nieobsługiwane.|Importuj Adobe FXG oraz PhotoShop, Illustrator kompozycji i implementują interfejs użytkownika w programie Blend for Visual Studio.|[Wstawianie obrazów, klipów wideo i klipów audio](../designers/insert-images-videos-and-audio-clips-in-xaml-designer.md)|
|**Edytuj formanty, szablony i style**|Wymaga kodowania i wiedzy na temat WPF — style i szablony.|Włącz obrazów w formancie.<br /><br /> Szablon narzędzi edycji Aby wprowadzić zmiany do kontrolek, stylów i szablonów za pomocą zaledwie kilkoma kliknięciami.<br /><br /> Na przykład można użyć programu Blend dla programu Visual Studio zasoby stylów, implementować wspólnych formantów WPF (takie jak przyciski, pola listy, paski przewijania, menu itd.) oraz zmieniać ich kolor, styl lub podstawowego szablonu bezpośrednio w programie Blend for Visual Studio. Można następnie przełączyć kod poprawek, jeśli chcesz.|[Modyfikowanie stylu obiektów](../designers/modify-the-style-of-objects-in-blend.md)|
|**Interfejs użytkownika łączą się z danymi**|Można utworzyć źródło danych z zasobów, takich jak bazy danych programu SQL Server, usługi WCF lub usług sieci web, obiektów lub listy programu SharePoint i powiązać źródła danych z formantów interfejsu użytkownika.<br /><br /> Dane w czasie projektowania musi zostać utworzony ręcznie dla środowisko interaktywne projektu.|Tworzenie danych przykładowych, łatwe do tworzenia prototypów i testowania aplikacji. Przełącz, aby dane na żywo, gdy wszystko będzie gotowe.<br /><br /> Program Blend for możliwości istnieją zaległe Generowanie danych programu Visual Studio (można dodać nazwy, liczby, adresy URL i zdjęcia prosty sposób na bieżąco) i zaoszczędzić dużo czasu.<br /><br /> W przypadku danych na żywo można powiązać formantów interfejsu użytkownika do pliku XML lub do dowolnego źródła danych środowiska CLR.|[Wyświetlanie danych](../designers/display-data-in-blend.md)|

Aby uzyskać więcej informacji na temat Zaawansowana konstrukcja XAML, zobacz [Tworzenie interfejsu użytkownika przy użyciu programu Blend for Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md).

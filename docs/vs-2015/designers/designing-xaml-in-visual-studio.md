---
title: Projektowanie XAML
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 288e2415-9fcf-408e-bc35-9848315e14fd
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6c48e44e0488d61e3061d680962bf22e42935090
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664712"
---
# <a name="designing-xaml-in-visual-studio"></a>Projektowanie XAML w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Programy Visual Studio i Blend for Visual Studio umożliwiają tworzenie wizualnych narzędzi do tworzenia atrakcyjnych interfejsów użytkownika i bogatych rozwiązań multimedialnych dla aplikacji klasycznych dla systemu Windows opartych na języku XAML, sieci Web, programów [Windows Phone](https://msdn.microsoft.com/library/windowsphone/develop/jj683071.aspx)i [sklepu Windows](https://msdn.microsoft.com/library/windows/apps/jj129478.aspx) . Oba te funkcje udostępniają wspólny zestaw okien projektowania i narzędzi oraz Edytor XAML, ale Blend for Visual Studio udostępnia dodatkowe narzędzia do projektowania dla bardziej zaawansowanych zadań, takich jak animacje i zachowania.

## <a name="choosing-the-right-tool"></a>Wybieranie odpowiedniego narzędzia
 Wybór narzędzi do projektowania jest w dużym stopniu zależny od zestawu umiejętności. Jeśli jest więcej zorientowane na kod, możesz napisać kod XAML w programie Visual Studio, aby osiągnąć jeszcze zaawansowane zadania projektowania. Jeśli jest więcej zorientowane na projekt, Blend for Visual Studio umożliwia wykonywanie zaawansowanych zadań bez pisania kodu.

 Można przełączać się między programem Visual Studio i Blend for Visual Studio, a nawet w tym samym czasie może być otwarty jednocześnie. Zmiany wprowadzone w plikach XAML w jednym środowisku IDE mogą być stosowane przez automatyczne ponowne ładowanie po przełączeniu do innego środowiska IDE. Możesz kontrolować zachowanie ponownego ładowania za pośrednictwem opcji w oknie dialogowym **Narzędzia**, **Opcje** w obu IDE.

### <a name="shared-capabilities"></a>Współdzielone możliwości
 W przypadku większości podstawowych zadań środowisko IDE dla programu Visual Studio i Blend for Visual Studio współdzielą ten sam zestaw okien i możliwości, z niewielkimi różnicami. Jej najważniejsze funkcje obejmują:

- **Spójny interfejs użytkownika:** Aplikacje można projektować w znanym kontekście interfejsu użytkownika programu Visual Studio, co sprawia, że przełączanie między środowisk IDE a bardziej przyjemnym i wydajnym środowiskiem. Blend for Visual Studio korzysta z ciemnego motywu programu Visual Studio, który ułatwia skoncentrowanie się na projektowanej zawartości przez zwiększenie kontrastu zawartości i interfejsu użytkownika. Zobacz [Tworzenie interfejsu użytkownika przy użyciu Projektant XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

     ![Blend for Visual Studio IDE](../designers/media/blendide.png "BlendIDE")

- **IntelliSense języka XAML:** Obydwie środowisk IDE obsługują wszystkie typowe funkcje, które można oczekiwać od IntelliSense, w tym uzupełnianie instrukcji, obsługę typowych operacji edytora, takich jak komentowanie i formatowanie kodu oraz nawigowanie do zasobów, powiązań i kodu.

- **Podstawowe możliwości debugowania:** Teraz można debugować w programie Blend, w tym ustawianie punktów przerwania w kodzie do debugowania uruchomionej aplikacji. Aby zachować spójne środowisko debugowania w programie Visual Studio, Blend for Visual Studio zawiera większość okien debugowania i pasków narzędzi programu Visual Studio. Zaawansowane funkcje debugowania, takie jak diagnostyka i analiza kodu, są dostępne tylko w programie Visual Studio. Zobacz [debugowanie w programie Visual Studio](../debugger/debugging-in-visual-studio.md).

- **Środowisko ponownego ładowania plików:** Pliki XAML można edytować w Blend for Visual Studio lub w programie Visual Studio i automatycznie ładować pliki po przełączeniu między nimi. Aby zminimalizować przerwy w przepływie pracy, można teraz ustawić preferencje ponownego ładowania pliku w oknie dialogowym Ponowne ładowanie pliku.

     ![Środowisko ponownego ładowania plików](../designers/media/blendfilereload.png "BlendFileReload")

- **Zsynchronizowane układy i ustawienia:** Układy niestandardowe umożliwiają zapisywanie i stosowanie dostosowań układu okna narzędzi. Program Visual Studio zsynchronizuje te dostosowania i preferencje dla programu Visual Studio i Blend for Visual Studio między maszynami, gdy zalogujesz się za pomocą tej samej konto Microsoft. Zobacz [Dostosowywanie ustawień programistycznych w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

- **Typowy Eksplorator rozwiązań:** Eksplorator rozwiązań udostępnia zorganizowany widok projektów i ich plików, a także gotowy dostęp do poleceń skojarzonych z nimi. Dzięki Eksplorator rozwiązań łatwiej jest współpracować z dużymi projektami przedsiębiorstwa. Zobacz [rozwiązania i projekty](../ide/solutions-and-projects-in-visual-studio.md).

- **Team Explorer:** Dzięki Team Explorer możesz zarządzać projektami za pomocą repozytoriów GIT lub TFS, aby ułatwić współpracę zespołową. Zobacz [pracy w Team Explorer](https://msdn.microsoft.com/library/fd7a5cf7-7916-4fa0-b5e6-5a83cf377a02).

- Pakiet **NuGet:** Można zarządzać pakietami NuGet zarówno w programie Visual Studio, jak i w Blend for Visual Studio. NuGet to Menedżer pakietów dla .NET Framework, który upraszcza instalację i usuwanie pakietów z rozwiązania.

## <a name="advanced-capabilities-in-blend-for-visual-studio"></a>Zaawansowane możliwości w Blend for Visual Studio
 Aby zwiększyć produktywność, należy rozważyć użycie Blend for Visual Studio dla następujących zadań. Poniżej znajdują się obszary, w których Blend for Visual Studio oferuje większą szybkość i funkcjonalność niż Projektant lub sam kod programu Visual Studio.

|Działanie|Visual Studio|Blend for Visual Studio|Więcej informacji|
|--------|-------------------|-----------------------------|----------------------|
|**Tworzenie animacji**|Nie istnieje narzędzie projektowania dla animacji; należy je tworzyć programowo. Wymaga to wiedzy na temat animacji i systemu chronometrażu w WPF i obszernej znajomości kodu.|Animacje można tworzyć wizualnie i wyświetlać je w Blend for Visual Studio. Jest to szybsze i bardziej dokładne niż Kompilowanie animacji w kodzie. Możesz dodać wyzwalacze do obsługi interakcji z użytkownikiem i można przełączyć się do kodu, aby dodać programy obsługi zdarzeń i inne funkcje.|[Animowanie obiektów](../designers/animate-objects-in-xaml-designer.md)|
|**Przekształcanie kształtów i tekstu w ścieżki w celu ułatwienia manipulowania**|Nieobsługiwane.|Można wprowadzać delikatne lub znaczące zmiany w kształtach (takich jak prostokąty i wielokropki), konwertując je na ścieżki, co zapewnia lepszą kontrolę edycji.  Można przekształcać i łączyć ścieżki oraz tworzyć ścieżki złożone z wielu kształtów.<br /><br /> Możesz również skonwertować bloki tekstu na ścieżki, aby manipulować nimi w postaci obrazów wektorowych.|[Rysowanie kształtów i ścieżek](../designers/draw-shapes-and-paths.md)|
|**Dodawanie interakcji do projektów interfejsu użytkownika**|Wymaga kodu C#, Visual Basic lub C++.|Przeciągnij i upuść zachowania w kontrolkach, aby dodać interaktywność do projektów statycznych. Zachowania są gotowymi do użycia fragmentami kodu, które hermetyzują funkcje, takie jak przeciąganie i upuszczanie, powiększanie i zmiana stanu wizualnego. Istnieje coraz więcej zachowań, z których można skorzystać, i możesz utworzyć własne.<br /><br /> Następnie można dostosować każde zachowanie, zmieniając jego właściwości w Blend for Visual Studio lub przez dodanie obsługi zdarzeń w kodzie.|[Wstawianie kontrolek i modyfikowanie ich zachowania](../designers/insert-controls-and-modify-their-behavior-in-xaml-designer.md)|
|**Korzystanie z kompozycji Adobe**|Nieobsługiwane.|Zaimportuj kompozycję Adobe FXG, PhotoShop lub Illustrator i zaimplementuj interfejs użytkownika w Blend for Visual Studio.|[Wstawianie obrazów, klipów wideo i klipów audio](../designers/insert-images-videos-and-audio-clips-in-xaml-designer.md)|
|**Edytowanie kontrolek, szablonów i stylów**|Wymaga kodowania i znajomości stylów i szablonów WPF.|Przekształcenie dowolnego obrazu w kontrolkę.<br /><br /> Za pomocą narzędzi do edycji szablonów można wprowadzać zmiany w kontrolkach, stylach i szablonach za pomocą zaledwie kilku kliknięć myszą.<br /><br /> Na przykład możesz użyć zasobów stylów Blend for Visual Studio do implementowania wspólnych kontrolek WPF (takich jak przyciski, pola listy, paski przewijania, menu itp.), a także zmieniać kolory, style lub szablony bazowe bezpośrednio w Blend for Visual Studio. Następnie możesz przełączyć się do kodu, aby dokończył się w razie potrzeby.|[Modyfikowanie stylu obiektów](../designers/modify-the-style-of-objects-in-blend.md)|
|**Połącz interfejs użytkownika z danymi**|Można utworzyć źródło danych z zasobów, takich jak SQL Server baz danych, usług WCF lub sieci Web, obiektów lub list programu SharePoint, a także powiązać źródło danych z kontrolkami interfejsu użytkownika.<br /><br /> Dane czasu projektowania muszą być tworzone ręcznie dla interaktywnego środowiska projektowego.|Twórz przykładowe dane w celu łatwego tworzenia prototypów i testowania. Przejdź do danych na żywo, gdy wszystko będzie gotowe.<br /><br /> Funkcje generacji danych Blend for Visual Studio są zaległe (można dodawać nazwiska, cyfry, adresy URL, zdjęcia z łatwością na bieżąco), a także zaoszczędzić dużo czasu.<br /><br /> W przypadku danych na żywo można powiązać kontrolki interfejsu użytkownika z plikiem XML lub dowolnym źródłem danych CLR.|[Wyświetlanie danych](../designers/display-data-in-blend.md)|

 Aby uzyskać więcej informacji na temat zaawansowanego projektowania XAML, zobacz. [Tworzenie interfejsu użytkownika przy użyciu programu Blend for Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)

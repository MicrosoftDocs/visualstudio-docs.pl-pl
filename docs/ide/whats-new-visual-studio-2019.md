---
title: Co nowego w programie Visual Studio 2019
titleSuffix: ''
description: Dowiedz się więcej o nowych funkcjach w programie Visual Studio 2019 r.
ms.date: 02/07/2019
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 00bec66b-bcee-46f5-91d9-f73a2b469744
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.prod: visual-studio-dev16
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 9dd0785e3e20051a58fe46695f27d9be0ae8567a
ms.sourcegitcommit: 01334abf36d7e0774329050d34b3a819979c95a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "55853969"
---
# <a name="whats-new-in-visual-studio-2019-preview"></a>Co nowego w programie Visual Studio 2019 (wersja zapoznawcza)

**Zaktualizowano do programu [wersji 2 (wersja zapoznawcza)](/visualstudio/releases/2019/release-notes-preview?context=visualstudio/default&contextView=vs-2017)**

>[!div class="button"]
>[Pobierz wersję zapoznawczą](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019+preview)

Visual Studio 2019 Preview zawiera wiele ulepszeń ogólne oraz nowe funkcje, które optymalizują wydajność pracy deweloperskiej i współpracę zespołową. Czy używasz programu Visual Studio po raz pierwszy używasz go przez wiele lat, będziesz mieć możliwość wykorzystać jej funkcje dla wszystkich aspektów cyklu życia opracowywania&mdash;z uproszczonego tworzenia i kod kondycji zarządzania projektami, zespołu: i współpracy przepływy pracy typu open source.<br/><br/>

>[!VIDEO https://channel9.msdn.com/Events/Connect/Microsoft-Connect--2018/D190/player]

Poniżej przedstawiono podsumowanie wysokiego poziomu oferowane przez program Visual Studio:

* **[Osobistych i zespołowych produktywność](#personal-and-team-productivity)**. Produktywność dla wszystkich użytkowników, gdzie mają one największe znaczenie.
* **[Obsługa nowoczesnego projektowania](#modern-development-support)**. Obsługa bieżących projektów i rozwiązań w przyszłości.
* **[Ciągłe wprowadzanie innowacji](#continuous-innovation)**. Kod inteligentne z obsługą inteligentną i w chmurze.

> [!NOTE]
> Aby uzyskać pełną listę nowych funkcji i funkcjonalności w Visual Studio Preview 2019 r, zobacz [informacje o wersji](/visualstudio/releases/2019/release-notes-preview?context=visualstudio/default&contextView=vs-2017). I roundup nowości w naszej drugiej wersji zapoznawczej, można zobaczyć [programu Visual Studio 2 2019 r w wersji zapoznawczej jest teraz dostępna](https://blogs.msdn.microsoft.com/visualstudio/2019/01/24/visual-studio-2019-preview-2-is-now-available/) wpis w blogu.

## <a name="personal-and-team-productivity"></a>Osobistych i zespołowych produktywności

Jest biorąc pod uwagę, że ulepszenia wydajności są najważniejsze z każdą wersją programu Visual Studio, ale po prawej stronie się tam z nim w celu ulepszania wydajności pracy. Oto, jak możemy pomóc korzystając z niego.

### <a name="new-start-window"></a>Nowe okno uruchamiania

Pierwszą rzeczą, zauważysz, po otwarciu programu Visual Studio 2019 r jest jego nowe okno rozpoczęcia.

   ![Nowe okno początek w Visual Studio 2019 r.](media/start-window.png)

To nowe okno rozpoczęcia przedstawia opcje, aby sklonować lub zapoznaj się z kodu, otwórz projekt lub rozwiązanie, otwórz folder lokalny lub Utwórz nowy projekt. Posiadanie tych opcji w oknie dialogowym proste pomaga zarówno początkujących i zaawansowanych użytkowników programu Visual Studio, przejść do kodu szybko.

Aby uzyskać więcej informacji, zobacz [uzyskać dostęp do kodu: Jak został zaprojektowany nowe okno uruchamiania programu Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/2018/12/13/get-to-code-how-we-designed-the-new-visual-studio-start-window/) wpis w blogu.

### <a name="better-search"></a>Lepsze wyszukiwania

Znana wcześniej jako szybkiego uruchamiania, naszą nową funkcję wyszukiwania jest szybsze i bardziej skuteczne. Teraz wyniki wyszukiwania są wyświetlane dynamicznie podczas wpisywania. I wyniki wyszukiwania zawierają skróty klawiaturowe dla poleceń, dzięki czemu można łatwiej pamiętania do użytku w przyszłości.

   ![Nowa funkcja wyszukiwania w Visual Studio 2019 r.](media/search-feature.png)

Czy szukasz poleceń, ustawienia, dokumentacji i inne przydatne czynności nowej funkcji wyszukiwania sprawia, że łatwiej znaleźć, czego szukasz.

### <a name="one-click-code-cleanup"></a>Oczyszczania kodu jednym kliknięciem

Sparowane z wskaźnik kondycji dokumentu jest nowe polecenie czyszczenia kodu. To nowe polecenie służy do identyfikowania i następnie Rozwiąż ostrzeżenia i sugestie dotyczące kliknięciem przycisku.

   ![Nowa funkcja oczyszczania kodu w Visual Studio 2019 r.](media/code-cleanup.png)

Oczyszczanie będzie formatowania kodu i stosowanie poprawek kodu zgodnie z sugestią podaną przez [bieżące ustawienia](code-styles-and-quick-actions.md), [plików editorconfig](create-portable-custom-editor-options.md), lub [analizatorów Roslyn](../code-quality/roslyn-analyzers-overview.md).

### <a name="debugger-improvements"></a>Ulepszenia debugera

#### <a name="search-within-a-watch-window-and-format-watch-values"></a>Wyszukiwanie w oknie czujki i formatowanie wartości czujki

Prawdopodobnie byłeś istnieje, wyszukiwanie w oknie czujki ciągu oraz zestaw wartości. W Visual Studio 2019 Preview dodaliśmy wyszukiwania w oknach wyrażeń kontrolnych, zmiennych lokalnych i automatycznych ułatwią znalezienie obiektów i wartości, którego szukasz.

Możesz również sformatować, jak wartość jest wyświetlana w oknach wyrażenie kontrolne, zmiennych lokalnych i automatycznych.  Kliknij dwukrotnie jeden z elementów w żadnym z systemu windows, a następnie dodaj przecinek (","), aby uzyskać dostęp do listy rozwijanej specyfikatorów formatu możliwe, z których każdy zawiera opis jego zamierzony efekt.

   ![Obejrzyj okna i format wartości nowością w Visual Studio 2019 r.](media/search-watch-window.png)

Aby uzyskać więcej informacji, zobacz [rozszerzone w Visual Studio 2019 r.: Wyszukiwanie obiektów i właściwości w kontrolnych, zmiennych automatycznych i zmiennych lokalnych Windows](https://blogs.msdn.microsoft.com/visualstudio/2019/01/28/enhanced-in-visual-studio-2019-search-for-objects-and-properties-in-the-watch-autos-and-locals-windows/) wpis w blogu.

### <a name="visual-studio-live-share"></a>Visual Studio Live Share

[Visual Studio funkcja udostępniania na żywo](https://visualstudio.microsoft.com/services/live-share/) to usługa dla deweloperów, która umożliwia udostępnianie kodu i kontekst współpracownikom i uzyskać natychmiastowy współpracy dwukierunkowej bezpośrednio z poziomu programu Visual Studio. Za pomocą udostępniania na żywo partnerem można przeczytać, przejdź, edytować i debugować projekt, który został udostępniony z nimi i bezproblemowo i bezpiecznie w tym celu.

I za pomocą programu Visual Studio 2019 r (wersja zapoznawcza), ta usługa jest instalowana domyślnie.

Aby uzyskać więcej informacji, zobacz [Visual Studio udostępniania na żywo do przeglądów kodu w czasie rzeczywistym i interaktywne edukacji](https://blogs.msdn.microsoft.com/visualstudio/2018/12/06/visual-studio-live-share-for-real-time-code-reviews-and-interactive-education/) wpis w blogu.

## <a name="modern-development-support"></a>Obsługa nowoczesnego projektowania

### <a name="manage-pull-requests-prs-from-the-ide"></a>Zarządzanie żądania ściągnięcia (pr) z poziomu środowiska IDE

Wprowadzamy nowe rozszerzenie, które można pobrać za pomocą Visual Studio Preview 2019 r. Za pomocą tego nowego rozszerzenia można przejrzeć, uruchomić i nawet debugowanie żądań ściągnięcia od członków zespołu, bez opuszczania środowiska IDE programu Visual Studio [(zintegrowanym środowiskiem programistycznym)](../get-started/visual-studio-ide.md). Firma Microsoft obsługuje kodu w repozytoriach Azure już dziś, ale zostało rozszerzone, aby obsługiwać usługi GitHub oraz ulepszenia ogólnej.

Aby rozpocząć, Pobierz [żądania ściągnięcia dla programu Visual Studio](https://aka.ms/pr4vs) rozszerzenie z witryny Marketplace programu Visual Studio.

### <a name="develop-with-net-core-3-preview-1"></a>Programowanie przy użyciu platformy .NET Core 3 (wersja zapoznawcza) 1

Wersja zapoznawcza programu Visual Studio 2019 obsługuje tworzenie [.NET Core 3](http://aka.ms/netcore3preview1) aplikacje dla dowolnej platformy. Będziemy dalej do obsługi i poprawić Programowanie w języku C++ dla wielu platform, a także .NET opracowywania aplikacji mobilnych dla systemów iOS i Android za pomocą platformy Xamarin.

   ![Tworzenie aplikacji za pomocą programu .NET Core 3 Preview 1 w Visual Studio 2019 r.](media/dot-net-core-three-dev.png)

## <a name="continuous-innovation"></a>Ciągłe wprowadzanie innowacji

### <a name="per-monitor-aware-pma-rendering"></a>Świadomość renderowania (PMA) monitora

Jeśli używasz monitory, które są skonfigurowane przy użyciu innego ekranu skale, lub zdalnie połączyć się z maszyną za pomocą wyświetlania skali czynników, które różnią się od głównego urządzenia, można zauważyć, że Visual Studio wygląda rozmyty lub renderowanie w skali problem.

Wraz z wydaniem programu Visual Studio 2019 Preview podejmujemy pierwszy krok w kierunku co program Visual Studio — monitorowanie aplikacji obsługującej (PMA). Kładziemy podstawowe prace, która umożliwi programu Visual Studio zapewnić prawidłowe renderowanie, niezależnie od tego, co wyświetlane skale, którego używasz.

   ![Świadomość renderowania (PMA) w Visual Studio 2019 monitora](media/per-monitor-aware-dpi-scaling.png)

Aby uzyskać więcej informacji, zobacz [lepiej wielu monitorów z programu Visual Studio 2019](https://blogs.msdn.microsoft.com/visualstudio/2019/02/07/a-better-multi-monitor-experience-with-visual-studio-2019/) wpis w blogu.

### <a name="visual-studio-intellicode"></a>Visual Studio IntelliCode

[Visual Studio IntelliCode](/visualstudio/intellicode/) to rozszerzenie, które rozszerza Twoje wysiłki na rzecz rozwoju oprogramowania przy użyciu sztucznego inteligencji (AI). Rozszerzenie IntelliCode pociągów 2000 projektów typu open source w serwisie GitHub&mdash;każdy z ponad 100 gwiazdek&mdash;do generowania zalecenia.

Oto kilka sposobów, że program Visual Studio IntelliCode może pomóc zwiększyć wydajność:

* Dostarczanie uzupełnianie kodu oparte na kontekście
* Przewodnik deweloperów stosować się do wzorców i style ich zespołu
* Znajdowanie problemów z kodem trudne catch
* Przeglądy kodu fokus przez zwrócenie uwagi do obszarów, które naprawdę mają znaczenie

Początkowo obsługiwane tylko C# kiedy możemy najpierw podglądu rozszerzenia IntelliCode dla programu Visual Studio. Teraz Dodaliśmy obsługę języków C++ i XAML w programie Visual Studio, zbyt.

A jeśli używasz C#, dodaliśmy także możliwość uczenia modelu niestandardowego na własny kod.

Aby uzyskać więcej informacji o najnowszych aktualizacjach, zobacz [Visual Studio IntelliCode obsługuje więcej języków i uczy się z kodu](https://blogs.msdn.microsoft.com/visualstudio/2018/12/05/visual-studio-intellicode-supports-more-languages-and-learns-from-your-code/) wpis w blogu. A, aby uzyskać więcej informacji na temat rozszerzenia i jak ją pobrać, zobacz [Visual Studio IntelliCode — wersja zapoznawcza](https://go.microsoft.com/fwlink/?linkid=872707) stronie DevLabs firmy Microsoft.

## <a name="give-us-feedback"></a>Przekaż nam swoją opinię

Dlaczego warto wysłać opinię do zespołu usługi Visual Studio? Ponieważ traktujemy opinie naszych użytkowników bardzo poważnie. Zależy od ilości co możemy zrobić.

* Jeśli chcesz sugestię o jak możemy ulepszyć program Visual Studio, możesz to zrobić za pomocą [sugestię](talk-to-us.md#i-want-to-make-a-suggestion-about-visual-studio-features) narzędzia.

* Jeśli wystąpią, zawieszenie, awarii lub innych problemów z wydajnością, można łatwo udostępniać kroki odtwarzania i towarzyszące mu pliki z nami za pomocą [Zgłoś Problem](talk-to-us.md#i-want-to-report-a-problem-with-visual-studio) narzędzia.

## <a name="see-also"></a>Zobacz także

* [Informacje o wersji programu Visual Studio 2019 r](/visualstudio/releases/2019/release-notes-preview?context=visualstudio/default&contextView=vs-2017)
* [Microsoft Connect(); 2018 conference](https://www.microsoft.com/connectevent)
* [Co nowego w programie Visual Studio 2017](whats-new-visual-studio-2017.md)

---
title: Co nowego w programie Visual Studio 2019
titleSuffix: ''
description: Dowiedz się więcej o nowych funkcjach w programie Visual Studio 2019 r.
ms.date: 04/23/2019
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 00bec66b-bcee-46f5-91d9-f73a2b469744
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 3093641ad07ad3ae0f4796c2064c3e6901ae03ba
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432028"
---
# <a name="whats-new-in-visual-studio-2019"></a>Co nowego w programie Visual Studio 2019

**Zaktualizowano do programu [16,0 wydania](/visualstudio/releases/2019/release-notes/)**

>[!div class="button"]
>[Pobierz program Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)

Za pomocą programu Visual Studio 2019 r uzyskasz najlepsze w swojej klasie narzędzi i usług dla każdego dewelopera, każdej aplikacji i dowolnej platformy. Czy używasz programu Visual Studio po raz pierwszy używasz go przez wiele lat, jest dużo, np. w tej nowej wersji!

Poniżej przedstawiono podsumowanie wysokiego poziomu what's new:

* **[Twórz](#develop)**: Zachowanie, ukierunkowanych i produktywności z lepszą wydajność, oczyszczania błyskawiczne kodu i lepsze wyniki wyszukiwania.
* **[Współpraca](#collaborate)**: Korzystaj naturalne współpracy przy użyciu Git pierwszego przepływu pracy w czasie rzeczywistym, edytowanie i debugowanie, i przeglądów kodu po prawej stronie w programie Visual Studio.
* **[Debugowanie](#debug)**: Wyróżnij i przejdź do określonej wartości, optymalizacja zużycia pamięci i automatycznych migawek wykonywania aplikacji.

Aby uzyskać pełną listę wszystkich elementów, co nowego w tej wersji, zobacz [informacje o wersji](/visualstudio/releases/2019/release-notes/).

## <a name="develop"></a>Programowanie

Oszczędzaj czas dzięki nowym funkcjom.
<br><br>
> [!VIDEO https://www.youtube.com/embed/n5sJ4EewKGk]

### <a name="improved-search"></a>Udoskonalonej funkcji wyszukiwania

Znana wcześniej jako szybkiego uruchamiania, naszą nową funkcję wyszukiwania jest szybsze i bardziej skuteczne. Teraz wyniki wyszukiwania są wyświetlane dynamicznie podczas wpisywania. I wyniki wyszukiwania można często zawierają skróty klawiaturowe dla poleceń, dzięki czemu można łatwiej pamiętania do użytku w przyszłości.

   ![Animacji z nowej funkcji wyszukiwania w programie Visual Studio 2019 r.](media/vs-2019/new-search-feature.gif)

Nowej logiki Wyszukiwanie rozmyte znajduje się coś, czego potrzebujesz, niezależnie od tego, literówki. Tak czy szukasz poleceń, ustawienia, dokumentacji i inne przydatne czynności nowej funkcji wyszukiwania sprawia, że łatwiej znaleźć, czego szukasz.

### <a name="refactorings"></a>Operacje refaktoryzacji

Dostępnych jest wiele nowych i bardzo przydatna refaktoryzacji w C# , ułatwiają organizowanie kodu. One są wyświetlane jako sugestie w żarówki i obejmują akcje, takie jak przeniesienie członków do interfejsu lub klasy bazowej, dostosowując obszary nazw, aby dopasować strukturę folderów, należy przekonwertować pętli foreach do zapytań Linq i nie tylko.

   ![Animacja środowiska refaktoryzacji w Visual Studio 2019 r.](media/vs-2019/refactorings.gif)

Po prostu wywołać refaktoryzacji, naciskając klawisz **Ctrl +.** i wybierając akcję, którą chcesz wykonać.

### <a name="intellicode"></a>IntelliCode

[Visual Studio IntelliCode](/visualstudio/intellicode/) to rozszerzenie, które rozszerza Twoje wysiłki na rzecz rozwoju oprogramowania za pomocą sztucznej inteligencji (AI). Rozszerzenie IntelliCode pociągów 2000 projektów typu open source w serwisie GitHub&mdash;każdy z ponad 100 gwiazdek&mdash;do generowania zalecenia.

 ![Animacja IntelliCode w Visual Studio 2019 r.](media/vs-2019/IntelliCode.gif)

Oto kilka sposobów, że program Visual Studio IntelliCode może pomóc zwiększyć wydajność:

* Dostarczanie uzupełnianie kodu oparte na kontekście
* Przewodnik deweloperów stosować się do wzorców i style ich zespołu
* Znajdowanie problemów z kodem trudne catch
* Przeglądy kodu fokus przez zwrócenie uwagi do obszarów, które naprawdę mają znaczenie

Początkowo obsługiwane tylko C# kiedy możemy najpierw podglądu rozszerzenia IntelliCode dla programu Visual Studio. Teraz Dodaliśmy obsługę języków C++ i XAML w programie Visual Studio, zbyt.

A jeśli używasz C#, dodaliśmy także możliwość uczenia modelu niestandardowego na własny kod.

Aby uzyskać więcej informacji na temat IntelliCode zobacz [więcej kodu, przewiń w mniej z programu Visual Studio IntelliCode](https://devblogs.microsoft.com/visualstudio/code-more-scroll-less-with-visual-studio-intellicode/) wpis w blogu.

### <a name="code-cleanup"></a>Oczyszczanie kodu

Sparowane z wskaźnik kondycji dokumentu jest nowe polecenie czyszczenia kodu. To nowe polecenie służy do identyfikowania i następnie Rozwiąż ostrzeżenia i sugestie dotyczące kliknięciem przycisku.

Oczyszczanie będzie formatowania kodu i stosowanie poprawek kodu zgodnie z sugestią podaną przez [bieżące ustawienia](code-styles-and-quick-actions.md) i [plików editorconfig](create-portable-custom-editor-options.md).

   ![Zrzut ekranu przedstawiający nowy formant oczyszczania kodu w Visual Studio 2019 r.](media/vs-2019/code-cleanup-profile.png)

Kolekcje programów naprawiających można także zapisać jako profil. Na przykład jeśli mają niewielki zestaw programów naprawiających docelowych, które są często stosowane podczas kodowania, a następnie mają inny kompleksowy zestaw programów naprawiających, aby przesłać wniosek przed przeglądu kodu, można skonfigurować profile, aby rozwiązać te różne zadania.

   ![Zrzut ekranu przedstawiający nowy formant oczyszczania kodu w Visual Studio 2019 r.](media/vs-2019/code-cleanup-profile-configure.png)

## <a name="collaborate"></a>Współpraca

Sił do rozwiązywania problemów.
<br><br>
> [!VIDEO https://www.youtube.com/embed/dKLJsiK1QU8]

### <a name="cloud-first-workflow"></a>Przepływ pracy w chmurze

Coś, co można zauważyć po otwarciu programu Visual Studio 2019 r jest jego nowe okno rozpoczęcia.

   ![Zrzut ekranu okna nowy początek w Visual Studio 2019 r.](media/vs-2019/start-window-dark.png)

W oknie uruchamiania przedstawia kilka opcji, aby szybko przejść do kodu. Firma Microsoft zostały umieszczone opcję, aby sklonować lub zapoznaj się z kodu z repozytorium, najpierw.  

   ![Animacja środowiska "Git-first" w programie Visual Studio 2019 r.](media/vs-2019/git-first.gif)

W oknie start zawiera również opcje, aby otworzyć projekt lub rozwiązanie, otwórz folder lokalny lub Utwórz nowy projekt.

Aby uzyskać więcej informacji, zobacz [uzyskać dostęp do kodu: Jak został zaprojektowany nowe okno uruchamiania programu Visual Studio](https://devblogs.microsoft.com/visualstudio/get-to-code-how-we-designed-the-new-visual-studio-start-window/) wpis w blogu.

### <a name="live-share"></a>Live Share

[Visual Studio funkcja udostępniania na żywo](https://visualstudio.microsoft.com/services/live-share/) to usługa dla deweloperów, która umożliwia udostępnianie kodu i kontekst współpracownikom i Uzyskaj natychmiastowej dwukierunkowej możliwości współpracy bezpośrednio z poziomu programu Visual Studio. Za pomocą udostępniania na żywo partnerem można przeczytać, przejdź, edytować i debugować projekt, który został udostępniony z nimi i bezproblemowo i bezpiecznie w tym celu.

I za pomocą programu Visual Studio 2019 r, ta usługa jest instalowana domyślnie.

![Animację, pokazujący funkcję współpracy udostępniania na żywo w programie Visual Studio 2019 r.](media/vs-2019/live-share.gif)

Aby uzyskać więcej informacji, zobacz [Visual Studio udostępniania na żywo do przeglądów kodu w czasie rzeczywistym i interaktywne edukacji](https://devblogs.microsoft.com/visualstudio/visual-studio-live-share-for-real-time-code-reviews-and-interactive-education/) wpis w blogu i [udostępniania na żywo, teraz dołączone do programu Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/live-share-now-included-with-visual-studio-2019/) wpis w blogu.

### <a name="integrated-code-reviews"></a>Przeglądy kodu zintegrowane

Wprowadzamy nowe rozszerzenie, które można pobrać za pomocą programu Visual Studio 2019 r. Za pomocą tego nowego rozszerzenia Przejrzyj, uruchom, a nawet debugowanie żądań ściągnięcia od członków zespołu, bez opuszczania programu Visual Studio. Firma Microsoft obsługuje kodu w repozytoriach usługi GitHub i DevOps platformy Azure.

   ![Zrzut ekranu okna nowy początek w Visual Studio 2019 r.](media/vs-2019/pr-experience.png)

Aby rozpocząć, Pobierz [żądania ściągnięcia dla programu Visual Studio](https://aka.ms/pr4vs) rozszerzenie z witryny Marketplace programu Visual Studio.

## <a name="debug"></a>Debugowanie

Zero, przy użyciu precyzyjnego określania wartości docelowej.
<br><br>
> [!VIDEO https://www.youtube.com/embed/hr72Fs8n_9c]

### <a name="performance-gains"></a>Wzrost wydajności

Firma Microsoft została podjęta punkty przerwania danych w języku C++ wykluczającymi się jeden raz i dostosować je do aplikacji .NET Core.

   ![Animacji, który zawiera punkty przerwania danych debugowania w Visual Studio 2019 r](media/vs-2019/debug-data-breakpoints.gif)

Tak czy jesteś kodowania w C++ i .NET Core, punkty przerwania danych może być jest dobrą alternatywą gracze współczesnego rynku regularne punkty przerwania. Punkty przerwania danych są również doskonałe rozwiązanie dla scenariuszy, takich jak wyszukiwanie, gdzie jest modyfikowana obiektów globalnych lub dodawany lub usuwany z listy.

Ponadto jeśli dewelopera języka C++, który opracowuje dużych aplikacji Visual Studio 2019 podejścia biznesowego uczyniło symbole poza proc, dzięki czemu można debugować te aplikacje bez którym wystąpiły problemy związane z pamięcią.

### <a name="search-while-debugging"></a>Wyszukaj podczas debugowania

Prawdopodobnie byłeś istnieje, wyszukiwanie w oknie czujki ciągu oraz zestaw wartości. W programie Visual Studio 2019 r dodaliśmy wyszukiwania w oknach wyrażeń kontrolnych, zmiennych lokalnych i automatycznych ułatwią znalezienie obiektów i wartości, którego szukasz.

   ![Animację, pokazujący okno wyszukiwania debugowania w programie Visual Studio 2019 r.](media/vs-2019/debug-window-search.gif)

Możesz również sformatować, jak wartość jest wyświetlana w oknach wyrażenie kontrolne, zmiennych lokalnych i automatycznych.  Kliknij dwukrotnie jeden z elementów w żadnym z systemu windows, a następnie dodaj przecinek (","), aby uzyskać dostęp do listy rozwijanej specyfikatorów formatu możliwe, z których każdy zawiera opis jego zamierzony efekt.

   ![Obejrzyj okna i format wartości nowością w Visual Studio 2019 r.](media/search-watch-window.png)

Aby uzyskać więcej informacji, zobacz [rozszerzone w Visual Studio 2019 r.: Wyszukiwanie obiektów i właściwości w kontrolnych, zmiennych automatycznych i zmiennych lokalnych Windows](https://devblogs.microsoft.com/visualstudio/enhanced-in-visual-studio-2019-search-for-objects-and-properties-in-the-watch-autos-and-locals-windows/) wpis w blogu.

### <a name="snapshot-debugger"></a>Rozszerzenie Snapshot Debugger

Pobierz migawkę wykonywanie danej aplikacji w chmurze, aby zobaczyć dokładnie co się dzieje. (Ta funkcja jest dostępna w programie Visual Studio Enterprise,.)

   ![Animacji, który zawiera rozszerzenie Snapshot Debugger w Visual Studio Enterprise 2019 r](media/vs-2019/snapshot-debugger.gif)

Dodaliśmy obsługę przeznaczone dla aplikacji ASP.NET (desktop i Core), które są uruchamiane na Maszynie wirtualnej platformy Azure. Ponadto Dodaliśmy obsługę aplikacji działających w usłudze Azure Kubernetes Service. Rozszerzenie Snapshot Debugger może pomóc w znacznie skrócić czas potrzebny do rozwiązywania problemów występujących w środowiskach produkcyjnych.

Aby uzyskać więcej informacji, zobacz [debugowanie na żywo aplikacji ASP.NET, Azure, przy użyciu rozszerzenia Snapshot Debugger](../debugger/debug-live-azure-applications.md) strony, a [wprowadzenie do czasu podróży debugowania dla programu Visual Studio Enterprise 2019](https://devblogs.microsoft.com/visualstudio/introducing-time-travel-debugging-for-visual-studio-enterprise-2019/) wpis w blogu.

## <a name="whats-next"></a>Jaka jest przyszłość

Firma Microsoft aktualizuje program Visual Studio 2019 r często z nowymi funkcjami, które mogą ułatwić programowanie jeszcze lepsze środowisko. Aby dowiedzieć się więcej na temat naszych najnowszych innowacji, zapoznaj się z [Blog dotyczący programu Visual Studio](https://devblogs.microsoft.com/visualstudio/). I dla rekordu udostępniliśmy w wersji zapoznawczej do daty, Przyjrzyj się [informacje o wersji zapoznawczej](/visualstudio/releases/2019/release-notes-preview/).

Chcesz wiedzieć więcej o tym, co jeszcze znajduje się w działa dla programu Visual Studio 2019 r.? Zobacz [harmonogram działania programu Visual Studio](/visualstudio/productinfo/vs-roadmap/).

## <a name="give-us-feedback"></a>Przekaż nam swoją opinię

Dlaczego warto wysłać opinię do zespołu usługi Visual Studio? Ponieważ traktujemy opinie naszych użytkowników bardzo poważnie. Zależy od ilości co możemy zrobić.

* Jeśli chcesz sugestię o jak możemy ulepszyć program Visual Studio, możesz to zrobić za pomocą [sugestię](talk-to-us.md#i-want-to-make-a-suggestion-about-visual-studio-features) narzędzia.

* Jeśli wystąpią, zawieszenie, awarii lub innych problemów z wydajnością, można łatwo udostępniać kroki odtwarzania i towarzyszące mu pliki z nami za pomocą [Zgłoś Problem](talk-to-us.md#i-want-to-report-a-problem-with-visual-studio) narzędzia.

## <a name="see-also"></a>Zobacz także

* [Announcing Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/visual-studio-2019-code-faster-work-smarter-create-the-future/)
* [Informacje o wersji programu Visual Studio 2019 r](/visualstudio/releases/2019/release-notes/)
* [What's New in Visual Studio SDK 2019 r](../extensibility/whats-new-visual-studio-2019-sdk.md)
* [Visual Studio 2019 r dla komputerów Mac jest teraz dostępna](https://devblogs.microsoft.com/visualstudio/visual-studio-2019-for-mac-is-now-available/)
* [Microsoft Connect(); 2018 conference](https://www.microsoft.com/connectevent)

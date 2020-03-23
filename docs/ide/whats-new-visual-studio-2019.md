---
title: Co nowego w programie Visual Studio 2019
titleSuffix: ''
description: Dowiedz się więcej o nowych funkcjach programu Visual Studio 2019.
ms.date: 03/16/2020
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
ms.openlocfilehash: bf251ade250a466cefe02db6f5cc709a0c18837b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79437747"
---
# <a name="whats-new-in-visual-studio-2019"></a>Co nowego w programie Visual Studio 2019

**Aktualizacja [wersji 16.5](/visualstudio/releases/2019/release-notes/)**

>[!div class="button"]
>[Pobierz program Visual Studio 2019](https://visualstudio.microsoft.com/downloads)

Dzięki programowi Visual Studio 2019 otrzymasz najlepsze w swojej klasie narzędzia i usługi dla dowolnego dewelopera, dowolnej aplikacji i dowolnej platformy. Niezależnie od tego, czy używasz programu Visual Studio po raz pierwszy, czy używasz go od lat, w tej nowej wersji jest wiele do polubienia!

Oto podsumowanie tego, co nowego:

* **[Rozwijaj:](#develop)** Bądź skoncentrowany i produktywny dzięki lepszej wydajności, natychmiastowym oczyszczaniu kodu i lepszym wynikom wyszukiwania.
* **[Współpraca:](#collaborate)** Ciesz się naturalną współpracą dzięki przepływowi pracy po raz pierwszy w git, edycji i debugowaniu w czasie rzeczywistym oraz przeglądom kodu bezpośrednio w programie Visual Studio.
* **[Debugowanie:](#debug)** Wyróżnij i przejdź do określonych wartości, zoptymalizuj użycie pamięci i zrób automatyczne migawki wykonywania aplikacji.

Aby uzyskać pełną listę wszystkiego, co nowe w tej wersji, zobacz [informacje o wersji](/visualstudio/releases/2019/release-notes/).

## <a name="develop"></a>Programowanie

Zobacz poniższy film, aby dowiedzieć się więcej o tym, jak zaoszczędzić czas dzięki nowym funkcjom. <br><br>*Długość filmu: 3,00 minuty*

> [!VIDEO https://www.youtube.com/embed/n5sJ4EewKGk]

### <a name="improved-search"></a>Ulepszone wyszukiwanie

Dawniej znany jako Szybkie uruchamianie, nasze nowe doświadczenie wyszukiwania jest szybsze i bardziej skuteczne. Teraz wyniki wyszukiwania są wyświetlane dynamicznie podczas pisania. Wyniki wyszukiwania często zawierają skróty klawiaturowe dla poleceń, dzięki czemu można łatwiej zapamiętać je do wykorzystania w przyszłości.

   ![Animacja nowego środowiska wyszukiwania w programie Visual Studio 2019](media/vs-2019/new-search-feature.gif)

Nowa logika wyszukiwania rozmytego znajdzie wszystko, czego potrzebujesz, niezależnie od literówek. Niezależnie od tego, czy szukasz poleceń, ustawień, dokumentacji czy innych przydatnych rzeczy, nowa funkcja wyszukiwania ułatwia znalezienie tego, czego szukasz.

### <a name="refactorings"></a>Refaktoryzowania

Istnieje wiele nowych i bardzo przydatne refaktoryzacji w języku C#, które ułatwiają organizowanie kodu. Są one wyświetlane jako sugestie w żarówce i obejmują akcje, takie jak przenoszenie elementów członkowskich do interfejsu lub klasy podstawowej, dostosowywanie obszarów nazw w celu dopasowania struktury folderów, konwertowanie pętli foreach na zapytania Linq i inne.

   ![Animacja środowiska refaktoryzacji w programie Visual Studio 2019](media/vs-2019/refactorings.gif)

Wystarczy wywołać refaktoryzowania, naciskając **klawisze Ctrl+.** i wybierz akcję, którą chcesz podjąć.

### <a name="intellicode"></a>IntelliCode

[Visual Studio IntelliCode](/visualstudio/intellicode/) zwiększa wysiłki tworzenia oprogramowania przy użyciu sztucznej inteligencji (AI). IntelliCode trenuje w 2000 projektach typu&mdash;open source na GitHubie z ponad 100 gwiazdkami,&mdash;aby wygenerować swoje rekomendacje.

![Animacja intellicode w programie Visual Studio 2019](media/vs-2019/IntelliCode.gif)

Oto kilka sposobów, które program Visual Studio IntelliCode może pomóc zwiększyć produktywność:

* Dostarczanie uzupełnień kodu z uwzględnieniem kontekstu
* Poprowadź programistów, aby przestrzegali wzorców i stylów swojego zespołu
* Znajdowanie trudnych do wysypania problemów z kodem
* Przegląd kodu fokusowego, zwracając uwagę na obszary, które naprawdę mają znaczenie

Początkowo obsługiwane tylko C# podczas pierwszego podglądu IntelliCode jako rozszerzenie dla programu Visual Studio. Teraz **nowy w 16.1**, dodaliśmy obsługę języka C# i XAML "in-the-box". (Obsługa języka C++ i TypeScript/JavaScript jest jednak nadal w wersji zapoznawczej).

A jeśli używasz języka C#, dodaliśmy również możliwość uczenia niestandardowego modelu na własny kod.

Aby uzyskać więcej informacji na temat intellicode, zobacz [Ogłaszając ogólną dostępność IntelliCode plus sneak peek](https://devblogs.microsoft.com/visualstudio/announcing-the-general-availability-of-intellicode-plus-a-sneak-peek/) i [Kod więcej, przewiń mniej z Visual Studio IntelliCode](https://devblogs.microsoft.com/visualstudio/code-more-scroll-less-with-visual-studio-intellicode/) wpisów w blogu.

### <a name="code-cleanup"></a>Oczyszczanie kodu

W połączeniu z nowym wskaźnikiem kondycji dokumentu jest nowe polecenie oczyszczania kodu. Za pomocą tego nowego polecenia można zidentyfikować, a następnie naprawić ostrzeżenia i sugestie za pomocą kliknięcia przycisku.

Oczyszczanie sformatuje kod i zastosuje wszelkie poprawki kodu zgodnie z [sugestią bieżących ustawień](code-styles-and-code-cleanup.md) i [plików .editorconfig](create-portable-custom-editor-options.md).

   ![Zrzut ekranu przedstawiający nową kontrolkę oczyszczania kodu w programie Visual Studio 2019](media/vs-2019/code-cleanup-profile.png)

Można również zapisać kolekcje utrwalaczy jako profil. Na przykład jeśli masz mały zestaw fixerów docelowych, które są często stosowane podczas kodowania, a następnie masz inny kompleksowy zestaw utrwalaczy do zastosowania przed przeglądem kodu, można skonfigurować profile do rozwiązywania tych różnych zadań.

   ![Zrzut ekranu przedstawiający formant oczyszczania kodu w programie Visual Studio 2019](media/vs-2019/code-cleanup-profile-configure.png)

### <a name="per-monitor-aware-pma-rendering"></a>Renderowanie z uwzględnieniem monitora (PMA)

Jeśli używasz monitorów, które są skonfigurowane z różnymi współczynnikami skali wyświetlania lub łączą się zdalnie z komputerem z współczynnikami skali wyświetlania, które różnią się od urządzenia głównego, można zauważyć, że program Visual Studio wygląda rozmyte lub renderuje w niewłaściwej skali.

Wraz z wydaniem programu Visual Studio 2019 wprowadzamy aplikację dotwarujenia programu Visual Studio na monitor (PMA). Teraz Visual Studio renderuje poprawnie niezależnie od używanych współczynników skali wyświetlania.

   ![Renderowanie pma (pma) w programie Visual Studio 2019](media/vs-2019/pma-dpi-scaling.png)

Aby uzyskać więcej informacji, zobacz lepsze środowisko wielu monitorów z wpisem w blogu [programu Visual Studio 2019.](https://devblogs.microsoft.com/visualstudio/a-better-multi-monitor-experience-with-visual-studio-2019/)

### <a name="test-explorer"></a>Eksplorator testów

**Nowość w 16.2:** Zaktualizowaliśmy Eksploratora testów, aby zapewnić lepszą obsługę dużych zestawów testowych, łatwiejsze filtrowanie, bardziej wykrywalne polecenia, widoki listy odtwarzania z kartami i dostosowywane kolumny, które pozwalają dostosować wyświetlane informacje testowe.

   ![Zrzut ekranu przedstawiający ulepszenia interfejsu użytkownika w Eksploratorze testów](media/vs-2019/test-explorer-ui.png)

### <a name="net-core"></a>.NET Core

**Nowość w 16.3**: Uwzględniliśmy obsługę .NET Core 3.0. Międzyplatformowe,&mdash;open source i w pełni obsługiwane przez firmę Microsoft.

Aby uzyskać więcej informacji, zobacz wpis w blogu [Announcing .NET Core 3.0.](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/)

## <a name="collaborate"></a>Współpraca

Zobacz poniższy film, aby dowiedzieć się więcej o tym, jak współpracować, aby rozwiązać problemy. <br><br>*Długość filmu: 4,22 minuty*

> [!VIDEO https://www.youtube.com/embed/dKLJsiK1QU8]

### <a name="git-first-workflow"></a>Git-pierwszy przepływ pracy

Coś, co zauważysz po otwarciu programu Visual Studio 2019, to jego nowe okno startowe.

   ![Zrzut ekranu przedstawiający nowe okno startowe w programie Visual Studio 2019](media/vs-2019/start-window-dark.png)

Okno startowe przedstawia kilka opcji, aby szybko uzyskać kod. Umieściliśmy opcję klonowania lub wyewidencjonowywania kodu z repozytorium, najpierw.

   ![Animacja "Git-first" w programie Visual Studio 2019](media/vs-2019/git-first.gif)

Okno startowe zawiera również opcje otwierania projektu lub rozwiązania, otwierania folderu lokalnego lub tworzenia nowego projektu.

Aby uzyskać więcej informacji, zobacz [Get to code: Jak zaprojektowaliśmy nowy wpis w blogu okna startowego programu Visual Studio.](https://devblogs.microsoft.com/visualstudio/get-to-code-how-we-designed-the-new-visual-studio-start-window/)

### <a name="live-share"></a>Live Share

[Visual Studio Live Share](https://visualstudio.microsoft.com/services/live-share/) to usługa dewelopera, która umożliwia udostępnianie bazy kodu i jej kontekstu z kolegą z zespołu i uzyskać natychmiastową dwukierunkową współpracę bezpośrednio z poziomu programu Visual Studio. Dzięki usłudze Live Share członek zespołu może czytać, nawigować, edytować i debugować projekt, który został mu udostępniony, i robić to bezproblemowo i bezpiecznie.

A w programie Visual Studio 2019 ta usługa jest instalowana domyślnie.

![Animacja z funkcją współpracy udostępniania na żywo w programie Visual Studio 2019](media/vs-2019/live-share.gif)

Aby uzyskać więcej informacji, zobacz [Visual Studio Live Share dla przeglądów kodu w czasie rzeczywistym i interaktywnych wpisów](https://devblogs.microsoft.com/visualstudio/visual-studio-live-share-for-real-time-code-reviews-and-interactive-education/) w blogu edukacji i live share teraz dołączone do programu Visual Studio [2019](https://devblogs.microsoft.com/visualstudio/live-share-now-included-with-visual-studio-2019/) wpis w blogu.

### <a name="integrated-code-reviews"></a>Zintegrowane przeglądy kodu

Wprowadzamy nowe rozszerzenie, które można pobrać do użycia w programie Visual Studio 2019. Dzięki temu nowemu rozszerzeniu można przeglądać, uruchamiać, a nawet debugować żądania ściągania z zespołu bez opuszczania programu Visual Studio. Obsługujemy kod w repozytoriach GitHub i Azure DevOps.

   ![Zrzut ekranu przedstawiający nowe okno startowe w programie Visual Studio 2019](media/vs-2019/pr-experience.png)

Aby uzyskać więcej informacji, zobacz [przeglądy kodu przy użyciu wpisu w blogu rozszerzenia żądania ciągnienia programu Visual Studio.](https://devblogs.microsoft.com/visualstudio/code-reviews-using-the-visual-studio-pull-requests-extension/)

## <a name="debug"></a>Debugowanie

Zobacz poniższy film, aby dowiedzieć się więcej o tym, jak można wyzerować z precyzyjnym kierowaniem podczas debugowania. <br><br>*Długość filmu: 3,54 minuty*

> [!VIDEO https://www.youtube.com/embed/hr72Fs8n_9c]

### <a name="performance-gains"></a>Wzrost wydajności

Wzięliśmy raz wyłączne punkty przerwania danych języka C++ i dostosowaliśmy je do aplikacji .NET Core.

   ![Animacja, która pokazuje punkty przerwania danych debugowania w programie Visual Studio 2019](media/vs-2019/debug-data-breakpoints.gif)

Niezależnie od tego, czy kodujesz w języku C++ czy .NET Core, punkty przerwania danych mogą być dobrą alternatywą dla umieszczania regularnych punktów przerwania. Punkty przerwania danych są również idealne dla scenariuszy, takich jak znalezienie, gdzie obiekt globalny jest modyfikowany lub dodawany lub usuwany z listy.

A jeśli jesteś deweloperem języka C++, który rozwija duże aplikacje, Visual Studio 2019 dokonał symboli z proc, co pozwala na debugowanie tych aplikacji bez występowania problemów związanych z pamięcią.

### <a name="search-while-debugging"></a>Wyszukiwanie podczas debugowania

Prawdopodobnie byłeś tam wcześniej, patrząc w oknie czujki dla ciągu wśród zestawu wartości. W programie Visual Studio 2019 dodaliśmy wyszukiwanie w oknach Czujka, Lokalni mieszkańcy i Autos, aby ułatwić znajdowanie obiektów i wartości, których szukasz.

   ![Animacja z oknem wyszukiwania debugowania w programie Visual Studio 2019](media/vs-2019/debug-window-search.gif)

Można również sformatować sposób wyświetlania wartości w oknach Czujka, Zmienne lokalne i Autos.  Kliknij dwukrotnie jeden z elementów w dowolnym okienku i dodaj przecinek (","), aby uzyskać dostęp do listy rozwijanej możliwych specyfikatorów formatu, z których każdy zawiera opis zamierzonego efektu.

   ![Nowa funkcja funkcji okna i formatu zegarka w programie Visual Studio 2019](media/search-watch-window.png)

Aby uzyskać więcej informacji, zobacz [rozszerzone w programie Visual Studio 2019: Wyszukiwanie obiektów i właściwości w blogu czujki, autos i lokalnych mieszkańców systemu Windows.](https://devblogs.microsoft.com/visualstudio/enhanced-in-visual-studio-2019-search-for-objects-and-properties-in-the-watch-autos-and-locals-windows/)

### <a name="snapshot-debugger"></a>Debuger migawek

Pobierz migawkę wykonania aplikacji w chmurze, aby zobaczyć dokładnie, co się dzieje. (Ta funkcja jest dostępna tylko w programie Visual Studio Enterprise).

   ![Animacja z debugerem migawek w programie Visual Studio 2019 Enterprise](media/vs-2019/snapshot-debugger.gif)

Dodaliśmy obsługę aplikacji do kierowania ASP.NET (Core i desktop), które są uruchamiane na maszynie Wirtualnej platformy Azure. Dodaliśmy również obsługę aplikacji uruchamianych w usłudze Azure Kubernetes. Debuger migawek może pomóc znacznie skrócić czas potrzebny do rozwiązania problemów występujących w środowiskach produkcyjnych.

Aby uzyskać więcej informacji, zobacz [debugowanie aplikacji na żywo ASP.NET platformy Azure przy użyciu strony Debuger migawek](../debugger/debug-live-azure-applications.md) i wprowadzenie do [debugowania podróży w czasie dla programu Visual Studio Enterprise 2019](https://devblogs.microsoft.com/visualstudio/introducing-time-travel-debugging-for-visual-studio-enterprise-2019/) w blogu.

### <a name="microsoft-edge-insider-support"></a>Pomoc techniczna programu Microsoft Edge dla niejawnych testerów

**Nowość w 16.2**: Można ustawić punkt przerwania w aplikacji JavaScript i rozpocząć sesję debugowania za pomocą przeglądarki [Microsoft Edge Insider.](https://www.microsoftedgeinsider.com/) Po wykonaniu tej tej funkcji program Visual Studio otwiera nowe okno przeglądarki z włączonym debugowaniem, za pomocą którego można przejść przez aplikację JavaScript w programie Visual Studio.

   ![Zrzut ekranu przedstawiający renderowanie kodu JavaScript w przeglądarce](media/vs-2019/edge-chromium-breakpoint.png)

### <a name="pinnable-properties-tool"></a>Narzędzie Właściwości z przypinanymi

**Nowość w 16.4:** Teraz łatwiej jest zidentyfikować obiekty według ich właściwości podczas debugowania za pomocą nowego narzędzia Właściwości pinnable. Wystarczy najechać kursorem na właściwość, którą chcesz wyświetlić w oknie debugera okien Czujka, Autos i Locals, wybierz ikonę pinezki i natychmiast zobacz informacje, których szukasz w górnej części okna!

   ![Animacja, która pokazuje, jak przypiąć właściwości w debugerze programu Visual Studio przy użyciu narzędzia Właściwości pinnable](media/vs-2019/debugger-pinnable-properties.gif)

Aby uzyskać więcej informacji, zobacz wpis w blogu [Właściwości pinnable: Debug & Display Managed Objects YOUR Way.](https://devblogs.microsoft.com/visualstudio/pinnable-properties-debug-display-managed-objects-your-way/)

## <a name="whats-next"></a>Co dalej

Możemy aktualizować visual studio 2019 często z nowych funkcji, które mogą uczynić swoje środowisko programistyczne jeszcze lepiej. Aby dowiedzieć się więcej o naszych najnowszych innowacjach, zapoznaj się z [blogiem programu Visual Studio.](https://devblogs.microsoft.com/visualstudio/) Aby uzyskać zapis tego, co do tej pory opublikowaliśmy w wersji zapoznawczej, zapoznaj się z [uwagami do wersji zapoznawczej](/visualstudio/releases/2019/release-notes-preview/). Aby uzyskać listę tego, co planujemy wydać w następnej wersji, zobacz [plan działania programu Visual Studio](/visualstudio/productinfo/vs-roadmap).

Chcesz dowiedzieć się więcej o tym, co jeszcze znajduje się w pracach nad programem Visual Studio 2019? Zobacz [plan działania programu Visual Studio](/visualstudio/productinfo/vs-roadmap/).

## <a name="give-us-feedback"></a>Wyślij do nas swoją opinię

Dlaczego warto wysyłać opinie do zespołu programu Visual Studio? Ponieważ traktujemy opinie klientów poważnie. To napędza wiele z tego, co robimy.

* Jeśli chcesz przedstawić sugestię dotyczącą sposobu ulepszania programu Visual Studio, możesz to zrobić za pomocą narzędzia [Zaproponuj funkcję.](suggest-a-feature.md)

* Jeśli wystąpi problem z zawieszaniem się, awarią lub innym problemem z wydajnością, możesz łatwo udostępnić nam kroki repropro i pliki pomocnicze za pomocą narzędzia [Zgłoś problem.](how-to-report-a-problem-with-visual-studio.md)

## <a name="see-also"></a>Zobacz też

* [Informacje o wersji programu Visual Studio 2019](/visualstudio/releases/2019/release-notes/)
* [Informacje o wersji programu Visual Studio 2019 dla komputerów Mac](/visualstudio/releasenotes/vs2019-mac-relnotes/)
* [Co nowego w SDK programu Visual Studio 2019](../extensibility/whats-new-visual-studio-2019-sdk.md)
* [Konferencja microsoft build](https://www.microsoft.com/build)
* [Konferencja Microsoft Ignite](https://www.microsoft.com/ignite)

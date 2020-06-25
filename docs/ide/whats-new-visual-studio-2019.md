---
title: Co nowego w programie Visual Studio 2019
titleSuffix: ''
description: Dowiedz się więcej o nowych funkcjach w programie Visual Studio 2019.
ms.date: 05/20/2020
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
ms.openlocfilehash: 6b5058e0f1fabbf834a1adfb20d4f3a9a11094f5
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85283596"
---
# <a name="whats-new-in-visual-studio-2019"></a>Co nowego w programie Visual Studio 2019

**Zaktualizowano w [wersji 16,6](/visualstudio/releases/2019/release-notes/)**

>[!div class="button"]
>[Pobierz program Visual Studio 2019](https://visualstudio.microsoft.com/downloads)

Program Visual Studio ciągle zmienia się w celu spełnienia wymagań deweloperów. W poniższym filmie wideo z biblioteki **[kompilacji firmy Microsoft](https://mybuild.microsoft.com/)** Dołącz do nas, aby zapoznać się z [najnowszymi funkcjami](/visualstudio/releases/2019/release-notes/) i [zobaczyć wgląd](/visualstudio/releases/2019/release-notes-preview/) w to, co się stało: <br><br>*Długość wideo: 44,58 minut*

> [!VIDEO https://channel9.msdn.com/Events/Build/2020/BOD111/player]

W programie Visual Studio 2019 uzyskasz najlepsze w swojej klasie narzędzia i usługi dla każdego dewelopera, każdej aplikacji i dowolnej platformy. Bez względu na to, czy korzystasz z programu Visual Studio po raz pierwszy, czy korzystasz z niego przez kilka lat, możesz skorzystać z naszej najnowszej wersji.

Oto podsumowanie o nowościach, które są nowe:

* **[Programowanie](#develop)**: zapewnianie koncentracji i produktywności dzięki ulepszonej wydajności, błyskawicznemu oczyszczaniu kodu i lepszym wynikom wyszukiwania.
* **[Współpraca](#collaborate)**: Ciesz się naturalną pracą w ramach przepływu pracy usługi git — pierwszego, edytowania i debugowania w czasie rzeczywistym oraz przeglądów kodu w programie Visual Studio.
* **[Debugowanie](#debug)**: Wyróżnij i przejdź do określonych wartości, Optymalizuj użycie pamięci i wykonaj automatyczne migawki wykonywania aplikacji.

Aby zapoznać się z pełną listą wszystkiego, co nowego w tej wersji, zobacz [Informacje o wersji](/visualstudio/releases/2019/release-notes/).

## <a name="develop"></a>Programowanie

Obejrzyj poniższe wideo, aby dowiedzieć się więcej o tym, jak zaoszczędzić czas dzięki nowym funkcjom. <br><br>*Długość wideo: 3,00 minut*

> [!VIDEO https://www.youtube.com/embed/n5sJ4EewKGk]

### <a name="improved-search"></a>Ulepszone wyszukiwanie

Nowe środowisko wyszukiwania znane wcześniej jako szybkie uruchamianie jest szybsze i bardziej wydajne. Teraz wyniki wyszukiwania są wyświetlane dynamicznie podczas wpisywania. Wyniki wyszukiwania mogą często zawierać skróty klawiaturowe poleceń, dzięki czemu można łatwiej znają je do użytku w przyszłości.

   ![Animacja nowego środowiska wyszukiwania w programie Visual Studio 2019](media/vs-2019/new-search-feature.gif)

Nowa logika wyszukiwania rozmytego będzie dowiedzieć się, co jest potrzebne, bez względu na literówki. Tak więc, niezależnie od tego, czy szukasz poleceń, ustawień, dokumentacji lub innych użytecznych funkcji, Nowa funkcja wyszukiwania ułatwia znalezienie szukanych informacji.

### <a name="refactorings"></a>Refaktoryzacje

W języku C# istnieje wiele nowych i wysoko przydatnych refaktoryzacji, które ułatwiają organizowanie kodu. Są one wyświetlane jako sugestie w żarówki i obejmują akcje, takie jak przeniesienie elementów członkowskich do interfejsu lub klasy bazowej, dostosowując przestrzenie nazw do struktury folderów, Konwertuj pętle foreach na zapytania LINQ i nie tylko.

   ![Animacja środowiska refaktoryzacji w programie Visual Studio 2019](media/vs-2019/refactorings.gif)

Po prostu wywołaj refaktoryzację, naciskając **klawisze CTRL +.** i wybierając akcję, którą chcesz wykonać.

### <a name="intellicode"></a>IntelliCode

[Program Visual Studio rozszerzenia intellicode](/visualstudio/intellicode/) ulepsza działania związane z programowaniem oprogramowania przy użyciu sztucznej analizy (AI). Rozszerzenia intellicode pociągs 2 000 w projektach "open source" w witrynie GitHub &mdash; z ponad 100 gwiazdkami w &mdash; celu wygenerowania własnych zaleceń.

![Animacja rozszerzenia intellicode w programie Visual Studio 2019](media/vs-2019/IntelliCode.gif)

Oto kilka sposobów, które program Visual Studio rozszerzenia intellicode może pomóc w zwiększeniu produktywności:

* Dostarczanie uzupełniania kodu z obsługą kontekstu
* Przewodnik dla deweloperów, aby przestrzegać wzorców i stylów zespołu
* Znajdź problemy związane z kodem trudnym do przechwycenia
* Przeglądanie przeglądów kodu przez rysowanie uwagi do obszarów, które naprawdę się interesują

Początkowo obsługujemy tylko język C#, gdy najpierw rozszerzenia intellicode jako rozszerzenie programu Visual Studio. Teraz **Nowość w 16,1**, dodaliśmy obsługę języka C# i XAML "w polu". (Obsługa języka C++ i języka TypeScript/JavaScript jest jednak nadal w wersji zapoznawczej).

A jeśli korzystasz z języka C#, dodaliśmy również możliwość uczenia modelu niestandardowego na własnym kodzie.

Aby uzyskać więcej informacji na temat rozszerzenia intellicode, zobacz temat [ogłaszanie ogólnej dostępności rozszerzenia intellicode Plus a zobaczyć wglądu](https://devblogs.microsoft.com/visualstudio/announcing-the-general-availability-of-intellicode-plus-a-sneak-peek/) i [kodu, Przewiń mniej do wpisów w blogu programu Visual Studio rozszerzenia intellicode](https://devblogs.microsoft.com/visualstudio/code-more-scroll-less-with-visual-studio-intellicode/) .

### <a name="code-cleanup"></a>Czyszczenie kodu

Sparowany z nowym wskaźnikiem kondycji dokumentu jest nowym poleceniem oczyszczania kodu. To nowe polecenie służy do identyfikowania i naprawiania zarówno ostrzeżeń, jak i sugestii po kliknięciu przycisku.

Oczyszczanie sformatuje kod i zastosuje wszelkie poprawki kodu zgodnie z sugerowanymi przez [bieżące ustawienia](code-styles-and-code-cleanup.md) i [pliki. editorconfig](create-portable-custom-editor-options.md).

   ![Zrzut ekranu przedstawiający nową kontrolkę oczyszczania kodu w programie Visual Studio 2019](media/vs-2019/code-cleanup-profile.png)

Kolekcje naprawiających można także zapisywać jako profil. Na przykład jeśli masz niewielki zestaw dostosowanych naprawiających, które są często stosowane podczas kodu, a następnie masz inny kompleksowy zestaw naprawiających do zastosowania przed przeglądem kodu, możesz skonfigurować profile, aby rozwiązać te różne zadania.

   ![Zrzut ekranu przedstawiający kontrolkę Konfigurowanie czyszczenia kodu w programie Visual Studio 2019](media/vs-2019/code-cleanup-profile-configure.png)

### <a name="per-monitor-aware-pma-rendering"></a>Renderowanie oparte na monitorze (PMA)

Jeśli używasz monitorów, które są skonfigurowane przy użyciu różnych współczynników skalowania ekranu, lub Połącz się zdalnie z maszyną o współczynnikach skalowania, które różnią się od głównego urządzenia, możesz zauważyć, że program Visual Studio Wyświetla nierozmyte lub renderuje w niewłaściwej skali.

Dzięki wydaniu programu Visual Studio 2019 tworzymy program Visual Studio a na monitor (PMA). Teraz program Visual Studio jest poprawnie renderowany niezależnie od użytych czynników skalowania ekranu.

   ![Renderowanie oparte na monitorze (PMA) w programie Visual Studio 2019](media/vs-2019/pma-dpi-scaling.png)

Aby uzyskać więcej informacji, zobacz [lepsze środowisko z wieloma monitorami w blogu programu Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/a-better-multi-monitor-experience-with-visual-studio-2019/) .

### <a name="test-explorer"></a>Eksplorator testów

**Nowość w 16,2**: Zaktualizowaliśmy Eksploratora testów w celu zapewnienia lepszej obsługi dużych zestawów testów, łatwiejszego filtrowania, bardziej wykrywalnych poleceń, widoków listy odtwarzania z kartami i dostosowywalnych kolumn, które umożliwiają precyzyjne dostosowanie informacji o testowaniu.

   ![Zrzut ekranu pokazujący ulepszenia interfejsu użytkownika w Eksploratorze testów](media/vs-2019/test-explorer-ui.png)

### <a name="net-core"></a>.NET Core

**Nowość w 16,3**: dołączono obsługę programu .net Core 3,0. Międzyplatformowe, Open Source &mdash; i w pełni obsługiwane przez firmę Microsoft.

Aby uzyskać więcej informacji, zobacz wpis na blogu dotyczący [programu .NET Core 3,0](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/) .

## <a name="collaborate"></a>Współpraca

Obejrzyj poniższe wideo, aby dowiedzieć się więcej o tym, jak zespół może rozwiązać problemy. <br><br>*Długość wideo: 4,22 minut*

> [!VIDEO https://www.youtube.com/embed/dKLJsiK1QU8]

### <a name="git-first-workflow"></a>Git — pierwszy przepływ pracy

Informacje, które należy zauważyć po otwarciu programu Visual Studio 2019, jest nowym oknem startowym.

   ![Zrzut ekranu przedstawiający nowe okno uruchamiania w programie Visual Studio 2019](media/vs-2019/start-window-dark.png)

Okno startowe zawiera kilka opcji umożliwiających szybkie przechodzenie do kodu. W pierwszej kolejności została umieszczona opcja klonowania lub wyewidencjonowywania kodu z repozytorium.

   ![Animacja środowiska "Git-First" w programie Visual Studio 2019](media/vs-2019/git-first.gif)

Okno uruchamiania zawiera również opcje otwierania projektu lub rozwiązania, otwierania folderu lokalnego lub tworzenia nowego projektu.

Aby uzyskać więcej informacji, zobacz artykuł [wprowadzenie do kodu: jak zaprojektowano nowy wpis w blogu uruchamiania programu Visual Studio](https://devblogs.microsoft.com/visualstudio/get-to-code-how-we-designed-the-new-visual-studio-start-window/) .

### <a name="live-share"></a>Live Share

[Visual Studio Live Share](https://visualstudio.microsoft.com/services/live-share/) to usługa dla deweloperów, która umożliwia udostępnianie bazy kodu i jej kontekstu członkom zespołu i szybkie współpracę dwukierunkową bezpośrednio z poziomu programu Visual Studio. Za pomocą Live Share, członkowie zespołu mogą odczytywać, nawigować, edytować i debugować projekt, który został Ci udostępniony, a tym samym bezproblemowo i bezpieczniej.

I w programie Visual Studio 2019 ta usługa jest instalowana domyślnie.

![Animacja pokazująca funkcję współpracy Live Share w programie Visual Studio 2019](media/vs-2019/live-share.gif)

Aby uzyskać więcej informacji, zobacz [Visual Studio Live Share do przeglądu kodu w czasie rzeczywistym i wpisu w blogu interaktywnej edukacji](https://devblogs.microsoft.com/visualstudio/visual-studio-live-share-for-real-time-code-reviews-and-interactive-education/) oraz [Live Share teraz zawarte w blogu programu Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/live-share-now-included-with-visual-studio-2019/) .

### <a name="integrated-code-reviews"></a>Zintegrowane przeglądy kodu

Wprowadzamy nowe rozszerzenie, które można pobrać do użycia z programem Visual Studio 2019. Dzięki temu nowemu rozszerzeniu można przeglądać, uruchamiać i nawet debugować żądania ściągnięcia z zespołu bez opuszczania programu Visual Studio. Obsługujemy kod zarówno w repozytoriach GitHub, jak i na platformie Azure DevOps.

   ![Zrzut ekranu przedstawiający nowe okno uruchamiania w programie Visual Studio 2019](media/vs-2019/pr-experience.png)

Aby uzyskać więcej informacji, zobacz wpis w blogu dotyczący [przeglądów kodu przy użyciu rozszerzenia żądań ściągnięcia programu Visual Studio](https://devblogs.microsoft.com/visualstudio/code-reviews-using-the-visual-studio-pull-requests-extension/) .

## <a name="debug"></a>Debugowanie

Obejrzyj poniższy film wideo, aby dowiedzieć się więcej o tym, jak można się od zera w programie przy użyciu precyzyjnego określania wartości docelowej podczas debugowania. <br><br>*Długość wideo: 3,54 minut*

> [!VIDEO https://www.youtube.com/embed/hr72Fs8n_9c]

### <a name="performance-gains"></a>Zyski wydajności

Przeprowadzono jednorazowe punkty przerwania danych języka C++ i dostosowuje je do aplikacji .NET Core.

   ![Animacja pokazująca punkty przerwania danych debugowania w programie Visual Studio 2019](media/vs-2019/debug-data-breakpoints.gif)

Dlatego niezależnie od tego, czy kodowanie jest kodowane w języku C++, czy .NET Core, punkty przerwania danych mogą być dobrym rozwiązaniem alternatywnym do wprowadzania zwykłych punktów przerwania. Punkty przerwania danych są również doskonałe dla scenariuszy, takich jak znajdowanie, gdzie obiekt globalny jest modyfikowany lub dodawany lub usuwany z listy.

Jeśli jesteś deweloperem języka C++, który opracowuje duże aplikacje, program Visual Studio 2019 ma symbole z procesu, co umożliwia debugowanie tych aplikacji bez problemów związanych z pamięcią.

### <a name="search-while-debugging"></a>Wyszukaj podczas debugowania

Prawdopodobnie już wcześniej szukasz w okno wyrażeń kontrolnych ciągu z zestawu wartości. W programie Visual Studio 2019 dodaliśmy wyszukiwanie w oknach czujka, lokalne i autostarty, aby ułatwić znalezienie szukanych obiektów i wartości.

   ![Animacja pokazująca okno wyszukiwania debugowania w programie Visual Studio 2019](media/vs-2019/debug-window-search.gif)

Możesz również sformatować sposób wyświetlania wartości w oknach czujki, lokalne i autouzupełniania.  Kliknij dwukrotnie jeden z elementów w dowolnym z okien i Dodaj przecinek (","), aby uzyskać dostęp do listy rozwijanej możliwych specyfikatorów formatu, z których każdy zawiera opis zamierzonego efektu.

   ![Nowa funkcja wartości okno wyrażeń kontrolnych i format w programie Visual Studio 2019](media/search-watch-window.png)

Aby uzyskać więcej informacji, zobacz [ulepszony w programie Visual Studio 2019: wyszukiwanie obiektów i właściwości w wpisie w blogu "Watch, autostarts" i lokalnych](https://devblogs.microsoft.com/visualstudio/enhanced-in-visual-studio-2019-search-for-objects-and-properties-in-the-watch-autos-and-locals-windows/) .

### <a name="snapshot-debugger"></a>Debuger migawek

Utwórz migawkę wykonywania aplikacji w chmurze, aby zobaczyć dokładnie, co się dzieje. (Ta funkcja jest dostępna tylko w Visual Studio Enterprise.)

   ![Animacja pokazująca Snapshot Debugger w programie Visual Studio 2019 Enterprise](media/vs-2019/snapshot-debugger.gif)

Dodaliśmy obsługę aplikacji ASP.NET (Core i Desktop), które działają na maszynie wirtualnej platformy Azure. Dodaliśmy obsługę aplikacji uruchamianych w usłudze Azure Kubernetes. Snapshot Debugger może pomóc znacząco skrócić czas potrzebny do rozwiązania problemów występujących w środowiskach produkcyjnych.

Aby uzyskać więcej informacji, zobacz Debugowanie [live ASP.NET Azure Apps przy użyciu strony Snapshot Debugger](../debugger/debug-live-azure-applications.md) i wprowadzenie do [debugowania czasu podróży dla Visual Studio Enterprise 2019](https://devblogs.microsoft.com/visualstudio/introducing-time-travel-debugging-for-visual-studio-enterprise-2019/) .

### <a name="microsoft-edge-insider-support"></a>Pomoc techniczna programu Microsoft Edge dla niejawnych testerów

**Nowość w 16,2**: można ustawić punkt przerwania w aplikacji JavaScript i rozpocząć sesję debugowania przy użyciu przeglądarki [Microsoft Edge insideer](https://www.microsoftedgeinsider.com/) . Gdy to zrobisz, program Visual Studio otworzy nowe okno przeglądarki z włączonym debugowaniem, którego można następnie użyć do przechodzenia przez aplikację JavaScript w programie Visual Studio.

   ![Zrzut ekranu, który pokazuje renderowanie kodu JavaScript w przeglądarce](media/vs-2019/edge-chromium-breakpoint.png)

### <a name="pinnable-properties-tool"></a>Narzędzie właściwości Pinnable

**Nowość w 16,4**: teraz łatwiej jest identyfikować obiekty według ich właściwości podczas debugowania za pomocą nowego narzędzia Pinnable Properties. Po prostu umieść kursor nad właściwością, która ma zostać wyświetlona w oknie Debuger w oknach czujka, automatycznie i lokalne, wybierz ikonę pinezki i od razu Zobacz informacje, których szukasz w górnej części okna.

   ![Animacja pokazująca, jak przypiąć właściwości w debugerze programu Visual Studio za pomocą narzędzia właściwości Pinnable](media/vs-2019/debugger-pinnable-properties.gif)

Aby uzyskać więcej informacji, zobacz [Pinnablee właściwości: Debug & Wyświetlaj obiekty zarządzane](https://devblogs.microsoft.com/visualstudio/pinnable-properties-debug-display-managed-objects-your-way/) w blogu.

## <a name="whats-next"></a>Co dalej

Często aktualizujemy program Visual Studio 2019 dzięki nowym funkcjom, które mogą usprawnić pracę programistyczną. Aby dowiedzieć się więcej na temat najnowszych innowacji, zapoznaj się z [blogiem dotyczącym programu Visual Studio](https://devblogs.microsoft.com/visualstudio/). Aby zapoznać się z rekordem, który został ogłoszony w wersji zapoznawczej, zapoznaj się z informacjami dotyczącymi [wersji zapoznawczej](/visualstudio/releases/2019/release-notes-preview/). Aby zapoznać się z listą zaplanowanych do wydania usługi, zobacz [Przewodnik po programie Visual Studio](/visualstudio/productinfo/vs-roadmap).

Chcesz dowiedzieć się więcej na temat tego, co jeszcze znajduje się w programie Works dla programu Visual Studio 2019? Zapoznaj się z [planem programu Visual Studio](/visualstudio/productinfo/vs-roadmap/).

## <a name="give-us-feedback"></a>Wyślij do nas swoją opinię

Dlaczego warto wysłać opinię do zespołu programu Visual Studio? Ze względu na to, że potraktujemy Opinie klientów. To wszystko, co robimy.

* Jeśli chcesz dowiedzieć się, jak możemy ulepszyć program Visual Studio, możesz to zrobić za pomocą narzędzia [Sugeruj funkcję](suggest-a-feature.md) .

* W przypadku wystąpienia zawieszenia, awarii lub innego problemu z wydajnością można łatwo udostępnić Odtwórz kroki i pliki pomocnicze za pomocą narzędzia [Zgłoś problem](how-to-report-a-problem-with-visual-studio.md) .

## <a name="see-also"></a>Zobacz też

* [Informacje o wersji programu Visual Studio 2019](/visualstudio/releases/2019/release-notes/)
* [Informacje o wersji programu Visual Studio 2019 dla komputerów Mac](/visualstudio/releasenotes/vs2019-mac-relnotes/)
* [Co nowego w zestawie SDK programu Visual Studio 2019](../extensibility/whats-new-visual-studio-2019-sdk.md)
* [Co nowego w języku C++ w programie Visual Studio](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio.md)
* [Co nowego w języku C# 8,0](/dotnet/csharp/whats-new/csharp-8.md)
* [Co nowego w programie .NET Core 3.1](/dotnet/core/whats-new/dotnet-core-3-1.md)
* [Co nowego w .NET Framework](/dotnet/framework/whats-new.md)
* [Konferencja Build firmy Microsoft](https://www.microsoft.com/build)
* [Konferencja Microsoft Ignite](https://www.microsoft.com/ignite)

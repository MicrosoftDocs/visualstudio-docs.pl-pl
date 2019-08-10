---
title: Co nowego w programie Visual Studio 2019
titleSuffix: ''
description: Dowiedz się więcej o nowych funkcjach w programie Visual Studio 2019.
ms.date: 07/23/2019
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
ms.openlocfilehash: 1f4a055f62fe76c701858f82b4778f7a3b19fa0a
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68918788"
---
# <a name="whats-new-in-visual-studio-2019"></a>Co nowego w programie Visual Studio 2019

**Zaktualizowano w [wersji 16,2](/visualstudio/releases/2019/release-notes/)**

>[!div class="button"]
>[Pobierz program Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)

W programie Visual Studio 2019 uzyskasz najlepsze w swojej klasie narzędzia i usługi dla każdego dewelopera, każdej aplikacji i dowolnej platformy. Bez względu na to, czy korzystasz z programu Visual Studio po raz pierwszy, czy korzystasz z niego przez kilka lat, w tej nowej wersji możesz użyć dużej ilości danych.

Oto podsumowanie o nowościach:

* **[Programowanie](#develop)** : Kontynuuj pracę i produktywność dzięki ulepszonej wydajności, błyskawicznemu oczyszczaniu kodu i lepszym wynikom wyszukiwania.
* **[Współpraca](#collaborate)** : Ciesz się naturalną pracą w ramach przepływu pracy usługi git — pierwszego, edytowania i debugowania w czasie rzeczywistym oraz przeglądów kodu w programie Visual Studio.
* **[Debuguj](#debug)** : Wyróżnij i przejdź do określonych wartości, Optymalizuj użycie pamięci i wykonaj automatyczne migawki wykonywania aplikacji.

Aby zapoznać się z pełną listą wszystkiego, co nowego w tej wersji, zobacz [Informacje o wersji](/visualstudio/releases/2019/release-notes/).

## <a name="develop"></a>Programowanie

Obejrzyj poniższe wideo, aby dowiedzieć się więcej o tym, jak zaoszczędzić czas dzięki nowym funkcjom. <br><br>*Długość wideo: 3,00 minut*

> [!VIDEO https://www.youtube.com/embed/n5sJ4EewKGk]

### <a name="improved-search"></a>Ulepszone wyszukiwanie

Nowe środowisko wyszukiwania znane wcześniej jako szybkie uruchamianie jest szybsze i bardziej wydajne. Teraz wyniki wyszukiwania są wyświetlane dynamicznie podczas wpisywania. Wyniki wyszukiwania mogą często zawierać skróty klawiaturowe poleceń, dzięki czemu można łatwiej znają je do użytku w przyszłości.

   ![Animacja nowego środowiska wyszukiwania w programie Visual Studio 2019](media/vs-2019/new-search-feature.gif)

Nowa logika wyszukiwania rozmytego będzie dowiedzieć się, co jest potrzebne, bez względu na literówki. Tak więc, niezależnie od tego, czy szukasz poleceń, ustawień, dokumentacji lub innych użytecznych funkcji, Nowa funkcja wyszukiwania ułatwia znalezienie szukanych informacji.

### <a name="refactorings"></a>Refaktoryzacje

Istnieje wiele nowych i wysoko przydatnych operacji refaktoryzacji w programie C# , które ułatwiają organizowanie kodu. Są one wyświetlane jako sugestie w żarówki i obejmują akcje, takie jak przeniesienie elementów członkowskich do interfejsu lub klasy bazowej, dostosowując przestrzenie nazw do struktury folderów, Konwertuj pętle foreach na zapytania LINQ i nie tylko.

   ![Animacja środowiska refaktoryzacji w programie Visual Studio 2019](media/vs-2019/refactorings.gif)

Po prostu wywołaj refaktoryzację, naciskając **klawisze CTRL +.** i wybierając akcję, którą chcesz wykonać.

### <a name="intellicode"></a>IntelliCode

[Program Visual Studio rozszerzenia intellicode](/visualstudio/intellicode/) ulepsza działania związane z programowaniem oprogramowania przy użyciu sztucznej analizy (AI). Rozszerzenia intellicode pociągs 2 000 w projektach "open source"&mdash;w witrynie GitHub z ponad&mdash;100 gwiazdkami w celu wygenerowania własnych zaleceń.

![Animacja rozszerzenia intellicode w programie Visual Studio 2019](media/vs-2019/IntelliCode.gif)

Oto kilka sposobów, które program Visual Studio rozszerzenia intellicode może pomóc w zwiększeniu produktywności:

* Dostarczanie uzupełniania kodu z obsługą kontekstu
* Przewodnik dla deweloperów, aby przestrzegać wzorców i stylów zespołu
* Znajdź problemy związane z kodem trudnym do przechwycenia
* Przeglądanie przeglądów kodu przez rysowanie uwagi do obszarów, które naprawdę się interesują

Początkowo są obsługiwane tylko C# wtedy, gdy najpierw przeglądamy rozszerzenia intellicode jako rozszerzenie dla programu Visual Studio. Teraz, **Nowość w 16,1**, dodaliśmy obsługę języka C# i XAML "w polu". (Obsługa C++ i język TypeScript/JavaScript są jednak nadal dostępne w wersji zapoznawczej).

W przypadku korzystania C#z programu Dodaliśmy także możliwość uczenia modelu niestandardowego na własnym kodzie.

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

**Nowość w 16,2**: Zaktualizowaliśmy Eksploratora testów w celu zapewnienia lepszej obsługi dużych zestawów testów, łatwiejszego filtrowania, bardziej wykrywalnych poleceń, widoków listy odtwarzania z kartami i dostosowywalnych kolumn umożliwiających precyzyjne dostosowanie informacji o testowaniu.

   ![Zrzut ekranu pokazujący ulepszenia interfejsu użytkownika w Eksploratorze testów](media/vs-2019/test-explorer-ui.png)

## <a name="collaborate"></a>Współpraca

Obejrzyj poniższe wideo, aby dowiedzieć się więcej o tym, jak zespół może rozwiązać problemy. <br><br>*Długość wideo: 4,22 minut*

> [!VIDEO https://www.youtube.com/embed/dKLJsiK1QU8]

### <a name="cloud-first-workflow"></a>Cloud-pierwszy przepływ pracy

Informacje, które należy zauważyć po otwarciu programu Visual Studio 2019, jest nowym oknem startowym.

   ![Zrzut ekranu przedstawiający nowe okno uruchamiania w programie Visual Studio 2019](media/vs-2019/start-window-dark.png)

Okno startowe zawiera kilka opcji umożliwiających szybkie przechodzenie do kodu. W pierwszej kolejności została umieszczona opcja klonowania lub wyewidencjonowywania kodu z repozytorium.

   ![Animacja środowiska "Git-First" w programie Visual Studio 2019](media/vs-2019/git-first.gif)

Okno uruchamiania zawiera również opcje otwierania projektu lub rozwiązania, otwierania folderu lokalnego lub tworzenia nowego projektu.

Aby uzyskać więcej informacji, zobacz [wprowadzenie do kodu: Jak zaprojektowano nowy wpis w blogu dla](https://devblogs.microsoft.com/visualstudio/get-to-code-how-we-designed-the-new-visual-studio-start-window/) okna startowego programu Visual Studio.

### <a name="live-share"></a>Live Share

[Visual Studio Live Share](https://visualstudio.microsoft.com/services/live-share/) to usługa dla deweloperów, która umożliwia udostępnianie bazy kodu i jej kontekstu członkom zespołu i szybkie współpracę dwukierunkową bezpośrednio z poziomu programu Visual Studio. Za pomocą Live Share, członkowie zespołu mogą odczytywać, nawigować, edytować i debugować projekt, który został Ci udostępniony, a tym samym bezproblemowo i bezpieczniej.

I w programie Visual Studio 2019 ta usługa jest instalowana domyślnie.

![Animacja pokazująca funkcję współpracy Live Share w programie Visual Studio 2019](media/vs-2019/live-share.gif)

Aby uzyskać więcej informacji, zobacz [Visual Studio Live Share do przeglądu kodu w czasie rzeczywistym i](https://devblogs.microsoft.com/visualstudio/visual-studio-live-share-for-real-time-code-reviews-and-interactive-education/) wpisu w blogu interaktywnej edukacji oraz [Live Share teraz zawarte w blogu programu Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/live-share-now-included-with-visual-studio-2019/) .

### <a name="integrated-code-reviews"></a>Zintegrowane przeglądy kodu

Wprowadzamy nowe rozszerzenie, które można pobrać do użycia z programem Visual Studio 2019. Dzięki temu nowemu rozszerzeniu można przeglądać, uruchamiać i nawet debugować żądania ściągnięcia z zespołu bez opuszczania programu Visual Studio. Obsługujemy kod zarówno w repozytoriach GitHub, jak i na platformie Azure DevOps.

   ![Zrzut ekranu przedstawiający nowe okno uruchamiania w programie Visual Studio 2019](media/vs-2019/pr-experience.png)

Aby uzyskać więcej informacji, zobacz wpis w blogu dotyczący [przeglądów kodu przy użyciu rozszerzenia żądań ściągnięcia programu Visual Studio](https://devblogs.microsoft.com/visualstudio/code-reviews-using-the-visual-studio-pull-requests-extension/) .

## <a name="debug"></a>Debugowanie

Obejrzyj poniższy film wideo, aby dowiedzieć się więcej o tym, jak można się od zera w programie przy użyciu precyzyjnego określania wartości docelowej podczas debugowania. <br><br>*Długość wideo: 3,54 minut*

> [!VIDEO https://www.youtube.com/embed/hr72Fs8n_9c]

### <a name="performance-gains"></a>Zyski wydajności

Przeprowadzono jednorazowe punkty przerwania C++ danych i dostosowuje je do aplikacji .NET Core.

   ![Animacja pokazująca punkty przerwania danych debugowania w programie Visual Studio 2019](media/vs-2019/debug-data-breakpoints.gif)

Dlatego niezależnie od tego, czy C++ używasz kodowania w programie, czy .NET Core, punkty przerwania danych mogą być dobrym rozwiązaniem alternatywnym do wprowadzania zwykłych punktów przerwania. Punkty przerwania danych są również doskonałe dla scenariuszy, takich jak znajdowanie, gdzie obiekt globalny jest modyfikowany lub dodawany lub usuwany z listy.

A jeśli jesteś C++ deweloperem, który opracowuje duże aplikacje, program Visual Studio 2019 ma symbole z procesu, co umożliwia debugowanie tych aplikacji bez problemów związanych z pamięcią.

### <a name="search-while-debugging"></a>Wyszukaj podczas debugowania

Prawdopodobnie już wcześniej szukasz w okno wyrażeń kontrolnych ciągu z zestawu wartości. W programie Visual Studio 2019 dodaliśmy wyszukiwanie w oknach czujka, lokalne i autostarty, aby ułatwić znalezienie szukanych obiektów i wartości.

   ![Animacja pokazująca okno wyszukiwania debugowania w programie Visual Studio 2019](media/vs-2019/debug-window-search.gif)

Możesz również sformatować sposób wyświetlania wartości w oknach czujki, lokalne i autouzupełniania.  Kliknij dwukrotnie jeden z elementów w dowolnym z okien i Dodaj przecinek (","), aby uzyskać dostęp do listy rozwijanej możliwych specyfikatorów formatu, z których każdy zawiera opis zamierzonego efektu.

   ![Nowa funkcja wartości okno wyrażeń kontrolnych i format w programie Visual Studio 2019](media/search-watch-window.png)

Aby uzyskać więcej informacji, zobacz [ulepszony w programie Visual Studio 2019: Wyszukaj obiekty i właściwości w wpisie w](https://devblogs.microsoft.com/visualstudio/enhanced-in-visual-studio-2019-search-for-objects-and-properties-in-the-watch-autos-and-locals-windows/) blogu "Watch, autoi".

### <a name="snapshot-debugger"></a>Rozszerzenie Snapshot Debugger

Utwórz migawkę wykonywania aplikacji w chmurze, aby zobaczyć dokładnie, co się dzieje. (Ta funkcja jest dostępna tylko w Visual Studio Enterprise.)

   ![Animacja pokazująca Snapshot Debugger w programie Visual Studio 2019 Enterprise](media/vs-2019/snapshot-debugger.gif)

Dodaliśmy obsługę aplikacji ASP.NET (Core i Desktop), które działają na maszynie wirtualnej platformy Azure. Dodaliśmy obsługę aplikacji uruchamianych w usłudze Azure Kubernetes. Rozszerzenie Snapshot Debugger może pomóc w znacznie skrócić czas potrzebny do rozwiązywania problemów występujących w środowiskach produkcyjnych.

Aby uzyskać więcej informacji, zobacz Debugowanie [live ASP.NET Azure Apps przy użyciu strony Snapshot Debugger](../debugger/debug-live-azure-applications.md) i wprowadzenie do [debugowania czasu podróży dla Visual Studio Enterprise 2019](https://devblogs.microsoft.com/visualstudio/introducing-time-travel-debugging-for-visual-studio-enterprise-2019/) .

### <a name="microsoft-edge-insider-support"></a>Pomoc techniczna programu Microsoft Edge dla niejawnych testerów

**Nowość w 16,2**: Możesz ustawić punkt przerwania w aplikacji JavaScript i rozpocząć sesję debugowania przy użyciu przeglądarki niejawnego [testera programu Microsoft Edge](https://www.microsoftedgeinsider.com/) . Gdy to zrobisz, program Visual Studio otworzy nowe okno przeglądarki z włączonym debugowaniem, którego można następnie użyć do przechodzenia przez aplikację JavaScript w programie Visual Studio.

   ![Zrzut ekranu, który pokazuje renderowanie kodu JavaScript w przeglądarce](media/vs-2019/edge-chromium-breakpoint.png)

## <a name="whats-next"></a>Co dalej

Często aktualizujemy program Visual Studio 2019 dzięki nowym funkcjom, które mogą usprawnić pracę programistyczną. Aby dowiedzieć się więcej na temat najnowszych innowacji, zapoznaj się z blogiem dotyczącym [programu Visual Studio](https://devblogs.microsoft.com/visualstudio/). Aby uzyskać informacje o tym, co opublikowano w wersji zapoznawczej, zapoznaj się z [informacjami o wersji](/visualstudio/releases/2019/release-notes-preview/)zapoznawczej.

Chcesz dowiedzieć się więcej na temat tego, co jeszcze znajduje się w programie Works dla programu Visual Studio 2019? Zapoznaj się z [planem programu Visual Studio](/visualstudio/productinfo/vs-roadmap/).

## <a name="give-us-feedback"></a>Przekaż nam swoją opinię

Dlaczego warto wysłać opinię do zespołu usługi Visual Studio? Ponieważ traktujemy opinie naszych użytkowników bardzo poważnie. To wszystko, co robimy.

* Jeśli chcesz dowiedzieć się, jak możemy ulepszyć program Visual Studio, możesz to zrobić za pomocą narzędzia [Sugeruj funkcję](suggest-a-feature.md) .

* W przypadku wystąpienia zawieszenia, awarii lub innego problemu z wydajnością można łatwo udostępnić Odtwórz kroki i pliki pomocnicze za pomocą narzędzia [Zgłoś problem](how-to-report-a-problem-with-visual-studio.md) .

## <a name="see-also"></a>Zobacz także

* [Informacje o wersji programu Visual Studio 2019](/visualstudio/releases/2019/release-notes/)
* [Co nowego w zestawie SDK programu Visual Studio 2019](../extensibility/whats-new-visual-studio-2019-sdk.md)
* [Informacje o wersji programu Visual Studio 2019 dla komputerów Mac](/visualstudio/releasenotes/vs2019-mac-relnotes/)
* [Konferencja Microsoft Build 2019](https://www.microsoft.com/build)
* [Microsoft Connect (); Konferencja 2018](https://www.microsoft.com/connectevent)

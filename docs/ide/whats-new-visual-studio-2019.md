---
title: Co nowego w programie Visual Studio 2019
titleSuffix: ''
description: Dowiedz się więcej o nowych funkcjach w Visual Studio 2019 r.
ms.date: 05/28/2021
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 00bec66b-bcee-46f5-91d9-f73a2b469744
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 1860c399318dbe68c55db9b07068c3dd635481c9
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2021
ms.locfileid: "112113064"
---
# <a name="whats-new-in-visual-studio-2019"></a>Co nowego w programie Visual Studio 2019

**Zaktualizowano w wersji 16.10.** Zobacz [pełne informacje o wersji |](/visualstudio/releases/2019/release-notes/) Wyświetlanie [planu rozwoju produktu](/visualstudio/productinfo/vs-roadmap)

>[!div class="button"]
>[Pobierz program Visual Studio 2019](https://visualstudio.microsoft.com/downloads)

W Visual Studio 2019 r. otrzymasz najlepsze w swojej klasie narzędzia i usługi dla dowolnego dewelopera, dowolnej aplikacji i dowolnej platformy. Bez względu na to, czy używasz aplikacji Visual Studio po raz pierwszy, czy od lat, w naszej najnowszej wersji jest wiele podobnych funkcji!

Oto podsumowanie wszystkich nowości na wysokim poziomie:

* **[Opracowywanie:](#develop)** pozostań skoncentrowany i produktywny dzięki lepszej wydajności, błyskawicznemu czyszczeniu kodu i lepszym wynikom wyszukiwania.
* **[Współpraca:](#collaborate)** korzystaj z naturalnej współpracy dzięki przepływowi pracy, edytowaniu i debugowaniu w czasie rzeczywistym oraz przeglądom kodu bezpośrednio w Visual Studio.
* **[Debugowanie:](#debug)** wyróżnianie określonych wartości i przechodzenie do nich, optymalizowanie użycia pamięci i automatyczne tworzenie migawek wykonywania aplikacji.

Aby uzyskać pełną listę wszystkich nowości w tej wersji, zobacz informacje [o wersji](/visualstudio/releases/2019/release-notes/).

## <a name="develop"></a>Programowanie

Zobacz poniższy film wideo, aby dowiedzieć się więcej o tym, jak zaoszczędzić czas dzięki nowym funkcji. <br><br>*Długość wideo: 3,00 min*

> [!VIDEO https://www.youtube.com/embed/n5sJ4EewKGk]

### <a name="improved-search"></a>Ulepszone wyszukiwanie

Nasza nowa Szybkie uruchamianie, wcześniej znana jako Szybkie uruchamianie, jest szybsza i bardziej efektywna. Teraz wyniki wyszukiwania są wyświetlane dynamicznie podczas wpisywania. Wyniki wyszukiwania mogą często zawierać skróty klawiaturowe dla poleceń, dzięki czemu można je zapamiętać do użytku w przyszłości.

   ![Animacja nowego funkcji wyszukiwania w programie Visual Studio 2019](media/vs-2019/new-search-feature.gif "Nowe środowisko wyszukiwania w Visual Studio 2019 r.")

Nowa logika wyszukiwania rozmytego znajdzie wszystko, czego potrzebujesz, niezależnie od literówek. Niezależnie od tego, czy szukasz poleceń, ustawień, dokumentacji czy innych przydatnych rzeczy, nowa funkcja wyszukiwania ułatwia znajdowanie tego, czego szukasz.

Aby uzyskać więcej informacji, zobacz [Używanie Visual Studio wyszukiwania](visual-studio-search.md).

#### <a name="intelligent-search-service"></a>Usługa inteligentnego wyszukiwania

**Nowość w wersjach 16.9:** Korzystając z technologii opartych na chmurze, sztucznej inteligencji i uczenia maszynowego, ulepszyliśmy nasze wyniki wyszukiwania. Teraz nie tylko wyszukiwanie w Visual Studio daje bardziej odpowiednie wyniki, ale może również ułatwić odnajdywanie funkcji produktów.

Aby uzyskać więcej informacji, zobacz wpis w blogu intelligent Visual Studio search service (Usługa [wyszukiwania inteligentnego](https://devblogs.microsoft.com/visualstudio/intelligent-visual-studio-search-service/) wyszukiwania).

### <a name="refactorings"></a>Refaktoryzacje

W języku C# istnieje wiele nowych i bardzo przydatnych refaktoryzacji, które ułatwiają organizowanie kodu. Są one wyświetlane jako sugestie w żarówki i obejmują akcje, takie jak przenoszenie składowych do interfejsu lub klasy bazowej, dostosowywanie przestrzeni nazw w celu dopasowania do struktury folderów, konwertowanie pętli foreach na zapytania Linq i nie tylko.

   ![Animacja obsługi refaktoryzacji w Visual Studio 2019 r.](media/vs-2019/refactorings.gif "Środowisko refaktoryzacji w Visual Studio 2019 r.")

Po prostu wywołaj refaktoryzowanie, naciskając **klawisze Ctrl+.** i wybierając akcję, którą chcesz podjąć.

### <a name="intellicode"></a>IntelliCode

[Visual Studio IntelliCode](/visualstudio/intellicode/) zwiększa nakład pracy nad tworzeniem oprogramowania przy użyciu sztucznej inteligencji. Funkcja IntelliCode szkoli się w 2000 projektach typu open source w usłudze GitHub. Każdy z nich ma ponad 100 gwiazdek w celu &mdash; &mdash; wygenerowania rekomendacji.

![Animacja funkcji IntelliCode w programie Visual Studio 2019](media/vs-2019/IntelliCode.gif "IntelliCode w Visual Studio 2019 r.")

Oto kilka sposobów, dzięki Visual Studio IntelliCode może zwiększyć produktywność:

* Dostarczanie uzupełniania kodu kontekstowego
* Przewodnik dla deweloperów dotyczący przestrzegania wzorców i stylów ich zespołu
* Znajdowanie trudnych do przechwytania problemów z kodem
* Skup się na przeglądach kodu, zwracając uwagę na obszary, które naprawdę mają znaczenie

Początkowo obsługiwano tylko język C# podczas pierwszego wyświetlania podglądu funkcji IntelliCode jako rozszerzenia dla Visual Studio. Teraz, **nowość w 16.1,** dodaliśmy obsługę języków C# i XAML "w opakowaniu". (Obsługa języków C++ i TypeScript/JavaScript jest jednak nadal w wersji zapoznawczej).

A jeśli używasz języka C#, dodaliśmy również możliwość trenowania modelu niestandardowego przy użyciu własnego kodu.

Aby uzyskać więcej informacji na temat funkcji IntelliCode, zobacz [Announcing the general availability of IntelliCode plus a peek](https://devblogs.microsoft.com/visualstudio/announcing-the-general-availability-of-intellicode-plus-a-sneak-peek/) and Code more (Ogłaszanie ogólnej dostępności funkcji IntelliCode oraz zobacz więcej podglądu kodu i kodu), przewiń mniej Visual Studio wpisów w blogu [funkcji IntelliCode.](https://devblogs.microsoft.com/visualstudio/code-more-scroll-less-with-visual-studio-intellicode/)

### <a name="code-cleanup"></a>Oczyszczanie kodu

W połączeniu z nowym wskaźnikiem kondycji dokumentu jest nowe polecenie oczyszczania kodu. To nowe polecenie umożliwia zidentyfikowanie, a następnie naprawienie ostrzeżeń i sugestii za pomocą jednej akcji (lub kliknięcia przycisku).

Oczyszczanie sformatuje kod i zastosuje poprawki kodu [](code-styles-and-code-cleanup.md) zgodnie z sugestią bieżących ustawień i [plików .editorconfig.](create-portable-custom-editor-options.md)

   ![Zrzut ekranu przedstawiający nową kontrolkę oczyszczania kodu w programie Visual Studio 2019](media/vs-2019/code-cleanup-profile.png "Nowa kontrolka oczyszczania kodu w Visual Studio 2019 r.")

Kolekcje poprawek można również zapisać jako profil. Jeśli na przykład masz niewielki zestaw narzędzi naprawiających, które są często stosowane podczas kodu, a następnie masz inny kompleksowy zestaw poprawek do zastosowania przed przeglądem kodu, możesz skonfigurować profile, aby wykonywać te różne zadania.

   ![Zrzut ekranu przedstawiający kontrolkę konfigurowania oczyszczania kodu w programie Visual Studio 2019](media/vs-2019/code-cleanup-profile-configure.png "Kontrolka konfigurowania oczyszczania kodu w programie Visual Studio 2019.")

### <a name="per-monitor-aware-pma-rendering"></a>Renderowanie z informacjami o monitorze (PMA)

Jeśli używasz monitorów skonfigurowanych przy użyciu różnych współczynników skalowania wyświetlania lub łączysz się zdalnie z maszyną z współczynnikami skalowania wyświetlania, które różnią się od głównego urządzenia, możesz zauważyć, że program Visual Studio wygląda rozmyty lub renderuje się w niewłaściwej skali.

Wraz z wydaniem Visual Studio 2019 r. Visual Studio aplikację z informacjami o monitorze (PMA). Teraz Visual Studio są renderowane poprawnie niezależnie od współczynników skalowania wyświetlania.

   ![Renderowanie z monitorem (PMA) w Visual Studio 2019 r.](media/vs-2019/pma-dpi-scaling.png "Renderowanie na monitor (PMA) w Visual Studio 2019 r.")

Aby uzyskać więcej informacji, zobacz wpis w blogu [Better multi-monitor experience with Visual Studio 2019 (Lepsza](https://devblogs.microsoft.com/visualstudio/a-better-multi-monitor-experience-with-visual-studio-2019/) obsługa wielu monitorów w programie Visual Studio 2019).

### <a name="test-explorer"></a>Eksplorator testów

Nowość **w wersji 16.2:** Zaktualizowaliśmy Eksplorator testów, aby zapewnić lepszą obsługę dużych zestawów testów, łatwiejsze filtrowanie, łatwiejsze do odnajdywania polecenia, widoki list odtwarzania z kartami i dostosowywalne kolumny, które umożliwiają dostosowanie wyświetlanych informacji testowych.

   ![Zrzut ekranu przedstawiający ulepszenia interfejsu użytkownika w Eksploratorze testów](media/vs-2019/test-explorer-ui.png "Ulepszenia interfejsu użytkownika w Eksploratorze testów.")

### <a name="net-core"></a>.NET Core

**Nowość w 16.3:** Dodano obsługę platform .NET Core 3.0. Międzyplatformowe, open source &mdash; i w pełni obsługiwane przez firmę Microsoft.

Aby uzyskać więcej informacji, zobacz wpis [w blogu Announcing .NET Core 3.0](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/) (Ogłaszanie pracy z platformą .NET Core 3.0).

## <a name="collaborate"></a>Współpraca

Zapoznaj się z poniższym wideo, aby dowiedzieć się więcej o tym, jak możesz nawiązyć zespół w celu rozwiązania problemów. <br><br>*Długość wideo: 4,22 min*

> [!VIDEO https://www.youtube.com/embed/dKLJsiK1QU8]

### <a name="git-first-workflow"></a>Przepływ pracy po raz pierwszy w usłudze Git

Coś, co zauważysz po otwarciu programu Visual Studio 2019, jest jego nowym oknem startowym.

   ![Zrzut ekranu przedstawiający nowe okno uruchamiania w Visual Studio 2019 r.](media/vs-2019/start-window-dark.png "Nowe okno uruchamiania w Visual Studio 2019 r.")

W oknie uruchamiania jest dostępnych kilka opcji, dzięki których można szybko kodować. Najpierw umieściliśmy opcję sklonowania lub wyewidencjiowania kodu z repo.

   ![Animacja "Git-first" w programie Visual Studio 2019](media/vs-2019/git-first.gif "Środowisko &quot;Git-first&quot; w 2019 Visual Studio 2019 r.")

Okno uruchamiania zawiera również opcje otwierania projektu lub rozwiązania, otwierania folderu lokalnego lub tworzenia nowego projektu.

Aby uzyskać więcej informacji, zobacz wpis w blogu [Get to code: How we designed the new Visual Studio start window](https://devblogs.microsoft.com/visualstudio/get-to-code-how-we-designed-the-new-visual-studio-start-window/) (Uzyskiwanie dostępu do kodu: jak zaprojektowaliśmy nowy Visual Studio w oknie startowym).

### <a name="git-productivity"></a>Produktywność usługi Git

**Nowość w wersji 16.8:** usługa Git jest teraz domyślnym środowiskom kontroli wersji w Visual Studio 2019 r. Wybudowaliśmy zestaw funkcji i iterowaliśmy po nim na podstawie opinii użytkowników z ostatnich dwóch wersji. Nowe środowisko jest teraz domyślnie włączone dla wszystkich użytkowników. Z nowego menu Usługi Git możesz klonować, tworzyć i otwierać repozytoria. Użyj zintegrowanych okien narzędzi Git, aby zatwierdzić i wypchnąć zmiany do kodu, zarządzać gałęziami, być na bieżąco z repozytoriami zdalnymi i rozwiązywać konflikty scalania.

Aby uzyskać więcej informacji, zobacz środowisko [git w Visual Studio](../version-control/git-with-visual-studio.md) strony.

### <a name="live-share"></a>Live Share

[Visual Studio Live Share](https://visualstudio.microsoft.com/services/live-share/) to usługa dewelopera, która umożliwia udostępnianie bazy kodu i jej kontekstu zespołowi oraz uzyskiwanie natychmiastowej dwukierunkowej współpracy bezpośrednio z poziomu Visual Studio. Dzięki Live Share członkowie zespołu mogą odczytywać, nawigować, edytować i debugować projekt, który został im udostępniony, i robić to bezproblemowo i bezpiecznie.

A w Visual Studio 2019 r. ta usługa jest instalowana domyślnie.

![Animacja, która pokazuje Live Share współpracy w Visual Studio 2019 r.](media/vs-2019/live-share.gif "Funkcja Live Share współpracy w Visual Studio 2019 r.")

Aby uzyskać więcej [](https://devblogs.microsoft.com/visualstudio/visual-studio-live-share-for-real-time-code-reviews-and-interactive-education/) informacji, zobacz Visual Studio Live Share na temat przeglądów kodu w czasie rzeczywistym i interaktywnego wpisu w blogu dla edukacji oraz Live Share wpis w blogu Visual Studio [2019.](https://devblogs.microsoft.com/visualstudio/live-share-now-included-with-visual-studio-2019/)

### <a name="integrated-code-reviews"></a>Przeglądy zintegrowanego kodu

Wprowadzamy nowe rozszerzenie, które można pobrać z programem Visual Studio 2019. To nowe rozszerzenie umożliwia przeglądanie, uruchamianie, a nawet debugowanie żądań ściągnęć od zespołu bez opuszczania Visual Studio. Obsługujemy kod zarówno w repozytoriach GitHub, jak Azure DevOps repozytoriach.

   ![Zrzut ekranu przedstawiający nowe rozszerzenie Żądania ściągnięć w programie Visual Studio 2019](media/vs-2019/pr-experience.png "Nowe rozszerzenie Żądania ściągnięć w Visual Studio 2019 r.")

Aby uzyskać więcej informacji, zobacz wpis w blogu [Code reviews using the Visual Studio Pull Requests extension (Przeglądy](https://devblogs.microsoft.com/visualstudio/code-reviews-using-the-visual-studio-pull-requests-extension/) kodu przy użyciu rozszerzenia żądania ściągnięć).

## <a name="debug"></a>Debugowanie

Zapoznaj się z poniższym wideo, aby dowiedzieć się więcej o tym, jak można zerować przy użyciu precyzyjnego określania wartości docelowej podczas debugowania. <br><br>*Długość wideo: 3,54 min*

> [!VIDEO https://www.youtube.com/embed/hr72Fs8n_9c]

### <a name="performance-gains"></a>Wzrost wydajności

Zrobiliśmy tylko raz punkty przerwania danych języka C++ i dostosowaliśmy je do aplikacji .NET Core.

   ![Animacja, która pokazuje punkty przerwania danych debugowania w Visual Studio 2019 r.](media/vs-2019/debug-data-breakpoints.gif "Punkty przerwania danych debugowania w Visual Studio 2019 r.")

Niezależnie od tego, czy kodowanie jest w języku C++ czy .NET Core, punkty przerwania danych mogą być dobrą alternatywą dla umieszczania zwykłych punktów przerwania. Punkty przerwania danych są również doskonałe w scenariuszach takich jak znajdowanie miejsca, w którym obiekt globalny jest modyfikowany lub dodawany bądź usuwany z listy.

Jeśli jesteś deweloperem języka C++, który opracowuje duże aplikacje, w programie Visual Studio 2019 zostały wprowadzone symbole poza programem , co umożliwia debugowanie tych aplikacji bez problemów związanych z pamięcią.

### <a name="search-while-debugging"></a>Wyszukiwanie podczas debugowania

Prawdopodobnie jesteś tam wcześniej, szukając w okno wyrażeń kontrolnych ciągu spośród zestawu wartości. W Visual Studio 2019 r. dodaliśmy wyszukiwanie w oknach Czujka, Ustawienia lokalne i Automatyczne, aby ułatwić znajdowanie szukanych obiektów i wartości.

   ![Animacja, która pokazuje okno wyszukiwania debugowania w Visual Studio 2019 r.](media/vs-2019/debug-window-search.gif "Okno wyszukiwania debugowania w Visual Studio 2019 r.")

Możesz również sformatować sposób wyświetlania wartości w oknach Czujka, Ustawienia lokalne i Automatyczne. Wybierz (przez dwukrotne kliknięcie) jeden z elementów w dowolnym z okien i dodaj przecinek (","), aby uzyskać dostęp do listy rozwijanej możliwych specyfikatorów formatu, z których każdy zawiera opis zamierzonego efektu.

   ![Nowa funkcja okno wyrażeń kontrolnych i formatowania w programie Visual Studio 2019](media/search-watch-window.png "Nowa funkcja okno wyrażeń kontrolnych formatowania w programie Visual Studio 2019.")

Aby uzyskać więcej informacji, zobacz wpis w blogu [Enhanced in Visual Studio 2019: Search for Objects and Properties](https://devblogs.microsoft.com/visualstudio/enhanced-in-visual-studio-2019-search-for-objects-and-properties-in-the-watch-autos-and-locals-windows/) (Rozszerzone w wersji 2019: wyszukiwanie obiektów i właściwości) we wpisie w blogu Watch, Autos, and Locals Windows (Czujka, automatyczne i lokalne) w systemie Windows.

### <a name="snapshot-debugger"></a>Debuger migawek

Pobierz migawkę wykonania aplikacji w chmurze, aby zobaczyć dokładnie, co się dzieje. (Ta funkcja jest dostępna tylko Visual Studio Enterprise).

   ![Animacja, która pokazuje Snapshot Debugger w programie Visual Studio 2019 Enterprise](media/vs-2019/snapshot-debugger.gif "Ten Snapshot Debugger w Visual Studio 2019 Enterprise.")

Dodaliśmy obsługę określania wartości docelowych dla ASP.NET (podstawowych i klasycznych) uruchamianych na maszynie wirtualnej platformy Azure. Ponadto dodaliśmy obsługę aplikacji uruchamianych w Azure Kubernetes Service. Ten Snapshot Debugger znacznie skrócić czas rozwiązywania problemów, które występują w środowiskach produkcyjnych.

Aby uzyskać więcej informacji, zobacz debugowanie aplikacji platformy Azure ASP.NET na żywo przy użyciu strony [Snapshot Debugger](../debugger/debug-live-azure-applications.md) oraz wpis w blogu Introducing Time Travel Debugging for Visual Studio Enterprise 2019 (Wprowadzenie do debugowania podróży w czasie dla platformy [Visual Studio Enterprise 2019).](https://devblogs.microsoft.com/visualstudio/introducing-time-travel-debugging-for-visual-studio-enterprise-2019/)

### <a name="microsoft-edge-insider-support"></a>Pomoc techniczna programu Microsoft Edge dla niejawnych testerów

**Nowość w wersji 16.2:** możesz ustawić punkt przerwania w aplikacji JavaScript i rozpocząć sesję debugowania przy użyciu przeglądarki [Microsoft Edge Insider.](https://www.microsoftedgeinsider.com/) Gdy to zrobisz, Visual Studio zostanie otwarte nowe okno przeglądarki z włączonym debugowaniem, za pomocą którego można przechodzić przez kod JavaScript aplikacji w Visual Studio.

   ![Zrzut ekranu przedstawiający renderowanie kodu JavaScript w przeglądarce](media/vs-2019/edge-chromium-breakpoint.png "Renderowanie kodu JavaScript w przeglądarce.")

### <a name="pinnable-properties-tool"></a>Narzędzie Właściwości przypinalne

**Nowość w 16.4:** teraz łatwiej jest identyfikować obiekty według ich właściwości podczas debugowania za pomocą nowego narzędzia Właściwości możliwe do przypinania. Po prostu umieść kursor na właściwości, która ma być wyświetlana w oknie debugera okien Czujka, Automatyczne i Lokalne, wybierz ikonę pinezki i natychmiast wyświetl informacje, których szukasz w górnej części okna.

   ![Animacja, która pokazuje, jak przypinać właściwości w debugerze Visual Studio przy użyciu narzędzia Pinnable Properties](media/vs-2019/debugger-pinnable-properties.gif "Przypinanie właściwości Visual Studio debugerze przy użyciu narzędzia Pinnable Properties.")

Aby uzyskać więcej informacji, zobacz wpis w blogu [Pinnable Properties: Debug & Display Managed Objects YOUR Way (Właściwości przypinalne:](https://devblogs.microsoft.com/visualstudio/pinnable-properties-debug-display-managed-objects-your-way/) debugowanie i wyświetlanie obiektów zarządzanych).

## <a name="whats-next"></a>Co dalej

Często aktualizujemy Visual Studio 2019 r. o nowe funkcje, które mogą sprawić, że środowisko programowe będzie jeszcze lepsze. Aby dowiedzieć się więcej o naszych najnowszych innowacjach, zobacz [blog Visual Studio bloga](https://devblogs.microsoft.com/visualstudio/). Aby uzyskać informacje o tym, co do tej pory wydaliśmy w wersji [zapoznawczej,](/visualstudio/releases/2019/release-notes-preview/)zobacz Informacje o wersji zapoznawczej . Aby uzyskać listę informacji o tym, co planujemy w następnej wersji, zobacz plan rozwoju Visual Studio [mapy.](/visualstudio/productinfo/vs-roadmap)

W międzyczasie jest dostępna nowa funkcja, która jest obecnie w trakcie prac.

- **Ulepszone środowisko git w wersji Visual Studio 2019 (wersja zapoznawcza)**

   Mimo że nowe środowisko kontroli wersji usługi Git jest teraz domyślnie włączone w wersji [16.8](/visualstudio/releases/2019/release-notes/)programu Visual Studio 2019, nadal dodajemy funkcje, aby ulepszyć środowisko w najnowszej wersji zapoznawczej.

   Aby uzyskać więcej informacji, zobacz [stronę Kontrola wersji Visual Studio](/visualstudio/version-control/) stronie.

Aby uzyskać więcej informacji na temat wersji zapoznawczej programu Visual Studio 2019 i link do pobierania, jeśli chcesz go wypróbować, zobacz stronę Visual Studio Preview &mdash; &mdash; pobierania. **[](https://aka.ms/vspreview/)**

> [!TIP]
> Aby dowiedzieć się więcej o następnej wersji, **[zobacz wpis w blogu Visual Studio 2022.](https://devblogs.microsoft.com/visualstudio/visual-studio-2022/)**

## <a name="give-us-feedback"></a>Wyślij do nas swoją opinię

Dlaczego warto wysyłać opinie do Visual Studio zespołu? Ponieważ opinie klientów są bardzo poważne. Jest to ważne w dużej części tego, co robimy.

* Jeśli chcesz zasugerować, jak możemy ulepszyć Visual Studio, możesz to zrobić za pomocą narzędzia Zaproponuj [funkcję.](suggest-a-feature.md)

* Jeśli wystąpi problem, Visual Studio przestaje odpowiadać, ulega awarii lub występuje inny problem z wydajnością, możesz łatwo udostępnić nam kroki dotyczące odnów i pliki obsługi za pomocą narzędzia Zgłoś [problem.](how-to-report-a-problem-with-visual-studio.md)

## <a name="see-also"></a>Zobacz też

* [Co nowego w Visual Studio dokumentów](whats-new-visual-studio-docs.md)
* [Visual Studio wersji 2019](/visualstudio/releases/2019/release-notes/)
* [Visual Studio 2019 dla komputerów Mac — informacje o wersji](/visualstudio/releasenotes/vs2019-mac-relnotes/)
* [Co nowego w zestawie SDK Visual Studio 2019](../extensibility/whats-new-visual-studio-2019-sdk.md)
* [Co nowego w języku C++ w programie Visual Studio](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio/)
* [Co nowego w języku C# 9.0](/dotnet/csharp/whats-new/csharp-9)
* [Co nowego w wersji .NET 5](/dotnet/core/dotnet-five)
* [Co nowego w programie .NET Framework](/dotnet/framework/whats-new/)
* [Konferencja Microsoft Build](https://www.microsoft.com/build)
* [Konferencja Microsoft Ignite](https://www.microsoft.com/ignite)

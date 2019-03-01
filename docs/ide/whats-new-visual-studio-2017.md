---
title: Co nowego w programie Visual Studio 2017
titleSuffix: ''
description: Dowiedz się więcej o nowych funkcjach w programie Visual Studio 2017.
ms.date: 12/18/2018
f1_keywords:
- VS.StartPage.WhatsNew
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 7307e180-ba28-4774-8a43-cbb980085a71
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 2af264ec8cf44f435f640a81a61dbd4cdbd84bd3
ms.sourcegitcommit: 87d7123c09812534b7b08743de4d11d6433eaa13
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57223315"
---
# <a name="whats-new-in-visual-studio-2017"></a>Co nowego w programie Visual Studio 2017

**Zaktualizowano do programu [wersji 15.9](/visualstudio/releasenotes/vs2017-relnotes?context=visualstudio/default&contextView=vs-2017)**

Chcesz uaktualnienie z poprzedniej wersji programu Visual Studio? Oto, co program Visual Studio 2017 można umożliwiają: Niezrównana wydajność dla każdego programisty, każdej aplikacji i dowolnej platformy. Visual Studio 2017 umożliwia tworzenie aplikacji dla systemów Android, iOS, Windows, Linux, sieci web i chmury. Szybko twórz kod, z łatwością debuguj i diagnozuj, często testuj i swobodnie wydawaj. Możesz również rozszerzać funkcjonalność programu Visual Studio oraz go dostosowywać, tworząc własne rozszerzenia. Korzystanie z kontroli wersji, elastyczność i Współpracuj efektywnie dzięki tej wersji!

>[!div class="button"]
>[Pobierz program Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

Poniżej przedstawiono podsumowanie wysokiego poziomu zmiany wprowadzone od poprzedniej wersji programu Visual Studio 2015:

* **[Nowe spojrzenie podstawy](#redefined-fundamentals)**. Nowe środowisko instalacji oznacza, że można zainstalować szybciej i zainstalować ma gdy jej potrzebujesz.
* **[Wydajność i produktywność](#performance-and-productivity)**. Koncentrowaliśmy się na nowe i nowoczesne mobilnych, chmury i możliwości tworzenia aplikacji klasycznych. Ponadto program Visual Studio rozpoczyna się szybciej, jest bardziej elastyczny i zużywa mniej pamięci niż wcześniej.
* **[Tworzenie aplikacji za pomocą platformy Azure w chmurze](#cloud-app-development-with-azure)**. Wbudowany zestaw narzędzi platformy Azure umożliwiają łatwe tworzenie aplikacji chmurze obsługiwane przez Microsoft Azure. Program Visual Studio ułatwia konfigurowanie, tworzenie, debugowanie, pakowanie i wdrażanie aplikacji i usług na platformie Azure.
* **[Tworzenie aplikacji Windows](#windows-app-development)**. Użyj szablonów platformy uniwersalnej systemu Windows w programie Visual Studio 2017 do utworzenia pojedynczego projektu dla wszystkich urządzeń z systemem Windows 10 &ndash; komputer, tablet, telefon, Xbox, HoloLens, Surface Hub i więcej.
* **[Tworzenie aplikacji mobilnych](#mobile-app-development)**. Wprowadzaj innowacje i uzyskuj wyniki szybciej za pomocą platformy Xamarin, która łączy wymagań dla wielu platform mobilnych do jednego rdzenia kodu i zestawu umiejętności.
* **[Programowanie dla wielu platform](#cross-platform-development)**. Bezproblemowo dostarczać oprogramowanie na każdą platformę docelową. Rozszerz procesy DevOps do programu SQL Server za pomocą narzędzia danych Redgate i bezpiecznie Automatyzuj wdrożenia baz danych z programu Visual Studio. Możesz też użyć platformy .NET Core do pisania aplikacji i bibliotek, które uruchomienie niemodyfikowanego między systemami operacyjnymi z systemem macOS, Linux i Windows.
* **[Programowanie gier](#games-development)**. Program Visual Studio Tools for Unity (VSTU) można użyć programu Visual Studio tworzyć gry i Edytor skrypty w języku C#, a następnie użyć jej zaawansowany debuger, można znaleźć i naprawić błędy.
* **[Opracowywania sztucznej Inteligencji](#ai-development)**. Za pomocą programu Visual Studio Tools for AI można użyć z funkcji produktywności programu Visual Studio, aby przyspieszyć wprowadzanie innowacji sztucznej Inteligencji. Twórz, Testuj i wdrażaj uczenia głębokiego / rozwiązań sztucznej Inteligencji, bezproblemowo zintegrować z usługą Azure Machine Learning eksperymentowania niezawodne możliwości.

> [!NOTE]
> Aby uzyskać pełną listę nowych funkcji i funkcjonalności w programie Visual Studio 2017, zobacz [bieżące informacje o wersji](/visualstudio/releasenotes/vs2017-relnotes?context=visualstudio/default&contextView=vs-2017). Oraz uzyskać wgląd w oferty z nowymi funkcjami, zobacz [informacje o wersji zapoznawczej](/visualstudio/releasenotes/vs2017-preview-relnotes?context=visualstudio/default&contextView=vs-2017).

Oto bardziej szczegółowe informacje o niektórych najbardziej istotnych ulepszeń i nowych funkcji w programie Visual Studio 2017.

## <a name="redefined-fundamentals"></a>Udoskonalone podstawy

### <a name="a-new-setup-experience"></a>Nowe środowisko instalacji

Program Visual Studio sprawia, że łatwiej i szybciej, aby zainstalować tylko funkcje, których potrzebujesz, gdy ich potrzebujesz. Ponadto on także czyste odinstalowanie, zbyt.

Najważniejsze zmiany, należy pamiętać podczas instalowania programu Visual Studio jest jego nowe środowisko instalacji. Na **obciążeń** kartę, zostaną wyświetlone opcje instalacji, które są grupowane, aby przedstawić typowe struktury, języki i platformy. Obejmuje on wszystko — od tworzenia aplikacji klasycznych .NET do tworzenia aplikacji języka C++ w Windows, Linux i z systemem iOS.

Wybierz obciążeń zapotrzebowania, a jeśli musisz je zmienić.

 ![Okno dialogowe Ustawienia programu Visual Studio 2017](../install/media/install-visual-studio-enterprise.png)

I inne opcje, aby precyzyjnie dostosować instalację, za:

* Czy chcesz wybrać składniki zamiast przy użyciu obciążeń? Wybierz **poszczególne składniki** kartę z poziomu Instalatora.
* Chcesz zainstalować pakiety językowe, bez konieczności zmiany opcji języka Windows? Wybierz **pakiety językowe** kartę Instalatora.
* **Nowość w wersji 15.7**: Czy chcesz zmienić lokalizację, w którym program Visual Studio instaluje? Wybierz **opcje instalacji** kartę Instalatora.

Aby dowiedzieć się więcej o nowe środowisko instalacji, w tym instrukcje krok po kroku, które przeprowadzą Cię przez, zobacz [Zainstaluj program Visual Studio](../install/install-visual-studio.md) strony.

### <a name="a-focus-on-accessibility"></a>Fokus w ułatwienia dostępu

**Nowość w 15.3**, wprowadziliśmy za pośrednictwem 1700 poprawki docelowych Aby zwiększyć zgodność między Visual Studio i technologiami pomocniczymi, korzystających z wielu klientów. Istnieją dziesiątek scenariusze, które są bardziej zgodne z czytników ekranu, wysokiego kontrastu, motywów i innych technologiami pomocniczymi niż kiedykolwiek wcześniej. Debugera, edytora i powłoki ma zbyt wszystkich gotten znaczne ulepszenia.

Aby uzyskać więcej informacji, zobacz [ulepszenia ułatwień dostępu w programie Visual Studio 2017 w wersji 15.3](https://devblogs.microsoft.com/visualstudio/accessibility-improvements-in-visual-studio-2017-version-15-3/) wpis w blogu.

## <a name="performance-and-productivity"></a>Wydajność i produktywność

### <a name="sign-in-across-multiple-accounts"></a>Zaloguj się na wielu kontach

Wprowadziliśmy nową usługę tożsamości w programie Visual Studio, która umożliwia udostępnianie kont użytkowników w Team Explorer, narzędzia platformy Azure, publikowanie Microsoft Store i.

Użytkownik może nie wylogowuj dłużej zbyt. Program Visual Studio nie będzie poprosić Zaloguj się ponownie na 12 godzin. Aby dowiedzieć się więcej, zobacz [logowania mniej programu Visual Studio wyświetla monit o](https://devblogs.microsoft.com/visualstudio/fewer-visual-studio-sign-in-prompts/) wpis w blogu.

### <a name="start-visual-studio-faster"></a>Szybsze uruchamianie programu Visual Studio

Nowe Centrum wydajności programu Visual Studio może pomóc w lepszego wykorzystania czasu uruchamiania środowiska IDE. Centrum wydajności Wyświetla listę wszystkich rozszerzeń i okna narzędzi, które może spowolnić uruchamiania środowiska IDE. Służy on do zwiększeniu wydajności uruchamiania, ustalając, podczas uruchamiania rozszerzenia, lub czy okien są otwarte przy uruchamianiu.

### <a name="faster-on-demand-loading-of-extensions"></a>Szybsze ładowanie na żądanie rozszerzenia

Program Visual Studio jest przeniesienie jego rozszerzenia (i Praca z rozszerzeniami innych firm za) tak, aby ich ładowania na żądanie, a nie podczas uruchamiania środowiska IDE. Wiedzieć o tym, jakie rozszerzenia mieć wpływ na uruchamianie, ładowanie rozwiązania i wpisując wydajności? Możesz zobaczyć te informacje w **pomocy** > **zarządzanie wydajnością programu Visual Studio**.

  ![Okno dialogowe Opcje w programie Visual Studio 2017](media/vs2017ide-manage-vs-perf.png)

#### <a name="manage-your-extensions-with-roaming-extensions-manager"></a>Zarządzanie za pomocą przystawki Menedżer rozszerzenia roamingu rozszerzeń

Jest to łatwiejsze do skonfigurowania każdego środowiska programowania przy użyciu ulubionych rozszerzeń po zalogowaniu się do programu Visual Studio. Nowy Menedżer rozszerzenia roamingu przechowuje informacje o wszystkie ulubione rozszerzenia przez utworzenie zsynchronizowanej listy w chmurze.

Aby wyświetlić listę rozszerzeń w programie Visual Studio, kliknij przycisk **narzędzia** > **rozszerzenia i aktualizacje**, a następnie kliknij przycisk **Menedżer roamingu rozszerzeń**.

![Visual Studio 2017 — okno dialogowe rozszerzenia i aktualizacje](media/vs2017ide-extensions-and-updates.png)

Menedżer roamingu rozszerzeń śledzi wszystkie rozszerzenia, które należy zainstalować, ale można wybrać te, które chcesz dodać do listy roamingu.

![Visual Studio 2017 — okno dialogowe rozszerzenia i aktualizacje](media/vs2017ide-RoamingExtensionManager.png)

Gdy używasz Menedżer roamingu rozszerzeń, istnieją trzy typy ikon na liście:

* ![Ikony rozszerzeń korzystających z roamingu](media/vs2017ide-roamedicon.png)  **_rozszerzeń korzystających z roamingu_**: Rozszerzenie jest częścią tej listy roamingu, ale nie została zainstalowana na tym komputerze.
  (Można zainstalować je przy użyciu **Pobierz** przycisku.)
* ![Ikony rozszerzeń korzystających z roamingu i zainstalowanych](media/vs2017ide-roamedinstalledicon.png)  **_korzystania z roamingu i zainstalowane_**: Wszystkie rozszerzenia, które są częścią tej listy roamingu i zainstalowane w środowisku deweloperskim.
  (Jeśli zdecydujesz się zrezygnować z roamingu, możesz usunąć te elementy przy użyciu **Zatrzymaj Roaming** przycisku.)
* ![Ikona zainstalowane](media/vs2017ide-installedicon.png)  **_zainstalowane_**: Wszystkie rozszerzenia, które są zainstalowane w tym środowisku, ale nie są częścią listy roamingu.
  (Rozszerzenia można dodać do listy roamingu, używając **Rozpocznij Roaming** przycisku.)

Rozszerzenia, które możesz pobrać, gdy użytkownik jest zalogowany, zostanie dodany do listy jako **korzystania z roamingu i zainstalowane**. Rozszerzenie staje się częścią listy roamingu, który umożliwia dostęp do nich z dowolnego komputera.

### <a name="experience-live-unit-testing"></a>Środowisko testów jednostkowych na żywo

W programie Visual Studio Enterprise 2017 funkcji live unit testing zapewnia możesz na żywo wyniki testów jednostek i pokrycie kodu w edytorze podczas kodowania. Działa z projektami w języku C# i Visual Basic .NET Framework i .NET Core i obsługuje trzy platformy testowe MSTest, xUnit i NUnit.

![Live Unit Testing](media/lut-codewindow.png)

Aby uzyskać więcej informacji, zobacz [Przedstawiamy Live Unit Testing](../test/live-unit-testing-intro.md). Aby uzyskać listę nowych funkcji dodanych w każdej wersji programu Visual Studio Enterprise 2017, zobacz [What's new in Live Unit Testing](../test/live-unit-testing-whats-new.md).

### <a name="set-up-a-cicd-pipeline"></a>Skonfiguruj potok ciągłej integracji/ciągłego wdrażania

#### <a name="automated-testing"></a>Testowanie automatyczne

Testowanie automatyczne jest kluczową rolę w dowolnym potoku metodyki DevOps. Go umożliwia spójne i niezawodne testowania i wydawania swoje rozwiązanie na znacznie krótsze cykle. Przepływy ciągłej integracji/ciągłego wdrażania (ciągłej integracji i ciągłego dostarczania), mogą pomóc proces bardziej wydajne.

Aby uzyskać więcej informacji na temat testów automatycznych, zobacz [potoku CI/CD dla testów automatycznych w infrastrukturze DevOps](https://blogs.msdn.microsoft.com/visualstudioalmrangers/2017/04/20/set-up-a-cicd-pipeline-to-run-automated-tests-efficiently/) wpis w blogu.

A, aby uzyskać więcej informacji na temat nowości w [narzędzi Continuous delivery tools for Visual Studio](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) rozszerzenia DevLabs zobacz [zatwierdzenia z pewnością: Zatwierdź jakość kodu w czasie](https://devblogs.microsoft.com/visualstudio/committing-with-confidence-commit-time-code-quality-information-updated/) wpis w blogu.

### <a name="visual-studio-ide-enhancements"></a>Ulepszenia usługi Visual Studio IDE

#### <a name="multi-caret-editing"></a>Edytowanie wielu karetki

**Nowość w 15.8**: Edytowanie jednocześnie wiele lokalizacji w pliku, jest obecnie łatwy. Rozpocznij od utworzenia punkty wstawienia i zaznaczenia w wielu lokalizacjach w pliku. Następnie funkcja wielu karetki edycji, aby dokonać edycji tych samych w dwóch lub więcej miejsc, w tym samym czasie.

Aby uzyskać więcej informacji, zobacz [zaznaczenie wielu karetki](finding-and-replacing-text.md#multi-caret-selection) części z [Znajdowanie i zastępowanie tekstu](finding-and-replacing-text.md) strony.

#### <a name="keep-keybinding-profiles-consistent"></a>Utrzymuj spójność profile powiązanie klawiszy

**Nowość w 15.8**: Teraz możesz zachować swoje powiązania klawiszy spójne w narzędziach przy użyciu dwóch nowych profilów klawiatury: Visual Studio Code and ReSharper (Visual Studio). Można znaleźć tych systemów, w ramach **narzędzia** > **opcje** > **ogólne** > **klawiatury**i górnego menu rozwijanego.

  ![Nowe profile powiązanie klawiszy dla programu Visual Studio Code i ReSharper](media/vs-keyboard-mappings-code-resharper.png)

#### <a name="use-new-refactorings"></a>Użyj nowych refaktoryzacji

Refaktoryzacja to proces po został zapisany w celu ulepszania kodu. Refaktoryzacja zmiany wewnętrznej struktury kodu bez zmiany jego zachowania. Dodajemy nowe refaktoryzacje często; Poniżej przedstawiono kilka:

* Dodaj parametr (od miejsca wywołania)
* Generowanie zastąpienia
* Dodaj argument nazwany
* Dodaj sprawdzanie wartości null dla parametrów
* Wstawianie separatory cyfr literałów
* Podstawa zmiany w literałach numerycznych (na przykład szesnastkowy do pliku binarnego)
* Konwertuj if — przełącznik
* Usuń nieużywaną zmienną

Aby uzyskać więcej informacji, zobacz [szybkie akcje](common-quick-actions.md).

#### <a name="interact-with-git"></a>Wchodzić w interakcje przy użyciu narzędzia Git

Podczas pracy z projektem w programie Visual Studio można skonfigurować i szybko zatwierdzenia i opublikować swój kod do usługi Git. Można również zarządzać repozytoriami Git za pomocą menu kliknięcia przycisku w prawym dolnym rogu IDE.

![Program Visual Studio 2017 wchodzi w interakcję z okna dialogowego narzędzia Git](media/vsIDE-GitInteraction.png)

#### <a name="experience-improved-navigation-controls"></a>Ulepszona nawigacja kontroli środowiska

Firma Microsoft została odświeżona środowisko nawigacji, aby pomóc Ci rozpocząć od A do B z większą pewnością i przeszkadzał.

* **Nowość w wersji 15.4**: **Przejdź do definicji** (**Ctrl**+**kliknij** lub **F12**) &ndash; myszy użytkownicy mają łatwiejszy sposób, aby przejść do definicji element członkowski, naciskając klawisz **Ctrl** a następnie klikając pozycję elementu członkowskiego. Naciśnięcie klawisza **Ctrl** i przenosząc kursor myszy nad symbol kodu będzie underline go i przekształcać je w łącze. Zobacz [przejdź do definicji i zobacz definicję](go-to-and-peek-definition.md) Aby uzyskać więcej informacji.

* **Przejdź do implementacji** (**Ctrl**+**F12**) &ndash; przejdź z dowolnego typu podstawowego lub elementu członkowskiego do jego różne implementacje.

* **Przejdź do wszystkich** (**Ctrl**+**T** lub **Ctrl**+**,**) &ndash; przejdź bezpośrednio do żadnych deklaracji w pliku/typu/elementu członkowskiego/symbolu. Można filtrować listę wyników lub użyj składni zapytania (na przykład, "f searchTerm" dla plików.), "t searchTerm" dla typów itp.

  ![Ulepszone przechodzenia do wszystkich](media/vs2017ide-navigation-go-to.png)

* **Znajdź wszystkie odwołania** (**Shift**+**F12**) &ndash; za pomocą kolorowania składni, przy użyciu kombinacji projektu, definicji, można grupować wyniki Znajdź wszystkie odwołania i ścieżkę. Można również "zablokować" wyniki, aby móc znaleźć inne odniesienia bez utraty oryginalne wyniki.

  ![Nowe narzędzie do znajdowania wszystkich odwołań](media/vs2017ide-find-all-references.png)

* **Wizualizator struktury** &ndash; kropkowana, szary pionowych linii (prowadnice wcięcia) działają jako charakterystycznych elementów krajobrazu w kodzie, aby zapewnić kontekst w ramce, widoku. Może je rozpoznać z popularnych Productivity Power Tools. Umożliwia ich wizualizację i sprawdzenie bloku kodu znajdujesz się w dowolnym momencie bez konieczności przewijania. Kursor wiersze wyświetla etykietkę narzędzia, która pokazuje otwierania tego bloku i jego elementów nadrzędnych. Jest ona dostępna dla wszystkich języków, które są obsługiwane za pośrednictwem gramatyki TextMate, tak jak C#, Visual Basic i XAML.

  ![Wizualizator struktury w usłudze Visual Studio 2017](media/vsIDE-StructureVisualizer.png)

Aby uzyskać więcej informacji na temat nowych funkcji, zobacz [produktywność w programie Visual Studio 2017](https://devblogs.microsoft.com/visualstudio/productivity-in-visual-studio-2017-rc/) wpis w blogu przez Wilson Thomas znacznika.

### <a name="visual-c"></a>Visual C++

Zobaczysz kilka ulepszeń w programie Visual Studio, takich jak dystrybucja podstawowych wytycznych dotyczących języka C++ z programem Visual Studio, aktualizowanie kompilator, dodając ulepszoną obsługę języka C ++ 11 i funkcje C++ i dodawanie i aktualizowanie funkcji w bibliotekach C++. Udoskonaliliśmy także wydajność środowisko IDE języka C++, obciążenia instalacji i nie tylko.

Także już firma Microsoft usunęła ponad 250 usterek i zgłoszonych problemów w kompilatorze i narzędziach, wiele przesłanych przez klientów za pośrednictwem [społeczności deweloperów dla języka C++](https://developercommunity.visualstudio.com/spaces/62/index.html "społeczności deweloperów dla języka C++").

Aby uzyskać szczegółowe informacje, zobacz [co nowego w języku Visual C++ w Visual 2017](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio) strony.

### <a name="debugging-and-diagnostics"></a>Debugowanie i Diagnostyka

#### <a name="run-to-click"></a>Uruchom do kliknięcia

Teraz możesz łatwo przejść od razu podczas debugowania, bez konieczności ustawiania punkt przerwania, aby zatrzymać w wierszu, który ma. Po zatrzymaniu debugera po prostu kliknij ikonę, która pojawia się obok wiersza kodu. Kod będzie Uruchom i Zatrzymaj w danym wierszu przy następnym zostanie osiągnięty w ścieżce kodu.

![Visual Studio 2017 debug - Run To Click](media/vs2017ide-RunToClick.png)

#### <a name="the-new-exception-helper"></a>Nowy Pomocnik wyjątków

Nowy Pomocnik wyjątków pomaga przeglądać swoje wyjątek informacji w skrócie. Informacje są prezentowane w postaci compact zapewnia błyskawiczny dostęp do wyjątków wewnętrznych. Po zdiagnozowaniu obiektu NullReferenceException można szybko wyświetlić, jakie było prawo null w Pomocniku wyjątków.

![Okno dialogowe nowego pomocnika wyjątków w programie Visual Studio](media/vs2017ide-ExceptionHelper.png)

Aby uzyskać więcej informacji, zobacz [Użyj nowego pomocnika wyjątków w programie Visual Studio](https://devblogs.microsoft.com/devops/using-the-new-exception-helper-in-visual-studio-15-preview/) wpis w blogu.

#### <a name="snapshots-and-intellitrace-step-back"></a>Migawki i IntelliTrace krok do tyłu

**Nowość w wersji 15.5**: Krok do tyłu IntelliTrace umożliwia automatyczne utworzenie migawki aplikacji na każdym punkcie przerwania i debuger krok zdarzenia. Zarejestrowane migawek umożliwiają wrócić do poprzednich punktów przerwania lub kroków i wyświetlić stan aplikacji, tak jak w przeszłości. IntelliTrace krok do tyłu pozwalają zaoszczędzić czas podczas mają być wyświetlane poprzedni stan aplikacji, ale nie chcesz ponownie uruchomić debugowanie lub Utwórz ponownie stan żądaną aplikację.

Można poruszać się i Wyświetl migawki za pomocą **krok do tyłu** i **krok do przodu** przycisków w **debugowania** paska narzędzi. Te przyciski nawigacji zdarzenia, które pojawiają się w **zdarzenia** karcie **narzędzia diagnostyczne** okna. Przechodzenie krok po kroku do tyłu lub do przodu do zdarzenia automatycznie aktywuje debugowania historycznego wybranego zdarzenia.

![Okno dialogowe nowego pomocnika wyjątków w programie Visual Studio](../debugger/media/intellitrace-step-back-icons-description.png  "przyciski krok do tyłu i do przodu")

Aby uzyskać więcej informacji, zobacz [wyświetlanie migawki za pomocą funkcji IntelliTrace krok do tyłu](../debugger/view-historical-application-state.md) strony.

### <a name="containerization"></a>Konteneryzacji

Kontenery umożliwiają gęstość aplikacji i niższy koszt wdrożenia oraz poprawę wydajności i elastyczności infrastruktury DevOps.

#### <a name="docker-container-tooling"></a>Narzędzia kontenerów docker

**Nowość w wersji 15.5**:

* Visual Studio zawiera narzędzia dla kontenerów Docker, które obsługują teraz wieloetapowe pliki Dockerfile, który Usprawnij tworzenie zoptymalizowanych obrazów kontenera.
* Domyślnie program Visual Studio będzie automatycznie ściągać, kompilować i uruchamiać niezbędne obrazy kontenera w tle podczas otwierania projektu obsługującego platformę Docker. Tę opcję można wyłączyć za pomocą ustawienia **Automatycznie uruchom kontenery w tle** w programie Visual Studio.

## <a name="cloud-app-development-with-azure"></a>Tworzenie aplikacji w chmurze dzięki platformie Azure

### <a name="azure-functions-tools"></a>Narzędzia usługi Azure Functions

Jako część obciążenia "Programowanie na platformie Azure" uwzględniliśmy narzędzia ułatwiające tworzenie funkcji platformy Azure przy użyciu wstępnie skompilowanych bibliotek klas języka C#. Możesz teraz utworzyć, uruchamianie, debugowanie na lokalnej maszynie do programowania i następnie opublikować bezpośrednio na platformie Azure z programu Visual Studio.

Aby uzyskać więcej informacji, zobacz [narzędzia usługi Azure Functions dla programu Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-develop-vs) strony.

### <a name="debug-live-aspnet-apps-using-snappoints-and-logpoints-in-live-azure-applications"></a>Debugowanie na żywo aplikacji ASP.NET przy użyciu punkty przyciągania i punkty rejestrowania w aplikacjach platformy Azure na żywo

**Nowość w wersji 15.5**: Rozszerzenie Snapshot Debugger tworzy migawkę aplikacji w środowisku produkcyjnym, gdy wykonuje kod, który Cię interesuje. Aby nakazać debugera, aby utworzyć migawkę, należy ustawić punkty przyciągania i punkty rejestrowania w kodzie. Debuger pozwala zobaczyć dokładnie tego, co poszło, bez wywierania wpływu na ruch z aplikacji produkcyjnej. Rozszerzenie Snapshot Debugger może pomóc w znacznie skrócić czas potrzebny do rozwiązywania problemów występujących w środowiskach produkcyjnych.

Zbieranie migawek jest dostępna dla następujących aplikacji sieci web działające w usłudze Azure App Service:

* Aplikacji ASP.NET uruchomionych w programie .NET Framework 4.6.1 lub nowszej.
* Aplikacje platformy ASP.NET Core uruchomiony w programie .NET Core 2.0 lub nowszych na Windows.

Aby uzyskać więcej informacji, zobacz [debugowania działających aplikacji platformy ASP.NET przy użyciu punkty przyciągania i punkty rejestrowania](../debugger/debug-live-azure-applications.md).

## <a name="windows-app-development"></a>Tworzenie aplikacji na komputer z systemem Windows

### <a name="universal-windows-platform"></a>Platforma uniwersalna systemu Windows

Uniwersalnej platformy Windows (UWP) to platforma aplikacji dla systemu Windows 10. Możesz opracowywać aplikacje platformy uniwersalnej systemu Windows za pomocą tylko jednego zestawu interfejsów API, jeden pakiet aplikacji i jeden magazyn, aby dotrzeć do wszystkich urządzeń z systemem Windows 10 &ndash; komputer, tablet, telefon, Xbox, HoloLens, Surface Hub i więcej. Platformy uniwersalnej systemu Windows obsługuje różnych rozmiarów ekranu i z różnych modeli interakcji, czy jest to touch, mysz i klawiatura, kontrolerów gier lub pióra. Aplikacje platformy uniwersalnej systemu Windows jest rozwiązaniem, w jaki użytkownicy chcą doświadczeniem być przenośne na wszystkie swoje urządzenia i chcą używać niezależnie od urządzenia jest najbardziej wygodne lub wydajność dla wykonywanego zadania.

 ![Platforma uniwersalna systemu Windows](../cross-platform/media/uwp_coreextensions.png)

Wybierz język programowania preferowanych&mdash;w językach C#, Visual Basic, C++ lub JavaScript&mdash;umożliwiające utworzenie aplikacji Universal Windows Platform dla urządzeń z systemem Windows 10. Program Visual Studio 2017 zawiera szablon aplikacji platformy uniwersalnej systemu Windows dla każdego z języków, która umożliwia utworzenie jednego projektu dla wszystkich urządzeń. Po zakończeniu pracy możesz produkcji pakietu aplikacji i przesłać go do Microsoft Store z poziomu programu Visual Studio do swojej aplikacji dla klientów na dowolnym urządzeniu z systemem Windows 10.

**Nowość w wersji 15.5**: Visual Studio 2017 w wersji 15.5 zapewnia najlepszą obsługę Windows 10 Fall Creators Update SDK (10.0.16299.0). Windows 10 Fall Creators Update zapewnia również wiele usprawnień dla deweloperów platformy uniwersalnej systemu Windows. Poniżej przedstawiono niektóre z największych zmian: 

* **Obsługa .NET Standard 2.0**<br/>Oprócz wdrażania usprawnione aplikacji systemu Windows 10 Fall Creators Update jest pierwsza wersja systemu Windows 10, aby zapewnić obsługę .NET Standard 2.0. W rezultacie [.NET Standard](https://devblogs.microsoft.com/dotnet/introducing-net-standard/) jest referencyjnej implementacji Biblioteka klasy podstawowej, który może implementować dowolną platformę .NET. Celem .NET Standard jest zapewnienie bardzo proste, jak to możliwe, dla deweloperów platformy .NET, które umożliwiają współużytkowanie kodu dla dowolnej platformy .NET, które postanowili pracować nad.
* **Najlepsze cechy zarówno platformy uniwersalnej systemu Windows, jak i Win32**<br/>Firma Microsoft ulepszyła platformy Windows 10 za pomocą [Desktop Bridge](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-root) Aby ulepszyć systemu Windows 10 dla wszystkich deweloperów platformy .NET, czy ich bieżący fokus jest ustawiony na platformy UWP, WPF, Windows Forms lub Xamarin. Z nowym typem projektu pakietu aplikacji w programie Visual Studio 2017 w wersji 15.5 można tworzyć pakiety aplikacji Windows dla Twoich projektów WPF i formularze Windows, tak samo jak w przypadku projektów platformy uniwersalnej systemu Windows. Po spakowaniu aplikacji korzyści wdrożenia aplikacji systemu Windows 10 i mieć możliwość dystrybucji za pośrednictwem Microsoft Store (w przypadku aplikacji konsumenta) lub Microsoft Store dla firm i instytucji edukacyjnych. Ponieważ spakowane aplikacje mają dostęp do pełnego powierzchni interfejsu API platformy uniwersalnej systemu Windows oraz interfejsów API systemu Win32 na pulpicie, można teraz modernizowanie aplikacji WPF i formularze Windows stopniowo dzięki funkcjom interfejsów API platformy uniwersalnej systemu Windows i Windows 10. Ponadto możesz dołączyć składniki systemu Win32 w aplikacjach platformy uniwersalnej systemu Windows, które dostarczone na pulpicie ze wszystkimi funkcjami systemu Win32.

Aby uzyskać więcej informacji na temat platformy uniwersalnej systemu Windows, zobacz [opracowywanie aplikacji dla uniwersalnej platformy Windows (UWP)](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md) strony.

## <a name="mobile-app-development"></a>Tworzenie aplikacji mobilnych

### <a name="xamarin"></a>Xamarin

Jako część obciążenia "Programowanie aplikacji mobilnych przy użyciu platformy .NET" deweloperom zapoznać się z C# .NET i Visual Studio może dostarczać natywnych aplikacji systemów Android, iOS i Windows za pomocą platformy Xamarin. Deweloperzy mogą korzystać takie same możliwości i wydajność podczas pracy z platformą Xamarin dla aplikacji mobilnych, w tym zdalnego debugowania na urządzeniach z systemem Android, iOS i Windows&mdash;bez konieczności uczenia się natywnych kodowania w językach Objective-C lub Java.

Aby uzyskać więcej informacji, zobacz [Visual Studio i Xamarin](/xamarin/) strony.

### <a name="entitlements-editor"></a>Edytor uprawnień

**Nowość w 15.3**: Dla potrzeb programowania dla systemu iOS dodaliśmy autonomicznej Edytor uprawnień. Obejmuje ona Komfortowy interfejs użytkownika, który można łatwo przeglądać. Aby go uruchomić, kliknij dwukrotnie użytkownika *plik entitlements.plist* pliku.

![Edytor uprawnień dla platformy Xamarin](media/xamarin-entitlements-editor.png)

### <a name="visual-studio-tools-for-xamarin"></a>Visual Studio Tools for Xamarin

**Nowość w wersji 15.4**: Platforma Xamarin Live umożliwia deweloperom ciągłe wdrażanie, testowanie i debugowanie swoich aplikacji bezpośrednio na urządzeniach z systemem iOS i Android. Po pobraniu aplikacji Xamarin Live Player&mdash;dostępnej w App Store lub Google Play&mdash;można sparować urządzenie z programem Visual Studio i zrewolucjonizować sposób tworzenia aplikacji mobilnych. Ta funkcja jest teraz zawarta w programie Visual Studio i można ją włączyć, przechodząc do opcji **Narzędzia** > **Opcje** > **Xamarin**  > **Inne** > **Włącz Xamarin Live Player**.

![Animacja pary Xamarin Live Player, wdrożenie i tryby edycji na żywo](media/xamarinliveplayer.gif)

### <a name="support-for-google-android-emulator"></a>Obsługa Emulator systemu Google Android

**Nowość w 15.8**: Gdy używasz funkcji Hyper-V, można teraz używać firmy Google emulatora systemu Android side-by-side z innymi technologiami, które są oparte na funkcji Hyper-V, takich jak funkcji Hyper-V maszyny wirtualne platformy Docker narzędzia, HoloLens emulator i więcej. (Ta funkcja wymaga systemu Windows 10 kwietnia 2018 r. Zaktualizuj lub nowszej.)

![Emulator systemu Google Android na technologii Hyper-V](media/xamarin-hyperv-android-emulator.png)

#### <a name="xamarinandroid-designer-split-view-editor"></a>Edytor widoku podzielonego projektanta platformy Xamarin.Android

Również **nowego w programie 15.8**: Wprowadziliśmy znaczne ulepszenia do projektanta środowisko dla platformy Xamarin.Android. Wyróżnienie jest nowy Edytor widoku złożonego, która pozwala na tworzenie, Edycja i Podgląd układów w tym samym czasie.

![Projektant Xamarin.Adroid Edytor widoku złożonego](media/android-designer-split-view.png)

Aby uzyskać więcej informacji, zobacz [przyspieszanie sprzętowe emulatora wydajności](/xamarin/android/get-started/installation/android-emulator/hardware-acceleration?tabs=vswin)

### <a name="visual-studio-app-center"></a>Visual Studio App Center

**Nowość w wersji 15.5**: Visual Studio App Center&mdash;która jest teraz ogólnie dostępna dla aplikacji systemów Android, iOS, macOS i Windows&mdash;ma wszystko, czego potrzebujesz do zarządzania cyklem życia aplikacji, w tym automatycznym kompilacjom testowanie na rzeczywistych urządzeniach w chmurze Dystrybucja do testerów wersji beta i sklepów z aplikacjami i monitorowania użycia rzeczywistych za pomocą awarii i danym analitycznym. Aplikacje napisane w językach Objective-C, Swift, Java, C#, Xamarin i React Native są obsługiwane we wszystkich funkcji.

  ![Środowisko testowe programu Visual Studio App Center](media/app-center-test-env.png)

Aby uzyskać więcej informacji, zobacz [Introducing App Center: Tworzenia, testowania, dystrybucji i monitorować aplikacje w chmurze](https://blogs.msdn.microsoft.com/vsappcenter/introducing-visual-studio-app-center/) wpis w blogu.

## <a name="cross-platform-development"></a>Programowanie dla wielu platform

### <a name="redgate-data-tools"></a>Redgate Data Tools

Aby rozszerzyć funkcje operacji programistycznych do tworzenia bazy danych programu SQL Server, narzędzie Redgate Data Tools są teraz dostępne w programie Visual Studio.

Dołączone do programu Visual Studio 2017 Enterprise:

* [Redgate ReadyRoll Core](http://www.red-gate.com/products/sql-development/readyroll/entrypage/microsoft-and-readyroll?utm_source=microsoft&utm_medium=link&utm_campaign=readyroll&utm_term=docs-newinvs) ułatwia tworzenie skryptów migracji, zarządzanie zmianami w bazie danych przy użyciu kontroli źródła i bezpiecznie Automatyzuj wdrożenia programu SQL Server, bazy danych zmian w aplikacji.
* [Narzędzia Redgate SQL Prompt Core](http://www.red-gate.com/products/sql-development/sql-prompt/entrypage/microsoft-and-sql-prompt?utm_source=microsoft&utm_medium=link&utm_campaign=sqlprompt&utm_term=docs-newinvs) uzupełnianie kodu pozwala pisać w języku SQL szybciej i dokładniej za pomocą inteligentnego. Dodatek SQL Prompt pozwala automatycznie uzupełnić bazę danych, obiekty systemowe oraz słowa kluczowe i oferuje sugestie dla kolumn podczas wpisywania. Skutkuje to kod jest czystszy i występuje mniej błędów, ponieważ nie trzeba pamiętać wszystkich nazw kolumn ani aliasów.

Uwzględnione we wszystkich wersjach programu Visual Studio 2017:

* [Narzędzia Redgate SQL Search](http://www.red-gate.com/products/sql-development/sql-search/?utm_source=microsoft&utm_medium=link&utm_campaign=sqlsearch&utm_term=docs-newinvs) zwiększa wydajność, ułatwiając szybkie znajdowanie fragmentów i obiektów SQL w wielu bazach danych.

Aby dowiedzieć się więcej, zobacz [Redgate Data Tools w programie Visual Studio 2017](https://devblogs.microsoft.com/visualstudio/redgate-data-tools-in-visual-studio-2017/) wpis w blogu.

### <a name="net-core"></a>.NET Core

.NET core jest ogólnego przeznaczenia, modułowe oprogramowanie, dla wielu platform i implementację typu open source .NET Standard i zawiera wiele tych samych interfejsów API jako .NET Framework.

Platforma .NET Core składa się z kilku składników, które obejmują zarządzane kompilatory, środowisko uruchomieniowe, biblioteki klas bazowych i wiele modeli aplikacji, takich jak ASP.NET Core. .NET core obsługuje trzy główne systemy operacyjne: Windows, Linux i macOS. Za pomocą platformy .NET Core w urządzeń, chmury i scenariuszach osadzonych IoT.

A teraz obejmuje obsługę platformy Docker.

**Nowość w 15.3**: Visual Studio 2017 w wersji 15.3 obsługuje programowania .NET Core 2.0. Korzystanie z platformy .NET Core 2.0 wymaga pobieranie i Instalowanie zestawu .NET Core 2.0 SDK oddzielnie.

Aby uzyskać więcej informacji, zobacz [przewodnik platformy .NET Core](/dotnet/core/index) strony.

## <a name="games-development"></a>Tworzenie gier

### <a name="visual-studio-tools-for-unity"></a>Narzędzia Visual Studio Tools for Unity

Jako część obciążenia "Programowanie gier dla aparatu Unity" uwzględniliśmy narzędzia, które pomogą Ci tworzyć i platform do tworzenia gier 2D i 3D oraz zawartości interaktywnej. Utwórz raz, a następnie opublikować na 21 platformach, w tym wszystkich platform urządzeń przenośnych, WebGL, Mac, PC i Linux pulpitu, sieci web lub konsoli przy użyciu programu Visual Studio 2017 i środowisko Unity 5.6.

Aby uzyskać więcej informacji, zobacz [Visual Studio Tools for Unity](../cross-platform/visual-studio-tools-for-unity.md) strony.

## <a name="ai-development"></a>Opracowywania sztucznej Inteligencji

### <a name="visual-studio-tools-for-ai"></a>Narzędzia Visual Studio Tools for AI

**Nowość w wersji 15.5**: Skorzystaj z funkcji produktywności programu Visual Studio, aby przyspieszyć innowacji sztucznej Inteligencji już dziś. Użyj kodu wbudowanego edytora funkcje, takie jak wyróżniania składni, funkcję IntelliSense i tekst automatycznego formatowania. Możesz przetestować interaktywnie swoje głębokie uczenie aplikacji w środowisku lokalnym za pomocą krokowym debugowanie, zmienne lokalne i modeli.

  ![Środowisko IDE do uczenia głębokiego](../ai/media/about/ide.png)

Aby uzyskać więcej informacji, zobacz [Visual Studio Tools for AI](../ai/about-ai-tools.md) strony.

## <a name="whats-next"></a>Jaka jest przyszłość

Firma Microsoft aktualizuje program Visual Studio 2017 często z nowymi funkcjami, które mogą ułatwić programowanie jeszcze lepsze środowisko. Poniżej przedstawiono podsumowanie niektórych nasze najbardziej znaczące aktualizacje, które znajdują się w eksperymentalnej wersji zapoznawczej:

* **[Na żywo udziału](https://visualstudio.microsoft.com/services/live-share/)**, nowe narzędzie, które pozwala na udostępnianie kodu i kontekst współpracownikom i Uzyskaj natychmiastowej dwukierunkowej możliwości współpracy bezpośrednio z poziomu programu Visual Studio. Za pomocą udostępniania na żywo partnerem można przeczytać, przejdź, edytować i debugować projekt, który został udostępniony z nimi i bezproblemowo i bezpiecznie w tym celu.<br><br>Aby uzyskać więcej informacji, zobacz [często zadawane pytania dotyczące udostępniania na żywo](/visualstudio/liveshare/faq).<br><br>
* **[Rozszerzenie IntelliCode](https://visualstudio.microsoft.com/services/intellicode/)**, nową możliwość, która rozszerza Wytwarzanie oprogramowania za pomocą sztucznej Inteligencji do dostarczania uzupełnienia lepiej oparte na kontekście kodu przewodnik deweloperom kodu do wzorców i style ich zespołu, znajdowanie problemów z kodem trudne catch , i przeglądy kodu skoncentrować się na obszarach, które naprawdę mają znaczenie. <br><br>Aby uzyskać więcej informacji, zobacz [IntelliCode — często zadawane pytania](/visualstudio/intellicode/faq).

Chcesz wiedzieć więcej o tym, co jeszcze jest działa w programie Visual Studio 2017? Zobacz [Visual Studio plan](/visualstudio/productinfo/vs2018-roadmap) strony.

## <a name="contact-us"></a>Skontaktuj się z nami

 Dlaczego warto wysłać opinię do zespołu usługi Visual Studio? Ponieważ traktujemy opinie naszych użytkowników bardzo poważnie. Zależy od ilości co możemy zrobić.

Jeśli chcesz sugestię o jak możemy ulepszyć program Visual Studio, lub Dowiedz się więcej o opcjach pomocy technicznej produktu, zapoznaj się z artykułem [Porozmawiaj z nami](talk-to-us.md) strony.

### <a name="report-a-problem"></a>zgłaszanie problemu

 Czasami komunikat nie jest wystarczająca do przekazania pełnego wpływu napotkany problem. Występują zawieszenie, awarii lub innych problemów z wydajnością, możesz w prosty sposób udostępniać Odtwórz kroki i pliki pomocnicze (takie jak zrzuty ekranu i śledzenia i sterty pliki zrzutu) z nami za pomocą **Zgłoś Problem** narzędzia. Aby uzyskać więcej informacji na temat używania tego narzędzia, zobacz [jak zgłosić problem](how-to-report-a-problem-with-visual-studio.md) strony.

## <a name="see-also"></a>Zobacz także

* [Informacje o wersji programu Visual Studio 2017](/visualstudio/releasenotes/vs2017-relnotes?context=visualstudio/default&contextView=vs-2017)
* [Co nowego w zestawie Visual Studio 2017 SDK](/visualstudio/extensibility/what-s-new-in-the-visual-studio-2017-sdk?view=vs-2017)
* [What's new in Visual C++](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio)
* [Co nowego w języku C#](/dotnet/csharp/whats-new)
* [What's new for Team Foundation Server](/tfs/server/whats-new?view=vsts)
* [Co nowego w programie Visual Studio dla komputerów Mac](https://visualstudio.microsoft.com/vs/visual-studio-mac/)
* [What's new in Visual Studio 2019 r.](whats-new-visual-studio-2019.md)

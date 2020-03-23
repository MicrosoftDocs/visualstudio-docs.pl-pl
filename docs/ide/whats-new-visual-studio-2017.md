---
title: Co nowego w programie Visual Studio 2017
titleSuffix: ''
description: Dowiedz się więcej o nowych funkcjach programu Visual Studio 2017.
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
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: de26054894783df283d38223a59741c0500d0bc5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74955039"
---
# <a name="whats-new-in-visual-studio-2017"></a>Co nowego w programie Visual Studio 2017

**Aktualizacja [wersji 15.9](/visualstudio/releasenotes/vs2017-relnotes?context=visualstudio/default&contextView=vs-2017)**

Chcesz uaktualnić z poprzedniej wersji programu Visual Studio? Oto, co program Visual Studio 2017 może zaoferować: Niezrównana produktywność dla każdego dewelopera, dowolnej aplikacji i dowolnej platformy. Program Visual Studio 2017 służy do tworzenia aplikacji dla systemów Android, iOS, Windows, Linux, web i cloud. Szybko twórz kod, z łatwością debuguj i diagnozuj, często testuj i swobodnie wydawaj. Możesz również rozszerzać funkcjonalność programu Visual Studio oraz go dostosowywać, tworząc własne rozszerzenia. Korzystaj z kontroli wersji, bądź zwinny i współpracuj wydajnie z tą wersją!

>[!div class="button"]
>[Pobierz program Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

Oto podsumowanie wysokiego poziomu zmian wprowadzonych od poprzedniej wersji programu Visual Studio 2015:

* **[Przedefiniowane podstawy](#redefined-fundamentals)**. Nowe środowisko konfiguracji oznacza, że można zainstalować szybciej i zainstalować to, co chcesz, gdy jest to potrzebne.
* **[Wydajność i produktywność](#performance-and-productivity)**. Skupiliśmy się na nowych i nowoczesnych możliwościach rozwoju urządzeń mobilnych, chmur i komputerów stacjonarnych. Program Visual Studio uruchamia się szybciej, jest bardziej responsywny i zużywa mniej pamięci niż wcześniej.
* **[Tworzenie aplikacji w chmurze za pomocą platformy Azure](#cloud-app-development-with-azure)**. Wbudowany zestaw narzędzi platformy Azure umożliwia łatwe tworzenie aplikacji opartych na chmurze z platformą Microsoft Azure. Visual Studio ułatwia konfigurowanie, tworzenie, debugowanie, pakowanie i wdrażanie aplikacji i usług na platformie Azure.
* **[Tworzenie aplikacji systemu Windows](#windows-app-development)**. Użyj szablonów platformy uniwersalnej systemu Windows w programie Visual Studio 2017, aby utworzyć pojedynczy projekt dla wszystkich urządzeń &ndash; z systemem Windows 10 PC, tablet, telefon, Xbox, HoloLens, Surface Hub i innych.
* **[Tworzenie aplikacji mobilnych](#mobile-app-development)**. Wprowadzaj innowacje i szybko utrzymuj wyniki dzięki platformie Xamarin, która ujednolica wymagania mobilne na wielu platformach z jedną podstawową bazą kodu i zestawem umiejętności.
* **[Rozwój międzyplatformowy](#cross-platform-development)**. Bezproblemowe dostarczanie oprogramowania na dowolną docelową platformę. Rozszerzanie procesów DevOps do programu SQL Server za pośrednictwem narzędzi Redgate Data Tools i bezpieczne automatyzacja wdrożeń bazy danych z programu Visual Studio. Można też używać programu .NET Core do pisania aplikacji i bibliotek, które działają bez modyfikacji w systemach operacyjnych Windows, Linux i macOS.
* **[Rozwój gier](#games-development)**. Za pomocą programu Visual Studio Tools for Unity (VSTU) można używać programu Visual Studio do pisania skryptów gier i edytorów w języku C#, a następnie używać zaawansowanego debugera do znajdowania i naprawiania błędów.
* **[rozwój SI](#ai-development)**. Dzięki narzędziom programu Visual Studio dla urządzeń SI można korzystać z funkcji zwiększających produktywność programu Visual Studio w celu przyspieszenia innowacji w zakresie ai. Twórz, testuj i wdrażaj rozwiązania deep learning/ sztucznej inteligencji, które bezproblemowo integrują się z usługą Azure Machine Learning w celu uzyskania niezawodnych możliwości eksperymentowania.

> [!NOTE]
> Aby uzyskać pełną listę nowych funkcji i funkcji w programie Visual Studio 2017, zobacz [Bieżące informacje o wersji](/visualstudio/releasenotes/vs2017-relnotes?context=visualstudio/default&contextView=vs-2017). Aby zapoznać się z przyszłymi ofertami funkcji, zobacz [informacje o wersji podglądu](/visualstudio/releasenotes/vs2017-preview-relnotes?context=visualstudio/default&contextView=vs-2017).

Oto bardziej szczegółowe informacje na temat niektórych z najbardziej znaczących ulepszeń i nowych funkcji w programie Visual Studio 2017.

## <a name="redefined-fundamentals"></a>Przedefiniowane podstawy

### <a name="a-new-setup-experience"></a>Nowe środowisko konfiguracji

Visual Studio ułatwia i przyspiesza instalowanie tylko tych funkcji, których potrzebujesz, gdy ich potrzebujesz. I, to odinstalowuje czysto, zbyt.

Najważniejszą zmianą, na którą należy zwrócić uwagę podczas instalowania programu Visual Studio, jest jego nowe środowisko konfiguracji. Na karcie **Obciążenia** zobaczysz opcje instalacji, które są zgrupowane w celu reprezentowania wspólnych struktur, języków i platform. Obejmuje wszystko, od tworzenia pulpitu .NET do tworzenia aplikacji C++ w systemach Windows, Linux i iOS.

Wybierz potrzebne obciążenia i zmień je, gdy zajdzie taka potrzeba.

![Okno dialogowe ustawień programu Visual Studio 2017](../install/media/install-visual-studio-enterprise.png)

Masz też opcje dostrojenia instalacji:

* Chcesz wybrać własne składniki zamiast obciążeń? Wybierz kartę **Poszczególne składniki** z instalatora.
* Chcesz zainstalować pakiety językowe bez konieczności zmiany opcji języka systemu Windows? Wybierz kartę **Pakiety językowe** instalatora.
* **Nowość w wersji 15.7**: Chcesz zmienić lokalizację instalacji programu Visual Studio? Wybierz kartę **Opcje instalacji** instalatora.

Aby dowiedzieć się więcej o nowym środowisko instalacji, w tym instrukcje krok po kroku, które cię przez to, zobacz [Install Visual Studio](../install/install-visual-studio.md) strony.

### <a name="a-focus-on-accessibility"></a>Nacisk na dostępność

**Nowością w wersji 15.3,** dokonaliśmy ponad 1700 ukierunkowanych poprawek w celu poprawy zgodności między programem Visual Studio a technologiami pomocniczymi używanymi przez wielu klientów. Istnieją dziesiątki scenariuszy, które są bardziej zgodne z czytnikami ekranu, motywami o wysokim kontraście i innymi technologiami pomocniczymi niż kiedykolwiek wcześniej. Debuger, edytor i powłoka mają wszystkie zdobyć znaczące ulepszenia, zbyt.

Aby uzyskać więcej informacji, zobacz wpis w blogu [dotyczące ułatwień dostępu w programie Visual Studio 2017 w wersji 15.3.](https://devblogs.microsoft.com/visualstudio/accessibility-improvements-in-visual-studio-2017-version-15-3/)

## <a name="performance-and-productivity"></a>Wydajność i produktywność

### <a name="sign-in-across-multiple-accounts"></a>Logowanie się na wielu kontach

Wprowadziliśmy nową usługę tożsamości w programie Visual Studio, która umożliwia udostępnianie kont użytkowników w Eksploratorze zespołu, narzędziach platformy Azure, publikowaniu w sklepie Microsoft Store i innych.

Możesz pozostać zalogowany dłużej, zbyt. Visual Studio nie prosi o ponowne zalogowanie się co 12 godzin. Aby dowiedzieć się więcej, zobacz wpis w blogu [Monity o mniej logowania programu Visual Studio.](https://devblogs.microsoft.com/visualstudio/fewer-visual-studio-sign-in-prompts/)

### <a name="start-visual-studio-faster"></a>Szybsze uruchamianie programu Visual Studio

Nowe Centrum wydajności programu Visual Studio może pomóc zoptymalizować czas uruchamiania ide. Centrum wydajności zawiera listę wszystkich rozszerzeń i okien narzędzi, które mogą spowolnić uruchamianie IDE. Można go użyć, aby poprawić wydajność uruchamiania, określając, kiedy rozszerzenia są uruchamiane lub czy okna narzędzi są otwarte podczas uruchamiania.

### <a name="faster-on-demand-loading-of-extensions"></a>Szybsze ładowanie rozszerzeń na żądanie

Visual Studio przenosi jego rozszerzenia (i pracy z rozszerzeniami innych firm też), tak aby załadować na żądanie, a nie podczas uruchamiania IDE. Zastanawiasz się, które rozszerzenia wpływają na wydajność uruchamiania, ładowania rozwiązań i wpisywania tekstu? Informacje te można wyświetlić w **programie Pomoc** > w**zarządzaniu wydajnością programu Visual Studio**.

  ![Okno dialogowe Opcje w programie Visual Studio 2017](media/vs2017ide-manage-vs-perf.png)

#### <a name="manage-your-extensions-with-roaming-extensions-manager"></a>Zarządzanie rozszerzeniami za pomocą Menedżera rozszerzeń roamingu

Jest to łatwiejsze do skonfigurowania każdego środowiska programistycznego z ulubionych rozszerzeń po zalogowaniu się do programu Visual Studio. Nowy Menedżer rozszerzeń roamingu śledzi wszystkie ulubione rozszerzenia, tworząc zsynchronizowany wykaz w chmurze.

Aby wyświetlić listę rozszerzeń w programie Visual Studio, kliknij pozycję Rozszerzenia **narzędzi** > **& aktualizacje**, a następnie kliknij pozycję Menedżer **rozszerzeń mobilnych**.

![Visual Studio 2017 — okno dialogowe Rozszerzenia i aktualizacje](media/vs2017ide-extensions-and-updates.png)

Menedżer rozszerzeń mobilnych śledzi wszystkie instalowane rozszerzenia, ale możesz wybrać te, które chcesz dodać do listy roamingu.

![Visual Studio 2017 — okno dialogowe Rozszerzenia i aktualizacje](media/vs2017ide-RoamingExtensionManager.png)

Podczas korzystania z Menedżera rozszerzeń roamingu na liście znajdują się trzy typy ikon:

* ![Wędrowała ikona](media/vs2017ide-roamedicon.png) **_Roamed:_** Rozszerzenie, które jest częścią tej listy roamingu, ale nie jest zainstalowane na komputerze.
  (Można je zainstalować za pomocą przycisku **Pobierz).**
* ![Wędrował & Zainstalowana](media/vs2017ide-roamedinstalledicon.png) **_ikona Roamed & Zainstalowany:_** Wszystkie rozszerzenia, które są częścią tej listy roamingu i zainstalowane w środowisku deweloperskim.
  (Jeśli zdecydujesz, że nie chcesz wędrować, możesz je usunąć za pomocą przycisku **Zatrzymaj roaming).**
* ![Zainstalowana](media/vs2017ide-installedicon.png) **_ikona zainstalowana:_** Wszystkie rozszerzenia, które są zainstalowane w tym środowisku, ale nie są częścią listy roamingu.
  (Rozszerzenia można dodawać do listy roamingowej za pomocą przycisku **Rozpocznij roaming).**

Każde rozszerzenie pobrane po zalogowaniu się jest dodawane do listy jako **Roamed & Installed**. Rozszerzenie staje się częścią listy roamingu, co daje dostęp do niego z dowolnego komputera.

### <a name="experience-live-unit-testing"></a>Doświadcz testów jednostkowych na żywo

W programie Visual Studio Enterprise 2017 testowanie jednostek na żywo zapewnia wyniki testów jednostkowych na żywo i pokrycie kodu w edytorze podczas kodowania. Działa z projektami języka C# i Visual Basic dla platformy .NET Framework i .NET Core i obsługuje trzy struktury testowe mstest, xUnit i NUnit.

![Live Unit Testing](media/lut-codewindow.png)

Aby uzyskać więcej informacji, zobacz [Wprowadzenie do testowania jednostek na żywo](../test/live-unit-testing-intro.md). Aby uzyskać listę nowych funkcji dodanych w każdej wersji programu Visual Studio Enterprise 2017, zobacz [Co nowego w testach jednostek na żywo](../test/live-unit-testing-whats-new.md).

### <a name="set-up-a-cicd-pipeline"></a>Konfigurowanie potoku ciągłej integracji/ciągłego dostarczania

#### <a name="automated-testing"></a>Automatyczne testowanie

Automatyczne testowanie jest kluczową częścią każdego potoku DevOps. Pozwala na spójne i niezawodne testowanie i uwalnianie rozwiązania w znacznie krótszych cyklach. Przepływy ciągłej integracji i ciągłego dostarczania (ciągła integracja i ciągłe dostarczanie) mogą pomóc w zwiększenia wydajności procesu.

Aby uzyskać więcej informacji na temat testów automatycznych, zobacz [potok ciągłej integracji/ciągłego wdrażania dla zautomatyzowanych testów w blogu DevOps.](https://blogs.msdn.microsoft.com/visualstudioalmrangers/2017/04/20/set-up-a-cicd-pipeline-to-run-automated-tests-efficiently/)

Aby uzyskać więcej informacji na temat nowości w [narzędziach ciągłego dostarczania dla](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) rozszerzenia Visual Studio DevLabs, zobacz Wpis w blogu [Commit with confidence: Commit time code quality.](https://devblogs.microsoft.com/visualstudio/committing-with-confidence-getting-code-quality-information-at-commit-time/)

### <a name="visual-studio-ide-enhancements"></a>Ulepszenia IDE programu Visual Studio

#### <a name="multi-caret-editing"></a>Edycja przy użyciu wielokaretki

**Nowość w 15.8**: Jednoczesna edycja wielu lokalizacji w pliku jest teraz łatwa. Zacznij od utworzenia punktów wstawiania i zaznaczeń w wielu lokalizacjach w pliku. Następnie użyj funkcji edycji wielu elementów, aby dokonać tej samej edycji w dwóch lub więcej miejscach w tym samym czasie.

Aby uzyskać więcej informacji, zobacz sekcję [Wyboru wielu łóżek](finding-and-replacing-text.md#multi-caret-selection) na stronie [tekstowej Znajdź i zastąp.](finding-and-replacing-text.md)

#### <a name="keep-keybinding-profiles-consistent"></a>Utrzymuj spójność profili wiązania kluczy

**Nowość w wersji 15.8**: Teraz można zachować spójność funkcji wiązania klawiszy w narzędziach za pomocą dwóch nowych profilów klawiatury: Visual Studio Code i ReSharper (Visual Studio). Schematy te można znaleźć w menu **Narzędzia** > **Opcje** > **klawiatury** **ogólnej** > i menu rozwijanego.

  ![Nowe profile wiązania kluczy dla programu Visual Studio Code i ReSharper](media/vs-keyboard-mappings-code-resharper.png)

#### <a name="use-new-refactorings"></a>Używanie nowych refaktoryzacji

Refaktoryzowanie jest procesem poprawy kodu po jego zapisaniu. Refaktoryzowanie zmienia wewnętrzną strukturę kodu bez zmiany jego zachowania. Często dodajemy nowe refaktoryzje; oto kilka z nich:

* Dodaj parametr (z callsite)
* Generowanie przesłomów
* Dodawanie nazwanego argumentu
* Dodawanie sprawdzania wartości null pod kątem parametrów
* Wstawianie separatorów cyfr do literałów
* Zmień podstawę dla literałów liczbowych (na przykład sześciokątnych na binarne)
* Konwertowanie if-to-switch
* Usuwanie nieużywanych zmiennych

Aby uzyskać więcej informacji, zobacz [Szybkie akcje](common-quick-actions.md).

#### <a name="interact-with-git"></a>Interakcja z gitem

Podczas pracy z projektem w programie Visual Studio, można skonfigurować i szybko zatwierdzić i opublikować kod do usługi Git. Repozytoria Git można również zarządzać za pomocą kliknięć menu z przycisków w prawym dolnym rogu IDE.

![Visual Studio 2017 wchodzi w interakcję z dialogiem git](media/vsIDE-GitInteraction.png)

#### <a name="experience-improved-navigation-controls"></a>Doświadcz ulepszonych kontroli nawigacji

Odświeżyliśmy nawigację, aby pomóc Ci uzyskać od A do B z większą pewnością siebie i mniejszą ilością zakłóceń.

* **Nowość w 15.4**: **Przejdź do definicji** &ndash; **(Ctrl**+**kliknij** lub **F12**) Użytkownicy myszy mają łatwiejszy sposób, aby przejść do definicji członka, naciskając **Ctrl,** a następnie klikając element członkowski. Naciśnięcie **klawisza Ctrl** i najechanie kursorem na symbol kodu podkreśli go i zmieni w łącze. Aby uzyskać więcej informacji, zobacz [Przejdź do definicji i Zajrzeć do definicji.](go-to-and-peek-definition.md)

* **Przejdź do implementacji** **(Ctrl**+**F12**) &ndash; Przejdź od dowolnego typu podstawowego lub elementu członkowskiego do jego różnych implementacji.

* **Przejdź do wszystkich** **(Ctrl**+**T** &ndash; lub **Ctrl**+**,**) Przejdź bezpośrednio do dowolnego pliku / typu / elementu członkowskiego / symbol deklaracji. Możesz filtrować listę wyników lub użyć składni kwerendy (na przykład "f searchTerm" dla plików, "t searchTerm" dla typów itp.).

  ![Ulepszone Przejdź do wszystkich](media/vs2017ide-navigation-go-to.png)

* **Znajdź wszystkie odwołania** **(Shift**+**F12)** &ndash; Za pomocą koloryzacji składni można pogrupować wyniki znajdź wszystkie odniesienia według kombinacji projektu, definicji i ścieżki. Można również "zablokować" wyniki, dzięki czemu można nadal znaleźć inne odwołania bez utraty oryginalnych wyników.

  ![Narzędzie Nowe znajdź wszystkie odwołania](media/vs2017ide-find-all-references.png)

* **Wizualizacja struktury** &ndash; Kropkowane, szare pionowe linie (linie pomocnicze wcięci) działają jako punkty orientacyjne w kodzie, aby zapewnić kontekst w ramce widoku. Możesz je rozpoznać w popularnych narzędziach zwiększających produktywność. Możesz ich użyć do wizualizacji i odkrycia, w jakim bloku kodu jesteś w dowolnym momencie bez konieczności przewijania. Kursowanie kursorem nad wierszami powoduje wyświetlenie etykietki narzędzia, która pokazuje otwarcie tego bloku i jego chyłek. Jest on dostępny dla wszystkich języków obsługiwanych za pośrednictwem gramatyki TextMate, a także C#, Visual Basic i XAML.

  ![Wizualizator struktury programu Visual Studio 2017](media/vsIDE-StructureVisualizer.png)

Aby uzyskać więcej informacji na temat nowych funkcji produktywności, zobacz wpis w blogu [programu Visual Studio 2017: Produktywność, wydajność i partnerzy.](https://devblogs.microsoft.com/visualstudio/visual-studio-2017-productivity-performance-and-partners/)

### <a name="visual-c"></a>Visual C++

Zobaczysz kilka ulepszeń w programie Visual Studio, takich jak dystrybucja C++ Podstawowych Wskazówek z visual studio, aktualizowanie kompilatora przez dodanie rozszerzonej obsługi funkcji C++ 11 i C++ oraz dodawanie i aktualizowanie funkcji w bibliotekach języka C++. Firma We've also improved the performance of the C++ IDE, installation workloads, and more.

Naprawiliśmy również ponad 250 błędów i zgłosiliśmy problemy w kompilatorze i narzędziach, wiele przesłanych przez klientów za pośrednictwem [społeczności programistów dla języka C++](https://developercommunity.visualstudio.com/spaces/62/index.html "Społeczność programistów dla języka C++").

Aby uzyskać szczegółowe informacje, zobacz [co nowego dla języka Visual C++ w visual 2017](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio) strony.

### <a name="debugging-and-diagnostics"></a>Debugowanie i diagnostyka

#### <a name="run-to-click"></a>Uruchom do kliknięcia

Teraz można łatwiej przejść do przodu podczas debugowania bez ustawiania punktu przerwania, aby zatrzymać na linii, który chcesz. Po zatrzymaniu w debugerze, po prostu kliknij ikonę, która pojawia się obok wiersza kodu. Kod zostanie uruchomiony i zatrzyma się w tym wierszu, gdy następnym razem zostanie trafiony w ścieżce kodu.

![Debugowanie programu Visual Studio 2017 — uruchamianie do kliknięcia](media/vs2017ide-RunToClick.png)

#### <a name="the-new-exception-helper"></a>Nowy pomocnik wyjątków

Nowy Pomocnik wyjątków ułatwia przeglądanie informacji o wyjątkach w skrócie. Informacje są prezentowane w formie kompaktowej z natychmiastowym dostępem do wewnętrznych wyjątków. Podczas diagnozowania NullReferenceException, można szybko zobaczyć, co było null prawo wewnątrz Pomocnika wyjątku.

![Okno dialogowe Pomocnik nowego wyjątku w programie Visual Studio](media/vs2017ide-ExceptionHelper.png)

Aby uzyskać więcej informacji, zobacz [użyj nowego pomocnika wyjątków w blogu programu Visual Studio.](https://devblogs.microsoft.com/devops/using-the-new-exception-helper-in-visual-studio-15-preview/)

#### <a name="snapshots-and-intellitrace-step-back"></a>Migawki i krok po kroku IntelliTrace

**Nowość w 15.5:** IntelliTrace step-back automatycznie wykonuje migawkę aplikacji przy każdym zdarzeniu kroku punktu przerwania i debugera. Zarejestrowane migawki umożliwiają powrót do poprzednich punktów przerwania lub kroki i wyświetlić stan aplikacji, jak to było w przeszłości. IntelliTrace krok wstecz można zaoszczędzić czas, gdy chcesz zobaczyć poprzedni stan aplikacji, ale nie chcesz ponownie debugowania lub ponownie utworzyć żądany stan aplikacji.

Migawki można nawigować i wyświetlać za pomocą przycisków **Krok do tyłu** i Krok do **przodu** na pasku narzędzi **Debugowania.** Te przyciski nawigują po zdarzeniach wyświetlanych na karcie **Zdarzenia** w oknie **Narzędzia diagnostyczne.** Przechodzenie do tyłu lub do przodu do zdarzenia automatycznie aktywuje debugowanie historyczne na wybrane zdarzenie.

![Okno dialogowe Pomocnik nowego wyjątku w programie Visual Studio](../debugger/media/intellitrace-step-back-icons-description.png  "Przyciski Krok do tyłu i Do przodu")

Aby uzyskać więcej informacji, zobacz [Wyświetlanie migawek przy użyciu strony krok po kroku IntelliTrace.](../debugger/view-historical-application-state.md)

### <a name="containerization"></a>Przechowywanie w kontenerach

Kontenery zapewniają większą gęstość aplikacji i niższe koszty wdrożenia wraz z lepszą wydajnością i elastycznością DevOps.

#### <a name="docker-container-tooling"></a>Narzędzia kontenerów Docker

**Nowość w 15.5**:

* Program Visual Studio zawiera narzędzia dla kontenerów platformy Docker, które teraz obsługują wieloetapowe pliki dockerfiles, które usprawniają tworzenie zoptymalizowanych obrazów kontenerów.
* Domyślnie program Visual Studio będzie automatycznie ściągać, kompilować i uruchamiać niezbędne obrazy kontenera w tle podczas otwierania projektu obsługującego platformę Docker. Tę opcję można wyłączyć za pomocą ustawienia **Automatycznie uruchom kontenery w tle** w programie Visual Studio.

## <a name="cloud-app-development-with-azure"></a>Tworzenie aplikacji w chmurze za pomocą platformy Azure

### <a name="azure-functions-tools"></a>Narzędzia usługi Azure Functions

W ramach obciążenia "rozwoju platformy Azure" uwzględniliśmy narzędzia ułatwiające tworzenie funkcji platformy Azure przy użyciu wstępnie skompilowanych bibliotek klas C#. Teraz można tworzyć, uruchamiać i debugować na komputerze lokalnego tworzenia, a następnie publikować bezpośrednio na platformie Azure z programu Visual Studio.

Aby uzyskać więcej informacji, zobacz [narzędzia usługi Azure Functions dla programu Visual Studio](/azure/azure-functions/functions-develop-vs) strony.

### <a name="debug-live-aspnet-apps-using-snappoints-and-logpoints-in-live-azure-applications"></a>Debugowanie aplikacji na żywo ASP.NET przy użyciu punktów przyciągania i punktów dziennika w aplikacjach platformy Azure na żywo

**Nowość w 15.5:** Debuger migawki wykonuje migawkę aplikacji w produkcji, gdy kod, który cię interesuje wykonuje. Aby poinstruować debugera, aby zrobić migawkę, należy ustawić punkty przyciągania i punkty dziennika w kodzie. Debuger pozwala zobaczyć dokładnie, co poszło nie tak, bez wpływu na ruch aplikacji produkcyjnej. Debuger migawek może pomóc znacznie skrócić czas potrzebny do rozwiązania problemów występujących w środowiskach produkcyjnych.

Kolekcja migawek jest dostępna dla następujących aplikacji sieci web uruchomionych w usłudze Azure App Service:

* ASP.NET aplikacji uruchomionych w programie .NET Framework 4.6.1 lub nowszym.
* ASP.NET aplikacje Core działające w systemie .NET Core 2.0 lub nowszym w systemie Windows.

Aby uzyskać więcej informacji, zobacz [Debugowanie aplikacji na żywo ASP.NET przy użyciu punktów przyciągania i punktów dziennika](../debugger/debug-live-azure-applications.md).

## <a name="windows-app-development"></a>Tworzenie aplikacji na komputer z systemem Windows

### <a name="universal-windows-platform"></a>Platforma uniwersalna systemu Windows

Uniwersalna platforma systemu Windows (UWP) to platforma aplikacji dla systemu Windows 10. Możesz tworzyć aplikacje dla platformy uniwersalnej systemu Windows za pomocą jednego zestawu interfejsu &ndash; API, jednego pakietu aplikacji i jednego sklepu, aby dotrzeć do wszystkich urządzeń z systemem Windows 10 PC, tablet, telefon, Xbox, HoloLens, Surface Hub i innych. Platforma uniwersalna systemuśpicia obsługuje różne rozmiary ekranu i różne modele interakcji, niezależnie od tego, czy są to dotyk, mysz i klawiatura, kontroler gier czy pióro. Sednem aplikacji platformy uniwersalnej systemu Windows jest pomysł, że użytkownicy chcą, aby ich środowiska były mobilne na wszystkich swoich urządzeniach i że chcą używać dowolnego urządzenia, które jest najwygodniejsze lub produktywne do wykonywanego zadania.

![Platforma uniwersalna systemu Windows](../cross-platform/media/uwp_coreextensions.png)

Wybierz preferowany&mdash;język programowania z języka C#, Visual&mdash;Basic, C++ lub JavaScript, aby utworzyć aplikację uniwersalną platformy systemu Windows dla urządzeń z systemem Windows 10. Visual Studio 2017 udostępnia szablon aplikacji platformy uniwersalnej systemu Windows dla każdego języka, który umożliwia utworzenie jednego projektu dla wszystkich urządzeń. Po zakończeniu pracy można utworzyć pakiet aplikacji i przesłać go do sklepu Microsoft Store z poziomu programu Visual Studio, aby uzyskać aplikację do klientów na dowolnym urządzeniu z systemem Windows 10.

**Nowość w wersji 15.5**: Visual Studio 2017 w wersji 15.5 zapewnia najlepszą obsługę pakietu SDK aktualizacji Windows 10 Fall Creators Update (10.0.16299.0). Aktualizacja Windows 10 Fall Creators Update zawiera również wiele ulepszeń dla programistów platformy uniwersalnej systemu Windows. Oto niektóre z największych zmian: 

* **Obsługa platformy .NET Standard 2.0**<br/>Oprócz usprawnienia wdrażania aplikacji, Windows 10 Fall Creators Update jest pierwszą wersją systemu Windows 10, która zapewnia obsługę .NET Standard 2.0. Skutecznie [.NET Standard](https://devblogs.microsoft.com/dotnet/introducing-net-standard/) jest implementacją odwołania biblioteki klas podstawowych, które można zaimplementować dowolnej platformy .NET. Celem programu .NET Standard jest ułatwienie deweloperom platformy .NET udostępniania kodu na dowolnej platformie platformy .NET, nad którą chcą pracować.
* **Najlepsze zarówno platformy uniwersalne systemu jak uwp i Win32**<br/>Ulepszyliśmy platformę Windows 10 za pomocą [mostka pulpitu,](/windows/uwp/porting/desktop-to-uwp-root) aby system Windows 10 był lepszy dla wszystkich programistów platformy .NET, niezależnie od tego, czy ich obecne skupienie się na platformie UWP, WPF, Windows Forms czy Xamarin. Dzięki nowemu typowi projektu pakowania aplikacji w programie Visual Studio 2017 w wersji 15.5 można tworzyć pakiety aplikacji systemu Windows dla projektów WPF lub Formularze systemu Windows, tak jak w przypadku projektów platformy uniwersalnej systemu Windows. Po spakowaniu aplikacji otrzymasz wszystkie korzyści związane z wdrażaniem aplikacji systemu Windows 10 i możesz rozpowszechniać za pośrednictwem sklepu Microsoft Store (dla aplikacji konsumenckich) lub sklepu Microsoft Store dla firm i edukacji. Ponieważ spakowane aplikacje mają dostęp zarówno do pełnej powierzchni interfejsu API platformy uniwersalnej systemu Windows, jak i interfejsów API systemu Win32 na komputerze, można teraz stopniowo modernizować aplikacje WPF i formularzy systemu Windows za pomocą interfejsów API systemu Windows i funkcji systemu Windows 10. Ponadto można uwzględnić składniki Win32 w aplikacjach platformy uniwersalnej systemu Windows, które zapalają się na pulpicie ze wszystkimi funkcjami usługi Win32.

Aby uzyskać więcej informacji na temat platformy uniwersalnej systemu Windows, zobacz stronę [Tworzenie aplikacji dla platformy uniwersalnej systemu Windows (PLATFORMY UNIWERSALNEJ SYSTEMU Windows).](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md)

## <a name="mobile-app-development"></a>Tworzenie aplikacji mobilnych

### <a name="xamarin"></a>Xamarin

W ramach obciążenia "Mobile development with .NET" deweloperzy zaznajomieni z C#, .NET i Visual Studio mogą dostarczać natywne aplikacje dla systemów Android, iOS i Windows przy użyciu platformy Xamarin. Deweloperzy mogą cieszyć się taką samą mocą i wydajnością podczas pracy z platformą Xamarin&mdash;dla aplikacji mobilnych, w tym zdalnego debugowania na urządzeniach z systemem Android, iOS i Windows bez konieczności uczenia się natywnych języków kodowania, takich jak Objective-C lub Java.

Aby uzyskać więcej informacji, zobacz [Visual Studio i Xamarin](/xamarin/) strony.

### <a name="entitlements-editor"></a>Edytor uprawnień

**Nowość w 15.3**: Dla potrzeb programistów systemu iOS dodaliśmy autonomiczny edytor uprawnień. Zawiera przyjazny dla użytkownika interfejs użytkownika, który można łatwo przeglądać. Aby go uruchomić, kliknij dwukrotnie plik *entitlements.plist.*

![Edytor uprawnień dla platformy Xamarin](media/xamarin-entitlements-editor.png)

### <a name="visual-studio-tools-for-xamarin"></a>Visual Studio Tools for Xamarin

**Nowość w wersji 15.4:** Xamarin Live umożliwia deweloperom ciągłe wdrażanie, testowanie i debugowanie aplikacji bezpośrednio na urządzeniach z systemami iOS i Android. Po pobraniu programu Xamarin Live Player&mdash;dostępnego&mdash;w sklepie App Store lub Google Play możesz sparować urządzenie z programem Visual Studio i zrewolucjonizować sposób tworzenia aplikacji mobilnych. Ta funkcja jest teraz dostępna w programie Visual Studio i można ją włączyć, przechodząc do**opcji** >  **Narzędzia** > **Xamarin** > **Inne** > **Włącz Xamarin Live Player**.

![Animacja pary, wdrażania i edycji na żywo w trybach programu Xamarin Live Player](media/xamarinliveplayer.gif)

### <a name="support-for-google-android-emulator"></a>Obsługa emulatora Google Android

**Nowość w wersji 15.8**: Korzystając z funkcji Hyper-V, teraz możesz używać emulatora Androida Google obok innych technologii opartych na technologii Hyper-V, takich jak maszyny wirtualne Hyper-V, narzędzia Docker, emulator HoloLens i inne. (Ta funkcja wymaga aktualizacji systemu Windows 10 z kwietnia 2018 r. lub nowszej).

![Emulator Google Android na technologiach Hyper-V](media/xamarin-hyperv-android-emulator.png)

#### <a name="xamarinandroid-designer-split-view-editor"></a>Xamarin.Android Designer edytor widoku podzielonego

Również **nowy w 15.8:** Zrobiliśmy znaczące ulepszenia do doświadczenia projektanta dla Xamarin.Android. Wyróżnione to nowy edytor widoku podzielonego, który umożliwia tworzenie, edytowanie i wyświetlanie podglądu układów w tym samym czasie.

![Edytor widoku podzielonego Xamarin.Adroid Designer](media/android-designer-split-view.png)

Aby uzyskać więcej informacji, zobacz [Przyspieszanie sprzętowe w celu uzyskania wydajności emulatora](/xamarin/android/get-started/installation/android-emulator/hardware-acceleration?tabs=vswin)

### <a name="visual-studio-app-center"></a>Visual Studio App Center

**Nowość w wersji 15.5:** Visual Studio App Center,&mdash;która jest teraz ogólnie&mdash;dostępna dla aplikacji android, iOS, macOS i Windows, ma wszystko, czego potrzebujesz do zarządzania cyklem życia aplikacji, w tym automatyczne kompilacje, testowanie na rzeczywistych urządzeniach w chmurze, dystrybucja do testerów wersji beta i sklepów z aplikacjami oraz monitorowanie rzeczywistego użycia za pomocą danych dotyczących awarii i analiz. Aplikacje napisane w językach Objective-C, Swift, Java, C#, Xamarin i React Native są obsługiwane we wszystkich funkcjach.

  ![Środowisko testowe centrum aplikacji programu Visual Studio](media/app-center-test-env.png)

Aby uzyskać więcej informacji, zobacz [Wprowadzenie Centrum aplikacji: tworzenie, testowanie, rozpowszechnianie i monitorowanie aplikacji w blogu w chmurze.](https://blogs.msdn.microsoft.com/vsappcenter/introducing-visual-studio-app-center/)

## <a name="cross-platform-development"></a>Tworzenie aplikacji wieloplatformowych

### <a name="redgate-data-tools"></a>Narzędzia do przekazywania danych

Aby rozszerzyć możliwości Programu DevOps na tworzenie bazy danych programu SQL Server, narzędzia Redgate Data Tools są teraz dostępne w programie Visual Studio.

Dołączone do programu Visual Studio 2017 Enterprise:

* [Redgate ReadyRoll Core](https://www.red-gate.com/products/sql-development/sql-change-automation/?utm_source=microsoft&utm_medium=link&utm_campaign=readyroll&utm_term=docs-newinvs) pomaga tworzyć skrypty migracji, zarządzać zmianami bazy danych za pomocą kontroli źródła i bezpiecznie zautomatyzować wdrożenia zmian bazy danych programu SQL Server wraz ze zmianami aplikacji.
* [Redgate SQL Prompt Core](https://www.red-gate.com/products/sql-development/sql-prompt/?utm_source=microsoft&utm_medium=link&utm_campaign=sqlprompt&utm_term=docs-newinvs) pomaga pisać SQL szybciej i dokładniej za pomocą inteligentnego uzupełniania kodu. Dodatek SQL Prompt pozwala automatycznie uzupełnić bazę danych, obiekty systemowe oraz słowa kluczowe i oferuje sugestie dla kolumn podczas wpisywania. Powoduje to czystsze kodu i mniej błędów, ponieważ nie trzeba pamiętać każdej nazwy kolumny lub aliasu.

Zawiera wszystkie wersje programu Visual Studio 2017:

* [Redgate SQL Search](https://www.red-gate.com/products/sql-development/sql-search/?utm_source=microsoft&utm_medium=link&utm_campaign=sqlsearch&utm_term=docs-newinvs) zwiększa produktywność, pomagając szybko znaleźć fragmenty SQL i obiekty w wielu bazach danych.

Aby dowiedzieć się więcej, zobacz [Redgate Data Tools w programie Visual Studio 2017](https://devblogs.microsoft.com/visualstudio/redgate-data-tools-in-visual-studio-2017/) wpis w blogu.

### <a name="net-core"></a>.NET Core

.NET Core jest implementacją standardu .NET ogólnego przeznaczenia, modułowego, wieloplatformowego i open source i zawiera wiele tych samych interfejsów API co program .NET Framework.

Platforma .NET Core składa się z kilku składników, które obejmują kompilatory zarządzane, środowisko wykonawcze, biblioteki klas podstawowych i wiele modeli aplikacji, takich jak ASP.NET Core. Program .NET Core obsługuje trzy główne systemy operacyjne: Windows, Linux i macOS. Można użyć programu .NET Core w scenariuszach urządzenia, chmury i osadzonych/IoT.

I teraz zawiera obsługę platformy Docker.

**Nowość w wersji 15.3**: Visual Studio 2017 w wersji 15.3 obsługuje program .NET Core 2.0. Korzystanie z platformy .NET Core 2.0 wymaga oddzielnego pobierania i instalowania zestawu .NET Core 2.0 SDK.

Aby uzyskać więcej informacji, zobacz stronę [przewodnika .NET Core.](/dotnet/core/index)

## <a name="games-development"></a>Rozwój gier

### <a name="visual-studio-tools-for-unity"></a>Narzędzia Visual Studio Tools for Unity

W ramach zadania "Tworzenie gier dla jedności" uwzględniliśmy narzędzia ułatwiające tworzenie wieloplatformowych gier 2D i 3D oraz interaktywnych treści. Twórz raz i publikuj na 21 platformach, w tym na wszystkich platformach mobilnych, WebGL, Mac, PC i Linux, w sieci Web lub konsolach za pomocą programu Visual Studio 2017 i Unity 5.6.

Aby uzyskać więcej informacji, zobacz Visual [Studio Tools for Unity](../cross-platform/visual-studio-tools-for-unity.md) strony.

## <a name="ai-development"></a>Rozwój SI

### <a name="visual-studio-tools-for-ai"></a>Visual Studio Tools for AI

**Nowość w wersji 15.5**: Wykorzystaj funkcje zwiększające produktywność programu Visual Studio, aby przyspieszyć innowacje w dziedzinie si. Użyj wbudowanych funkcji edytora kodu, takich jak wyróżnianie składni, IntelliSense i automatyczne formatowanie tekstu. Aplikację uczenia głębokiego można interaktywnie przetestować w środowisku lokalnym przy użyciu debugowania krok po kroku na zmiennych lokalnych i modeli.

  ![Ide uczenia głębokiego](../ai/media/about/ide.png)

Aby uzyskać więcej informacji, zobacz visual [studio narzędzia dla ai](../ai/about-ai-tools.md) stronie.

## <a name="whats-next"></a>Co dalej

Możemy aktualizować Visual Studio 2017 często z nowymi funkcjami, które mogą uczynić swoje środowisko programistyczne jeszcze lepiej. Oto podsumowanie niektórych z naszych najbardziej znaczących aktualizacji, które są w wersji zapoznawczej eksperymentalnej:

* **[Udostępnianie na żywo](https://visualstudio.microsoft.com/services/live-share/)**, nowe narzędzie, które pozwala na udostępnianie bazy kodu i jego kontekst z kolegą z zespołu i uzyskać natychmiastową dwukierunkową współpracę bezpośrednio z poziomu programu Visual Studio. Dzięki usłudze Live Share członek zespołu może czytać, nawigować, edytować i debugować projekt, który został mu udostępniony, i robić to bezproblemowo i bezpiecznie.<br><br>Aby uzyskać więcej informacji, zobacz często zadawane [pytania dotyczące udostępniania na żywo](/visualstudio/liveshare/faq).<br><br>
* **[IntelliCode](https://visualstudio.microsoft.com/services/intellicode/)**, nowa funkcja, która usprawnia tworzenie oprogramowania za pomocą AI, aby zapewnić lepsze uzupełnianie kodu kontekstowe, przewodnik programistów do kodu do wzorców i stylów ich zespołu, znaleźć trudne do złapania problemy z kodem i skupić przeglądy kodu na obszarach, które naprawdę mają znaczenie. <br><br>Aby uzyskać więcej informacji, zobacz często zadawane pytania [dotyczące intellicode](/visualstudio/intellicode/faq).

Chcesz dowiedzieć się więcej o tym, co jeszcze znajduje się w pracach dla programu Visual Studio 2017? Zobacz stronę [mapy drogowej programu Visual Studio.](/visualstudio/productinfo/vs2018-roadmap)

I nie zapomnij sprawdzić naszą najnowszą wersję, [Visual Studio 2019](whats-new-visual-studio-2019.md).

## <a name="contact-us"></a>Skontaktuj się z nami

Dlaczego warto wysyłać opinie do zespołu programu Visual Studio? Ponieważ traktujemy opinie klientów poważnie. To napędza wiele z tego, co robimy.

Jeśli chcesz przedstawić sugestię dotyczącą sposobu, w jaki możemy ulepszyć program Visual Studio lub dowiedzieć się więcej o opcjach pomocy technicznej dotyczącej produktu, zobacz stronę [Wyślij nam opinię.](feedback-options.md)

### <a name="report-a-problem"></a>zgłaszanie problemu

Czasami wiadomość nie wystarczy, aby przekazać pełny wpływ napotkanego problemu. Jeśli wystąpi problem z zawieszaniem się, awarią lub innym problemem z wydajnością, możesz łatwo udostępnić nam kroki ponownego tworzenia i pliki pomocnicze (takie jak zrzuty ekranu oraz pliki śledzenia i zrzutu sterty) za pomocą narzędzia **Zgłoś problem.** Aby uzyskać więcej informacji na temat korzystania z tego narzędzia, zobacz [jak zgłosić problem](how-to-report-a-problem-with-visual-studio.md) strony.

## <a name="see-also"></a>Zobacz też

* [Informacje o wersji programu Visual Studio 2017](/visualstudio/releasenotes/vs2017-relnotes)
* [Co nowego w zestawie Visual Studio 2017 SDK](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md)
* [Co nowego w języku Visual C++](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio)
* [Co nowego w języku C#](/dotnet/csharp/whats-new)
* [Co nowego w Team Foundation Server](/azure/devops/server/whats-new)
* [Co nowego w programie Visual Studio dla komputerów Mac](https://visualstudio.microsoft.com/vs/visual-studio-mac/)
* [Co nowego w programie Visual Studio 2019](whats-new-visual-studio-2019.md)

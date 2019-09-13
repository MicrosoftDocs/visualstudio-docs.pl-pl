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
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 4fd3bde36b81dde254f3447d46bd05ffc41c6cde
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68925911"
---
# <a name="whats-new-in-visual-studio-2017"></a>Co nowego w programie Visual Studio 2017

**Zaktualizowano do programu [wersji 15.9](/visualstudio/releasenotes/vs2017-relnotes?context=visualstudio/default&contextView=vs-2017)**

Chcesz uaktualnić poprzednią wersję programu Visual Studio? Oto, co może być oferowane przez program Visual Studio 2017: Niezrównana produktywność dla każdego dewelopera, każdej aplikacji i dowolnej platformy. Użyj programu Visual Studio 2017 do tworzenia aplikacji dla systemów Android, iOS, Windows, Linux, sieci Web i chmury. Szybko twórz kod, z łatwością debuguj i diagnozuj, często testuj i swobodnie wydawaj. Możesz również rozszerzać funkcjonalność programu Visual Studio oraz go dostosowywać, tworząc własne rozszerzenia. Używaj kontroli wersji, być Agile i wydajnie Współpracuj z tą wersją.

>[!div class="button"]
>[Pobierz program Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

Oto ogólny podsumowanie zmian wprowadzonych od czasu poprzedniej wersji programu Visual Studio 2015:

* **[Definicje podstawowe](#redefined-fundamentals)** . Nowe środowisko instalacji oznacza, że można je instalować szybciej i instalować w razie potrzeby.
* **[Wydajność i produktywność](#performance-and-productivity)** . Firma Microsoft koncentruje się na nowych i nowoczesnych możliwościach deweloperskich, chmurowych i klasycznych. Program Visual Studio jest uruchamiany szybciej, jest bardziej wydajny i zużywa mniej pamięci niż wcześniej.
* **[Tworzenie aplikacji w chmurze przy użyciu platformy Azure](#cloud-app-development-with-azure)** . Wbudowany zestaw narzędzi platformy Azure umożliwia łatwe tworzenie aplikacji w chmurze, które są obsługiwane przez Microsoft Azure. Program Visual Studio ułatwia konfigurowanie, kompilowanie, debugowanie, pakowanie i wdrażanie aplikacji oraz usług na platformie Azure.
* **[Programowanie aplikacji systemu Windows](#windows-app-development)** . Użyj szablonów platformy UWP w programie Visual Studio 2017, aby utworzyć pojedynczy projekt dla wszystkich urządzeń &ndash; z systemem Windows 10, tabletu, telefonu, konsoli Xbox, Hololens, Surface Hub i innych.
* **[Opracowywanie aplikacji mobilnych](#mobile-app-development)** . Wprowadzaj innowacje i uzyskuj wyniki szybko przy użyciu platformy Xamarin, która łączy wymagania dotyczące wielu platform dla urządzeń przenośnych do jednej podstawowej bazy kodu i zestawu umiejętności.
* **[Programowanie dla wielu platform](#cross-platform-development)** . Bezproblemowo dostarcza oprogramowanie do dowolnej platformy dostosowanej. Rozszerzając DevOps procesy, aby SQL Server za pośrednictwem narzędzi Redgate Data Tools i bezpiecznie automatyzować wdrożenia baz danych z programu Visual Studio. Można też używać platformy .NET Core do zapisywania aplikacji i bibliotek, które są uruchamiane niemodyfikowane w systemach operacyjnych Windows, Linux i macOS.
* **[Opracowywanie gier](#games-development)** . Program Visual Studio Tools for Unity (VSTU) można użyć programu Visual Studio tworzyć gry i Edytor skrypty w języku C#, a następnie użyć jej zaawansowany debuger, można znaleźć i naprawić błędy.
* **[Programowanie AI](#ai-development)** . Za pomocą Visual Studio Tools for AI można korzystać z funkcji produktywności programu Visual Studio w celu przyspieszenia innowacji AI. Kompiluj, Testuj i wdrażaj rozwiązania głębokiego uczenia/AI, które bezproblemowo integrują się z Azure Machine Learning w celu zapewnienia niezawodnej obsługi eksperymentów.

> [!NOTE]
> Aby uzyskać pełną listę nowych funkcji i funkcji w programie Visual Studio 2017, zobacz [bieżące informacje o wersji](/visualstudio/releasenotes/vs2017-relnotes?context=visualstudio/default&contextView=vs-2017). Aby uzyskać wgląd w przyszłe oferty funkcji, zobacz informacje o [wersji](/visualstudio/releasenotes/vs2017-preview-relnotes?context=visualstudio/default&contextView=vs-2017)zapoznawczej.

Poniżej przedstawiono bardziej szczegółowe informacje na temat niektórych najbardziej istotnych ulepszeń i nowych funkcji w programie Visual Studio 2017.

## <a name="redefined-fundamentals"></a>Definicje podstawowe

### <a name="a-new-setup-experience"></a>Nowe środowisko instalacji

Program Visual Studio ułatwia i przyspiesza Instalowanie tylko potrzebnych funkcji, gdy będą potrzebne. Ponadto Odinstalowuje również czyste.

Najważniejszym zmianą do uwagi podczas instalowania programu Visual Studio jest jego nowe środowisko konfiguracji. Na karcie **obciążenia** zobaczysz opcje instalacji, które są pogrupowane w celu reprezentowania typowych struktur, języków i platform. Obejmuje ona wszystkie czynności związane z programowaniem C++ aplikacji klasycznych na platformie .NET w systemach Windows, Linux i iOS.

Wybierz potrzebne obciążenia i zmień je w razie potrzeby.

![Okno dialogowe Instalatora programu Visual Studio 2017](../install/media/install-visual-studio-enterprise.png)

Dostępne są również opcje umożliwiające precyzyjne dostosowanie instalacji:

* Chcesz wybrać własne składniki zamiast korzystać z obciążeń? Wybierz kartę **poszczególne składniki** w instalatorze.
* Czy chcesz zainstalować pakiety językowe bez konieczności zmiany opcji języka systemu Windows? Wybierz kartę **pakiety językowe** Instalatora.
* **Nowość w 15,7**: Czy chcesz zmienić lokalizację instalacji programu Visual Studio? Wybierz kartę **Opcje instalacji** w instalatorze.

Aby dowiedzieć się więcej na temat nowego środowiska instalacji, w tym instrukcje krok po kroku, które przeprowadzą Cię przez ten proces, zobacz stronę [Instalowanie programu Visual Studio](../install/install-visual-studio.md) .

### <a name="a-focus-on-accessibility"></a>Skupienie się na ułatwieniach dostępu

**Nowość w 15,3**, wprowadziliśmy ponad 1 700 poprawek do poprawy zgodności między programem Visual Studio i technologiami pomocniczymi używanymi przez wielu klientów. Istnieje wiele scenariuszy, które są bardziej zgodne z czytnikami zawartości ekranu, kompozycjami o dużym kontraście i innymi technologiami pomocniczymi niż kiedykolwiek wcześniej. Narzędzia debugger, Editor i Shell mają również znacznie znaczące ulepszenia.

Aby uzyskać więcej informacji, zobacz wpisy w blogu dotyczące [ulepszeń ułatwień dostępu w programie Visual Studio 2017 w wersji 15,3](https://devblogs.microsoft.com/visualstudio/accessibility-improvements-in-visual-studio-2017-version-15-3/) .

## <a name="performance-and-productivity"></a>Wydajność i produktywność

### <a name="sign-in-across-multiple-accounts"></a>Zaloguj się na wielu kontach

W programie Visual Studio wprowadziliśmy nową usługę tożsamości, która umożliwia udostępnianie kont użytkowników w ramach Team Explorer, narzędzi platformy Azure, Microsoft Store publikowania i nie tylko.

Możesz już się zalogować. Program Visual Studio nie będzie prosił o ponowne zalogowanie co 12 godzin. Aby dowiedzieć się więcej, zobacz wpis w blogu dotyczący mniej informacji dotyczących [logowania w programie Visual Studio](https://devblogs.microsoft.com/visualstudio/fewer-visual-studio-sign-in-prompts/) .

### <a name="start-visual-studio-faster"></a>Szybsze uruchamianie programu Visual Studio

Nowe centrum wydajności programu Visual Studio może pomóc zoptymalizować czas uruchamiania środowiska IDE. Centrum wydajności zawiera listę wszystkich rozszerzeń i okien narzędzi, które mogą spowalniać Uruchamianie środowiska IDE. Można jej użyć, aby zwiększyć wydajność uruchamiania przez określenie, kiedy rozszerzenia zaczynają się lub czy okna narzędzi są otwarte przy uruchamianiu.

### <a name="faster-on-demand-loading-of-extensions"></a>Szybsze ładowanie rozszerzeń na żądanie

Program Visual Studio przenosi swoje rozszerzenia (i współpracuje z rozszerzeniami innych firm), aby załadować je na żądanie, a nie przy uruchamianiu IDE. Chcesz wiedzieć o tym, które rozszerzenia mają wpływ na uruchamianie, ładowanie rozwiązań i wprowadzanie wydajności? Te informacje można znaleźć w temacie **ułatwiają** > **Zarządzanie wydajnością programu Visual Studio**.

  ![Okno dialogowe Opcje w programie Visual Studio 2017](media/vs2017ide-manage-vs-perf.png)

#### <a name="manage-your-extensions-with-roaming-extensions-manager"></a>Zarządzanie rozszerzeniami za pomocą Menedżera rozszerzeń roamingu

W przypadku logowania się do programu Visual Studio łatwiej jest skonfigurować każde środowisko programistyczne przy użyciu ulubionych rozszerzeń. Nowy Menedżer rozszerzenia roamingu śledzi wszystkie ulubione rozszerzenia przez utworzenie zsynchronizowanej listy w chmurze.

Aby wyświetlić listę rozszerzeń w programie Visual Studio, kliknij pozycję **Narzędzia** > **rozszerzenia & aktualizacje**, a następnie kliknij pozycję **Menedżer rozszerzenia roamingu**.

![Visual Studio 2017 — okno dialogowe rozszerzenia i aktualizacje](media/vs2017ide-extensions-and-updates.png)

Menedżer rozszerzenia roamingu śledzi wszystkie instalowane rozszerzenia, ale możesz wybrać, które z nich mają zostać dodane do listy roamingu.

![Visual Studio 2017 — okno dialogowe rozszerzenia i aktualizacje](media/vs2017ide-RoamingExtensionManager.png)

W przypadku korzystania z Menedżera rozszerzenia roamingu na liście istnieją trzy typy ikon:

* ![](media/vs2017ide-roamedicon.png) Mobilny **_dostęp_** do ikony: Rozszerzenie, które jest częścią tej listy roamingu, ale nie jest zainstalowane na tej maszynie.
  (Można je zainstalować przy użyciu przycisku **Pobierz** ).
* ![& Zainstalowana ikona](media/vs2017ide-roamedinstalledicon.png) instalacji z roamingiem **_& zainstalowana_** : Wszystkie rozszerzenia, które są częścią tej listy roamingu i zainstalowane w środowisku deweloperskim.
  (Jeśli zdecydujesz, że nie chcesz korzystać z roamingu, możesz je usunąć za pomocą przycisku **Zatrzymaj roaming** ).
* ![ **_Zainstalowana_** ikona](media/vs2017ide-installedicon.png) instalacji: Wszystkie rozszerzenia, które są zainstalowane w tym środowisku, ale nie są częścią listy roamingu.
  (Rozszerzenia można dodać do listy roaming przy użyciu przycisku **Uruchom roaming** ).

Wszystkie rozszerzenia pobrane po zalogowaniu się zostaną dodane do listy jako zainstalowano **& roamingu**. Rozszerzenie zostanie następnie częścią listy roamingu, co zapewnia dostęp do niego z dowolnego komputera.

### <a name="experience-live-unit-testing"></a>Testowanie jednostkowe na żywo

W Visual Studio Enterprise 2017 testy jednostkowe na żywo umożliwiają dynamiczne wyniki testów jednostkowych i pokrycie kodu w edytorze podczas kodowania. Współpracuje z C# i Visual Basic projekty zarówno dla .NET Framework i .NET Core, jak i obsługuje trzy środowiska testowe MSTest, XUnit i NUnit.

![Live Unit Testing](media/lut-codewindow.png)

Aby uzyskać więcej informacji, zobacz [wprowadzenie Live Unit Testing](../test/live-unit-testing-intro.md). Aby zapoznać się z listą nowych funkcji dodanych w poszczególnych wersjach Visual Studio Enterprise 2017, zobacz [co nowego w programie Live Unit Testing](../test/live-unit-testing-whats-new.md).

### <a name="set-up-a-cicd-pipeline"></a>Konfigurowanie potoku ciągłej integracji/ciągłego dostarczania

#### <a name="automated-testing"></a>Testowanie automatyczne

Testowanie automatyczne jest kluczowym elementem dowolnego potoku DevOps. Pozwala to na spójne i niezawodne testowanie i wydawanie rozwiązań w znacznie krótszych cyklach. Przepływy ciągłej integracji i ciągłego dostarczania mogą pomóc zwiększyć wydajność procesu.

Aby uzyskać więcej informacji o zautomatyzowanych testach, zobacz potok ciągłej integracji/ciągłego wdrażania [w blogu DevOps](https://blogs.msdn.microsoft.com/visualstudioalmrangers/2017/04/20/set-up-a-cicd-pipeline-to-run-automated-tests-efficiently/) .

Aby uzyskać więcej informacji o nowościach w rozszerzeniu [Narzędzia do ciągłego dostarczania dla rozszerzenia Visual Studio](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) DevLabs, zobacz temat [zatwierdzanie z zaufaniem: Wpis w blogu dotyczący jakości](https://devblogs.microsoft.com/visualstudio/committing-with-confidence-getting-code-quality-information-at-commit-time/) czasu zatwierdzenia.

### <a name="visual-studio-ide-enhancements"></a>Ulepszenia środowiska IDE programu Visual Studio

#### <a name="multi-caret-editing"></a>Edycja przy użyciu wielokaretki

**Nowość w 15,8**: Jednoczesne edytowanie wielu lokalizacji w pliku jest teraz łatwe. Zacznij od utworzenia punktów wstawiania i opcji w wielu lokalizacjach w pliku. Następnie użyj funkcji edycji wielokolorowej, aby zmienić tę samą edycję w dwóch lub więcej miejscach w tym samym czasie.

Aby uzyskać więcej informacji, zobacz sekcję [wybór wielu karetki](finding-and-replacing-text.md#multi-caret-selection) na stronie [Znajdowanie i zastępowanie tekstu](finding-and-replacing-text.md) .

#### <a name="keep-keybinding-profiles-consistent"></a>Zachowaj spójne profile powiązanie klawiszy

**Nowość w 15,8**: Teraz można zachować spójność powiązań klawiszy między narzędziami, które mają dwa nowe profile klawiatury: Visual Studio Code i Resharper (Visual Studio). Te schematy można znaleźć w obszarze **Narzędzia** > **Opcje** > **Ogólne** > **Klawiatura** i górne menu rozwijane.

  ![Nowe profile powiązanie klawiszy dla Visual Studio Code i Resharper](media/vs-keyboard-mappings-code-resharper.png)

#### <a name="use-new-refactorings"></a>Użyj nowych refaktoryzacji

Refaktoryzacja to proces ulepszania kodu po jego zapisaniu. Refaktoryzacja zmienia wewnętrzną strukturę kodu bez zmiany jego działania. Często dodawane są nowe refaktoryzacje; Oto kilka z nich:

* Dodaj parametr (z szczegóły)
* Generuj zastąpienia
* Dodaj nazwany argument
* Dodaj sprawdzanie wartości null dla parametrów
* Wstawianie separatorów cyfr do literałów
* Zmień bazę dla literałów liczbowych (na przykład szesnastkowe na Binary)
* Konwertuj przełącznik if-to-switch
* Usuń nieużywaną zmienną

Aby uzyskać więcej informacji, zobacz [szybkie akcje](common-quick-actions.md).

#### <a name="interact-with-git"></a>Korzystanie z narzędzia Git

Podczas pracy z projektem w programie Visual Studio można skonfigurować i szybko zatwierdzić i opublikować swój kod w usłudze git. Repozytoriami git można także zarządzać za pomocą menu kliknięć z przycisków w prawym dolnym rogu IDE.

![Program Visual Studio 2017 współdziała z oknem dialogowym usługi git](media/vsIDE-GitInteraction.png)

#### <a name="experience-improved-navigation-controls"></a>Udoskonalone kontrolki nawigacji

Odświeżono środowisko nawigacji, aby pomóc w uzyskaniu od A do B z większą pewnością i mniejszą liczbą odniesień.

* **Nowość w 15,4**: **Przejdź do definicji** (**Ctrl**+**kliknięcia** lub **F12**) &ndash; użytkownicy myszy mają łatwiejszy sposób, aby przejść do definicji elementu członkowskiego, naciskając klawisz **Ctrl** , a następnie klikając element członkowski. Naciśnięcie klawisza **Ctrl** i umieszczenie kursora nad symbolem kodu spowoduje podkreślenie go i przełączenie go do linku. Aby uzyskać więcej informacji, zobacz sekcję [Przejdź do definicji i wgląd do definicji](go-to-and-peek-definition.md) .

* **Przejdź do implementacji** (**Ctrl**+**F12** )&ndash; przechodzenie z dowolnego typu podstawowego lub składowej do różnych implementacji.

* **Przejdź do wszystkiego** (**Ctrl**+**T** lub **Ctrl**+ )&ndash; przejdź bezpośrednio do dowolnej deklaracji File/Type/member/symbol. Możesz filtrować listę wyników lub użyć składni zapytania (na przykład "f searchTerm" dla plików "t searchTerm" dla typów itp.).

  ![Udoskonalone przechodzenie do wszystkiego](media/vs2017ide-navigation-go-to.png)

* **Znajdź wszystkie odwołania** (**SHIFT**+**F12** )&ndash; za pomocą kolorowania składni można grupować wyniki wyszukiwania wszystkich odwołań według kombinacji projektu, definicji i ścieżki. Możesz również "zablokować" wyniki, aby można było dalej znajdować inne odwołania bez utraty oryginalnych wyników.

  ![Nowe narzędzie Znajdź wszystkie odwołania](media/vs2017ide-find-all-references.png)

* **Wizualizator struktury** &ndash; Kropkowane, szare linie pionowe (prowadnice wcięcia) działają jako dzielnice w kodzie, aby zapewnić kontekst w ramce widoku. Można je rozpoznać z popularnych narzędzi do wydajnej pracy. Można ich używać do wizualizacji i wykrywania bloku kodu w dowolnym momencie bez konieczności przewijania. Umieszczenie kursora nad wierszami powoduje wyświetlenie etykietki narzędzia, która pokazuje otwieranie tego bloku i jego obiektów nadrzędnych. Jest ona dostępna dla wszystkich języków obsługiwanych za pośrednictwem gramatyki textoficer, a także C#Visual Basic i XAML.

  ![Wizualizator struktury programu Visual Studio 2017](media/vsIDE-StructureVisualizer.png)

Aby uzyskać więcej informacji na temat nowych funkcji produktywności, [zobacz Visual Studio 2017: Wpis w blogu dotyczący produktywności, wydajności i partnerów](https://devblogs.microsoft.com/visualstudio/visual-studio-2017-productivity-performance-and-partners/) .

### <a name="visual-c"></a>Visual C++

Zobaczysz kilka ulepszeń w programie Visual Studio, takich jak dystrybuowanie C++ podstawowych wytycznych przy użyciu programu Visual Studio, aktualizowanie kompilatora przez dodanie rozszerzonej obsługi języka C++ c++ 11 i funkcji oraz dodawanie i aktualizowanie funkcji C++ w bibliotece. Ulepszono również wydajność C++ środowiska IDE, obciążeń instalacyjnych i nie tylko.

Ponadto Naprawiono ponad 250 usterek i zgłoszono problemy w kompilatorze i narzędziach, wiele przesłanych przez klientów przez [społeczność deweloperów dla C++ ] (https://developercommunity.visualstudio.com/spaces/62/index.html " C++społeczności deweloperów ").

Aby uzyskać szczegółowe informacje, zobacz stronę [co nowego w wizualizacji C++ w programie Visual 2017](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio) .

### <a name="debugging-and-diagnostics"></a>Debugowanie i Diagnostyka

#### <a name="run-to-click"></a>Uruchom do kliknięcia

Teraz można łatwiej przechodzić w trakcie debugowania bez ustawiania punktu przerwania, który ma zostać zatrzymany w pożądanym wierszu. Po zatrzymaniu w debugerze wystarczy kliknąć ikonę widoczną obok wiersza kodu. Kod zostanie uruchomiony i zatrzymany w tym wierszu przy następnym trafieniu w ścieżce kodu.

![Debugowanie programu Visual Studio 2017 — uruchamianie do kliknięcia](media/vs2017ide-RunToClick.png)

#### <a name="the-new-exception-helper"></a>Nowy pomocnik wyjątków

Nowy pomocnik wyjątków ułatwia wyświetlanie informacji o wyjątkach w skrócie. Informacje są prezentowane w postaci kompaktowej z natychmiastowym dostępem do wyjątków wewnętrznych. Po zdiagnozowaniu NullReferenceException można szybko zobaczyć, co miało prawo null w Pomocniku wyjątków.

![Okno dialogowe nowego pomocnika wyjątków w programie Visual Studio](media/vs2017ide-ExceptionHelper.png)

Aby uzyskać więcej informacji, zobacz wpis w blogu [Korzystanie z nowego pomocnika wyjątków w programie Visual Studio](https://devblogs.microsoft.com/devops/using-the-new-exception-helper-in-visual-studio-15-preview/) .

#### <a name="snapshots-and-intellitrace-step-back"></a>Migawki i IntelliTrace krok po kroku

**Nowość w 15,5**: Krok do tyłu IntelliTrace umożliwia automatyczne utworzenie migawki aplikacji na każdym punkcie przerwania i debuger krok zdarzenia. Zarejestrowane migawek umożliwiają wrócić do poprzednich punktów przerwania lub kroków i wyświetlić stan aplikacji, tak jak w przeszłości. IntelliTrace krok do tyłu pozwalają zaoszczędzić czas podczas mają być wyświetlane poprzedni stan aplikacji, ale nie chcesz ponownie uruchomić debugowanie lub Utwórz ponownie stan żądaną aplikację.

Możesz nawigować i przeglądać migawki przy użyciu przycisków **krok wstecz** i **dalej** na pasku narzędzi **debugowania** . Te przyciski służą do przechodzenia do zdarzeń, które pojawiają się na karcie **zdarzenia** w oknie **Narzędzia diagnostyczne** . Przechodzenie do tyłu lub w przód do zdarzenia automatycznie aktywuje debugowanie historyczne na wybranym zdarzeniu.

![Okno dialogowe nowego pomocnika wyjątków w programie Visual Studio](../debugger/media/intellitrace-step-back-icons-description.png  "Przyciski do tyłu i do przodu")

Aby uzyskać więcej informacji, zobacz stronę [Wyświetlanie migawek przy użyciu IntelliTrace kroku-back](../debugger/view-historical-application-state.md) .

### <a name="containerization"></a>Kontenerach

Kontenery zapewniają zwiększoną gęstość aplikacji i niższe koszty wdrożenia oraz zwiększają produktywność i elastyczność DevOps.

#### <a name="docker-container-tooling"></a>Narzędzia kontenera Docker

**Nowość w 15,5**:

* Program Visual Studio zawiera narzędzia dla kontenerów platformy Docker, które teraz obsługują Wieloetapową wieloetapowe dockerfile, co upraszcza tworzenie zoptymalizowanych obrazów kontenerów.
* Domyślnie program Visual Studio będzie automatycznie ściągać, kompilować i uruchamiać niezbędne obrazy kontenera w tle podczas otwierania projektu obsługującego platformę Docker. Tę opcję można wyłączyć za pomocą ustawienia **Automatycznie uruchom kontenery w tle** w programie Visual Studio.

## <a name="cloud-app-development-with-azure"></a>Programowanie aplikacji w chmurze przy użyciu platformy Azure

### <a name="azure-functions-tools"></a>Narzędzia Azure Functions

W ramach obciążenia "Programowanie platformy Azure" dołączono narzędzia ułatwiające tworzenie usługi Azure Functions przy użyciu wstępnie skompilowanych C# bibliotek klas. Teraz można kompilować, uruchamiać i debugować na lokalnym komputerze deweloperskim, a następnie publikować je bezpośrednio na platformie Azure z poziomu programu Visual Studio.

Aby uzyskać więcej informacji, zobacz stronę [Azure Functions Tools for Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-develop-vs) .

### <a name="debug-live-aspnet-apps-using-snappoints-and-logpoints-in-live-azure-applications"></a>Debuguj aplikacje Live ASP.NET za pomocą punkty przyciągania i punkty rejestrowania w aplikacjach na żywo platformy Azure

**Nowość w 15,5**: Snapshot Debugger wykonuje migawkę aplikacji w środowisku produkcyjnym, gdy interesujący kod jest wykonywany. Aby nakazać debugera, aby utworzyć migawkę, należy ustawić punkty przyciągania i punkty rejestrowania w kodzie. Debuger pozwala zobaczyć dokładnie tego, co poszło, bez wywierania wpływu na ruch z aplikacji produkcyjnej. Rozszerzenie Snapshot Debugger może pomóc w znacznie skrócić czas potrzebny do rozwiązywania problemów występujących w środowiskach produkcyjnych.

Zbieranie migawek jest dostępna dla następujących aplikacji sieci web działające w usłudze Azure App Service:

* Aplikacji ASP.NET uruchomionych w programie .NET Framework 4.6.1 lub nowszej.
* Aplikacje platformy ASP.NET Core uruchomiony w programie .NET Core 2.0 lub nowszych na Windows.

Aby uzyskać więcej informacji, zobacz [debugowanie live ASP.NET Apps przy użyciu punkty przyciągania i punkty rejestrowania](../debugger/debug-live-azure-applications.md).

## <a name="windows-app-development"></a>Tworzenie aplikacji na komputer z systemem Windows

### <a name="universal-windows-platform"></a>Platforma uniwersalna systemu Windows

Platforma uniwersalna systemu Windows (platformy UWP) to platforma aplikacji dla systemu Windows 10. Aplikacje dla platformy UWP można opracowywać przy użyciu tylko jednego zestawu interfejsów API, jednego pakietu aplikacji i jednego sklepu, aby uzyskać dostęp do wszystkich &ndash; urządzeń z systemem Windows 10, tabletów, telefonów, Xbox, Hololens, Surface Hub i innych. Program platformy UWP obsługuje różne rozmiary ekranu i różne modele interakcji, bez względu na to, czy jest to dotyk, mysz, klawiatura, kontroler gier czy pióro. Na początku aplikacji platformy UWP jest dobrym pomysłem, że użytkownicy chcą, aby ich środowiska były mobilne na wszystkich swoich urządzeniach, oraz że chcą korzystać z każdego urządzenia, które jest najbardziej wygodne lub produktywne dla tego zadania.

![Platforma uniwersalna systemu Windows](../cross-platform/media/uwp_coreextensions.png)

&mdash;Wybierz preferowany język programistyczny C#od, Visual Basic C++lub JavaScript&mdash;, aby utworzyć aplikację platforma uniwersalna systemu Windows dla urządzeń z systemem Windows 10. Program Visual Studio 2017 udostępnia szablon aplikacji platformy UWP dla każdego języka, który umożliwia tworzenie pojedynczego projektu dla wszystkich urządzeń. Po zakończeniu pracy możesz utworzyć pakiet aplikacji i przesłać go do Microsoft Store z poziomu programu Visual Studio, aby uzyskać dostęp do aplikacji klientom na dowolnym urządzeniu z systemem Windows 10.

**Nowość w 15,5**: Program Visual Studio 2017 w wersji 15,5 zapewnia najlepszą obsługę zestawu SDK aktualizacji systemu Windows 10 dla twórców (10.0.16299.0). Aktualizacja systemu Windows 10 dla twórców oferuje także wiele ulepszeń dla deweloperów platformy UWP. Poniżej przedstawiono niektóre największe zmiany: 

* **Obsługa .NET Standard 2,0**<br/>Oprócz usprawnionego wdrażania aplikacji Aktualizacja systemu Windows 10 dla twórców jest pierwszą wersją systemu Windows 10, aby zapewnić obsługę .NET Standard 2,0. Efektywnie, [.NET Standard](https://devblogs.microsoft.com/dotnet/introducing-net-standard/) jest implementacją referencyjną biblioteki klas podstawowych, którą można zaimplementować na dowolnej platformie .NET. Celem .NET Standard jest ułatwienie deweloperom platformy .NET udostępniania kodu na dowolnej platformie .NET, w której pracują.
* **Najlepsze zarówno platformy UWP, jak i Win32**<br/>Ulepszono platformę Windows 10 za pomocą [mostka Desktop](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-root) , aby zapewnić lepszą obsługę systemu Windows 10 dla wszystkich deweloperów platformy .NET, niezależnie od tego, czy bieżący fokus to platformy UWP, WPF, Windows Forms czy Xamarin. Nowy typ projektu pakietu aplikacji w programie Visual Studio 2017 w wersji 15,5 umożliwia tworzenie pakietów aplikacji dla platformy WPF lub Windows Forms projektów, podobnie jak w przypadku projektów platformy UWP. Po spakowaniu aplikacji uzyskasz wszystkie korzyści z wdrożenia aplikacji dla systemu Windows 10 i możesz skorzystać z opcji dystrybucji za pośrednictwem Microsoft Store (dla aplikacji konsumenckich) lub Microsoft Store dla firm i edukacji. Ponieważ spakowane aplikacje mają dostęp do całej powierzchni interfejsu API platformy UWP i interfejsów API Win32 na komputerze stacjonarnym, można teraz przeprowadzić modernizację środowiska WPF i Windows Forms aplikacji stopniowo przy użyciu interfejsów API platformy UWP i funkcji systemu Windows 10. Ponadto możesz dołączać składniki Win32 do aplikacji platformy UWP, które są widoczne na pulpicie ze wszystkimi funkcjami Win32.

Aby uzyskać więcej informacji na temat platformy UWP, zobacz stronę [opracowywanie aplikacji dla platforma uniwersalna systemu Windows (platformy UWP)](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md) .

## <a name="mobile-app-development"></a>Opracowywanie aplikacji mobilnych

### <a name="xamarin"></a>Xamarin

W ramach obciążenia "Programowanie aplikacji mobilnych za pomocą platformy .NET" deweloperzy znający C#programy, .NET i Visual Studio mogą dostarczać natywne aplikacje dla systemów Android, iOS i Windows przy użyciu platformy Xamarin. Deweloperzy mogą korzystać z tych samych możliwości i wydajności podczas pracy z platformą Xamarin dla aplikacji mobilnych, w tym do zdalnego debugowania na urządzeniach&mdash;z systemami Android, iOS i Windows bez konieczności uczenia natywnych języków kodowania, takich jak obiektyw-C lub Java.

Aby uzyskać więcej informacji, zobacz stronę [Visual Studio i Xamarin](/xamarin/) .

### <a name="entitlements-editor"></a>Edytor uprawnień

**Nowość w 15,3**: W przypadku potrzeb związanych z programowaniem w systemie iOS dodaliśmy Edytor uprawnień autonomicznych. Zawiera przyjazny dla użytkownika interfejs użytkownika, który można łatwo przeglądać. Aby go uruchomić, kliknij dwukrotnie plik *uprawnień. plist* .

![Edytor uprawnień dla platformy Xamarin](media/xamarin-entitlements-editor.png)

### <a name="visual-studio-tools-for-xamarin"></a>Visual Studio Tools for Xamarin

**Nowość w 15,4**: Platforma Xamarin Live umożliwia deweloperom ciągłe wdrażanie, testowanie i debugowanie swoich aplikacji bezpośrednio na urządzeniach z systemem iOS i Android. Po pobraniu Xamarin Live Player&mdash;dostępnych w sklepie App Store lub na Google Play&mdash;można sparować urządzenie z programem Visual Studio i zrewolucjonizować sposób tworzenia aplikacji mobilnych. Ta funkcja jest teraz zawarta w programie Visual Studio i można ją włączyć, przechodząc do opcji **Narzędzia** > **Opcje** > **Xamarin**  > **Inne** > **Włącz Xamarin Live Player**.

![Animacja Xamarin Live Player para, wdrożenie i tryby edycji na żywo](media/xamarinliveplayer.gif)

### <a name="support-for-google-android-emulator"></a>Obsługa usługi Google Emulator systemu Android

**Nowość w 15,8**: Korzystając z funkcji Hyper-V, można teraz używać usługi firmy Google Emulator systemu Android obok innych technologii opartych na funkcji Hyper-V, takich jak maszyny wirtualne funkcji Hyper-V, narzędzia platformy Docker, Emulator HoloLens i inne. (Ta funkcja wymaga aktualizacji systemu Windows 10 kwiecień 2018 lub nowszej).

![Emulator systemu Google Android w technologiach funkcji Hyper-V](media/xamarin-hyperv-android-emulator.png)

#### <a name="xamarinandroid-designer-split-view-editor"></a>Xamarin. Android Designer — Edytor Split-View

Również **Nowość w 15,8**: Wprowadziliśmy znaczne ulepszenia środowiska projektanta dla platformy Xamarin. Android. Wyróżnienie jest nowym edytorem podzielonym widoku, który umożliwia tworzenie, edytowanie i Podgląd układów w tym samym czasie.

![Edytor zestawu Split-View projektanta platformy Xamarin. Adroid](media/android-designer-split-view.png)

Aby uzyskać więcej informacji, zobacz [przyspieszanie sprzętowe dla wydajności emulatora](/xamarin/android/get-started/installation/android-emulator/hardware-acceleration?tabs=vswin)

### <a name="visual-studio-app-center"></a>Visual Studio App Center

**Nowość w 15,5**: Visual Studio App Center&mdash;, która jest teraz ogólnie dostępna dla aplikacji&mdash;systemów Android, iOS, macOS i Windows, ma wszystko, czego potrzebujesz do zarządzania cyklem życia aplikacji, w tym zautomatyzowanymi kompilacjami, testowaniem na rzeczywistych urządzeniach w chmurze, dystrybucję do testerów wersji beta i sklepów z aplikacjami oraz monitorowania rzeczywistych zastosowań za poorednictwem danych o awarii i analizie. Aplikacje, które są zapisywane w języku "zamierzenia C#-C", Swift, Java, Xamarin i reagują natywnie, są obsługiwane we wszystkich funkcjach.

  ![Środowisko testowe Visual Studio App Center](media/app-center-test-env.png)

Aby uzyskać więcej informacji, zobacz [wprowadzenie App Center: Kompiluj, Testuj, Dystrybuuj i Monitoruj aplikacje w blogu w](https://blogs.msdn.microsoft.com/vsappcenter/introducing-visual-studio-app-center/) chmurze.

## <a name="cross-platform-development"></a>Tworzenie aplikacji wieloplatformowych

### <a name="redgate-data-tools"></a>Narzędzia danych Redgate

Aby zwiększyć możliwości DevOps na SQL Server potrzeby tworzenia baz danych, narzędzia danych Redgate są teraz dostępne w programie Visual Studio.

Uwzględniono w programie Visual Studio 2017 Enterprise:

* [Redgate ReadyRoll Core](http://www.red-gate.com/products/sql-development/readyroll/entrypage/microsoft-and-readyroll?utm_source=microsoft&utm_medium=link&utm_campaign=readyroll&utm_term=docs-newinvs) ułatwia tworzenie skryptów migracji, zarządzanie zmianami bazy danych przy użyciu kontroli źródła i bezpieczne Automatyzowanie wdrożeń SQL Server zmian w bazie danych wraz ze zmianami aplikacji.
* Usługa [Redgate w wierszu polecenia SQL](http://www.red-gate.com/products/sql-development/sql-prompt/entrypage/microsoft-and-sql-prompt?utm_source=microsoft&utm_medium=link&utm_campaign=sqlprompt&utm_term=docs-newinvs) ułatwia szybsze i precyzyjne pisanie kodu SQL za pomocą inteligentnego uzupełniania kodów. Dodatek SQL Prompt pozwala automatycznie uzupełnić bazę danych, obiekty systemowe oraz słowa kluczowe i oferuje sugestie dla kolumn podczas wpisywania. Powoduje to niewielką liczbę błędów, ponieważ nie trzeba pamiętać każdej nazwy kolumny lub aliasu.

Uwzględnione we wszystkich wersjach programu Visual Studio 2017:

* [Redgate Search SQL](http://www.red-gate.com/products/sql-development/sql-search/?utm_source=microsoft&utm_medium=link&utm_campaign=sqlsearch&utm_term=docs-newinvs) zwiększa produktywność, pomagając szybko znaleźć fragmenty i obiekty SQL w wielu bazach danych.

Aby dowiedzieć się więcej, zobacz wpis w blogu [Redgate Data Tools in Visual Studio 2017](https://devblogs.microsoft.com/visualstudio/redgate-data-tools-in-visual-studio-2017/) .

### <a name="net-core"></a>.NET Core

.NET Core to implementacja ogólna, modularna, międzyplatformowa i typu open source .NET Standard i zawiera wiele z tych samych interfejsów API, co .NET Framework.

Platforma .NET Core zawiera kilka składników, takich jak zarządzane kompilatory, środowisko uruchomieniowe, biblioteki klas podstawowych i liczne modele aplikacji, takie jak ASP.NET Core. Platforma .NET Core obsługuje trzy główne systemy operacyjne: Windows, Linux i macOS. Można używać platformy .NET Core w scenariuszach dotyczących urządzeń, chmury i osadzonych/IoT.

Teraz zawiera również obsługę platformy Docker.

**Nowość w 15,3**: Program Visual Studio 2017 w wersji 15,3 obsługuje programowanie na platformie .NET 2,0 Core. Korzystanie z programu .NET Core 2,0 wymaga oddzielnego pobierania i instalowania zestawu SDK programu .NET Core 2,0.

Aby uzyskać więcej informacji, zobacz stronę przewodnika dotyczącego [platformy .NET Core](/dotnet/core/index) .

## <a name="games-development"></a>Programowanie gier

### <a name="visual-studio-tools-for-unity"></a>Narzędzia Visual Studio Tools for Unity

W ramach obciążenia "opracowywanie gier dla środowiska Unity" dołączono narzędzia ułatwiające tworzenie międzyplatformowych aplikacji do tworzenia gier 2D i 3W oraz zawartości interaktywnej. Twórz raz i Publikuj na 21 platformach, w tym wszystkie platformy mobilne, komputery z systemami WebGL, Mac, komputery i Linux, sieci Web lub konsole przy użyciu programu Visual Studio 2017 i aparatu Unity 5,6.

Aby uzyskać więcej informacji, zobacz stronę [Visual Studio Tools for Unity](../cross-platform/visual-studio-tools-for-unity.md) .

## <a name="ai-development"></a>Programowanie AI

### <a name="visual-studio-tools-for-ai"></a>Narzędzia Visual Studio Tools for AI

**Nowość w 15,5**: Korzystaj z funkcji produktywności programu Visual Studio, aby przyspieszyć innowacje AI. Korzystaj z wbudowanych funkcji edytora kodu, takich jak wyróżnianie składni, IntelliSense i formatowanie tekstu. Możesz interaktywnie przetestować aplikację głębokiego uczenia w środowisku lokalnym, używając debugowania krok po kroku dla zmiennych lokalnych i modeli.

  ![Środowisko IDE uczenia głębokiego](../ai/media/about/ide.png)

Aby uzyskać więcej informacji, zobacz stronę [Visual Studio Tools for AI](../ai/about-ai-tools.md) .

## <a name="whats-next"></a>Co dalej

Często aktualizujemy program Visual Studio 2017 dzięki nowym funkcjom, które mogą usprawnić pracę programistyczną. Oto podsumowanie niektórych z naszych najbardziej istotnych aktualizacji, które są w wersji eksperymentalnej:

* **[Live Share](https://visualstudio.microsoft.com/services/live-share/)** , nowe narzędzie, które umożliwia udostępnianie bazy kodu i jej kontekstu członkom zespołu i szybkie współpracę dwukierunkową bezpośrednio z poziomu programu Visual Studio. Za pomocą Live Share, członkowie zespołu mogą odczytywać, nawigować, edytować i debugować projekt, który został Ci udostępniony, a tym samym bezproblemowo i bezpieczniej.<br><br>Aby uzyskać więcej informacji, zobacz [Live Share często zadawanych pytań](/visualstudio/liveshare/faq).<br><br>
* **[Rozszerzenia intellicode](https://visualstudio.microsoft.com/services/intellicode/)** , Nowa funkcja, która rozszerza programowanie oprogramowania przy użyciu systemu AI, aby zapewnić lepsze uzupełnianie kodu z obsługą kontekstu, przewodniki deweloperów do kodu wzorców i stylów ich zespołu, znajdowanie trudnych do przechwycenia problemów z kodem i skupienie się na kodzie Przeglądy dotyczące obszarów, które naprawdę ważne. <br><br>Aby uzyskać więcej informacji, zobacz [często zadawane pytania](/visualstudio/intellicode/faq)dotyczące usługi rozszerzenia intellicode.

Chcesz dowiedzieć się więcej na temat tego, co jeszcze znajduje się w programie Works dla programu Visual Studio 2017? Zobacz stronę z [planem programu Visual Studio](/visualstudio/productinfo/vs2018-roadmap) .

Nie zapomnij zaewidencjonować naszej najnowszej wersji [programu Visual Studio 2019](whats-new-visual-studio-2019.md).

## <a name="contact-us"></a>Skontaktuj się z nami

Dlaczego warto wysłać opinię do zespołu usługi Visual Studio? Ponieważ traktujemy opinie naszych użytkowników bardzo poważnie. To wszystko, co robimy.

Jeśli chcesz dowiedzieć się, jak możemy ulepszyć program Visual Studio, lub Dowiedz się więcej o opcjach pomocy technicznej, zobacz stronę [Prześlij nam opinię](feedback-options.md) .

### <a name="report-a-problem"></a>zgłaszanie problemu

Czasami komunikat jest zbyt mały, aby przekazać pełny wpływ napotkanego problemu. W przypadku wystąpienia zawieszenia, awarii lub innych problemów z wydajnością można łatwo udostępnić Odtwórz kroki i pliki pomocnicze (takie jak zrzuty ekranu, pliki śledzenia i zrzutu sterty) przy użyciu narzędzia **Zgłoś problem** . Aby uzyskać więcej informacji na temat korzystania z tego narzędzia, zobacz stronę [Jak zgłosić problem](how-to-report-a-problem-with-visual-studio.md) .

## <a name="see-also"></a>Zobacz także

* [Informacje o wersji programu Visual Studio 2017](/visualstudio/releasenotes/vs2017-relnotes)
* [Co nowego w zestawie Visual Studio 2017 SDK](/visualstudio/extensibility/what-s-new-in-the-visual-studio-2017-sdk)
* [Co nowego w wizualizacjiC++](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio)
* [Co nowego w języku C#](/dotnet/csharp/whats-new)
* [Co nowego w Team Foundation Server](/tfs/server/whats-new?view=vsts)
* [Co nowego w Visual Studio dla komputerów Mac](https://visualstudio.microsoft.com/vs/visual-studio-mac/)
* [Co nowego w programie Visual Studio 2019](whats-new-visual-studio-2019.md)

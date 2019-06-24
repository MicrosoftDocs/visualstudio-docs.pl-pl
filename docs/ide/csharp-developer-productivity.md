---
title: Zwiększ wydajność pracy podczas tworzenia aplikacji .NET
description: Przegląd Nawigacja, analizy kodu jednostki testowania i inne funkcje ułatwiające pisanie lepiej kodu platformy .NET szybciej.
author: kuhlenh
ms.author: gewarren
manager: jillfra
ms.date: 04/25/2019
ms.topic: conceptual
helpviewer_keywords:
- editor
ms.workload:
- dotnet
ms.openlocfilehash: bd36b75f3df640df0e1910fb3a7a52d17c37d30f
ms.sourcegitcommit: 7eb2fb21805d92f085126f3a820ac274f2216b4e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/22/2019
ms.locfileid: "67328776"
---
# <a name="visual-studio-productivity-guide-for-c-developers"></a>Przewodnik dotyczący programu Visual Studio zwiększa produktywność C# deweloperów

Dowiedz się, jak Visual Studio zwiększa wydajność deweloperów niż kiedykolwiek wcześniej. Skorzystaj z zalet naszej wydajność i produktywność ulepszenia, takie jak nawigacja do dekompilowanych zestawów, nazwa zmiennej sugestie, podczas wpisywania widok hierarchii w **Eksplorator testów**, przejdź do wszystkich (**Ctrl** + **T**) przejdź do pliku/typu/elementu członkowskiego/symbolu deklaracji, inteligentnej **pomocnika wyjątków**, konfiguracja stylu kodu i wymuszania i wiele operacji refaktoryzacji i kodu poprawki.

## <a name="im-used-to-keyboard-shortcuts-from-a-different-editor"></a>Z przyzwyczajenia używam skróty klawiaturowe od innego edytora

::: moniker range="vs-2017"

**Nowość w programie Visual Studio 2017 w wersji 15.8**

::: moniker-end

Jeśli podchodzisz z innego środowiska IDE lub środowisko programistyczne, należy zmienić schemat klawiatury do *programu Visual Studio Code* lub *ReSharper (Visual Studio)* :

![Schematy klawiatury programu Visual Studio](../ide/media/VS2017Guide-Keyboard.png)

Niektóre rozszerzenia oferują również schematy klawiatury:

- [Klawisze dostępu dla programu Visual Studio (ReSharper/IntelliJ)](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.HotKeys)
- [Emulacja emacs](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.EmacsEmulation)
- [VSVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)

Dostępne są następujące popularne skróty programu Visual Studio:

| Skrót (wszystkie profile) | Polecenie | Opis |
|-|-|-|
| **CTRL**+**T** | Przejdź do wszystkich | Przejdź do pliku, typu, składowej lub deklaracji symbolu |
| **F12** (również **Ctrl**+**kliknij**) | Przejdź do definicji | Przejdź do której jest zdefiniowany symbol |
| **Ctrl**+**F12** | Przejdź do implementacji | Przechodzenie z typem bazowym lub elementu członkowskiego do jej różnych implementacji |
| **SHIFT**+**F12** | Znajdź wszystkie odwołania | Zobacz wszystkie symboli lub literału odwołania |
| **Ctrl**+ **.** (również **Alt**+**wprowadź** w profilu C#) | Szybkie akcje i operacje refaktoryzacji | Zobacz, jaki kod poprawki, akcje generowania kodu, refaktoryzacji lub innych szybkie akcje są dostępne na wybór pozycji lub kod kursora |
| **Ctrl**+**D** | Duplikuj wiersz | Duplikuje wiersz kodu, w którym znajduje się kursor (dostępne w **programu Visual Studio 2017 w wersji 15.6** i nowsze) |
| **Shift**+**Alt**+ **+** / **-** | Rozwijania/zwijania zaznaczenia | Zwiększa lub zmniejsza bieżące zaznaczenie w edytorze (dostępne w **programu Visual Studio 2017 w wersji 15.5** i nowsze) |
| **SHIFT** + **Alt** +  **.** | Wstaw dalej pasującego karetki | Dodaje zaznaczenia i karetki w następnej lokalizacji, która pasuje do bieżącego zaznaczenia (dostępne w **Visual Studio 2017 w wersji 15.8** i nowsze) |
| **CTRL**+**funkcji pytania i odpowiedzi** | Wyszukaj | Wyszukaj wszystkie ustawienia programu Visual Studio |
| **F5** | Rozpocznij debugowanie | Rozpocznij debugowanie aplikacji |
| **Ctrl**+**F5** | Uruchom bez debugowania | Uruchamianie aplikacji lokalnie bez debugowania |
| **CTRL**+**K**,**D** (profil domyślny) lub **Ctrl**+**E**,**D**  (Profilu w języku C#) | Formatuj dokument | Czyści formatowanie naruszeń w pliku na podstawie nowego wiersza, odstępy i ustawienia wcięć |
| **CTRL**+ **\\** ,**Ctrl**+**E** (profil domyślny) lub **Ctrl** + **W**,**E** (profilu w języku C#) | Wyświetl listę błędów | Zobacz wszystkie błędy w dokumencie, projekt lub rozwiązanie |
| **Alt** + **PgUp/PgDn** | Przejdź do następnego/poprzedniego wydania | Przejdź do poprzedniego/dalej błąd, ostrzeżenie, sugestii w dokumencie (dostępne w **Visual Studio 2017 w wersji 15.8** i nowsze) |
| **CTRL**+**K**, **/** | Przełącz jednowierszowego komentarza lub usuń znaczniki komentarza | To polecenie dodaje lub usuwa pojedynczy wiersz komentarza w zależności od tego, czy zaznaczenie jest już oznaczone jako |
| **Ctrl**+**Shift**+ **/** | Przełącz blok komentarza lub usuń znaczniki komentarza | To polecenie dodaje lub usuwa blokowania komentarze, w zależności od wybranego |

> [!NOTE]
> Niektóre rozszerzenia unbind powiązania klawiszy programu Visual Studio domyślną. Aby użyć poleceń powyżej, Przywróć usługi powiązania klawiszy programu Visual Studio domyślne, przechodząc do **narzędzia** > **Import i eksport ustawień** > **Resetuj wszystkie ustawienia**  lub **narzędzia** > **opcje** > **klawiatury** > **resetowania**.

Aby uzyskać więcej informacji na temat poleceń i skrótów klawiaturowych, zobacz [skróty wydajności](../ide/productivity-shortcuts.md) i [skróty klawiaturowe popularnych](default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md).

## <a name="navigate-quickly-to-files-or-types"></a>Szybko przechodzić do plików lub typów

Program Visual Studio zawiera funkcję o nazwie **przejdź do wszystkich** (**Ctrl**+**T**). **Przejdź do wszystkich** pozwala na szybkie przejście do pliku, typu, składowej lub deklaracji symbolu.

- Zmień lokalizację tego paska wyszukiwania lub wyłącz podgląd na żywo nawigacji za pomocą **koło zębate** ikony.
- Filtrowanie wyników, takich jak przy użyciu składni `t mytype`.
- Ograniczyć wyszukiwanie do bieżącego dokumentu.
- Pisane dopasowania wielkości liter jest obsługiwane.

![Przejdź do wszystkich w programie Visual Studio](../ide/media/VS2017Guide-go-to-all.png)

## <a name="enforce-code-style-rules"></a>Wymuszanie reguł stylu kodu

Można użyć pliku EditorConfig skodyfikowanie Konwencji kodowania i ich podróży z źródła.

![Wymuszanie stylu kodu w programie Visual Studio](../ide/media/VSGuide_CodeStyle.png)

- Dodaj domyślną lub. Styl NET EditorConfig plik do projektu, wybierając **Dodaj** > **nowy element**. W **Dodaj nowy element** okno dialogowe, wyszukaj "editorconfig". Wybierz jedną z **editorconfig pliku** elementu szablony, a następnie wybierz **Dodaj**.

   ![Szablony elementów polecenia EditorConfig w programie Visual Studio](media/editorconfig-item-templates.png)

::: moniker range=">=vs-2019"

- Automatycznie twórz *.editorconfig* ustawienia stylu kodu w oparciu o plik **narzędzia** > **opcje** > **tekstu Edytor** > **C#** > **styl kodu**.

   ![Generowanie pliku .editorconfig z ustawień w 2019 programu VS](media/vs-2019/generate-editorconfig-file.png)

::: moniker-end

- [Funkcja wnioskowania kodu](/visualstudio/intellicode/code-style-inference) z IntelliCode dla programu Visual Studio wnioskuje style kodu z istniejącego kodu. Następnie tworzy pusty plik wtyczki EditorConfig za pomocą preferencji stylu kodu już zdefiniowane.

Zapoznaj się z [opcjami Konwencji kodowania .NET](editorconfig-code-style-settings-reference.md) dokumentacji zawiera również przykład całego pliku EditorConfig.

::: moniker range=">=vs-2019"

## <a name="code-cleanup"></a>Oczyszczanie kodu

Program Visual Studio oferuje na żądanie formatowania pliku kodu, w tym preferencji stylu kodu, w ramach **oczyszczania kodu** funkcji. Aby uruchomić kod czyszczenia, kliknij ikonę miotła w dolnej części edytora lub naciśnij klawisz **Ctrl**+**K**, **Ctrl**+**E**.

![Przycisk Wyczyść kod w Visual Studio 2019 r.](media/execute-code-cleanup.png)

Można również uruchomić oczyszczania kodu dla całego projektu lub rozwiązania. Kliknij prawym przyciskiem myszy nazwę projektu lub rozwiązania w **Eksploratora rozwiązań**, wybierz opcję **analizy i oczyszczania kodu**, a następnie wybierz **Uruchom oczyszczanie kodu**.

![Uruchamianie czyszczenia kodu dla całego projektu lub rozwiązania](media/run-code-cleanup-project-solution.png)

Oprócz formatowania pliku dla miejsca do magazynowania, wcięcia, masę, **oczyszczania kodu** dotyczy także style zaznaczonego kodu. Preferencje dotyczące każdego stylu kodu są odczytywane z [pliku EditorConfig](code-styles-and-code-cleanup.md#code-styles-in-editorconfig-files), jeśli nie masz projektu lub z [ustawienia stylu kodu](code-styles-and-code-cleanup.md#code-styles-in-the-options-dialog-box) w **opcje** okno dialogowe.

::: moniker-end

## <a name="refactorings-and-code-fixes"></a>Poprawki refaktoryzacji i kodu

Program Visual Studio jest dostarczany z wiele operacji refaktoryzacji, akcji generowania kodu i poprawek kodu. Czerwone faliste linie reprezentującego błędy, zielone symbole reprezentują ostrzeżenia i trzy kropki znajdujące się szare reprezentują sugestie kodu. Poprawki kodu dostępu, można przez kliknięcie żarówki lub ikonę śrubokręt lub naciskając **Ctrl**+ **.** lub **Alt**+**wprowadź**. Każda poprawka jest powiązana z okno podglądu, który pokazuje różnice kodu na żywo, sposobu działania poprawki.

Popularne szybkich poprawek i operacje refaktoryzacji obejmują:

- Zmień nazwę
- Wyodrębnij metodę
- Zmiana sygnatury metody
- Generowanie konstruktora
- Generuj metodę
- Przeniesienie typu do pliku
- Dodaj sprawdzanie wartości Null
- Dodaj parametr
- Usuń niepotrzebne użycia
- Pętla foreach do zapytań LINQ lub metoda LINQ
- Obudowach elementów członkowskich

Aby uzyskać więcej informacji, zobacz [funkcjom generowania kodu](code-generation-in-visual-studio.md).

Możesz [zainstalować analizatory FxCop analizujące kod](../code-quality/install-fxcop-analyzers.md) do problemów z kodem flagi. Ewentualnie zapisu własnych refaktoryzacji lub kod naprawy w [analizatorów Roslyn](https://github.com/dotnet/roslyn/wiki/Getting-Started-Writing-a-Custom-Analyzer-&-Code-Fix).

Kilka członków społeczności napisano bezpłatnych rozszerzeń kontroli dodatkowego kodu:

- [Roslynator](https://marketplace.visualstudio.com/items?itemName=josefpihrt.Roslynator2017)
- [SonarLint for Visual Studio](https://marketplace.visualstudio.com/items?itemName=SonarSource.SonarLintforVisualStudio2017)
- [StyleCopAnalyzers](https://www.nuget.org/packages/stylecop.analyzers/)
- [CodeCracker](https://www.nuget.org/packages/codecracker.CSharp/)

![Refaktoryzacje w programie Visual Studio](../ide/media/VSGuide_CodeAnalysis.png)

## <a name="find-usages-go-to-implementation-and-navigate-to-decompiled-assemblies"></a>Znajdź użycia, przejdź do implementacji i przejdź do Dekompilowanych zestawów

Program Visual Studio oferuje wiele funkcji, aby pomóc wyszukiwanie i [Nawiguj po kodzie](../ide/navigating-code.md).

| Funkcja | Skrót | Szczegóły/ulepszeń |
|- | - | -|
| Znajdź wszystkie odwołania | **SHIFT**+**F12**| Wyniki są wyróżnione kolorem i mogą być grupowane według projektu, definicji i typ odwołania, takich jak Odczyt lub zapis. Można również "zablokować" wyników. |
| Przejdź do implementacji | **Ctrl**+**F12** | Przejdź do definicji można używać na `override` — słowo kluczowe, aby przejść do zgodnym z przesłoniętą składową |
| Przejdź do definicji | **F12** lub **Ctrl**+**kliknij**| Naciśnij klawisz **Ctrl** podczas klikania, aby przejść do definicji |
| Zobacz definicję | **ALT**+**F12** | Wbudowany view definicji |
| Wizualizator struktury | Szare, kropkowana — linie między nawiasy klamrowe | Po wskazaniu wskaźnikiem, aby zobaczyć strukturę kodu |
| Nawigacja do dekompilowanych zestawów | **F12** lub **Ctrl**+**kliknij** | Przejdź do źródła zewnętrznego (decompiled przy użyciu narzędzia do dekompilacji) poprzez włączenie funkcji: **Narzędzia** > **opcje** > **edytora tekstów**  >  **C#**  >   **Zaawansowane** > **Włącz nawigację do dekompilowanych źródeł**. |

![Przejdź do wszystkich i Znajdź wszystkie odwołania](../ide/media/VSIDE_Productivity_Navigation.png)

## <a name="improved-intellisense"></a>Ulepszona funkcja IntelliSense

Użyj IntelliCode dla programu Visual Studio, aby pobrać [uzupełnianie kodu oparte na kontekście](/visualstudio/intellicode/intellicode-visual-studio) zamiast po prostu uzyskać alfabetyczną listę. Możesz również uczyć [modelu niestandardowego IntelliSense](/visualstudio/intellicode/custom-model-faq) oparte na bibliotekach specyficznego dla domeny.

## <a name="unit-testing"></a>Testowanie jednostek

Począwszy od programu Visual Studio 2017, istnieją liczne ulepszenia dotyczące testowania środowiska. Możesz przetestować przy użyciu MSTest w wersji 1, MSTest w wersji 2, NUnit oraz XUnit środowisk testowych.

- **Eksplorator testów** odnajdywanie testów jest szybkie.

- Organizowanie testów w **Eksplorator testów** z *hierarchiczne sortowanie*.

   ![Widok hierarchii w Eksploratorze tekstu w programie Visual Studio](../ide/media/VSGuide_Testing.png)

- [Testowanie jednostek na żywo](../test/live-unit-testing.md) stale uruchamia testy, których dotyczą zmiany kodu i aktualizuje wbudowanego edytora ikon z informacją, stan testów. Uwzględnić lub wykluczyć określonych testów lub testowanie projektów z zestawu testów na żywo. (Tylko wersja programu visual Studio Enterprise).

## <a name="debugging"></a>Debugowanie

Oto niektóre z możliwości debugowania programu Visual Studio:

::: moniker range=">=vs-2019"

- Możliwość wyszukiwania ciągu w ramach **Obejrzyj**, **Autos**, i **lokalne** systemu windows.
- *Uruchom do kliknięcia*, pozwalającej umieść obok wiersza kodu, osiągnięty zieloną ikonę "play", który pojawia się i uruchomić program, aż do osiągnięcia tego wiersza.
- **Pomocnika wyjątków**, która umieszcza najważniejsze informacje na najwyższym poziomie w oknie dialogowym, na przykład zmienna, która jest `null` w `NullReferenceException`.
- [Krok ponownie debugowanie](../debugger/view-historical-application-state.md), który umożliwia wrócić do poprzednich punktów przerwania lub kroków i wyświetlić stan aplikacji, tak jak w przeszłości.
- [Debugowanie migawki](/azure/application-insights/app-insights-snapshot-debugger), który umożliwia badanie stanu aplikacji internetowej na żywo w tej chwili Wystąpił wyjątek (musi być na platformie Azure).

::: moniker-end

::: moniker range="vs-2017"

- *Uruchom do kliknięcia*, pozwalającej umieść obok wiersza kodu, osiągnięty zieloną ikonę "play", który pojawia się i uruchomić program, aż do osiągnięcia tego wiersza.
- **Pomocnika wyjątków**, która umieszcza najważniejsze informacje na najwyższym poziomie w oknie dialogowym, na przykład zmienna, która jest `null` w `NullReferenceException`.
- [Krok ponownie debugowanie](../debugger/view-historical-application-state.md), który umożliwia wrócić do poprzednich punktów przerwania lub kroków i wyświetlić stan aplikacji, tak jak w przeszłości.
- [Debugowanie migawki](/azure/application-insights/app-insights-snapshot-debugger), który umożliwia badanie stanu aplikacji internetowej na żywo w tej chwili Wystąpił wyjątek (musi być na platformie Azure).

::: moniker-end

![Pomocnik wyjątków w programie Visual Studio](../ide/media/VSGuide_Debugging.png)

## <a name="version-control"></a>Kontrola wersji

Git lub TFVC służy do przechowywania i aktualizowania kodu w programie Visual Studio.

::: moniker range=">=vs-2019"

- Zainstaluj [żądań ściągnięcia dla programu Visual Studio](https://marketplace.visualstudio.com/items?itemName=vsideversioncontrolmsft.pr4vs) do tworzenia, przejrzyj, zapoznaj się z i uruchomić żądania ściągnięcia bez opuszczania programu Visual Studio.

::: moniker-end

- Organizowanie lokalnych zmian w [Team Explorer](reference/team-explorer-reference.md) i umożliwia śledzenie oczekujące zatwierdzenia i zmiany na pasku stanu.

- Konfigurowanie ciągłej integracji i ciągłego dostarczania dla projektów programu ASP.NET w programie Visual Studio za pomocą [narzędzi Continuous delivery tools for Visual Studio](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) rozszerzenia.

![Kontrola źródła w programie Visual Studio](../ide/media/VSIDE_Productivity_SourceControl.png)

## <a name="what-other-features-should-i-know-about"></a>Jakie inne funkcje wiedzieć o

Poniżej przedstawiono listę funkcji edytora i produktywności, aby wprowadzić bardziej wydajne pisanie kodu. Niektóre funkcje mogą muszą być włączone, ponieważ są one wyłączone domyślnie (może indeksie rzeczy na komputerze, to kontrowersyjny lub są obecnie eksperymentalne).

| Funkcja | Szczegóły | Jak włączyć |
|-|-|-|
| Zlokalizuj plik w Eksploratorze rozwiązań | Wyróżnia aktywnego pliku w **Eksploratora rozwiązań** | **Narzędzia** > **opcje** > **projekty i rozwiązania** > **Śledź aktywny element w Eksploratorze rozwiązań** |
| Dodaj dyrektywy Using dla typów odwołań do zestawów i pakietów NuGet | Pokazuje błąd ikona żarówki z poprawki kodu, aby zainstalować pakiet NuGet dla typu bez odwołań | **Narzędzia** > **opcje** > **edytora tekstów** > **C#**  > **zaawansowane**   >  **Sugeruj dyrektywy Using dla typów w zestawach referencyjnych** i **Sugeruj dyrektywy Using dla typów w pakietach NuGet** |
| Włączanie pełnej analizy rozwiązania | Zobacz wszystkie błędy w rozwiązaniu w **lista błędów** | **Narzędzia** > **opcje** > **edytora tekstów** > **C#**  > **zaawansowane**   >  **Włączanie pełnej analizy rozwiązania** |
| Włącz nawigację do dekompilowanych źródeł | Zezwalaj na przechodzenie do definicji na typy/członków ze źródeł zewnętrznych i użyj decompiler użyciu narzędzia do dekompilacji do wyświetlenia treści metod | **Narzędzia** > **opcje** > **edytora tekstów** > **C#**  > **zaawansowane**   >  **Włącz nawigację do dekompilowanych źródeł** |
| Tryb uzupełniania/sugestii | Zmienia zachowanie uzupełnianie przez funkcję IntelliSense. Deweloperom tła IntelliJ zwykle użyć innych niż domyślne ustawień w tym miejscu. | **Menu** > **Edytuj** > **IntelliSense** > **Przełącz tryb uzupełniania** |
| [Funkcja CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) | Wyświetla kod informacje i zmieniać historię w edytorze. (Formant CodeLens źródła wskaźniki nie są dostępne w programie Visual Studio Community edition.) | **Narzędzia** > **opcje** > **edytora tekstów** > **wszystkie języki**  >   **Funkcja CodeLens** |
| [Fragmenty kodu](../ide/visual-csharp-code-snippets.md) | Pomoc namiastki wspólnej standardowy kod | Wpisz nazwy fragmentu kodu i naciśnij klawisz **kartę** dwa razy. |

---
title: Zwiększ produktywność w zakresie rozwoju platformy .NET
description: Omówienie nawigacji, analizy kodu, testowania jednostek i innych funkcji, które ułatwiają szybsze pisanie kodu platformy .NET.
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.date: 11/21/2019
ms.topic: conceptual
helpviewer_keywords:
- editor
ms.workload:
- dotnet
ms.openlocfilehash: 0aa8e19f2be78671587dd1d9bc6254306c82a78c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75567505"
---
# <a name="visual-studio-productivity-guide-for-c-developers"></a>Przewodnik po produktywności programu Visual Studio dla deweloperów języka C#

Dowiedz się, jak program Visual Studio sprawia, że deweloperzy są bardziej produktywni niż kiedykolwiek wcześniej. Skorzystaj z naszych ulepszeń wydajności i produktywności, takich jak nawigacja do dekompilowanych zestawów, sugestie nazw zmiennych podczas pisania, widok hierarchii w **Eksploratorze testów,** Przejdź do wszystkich **(Ctrl**+**T**), aby przejść do deklaracji plików/typu/elementu członkowskiego/symbolu, inteligentny **pomocnik wyjątków,** konfiguracja i wymuszanie stylu kodu oraz wiele refaktoryzacji i poprawek kodu.

## <a name="im-used-to-keyboard-shortcuts-from-a-different-editor"></a>Używam skrótów klawiaturowych z innego edytora

::: moniker range="vs-2017"

**Nowość w programie Visual Studio 2017 w wersji 15.8**

::: moniker-end

Jeśli pochodzisz z innego środowiska IDE lub kodowania, możesz zmienić schemat klawiatury na *Visual Studio Code* lub *ReSharper (Visual Studio)*:

![Schematy klawiatury w programie Visual Studio](../ide/media/VS2017Guide-Keyboard.png)

Niektóre rozszerzenia oferują również schematy klawiatury:

- [Klawisze skrótów dla programu Visual Studio (ReSharper/IntelliJ)](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.HotKeys)
- [Emulacja Emacsa](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.EmacsEmulation)
- [vsvim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)

Poniżej znajdują się popularne skróty programu Visual Studio:

| Skrót (wszystkie profile) | Polecenie | Opis |
|-|-|-|
| **Ctrl**+**T (ctrl t)** | Przejdź do wszystkich | Przechodzenie do dowolnego pliku, typu, elementu członkowskiego lub deklaracji symbolu |
| **F12** (również **Ctrl**+**Click**) | Przejdź do definicji | Przechodzenie do miejsca zdefiniowanego symbolu |
| **Ctrl**+**F12** | Przejdź do implementacji | Przechodzenie z typu podstawowego lub elementu członkowskiego do jego różnych implementacji |
| **Przesunięcie**+**F12** | Znajdź wszystkie odwołania | Zobacz wszystkie odniesienia do symboli lub literału |
| **Alt**+**Strona główna** | Polecenie Go To Base (Przejdź do podstawy) | Poruszanie się w górę łańcucha dziedziczenia |
| **Ctrl**+**.** (również **Alt**+**Enter** w profilu C#) | Szybkie akcje i operacje refaktoryzacji | Zobacz, jakie poprawki kodu, akcje generowania kodu, refaktoryzowania lub inne szybkie akcje są dostępne w pozycji kursora lub wyborze kodu |
| **Ctrl**+**D** | Zduplikowany wiersz | Powiela wiersz kodu, w który znajduje się kursor (dostępny w **programie Visual Studio 2017 w wersji 15.6 i nowszej)** |
| **Klawisz Shift**+**Alt**+**+**/**-** | Rozwiń/Wybór kontraktu | Rozszerza lub zawiera umowy bieżącego wyboru w edytorze (dostępne w **programie Visual Studio 2017 w wersji 15.5** i nowszej) |
| **Shift** + **Alt** + **.** | Wstaw następną pasującą cieszkę | Dodaje zaznaczenie i cieszę w następnej lokalizacji, która pasuje do bieżącego zaznaczenia (dostępne w **programie Visual Studio 2017 w wersji 15.8** i nowszej) |
| **Ctrl**+**Q** | Wyszukiwanie | Wyszukiwanie wszystkich ustawień programu Visual Studio |
| **F5** | Rozpocznij debugowanie | Rozpoczynanie debugowania aplikacji |
| **Ctrl**+**F5** | Uruchamianie bez debugowania | Uruchamianie aplikacji lokalnie bez debugowania |
| **Ctrl**+**K**,**D** (profil domyślny) lub **Ctrl**+**E**,**D** (profil C#) | Formatuj dokument | Czyści naruszenia formatowania w pliku na podstawie ustawień nowego początku, odstępów i wc. |
| **Ctrl**+**\\**,**Ctrl**+**E** (profil domyślny) lub **Ctrl**+**W**,**E** (profil C#) | Wyświetl listę błędów | Wyświetlanie wszystkich błędów w dokumencie, projekcie lub rozwiązaniu |
| **Alt** + **PgUp/PgDn** | Przejdź do następnego/poprzedniego wydania | Przejdź do poprzedniego/następnego błędu, ostrzeżenia, sugestii w dokumencie (dostępnego w **programie Visual Studio 2017 w wersji 15.8** i nowszych) |
| **Ctrl**+**K**,**/** | Przełączanie komentarza/odkomentowywać jednowierszowe | To polecenie dodaje lub usuwa komentarz pojedynczego wiersza w zależności od tego, czy wybór jest już skomentowany |
| **Ctrl**+**Przesunięcie** ctrl+**/** | Przełączanie komentarza/odkomentowywać blok | To polecenie dodaje lub usuwa komentarze bloków w zależności od tego, co zostało wybrane |

> [!NOTE]
> Niektóre rozszerzenia odłączają domyślne powiązania kluczy programu Visual Studio. Aby użyć powyższych poleceń, przywróć powiązania klawiszy do ustawień domyślnych programu Visual Studio, przechodząc do **pozycji Ustawienia** > **importowania i eksportowania** > Narzędzia**Resetuj wszystkie ustawienia** lub**Opcje** >  **narzędzi** > **Resetowanie****klawiatury** > .

Aby uzyskać więcej informacji na temat skrótów klawiaturowych i poleceń, zobacz [Skróty zwiększające produktywność](../ide/productivity-shortcuts.md) i [Popularne skróty klawiaturowe](default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md).

## <a name="navigate-quickly-to-files-or-types"></a>Szybkie przechodzenie do plików lub typów

Visual Studio ma funkcję o nazwie **Przejdź do wszystkich** (**Ctrl**+**T**). **Przejdź do wszystkich** umożliwia szybkie przejście do dowolnego pliku, typu, elementu członkowskiego lub deklaracji symbolu.

- Zmień lokalizację tego paska wyszukiwania lub wyłącz podgląd nawigacji na żywo za pomocą ikony **koła zębatego.**
- Filtrowanie wyników przy użyciu `t mytype`składni, takich jak .
- Zakres wyszukiwania tylko do bieżącego dokumentu.
- Obsługa dopasowywania przypadku wielbłąda jest obsługiwana.

![Przejdź do wszystkich w programie Visual Studio](../ide/media/VS2017Guide-go-to-all.png)

## <a name="enforce-code-style-rules"></a>Wymuszanie reguł stylu kodu

Można użyć editorconfig pliku do kodyfikacji konwencji kodowania i ich podróży ze źródłem.

![Wymuszanie stylu kodu w programie Visual Studio](../ide/media/VSGuide_CodeStyle.png)

- Dodaj domyślny lub . Net-style EditorConfig pliku do projektu, wybierając pozycję **Dodaj** > **nowy element**. W oknie dialogowym **Dodawanie nowego elementu** wyszukaj hasło "editorconfig". Wybierz jeden z szablonów elementów **pliku editorconfig,** a następnie wybierz pozycję **Dodaj**.

   ![Szablony elementów EditorConfig w programie Visual Studio](media/editorconfig-item-templates.png)

::: moniker range=">=vs-2019"

- Automatyczne tworzenie pliku *.editorconfig* na podstawie ustawień stylu kodu w polu Opcje tekstu **Options** > **Edytor** > tekstu **w języku C#** > **Styl kodu** **.** >

   ![Generowanie pliku .editorconfig z ustawień w programie VS 2019](media/vs-2019/generate-editorconfig-file.png)

::: moniker-end

- [Funkcja wnioskowania kodu](/visualstudio/intellicode/code-style-inference) IntelliCode for Visual Studio wywnioskować style kodu z istniejącego kodu. Następnie tworzy niepusty plik EditorConfig z preferencjami stylu kodu już zdefiniowane.

- Skonfiguruj poziom ważności reguły stylu kodu bezpośrednio za pośrednictwem edytora. Jeśli obecnie nie masz pliku .editorconfig, zostanie wygenerowany dla Ciebie. Umieść kursor na błędzie, ostrzeżeniu lub sugestii i wpisz **klawisz Ctrl**+**.** , aby otworzyć menu Szybkie akcje i Refaktoryzowania. Wybierz **pozycję Konfiguruj lub wyłącz problemy**. Następnie wybierz regułę i poziom ważności, który chcesz skonfigurować dla tej reguły. Spowoduje to zaktualizowanie istniejącego pliku EditorConfig przy użyciu nowej ważności reguły.

   ![Konfigurowanie poziomu ważności reguły stylu kodu bezpośrednio w edytorze](../ide/media/configure-severity-level.png)

Zapoznaj się z dokumentacją [opcji konwencji kodowania .NET,](editorconfig-code-style-settings-reference.md) która zawiera również przykład kompletnego pliku EditorConfig.

::: moniker range=">=vs-2019"

## <a name="code-cleanup"></a>Oczyszczanie kodu

Visual Studio zapewnia formatowanie na żądanie pliku kodu, w tym preferencje stylu kodu, za pośrednictwem funkcji **oczyszczania kodu.** Aby uruchomić oczyszczanie kodu, kliknij ikonę miotły u dołu edytora lub naciśnij **klawisze Ctrl**+**K**, **Ctrl**+**E**.

![Przycisk Oczyszczanie kodu w programie Visual Studio 2019](media/execute-code-cleanup.png)

Można również uruchomić oczyszczanie kodu w całym projekcie lub rozwiązaniu. Kliknij prawym przyciskiem myszy nazwę projektu lub rozwiązania w **Eksploratorze rozwiązań**, wybierz **pozycję Analizuj i Oczyszczanie kodu**, a następnie wybierz polecenie **Uruchom oczyszczanie kodu**.

![Uruchamianie oczyszczania kodu w całym projekcie lub rozwiązaniu](media/run-code-cleanup-project-solution.png)

Oprócz formatowania pliku dla spacji, wcjęcia, et cetera, **Oczyszczanie kodu** stosuje również wybrane style kodu. Preferencje dla każdego stylu kodu są odczytywane z [pliku EditorConfig](code-styles-and-code-cleanup.md#code-styles-in-editorconfig-files), jeśli masz go dla projektu lub z [ustawień stylu kodu](code-styles-and-code-cleanup.md#code-styles-in-the-options-dialog-box) w oknie dialogowym **Opcje.**

::: moniker-end

## <a name="refactorings-and-code-fixes"></a>Refaktoryzowania i poprawki kodu

Visual Studio zawiera wiele refaktoryzacji, akcje generowania kodu i poprawki kodu. Czerwone faliści reprezentują błędy, zielone faliszki reprezentują ostrzeżenia, a trzy szare kropki reprezentują sugestie kodu. Poprawki kodu można uzyskać, klikając ikonę żarówki lub śrubokręta lub naciskając klawisz **Ctrl**+**.** lub **Alt**+**Enter**. Każda poprawka jest dostarczany z oknem podglądu, który pokazuje różnice kodu na żywo, jak działa poprawka.

Popularne szybkie poprawki i refaktoryzowania obejmują:

- Zmiana nazwy
- Wyodrębnij metodę
- Zmień podpis metody
- Generowanie konstruktora
- Generuj metodę
- Przenieś typ do pliku
- Dodaj czek zerowy
- Dodaj parametr
- Usuń niepotrzebne użycie
- Pętla foreach do zapytania LINQ lub do metody LINQ
- Pociągnij członków w górę

Aby uzyskać więcej informacji, zobacz [funkcje generowania kodu](code-generation-in-visual-studio.md).

Analizatory FxCop można zainstalować, aby [oznaczyć](../code-quality/install-fxcop-analyzers.md) problemy z kodem. Lub napisać własną refaktoryzacji lub poprawki kodu z [analizatorów Roslyn](https://github.com/dotnet/roslyn/wiki/Getting-Started-Writing-a-Custom-Analyzer-&-Code-Fix).

Kilku członków społeczności napisało bezpłatne rozszerzenia, które dodają dodatkowe inspekcje kodu:

- [Roslynator ( Roslynator )](https://marketplace.visualstudio.com/items?itemName=josefpihrt.Roslynator2017)
- [SonarLint dla programu Visual Studio](https://marketplace.visualstudio.com/items?itemName=SonarSource.SonarLintforVisualStudio2017)
- [StyleCopAnalyzers](https://www.nuget.org/packages/stylecop.analyzers/)
- [CodeCracker (KodCracker)](https://www.nuget.org/packages/codecracker.CSharp/)

![Refaktoryzowania w programie Visual Studio](../ide/media/VSGuide_CodeAnalysis.png)

## <a name="find-usages-go-to-implementation-and-navigate-to-decompiled-assemblies"></a>Znajdź użycia, Przejdź do implementacji i przejdź do dekompilowanych zestawów

Visual Studio ma wiele funkcji ułatwiające wyszukiwanie i [poruszanie się po kodzie.](../ide/navigating-code.md)

| Funkcja | Skrót | Szczegóły/ulepszenia |
|- | - | -|
| Znajdź wszystkie odwołania | **Przesunięcie**+**F12**| Wyniki są pokolorowane i mogą być pogrupowane według projektu, definicji i typu odwołania, takich jak odczyt lub zapis. Można również "zablokować" wyniki. |
| Przejdź do implementacji | **Ctrl**+**F12** | Aby przejść do przesłoniętego elementu członkowskiego, można użyć funkcji Przejdź do definicji. `override` |
| Przejdź do definicji | **Kliknięcie klawisza F12** lub **Ctrl**+**Click**| Naciśnij **klawisz Ctrl** podczas klikania, aby przejść do definicji |
| Podejrzyj definicję | **Alt**+**F12** | Wbudowany widok definicji |
| Wizualizator struktury | Szare, kropkowane linie między nawiasami klamrowymi | Najedź kursorem, aby wyświetlić strukturę kodu |
| Nawigacja do dekompilowanych zespołów | **Kliknięcie klawisza F12** lub **Ctrl**+**Click** | Przejdź do zewnętrznego źródła (dekompilowanego z ILSpy), włączając funkcję: **Opcje narzędzi** > **Options** > **Edytor** > tekstu**C#** > **Zaawansowane** > **Włączanie nawigacji do dekompilowanych źródeł**. |

![Przejdź do wszystkich i znajdź wszystkie referencje](../ide/media/VSIDE_Productivity_Navigation.png)

## <a name="improved-intellisense"></a>Ulepszona funkcja IntelliSense

Użyj IntelliCode dla programu Visual Studio, aby uzyskać [kontekstowe uzupełnienia kodu](/visualstudio/intellicode/intellicode-visual-studio) zamiast tylko listy alfabetycznej. Można również szkolić [niestandardowy model IntelliSense](/visualstudio/intellicode/custom-model-faq) na podstawie własnych bibliotek specyficznych dla domeny.

## <a name="unit-testing"></a>Testy jednostkowe

Począwszy od programu Visual Studio 2017, istnieje wiele ulepszeń środowiska testowania. Można przetestować za pomocą mstest v1, MSTest v2, NUnit lub XUnit struktury testów.

- **Odnajdowanie testów Eksploratora testów** jest szybkie.

- Zorganizuj testy w **Eksploratorze testów** za pomocą *hierarchicznego sortowania*.

   ![Widok hierarchii dla Eksploratora tekstu w programie Visual Studio](../ide/media/VSGuide_Testing.png)

- [Testowanie jednostkowe na żywo](../test/live-unit-testing.md) stale uruchamia testy, na które mają wpływ zmiany kodu i aktualizacje wbudowanych ikon edytora, aby poinformować o stanie testów. Uwzględnij lub wyklucz określone testy lub projekty testowe z zestawu testów na żywo. (Tylko wersja programu Visual Studio Enterprise).

## <a name="debugging"></a>Debugging

Niektóre funkcje debugowania programu Visual Studio obejmują:

::: moniker range=">=vs-2019"

- Możliwość wyszukiwania ciągu w oknach **Czujka,** **Autos**i **Locals.**
- *Uruchom, aby kliknąć*, który pozwala na kursor obok linii kodu, naciśnij zieloną ikonę "play", która się pojawi, i uruchomić program, aż osiągnie tę linię.
- **Pomocnik wyjątków**, który umieszcza najważniejsze informacje na najwyższym poziomie w oknie `null` dialogowym, na przykład, która zmienna znajduje się w . `NullReferenceException`
- [Krok wstecz debugowania](../debugger/view-historical-application-state.md), który pozwala wrócić do poprzednich punktów przerwania lub kroki i wyświetlić stan aplikacji, jak to było w przeszłości.
- [Debugowanie migawki](/azure/application-insights/app-insights-snapshot-debugger), który pozwala zbadać stan aplikacji sieci web na żywo w momencie zgłoszenia wyjątku (musi być na platformie Azure).

::: moniker-end

::: moniker range="vs-2017"

- *Uruchom, aby kliknąć*, który pozwala na kursor obok linii kodu, naciśnij zieloną ikonę "play", która się pojawi, i uruchomić program, aż osiągnie tę linię.
- **Pomocnik wyjątków**, który umieszcza najważniejsze informacje na najwyższym poziomie w oknie `null` dialogowym, na przykład, która zmienna znajduje się w . `NullReferenceException`
- [Krok wstecz debugowania](../debugger/view-historical-application-state.md), który pozwala wrócić do poprzednich punktów przerwania lub kroki i wyświetlić stan aplikacji, jak to było w przeszłości.
- [Debugowanie migawki](/azure/application-insights/app-insights-snapshot-debugger), który pozwala zbadać stan aplikacji sieci web na żywo w momencie zgłoszenia wyjątku (musi być na platformie Azure).

::: moniker-end

![Pomocnik wyjątków w programie Visual Studio](../ide/media/VSGuide_Debugging.png)

## <a name="version-control"></a>Kontrola wersji

Git lub TFVC służy do przechowywania i aktualizowania kodu w programie Visual Studio.

::: moniker range=">=vs-2019"

- Zainstaluj [żądania ściągania dla programu Visual Studio,](https://marketplace.visualstudio.com/items?itemName=vsideversioncontrolmsft.pr4vs) aby utworzyć, przejrzeć, wyewidencjonować i uruchomić żądania ściągania bez opuszczania programu Visual Studio.

::: moniker-end

- Zorganizuj lokalne zmiany w [Eksploratorze zespołu](reference/team-explorer-reference.md) i użyj paska stanu do śledzenia oczekujących zatwierdzeń i zmian.

- Skonfiguruj ciągłą integrację i dostarczanie dla ASP.NET projektów wewnątrz programu Visual Studio za pomocą [narzędzi ciągłego dostarczania dla](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) rozszerzenia programu Visual Studio.

![Kontrola źródła w programie Visual Studio](../ide/media/VSIDE_Productivity_SourceControl.png)

## <a name="what-other-features-should-i-know-about"></a>O jakich innych funkcjach powinienem wiedzieć?

Oto lista funkcji edytora i produktywności, aby pisanie kodu było bardziej wydajne. Niektóre funkcje mogą wymagać włączenia, ponieważ są domyślnie wyłączone (mogą indeksować rzeczy na komputerze, są kontrowersyjne lub są obecnie eksperymentalne).

| Funkcja | Szczegóły | Jak włączyć |
|-|-|-|
| Zlokalizuj plik w Eksploratorze rozwiązań | Wyróżnia aktywny plik w **Eksploratorze rozwiązań** | **Projekty** > **i rozwiązania** > **opcje** > narzędzi**śledzą aktywny element w Eksploratorze rozwiązań** |
| Dodawanie użycia typów w zestawach referencyjnych i pakietach NuGet | Pokazuje żarówkę błędu z poprawką kodu, aby zainstalować pakiet NuGet dla typu nieodniesionego | **Opcje narzędzi** > **Options****Edytor** > tekstu**C#** > **Zaawansowane** > **sugerowanie używa dla typów w zestawach referencyjnych** i **zasugeruj użycie typów w pakietach NuGet**  >  |
| Włączanie pełnej analizy rozwiązania | Zobacz wszystkie błędy w rozwiązaniu na **liście błędów** | **Opcje narzędzi** > **Options****Edytor** > tekstu**C#** > **Zaawansowane** > **Włączanie pełnej analizy rozwiązania**  >  |
| Włączanie nawigacji do dekompilowanych źródeł | Zezwalaj na definicję przejdź do typów/elementów członkowskich ze źródeł zewnętrznych i użyj dekompilatora ILSpy, aby pokazać obiekty metody | **Opcje narzędzi** > **Options****Edytor** > tekstu**C#** > **Zaawansowane** > **Włączanie nawigacji do dekompilowanych źródeł**  >  |
| Tryb uzupełniania/sugestii | Zmienia zachowanie ukończenia w IntelliSense. Deweloperzy z intellij tła mają tendencję do korzystania z ustawienia nie domyślne tutaj. | **Tryb** > **ukończenia przełączania** przełącznika**Edycji** > Menu**IntelliSense** >  |
| [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) | Wyświetla informacje o odwołaniu do kodu i historii zmian w edytorze. (Wskaźniki codelens kontroli źródła nie są dostępne w wersji społeczności programu Visual Studio.) | **Opcje** > **narzędzi** > **Edytor** > tekstu**Wszystkie języki** > **CodeLens** |
| [Fragmenty kodu](../ide/visual-csharp-code-snippets.md) | Pomoc wykreślić wspólny kod standardowy | Wpisz nazwę urywka i naciśnij dwukrotnie **klawisz Tab.** |

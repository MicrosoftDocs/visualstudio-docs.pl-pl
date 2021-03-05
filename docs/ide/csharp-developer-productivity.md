---
title: Zwiększ swoją produktywność na potrzeby programowania na platformie .NET
description: Przegląd nawigacji, analizy kodu, testowania jednostkowego i innych funkcji, które ułatwiają szybsze pisanie lepszego kodu platformy .NET.
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.date: 11/21/2019
ms.topic: conceptual
helpviewer_keywords:
- editor
ms.workload:
- dotnet
ms.openlocfilehash: a3ac2e91ed9166a2eb8bdc4a19f2143c4fc71640
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161316"
---
# <a name="visual-studio-productivity-guide-for-c-developers"></a>Przewodnik dotyczący wydajności programu Visual Studio dla deweloperów języka C#

Dowiedz się, jak program Visual Studio zwiększa produktywność deweloperów niż kiedykolwiek. Skorzystaj z naszych ulepszeń dotyczących wydajności i produktywności, takich jak Nawigacja do dekompilowanych zestawów, sugestie nazw zmiennych podczas pisania, widok hierarchii w **Eksploratorze testów**, przejdź do wszystkich (**Ctrl** + **T**), aby przejść do pozycji plik/typ/element członkowski/symbol, inteligentne **pomocnika wyjątków**, konfiguracja i wymuszanie stylu kodu oraz wiele refaktoryzacji i poprawek kodu.

## <a name="im-used-to-keyboard-shortcuts-from-a-different-editor"></a>Używam skrótu klawiaturowego z innego edytora

::: moniker range="vs-2017"

**Nowość w programie Visual Studio 2017 w wersji 15,8**

::: moniker-end

Jeśli korzystasz z innego środowiska IDE lub kodowania, możesz zmienić schemat klawiatury na *Visual Studio Code* lub *Resharp (Visual Studio)*:

![Schematy klawiatury w programie Visual Studio](../ide/media/VS2017Guide-Keyboard.png)

Niektóre rozszerzenia oferują również schematy klawiatury:

- [Klawisze dostępu dla programu Visual Studio (Resharper/IntelliJ)](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.HotKeys)
- [Emulacja Emacs:](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.EmacsEmulation)
- [VSVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)

Poniżej przedstawiono popularne skróty programu Visual Studio:

| Skrót (wszystkie profile) | Polecenie | Opis |
|-|-|-|
| **Ctrl** + **T** | Przejdź do wszystkiego | Przejdź do dowolnego pliku, typu, składowej lub deklaracji symbolu |
| **F12** (kliknij również **Ctrl** + ) | Przejdź do definicji | Przejdź do miejsca, w którym zdefiniowano symbol |
| **Ctrl** + **F12** | Przejdź do implementacji | Nawigacja z typu podstawowego lub składowej do różnych implementacji |
| **SHIFT** + **F12** | Znajdź wszystkie odwołania | Zobacz wszystkie odwołania do symboli lub literałów |
| **Alt** + **Strona główna** | Polecenie Go To Base (Przejdź do podstawy) | Nawigowanie po łańcuchu dziedziczenia |
| **Ctrl** + **.** (również **Alt** + **Wprowadź** w profilu C#) | Szybkie akcje i operacje refaktoryzacji | Zobacz, jakie poprawki kodu, akcje generowania kodu, refaktoryzacje lub inne szybkie akcje są dostępne na pozycji kursora lub w wybranym kodzie |
| **Ctrl** + **D** | Duplikuj wiersz | Duplikuje wiersz kodu, w którym znajduje się kursor (dostępny w programie **Visual Studio 2017 w wersji 15,6** lub nowszej) |
| **SHIFT** + **Alt**+**+**/**-** | Rozwiń/Zwiń zaznaczenie | Rozwija lub kontraktuje bieżące zaznaczenie w edytorze (dostępne w programie **Visual Studio 2017 w wersji 15,5** i nowszych) |
| **SHIFT**  +  **Alt**  +  **.** | Wstaw następny pasujący karetkę | Dodaje zaznaczenie i karetkę w następnej lokalizacji pasującej do bieżącego zaznaczenia (dostępne w programie **Visual Studio 2017 w wersji 15,8** i nowszych) |
| **Ctrl** + **P** | Wyszukaj | Przeszukaj wszystkie ustawienia programu Visual Studio |
| **F5** | Rozpocznij debugowanie | Rozpocznij debugowanie aplikacji |
| **Ctrl** + **F5** | Uruchom bez debugowania | Uruchamianie aplikacji lokalnie bez debugowania |
| **Ctrl** + **K**,**d** (profil domyślny) lub **Ctrl** + **E**,**d** (profil C#) | Formatuj dokument | Czyści naruszenia formatowania pliku na podstawie nowego wiersza, odstępów i ustawień wcięć |
| **Ctrl** + **\\** ,**Ctrl** + **E** (profil domyślny) lub **Ctrl** + **W**,**E** (profil C#) | Wyświetl Lista błędów | Zobacz wszystkie błędy w dokumencie, projekcie lub rozwiązaniu |
| **Alt**  +  **PgUp/PgDn** | Przejdź do następnego/poprzedniego problemu | Przejdź do poprzedniego/następnego błędu, ostrzeżenia i sugestii w dokumencie (dostępne w programie **Visual Studio 2017 w wersji 15,8** lub nowszej) |
| **Ctrl** + **K**,**/** | Przełącz Komentarz jednowierszowy/Usuń komentarz | To polecenie dodaje lub usuwa Komentarz jednowierszowy w zależności od tego, czy zaznaczenie jest już komentarzem |
| **Ctrl** + **SHIFT**+**/** | Przełącz komentarz bloku/Usuń komentarz | To polecenie dodaje lub usuwa komentarze bloku w zależności od wybranych elementów |

> [!NOTE]
> Niektóre rozszerzenia odpinają domyślne powiązania klawiszy programu Visual Studio. Aby użyć powyższych poleceń, Przywróć wartości domyślne powiązań klawiszy do ustawień domyślnych programu Visual Studio, przechodząc do opcji **Narzędzia**  >  **Importuj i Eksportuj ustawienia**  >  **Zresetuj wszystkie ustawienia** lub **Narzędzia**  >  **Opcje**  >    >  **Zresetuj**.

Aby uzyskać więcej informacji na temat skrótów klawiaturowych i poleceń, zobacz [Skróty dotyczące produktywności](../ide/productivity-shortcuts.md) i [popularne skróty klawiaturowe](default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md).

## <a name="navigate-quickly-to-files-or-types"></a>Szybkie nawigowanie do plików lub typów

Program Visual Studio ma funkcję o nazwie **Przejdź do wszystkich** (**Ctrl** + **T**). Polecenie **Przejdź do wszystkich** umożliwia szybkie przechodzenie do dowolnego pliku, typu, składowej lub deklaracji symbolu.

- Zmień lokalizację tego paska wyszukiwania lub wyłącz podgląd nawigacji na żywo przy użyciu ikony **koła zębatego** .
- Filtrowanie wyników przy użyciu składni takiej jak `t mytype` .
- Przeszukaj zakres wyszukiwania tylko do bieżącego dokumentu.
- Obsługiwane jest dopasowywanie wielkości liter notacji CamelCase.

![Przejdź do wszystkich w programie Visual Studio](../ide/media/VS2017Guide-go-to-all.png)

## <a name="enforce-code-style-rules"></a>Wymuś reguły stylu kodu

Można użyć pliku EditorConfig do codify konwencji kodowania i uzyskać do nich podróże ze źródłem.

![Wymuszanie stylu kodu w programie Visual Studio](../ide/media/VSGuide_CodeStyle.png)

- Dodaj wartość domyślną lub. Plik EditorConfig w stylu NET do projektu, wybierając pozycję **Dodaj**  >  **nowy element**. W oknie dialogowym **Dodaj nowy element** Wyszukaj ciąg "editorconfig". Wybierz jeden z szablonów elementu **Editorconfig pliku** , a następnie wybierz pozycję **Dodaj**.

   ![Szablony elementów EditorConfig w programie Visual Studio](media/editorconfig-item-templates.png)

::: moniker range=">=vs-2019"

- Automatycznie Utwórz plik *. editorconfig* na podstawie ustawień stylu kodu w opcji **Narzędzia** >  > **Edytor tekstu** > **C#** > **styl kodu**.

   ![Generuj plik. editorconfig na podstawie ustawień w programie VS 2019](media/vs-2019/generate-editorconfig-file.png)

::: moniker-end

- [Funkcja wnioskowania kodu](/visualstudio/intellicode/code-style-inference) rozszerzenia intellicode dla programu Visual Studio wnioskuje style kodu z istniejącego kodu. Następnie tworzy niepusty plik EditorConfig z preferencjami stylu kodu.

- Skonfiguruj poziom ważności reguły stylu kodu bezpośrednio za pomocą edytora. Jeśli obecnie nie masz pliku. editorconfig, zostanie on wygenerowany dla Ciebie. Umieść kursor na błędzie, ostrzeżenie lub sugestię i wpisz **Ctrl** + **.** , aby otworzyć menu szybkie akcje i operacje refaktoryzacji. Wybierz pozycję **Konfiguruj lub Pomiń problemy**. Następnie wybierz regułę i poziom ważności, który chcesz skonfigurować dla tej reguły. Spowoduje to zaktualizowanie istniejącego pliku EditorConfig przy użyciu nowej ważności reguły.

   ![Skonfiguruj poziom ważności reguły w stylu kodu bezpośrednio w edytorze](../ide/media/configure-severity-level.png)

Zapoznaj się z dokumentacją [opcji konwencji kodowania .NET](/dotnet/fundamentals/code-analysis/code-style-rule-options) , która zawiera również przykład kompletnego pliku EditorConfig.

::: moniker range=">=vs-2019"

## <a name="code-cleanup"></a>Czyszczenie kodu

Program Visual Studio zapewnia formatowanie pliku kodu na żądanie, w tym preferencje stylu kodu, za pomocą funkcji **czyszczenia kodu** . Aby uruchomić oczyszczanie kodu, kliknij ikonę Broom w dolnej części edytora lub naciśnij **klawisze CTRL** + **K**, **Ctrl** + **E**.

![Przycisk oczyszczania kodu w programie Visual Studio 2019](media/execute-code-cleanup.png)

Możesz również uruchomić oczyszczanie kodu w całym projekcie lub rozwiązaniu. Kliknij prawym przyciskiem myszy nazwę projektu lub rozwiązania w **Eksplorator rozwiązań**, wybierz pozycję **Analizuj i wyczyść kod**, a następnie wybierz polecenie **Uruchom oczyszczanie kodu**.

![Uruchom oczyszczanie kodu w całym projekcie lub rozwiązaniu](media/run-code-cleanup-project-solution.png)

Oprócz formatowania pliku dla spacji, wcięcia, et zadanie, **czyszczenie kodu** stosuje się również do wybranych stylów kodu. Preferencje dla każdego stylu kodu są odczytywane z [pliku EditorConfig](code-styles-and-code-cleanup.md#code-styles-in-editorconfig-files), jeśli istnieje dla projektu lub z [ustawień stylu kodu](code-styles-and-code-cleanup.md#code-styles-in-the-options-dialog-box) w oknie dialogowym **Opcje** .

::: moniker-end

## <a name="refactorings-and-code-fixes"></a>Refaktoryzacje i poprawki kodu

Program Visual Studio zawiera wiele refaktoryzacji, akcji generowania kodu i poprawek kodu. Czerwone zygzaki reprezentują błędy, zielone zygzaki reprezentują ostrzeżenia, a trzy szare kropki reprezentują sugestie dotyczące kodu. Możesz uzyskać dostęp do poprawek kodu, klikając ikonę żarówki lub śrubokrętu lub naciskając klawisz **Ctrl** + **.** lub **klawisz** + **Enter**. Każda poprawka zawiera okno podglądu, w którym znajduje się porównanie kodu na żywo, w jaki sposób działa poprawka.

Popularne szybkie poprawki i refaktoryzacje obejmują:

- Zmień nazwę
- Wyodrębnij metodę
- Zmień sygnaturę metody
- Generuj Konstruktor
- Generate — Metoda
- Przenieś typ do pliku
- Dodaj Null-Check
- Dodaj parametr
- Usuń niepotrzebne użycia
- Pętla foreach do zapytania LINQ lub metoda LINQ
- Ściąganie członków

Aby uzyskać więcej informacji, zobacz [funkcje generowania kodu](code-generation-in-visual-studio.md).

[Analizatory FxCop można zainstalować](../code-quality/install-fxcop-analyzers.md) , aby oflagować problemy związane z kodem. Lub napisz własną poprawkę refaktoryzacji lub kodu za pomocą [analizatorów Roslyn](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Getting-Started-Writing-a-Custom-Analyzer-&-Code-Fix.md).

Kilku członków społeczności dodała bezpłatne rozszerzenia, które dodają dodatkowe inspekcje kodu:

::: moniker range="vs-2017"

- [Roslynator](https://marketplace.visualstudio.com/items?itemName=josefpihrt.Roslynator2017)
- [SonarLint dla programu Visual Studio](https://marketplace.visualstudio.com/items?itemName=SonarSource.SonarLintforVisualStudio2017)
- [StyleCopAnalyzers](https://www.nuget.org/packages/stylecop.analyzers/)
- [CodeCracker](https://www.nuget.org/packages/codecracker.CSharp/)

::: moniker-end

::: moniker range="vs-2019"

- [Roslynator](https://marketplace.visualstudio.com/items?itemName=josefpihrt.Roslynator2019)
- [SonarLint dla programu Visual Studio](https://marketplace.visualstudio.com/items?itemName=SonarSource.SonarLintforVisualStudio2019)
- [StyleCopAnalyzers](https://www.nuget.org/packages/stylecop.analyzers/)
- [CodeCracker](https://www.nuget.org/packages/codecracker.CSharp/)

::: moniker-end

![Refaktoryzacje w programie Visual Studio](../ide/media/VSGuide_CodeAnalysis.png)

## <a name="find-usages-go-to-implementation-and-navigate-to-decompiled-assemblies"></a>Znajdź użycie, przejdź do implementacji i przejdź do dekompilowanych zestawów

Program Visual Studio ma wiele funkcji ułatwiających wyszukiwanie i [nawigowanie po kodzie](../ide/navigating-code.md).

| Cecha | Skrót | Szczegóły/ulepszenia |
|- | - | -|
| Znajdź wszystkie odwołania | **SHIFT** + **F12**| Wyniki są kolorowe i mogą być pogrupowane według projektu, definicji i typu referencyjnego, takich jak Odczyt lub zapis. Możesz również "zablokować" wyniki. |
| Przejdź do implementacji | **Ctrl** + **F12** | Możesz użyć przejdź do definicji `override` słowa kluczowego, aby przejść do przesłoniętego elementu członkowskiego |
| Przejdź do definicji | **F12** lub **Ctrl** + **kliknij**| Naciśnij klawisz **Ctrl** podczas klikania, aby przejść do definicji |
| Podejrzyj definicję | **Alt** + **F12** | Wbudowany widok definicji |
| Wizualizator struktury | Szare, kropkowane linie między nawiasami klamrowymi | Umieść wskaźnik myszy, aby zobaczyć strukturę kodu |
| Nawigacja do dekompilowanych zestawów | **F12** lub **Ctrl** + **kliknij** | Przejdź do zewnętrznego źródła (dekompilowanego za pomocą ILSpy), włączając funkcję: **Narzędzia**  >  **Opcje**  >  **Edytor tekstu**  >  **C#**  >  **Zaawansowane**  >  **Włącz nawigację do dekompilowanych źródeł**. |

![Przejdź do wszystkich i Znajdź wszystkie odwołania](../ide/media/VSIDE_Productivity_Navigation.png)

## <a name="improved-intellisense"></a>Ulepszona funkcja IntelliSense

Użyj rozszerzenia intellicode dla programu Visual Studio, aby uzyskać [uzupełnianie kodu z obsługą kontekstu](/visualstudio/intellicode/intellicode-visual-studio) zamiast zwykłej listy. Możesz również przeszkolić [niestandardowy model IntelliSense](/visualstudio/intellicode/custom-model-faq) na podstawie własnych bibliotek specyficznych dla domeny.

## <a name="unit-testing"></a>Testowanie jednostek

Począwszy od programu Visual Studio 2017, wprowadzono liczne ulepszenia środowiska testowania. Można testować za pomocą platform MSTest V1, MSTest v2, NUnit lub XUnit.

- Odnajdywanie testów w **Eksploratorze testów** jest szybkie.

- Organizuj testy w **Eksploratorze testów** przy użyciu *sortowania hierarchicznego*.

   ![Widok hierarchii dla Eksploratora tekstów w programie Visual Studio](../ide/media/VSGuide_Testing.png)

- [Testowanie jednostkowe na żywo](../test/live-unit-testing.md) w sposób ciągły uruchamia testy, na które wpływa zmiana kodu i aktualizuje ikony edytora wbudowanego, aby poinformować o stanie testów. Dołącz lub Wyklucz określone testy lub projekty testowe z zestawu testów na żywo. (Tylko wersja Visual Studio Enterprise).

## <a name="debugging"></a>Debugowanie

Niektóre funkcje debugowania programu Visual Studio obejmują:

::: moniker range=">=vs-2019"

- Możliwość wyszukania ciągu w oknach **czujki** **, autoi** **lokalnych** .
- *Uruchom polecenie, aby kliknąć*, które pozwala na umieszczenie kursora obok wiersza kodu, kliknij zieloną ikonę "Odtwórz" i uruchom program do momentu osiągnięcia tego wiersza.
- **Pomocnik wyjątku**, który wprowadza najważniejsze informacje na najwyższego poziomu w oknie dialogowym, na przykład, która zmienna znajduje się `null` w `NullReferenceException` .
- [Debugowanie krok po kroku](../debugger/view-historical-application-state.md)umożliwia powrót do poprzednich punktów przerwania lub kroków oraz wyświetlenie stanu aplikacji w przeszłości.
- [Debugowanie migawek](/azure/application-insights/app-insights-snapshot-debugger), które umożliwia badanie stanu działającej aplikacji sieci Web w momencie zgłoszenia wyjątku (musi być na platformie Azure).

::: moniker-end

::: moniker range="vs-2017"

- *Uruchom polecenie, aby kliknąć*, które pozwala na umieszczenie kursora obok wiersza kodu, kliknij zieloną ikonę "Odtwórz" i uruchom program do momentu osiągnięcia tego wiersza.
- **Pomocnik wyjątku**, który wprowadza najważniejsze informacje na najwyższego poziomu w oknie dialogowym, na przykład, która zmienna znajduje się `null` w `NullReferenceException` .
- [Debugowanie krok po kroku](../debugger/view-historical-application-state.md)umożliwia powrót do poprzednich punktów przerwania lub kroków oraz wyświetlenie stanu aplikacji w przeszłości.
- [Debugowanie migawek](/azure/application-insights/app-insights-snapshot-debugger), które umożliwia badanie stanu działającej aplikacji sieci Web w momencie zgłoszenia wyjątku (musi być na platformie Azure).

::: moniker-end

![Pomocnik wyjątków w programie Visual Studio](../ide/media/VSGuide_Debugging.png)

## <a name="version-control"></a>Kontrola wersji

Za pomocą narzędzia Git lub TFVC można przechowywać i aktualizować kod w programie Visual Studio.

::: moniker range=">=vs-2019"

- Zainstaluj [żądania ściągnięcia dla programu Visual Studio](https://marketplace.visualstudio.com/items?itemName=vsideversioncontrolmsft.pr4vs) , aby tworzyć, przeglądać, wyewidencjonowywać i uruchamiać żądania ściągnięcia bez opuszczania programu Visual Studio.

::: moniker-end

- Organizuj lokalne zmiany w [Team Explorer](reference/team-explorer-reference.md) i Użyj paska stanu do śledzenia oczekujących zatwierdzeń i zmian.

- Skonfiguruj ciągłą integrację i dostarczanie dla projektów ASP.NET w programie Visual Studio przy użyciu [narzędzi ciągłego dostarczania dla rozszerzenia programu Visual Studio](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) .

![Kontrola źródła w programie Visual Studio](../ide/media/VSIDE_Productivity_SourceControl.png)

## <a name="what-other-features-should-i-know-about"></a>Jakie inne funkcje należy wiedzieć?

Poniżej znajduje się lista funkcji edytora i produktywności, które umożliwiają efektywniejsze pisanie kodu. Może być konieczne włączenie niektórych funkcji, ponieważ są one domyślnie wyłączone (mogą być indeksowane na komputerze, są kontrowersyjnye lub są obecnie eksperymentalne).

| Cecha | Szczegóły | Jak włączyć |
|-|-|-|
| Zlokalizuj plik w Eksplorator rozwiązań | Podświetla aktywny plik w **Eksplorator rozwiązań** | **Narzędzia**  >  **Opcje**  >  **Projekty i rozwiązania**  >  **Śledź aktywny element w Eksplorator rozwiązań** |
| Dodaj using dla typów w zestawach odwołań i pakietach NuGet | Pokazuje żarówkę błędu z poprawkami kodu, aby zainstalować pakiet NuGet dla typu niereferencyjnego | **Narzędzia**  >  **Opcje**  >  **Edytor tekstu**  >  Język **C#**  >  **Zaawansowane**  >  **Sugeruj użycie dla typów w zestawach odwołań** i **Sugeruj użycie dla typów w pakietach NuGet** |
| Włączanie pełnej analizy rozwiązania | Zobacz wszystkie błędy w rozwiązaniu w **Lista błędów** | **Narzędzia**  >  **Opcje**  >  **Edytor tekstu**  >  Język **C#**  >  **Zaawansowane**  >  **Włącz pełną analizę rozwiązania** |
| Włącz nawigację do dekompilowanych źródeł | Zezwalaj na przechodzenie do definicji typów/członków ze źródeł zewnętrznych i używanie ILSpy dekompilator — informacje do wyświetlania treści metod | **Narzędzia**  >  **Opcje**  >  **Edytor tekstu**  >  Język **C#**  >  **Zaawansowane**  >  **Włącz nawigację do dekompilowanych źródeł** |
| Tryb uzupełniania/sugestii | Zmienia zachowanie uzupełniania w IntelliSense. Deweloperzy z tłem IntelliJą używają tutaj ustawienia innego niż domyślne. | **Menu**  >  **Edytuj**  >  Funkcja **IntelliSense**  >  **Przełącz tryb uzupełniania** |
| [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) | Wyświetla informacje o odwołaniach do kodu i historię zmian w edytorze. (Wskaźniki CodeLens kontroli źródła nie są dostępne w programie Visual Studio Community Edition). | **Narzędzia**  >  **Opcje**  >  **Edytor tekstu**  >  **Wszystkie języki**  >  **CodeLens** |
| [Fragmenty kodu](../ide/visual-csharp-code-snippets.md) | Pomoc w wypełnieniu wspólnego kodu standardowego | Wpisz nazwę fragmentu i naciśnij dwukrotnie klawisz **Tab** . |

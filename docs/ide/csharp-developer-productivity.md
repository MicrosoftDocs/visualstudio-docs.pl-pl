---
title: Zwiększanie produktywności podczas tworzenia aplikacji na platformie .NET
description: Omówienie nawigacji, analizy kodu, testowania jednostkowego i innych funkcji, które ułatwiają szybsze pisanie lepszego kodu .NET.
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.date: 11/21/2019
ms.topic: conceptual
helpviewer_keywords:
- editor
ms.workload:
- dotnet
ms.openlocfilehash: 6de31ed1b649f226ac47161fdadfe44d434289b9
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308522"
---
# <a name="visual-studio-productivity-guide-for-c-developers"></a>Visual Studio przewodnik dotyczący produktywności dla deweloperów języka C#

Dowiedz się, Visual Studio sprawia, że deweloperzy są bardziej wydajni niż kiedykolwiek wcześniej. Skorzystaj z naszych ulepszeń wydajności i produktywności, takich jak nawigacja do dekompilowanych zestawów, sugestie dotyczące nazw zmiennych podczas wpisywania, widok hierarchii w Eksploratorze **testów,** funkcja Przejdź do wszystkich **(Ctrl** T), aby przejść do deklaracji + plików/typów/elementów członkowskich/symboli, inteligentnego pomocnika wyjątków, konfiguracji i wymuszania stylu kodu oraz wielu refaktoryzacji i poprawek kodu. 

## <a name="im-used-to-keyboard-shortcuts-from-a-different-editor"></a>Jestem używany do skrótów klawiaturowych z innego edytora

::: moniker range="vs-2017"

**Nowość w Visual Studio 2017 w wersji 15.8**

::: moniker-end

Jeśli pochodzisz z innego środowiska IDE lub środowiska kodowania,  możesz zmienić schemat klawiatury na Visual Studio Code *lub ReSharper (Visual Studio):*

![Schematy klawiatury w Visual Studio](../ide/media/VS2017Guide-Keyboard.png)

Niektóre rozszerzenia oferują również schematy klawiatury:

- [Klawisze dostępu dla Visual Studio (ReSharper/IntelliJ)](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.HotKeys)
- [Emacs Emulation](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.EmacsEmulation)
- [VsVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)

Poniżej przedstawiono popularne skróty Visual Studio skróty:

| Skrót (wszystkie profile) | Polecenie | Opis |
|-|-|-|
| **Ctrl** + **T** | Przejdź do wszystkich | Przejdź do dowolnego pliku, typu, członka lub deklaracji symbolu |
| **F12** (również **Ctrl** + **Kliknij**) | Przejdź do definicji | Przechodzenie do miejsca, w którym jest zdefiniowany symbol |
| **Ctrl** + **F12** | Przejdź do implementacji | Przechodzenie z typu podstawowego lub członka do jego różnych implementacji |
| **Shift (Przesunięcie)** + **F12** | Znajdź wszystkie odwołania | Wyświetlanie wszystkich odwołań do symboli lub literałów |
| **Alt (Alt)** + **Strona główna** | Polecenie Go To Base (Przejdź do podstawy) | Przechodzenie w górę łańcucha dziedziczenia |
| **Ctrl** + **.** (również **Alt** + **Wprowadź** w profilu C#) | Szybkie akcje i operacje refaktoryzacji | Zobacz, jakie poprawki kodu, akcje generowania kodu, refaktoryzowanie lub inne szybkie akcje są dostępne po pozycji kursora lub wyborze kodu |
| **Ctrl** + **D** | Duplikuj wiersz | Duplikuje wiersz kodu, w którym znajduje się kursor (dostępny **Visual Studio 2017 w wersji 15.6** i nowszych) |
| **Shift (Przesunięcie)** + **Alt (Alt)**+**+**/**-** | Rozwijanie/zaznaczanie kontraktu | Rozwija lub zawęnia bieżący wybór w edytorze (dostępne **w wersji Visual Studio 2017 15.5** lub nowszej) |
| **Shift (Przesunięcie)**  +  **Alt (Alt)**  +  **.** | Wstaw następny pasujący wieniec | Dodaje zaznaczenie i caret w następnej lokalizacji, która pasuje do bieżącego wyboru (dostępne Visual Studio **2017 w wersji 15.8** i nowszych) |
| **Ctrl** + **Q (Pytanie)** | Wyszukaj | Przeszukaj wszystkie Visual Studio wyszukiwania |
| **F5** | Rozpocznij debugowanie | Rozpoczynanie debugowania aplikacji |
| **Ctrl** + **F5** | Uruchamianie bez debugowania | Uruchamianie aplikacji lokalnie bez debugowania |
| **Ctrl** + **K,****D** (profil domyślny) lub **Ctrl** + **E,****D** (profil C#) | Formatuj dokument | Czyści naruszenia formatowania w pliku na podstawie nowego wiersza, odstępów i ustawień wcięcia |
| **Ctrl,** + **\\** **Ctrl** + **E** (profil domyślny) lub **Ctrl** + **W,****E** (profil C#) | Wyświetlanie listy błędów | Wyświetlanie wszystkich błędów w dokumencie, projekcie lub rozwiązaniu |
| **Alt (Alt)**  +  **PgUp/PgDn** | Przejdź do następnego/poprzedniego problemu | Przejdź do poprzedniego/następnego błędu, ostrzeżenia i sugestii w dokumencie (dostępnego w wersji **Visual Studio 2017 15.8** lub nowszej) |
| **Ctrl** + **K**,**/** | Przełączanie komentarza/komentarza jedno wierszowego | To polecenie dodaje lub usuwa komentarz jedno wierszowy w zależności od tego, czy zaznaczenie zostało już skomentowane |
| **Ctrl** + **Shift (Przesunięcie)**+**/** | Przełączanie komentarza/komentarza do bloku | To polecenie dodaje lub usuwa komentarze do bloku w zależności od tego, co zostało wybrane |

> [!NOTE]
> Niektóre rozszerzenia odłączyły domyślne Visual Studio powiązyń klawiszy. Aby użyć powyższych poleceń, przywróć swoje Visual Studio do domyślnych ustawień, przechodząc do opcji Narzędzia Importowanie i eksportowanie ustawień  >    >  **Resetuj** wszystkie ustawienia lub Opcje narzędzi Resetowanie  >    >    >  **klawiatury.**

Aby uzyskać więcej informacji na temat skrótów klawiaturowych i poleceń, zobacz [Productivity shortcuts (Skróty zwiększające produktywność)](../ide/productivity-shortcuts.md) [i Popular keyboard shortcuts (Popularne skróty klawiaturowe).](default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md)

## <a name="navigate-quickly-to-files-or-types"></a>Szybkie przechodzenie do plików lub typów

Visual Studio ma funkcję o nazwie **Przejdź do wszystkich** **(Ctrl** + **T).** **Funkcja Przejdź do wszystkich** umożliwia szybkie przejście do dowolnego pliku, typu, członka lub deklaracji symboli.

- Zmień lokalizację tego paska wyszukiwania lub wyłącz podgląd nawigacji na żywo za pomocą **ikony koła zębatego.**
- Filtruj wyniki przy użyciu składni, takiej jak `t mytype` .
- Zakres wyszukiwania obejmuje tylko bieżący dokument.
- Obsługiwane jest dopasowywanie camel case.

![Przejdź do wszystkich w Visual Studio](../ide/media/VS2017Guide-go-to-all.png)

## <a name="enforce-code-style-rules"></a>Wymuszanie reguł stylu kodu

Pliku EditorConfig można użyć do ujednolicenia konwencji kodowania i nakłoniania ich do podróży ze źródłem.

![Wymuszanie stylu kodu w Visual Studio](../ide/media/VSGuide_CodeStyle.png)

- Dodaj wartość domyślną lub . Plik EditorConfig w stylu net do projektu, wybierając **pozycję Dodaj**  >  **nowy element.** W **oknie dialogowym Dodawanie** nowego elementu wyszukaj pozycję "editorconfig". Wybierz jeden z szablonów **elementów pliku editorconfig,** a następnie wybierz pozycję **Dodaj**.

   ![Szablony elementów EditorConfig w Visual Studio](media/editorconfig-item-templates.png)

::: moniker range=">=vs-2019"

- Automatycznie utwórz plik *.editorconfig* na podstawie ustawień stylu kodu w menu **Narzędzia** > **Opcje** > **Edytor tekstu** Styl kodu języka >  > **C#.**

   ![Generowanie pliku .editorconfig na podstawie ustawień w programie VS 2019](media/vs-2019/generate-editorconfig-file.png)

::: moniker-end

- Funkcja [wnioskowania kodu funkcji](/visualstudio/intellicode/code-style-inference) IntelliCode for Visual Studio wywnioskuje style kodu z istniejącego kodu. Następnie tworzy niepusty plik EditorConfig z już zdefiniowanymi preferencjami stylu kodu.

- Skonfiguruj poziom ważności reguły stylu kodu bezpośrednio za pośrednictwem edytora. Jeśli obecnie nie masz pliku .editorconfig, zostanie on wygenerowany automatycznie. Umieść kursor na błędzie, ostrzeżeniu lub sugestii i naciśnij **klawisze Ctrl** + **.** , aby otworzyć menu Szybkie akcje i refaktoryzowanie. Wybierz **pozycję Konfiguruj lub Pomiń problemy.** Następnie wybierz regułę i poziom ważności, który chcesz skonfigurować dla tej reguły. Spowoduje to zaktualizowanie istniejącego pliku EditorConfig przy użyciu nowej ważności reguły.

   ![Konfigurowanie poziomu ważności reguły stylu kodu bezpośrednio w edytorze](../ide/media/configure-severity-level.png)

Zapoznaj się z [dokumentacją opcji konwencji kodowania .NET,](/dotnet/fundamentals/code-analysis/code-style-rule-options) która zawiera również przykład kompletnego pliku EditorConfig.

::: moniker range=">=vs-2019"

## <a name="code-cleanup"></a>Oczyszczanie kodu

Visual Studio udostępnia formatowanie pliku kodu na żądanie, w tym preferencje stylu kodu, za pomocą **funkcji oczyszczania** kodu. Aby uruchomić oczyszczanie kodu, kliknij ikonę mioteł w dolnej części edytora lub naciśnij **klawisze Ctrl** + **K,** **Ctrl** + **E**.

![Przycisk Oczyszczanie kodu w Visual Studio 2019 r.](media/execute-code-cleanup.png)

Możesz również uruchomić oczyszczanie kodu w całym projekcie lub rozwiązaniu. Kliknij prawym przyciskiem myszy nazwę projektu lub rozwiązania w **programie Eksplorator rozwiązań,** wybierz pozycję Analizuj i wyczyść **kod,** a następnie wybierz polecenie **Uruchom oczyszczanie kodu.**

![Uruchamianie oczyszczania kodu w całym projekcie lub rozwiązaniu](media/run-code-cleanup-project-solution.png)

Oprócz formatowania pliku dla spacji, wcięć, et cetera, **oczyszczanie** kodu stosuje również wybrane style kodu. Preferencje dla każdego stylu kodu są odczytywane z pliku [EditorConfig](code-styles-and-code-cleanup.md#code-styles-in-editorconfig-files), [](code-styles-and-code-cleanup.md#code-styles-in-the-options-dialog-box) jeśli jest dostępny dla projektu, lub z ustawień stylu kodu w **oknie dialogowym** Opcje.

::: moniker-end

## <a name="refactorings-and-code-fixes"></a>Refaktoryzowanie i poprawki kodu

Visual Studio zawiera wiele refaktoryzacji, akcji generowania kodu i poprawek kodu. Czerwone zygniaki reprezentują błędy, zielone zygniaki reprezentują ostrzeżenia, a trzy szare kropki reprezentują sugestie dotyczące kodu. Aby uzyskać dostęp do poprawek kodu, kliknij ikonę żarówki lub śrubokręta albo naciśnij **klawisze Ctrl** + **.** lub **Alt** + **Enter**. Każda poprawka jest doprowadzona w oknie podglądu, które pokazuje różnicę kodu na żywo w oknie działania poprawki.

Popularne szybkie poprawki i refaktoryzowanie obejmują:

- Zmień nazwę
- Wyodrębnij metodę
- Zmiana sygnatury metody
- Generowanie konstruktora
- Generate, metoda
- Przenoszenie typu do pliku
- Dodawanie Null-Check
- Dodaj parametr
- Usuwanie niepotrzebnych using
- Foreach Loop to LINQ Query or to LINQ method (Pętla Foreach na zapytanie LINQ lub metoda LINQ)
- Pull Members Up

Aby uzyskać więcej informacji, zobacz [funkcje generowania kodu](code-generation-in-visual-studio.md).

Możesz zainstalować [analizatory FxCop, aby](../code-quality/install-fxcop-analyzers.md) flagować problemy z kodem. Możesz też napisać własną refaktoryzowanie lub poprawkę kodu za pomocą [analizatorów Roslyn](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Getting-Started-Writing-a-Custom-Analyzer-&-Code-Fix.md).

Kilku członków społeczności ma napisane bezpłatne rozszerzenia, które dodają dodatkowe przeglądy kodu:

::: moniker range="vs-2017"

- [Roslynator](https://marketplace.visualstudio.com/items?itemName=josefpihrt.Roslynator2017)
- [SonarLint dla Visual Studio](https://marketplace.visualstudio.com/items?itemName=SonarSource.SonarLintforVisualStudio2017)
- [StyleCopAnalyzers](https://www.nuget.org/packages/stylecop.analyzers/)
- [Code Niechcący](https://www.nuget.org/packages/codecracker.CSharp/)

::: moniker-end

::: moniker range=">=vs-2019"

- [Roslynator](https://marketplace.visualstudio.com/items?itemName=josefpihrt.Roslynator2019)
- [SonarLint dla Visual Studio](https://marketplace.visualstudio.com/items?itemName=SonarSource.SonarLintforVisualStudio2019)
- [StyleCopAnalyzers](https://www.nuget.org/packages/stylecop.analyzers/)
- [Code Niechcący](https://www.nuget.org/packages/codecracker.CSharp/)

::: moniker-end

![Refaktoryzowanie w Visual Studio](../ide/media/VSGuide_CodeAnalysis.png)

## <a name="find-usages-go-to-implementation-and-navigate-to-decompiled-assemblies"></a>Znajdź użycie, przejdź do implementacji i przejdź do dekompilowanych zestawów

Visual Studio wiele funkcji, które ułatwiają wyszukiwanie kodu [i nawigowanie po nim.](../ide/navigating-code.md)

| Cecha | Skrót | Szczegóły/ulepszenia |
|- | - | -|
| Znajdź wszystkie odwołania | **Shift (Przesunięcie)** + **F12**| Wyniki są pokolorowane i mogą być grupowane według projektu, definicji i typu odwołania, takiego jak odczyt lub zapis. Możesz również "zablokować" wyniki. |
| Przejdź do implementacji | **Ctrl** + **F12** | Możesz użyć funkcji Przejdź do definicji dla słowa `override` kluczowego, aby przejść do zastąpionego członka |
| Przejdź do definicji | **F12** lub **Ctrl** + **Kliknij**| Naciśnij **klawisz Ctrl** podczas klikania, aby przejść do definicji |
| Podejrzyj definicję | **Alt (Alt)** + **F12** | Widok wbudowanej definicji |
| Wizualizator struktury | Szare, kropkowane linie między nawiasami klamrowych | Zatrzymaj wskaźnik myszy, aby wyświetlić strukturę kodu |
| Nawigacja do dekompilowanych zestawów | **F12** lub **Ctrl** + **Kliknij** | Przejdź do źródła zewnętrznego (dekompilowanego za pomocą programu ILSpy), włączając funkcję: **Narzędzia** Opcje Edytor tekstu C# Zaawansowane Włączanie nawigacji do  >    >    >    >    >  **dekompilowanych źródeł.** |

![Przejdź do wszystkich i znajdź wszystkie odwołania](../ide/media/VSIDE_Productivity_Navigation.png)

## <a name="improved-intellisense"></a>Ulepszona funkcja IntelliSense

Użyj funkcji IntelliCode Visual Studio, aby uzyskać [kontekstowe](/visualstudio/intellicode/intellicode-visual-studio) uzupełnianie kodu, a nie tylko listę alfabetyczną. Możesz również wytszkolić [niestandardowy model IntelliSense](/visualstudio/intellicode/custom-model-faq) na podstawie własnych bibliotek specyficznych dla domeny.

## <a name="unit-testing"></a>Testowanie jednostek

Począwszy od Visual Studio 2017 r., wprowadzono wiele ulepszeń w zakresie testowania. Możesz testować przy użyciu platform testowych MSTest v1, MSTest v2, NUnit lub XUnit.

- **Odnajdywanie testów** w Eksploratorze testów jest szybkie.

- Organizowanie testów w **Eksploratorze testów** *za pomocą sortowania hierarchicznego*.

   ![Widok hierarchii dla Eksploratora tekstu w programie Visual Studio](../ide/media/VSGuide_Testing.png)

- [Testy jednostkowe na](../test/live-unit-testing.md) żywo nieprzerwanie uruchamiają testy, na które mają wpływ zmiany kodu i aktualizacje ikon edytora wbudowanego, aby sprawdzić stan testów. Uwzględnij lub wyklucz określone testy lub projekty testowe z zestawu testów na żywo. (tylko Visual Studio Enterprise wersji).

## <a name="debugging"></a>Debugowanie

Niektóre z Visual Studio debugowania są następujące:

::: moniker range=">=vs-2019"

- Możliwość wyszukiwania ciągu w oknach **Czujka,** **Automatyczne i** **Ustawienia** lokalne.
- *Uruchom polecenie*, aby kliknąć pozycję , która umożliwia umieszczenie wskaźnika myszy obok wiersza kodu, klikanie zielonej ikony odtwarzania, która zostanie wyświetlona, i uruchamianie programu do momentu osiągnięcia tego wiersza.
- Pomocnik **wyjątków**, który umieszcza najważniejsze informacje na najwyższym poziomie w oknie dialogowym, na przykład, która zmienna `null` znajduje się w zmiennej `NullReferenceException` .
- [Krok do tyłu debugowania](../debugger/view-historical-application-state.md), które pozwala wrócić do poprzednich punktów przerwania lub kroków i wyświetlić stan aplikacji, jaki był w przeszłości.
- [Debugowanie migawek](/azure/application-insights/app-insights-snapshot-debugger), które umożliwia badanie stanu aplikacji internetowej na żywo w momencie zgłoszenia wyjątku (musi znajdować się na platformie Azure).

::: moniker-end

::: moniker range="vs-2017"

- *Uruchom polecenie*, aby kliknąć pozycję , która umożliwia umieszczenie wskaźnika myszy obok wiersza kodu, klikanie zielonej ikony odtwarzania, która zostanie wyświetlona, i uruchamianie programu do momentu osiągnięcia tego wiersza.
- Pomocnik **wyjątków**, który umieszcza najważniejsze informacje na najwyższym poziomie w oknie dialogowym, na przykład, która zmienna `null` znajduje się w zmiennej `NullReferenceException` .
- [Krok do tyłu debugowania](../debugger/view-historical-application-state.md), które pozwala wrócić do poprzednich punktów przerwania lub kroków i wyświetlić stan aplikacji, jaki był w przeszłości.
- [Debugowanie migawek](/azure/application-insights/app-insights-snapshot-debugger), które umożliwia badanie stanu aplikacji internetowej na żywo w momencie zgłoszenia wyjątku (musi znajdować się na platformie Azure).

::: moniker-end

![Pomocnik wyjątków w Visual Studio](../ide/media/VSGuide_Debugging.png)

## <a name="version-control"></a>Kontrola wersji

Do przechowywania i aktualizowania kodu w programie można użyć narzędzia git lub kontroli wersji serwera Team Visual Studio.

::: moniker range=">=vs-2019"

- Zainstaluj żądania [ściągnięć dla Visual Studio,](https://marketplace.visualstudio.com/items?itemName=vsideversioncontrolmsft.pr4vs) aby tworzyć, przeglądać, wyewidencjonić i uruchamiać żądania ściągnięć bez opuszczania Visual Studio.

::: moniker-end

- Zorganizuj zmiany lokalne [w Team Explorer](reference/team-explorer-reference.md) i użyj paska stanu do śledzenia oczekujących zatwierdzeń i zmian.

- Skonfiguruj ciągłą integrację i ciągłe dostarczanie dla projektów ASP.NET wewnątrz Visual Studio za pomocą rozszerzenia [Continuous delivery tools for Visual Studio.](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio)

![Kontrola źródła w programie Visual Studio](../ide/media/VSIDE_Productivity_SourceControl.png)

## <a name="what-other-features-should-i-know-about"></a>Jakie inne funkcje należy znać?

Poniżej znajduje się lista funkcji edytora i produktywności, które sprawiają, że pisanie kodu jest bardziej wydajne. Niektóre funkcje mogą wymagać ich wyłączenia, ponieważ są domyślnie wyłączone (mogą indeksować elementy na maszynie, są nieswoje lub są obecnie eksperymentalne).

| Cecha | Szczegóły | Jak włączyć |
|-|-|-|
| Zlokalizuj plik w Eksplorator rozwiązań | Wyróżnia aktywny plik w **Eksplorator rozwiązań** | **Narzędzia**  >  **Opcje**  >  **Projekty i rozwiązania**  >  **Śledzenie aktywnego elementu w Eksplorator rozwiązań** |
| Dodawanie using dla typów w zestawach odwoływczych i pakietach NuGet | Wyświetla żarówkę błędu z poprawką kodu w celu zainstalowania pakietu NuGet dla nieużywanego typu | **Narzędzia**  >  **Opcje**  >  **Edytor tekstu**  >  **C#**  >  **Zaawansowane**  >  **Sugerowanie using dla typów w zestawach odwoływczych** i **Sugerowanie using dla typów w pakietach NuGet** |
| Włączanie pełnej analizy rozwiązania | Wyświetlanie wszystkich błędów w rozwiązaniu na **liście błędów** | **Narzędzia**  >  **Opcje**  >  **Edytor tekstu**  >  **C#**  >  **Zaawansowane**  >  **Włączanie pełnej analizy rozwiązania** |
| Włączanie nawigacji do dekompilowanych źródeł | Zezwalaj na używanie definicji Przejdź do dla typów/elementów członkowskich ze źródeł zewnętrznych i używanie dekompileru ILSpy do pokazywania treści metod | **Narzędzia**  >  **Opcje**  >  **Edytor tekstu**  >  **C#**  >  **Zaawansowane**  >  **Włączanie nawigacji do dekompilowanych źródeł** |
| Uzupełnianie/tryb sugestii | Zmienia zachowanie uzupełniania w funkcji IntelliSense. Deweloperzy z tłami IntelliJ zwykle używają tutaj ustawienia nie domyślnego. | **Menu**  >  **Edytuj**  >  **IntelliSense**  >  **Przełącz tryb uzupełniania** |
| [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) | Wyświetla informacje dotyczące kodu i historię zmian w edytorze. (Wskaźniki CodeLens kontroli źródła nie są dostępne w Visual Studio Community wersji). | **Narzędzia**  >  **Opcje**  >  **Edytor tekstu**  >  **Wszystkie języki**  >  **CodeLens** |
| [Fragmenty kodu](../ide/visual-csharp-code-snippets.md) | Pomoc w wycięcie wspólnego kodu ze wspólnym kodem | Wpisz nazwę fragmentu kodu i **dwukrotnie** naciśnij klawisz Tab. |

---
title: Zwiększ wydajność pracy podczas tworzenia aplikacji .NET
description: Przegląd Nawigacja, analizy kodu jednostki testowania i inne funkcje ułatwiające pisanie lepiej kodu platformy .NET szybciej.
author: kuhlenh
ms.author: gewarren
manager: jillfra
ms.date: 06/14/2018
ms.topic: conceptual
helpviewer_keywords:
- editor
ms.workload:
- dotnet
ms.openlocfilehash: dd467adc2ff45e38f193b1b87aea471682d40c0c
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55920603"
---
# <a name="visual-studio-2017-c-productivity-guide"></a>Przewodnik dotyczący programu Visual Studio 2017 C# produktywności

Dowiedz się, jak [programu Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) sprawia, że deweloperzy jest bardziej wydajne niż kiedykolwiek wcześniej. Skorzystaj z zalet naszej wydajność i produktywność ulepszenia, takie jak nawigacja do dekompilowanych zestawów, nazwa zmiennej sugestie, podczas wpisywania widok hierarchii w **Eksplorator testów**, przejdź do wszystkich (**Ctrl** + **T**) przejdź do pliku/typu/elementu członkowskiego/symbolu deklaracji, inteligentnej **pomocnika wyjątków**, styl konfiguracji i wymuszania i wiele operacji refaktoryzacji kodu oraz poprawki kodu.

## <a name="im-used-to-my-keyboard-shortcuts-from-a-different-extensioneditoride"></a>Z przyzwyczajenia używam Moje skrótów klawiaturowych z inne rozszerzenie/Edytor/środowisko IDE

**Nowe w programie Visual Studio 2017 wersja 15.8** Jeśli podchodzisz z innego środowiska IDE lub środowisko programistyczne, należy zmienić schemat klawiatury do *programu Visual Studio Code* lub *ReSharper (Visual Studio)*:

![Schematy klawiatury programu Visual Studio](../ide/media/VS2017Guide-Keyboard.png)

Niektóre rozszerzenia oferują również schematy klawiatury:

- [Klawisze dostępu dla programu Visual Studio (ReSharper/IntelliJ)](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.HotKeys)
- [Emulacja emacs](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.EmacsEmulation)
- [VSVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)

Dostępne są następujące popularne skróty programu Visual Studio:

| Skrót (wszystkie profile) | Polecenie | Opis |
|-|-|-|
| **CTRL**+**T** | Przejdź do wszystkich | Przejdź do dowolnego pliku/typu/elementu członkowskiego/symbolu deklaracji |
| **F12** (również **Ctrl**+**kliknij**) | Przejdź do definicji | Przejdź do której jest zdefiniowany symbol |
| **Ctrl**+**F12** | Przejdź do implementacji | Przechodzenie z typem bazowym lub elementu członkowskiego do jej różnych implementacji |
| **SHIFT**+**F12** | Znajdź wszystkie odwołania | Zobacz wszystkie symboli lub literału odwołania |
| **Ctrl**+**.** (również **Alt**+**wprowadź** w profilu C#) | Szybkie akcje i operacje refaktoryzacji | Zobacz, jaki kod poprawki, akcje generowania kodu, refaktoryzacji lub innych szybkie akcje są dostępne na wybór pozycji lub kod kursora |
| **Ctrl**+**D** | Duplikuj wiersz | Duplikuje wiersz kodu, w którym znajduje się kursor (dostępne w **programu Visual Studio 2017 w wersji 15.6** i nowsze) |
| **Shift**+**Alt**+**+**/**-** | Rozwijania/zwijania zaznaczenia | Zwiększa lub zmniejsza bieżące zaznaczenie w edytorze (dostępne w **programu Visual Studio 2017 w wersji 15.5** i nowsze) |
| **SHIFT** + **Alt** + **.** | Wstaw dalej pasującego karetki | Dodaje zaznaczenia i karetki w następnej lokalizacji, która pasuje do bieżącego zaznaczenia (dostępne w **Visual Studio 2017 w wersji 15.8** i nowsze) |
| **CTRL**+**funkcji pytania i odpowiedzi** | Szybkie uruchamianie | Wyszukaj wszystkie ustawienia programu Visual Studio |
| **F5** | Rozpocznij debugowanie | Rozpocznij debugowanie aplikacji |
| **Ctrl**+**F5** | Uruchom bez debugowania | Uruchamianie aplikacji lokalnie bez debugowania |
| **CTRL**+**K**,**D** (profil domyślny) lub **Ctrl**+**E**,**D**  (Profilu w języku C#) | [Formatuj dokument](code-styles-and-quick-actions.md#format-document-command) | Czyści formatowanie naruszeń w pliku na podstawie nowego wiersza, odstępy i ustawienia wcięć |
| **CTRL**+**\\**,**Ctrl**+**E** (profil domyślny) lub **Ctrl** + **W**,**E** (profilu w języku C#) | Wyświetl listę błędów | Zobacz wszystkie błędy w dokumencie, projekt lub rozwiązanie |
| **Alt** + **PgUp/PgDn** | Przejdź do następnego/poprzedniego wydania | Przejdź do poprzedniego/dalej błąd, ostrzeżenie, sugestii w dokumencie (dostępne w **Visual Studio 2017 w wersji 15.8** i nowsze) |

> [!NOTE]
> Niektóre rozszerzenia unbind powiązania klawiszy programu Visual Studio domyślną. Aby użyć poleceń powyżej, Przywróć usługi powiązania klawiszy programu Visual Studio domyślne, przechodząc do **narzędzia** > **Import i eksport ustawień** > **Resetuj wszystkie ustawienia**  lub **narzędzia** > **opcje** > **klawiatury** > **resetowania**.

Dowiedz się więcej skrótów klawiaturowych i poleceń w programie Visual Studio w [naszej dokumentacji](../ide/tips-and-tricks-for-visual-studio.md).

## <a name="i-need-a-way-to-quickly-navigate-to-files-or-types"></a>Potrzebuję metody szybkie przechodzenie do plików lub typów

Program Visual Studio 2017 zawiera funkcję o nazwie **przejdź do wszystkich** (**Ctrl**+**T**). **Przejdź do wszystkich** pozwala na szybkie przejście do pliku, typu, składowej lub deklaracji symbolu.

- Zmień lokalizację tego paska wyszukiwania lub wyłączyć na podglądzie nawigacyjnego na żywo za pomocą **koło zębate** ikony.
- Filtrowanie wyników za pomocą naszych składnia zapytania (na przykład "mytype t"). Można również ograniczyć wyszukiwanie do bieżącego dokumentu.
- Dopasowywanie camelCase jest obsługiwany!

![Przejdź do wszystkich w programie Visual Studio](../ide/media/VS2017Guide-go-to-all.png)

## <a name="my-team-enforces-code-style-rules-on-our-codebase"></a>Mój zespół wymusza reguł stylu kodu w naszej bazie kodu

Możesz użyć *.editorconfig* plik skodyfikować Konwencji kodowania i ich podróży z źródła.

- Możesz zainstalować [rozszerzenia usługi w języka EditorConfig](https://aka.ms/editorconfig), który można łatwo dodawać i edytować *.editorconfig* pliku w programie Visual Studio.
- Wypróbuj [rozszerzenia IntelliCode dla programu Visual Studio](/visualstudio/intellicode/intellicode-visual-studio). To rozszerzenie eksperymentalne wnioskuje style kodu z istniejącego kodu, a następnie tworzy niepusty *.editorconfig* plików za pomocą preferencji stylu kodu już zdefiniowane.
- Zapoznaj się z [opcjami Konwencji kodowania .NET](https://aka.ms/editorconfigDocs) dokumentacji.
- Zobacz [to gist](https://gist.github.com/kuhlenh/5471666a7a2c57fea427e81cf0a41da8) przykład *.editorconfig* pliku.

![Wymuszanie stylu kodu w programie Visual Studio](../ide/media/VSGuide_CodeStyle.png)

## <a name="i-need-more-refactorings-and-code-fixes"></a>Potrzebuję więcej poprawek refaktoryzacji i kodu

Program Visual Studio 2017 jest dostarczany z dużą liczbą operacji refaktoryzacji, akcji generowania kodu i poprawek kodu. Czerwone faliste linie reprezentującego błędy, zielone symbole reprezentują ostrzeżenia i trzy kropki znajdujące się szare reprezentują sugestie kodu. Poprawki kodu dostępu, można przez kliknięcie żarówki lub ikonę śrubokręt lub naciskając **Ctrl**+**.** lub **Alt**+**wprowadź**. Każda poprawka jest powiązana z okno podglądu, który pokazuje różnice kodu na żywo, sposobu działania poprawki.

- Popularne szybkich poprawek i operacje refaktoryzacji obejmują:
  - *Zmiana nazwy*
  - *Wyodrębnianie metody*
  - *Zmiana sygnatury metody*
  - *Generowanie konstruktora*
  - *Generowanie metody*
  - *Przeniesienie typu do pliku*
  - *Dodaj sprawdzanie wartości Null*
  - *Dodaj parametr*
  - *Usuń niepotrzebne użycia*
  - Zobacz więcej w naszym [dokumentacji](https://aka.ms/refactorings)
- Napisać własne dzięki kanałowi refaktoryzacji lub kod [analizatorów Roslyn](https://github.com/dotnet/roslyn/wiki/Getting-Started-Writing-a-Custom-Analyzer-&-Code-Fix).
- Kilka członków społeczności napisano bezpłatne rozszerzenia, które dodać dodatkowy kod inspekcji:
  - [Analizatory FxCop analizujące kod](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/)
  - [Roslynator](https://marketplace.visualstudio.com/items?itemName=josefpihrt.Roslynator2017)
  - [SonarLint for Visual Studio](https://marketplace.visualstudio.com/items?itemName=SonarSource.SonarLintforVisualStudio2017)
  - [StyleCopAnalyzers](https://www.nuget.org/packages/stylecop.analyzers/)

![Refaktoryzacje w programie Visual Studio](../ide/media/VSGuide_CodeAnalysis.png)

## <a name="i-need-find-usages-go-to-implementation-navigate-to-decompiled-assemblies"></a>Należy znaleźć użycia, przejdź do implementacji, przejdź do Dekompilowanych zestawów

Program Visual Studio 2017 oferuje wiele funkcji ułatwiające wyszukiwanie i przejdź do kodu. Przeczytaj więcej na temat [funkcji nawigacji w kodzie](../ide/navigating-code.md)

| Funkcja | Skrót | Szczegóły/ulepszeń |
|- | - | -|
| Znajdź wszystkie odwołania | **SHIFT**+**F12**| Wyniki są wyróżnione kolorem i mogą być grupowane według projektu, definicji, itp. Można również "zablokować" wyników. |
| Przejdź do implementacji | **Ctrl**+**F12** | Przejdź do definicji można używać na `override` — słowo kluczowe, aby przejść do zgodnym z przesłoniętą składową |
| Przejdź do definicji | **F12** lub **Ctrl**+**kliknij**| Naciśnij i przytrzymaj **Ctrl** przy zaznaczaniu navgiate do definicji |
| Zobacz definicję | **ALT**+**F12** | Wbudowany view definicji |
| Wizualizator struktury | Szare, kropkowana — linie między nawiasy klamrowe | Po wskazaniu wskaźnikiem, aby zobaczyć strukturę kodu |
| Nawigacja do dekompilowanych zestawów | **F12** lub **Ctrl**+**kliknij** | Przejdź do źródła zewnętrznego (decompiled przy użyciu narzędzia do dekompilacji) poprzez włączenie funkcji: **Narzędzia** > **opcje** > **edytora tekstów**  >  **C#**  >   **Zaawansowane** > **Włącz nawigację do dekompilowanych źródeł**. |

![Przejdź do wszystkich i Znajdź wszystkie odwołania](../ide/media/VSIDE_Productivity_Navigation.png)

## <a name="i-want-to-run-and-see-my-unit-tests"></a>Czy chcesz uruchomić, a następnie zobacz Moje testy jednostkowe

Wprowadziliśmy wiele ulepszeń środowiska testowania w programie Visual Studio 2017. Użyj jednej z naszych jednostki testowania przy użyciu MSTest w wersji 1, MSTest w wersji 2, NUnit oraz XUnit struktury testów.

- **Eksplorator testów** odnajdywanie testów jest szybkie w wersji 15.6 (Aby uzyskać najlepsze wyniki, przeprowadź uaktualnienie do najnowszej wersji adaptera testowego).
- Organizowanie testów w Eksploratorze testów dzięki naszej nowej *hierarchiczne sortowanie* w wersji 15.6.
- [Testowanie jednostek na żywo](../test/live-unit-testing.md) stale uruchamia testy, których dotyczą zmiany kodu i aktualizuje wbudowanego edytora ikon z informacją, stan testów. Uwzględnić lub wykluczyć określonych testów lub testowanie projektów z Twojej *Live testowanie zestawu*.

![Widok hierarchii w Eksploratorze tekstu w programie Visual Studio](../ide/media/VSGuide_Testing.png)

## <a name="i-want-to-debug-my-code"></a>Czy chcesz debugować mój kod

Dodaliśmy wiele nowych funkcji debugowania w programie Visual Studio 2017:

- *Uruchom do kliknięcia* umożliwia umieść obok wiersza kodu, trafienia zieloną ikonę "play", który pojawia się i uruchomić program, aż do osiągnięcia tego wiersza.
- Nowy **pomocnika wyjątków** umieszcza najważniejsze informacje, takie jak zmienna, która jest w obiektu NullReferenceException, na najwyższym poziomie, w oknie dialogowym "null".
- [Cofnijmy](../debugger/view-historical-application-state.md) debugowanie pozwala na wrócić do poprzednich punktów przerwania lub kroków i wyświetlić stan aplikacji, tak jak w przeszłości.
- [Debugowanie migawki](/azure/application-insights/app-insights-snapshot-debugger) umożliwia badanie stanu aplikacji internetowej na żywo w tej chwili Wystąpił wyjątek (musi być na platformie Azure).

![Nowy Pomocnik wyjątków w programie Visual Studio 2017](../ide/media/VSGuide_Debugging.png)

## <a name="i-want-to-use-version-control-with-my-projects"></a>Chcę korzystać z kontroli wersji z projektami

Git lub TFVC służy do przechowywania i aktualizowania kodu w programie Visual Studio.

- Organizowanie zmiany lokalne z **Team Explorer** i umożliwia śledzenie oczekujące zatwierdzenia i zmiany na pasku stanu.
- Konfigurowanie ciągłej integracji i ciągłego dostarczania dla projektów w programie Visual Studio z naszego [narzędzi Continuous delivery tools for Visual Studio](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) rozszerzenia i przepływu pracy dewelopera agile.

![Kontrola źródła w programie Visual Studio](../ide/media/VSIDE_Productivity_SourceControl.png)

## <a name="what-other-features-do-i-need-to-know-about"></a>Jakie inne funkcje muszę wiedzieć?

Poniżej przedstawiono listę funkcji edytora i produktywności, aby wprowadzić bardziej wydajne pisanie kodu. Niektóre funkcje mogą muszą być włączone, ponieważ są one wyłączone domyślnie (może indeksie rzeczy na komputerze, to kontrowersyjny lub są obecnie eksperymentalne).

| Funkcja | Szczegóły | Jak włączyć |
|-|-|-|
| Zlokalizuj plik w Eksploratorze rozwiązań | Wyróżnia aktywnego pliku w **Eksploratora rozwiązań** | **Narzędzia** > **opcje** > **projekty i rozwiązania** > **Śledź aktywny element w Eksploratorze rozwiązań** |
| Dodaj dyrektywy Using dla typów odwołań do zestawów i pakietów NuGet | Pokazuje błąd ikona żarówki z poprawki kodu, aby zainstalować pakiet NuGet dla typu bez odwołań | **Narzędzia** > **opcje** > **edytora tekstów** > **C#** > **zaawansowane**   >  **Sugeruj dyrektywy Using dla typów w zestawach referencyjnych** i **Sugeruj dyrektywy Using dla typów w pakietach NuGet** |
| Włączanie pełnej analizy rozwiązania | Zobacz wszystkie błędy w rozwiązaniu w **lista błędów** | **Narzędzia** > **opcje** > **edytora tekstów** > **C#** > **zaawansowane**   >  **Włączanie pełnej analizy rozwiązania** |
| Włącz nawigację do dekompilowanych źródeł | Zezwalaj na przechodzenie do definicji na typy/członków ze źródeł zewnętrznych i użyj decompiler użyciu narzędzia do dekompilacji do wyświetlenia treści metod | **Narzędzia** > **opcje** > **edytora tekstów** > **C#** > **zaawansowane**   >  **Włącz nawigację do dekompilowanych źródeł** |
| Tryb uzupełniania/sugestii | Zmiany zachowania uzupełnianie przez funkcję IntelliSense — deweloperom tła IntelliJ zwykle konieczna zmiana ustawienia tutaj z domyślnego | **Menu** > **Edytuj** > **IntelliSense** > **Przełącz tryb uzupełniania** |
| [Funkcja CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) | Wyświetla informacje referencyjne kodu i zmień historii w edytorze | **Narzędzia** > **opcje** > **edytora tekstów** > **wszystkie języki**  >   **Funkcja CodeLens** |
| [Fragmenty kodu](../ide/visual-csharp-code-snippets.md) | Pomoc namiastki się typowe standardowy | Wpisz nazwy fragmentu kodu i naciśnij klawisz **kartę** dwa razy. |

## <a name="missing-a-feature-that-makes-you-productive-or-experiencing-poor-performance"></a>Brak funkcji, dzięki której produktywność lub obciążony słabą wydajność?

Istnieje kilka sposobów, aby przesłać nam opinię:

- Żądania funkcji platformy .NET mogą być zgłaszane na naszych [repozytorium GitHub](https://github.com/dotnet/roslyn/issues).
- Żądania funkcji usługi Visual Studio, usterki i problemy z wydajnością można złożyć przy użyciu **Wyślij opinię** ikonę w prawym górnym rogu okna programu Visual Studio.

---
title: Edytowanie kodu w języku Python
description: W języku Python program Visual Studio udostępnia rozbudowaną funkcję IntelliSense, fragmenty kodu i funkcje nawigacji, obok formatowania, Zaznaczanie błędów i refaktoryzacji.
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: eb3e3ca5d18429c60894c42bda12328836dc6fc8
ms.sourcegitcommit: bb5425b9c6d8fd7135d9584c2963831754071347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73024721"
---
# <a name="edit-python-code"></a>Edytowanie kodu w języku Python

Ponieważ poświęcasz dużo czasu na programowanie w edytorze kodu, [Obsługa języka Python w programie Visual Studio](installing-python-support-in-visual-studio.md) udostępnia funkcje, które ułatwiają zwiększenie produktywności. Funkcje obejmują wyróżnianie składni IntelliSense, Autouzupełnianie, pomoc dotyczącą podpisu, metody zastąpień, wyszukiwanie i nawigowanie.

Edytor jest również zintegrowany z oknem **interaktywnym** w programie Visual Studio, co ułatwia wymianę kodu między nimi. Zobacz [samouczek krok 3. Użyj](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md) interaktywnego okna REPL i [Użyj interaktywnego okna — Wyślij do interaktywnego polecenia](python-interactive-repl-in-visual-studio.md#send-to-interactive-command) , aby uzyskać szczegółowe informacje.

Aby uzyskać ogólną dokumentację dotyczącą edytowania kodu w programie Visual Studio, zobacz [funkcje edytora kodu](../ide/writing-code-in-the-code-and-text-editor.md). Zobacz też [Tworzenie konspektu](../ide/outlining.md), które pomaga w zachowaniu określonych sekcji kodu.

Możesz również użyć programu Visual Studio **Przeglądarka obiektów** (**wyświetl** > **innych** > **Przeglądarka obiektów** lub **Ctrl**+**W** > **J**), aby sprawdzić klasy języka Python zdefiniowane w poszczególnych moduł i funkcje zdefiniowane w tych klasach.

## <a name="intellisense"></a>IntelliSense

Technologia IntelliSense zapewnia [uzupełnianie](#completions), [Pomoc dotyczącą podpisu](#signature-help), [szybkie informacje](#quick-info)i [kolorowanie kodu](#code-coloring). Program Visual Studio 2017 wersje 15,7 i nowsze obsługują również [wskazówki dotyczące typów](#type-hints).

Aby zwiększyć wydajność, funkcja IntelliSense w programie Visual Studio 2017 w wersji 15,5 i starszej zależy od bazy danych uzupełniania, która jest generowana dla każdego środowiska Python w projekcie. Po dodaniu, usunięciu lub zaktualizowaniu pakietów bazy danych może być konieczne odświeżenie. Stan bazy danych jest wyświetlany w oknie **środowiska języka Python** (element równorzędny **Eksplorator rozwiązań**) na karcie **IntelliSense** (zobacz [Dokumentacja okna środowiska](python-environments-window-tab-reference.md)).

Program Visual Studio 2017 w wersji 15,6 lub nowszej używa różnych środków, aby zapewnić uzupełnianie IntelliSense, które nie są zależne od bazy danych.

### <a name="completions"></a>Uzupełnienia

Zakończenia są wyświetlane jako instrukcje, identyfikatory i inne wyrazy, które mogą być odpowiednio wprowadzane w bieżącej lokalizacji w edytorze. Elementy wyświetlane na liście są oparte na kontekście i są filtrowane w celu pominięcia nieprawidłowych lub rozpraszających się opcji. Zakończenia są często wyzwalane przez wpisanie różnych instrukcji (takich jak `import`) i operatorów (łącznie z kropką), ale można je wyświetlać w dowolnym momencie, wpisując **Ctrl**+**J** > **Space**.

![Ukończenie elementu członkowskiego w edytorze programu Visual Studio](media/code-editing-completions-simple.png)

Gdy lista uzupełniania jest otwarta, można wyszukać żądane zakończenie przy użyciu klawiszy strzałek, myszy lub przez kontynuowanie wpisywania. Podczas wpisywania więcej liter lista jest przefiltrowana w celu pokazania prawdopodobnie ukończonych. Można również użyć skrótów, takich jak:

- Wpisywanie liter, które nie znajdują się na początku nazwy, na przykład "Parse", aby znaleźć "modułu argparse"
- Wpisywanie tylko liter, które znajdują się na początku wyrazów, takich jak "ABC", aby znaleźć "AbstractBaseClass" lub "Air", aby znaleźć "as_integer_ratio"
- Pomijanie liter, takich jak "B64", aby znaleźć "Base64"

Przykłady:

![Ukończenie elementu członkowskiego z filtrowaniem w edytorze programu Visual Studio](media/code-editing-completion-filtering.png)

Uzupełniania elementów członkowskich pojawiają się automatycznie po wpisaniu okresu po zmiennej lub wartości, wraz z metodami i atrybutami potencjalnych typów. Jeśli zmienna może być więcej niż jeden typ, lista zawiera wszystkie możliwości ze wszystkich typów, z dodatkowymi informacjami wskazującymi, które typy obsługują każde ukończenie. Gdy uzupełnianie jest obsługiwane przez wszystkie możliwe typy, jest on pokazywany bez adnotacji.

![Ukończenie elementu członkowskiego dla wielu typów w edytorze programu Visual Studio](media/code-editing-completion-types.png)

Domyślnie elementy członkowskie "dunder" (elementy członkowskie zaczynające się i kończące podwójnym podkreśleniem) nie są wyświetlane. Ogólnie rzecz biorąc takie elementy członkowskie nie powinny być dostępne bezpośrednio. Jeśli jest potrzebny, jednak wpisanie wiodącego podwójnego podkreślenia spowoduje dodanie następujących uzupełnień do listy:

![Kończenie prywatnego elementu członkowskiego w edytorze programu Visual Studio](media/code-editing-completion-dunder.png)

Instrukcje `import` i `from ... import` zawierają listę modułów, które mogą być importowane. Za pomocą `from ... import`lista zawiera elementy członkowskie, które mogą być importowane z określonego modułu.

![Zaimportuj ukończenie w edytorze programu Visual Studio](media/code-editing-completion-import.png)

Instrukcje `raise` i `except` wyświetlają listy klas, które mogą być typami błędów. Lista nie może zawierać wszystkich wyjątków zdefiniowanych przez użytkownika, ale ułatwia szybkie znajdowanie odpowiednich wbudowanych wyjątków:

![Kończenie wyjątku w edytorze programu Visual Studio](media/code-editing-completion-exception.png)

Wpisanie @ uruchamia dekoratora i wyświetla potencjalne dekoratory. Wiele z tych elementów nie jest użytecznych jako dekoratory; Zapoznaj się z dokumentacją biblioteki, aby określić, która z nich ma być używana.

![Dekoratora uzupełniania w edytorze programu Visual Studio](media/code-editing-completion-decorator.png)

> [!Tip]
> Można skonfigurować zachowanie uzupełniania za pomocą **narzędzi** > **Opcje** > **edytorze tekstów** > **Python** > **Advanced**. Wśród tych elementów **list filtrów opartych na ciągu wyszukiwania** stosuje filtrowanie sugestii uzupełniania podczas wpisywania (wartość domyślna to zaznaczone), a funkcja **uzupełniania elementów członkowskich wyświetla część wspólną** , które są obsługiwane przez wszystkie możliwe typy (wartość domyślna to unchecked). Zobacz [Opcje — wyniki uzupełniania](python-support-options-and-settings-in-visual-studio.md#completion-results).

### <a name="type-hints"></a>Wskazówki dotyczące typu

*Program Visual Studio 2017 w wersji 15,7 lub nowszej.*

"Wskazówki dotyczące typów" w języku Python 3.5 + ([PEP 484](https://www.python.org/dev/peps/pep-0484/) (Python.org) to składnia adnotacji dla funkcji i klas, które wskazują typy argumentów, wartości zwracane i atrybuty klas. Funkcja IntelliSense wyświetla wskazówki dotyczące typów po umieszczeniu wskaźnika myszy na wywołaniach funkcji, argumentach i zmiennych, które mają te adnotacje.

W poniższym przykładzie Klasa `Vector` jest zadeklarowana jako `List[float]`, a funkcja `scale` zawiera wskazówki typu dla obu argumentów i wartości zwracanej. Umieszczenie kursora w wywołaniu tej funkcji pokazuje wskazówki dotyczące typów:

![Umieszczenie kursora w wywołaniu funkcji, aby odsłonić wskazówki dotyczące typów](media/code-editing-type-hints1.png)

W poniższym przykładzie można zobaczyć, jak atrybuty klasy `Employee` pojawiają się w menu podręcznym uzupełniania IntelliSense dla atrybutu:

![Uzupełnianie IntelliSense przedstawiające wskazówki dotyczące typów](media/code-editing-type-hints2.png)

Pomocne jest również zweryfikowanie wskazówek dotyczących typu w całym projekcie, ponieważ błędy nie są zwykle wyświetlane do czasu uruchomienia. W tym celu program Visual Studio integruje standardowe narzędzie MyPy, korzystając z polecenia menu kontekstowego **Python** > **Run MyPy** w **Eksplorator rozwiązań**:

![Uruchom polecenie menu kontekstowego MyPy w Eksplorator rozwiązań](media/code-editing-type-hints-run-mypy.png)

Po uruchomieniu polecenia zostanie wyświetlony komunikat z prośbą o zainstalowanie pakietu mypy, jeśli jest to konieczne. Program Visual Studio uruchamia następnie mypy, aby zweryfikować wskazówki dotyczące typu w każdym pliku Python w projekcie. Błędy pojawiają się w oknie **Lista błędów** programu Visual Studio. Wybranie elementu w oknie powoduje przejście do odpowiedniego wiersza w kodzie.

Jako prosty przykład, następująca definicja funkcji zawiera wskazówkę typu, aby wskazać, że argument `input` jest typu `str`, podczas gdy wywołanie tej funkcji próbuje przekazać liczbę całkowitą:

```python
def commas_to_colons(input: str):
    items = input.split(',')
    items = [x.strip() for x in items]
    return ':'.join(items)

commas_to_colons(1)
```

Użycie polecenia **Uruchom Mypy** w tym kodzie spowoduje wygenerowanie następującego błędu:

![Przykładowy wynik mypy wskazówek typu](media/code-editing-type-hints-validation-error.png)

::: moniker range="vs-2017"
> [!Tip]
> W przypadku wersji środowiska Python przed 3,5, Visual Studio Wyświetla również wskazówki dotyczące wpisywania dostarczone przez zbioru typeshed *pliki szczątkowe* (*Pyi*). Możesz użyć plików szczątkowych, gdy nie chcesz uwzględniać wskazówek typu bezpośrednio w kodzie, lub gdy chcesz utworzyć wskazówki dotyczące typów dla biblioteki, która nie korzysta bezpośrednio z nich. Aby uzyskać więcej informacji, zobacz [Tworzenie wycinków dla modułów języka Python](https://github.com/python/mypy/wiki/Creating-Stubs-For-Python-Modules) w witrynie typu wiki projektu mypy.
>
> W tej chwili program Visual Studio nie obsługuje wskazówek dotyczących typów w komentarzach.
::: moniker-end
::: moniker range=">=vs-2019"
> [!Tip]
> W przypadku wersji środowiska Python przed 3,5, Visual Studio Wyświetla również wskazówki dotyczące wpisywania dostarczone przez zbioru typeshed *pliki szczątkowe* (*Pyi*). Możesz użyć plików szczątkowych, gdy nie chcesz uwzględniać wskazówek typu bezpośrednio w kodzie, lub gdy chcesz utworzyć wskazówki dotyczące typów dla biblioteki, która nie korzysta bezpośrednio z nich. Aby uzyskać więcej informacji, zobacz [Tworzenie wycinków dla modułów języka Python](https://github.com/python/mypy/wiki/Creating-Stubs-For-Python-Modules) w witrynie typu wiki projektu mypy.
>
> Program Visual Studio zawiera zestaw pakietów zbioru typeshed dla języka Python 2 i 3, więc dodatkowe pliki do pobrania nie są konieczne. Jeśli jednak chcesz użyć innego zestawu plików, możesz określić ścieżkę w obszarze **narzędzia** > **Opcje** > języka **Python** > opcje **serwera językowego** . Zobacz [Opcje — serwer języka](python-support-options-and-settings-in-visual-studio.md#language-server-options).
>
> W tej chwili program Visual Studio nie obsługuje wskazówek dotyczących typów w komentarzach.
::: moniker-end

### <a name="signature-help"></a>Pomoc dotycząca podpisu

Podczas pisania kodu, który wywołuje funkcję, pomoc w sygnaturze pojawia się po wpisaniu `(` otwierającej i wyświetleniu dostępnej dokumentacji i informacji o parametrach. Można również sprawić, aby był wyświetlany z **klawiszem Ctrl**+**SHIFT**+**miejsce** wewnątrz wywołania funkcji. Wyświetlane informacje są zależne od ciągów dokumentacji w kodzie źródłowym funkcji, ale zawierają wszystkie wartości domyślne.

![Pomoc dotycząca podpisu w edytorze programu Visual Studio](media/code-editing-signature-help.png)

> [!Tip]
> Aby wyłączyć pomoc dotyczącą podpisu, przejdź do pozycji **narzędzia** > **Opcje** > **Edytor tekstu** > **Python** > **Ogólne** i wyczyść **uzupełnianie instrukcji** > **Informacje o parametrach**.

### <a name="quick-info"></a>Szybkie informacje

Umieszczenie wskaźnika myszy nad identyfikatorem powoduje wyświetlenie etykietka Szybka podpowiedź. W zależności od identyfikatora, szybkie informacje mogą wyświetlać potencjalne wartości lub typy, dowolną dostępną dokumentację, typy zwracane i lokalizacje definicji:

![Szybkie informacje w edytorze programu Visual Studio](media/code-editing-quick-info.png)

### <a name="code-coloring"></a>Kolorowanie kodu

Kolorowanie kodu używa informacji z analizy kodu do zmiennych, instrukcji i innych fragmentów kodu. Na przykład zmienne odwołujące się do modułów lub klas mogą być wyświetlane w innym kolorze niż funkcje lub inne wartości, a nazwy parametrów są wyświetlane w innym kolorze niż zmienne lokalne lub globalne. (Domyślnie funkcje nie są pokazywane pogrubioną czcionką):

![Kolorowanie kodu i składni w edytorze programu Visual Studio](media/code-editing-code-coloring.png)

Aby dostosować kolory, przejdź do pozycji **narzędzia** > **opcje** > **środowisko** > **czcionki i kolory** , a następnie zmodyfikuj wpisy w języku **Python** na liście **elementy wyświetlane** :

![Opcje czcionek i kolorów w programie Visual Studio](media/code-editing-customize-colors.png)

> [!Tip]
> Aby wyłączyć kolorowanie kodu, przejdź do pozycji **narzędzia** > **Opcje** > **Edytor tekstu** > **Python** > **Zaawansowane** i wyczyść **różne opcje** > **nazwy kolorów na podstawie typu**. Zobacz [Opcje — różne opcje](python-support-options-and-settings-in-visual-studio.md#miscellaneous-options).

## <a name="code-snippets"></a>Fragmenty kodu

Fragmenty kodu to fragmenty kodu, które można wstawić do plików przez wpisanie skrótu i naciśnięcie klawisza **Tab**lub użycie opcji **edytuj** > **IntelliSense** > **Wstawianie fragmentu kodu** i **Otocz przy użyciu** poleceń, wybranie języka **Python**, a następnie wybranie żądanego fragmentu kodu.

Na przykład `class` jest skrótem do fragmentu kodu, który wstawia definicję klasy. Po wpisaniu `class`zostanie wyświetlony fragment na liście autouzupełniania:

![Fragment kodu dotyczący skrótu do klasy](media/code-editing-code-snippet-class.png)

Naciśnięcie klawisza **Tab** spowoduje wygenerowanie reszty klasy. Następnie można wpisać nad listą i bazami danych, poruszając się między wyróżnionymi polami z **tabulatorem**, a następnie naciskając klawisz **Enter** , aby rozpocząć wpisywanie treści.

![Najważniejsze elementy fragmentu kodu do ukończenia](media/code-editing-code-snippets.png)

### <a name="menu-commands"></a>Polecenia menu

W przypadku używania polecenia **edytuj** > **IntelliSense** > **Wstaw fragment kodu** menu, najpierw wybierz język **Python**, a następnie wybierz fragment kodu:

![Wybieranie fragmentu kodu za pomocą polecenia Wstaw fragment kodu](media/code-editing-code-snippet-insert.png)

Polecenie **Edit** > **IntelliSense** > **Otocz za pomocą** polecenia, podobnie, umieszcza bieżące zaznaczenie w edytorze tekstów wewnątrz wybranego elementu strukturalnego. Załóżmy na przykład, że masz nieco następujący kod:

```python
sum = 0
for x in range(1, 100):
    sum = sum + x
```

Wybranie tego kodu i wybranie opcji **Otocz za pomocą** polecenia powoduje wyświetlenie listy dostępnych wstawek kodu. Wybranie opcji **def** z listy powoduje umieszczenie wybranego kodu w ramach definicji funkcji. możesz użyć klawisza **Tab** , aby Przechodź między wyróżnioną nazwą funkcji a argumentami:

![Używanie polecenia Otocz z poleceniem dla fragmentów kodu](media/code-editing-code-snippet-surround-with.png)

### <a name="examine-available-snippets"></a>Badaj dostępne fragmenty kodu

Dostępne fragmenty kodu są widoczne w **Menedżerze fragmentów kodu**, otwierane przy użyciu **narzędzi** > polecenia menu **Menedżera fragmentów kodu** i wybierając **Python** jako język:

![Menedżer fragmentów kodu w programie Visual Studio](media/code-editing-code-snippets-manager.png)

Aby utworzyć własne wstawki, zobacz [Przewodnik: Tworzenie fragmentu kodu](../ide/walkthrough-creating-a-code-snippet.md).

Jeśli napiszesz doskonałe fragmenty kodu, które chcesz udostępnić, możesz bezpłatnie ogłosić je w rejestrze i [poinformować nas](https://github.com/Microsoft/PTVS/issues)o tym. Możemy włączyć ją w przyszłej wersji programu Visual Studio.

## <a name="navigate-your-code"></a>Poruszanie się po kodzie

Obsługa języka Python w programie Visual Studio oferuje kilka metod szybkiego nawigowania w kodzie, w tym biblioteki, dla których kod źródłowy jest dostępny: [pasek nawigacyjny](#navigation-bar), [**Przejdź do definicji**](#go-to-definition), [**Przejdź do**](#navigate-to)i [**Znajdź wszystkie odwołania** ](#find-all-references). Możesz również użyć programu Visual Studio [**Przeglądarka obiektów**](../ide/viewing-the-structure-of-code.md#BKMK_ObjectBrowser).

### <a name="navigation-bar"></a>Pasek nawigacyjny

Pasek nawigacyjny jest wyświetlany w górnej części każdego okna edytora i zawiera listę definicji na dwóch poziomach. Lewe menu rozwijane zawiera definicje klas i funkcji najwyższego poziomu w bieżącym pliku; po prawej stronie listy rozwijanej zostanie wyświetlona lista definicji w zakresie pokazanym po lewej stronie. W trakcie poruszania się w edytorze lista zawiera aktualizację pokazującą bieżący kontekst i można również wybrać wpis z tych list, aby przejść bezpośrednio do programu.

![Pasek nawigacyjny w edytorze programu Visual Studio](media/code-editing-navigation-bar.png)

> [!Tip]
> Aby ukryć pasek nawigacyjny, przejdź do **pozycji narzędzia** > **Opcje** > **Edytor tekstu** > **Python** > **Ogólne** i wyczyść **Ustawienia** > **pasku nawigacyjnym**.

### <a name="go-to-definition"></a>Przejdź do definicji

**Przejdź do definicji** szybko przeskakuje od używania identyfikatora (takiego jak nazwa funkcji, Klasa lub zmienna) do kodu źródłowego, gdzie jest zdefiniowany. Wywołujesz ją, klikając prawym przyciskiem myszy identyfikator i wybierając pozycję **Przejdź do definicji** lub, umieszczając karetkę w identyfikatorze i naciskając klawisz **F12**. Działa w ramach kodu i bibliotek zewnętrznych, pod warunkiem, że kod źródłowy jest dostępny. Jeśli kod źródłowy biblioteki nie jest dostępny, **Przejdź do pozycji definicja** przeskakuje do odpowiedniej instrukcji `import` dla odwołania do modułu lub wyświetli błąd.

![Polecenie Przejdź do definicji w programie Visual Studio](media/code-editing-go-to-definition.png)

### <a name="navigate-to"></a>Przejdź do

**Edytuj** > **Przejdź do** polecenia (**Ctrl**+ **,** ) powoduje wyświetlenie pola wyszukiwania w edytorze, w którym można wpisać dowolny ciąg i zobaczyć możliwe dopasowania w kodzie, który definiuje funkcję, klasę lub zmienną zawierającą tę parametry. Ta funkcja udostępnia podobną funkcję, jak **Przejdź do definicji** , ale bez konieczności lokalizowania identyfikatora.

Dwukrotne kliknięcie dowolnej nazwy lub wybranie klawiszy strzałek i **Enter**powoduje przejście do definicji tego identyfikatora.

![Przejdź do polecenia w programie Visual Studio](media/code-editing-navigate-to.png)

### <a name="find-all-references"></a>Znajdź wszystkie odwołania

Opcja **Znajdź wszystkie odwołania** jest przydatnym sposobem odnajdowania, gdzie każdy identyfikator jest zdefiniowany i używany, w tym do importowania i przypisań. Wywołujesz ją przez kliknięcie prawym przyciskiem myszy identyfikatora i wybranie opcji **Znajdź wszystkie odwołania**lub przez umieszczenie karetki w identyfikatorze, a następnie naciśnięcie klawisza **SHIFT**+**F12**. Dwukrotne kliknięcie elementu na liście powoduje przejście do jego lokalizacji.

![Znajdź wszystkie odwołania do wyników](media/code-editing-find-all-references.png)

## <a name="see-also"></a>Zobacz także

- [Formatowanie](formatting-python-code.md)
- [Refaktoryzacja](refactoring-python-code.md)
- [Użyj Linter](linting-python-code.md)

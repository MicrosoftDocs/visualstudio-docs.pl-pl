---
title: Edytowanie kodu w języku Python
description: Dla języka Python Visual Studio zapewnia zaawansowane funkcji IntelliSense, fragmenty kodu i funkcje nawigacji, wraz z formatowania, Zaznaczanie błędów i refaktoryzacji.
ms.date: 11/19/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 15020111702d68c8c35fb09655018215e3a11d3b
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062819"
---
# <a name="edit-python-code"></a>Edytowanie kodu w języku Python

Ponieważ większość czasu projektowania w edytorze kodu wydatków [obsługi języka Python w programie Visual Studio](installing-python-support-in-visual-studio.md) udostępnia funkcje ułatwiające mu bardziej wydajnej pracy. Funkcje obejmują IntelliSense wyróżniania składni, automatyczne uzupełnianie, pomocy dotyczącej sygnatur, zastąpienia metody, wyszukiwania i nawigacji.

Edytor jest także zintegrowana z **Interactive** okna w programie Visual Studio, ułatwiając wymiany kodu między nimi. Zobacz [samouczek krok 3: Korzystanie z okna interaktywnego REPL](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md) i [użycie okna interaktywnego — Wyślij polecenie interaktywne](python-interactive-repl-in-visual-studio.md#send-to-interactive-command) Aby uzyskać szczegółowe informacje.

|   |   |
|---|---|
| ![Ikona aparatu film wideo](../install/media/video-icon.png "Obejrzyj klip wideo") | [Obejrzyj film wideo (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Editing-Python-Code-r2iQH5LWE_4605918567) demonstracyjne edycji kodu w języku Python (2 mln 30 sekund).|

Ogólna dokumentacja na temat edytowania kodu w programie Visual Studio, można zobaczyć [funkcje edytora kodu](../ide/writing-code-in-the-code-and-text-editor.md). Zobacz też [konspekt](../ide/outlining.md), co pomoże Ci bieżąco koncentruje się na określonych sekcji kodu.

Można również używać programu Visual Studio **przeglądarki obiektów** (**widoku** > **Windows inne** > **przeglądarki obiektów**lub **Ctrl**+**W** > **"j"**) do sprawdzania klasy Python określone w każdym module i funkcji zdefiniowanych w tych klasy.

## <a name="intellisense"></a>IntelliSense

Technologia IntelliSense zawiera [uzupełnienia](#completions), [pomocy dotyczącej sygnatur](#signature-help), [szybka podpowiedź](#quick-info), i [kolorowanie kodu](#code-coloring). Visual Studio 2017 w wersji 15.7 lub nowszej obsługują także [wskazówek dotyczących typów](#type-hints).

Aby zwiększyć wydajność, funkcja IntelliSense w **programu Visual Studio 2017 w wersji 15.5** i wcześniej zależy od bazy danych uzupełniania, który jest generowany dla każdego środowiska Python w projekcie. Bazy danych może być konieczne odświeżenie, jeśli dodać, usunąć lub zaktualizować pakiety. Stan bazy danych jest wyświetlany w **środowiska Python** okna (element równorzędny **Eksploratora rozwiązań**) na **IntelliSense** kartę (zobacz [okna środowiska Dokumentacja](python-environments-window-tab-reference.md#intellisense-tab)).

**Visual Studio 2017 w wersji 15.6** później przy użyciu różnych środków dostarcza uzupełnianiu IntelliSense, które nie są zależne od bazy danych.

### <a name="completions"></a>Uzupełnianie

Uzupełnianie są traktowane jako instrukcji, identyfikatorów i słów, które mogą być wprowadzane prawidłowo w bieżącej lokalizacji w edytorze. Co to jest wyświetlane na liście jest na podstawie kontekstu i jest filtrowana, aby pominąć opcje niepoprawne lub rozprasza uwagę. Uzupełnianie często są wyzwalane, wpisując różne instrukcje (takie jak `import`) i operatory (w tym okresie), ale można je pojawiają się w dowolnym momencie, wpisując **Ctrl**+**"j"**  >  **Miejsca**.

![Uzupełnianie składowych w edytorze programu Visual Studio](media/code-editing-completions-simple.png)

Po otwarciu listy uzupełniania, można wyszukać uzupełnianie przy użyciu klawiszy strzałek, mysz, lub, przechodząc do typu. Podczas pisania więcej liter listy jest dalej filtrowana pokazanie prawdopodobnie uzupełnienia. Można również użyć skrótów takich jak:

- Wpisywanie liter, które nie znajdują się na początku nazwy, np. analizy, aby znaleźć "argparse"
- Wpisanie tylko liter, które są na początku wyrazy, takie jak "abc", aby znaleźć "AbstractBaseClass" lub "air", aby znaleźć "as_integer_ratio"
- Pomijanie liter, takich jak b64, aby znaleźć "base64"

Kilka przykładów:

![Uzupełnianie składowych z filtrowaniem w edytorze programu Visual Studio](media/code-editing-completion-filtering.png)

Uzupełnienia Członkowskie pojawiają się automatycznie, gdy wpiszesz kropkę po zmiennej lub wartość, oraz metody i atrybuty potencjalnych typów. Jeśli zmienna może być więcej niż jeden typ, lista zawiera wszystkie możliwości ze wszystkich typów, przy użyciu dodatkowych informacji, aby wskazać, typy, które obsługują każdego uzupełnianie. W przypadku, gdy uzupełniania jest obsługiwana przez wszystkie możliwe typy, przedstawiono bez adnotacji.

![Uzupełnianie składowych na wiele typów w edytorze programu Visual Studio](media/code-editing-completion-types.png)

Domyślnie członkowie "dunder" (członkowie rozpoczynający się i kończy z podwójnym podkreśleniem) nie są wyświetlane. Ogólnie rzecz biorąc takich elementów członkowskich nie powinna być dostępna bezpośrednio. Jeśli potrzebujesz jednej, wpisując wiodącego podwójnego podkreślenia dodaje te uzupełnienia do listy:

![Uzupełnianie prywatnego elementu członkowskiego w edytorze programu Visual Studio](media/code-editing-completion-dunder.png)

`import` i `from ... import` instrukcji wyświetlić listę modułów, które mogą zostać zaimportowane. Za pomocą `from ... import`, lista zawiera elementy członkowskie, które mogą zostać zaimportowane z określonym module.

![Importowanie uzupełnianie w edytorze programu Visual Studio](media/code-editing-completion-import.png)

`raise` i `except` instrukcje wyświetlania list klas, które mogą być typów błędów. Lista może nie zawierać wszystkich wyjątków zdefiniowanych przez użytkownika, ale pomaga szybko znaleźć odpowiednie wyjątki wbudowane:

![Uzupełnianie wyjątek w edytorze programu Visual Studio](media/code-editing-completion-exception.png)

Wpisywanie uruchamia dekoratora i pokazuje potencjalne dekoratory. Wiele z tych elementów nie są możliwe do użycia jako dekoratory; Zapoznaj się z dokumentacją biblioteki, aby określić, której mają zostać użyte.

![Uzupełnianie dekoratora w edytorze programu Visual Studio](media/code-editing-completion-decorator.png)

> [!Tip]
> Można skonfigurować zachowanie uzupełniania za pośrednictwem **narzędzia** > **opcje** > **edytora tekstów**  >   **Python** > **zaawansowane**. Wśród nich **listy filtrów na podstawie wyszukiwania ciągu** stosuje filtrowanie sugestie uzupełniania podczas wpisywania (pole jest domyślnie zaznaczone), i **uzupełnianie składowych Wyświetla część wspólną członków** zawiera tylko uzupełnianie, które są obsługiwane przez wszystkie możliwe typy (Domyślnie zaznaczenie jest usunięte). Zobacz [opcje — wyniki zakończenia](python-support-options-and-settings-in-visual-studio.md#completion-results).

### <a name="type-hints"></a>Wskazówek dotyczących typów

*Visual Studio 2017 w wersji 15.7 lub nowszej.*

"Wskazówek dotyczących typów" w języku Python 3.5 + ([484 program ten](https://www.python.org/dev/peps/pep-0484/) (python.org) jest składnia adnotacji dla funkcji i klas, które wskazują typy argumentów, zwracać wartości i atrybuty klasy. Funkcja IntelliSense wyświetla wskazówek dotyczących typów, po najechaniu kursorem na wywołania funkcji, argumentów i zmiennych, które mają tych adnotacji.

W poniższym przykładzie `Vector` klasy jest zadeklarowana jako `List[float]`i `scale` funkcja zawiera wskazówek dotyczących typów dla jego argumentów i wartości zwracanej. Kursor wywołanie tej funkcji zawiera wskazówek dotyczących typów:

![Kursor wywołanie funkcji, aby wyświetlić wskazówek dotyczących typów](media/code-editing-type-hints1.png)

W poniższym przykładzie można zobaczyć jak atrybuty z adnotacjami `Employee` klasy są wyświetlane w okienku wyskakującym uzupełniania IntelliSense dla atrybutu:

![Wskazówki typu przedstawiający uzupełniania IntelliSense](media/code-editing-type-hints2.png)

Warto także sprawdzić poprawność wskazówek dotyczących typów w całym projekcie, ponieważ błędy zwykle nie są wyświetlane do czasu wykonywania. W tym celu program Visual Studio integruje się branży narzędzie MyPy standard za pomocą polecenia menu kontekstowego **Python** > **Uruchom narzędzie Mypy** w **Eksploratora rozwiązań**:

![Uruchom narzędzie MyPy polecenie z menu kontekstowego w Eksploratorze rozwiązań](media/code-editing-type-hints-run-mypy.png)

Uruchomiony wiersz polecenia do zainstalowania pakietu mypy, jeśli potrzebna. Visual Studio uruchamia następnie mypy w celu zweryfikowania wskazówek dotyczących typów w każdym pliku Python w projekcie. Błędy są wyświetlane w programie Visual Studio **lista błędów** okna. Zaznaczenie elementu w oknie powoduje przejście do odpowiedniego wiersza kodu.

Prostym przykładem następującą definicję funkcji zawiera wskazówki typu w celu wskazania, że `input` argument jest typu `str`, podczas gdy wywołaniu tej funkcji, podejmie próbę przekazać liczbę całkowitą:

```python
def commas_to_colons(input: str):
    items = input.split(',')
    items = [x.strip() for x in items]
    return ':'.join(items)

commas_to_colons(1)
```

Za pomocą **Uruchom narzędzie Mypy** polecenie na ten kod generuje następujący błąd:

![Przykład wyniku sprawdzania poprawności wskazówek dotyczących typów mypy](media/code-editing-type-hints-validation-error.png)

> [!Tip]
> W przypadku wersji środowiska Python wcześniejsze niż 3.5, Visual Studio wyświetla również wskazówek dotyczących typów, które należy podać za pośrednictwem *namiastki pliki* (*.pyi*). Można użyć pliki szczątkowe, zawsze wtedy, gdy nie chcesz uwzględnić wskazówek dotyczących typów bezpośrednio w kodzie lub w przypadku, gdy chcesz utworzyć wskazówek dotyczących typów, biblioteki, która nie korzysta z ich bezpośrednio. Aby uzyskać więcej informacji, zobacz [tworzenia wycinków dla modułów języka Python](https://github.com/python/mypy/wiki/Creating-Stubs-For-Python-Modules) w witrynie Wiki dotyczącej projektu mypy.
>
> Obecnie program Visual Studio nie obsługuje wskazówek dotyczących typów w komentarzach.

### <a name="signature-help"></a>Pomocy dotyczącej sygnatur

Podczas pisania kodu, który wywołuje funkcję pomocy dotyczącej sygnatur pojawia się po wpisaniu otwarcia `(` i wyświetla dostępne informacje dotyczące dokumentacji i parametrów. Można również wyświetlić ją za pomocą **Ctrl**+**Shift**+**miejsca** wewnątrz wywołania funkcji. Informacje wyświetlane jest zależna od ciągów dokumentacji w kodzie źródłowym funkcji, ale zawiera wartości domyślne.

![Pomocy dotyczącej sygnatur w edytorze programu Visual Studio](media/code-editing-signature-help.png)

> [!Tip]
> Aby wyłączyć pomocy dotyczącej sygnatur, przejdź do **narzędzia** > **opcje** > **edytora tekstów** > **Python**  >  **Ogólne** i wyczyść **uzupełniania instrukcji** > **informacje o parametrach**.

### <a name="quick-info"></a>Szybkie informacje

Kursor myszy nad identyfikator są wyświetlane etykietki narzędzia Szybkie informacje. W zależności od identyfikatora szybkie informacje mogą być wyświetlane potencjalnych wartości lub typy, dowolnej dostępnej dokumentacji, zwracane typy i lokalizacje definicji:

![Szybkie informacje w edytorze programu Visual Studio](media/code-editing-quick-info.png)

### <a name="code-coloring"></a>Kolorowanie kodu

Kolorowanie kodu używa informacji z analizy kodu do zmiennych koloru, instrukcje i inne części kodu. Na przykład zmienne, które odwołują się do modułów lub klasy mogą być wyświetlane w innym kolorze niż funkcji lub innych wartości i nazwy parametrów są wyświetlane w innym kolorze niż zmiennych lokalnych lub globalnych. (Domyślnie, funkcje nie są wyświetlane pogrubioną czcionką):

![Kod i kolorowanie składni w edytorze programu Visual Studio](media/code-editing-code-coloring.png)

Aby dostosować kolory, przejdź do **narzędzia** > **opcje** > **środowiska** > **czcionki i kolory** i modyfikować **Python** wpisów w **wyświetlania elementów** listy:

![Opcje czcionek i kolorów w programie Visual Studio](media/code-editing-customize-colors.png)

> [!Tip]
> Aby wyłączyć kolorowaniem kodu, przejdź do **narzędzia** > **opcje** > **edytora tekstów** > **Python**  >  **Zaawansowane** i wyczyść **różne opcje** > **koloru na podstawie typu nazwy**. Zobacz [opcje - różne opcje](python-support-options-and-settings-in-visual-studio.md#miscellaneous-options).

## <a name="code-snippets"></a>Fragmenty kodu

Fragmenty kodu pochodzą z fragmentami kodu, które mogą być wstawiane do plików, wpisując skrót, a następnie naciskając klawisz **kartę**, lub za pomocą **Edytuj** > **IntelliSense**  >  **Wstaw fragment kodu** i **Otocz** polecenia, wybierając **Python**, a następnie wybierając żądany fragment kodu.

Na przykład `class` jest skrótem dla fragmentu kodu, który wstawia definicji klasy. Zostanie wyświetlony fragment kodu, są wyświetlane na liście automatycznego uzupełniania, podczas wpisywania tekstu `class`:

![Fragment kodu dotyczący skrótów klasy](media/code-editing-code-snippet-class.png)

Naciśnięcie klawisza **kartę** generuje pozostałą część tej klasy. Możesz wpisać nazwy i typy bazowe listą przechodzenia między wyróżnione pola z **kartę**, naciśnij klawisz **Enter** do rozpoczęcia pisania treści.

![Najważniejsze funkcje w obszarach fragmentu kodu, aby móc wykonać](media/code-editing-code-snippets.png)

### <a name="menu-commands"></a>Polecenia menu

Kiedy używasz **Edytuj** > **IntelliSense** > **Wstaw fragment kodu** polecenia menu, najpierw wybierz **Python**, następnie wybierz fragment kodu:

![Wybierając fragment kodu za pomocą polecenia Wstaw fragment kodu](media/code-editing-code-snippet-insert.png)

**Edytuj** > **IntelliSense** > **Otocz** polecenie podobnie umieszcza bieżące zaznaczenie w edytorze tekstów wewnątrz wybrane element strukturalnych. Na przykład załóżmy, że masz ilość kodu, jak pokazano poniżej:

```python
sum = 0
for x in range(1, 100):
    sum = sum + x
```

Wybierając ten kod i wybierając pozycję **Otocz** polecenie wyświetla listę dostępnych fragmentów kodu. Wybieranie **def** z listy umieszcza zaznaczony kod w definicji funkcji, na które można użyć **kartę** klawisz, aby przechodzić między nazwą funkcji wyróżnione i argumenty:

![Za pomocą polecenia Otocz wstawek kodu](media/code-editing-code-snippet-surround-with.png)

### <a name="examine-available-snippets"></a>Sprawdź dostępne fragmenty kodu

Możesz zobaczyć fragmenty kodu dostępne w **Menedżera wstawek kodu**, otwartego za pomocą **narzędzia** > **Menedżera wstawek kodu** polecenia menu i wybierając polecenie **Python** jako język:

![Menedżer fragmentów kodu w programie Visual Studio](media/code-editing-code-snippets-manager.png)

Aby utworzyć własne fragmenty kodu, zobacz [wskazówki: Tworzenie fragmentu kodu](../ide/walkthrough-creating-a-code-snippet.md).

Jeśli piszesz fragmentu świetnego kodu, które chcesz udostępnić, możesz opublikować ją w gist i [Daj nam znać](https://github.com/Microsoft/PTVS/issues). Firma Microsoft może mieć uwzględniania go w przyszłej wersji programu Visual Studio.

## <a name="navigate-your-code"></a>Poruszanie się po kodzie

Obsługa języka Python w programie Visual Studio zawiera kilka oznacza, że można szybko przejść w kodzie, w tym bibliotek, dla którego źródło kod jest dostępny: [pasek nawigacyjny](#navigation-bar), [ **przejdź do definicji** ](#go-to-definition), [ **Przejdź do**](#navigate-to), i [ **Znajdź wszystkie odwołania**](#find-all-references). Można również używać programu Visual Studio [ **przeglądarki obiektów**](../ide/viewing-the-structure-of-code.md#BKMK_ObjectBrowser).

### <a name="navigation-bar"></a>Pasek nawigacyjny

Na pasku nawigacyjnym jest wyświetlana w górnej części każdego okna edytora i zawiera listę dwupoziomowej definicji. Lista rozwijana po lewej stronie zawiera klasę najwyższego poziomu i definicje funkcji w bieżącym pliku; prawo rozwijanej Wyświetla listę definicji w zakresie wyświetlane po lewej stronie. Jak zmieniają położenie w edytorze list zaktualizowane, aby wyświetlić bieżący kontekst i można również wybrać wpis z tych list można przechodzić bezpośrednio do.

! [Pasek nawigacyjny] w editor(media/code-editing-navigation-bar.png) programu Visual Studio

> [!Tip]
> Aby ukryć pasek nawigacyjny, przejdź do **narzędzia** > **opcje** > **edytora tekstów** > **Python**  >  **Ogólne** i wyczyść **ustawienia** > **pasek nawigacyjny**.

### <a name="go-to-definition"></a>Przejdź do definicji

**Przejdź do definicji** szybko przechodzi z użytkowania identyfikator (np. nazwę funkcji, klasy lub zmiennej), do kodu źródłowego którym jest zdefiniowana. Można wywołać, klikając prawym przyciskiem myszy identyfikator i wybierając **przejdź do definicji** lub umieszczając karetkę na identyfikator i naciskając klawisz **F12**. Działa ona za pośrednictwem kodu oraz zewnętrznych bibliotekach pod warunkiem, że kod źródłowy jest dostępny. Jeśli kod źródłowy biblioteki nie jest dostępna, **przejdź do definicji** skacze do odpowiedniego `import` poufności informacji dla odwołania do modułu, lub wyświetla komunikat o błędzie.

![Polecenie Przejdź do definicji w programie Visual Studio](media/code-editing-go-to-definition.png)

### <a name="navigate-to"></a>Przejdź do

**Edytuj** > **przejdź do** polecenia (**Ctrl**+**,**) Wyświetla pola wyszukiwania w edytorze gdzie możesz można wpisać dowolny ciąg i wyświetlić możliwych dopasowań w kodzie, który definiuje funkcję, klasę lub zmienną, która zawiera ciąg. Ta funkcja udostępnia podobną funkcję jak **przejdź do definicji** , ale bez konieczności zlokalizować Użyj identyfikatora.

Dwukrotne kliknięcie dowolną nazwę, albo wybierz przy użyciu klawiszy strzałek oraz **Enter**, przechodzi do definicji tego identyfikatora.

![Przejdź do polecenia w programie Visual Studio](media/code-editing-navigate-to.png)

### <a name="find-all-references"></a>Znajdź wszystkie odwołania

**Znajdź wszystkie odwołania** jest pomocny sposób odnajdowania, gdzie jest zarówno z dowolnym danym identyfikatorem zdefiniowane i używane w tym Importy i przydziałów. Można wywołać, klikając prawym przyciskiem myszy identyfikator i wybierając **Znajdź wszystkie odwołania**, lub umieszczając karetkę na identyfikator i naciskając klawisz **Shift**+**F12**. Dwukrotne kliknięcie elementu na liście powoduje przejście do jego lokalizacji.

![Znajdź wszystkie odwołania wyniki](media/code-editing-find-all-references.png)

## <a name="see-also"></a>Zobacz także

- [Formatowanie](formatting-python-code.md)
- [Refaktoryzacja](refactoring-python-code.md)
- [Użyj linter](linting-python-code.md)

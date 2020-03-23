---
title: Edytowanie kodu w języku Python
description: W przypadku języka Python visual studio udostępnia bogate intellisense, fragmenty kodu i funkcje nawigacji, obok formatowania, linting i refaktoryzacji.
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "73024721"
---
# <a name="edit-python-code"></a>Edytowanie kodu w języku Python

Ponieważ spędzasz dużo czasu na programach programistów w edytorze kodu, [obsługa języka Python w programie Visual Studio](installing-python-support-in-visual-studio.md) zapewnia funkcje, które pomogą Ci zwiększyć produktywność. Funkcje obejmują wyróżnianie składni IntelliSense, automatyczne uzupełnianie, pomoc dotyczącą podpisu, zastępowanie metody, wyszukiwanie i nawigację.

Edytor jest również zintegrowany z **interaktywnym** oknem w programie Visual Studio, dzięki czemu można łatwo wymienić kod między nimi. Zobacz [samouczek Krok 3: Użyj interaktywnego okna REPL](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md) i [użyj interaktywnego okna — Wyślij do interaktywnego polecenia, aby](python-interactive-repl-in-visual-studio.md#send-to-interactive-command) uzyskać szczegółowe informacje.

Aby uzyskać ogólną dokumentację dotyczącą edytowania kodu w programie Visual Studio, zobacz [Funkcje edytora kodu](../ide/writing-code-in-the-code-and-text-editor.md). Zobacz także [Konspekt](../ide/outlining.md), który pomaga skupić się na poszczególnych sekcjach kodu.

Można również użyć **przeglądarki obiektów** programu Visual Studio (**Zobacz** > inne**przeglądarki obiektów** **systemu Windows** > lub **Ctrl**+**W** > **J**) do sprawdzania klas Języka Python zdefiniowanych w każdym module i funkcji zdefiniowanych w tych klasach.

## <a name="intellisense"></a>IntelliSense

IntelliSense zapewnia [uzupełnienia,](#completions) [pomoc podpisu,](#signature-help) [szybkie informacje](#quick-info)i [kolorowanie kodu.](#code-coloring) Program Visual Studio 2017 w wersji 15.7 i nowszych obsługują również [wskazówki dotyczące typów.](#type-hints)

Aby zwiększyć wydajność, IntelliSense w programie Visual Studio 2017 w wersji 15.5 i wcześniejszych zależy od bazy danych ukończenia, który jest generowany dla każdego środowiska języka Python w projekcie. Bazy danych mogą wymagać odświeżenia, jeśli dodasz, usuniesz lub zaktualizujesz pakiety. Stan bazy danych jest wyświetlany w oknie **Środowiska języka Python** (równorzędne **Eksploratora rozwiązań)** na karcie **IntelliSense** (zobacz [odwołanie do okna Środowiska).](python-environments-window-tab-reference.md)

Visual Studio 2017 w wersji 15.6 i nowszych używa innego środka, aby zapewnić intellisense uzupełnień, które nie są zależne od bazy danych.

### <a name="completions"></a>Completions

Uzupełnienia są wyświetlane jako instrukcje, identyfikatory i inne wyrazy, które mogą być odpowiednio wprowadzone w bieżącej lokalizacji w edytorze. To, co jest wyświetlane na liście, jest oparte na kontekście i jest filtrowane w celu pominięcia nieprawidłowych lub rozpraszających opcji. Uzupełnienia są często wyzwalane przez wpisanie `import`różnych instrukcji (takich jak) i operatorów (w tym kropki), ale można je wyświetlać w dowolnym momencie, wpisując **klawisz Ctrl**+**J** > **Space**.

![Ukończenie elementu członkowskiego w edytorze programu Visual Studio](media/code-editing-completions-simple.png)

Gdy lista uzupełnień jest otwarta, można wyszukać zakończenie, które ma być używane za pomocą klawiszy strzałek, myszy lub kontynuując wpisywać. Podczas wpisywalnych kolejnych liter lista jest dalej filtrowana, aby wyświetlić prawdopodobne uzupełnienia. Można również użyć skrótów, takich jak:

- Wpisywanie liter, które nie znajdują się na początku nazwy, takie jak "analizowanie", aby znaleźć "argparse"
- Wpisywanie tylko liter, które znajdują się na początku słów, takich jak "abc", aby znaleźć "AbstractBaseClass" lub "air", aby znaleźć "as_integer_ratio"
- Pomijanie liter, takich jak "b64", aby znaleźć "base64"

Oto niektóre przykłady:

![Ukończenie elementu członkowskiego za pomocą filtrowania w edytorze visual studio](media/code-editing-completion-filtering.png)

Uzupełnienia elementów członkowskich pojawiają się automatycznie po wpisaniu kropki po zmiennej lub wartości, wraz z metodami i atrybutami potencjalnych typów. Jeśli zmienna może być więcej niż jeden typ, lista zawiera wszystkie możliwości ze wszystkich typów, z dodatkowymi informacjami, aby wskazać, które typy obsługują każdego zakończenia. Jeśli zakończenie jest obsługiwane przez wszystkie możliwe typy, jest wyświetlany bez adnotacji.

![Uzupełnianie elementów członkowskich w wielu typach w edytorze programu Visual Studio](media/code-editing-completion-types.png)

Domyślnie nie są wyświetlane elementy członkowskie "dunder" (elementy rozpoczynające się i kończące z podwójnym podkreśleniem). Ogólnie rzecz biorąc, takie elementy członkowskie nie powinny być dostępne bezpośrednio. Jeśli jednak potrzebujesz, wpisanie wiodącego podwójnego podkreślenia powoduje dodanie tych uzupełnień do listy:

![Ukończenie prywatnego elementu członkowskiego w edytorze programu Visual Studio](media/code-editing-completion-dunder.png)

`import` Instrukcje `from ... import` i instrukcje wyświetlają listę modułów, które można zaimportować. Z `from ... import`, lista zawiera elementy członkowskie, które mogą być importowane z określonego modułu.

![Importowanie uzupełniania w edytorze programu Visual Studio](media/code-editing-completion-import.png)

`raise` Instrukcje `except` i wyświetlać listy klas, które mogą być typy błędów. Lista może nie zawierać wszystkich wyjątków zdefiniowanych przez użytkownika, ale pomaga szybko znaleźć odpowiednie wbudowane wyjątki:

![Ukończenie wyjątku w edytorze programu Visual Studio](media/code-editing-completion-exception.png)

Wpisując @ uruchamia dekoratora i pokazuje potencjalnych dekoratorów. Wiele z tych przedmiotów nie nadają się do użytku jako dekoratorzy; sprawdź dokumentację biblioteki, aby określić, którego użyć.

![Ukończenie dekoratora w edytorze programu Visual Studio](media/code-editing-completion-decorator.png)

> [!Tip]
> Zachowanie uzupełnień można skonfigurować za pomocą **funkcji Narzędzia** > **Opcje** > **Edytor** > tekstu**Python** > **Advanced**. Wśród nich **lista filtrów na podstawie ciągu wyszukiwania** stosuje filtrowanie sugestii ukończenia podczas pisania (domyślnie jest zaznaczone), a **ukończenie elementu członkowskiego wyświetla przecięcie elementów członkowskich** pokazuje tylko uzupełnienia, które są obsługiwane przez wszystkie możliwe typy (domyślnie nie jest zaznaczone). Zobacz [Opcje - wyniki ukończenia](python-support-options-and-settings-in-visual-studio.md#completion-results).

### <a name="type-hints"></a>Wskazówki dotyczące wpisywać

*Visual Studio 2017 w wersji 15.7 i nowszych.*

"Wskazówki dotyczące typu" w języku Python 3.5+[(PEP 484](https://www.python.org/dev/peps/pep-0484/) (python.org) to składnia adnotacji dla funkcji i klas, które wskazują typy argumentów, zwracane wartości i atrybuty klasy. IntelliSense wyświetla wskazówki dotyczące typu po umieszczeniu wskaźnika myszy na wywołaniach funkcji, argumentach i zmiennych, które mają te adnotacje.

W poniższym przykładzie `Vector` klasa `List[float]`jest zadeklarowana jako , a `scale` funkcja zawiera wskazówki dotyczące typu zarówno dla jego argumentów, jak i wartości zwracanej. Najechanie kursorem na wywołanie tej funkcji pokazuje wskazówki dotyczące typu:

![Najechanie kursorem na wywołanie funkcji w celu ujawnienia wskazówek dotyczących typu](media/code-editing-type-hints1.png)

W poniższym przykładzie można zobaczyć, jak atrybuty z adnotacjami `Employee` klasy są wyświetlane w wyskakującym okienku intellisense zakończenia dla atrybutu:

![Zakończenie intellisense z podpowiedziami typu](media/code-editing-type-hints2.png)

Jest również przydatne do sprawdzania poprawności wskazówek dotyczących typu w całym projekcie, ponieważ błędy zwykle nie będą wyświetlane do czasu wykonywania. W tym celu program Visual Studio integruje standardowe narzędzie MyPy za pomocą polecenia menu kontekstowego **Python** > **Run Mypy** w **Eksploratorze rozwiązań:**

![Polecenie Uruchom menu kontekstowe MyPy w Eksploratorze rozwiązań](media/code-editing-type-hints-run-mypy.png)

Uruchomienie polecenia powoduje wyświetlenie monitu o zainstalowanie pakietu mypy w razie potrzeby. Visual Studio następnie uruchamia mypy, aby sprawdzić poprawność wskazówek dotyczących typu w każdym pliku języka Python w projekcie. Błędy są wyświetlane w oknie **Lista błędów** programu Visual Studio. Wybranie elementu w oknie przechodzi do odpowiedniego wiersza w kodzie.

Jako prosty przykład następująca definicja funkcji zawiera wskazówkę typu, aby wskazać, że `input` argument jest typem `str`, podczas gdy wywołanie tej funkcji próbuje przekazać całkowitą wartość:

```python
def commas_to_colons(input: str):
    items = input.split(',')
    items = [x.strip() for x in items]
    return ':'.join(items)

commas_to_colons(1)
```

Użycie polecenia **Uruchom Mypy** w tym kodzie generuje następujący błąd:

![Przykładowy wynik mypy sprawdzania poprawności wskazówek dotyczących typu](media/code-editing-type-hints-validation-error.png)

::: moniker range="vs-2017"
> [!Tip]
> W przypadku wersji języka Python przed wersją 3.5 program Visual Studio wyświetla również wskazówki dotyczące typów, które są wyświetlane za pośrednictwem *plików skrótowych* Typeshed (*.pyi*). Pliki skrótowe można używać zawsze, gdy nie chcesz dołączać wskazówek o typie bezpośrednio do kodu lub gdy chcesz utworzyć wskazówki dotyczące typu dla biblioteki, która nie używa ich bezpośrednio. Aby uzyskać więcej informacji, zobacz [Tworzenie wycinków dla modułów języka Python](https://github.com/python/mypy/wiki/Creating-Stubs-For-Python-Modules) na wiki projektu mypy.
>
> Obecnie visual studio nie obsługuje wskazówek typu w komentarzach.
::: moniker-end
::: moniker range=">=vs-2019"
> [!Tip]
> W przypadku wersji języka Python przed wersją 3.5 program Visual Studio wyświetla również wskazówki dotyczące typów, które są wyświetlane za pośrednictwem *plików skrótowych* Typeshed (*.pyi*). Pliki skrótowe można używać zawsze, gdy nie chcesz dołączać wskazówek o typie bezpośrednio do kodu lub gdy chcesz utworzyć wskazówki dotyczące typu dla biblioteki, która nie używa ich bezpośrednio. Aby uzyskać więcej informacji, zobacz [Tworzenie wycinków dla modułów języka Python](https://github.com/python/mypy/wiki/Creating-Stubs-For-Python-Modules) na wiki projektu mypy.
>
> Visual Studio zawiera zestaw plików Typeshed dla języka Python 2 i 3, więc dodatkowe pliki do pobrania nie są konieczne. Jeśli jednak chcesz użyć innego zestawu plików, możesz określić ścieżkę w opcjach **narzędzia** > **Opcje** > **serwera języka** **Python.** >  Zobacz [Opcje - Serwer języka](python-support-options-and-settings-in-visual-studio.md#language-server-options).
>
> Obecnie visual studio nie obsługuje wskazówek typu w komentarzach.
::: moniker-end

### <a name="signature-help"></a>Pomoc dotycząca podpisu

Podczas pisania kodu, który wywołuje funkcję, pomoc `(` podpisu pojawia się po wpisaniu otwierania i wyświetla dostępną dokumentację i informacje o parametrach. Można również sprawić, że pojawi się z **ctrl**+**shift**+**space** wewnątrz wywołania funkcji. Wyświetlane informacje zależą od ciągów dokumentacji w kodzie źródłowym funkcji, ale zawierają wszystkie wartości domyślne.

![Pomoc dotycząca podpisu w edytorze programu Visual Studio](media/code-editing-signature-help.png)

> [!Tip]
> Aby wyłączyć pomoc dotyczącą podpisu, przejdź do pozycji**Edytor** > tekstu**Options** >  **Narzędzia** > **Python** > **Ogólne** i wyczyść informacje o**parametrach** **uzupełniania** > instrukcji .

### <a name="quick-info"></a>Szybkie informacje

Najechanie wskaźnika myszy na identyfikator powoduje wyświetlenie etykietki narzędzia Szybkie informacje. W zależności od identyfikatora szybkie informacje mogą wyświetlać potencjalne wartości lub typy, dowolną dostępną dokumentację, typy zwrotów i lokalizacje definicji:

![Szybkie informacje w edytorze programu Visual Studio](media/code-editing-quick-info.png)

### <a name="code-coloring"></a>Kolorowanie kodu

Kolorowanie kodu używa informacji z analizy kodu do zmiennych kolorów, instrukcji i innych części kodu. Na przykład zmienne, które odwołują się do modułów lub klas mogą być wyświetlane w innym kolorze niż funkcje lub inne wartości, a nazwy parametrów są wyświetlane w innym kolorze niż zmienne lokalne lub globalne. (Domyślnie funkcje nie są wyświetlane pogrubioną czcionką):

![Kolorowanie kodu i składni w edytorze programu Visual Studio](media/code-editing-code-coloring.png)

Aby dostosować kolory, przejdź > do pozycji > **Czcionki** > **i kolory** **środowiska** **Opcje narzędzi**i zmodyfikuj wpisy **języka Python** na liście **Elementy wyświetlane:**

![Opcje czcionek i kolorów w programie Visual Studio](media/code-editing-customize-colors.png)

> [!Tip]
> Aby wyłączyć kolorowanie kodu, przejdź do **edytora** > **Options** > **tekstu** > Narzędzia**Python** > **Zaawansowane** i **wyczyść** > różne**opcje nazwy kolorów na podstawie typu**. Zobacz [Opcje — różne opcje](python-support-options-and-settings-in-visual-studio.md#miscellaneous-options).

## <a name="code-snippets"></a>Fragmenty kodu

Fragmenty kodu to fragmenty kodu, które można wstawiać do plików, wpisując skrót i naciskając **klawisz Tab**lub używając poleceń **Edytuj** > fragment kodu**IntelliSense** > **Insert Code** i Surround **With,** wybierając **python,** a następnie wybierając żądany fragment kodu.

Na przykład `class` jest skrótem do fragmentu kodu, który wstawia definicję klasy. Fragment kodu jest wyświetlany na liście automatycznego uzupełniania `class`po wpisaniu:

![Fragment kodu skrótu klasy](media/code-editing-code-snippet-class.png)

Naciśnięcie **klawisza Tab** generuje resztę klasy. Następnie można wpisać listę nazw i baz, przechodząc między wyróżnionymi polami za pomocą **karty**, a następnie naciśnij **klawisz Enter,** aby rozpocząć wpisywanie obiektu.

![Najważniejsze informacje o obszarach fragmentu kodu, które można ukończyć](media/code-editing-code-snippets.png)

### <a name="menu-commands"></a>Polecenia menu

Korzystając z polecenia menu Edytuj fragment kodu > **IntelliSense** > **Wstaw kod,** najpierw wybierz **python**, a następnie wybierz fragment kodu: **Edit**

![Wybieranie fragmentu kodu za pomocą polecenia Wstaw fragment kodu](media/code-editing-code-snippet-insert.png)

Polecenie **Edytuj** > **intellisense** > surround**z** podobnie umieszcza bieżące zaznaczenie w edytorze tekstu wewnątrz wybranego elementu strukturalnego. Załóżmy na przykład, że masz trochę kodu, jak następujące:

```python
sum = 0
for x in range(1, 100):
    sum = sum + x
```

Wybranie tego kodu i wybranie polecenia **Surround With** powoduje wyświetlenie listy dostępnych fragmentów kodu. Wybranie **def** z listy umieszcza wybrany kod w definicji funkcji i można użyć **klawisza Tab,** aby poruszać się między wyróżnioną nazwą funkcji a argumentami:

![Używanie polecenia Surround With dla fragmentów kodu](media/code-editing-code-snippet-surround-with.png)

### <a name="examine-available-snippets"></a>Sprawdzanie dostępnych urywków

Dostępne fragmenty kodu można zobaczyć w **Menedżerze urywków kodu,** otwartym za pomocą polecenia menu**Menedżer urywków** **kodu narzędzi** > i wybraniu **języka Python** jako języka:

![Menedżer urywków kodu w programie Visual Studio](media/code-editing-code-snippets-manager.png)

Aby utworzyć własne fragmenty kodu, zobacz [Instruktaż: Tworzenie fragmentu kodu](../ide/walkthrough-creating-a-code-snippet.md).

Jeśli piszesz świetny fragment kodu, który chcesz udostępnić, możesz opublikować go w sednach i [daj nam znać.](https://github.com/Microsoft/PTVS/issues) Możemy być w stanie uwzględnić go w przyszłej wersji programu Visual Studio.

## <a name="navigate-your-code"></a>Poruszanie się po kodzie

Obsługa języka Python w programie Visual Studio zapewnia kilka sposobów szybkiego poruszania się po kodzie, w tym biblioteki, dla których dostępny jest kod źródłowy: [pasek nawigacyjny](#navigation-bar), Przejdź [**do definicji,**](#go-to-definition) [**Przejdź do**](#navigate-to)i znajdź [**wszystkie odwołania.**](#find-all-references) Można również użyć [**przeglądarki obiektów**](../ide/viewing-the-structure-of-code.md#BKMK_ObjectBrowser)programu Visual Studio .

### <a name="navigation-bar"></a>Pasek nawigacyjny

Pasek nawigacyjny jest wyświetlany w górnej części każdego okna edytora i zawiera dwupoziomową listę definicji. Lewica rozwijana zawiera definicje klas i funkcji najwyższego poziomu w bieżącym pliku; z prawej strony wyświetlana jest lista definicji w zakresie pokazanym po lewej stronie. Podczas poruszania się w edytorze listy są aktualizowane w celu wyświetlenia bieżącego kontekstu, a także można wybrać wpis z tych list, do którego można przejść bezpośrednio.

![Pasek nawigacyjny w edytorze programu Visual Studio](media/code-editing-navigation-bar.png)

> [!Tip]
> Aby ukryć pasek nawigacyjny, przejdź do pozycji**Edytor** > tekstu **Narzędzia** > **Options** > **Python** > **Ogólne** i wyczyść**pasek nawigacyjny** **Ustawienia** > .

### <a name="go-to-definition"></a>Przejdź do definicji

**Przejdź do definicji** szybko przechodzi z użycia identyfikatora (na przykład nazwę funkcji, klasy lub zmiennej), do kodu źródłowego, w którym jest zdefiniowany. Wywołujesz go, klikając prawym przyciskiem myszy identyfikator i wybierając **opcję Przejdź do definicji** lub umieszczając karetkę w identyfikatorze i naciskając **klawisz F12**. Działa w całym kodzie i bibliotekach zewnętrznych, pod warunkiem, że kod źródłowy jest dostępny. Jeśli kod źródłowy biblioteki nie jest dostępny, `import` Przejdź do **definicji** przeskakuje do odpowiedniej instrukcji dla odwołania do modułu lub wyświetla błąd.

![Polecenie Przejdź do definicji w programie Visual Studio](media/code-editing-go-to-definition.png)

### <a name="navigate-to"></a>Nawiguj do

Polecenie **Edytuj** > **nawiguj do** (**Ctrl**+) wyświetla w edytorze pole**wyszukiwania,** w którym można wpisać dowolny ciąg i zobaczyć możliwe dopasowania w kodzie definiujące funkcję, klasę lub zmienną zawierającą ten ciąg. Ta funkcja zapewnia podobną funkcję jak **Przejdź do definicji,** ale bez konieczności lokalizowania użycia identyfikatora.

Dwukrotne kliknięcie dowolnej nazwy lub wybranie za pomocą klawiszy strzałek i **klawisz Enter**przechodzi do definicji tego identyfikatora.

![Nawigowanie do polecenia w programie Visual Studio](media/code-editing-navigate-to.png)

### <a name="find-all-references"></a>Znajdź wszystkie odwołania

**Znajdź wszystkie odwołania** jest pomocnym sposobem wykrywania, gdzie dany identyfikator jest zdefiniowany i używany, w tym importu i przypisań. Wywołujesz go, klikając prawym przyciskiem myszy identyfikator i wybierając **pozycję Znajdź wszystkie odwołania**lub umieszczając karetkę w identyfikatorze i naciskając klawisz **Shift**+**F12**. Dwukrotne kliknięcie elementu na liście przechodzi do jego lokalizacji.

![Znajdź wszystkie odwołania wyniki](media/code-editing-find-all-references.png)

## <a name="see-also"></a>Zobacz też

- [Formatowanie](formatting-python-code.md)
- [Refaktoryzacja](refactoring-python-code.md)
- [Użyj linteru](linting-python-code.md)

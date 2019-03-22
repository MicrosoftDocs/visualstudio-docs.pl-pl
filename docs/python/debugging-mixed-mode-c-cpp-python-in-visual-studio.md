---
title: Trybu mieszanego debugowania dla języka Python
description: Jednocześnie debugować C++ i Python w programie Visual Studio, w tym przechodzenie między środowiskami, wyświetlanie wartości i wyrażeń.
ms.date: 11/12/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: fc7148e9ba2ad9882f42d3c2acdb067329ec4ee5
ms.sourcegitcommit: 3201da3499051768ab59f492699a9049cbc5c3c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2019
ms.locfileid: "58355237"
---
# <a name="debug-python-and-c-together"></a>Debugowanie języka Python i C++ razem

Najbardziej regularne debugery Python obsługi debugowania tylko kodu w języku Python. W praktyce jednak Python umożliwia w połączeniu z C lub C++ w scenariuszach wymagających wysokiej wydajności lub możliwości bezpośrednie wywoływanie interfejsów API platformy. (Zobacz [Tworzenie rozszerzenia C++ dla języka Python](working-with-c-cpp-python-in-visual-studio.md) przewodnik.)

Program Visual Studio zawiera zintegrowane, jednocześnie dla języka Python oraz natywnego języka C/C++, debugowanie w trybie mieszanym, pod warunkiem, że wybierzesz **Python natywne narzędzia programistyczne** opcja dla **programowania w języku Python** obciążenie w Instalatorze programu Visual Studio.

> [!Note]
> Debugowanie w trybie mieszanym nie jest dostępna za pomocą narzędzi Python Tools for Visual Studio 1.x w programie Visual Studio 2015 i starszych wersji.

Funkcje debugowania trybu mieszanego zawierają następujące informacje, jak wyjaśniono w tym artykule:

- Stosy wywołań połączone
- Krok między języka Python i kodu natywnego
- Punkty przerwania w przypadku obu typów kodu
- Zobacz Python reprezentacje obiektów w ramek natywnych i na odwrót
- Debugowanie w kontekście projektu w języku Python lub projektu C++

![Debugowanie w trybie mieszanym dla języka Python w programie Visual Studio](media/mixed-mode-debugging.png)

|   |   |
|---|---|
| ![Ikona aparatu film wideo](../install/media/video-icon.png "Obejrzyj klip wideo") | Wprowadzenie do tworzenia, testowania i debugowania natywnych modułów języka C z programem Visual Studio, zobacz [szczegółowe informacje: Tworzenie modułów macierzystych](https://youtu.be/D9RlT06a1EI) (witrynie youtube.com, 9 m 09s). Plik wideo ma zastosowanie do programu Visual Studio 2015 i 2017. |

## <a name="enable-mixed-mode-debugging-in-a-python-project"></a>Włącz debugowanie w trybie mieszanym w projekcie języka Python

1. Kliknij prawym przyciskiem myszy projekt języka Python w **Eksploratora rozwiązań**, wybierz opcję **właściwości**, wybierz opcję **debugowania** , a następnie wybierz pozycję **Włącz debugowanie kodu natywnego** . Ta opcja umożliwia trybu mieszanego sesji wszystkie debugowania.

    ![Włączanie debugowania kodu natywnego](media/mixed-mode-debugging-enable-native.png)

    > [!Tip]
    > Jeśli włączone jest debugowanie kodu natywnego, w oknie danych wyjściowych języka Python może zniknąć natychmiast po zakończeniu program bez umożliwiając zwykłego **naciśnij dowolny klawisz, aby kontynuować** wstrzymania. Aby wymusić przerwie, należy dodać `-i` opcję **Uruchom** > **argumenty Interpreter** na **debugowania** kartę, gdy włączone jest debugowanie kodu natywnego . Ten argument umieszcza interpreter języka Python w trybie interaktywnym po zakończeniu wykonywania kodu, w tym momencie czeka na naciśnięcie klawisza **Ctrl**+**Z** > **Enter**  aby wyjść.

1. Podczas dołączania debugera trybu mieszanego do istniejącego procesu (**debugowania** > **dołączyć do procesu**), użyj **wybierz** przycisk, aby otworzyć  **Vybrat typ kódu** okna dialogowego. Następnie ustaw **debugowania tych typów kodu** opcję i zaznacz **natywnych** i **Python** na liście:

    ![Wybieranie typów kodu macierzystego i Python](media/mixed-mode-debugging-code-type.png)

    Ustawienia typu kodu są trwałe, więc jeśli chcesz wyłączyć debugowanie w trybie mieszanym podczas dołączania do innego procesu później, wyczyść **Python** kod typu.

    Można wybrać inne typy kodu, oprócz lub zamiast **natywnych**. Na przykład, jeśli zarządzanej aplikacji obsługuje CPython, z kolei są używane moduły natywne rozszerzenia, a chcesz debugować wszystkie trzy, można sprawdzić **Python**, **natywnych**, i **zarządzane**ze sobą w celu ujednolicone środowisko debugowania m.in. stosy wywołań połączone i Krokowe przechodzenie między wszystkie trzy środowisk uruchomieniowych.

1. Po rozpoczęciu debugowania w trybie mieszanym po raz pierwszy, może zostać wyświetlony **wymagane symbole Python** okna dialogowego (zobacz [symbole debugowania w trybie mieszanym](debugging-symbols-for-mixed-mode-c-cpp-python.md)). Musisz zainstalować symbole tylko raz dla dowolnego danego środowiska Python. Symbole są automatycznie dołączane, po zainstalowaniu obsługi języka Python za pomocą Instalatora programu Visual Studio (Visual Studio 2017 i nowsze).

1. Aby udostępnić kod źródłowy dla standardowego języka Python, sama podczas debugowania, odwiedź stronę [ https://www.python.org/downloads/source/ ](https://www.python.org/downloads/source/), Pobierz archiwum odpowiednie dla posiadanej wersji i Wyodrębnij jego zawartość do folderu. Możesz następnie punktu programu Visual Studio do określonych plików w tym folderze na dowolnie punkt wyświetli monit.

## <a name="enable-mixed-mode-debugging-in-a-cc-project"></a>Włącz debugowanie w trybie mieszanym w projekcie języka C/C++

Visual Studio (2017 w wersji 15.5 lub nowszej) obsługuje trybu mieszanego debugowanie z projektu języka C/C++ (na przykład, gdy [osadzania języka Python w innej aplikacji, zgodnie z opisem w witrynie python.org](https://docs.python.org/3/extending/embedding.html)). Aby włączyć debugowanie w trybie mieszanym, należy skonfigurować projekt języka C/C++ do uruchomienia **debugowania języka Python/środowiska macierzystego**:

1. Kliknij prawym przyciskiem myszy projekt języka C/C++ w **Eksploratora rozwiązań** i wybierz **właściwości**.
1. Wybierz **debugowanie** zaznacz **debugowania języka Python/środowiska macierzystego** z **debuger do uruchomienia**i wybierz **OK**.

    ![Wybieranie debugera języka Python/środowiska macierzystego w projekcie języka C/C++](media/mixed-mode-debugging-select-cpp-debugger.png)

Za pomocą tej metody należy pamiętać, że nie można debugować *py.exe* uruchamiania, ponieważ jej spowoduje utworzenie elementu podrzędnego *python.exe* nie można dołączyć debuger do procesu. Jeśli chcesz uruchomić *python.exe* bezpośrednio z argumentami, zmień **polecenia** opcji **debugowania języka Python/środowiska macierzystego** właściwości (pokazane na poprzedniej ilustracji) Wprowadź pełną ścieżkę do *python.exe*, następnie określ argumentów **argumenty wiersza polecenia**.

### <a name="attaching-the-mixed-mode-debugger"></a>Dołączanie debugera w trybie mieszanym

Wszystkie poprzednie wersje programu Visual Studio debugowanie w trybie mieszanym bezpośredniego można włączyć tylko wtedy, gdy uruchamiasz projekt języka Python w programie Visual Studio, ponieważ jest używany przez debuger natywny projektów C/C++. Można jednak dołączyć debuger oddzielnie:

1. Uruchom projekt języka C++ bez debugowania (**debugowania** > **Uruchom bez debugowania** lub **Ctrl**+**F5**) .
1. Wybierz **debugowania** > **dołączyć do procesu**. W wyświetlonym oknie dialogowym Wybieranie odpowiedniego procesu, a następnie użyj **wybierz** przycisk, aby otworzyć **Wybieranie typu kodu** okna dialogowego, w którym można wybrać **Python**:

    ![Wybór języka Python jako typ debugowania, podczas dołączania debugera](media/mixed-mode-debugging-attach-type.png)

1. Wybierz **OK** zamknięcie tego okna dialogowego, następnie **Dołącz** można uruchomić debugera.
1. Może być konieczne wprowadzenie odpowiednich wstrzymania lub opóźnienia w aplikacji C++, aby upewnić się, że nie on wywołać kod języka Python, który chcesz debugować przed masz szansę, aby dołączyć debuger.

## <a name="mixed-mode-specific-features"></a>Określone funkcje w trybie mieszanym

- [Stos wywołań połączone](#combined-call-stack)
- [Krok między języka Python i kodu natywnego](#step-between-python-and-native-code)
- [Wyświetl wartości PyObject w kodzie natywnym](#pyobject-values-view-in-native-code)
- [Wyświetl natywnej wartości w kodzie języka Python](#native-values-view-in-python-code)

### <a name="combined-call-stack"></a>Stos wywołań połączone

**Stos wywołań** okno zawiera natywny i ramek stosu języka Python z przeplotem, za pomocą przejścia oznaczone między tymi dwoma:

![Stos wywołań połączone w debugowaniu trybu mieszanego](media/mixed-mode-debugging-call-stack.png)

Przejścia są traktowane jako **[kod zewnętrzny]**, bez określania kierunku przejście, jeśli **narzędzia** > **opcje**  >  **Debugowanie** > **ogólne** > **Włącz tylko mój kod** ustawiono opcję.

Dwukrotne kliknięcie ramki żadnych wywołań sprawia, że aktywna i spowoduje otwarcie odpowiedniego kodu źródłowego, jeśli jest to możliwe. Jeśli kod źródłowy jest niedostępny, ramki nadal zostanie aktywowane i mogą być kontrolowane zmiennych lokalnych.

### <a name="step-between-python-and-native-code"></a>Krok między języka Python i kodu natywnego

Korzystając z **Step Into** (**F11**) lub **Step Out** (**Shift**+**F11**) polecenia Debuger trybu mieszanego poprawnie obsługuje zmiany między typów kodu. Na przykład gdy Python wywołuje metody typu, który jest implementowany w języku C, wykonywanie krokowe w w wywołaniu metody zatrzymuje się na początku funkcji natywnej implementacji metody. Podobnie, kiedy kod macierzysty wywołuje niektórych funkcji interfejsu API języka Python, który skutkuje wywoływanie kodu w języku Python. Na przykład, przechodzenie do `PyObject_CallObject` na wartość funkcja, która została pierwotnie zdefiniowana w języku Python zatrzymuje się na początku funkcji języka Python. Przechodzenie krok po kroku języku Python do native jest również obsługiwana dla funkcje natywne wywołane z języka Python za pomocą [ctypes](https://docs.python.org/3/library/ctypes.html).

### <a name="pyobject-values-view-in-native-code"></a>Wyświetl wartości PyObject w kodzie natywnym

Po uaktywnieniu ramka natywna (C lub C++) jej zmienne lokalne wyświetlane w debugerze **lokalne** okna. W moduły macierzyste rozszerzenia języka Python, wiele z tych zmiennych są typu `PyObject` (czyli element typedef dla `_object`), lub kilka innych Python typy podstawowe (patrz lista poniżej). W debugowaniu trybu mieszanego, te wartości obecne dodatkowe podrzędnym etykietą **[widok Python]**. Po rozwinięciu ten węzeł zawiera reprezentację Python zmiennej, taka sama jak co widział, jeśli zmienna lokalna odwołuje się do tego samego obiektu znajdował się w ramce języka Python. Element podrzędny tego węzła są edytowalne.

![Widok języka Python w oknie zmienne lokalne](media/mixed-mode-debugging-python-view.png)

Aby wyłączyć tę funkcję, kliknij prawym przyciskiem myszy **lokalne** okna i Przełącz **Python** > **Pokaż węzły widoku Python** opcji menu:

![Włączanie widok języka Python w oknie zmienne lokalne](media/mixed-mode-debugging-enable-python-view.png)

C typy przedstawiające **[widok Python]** węzłów (jeśli jest włączona):

- `PyObject`
- `PyVarObject`
- `PyTypeObject`
- `PyByteArrayObject`
- `PyBytesObject`
- `PyTupleObject`
- `PyListObject`
- `PyDictObject`
- `PySetObject`
- `PyIntObject`
- `PyLongObject`
- `PyFloatObject`
- `PyStringObject`
- `PyUnicodeObject`

**[Widok Python]**  nie jest automatycznie wyświetlana dla typów samodzielnie tworzyć. Podczas tworzenia rozszerzeń dla języka Python 3.x, ten brak zwykle nie jest problemem, ponieważ każdy obiekt ostatecznie `ob_base` pola jednego z typów powyżej, co powoduje, że **[widok Python]** się pojawić.

Dla języka Python 2.x, jednak zwykle deklaruje jej nagłówek jako zbiór pól wbudowanych w każdego typu obiektu i istnieje skojarzenie między typami niestandardowymi utworzone i `PyObject` na poziomie systemu typów w kodzie języka C/C++. Aby włączyć **[widok Python]** edytowanie węzłów dla tych typów niestandardowych *PythonDkm.natvis* w pliku [katalog_instalacji narzędzi Python tools](installing-python-support-in-visual-studio.md#install-locations)i Dodaj innego elementu w pliku XML Struktura C lub C++ klasy.

Opcja alternatywny (i lepsze) jest wykonanie czynności opisanych [3123 program ten](https://www.python.org/dev/peps/pep-3123/) i użyć jawnego `PyObject ob_base;` pola zamiast `PyObject_HEAD`, ale która może nie zawsze jest możliwe ze względów zgodności z poprzednimi wersjami.

### <a name="native-values-view-in-python-code"></a>Wyświetl natywnej wartości w kodzie języka Python

Podobnie jak w poprzedniej sekcji, aby umożliwić **[C++ widok]** natywnej wartości w **lokalne** okna, jeśli ramka Python jest aktywny. Ta funkcja nie jest włączona domyślnie, dzięki czemu możesz ją włączyć, kliknij prawym przyciskiem myszy w **lokalne** okna i przełączania **Python** > **Pokaż węzły widoku C++** menu Opcja.

![Włączanie widok C++ w oknie zmienne lokalne](media/mixed-mode-debugging-enable-cpp-view.png)

**[C++ widok]** węzła zawiera reprezentację wewnętrzna struktura C/C++ dla wartości, taka sama jak zobaczysz w ramka natywna. Na przykład pokazuje wystąpienie `_longobject` (dla której `PyLongObject` jest element typedef) dla języka Python liczba całkowita typu long, a stara się wnioskowanie typów dla natywnych klas, które zostały zredagowane samodzielnie. Element podrzędny tego węzła są edytowalne.

![Widok C++ w oknie zmienne lokalne](media/mixed-mode-debugging-cpp-view.png)

Jeśli pole podrzędne obiektu jest typu `PyObject`, lub jednego z innych obsługiwanych typów, a następnie w nim **[widok Python]** reprezentacji węzła (Jeśli te oświadczenia są włączone), dzięki czemu można przejść do obiektu wykresów where łącza nie są bezpośrednio widoczne dla języka Python.

W odróżnieniu od **[widok Python]** węzły, które można określić typu obiektu, należy użyć metadane obiektu języka Python, nie istnieje mechanizm podobnie niezawodne dla **[C++ widok]**. Ogólnie rzecz biorąc, danej wartości Python (czyli `PyObject` odwołania) nie jest możliwe ustalenie niezawodnie struktury języka C/C++, które jest wspierającą. Tryb mieszany debuger próbuje odgadnąć tego typu, patrząc na różnych pól typu obiektu (takie jak `PyTypeObject` wskazywanym przez jego `ob_type` pole) mają typy wskaźników funkcji. Jeśli jeden z tych wskaźników funkcji, który odwołuje się funkcja, która może zostać rozwiązany i ma tę funkcję `self` parametrem typu bardziej szczegółowe niż `PyObject*`, a następnie tego typu będzie traktowana jako zapasowy typ. Na przykład jeśli `ob_type->tp_init` punktów danego obiektu w następujących funkcji:

```c
static int FobObject_init(FobObject* self, PyObject* args, PyObject* kwds) {
    return 0;
}
```

następnie jest debugera poprawnie można ustalić, czy typ C obiektu jest `FobObject`. Jeśli nie można ustalić typu bardziej precyzyjne z `tp_init`, go przechodzi do innych pól. Jeśli nie wywnioskował typ z dowolnego z tych pól **[C++ widok]** węzła przedstawia obiektu jako `PyObject` wystąpienia.

Aby zawsze uzyskać użytecznej reprezentacji dla niestandardowych typów utworzone, najlepiej zarejestrować co najmniej jedna funkcja specjalne podczas rejestrowania typu i używać silnie typizowanego `self` parametru. Większość typów spełnienia tego wymagania naturalnie; Jeśli nie jest to przypadek, następnie `tp_init` jest zazwyczaj najwygodniejsza wpisu do użycia w tym celu. Fikcyjny implementacji `tp_init` dla typu, który znajduje się wyłącznie umożliwiające typ debugera wnioskowania można po prostu zwracają zero natychmiast, tak jak w powyższym przykładowym kodzie.

## <a name="differences-from-standard-python-debugging"></a>Różnice w stosunku do standardowego debugowania języka Python

Debuger trybu mieszanego różni się od [standardowa debugera języka Python](debugging-python-in-visual-studio.md) , ponieważ wprowadza niektóre dodatkowe funkcje, ale brakuje niektórych funkcji związanych z języka Python:

- Nieobsługiwane funkcje: warunkowe punkty przerwania, **debugowanie interakcyjne** okno i zdalne debugowanie dla wielu platform.
- **Natychmiastowe** okna: dostępne ale ograniczonym podzbiorem jego działanie, w tym wszelkie ograniczenia znajduje się w tym miejscu.
- Obsługiwane wersje języka Python: CPython 2.7 i 3.3 + tylko.
- Visual Studio Shell: Po za pomocą języka Python za pomocą programu Visual Studio Shell (na przykład, jeśli został zainstalowany przy użyciu zintegrowanego Instalatora), program Visual Studio nie można otworzyć projektów w języku C++ i środowisko edytowania plików języka C++ jest to edytor tekstu podstawowego. Jednak debugowania języka C/C++ i debugowanie w trybie mieszanym są w pełni obsługiwane w powłoce z kodem źródłowym, przechodzenie do kodu macierzystego i C++ oceny wyrażenia w oknach debugera.
- Wyświetlanie i rozwijanie obiektów: Podczas przeglądania obiektów języka Python w **lokalne** i **Obejrzyj** debugera okien narzędzi debugowania trybu mieszanego pokazuje tylko strukturę obiektów. Go nie automatycznie ocenić właściwości lub Pokaż atrybuty obliczane. Dla kolekcji, pokazywane są tylko elementy kolekcji wbudowanych typów (`tuple`, `list`, `dict`, `set`). Niestandardowe typy kolekcji nie są odzwierciedlane wiernie jako kolekcje, chyba że są one dziedziczone z pewnego typu kolekcji wbudowanych.
- Obliczanie wyrażenia: patrz poniżej.

### <a name="expression-evaluation"></a>Szacowanie wyrażeń

Standardowa debugera języka Python umożliwia ocenę dowolnego wyrażenia języka Python w **Obejrzyj** i **bezpośrednie** systemu windows, gdy debugowanym procesie nie jest wykorzystywana w dowolnym momencie w kodzie, tak długo, jak nie jest zablokowany Operacja We/Wy lub inne podobne wywołanie systemowe. W debugowaniu trybu mieszanego, dowolnego wyrażenia będzie możliwe tylko wtedy, gdy zatrzymany w kodzie języka Python po punktu przerwania lub przy przechodzeniu do kodu. Wyrażenia nie można ocenić tylko wątku, na którym wystąpił punkt przerwania lub operacji przechodzenia krok po kroku.

Po zatrzymaniu kodu macierzystego lub kodu w języku Python o tym, gdzie powyższe warunki nie mają zastosowania (na przykład po zakończeniu operacji krok w poziomie lub w innym wątku), obliczanie wyrażeń jest ograniczona do uzyskiwania dostępu do zmiennych lokalnych i globalnych w obecnie wybranym zakresie Ramka, uzyskiwanie dostępu do ich pól i indeksowanie kolekcji wbudowanych typów z literałami. Na przykład poniższe wyrażenie może przyjąć w dowolnym kontekście (pod warunkiem, że wszystkie identyfikatory odnoszą się do istniejących zmiennych i pól odpowiednich typów):

```python
foo.bar[0].baz['key']
```

Debuger trybu mieszanego rozwiązuje również takich wyrażeń inaczej. Wszystkie operacje dostępu do elementu członkowskiego wyszukiwać tylko pola, które są bezpośrednio część obiektu (np. wpis w jego `__dict__` lub `__slots__`, lub pole natywnej struktury, która jest widoczna dla języka Python za pomocą `tp_members`) i Ignoruj wszystkie `__getattr__`, `__getattribute__`lub logiki deskryptora. Podobnie, Ignoruj wszystkich operacji indeksowania `__getitem__`oraz bezpośredni dostęp do struktur danych wewnętrznych kolekcji.

Dla spójności ten schemat rozpoznawania nazw jest używana do wszystkich wyrażeń, które pasują do ograniczeń do obliczenia wyrażenia ograniczone, niezależnie od tego, czy dowolnego wyrażenia są dozwolone w bieżącym punkcie zatrzymania. Aby wymusić odpowiednie semantyki Python po w pełni funkcjonalne ewaluatora jest dostępna, ujmij wyrażenie w nawiasach:

```python
(foo.bar[0].baz['key'])
```

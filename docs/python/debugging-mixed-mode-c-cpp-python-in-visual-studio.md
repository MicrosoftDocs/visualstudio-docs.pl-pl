---
title: Debugowanie w trybie mieszanym dla języka Python
description: Jednoczesne debugowanie języka C++ i Python w programie Visual Studio, w tym przechodzenie między środowiskami, wyświetlanie wartości i oceny wyrażeń.
ms.date: 11/12/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: bc90d659a32c14f92e1eff058dd22d4a17d0b1cb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75679003"
---
# <a name="debug-python-and-c-together"></a>Debugowanie Pythona i C++ razem

Większość zwykłych debugerów Języka Python obsługuje debugowanie tylko kodu języka Python. W praktyce jednak Python jest używany w połączeniu z C lub C++ w scenariuszach wymagających wysokiej wydajności lub możliwość bezpośredniego wywoływania interfejsów API platformy. (Zobacz [Tworzenie rozszerzenia Języka C++ dla języka Python](working-with-c-cpp-python-in-visual-studio.md) dla instruktażu.)

Visual Studio zapewnia zintegrowane, jednoczesne debugowanie w trybie mieszanym dla języka Python i natywnego C/C++, pod warunkiem, że wybierzesz opcję **natywnych narzędzi programistycznych języka Python** dla obciążenia **deweloperskiego języka Python** w instalatorze programu Visual Studio.

> [!Note]
> Debugowanie w trybie mieszanym nie jest dostępne w programie Python Tools for Visual Studio 1.x w programie Visual Studio 2015 i wcześniejszych.

Funkcje debugowania w trybie mieszanym są następujące, jak wyjaśniono w tym artykule:

- Stosy połączeń łączonych
- Krok między pythonem a kodem macierzystym
- Punkty przerwania w obu typach kodu
- Zobacz reprezentacje obiektów języka Python w ramkach natywnych i odwrotnie
- Debugowanie w kontekście projektu języka Python lub projektu C++

![Debugowanie w trybie mieszanym dla języka Python w programie Visual Studio](media/mixed-mode-debugging.png)

|   |   |
|---|---|
| ![ikona kamery filmowa dla wideo](../install/media/video-icon.png "Obejrzyj film") | Aby uzyskać wprowadzenie do tworzenia, testowania i debugowania natywnych modułów C za pomocą programu Visual Studio, zobacz [Głębokie dive: Tworzenie modułów natywnych](https://youtu.be/D9RlT06a1EI) (youtube.com, 9m 09s). Klip wideo ma zastosowanie zarówno do programu Visual Studio 2015, jak i 2017. |

## <a name="enable-mixed-mode-debugging-in-a-python-project"></a>Włączanie debugowania w trybie mieszanym w projekcie języka Python

1. Kliknij prawym przyciskiem myszy projekt języka Python w **Eksploratorze rozwiązań**, wybierz polecenie **Właściwości**, wybierz kartę **Debugowanie,** a następnie wybierz pozycję **Włącz debugowanie kodu natywnego**. Ta opcja umożliwia tryb mieszany dla wszystkich sesji debugowania.

    ![Włączanie debugowania kodu macierzystego](media/mixed-mode-debugging-enable-native.png)

    > [!Tip]
    > Po włączeniu debugowania kodu macierzystego okno danych wyjściowych języka Python może zniknąć natychmiast po zakończeniu programu bez podawania zwykłego **naciśnięcia dowolnego klawisza, aby kontynuować** pauzę. Aby wymusić wstrzymanie, dodaj `-i` tę opcję do pola **Uruchom** > argumenty**interpretera** na karcie **Debugowanie** po włączeniu debugowania kodu macierzystego. Ten argument przełącza interpretera Języka Python w tryb interaktywny po zakończeniu kodu, w którym to momencie czeka na naciśnięcie **klawisza Ctrl**+**Z** > **Enter,** aby zakończyć.

1. Podczas dołączania debugera trybu mieszanego do istniejącego procesu **(Debug** > **dołącz do procesu)** użyj przycisku **Wybierz,** aby otworzyć okno dialogowe **Wybierz typ kodu.** Następnie ustaw opcję **Debugowania tych typów kodu** i wybierz na liście zarówno **natywne,** jak i **Pythona:**

    ![Wybieranie typów kodu natywnego i pythonowego](media/mixed-mode-debugging-code-type.png)

    Ustawienia typu kodu są trwałe, więc jeśli chcesz wyłączyć debugowanie w trybie mieszanym podczas dołączania do innego procesu później, wyczyść typ kodu **Języka Python.**

    Można wybrać inne typy kodów oprócz lub zamiast **natywnego**. Na przykład jeśli aplikacja zarządzana obsługuje CPython, który z kolei używa natywnych modułów rozszerzeń i chcesz debugować wszystkie trzy, można sprawdzić **Python**, **Native**i **zarządzane** razem dla ujednoliconego debugowania środowiska, w tym połączone stosy wywołań i przechodzenie między wszystkimi trzema środowiskami uruchomieniowymi.

1. Po uruchomieniu debugowania w trybie mieszanym po raz pierwszy może zostać wyświetlone okno dialogowe **Wymagane symbole języka Python** (zobacz [Symbole do debugowania w trybie mieszanym](debugging-symbols-for-mixed-mode-c-cpp-python.md)). Symbole należy zainstalować tylko raz dla danego środowiska Języka Python. Symbole są automatycznie uwzględniane po zainstalowaniu obsługi języka Python za pośrednictwem instalatora programu Visual Studio (Visual Studio 2017 i nowszych).

1. Aby udostępnić kod źródłowy standardowego języka Python [https://www.python.org/downloads/source/](https://www.python.org/downloads/source/)podczas debugowania, odwiedź , pobierz archiwum odpowiednie dla twojej wersji i wyodrębnij go do folderu. Następnie punkt Visual Studio do określonych plików w tym folderze w dowolnym momencie monituje.

## <a name="enable-mixed-mode-debugging-in-a-cc-project"></a>Włączanie debugowania w trybie mieszanym w projekcie C/C++

Visual Studio (2017 w wersji 15.5 i nowszej) obsługuje debugowanie w trybie mieszanym z projektu C/C++ (na przykład podczas [osadzania języka Python w innej aplikacji, jak opisano w python.org](https://docs.python.org/3/extending/embedding.html)). Aby włączyć debugowanie w trybie mieszanym, skonfiguruj projekt C/C++, aby uruchomić **debugowanie języka Python/natywne:**

1. Kliknij prawym przyciskiem myszy projekt C/C++ w **Eksploratorze rozwiązań** i wybierz polecenie **Właściwości**.
1. Wybierz kartę **Debugowanie,** wybierz pozycję **Python/Natywne debugowanie** z **debugera, aby uruchomić,** a następnie wybierz przycisk **OK**.

    ![Wybieranie debugera Pythona/natywnego w projekcie C/C++](media/mixed-mode-debugging-select-cpp-debugger.png)

> [!Note]
> Jeśli nie masz opcji wybrania **python/natywnego debugowania,** musisz najpierw zainstalować **narzędzia programistyczne natywnego języka Python** przy użyciu instalatora VS. Można go znaleźć jako opcję w ramach obciążenia dewelopera Języka Python. Aby uzyskać dodatkowe informacje, zobacz [Jak zainstalować obsługę języka Python w programie Visual Studio w systemie Windows](installing-python-support-in-visual-studio.md).

Korzystając z tej metody, należy pamiętać, że nie można debugować *py.exe* launcher się, ponieważ powoduje uruchomienie *python.exe* podrzędnych, że debuger nie będzie dołączony do. Jeśli chcesz uruchomić *program python.exe* bezpośrednio z argumentami, zmień opcję **Polecenie** we właściwościach **Python/Debugowania natywnego** (pokazane na poprzednim obrazie), aby określić pełną ścieżkę do *pliku python.exe*, a następnie określ argumenty w **argumentach polecenia**.

### <a name="attaching-the-mixed-mode-debugger"></a>Dołączanie debugera trybu mieszanego

Dla wszystkich poprzednich wersji programu Visual Studio debugowanie w trybie mieszanym jest włączone tylko podczas uruchamiania projektu języka Python w programie Visual Studio, ponieważ projekty C/C++ używają tylko natywnego debugera. Debuger można jednak dołączyć oddzielnie:

1. Uruchom projekt C++ bez debugowania > **(Debug start bez debugowania** lub **Ctrl**+**F5**).**Debug**
1. Wybierz **debugowanie** > **Dołącz do procesu**. W wyświetlonym oknie dialogowym wybierz odpowiedni proces, a następnie użyj przycisku **Wybierz,** aby otworzyć okno dialogowe **Wybierz typ kodu,** w którym można wybrać **python:**

    ![Wybieranie języka Python jako typu debugowania podczas dołączania debugera](media/mixed-mode-debugging-attach-type.png)

1. Wybierz **przycisk OK,** aby zamknąć to okno dialogowe, a następnie **dołącz,** aby uruchomić debuger.
1. Może być konieczne wprowadzenie odpowiedniej pauzy lub opóźnienia w aplikacji C++, aby upewnić się, że nie wywoła kodu języka Python, który chcesz debugować, zanim będzie można dołączyć debuger.

## <a name="mixed-mode-specific-features"></a>Funkcje specyficzne dla trybu mieszanego

- [Połączony stos połączeń](#combined-call-stack)
- [Krok między pythonem a kodem macierzystym](#step-between-python-and-native-code)
- [Widok wartości PyObject w kodzie macierzystym](#pyobject-values-view-in-native-code)
- [Widok wartości natywnych w kodzie języka Python](#native-values-view-in-python-code)

### <a name="combined-call-stack"></a>Połączony stos połączeń

Okno **Stos wywołań** pokazuje ramki stosu macierzystego i pythona z przeplotem, z przejściami oznaczonymi między tymi dwoma:

![Połączony stos połączeń z debugowaniem w trybie mieszanym](media/mixed-mode-debugging-call-stack.png)

Przejścia są wyświetlane jako **[Kod zewnętrzny]** bez określania kierunku przejścia, jeśli **ustawiona** > **Options** > jest opcja Opcje**debugowania** > **ogólne** > narzędzia Włącz tylko mój**kod.**

Dwukrotne kliknięcie dowolnej ramki wywołania powoduje, że jest ona aktywna i otwiera odpowiedni kod źródłowy, jeśli to możliwe. Jeśli kod źródłowy nie jest dostępny, ramka jest nadal aktywna i można sprawdzić zmienne lokalne.

### <a name="step-between-python-and-native-code"></a>Krok między pythonem a kodem macierzystym

Podczas korzystania z poleceń **Step Into** (**F11**) lub **Step Out** **(Shift**+**F11**) debuger trybu mieszanego poprawnie obsługuje zmiany między typami kodu. Na przykład, gdy Python wywołuje metodę typu, który jest implementowany w języku C, przechodzenie na wywołanie tej metody zatrzymuje się na początku funkcji macierzystej implementującej metodę. Podobnie, gdy kod macierzysty wywołuje niektóre python funkcji interfejsu API, który powoduje, że kod języka Python jest wywoływany. Na przykład przechodzenie `PyObject_CallObject` do wartości funkcji, która została pierwotnie zdefiniowana w języku Python zatrzymuje się na początku funkcji Języka Python. Przechodzenie z Języka Python do natywnego jest również obsługiwane dla funkcji natywnych wywoływanych z języka Python za pośrednictwem [ctypes](https://docs.python.org/3/library/ctypes.html).

### <a name="pyobject-values-view-in-native-code"></a>Widok wartości PyObject w kodzie macierzystym

Gdy ramka macierzysta (C lub C++) jest aktywna, jej zmienne lokalne są wyświetlane w oknie **zmiennych zmiennych debugera.** W natywnych modułach rozszerzeń Języka `PyObject` Python wiele z `_object`tych zmiennych jest typu (co jest typedef for) lub kilka innych podstawowych typów Języka Python (patrz lista poniżej). W debugowaniu w trybie mieszanym wartości te przedstawiają dodatkowy węzeł podrzędny oznaczony **jako [widok Python]**. Po rozwinięciu ten węzeł pokazuje reprezentację języka Python zmiennej, identyczną z tym, co można zobaczyć, jeśli zmienna lokalna odwołująca się do tego samego obiektu była obecna w ramce języka Python. Śmigacie tego węzła są edytowalne.

![Widok języka Python w oknie Zmiennik](media/mixed-mode-debugging-python-view.png)

Aby wyłączyć tę funkcję, kliknij prawym przyciskiem myszy dowolne miejsce w oknie **Zmienników** lokalnych i przełącz opcję menu **Python** > **Pokaż węzły widoku języka Python:**

![Włączanie widoku języka Python w oknie Zmiennym](media/mixed-mode-debugging-enable-python-view.png)

Typy C, które pokazują węzły **[widok Języka Python]** (jeśli jest włączona):

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

**[Widok Języka Python]** nie pojawia się automatycznie dla typów, które samodzielnie autor. Podczas tworzenia rozszerzeń dla języka Python 3.x, ten brak `ob_base` zwykle nie jest problemem, ponieważ każdy obiekt ostatecznie ma pole jednego z powyższych typów, co powoduje, że pojawia się **[widok Pythona].**

Jednak w przypadku języka Python 2.x każdy typ obiektu zazwyczaj deklaruje swój nagłówek jako zbiór pól wbudowanych `PyObject` i nie ma skojarzenia między niestandardowymi typami autorskimi i na poziomie systemu typu w kodzie C/C++. Aby włączyć węzły **[Widok Języka Python]** dla takich typów niestandardowych, edytuj plik *PythonDkm.natvis* w [katalogu instalowania narzędzi Pythona](installing-python-support-in-visual-studio.md#install-locations)i dodaj kolejny element w pliku XML dla klasy C struct lub C++.

Alternatywną (i lepszą) opcją jest podążanie za [PEP 3123](https://www.python.org/dev/peps/pep-3123/) i używanie wyraźnego `PyObject ob_base;` pola, a nie `PyObject_HEAD`, choć nie zawsze może to być możliwe ze względu na zgodność z powrotem.

### <a name="native-values-view-in-python-code"></a>Widok wartości natywnych w kodzie języka Python

Podobnie jak w poprzedniej sekcji, można włączyć **[Widok C++]** dla wartości natywnych w oknie **Zmiennych lokalnych,** gdy ramka języka Python jest aktywna. Ta funkcja nie jest domyślnie włączona, więc możesz ją włączyć, klikając ją prawym przyciskiem myszy w oknie **Zmiennych** i przełączanie opcji menu **Python** > **Show C++ View Nodes.**

![Włączanie widoku języka C++ w oknie Zmiennicy](media/mixed-mode-debugging-enable-cpp-view.png)

Węzeł **[Widok C++]** zapewnia reprezentację podstawowej struktury C/C++ dla wartości, identycznej z wartością, którą można zobaczyć w ramce macierzystej. Na przykład pokazuje wystąpienie `_longobject` (dla `PyLongObject` którego jest typedef) dla python długiej liczby całkowitej i próbuje wywnioskować typy dla klas natywnych, które zostały autorstwa samodzielnie. Śmigacie tego węzła są edytowalne.

![Widok języka C++ w oknie Zmiennik](media/mixed-mode-debugging-cpp-view.png)

Jeśli pole podrzędne obiektu jest `PyObject`typu lub jeden z innych obsługiwanych typów, a następnie ma węzeł reprezentacji **[Python view]** (jeśli te reprezentacje są włączone), dzięki czemu można poruszać się wykresy obiektów, gdzie łącza nie są bezpośrednio narażone na Python.

W przeciwieństwie do węzłów **[Widok Języka Python],** które używają metadanych obiektu Języka Python do określenia typu obiektu, nie ma podobnie niezawodnego mechanizmu dla **[widoku C++]**. Ogólnie rzecz biorąc, biorąc pod uwagę wartość `PyObject` Języka Python (czyli odwołanie) nie jest możliwe niezawodne określenie, która struktura C/C++ jest jej kopii zapasowej. Debuger trybu mieszanego próbuje odgadnąć tego typu, patrząc na różne pola `PyTypeObject` typu obiektu `ob_type` (takie jak odwołuje się jego pole), które mają typy wskaźników funkcji. Jeśli jeden z tych wskaźników funkcji odwołuje się do funkcji, która `self` może być rozwiązana, a ta funkcja ma parametr o typie bardziej szczegółowym niż `PyObject*`, to ten typ jest uważany za typ zapasowy. Na przykład, `ob_type->tp_init` jeśli dany obiekt wskazuje na następującą funkcję:

```c
static int FobObject_init(FobObject* self, PyObject* args, PyObject* kwds) {
    return 0;
}
```

następnie debuger może poprawnie wywnić, że `FobObject`typ C obiektu jest . Jeśli nie jest w stanie określić `tp_init`bardziej precyzyjnego typu z , przechodzi do innych pól. Jeśli nie można wywnić typu z dowolnego z tych pól, węzeł **[Widok C++]** przedstawia obiekt jako wystąpienie. `PyObject`

Aby zawsze uzyskać użyteczną reprezentację dla niestandardowych typów autorów, najlepiej zarejestrować co najmniej jedną funkcję `self` specjalną podczas rejestrowania typu i użyć parametru silnie typizowane. Większość typów spełnia ten wymóg naturalnie; jeśli tak nie jest, `tp_init` to jest zwykle najwygodniejszym wejściem do wykorzystania w tym celu. Atrapa implementacji `tp_init` dla typu, który jest obecny wyłącznie w celu włączenia wnioskowania o typ debugera można po prostu zwrócić zero natychmiast, jak w przykładzie kodu powyżej.

## <a name="differences-from-standard-python-debugging"></a>Różnice w stosunku do standardowego debugowania języka Python

Debuger trybu mieszanego różni się od [standardowego debugera Języka Python,](debugging-python-in-visual-studio.md) ponieważ wprowadza pewne dodatkowe funkcje, ale brakuje niektórych możliwości związanych z Pythonem:

- Nieobsługiwały funkcje: warunkowe punkty przerwania, okno **Debug Interactive** i zdalne debugowanie na wielu platformach.
- **Okno natychmiastowe:** jest dostępne, ale z ograniczonym podzbiorem jego funkcjonalności, w tym wszystkimi ograniczeniami wymienionymi tutaj.
- Obsługiwane wersje języka Python: CPython 2.7 i 3.3+ tylko.
- Powłoka programu Visual Studio: Podczas korzystania z języka Python z powłoką programu Visual Studio (na przykład, jeśli zainstalowano go przy użyciu zintegrowanego instalatora), visual studio nie może otwierać projektów języka C++, a środowisko edycji dla plików W++ jest tylko w podstawowym edytorze tekstu. Jednak debugowanie C/C++ i debugowanie w trybie mieszanym są w pełni obsługiwane w aplikacji Shell z kodem źródłowym, przechodzenie do kodu macierzystego i oceny wyrażenia C++ w oknach debugera.
- Wyświetlanie i rozwijanie obiektów: Podczas wyświetlania obiektów języka Python w oknach narzędzi debugera **lokalne** i **czujki** debuger debugera debuger w trybie mieszanym pokazuje tylko strukturę obiektów. Nie ocenia automatycznie właściwości ani nie pokazuje obliczonych atrybutów. W przypadku kolekcji jest wyświetlany tylko elementy`tuple`dla `list` `dict`typów `set`kolekcji wbudowanych ( , , , ). Typy kolekcji niestandardowej nie są wizualizowane jako kolekcje, chyba że są dziedziczone z niektórych wbudowanych typów kolekcji.
- Ocena wyrażenia: patrz poniżej.

### <a name="expression-evaluation"></a>Ocena wyrażenia

Standardowy debuger języka Python umożliwia ocenę dowolnych wyrażeń języka Python w **oknach Watch** i **Immediate,** gdy debugowany proces jest wstrzymany w dowolnym momencie kodu, o ile nie jest zablokowany w operacji We/Wy lub innym podobnym wywołaniu systemowym. W debugowaniu w trybie mieszanym dowolne wyrażenia mogą być oceniane tylko wtedy, gdy są zatrzymane w kodzie języka Python, po punkcie przerwania lub podczas przechodzenia do kodu. Wyrażenia mogą być oceniane tylko w wątku, w którym wystąpił punkt przerwania lub operacja krokowa.

Po zatrzymaniu w kodzie macierzystym lub w kodzie Języka Python, gdzie powyższe warunki nie mają zastosowania (na przykład po operacji wysuwania lub w innym wątku), ocena wyrażenia jest ograniczona do uzyskiwania dostępu do zmiennych lokalnych i globalnych w zakresie aktualnie wybranego ramki, uzyskiwanie dostępu do ich pól i indeksowanie typów wbudowanych kolekcji za pomocą literałów. Na przykład następujące wyrażenie można ocenić w dowolnym kontekście (pod warunkiem, że wszystkie identyfikatory odnoszą się do istniejących zmiennych i pól odpowiednich typów):

```python
foo.bar[0].baz['key']
```

Debuger trybu mieszanego również rozwiązuje takie wyrażenia inaczej. All member-access operations look up only fields that are directly part of the object (such as an entry in its `__dict__` or `__slots__`, or a field of a native struct that is exposed to Python via `tp_members`), and ignore any `__getattr__`, `__getattribute__` or descriptor logic. Podobnie wszystkie operacje indeksowania `__getitem__`ignorują i bezpośrednio uzyskują dostęp do wewnętrznych struktur danych kolekcji.

Ze względu na spójność ten schemat rozpoznawania nazw jest używany dla wszystkich wyrażeń, które pasują do ograniczeń dla oceny ograniczonego wyrażenia, niezależnie od tego, czy dowolne wyrażenia są dozwolone w bieżącym punkcie zatrzymania. Aby wymusić prawidłową semantykę języka Python, gdy dostępny jest w pełni funkcjonalny oceniający, ujęć wyrażenie w nawiasy:

```python
(foo.bar[0].baz['key'])
```

---
title: Debugowanie w trybie mieszanym dla języka Python
description: Jednocześnie Debuguj Języki C++ i Python w programie Visual Studio, w tym taktowanie między środowiskami, wyświetlanie wartości i ocenianie wyrażeń.
ms.date: 11/12/2018
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 953ff26a6094a9de9dcf974d5e4cb5a02aaa503f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85533565"
---
# <a name="debug-python-and-c-together"></a>Debugowanie kodu Python i języka C++

Najbardziej regularne debugery języka Python obsługują debugowanie tylko kodu w języku Python. W tym przypadku Język Python jest używany w połączeniu z językiem C lub C++ w scenariuszach wymagających wysokiej wydajności lub możliwości bezpośredniego wywoływania interfejsów API platformy. (Zobacz [Tworzenie rozszerzenia C++ dla języka Python](working-with-c-cpp-python-in-visual-studio.md) , aby zapoznać się z przewodnikiem).

Program Visual Studio zapewnia zintegrowane, jednoczesne debugowanie w trybie mieszanym dla języka Python i natywnego języka C/C++, pod warunkiem wybrania opcji **natywnych narzędzi programistycznych języka Python** dla obciążenia programowania w języku **Python** w Instalatorze programu Visual Studio.

> [!Note]
> Debugowanie w trybie mieszanym nie jest dostępne z Python Tools for Visual Studio 1. x w programie Visual Studio 2015 i jego wcześniejszych wersjach.

Funkcje debugowania w trybie mieszanym obejmują następujące elementy, jak wyjaśniono w tym artykule:

- Połączone stosy wywołań
- Krok między językiem Python a kodem natywnym
- Punkty przerwania w obu typach kodu
- Zobacz reprezentacje obiektów w języku Python w ramkach natywnych i na odwrót
- Debugowanie w kontekście projektu Python lub projektu C++

![Debugowanie w trybie mieszanym dla języka Python w programie Visual Studio](media/mixed-mode-debugging.png)

|   |   |
|---|---|
| ![ikona aparatu filmu wideo](../install/media/video-icon.png "Obejrzyj film") | Aby zapoznać się z wprowadzeniem do kompilowania, testowania i debugowania natywnych modułów C przy użyciu programu Visual Studio, zobacz [głębokie szczegółowe: Create Native modules](https://youtu.be/D9RlT06a1EI) (YouTube.com, 9 m 09s). Film wideo ma zastosowanie zarówno do programu Visual Studio 2015, jak i 2017. |

## <a name="enable-mixed-mode-debugging-in-a-python-project"></a>Włączanie debugowania w trybie mieszanym w projekcie języka Python

1. Kliknij prawym przyciskiem myszy projekt Python w **Eksplorator rozwiązań**, wybierz polecenie **Właściwości**, wybierz kartę **debugowanie** , a następnie wybierz opcję **Włącz debugowanie kodu natywnego**. Ta opcja umożliwia tryb mieszany dla wszystkich sesji debugowania.

    ![Włączanie debugowania kodu natywnego](media/mixed-mode-debugging-enable-native.png)

    > [!Tip]
    > Po włączeniu debugowania kodu natywnego okno danych wyjściowych w języku Python może zniknąć natychmiast po zakończeniu działania programu bez podawania zwykłych **klawiszy, aby kontynuować** wstrzymywanie. Aby wymusić wstrzymanie, należy dodać `-i` opcję **Run**do  >  pola argumentów uruchamiania**interpretera** na karcie **debugowanie** po włączeniu debugowania kodu natywnego. Ten argument powoduje przełączenie interpretera języka Python w tryb interaktywny po zakończeniu kodu, w którym momencie czeka na naciśnięcie klawisza **Ctrl** + **z**  >  **Enter** , aby wyjść.

1. Podczas dołączania debugera w trybie mieszanym do istniejącego procesu (**debugowanie**  >  **dołączanie do procesu**), użyj przycisku **Wybierz** , aby otworzyć okno dialogowe **Wybieranie typu kodu** . Następnie ustaw opcję **Debuguj te typy kodu** i wybierz zarówno **natywne** , jak i **Python** na liście:

    ![Wybieranie typów kodu natywnego i języka Python](media/mixed-mode-debugging-code-type.png)

    Ustawienia typu kodu są trwałe, więc jeśli chcesz wyłączyć debugowanie w trybie mieszanym podczas późniejszego dołączania do innego procesu, wyczyść typ kodu języka **Python** .

    Można wybrać inne typy kodu oprócz, lub zamiast, **natywne**. Na przykład, jeśli zarządzana aplikacja obsługuje CPython, która z kolei używa natywnych modułów rozszerzeń i chcesz debugować wszystkie trzy, możesz sprawdzić środowisko **Python**, **natywne**i **zarządzane** razem w celu zapewnienia ujednoliconego środowiska debugowania, w tym połączone stosy wywołań i przechodzenie między wszystkimi trzema środowiskami uruchomieniowymi.

1. Po pierwszym uruchomieniu debugowania w trybie mieszanym można zobaczyć okno dialogowe **wymagane symbole języka Python** (zobacz [symbole dla debugowania w trybie mieszanym](debugging-symbols-for-mixed-mode-c-cpp-python.md)). Należy zainstalować symbole tylko raz dla danego środowiska języka Python. Symbole są automatycznie dołączane, jeśli zainstalowano obsługę języka Python za pomocą Instalatora programu Visual Studio (Visual Studio 2017 i nowsze).

1. Aby kod źródłowy dla standardowego środowiska Python był dostępny podczas debugowania, odwiedź stronę [https://www.python.org/downloads/source/](https://www.python.org/downloads/source/) , Pobierz archiwum odpowiednie dla danej wersji i wyodrębnij go do folderu. Następnie należy wskazać program Visual Studio do określonych plików w tym folderze w dowolnym momencie, w którym zostanie wyświetlony odpowiednika.

## <a name="enable-mixed-mode-debugging-in-a-cc-project"></a>Włącz debugowanie w trybie mieszanym w projekcie C/C++

Program Visual Studio (2017 w wersji 15,5 lub nowszej) obsługuje debugowanie w trybie mieszanym z projektu C/C++ (na przykład podczas [osadzania języka Python w innej aplikacji zgodnie z opisem w Python.org](https://docs.python.org/3/extending/embedding.html)). Aby włączyć debugowanie w trybie mieszanym, należy skonfigurować projekt C/C++ do uruchamiania języka **Python/natywnego debugowania**:

1. Kliknij prawym przyciskiem myszy projekt C/C++ w **Eksplorator rozwiązań** i wybierz polecenie **Właściwości**.
1. Wybierz kartę **debugowanie** , wybierz opcję **Debugowanie kodu Python/natywne** z **debugera do uruchomienia**, a następnie wybierz **przycisk OK**.

    ![Wybieranie debugera języka Python/natywnego w projekcie C/C++](media/mixed-mode-debugging-select-cpp-debugger.png)

> [!Note]
> Jeśli nie masz możliwości wybrania debugowania języka **Python/natywnego** , musisz najpierw zainstalować **natywne narzędzia programistyczne języka Python** przy użyciu Instalatora programu vs. Można go znaleźć jako opcję w ramach obciążenia programowania w języku Python. Aby uzyskać dodatkowe informacje, zobacz [temat jak zainstalować obsługę języka Python w programie Visual Studio w systemie Windows](installing-python-support-in-visual-studio.md).

Korzystając z tej metody, należy pamiętać, że nie można debugować samego uruchamiania *py.exe* , ponieważ spowoduje to zduplikowanie podrzędnego procesu *python.exe* , do którego debuger nie zostanie dołączony. Jeśli chcesz uruchomić *python.exe* bezpośrednio z argumentami, Zmień opcję **polecenia** we właściwościach **debugowania języka Python/natywnego** (pokazanym na poprzedniej ilustracji), aby określić pełną ścieżkę do *python.exe*, a następnie określ argumenty w **argumentach poleceń**.

### <a name="attaching-the-mixed-mode-debugger"></a>Dołączanie debugera w trybie mieszanym

W przypadku wszystkich poprzednich wersji programu Visual Studio bezpośrednie debugowanie w trybie mieszanym jest włączone tylko podczas uruchamiania projektu Python w programie Visual Studio, ponieważ projekty C/C++ używają tylko debugera natywnego. Można jednak dołączyć debuger osobno:

1. Uruchom projekt C++ bez debugowania (**Debuguj**  >  **Uruchom bez debugowania** lub **Ctrl** + **F5**).
1. Wybierz pozycję **Debuguj**  >  **Dołącz do procesu**. W wyświetlonym oknie dialogowym wybierz odpowiedni proces, a następnie użyj przycisku **Wybierz** , aby otworzyć okno dialogowe **Wybieranie typu kodu** , w którym można wybrać język **Python**:

    ![Wybieranie języka Python jako typu debugowania podczas dołączania debugera](media/mixed-mode-debugging-attach-type.png)

1. Wybierz **przycisk OK** , aby zamknąć to okno dialogowe, a następnie **Dołącz** do uruchomienia debugera.
1. Może być konieczne wprowadzenie odpowiedniej przerwy lub opóźnienia w aplikacji C++, aby upewnić się, że nie wywoła kodu Python, który ma być debugowany, zanim będzie możliwe dołączenie debugera.

## <a name="mixed-mode-specific-features"></a>Funkcje specyficzne dla trybu mieszanego

- [Połączony stos wywołań](#combined-call-stack)
- [Krok między językiem Python a kodem natywnym](#step-between-python-and-native-code)
- [Widok wartości PyObject w kodzie natywnym](#pyobject-values-view-in-native-code)
- [Widok wartości natywnych w kodzie języka Python](#native-values-view-in-python-code)

### <a name="combined-call-stack"></a>Połączony stos wywołań

W oknie **stos wywołań** są wyświetlane ramki stosu natywnego i języka Python z przeplotem, z przejściami oznaczonymi między tymi dwoma:

![Połączony stos wywołań z debugowaniem w trybie mieszanym](media/mixed-mode-debugging-call-stack.png)

Przejścia są wyświetlane jako **[kod zewnętrzny]** bez określania kierunku przejścia, jeśli opcja narzędzia do **Tools**  >  **Options**  >  **debugowania**opcji  >  **General**  >  **Włącz ogólne tylko mój kod** jest ustawiona.

Dwukrotne kliknięcie dowolnej ramki wywołania powoduje jej uaktywnienie i otwarcie odpowiedniego kodu źródłowego, jeśli jest to możliwe. Jeśli kod źródłowy jest niedostępny, ramka nadal zostanie uaktywniona, a zmienne lokalne można sprawdzić.

### <a name="step-between-python-and-native-code"></a>Krok między językiem Python a kodem natywnym

W przypadku korzystania z poleceń **Step Into** (**F11**) lub **krok po kroku** (**SHIFT** + **F11**) debuger trybu mieszanego prawidłowo obsługuje zmiany między typami kodu. Na przykład, gdy język Python wywołuje metodę typu, który jest implementowany w języku C, krokowe wywołanie tej metody zatrzyma się na początku funkcji natywnej implementującej metodę. Podobnie, gdy kod natywny wywołuje pewną funkcję interfejsu API języka Python, która powoduje Wywoływanie kodu języka Python. Na przykład przechodzenie do `PyObject_CallObject` wartości funkcji, która została pierwotnie zdefiniowana w języku Python, zatrzyma się na początku funkcji języka Python. Przechodzenie z języka Python do kodu natywnego jest również obsługiwane dla funkcji natywnych wywoływanych przez środowisko Python za pośrednictwem [ctypes](https://docs.python.org/3/library/ctypes.html).

### <a name="pyobject-values-view-in-native-code"></a>Widok wartości PyObject w kodzie natywnym

Gdy ramka natywna (C lub C++) jest aktywna, jej zmienne lokalne są wyświetlane w oknie **Ustawienia regionalne** debugera. W natywnych modułach rozszerzenia Python wiele z tych zmiennych jest typu `PyObject` (będącego elementem TypeDef dla `_object` ) lub kilkoma innymi podstawowymi typami języka Python (patrz lista poniżej). W przypadku debugowania w trybie mieszanym te wartości składają się na dodatkowy węzeł podrzędny o nazwie **[widok Python]**. Po rozwinięciu ten węzeł pokazuje reprezentację języka Python zmiennej, identyczną z tym, co widzisz, jeśli zmienna lokalna odwołująca się do tego samego obiektu była obecna w ramce języka Python. Elementy podrzędne tego węzła można edytować.

![Widok języka Python w oknie zmiennych lokalnych](media/mixed-mode-debugging-python-view.png)

Aby wyłączyć tę funkcję, kliknij prawym przyciskiem myszy w dowolnym miejscu w oknie **zmiennych lokalnych** i Przełącz opcję menu Pokaż węzły w widoku **Python w języku**  >  **Python** :

![Włączanie widoku języka Python w oknie zmiennych lokalnych](media/mixed-mode-debugging-enable-python-view.png)

Typy języka C, które są wyświetlane w węzłach **[widok Python]** (jeśli są włączone):

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

**[Widok języka Python]** nie pojawia się automatycznie dla typów utworzonych przez Ciebie. Podczas tworzenia rozszerzeń dla języka Python 3. x ten brak zazwyczaj nie jest problemem, ponieważ każdy obiekt ma w końcu `ob_base` pole jednego z powyższych typów, które powoduje wyświetlenie **[widok Python]** .

W przypadku języka Python 2. x, jednak każdy typ obiektu zazwyczaj deklaruje swój nagłówek jako kolekcję pól wbudowanych i nie ma skojarzenia między niestandardowymi typami utworzonymi i `PyObject` na poziomie systemu typu w kodzie C/C++. Aby włączyć węzły **[widok Python]** dla takich typów niestandardowych, edytuj plik *PythonDkm. Natvis* w [katalogu instalacyjnym narzędzi Python](installing-python-support-in-visual-studio.md#install-locations)i Dodaj inny element w kodzie XML dla klasy języka C lub C++.

Alternatywna (i lepsza) opcja polega na obserwowanie [PEP 3123](https://www.python.org/dev/peps/pep-3123/) i używanie jawnego `PyObject ob_base;` pola `PyObject_HEAD` , a nie zawsze, chociaż może to być niemożliwe ze względu na zgodność z poprzednimi wersjami.

### <a name="native-values-view-in-python-code"></a>Widok wartości natywnych w kodzie języka Python

Podobnie jak w poprzedniej sekcji, można włączyć **[widok C++]** dla natywnych wartości w oknie **zmiennych lokalnych** , gdy ramka języka Python jest aktywna. Ta funkcja nie jest domyślnie włączona, więc należy ją włączyć, klikając prawym przyciskiem myszy w oknie **zmiennych lokalnych** i przełączając **Python**  >  opcję menu**Pokaż węzły języka C++ w języku** Python.

![Włączanie widoku C++ w oknie zmiennych lokalnych](media/mixed-mode-debugging-enable-cpp-view.png)

Węzeł **[widok C++]** zawiera reprezentację źródłowej struktury C/C++ dla wartości, tak samo jak w ramce natywnej. Na przykład pokazuje wystąpienie `_longobject` (dla którego `PyLongObject` jest typedef) dla długiej liczby całkowitej w języku Python i próbuje wywnioskować typy dla natywnych klas, które zostały przez Ciebie utworzone. Elementy podrzędne tego węzła można edytować.

![Widok języka C++ w oknie zmiennych lokalnych](media/mixed-mode-debugging-cpp-view.png)

Jeśli pole podrzędne obiektu jest typu `PyObject` lub jeden z innych obsługiwanych typów, ma on węzeł reprezentacji **[Python View]** (jeśli te oświadczenia są włączone), co umożliwia nawigowanie po wykresach obiektów, w których linki nie są bezpośrednio udostępniane w języku Python.

W przeciwieństwie do węzłów **[widok Python]** , które używają metadanych obiektu języka Python do określenia typu obiektu, nie istnieje podobnie niezawodny mechanizm dla **[widok C++]**. Ogólnie mówiąc, dana wartość języka Python (czyli `PyObject` odwołanie) nie jest możliwa do niezawodnego określania, którą strukturę C/C++ tworzy. Debuger trybu mieszanego próbuje odgadnąć ten typ, przeglądając różne pola typu obiektu (takie jak `PyTypeObject` odwołania do `ob_type` pola), które mają typy wskaźnika funkcji. Jeśli jeden z tych wskaźników funkcji odwołuje się do funkcji, którą można rozpoznać, a ta funkcja ma `self` parametr o typie bardziej szczegółowym niż `PyObject*` , wówczas ten typ jest przyjęty jako typ zapasowy. Na przykład, jeśli w `ob_type->tp_init` danym punkcie obiektu znajduje się następująca funkcja:

```c
static int FobObject_init(FobObject* self, PyObject* args, PyObject* kwds) {
    return 0;
}
```

następnie debuger może prawidłowo określić, że typ obiektu to `FobObject` . Jeśli nie można określić bardziej precyzyjnego typu z `tp_init` , przejdzie on do innych pól. Jeśli nie można wywnioskować typu z dowolnego z tych pól, węzeł **[widok C++]** przedstawia obiekt jako `PyObject` wystąpienie.

Aby zawsze uzyskać przydatną reprezentację dla niestandardowych typów, najlepiej zarejestrować co najmniej jedną specjalną funkcję podczas rejestrowania typu i użyć parametru o jednoznacznie określonym typie `self` . Większość typów spełnia ten wymóg w naturalny sposób; Jeśli tak się nie dzieje, `tp_init` zazwyczaj jest to najbardziej wygodny wpis do użycia w tym celu. Fikcyjna implementacja `tp_init` dla typu, który jest obecny wyłącznie do włączenia wnioskowania typu debuger, może po prostu zwrócić zero, jak w powyższym przykładzie kodu.

## <a name="differences-from-standard-python-debugging"></a>Różnice dotyczące standardowej debugowania języka Python

Debuger trybu mieszanego różni się od [standardowego debugera języka Python](debugging-python-in-visual-studio.md) w systemie, w którym wprowadzono kilka dodatkowych funkcji, ale brakuje niektórych funkcji związanych z językiem Python:

- Nieobsługiwane funkcje: warunkowe punkty przerwania, **debugowanie interaktywnego** okna i Międzyplatformowe debugowanie zdalne.
- Okno **bezpośrednie** : jest dostępne, ale z ograniczonym podzbiorem jego funkcjonalności, w tym ze wszystkimi ograniczeniami wymienionymi w tym miejscu.
- Obsługiwane wersje języka Python: CPython 2,7 i 3.3 +.
- Visual Studio Shell: w przypadku korzystania z języka Python z programem Visual Studio Shell (na przykład jeśli został on zainstalowany przy użyciu zintegrowanego Instalatora), program Visual Studio nie może otworzyć projektów języka C++, a środowisko edytowania dla plików języka C++ jest tylko podstawowym edytorem tekstu. Jednak debugowanie C/C++ i debugowanie w trybie mieszanym są w pełni obsługiwane w powłoce z kodem źródłowym, przechodzenie do kodu natywnego i obliczanie wyrażeń języka C++ w oknach debugera.
- Wyświetlanie i rozszerzanie obiektów: podczas wyświetlania obiektów języka Python w oknach **lokalnych** i narzędzi debugera **czujki** debuger trybu mieszanego pokazuje tylko strukturę obiektów. Nie oblicza automatycznie właściwości ani nie wyświetla obliczanych atrybutów. W przypadku kolekcji są wyświetlane tylko elementy dla wbudowanych typów kolekcji ( `tuple` , `list` , `dict` , `set` ). Niestandardowe typy kolekcji nie są wizualizacją jako kolekcje, chyba że są dziedziczone z niektórych typów kolekcji wbudowanej.
- Obliczanie wyrażenia: Zobacz poniżej.

### <a name="expression-evaluation"></a>Obliczanie wyrażeń

Standardowy debuger języka Python umożliwia obliczanie dowolnych wyrażeń języka Python w oknach **czujka** i **natychmiastowe** , gdy debugowany proces jest wstrzymywany w dowolnym momencie w kodzie, o ile nie jest zablokowany w operacji we/wy lub innym podobnym wywołaniu systemowym. W przypadku debugowania w trybie mieszanym dowolne wyrażenia można ocenić tylko w przypadku zatrzymania w kodzie języka Python, po punkcie przerwania lub podczas wykonywania kodu. Wyrażenia można ocenić tylko w wątku, w którym wystąpiło punkt przerwania lub operacji taktowania.

Po zatrzymaniu w kodzie natywnym lub w kodzie języka Python, w którym powyższe warunki nie mają zastosowania (na przykład po wykonaniu kroku lub w innym wątku), obliczenia wyrażenia są ograniczone do uzyskiwania dostępu do zmiennych lokalnych i globalnych w zakresie aktualnie wybranej ramki, uzyskiwania dostępu do pól i indeksowania wbudowanych typów kolekcji z literałami. Na przykład następujące wyrażenie może być oceniane w dowolnym kontekście (pod warunkiem, że wszystkie identyfikatory odwołują się do istniejących zmiennych i pól odpowiednich typów):

```python
foo.bar[0].baz['key']
```

Debuger trybu mieszanego również rozwiązuje takie wyrażenia inaczej. Wszystkie operacje dostępu do elementów członkowskich wyszukują tylko pola, które są bezpośrednio częścią obiektu (takie jak wpis w jego `__dict__` lub lub `__slots__` pole natywnej struktury, która jest dostępna w języku Python przez `tp_members` ), i ignorowanie `__getattr__` `__getattribute__` logiki deskryptora. Podobnie wszystkie operacje indeksowania są ignorowane `__getitem__` i bezpośrednio uzyskują dostęp do wewnętrznych struktur danych kolekcji.

W celu zapewnienia spójności ten schemat rozpoznawania nazw jest używany dla wszystkich wyrażeń, które pasują do ograniczeń obliczeń wyrażenia ograniczonego, bez względu na to, czy dowolne wyrażenia są dozwolone w bieżącym punkcie zatrzymania. Aby wymusić poprawną semantykę języka Python, gdy jest dostępna w pełni funkcjonalna ewaluatora, umieść wyrażenie w nawiasach:

```python
(foo.bar[0].baz['key'])
```

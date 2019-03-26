---
title: Pisanie rozszerzeń języka C++ dla języka Python
description: Przewodnik po Tworzenie rozszerzenia C++ dla języka Python za pomocą programu Visual Studio, CPython i PyBind11, włączając debugowanie w trybie mieszanym.
ms.date: 11/19/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 64c200ffa0bb70b52f9e42d40daf3fd2a39df729
ms.sourcegitcommit: 489aca71046fb6e4aafd0a4509cd7dc149d707b1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2019
ms.locfileid: "58416048"
---
# <a name="create-a-c-extension-for-python"></a>Tworzenie rozszerzenia C++ dla języka Python

Modułów napisanych w języku C++ (lub C) są często używane, aby rozszerzyć możliwości interpreter języka Python, który jest również umożliwiających dostęp do funkcji niskiego poziomu systemu operacyjnego. Istnieją trzy podstawowe typy modułów:

- Moduły akceleratora: ponieważ interpretacji języka Python, pewne fragmenty kodu można napisanego w języku C++ większą wydajność.
- Moduły otoki: ujawniają istniejące interfejsy C/C++ do kodu w języku Python i udostępnić więcej interfejsu API "Pythonic", który jest łatwy w użyciu za pomocą języka Python.
- Moduły dostęp do niskiego poziomu systemu: utworzone w celu uzyskania dostępu do niższego poziomu funkcji środowiska uruchomieniowego języka CPython, system operacyjny lub bazowego sprzętu.

W tym artykule przedstawiono tworzenie modułu rozszerzenia języka C++ dla języka CPython, który oblicza tangens hiperboliczny i określa je z poziomu kodu Python. Procedura jest implementowany najpierw w języku Python, aby zademonstrować przyrost względnej wydajności wykonawczych taką samą procedurę w języku C++.

W tym artykule przedstawiono również udostępnić C++ języka Python na dwa sposoby:

- Standardowa rozszerzenia języka CPython, zgodnie z opisem w [dokumentace Pro Python](https://docs.python.org/3/c-api/)
- [PyBind11](https://github.com/pybind/pybind11), która jest zalecana dla c ++ 11 ze względu na prostotę jej.

Porównanie tych i innych środków znajduje się w folderze [alternatywnych metod](#alternative-approaches) na końcu tego artykułu.

Ukończone próbkę z tego przewodnika znajdują się na [rozszerzenie języka python — przykłady vs-cpp](https://github.com/Microsoft/python-sample-vs-cpp-extension) (GitHub).

## <a name="prerequisites"></a>Wymagania wstępne

- Visual Studio 2017 lub nowszego z programem **programowanie aplikacji klasycznych w języku C++** i **programowania w języku Python** obciążeń zainstalowany z użyciem opcji domyślnych.
- W **programowania w języku Python** obciążenie, zaznacz także pole po prawej stronie, aby uzyskać **Python natywne narzędzia programistyczne**. Ta opcja umożliwia ustawienie większość konfiguracji opisanej w tym artykule. (Ta opcja również powoduje dołączenie obciążeniu C++ dla automatycznie.)

    ![Wybranie opcji narzędzia programowania natywnego języka Python](media/cpp-install-native.png)

    > [!Tip]
    > Instalowanie **aplikacji analitycznych i naukowych opracowań danych** obejmowały obciążenie języka Python i **Python natywne narzędzia programistyczne** opcja domyślnie.

Aby uzyskać więcej informacji, zobacz [Instalowanie obsługi języka Python dla programu Visual Studio](installing-python-support-in-visual-studio.md), tym o korzystaniu z innymi wersjami programu Visual Studio. Jeśli zainstalujesz środowisko Python oddzielnie, pamiętaj o wybraniu **pobrać symbole debugowania** i **pliki binarne debugowania pobierania** w obszarze **zaawansowane opcje** w Instalatorze. Ta opcja zapewnia mieć dostępne biblioteki debugowania konieczne, Jeśli postanowisz to zrobić kompilacji debugowania.

## <a name="create-the-python-application"></a>Tworzenie aplikacji Python

1. Utwórz nowy projekt języka Python w programie Visual Studio, wybierając **pliku** > **New** > **projektu**. Wyszukaj "Python", wybierz **aplikację w języku Python** szablonu, nadaj mu odpowiednią nazwę i lokalizację, a następnie wybierz pozycję **OK**.

1. Pracy przy użyciu języka C++ wymaga używania 32-bitowy interpreter języka Python (Python 3.6 lub nowszej jest zalecane). W **Eksploratora rozwiązań** okna programu Visual Studio, rozwiń węzeł projektu, a następnie rozwiń węzeł **środowiska Python** węzła. Jeśli nie widzisz 32-bitowego środowiska jako domyślny (pogrubienie lub oznaczone za pomocą **domyślnie globalne**), następnie postępuj zgodnie z instrukcjami [wybierz środowisko Python w projekcie](selecting-a-python-environment-for-a-project.md). Jeśli nie masz interpreter 32-bitowych, zainstalowane, zobacz [Python Zainstaluj interpretery](installing-python-interpreters.md).

1. W projekcie *PY* plików, wklej następujący kod, który wzorców obliczeń tangens hiperboliczny (zaimplementowano bez użycia biblioteka funkcji matematycznych ułatwia porównanie). Możesz wprowadzić kod ręcznie zapoznać się z niektórymi z [Python funkcje edytowania](editing-python-code-in-visual-studio.md).

    ```python
    from itertools import islice
    from random import random
    from time import perf_counter

    COUNT = 500000  # Change this value depending on the speed of your computer
    DATA = list(islice(iter(lambda: (random() - 0.5) * 3.0, None), COUNT))

    e = 2.7182818284590452353602874713527

    def sinh(x):
        return (1 - (e ** (-2 * x))) / (2 * (e ** -x))

    def cosh(x):
        return (1 + (e ** (-2 * x))) / (2 * (e ** -x))

    def tanh(x):
        tanh_x = sinh(x) / cosh(x)
        return tanh_x

    def test(fn, name):
        start = perf_counter()
        result = fn(DATA)
        duration = perf_counter() - start
        print('{} took {:.3f} seconds\n\n'.format(name, duration))

        for d in result:
            assert -1 <= d <= 1, " incorrect values"

    if __name__ == "__main__":
        print('Running benchmarks with COUNT = {}'.format(COUNT))

        test(lambda d: [tanh(x) for x in d], '[tanh(x) for x in d] (Python implementation)')
    ```

1. Uruchamianie przy użyciu programu **debugowania** > **Uruchom bez debugowania** (**Ctrl**+**F5**) aby wyświetlić wyniki. Można dostosować `COUNT` zmiennej do zmiany, jak długo trwa testów porównawczych, aby uruchomić. Na potrzeby tego przewodnika Ustaw liczbę, tak aby testu porównawczego około dwóch sekund.

> [!TIP]
> Podczas uruchamiania testów porównawczych, należy zawsze używać **debugowania** > **Uruchom bez debugowania** w celu uniknięcia koszty naliczane podczas uruchamiania kodu w debugerze programu Visual Studio.

## <a name="create-the-core-c-projects"></a>Tworzenie podstawowych projektów C++

Postępuj zgodnie z instrukcjami w tej sekcji, aby utworzyć dwa identyczne projekty języka C++ o nazwie "superfastcode" i "superfastcode2". Później użyjesz innego oznacza, że w każdym projekcie do udostępnienia kodu C++ do języka Python.

1. Upewnij się, że `PYTHONHOME` zmienna środowiskowa jest ustawiona do interpretera języka Python chcesz użyć. Projekty języka C++ w programie Visual Studio zależą od tej zmiennej, aby zlokalizować pliki, takie jak *python.h*, które są używane podczas tworzenia rozszerzenie języka Python.

1. Kliknij prawym przyciskiem myszy rozwiązanie w **Eksploratora rozwiązań** i wybierz **Dodaj** > **nowy projekt**. Rozwiązania programu Visual Studio może zawierać zarówno Python projektów języka C++ i razem (czyli jedną z zalet używania programu Visual Studio dla języka Python).

1. Wyszukiwanie w "C++" Wybierz **pusty projekt**, określ nazwę "superfastcode" ("superfastcode2" dla drugiego projektu) i wybierz **OK**.

    > [!Tip]
    > Za pomocą **Python natywne narzędzia programistyczne** zainstalowany w programie Visual Studio, można uruchomić z **modułu rozszerzenia języka Python** szablonu zamiast tego, który ma wiele opisane poniżej już w miejscu. W ramach tego przewodnika, zaczynając od pustego projektu pokazuje tworzenia modułu rozszerzenia krok po kroku. Po zrozumieniu procesu zapisuje szablon pozwala oszczędzić czas podczas pisania własnych rozszerzeń.

1. Utwórz plik języka C++ w nowym projekcie, klikając prawym przyciskiem myszy **pliki źródłowe** węzła, następnie wybierz pozycję **Dodaj** > **nowy element**, wybierz opcję **pliku C++**, nadaj jej nazwę `module.cpp`i wybierz **OK**.

    > [!Important]
    > Plik o *.cpp* rozszerzenie jest konieczne włączyć na stronach właściwości języka C++ w kolejnych krokach.

1. Kliknij prawym przyciskiem myszy projekt C++ w **Eksploratora rozwiązań**, wybierz opcję **właściwości**.

1. W górnej części **stron właściwości** wyświetlonym oknie dialogowym Ustaw **konfiguracji** do **wszystkie konfiguracje** i **platformy** do **Win32**.

1. Ustaw określone właściwości, zgodnie z opisem w poniższej tabeli, a następnie wybierz **OK**.

    | Tab | Właściwość | Wartość |
    | --- | --- | --- |
    | **Ogólne** | **Ogólne** > **Nazwa docelowej** | Określ nazwę modułu dowolną do odwoływania się do niego za pomocą języka Python w `from...import` instrukcji. Użyjesz tej samej nazwie w C++ podczas definiowania modułu dla języka Python. Jeśli chcesz użyć nazwy projektu jako nazwa modułu, pozostaw wartość domyślną **$(ProjectName)**. |
    | | **Ogólne** > **rozszerzenie docelowe** | **.pyd** |
    | | **Wartości domyślne projektu** > **typ konfiguracji** | **Biblioteka dynamiczna (dll)** |
    | **C/C++** > **ogólne** | **Dodatkowe katalogi dyrektywy Include** | Język Python został dodany *obejmują* folder jako odpowiednią dla tej instalacji, na przykład `c:\Python36\include`.  |
    | **C/C++** > **preprocesora** | **Definicje preprocesora** | **CPython tylko**: Dodaj `Py_LIMITED_API;` na początku ciągu znaków (łącznie ze średnikiem). Ta definicja ogranicza niektóre funkcje, można wywołać za pomocą języka Python i sprawia, że kod jest bardziej przenośny między różnymi wersjami języka Python. Jeśli pracujesz z PyBind11, nie dodawaj tej definicji, w przeciwnym razie zostaną wyświetlone błędy kompilacji. |
    | **C/C++** > **generowanie kodu** | **Biblioteka środowiska uruchomieniowego** | **Wielowątkowa Biblioteka DLL (/ MD)** (zobacz poniższe ostrzeżenie) |
    | **Konsolidator** > **ogólne** | **Dodatkowe katalogi biblioteki** | Język Python został dodany *libs* folder zawierający *.lib* pliki jako odpowiednią dla tej instalacji, na przykład `c:\Python36\libs`. (Pamiętaj wskazywał *libs* folder, który zawiera *.lib* pliki, i *nie* *Lib* folder, który zawiera *.py*  pliki.) |

    > [!Tip]
    > Jeśli nie widzisz karty C/C++ we właściwościach projektu jest to, ponieważ projekt nie zawiera wszystkie pliki, które identyfikuje go jako pliki źródłowe C/C++. Ten stan może wystąpić, jeśli utworzysz plik źródłowy bez *.c* lub *.cpp* rozszerzenia. Na przykład, jeśli przypadkowo wprowadzone `module.coo` zamiast `module.cpp` w okno dialogowe nowego elementu wcześniej, następnie programu Visual Studio tworzy plik, ale nie ustawiono typu pliku "C / C + kodu," który jest co aktywuje kartę właściwości języka C/C++. Takie misidentification pozostaje tak, nawet w przypadku zmiany nazwy pliku z `.cpp`. Aby prawidłowo ustawić typ pliku, kliknij prawym przyciskiem myszy plik w **Eksploratora rozwiązań**, wybierz opcję **właściwości**, a następnie ustaw **typ pliku** do **kodu C/C++**.

    > [!Warning]
    > Zawsze wartość **C/C++** > **generowania kodu** > **biblioteki środowiska uruchomieniowego** opcję **Multi-threaded biblioteki DLL (/ MD)**, nawet dla konfiguracji debugowania, ponieważ jest to ustawienie, co to są tworzone za pomocą plików binarnych języka Python bez debugowania. Za pomocą języka CPython, jeśli to się zdarzyć, aby ustawić **Multi-threaded DLL debugowania (/ MDd)** opcję tworzenia **debugowania** konfiguracji powoduje błąd **C1189: Py_LIMITED_API jest niezgodna z Py_DEBUG Py_TRACE_REFS i Py_REF_DEBUG**. Ponadto jeśli usuniesz `Py_LIMITED_API` (który jest wymagany przy użyciu języka CPython, ale nie PyBind11) w celu uniknięcia błędów kompilacji, Python ulega awarii podczas próby zaimportowania modułu. (Awaria się dzieje w ramach wywołania biblioteki DLL `PyModule_Create` opisana poniżej, z komunikatu wyjściowego **błąd krytyczny Python: PyThreadState_Get: nie bieżącego wątku**.)
    >
    > Opcja/mdd służy do tworzenia plików binarnych debugowania języka Python (takie jak *python_d.exe*), ale wybierając go z rozszerzeniem DLL nadal powoduje błąd kompilacji za pomocą `Py_LIMITED_API`.

1. Kliknij prawym przyciskiem myszy projekt C++, a następnie wybierz pozycję **kompilacji** do testowania konfiguracji (zarówno **debugowania** i **wersji**). *.Pyd* pliki znajdują się w **rozwiązania** folderze **debugowania** i **wersji**, nie C++ projektu sam folder.

1. Dodaj następujący kod do projektu C++ *module.cpp* pliku:

    ```cpp
    #include <Windows.h>
    #include <cmath>

    const double e = 2.7182818284590452353602874713527;

    double sinh_impl(double x) {
        return (1 - pow(e, (-2 * x))) / (2 * pow(e, -x));
    }

    double cosh_impl(double x) {
        return (1 + pow(e, (-2 * x))) / (2 * pow(e, -x));
    }

    double tanh_impl(double x) {
        return sinh_impl(x) / cosh_impl(x);
    }
    ```

1. Tworzenie projektu C++ ponownie, aby potwierdzić, że Twój kod jest poprawny.

1. Jeśli nie zostało to jeszcze zrobione, powtórz powyższe kroki, aby utworzyć drugi projekt o nazwie "superfastcode2" z identyczną zawartość.

## <a name="convert-the-c-projects-to-extensions-for-python"></a>Konwertowanie projektów w języku C++ do rozszerzenia dla języka Python

Aby biblioteki DLL C++ do rozszerzenia dla języka Python, po raz pierwszy zmodyfikujesz wyeksportowanego metody służące do interakcji z typów języka Python. Następnie dodaj funkcję, która eksportuje moduł oraz definicje metod modułu.

W kolejnych sekcjach wyjaśniono, jak wykonać te kroki przy użyciu rozszerzenia języka CPython i PyBind11.

### <a name="cpython-extensions"></a>Rozszerzenia języka CPython

W tle, na które zostaną uwzględnione w tej sekcji dla języka Python 3.x, można znaleźć [Python/C API Reference Manual](https://docs.python.org/3/c-api/index.html) , a w szczególności [obiektów modułu](https://docs.python.org/3/c-api/module.html) w witrynie python.org (Pamiętaj wybrać wersję języka Python z Kontrolka listy rozwijanej w prawym górnym rogu, aby wyświetlić poprawne dokumentację).

Jeśli pracujesz z języka Python 2.7 się [rozszerzenie języka Python 2.7 z C lub C++](https://docs.python.org/2.7/extending/extending.html) i [przenoszenie modułów rozszerzeń Python 3](https://docs.python.org/2.7/howto/cporting.html) (python.org).

1. W górnej części *module.cpp*, obejmują *Python.h*:

    ```cpp
    #include <Python.h>
    ```

1. Modyfikowanie `tanh_impl` metodę, aby zaakceptować i zwracanych typów języka Python ( `PyOjbect*`, to znaczy):

    ```cpp
    PyObject* tanh_impl(PyObject *, PyObject* o) {
        double x = PyFloat_AsDouble(o);
        double tanh_x = sinh_impl(x) / cosh_impl(x);
        return PyFloat_FromDouble(tanh_x);
    }
    ```

1. Dodaj strukturę, która definiuje sposób C++ `tanh_impl` funkcji jest prezentowana w języku Python:

    ```cpp
    static PyMethodDef superfastcode_methods[] = {
        // The first property is the name exposed to Python, fast_tanh, the second is the C++
        // function name that contains the implementation.
        { "fast_tanh", (PyCFunction)tanh_impl, METH_O, nullptr },

        // Terminate the array with an object containing nulls.
        { nullptr, nullptr, 0, nullptr }
    };
    ```

1. Dodaj to struktura, która definiuje moduł, w których chcesz się do niego odwoływać w kodzie języka Python, szczególnie w przypadku korzystania z `from...import` instrukcji. (To pasuje do wartości we właściwościach projektu w obszarze **właściwości konfiguracji** > **ogólne** > **Nazwa docelowego**.) W poniższym przykładzie nazwa modułu "superfastcode" oznacza, że można użyć `from superfastcode import fast_tanh` w języku Python, ponieważ `fast_tanh` jest zdefiniowana w `superfastcode_methods`. (Takich jak nazwy plików wewnętrznych do projektu C++, *module.cpp*, nie mają wpływu.)

    ```cpp
    static PyModuleDef superfastcode_module = {
        PyModuleDef_HEAD_INIT,
        "superfastcode",                        // Module name to use with Python import statements
        "Provides some functions, but faster",  // Module description
        0,
        superfastcode_methods                   // Structure that defines the methods of the module
    };
    ```

1. Dodaj metodę, która wywołuje języka Python, ładuje moduł, który musi mieć nazwę `PyInit_<module-name>`, gdzie &lt;Nazwa modułu&gt; dokładnie odpowiada projektu C++ **ogólne** > **docelowej Nazwa** właściwości (oznacza to, że jest on zgodny nazwę pliku *.pyd* skompilowany na podstawie projektu).

    ```cpp
    PyMODINIT_FUNC PyInit_superfastcode() {
        return PyModule_Create(&superfastcode_module);
    }
    ```

1. Ustaw docelową konfigurację **wersji** i skompiluj projekt C++, ponownie, aby zweryfikować Twojego kodu. Jeśli wystąpią błędy, zobacz [Rozwiązywanie problemów](#troubleshooting) poniższej sekcji.

### <a name="pybind11"></a>PyBind11

Jeśli wykonaniu kroków opisanych w poprzedniej sekcji, możesz bez obaw zauważyć używane mnóstwo schematyczny kod służący do tworzenia struktur niezbędny moduł dla kodu C++. PyBind11 upraszcza ten proces, za pomocą makr w pliku nagłówka C++, które osiągnąć ten sam wynik, za pomocą znacznie mniejszej ilości kodu. Aby uzyskać podstawowe informacje dotyczące przedstawionego w tej sekcji, zobacz [podstawy PyBind11](https://github.com/pybind/pybind11/blob/master/docs/basics.rst) (github.com).

1. Zainstaluj PyBind11 przy użyciu narzędzia pip: `pip install pybind11` lub `py -m pip install pybind11`.

1. W górnej części *module.cpp*, obejmują *pybind11.h*:

    ```cpp
    #include <pybind11/pybind11.h>
    ```

1. W dolnej części *module.cpp*, użyj `PYBIND11_MODULE` makra, aby zdefiniować punkt wejścia dla funkcji języka C++:

    ```cpp
    namespace py = pybind11;

    PYBIND11_MODULE(superfastcode2, m) {
        m.def("fast_tanh2", &tanh_impl, R"pbdoc(
            Compute a hyperbolic tangent of a single argument expressed in radians.
        )pbdoc");

    #ifdef VERSION_INFO
        m.attr("__version__") = VERSION_INFO;
    #else
        m.attr("__version__") = "dev";
    #endif
    }
    ```

1. Ustaw docelową konfigurację **wersji** i skompiluj projekt C++, aby zweryfikować Twojego kodu. Jeśli wystąpią błędy, zobacz następną sekcję na temat rozwiązywania problemów.

### <a name="troubleshooting"></a>Rozwiązywanie problemów

Modułu języka C++ mogą kompilacja nie powiedzie się z następujących powodów:

- Nie można zlokalizować *Python.h* (**E1696: nie można otworzyć pliku źródłowego "Python.h"** i/lub **C1083: Otwórz, nie można dołączyć plik: "Python.h": Nie ma takiego pliku lub katalogu**): Upewnij się, że ścieżka w **C/C++** > **ogólne** > **dodatkowe katalogi dołączenia** w Projekt właściwości punkty z instalacją języka Python *obejmują* folderu. Zobacz krok 6 w sekcji [Tworzenie projektu core C++](#create-the-core-c-projects).

- Nie można zlokalizować biblioteki języka Python: Upewnij się, że ścieżka w **konsolidatora** > **ogólne** > **dodatkowe katalogi bibliotek** w projekcie wskazuje właściwości z instalacją języka Python *libs* folderu. Zobacz krok 6 w sekcji [Tworzenie projektu core C++](#create-the-core-c-projects).

- Błędy konsolidatora dotyczące architektury docelowej: zmiana docelowej C++ projektu architektury, aby był zgodny z instalacją języka Python. Na przykład jeśli zostaną objęci x64 z projektu C++, ale z instalacją języka Python jest x86, należy zmienić projektu C++ pod kątem x86.

## <a name="test-the-code-and-compare-the-results"></a>Testowanie kodu i porównać wyniki

Teraz, gdy masz biblioteki DLL postacią rozszerzenia języka Python, można odwoływać się do nich z projektu języka Python, zaimportuj moduły i użyć ich metod.

### <a name="make-the-dll-available-to-python"></a>Udostępnia bibliotekę DLL języka Python

Istnieją dwa sposoby, aby udostępnić biblioteki DLL języka Python.

Pierwsza metoda działa, jeśli projektu w języku Python i projektu C++ znajdują się w tym samym rozwiązaniu. Przejdź do **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania** węzła w projektu w języku Python, a następnie wybierz **Dodaj odwołanie**. W wyświetlonym oknie dialogowym wybierz **projektów** , a następnie wybierz oba **superfastcode** i **superfastcode2** projektów, a następnie wybierz **OK**.

![Dodawanie odwołania do projektu superfastcode](media/cpp-add-reference.png)

Alternatywna metoda, opisane w poniższych krokach instaluje moduł w środowisku globalnym języka Python, udostępniając je do innych projektów języka Python. (Dlatego zwykle wymaga odświeżania bazy danych uzupełniania IntelliSense dla tego środowiska w programie Visual Studio 2017 w wersji 15.5 i starszych. Trwa odświeżanie jest również podczas usuwania modułu ze środowiska.)

1. Jeśli używasz programu Visual Studio 2017 lub później, uruchom Instalatora programu Visual Studio, wybierz **Modyfikuj**, wybierz opcję **poszczególne składniki** > **kompilatory, narzędzia do kompilacji i środowiska uruchomieniowe**   >  **Zestaw narzędzi w wersji 140 visual C++ 2015.3**. Ten krok jest niezbędny, ponieważ Python (dla Windows) jest tworzone za pomocą programu Visual Studio 2015 (wersja 14.0) i oczekuje, że te narzędzia są dostępne podczas kompilowania rozszerzenia za pomocą metody opisane w tym miejscu. (Zwróć uwagę, że może być konieczne do zainstalowania 32-bitowej wersji środowiska Python i docelowa bibliotek DLL systemu Win32 i nie x64).

1. Utwórz plik o nazwie *pliku setup.py* w projekcie języka C++, klikając prawym przyciskiem myszy projekt i wybierając **Dodaj** > **nowy element**. Następnie wybierz pozycję **plik C++ (.cpp)**, nadaj plikowi nazwę `setup.py`i wybierz **OK** (plikowi z *PY* rozszerzenia sprawia, że program Visual Studio rozpoznaje je jako języka Python Pomimo przy użyciu języka C++ plik szablonu). Gdy plik zostanie wyświetlony w edytorze, wklej następujący kod do niego odpowiednie dla metody rozszerzenia:

    **Rozszerzenia języka CPython (projekt superfastcode):**

    ```python
    from distutils.core import setup, Extension, DEBUG

    sfc_module = Extension('superfastcode', sources = ['module.cpp'])

    setup(name = 'superfastcode', version = '1.0',
        description = 'Python Package with superfastcode C++ extension',
        ext_modules = [sfc_module]
        )
    ```

    Zobacz [rozszerzenia konstrukcyjne C i C++](https://docs.python.org/3/extending/building.html) (python.org) dokumentację dotyczącą tego skryptu.

    **PyBind11 (projekt superfastcode2):**

    ```python
    import os, sys

    from distutils.core import setup, Extension
    from distutils import sysconfig

    cpp_args = ['-std=c++11', '-stdlib=libc++', '-mmacosx-version-min=10.7']

    sfc_module = Extension(
        'superfastcode2', sources = ['module.cpp'],
        include_dirs=['pybind11/include'],
        language='c++',
        extra_compile_args = cpp_args,
        )

    setup(
        name = 'superfastcode2',
        version = '1.0',
        description = 'Python package with superfastcode2 C++ extension (PyBind11)',
        ext_modules = [sfc_module],
    )
    ```

1. *Pliku setup.py* kodu powoduje, że języka Python w celu skompilowania rozszerzenia przy użyciu zestawu narzędzi Visual Studio 2015 C++, gdy jest używana z wiersza polecenia. Otwórz wiersz polecenia z podwyższonym poziomem uprawnień, przejdź do folderu zawierającego projekt języka C++ (czyli folderu, który zawiera *pliku setup.py*), a następnie wprowadź następujące polecenie:

    ```command
    pip install .
    ```

    lub:

    ```command
    py -m pip install .
    ```

### <a name="call-the-dll-from-python"></a>Wywołania biblioteki DLL za pomocą języka Python

Po utworzeniu biblioteki DLL dostępnych do języka Python zgodnie z opisem w poprzedniej sekcji, teraz można wywołać `superfastcode.fast_tanh` i `superfastcode2.fast_tanh2` funkcji za pomocą języka Python code i porównaj ich wydajności do implementacji języka Python:

1. Dodaj następujące wiersze w swojej *PY* plik, aby wywołać metody wyeksportowane z biblioteki dll i wyświetlić ich dane wyjściowe:

    ```python
    from superfastcode import fast_tanh
    test(lambda d: [fast_tanh(x) for x in d], '[fast_tanh(x) for x in d] (CPython C++ extension)')

    from superfastcode2 import fast_tanh2
    test(lambda d: [fast_tanh2(x) for x in d], '[fast_tanh2(x) for x in d] (PyBind11 C++ extension)')
    ```

1. Uruchom Python program (**debugowania** > **Uruchom bez debugowania** lub **Ctrl**+**F5**) i Zauważ, że procedury C++ uruchomić około pięciu do dwudziestego razy szybciej niż implementacji języka Python. Typowe dane wyjściowe wyglądają następująco:

    ```output
    Running benchmarks with COUNT = 500000
    [tanh(x) for x in d] (Python implementation) took 0.758 seconds

    [fast_tanh(x) for x in d] (CPython C++ extension) took 0.076 seconds

    [fast_tanh2(x) for x in d] (PyBind11 C++ extension) took 0.204 seconds
    ```

    Jeśli **Rozpocznij bez debugowania** polecenie jest wyłączone, kliknij prawym przyciskiem myszy projekt języka Python w **Eksploratora rozwiązań** i wybierz **Ustaw jako projekt startowy**.

1. Spróbuj zwiększyć `COUNT` zmiennej, dzięki czemu różnic jest bardziej widoczny. A **debugowania** kompilacji modułu języka C++ również działa wolniej niż **wersji** kompilacji, ponieważ **debugowania** kompilacji mniej jest zoptymalizowany i zawiera różne sprawdzanie błędów. Możesz przełączać się między tymi konfiguracjami dla porównania.

> [!NOTE]
> W danych wyjściowych można zobaczyć, czy rozszerzenie PyBind11 nie jest tak szybko, jak rozszerzenie języka CPython, jakby było nadal znacznie szybsze niż prosta implementacja języka Python. Różnica polega na ze względu na małą ilością obciążenie każdego wywołania PyBind11 wprowadzono w celu zapewnienia jego interfejs C++ znacznie prostsze. Ta różnica na wywołanie jest rzeczywiście dość nieznaczny: ponieważ kod testowy wywołuje funkcje rozszerzenia 500 000 razy, wyniki, zobaczysz tutaj znacznie uzupełnienie tego obciążenie! Zazwyczaj funkcji języka C++ jest dużo więcej pracy niż prosta `fast_tanh[2]` metody używane w tym miejscu, w którym to przypadku obciążenie "nieważne". Jednak w przypadku wdrażania metod, które mogą być wywoływane tysięcy razy na sekundę, przy użyciu podejścia CPython może spowodować lepszą wydajność niż PyBind11.

## <a name="debug-the-c-code"></a>Możliwe jest debugowanie kodu języka C++

Program Visual Studio obsługuje debugowania kodu języka Python i C++ ze sobą. W tej sekcji przedstawiono proces, za pomocą **superfastcode** projektu; kroki są takie same dla **superfastcode2** projektu.

1. Kliknij prawym przyciskiem myszy projekt języka Python w **Eksploratora rozwiązań**, wybierz opcję **właściwości**, wybierz opcję **debugowania** , a następnie wybierz pozycję **debugowania**  >  **Włącz debugowanie kodu natywnego** opcji.

    > [!Tip]
    > Jeśli włączone jest debugowanie kodu natywnego, w oknie danych wyjściowych języka Python może zniknąć natychmiast po zakończeniu program bez umożliwiając zwykłego **naciśnij dowolny klawisz, aby kontynuować** wstrzymania. Aby wymusić przerwie, należy dodać `-i` opcję **Uruchom** > **argumenty Interpreter** na **debugowania** kartę, gdy włączone jest debugowanie kodu natywnego . Ten argument umieszcza interpreter języka Python w trybie interaktywnym po zakończeniu wykonywania kodu, w tym momencie czeka na naciśnięcie klawisza **Ctrl**+**Z** > **Enter**  aby wyjść. (Alternatywnie Jeśli nie masz nic, modyfikowania kodu w języku Python, możesz dodać `import os` i `os.system("pause")` instrukcji pod koniec programu. Ten kod jest duplikatem oryginalnego wiersza wstrzymania.)

1. Wybierz **pliku** > **Zapisz** można zapisać zmiany właściwości.

1. Ustaw konfigurację kompilacji **debugowania** na pasku narzędzi programu Visual Studio.

    ![Ustawienie konfiguracji kompilacji do debugowania](media/cpp-set-debug.png)

1. Ponieważ kod jest ogólnie dłużej do uruchamiania w debugerze, możesz chcieć zmienić `COUNT` zmienną swoje *PY* plik, aby wartość, która jest około 5 razy mniejsza (na przykład zmień go z `500000` do `100000`).

1. W kodzie języka C++, należy ustawić punkt przerwania w pierwszym wierszu `tanh_impl` metody, a następnie uruchamiania debugera (**F5** lub **debugowania** > **Rozpocznij debugowanie**). Debuger zatrzymuje się po wywołaniu tego kodu. Jeśli nie zostanie osiągnięty punkt przerwania, sprawdź, czy konfiguracja jest ustawiona **debugowania** i zapisany projekt (co nie jest wykonywane automatycznie podczas uruchamiania debugowania).

    ![Zatrzymywanie w punkcie przerwania w kodzie C++](media/cpp-debugging.png)

1. W tym momencie można przejść przez kod języka C++, Sprawdź zmienne i tak dalej. Te funkcje są szczegółowo opisane w [debugowania C++ i Python razem](debugging-mixed-mode-c-cpp-python-in-visual-studio.md).

## <a name="alternative-approaches"></a>Alternatywnych metod

Istnieją różne oznacza, że do tworzenia rozszerzenia języka Python, zgodnie z opisem w poniższej tabeli. Pierwsze dwie pozycje CPython i PyBind11 to, co została omówiona w tym artykule już.

| Podejście | Zbioru | Reprezentatywny użytkowników | Pro(s) | CON(s) |
| --- | --- | --- | --- | --- |
| Moduły rozszerzenia języka C/C++ dla języka CPython | 1991 | Standardowa biblioteka | [Szczegółową dokumentację i samouczki](https://docs.python.org/3/c-api/). Łączna liczba kontroli. | Kompilacja, przenoszenia odwoływać się do zarządzania. Wysoka znajomość języka C. |
| [PyBind11](https://github.com/pybind/pybind11) (zalecane dla języka C++) | 2015 |  | Lekkie, tylko nagłówek Biblioteka do tworzenia powiązań języka Python z istniejącego kodu C++. Kilka zależności. Zgodność PyPy. | Nowsze, mniej dojrzałe. Dużego wykorzystania funkcji C ++ 11. Krótką listę wymagań obsługiwane kompilatory (Visual Studio jest dołączony). |
| Cython (zalecane dla języka C) | 2007 | [gevent](https://www.gevent.org/), [kivy](https://kivy.org/) | Podobne języka Python. Wysoce dojrzała. O wysokiej wydajności. | Kompilacja, nowej składni, nowe łańcucha narzędzi. |
| [Boost.Python](https://www.boost.org/doc/libs/1_66_0/libs/python/doc/html/index.html) | 2002 | | Działa z niemal każdego kompilatora języka C++. | Pakiet biblioteki; dużych i złożonych zawiera wiele obejścia stare kompilatory. |
| ctypes | 2003 | [oscrypto](https://github.com/wbond/oscrypto) | Nie kompilacja powszechną dostępność. | Uzyskiwanie dostępu do i mutacja struktur C skomplikowana względem i podatne. |
| SWIG | 1996 | [crfsuite](http://www.chokkan.org/software/crfsuite/) | Generowanie jednocześnie powiązania dla wielu języków. | Nadmiernego obciążenia, jeśli Python jest jedynym miejscem docelowym. |
| cffi | 2013 | [Kryptografia](https://cryptography.io/en/latest/), [pypy](https://pypy.org/) | Łatwość integracji, PyPy zgodności. | Nowsze, mniej dojrzałe. |
| [cppyy](https://cppyy.readthedocs.io/en/latest/) | 2017 | | Podobnie jak cffi przy użyciu języka C++. | Nowsze, może mieć problemy z programu VS 2017. |

## <a name="see-also"></a>Zobacz także

Ukończone próbkę z tego przewodnika znajdują się na [rozszerzenie języka python — przykłady vs-cpp](https://github.com/Microsoft/python-sample-vs-cpp-extension) (GitHub).

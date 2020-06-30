---
title: Pisanie rozszerzeń C++ dla języka Python
description: Przewodnik tworzenia rozszerzenia C++ dla języka Python przy użyciu programu Visual Studio, CPython i PyBind11, w tym debugowania w trybie mieszanym.
ms.date: 11/19/2018
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 0871361d25131b493838bac12945a64a19a0f173
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543731"
---
# <a name="create-a-c-extension-for-python"></a>Tworzenie rozszerzenia C++ dla języka Python

Moduły w języku C++ (lub C) są zwykle używane do rozbudowy funkcji interpretera języka Python, a także do zapewnienia dostępu do funkcji systemu operacyjnego niskiego poziomu. Istnieją trzy podstawowe typy modułów:

- Moduły akceleratora: ponieważ Python jest językiem interpretowanym, niektóre fragmenty kodu można napisać w języku C++ w celu zwiększenia wydajności.
- Moduły otoki: udostępniają istniejące interfejsy C/C++ do kodu Python lub uwidaczniają więcej interfejsu API "Python", który jest łatwy do użycia w języku Python.
- Moduły dostępu do systemu niskiego poziomu: utworzone w celu uzyskania dostępu do funkcji niższego poziomu środowiska uruchomieniowego CPython, systemu operacyjnego lub podstawowego sprzętu.

Ten artykuł zawiera instrukcje tworzenia modułu rozszerzenia C++ dla CPython, który oblicza tangens hiperboliczny i wywołuje go z kodu języka Python. Procedura jest implementowana najpierw w języku Python, aby zademonstrować względny wzrost wydajności implementacji tej samej procedury w C++.

W tym artykule przedstawiono również dwa sposoby udostępnienia C++ w języku Python:

- Standardowe rozszerzenia CPython zgodnie z opisem w [dokumentacji języka Python](https://docs.python.org/3/c-api/)
- [PyBind11](https://github.com/pybind/pybind11), która jest zalecana dla języka C++ 11 ze względu na prostotę.

Porównanie tych i innych metod znajduje się w ramach [alternatywnych metod](#alternative-approaches) na końcu tego artykułu.

Ukończony przykład z tego przewodnika można znaleźć w języku [Python-Samples-vs-CPP-Extension](https://github.com/Microsoft/python-sample-vs-cpp-extension) (GitHub).

## <a name="prerequisites"></a>Wymagania wstępne

- Program Visual Studio 2017 lub nowszy z **programowaniem dla komputerów stacjonarnych** i środowiskami programowania w języku C++ i **Python** instalowanymi z opcjami domyślnymi.
- W obciążeniu programowanie w języku **Python** zaznacz również pole po prawej stronie dla **natywnych narzędzi programistycznych języka Python**. Ta opcja umożliwia skonfigurowanie większości konfiguracji opisanej w tym artykule. (Ta opcja obejmuje również automatyczne obciążenie języka C++).

    ![Wybieranie opcji natywnych narzędzi programistycznych języka Python](media/cpp-install-native.png)

    > [!Tip]
    > Zainstalowanie obciążenia analizy **danych i aplikacji analitycznych** obejmuje również opcję Python i **natywne narzędzia programistyczne języka Python** .

Aby uzyskać więcej informacji, zobacz [Instalowanie obsługi języka Python dla programu Visual Studio](installing-python-support-in-visual-studio.md), w tym używanie innych wersji programu Visual Studio. Jeśli instalujesz środowisko Python oddzielnie, pamiętaj o wybraniu pozycji **Pobierz symbole debugowania** i **Pobierz pliki binarne debugowania** w obszarze **Opcje zaawansowane** w instalatorze. Ta opcja zapewnia, że wymagane biblioteki debugowania są dostępne w przypadku wybrania opcji wykonaj kompilację debugowania.

## <a name="create-the-python-application"></a>Tworzenie aplikacji w języku Python

1. Utwórz nowy projekt w języku Python w programie Visual Studio, wybierając pozycję **plik**  >  **Nowy**  >  **projekt**. Wyszukaj ciąg "Python", wybierz szablon **aplikacji** w języku Python, nadaj mu odpowiednią nazwę i lokalizację, a następnie wybierz **przycisk OK**.

1. Praca z C++ wymaga użycia interpretera języka Python 32-bitowego (zalecane środowisko Python 3,6 lub nowsze). W oknie **Eksplorator rozwiązań** programu Visual Studio rozwiń węzeł projektu, a następnie rozwiń węzeł **środowiska Python** . Jeśli nie widzisz środowiska 32-bitowego jako domyślnego (pogrubione lub oznaczone jako domyślne **globalne**), postępuj zgodnie z instrukcjami w sekcji [Wybierz środowisko Python dla projektu](selecting-a-python-environment-for-a-project.md). Jeśli nie masz zainstalowanego interpretera 32-bitowego, zobacz [Instalowanie interpreterów języka Python](installing-python-interpreters.md).

1. W pliku *. PR* projektu wklej następujący kod, który przeprowadza testy porównawcze dla obliczeń tangensa hiperbolicznego (zaimplementowane bez użycia biblioteki matematycznej w celu łatwiejszego porównania). Możesz wprowadzić kod ręcznie, aby korzystać z niektórych [funkcji edytowania języka Python](editing-python-code-in-visual-studio.md).

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

1. Uruchom program przy użyciu polecenia **Debuguj**  >  **Uruchom bez debugowania** (**Ctrl** + **F5**), aby wyświetlić wyniki. Można dostosować zmienną, `COUNT` Aby zmienić czas wykonywania testu porównawczego. Na potrzeby tego instruktażu Ustaw liczbę tak, aby wynik testu porównawczego wynosił około dwóch sekund.

> [!TIP]
> Podczas wykonywania testów porównawczych należy zawsze używać **debugowania**  >  **Rozpocznij bez debugowania** , aby uniknąć narzutu związanego z uruchamianiem kodu w debugerze programu Visual Studio.

## <a name="create-the-core-c-projects"></a>Tworzenie podstawowych projektów C++

Postępuj zgodnie z instrukcjami w tej sekcji, aby utworzyć dwa identyczne projekty C++ o nazwie "superfastcode" i "superfastcode2". Później będziesz używać różnych środków w każdym projekcie w celu udostępnienia kodu C++ w języku Python.

1. Upewnij się, że `PYTHONHOME` zmienna środowiskowa jest ustawiona na interpreter języka Python, którego chcesz użyć. Projekty C++ w programie Visual Studio polegają na tej zmiennej do lokalizowania plików, takich jak *Python. h*, które są używane podczas tworzenia rozszerzenia języka Python.

1. Kliknij prawym przyciskiem myszy rozwiązanie w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj**  >  **Nowy projekt**. Rozwiązanie programu Visual Studio może zawierać zarówno projekty w języku Python, jak i C++ (które są jedną z zalet korzystania z programu Visual Studio dla języka Python).

1. Wyszukaj ciąg "C++", wybierz pozycję **pusty projekt**, określ nazwę "superfastcode" ("superfastcode2" dla drugiego projektu), a następnie wybierz **przycisk OK**.

    > [!Tip]
    > Za pomocą **natywnych narzędzi programistycznych języka Python** zainstalowanych w programie Visual Studio można zacząć od szablonu **modułu rozszerzenia języka Python** , który ma wiele czynności opisanych poniżej. W tym instruktażu, zaczynając od pustego projektu, pokazuje, jak utworzyć moduł rozszerzenia krok po kroku. Po zrozumieniu tego procesu szablon zapisuje czas podczas pisania własnych rozszerzeń.

1. Utwórz plik języka C++ w nowym projekcie, klikając prawym przyciskiem myszy węzeł **pliki źródłowe** , a następnie wybierz polecenie **Dodaj**  >  **nowy element**, wybierz **plik C++** i nadaj mu nazwę `module.cpp` , a następnie wybierz **przycisk OK**.

    > [!Important]
    > Plik z rozszerzeniem *. cpp* jest niezbędny do włączenia stron właściwości C++ w następujących krokach.

1. Kliknij prawym przyciskiem myszy projekt C++ w **Eksplorator rozwiązań**, wybierz pozycję **Właściwości**.

1. W górnej części okna dialogowego **strony właściwości** , które zostanie wyświetlone, ustaw **konfigurację** na **wszystkie konfiguracje** i **platformę** **Win32**.

1. Ustaw określone właściwości zgodnie z opisem w poniższej tabeli, a następnie wybierz przycisk **OK**.

    | Tab | Właściwość | Wartość |
    | --- | --- | --- |
    | **Ogólne** | **Ogólne**  >  **Nazwa elementu docelowego** | Określ nazwę modułu, która ma być odwołująca się do niego z języka Python w `from...import` instrukcjach. Ta sama nazwa jest używana w języku C++ podczas definiowania modułu dla języka Python. Jeśli chcesz użyć nazwy projektu jako nazwy modułu, pozostaw wartość domyślną **$ (ProjectName)**. |
    | | **Ogólne**  >  **Rozszerzenie docelowe** | **. PYD** |
    | | **Wartości domyślne projektu**  >  **Typ konfiguracji** | **Biblioteka dynamiczna (. dll)** |
    | **C/C++**  >  **Ogólne** | **Dodatkowe katalogi dołączane** | Dodaj folder *dołączania* do języka Python zgodnie z potrzebami instalacji, na przykład `c:\Python36\include` .  |
    | **C/C++**  >  **Preprocesor** | **Definicje preprocesora** | **Tylko CPython**: Dodaj `Py_LIMITED_API;` do początku ciągu (z uwzględnieniem średnika). Ta definicja ogranicza niektóre funkcje, które można wywołać z języka Python i sprawia, że kod jest bardziej przenośny między różnymi wersjami języka Python. Jeśli pracujesz z usługą PyBind11, nie dodawaj tej definicji, w przeciwnym razie zobaczysz błędy kompilacji. |
    | **C/C++**  >  **Generowanie kodu** | **Biblioteka środowiska uruchomieniowego** | **Wielowątkowa Biblioteka DLL (/MD)** (Zobacz ostrzeżenie poniżej) |
    | **Konsolidator**  >  **Ogólne** | **Dodatkowe katalogi biblioteki** | Dodaj folder *libs* języka Python zawierający pliki *lib* , które są odpowiednie dla danej instalacji, na przykład `c:\Python36\libs` . (Należy wskazać folder *libs* zawierający pliki *. lib* , a *nie* folder *lib* zawierający pliki *. PR* ). |

    > [!Tip]
    > Jeśli nie widzisz karty C/C++ we właściwościach projektu, jest to spowodowane tym, że projekt nie zawiera żadnych plików identyfikowanych jako pliki źródłowe C/C++. Ten stan może wystąpić w przypadku utworzenia pliku źródłowego bez rozszerzenia *c* lub *CPP* . Jeśli na przykład przypadkowo wprowadzisz `module.coo` zamiast `module.cpp` w oknie dialogowym Nowy element, program Visual Studio utworzy plik, ale nie ustawi typu pliku na "C/C + Code", co oznacza, że aktywuje kartę właściwości C/C++. Taka niepodzielna identyfikacja pozostaje w przypadku, nawet jeśli zmieniono nazwę pliku na `.cpp` . Aby prawidłowo ustawić typ pliku, kliknij prawym przyciskiem myszy plik w **Eksplorator rozwiązań**, wybierz polecenie **Właściwości**, a następnie ustaw **Typ pliku** na **kod C/C++**.

    > [!Warning]
    > Zawsze ustawiaj **C/C++**  >  **Code Generation**  >  opcję**Biblioteka środowiska uruchomieniowego** generowania kodu C/C++ na **wielowątkową bibliotekę DLL (/MD)**, nawet w przypadku konfiguracji debugowania, ponieważ to ustawienie określa, które pliki binarne języka Python nie są debugowane. W przypadku korzystania z CPython, jeśli chcesz ustawić opcję **/MDD (wielowątkowe debugowanie biblioteki dll)** , utworzenie konfiguracji **debugowania** powoduje błąd **C1189: Py_LIMITED_API jest niezgodna z Py_DEBUG, Py_TRACE_REFS i Py_REF_DEBUG**. Ponadto jeśli usuniesz `Py_LIMITED_API` (który jest wymagany z CPython, ale nie PyBind11), aby uniknąć błędu kompilacji, podczas próby zaimportowania modułu środowisko Python ulega awarii. (Awaria występuje w ramach wywołania biblioteki DLL w `PyModule_Create` sposób opisany w dalszej części, z komunikatem wyjściowym **krytycznego błędu Python: PyThreadState_Get: Brak bieżącego wątku**).
    >
    > Opcja/MDd jest używana do kompilowania plików binarnych debugowania języka Python (takich jak *python_d.exe*), ale wybranie jej dla biblioteki DLL rozszerzenia nadal powoduje błąd kompilacji z `Py_LIMITED_API` .

1. Kliknij prawym przyciskiem myszy projekt C++ i wybierz opcję **Kompiluj** , aby przetestować konfiguracje ( **debugowanie** i **wydanie**). Pliki *. PYD* znajdują się w folderze **rozwiązania** w obszarze **debugowanie** i **wydanie**, a nie do samego folderu projektu C++.

1. Dodaj następujący kod do pliku *CPP modułu* projektu C++:

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

1. Ponownie skompiluj projekt C++, aby upewnić się, że kod jest poprawny.

1. Jeśli jeszcze tego nie zrobiono, powtórz powyższe kroki, aby utworzyć drugi projekt o nazwie "superfastcode2" z identyczną zawartością.

## <a name="convert-the-c-projects-to-extensions-for-python"></a>Konwertuj projekty C++ na rozszerzenia dla języka Python

Aby przekształcić bibliotekę C++ w rozszerzenie dla języka Python, należy najpierw zmodyfikować wyeksportowane metody w celu współpracy z typami języka Python. Następnie dodasz funkcję, która eksportuje moduł, wraz z definicjami metod modułu.

W poniższych sekcjach wyjaśniono, jak wykonać te kroki przy użyciu zarówno rozszerzeń CPython, jak i PyBind11.

### <a name="cpython-extensions"></a>Rozszerzenia CPython

Aby uzyskać informacje na temat elementów przedstawionych w tej sekcji dla języka Python 3. x, zapoznaj się z [podręcznikiem API języka Python/C](https://docs.python.org/3/c-api/index.html) , a zwłaszcza [obiektów modułów](https://docs.python.org/3/c-api/module.html) w Python.org (Pamiętaj o wybraniu wersji języka Python z kontrolki rozwijanej w górnym rogu, aby wyświetlić poprawną dokumentację).

Jeśli pracujesz z językiem Python 2,7, zapoznaj się z tematem [Rozszerzanie kodu python 2,7 przy użyciu języka C lub C++](https://docs.python.org/2.7/extending/extending.html) i [przenoszenie modułów rozszerzeń do języka Python 3](https://docs.python.org/2.7/howto/cporting.html) (Python.org).

1. W górnej części *modułu. cpp*Uwzględnij język *Python. h*:

    ```cpp
    #include <Python.h>
    ```

1. Zmodyfikuj `tanh_impl` metodę, aby akceptować i zwracać typy języka Python (a `PyOjbect*` , czyli):

    ```cpp
    PyObject* tanh_impl(PyObject *, PyObject* o) {
        double x = PyFloat_AsDouble(o);
        double tanh_x = sinh_impl(x) / cosh_impl(x);
        return PyFloat_FromDouble(tanh_x);
    }
    ```

1. Dodaj strukturę, która definiuje sposób `tanh_impl` przedstawiania funkcji języka C++ w języku Python:

    ```cpp
    static PyMethodDef superfastcode_methods[] = {
        // The first property is the name exposed to Python, fast_tanh, the second is the C++
        // function name that contains the implementation.
        { "fast_tanh", (PyCFunction)tanh_impl, METH_O, nullptr },

        // Terminate the array with an object containing nulls.
        { nullptr, nullptr, 0, nullptr }
    };
    ```

1. Dodaj strukturę, która definiuje moduł w taki sposób, aby odwoływać się do niego w kodzie w języku Python, w odniesieniu do `from...import` instrukcji. (Dopasuj ten element do wartości we właściwościach projektu w obszarze **Właściwości konfiguracji**  >  **Ogólne**  >  **Nazwa elementu docelowego**). W poniższym przykładzie nazwa modułu "superfastcode" oznacza, że można użyć w języku `from superfastcode import fast_tanh` Python, ponieważ `fast_tanh` jest zdefiniowana w `superfastcode_methods` . (Nazwy plików wewnętrznych dla projektu C++, takie jak *module. cpp*, są nieodpowiednie).

    ```cpp
    static PyModuleDef superfastcode_module = {
        PyModuleDef_HEAD_INIT,
        "superfastcode",                        // Module name to use with Python import statements
        "Provides some functions, but faster",  // Module description
        0,
        superfastcode_methods                   // Structure that defines the methods of the module
    };
    ```

1. Dodaj metodę, która jest wywoływana przez środowisko Python podczas ładowania modułu, który musi mieć nazwę `PyInit_<module-name>` , gdzie &lt; module-name &gt; dokładnie pasuje do **ogólnej**  >  właściwości**nazwy docelowej** projektu C++ (oznacza to, że jest zgodna z nazwą pliku *. PYD* skompilowaną przez projekt).

    ```cpp
    PyMODINIT_FUNC PyInit_superfastcode() {
        return PyModule_Create(&superfastcode_module);
    }
    ```

1. Ustaw konfigurację docelową, aby **zwolnić** i skompilować projekt C++ ponownie w celu zweryfikowania kodu. W przypadku wystąpienia błędów zapoznaj się z sekcją [Rozwiązywanie problemów](#troubleshooting) poniżej.

### <a name="pybind11"></a>PyBind11

Jeśli wykonano kroki opisane w poprzedniej sekcji, zauważysz, że użyto wielu standardowych kodu do utworzenia niezbędnych struktur modułu dla kodu C++. PyBind11 upraszcza proces przez makra w pliku nagłówkowym języka C++, który osiąga ten sam wynik z znacznie mniejszym kodem. Aby uzyskać informacje na temat informacji przedstawionych w tej sekcji, zobacz [PyBind11 Basics](https://github.com/pybind/pybind11/blob/master/docs/basics.rst) (GitHub.com).

1. Zainstaluj PyBind11 przy użyciu narzędzia PIP: `pip install pybind11` lub `py -m pip install pybind11` .

1. W górnej części *modułu. cpp*Uwzględnij *pybind11. h*:

    ```cpp
    #include <pybind11/pybind11.h>
    ```

1. W dolnej części *modułu. cpp*Użyj `PYBIND11_MODULE` makra, aby zdefiniować punkt wejścia do funkcji języka C++:

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

1. Ustaw konfigurację docelową na **Zwolnij** i skompiluj projekt C++, aby zweryfikować swój kod. Jeśli wystąpią błędy, zobacz następną sekcję dotyczącą rozwiązywania problemów.

### <a name="troubleshooting"></a>Rozwiązywanie problemów

Kompilowanie modułu C++ może zakończyć się niepowodzeniem z następujących powodów:

- Nie można zlokalizować języka *Python. h* (**E1696: nie można otworzyć pliku źródłowego "Python. h"** i/lub **C1083: nie można otworzyć pliku dołączanego: "Python. h": brakujący plik lub katalog**): Sprawdź, czy ścieżka w ogólnych **C/C++**  >  **General**  >  **Dodatkowe katalogi dołączane** do folderu *dołączenia* do instalacji języka Python. Zobacz Krok 6 w obszarze [Tworzenie podstawowego projektu C++](#create-the-core-c-projects).

- Nie można zlokalizować bibliotek języka Python: Upewnij się, że ścieżka w polu **konsolidator**  >  **Ogólne**  >  **Dodatkowe katalogi biblioteki** we właściwościach projektu wskazuje folder *libs* instalacji języka Python. Zobacz Krok 6 w obszarze [Tworzenie podstawowego projektu C++](#create-the-core-c-projects).

- Błędy konsolidatora związane z architekturą docelową: Zmień architekturę projektu docelowego języka C++ na zgodną z instalacją w języku Python. Na przykład jeśli jest przeznaczony dla architektury x64 za pomocą projektu C++, ale instalacja języka Python to x86, Zmień projekt C++ na docelowy x86.

## <a name="test-the-code-and-compare-the-results"></a>Przetestuj kod i Porównaj wyniki

Teraz, gdy masz biblioteki DLL uporządkowane jako rozszerzenia języka Python, możesz odwoływać się do nich z projektu języka Python, importować moduły i korzystać z ich metod.

### <a name="make-the-dll-available-to-python"></a>Udostępnienie biblioteki DLL w języku Python

Istnieją dwa sposoby udostępnienia biblioteki DLL w języku Python.

Pierwsza metoda działa, jeśli projekt Python i projekt C++ znajdują się w tym samym rozwiązaniu. Przejdź do **Eksplorator rozwiązań**, kliknij prawym przyciskiem myszy węzeł **odwołania** w projekcie języka Python, a następnie wybierz polecenie **Dodaj odwołanie**. W wyświetlonym oknie dialogowym Wybierz kartę **projekty** , zaznacz zarówno projekty **superfastcode** , jak i **superfastcode2** , a następnie wybierz przycisk **OK**.

![Dodawanie odwołania do projektu superfastcode](media/cpp-add-reference.png)

Alternatywna metoda opisana w poniższych krokach powoduje zainstalowanie modułu w globalnym środowisku języka Python i udostępnienie go również innym projektom języka Python. (Zwykle wymaga to odświeżenia bazy danych uzupełniania IntelliSense dla tego środowiska w programie Visual Studio 2017 w wersji 15,5 lub starszej). W przypadku usuwania modułu ze środowiska należy również odświeżyć.

1. Jeśli używasz programu Visual Studio 2017 lub nowszego, uruchom Instalatora programu Visual Studio, wybierz opcję **Modyfikuj**, wybierz **poszczególne składniki**  >  **kompilatorów, narzędzia kompilacji i środowiska uruchomieniowe**  >  **Visual C++ 2015,3 zestaw narzędzi wersji 140**. Ten krok jest niezbędny, ponieważ środowisko Python (dla systemu Windows) jest wbudowane z programem Visual Studio 2015 (wersja 14,0) i oczekuje, że te narzędzia są dostępne podczas kompilowania rozszerzenia za pomocą metody opisanej w tym miejscu. (Należy pamiętać, że może być konieczne zainstalowanie 32-bitowej wersji języka Python i docelowa Biblioteka DLL do Win32, a nie x64).

1. Utwórz plik o nazwie *Setup.py* w projekcie C++, klikając prawym przyciskiem myszy projekt i wybierając polecenie **Dodaj**  >  **nowy element**. Następnie wybierz **plik C++ (. cpp)**, Nazwij plik `setup.py` i wybierz **przycisk OK** (Nadawanie nazwy plikowi z rozszerzeniem *. PR* sprawia, że program Visual Studio rozpoznaje go jako Python pomimo użycia szablonu pliku C++). Gdy plik pojawi się w edytorze, wklej do niego następujący kod zgodnie z opisem metody rozszerzenia:

    **Rozszerzenia CPython (projekt superfastcode):**

    ```python
    from distutils.core import setup, Extension, DEBUG

    sfc_module = Extension('superfastcode', sources = ['module.cpp'])

    setup(name = 'superfastcode', version = '1.0',
        description = 'Python Package with superfastcode C++ extension',
        ext_modules = [sfc_module]
        )
    ```

    Zobacz [Tworzenie rozszerzeń C i C++](https://docs.python.org/3/extending/building.html) (Python.org) w celu uzyskania dokumentacji dotyczącej tego skryptu.

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

1. Kod *Setup.py* instruuje Python, aby kompilować rozszerzenie przy użyciu zestawu narzędzi Visual Studio 2015 C++, gdy jest używany z wiersza polecenia. Otwórz wiersz polecenia z podwyższonym poziomem uprawnień, przejdź do folderu zawierającego projekt C++ (czyli folder zawierający *Setup.py*), a następnie wprowadź następujące polecenie:

    ```command
    pip install .
    ```

    lub:

    ```command
    py -m pip install .
    ```

### <a name="call-the-dll-from-python"></a>Wywoływanie biblioteki DLL z języka Python

Po udostępnieniu biblioteki DLL w języku Python zgodnie z opisem w poprzedniej sekcji można teraz wywołać `superfastcode.fast_tanh` `superfastcode2.fast_tanh2` funkcje i z kodu Python i porównać ich wydajność z implementacją języka Python:

1. Dodaj następujące wiersze w pliku *. PR* , aby wywoływać metody wyeksportowane z bibliotek DLL i wyświetlić ich dane wyjściowe:

    ```python
    from superfastcode import fast_tanh
    test(lambda d: [fast_tanh(x) for x in d], '[fast_tanh(x) for x in d] (CPython C++ extension)')

    from superfastcode2 import fast_tanh2
    test(lambda d: [fast_tanh2(x) for x in d], '[fast_tanh2(x) for x in d] (PyBind11 C++ extension)')
    ```

1. Uruchom program Python (Rozpocznij**debugowanie**  >  **bez debugowania** lub **Ctrl** + **F5**) i obserwuj, że procedury języka C++ są uruchamiane około 5 – dwadzieścia razy szybciej niż implementacja środowiska Python. Typowe dane wyjściowe są wyświetlane w następujący sposób:

    ```output
    Running benchmarks with COUNT = 500000
    [tanh(x) for x in d] (Python implementation) took 0.758 seconds

    [fast_tanh(x) for x in d] (CPython C++ extension) took 0.076 seconds

    [fast_tanh2(x) for x in d] (PyBind11 C++ extension) took 0.204 seconds
    ```

    Jeśli polecenie **Uruchom bez debugowania** jest wyłączone, kliknij prawym przyciskiem myszy projekt Python w **Eksplorator rozwiązań** i wybierz pozycję **Ustaw jako projekt startowy**.

1. Spróbuj zwiększyć `COUNT` zmienną, aby różnice były bardziej wyraźne. Kompilacja **debugowania** modułu języka C++ jest również uruchamiana wolniej niż kompilacja **wydania** , ponieważ kompilacja **debugowania** jest mniej zoptymalizowana i zawiera różne kontrole błędów. Możesz przełączać się między tymi konfiguracjami do porównania.

> [!NOTE]
> W danych wyjściowych można zobaczyć, że rozszerzenie PyBind11 nie jest tak szybkie jak rozszerzenie CPython, chociaż jest nadal znacznie szybsze niż w przypadku prostej implementacji języka Python. Różnica wynika z niewielkiej liczby obciążeń dla wywołań, które PyBind11 wprowadza, aby znacznie uprościć jego interfejs języka C++. Ta różnica dla wywołań jest rzeczywiście nieistotna: ponieważ kod testowy wywołuje funkcje rozszerzenia 500 000 razy, wyniki widoczne w tym miejscu znacznie wzmocnią ten koszt! Zwykle funkcja C++ wykonuje znacznie więcej pracy niż `fast_tanh[2]` metody proste używane w tym miejscu. w takim przypadku obciążenie jest nieważne. Jednak w przypadku implementowania metod, które mogą być nazywane tysiącami razy na sekundę, użycie metody CPython może skutkować lepszą wydajnością niż PyBind11.

## <a name="debug-the-c-code"></a>Debugowanie kodu C++

Program Visual Studio obsługuje jednocześnie Debugowanie kodu Python i C++. Ta sekcja przeprowadzi Cię przez proces przy użyciu projektu **superfastcode** ; kroki są takie same dla projektu **superfastcode2** .

1. Kliknij prawym przyciskiem myszy projekt Python w **Eksplorator rozwiązań**, wybierz pozycję **Właściwości**, wybierz kartę **debugowanie** , a następnie wybierz opcję **Debuguj**  >  **Włącz debugowanie kodu natywnego** .

    > [!Tip]
    > Po włączeniu debugowania kodu natywnego okno danych wyjściowych w języku Python może zniknąć natychmiast po zakończeniu działania programu bez podawania zwykłych **klawiszy, aby kontynuować** wstrzymywanie. Aby wymusić wstrzymanie, należy dodać `-i` opcję **Run**do  >  pola argumentów uruchamiania**interpretera** na karcie **debugowanie** po włączeniu debugowania kodu natywnego. Ten argument powoduje przełączenie interpretera języka Python w tryb interaktywny po zakończeniu kodu, w którym momencie czeka na naciśnięcie klawisza **Ctrl** + **z**  >  **Enter** , aby wyjść. (Alternatywnie, jeśli nie chcesz modyfikować kodu w języku Python, możesz dodać `import os` `os.system("pause")` instrukcje i na końcu programu. Ten kod duplikuje oryginalny monit wstrzymania.

1. Wybierz pozycję **plik**  >  **Zapisz** , aby zapisać zmiany właściwości.

1. Ustaw konfigurację kompilacji na **Debuguj** na pasku narzędzi programu Visual Studio.

    ![Ustawianie konfiguracji kompilacji do debugowania](media/cpp-set-debug.png)

1. Ponieważ kod zwykle trwa dłużej w debugerze, można zmienić `COUNT` zmienną w pliku *. PR* na wartość, która jest około pięciu razy mniejsza (na przykład zmienić ją z `500000` na `100000` ).

1. W kodzie języka C++ Ustaw punkt przerwania w pierwszym wierszu `tanh_impl` metody, a następnie uruchom debuger (Rozpocznij debugowanie**F5** lub **Debug**  >  **Start Debugging**). Debuger zostaje zatrzymany, gdy ten kod jest wywoływany. Jeśli punkt przerwania nie zostanie trafiony, sprawdź, czy konfiguracja jest ustawiona na **Debuguj** i czy zapisano projekt (który nie jest automatycznie uruchamiany podczas uruchamiania debugera).

    ![Zatrzymywanie w punkcie przerwania w kodzie C++](media/cpp-debugging.png)

1. W tym momencie możesz przejść przez kod języka C++, przeanalizować zmienne i tak dalej. Te funkcje są szczegółowo opisane w temacie [debugowanie C++ i Python](debugging-mixed-mode-c-cpp-python-in-visual-studio.md).

## <a name="alternative-approaches"></a>Alternatywne podejścia

Istnieją różne metody tworzenia rozszerzeń języka Python zgodnie z opisem w poniższej tabeli. Pierwsze dwa wpisy dotyczące CPython i PyBind11 zostały omówione w tym artykule.

| Podejście | Rocznik | Użytkownicy reprezentatywni | Pro (s) | Con |
| --- | --- | --- | --- | --- |
| Moduły rozszerzenia C/C++ dla CPython | 1991 | Standardowa biblioteka | [Obszerna dokumentacja i samouczki](https://docs.python.org/3/c-api/). Całkowita kontrola. | Kompilacja, przenośność, Zarządzanie odwołaniami. Wysoka wiedza C. |
| [PyBind11](https://github.com/pybind/pybind11) (zalecane dla języka C++) | 2015 |  | Uproszczona Biblioteka tylko do nagłówka do tworzenia powiązań języka Python istniejącego kodu C++. Kilka zależności. Zgodność PyPy. | Nowsze, mniej dojrzałe. Duże wykorzystanie funkcji języka C++ 11. Krótka lista obsługiwanych kompilatorów (uwzględniono Visual Studio). |
| Cython (zalecane dla C) | 2007 | [gevent](https://www.gevent.org/), [kivy](https://kivy.org/) | Język Python. Wysoce dojrzały. Wysoka wydajność. | Kompilacja, Nowa składnia, New łańcucha narzędzi. |
| [Zwiększ efektywność. Python](https://www.boost.org/doc/libs/1_66_0/libs/python/doc/html/index.html) | 2002 | | Działa w przypadku wszystkich kompilatorów języka C++. | Duży i złożony zestaw bibliotek; zawiera wiele obejść dla starych kompilatorów. |
| ctypes | 2003 | [oscrypto](https://github.com/wbond/oscrypto) | Brak kompilacji, szerokiej dostępności. | Uzyskiwanie dostępu do i mutacja struktur C nieskomplikowanych i podatnych na błędy. |
| SWIG | 1996 | [crfsuite](http://www.chokkan.org/software/crfsuite/) | Generuj powiązania dla wielu języków jednocześnie. | Nadmierne obciążenie, jeśli język Python jest jedynym elementem docelowym. |
| cffi | 2013 | [Kryptografia](https://cryptography.io/en/latest/), [PyPy](https://pypy.org/) | Łatwość integracji i zgodność PyPy. | Nowsze, mniej dojrzałe. |
| [cppyy](https://cppyy.readthedocs.io/en/latest/) | 2017 | | Podobne do cffi przy użyciu języka C++. | Nowszy może mieć pewne problemy z programem VS 2017. |

## <a name="see-also"></a>Zobacz też

Ukończony przykład z tego przewodnika można znaleźć w języku [Python-Samples-vs-CPP-Extension](https://github.com/Microsoft/python-sample-vs-cpp-extension) (GitHub).

---
title: Pisanie rozszerzeń języka C++ dla języka Python
description: Przewodnik tworzenia rozszerzenia Języka C++ dla języka Python przy użyciu programu Visual Studio, CPython i PyBind11, w tym debugowania w trybie mieszanym.
ms.date: 11/19/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 9c81984e8921e44e32b58ae7f5c5c27c5fe8b12f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62956978"
---
# <a name="create-a-c-extension-for-python"></a>Tworzenie rozszerzenia języka C++ dla języka Python

Moduły napisane w języku C++ (lub C) są powszechnie używane do rozszerzania możliwości interpretera języka Python, a także w celu umożliwienia dostępu do możliwości systemu operacyjnego niskiego poziomu. Istnieją trzy podstawowe typy modułów:

- Moduły akceleratora: ponieważ Python jest językiem interpretowanym, niektóre fragmenty kodu mogą być zapisywane w języku C++ dla wyższej wydajności.
- Moduły otoki: uwidaczniają istniejące interfejsy C/C++ do kodu języka Python lub udostępniają bardziej "Pythonic" API, który jest łatwy w użyciu z Języka Python.
- Moduły dostępu do systemu niskiego poziomu: utworzone w celu uzyskania dostępu do funkcji niższego poziomu środowiska wykonawczego CPython, systemu operacyjnego lub sprzętu źródłowego.

W tym artykule o wiele mówi się o tworzeniu modułu rozszerzenia C++ dla CPython, który oblicza styczne hiperboliczne i wywołuje go z kodu Języka Python. Procedura jest implementowana najpierw w pythonie, aby zademonstrować względny przyrost wydajności implementowania tej samej procedury w języku C++.

W tym artykule przedstawiono również dwa sposoby, aby C++ dostępne dla języka Python:

- Standardowe rozszerzenia CPython opisane w [dokumentacji Języka Python](https://docs.python.org/3/c-api/)
- [PyBind11](https://github.com/pybind/pybind11), który jest zalecany dla C++ 11 ze względu na jego prostotę.

Porównanie tych i innych środków znajduje się w ramach [alternatywnych podejść](#alternative-approaches) na końcu tego artykułu.

Wypełniony przykład z tego przewodnika można znaleźć na [python-samples-vs-cpp-extension](https://github.com/Microsoft/python-sample-vs-cpp-extension) (GitHub).

## <a name="prerequisites"></a>Wymagania wstępne

- Visual Studio 2017 lub nowsze z obu **desktop development z c++** i **Python Deweloper** obciążeń zainstalowanych z opcjami domyślnymi.
- W obciążeniu **rozwoju języka Python** wybierz również pole po prawej stronie dla **natywnych narzędzi programistycznych języka Python**. Ta opcja konfiguruje większość konfiguracji opisanych w tym artykule. (Ta opcja zawiera również obciążenie języka C++)

    ![Wybieranie opcji natywnych narzędzi programistycznych języka Python](media/cpp-install-native.png)

    > [!Tip]
    > Instalowanie danych **nauki i aplikacji analitycznych** obciążenia obejmuje również Python i **Python natywne narzędzia programistyczne** opcja domyślnie.

Aby uzyskać więcej informacji, zobacz [Instalowanie obsługi języka Python dla programu Visual Studio,](installing-python-support-in-visual-studio.md)w tym przy użyciu innych wersji programu Visual Studio. Jeśli python jest instalowany oddzielnie, należy wybrać **opcję Pobierz symbole debugowania** i **Pobierz pliki binarne debugowania** w obszarze **Opcje zaawansowane** w instalatorze. Ta opcja zapewnia, że masz niezbędne biblioteki debugowania dostępne, jeśli zdecydujesz się wykonać kompilację debugowania.

## <a name="create-the-python-application"></a>Tworzenie aplikacji języka Python

1. Utwórz nowy projekt języka Python w programie Visual Studio, wybierając **pozycję Plik** > **nowego** > **projektu**. Wyszukaj "Python", wybierz szablon **aplikacji Python,** nadaj mu odpowiednią nazwę i lokalizację, a następnie wybierz **PRZYCISK OK**.

1. Praca z c++ wymaga użycia 32-bitowego interpretera języka Python (zalecane w języku Python 3.6 lub nowszym). W oknie **Eksploratora rozwiązań** programu Visual Studio rozwiń węzeł projektu, a następnie rozwiń węzeł **Środowiska języka Python.** Jeśli nie widzisz środowiska 32-bitowego jako domyślnego (pogrubionego lub oznaczonego **domyślnie globalnym),** postępuj zgodnie z instrukcjami dotyczącymi [Wybierania środowiska języka Python dla projektu.](selecting-a-python-environment-for-a-project.md) Jeśli nie masz zainstalowanego interpretera 32-bitowego, zobacz [Instalowanie interpreterów języka Python](installing-python-interpreters.md).

1. W pliku *py* projektu wklej następujący kod, który testuje obliczenia stycznej hiperbolicznej (zaimplementowane bez użycia biblioteki matematycznej w celu łatwiejszego porównania). Możesz wprowadzić kod ręcznie, aby doświadczyć niektórych [funkcji edycji Pythona](editing-python-code-in-visual-studio.md).

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

1. Uruchom program przy użyciu **debugowania** > **start bez debugowania** **(Ctrl**+**F5**), aby zobaczyć wyniki. Można dostosować `COUNT` zmienną, aby zmienić czas działania benchmarku. Na potrzeby tego przewodnika należy ustawić liczbę, tak aby wskaźnik porównawczy trwać około dwóch sekund.

> [!TIP]
> Podczas uruchamiania testów porównawczych, zawsze należy użyć **debugowania** > **start bez debugowania,** aby uniknąć narzutów poniesionych podczas uruchamiania kodu w debugerze programu Visual Studio.

## <a name="create-the-core-c-projects"></a>Tworzenie podstawowych projektów języka C++

Postępuj zgodnie z instrukcjami w tej sekcji, aby utworzyć dwa identyczne projekty C++ o nazwie "superfastcode" i "superfastcode2". Później użyjesz różnych środków w każdym projekcie, aby udostępnić kod C++ na język Python.

1. Upewnij się, że zmienna `PYTHONHOME` środowiskowa jest ustawiona na interpreter języka Python, którego chcesz użyć. Projekty języka C++ w programie Visual Studio polegają na tej zmiennej, aby zlokalizować pliki, takie jak *python.h*, które są używane podczas tworzenia rozszerzenia języka Python.

1. Kliknij prawym przyciskiem myszy rozwiązanie w **Eksploratorze rozwiązań** i wybierz pozycję **Dodaj** > **nowy projekt**. Rozwiązanie programu Visual Studio może zawierać projekty języka Python i C++ razem (co jest jedną z zalet korzystania z programu Visual Studio dla języka Python).

1. Wyszukaj w "C++", wybierz **pusty projekt,** określ nazwę "superfastcode" ("superfastcode2" dla drugiego projektu) i wybierz **PRZYCISK OK**.

    > [!Tip]
    > Z **python natywnych narzędzi programistycznych** zainstalowanych w programie Visual Studio, można rozpocząć od **szablonu moduł rozszerzenia Języka Python** zamiast tego, który ma wiele z tego, co jest opisane poniżej już w miejscu. W tym instruktażu, jednak, począwszy od pustego projektu demonstruje tworzenie modułu rozszerzenia krok po kroku. Po zrozumieniu procesu szablon pozwala zaoszczędzić czas podczas pisania własnych rozszerzeń.

1. Utwórz plik C++ w nowym projekcie, klikając prawym przyciskiem myszy węzeł **Pliki źródłowe,** a `module.cpp`następnie wybierz polecenie **Dodaj** > nowy**element,** wybierz pozycję Plik **C++,** nazwij go i wybierz przycisk **OK**.

    > [!Important]
    > Plik z rozszerzeniem *.cpp* jest konieczne, aby włączyć strony właściwości Języka C++ w krokach, które należy wykonać.

1. Kliknij prawym przyciskiem myszy projekt C++ w **Eksploratorze rozwiązań**, wybierz polecenie **Właściwości**.

1. W górnej części wyświetlonego okna dialogowego **Strony właściwości** ustaw **konfigurację** na **Wszystkie konfiguracje** i **platformę** na **Win32**.

1. Ustaw określone właściwości zgodnie z opisem w poniższej tabeli, a następnie wybierz **przycisk OK**.

    | Tab | Właściwość | Wartość |
    | --- | --- | --- |
    | **Ogólne** | **Ogólna** > **nazwa docelowa** | Określ nazwę modułu, jak chcesz odwoływać `from...import` się do niego z Python w instrukcjach. Tej samej nazwy używasz w języku C++ podczas definiowania modułu dla języka Python. Jeśli chcesz użyć nazwy projektu jako nazwy modułu, pozostaw domyślną wartość **$(ProjectName).** |
    | | **Ogólne** > **rozszerzenie celu** | **.pyd (pyd)** |
    | | **Project Defaults** > **Typ konfiguracji** domyślne projektu | **Biblioteka dynamiczna (dll)** |
    | **C/C++** > **Ogólne** | **Dodatkowe katalogi dołączania** | Dodaj folder *do dołączania* języka Python odpowiednio `c:\Python36\include`do instalacji, na przykład .  |
    | **C/C++** > **Preprocesor** C/C++ | **Definicje preprocesora** | **CPython tylko** `Py_LIMITED_API;` : dodać na początku ciągu (w tym średnika). Ta definicja ogranicza niektóre funkcje, które można wywołać z języka Python i sprawia, że kod bardziej przenośny między różnymi wersjami języka Python. Jeśli pracujesz z PyBind11, nie dodawaj tej definicji, w przeciwnym razie zobaczysz błędy kompilacji. |
    | **Generowanie kodu C/C++** > **Code Generation** | **Biblioteka środowiska uruchomieniowego** | **Wielowątkowa biblioteka DLL (/MD)** (patrz ostrzeżenie poniżej) |
    | **Linker** > **Ogólne** | **Dodatkowe katalogi bibliotek** | Dodaj folder Języka Python *libs zawierający* pliki *lib* odpowiednie `c:\Python36\libs`dla twojej instalacji, na przykład . (Pamiętaj, aby wskazać folder *libs zawierający* pliki *lib,* a *nie* folder *Lib* zawierający pliki *py).* |

    > [!Tip]
    > Jeśli nie widzisz c/c++ kartę we właściwościach projektu, to dlatego, że projekt nie zawiera żadnych plików, które identyfikuje jako pliki źródłowe C/C++. Ten warunek może wystąpić, jeśli utworzysz plik źródłowy bez rozszerzenia *.c* lub *.cpp.* Na przykład jeśli przypadkowo `module.coo` wprowadzone zamiast `module.cpp` w oknie dialogowym nowego elementu wcześniej, a następnie Visual Studio tworzy plik, ale nie ustawia typ pliku na "Kod C/C+", który jest, co aktywuje c/c++ karty właściwości. Taka błędna identyfikacja pozostaje w przypadku, nawet `.cpp`jeśli zmienisz nazwę pliku z . Aby poprawnie ustawić typ pliku, kliknij prawym przyciskiem myszy plik w **Eksploratorze rozwiązań**, wybierz **polecenie Właściwości**, a następnie ustaw kod **Typu pliku** na **Kod C/C++.**

    > [!Warning]
    > Zawsze ustawiaj opcję**Biblioteka wykonawcza** **generowania** > kodu **C/C++** > na **wielowątkową bibliotekę DLL (/MD),** nawet dla konfiguracji debugowania, ponieważ to ustawienie jest tym, z czym są zbudowane pliki binarne języka Python bez debugowania. W przypadku CPython, jeśli zdarzy ci się ustawić opcję **wielowątkowej biblioteki DLL debugowania (/MDd),** tworzenie konfiguracji **debugowania** powoduje błąd **C1189: Py_LIMITED_API jest niezgodne z Py_DEBUG, Py_TRACE_REFS i Py_REF_DEBUG**. Ponadto w przypadku `Py_LIMITED_API` usunięcia (co jest wymagane z CPython, ale nie PyBind11), aby uniknąć błędu kompilacji, Python ulega awarii podczas próby zaimportowania modułu. (Awaria dzieje się w wywołaniu `PyModule_Create` biblioteki DLL, jak opisano później, z komunikatem wyjściowym **fatal python błąd: PyThreadState_Get: brak bieżącego wątku**.)
    >
    > Opcja /MDd służy do tworzenia plików binarnych debugowania języka Python (takich jak *python_d.exe),* ale wybranie `Py_LIMITED_API`jej dla biblioteki DLL rozszerzenia nadal powoduje błąd kompilacji za pomocą .

1. Kliknij prawym przyciskiem myszy projekt C++ i wybierz polecenie **Kompilacja,** aby przetestować konfiguracje (zarówno **debugowanie,** jak i **wydanie).** Pliki *pyd* znajdują się w folderze **rozwiązania** w obszarze **Debugowanie** i **zwalnianie**, a nie w samym folderze projektu C++.

1. Dodaj następujący kod do pliku *module.cpp* projektu C++:

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

1. Skompiluj projekt C++ ponownie, aby potwierdzić, że kod jest poprawny.

1. Jeśli jeszcze tego nie zrobiono, powtórz powyższe kroki, aby utworzyć drugi projekt o nazwie "superfastcode2" o identycznej zawartości.

## <a name="convert-the-c-projects-to-extensions-for-python"></a>Konwertowanie projektów języka C++ na rozszerzenia dla języka Python

Aby wprowadzić bibliotekę DLL języka C++ w rozszerzenie dla języka Python, należy najpierw zmodyfikować eksportowane metody do interakcji z typami języka Python. Następnie należy dodać funkcję, która eksportuje moduł, wraz z definicjami metod modułu.

Sekcje, które należy wykonać wyjaśnić, jak wykonać te kroki przy użyciu rozszerzeń CPython i PyBind11.

### <a name="cpython-extensions"></a>Rozszerzenia CPython

W tle, co jest pokazane w tej sekcji dla języka Python 3.x, zapoznaj się z [Podręcznikiem odwołania do interfejsu API języka Python/C,](https://docs.python.org/3/c-api/index.html) a zwłaszcza [obiektami modułu](https://docs.python.org/3/c-api/module.html) na python.org (pamiętaj, aby wybrać wersję języka Python z rozwijanej kontrolki w prawym górnym rogu, aby wyświetlić poprawną dokumentację).

Jeśli pracujesz z Python 2.7, zamiast tego odnoszą się do [rozszerzania Python 2.7 z C lub C++](https://docs.python.org/2.7/extending/extending.html) i [przenoszenia modułów rozszerzeń do Pythona 3](https://docs.python.org/2.7/howto/cporting.html) (python.org).

1. W górnej części *module.cpp*, obejmują *Python.h*:

    ```cpp
    #include <Python.h>
    ```

1. Zmodyfikuj `tanh_impl` metodę akceptowania `PyOjbect*`i zwracania typów Języka Python (a , czyli):

    ```cpp
    PyObject* tanh_impl(PyObject *, PyObject* o) {
        double x = PyFloat_AsDouble(o);
        double tanh_x = sinh_impl(x) / cosh_impl(x);
        return PyFloat_FromDouble(tanh_x);
    }
    ```

1. Dodaj strukturę, która definiuje sposób `tanh_impl` prezentowania funkcji C++ w języku Python:

    ```cpp
    static PyMethodDef superfastcode_methods[] = {
        // The first property is the name exposed to Python, fast_tanh, the second is the C++
        // function name that contains the implementation.
        { "fast_tanh", (PyCFunction)tanh_impl, METH_O, nullptr },

        // Terminate the array with an object containing nulls.
        { nullptr, nullptr, 0, nullptr }
    };
    ```

1. Dodaj strukturę, która definiuje moduł, jak chcesz odwoływać się do niego `from...import` w kodzie języka Python, w szczególności podczas korzystania z instrukcji. (Upewnij się, że jest to zgodne z wartością we właściwościach projektu w obszarze Nazwa ogólnego obiektu > **docelowego** > **Target Name** **właściwości konfiguracji).** W poniższym przykładzie nazwa modułu "superfastcode" oznacza, że można używać `from superfastcode import fast_tanh` w Pythonie, ponieważ `fast_tanh` jest zdefiniowany w ramach `superfastcode_methods`. (Nazwy plików wewnętrzne projektu C++, takie jak *module.cpp,* są nieistotne).

    ```cpp
    static PyModuleDef superfastcode_module = {
        PyModuleDef_HEAD_INIT,
        "superfastcode",                        // Module name to use with Python import statements
        "Provides some functions, but faster",  // Module description
        0,
        superfastcode_methods                   // Structure that defines the methods of the module
    };
    ```

1. Dodaj metodę, która wywołuje języka Python podczas ładowania `PyInit_<module-name>`modułu, który musi &lt;być nazwany , gdzie nazwa&gt; modułu dokładnie odpowiada właściwości **Ogólna** > nazwa**docelowa** projektu C++ (oznacza to, że jest zgodna z nazwą pliku *.pyd* zbudowany przez projekt).

    ```cpp
    PyMODINIT_FUNC PyInit_superfastcode() {
        return PyModule_Create(&superfastcode_module);
    }
    ```

1. Ustaw konfigurację docelową na **Zwolnij** i ponownie skompiluj projekt C++, aby zweryfikować kod. Jeśli wystąpią błędy, zobacz sekcję [Rozwiązywanie problemów](#troubleshooting) poniżej.

### <a name="pybind11"></a>PyBind11

Po wykonaniu kroków w poprzedniej sekcji, z pewnością zauważyłeś, że użyto wiele kodu standardowego do utworzenia niezbędnych struktur modułu dla kodu C++. PyBind11 upraszcza proces za pośrednictwem makr w pliku nagłówka Języka C++, które osiągają ten sam wynik przy znacznie mniejszym kodzie. Aby uzyskać informacje na temat tego, co jest wyświetlane w tej sekcji, zobacz [Podstawy PyBind11](https://github.com/pybind/pybind11/blob/master/docs/basics.rst) (github.com).

1. Zainstaluj PyBind11 za `pip install pybind11` `py -m pip install pybind11`pomocą pip: lub .

1. W górnej części *module.cpp*, obejmują *pybind11.h*:

    ```cpp
    #include <pybind11/pybind11.h>
    ```

1. W dolnej części *module.cpp*użyj `PYBIND11_MODULE` makra, aby zdefiniować punkt wejścia do funkcji C++:

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

1. Ustaw konfigurację docelową na **Zwolnij** i skompiluj projekt C++, aby zweryfikować kod. Jeśli wystąpią błędy, zobacz następną sekcję dotyczącą rozwiązywania problemów.

### <a name="troubleshooting"></a>Rozwiązywanie problemów

Moduł C++ może nie zostać skompilowany z następujących powodów:

- Nie można zlokalizować *Python.h* (**E1696: nie można otworzyć pliku źródłowego "Python.h"** i/lub **C1083: Nie można otworzyć pliku include: "Python.h": Brak takiego pliku lub katalogu**): sprawdź, czy ścieżka w **C/C++** > **Ogólne** > **dodatkowe katalogi w** właściwościach projektu wskazuje na folder *dołączany* instalacji Języka Python. Zobacz krok 6 w obszarze [Tworzenie podstawowego projektu C++](#create-the-core-c-projects).

- Nie można zlokalizować bibliotek języka Python: sprawdź, czy ścieżka w dodatkowych**General** > **katalogach biblioteki** **linkera** > w właściwościach projektu wskazuje folder *libs* instalacji języka Python. Zobacz krok 6 w obszarze [Tworzenie podstawowego projektu C++](#create-the-core-c-projects).

- Błędy konsolidatora związane z architekturą docelową: zmień architekturę projektu obiektu docelowego języka C++, aby dopasować się do architektury instalacji języka Python. Na przykład jeśli kierujesz x64 z projektu C++, ale instalacja języka Python jest x86, zmień projekt C++ na docelowy x86.

## <a name="test-the-code-and-compare-the-results"></a>Przetestuj kod i porównaj wyniki

Teraz, gdy masz biblioteki DLL skonstruowane jako rozszerzenia Języka Python, możesz odwoływać się do nich z projektu Pythona, importować moduły i używać ich metod.

### <a name="make-the-dll-available-to-python"></a>Udostępnianie biblioteki DLL w języku Python

Istnieją dwa sposoby udostępniania biblioteki DLL w języku Python.

Pierwsza metoda działa, jeśli projekt języka Python i projekt C++ znajdują się w tym samym rozwiązaniu. Przejdź do **Programu Solution Explorer**, kliknij prawym przyciskiem myszy węzeł **Odwołania** w projekcie języka Python, a następnie wybierz pozycję **Dodaj odwołanie**. W wyświetlonym oknie dialogowym wybierz kartę **Projekty,** wybierz zarówno projekty **superszybkiego, jak** i **superszybkiego 2,** a następnie wybierz przycisk **OK**.

![Dodawanie odwołania do projektu superszybkiego kodu](media/cpp-add-reference.png)

Alternatywna metoda, opisana w poniższych krokach, instaluje moduł w globalnym środowisku Pythona, udostępniając go również innym projektom języka Python. (W ten sposób zazwyczaj wymaga odświeżenia bazy danych ukończenia IntelliSense dla tego środowiska w programie Visual Studio 2017 w wersji 15.5 i wcześniejszych. Odświeżenie jest również konieczne podczas usuwania modułu ze środowiska.)

1. Jeśli używasz programu Visual Studio 2017 lub nowszego, uruchom instalator programu Visual Studio, wybierz pozycję **Modyfikuj,** wybierz pozycję **Kompilatory poszczególnych składników,** > **narzędzia kompilacji i środowiska wykonawcze** > **Visual C++ 2015.3 v140.** Ten krok jest konieczne, ponieważ Python (dla systemu Windows) jest sam zbudowany z programu Visual Studio 2015 (wersja 14.0) i oczekuje, że te narzędzia są dostępne podczas tworzenia rozszerzenia za pomocą metody opisanej tutaj. (Należy zauważyć, że może być konieczne zainstalowanie 32-bitowej wersji języka Python i kierowanie biblioteki DLL na win32, a nie x64).

1. Utwórz plik o nazwie *setup.py* w projekcie C++, klikając prawym przyciskiem myszy projekt i wybierając pozycję **Dodaj** > **nowy element**. Następnie wybierz **opcję Plik C++ (.cpp)**, nazwij plik `setup.py`i wybierz PRZYCISK **OK** (nazwanie pliku rozszerzeniem *.py* sprawia, że program Visual Studio rozpoznaje go jako Python pomimo użycia szablonu pliku C++). Gdy plik pojawi się w edytorze, wklej do niego następujący kod, stosownie do metody rozszerzenia:

    **Rozszerzenia CPython (projekt superszybkiego kodu):**

    ```python
    from distutils.core import setup, Extension, DEBUG

    sfc_module = Extension('superfastcode', sources = ['module.cpp'])

    setup(name = 'superfastcode', version = '1.0',
        description = 'Python Package with superfastcode C++ extension',
        ext_modules = [sfc_module]
        )
    ```

    Zobacz [tworzenie rozszerzeń C i C++](https://docs.python.org/3/extending/building.html) (python.org) dla dokumentacji tego skryptu.

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

1. Kod *setup.py* nakazuje Pythonowi tworzenie rozszerzenia przy użyciu zestawu narzędzi Visual Studio 2015 C++, gdy jest używany z wiersza polecenia. Otwórz wiersz polecenia z podwyższonem poziomem uprawnień, przejdź do folderu zawierającego projekt C++ (czyli folder zawierający *setup.py)* i wprowadź następujące polecenie:

    ```command
    pip install .
    ```

    lub:

    ```command
    py -m pip install .
    ```

### <a name="call-the-dll-from-python"></a>Wywoływanie biblioteki DLL z języka Python

Po udostępnienie biblioteki DLL w języku Python, zgodnie z opisem `superfastcode.fast_tanh` `superfastcode2.fast_tanh2` w poprzedniej sekcji, można teraz wywołać i funkcje z kodu Języka Python i porównać ich wydajność z implementacją języka Python:

1. Dodaj następujące wiersze w pliku *py,* aby wywołać metody eksportowane z bibliotek DLL i wyświetlić ich dane wyjściowe:

    ```python
    from superfastcode import fast_tanh
    test(lambda d: [fast_tanh(x) for x in d], '[fast_tanh(x) for x in d] (CPython C++ extension)')

    from superfastcode2 import fast_tanh2
    test(lambda d: [fast_tanh2(x) for x in d], '[fast_tanh2(x) for x in d] (PyBind11 C++ extension)')
    ```

1. Uruchom program Python **(Debug** > **Start bez debugowania** lub **Ctrl**+**F5**) i obserwować, że procedury C++ działają około pięć do dwudziestu razy szybciej niż implementacja języka Python. Typowe dane wyjściowe są następujące:

    ```output
    Running benchmarks with COUNT = 500000
    [tanh(x) for x in d] (Python implementation) took 0.758 seconds

    [fast_tanh(x) for x in d] (CPython C++ extension) took 0.076 seconds

    [fast_tanh2(x) for x in d] (PyBind11 C++ extension) took 0.204 seconds
    ```

    Jeśli polecenie **Rozpocznij bez debugowania** jest wyłączone, kliknij prawym przyciskiem myszy projekt języka Python w **Eksploratorze rozwiązań** i wybierz polecenie **Ustaw jako projekt startowy**.

1. Spróbuj zwiększyć `COUNT` zmienną, tak aby różnice były bardziej wyraźne. Kompilacja **debugowania** modułu C++ działa również wolniej niż **kompilacja release,** ponieważ kompilacja **debugowania** jest mniej zoptymalizowana i zawiera różne testy błędów. Zapraszam do przełączania się między tymi konfiguracjami dla porównania.

> [!NOTE]
> W danych wyjściowych widać, że rozszerzenie PyBind11 nie jest tak szybkie jak rozszerzenie CPython, chociaż nadal jest znacznie szybsze niż prosta implementacja języka Python. Różnica wynika z niewielkiej ilości narzutów na wywołanie, które wprowadza PyBind11, aby jego interfejs C++ znacznie prostszy. Ta różnica na wywołanie jest rzeczywiście dość nieistotne: ponieważ kod testowy wywołuje funkcje rozszerzenia 500.000 razy, wyniki widać tutaj znacznie wzmocnić, że obciążenie! Zazwyczaj funkcja C++ wykonuje znacznie więcej pracy `fast_tanh[2]` niż metody trywialne używane w tym miejscu, w którym to przypadku obciążenie jest nieistotne. Jednak jeśli implementujesz metody, które mogą być wywoływane tysiące razy na sekundę, przy użyciu CPython podejście może spowodować lepszą wydajność niż PyBind11.

## <a name="debug-the-c-code"></a>Debugowanie kodu języka C++

Visual Studio obsługuje debugowanie kodu Python i C++ razem. W tej sekcji przechodzi przez proces przy użyciu projektu **superszybkiego;** kroki są takie same dla projektu **superfastcode2.**

1. Kliknij prawym przyciskiem myszy projekt języka Python w **Eksploratorze rozwiązań**, wybierz **polecenie Właściwości**, wybierz kartę **Debugowanie,** a następnie wybierz opcję **Debuguj włącz debugowanie** > **kodu natywnego.**

    > [!Tip]
    > Po włączeniu debugowania kodu macierzystego okno danych wyjściowych języka Python może zniknąć natychmiast po zakończeniu programu bez podawania zwykłego **naciśnięcia dowolnego klawisza, aby kontynuować** pauzę. Aby wymusić wstrzymanie, dodaj `-i` tę opcję do pola **Uruchom** > argumenty**interpretera** na karcie **Debugowanie** po włączeniu debugowania kodu macierzystego. Ten argument przełącza interpretera Języka Python w tryb interaktywny po zakończeniu kodu, w którym to momencie czeka na naciśnięcie **klawisza Ctrl**+**Z** > **Enter,** aby zakończyć. (Alternatywnie, jeśli nie masz nic przeciwko modyfikowaniu `import os` kodu `os.system("pause")` Języka Python, możesz dodać i instrukcje na końcu programu. Ten kod powiela oryginalny monit o wstrzymanie).)

1. Wybierz **pozycję Zapisz plik,** > **Save** aby zapisać zmiany właściwości.

1. Ustaw konfigurację kompilacji na **Debugowanie** na pasku narzędzi programu Visual Studio.

    ![Ustawianie konfiguracji kompilacji na Debugowanie](media/cpp-set-debug.png)

1. Ponieważ uruchamianie kodu w debugerze trwa zwykle dłużej, można `COUNT` zmienić zmienną w pliku *py* na wartość około pięciokrotnie mniejszą (na przykład zmienić ją z `500000` na `100000`).

1. W kodzie C++ ustaw punkt przerwania w `tanh_impl` pierwszym wierszu metody, a następnie uruchom debuger (**F5** lub **Debug** > **start debugowania**). Debuger zatrzymuje się, gdy ten kod jest wywoływany. Jeśli punkt przerwania nie zostanie trafiony, sprawdź, czy konfiguracja jest ustawiona na **Debugowanie** i czy projekt został zapisany (co nie odbywa się automatycznie podczas uruchamiania debugera).

    ![Zatrzymywanie się w punkcie przerwania w kodzie języka C++](media/cpp-debugging.png)

1. W tym momencie można przejść przez kod C++, zbadać zmienne i tak dalej. Te funkcje są szczegółowo opisane w [debugowania C++ i Python razem](debugging-mixed-mode-c-cpp-python-in-visual-studio.md).

## <a name="alternative-approaches"></a>Alternatywne podejścia

Istnieje wiele sposobów tworzenia rozszerzeń języka Python, zgodnie z opisem w poniższej tabeli. Pierwsze dwa wpisy dla CPython i PyBind11 są to, co zostało omówione w tym artykule już.

| Podejście | Vintage | Reprezentatywny użytkownik(-i) | Profesjonaliści | Kon(y) |
| --- | --- | --- | --- | --- |
| Moduły rozszerzeń C/C++ dla CPython | 1991 | Standardowa biblioteka | [Obszerna dokumentacja i tutoriale](https://docs.python.org/3/c-api/). Całkowita kontrola. | Kompilacja, przenośność, zarządzanie odniesieniami. Wysoka wiedza C. |
| [PyBind11](https://github.com/pybind/pybind11) (zalecane dla języka C++) | 2015 |  | Uproszczona biblioteka tylko do nagłówka do tworzenia powiązań języka Python istniejącego kodu C++. Kilka zależności. Zgodność pyPy. | Nowsze, mniej dojrzałe. Intensywne korzystanie z funkcji C++11. Krótka lista obsługiwanych kompilatorów (w zestawie jest program Visual Studio). |
| Cython (zalecany do C) | 2007 | [gevent](https://www.gevent.org/), [kivy](https://kivy.org/) | Python-like. Bardzo dojrzały. Wysoka wydajność. | Kompilacja, nowa składnia, nowy pasek narzędzi. |
| [Boost.Python](https://www.boost.org/doc/libs/1_66_0/libs/python/doc/html/index.html) | 2002 | | Współpracuje z prawie każdym kompilatorem języka C++. | Duży i złożony pakiet bibliotek; zawiera wiele obejść starych kompilatorów. |
| ctypes | 2003 | [oscrypto](https://github.com/wbond/oscrypto) | Brak kompilacji, szeroka dostępność. | Dostęp i mutowanie struktur C uciążliwe i podatne na błędy. |
| Swig | 1996 | [crfsuite ( crfsuite )](http://www.chokkan.org/software/crfsuite/) | Generowanie powiązań dla wielu języków jednocześnie. | Nadmierne obciążenie, jeśli Python jest jedynym celem. |
| cffi ( cffi ) | 2013 | [kryptografia](https://cryptography.io/en/latest/), [pypy](https://pypy.org/) | Łatwość integracji, kompatybilność PyPy. | Nowsze, mniej dojrzałe. |
| [cppyy ( cppyy )](https://cppyy.readthedocs.io/en/latest/) | 2017 | | Podobne do cffi przy użyciu języka C++. | Nowsze, może mieć pewne problemy z VS 2017. |

## <a name="see-also"></a>Zobacz też

Wypełniony przykład z tego przewodnika można znaleźć na [python-samples-vs-cpp-extension](https://github.com/Microsoft/python-sample-vs-cpp-extension) (GitHub).

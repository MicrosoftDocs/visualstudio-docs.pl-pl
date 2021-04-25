---
title: Pisanie rozszerzeń języka C++ dla języka Python
description: Przewodnik tworzenia rozszerzenia języka C++ dla języka Python przy użyciu języków Visual Studio, CPython i PyBind11, w tym debugowania w trybie mieszanym.
ms.date: 11/19/2018
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: df3d32bfedfc730b8fae0837ce0e48f50e6496f4
ms.sourcegitcommit: 925db7adb9cb554b081c7e727d09680d4863feed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2021
ms.locfileid: "107941152"
---
# <a name="create-a-c-extension-for-python"></a>Tworzenie rozszerzenia C++ dla języka Python

Moduły napisane w języku C++ (lub C) są często używane do rozszerzania możliwości interpretera języka Python, a także do włączania dostępu do funkcji systemu operacyjnego niskiego poziomu. Istnieją trzy podstawowe typy modułów:

- Moduły akceleratora: ponieważ Python to język interpretowany, niektóre fragmenty kodu można zapisywać w języku C++, aby uzyskać wyższą wydajność.
- Moduły otoki: uwidocznij istniejące interfejsy C/C++ dla kodu w języku Python lub uwidocznij bardziej "pythonowy" interfejs API, który jest łatwy w użyciu z języka Python.
- Moduły dostępu do systemu niskiego poziomu: utworzone w celu uzyskania dostępu do funkcji niższego poziomu środowiska uruchomieniowego CPython, systemu operacyjnego lub podstawowego sprzętu.

W tym artykule o mowa o budowania modułu rozszerzenia języka C++ dla języka CPython, który oblicza tangens hiperboliczny i wywołuje go z kodu w języku Python. Procedura jest implementowane najpierw w języku Python w celu zademonstrowania względnego przyrostu wydajności implementacji tej samej procedury w języku C++.

W tym artykule pokazano również dwa sposoby, aby udostępnić język C++ językowi Python:

- Standardowe rozszerzenia CPython, zgodnie z opisem w dokumentacji [języka Python](https://docs.python.org/3/c-api/)
- [PyBind11,](https://github.com/pybind/pybind11)który jest zalecany dla języka C++ 11 ze względu na jego prostotę.

Porównanie tych i innych metod znajduje się w [alternatywnych](#alternative-approaches) podejściach na końcu tego artykułu.

Ukończony przykład z tego przewodnika można znaleźć w witrynie [python-samples-vs-cpp-extension](https://github.com/Microsoft/python-sample-vs-cpp-extension) (GitHub).

## <a name="prerequisites"></a>Wymagania wstępne

- Visual Studio wersji 2017 lub nowszej z zainstalowanymi domyślnymi opcjami obciążeń Programowanie aplikacji klasycznych w języku **C++** i **Python.**
- W **obciążeniu Programowanie w języku Python** zaznacz również pole wyboru po prawej stronie dla natywnych narzędzi **deweloperskie języka Python.** Ta opcja konfiguruje większość konfiguracji opisanej w tym artykule. (Ta opcja automatycznie uwzględnia również obciążenie języka C++).

    ![Wybieranie opcji Natywne narzędzia programskie języka Python](media/cpp-install-native.png)

    > [!Tip]
    > Instalowanie obciążenia **Aplikacje do analizy i przetwarzania** danych domyślnie obejmuje również język Python i natywne narzędzia programistyczne języka **Python.**

Aby uzyskać więcej informacji, zobacz Install Python support for Visual Studio , including using other versions of Visual Studio (Instalowanie obsługi języka Python dla środowiska [Visual Studio,](installing-python-support-in-visual-studio.md)w tym korzystanie z innych wersji Visual Studio. Jeśli język Python jest instalowany  oddzielnie, pamiętaj o wybraniu opcji Pobierz symbole debugowania i Pobierz **pliki binarne** debugowania w obszarze **Opcje** zaawansowane w instalatorze. Ta opcja zapewnia, że dostępne są niezbędne biblioteki debugowania, jeśli zdecydujesz się na kompilację debugowania.

## <a name="create-the-python-application"></a>Tworzenie aplikacji w języku Python

1. Utwórz nowy projekt języka Python w programie Visual Studio wybierając **pozycję File** New Project  >  **(Plik nowy**  >  **projekt).** Wyszukaj pozycję "Python", wybierz szablon **Aplikacja języka Python,** nadaj mu odpowiednią nazwę i lokalizację, a następnie wybierz przycisk **OK.**

1. Praca z językiem C++ wymaga użycia 32-bitowego interpretera języka Python (zalecany jest język Python 3.6 lub jego wersja 3.6). W **Eksplorator rozwiązań** okna Visual Studio rozwiń węzeł projektu, a następnie rozwiń węzeł **Środowiska języka Python.** Jeśli nie widzisz środowiska 32-bitowego jako środowiska domyślnego (pogrubioną lub oznaczoną globalną wartością **domyślną),** postępuj zgodnie z instrukcjami na stronie Select a Python environment for a project (Wybieranie środowiska języka Python dla [projektu).](selecting-a-python-environment-for-a-project.md) Jeśli nie masz zainstalowanego interpretera 32-bitowego, zobacz [Instalowanie interpreterów języka Python.](installing-python-interpreters.md)

1. W pliku *PY* projektu wklej następujący kod, który testuje obliczenia tangensa hiperbolicznego (zaimplementowane bez użycia biblioteki matematycznej w celu łatwiejszego porównania). Możesz wprowadzić kod ręcznie, aby korzystać z niektórych funkcji edycji [języka Python.](editing-python-code-in-visual-studio.md)

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

1. Uruchom program przy użyciu polecenia **Rozpocznij**  >  **debugowanie bez debugowania** **(Ctrl** + **F5),** aby wyświetlić wyniki. Zmienną można `COUNT` dostosować, aby zmienić czas uruchamiania testu porównawczego. Na potrzeby tego przewodnika ustaw liczbę, aby test porównawczy potrwał około dwóch sekund.

> [!TIP]
> Podczas uruchamiania testów porównawczych należy zawsze używać uruchamiania debugowania bez debugowania, aby uniknąć narzutu związanego z uruchamianiem kodu  >   w Visual Studio debugowania.

## <a name="create-the-core-c-projects"></a>Tworzenie podstawowych projektów C++

Postępuj zgodnie z instrukcjami w tej sekcji, aby utworzyć dwa identyczne projekty języka C++ o nazwach "superfastcode" i "superfastcode2". Później użyjesz innych środków w każdym projekcie, aby uwidocznić kod C++ w języku Python.

1. Upewnij `PYTHONHOME` się, że zmienna środowiskowa jest ustawiona na interpreter języka Python, którego chcesz użyć. Projekty języka C++ w Visual Studio tej zmiennej do lokalizowania plików, takich jak *python.h*, które są używane podczas tworzenia rozszerzenia języka Python.

1. Kliknij prawym przyciskiem myszy rozwiązanie na stronie **Eksplorator rozwiązań** a następnie **wybierz pozycję Dodaj** nowy  >  **projekt.** Rozwiązanie Visual Studio może zawierać jednocześnie projekty języków Python i C++ (co jest jedną z zalet używania języka Visual Studio dla języka Python).

1. Wyszukaj ciąg "C++", wybierz **pozycję** Pusty projekt, podaj nazwę "superfastcode" ("superfastcode2" dla drugiego projektu), a następnie wybierz **przycisk OK.**

    > [!Tip]
    > Po **zainstalowaniu** natywnych narzędzi programist Visual Studio Python możesz zacząć od szablonu modułu rozszerzenia języka **Python,** który zawiera już większość czynności opisanych poniżej. Jednak w tym przewodniku rozpoczęcie od pustego projektu demonstruje krok po kroku tworzenie modułu rozszerzenia. Po zrozumieniu procesu szablon oszczędza czas podczas pisania własnych rozszerzeń.

1. Utwórz plik C++ w nowym projekcie,  klikając prawym przyciskiem myszy węzeł Pliki źródłowe, a następnie wybierz pozycję Dodaj nowy element, wybierz pozycję  >   **Plik C++,** nadaj jej nazwę `module.cpp` i wybierz przycisk **OK.**

    > [!Important]
    > Plik z *rozszerzeniem CPP* jest niezbędny, aby włączyć strony właściwości języka C++ w poniższych krokach.

1. Kliknij prawym przyciskiem myszy projekt C++ w **Eksplorator rozwiązań** wybierz pozycję **Właściwości**.

1. W górnej części wyświetlonego **okna dialogowego Strony** właściwości ustaw **opcję** Konfiguracja na Wszystkie **konfiguracje,** a **opcję Platforma** na **Win32.**

1. Ustaw określone właściwości zgodnie z opisem w poniższej tabeli, a następnie wybierz przycisk **OK**.

    | Tab | Właściwość | Wartość |
    | --- | --- | --- |
    | **Ogólne** | **Ogólne**  >  **Nazwa obiektu docelowego** | Określ nazwę modułu, aby odwoływać się do niego z języka Python w `from...import` instrukcjach. Użyj tej samej nazwy w języku C++ podczas definiowania modułu dla języka Python. Jeśli chcesz użyć nazwy projektu jako nazwy modułu, pozostaw wartość domyślną **$(ProjectName)**. |
    | | **Ogólne**  >  **Rozszerzenie docelowe** | **.pyd** |
    | | **Project Defaults (Ustawienia domyślne projektu)**  >  **Typ konfiguracji** | **Biblioteka dynamiczna (dll)** |
    | **C/C++**  >  **Ogólne** | **Dodatkowe katalogi dołączania** | Dodaj folder *dołączania języka* Python zgodnie z potrzebami instalacji, na przykład `c:\Python36\include` .  |
    | **C/C++**  >  **Preprocesor** | **Definicje preprocesora** | **Tylko CPython:** dodaj ciąg na początku ciągu `Py_LIMITED_API;` (w tym średnik). Ta definicja ogranicza niektóre funkcje, które można wywołać z języka Python, i sprawia, że kod jest bardziej przenośny między różnymi wersjami języka Python. Jeśli pracujesz z PyBind11, nie dodawaj tej definicji. W przeciwnym razie zobaczysz błędy kompilacji. |
    | **C/C++**  >  **Generowanie kodu** | **Biblioteka środowiska uruchomieniowego** | **Wielowątkowa biblioteka DLL (/MD)** (zobacz ostrzeżenie poniżej) |
    | **Linker**  >  **Ogólne** | **Dodatkowe katalogi biblioteki** | Dodaj folder *libs języka* Python zawierający *pliki .lib* zgodnie z potrzebami instalacji, na przykład `c:\Python36\libs` . (Pamiętaj, aby wskazać folder *libs* zawierający pliki  *.lib,* a nie folder *Lib* zawierający *pliki py).* |

    > [!Tip]
    > Jeśli nie widzisz karty C/C++ we właściwościach projektu, jest to spowodowane tym, że projekt nie zawiera żadnych plików, które identyfikuje jako pliki źródłowe C/C++. Ten warunek może wystąpić, jeśli utworzysz plik źródłowy bez *rozszerzenia C* *lub CPP.* Jeśli na przykład wcześniej wprowadzono plik zamiast w oknie dialogowym nowego elementu, program Visual Studio utworzy plik, ale nie ustawi typu pliku na `module.coo` "Kod C/C+", co spowoduje aktywowanie karty właściwości `module.cpp` C/C++. Taka błędnaidentyfikacja nadal ma miejsce, nawet jeśli zmienisz nazwę pliku na `.cpp` . Aby prawidłowo ustawić typ pliku, kliknij prawym przyciskiem myszy plik w oknie Eksplorator rozwiązań **właściwości,** **a następnie** ustaw typ pliku **na** **kod C/C++.**

    > [!Warning]
    > Zawsze ustawiaj opcję Biblioteka środowiska uruchomieniowego generowania kodu **C/C++** na wielowątkową bibliotekę  >    >   **DLL (/MD),** nawet w przypadku konfiguracji debugowania, ponieważ to ustawienie jest tym, za pomocą których są budowane pliki binarne języka Python bez debugowania. Jeśli w języku CPython ustawisz wielowątkową bibliotekę **DLL debugowania (/MDd),** kompilacja konfiguracji debugowania spowoduje błąd **C1189: program Py_LIMITED_API** jest niezgodny z bibliotekami Py_DEBUG, Py_TRACE_REFS i Py_REF_DEBUG .  Ponadto w przypadku usunięcia (co jest wymagane w przypadku języka CPython, ale nie PyBind11) w celu uniknięcia błędu kompilacji, język Python ulega awarii podczas próby zaimportowania `Py_LIMITED_API` modułu. (Awaria występuje w ramach wywołania biblioteki DLL do zgodnie z opisem w dalszej części, z komunikatem o błędzie krytycznym języka `PyModule_Create` **Python: PyThreadState_Get: brak bieżącego wątku).**
    >
    > Opcja /MDd służy do kompilowania plików binarnych *debugowania* języka Python (takich jakpython_d.exe), ale wybranie jej dla biblioteki DLL rozszerzenia nadal powoduje błąd kompilacji z `Py_LIMITED_API` .

1. Kliknij prawym przyciskiem myszy projekt C++ i wybierz pozycję **Kompilacja,** aby przetestować konfiguracje **(debugowanie** i **wydanie).** Pliki *pyd* znajdują się w folderze **rozwiązania** w obszarze **Debugowanie** i **wydanie,** a nie w samym folderze projektu języka C++.

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

1. Skompilowanie projektu języka C++ ponownie w celu potwierdzenia, że kod jest poprawny.

1. Jeśli jeszcze tego nie zrobiono, powtórz powyższe kroki, aby utworzyć drugi projekt o nazwie "superfastcode2" o identycznej zawartości.

## <a name="convert-the-c-projects-to-extensions-for-python"></a>Konwertowanie projektów języka C++ na rozszerzenia dla języka Python

Aby wprowadzić bibliotekę DLL języka C++ do rozszerzenia dla języka Python, najpierw zmodyfikuj wyeksportowane metody w celu interakcji z typami języka Python. Następnie dodasz funkcję, która eksportuje moduł wraz z definicjami metod modułu.

W kolejnych sekcjach wyjaśniono, jak wykonać te kroki przy użyciu rozszerzeń CPython i PyBind11.

### <a name="cpython-extensions"></a>Rozszerzenia CPython

Aby uzyskać podstawowe informacje na temat tego, co pokazano w tej sekcji dotyczącej języka Python 3.x, zapoznaj się z podręcznikiem dokumentacji interfejsu API języka [Python/C,](https://docs.python.org/3/c-api/index.html) a szczególnie z tematem [Module Objects](https://docs.python.org/3/c-api/module.html) on python.org (pamiętaj, aby wybrać swoją wersję języka Python z kontrolki listy rozwijanej w prawym górnym rogu, aby wyświetlić poprawną dokumentację).

Jeśli pracujesz z językiem Python 2.7, zapoznaj się z tematem Rozszerzanie języka [Python 2.7](https://docs.python.org/2.7/extending/extending.html) za pomocą języka C lub C++ i Przenoszenie modułów rozszerzeń do języka [Python 3](https://docs.python.org/2.7/howto/cporting.html) (python.org).

1. W górnej części *modułu module.cpp dołącz* *python.h:*

    ```cpp
    #include <Python.h>
    ```

1. `tanh_impl`Zmodyfikuj metodę , aby akceptowała i zwracała typy języka Python `PyObject*` (czyli :

    ```cpp
    PyObject* tanh_impl(PyObject *, PyObject* o) {
        double x = PyFloat_AsDouble(o);
        double tanh_x = sinh_impl(x) / cosh_impl(x);
        return PyFloat_FromDouble(tanh_x);
    }
    ```

1. Dodaj strukturę definiującą sposób, w jaki funkcja C++ `tanh_impl` jest prezentowana w języku Python:

    ```cpp
    static PyMethodDef superfastcode_methods[] = {
        // The first property is the name exposed to Python, fast_tanh, the second is the C++
        // function name that contains the implementation.
        { "fast_tanh", (PyCFunction)tanh_impl, METH_O, nullptr },

        // Terminate the array with an object containing nulls.
        { nullptr, nullptr, 0, nullptr }
    };
    ```

1. Dodaj strukturę definiującą moduł tak, jak chcesz odwoływać się do niego w kodzie języka Python, szczególnie w przypadku używania `from...import` instrukcji . (Upewnij się, że jest to zgodne z wartością we właściwościach projektu w **obszarze Właściwości konfiguracji**  >  **Ogólne**  >  **Nazwa obiektu docelowego).** W poniższym przykładzie nazwa modułu "superfastcode" oznacza, że można używać w języku Python, ponieważ jest `from superfastcode import fast_tanh` `fast_tanh` zdefiniowana w pliku `superfastcode_methods` . (Nazwy plików wewnętrzne projektu C++, takie *jak module.cpp*, są niesekwencjonalne).

    ```cpp
    static PyModuleDef superfastcode_module = {
        PyModuleDef_HEAD_INIT,
        "superfastcode",                        // Module name to use with Python import statements
        "Provides some functions, but faster",  // Module description
        0,
        superfastcode_methods                   // Structure that defines the methods of the module
    };
    ```

1. Dodaj metodę, którą język Python wywołuje podczas ładowania modułu, który musi mieć nazwę , gdzie nazwa modułu dokładnie odpowiada właściwości General Target Name projektu C++ (czyli jest taka sama jak nazwa pliku `PyInit_<module-name>` &lt; &gt;   >   *pyd* sbudowaną przez projekt).

    ```cpp
    PyMODINIT_FUNC PyInit_superfastcode() {
        return PyModule_Create(&superfastcode_module);
    }
    ```

1. Ustaw konfigurację docelową na **wartość Release (Wydanie)** i ponownie skompilowaj projekt C++, aby zweryfikować kod. Jeśli wystąpią błędy, zobacz [sekcję Rozwiązywanie](#troubleshooting) problemów poniżej.

### <a name="pybind11"></a>PyBind11

Jeśli zostały wykonane kroki opisane w poprzedniej sekcji, na pewno zauważono, że do utworzenia niezbędnych struktur modułów dla kodu języka C++ używano wielu kodów programowania standardowego. PyBind11 upraszcza proces za pomocą makr w pliku nagłówkowym języka C++, które osiągną ten sam wynik przy znacznie mniejszym kodzie. Aby uzyskać podstawowe informacje na temat informacji wyświetlanych w tej sekcji, zobacz [PyBind11 basics](https://github.com/pybind/pybind11/blob/master/docs/basics.rst) (github.com).

1. Zainstaluj pakiet PyBind11 przy użyciu narzędzia pip: `pip install pybind11` lub `py -m pip install pybind11` .

1. W górnej części *modułu module.cpp* dołącz *pybind11.h:*

    ```cpp
    #include <pybind11/pybind11.h>
    ```

1. W dolnej części *modułu module.cpp* użyj makra , `PYBIND11_MODULE` aby zdefiniować punkt wejścia do funkcji języka C++:

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

1. Ustaw konfigurację docelową na **wartość Release (Wydanie)** i skompilowanie projektu C++ w celu zweryfikowania kodu. Jeśli wystąpią błędy, zobacz następną sekcję na temat rozwiązywania problemów.

### <a name="troubleshooting"></a>Rozwiązywanie problemów

Kompilacja modułu C++ może się nie powieść z następujących powodów:

- Nie można zlokalizować pliku *Python.h* (**E1696: cannot open source file "Python.h"** and/or **C1083: Cannot open include file: "Python.h": No such file or directory**: verify that the path in C/C++ General Additional Include Directories in the project properties points to your Python installation's include folder (Nie można zlokalizować pliku dołączanego języka Python: nie można otworzyć pliku E1696: nie można odnaleźć takiego pliku lub katalogu): sprawdź, czy ścieżka w folderze **C/C++**  >  **General**  >  **Additional Include Directories**  we właściwościach projektu wskazuje folder include instalacji języka Python. Zobacz krok 6 w [obszarze Tworzenie podstawowego projektu C++.](#create-the-core-c-projects)

- Nie można zlokalizować bibliotek języka Python: sprawdź, czy ścieżka w dodatkowych katalogach biblioteki **linkera** we właściwościach projektu wskazuje  >    >   folder *libs instalacji języka* Python. Zobacz krok 6 w [obszarze Tworzenie podstawowego projektu C++.](#create-the-core-c-projects)

- Błędy łączenia związane z architekturą docelową: zmień architekturę projektu obiektu docelowego języka C++ tak, aby dopasować architekturę instalacji języka Python. Jeśli na przykład elementem docelowym jest x64 w projekcie języka C++, ale instalacja języka Python to x86, zmień projekt języka C++ na docelowy x86.

## <a name="test-the-code-and-compare-the-results"></a>Testowanie kodu i porównywanie wyników

Teraz, gdy masz biblioteki DLL ustrukturyzowane jako rozszerzenia języka Python, możesz odwoływać się do nich z projektu języka Python, importować moduły i używać ich metod.

### <a name="make-the-dll-available-to-python"></a>Udostępnij bibliotekę DLL językowi Python

Istnieją dwa sposoby, aby udostępnić bibliotekę DLL w języku Python.

Pierwsza metoda działa, jeśli projekt języka Python i projekt języka C++ znajdują się w tym samym rozwiązaniu. Przejdź do **Eksplorator rozwiązań**, kliknij prawym przyciskiem myszy węzeł **Odwołania** w projekcie języka Python, a następnie wybierz pozycję **Dodaj odwołanie**. W wyświetlonym oknie dialogowym wybierz **kartę Projekty,** wybierz projekty **superfastcode** i **superfastcode2,** a następnie wybierz przycisk **OK.**

![Dodawanie odwołania do projektu superfastcode](media/cpp-add-reference.png)

Alternatywna metoda, opisana w poniższych krokach, instaluje moduł w globalnym środowisku języka Python, dzięki czemu jest również dostępny dla innych projektów języka Python. (Zwykle wymaga to odświeżenia bazy danych uzupełniania IntelliSense dla tego środowiska w programie Visual Studio 2017 w wersji 15.5 i starszych. Odświeżanie jest również niezbędne podczas usuwania modułu ze środowiska).

1. Jeśli używasz programu Visual Studio 2017 lub nowszego, uruchom instalatora programu Visual Studio, wybierz pozycję Modyfikuj **,** wybierz pozycję Kompilatory poszczególnych składników, narzędzia kompilacji i środowiska uruchomieniowe   >    >  **Visual C++ 2015.3 w wersji 140.** Ten krok jest niezbędny, ponieważ język Python (dla systemu Windows) jest samodzielnie budowania przy użyciu programu Visual Studio 2015 (wersja 14.0) i oczekuje, że te narzędzia będą dostępne podczas budowania rozszerzenia za pomocą metody opisanej tutaj. (Pamiętaj, że może być konieczne zainstalowanie 32-bitowej wersji języka Python i ukierunkowanie biblioteki DLL na Win32, a nie x64).

1. Utwórz plik o *nazwie setup.py* w projekcie języka C++, klikając projekt prawym przyciskiem myszy i wybierając **polecenie Dodaj** nowy  >  **element**. Następnie wybierz pozycję **Plik C++ (cpp),** nadaj plikowi nazwę i wybierz przycisk OK (nazwanie pliku rozszerzeniem PY sprawia, że program Visual Studio rozpoznaje go jako język Python mimo używania szablonu pliku `setup.py` C++).   Gdy plik pojawi się w edytorze, wklej do niego następujący kod zgodnie z metodą rozszerzenia:

    **Rozszerzenia CPython (projekt superfastcode):**

    ```python
    from distutils.core import setup, Extension, DEBUG

    sfc_module = Extension('superfastcode', sources = ['module.cpp'])

    setup(name = 'superfastcode', version = '1.0',
        description = 'Python Package with superfastcode C++ extension',
        ext_modules = [sfc_module]
        )
    ```

    Aby uzyskać dokumentację dotyczącą tego skryptu, zobacz Building [C and C++ extensions](https://docs.python.org/3/extending/building.html) (python.org) (Tworzenie rozszerzeń C i C++ (python.org).

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

1. Kod *setup.py* instruuje język Python, aby skompilował rozszerzenie przy użyciu zestawu narzędzi języka C++ Visual Studio 2015, gdy jest używany z wiersza polecenia. Otwórz wiersz polecenia z podwyższonym poziomem uprawnień, przejdź do folderu zawierającego projekt języka C++ (czyli folder zawierający setup.py *)* i wprowadź następujące polecenie:

    ```command
    pip install .
    ```

    lub:

    ```command
    py -m pip install .
    ```

### <a name="call-the-dll-from-python"></a>Wywołanie biblioteki DLL z języka Python

Po wywróceniu biblioteki DLL w języku Python zgodnie z opisem w poprzedniej sekcji możesz teraz wywołać funkcje i z kodu języka Python i porównać ich wydajność z implementacją `superfastcode.fast_tanh` `superfastcode2.fast_tanh2` języka Python:

1. Dodaj następujące wiersze w pliku *py,* aby wywołać metody wyeksportowane z bibliotek DLL i wyświetlić ich dane wyjściowe:

    ```python
    from superfastcode import fast_tanh
    test(lambda d: [fast_tanh(x) for x in d], '[fast_tanh(x) for x in d] (CPython C++ extension)')

    from superfastcode2 import fast_tanh2
    test(lambda d: [fast_tanh2(x) for x in d], '[fast_tanh2(x) for x in d] (PyBind11 C++ extension)')
    ```

1. Uruchom program wjęzyku Python (Debuguj rozpocznij bez debugowania lub naciśnij klawisz  >    + **F5)** i zauważ, że procedury języka C++ są uruchamiane około pięć do dwudziestu razy szybciej niż implementacja języka Python. Typowe dane wyjściowe są wyświetlane w następujący sposób:

    ```output
    Running benchmarks with COUNT = 500000
    [tanh(x) for x in d] (Python implementation) took 0.758 seconds

    [fast_tanh(x) for x in d] (CPython C++ extension) took 0.076 seconds

    [fast_tanh2(x) for x in d] (PyBind11 C++ extension) took 0.204 seconds
    ```

    Jeśli polecenie **Uruchom bez debugowania** jest wyłączone, kliknij prawym przyciskiem myszy projekt języka Python Eksplorator rozwiązań **wybierz** pozycję Ustaw jako **projekt startowy.**

1. Spróbuj zwiększyć `COUNT` zmienną, aby różnice były bardziej wymawiane. Kompilacja **debugowania** modułu C++ działa  również wolniej niż kompilacja wydania, ponieważ **kompilacja debugowania** jest mniej zoptymalizowana i zawiera różne kontrole błędów. Możesz przełączać się między tymi konfiguracjami w celu porównania.

> [!NOTE]
> W danych wyjściowych widać, że rozszerzenie PyBind11 nie jest tak szybkie jak rozszerzenie CPython, chociaż nadal jest znacznie szybsze niż prosta implementacja języka Python. Różnica wynika z niewielkiego narzutu na wywołania, które wprowadza PyBind11, aby znacznie ułatwić interfejs języka C++. Różnica między wywołaniami jest w rzeczywistości dość niewielka: ponieważ kod testowy wywołuje funkcje rozszerzenia 500 000 razy, wyniki, które widzisz tutaj, znacznie wzmacniają ten narzut! Zazwyczaj funkcja języka C++ robi znacznie więcej pracy niż trywialne metody używane w tym miejscu, w takim przypadku obciążenie jest `fast_tanh[2]` nieistotne. Jeśli jednak wdrażasz metody, które mogą być wywoływane tysiące razy na sekundę, użycie podejścia CPython może spowodować lepszą wydajność niż PyBind11.

## <a name="debug-the-c-code"></a>Debugowanie kodu C++

Visual Studio obsługuje debugowanie kodu w językach Python i C++. W tej sekcji ominiesz proces przy użyciu **projektu superfastcode;** Kroki są takie same dla projektu **superfastcode2.**

1. Kliknij prawym przyciskiem myszy projekt języka Python w Eksplorator rozwiązań **,** wybierz pozycję **Właściwości,** wybierz kartę **Debugowanie,** a następnie wybierz opcję **Debuguj**  >  **Włącz debugowanie kodu natywnego.**

    > [!Tip]
    > Po włączeniu debugowania kodu natywnego okno danych wyjściowych języka Python może zniknąć natychmiast po zakończeniu działania programu bez zwykłego naciśnięcia dowolnego klawisza, aby **kontynuować wstrzymanie.** Aby wymusić wstrzymanie, dodaj opcję do pola Argumenty interpretera uruchamiania na karcie `-i`   >   **Debugowanie** po włączeniu debugowania kodu natywnego. Ten argument wprowadza interpreter języka Python w tryb interaktywny po zakończeniu działania kodu, po czym czeka na naciśnięcie klawisza **Ctrl** Z Enter w celu +   >   zakończenia działania. (Alternatywnie, jeśli nie przeszkadza Ci modyfikowanie kodu w języku Python, możesz dodać instrukcje i na `import os` `os.system("pause")` końcu programu. Ten kod duplikuje oryginalny monit o wstrzymanie).

1. Wybierz **pozycję Plik**  >  **Zapisz,** aby zapisać zmiany właściwości.

1. Ustaw konfigurację kompilacji na **debugowanie** na pasku Visual Studio narzędzi.

    ![Ustawianie konfiguracji kompilacji na debugowanie](media/cpp-set-debug.png)

1. Ponieważ zazwyczaj uruchamianie kodu w debugerze trwa dłużej, możesz zmienić zmienną w pliku py na wartość, która jest około pięć razy mniejsza (na przykład zmień ją z `COUNT`  `500000` na `100000` ).

1. W kodzie języka C++ ustaw punkt przerwania w pierwszym wierszu metody, a następnie uruchom `tanh_impl` debuger **(F5** lub **Rozpocznij**  >  **debugowanie debugowania).** Debuger zatrzymuje się po wywołaniu tego kodu. Jeśli punkt przerwania nie zostanie trafiony, sprawdź, czy konfiguracja jest ustawiona na debugowanie i czy projekt został zapisany (co nie dzieje się automatycznie podczas uruchamiania debugera). 

    ![Zatrzymywanie w punkcie przerwania w kodzie C++](media/cpp-debugging.png)

1. W tym momencie możesz przejść przez kod języka C++, przeanalizować zmienne i tak dalej. Te funkcje są szczegółowo opisane w te [tematach Debugowanie razem języków C++ i Python.](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)

## <a name="alternative-approaches"></a>Alternatywne podejścia

Istnieją różne sposoby tworzenia rozszerzeń języka Python zgodnie z opisem w poniższej tabeli. Dwa pierwsze wpisy dotyczące CPython i PyBind11 zostały już omówione w tym artykule.

| Podejście | Vintage | Reprezentatywni użytkownikom | 
| --- | --- | --- |
| Moduły rozszerzeń C/C++ dla języka CPython | 1991 | Standardowa biblioteka | 
| [PyBind11](https://github.com/pybind/pybind11) (zalecane dla języka C++) | 2015 |  |
| Cython (zalecane dla języka C) | 2007 | [gevent,](https://www.gevent.org/) [kivy](https://kivy.org/) |
| [Boost.Python](https://www.boost.org/doc/libs/1_66_0/libs/python/doc/html/index.html) | 2002 | |
| typy ctype | 2003 | [oscrypto](https://github.com/wbond/oscrypto) | 
| Swig | 1996 | [crfsuite](http://www.chokkan.org/software/crfsuite/) | 
| cffi | 2013 | [kryptografia,](https://cryptography.io/en/latest/) [pypy](https://pypy.org/) |
| [cppyy](https://cppyy.readthedocs.io/en/latest/) | 2017 | |

## <a name="see-also"></a>Zobacz też

Ukończony przykład z tego przewodnika można znaleźć w witrynie [python-samples-vs-cpp-extension](https://github.com/Microsoft/python-sample-vs-cpp-extension) (GitHub).

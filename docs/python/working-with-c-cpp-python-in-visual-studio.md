---
title: Pisanie rozszerzeń języka C++ dla języka Python
description: Przewodnik tworzenia rozszerzenia języka C++ dla języka Python przy użyciu języków Visual Studio, CPython i PyBind11, w tym debugowania w trybie mieszanym.
ms.date: 05/11/2021
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 286d5f2c316379316b1a1cf55334cab39cdc247c
ms.sourcegitcommit: 69256dc47489853dc66a037f5b0c1275977540c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2021
ms.locfileid: "109782637"
---
# <a name="create-a-c-extension-for-python"></a>Tworzenie rozszerzenia C++ dla języka Python

Moduły napisane w języku C++ (lub C) są często używane w celu rozszerzenia możliwości interpretera języka Python, a także umożliwienia dostępu do funkcji systemu operacyjnego niskiego poziomu. Istnieją trzy podstawowe typy modułów:

- Moduły akceleratora: ponieważ Python jest językiem interpretowany, niektóre fragmenty kodu można zapisywać w języku C++, aby uzyskać wyższą wydajność.
- Moduły otoki: uwidoczniają istniejące interfejsy C/C++ dla kodu języka Python lub uwidoczniają bardziej "pythonowy" interfejs API, który jest łatwy w użyciu z języka Python.
- Moduły dostępu do systemu niskiego poziomu: utworzone w celu uzyskania dostępu do funkcji niższego poziomu środowiska `CPython` uruchomieniowego, systemu operacyjnego lub bazowego sprzętu.

W tym artykule omykamy proces tworzenia modułu rozszerzenia języka C++ dla tego modułu, który oblicza `CPython` tangens hiperboliczny i wywołuje go z kodu w języku Python. Procedura jest wdrażana jako pierwsza w języku Python w celu zademonstrowania względnego przyrostu wydajności implementacji tej samej procedury w języku C++.

W tym artykule pokazano również dwa sposoby, aby udostępnić język C++ językowi Python:

- Standardowe rozszerzenia `CPython` zgodnie z opisem w [dokumentacji języka Python](https://docs.python.org/3/c-api/)
- [PyBind11](https://github.com/pybind/pybind11), który jest zalecany dla języka C++ 11 ze względu na jego prostotę.

Ukończony przykład z tego przewodnika można znaleźć w witrynie [python-samples-vs-cpp-extension](https://github.com/Microsoft/python-sample-vs-cpp-extension) (GitHub).

## <a name="prerequisites"></a>Wymagania wstępne

- Visual Studio 2017 r. lub nowszym z zainstalowanym obciążeniem Programowanie w języku **Python,** w tym natywnymi narzędziami programistyczmi języka **Python,** które wprowadzają obciążenie języka C++ i zestawy narzędzi niezbędne dla rozszerzeń natywnych.

    ![Wybieranie opcji Natywne narzędzia programowe w języku Python](media/cpp-install-native.png)

    > [!Tip]
    > Instalowanie obciążenia **Aplikacje do analizy i przetwarzania** danych domyślnie obejmuje również język Python i natywne narzędzia programistyczne języka **Python.**

Aby uzyskać więcej informacji na temat opcji instalacji, zobacz [Instalowanie obsługi języka Python dla Visual Studio](installing-python-support-in-visual-studio.md). Jeśli zainstalujesz język Python oddzielnie, pamiętaj, aby wybrać pozycję Pobierz symbole **debugowania** w obszarze **Opcje zaawansowane** w jego instalatorze. Ta opcja jest wymagana do korzystania z debugowania w trybie mieszanym między kodem języka Python a kodem natywnym.

## <a name="create-the-python-application"></a>Tworzenie aplikacji w języku Python

1. Utwórz nowy projekt języka Python w programie Visual Studio wybierając **pozycję File** New Project  >  **(Nowy projekt**  >  **pliku).** Wyszukaj pozycję "Python", wybierz szablon **Aplikacja języka Python,** nadaj mu nazwę i lokalizację, a następnie wybierz przycisk **OK.**

1. W pliku *PY* projektu wklej następujący kod (lub wprowadź go ręcznie, aby doświadczyć niektórych funkcji edycji [języka Python).](editing-python-code-in-visual-studio.md) Ten kod oblicza tangens hiperboliczny bez korzystania z biblioteki matematycznej i właśnie tym będziemy przyspieszać dzięki natywnym rozszerzeniom.

    > [!Tip]
    > Napisz kod w czystym języku Python przed napisem ponownie w języku C++. W ten sposób można łatwiej sprawdzić, czy kod natywny jest poprawny

    ```python
    from random import random
    from time import perf_counter

    COUNT = 500000  # Change this value depending on the speed of your computer
    DATA = [(random() - 0.5) * 3 for _ in range(COUNT)]

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
> Podczas uruchamiania testów porównawczych należy zawsze używać uruchamiania debugowania bez debugowania, aby uniknąć narzutu związanego z uruchamianiem kodu w  >   Visual Studio debugowania.

## <a name="create-the-core-c-projects"></a>Tworzenie podstawowych projektów C++

Postępuj zgodnie z instrukcjami w tej sekcji, aby utworzyć dwa identyczne projekty języka C++ o nazwach "superfastcode" i "superfastcode2". Później użyjesz dwóch różnych metod w każdym projekcie, aby uwidocznić kod C++ w języku Python.

1. Kliknij prawym przyciskiem myszy rozwiązanie na stronie **Eksplorator rozwiązań** a następnie **wybierz pozycję Dodaj** nowy  >  **projekt.** Rozwiązanie Visual Studio może zawierać jednocześnie projekty języków Python i C++ (co jest jedną z zalet używania języka Visual Studio dla języka Python).

1. Wyszukaj ciąg "C++", wybierz **pozycję** Pusty projekt, określ nazwę "superfastcode" ("superfastcode2" dla drugiego projektu), a następnie wybierz przycisk **OK**.

    > [!Tip]
    > Po **zainstalowaniu** natywnych narzędzi programistych języka Python w środowisku Visual Studio można zamiast tego rozpocząć od szablonu modułu rozszerzenia języka **Python,** który zawiera już większość czynności opisanych poniżej. Jednak w tym przewodniku, począwszy od pustego projektu, pokazano, jak budować moduł rozszerzenia krok po kroku. Po zrozumieniu procesu szablon oszczędza czas podczas pisania własnych rozszerzeń.

1. Utwórz plik C++ w nowym projekcie,  klikając prawym przyciskiem myszy węzeł Pliki źródłowe, a następnie wybierz pozycję Dodaj nowy element, wybierz pozycję  >   **Plik C++,** nadaj jej nazwę `module.cpp` i wybierz przycisk **OK.**

    > [!Important]
    > Plik z *rozszerzeniem CPP* jest niezbędny, aby włączyć strony właściwości języka C++ w poniższych krokach.

1. Jeśli używasz 64-bitowego środowiska uruchomieniowego języka Python, aktywuj konfigurację **x64** przy użyciu menu rozwijanego na głównym pasku narzędzi. W przypadku 32-bitowego środowiska uruchomieniowego języka Python aktywuj **konfigurację systemu Win32.**

1. Kliknij prawym przyciskiem myszy projekt C++ w **Eksplorator rozwiązań**, wybierz pozycję **Właściwości**. Wartość konfiguracji powinna **być** aktywna **(debugowanie),** a **wartość Platforma** będzie aktywna **(x64)** lub aktywna **(Win32)** w zależności od wyboru w poprzednim kroku.

    > [!Tip]
    > W przypadku własnych projektów należy skonfigurować konfiguracje debugowania i wydania. W tym miejscu skonfigurujemy tylko konfigurację  debugowania i ustawimy ją tak, aby używać kompilacji wydania , która wyłącza niektóre funkcje debugowania środowiska uruchomieniowego języka C++, w tym `CPython` asercji. Używanie `CPython` *plików* binarnych debugowania ( `python_d.exe` ) będzie wymagać różnych ustawień.

1. Ustaw określone właściwości zgodnie z opisem w poniższej tabeli, a następnie wybierz przycisk **OK**.
    ::: moniker range=">=vs-2019"
    | Tab | Właściwość | Wartość |
    | --- | --- | --- |
    | **Ogólne** | **Nazwa obiektu docelowego** | Określ nazwę modułu, aby odwoływać się do niego z języka Python w `from...import` instrukcjach. Użyj tej samej nazwy w języku C++ podczas definiowania modułu dla języka Python. Jeśli chcesz użyć nazwy projektu jako nazwy modułu, pozostaw wartość domyślną **$(ProjectName)**. W `python_d.exe` przypadku nazwy dodaj na końcu nazwy `_d` . |
    | | **Typ konfiguracji** | **Biblioteka dynamiczna (dll)** |
    | **Zaawansowany** | **Rozszerzenie pliku docelowego** | **.pyd** |
    | **C/C++** > **Ogólne** | **Dodatkowe katalogi dołączania** | Dodaj folder *dołączania języka* Python zgodnie z potrzebami instalacji, na przykład `c:\Python36\include` .  |
    | **C/C++** > **Preprocesor** | **Definicje preprocesora** | Jeśli tak, zmień wartość **_DEBUG** na **NDEBUG,** aby dopasować wersję niebugowania `CPython` . (W przypadku `python_d.exe` korzystania z funkcji pozostaw to bez zmian). |
    | **C/C++** > **Generowanie kodu** | **Biblioteka środowiska uruchomieniowego** | **Wielowątkowa biblioteka DLL (/MD)** do dopasowania wersji pliku bez `CPython` debugowania. (W przypadku `python_d.exe` korzystania z funkcji pozostaw to bez zmian). |
    | **Linker** > **Ogólne** | **Dodatkowe katalogi biblioteki** | Dodaj folder *libs języka* Python zawierający *pliki .lib* zgodnie z potrzebami instalacji, na przykład `c:\Python36\libs` . (Pamiętaj, aby wskazać folder *libs* zawierający pliki  *.lib,* a nie folder *Lib* zawierający *pliki py).* |
    ::: moniker-end
    ::: moniker range="=vs-2017"
    | Tab | Właściwość | Wartość |
    | --- | --- | --- |
    | **Ogólne** | **Ogólne** > **Nazwa obiektu docelowego** | Określ nazwę modułu, aby odwoływać się do niego w języku Python w `from...import` instrukcjach . Tej samej nazwy używa się w języku C++ podczas definiowania modułu dla języka Python. Jeśli chcesz użyć nazwy projektu jako nazwy modułu, pozostaw wartość domyślną **$(ProjectName)**. W `python_d.exe` przypadku nazwy dodaj na końcu nazwy `_d` . |
    | | **Ogólne** > **Rozszerzenie docelowe** | **.pyd** |
    | | **Project Defaults (Ustawienia domyślne projektu)** > **Typ konfiguracji** | **Biblioteka dynamiczna (dll)** |
    | **C/C++** > **Ogólne** | **Dodatkowe katalogi dołączania** | Dodaj folder *dołączania języka* Python zgodnie z potrzebami instalacji, na przykład `c:\Python36\include` .  |
    | **C/C++** > **Preprocesor** | **Definicje preprocesora** | Jeśli tak, zmień wartość **_DEBUG** na **NDEBUG,** aby dopasować wersję niebugowania `CPython` . (W przypadku `python_d.exe` korzystania z funkcji pozostaw to bez zmian). |
    | **C/C++** > **Generowanie kodu** | **Biblioteka środowiska uruchomieniowego** | **Wielowątkowa biblioteka DLL (/MD)** do dopasowania wersji pliku bez `CPython` debugowania. (W przypadku korzystania `python_d.exe` z funkcji pozostaw to bez zmian). |
    | **Linker** > **Ogólne** | **Dodatkowe katalogi biblioteki** | Dodaj folder *libs języka* Python zawierający *pliki .lib* zgodnie z potrzebami instalacji, na przykład `c:\Python36\libs` . (Pamiętaj, aby wskazać folder *libs* zawierający pliki  *lib,* a nie folder *Lib* zawierający *pliki py).* |
    ::: moniker-end
    
    > [!Tip]
    > Jeśli nie widzisz karty C/C++ we właściwościach projektu, jest to spowodowane tym, że projekt nie zawiera żadnych plików, które identyfikuje jako pliki źródłowe C/C++. Ten warunek może wystąpić, jeśli utworzysz plik źródłowy bez rozszerzenia *c* *lub cpp.* Jeśli na przykład przypadkowo wprowadzono element zamiast w oknie dialogowym nowego elementu, program Visual Studio utworzy plik, ale nie ustawi typu pliku na `module.coo` "Kod C/C+", co aktywuje kartę właściwości `module.cpp` C/C++. Taka błędnaidentyfikacja nadal ma miejsce, nawet jeśli zmienisz nazwę pliku na `.cpp` . Aby prawidłowo ustawić typ pliku, kliknij prawym przyciskiem myszy plik w pliku Eksplorator rozwiązań **właściwości,** **a następnie** ustaw typ pliku **na** **kod C/C++.**

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

Aby wprowadzić bibliotekę DLL języka C++ do rozszerzenia dla języka Python, najpierw zmodyfikuj wyeksportowane metody, aby wchodzić w interakcje z typami języka Python. Następnie dodasz funkcję, która eksportuje moduł wraz z definicjami metod modułu.

W kolejnych sekcjach wyjaśniono, jak wykonać te kroki przy użyciu rozszerzeń i `CPython` PyBind11.

### <a name="cpython-extensions"></a>Rozszerzenia CPython

Aby uzyskać więcej informacji na temat tego, co pokazano w tej sekcji, zapoznaj się z podręcznikiem interfejsu API języka [Python/języka C,](https://docs.python.org/3/c-api/index.html) a szczególnie z tematem [Module Objects](https://docs.python.org/3/c-api/module.html) on python.org (Pamiętaj, aby wybrać wersję języka Python z kontrolki listy rozwijanej w prawym górnym rogu, aby wyświetlić poprawną dokumentację).

1. W górnej części *modułu module.cpp dołącz* *python.h*:

    ```cpp
    #include <Python.h>
    ```

1. `tanh_impl`Zmodyfikuj metodę , aby akceptowała i zwracała typy języka Python `PyObject*` (czyli ):

    ```cpp
    PyObject* tanh_impl(PyObject* /* unused module reference */, PyObject* o) {
        double x = PyFloat_AsDouble(o);
        double tanh_x = sinh_impl(x) / cosh_impl(x);
        return PyFloat_FromDouble(tanh_x);
    }
    ```

1. Dodaj strukturę definiującą sposób, w jaki funkcja C++ `tanh_impl` jest prezentowana w języku Python:

    ```cpp
    static PyMethodDef superfastcode_methods[] = {
        // The first property is the name exposed to Python, fast_tanh
        // The second is the C++ function with the implementation
        // METH_O means it takes a single PyObject argument
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

1. Skompilowanie projektu języka C++ ponownie w celu zweryfikowania kodu. Jeśli wystąpią błędy, zobacz [sekcję Rozwiązywanie](#troubleshooting) problemów poniżej.

### <a name="pybind11"></a>PyBind11

Jeśli zostały wykonane kroki opisane w poprzedniej sekcji, na pewno zauważono, że do utworzenia niezbędnych struktur modułów dla kodu języka C++ używano wielu kodów programowania standardowego. PyBind11 upraszcza proces za pomocą makr w pliku nagłówkowym języka C++, które osiągną ten sam wynik przy znacznie mniejszym kodzie. Aby uzyskać podstawowe informacje na temat informacji wyświetlanych w tej sekcji, zobacz [PyBind11 basics](https://github.com/pybind/pybind11/blob/master/docs/basics.rst) (github.com).

1. Zainstaluj pakiet PyBind11 przy użyciu narzędzia pip: `pip install pybind11` lub `py -m pip install pybind11` . (Alternatywnie możesz zainstalować program przy użyciu okna Środowiska języka Python, a następnie użyć polecenia "Otwórz w programie Powershell" w następnym kroku).

1. W tym samym terminalu uruchom lub `python -m pybind11 --includes` `py -m pybind11 --includes` . Spowoduje to wydrukowanie listy ścieżek, które należy dodać do właściwości Ogólne dodatkowe katalogi dołączania **języka C/C++** projektu (usunięcie prefiksu, jeśli jest  >    >   `-I` obecny).

1. W górnej części nowego modułu *module.cpp,* który nie zawiera żadnych zmian z poprzedniej sekcji, uwzględnij *pybind11.h:*

    ```cpp
    #include <pybind11/pybind11.h>
    ```

1. W dolnej *części modułu module.cpp* użyj makra , `PYBIND11_MODULE` aby zdefiniować punkt wejścia do funkcji języka C++:

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

1. Skompilowanie projektu języka C++ w celu zweryfikowania kodu. Jeśli wystąpią błędy, zobacz następną sekcję na temat rozwiązywania problemów.

### <a name="troubleshooting"></a>Rozwiązywanie problemów

Kompilacja modułu C++ może się nie powieść z następujących powodów:

- Nie można zlokalizować pliku *Python.h* (**E1696: cannot open source file "Python.h"** and/or **C1083: Cannot open include file: "Python.h": No such file or directory**: verify that the path in C/C++ General Additional Include Directories in the project properties points to your Python installation's include folder (Nie można zlokalizować pliku dołączanego języka Python: nie można otworzyć pliku E1696: nie można odnaleźć takiego pliku lub katalogu): sprawdź, czy ścieżka w folderze **C/C++**  >  **General**  >  **Additional Include Directories**  we właściwościach projektu wskazuje folder include instalacji języka Python. Zobacz krok 6 w [obszarze Tworzenie podstawowego projektu C++.](#create-the-core-c-projects)

- Nie można zlokalizować bibliotek języka Python: sprawdź, czy ścieżka w dodatkowych katalogach biblioteki **linkera** we właściwościach projektu wskazuje  >    >   folder *libs instalacji języka* Python. Zobacz krok 6 w [obszarze Tworzenie podstawowego projektu C++.](#create-the-core-c-projects)

- Błędy łączenia związane z architekturą docelową: zmień architekturę projektu obiektu docelowego języka C++ tak, aby dopasować architekturę instalacji języka Python. Jeśli na przykład projekt **Win32** jest przeznaczony dla projektu języka C++, ale instalacja języka Python jest 64-bitowa, zmień projekt języka C++ na **x64.**

## <a name="test-the-code-and-compare-the-results"></a>Testowanie kodu i porównywanie wyników

Teraz, gdy masz biblioteki DLL ustrukturyzowane jako rozszerzenia języka Python, możesz odwoływać się do nich z projektu języka Python, importować moduły i używać ich metod.

### <a name="make-the-dll-available-to-python"></a>Udostępnij bibliotekę DLL językowi Python

Istnieją dwa sposoby, aby udostępnić bibliotekę DLL w języku Python.

Pierwsza metoda działa, jeśli projekt języka Python i projekt języka C++ znajdują się w tym samym rozwiązaniu. Przejdź do **Eksplorator rozwiązań**, kliknij prawym przyciskiem myszy węzeł **Odwołania** w projekcie języka Python, a następnie wybierz polecenie **Dodaj odwołanie**. W wyświetlonym oknie dialogowym wybierz **kartę Projekty,** wybierz projekty **superfastcode** i **superfastcode2,** a następnie wybierz przycisk **OK.**

![Dodawanie odwołania do projektu superfastcode](media/cpp-add-reference.png)

Alternatywna metoda, opisana w poniższych krokach, instaluje moduł w środowisku języka Python, dzięki czemu jest również dostępny dla innych projektów języka Python. Odwiedź stronę [ **projektu setuptools,** aby](https://setuptools.readthedocs.io/) uzyskać bardziej kompletną dokumentację.

1. Utwórz plik o *nazwie setup.py* w projekcie języka C++, klikając projekt prawym przyciskiem myszy i wybierając **polecenie Dodaj** nowy  >  **element**. Następnie wybierz pozycję **Plik C++ (cpp),** nadaj plikowi nazwę i wybierz przycisk OK (nazwanie pliku rozszerzeniem PY sprawia, że program Visual Studio rozpoznaje go jako język Python mimo używania szablonu pliku `setup.py` C++).   Gdy plik pojawi się w edytorze, wklej do niego następujący kod zgodnie z metodą rozszerzenia:

    **`CPython` rozszerzenia (projekt superfastcode):**

    ```python
    from setuptools import setup, Extension

    sfc_module = Extension('superfastcode', sources = ['module.cpp'])

    setup(
        name='superfastcode',
        version='1.0',
        description='Python Package with superfastcode C++ extension',
        ext_modules=[sfc_module]
    )
    ```

    **`PyBind11` (projekt superfastcode2):**

    ```python
    from setuptools import setup, Extension
    import pybind11

    cpp_args = ['-std=c++11', '-stdlib=libc++', '-mmacosx-version-min=10.7']

    sfc_module = Extension(
        'superfastcode2',
        sources=['module.cpp'],
        include_dirs=[pybind11.get_include()],
        language='c++',
        extra_compile_args=cpp_args,
        )

    setup(
        name='superfastcode2',
        version='1.0',
        description='Python package with superfastcode2 C++ extension (PyBind11)',
        ext_modules=[sfc_module],
    )
    ```

1. Utwórz drugi plik o *nazwie pyproject.toml* w projekcie języka C++ i wklej do niego następujący kod.

    ```toml
    [build-system]
    requires = ["setuptools", "wheel", "pybind11"]
    build-backend = "setuptools.build_meta"
    ```

1. Aby skompilować rozszerzenie, kliknij prawym przyciskiem myszy kartę otwórz plik *pyproject.toml* i wybierz pozycję "Kopiuj pełną ścieżkę" (przed użyciem ścieżki usuniemy nazwę *pyproject.toml).*

1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy aktywne środowisko języka Python i wybierz polecenie *Zarządzaj pakietami języka Python.*

    > [!Tip]
    > Jeśli pakiet został już zainstalowany, będzie on wymieniony tutaj. Przed kontynuowaniem kliknij znak "X", aby go odinstalować.

1. Wklej skopiowaną ścieżkę w polu wyszukiwania i usuń `pyproject.toml` ją na końcu. Następnie naciśnij klawisz Enter, aby zainstalować z tego katalogu.

    > [!Tip]
    > Jeśli instalacja nie powiedzie się z powodu błędu uprawnień, dodaj `--user` polecenie i spróbuj ponownie.


### <a name="call-the-dll-from-python"></a>Wywołanie biblioteki DLL z języka Python

Po wywróceniu biblioteki DLL dla języka Python zgodnie z opisem w poprzedniej sekcji możesz teraz wywołać funkcje i z kodu języka Python i porównać ich wydajność z implementacją `superfastcode.fast_tanh` `superfastcode2.fast_tanh2` języka Python:

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

1. Spróbuj zwiększyć `COUNT` zmienną, aby różnice były bardziej wymawiane. Kompilacja **debugowania** modułu C++ działa  również wolniej niż kompilacja wydania, ponieważ **kompilacja debugowania** jest mniej zoptymalizowana i zawiera różne kontrole błędów. Możesz przełączać się między tymi konfiguracjami w celu porównania (ale pamiętaj, aby wrócić i zaktualizować właściwości z wcześniejszej wersji dla **konfiguracji wydania).**

W danych wyjściowych może być widać, że rozszerzenie PyBind11 nie jest tak szybkie jak rozszerzenie, chociaż powinno być znacznie szybsze niż czysta implementacja `CPython` języka Python. Ta różnica wynika głównie z tego, że u używaliśmy wywołania , które nie obsługuje wielu parametrów, nazw `METH_O` parametrów ani argumentów słów kluczowych. PyBind11 generuje nieco bardziej złożony kod, aby zapewnić wywołującym interfejs podobny do języka Python, ale ponieważ kod testowy wywołuje funkcję 500 000 razy, wyniki mogą znacznie zwiększyć ten narzut!

Możemy jeszcze bardziej zmniejszyć obciążenie, przenosząc `for` pętlę do kodu natywnego. Wymagałoby to użycia [protokołu iteratora](https://docs.python.org/c-api/iter.html) (lub typu PyBind11 dla parametru funkcji ) do `py::iterable` przetwarzania każdego elementu. [](https://pybind11.readthedocs.io/en/stable/advanced/functions.html#python-objects-as-args) Usuwanie powtarzających się przejść między językami Python i C++ jest skutecznym sposobem skrócenia czasu przetwarzania sekwencji.

### <a name="troubleshooting"></a>Rozwiązywanie problemów

Jeśli podczas próby zaimportowania modułu otrzymasz komunikat , prawdopodobnie przyczyną jest jeden z `ImportError` następujących problemów:

* Podczas budowania za pomocą odwołania do projektu upewnij się, że właściwości projektu C++ są zgodne ze środowiskiem języka Python aktywowanym dla projektu języka Python, szczególnie katalogami Dołączanie i Biblioteka.

* Upewnij się, że plik wyjściowy ma nazwę `superfastcode.pyd` . Inna nazwa lub rozszerzenie uniemożliwi jego zaimportowanie.

* Jeśli moduł został zainstalowany przy użyciu *pliku setup.py,* sprawdź, czy uruchomiono polecenie *pip* w środowisku języka Python aktywowanym dla projektu języka Python. Rozszerzenie środowiska Języka Python w Eksplorator rozwiązań powinno pokazywać wpis dla `superfastcode` .

## <a name="debug-the-c-code"></a>Debugowanie kodu C++

Visual Studio obsługuje debugowanie kodu w językach Python i C++. Ta sekcja zawiera procesów przy użyciu **projektu superfastcode;** kroki są takie same dla projektu **superfastcode2.**

1. Kliknij prawym przyciskiem myszy projekt języka Python w oknie **Eksplorator rozwiązań** pozycję **Właściwości,** wybierz kartę **Debugowanie,** a następnie wybierz opcję **Debuguj**  >  Włącz debugowanie kodu **natywnego.**

    > [!Tip]
    > Po włączeniu debugowania kodu natywnego okno danych wyjściowych języka Python może zniknąć natychmiast po zakończeniu działania programu bez zwykłego naciśnięcia dowolnego klawisza, aby **kontynuować wstrzymanie.** Aby wymusić wstrzymanie, dodaj opcję do pola Argumenty interpretera uruchamiania na karcie `-i`   >   **Debugowanie** po włączeniu debugowania kodu natywnego. Ten argument wprowadza interpreter języka Python w tryb interaktywny po zakończeniu działania kodu, po czym czeka na naciśnięcie klawisza **Ctrl** Z Enter w celu +   >   zakończenia działania. (Alternatywnie, jeśli nie przeszkadza Ci modyfikowanie kodu w języku Python, możesz dodać instrukcje i na `import os` `os.system("pause")` końcu programu. Ten kod duplikuje oryginalny monit o wstrzymanie).

1. Wybierz **pozycję Zapisz**  >  **plik,** aby zapisać zmiany właściwości.

1. Ustaw konfigurację kompilacji na **debugowanie** na pasku Visual Studio narzędzi.

    ![Ustawianie konfiguracji kompilacji na debugowanie](media/cpp-set-debug.png)

1. Ponieważ uruchamianie kodu w debugerze trwa dłużej, możesz zmienić zmienną w pliku py na wartość, która jest około pięć razy mniejsza (na przykład zmień ją z na `COUNT`  `500000` `100000` ).

1. W kodzie języka C++ ustaw punkt przerwania w pierwszym wierszu metody, a następnie uruchom `tanh_impl` debuger **(F5** lub **Rozpocznij**  >  **debugowanie debugowania).** Debuger zatrzymuje się po wywołaniu tego kodu. Jeśli punkt przerwania nie zostanie trafiony, sprawdź, czy konfiguracja jest ustawiona na debugowanie i czy projekt został zapisany (co nie dzieje się automatycznie podczas uruchamiania debugera). 

    ![Zatrzymywanie w punkcie przerwania w kodzie C++](media/cpp-debugging.png)

1. W tym momencie możesz przejść przez kod C++, zbadać zmienne i tak dalej. Te funkcje są szczegółowo opisane w te [tematach Debug C++ and Python together](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)(Debugowanie języków C++ i Python razem).

## <a name="alternative-approaches"></a>Alternatywne podejścia

Istnieją różne sposoby tworzenia rozszerzeń języka Python zgodnie z opisem w poniższej tabeli. Dwa pierwsze wpisy dla i zostały już omówione `CPython` `PyBind11` w tym artykule.

| Podejście | Vintage | Reprezentatywni użytkownikom | 
| --- | --- | --- |
| Moduły rozszerzeń C/C++ dla programu `CPython` | 1991 | Standardowa biblioteka | 
| [PyBind11](https://github.com/pybind/pybind11) (zalecane dla języka C++) | 2015 |  |
| [Cython](https://cython.org) (zalecane dla języka C) | 2007 | [gevent,](https://www.gevent.org/) [kivy](https://kivy.org/) |
| [HPy](https://hpyproject.org/) | 2019 | |
| [mypyc](https://mypyc.readthedocs.io/) | 2017 | |
| typy ctype | 2003 | [oscrypto](https://github.com/wbond/oscrypto) | 
| cffi | 2013 | [kryptografia,](https://cryptography.io/) [pypy](https://pypy.org/) |
| Swig | 1996 | [crfsuite](http://www.chokkan.org/software/crfsuite/) | 
| [Boost.Python](https://www.boost.org/doc/libs/1_66_0/libs/python/doc/html/index.html) | 2002 | |
| [Cppyy](https://cppyy.readthedocs.io/) | 2017 | |

## <a name="see-also"></a>Zobacz też

Ukończony przykład z tego przewodnika można znaleźć w witrynie [python-samples-vs-cpp-extension](https://github.com/Microsoft/python-sample-vs-cpp-extension) (GitHub).

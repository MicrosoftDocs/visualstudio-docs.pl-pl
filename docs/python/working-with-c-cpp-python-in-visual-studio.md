---
title: Pisanie rozszerzeń języka C++ dla języka Python
description: W tym artykule opisano sposób tworzenia rozszerzenia języka C++ dla języka Python przy użyciu języków Visual Studio, CPython i PyBind11, w tym debugowania w trybie mieszanym.
ms.date: 05/11/2021
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: ce80ab6647ffc1043bcc452c387abcbdb80a2def
ms.sourcegitcommit: 162be102d2c22a1c4ad2c447685abd28e0e85d15
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2021
ms.locfileid: "109973443"
---
# <a name="create-a-c-extension-for-python"></a>Tworzenie rozszerzenia C++ dla języka Python

Moduły napisane w języku C++ (lub C) są często używane do rozszerzania możliwości interpretera języka Python. Są one również używane w celu umożliwienia dostępu do funkcji systemu operacyjnego niskiego poziomu. 

Moduły są dostępne w trzech typach podstawowych:

- **Moduły** akceleratora: Ponieważ Python jest językiem interpretowanych, można pisać moduły akceleratora w języku C++, aby uzyskać wyższą wydajność.
- **Moduły otoki:** te moduły uwidoczniają istniejące interfejsy C/C++ kodowi języka Python lub uwidoczniają bardziej "pythonowy" interfejs API, który jest łatwy w użyciu z języka Python.
- **Moduły dostępu do systemu niskiego poziomu:** możesz utworzyć te moduły, aby uzyskać dostęp do funkcji niższego poziomu środowiska uruchomieniowego, systemu operacyjnego `CPython` lub podstawowego sprzętu.

W tym artykule o mowa o budowania modułu rozszerzenia języka C++, który oblicza `CPython` tangens hiperboliczny i wywołuje go z kodu w języku Python. Procedura jest implementowane najpierw w języku Python w celu zademonstrowania względnego przyrostu wydajności implementacji tej samej procedury w języku C++.

W tym artykule pokazano również dwa sposoby, aby udostępnić rozszerzenie C++ dla języka Python:

- Użyj `CPython` standardowych rozszerzeń zgodnie z opisem w [dokumentacji języka Python.](https://docs.python.org/3/c-api/)
- Użyj [PyBind11,](https://github.com/pybind/pybind11)zalecanego dla języka C++11 ze względu na jego prostotę.

Ukończony przykład z tego przewodnika można znaleźć w witrynie GitHub na stronie [python-samples-vs-cpp-extension](https://github.com/Microsoft/python-sample-vs-cpp-extension).

## <a name="prerequisites"></a>Wymagania wstępne

- Visual Studio 2017 lub nowszym z zainstalowanym obciążeniem Programowanie w języku Python. Obciążenie obejmuje natywne narzędzia programskie języka Python, które obejmują obciążenie języka C++ i zestawy narzędzi, które są niezbędne dla rozszerzeń natywnych.

    ![Zrzut ekranu przedstawiający listę opcji programowania w języku Python z wyróżnioną opcją Natywne narzędzia programskie języka Python.](media/cpp-install-native.png)

    > [!NOTE]
    > Podczas instalowania obciążenia Aplikacje do analizy i **przetwarzania** danych język Python i natywne narzędzia programistyczne języka **Python** są instalowane domyślnie.

Aby uzyskać więcej informacji na temat opcji instalacji, zobacz [Instalowanie obsługi języka Python dla Visual Studio](installing-python-support-in-visual-studio.md). Jeśli język Python jest instalowany oddzielnie, pamiętaj, aby wybrać pozycję Pobierz symbole **debugowania** w obszarze **Opcje zaawansowane** w jego instalatorze. Ta opcja jest wymagana, aby można było używać debugowania w trybie mieszanym między kodem w języku Python a kodem natywnym.

## <a name="create-the-python-application"></a>Tworzenie aplikacji w języku Python

1. Utwórz nowy projekt języka Python w programie Visual Studio wybierając **pozycję File** New Project  >  **(Plik nowy**  >  **projekt).** Wyszukaj język **Python,** wybierz szablon **Aplikacja języka Python,** wprowadź nazwę i lokalizację, a następnie wybierz przycisk **OK.**

1. W pliku *PY projektu* wklej następujący kod. Aby wypróbować niektóre funkcje [edytowania języka Python,](editing-python-code-in-visual-studio.md)spróbuj wprowadzić kod ręcznie.  

   Ten kod oblicza tangens hiperboliczny bez użycia biblioteki matematycznej i będzie przyspieszać działanie przy użyciu rozszerzeń natywnych.

    > [!Tip]
    > Napisz kod w czystym języku Python, zanim napiszesz go ponownie w języku C++. Dzięki temu można łatwiej sprawdzić, czy kod natywny jest poprawny.

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

1. Aby wyświetlić wyniki, uruchom program, wybierając pozycję **Rozpocznij**  >  **debugowanie bez** debugowania lub naciskając klawisze Ctrl+F5. 

   Zmienną można `COUNT` dostosować, aby zmienić czas uruchamiania testu porównawczego. Na potrzeby tego przewodnika ustaw liczbę tak, aby test porównawczy potrwał około dwóch sekund.

   > [!TIP]
   > Podczas uruchamiania testów porównawczych zawsze używaj polecenia **Rozpocznij**  >  **debugowanie bez debugowania.** Pozwala to uniknąć narzutów, które są naliczane podczas uruchamiania kodu w Visual Studio debugerze.

## <a name="create-the-core-c-projects"></a>Tworzenie podstawowych projektów C++

Postępuj zgodnie z instrukcjami w tej sekcji, aby utworzyć dwa identyczne projekty języka C++: *superfastcode* i *superfastcode2.* Później użyjesz oddzielnego podejścia w każdym projekcie, aby uwidocznić kod C++ w języku Python.

1. W **Eksplorator rozwiązań** kliknij rozwiązanie prawym przyciskiem myszy, a następnie wybierz **pozycję Dodaj** nowy  >  **projekt.** Rozwiązanie Visual Studio może zawierać projekty języków Python i C++, co jest jedną z zalet używania języka Visual Studio python.

1. Wyszukaj w **języku C++,** wybierz pozycję Pusty **projekt,** określ **superfastcode** dla pierwszego projektu lub **superfastcode2** dla drugiego projektu, a następnie wybierz **przycisk OK**.

    > [!Tip]
    > Alternatywnie, po zainstalowaniu natywnych narzędzi programist Visual Studio Python w języku Visual Studio, możesz rozpocząć od szablonu modułu rozszerzenia języka Python. Szablon zawiera już większość opisanych tutaj czynności. 
    > 
    > Jednak w tym przewodniku rozpoczęcie od pustego projektu demonstruje krok po kroku tworzenie modułu rozszerzenia. Po zrozumieniu tego procesu możesz użyć szablonu, aby zaoszczędzić czas podczas pisania własnych rozszerzeń.

1. Aby utworzyć plik C++ w nowym projekcie, kliknij prawym przyciskiem myszy węzeł **Pliki źródłowe,** a następnie wybierz pozycję   >  **Dodaj nowy element**.

1. Wybierz **pozycję Plik C++,** nadaj jej nazwę *module.cpp,* a następnie wybierz przycisk **OK.**

    > [!Important]
    > Plik z *rozszerzeniem CPP* jest niezbędny, aby włączyć strony właściwości języka C++ w poniższych krokach.

1. Na głównym pasku narzędzi użyj menu rozwijanego, aby wykonać jedną z następujących czynności:

   * W przypadku 64-bitowego środowiska uruchomieniowego języka Python aktywuj **konfigurację x64.** 
   * W przypadku 32-bitowego środowiska uruchomieniowego języka Python aktywuj **konfigurację systemu Win32.**

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy projekt C++, wybierz pozycję **Właściwości**, a następnie wykonaj następujące czynności: 

   a. W **przypadku opcji Konfiguracja** wprowadź wartość Active **(Debuguj)**.  
   b. W **przypadku** opcji Platforma wprowadź wartość **Aktywna (x64)** lub **Aktywna (Win32)** w zależności od wyboru w poprzednim kroku.

    > [!NOTE]
    > Podczas tworzenia własnych projektów należy skonfigurować konfiguracje  debugowania *i wydania.* W tej jednostce skonfigurujesz tylko konfigurację debugowania i skonfigurujesz ją tak, aby używać kompilacji wydania języka CPython. Ta konfiguracja wyłącza niektóre funkcje debugowania środowiska uruchomieniowego języka C++, w tym asercji. Używanie plików binarnych debugowania CPython *(python_d.exe*) wymaga różnych ustawień.

1. Ustaw właściwości zgodnie z opisem w poniższej tabeli:

    ::: moniker range=">=vs-2019"

    | Tab | Właściwość | Wartość |
    | --- | --- | --- |
    | **Ogólne** | **Nazwa obiektu docelowego** | Określ nazwę modułu, aby odwoływać się do niego z języka Python w `from...import` instrukcjach. Tej samej nazwy używa się w kodzie języka C++ podczas definiowania modułu dla języka Python. Aby użyć nazwy projektu jako nazwy modułu, pozostaw wartość domyślną **$\<ProjectName>** .  W `python_d.exe` przypadku pliku dodaj na końcu `_d` nazwy. |
    | | **Typ konfiguracji** | **Biblioteka dynamiczna (dll)** |
    | | **Zaawansowane** > **Rozszerzenie pliku docelowego** | **.pyd** |
    | | **Project Defaults (Ustawienia domyślne projektu)** > **Typ konfiguracji** | **Biblioteka dynamiczna (dll)** |
    | **C/C++** > **Ogólne** | **Dodatkowe katalogi dołączania** | Dodaj folder *dołączania języka* Python zgodnie z potrzebami instalacji (na przykład `c:\Python36\include` ).  |
    | **C/C++** > **Preprocesor** | **Definicje preprocesora** | Jeśli jest obecna, zmień wartość **_DEBUG** na **NDEBUG,** aby była dopasowana do wersji CPython bez debugowania. Jeśli używasz usługi *python_d.exe*, pozostaw tę wartość bez zmian. |
    | **C/C++** > **Generowanie kodu** | **Biblioteka środowiska uruchomieniowego** | **Wielowątkowa biblioteka DLL (/MD)** do dopasowania wersji CPython bez debugowania. Jeśli używasz biblioteki *python_d.exe*, pozostaw tę wartość jako wielowątkową bibliotekę **DLL debugowania (/MDd).** |
    | **Linker** > **Ogólne** | **Dodatkowe katalogi biblioteki** | Dodaj folder *libs języka* Python zawierający *pliki .lib* zgodnie z potrzebami instalacji (na przykład *c:\Python36\libs).* Pamiętaj, aby wskazać folder *libs* zawierający pliki  *.lib,* a nie folder *Lib* zawierający *pliki PY.* |
    | | |

    ::: moniker-end

    ::: moniker range="=vs-2017"

    | Tab | Właściwość | Wartość |
    | --- | --- | --- |
    | **Ogólne** | **Ogólne** > **Nazwa obiektu docelowego** | Określ nazwę modułu, aby odwołać się do niego z języka Python w `from...import` instrukcjach . Tej samej nazwy używa się w kodzie języka C++ podczas definiowania modułu dla języka Python. Aby użyć nazwy projektu jako nazwy modułu, pozostaw wartość domyślną **$\<ProjectName>** . W `python_d.exe` przypadku nazwy dodaj na końcu nazwy `_d` . |
    | | **Ogólne** > **Rozszerzenie docelowe** | **.pyd** |
    | | **Project Defaults (Ustawienia domyślne projektu)** > **Typ konfiguracji** | **Biblioteka dynamiczna (dll)** |
    | **C/C++** > **Ogólne** | **Dodatkowe katalogi dołączania** | Dodaj folder *dołączania języka* Python zgodnie z potrzebami instalacji (na przykład *c:\Python36\include*).  |
    | **C/C++** > **Preprocesor** | **Definicje preprocesora** | Jeśli jest obecna, zmień wartość **_DEBUG** na **NDEBUG,** aby była dopasowana do wersji nieedytowania programu `CPython` . W przypadku korzystania z funkcji `python_d.exe` pozostaw tę wartość bez zmian. |
    | **C/C++** > **Generowanie kodu** | **Biblioteka środowiska uruchomieniowego** | **Biblioteka DLL wielowątkowa (/MD)** do dopasowania do wersji pliku bez `CPython` debugowania. W przypadku korzystania z funkcji `python_d.exe` pozostaw tę wartość bez zmian. |
    | **Linker** > **Ogólne** | **Dodatkowe katalogi biblioteki** | Dodaj folder *libs języka* Python zawierający *pliki .lib* zgodnie z potrzebami instalacji (na przykład *c:\Python36\libs).* Pamiętaj, aby wskazać folder *libs* zawierający pliki  *lib,* a nie folder *Lib* zawierający *pliki py.* |
    | | |

    ::: moniker-end
    
    > [!NOTE]
    > Jeśli karta **C/C++** nie jest wyświetlana we właściwościach projektu, projekt nie zawiera żadnych plików, które identyfikuje jako pliki źródłowe C/C++. Ten warunek może wystąpić, jeśli utworzysz plik źródłowy bez rozszerzenia *pliku c* *lub cpp.* 
    > 
    > Jeśli na przykład przypadkowo wprowadzono plik *module.coo* zamiast *module.cpp* wcześniej w oknie dialogowym nowego elementu, program Visual Studio utworzy plik, ale nie ustawi typu pliku na *kod C/C+,* który aktywuje kartę właściwości C/C++. Taka błędnaidentyfikacja pozostaje bezbłędna nawet w przypadku zmiany nazwy pliku na *rozszerzenie cpp.* 
    > 
    > Aby prawidłowo ustawić typ pliku, w **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy plik i wybierz polecenie **Właściwości.** Następnie dla **opcji Typ pliku** wybierz pozycję Kod **C/C++.**

1. Wybierz przycisk **OK**.

1. Aby przetestować konfiguracje (zarówno *debugowanie,* jak *i wydanie),* kliknij prawym przyciskiem myszy projekt C++, a następnie wybierz polecenie **Build (Skompilowanie).** 

   Pliki *pyd* znajdziesz w *folderze* rozwiązania w obszarze *Debugowanie* i *wydanie,* a nie w samym folderze projektu języka C++.

1. W pliku *module.cpp* projektu języka C++ dodaj następujący kod:

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

1. Skompilować ponownie projekt C++, aby potwierdzić, że kod jest poprawny.

1. Jeśli jeszcze tego nie zrobiono, powtórz poprzednie kroki, aby utworzyć drugi projekt o nazwie *superfastcode2* z identyczną konfiguracją.

## <a name="convert-the-c-projects-to-extensions-for-python"></a>Konwertowanie projektów języka C++ na rozszerzenia dla języka Python

Aby uczynić bibliotekę DLL języka C++ rozszerzeniem dla języka Python, należy najpierw zmodyfikować wyeksportowane metody w celu interakcji z typami języka Python. Następnie dodasz funkcję, która eksportuje moduł wraz z definicjami metod modułu.

W kolejnych sekcjach wyjaśniono, jak wykonać te kroki przy użyciu rozszerzeń CPython i PyBind11.

### <a name="use-cpython-extensions"></a>Korzystanie z rozszerzeń CPython

Aby uzyskać więcej informacji na temat kodu pokazanego w tej sekcji, zobacz podręcznik interfejsu API języka [Python/języka C,](https://docs.python.org/3/c-api/index.html) a zwłaszcza stronę [Obiekty](https://docs.python.org/3/c-api/module.html) modułu. Pamiętaj, aby wybrać swoją wersję języka Python z listy rozwijanej w prawym górnym rogu.

1. W górnej części pliku *module.cpp* dołącz *python.h:*

    ```cpp
    #include <Python.h>
    ```

1. `tanh_impl`Zmodyfikuj metodę , aby akceptowała i zwracała typy języka Python (czyli `PyObject*` :

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

1. Dodaj strukturę definiującą moduł tak, jak chcesz odwoływać się do niego w kodzie języka Python, szczególnie w przypadku używania `from...import` instrukcji . 

   Nazwa importowana w tym kodzie powinna odpowiadać wartości we właściwościach projektu w obszarze Właściwości konfiguracji  >  **Ogólna**  >  **nazwa docelowa**. 

   W poniższym przykładzie nazwa modułu oznacza, że można jej używać w języku `"superfastcode"` `from superfastcode import fast_tanh` Python, ponieważ jest `fast_tanh` zdefiniowana w pliku `superfastcode_methods` . Nazwy plików, które są wewnętrzne dla projektu języka C++, takie jak *module.cpp,* są niesekwencjonalne.

    ```cpp
    static PyModuleDef superfastcode_module = {
        PyModuleDef_HEAD_INIT,
        "superfastcode",                        // Module name to use with Python import statements
        "Provides some functions, but faster",  // Module description
        0,
        superfastcode_methods                   // Structure that defines the methods of the module
    };
    ```

1. Dodaj metodę, którą język Python wywołuje podczas ładowania modułu, który musi mieć nazwę , gdzie dokładnie odpowiada właściwości General Target Name projektu `PyInit_<module-name>` *\<module-name>*   >   C++. Oznacza to, że pasuje do nazwy pliku *pyd,* który jest budowany przez projekt.

    ```cpp
    PyMODINIT_FUNC PyInit_superfastcode() {
        return PyModule_Create(&superfastcode_module);
    }
    ```

1. Skompilowanie projektu języka C++ ponownie w celu zweryfikowania kodu. Jeśli wystąpią błędy, zobacz [sekcję "Rozwiązywanie](#troubleshoot-compiling-failures) problemów".

### <a name="use-pybind11"></a>Korzystanie z PyBind11

Jeśli zostały wykonane kroki opisane w poprzedniej sekcji, na pewno zauważono, że do utworzenia struktur modułów niezbędnych dla kodu C++ używano wielu kodów. PyBind11 upraszcza proces za pomocą makr w pliku nagłówkowym języka C++, które osiągną ten sam wynik, ale przy znacznie mniejszym kodzie. 

Aby uzyskać więcej informacji na temat kodu w tej sekcji, zobacz [PyBind11 basics (Podstawy PyBind11).](https://github.com/pybind/pybind11/blob/master/docs/basics.rst)

1. Zainstaluj pakiet PyBind11 przy użyciu narzędzia pip: `pip install pybind11` lub `py -m pip install pybind11` . 

   Alternatywnie możesz zainstalować pakiet PyBind11 przy użyciu okna Środowiska Python, a następnie użyć polecenia Otwórz w programie **PowerShell** w następnym kroku.

1. W tym samym terminalu uruchom lub `python -m pybind11 --includes` `py -m pybind11 --includes` . 

   Zostanie wyświetlona lista ścieżek, które należy dodać do właściwości Ogólne dodatkowe katalogi dołączania **C/C++**  >    >  **projektu.** Pamiętaj, aby usunąć `-I` prefiks , jeśli jest obecny.

1. W górnej części nowego modułu *module.cpp,* który nie zawiera żadnych zmian z poprzedniej sekcji, uwzględnij *pybind11.h:*

    ```cpp
    #include <pybind11/pybind11.h>
    ```

1. W dolnej części *modułu module.cpp* użyj makra , aby zdefiniować `PYBIND11_MODULE` punkt wejścia do funkcji języka C++:

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

1. Skompilowanie projektu języka C++ w celu zweryfikowania kodu. Jeśli wystąpią błędy, zobacz następną sekcję "Rozwiązywanie problemów z błędami kompilowania" dla rozwiązań.

### <a name="troubleshoot-compiling-failures"></a>Rozwiązywanie problemów z błędami kompilowania

Kompilacja modułu C++ może się nie powieść z następujących powodów:

- Błąd: Nie można zlokalizować pliku *Python.h* (**E1696:** nie można open source pliku "Python.h" i/lub C1083: Nie można otworzyć pliku **dołączania: "Python.h":** Brak takiego pliku lub katalogu ) 

  Rozwiązanie: Sprawdź, czy ścieżka w ogólnych katalogach dodatkowych dołączania w języku **C/C++** we właściwościach projektu wskazuje folder  >    >   include *instalacji języka* Python. Zobacz krok 6 w [obszarze Tworzenie podstawowego projektu C++.](#create-the-core-c-projects)

- Błąd: Nie można zlokalizować bibliotek języka Python 
 
   Rozwiązanie: Sprawdź, czy ścieżka w ogólnych katalogach biblioteki dodatkowej programu **Linker** we właściwościach projektu wskazuje  >    >   folder *libs instalacji języka* Python. Zobacz krok 6 w [obszarze Tworzenie podstawowego projektu C++.](#create-the-core-c-projects)

- Błędy łączenia związane z architekturą docelową
   
   Rozwiązanie: Zmień architekturę projektu obiektu docelowego języka C++, aby dopasować architekturę instalacji języka Python. Jeśli na przykład aplikacja jest ukierunkowana na win32 w projekcie języka C++, ale instalacja języka Python jest 64-bitowa, zmień projekt C++ na x64.

## <a name="test-the-code-and-compare-the-results"></a>Testowanie kodu i porównywanie wyników

Teraz, gdy masz biblioteki DLL ustrukturyzowane jako rozszerzenia języka Python, możesz odwoływać się do nich z projektu języka Python, importować moduły i używać ich metod.

### <a name="make-the-dll-available-to-python"></a>Udostępnij bibliotekę DLL językowi Python

Bibliotekę DLL można udostępnić językowi Python na kilka sposobów. Poniżej podano dwa podejścia, które należy wziąć pod uwagę: 

* Ta pierwsza metoda działa, jeśli projekt języka Python i projekt języka C++ znajdują się w tym samym rozwiązaniu. Wykonaj następujące czynności: 

   1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy węzeł **Odwołania** w projekcie języka Python, a następnie wybierz pozycję **Dodaj odwołanie**. 
   1. W wyświetlonym oknie dialogowym wybierz **kartę Projekty,** wybierz projekty **superfastcode** i **superfastcode2,** a następnie wybierz przycisk **OK.**

      ![Zrzut ekranu przedstawiający sposób dodawania odwołania do projektu "superfastcode".](media/cpp-add-reference.png)

* Alternatywna metoda instaluje moduł w środowisku języka Python, dzięki czemu moduł jest również dostępny dla innych projektów języka Python. Aby uzyskać więcej informacji, zobacz [ **dokumentację projektu setuptools**](https://setuptools.readthedocs.io/). Wykonaj następujące czynności:

    1. Utwórz plik o *nazwie setup.py* w projekcie języka C++, klikając projekt prawym przyciskiem myszy i wybierając **polecenie Dodaj** nowy  >  **element**. 
    
    1. Wybierz **pozycję Plik C++ (cpp),** nadaj plikowi *nazwę setup.py*, a następnie wybierz przycisk **OK.**
    
       Nazewnictwo pliku za pomocą rozszerzenia *PY* sprawia, że Visual Studio rozpoznają go jako plik w języku Python pomimo użycia szablonu pliku C++. 

       Gdy plik pojawi się w edytorze, wklej do niego następujący kod, zgodnie z metodą rozszerzenia:
    
        **Dla `CPython` rozszerzeń (projekt superfastcode):**
    
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
    
        **Dla `PyBind11` (projekt superfastcode2)**:
    
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
    
    1. Utwórz drugi plik o *nazwie pyproject.toml* w projekcie języka C++ i wklej do niego następujący kod:
    
        ```toml
        [build-system]
        requires = ["setuptools", "wheel", "pybind11"]
        build-backend = "setuptools.build_meta"
        ```
    
    1. Aby skompilować rozszerzenie, kliknij prawym przyciskiem myszy kartę *pyproject.toml,* a następnie wybierz polecenie **Kopiuj pełną ścieżkę.** Przed jej użyciem usuniesz nazwę *pyproject.toml* ze ścieżki.
    
    1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy aktywne środowisko języka Python, a następnie wybierz pozycję **Zarządzaj pakietami języka Python.**
    
        > [!Tip]
        > Jeśli pakiet został już zainstalowany, zobaczysz go tutaj. Przed kontynuowaniem kliknij przycisk **X,** aby go odinstalować.
    
    1. W polu wyszukiwania wklej skopiowaną ścieżkę, usuń plik *pyproject.toml* na końcu, a następnie naciśnij klawisz Enter, aby zainstalować moduł z tego katalogu.
    
        > [!Tip]
        > Jeśli instalacja nie powiedzie się z powodu błędu uprawnień, dodaj *pozycję --user* na końcu i spróbuj ponownie wykonać polecenie.


### <a name="call-the-dll-from-python"></a>Wywołanie biblioteki DLL z języka Python

Po udostępnionej bibliotece DLL dla języka Python zgodnie z opisem w poprzedniej sekcji możesz wywołać funkcje i z kodu języka Python i porównać ich wydajność z implementacją `superfastcode.fast_tanh` `superfastcode2.fast_tanh2` języka Python. Aby wywołać bibliotekę DLL, wykonaj następujące czynności:

1. Dodaj następujące wiersze w pliku *py,* aby wywołać metody wyeksportowane z bibliotek DLL i wyświetlić ich dane wyjściowe:

    ```python
    from superfastcode import fast_tanh
    test(lambda d: [fast_tanh(x) for x in d], '[fast_tanh(x) for x in d] (CPython C++ extension)')

    from superfastcode2 import fast_tanh2
    test(lambda d: [fast_tanh2(x) for x in d], '[fast_tanh2(x) for x in d] (PyBind11 C++ extension)')
    ```

1. Uruchom program w języku Python, wybierając pozycję **Rozpocznij**  >  **debugowanie bez** debugowania lub naciskając klawisze Ctrl+F5.

    > [!NOTE]
    > Jeśli polecenie **Uruchom bez debugowania** jest wyłączone, w Eksplorator rozwiązań **kliknij** prawym przyciskiem myszy projekt języka Python, a następnie wybierz pozycję Ustaw jako **projekt startowy.**  

    Zauważ, że procedury języka C++ są uruchamiane około pięć do dwudziestu razy szybciej niż implementacja języka Python. Typowe dane wyjściowe są wyświetlane w następujący sposób:

    ```output
    Running benchmarks with COUNT = 500000
    [tanh(x) for x in d] (Python implementation) took 0.758 seconds

    [fast_tanh(x) for x in d] (CPython C++ extension) took 0.076 seconds

    [fast_tanh2(x) for x in d] (PyBind11 C++ extension) took 0.204 seconds
    ```

1. Spróbuj zwiększyć `COUNT` zmienną, aby różnice były bardziej wymawiane. 

    Kompilacja *debugowania* modułu C++ działa  również wolniej niż kompilacja wydania, ponieważ kompilacja debugowania jest mniej zoptymalizowana i zawiera różne kontrole błędów. Możesz przełączać się między tymi konfiguracjami w celu porównania, ale pamiętaj, aby wrócić i zaktualizować właściwości ustawione wcześniej dla konfiguracji wydania.

W danych wyjściowych może się okazać, że rozszerzenie PyBind11 nie jest tak szybkie jak rozszerzenie CPython, chociaż powinno być znacznie szybsze niż implementacja czystego języka Python. Ta różnica wynika głównie z tego, że używaliśmy wywołania , które nie obsługuje wielu parametrów, nazw parametrów `METH_O` ani argumentów słów kluczowych. PyBind11 generuje nieco bardziej złożony kod, aby zapewnić wywołującym interfejs podobny do języka Python. Jednak ponieważ kod testowy wywołuje funkcję 500 000 razy, wyniki mogą znacznie zwiększyć ten narzut!

Możesz jeszcze bardziej zmniejszyć obciążenie, przenosząc `for` pętlę do kodu natywnego. Takie podejście wymagałoby użycia [protokołu iteratora](https://docs.python.org/c-api/iter.html) (lub typu PyBind11 dla parametru funkcji ) do `py::iterable` przetwarzania każdego elementu. [](https://pybind11.readthedocs.io/en/stable/advanced/functions.html#python-objects-as-args) Usuwanie powtarzających się przejść między językami Python i C++ jest efektywnym sposobem skrócenia czasu przetwarzania sekwencji.

### <a name="troubleshoot-importing-errors"></a>Rozwiązywanie problemów z błędami importowania

Jeśli podczas próby zaimportowania modułu zostanie wyświetlony komunikat, możesz rozwiązać go w `ImportError` jeden z następujących sposobów:

* Podczas tworzenia za pomocą odwołania do projektu upewnij się, że właściwości projektu C++ są zgodne ze  środowiskiem języka Python aktywowanym dla projektu języka Python, szczególnie katalogami Dołączanie i Biblioteka. 

* Upewnij się, że plik wyjściowy ma nazwę *superfastcode.pyd.* Wszelkie inne nazwy lub rozszerzenia uniemożliwią jego zaimportowanie.

* Jeśli moduł został zainstalowany przy użyciu pliku *setup.py,* upewnij się, że uruchomiono polecenie *pip* w środowisku języka Python aktywowanym dla projektu języka Python. Rozszerzenie środowiska Języka Python w Eksplorator rozwiązań powinno wyświetlić wpis dla *superszyfrowania*.

## <a name="debug-the-c-code"></a>Debugowanie kodu C++

Visual Studio obsługuje debugowanie kodu w językach Python i C++. W tej sekcji ominiesz proces przy użyciu *projektu superfastcode.* Proces jest taki sam dla projektu *superfastcode2.*

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy projekt języka Python, wybierz pozycję **Właściwości,** wybierz kartę **Debugowanie,** a następnie wybierz opcję **Debuguj** Włącz debugowanie kodu  >  **natywnego.**

    > [!Tip]
    > Po włączeniu debugowania kodu natywnego okno danych wyjściowych języka Python może zostać zamknięte natychmiast po zakończeniu działania programu bez podania zwykłego klawisza Naciśnij dowolny klawisz, aby kontynuować wstrzymywanie.  
    >
    > Rozwiązanie: Aby wymusić wstrzymanie po włączeniu debugowania kodu natywnego, dodaj opcję do pola Uruchom argumenty `-i`   >  **interpretera** na **karcie Debugowanie.** Ten argument wprowadza interpreter języka Python w tryb interaktywny po uruchomieniu kodu. W tym momencie czeka na wybranie kombinacji klawiszy Ctrl+Z, a następnie klawisz Enter w celu zamknięcia okna. 
    >
    > Alternatywnie, jeśli nie przeszkadza Ci modyfikowanie kodu w języku Python, możesz dodać instrukcje i na `import os` `os.system("pause")` końcu programu. Ten kod duplikuje oryginalny monit o wstrzymanie.

1. Wybierz **pozycję Zapisz**  >  **plik,** aby zapisać zmiany właściwości.

1. Na Visual Studio narzędziu ustaw konfigurację kompilacji na **debugowanie.**

    ![Zrzut ekranu przedstawiający ustawienie "Debuguj" na pasku Visual Studio narzędzi.](media/cpp-set-debug.png)

1. Ponieważ uruchamianie kodu w debugerze trwa dłużej, można zmienić zmienną w pliku py na wartość, która jest około pięć razy mniejsza niż wartość `COUNT` domyślna.  Na przykład zmień go z **5000000 na** **100000.**

1. W kodzie języka C++ ustaw punkt przerwania w pierwszym wierszu metody, a następnie uruchom `tanh_impl` debuger, wybierając **klawisz F5** lub **rozpocznij**  >  **debugowanie.** 

    Debuger zatrzymuje się po wywołaniu kodu punktu przerwania. Jeśli punkt przerwania nie zostanie trafiony, upewnij się, że konfiguracja jest ustawiona na **debugowanie** i że projekt został zapisany, co nie odbywa się automatycznie po uruchomieniu debugera.

    ![Zrzut ekranu przedstawiający kod języka C++, który zawiera punkt przerwania.](media/cpp-debugging.png)

1. W punkcie przerwania możesz przejść przez kod C++, zbadać zmienne i tak dalej. Aby uzyskać więcej informacji na temat tych funkcji, zobacz [Debugowanie języka Python i języka C++ razem](debugging-mixed-mode-c-cpp-python-in-visual-studio.md).

## <a name="alternative-approaches"></a>Alternatywne podejścia

Rozszerzenia języka Python można tworzyć na różne sposoby, zgodnie z opisem w poniższej tabeli. Pierwsze dwa wiersze, `CPython` i , zostały omówione w tym `PyBind11` artykule.

| Podejście | Vintage | Reprezentatywni użytkownicy | 
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
| [cppyy](https://cppyy.readthedocs.io/) | 2017 | |

## <a name="see-also"></a>Zobacz też

Ukończony przykład z tego przewodnika można znaleźć w witrynie GitHub na stronie [python-samples-vs-cpp-extension](https://github.com/Microsoft/python-sample-vs-cpp-extension).

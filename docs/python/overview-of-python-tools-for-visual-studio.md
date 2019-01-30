---
title: Obsługa języka Python w programie Visual Studio na Windows
titleSuffix: ''
description: Podsumowanie funkcji języka Python w programie Visual Studio, dzięki czemu najlepsze środowisko IDE języka Python na Windows (znany także jako narzędzi Python Tools for Visual Studio, PTVS).
ms.date: 11/19/2018
ms.prod: visual-studio-dev15
ms.topic: overview
author: kraigb
ms.author: kraigb
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 699578e564999db55562abaad764cde80fc8b618
ms.sourcegitcommit: a916ce1eec19d49f060146f7dd5b65f3925158dd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2019
ms.locfileid: "55232068"
---
# <a name="work-with-python-in-visual-studio-on-windows"></a>Praca z językiem Python w programie Visual Studio na Windows

Język Python jest popularnych języków programowania, które jest niezawodne, elastyczne, można łatwo dowiedzieć się, bezpłatnie do użycia we wszystkich systemach operacyjnych i obsługiwane przez społeczność deweloperów silne i wielu bezpłatnych bibliotek. Python obsługuje wszystkich sposobów rozwoju, w tym aplikacje sieci web, usług sieci web, aplikacje klasyczne, skryptów i obliczeń naukowych i jest używany przez wiele uniwersytety, analitykom, zwykłych deweloperów i podobne profesjonalnych deweloperów. Temat można znaleźć więcej informacji na temat języka na [python.org](https://www.python.org) i [języka Python dla początkujących](https://www.python.org/about/gettingstarted/).

Visual Studio to zaawansowane środowisko IDE języka Python na Windows. Program Visual Studio udostępnia [typu open-source](https://github.com/Microsoft/ptvs) obsługę języka Python za pomocą **programowania w języku Python** i **do nauki o danych** obciążeń (Visual Studio 2017) i bezpłatna Narzędzia Python Tools for Visual Studio rozszerzenia (Visual Studio 2015 i starsze).

Python nie jest obecnie obsługiwana w programie Visual Studio dla komputerów Mac, ale jest dostępna na komputerach Mac i Linux za pomocą programu Visual Studio Code (zobacz [pytań i odpowiedzi](#questions-and-answers)).

Aby rozpocząć pracę:

- Postępuj zgodnie z [instrukcje dotyczące instalacji](installing-python-support-in-visual-studio.md) skonfigurować obciążenie języka Python.
- Zapoznaj się z możliwościami Python programu Visual Studio za pomocą sekcji w niniejszym artykule. Możesz również [Obejrzyj serię wideo (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121) wprowadzenie do języka Python w programie Visual Studio (łączna liczba minut 22).
- Przechodzą przez co najmniej jeden z przewodników Szybki Start, aby utworzyć projekt. Jeśli wiesz, skorzystaj z [tworzenie aplikacji sieci web za pomocą Flask](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json).
- Postępuj zgodnie z [działał z językiem Python w programie Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md) samouczek dotyczący środowiska pełnej end-to-end.

## <a name="support-for-multiple-interpreters"></a>Obsługa wielu interpretery

Visual Studio **środowiska Python** okna (w widoku szerokie, rozwinięty pokazana poniżej) zapewnia jednego miejsca, aby zarządzać wszystkimi globalne środowiska Python, środowisk conda i środowisk wirtualnych. Visual Studio automatycznie wykrywa instalacje języka Python w lokalizacjach i pozwala na skonfigurowanie instalacje niestandardowe. Z każdym środowiskiem może łatwo zarządzania pakietami, Otwórz okno interaktywne dla danego środowiska i dostęp do folderów środowiska.

![Rozwinięty widok okna środowiska Python](media/environments-expanded-view.png)

Użyj **Otwórz okno interaktywne** polecenie, aby uruchomić interaktywnie języka Python, w ramach programu Visual Studio. Użyj **Otwórz w programie PowerShell** polecenie, aby otworzyć okno oddzielne polecenia w folderze wybranego środowiska. Z tego okna polecenia skrypt można uruchomić dowolnego języka python.

Informacje dodatkowe:

- Wideo (2 mln 35s): [Zarządzanie środowiskami Python](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=qrDmN4LWE_8305918567)
- Dokumentacja: [Zarządzanie środowiskami Python](managing-python-environments-in-visual-studio.md)
- Dokumentacja: [Dokumentacja środowiska Python](python-environments-window-tab-reference.md)

## <a name="rich-editing-intellisense-and-code-comprehension"></a>Zaawansowane edytowanie, IntelliSense i zrozumienie kodu

Program Visual Studio zapewnia najwyższej klasy Edytor języka Python obejmujący kolorowanie składni, automatyczne uzupełnianie kodu i bibliotek, formatowanie pomocy dotyczącej sygnatur, refaktoryzacji, Zaznaczanie błędów i wskazówek dotyczących typów kodu. Visual Studio udostępnia również unikatowych funkcji, takich jak Widok klas **przejdź do definicji**, **Znajdź wszystkie odwołania**i fragmenty kodu. Bezpośrednia Integracja z [okna interaktywnego](#interactive-window) ułatwia szybkie tworzenie kodu w języku Python, który już został zapisany w pliku.

![Uzupełnianie kodu dla kodu w języku Python w programie Visual Studio](media/code-editing-completions-simple.png)

Informacje dodatkowe:

- Wideo (2 mln 30 sekund): [Edytowanie kodu w języku Python](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=r2iQH5LWE_4605918567)
- Dokumentacja: [Edytowanie kodu w języku Python](editing-python-code-in-visual-studio.md)
- Dokumentacja: [Formatowanie kodu](formatting-python-code.md)
- Dokumentacja: [Refaktoryzacja kodu](refactoring-python-code.md)
- Dokumentacja: [Użyj linter](linting-python-code.md)
- Dokumentacja funkcji ogólne Visual Studio: [Funkcje edytora kodu](../ide/writing-code-in-the-code-and-text-editor.md)

## <a name="interactive-window"></a>Okno interaktywne

Dla każdego środowiska Python, wiadomo, że program Visual Studio możesz łatwo otworzyć tego samego środowiska interaktywnego (REPL) dla interpretera języka Python, bezpośrednio z poziomu programu Visual Studio, a nie przy użyciu oddzielnych wiersza polecenia. Można łatwo przełączać się między środowiskami, jak również. (Aby otworzyć osobnym wierszu polecenia, wybierz żądane środowiska w **środowiska Python** okna, następnie wybierz pozycję **Otwórz w programie PowerShell** polecenia jak wyjaśniono wcześniej w [pomocy technicznej dla wielu interpretery](#support-for-multiple-interpreters).)

![Oknie interakcyjnym środowiska Python w programie Visual Studio](media/interactive-window.png)

Visual Studio udostępnia również ścisłą integrację między Edytorem kodu języka Python i **Interactive** okna. **Ctrl**+**Enter** skrót klawiaturowy wygodnie wysyła bieżący wiersz kodu (lub blok kodu) w edytorze **Interactive** spowoduje przesunięcie okna do następnego wiersza (lub blok). **CTRL**+**Enter** pozwala łatwo Przechodź przez kod bez konieczności uruchamiania debugera. Możesz również wysłać zaznaczony kod do **Interactive** okna o takiej samej klawiszy i łatwo wkleić kod z **Interactive** okna do edytora. Razem te funkcje umożliwiają pracę bardziej szczegółowe informacje dla segmentu kodu w **Interactive** okna i łatwo zapisać wyniki w pliku w edytorze.

Program Visual Studio obsługuje również IPython/Jupyter w rozwiązaniu REPL, m.in. wbudowane powierzchnie, .NET i Windows Presentation Foundation (WPF).

Informacje dodatkowe:

- Wideo (2 mln 22s: [Okno interaktywne języka Python](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=gJYKY5LWE_4605918567)
- Dokumentacja: [Okno interaktywne](python-interactive-repl-in-visual-studio.md)
- Dokumentacja: [Program IPython w programie Visual Studio](interactive-repl-ipython.md)

## <a name="project-system-and-project-and-item-templates"></a>System projektów i szablonów projektów i elementów

Program Visual Studio pomaga uprościć projekt wzrostem wraz z upływem czasu. Projekt jest znacznie więcej niż struktury folderów: zawiera omówienie różnych plików są używane i jak powiązane są ze sobą. Program Visual Studio pozwala odróżnić kodu aplikacji, przetestować kod, stron sieci web, JavaScript, skrypty kompilacji i tak dalej, które następnie umożliwiają odpowiednich plików funkcji. Rozwiązania programu Visual Studio ułatwia ponadto zarządzanie wielu powiązanych projektów, takich jak projektu języka Python i rozszerzenie projektu w języku C++.

![Rozwiązania programu Visual Studio zawierający projektów języka C++ i Python](media/projects-solution-explorer-two-projects.png)

Szablony projektów i elementów zautomatyzować proces konfigurowania różnych typów projektów i plików, co cenny czas i zwalniania możesz zarządzać szczegóły skomplikowanych i obarczone ryzykiem błędów. Program Visual Studio udostępnia szablony dla sieci web, Azure, do nauki o danych, konsolę i innych rodzajów projektów, w tym szablony dla plików, takie jak klasy, testy jednostkowe, konfiguracji sieci web platformy Azure, HTML i nawet aplikacji Django języka Python.

[![Szablony projektów i elementów języka Python w programie Visual Studio](media/project-and-item-templates.png)](media/project-and-item-templates.png#lightbox)

Informacje dodatkowe:

- Dokumentacja: [Projekty Python](managing-python-projects-in-visual-studio.md)
- Dokumentacja: [Dokumentacja dotycząca szablonów elementu](python-item-templates.md)
- Dokumentacja: [Szablony projektów języka Python](managing-python-projects-in-visual-studio.md#project-templates)
- Dokumentacja: [Praca z C++ i Python](working-with-c-cpp-python-in-visual-studio.md)
- Dokumentacja funkcji ogólne Visual Studio: [Szablony projektów i elementów](../ide/creating-project-and-item-templates.md#visual-studio-templates)
- Dokumentacja funkcji ogólne Visual Studio: [Rozwiązania i projekty w programie Visual Studio](../ide/solutions-and-projects-in-visual-studio.md)

## <a name="full-featured-debugging"></a>Oferujący debugowania

Jedną z mocnych programu Visual Studio jest jego zaawansowany debuger. Dla języka Python w szczególności program Visual Studio zawiera języków Python/C++ trybu mieszanego debugowanie, zdalne debugowanie w systemie Linux, debugowania w ramach **Interactive** okna i debugowanie testów jednostkowych dla kodu Python.

![Debuger programu Visual Studio dla języka Python, przedstawiający okno podręczne wyjątku](media/debugging-exception-popup.png)

Informacje dodatkowe:

- Wideo: [Debugowanie języka Python 3m 32s](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=Ep5dp5LWE_3805918567)
- Dokumentacja: [Debugowanie języka Python](debugging-python-in-visual-studio.md)
- Dokumentacja: [Debugowanie dla języków Python/C++ w trybie mieszanym](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)
- Dokumentacja: [Zdalne debugowanie w systemie Linux](debugging-python-code-on-remote-linux-machines.md)
- Dokumentacja funkcji ogólne Visual Studio: [Przewodnik po funkcjach debugera programu Visual Studio](../debugger/debugger-feature-tour.md)

## <a name="profiling-tools-with-comprehensive-reporting"></a>Narzędzia profilowania przy użyciu kompleksowe raportowanie

Profilowanie przedstawiono, jak jest zużywany czas w aplikacji. Visual Studio obsługuje profilowanie przy użyciu opartych na CPython interpreterów i z możliwością porównania wydajności między różnych tras profilowania.

[![Visual Studio wyniki profiler dla projektu w języku Python](media/profiling-results.png)](media/profiling-results.png#lightbox)

Informacje dodatkowe:

- Wideo: [Profilowanie Python 3m 00s](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=s6FoC6LWE_1005918567)
- Dokumentacja: [Narzędzia profilowania języka Python](profiling-python-code-in-visual-studio.md)
- Dokumentacja funkcji ogólne Visual Studio: [Przewodnik po funkcjach profilowania](../profiling/profiling-feature-tour.md). (Nie wszystkie funkcje profilowania programu Visual Studio są dostępne dla języka Python).

## <a name="unit-testing-tools"></a>Narzędzia do testowania jednostkowego

Odkryj, uruchamianie i zarządzanie testami w Visual Studio **Eksplorator testów**i łatwo Debuguj testy jednostkowe.

![Profilowanie testu jednostkowego języka Python w programie Visual Studio](media/unit-test-debugging.png)

Informacje dodatkowe:

- Wideo: [Testowanie Python 2 mln 31s](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=hb46k6LWE_405918567)
- Dokumentacja: [Narzędzia do testowania jednostkowego w języku Python](unit-testing-python-in-visual-studio.md)
- Dokumentacja funkcji ogólne Visual Studio: [Kod testu jednostkowego](../test/unit-test-your-code.md).

## <a name="azure-sdk-for-python"></a>Zestaw Azure SDK dla języka Python

Obciążenie języka Python zawiera zestaw Azure SDK dla języka Python, co upraszcza korzystanie usług platformy Azure z aplikacji Windows, Mac OS X i Linux.

Aby uzyskać więcej informacji, zobacz [zestawu Azure SDK dla języka Python](/python/azure/?view=azure-python).

## <a name="python-training-on-microsoft-virtual-academy"></a>Python Szkolenie Microsoft Virtual Academy

|   |   |
|---|---|
| ![Ikona aparatu film wideo](../install/media/video-icon.png "Obejrzyj klip wideo") | <ul><li>[Wprowadzenie do programowania w języku Python](https://mva.microsoft.com/en-US/training-courses/introduction-to-programming-with-python-8360?l=lqhuMxFz_8904984382)</li><li>[Początkujący Python: Ciągi i funkcje](https://mva.microsoft.com/en-US/training-courses/python-beginner-strings-and-functions-18015)</li><li>[Podstawy języka Python: Listy i pętle](https://mva.microsoft.com/en-US/training-courses/python-fundamentals-lists-and-loops-18019)</li><li>[Najczęściej zadawane pytania w języku Python](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121)</li></ul> |

## <a name="questions-and-answers"></a>Pytania i odpowiedzi

**PYTANIA I ODPOWIEDZI. Czy obsługi języka Python w programie Visual Studio dla komputerów Mac?**

A. W tej chwili nie możesz nawet głosować na żądanie, ale [społeczności deweloperów](https://developercommunity.visualstudio.com/content/idea/351820/python-tools-for-visual-studio-mac.html). [Programu Visual Studio dla komputerów Mac](/visualstudio/mac/) dokumentacji identyfikuje bieżące typy programowania, który ją obsługuje. W międzyczasie, Visual Studio Code w Windows, Mac i Linux [dobrze działa z języka Python za pomocą dostępnych rozszerzeń](https://code.visualstudio.com/docs/languages/python).

**PYTANIA I ODPOWIEDZI. Do czego można używać do tworzenia interfejsu użytkownika za pomocą języka Python?**

A. Oferta głównego, w tym obszarze jest [projektu Qt](https://www.qt.io/qt-for-application-development/), powiązań dla języka Python, znane jako [PySide (oficjalna powiązania)](https://wiki.qt.io/PySide) (Zobacz też [PySide pliki do pobrania](https://download.qt.io/official_releases/pyside/.)) i [ PyQt](https://wiki.python.org/moin/PyQt). W chwili obecnej Obsługa w języku Python w programie Visual Studio nie ma żadnych określone narzędzia do tworzenia interfejsu użytkownika.

**PYTANIA I ODPOWIEDZI. Projektu języka Python, mogą wygenerować autonomicznego pliku wykonywalnego?**

A. Języka Python jest zwykle języku interpretowanych za pomocą którego kod jest uruchamiany na żądanie w odpowiednim środowisku obsługą języka Python, takie jak Visual Studio i serwery sieci web. Visual Studio nie obecnie udostępnia środki do utworzenia autonomicznego pliku wykonywalnego, co oznacza programu przy użyciu osadzonych interpreter języka Python. Jednak społeczności Python dostarczonych różne sposoby, aby utworzyć pliki wykonywalne, zgodnie z opisem na [StackOverflow](https://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency). CPython obsługuje również osadzona w aplikacji macierzystej, zgodnie z opisem na wpis w blogu [pliku zip możliwego do osadzenia przy użyciu CPython](https://blogs.msdn.microsoft.com/pythonengineering/2016/04/26/cpython-embeddable-zip-file/).

## <a name="features-matrix"></a>Tabela funkcji

Funkcje języka Python można zainstalować w następujących wersjach programu Visual Studio, zgodnie z opisem w [Przewodnik instalacji](installing-python-support-in-visual-studio.md):

- [Program Visual Studio 2017 (wszystkie wersje)](https://visualstudio.microsoft.com/vs/)
- Program Visual Studio 2015 (wszystkie wersje)
- Visual Studio 2013 Community Edition
- Visual Studio Express 2013 for Web i Update 2 lub nowszy
- Visual Studio 2013 Express for Desktop Update 2 lub nowszy
- Visual Studio 2013 (w wersji Pro lub nowszej)
- Program Visual Studio 2012 (w wersji Pro lub nowszej)
- Visual Studio 2010 SP1 (wersja Pro lub nowszy; wymagana .NET 4.5)

Visual Studio 2015 i starsze są dostępne pod adresem [visualstudio.microsoft.com/vs/older-downloads/](https://visualstudio.microsoft.com/vs/older-downloads/).

> [!Important]
> Funkcje są w pełni obsługiwane i zarządzania dla najnowszej wersji programu Visual Studio. Funkcje są dostępne w starszych wersjach, ale nie są zachowywane aktywnie.

|          Obsługa w języku Python          |   2017   |   2015   | 2013 Comm | Pulpit 2013 | 2013 w sieci web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|----------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|   Zarządzanie wieloma interpretery   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Automatyczne wykrywanie popularnych interpretery | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|     Dodaj niestandardowe interpretery      | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Środowiska wirtualne       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|         Instalowanie narzędzia PIP/łatwe         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>


|         System projektu         |   2017   |   2015   | 2013 Comm | Pulpit 2013 | 2013 w sieci web | 2013 Pro+ |      2012 Pro+       | 2010 SP1 Pro+ |
|--------------------------------|----------|----------|-----------|--------------|----------|-----------|----------------------|---------------|
| Nowy projekt z istniejącego kodu | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  |       &#10004;       |   &#10004;    |
|         Pokaż wszystkie pliki         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  |       &#10004;       |   &#10004;    |
|         Kontrola źródła         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  |       &#10004;       |   &#10004;    |
|        Integracja z usługą Git         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;<sup>1</sup> |   &#10007;    |

<br/>


|           Edytowanie            |   2017   |   2015   | 2013 Comm | Pulpit 2013 | 2013 w sieci web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|     Wyróżnianie składni      | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        Autouzupełnianie         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        Pomocy dotyczącej sygnatur        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|          Szybkie informacje          | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|  Widok przeglądarki/class obiektu   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        Pasek nawigacyjny        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Przejdź do definicji       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|         Przejdź do          | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|     Znajdź wszystkie odwołania      | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Automatyczne wcięcie       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Formatowanie kodu        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|      Refaktoryzuj — zmiana nazwy       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|  Refaktoryzacja - extrahovat metodu   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Refaktoryzuj — Dodaj/Usuń import | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|            PyLint            | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>


|     Okno interaktywne     |   2017   |   2015   | 2013 Comm | Pulpit 2013 | 2013 w sieci web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|----------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|     Okno interaktywne     | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Program IPython z wykresami wbudowane | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>


|               Pulpitu               |   2017   |   2015   | 2013 Comm | Pulpit 2013 | 2013 w sieci web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|-------------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|     Aplikacja konsoli/Windows     | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| WPF v Ironpythonu (przy użyciu projektanta XAML) | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|      IronPython Windows Forms       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>


|         sieć Web         |   2017   |   2015   | 2013 Comm | Pulpit 2013 | 2013 w sieci web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|---------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
| Projekt sieci web Django  | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Projekt sieci web Bottle  | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|  Projekt sieci web Flask  | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Projekt sieci web ogólnego | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>


|         Azure          |   2017   |   2015   | 2013 Comm | Pulpit 2013 |       2013 w sieci web       |      2013 Pro+       |      2012 Pro+       |    2010 SP1 Pro+     |
|------------------------|----------|----------|-----------|--------------|----------------------|----------------------|----------------------|----------------------|
|   Wdrażanie witryny sieci web   | &#10004; | &#10004; | &#10004;  |   &#10007;   |       &#10004;       |       &#10004;       |       &#10004;       | &#10004;<sup>2</sup> |
|   Wdrażanie w roli sieci web   | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> |       &#10007;       |
| Wdrażanie do roli procesu roboczego  |    ?     |    ?     |     ?     |   &#10007;   | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> |       &#10007;       |
| Uruchamianie w emulatorze platformy Azure  |    ?     |    ?     |     ?     |   &#10007;   | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> |       &#10007;       |
|    Debugowanie zdalne    | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>6</sup> | &#10004;<sup>8</sup> | &#10004;<sup>8</sup> |       &#10007;       |
| Dołącz Eksploratora serwera | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>7</sup> | &#10004;<sup>7</sup> |       &#10007;       |       &#10007;       |

<br/>


|           Szablony Django           |   2017   |   2015   | 2013 Comm | Pulpit 2013 |       2013 w sieci web       |      2013 Pro+       | 2012 Pro+ | 2010 SP1 Pro+ |
|--------------------------------------|----------|----------|-----------|--------------|----------------------|----------------------|-----------|---------------|
|              Debugowanie               | &#10004; | &#10004; | &#10004;  |   &#10007;   |       &#10004;       |       &#10004;       | &#10004;  |   &#10004;    |
|            Autouzupełnianie             | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10004;  |   &#10004;    |
| Autouzupełnianie dla CSS i JavaScript | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10007;  |   &#10007;    |

<br/>


|                  Debugowanie                  |   2017   |   2015   | 2013 Comm | Pulpit 2013 | 2013 w sieci web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|---------------------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|                  Debugowanie                  | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|         Debugowanie bez projektu         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        Debugowanie — Dołącz do edycji        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10007; | &#10004;  | &#10004;  |   &#10004;    |
|            Debugowanie w trybie mieszanym             | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |
| Zdalne debugowanie (Windows, Mac OS X, Linux) | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10007; | &#10004;  | &#10004;  |   &#10004;    |
|          Okno interaktywne debugowania           | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

<a name="matrix-profiling"></a>


| Profilowanie |   2017   |   2015   | 2013 Comm | Pulpit 2013 | 2013 w sieci web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|-----------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
| Profilowanie | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10007; | &#10004;  | &#10004;  |   &#10004;    |

<br/>


|     Test      |   2017   |   2015   | 2013 Comm | Pulpit 2013 | 2013 w sieci web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|---------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
| Eksplorator testów | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |
|   Uruchom test    | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |
|  Debuguj test   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |

<br/>

1. Obsługa Git programu Visual Studio 2012 jest dostępny w Visual Studio Tools dla rozszerzenia cyfry, dostępne na [galerii Visual Studio](https://marketplace.visualstudio.com/items?itemName=TFSPowerToolsTeam.VisualStudioToolsforGit).

1. Wdrożenie do witryny sieci Web platformy Azure wymaga [zestawu Azure SDK dla platformy .NET 2.1 — Visual Studio 2010 SP1](https://go.microsoft.com/fwlink/?LinkId=313855). Nowsze wersje nie obsługują programu Visual Studio 2010.

1. Pomoc techniczna dla roli sieci Web platformy Azure i roli procesu roboczego wymaga [zestawu Azure SDK dla platformy .NET 2.3 — VS 2012](https://go.microsoft.com/fwlink/?LinkId=323511) lub nowszej.

1. Pomoc techniczna dla roli sieci Web platformy Azure i roli procesu roboczego wymaga [zestawu Azure SDK dla platformy .NET 2.3 — VS 2013](https://go.microsoft.com/fwlink/?LinkId=323510) lub nowszej.

1. Edytor szablonów Django w programie Visual Studio 2013 zawiera niektóre znane problemy, które są rozpoznawane przez instalowania aktualizacji Update 2.

1. Wymaga systemu Windows 8 lub nowszy. Visual Studio Express 2013 for Web nie ma **dołączyć do procesu** okna dialogowego, ale witryny sieci Web platformy Azure, zdalne debugowanie jest nadal możliwe przy użyciu **dołączanie debugera (Python)** polecenia w pliku **serwera Eksplorator**. Zdalne debugowanie wymaga [zestawu Azure SDK dla platformy .NET 2.3 — Visual Studio 2013](https://go.microsoft.com/fwlink/?LinkId=323510) lub nowszej.

1. Wymaga systemu Windows 8 lub nowszy. **Dołącz debuger (Python)** polecenia w pliku **Eksploratora serwera** wymaga [zestawu Azure SDK dla platformy .NET 2.3 — Visual Studio 2013](https://go.microsoft.com/fwlink/?LinkId=323510) lub nowszej.

1. Wymaga systemu Windows 8 lub nowszy.

## <a name="additional-resources"></a>Dodatkowe zasoby

- [WFastCGI Most między usługami IIS a Python](https://pypi.org/p/wfastcgi) (pypi.org)
- [Bezpłatne kursy języka Python w Microsoft Virtual Academy](https://mva.microsoft.com/search/SearchResults.aspx#!q=python)
- [Najważniejsze pytania języka Python w Microsoft Virtual Academy](https://aka.ms/mva-top-python-questions)

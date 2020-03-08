---
title: Obsługa języka Python w programie Visual Studio na Windows
titleSuffix: ''
description: Podsumowanie funkcji języka Python w programie Visual Studio, dzięki czemu najlepsze środowisko IDE języka Python na Windows (znany także jako narzędzi Python Tools for Visual Studio, PTVS).
ms.date: 06/05/2019
ms.topic: overview
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: a913fa6abdcf59a64d8514f17656b8f8531d476d
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409034"
---
# <a name="work-with-python-in-visual-studio-on-windows"></a>Praca z językiem Python w programie Visual Studio na Windows

Język Python jest popularnych języków programowania, które jest niezawodne, elastyczne, można łatwo dowiedzieć się, bezpłatnie do użycia we wszystkich systemach operacyjnych i obsługiwane przez społeczność deweloperów silne i wielu bezpłatnych bibliotek. Python obsługuje wszystkich sposobów rozwoju, w tym aplikacje sieci web, usług sieci web, aplikacje klasyczne, skryptów i obliczeń naukowych i jest używany przez wiele uniwersytety, analitykom, zwykłych deweloperów i podobne profesjonalnych deweloperów. Możesz dowiedzieć się więcej o języku [Python.org](https://www.python.org) i [Python dla początkujących](https://www.python.org/about/gettingstarted/).

Visual Studio to zaawansowane środowisko IDE języka Python na Windows. Program Visual Studio zapewnia obsługę funkcji [Open Source](https://github.com/Microsoft/ptvs) dla języka Python za pomocą obciążeń związanych z **programowaniem** i analizą **danych** w języku Python (Visual Studio 2017 i nowszych) oraz rozszerzenia bezpłatnego Python Tools for Visual Studio (Visual Studio 2015 i starsze).

Język Python nie jest obecnie obsługiwany w Visual Studio dla komputerów Mac, ale jest dostępny na komputerach Mac i w systemie Linux za poorednictwem Visual Studio Code (zobacz [pytania i odpowiedzi](#questions-and-answers)).

Aby rozpocząć:

- Postępuj zgodnie z [instrukcjami instalacji](installing-python-support-in-visual-studio.md) , aby skonfigurować obciążenie języka Python.
- Zapoznaj się z możliwościami Python programu Visual Studio za pomocą sekcji w niniejszym artykule.
::: moniker range="vs-2017"
- Przechodzą przez co najmniej jeden z przewodników Szybki Start, aby utworzyć projekt. Jeśli nie masz pewności, Zacznij od [utworzenia aplikacji internetowej z kolbą](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json).
::: moniker-end
::: moniker range=">=vs-2019"
- Przechodzą przez co najmniej jeden z przewodników Szybki Start, aby utworzyć projekt. Jeśli nie masz pewności, Zacznij od [przewodnika Szybki Start: otwieranie i uruchamianie kodu w języku Python w folderze](quickstart-05-python-visual-studio-open-folder.md) lub [Tworzenie aplikacji sieci Web z kolbą](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json).
::: moniker-end
- Wykonaj czynności opisane w samouczku dotyczącym [języka Python w programie Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md) , aby zapoznać się z kompleksowym doświadczeniem.

::: moniker range=">=vs-2019"
> [!Note]
> Program Visual Studio obsługuje język Python w wersji 2,7, a także wersję 3,5 do 3,7. Chociaż można użyć programu Visual Studio do edycji kodu pisanego w innych wersjach języka Python, te wersje nie są oficjalnie obsługiwane, a funkcje takie jak IntelliSense i debugowanie mogą nie zadziałać. Obsługa języka Python w wersji 3,8 jest nadal w fazie opracowywania. Szczegółowe informacje na temat pomocy technicznej można zobaczyć w tym [problemie związanym ze](https://github.com/microsoft/PTVS/issues/5822)śledzeniem w witrynie GitHub.
::: moniker-end

## <a name="support-for-multiple-interpreters"></a>Obsługa wielu interpretery

Okno **środowiska Python** programu Visual Studio (pokazane poniżej w szerokim widoku rozszerzonym) oferuje jedno miejsce do zarządzania wszystkimi globalnymi środowiskami języka Python, środowiskami Conda i środowiskami wirtualnymi. Visual Studio automatycznie wykrywa instalacje języka Python w lokalizacjach i pozwala na skonfigurowanie instalacje niestandardowe. Z każdym środowiskiem może łatwo zarządzania pakietami, Otwórz okno interaktywne dla danego środowiska i dostęp do folderów środowiska.

::: moniker range="vs-2017"
![Rozwinięty widok okna środowiska Python](media/environments/environments-expanded-view.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Rozwinięty widok okna środowiska Python](media/environments/environments-expanded-view-2019.png)
::: moniker-end

Użyj polecenia **Otwórz okno interaktywne, aby interaktywnie** uruchomić środowisko Python w kontekście programu Visual Studio. Użyj polecenia **Otwórz w programie PowerShell** , aby otworzyć osobne okno polecenia w folderze wybranego środowiska. Z tego okna polecenia skrypt można uruchomić dowolnego języka python.

Więcej informacji:

- [Zarządzaj środowiskami języka Python](managing-python-environments-in-visual-studio.md)
- [Dokumentacja środowisk Python](python-environments-window-tab-reference.md)

## <a name="rich-editing-intellisense-and-code-comprehension"></a>Zaawansowane edytowanie, IntelliSense i zrozumienie kodu

Program Visual Studio zapewnia najwyższej klasy Edytor języka Python obejmujący kolorowanie składni, automatyczne uzupełnianie kodu i bibliotek, formatowanie pomocy dotyczącej sygnatur, refaktoryzacji, Zaznaczanie błędów i wskazówek dotyczących typów kodu. Program Visual Studio udostępnia również unikatowe funkcje, takie jak widok klasy, **Przejdź do definicji**, **Znajdź wszystkie odwołania**i fragmenty kodu. Bezpośrednia integracja z [oknem interaktywnym](#interactive-window) pomaga szybko opracowywać kod języka Python, który został już zapisany w pliku.

![Uzupełnianie kodu dla kodu w języku Python w programie Visual Studio](media/code-editing-completions-simple.png)

Więcej informacji:

- Docs: [Edytowanie kodu](editing-python-code-in-visual-studio.md) w języku Python
- Docs: [Formatuj kod](formatting-python-code.md)
- Docs: [kod refaktoryzacji](refactoring-python-code.md)
- Dokumentacja: [Korzystanie z Linter](linting-python-code.md)
- Ogólna dokumentacja funkcji programu Visual Studio: [funkcje edytora kodu](../ide/writing-code-in-the-code-and-text-editor.md)

## <a name="interactive-window"></a>Okno interaktywne

Dla każdego środowiska Python, wiadomo, że program Visual Studio możesz łatwo otworzyć tego samego środowiska interaktywnego (REPL) dla interpretera języka Python, bezpośrednio z poziomu programu Visual Studio, a nie przy użyciu oddzielnych wiersza polecenia. Można łatwo przełączać się między środowiskami, jak również. (Aby otworzyć osobnym wierszu polecenia, wybierz odpowiednie środowisko w oknie środowiska języka **Python** , a następnie wybierz polecenie **Otwórz w programie PowerShell** , jak wyjaśniono wcześniej w obszarze [Obsługa wielu interpreterów](#support-for-multiple-interpreters)).

![Oknie interakcyjnym środowiska Python w programie Visual Studio](media/interactive-window.png)

Program Visual Studio zapewnia także ścisłą integrację między edytorem kodu w języku Python a oknem **interaktywnym** . **Klawisz Ctrl**+**wprowadzanie** skrótu klawiaturowego wygodnie wysyła bieżący wiersz kodu (lub blok kodu) w edytorze do okna **interaktywnego** , a następnie przechodzi do następnego wiersza (lub bloku). **Klawisz Ctrl**+**Enter** umożliwia łatwe przechodzenie przez kod bez konieczności uruchamiania debugera. Możesz również wysłać zaznaczony kod do okna **interaktywnego** z tym samym naciśnięciem klawisza i z łatwością wkleić kod z okna **interaktywnego** do edytora. Ponadto te funkcje umożliwiają wykonywanie szczegółowych informacji o segmencie kodu w oknie **interaktywnym** i łatwe zapisywanie wyników w pliku w edytorze.

Program Visual Studio obsługuje również IPython/Jupyter w rozwiązaniu REPL, m.in. wbudowane powierzchnie, .NET i Windows Presentation Foundation (WPF).

Więcej informacji:

- [Okno interaktywne](python-interactive-repl-in-visual-studio.md)
- [IPython w programie Visual Studio](interactive-repl-ipython.md)

## <a name="project-system-and-project-and-item-templates"></a>System projektów i szablonów projektów i elementów

::: moniker range=">=vs-2019"
> [!Note]
> Program Visual Studio 2019 obsługuje Otwieranie folderu zawierającego kod języka Python i uruchamianie tego kodu bez tworzenia plików projektu i rozwiązania programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Szybki Start: otwieranie i uruchamianie kodu w języku Python w folderze](quickstart-05-python-visual-studio-open-folder.md). Istnieją jednak zalety korzystania z pliku projektu, zgodnie z opisem w tej sekcji.
::: moniker-end

Program Visual Studio pomaga uprościć projekt wzrostem wraz z upływem czasu. *Projekt programu Visual Studio* jest znacznie więcej niż struktura folderów: zawiera informacje na temat sposobu używania różnych plików i sposobu ich powiązania ze sobą. Program Visual Studio pozwala odróżnić kodu aplikacji, przetestować kod, stron sieci web, JavaScript, skrypty kompilacji i tak dalej, które następnie umożliwiają odpowiednich plików funkcji. Rozwiązania programu Visual Studio ułatwia ponadto zarządzanie wielu powiązanych projektów, takich jak projektu języka Python i rozszerzenie projektu w języku C++.

![Rozwiązania programu Visual Studio zawierający projektów języka C++ i Python](media/projects-solution-explorer-two-projects.png)

Szablony projektów i elementów zautomatyzować proces konfigurowania różnych typów projektów i plików, co cenny czas i zwalniania możesz zarządzać szczegóły skomplikowanych i obarczone ryzykiem błędów. Program Visual Studio udostępnia szablony dla sieci web, Azure, do nauki o danych, konsolę i innych rodzajów projektów, w tym szablony dla plików, takie jak klasy, testy jednostkowe, konfiguracji sieci web platformy Azure, HTML i nawet aplikacji Django języka Python.

[![szablonów projektu i elementów języka Python w programie Visual Studio](media/project-and-item-templates.png)](media/project-and-item-templates.png#lightbox)

Więcej informacji:

- Docs: [Zarządzanie projektami Python](managing-python-projects-in-visual-studio.md)
- Docs: [Dokumentacja szablonów elementów](python-item-templates.md)
- Docs: [Szablony projektów języka Python](managing-python-projects-in-visual-studio.md#project-templates)
- Dokumenty: [Pracuj z C++ i Python](working-with-c-cpp-python-in-visual-studio.md)
- Ogólne dokumenty funkcji programu Visual Studio: [Szablony projektów i elementów](../ide/creating-project-and-item-templates.md#visual-studio-templates)
- Dokumentacja funkcji ogólnych programu Visual Studio: [rozwiązania i projekty w programie Visual Studio](../ide/solutions-and-projects-in-visual-studio.md)

## <a name="full-featured-debugging"></a>Oferujący debugowania

Jedną z mocnych programu Visual Studio jest jego zaawansowany debuger. W szczególności środowisko Python programu Visual Studio zawiera debugowanie wC++ trybie Python/mieszane, zdalne debugowanie w systemie Linux, debugowanie w oknie **interaktywnym** i debugowanie testów jednostkowych w języku Python.

![Debuger programu Visual Studio dla języka Python, przedstawiający okno podręczne wyjątku](media/debugging-exception-popup.png)

::: moniker range=">=vs-2019"
W programie Visual Studio 2019 można uruchamiać i debugować kod bez pliku projektu programu Visual Studio. Aby uzyskać przykład, zobacz [Szybki Start: otwieranie i uruchamianie kodu w języku Python w folderze](quickstart-05-python-visual-studio-open-folder.md) .
::: moniker-end

Więcej informacji:

- Docs: [Debugowanie języka Python](debugging-python-in-visual-studio.md)
- Dokumenty: [debugowanie wC++ trybie Python/mieszany](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)
- Dokumentacja: [zdalne debugowanie w systemie Linux](debugging-python-code-on-remote-linux-machines.md)
- Ogólna dokumentacja funkcji programu Visual Studio: [Przewodnik po funkcjach debugera programu Visual Studio](../debugger/debugger-feature-tour.md)

## <a name="profiling-tools-with-comprehensive-reporting"></a>Narzędzia profilowania przy użyciu kompleksowe raportowanie

Profilowanie przedstawiono, jak jest zużywany czas w aplikacji. Visual Studio obsługuje profilowanie przy użyciu opartych na CPython interpreterów i z możliwością porównania wydajności między różnych tras profilowania.

[![wyniki programu Visual Studio profiler dla projektu języka Python](media/profiling-results.png)](media/profiling-results.png#lightbox)

Więcej informacji:

- Docs: [narzędzia profilowania języka Python](profiling-python-code-in-visual-studio.md)
- Ogólna dokumentacja funkcji programu Visual Studio: [profilowanie przewodnika](../profiling/profiling-feature-tour.md)dotyczącego funkcji. (Nie wszystkie funkcje profilowania programu Visual Studio są dostępne dla języka Python).

## <a name="unit-testing-tools"></a>Narzędzia do testowania jednostkowego

Wykrywaj i uruchamiaj testy w programie Visual Studio **Test Explorer**oraz łatwo Debuguj testy jednostkowe.

![Profilowanie testu jednostkowego języka Python w programie Visual Studio](media/unit-test-debugging.png)

Więcej informacji:

- Docs: [Narzędzia do testowania jednostkowego dla języka Python](unit-testing-python-in-visual-studio.md)
- Ogólna dokumentacja funkcji programu Visual Studio: [testowanie jednostkowe kodu](../test/unit-test-your-code.md).

## <a name="azure-sdk-for-python"></a>Zestaw Azure SDK dla środowiska Python

Biblioteki platformy Azure dla języka Python upraszczają używanie usług platformy Azure z poziomu aplikacji systemu Windows, Mac OS X i Linux. Można ich używać do tworzenia zasobów platformy Azure i zarządzania nimi, a także do nawiązywania połączeń z usługami platformy Azure. 

Aby uzyskać więcej informacji, zobacz [zestaw Azure SDK dla języka Python](/azure/python/) i [bibliotek platformy Azure dla języka Python](/azure/python/python-sdk-azure-overview) .

## <a name="questions-and-answers"></a>Pytania i odpowiedzi

**P. czy obsługa Visual Studio dla komputerów Mac jest dostępna w języku Python?**

A. Nie jest to możliwe, ale możesz zagłosować na żądanie w [społeczności deweloperów](https://developercommunity.visualstudio.com/content/idea/351820/python-tools-for-visual-studio-mac.html). Dokumentacja [Visual Studio dla komputerów Mac](/visualstudio/mac/) identyfikuje bieżące typy rozwoju, które obsługuje. W międzyczasie Visual Studio Code w systemach Windows, Mac i Linux [działają dobrze w języku Python za pomocą dostępnych rozszerzeń](https://code.visualstudio.com/docs/languages/python).

**P. czego można użyć do kompilowania interfejsu użytkownika przy użyciu języka Python?**

A. Główną ofertą w tym obszarze jest [projekt QT](https://www.qt.io/qt-for-application-development/)z powiązaniami dla języka Python znanego [jako pyside (oficjalne powiązanie)](https://wiki.qt.io/PySide) (Zobacz też [pobieranie pyside](https://download.qt.io/official_releases/pyside/.)) i [PyQt](https://wiki.python.org/moin/PyQt). W chwili obecnej Obsługa w języku Python w programie Visual Studio nie ma żadnych określone narzędzia do tworzenia interfejsu użytkownika.

**P. czy projekt języka Python tworzy autonomiczny plik wykonywalny?**

A. Języka Python jest zwykle języku interpretowanych za pomocą którego kod jest uruchamiany na żądanie w odpowiednim środowisku obsługą języka Python, takie jak Visual Studio i serwery sieci web. Visual Studio nie obecnie udostępnia środki do utworzenia autonomicznego pliku wykonywalnego, co oznacza programu przy użyciu osadzonych interpreter języka Python. Jednak społeczność języka Python dostarczyła różne metody tworzenia plików wykonywalnych zgodnie z opisem w [StackOverflow](https://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency). CPython obsługuje również osadzanie w aplikacji natywnej, zgodnie z opisem w wpisie w blogu, [przy użyciu pliku zip](https://devblogs.microsoft.com/python/cpython-embeddable-zip-file/)z możliwością osadzenia CPython.

::: moniker range="<=vs-2017"

## <a name="feature-support"></a>Obsługa funkcji

Funkcje języka Python można zainstalować w następujących wersjach programu Visual Studio, zgodnie z opisem w [przewodniku instalacji](installing-python-support-in-visual-studio.md):

- [Visual Studio 2019 (wszystkie wersje)](https://visualstudio.microsoft.com/vs/)
- Visual Studio 2017 (wszystkie wersje)
- Program Visual Studio 2015 (wszystkie wersje)
- Visual Studio 2013 Community Edition
- Visual Studio Express 2013 for Web i Update 2 lub nowszy
- Visual Studio 2013 Express for Desktop Update 2 lub nowszy
- Visual Studio 2013 (w wersji Pro lub nowszej)
- Program Visual Studio 2012 (w wersji Pro lub nowszej)
- Visual Studio 2010 SP1 (wersja Pro lub nowszy; wymagana .NET 4.5)

Program Visual Studio 2015 i jego starsze wersje są dostępne pod adresem [VisualStudio.Microsoft.com/vs/older-downloads/](https://visualstudio.microsoft.com/vs/older-downloads/).

> [!Important]
> Funkcje są w pełni obsługiwane i zarządzania dla najnowszej wersji programu Visual Studio. Funkcje są dostępne w starszych wersjach, ale nie są zachowywane aktywnie.

|          Obsługa w języku Python          |   2017+   |   2015   | 2013 Comm | Pulpit 2013 | 2013 w sieci web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|----------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|   Zarządzanie wieloma interpretery   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Automatyczne wykrywanie popularnych interpretery | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|     Dodaj niestandardowe interpretery      | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Środowiska wirtualne       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|         Instalowanie narzędzia PIP/łatwe         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|         System projektu         |   2017+   |   2015   | 2013 Comm | Pulpit 2013 | 2013 w sieci web | 2013 Pro+ |      2012 Pro+       | 2010 SP1 Pro+ |
|--------------------------------|----------|----------|-----------|--------------|----------|-----------|----------------------|---------------|
| Nowy projekt z istniejącego kodu | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  |       &#10004;       |   &#10004;    |
|         Pokaż wszystkie pliki         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  |       &#10004;       |   &#10004;    |
|         Kontrola źródła         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  |       &#10004;       |   &#10004;    |
|        Integracja z usługą Git         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;<sup>jedno</sup> |   &#10007;    |

<br/>

|           Edytowanie            |   2017+   |   2015   | 2013 Comm | Pulpit 2013 | 2013 w sieci web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|     Wyróżnianie składni      | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        Autouzupełnianie         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        Pomocy dotyczącej sygnatur        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|          Szybkie informacje          | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|  Widok przeglądarki/class obiektu   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        Pasek nawigacyjny        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Przejdź do definicji       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|         Przejdź do pozycji          | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|     Znajdź wszystkie odwołania      | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Automatyczne wcięcie       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Formatowanie kodu        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|      Refaktoryzuj — zmiana nazwy       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|  Refaktoryzacja - extrahovat metodu   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Refaktoryzuj — Dodaj/Usuń import | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|            PyLint            | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|     Okno interaktywne     |   2017+   |   2015   | 2013 Comm | Pulpit 2013 | 2013 w sieci web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|----------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|     Okno interaktywne     | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Program IPython z wykresami wbudowane | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|               Klasyczna               |   2017+   |   2015   | 2013 Comm | Pulpit 2013 | 2013 w sieci web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|-------------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|     Aplikacja konsoli/Windows     | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| WPF v Ironpythonu (przy użyciu projektanta XAML) | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|      IronPython Windows Forms       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|         Sieć Web         |   2017+   |   2015   | 2013 Comm | Pulpit 2013 | 2013 w sieci web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|---------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
| Projekt sieci web Django  | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Projekt sieci web Bottle  | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|  Projekt sieci web Flask  | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Projekt sieci web ogólnego | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|         Azure          |   2017+   |   2015   | 2013 Comm | Pulpit 2013 |       2013 w sieci web       |      2013 Pro+       |      2012 Pro+       |    2010 SP1 Pro+     |
|------------------------|----------|----------|-----------|--------------|----------------------|----------------------|----------------------|----------------------|
|   Wdrażanie witryny sieci web   | &#10004; | &#10004; | &#10004;  |   &#10007;   |       &#10004;       |       &#10004;       |       &#10004;       | &#10004;<sup>dwóch</sup> |
|   Wdrażanie w roli sieci web   | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>czwart</sup> | &#10004;<sup>czwart</sup> | &#10004;<sup>r.3</sup> |       &#10007;       |
| Wdrażanie do roli procesu roboczego  |    ?     |    ?     |     ?     |   &#10007;   | &#10004;<sup>czwart</sup> | &#10004;<sup>czwart</sup> | &#10004;<sup>r.3</sup> |       &#10007;       |
| Uruchamianie w emulatorze platformy Azure  |    ?     |    ?     |     ?     |   &#10007;   | &#10004;<sup>czwart</sup> | &#10004;<sup>czwart</sup> | &#10004;<sup>r.3</sup> |       &#10007;       |
|    Debugowanie zdalne    | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>ust</sup> | &#10004;<sup>0,8</sup> | &#10004;<sup>0,8</sup> |       &#10007;       |
| Dołącz Eksploratora serwera | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>7</sup> | &#10004;<sup>7</sup> |       &#10007;       |       &#10007;       |

<br/>

|           Szablony Django           |   2017+   |   2015   | 2013 Comm | Pulpit 2013 |       2013 w sieci web       |      2013 Pro+       | 2012 Pro+ | 2010 SP1 Pro+ |
|--------------------------------------|----------|----------|-----------|--------------|----------------------|----------------------|-----------|---------------|
|              Debugowanie               | &#10004; | &#10004; | &#10004;  |   &#10007;   |       &#10004;       |       &#10004;       | &#10004;  |   &#10004;    |
|            Autouzupełnianie             | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>5000</sup> | &#10004;<sup>5000</sup> | &#10004;  |   &#10004;    |
| Autouzupełnianie dla CSS i JavaScript | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>5000</sup> | &#10004;<sup>5000</sup> | &#10007;  |   &#10007;    |

<br/>

|                  Debugowanie                  |   2017+   |   2015   | 2013 Comm | Pulpit 2013 | 2013 w sieci web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|---------------------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|                  Debugowanie                  | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|         Debugowanie bez projektu         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        Debugowanie — Dołącz do edycji        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10007; | &#10004;  | &#10004;  |   &#10004;    |
|            Debugowanie w trybie mieszanym             | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |
| Zdalne debugowanie (Windows, Mac OS X, Linux) | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10007; | &#10004;  | &#10004;  |   &#10004;    |
|          Okno interaktywne debugowania           | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

<a name="matrix-profiling"></a>

| Profilowanie |   2017+   |   2015   | 2013 Comm | Pulpit 2013 | 2013 w sieci web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|-----------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
| Profilowanie | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10007; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|     Testowanie      |   2017+   |   2015   | 2013 Comm | Pulpit 2013 | 2013 w sieci web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|---------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
| Eksplorator testów | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |
|   Uruchom test    | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |
|  Debuguj test   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |

<br/>

1. Obsługa usługi git dla programu Visual Studio 2012 jest dostępna w Visual Studio Tools dla rozszerzenia git dostępnego na [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=TFSPowerToolsTeam.VisualStudioToolsforGit).

1. Wdrożenie w witrynie sieci Web systemu Azure wymaga [zestawu Azure SDK dla programu .net 2,1 — Visual Studio 2010 z dodatkiem SP1](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VS2010SP1AzurePack.2E2.2E1.appids). Nowsze wersje nie obsługują programu Visual Studio 2010.

1. Obsługa roli sieci Web i roli procesu roboczego platformy Azure wymaga [zestawu Azure SDK dla programu .net 2,3 — VS 2012](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs11AzurePack.appids) lub nowszego.

1. Obsługa roli sieci Web i roli procesu roboczego platformy Azure wymaga [zestawu Azure SDK dla programu .net 2,3 — VS 2013](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs2013AzurePack.appids) lub nowszego.

1. Edytor szablonów Django w programie Visual Studio 2013 zawiera niektóre znane problemy, które są rozpoznawane przez instalowania aktualizacji Update 2.

1. Wymaga systemu Windows 8 lub nowszy. Visual Studio 2013 Express for Web nie ma okna dialogowego **Dołącz do procesu** , ale zdalne debugowanie witryny sieci Web systemu Azure jest nadal możliwe przy użyciu polecenia **Dołącz debuger (Python)** w **Eksplorator serwera**. Zdalne debugowanie wymaga [zestawu Azure SDK dla programu .net 2,3 — Visual Studio 2013](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs2013AzurePack.appids) lub nowszego.

1. Wymaga systemu Windows 8 lub nowszy. Polecenie **Attach Debugger (Python)** w **Eksplorator serwera** wymaga [zestawu Azure SDK dla programu .NET 2,3 — Visual Studio 2013](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs2013AzurePack.appids) lub nowszego.

1. Wymaga systemu Windows 8 lub nowszy.
::: moniker-end

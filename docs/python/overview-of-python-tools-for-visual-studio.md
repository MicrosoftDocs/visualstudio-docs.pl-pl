---
title: Obsługa języka Python w programie Visual Studio w systemie Windows
titleSuffix: ''
description: Podsumowanie funkcji języka Python w programie Visual Studio, co czyni go najlepszym ide python w systemie Windows (znany również jako Python Tools for Visual Studio, PTVS).
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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "79302792"
---
# <a name="work-with-python-in-visual-studio-on-windows"></a>Praca z pythonem w programie Visual Studio w systemie Windows

Python to popularny język programowania, który jest niezawodny, elastyczny, łatwy do nauczenia się, darmowy w użyciu we wszystkich systemach operacyjnych i wspierany zarówno przez silną społeczność programistów, jak i wiele darmowych bibliotek. Python obsługuje wszystkie żyjących formę rozwoju, w tym aplikacje internetowe, usługi internetowe, aplikacje komputerowe, skrypty i obliczenia naukowe, i jest używany przez wiele uniwersytetów, naukowców, zwykłych programistów i profesjonalnych programistów. Możesz dowiedzieć się więcej o języku na [python.org](https://www.python.org) i [Python dla początkujących](https://www.python.org/about/gettingstarted/).

Visual Studio to potężny ide języka Python w systemie Windows. Visual Studio zapewnia obsługę języka języka języka Języka Python [typu open source](https://github.com/Microsoft/ptvs) za pośrednictwem obciążeń **deweloperskich** i do nauki **o danych** języka Python (Visual Studio 2017 i nowszych) oraz bezpłatnego rozszerzenia Narzędzia Python dla programu Visual Studio (Visual Studio 2015 i starsze).

Python nie jest obecnie obsługiwany w programie Visual Studio dla komputerów Mac, ale jest dostępny na komputerach Mac i Linux za pośrednictwem programu Visual Studio Code (zobacz [pytania i odpowiedzi).](#questions-and-answers)

Aby rozpocząć:

- Postępuj zgodnie z [instrukcjami instalacji,](installing-python-support-in-visual-studio.md) aby skonfigurować obciążenie języka Python.
- Zapoznaj się z możliwościami języka Python programu Visual Studio za pośrednictwem sekcji w tym artykule.
::: moniker range="vs-2017"
- Przejdź przez jeden lub więcej przewodników Szybki start, aby utworzyć projekt. Jeśli nie masz pewności, zacznij od [utwórz aplikację internetową z flask](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json).
::: moniker-end
::: moniker range=">=vs-2019"
- Przejdź przez jeden lub więcej przewodników Szybki start, aby utworzyć projekt. Jeśli nie masz pewności, zacznij od [przewodnika Szybki start: Otwórz i uruchom kod Języka Python w folderze](quickstart-05-python-visual-studio-open-folder.md) lub [Utwórz aplikację internetową za pomocą flask](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json).
::: moniker-end
- Postępuj zgodnie [z pracy z Python w programie Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md) samouczek dla pełnego środowiska end-to-end.

::: moniker range=">=vs-2019"
> [!Note]
> Visual Studio obsługuje język Python w wersji 2.7, a także w wersji od 3.5 do 3.7. Chociaż jest możliwe do edycji kodu napisanego w innych wersjach języka Python, te wersje nie są oficjalnie obsługiwane i funkcje, takie jak IntelliSense i debugowania może nie działać. Obsługa wersji 3.8 Pythona jest nadal w fazie rozwoju, szczegółowe informacje na temat pomocy technicznej można zobaczyć w tym problemie ze śledzeniem [na GitHub](https://github.com/microsoft/PTVS/issues/5822).
::: moniker-end

## <a name="support-for-multiple-interpreters"></a>Obsługa wielu tłumaczy ustnych

Okno Środowiska **języka Python** w programie Visual Studio (pokazane poniżej w widoku rozszerzonym) zapewnia jedno miejsce do zarządzania wszystkimi globalnymi środowiskami języka Python, środowiskami conda i środowiskami wirtualnymi. Program Visual Studio automatycznie wykrywa instalacje języka Python w standardowych lokalizacjach i umożliwia konfigurowanie instalacji niestandardowych. W każdym środowisku można łatwo zarządzać pakietami, otwierać interaktywne okno dla tego środowiska i uzyskiwać dostęp do folderów środowiska.

::: moniker range="vs-2017"
![Rozszerzony widok okna Środowiska języka Python](media/environments/environments-expanded-view.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Rozszerzony widok okna Środowiska języka Python](media/environments/environments-expanded-view-2019.png)
::: moniker-end

Polecenie **Otwórz okno interaktywne** służy do interaktywnego uruchamiania języka Python w kontekście programu Visual Studio. Polecenie **Otwórz w programie PowerShell** umożliwia otwarcie osobnego okna polecenia w folderze wybranego środowiska. W tym oknie polecenia można uruchomić dowolny skrypt pythona.

Więcej informacji:

- [Zarządzanie środowiskami języka Python](managing-python-environments-in-visual-studio.md)
- [Odwołanie do środowisk Języka Python](python-environments-window-tab-reference.md)

## <a name="rich-editing-intellisense-and-code-comprehension"></a>Bogata edycja, IntelliSense i rozumienie kodu

Visual Studio udostępnia edytor Python pierwszej klasy, w tym kolorowanie składni, automatyczne uzupełnianie wszystkich kodu i bibliotek, formatowanie kodu, pomoc podpisu, refaktoryzacji, linting i wskazówki dotyczące typu. Program Visual Studio udostępnia również unikatowe funkcje, takie jak widok klasy, **Przejdź do definicji,** **Znajdź wszystkie odwołania**i fragmenty kodu. Bezpośrednia integracja z [oknem Interaktywna](#interactive-window) pomaga szybko opracować kod Języka Python, który jest już zapisany w pliku.

![Uzupełnianie kodu dla kodu języka Python w programie Visual Studio](media/code-editing-completions-simple.png)

Więcej informacji:

- Dokumenty: [Edytowanie kodu Języka Python](editing-python-code-in-visual-studio.md)
- Dokumenty: [Formatowanie kodu](formatting-python-code.md)
- Dokumenty: [Kod refaktoryzatora](refactoring-python-code.md)
- Dokumenty: [Używanie lintera](linting-python-code.md)
- Dokumenty funkcji ogólnego programu Visual Studio: [funkcje edytora kodu](../ide/writing-code-in-the-code-and-text-editor.md)

## <a name="interactive-window"></a>Okno interaktywne

Dla każdego środowiska języka Python znanego programowi Visual Studio można łatwo otworzyć to samo środowisko interaktywne (REPL) dla interpretera języka Python bezpośrednio w programie Visual Studio, zamiast używać oddzielnego wiersza polecenia. Można łatwo przełączać się między środowiskami, jak również. (Aby otworzyć oddzielny wiersz polecenia, wybierz **żądane** środowisko w oknie Środowiska języka Python, a następnie wybierz polecenie **Otwórz w programie PowerShell,** jak wyjaśniono wcześniej w obszarze [Obsługa wielu interpreterów).](#support-for-multiple-interpreters)

![Interaktywne okno języka Python w programie Visual Studio](media/interactive-window.png)

Visual Studio zapewnia również ścisłą integrację między edytorem kodu języka Python i **interakcyjnym** oknie. Skrót klawiaturowy **Ctrl**+**Enter** wygodnie wysyła bieżący wiersz kodu (lub bloku kodu) w edytorze do okna **Interaktywne,** a następnie przechodzi do następnego wiersza (lub bloku). **Klawisz Ctrl**+**Enter** umożliwia łatwe przechodzenie przez kod bez konieczności uruchamiania debugera. Można również wysłać wybrany kod do okna **Interaktywne** za pomocą tego samego naciśnięcia klawisza i łatwo wkleić kod z okna **Interaktywne** do edytora. Razem te możliwości pozwalają wypracować szczegóły dla segmentu kodu w oknie **Interaktywna** i łatwo zapisać wyniki w pliku w edytorze.

Visual Studio obsługuje również IPython/Jupyter w REPL, w tym wykresy wbudowane, .NET i Windows Presentation Foundation (WPF).

Więcej informacji:

- [Okno interaktywne](python-interactive-repl-in-visual-studio.md)
- [IPython w programie Visual Studio](interactive-repl-ipython.md)

## <a name="project-system-and-project-and-item-templates"></a>System projektu oraz szablony projektów i elementów

::: moniker range=">=vs-2019"
> [!Note]
> Visual Studio 2019 obsługuje otwieranie folderu zawierającego kod języka Python i uruchamianie tego kodu bez tworzenia plików projektu i rozwiązania programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Szybki start: Otwieranie i uruchamianie kodu języka Python w folderze](quickstart-05-python-visual-studio-open-folder.md). Istnieją jednak korzyści z używania pliku projektu, jak wyjaśniono w tej sekcji.
::: moniker-end

Visual Studio pomaga zarządzać złożonością projektu, ponieważ rośnie w czasie. *Projekt programu Visual Studio* jest znacznie więcej niż struktura folderów: zawiera zrozumienie, jak różne pliki są używane i jak odnoszą się do siebie nawzajem. Program Visual Studio pomaga rozróżniać kod aplikacji, kod testowy, strony sieci web, javascript, skrypty kompilacji i tak dalej, które następnie włączyć funkcje odpowiednie dla pliku. Rozwiązanie programu Visual Studio, ponadto ułatwia zarządzanie wieloma powiązanymi projektami, takimi jak projekt języka Python i projekt rozszerzenia Języka C++.

![Rozwiązanie programu Visual Studio zawierające projekty języka Python i C++](media/projects-solution-explorer-two-projects.png)

Szablony projektów i elementów automatyzują proces konfigurowania różnych typów projektów i plików, oszczędzając cenny czas i zwalniając cię od zarządzania skomplikowanymi i podatnymi na błędy szczegółami. Program Visual Studio udostępnia szablony dla sieci Web, platformy Azure, nauki o danych, konsoli i innych typów projektów, wraz z szablonami dla plików, takich jak klasy Języka Python, testy jednostkowe, konfiguracja sieci Web platformy Azure, HTML, a nawet aplikacje Django.

[![Szablony projektów i elementów języka Python w programie Visual Studio](media/project-and-item-templates.png)](media/project-and-item-templates.png#lightbox)

Więcej informacji:

- Dokumenty: [Zarządzanie projektami języka Python](managing-python-projects-in-visual-studio.md)
- Dokumenty: [Odwołanie do szablonów elementów](python-item-templates.md)
- Dokumenty: [szablony projektów Języka Python](managing-python-projects-in-visual-studio.md#project-templates)
- Dokumenty: [Praca z językami C++ i Python](working-with-c-cpp-python-in-visual-studio.md)
- Dokumenty funkcji programu Visual Studio ogólne: [szablony projektów i elementów](../ide/creating-project-and-item-templates.md#visual-studio-templates)
- Dokumenty funkcji programu Ogólne programu Visual Studio: [Rozwiązania i projekty w programie Visual Studio](../ide/solutions-and-projects-in-visual-studio.md)

## <a name="full-featured-debugging"></a>W pełni funkcjonalne debugowanie

Jedną z mocnych stron programu Visual Studio jest jego zaawansowany debuger. W szczególności w przypadku języka Python visual studio zawiera debugowanie w trybie mieszanym Python/C++, zdalne debugowanie w systemie Linux, debugowanie w oknie **interaktywnym** i debugowanie testów jednostkowych języka Python.

![Debuger programu Visual Studio dla języka Python z wyskakującym okienkiem wyjątków](media/debugging-exception-popup.png)

::: moniker range=">=vs-2019"
W programie Visual Studio 2019 można uruchamiać i debugować kod bez posiadania pliku projektu programu Visual Studio. Zobacz [Szybki start: Otwórz i uruchom kod Języka Python w folderze](quickstart-05-python-visual-studio-open-folder.md) na przykład.
::: moniker-end

Więcej informacji:

- Dokumenty: [Debugowanie Pythona](debugging-python-in-visual-studio.md)
- Dokumenty: [Debugowanie w trybie mieszanym Python/C++](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)
- Dokumenty: [Zdalne debugowanie w systemie Linux](debugging-python-code-on-remote-linux-machines.md)
- Dokumenty funkcji programu Visual Studio ogólne: [przewodnik po debugerze programu Visual Studio](../debugger/debugger-feature-tour.md)

## <a name="profiling-tools-with-comprehensive-reporting"></a>Narzędzia profilowania z kompleksową relacją

Profilowanie eksploruje czas spędzony w aplikacji. Visual Studio obsługuje profilowanie za pomocą interpreterów opartych na języku CPython i zawiera możliwość porównywania wydajności między różnymi przebiegami profilowania.

[![Wyniki profilera programu Visual Studio dla projektu języka Python](media/profiling-results.png)](media/profiling-results.png#lightbox)

Więcej informacji:

- Dokumenty: [narzędzia do profilowania języka Python](profiling-python-code-in-visual-studio.md)
- Dokumenty funkcji programu Ogólne programu Visual Studio: [Przewodnik funkcji profilowania](../profiling/profiling-feature-tour.md). (Nie wszystkie funkcje profilowania programu Visual Studio są dostępne dla języka Python).

## <a name="unit-testing-tools"></a>Narzędzia do testowania jednostek

Odnajduj, uruchom i zarządzaj testami w **Eksploratorze testów**programu Visual Studio i łatwo debuguj testy jednostkowe.

![Debugowanie testu jednostkowego języka Python w programie Visual Studio](media/unit-test-debugging.png)

Więcej informacji:

- Dokumenty: [Narzędzia do testowania jednostek dla języka Python](unit-testing-python-in-visual-studio.md)
- Dokumenty funkcji programu Visual Studio ogólne: [jednostka testuj kod](../test/unit-test-your-code.md).

## <a name="azure-sdk-for-python"></a>Zestaw Azure SDK dla środowiska Python

Biblioteki platformy Azure dla języka Python upraszczają korzystanie z usług platformy Azure z aplikacji windows, Mac OS X i Linux. Można ich używać do tworzenia zasobów platformy Azure i zarządzania nimi, a także do łączenia się z usługami platformy Azure. 

Aby uzyskać więcej informacji, zobacz [Zestaw SDK platformy Azure dla języka Python](/azure/python/) i [biblioteki platformy Azure dla języka Python](/azure/python/python-sdk-azure-overview) .

## <a name="questions-and-answers"></a>Pytania i odpowiedzi

**P. Czy obsługa języka Python jest dostępna w programie Visual Studio dla komputerów Mac?**

A. Nie w tej chwili, ale można się głosować wniosek na [Społeczność programistów](https://developercommunity.visualstudio.com/content/idea/351820/python-tools-for-visual-studio-mac.html). Dokumentacja [programu Visual Studio dla komputerów Mac](/visualstudio/mac/) identyfikuje bieżące typy rozwoju, które obsługuje. W międzyczasie program Visual Studio Code w systemach Windows, Mac i Linux [działa dobrze z Pythonem za pośrednictwem dostępnych rozszerzeń.](https://code.visualstudio.com/docs/languages/python)

**P. Czego można użyć do tworzenia interfejsu użytkownika w pythonie?**

A. Główną ofertą w tej dziedzinie jest [Qt Project,](https://www.qt.io/qt-for-application-development/)z powiązaniami dla Pythona znanego jako [PySide (oficjalne powiązanie)](https://wiki.qt.io/PySide) (patrz również [pliki do pobrania PySide)](https://download.qt.io/official_releases/pyside/.)i [PyQt](https://wiki.python.org/moin/PyQt). Obecnie obsługa języka Python w programie Visual Studio nie zawiera żadnych określonych narzędzi do tworzenia interfejsu użytkownika.

**P. Czy projekt języka Python może tworzyć autonomiczny plik wykonywalny?**

A. Python jest zazwyczaj językiem interpretowanym, za pomocą którego kod jest uruchamiany na żądanie w odpowiednim środowisku obsługującym język Python, takim jak Visual Studio i serwery sieci web. Visual Studio sam obecnie nie zapewnia środków do tworzenia autonomicznego pliku wykonywalnego, co zasadniczo oznacza program z wbudowanym interpreterem Języka Python. Jednak społeczność Języka Python dostarczyła różne środki do tworzenia plików wykonywalnych, zgodnie z opisem w [StackOverflow](https://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency). CPython obsługuje również osadzanie w aplikacji natywnej, zgodnie z opisem w blogu, [Korzystanie z osadzonego pliku zip CPython.](https://devblogs.microsoft.com/python/cpython-embeddable-zip-file/)

::: moniker range="<=vs-2017"

## <a name="feature-support"></a>Obsługa funkcji

Funkcje języka Python można zainstalować w następujących wersjach programu Visual Studio, zgodnie z opisem w [podręczniku instalacji:](installing-python-support-in-visual-studio.md)

- [Visual Studio 2019 (wszystkie wersje)](https://visualstudio.microsoft.com/vs/)
- Visual Studio 2017 (wszystkie wersje)
- Visual Studio 2015 (wszystkie wersje)
- Visual Studio 2013 Wersja społecznościowa
- Visual Studio 2013 Express for Web, Aktualizacja 2 lub nowsza
- Visual Studio 2013 Express dla komputerów stacjonarnych, aktualizacja 2 lub nowsza
- Visual Studio 2013 (wersja Pro lub nowsza)
- Visual Studio 2012 (wersja Pro lub nowsza)
- Visual Studio 2010 z sp1 (wymagana wersja Pro lub wyższa; .NET 4.5)

Program Visual Studio 2015 i starsze są dostępne w [visualstudio.microsoft.com/vs/older-downloads/](https://visualstudio.microsoft.com/vs/older-downloads/).

> [!Important]
> Funkcje są w pełni obsługiwane i obsługiwane tylko dla najnowszej wersji programu Visual Studio. Funkcje są dostępne w starszych wersjach, ale nie są aktywnie obsługiwane.

|          Obsługa języka Python          |   2017 r....   |   2015   | 2013 Kom. | Pulpit 2013 | 2013 Sieć Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|----------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|   Zarządzanie wieloma interpretatorami   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Automatyczne wykrywanie popularnych tłumaczy ustnych | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|     Dodawanie niestandardowych interpreterów      | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Środowiska wirtualne       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|         Pip/Łatwa instalacja         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|         System projektu         |   2017 r....   |   2015   | 2013 Kom. | Pulpit 2013 | 2013 Sieć Web | 2013 Pro+ |      2012 Pro+       | 2010 SP1 Pro+ |
|--------------------------------|----------|----------|-----------|--------------|----------|-----------|----------------------|---------------|
| Nowy projekt z istniejącego kodu | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  |       &#10004;       |   &#10004;    |
|         Pokaż wszystkie pliki         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  |       &#10004;       |   &#10004;    |
|         Kontrola źródła         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  |       &#10004;       |   &#10004;    |
|        Integracja z usługą Git         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;<sup>1</sup> |   &#10007;    |

<br/>

|           Edytowanie            |   2017 r....   |   2015   | 2013 Kom. | Pulpit 2013 | 2013 Sieć Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|     Wyróżnianie składni      | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        Autouzupełnianie         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        Pomoc dotycząca podpisu        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|          Szybkie informacje          | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|  Przeglądarka obiektów/widok klasy   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        Pasek nawigacyjny        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Przejdź do definicji       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|         Przejdź do          | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|     Znajdź wszystkie odwołania      | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Automatyczne wcięcie       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Formatowanie kodu        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|      Refaktoryzator — zmiana nazwy       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|  Refaktoryzator - metoda wyodrębniania   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Refaktoryzator - dodawanie/usuwanie importu | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|            PyLint ( PyLint )            | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|     Okno interaktywne     |   2017 r....   |   2015   | 2013 Kom. | Pulpit 2013 | 2013 Sieć Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|----------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|     Okno interaktywne     | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| IPython z wbudowanymi wykresami | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|               Aplikacje klasyczne               |   2017 r....   |   2015   | 2013 Kom. | Pulpit 2013 | 2013 Sieć Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|-------------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|     Aplikacja konsoli/systemu Windows     | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| IronPython WPF (z projektantem XAML) | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|      Formularze systemu Windows IronPython       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|         sieć Web         |   2017 r....   |   2015   | 2013 Kom. | Pulpit 2013 | 2013 Sieć Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|---------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
| Projekt internetowy Django  | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Projekt sieci butelek  | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|  Projekt sieciowy kolby  | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Ogólny projekt internetowy | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|         Azure          |   2017 r....   |   2015   | 2013 Kom. | Pulpit 2013 |       2013 Sieć Web       |      2013 Pro+       |      2012 Pro+       |    2010 SP1 Pro+     |
|------------------------|----------|----------|-----------|--------------|----------------------|----------------------|----------------------|----------------------|
|   Wdrażanie w witrynie sieci Web   | &#10004; | &#10004; | &#10004;  |   &#10007;   |       &#10004;       |       &#10004;       |       &#10004;       | &#10004;<sup>2</sup> |
|   Wdrażanie w roli sieci Web   | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> |       &#10007;       |
| Wdrażanie do roli pracownika  |    ?     |    ?     |     ?     |   &#10007;   | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> |       &#10007;       |
| Uruchamianie emulatora platformy Azure  |    ?     |    ?     |     ?     |   &#10007;   | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> |       &#10007;       |
|    Debugowanie zdalne    | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>6</sup> | &#10004;<sup>8</sup> | &#10004;<sup>8</sup> |       &#10007;       |
| Dołącz Eksploratora serwera | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>7</sup> | &#10004;<sup>7</sup> |       &#10007;       |       &#10007;       |

<br/>

|           Szablony Django           |   2017 r....   |   2015   | 2013 Kom. | Pulpit 2013 |       2013 Sieć Web       |      2013 Pro+       | 2012 Pro+ | 2010 SP1 Pro+ |
|--------------------------------------|----------|----------|-----------|--------------|----------------------|----------------------|-----------|---------------|
|              Debugging               | &#10004; | &#10004; | &#10004;  |   &#10007;   |       &#10004;       |       &#10004;       | &#10004;  |   &#10004;    |
|            Autouzupełnianie             | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10004;  |   &#10004;    |
| Automatyczne uzupełnianie dla CSS i JavaScript | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10007;  |   &#10007;    |

<br/>

|                  Debugging                  |   2017 r....   |   2015   | 2013 Kom. | Pulpit 2013 | 2013 Sieć Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|---------------------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|                  Debugging                  | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|         Debugowanie bez projektu         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        Debugowanie — dołączanie do edycji        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10007; | &#10004;  | &#10004;  |   &#10004;    |
|            Debugowanie w trybie mieszanym             | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |
| Zdalne debugowanie (Windows, Mac OS X, Linux) | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10007; | &#10004;  | &#10004;  |   &#10004;    |
|          Okno Interaktywne debugowanie           | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

<a name="matrix-profiling"></a>

| Profilowanie |   2017 r....   |   2015   | 2013 Kom. | Pulpit 2013 | 2013 Sieć Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|-----------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
| Profilowanie | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10007; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|     Testowanie      |   2017 r....   |   2015   | 2013 Kom. | Pulpit 2013 | 2013 Sieć Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|---------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
| Eksplorator testów | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |
|   Uruchom test    | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |
|  Test debugowania   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |

<br/>

1. Obsługa git dla programu Visual Studio 2012 jest dostępna w rozszerzeniu Narzędzia programu Visual Studio dla Git, dostępne w [programie Visual Studio Marketplace.](https://marketplace.visualstudio.com/items?itemName=TFSPowerToolsTeam.VisualStudioToolsforGit)

1. Wdrożenie w witrynie azure w sieci Web wymaga [narzędzia Azure SDK dla platformy .NET 2.1 — Visual Studio 2010 z dodatku SP1](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VS2010SP1AzurePack.2E2.2E1.appids). Nowsze wersje nie obsługują programu Visual Studio 2010.

1. Obsługa roli sieci Web platformy Azure i roli procesu roboczego wymaga [pakietu Azure SDK dla platformy .NET 2.3 — VS 2012](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs11AzurePack.appids) lub nowszych.

1. Obsługa roli sieci Web platformy Azure i roli procesu roboczego wymaga [pakietu Azure SDK dla platformy .NET 2.3 — VS 2013](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs2013AzurePack.appids) lub nowszych.

1. Edytor szablonów Django w programie Visual Studio 2013 zawiera pewne znane problemy, które zostały rozwiązane przez zainstalowanie aktualizacji 2.

1. Wymaga systemu Windows 8 lub nowszego. Visual Studio 2013 Express dla sieci Web nie ma okna dialogowego **Dołącz do procesu,** ale zdalne debugowanie witryny sieci Azure w sieci Web jest nadal możliwe za pomocą polecenia **Dołącz debugera (Python)** w **Eksploratorze serwera**. Zdalne debugowanie wymaga [narzędzia Azure SDK dla platformy .NET 2.3 — Visual Studio 2013](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs2013AzurePack.appids) lub nowszego.

1. Wymaga systemu Windows 8 lub nowszego. **Polecenie Dołącz debugera (Python)** w **Eksploratorze serwera** wymaga [narzędzia Azure SDK dla platformy .NET 2.3 — Visual Studio 2013](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs2013AzurePack.appids) lub nowszego.

1. Wymaga systemu Windows 8 lub nowszego.
::: moniker-end

---
title: Obsługa języka Python w programie Visual Studio w systemie Windows
titleSuffix: ''
description: Podsumowanie funkcji języka Python w programie Visual Studio, dzięki czemu najlepszym środowiskiem IDE w języku Python w systemie Windows (znanym także jako Python Tools for Visual Studio, PTVS).
ms.date: 06/05/2019
ms.topic: overview
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 0283cb4332e9137550b74a85c38d7963f3c77a70
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99890477"
---
# <a name="work-with-python-in-visual-studio-on-windows"></a>Współpraca z językiem Python w programie Visual Studio w systemie Windows

Python to popularny język programowania, który jest niezawodny, elastyczny, łatwy do uczenia się, bezpłatny do użycia we wszystkich systemach operacyjnych i obsługiwany przez zarówno silną społeczność deweloperów, jak i wiele bezpłatnych bibliotek. Język Python obsługuje wszystkie rodzaje opracowywania, w tym aplikacje sieci Web, usługi sieci Web, aplikacje klasyczne, skrypty i obliczenia naukowe, a także jest używane przez wielu uniwersytetów, naukowców, specjalistycznych deweloperów i profesjonalnych deweloperów. Możesz dowiedzieć się więcej o języku [Python.org](https://www.python.org) i [Python dla początkujących](https://www.python.org/about/gettingstarted/).

Program Visual Studio to zaawansowane środowisko IDE języka Python w systemie Windows. Program Visual Studio zapewnia obsługę funkcji [Open Source](https://github.com/Microsoft/ptvs) dla języka Python za pomocą obciążeń związanych z **programowaniem** i analizą **danych** w języku Python (Visual Studio 2017 i nowszych) oraz rozszerzenia bezpłatnego Python Tools for Visual Studio (Visual Studio 2015 i starsze).

Język Python nie jest obecnie obsługiwany w Visual Studio dla komputerów Mac, ale jest dostępny na komputerach Mac i w systemie Linux za poorednictwem Visual Studio Code (zobacz [pytania i odpowiedzi](#questions-and-answers)).

Aby rozpocząć:

- Postępuj zgodnie z [instrukcjami instalacji](installing-python-support-in-visual-studio.md) , aby skonfigurować obciążenie języka Python.
- Zapoznaj się z możliwościami języka Python programu Visual Studio, korzystając z sekcji w tym artykule.
::: moniker range="vs-2017"
- Przejdź do jednego lub kilku przewodników Szybki Start, aby utworzyć projekt. Jeśli nie masz pewności, Zacznij od [utworzenia aplikacji internetowej z kolbą](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json).
::: moniker-end
::: moniker range=">=vs-2019"
- Przejdź do jednego lub kilku przewodników Szybki Start, aby utworzyć projekt. Jeśli nie masz pewności, Zacznij od [przewodnika Szybki Start: otwieranie i uruchamianie kodu w języku Python w folderze](quickstart-05-python-visual-studio-open-folder.md) lub [Tworzenie aplikacji sieci Web z kolbą](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json).
::: moniker-end
- Wykonaj czynności opisane w samouczku dotyczącym [języka Python w programie Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md) , aby zapoznać się z kompleksowym doświadczeniem.

::: moniker range=">=vs-2019"
> [!Note]
> Program Visual Studio obsługuje język Python w wersji 2,7, a także wersję 3,5 do 3,7. Chociaż można użyć programu Visual Studio do edycji kodu pisanego w innych wersjach języka Python, te wersje nie są oficjalnie obsługiwane, a funkcje takie jak IntelliSense i debugowanie mogą nie zadziałać. Obsługa języka Python w wersji 3,8 jest nadal w fazie opracowywania. Szczegółowe informacje na temat pomocy technicznej można zobaczyć w tym [problemie związanym ze](https://github.com/microsoft/PTVS/issues/5822)śledzeniem w witrynie GitHub.
::: moniker-end

## <a name="support-for-multiple-interpreters"></a>Obsługa wielu interpreterów

Okno **środowiska Python** programu Visual Studio (pokazane poniżej w szerokim widoku rozszerzonym) oferuje jedno miejsce do zarządzania wszystkimi globalnymi środowiskami języka Python, środowiskami Conda i środowiskami wirtualnymi. Program Visual Studio automatycznie wykrywa instalacje języka Python w standardowych lokalizacjach i pozwala na konfigurowanie instalacji niestandardowych. W każdym środowisku można łatwo zarządzać pakietami, otwierać okno interaktywne dla tego środowiska i uzyskiwać dostęp do folderów środowiska.

::: moniker range="vs-2017"
![Rozwinięty Widok okna środowiska Python](media/environments/environments-expanded-view.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Rozwinięty Widok okna środowiska Python](media/environments/environments-expanded-view-2019.png)
::: moniker-end

Użyj polecenia **Otwórz okno interaktywne, aby interaktywnie** uruchomić środowisko Python w kontekście programu Visual Studio. Użyj polecenia **Otwórz w programie PowerShell** , aby otworzyć osobne okno polecenia w folderze wybranego środowiska. Z tego okna polecenia można uruchomić dowolny skrypt języka Python.

Więcej informacji:

- [Zarządzanie środowiskami języka Python](managing-python-environments-in-visual-studio.md)
- [Dokumentacja środowisk Python](python-environments-window-tab-reference.md)

## <a name="rich-editing-intellisense-and-code-comprehension"></a>Zaawansowane edytowanie, IntelliSense i zrozumienie kodu

Program Visual Studio oferuje pierwszy, jednostronicowy Edytor Python, w tym kolorowanie składni, Autouzupełnianie całego kodu i bibliotek, formatowanie kodu, pomoc w sygnaturach, refaktoryzację, Zaznaczanie błędów i wskazówki dotyczące typów. Program Visual Studio udostępnia również unikatowe funkcje, takie jak widok klasy, **Przejdź do definicji**, **Znajdź wszystkie odwołania** i fragmenty kodu. Bezpośrednia integracja z [oknem interaktywnym](#interactive-window) pomaga szybko opracowywać kod języka Python, który został już zapisany w pliku.

![Uzupełnianie kodu dla kodu Python w programie Visual Studio](media/code-editing-completions-simple.png)

Więcej informacji:

- Docs: [Edytowanie kodu](editing-python-code-in-visual-studio.md) w języku Python
- Docs: [Formatuj kod](formatting-python-code.md)
- Docs: [kod refaktoryzacji](refactoring-python-code.md)
- Dokumentacja: [Korzystanie z Linter](linting-python-code.md)
- Ogólna dokumentacja funkcji programu Visual Studio: [funkcje edytora kodu](../ide/writing-code-in-the-code-and-text-editor.md)

## <a name="interactive-window"></a>Okno interaktywne

W przypadku każdego środowiska Python znanego dla programu Visual Studio można łatwo otworzyć to samo środowisko interaktywne (REPL) dla interpretera języka Python bezpośrednio w programie Visual Studio, zamiast używać oddzielnego wiersza polecenia. Możesz również łatwo przełączać się między środowiskami. (Aby otworzyć osobnym wierszu polecenia, wybierz odpowiednie środowisko w oknie środowiska języka **Python** , a następnie wybierz polecenie **Otwórz w programie PowerShell** , jak wyjaśniono wcześniej w obszarze [Obsługa wielu interpreterów](#support-for-multiple-interpreters)).

![Okno interaktywne języka Python w programie Visual Studio](media/interactive-window.png)

Program Visual Studio zapewnia także ścisłą integrację między edytorem kodu w języku Python a oknem **interaktywnym** . Skrót klawiaturowy **klawisza Ctrl** +  wygodnie wysyła bieżący wiersz kodu (lub blok kodu) w edytorze do okna **interaktywnego** , a następnie przechodzi do następnego wiersza (lub bloku). **Ctrl** + **Klawisz ENTER** umożliwia łatwe przechodzenie przez kod bez konieczności uruchamiania debugera. Możesz również wysłać zaznaczony kod do okna **interaktywnego** z tym samym naciśnięciem klawisza i z łatwością wkleić kod z okna **interaktywnego** do edytora. Ponadto te funkcje umożliwiają wykonywanie szczegółowych informacji o segmencie kodu w oknie **interaktywnym** i łatwe zapisywanie wyników w pliku w edytorze.

Program Visual Studio obsługuje również IPython/Jupyter w REPL, w tym wykresy wbudowane, .NET i Windows Presentation Foundation (WPF).

Więcej informacji:

- [Okno interaktywne](python-interactive-repl-in-visual-studio.md)
- [IPython w programie Visual Studio](interactive-repl-ipython.md)

## <a name="project-system-and-project-and-item-templates"></a>System projektu i szablony projektów i elementów

::: moniker range=">=vs-2019"
> [!Note]
> Program Visual Studio 2019 obsługuje Otwieranie folderu zawierającego kod języka Python i uruchamianie tego kodu bez tworzenia plików projektu i rozwiązania programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Szybki Start: otwieranie i uruchamianie kodu w języku Python w folderze](quickstart-05-python-visual-studio-open-folder.md). Istnieją jednak zalety korzystania z pliku projektu, zgodnie z opisem w tej sekcji.
::: moniker-end

Program Visual Studio ułatwia zarządzanie złożonością projektu w miarę ich wzrostu. *Projekt programu Visual Studio* jest znacznie więcej niż struktura folderów: zawiera informacje na temat sposobu używania różnych plików i sposobu ich powiązania ze sobą. Program Visual Studio ułatwia odróżnienie kodu aplikacji, kodu testowego, stron sieci Web, języka JavaScript, skryptów kompilacji itd., a następnie włączenie funkcji odpowiednich dla plików. Rozwiązanie programu Visual Studio ułatwia również zarządzanie wieloma powiązanymi projektami, takimi jak projekt Python i projekt rozszerzenia C++.

![Rozwiązanie programu Visual Studio zawierające zarówno projekty języka Python, jak i C++](media/projects-solution-explorer-two-projects.png)

Szablony projektów i elementów automatyzują proces konfigurowania różnych typów projektów i plików, co pozwala zaoszczędzić cenny czas i co uwalnia od zarządzania intricateami i podatnymi na błędy. Program Visual Studio udostępnia szablony dla sieci Web, platformy Azure, analizy danych, konsoli i innych typów projektów, a także szablony plików, takich jak klasy Python, testy jednostkowe, konfiguracja sieci Web platformy Azure, HTML, a nawet aplikacje Django.

[![Szablony projektów i elementów języka Python w programie Visual Studio](media/project-and-item-templates.png)](media/project-and-item-templates.png#lightbox)

Więcej informacji:

- Docs: [Zarządzanie projektami Python](managing-python-projects-in-visual-studio.md)
- Docs: [Dokumentacja szablonów elementów](python-item-templates.md)
- Docs: [Szablony projektów języka Python](managing-python-projects-in-visual-studio.md#project-templates)
- Docs: [współpraca z językami C++ i Python](working-with-c-cpp-python-in-visual-studio.md)
- Ogólne dokumenty funkcji programu Visual Studio: [Szablony projektów i elementów](../ide/creating-project-and-item-templates.md#visual-studio-templates)
- Dokumentacja funkcji ogólnych programu Visual Studio: [rozwiązania i projekty w programie Visual Studio](../ide/solutions-and-projects-in-visual-studio.md)

## <a name="full-featured-debugging"></a>W pełni funkcjonalne debugowanie

Jedną z zalet programu Visual Studio jest zaawansowany debuger. W szczególności w języku Python program Visual Studio obejmuje debugowanie w trybie mieszanym Python/C++, zdalne debugowanie w systemie Linux, debugowanie w oknie **interaktywnym** i debugowanie testów jednostkowych w języku Python.

![Debuger programu Visual Studio dla języka Python przedstawiający okno podręczne wyjątku](media/debugging-exception-popup.png)

::: moniker range=">=vs-2019"
W programie Visual Studio 2019 można uruchamiać i debugować kod bez pliku projektu programu Visual Studio. Aby uzyskać przykład, zobacz [Szybki Start: otwieranie i uruchamianie kodu w języku Python w folderze](quickstart-05-python-visual-studio-open-folder.md) .
::: moniker-end

Więcej informacji:

- Docs: [Debugowanie języka Python](debugging-python-in-visual-studio.md)
- Dokumenty: [debugowanie w trybie mieszanym Python/C++](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)
- Dokumentacja: [zdalne debugowanie w systemie Linux](debugging-python-code-on-remote-linux-machines.md)
- Ogólna dokumentacja funkcji programu Visual Studio: [Przewodnik po funkcjach debugera programu Visual Studio](../debugger/debugger-feature-tour.md)

## <a name="profiling-tools-with-comprehensive-reporting"></a>Narzędzia profilowania z kompleksowym raportowaniem

Profilowanie analizuje sposób, w jaki czas jest poświęcany na aplikację. Program Visual Studio obsługuje profilowanie przy użyciu interpreterów opartych na CPython i oferuje możliwość porównania wydajności między różnymi przebiegami profilowania.

[![Wyniki programu Visual Studio profiler dla projektu języka Python](media/profiling-results.png)](media/profiling-results.png#lightbox)

Więcej informacji:

- Docs: [narzędzia profilowania języka Python](profiling-python-code-in-visual-studio.md)
- Ogólna dokumentacja funkcji programu Visual Studio: [profilowanie przewodnika](../profiling/profiling-feature-tour.md)dotyczącego funkcji. (Nie wszystkie funkcje profilowania programu Visual Studio są dostępne dla języka Python).

## <a name="unit-testing-tools"></a>Narzędzia do testowania jednostkowego

Wykrywaj i uruchamiaj testy w programie Visual Studio **Test Explorer** oraz łatwo Debuguj testy jednostkowe.

![Debugowanie testów jednostkowych w języku Python w programie Visual Studio](media/unit-test-debugging.png)

Więcej informacji:

- Docs: [Narzędzia do testowania jednostkowego dla języka Python](unit-testing-python-in-visual-studio.md)
- Ogólna dokumentacja funkcji programu Visual Studio: [testowanie jednostkowe kodu](../test/unit-test-your-code.md).

## <a name="azure-sdk-for-python"></a>Zestaw Azure SDK dla środowiska Python

Biblioteki platformy Azure dla języka Python upraszczają używanie usług platformy Azure z poziomu aplikacji systemu Windows, Mac OS X i Linux. Można ich używać do tworzenia zasobów platformy Azure i zarządzania nimi, a także do nawiązywania połączeń z usługami platformy Azure. 

Aby uzyskać więcej informacji, zobacz [zestaw Azure SDK dla języka Python](/azure/python/) i [bibliotek platformy Azure dla języka Python](/azure/python/python-sdk-azure-overview) .

## <a name="questions-and-answers"></a>Pytania i odpowiedzi

**Pytania. Czy obsługa języka Python jest dostępna z Visual Studio dla komputerów Mac?**

A. Nie jest to możliwe, ale możesz zagłosować na żądanie w [społeczności deweloperów](https://developercommunity.visualstudio.com/content/idea/351820/python-tools-for-visual-studio-mac.html). Dokumentacja [Visual Studio dla komputerów Mac](/visualstudio/mac/) identyfikuje bieżące typy rozwoju, które obsługuje. W międzyczasie Visual Studio Code w systemach Windows, Mac i Linux [działają dobrze w języku Python za pomocą dostępnych rozszerzeń](https://code.visualstudio.com/docs/languages/python).

**Pytania. Czego można użyć do kompilowania interfejsu użytkownika przy użyciu języka Python?**

A. Główną ofertą w tym obszarze jest [projekt QT](https://www.qt.io/qt-for-application-development/)z powiązaniami dla języka Python znanego [jako pyside (oficjalne powiązanie)](https://wiki.qt.io/PySide) (Zobacz też [pobieranie pyside](https://download.qt.io/official_releases/pyside/.)) i [PyQt](https://wiki.python.org/moin/PyQt). W tej chwili obsługa języka Python w programie Visual Studio nie obejmuje żadnych konkretnych narzędzi do tworzenia interfejsu użytkownika.

**Pytania. Czy projekt w języku Python tworzy autonomiczny plik wykonywalny?**

A. Język Python jest ogólnie interpretowany, za pomocą którego kod jest uruchamiany na żądanie w odpowiednim środowisku z obsługą języka Python, takim jak Visual Studio i serwery sieci Web. Sam program Visual Studio nie zapewnia środków do utworzenia autonomicznego pliku wykonywalnego, co zasadniczo oznacza program z osadzonym interpreterem języka Python. Jednak społeczność języka Python dostarczyła różne metody tworzenia plików wykonywalnych zgodnie z opisem w [StackOverflow](https://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency). CPython obsługuje również osadzanie w aplikacji natywnej, zgodnie z opisem w wpisie w blogu, [przy użyciu pliku zip](https://devblogs.microsoft.com/python/cpython-embeddable-zip-file/)z możliwością osadzenia CPython.

::: moniker range="<=vs-2017"

## <a name="feature-support"></a>Obsługa funkcji

Funkcje języka Python można zainstalować w następujących wersjach programu Visual Studio, zgodnie z opisem w [przewodniku instalacji](installing-python-support-in-visual-studio.md):

- [Visual Studio 2019 (wszystkie wersje)](https://visualstudio.microsoft.com/vs/)
- Visual Studio 2017 (wszystkie wersje)
- Visual Studio 2015 (wszystkie wersje)
- Visual Studio 2013 wersja Community
- Visual Studio 2013 Express for Web, Update 2 lub nowszy
- Visual Studio 2013 Express for Desktop, aktualizacja 2 lub nowsza
- Visual Studio 2013 (wersja Pro lub nowsza)
- Visual Studio 2012 (wersja Pro lub nowsza)
- Visual Studio 2010 z dodatkiem SP1 (Pro Edition lub nowszy; wymagany jest program .NET 4,5)

Program Visual Studio 2015 i jego starsze wersje są dostępne pod adresem [VisualStudio.Microsoft.com/vs/older-downloads/](https://visualstudio.microsoft.com/vs/older-downloads/).

> [!Important]
> Funkcje są w pełni obsługiwane i obsługiwane tylko dla najnowszej wersji programu Visual Studio. Funkcje są dostępne we wcześniejszych wersjach, ale nie są aktywnie obsługiwane.

|          Obsługa języka Python          |   2017 +   |   2015   | 2013 comm | 2013 Desktop | 2013 Web | 2013 Pro + | 2012 Pro + | 2010 SP1 Pro + |
|----------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|   Zarządzanie wieloma interpreterami   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Automatycznie wykrywaj popularne interpretery | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|     Dodawanie interpreterów niestandardowych      | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Środowiska wirtualne       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|         PIP/łatwa instalacja         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|         System projektu         |   2017 +   |   2015   | 2013 comm | 2013 Desktop | 2013 Web | 2013 Pro + |      2012 Pro +       | 2010 SP1 Pro + |
|--------------------------------|----------|----------|-----------|--------------|----------|-----------|----------------------|---------------|
| Nowy projekt z istniejącego kodu | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  |       &#10004;       |   &#10004;    |
|         Pokaż wszystkie pliki         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  |       &#10004;       |   &#10004;    |
|         Kontrola źródła         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  |       &#10004;       |   &#10004;    |
|        Integracja z usługą Git         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;<sup>1</sup> |   &#10007;    |

<br/>

|           Edytowanie            |   2017 +   |   2015   | 2013 comm | 2013 Desktop | 2013 Web | 2013 Pro + | 2012 Pro + | 2010 SP1 Pro + |
|------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|     Podświetlanie składni      | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        Autouzupełnianie         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        Pomoc dotycząca podpisu        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|          Szybkie informacje          | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|  Przeglądarka obiektów/Widok klas   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        Pasek nawigacyjny        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Przejdź do definicji       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|         Przejdź do strony           | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|     Znajdź wszystkie odwołania      | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Automatyczne wcięcia       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Formatowanie kodu        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|      Refaktoryzacja — Zmień nazwę       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|  Refaktoryzacja — Metoda Extract   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Refaktoryzacja — Dodawanie/usuwanie importu | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|            PyLint            | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|     Okno interaktywne     |   2017 +   |   2015   | 2013 comm | 2013 Desktop | 2013 Web | 2013 Pro + | 2012 Pro + | 2010 SP1 Pro + |
|----------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|     Okno interaktywne     | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| IPython z wykresami wbudowanymi | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|               Klasyczna               |   2017 +   |   2015   | 2013 comm | 2013 Desktop | 2013 Web | 2013 Pro + | 2012 Pro + | 2010 SP1 Pro + |
|-------------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|     Konsola/aplikacja systemu Windows     | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| IronPython WPF (z projektantem XAML) | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|      IronPython Windows Forms       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|         Internet         |   2017 +   |   2015   | 2013 comm | 2013 Desktop | 2013 Web | 2013 Pro + | 2012 Pro + | 2010 SP1 Pro + |
|---------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
| Projekt sieci Web Django  | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Projekt sieci Web butelek  | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|  Przednie projektu sieci Web  | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Ogólny projekt sieci Web | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|         Azure          |   2017 +   |   2015   | 2013 comm | 2013 Desktop |       2013 Web       |      2013 Pro +       |      2012 Pro +       |    2010 SP1 Pro +     |
|------------------------|----------|----------|-----------|--------------|----------------------|----------------------|----------------------|----------------------|
|   Wdróż w witrynie sieci Web   | &#10004; | &#10004; | &#10004;  |   &#10007;   |       &#10004;       |       &#10004;       |       &#10004;       | &#10004;<sup>2</sup> |
|   Wdróż w roli sieci Web   | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> |       &#10007;       |
| Wdróż w roli procesu roboczego  |    ?     |    ?     |     ?     |   &#10007;   | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> |       &#10007;       |
| Uruchom w emulatorze platformy Azure  |    ?     |    ?     |     ?     |   &#10007;   | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> |       &#10007;       |
|    Debugowanie zdalne    | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>6</sup> | &#10004;<sup>8</sup> | &#10004;<sup>8</sup> |       &#10007;       |
| Dołącz Eksplorator serwera | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>7</sup> | &#10004;<sup>7</sup> |       &#10007;       |       &#10007;       |

<br/>

|           Szablony Django           |   2017 +   |   2015   | 2013 comm | 2013 Desktop |       2013 Web       |      2013 Pro +       | 2012 Pro + | 2010 SP1 Pro + |
|--------------------------------------|----------|----------|-----------|--------------|----------------------|----------------------|-----------|---------------|
|              Debugowanie               | &#10004; | &#10004; | &#10004;  |   &#10007;   |       &#10004;       |       &#10004;       | &#10004;  |   &#10004;    |
|            Autouzupełnianie             | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10004;  |   &#10004;    |
| Autouzupełnianie dla CSS i JavaScript | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10007;  |   &#10007;    |

<br/>

|                  Debugowanie                  |   2017 +   |   2015   | 2013 comm | 2013 Desktop | 2013 Web | 2013 Pro + | 2012 Pro + | 2010 SP1 Pro + |
|---------------------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|                  Debugowanie                  | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|         Debugowanie bez projektu         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        Debugowanie — dołączanie do edycji        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10007; | &#10004;  | &#10004;  |   &#10004;    |
|            Debugowanie w trybie mieszanym             | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |
| Zdalne debugowanie (Windows, Mac OS X, Linux) | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10007; | &#10004;  | &#10004;  |   &#10004;    |
|          Debuguj okno interaktywne           | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

<a name="matrix-profiling"></a>

| Profilowanie |   2017 +   |   2015   | 2013 comm | 2013 Desktop | 2013 Web | 2013 Pro + | 2012 Pro + | 2010 SP1 Pro + |
|-----------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
| Profilowanie | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10007; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|     Testowanie      |   2017 +   |   2015   | 2013 comm | 2013 Desktop | 2013 Web | 2013 Pro + | 2012 Pro + | 2010 SP1 Pro + |
|---------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
| Eksplorator testów | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |
|   Uruchom test    | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |
|  Debuguj test   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |

<br/>

1. Obsługa usługi git dla programu Visual Studio 2012 jest dostępna w Visual Studio Tools dla rozszerzenia git dostępnego na [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=TFSPowerToolsTeam.VisualStudioToolsforGit).

1. Wdrożenie w witrynie sieci Web systemu Azure wymaga [zestawu Azure SDK dla programu .net 2,1 — Visual Studio 2010 z dodatkiem SP1](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VS2010SP1AzurePack.2E2.2E1.appids). Nowsze wersje nie obsługują programu Visual Studio 2010.

1. Obsługa roli sieci Web i roli procesu roboczego platformy Azure wymaga [zestawu Azure SDK dla programu .net 2,3 — VS 2012](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs11AzurePack.appids) lub nowszego.

1. Obsługa roli sieci Web i roli procesu roboczego platformy Azure wymaga [zestawu Azure SDK dla programu .net 2,3 — VS 2013](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs2013AzurePack.appids) lub nowszego.

1. Edytor szablonów Django w Visual Studio 2013 zawiera znane problemy, które zostały rozwiązane przez zainstalowanie aktualizacji Update 2.

1. Wymaga systemu Windows 8 lub nowszego. Visual Studio 2013 Express for Web nie ma okna dialogowego **Dołącz do procesu** , ale zdalne debugowanie witryny sieci Web systemu Azure jest nadal możliwe przy użyciu polecenia **Dołącz debuger (Python)** w **Eksplorator serwera**. Zdalne debugowanie wymaga [zestawu Azure SDK dla programu .net 2,3 — Visual Studio 2013](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs2013AzurePack.appids) lub nowszego.

1. Wymaga systemu Windows 8 lub nowszego. Polecenie **Attach Debugger (Python)** w **Eksplorator serwera** wymaga [zestawu Azure SDK dla programu .NET 2,3 — Visual Studio 2013](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs2013AzurePack.appids) lub nowszego.

1. Wymaga systemu Windows 8 lub nowszego.
::: moniker-end

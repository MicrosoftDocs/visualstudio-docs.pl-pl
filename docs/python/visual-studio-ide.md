---
title: Omówienie programu Visual Studio dla deweloperów języka Python
titleSuffix: ''
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
dev_langs:
- Python
ms.workload:
- python
- data-science
ms.openlocfilehash: 8b8b656aaefe4440e811378da2b84d1b944d4fb1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "73661934"
---
# <a name="welcome-to-the-visual-studio-ide--python"></a>Środowisko IDE programu Visual Studio | Python

*Zintegrowane środowisko programistyczne* programu Visual Studio to kreatywna klawiatura uruchamiania dla języka Python (i innych języków), której można używać do edytowania, debugowania i testowania kodu, a następnie publikowania aplikacji. Zintegrowane środowisko programistyczne (IDE) to bogaty w funkcje program, który może być używany do wielu aspektów tworzenia oprogramowania. Poza standardowym edytorem i debugerem, które zapewnia większość środowisk IDE, program Visual Studio zawiera narzędzia do uzupełniania kodu, interaktywne środowiska REPL i inne funkcje ułatwiające proces tworzenia oprogramowania.

[![Visual Studio z projektem Języka Python](media/tour-ide-overview.png)](media/tour-ide-overview.png#lightbox)

Ten obraz przedstawia program Visual Studio z otwartym projektem Języka Python i kilkoma kluczowymi oknami narzędzi, których prawdopodobnie użyjesz:

- [**Eksplorator rozwiązań**](../ide/solutions-and-projects-in-visual-studio.md) (w prawym górnym rogu) umożliwia wyświetlanie, nawigację i zarządzanie plikami kodu. **Eksplorator rozwiązań** może pomóc w zorganizowaniu kodu, grupując pliki w [rozwiązania i projekty.](../get-started/tutorial-projects-solutions.md)
  - Obok **Eksploratora rozwiązań** jest [**Środowisko Pythona,**](managing-python-environments-in-visual-studio.md)w którym zarządzasz różnymi interpreterami Języka Python zainstalowanymi na komputerze.

  ::: moniker range=">=vs-2019"
  - Można również otworzyć i uruchomić kod języka Python w folderze bez tworzenia plików projektu i rozwiązania programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Szybki start: Otwieranie i uruchamianie kodu języka Python w folderze](quickstart-05-python-visual-studio-open-folder.md).
  ::: moniker-end

- [Okno edytora](../ide/writing-code-in-the-code-and-text-editor.md) (w środku), w którym prawdopodobnie spędzisz większość czasu, wyświetla zawartość pliku. W tym miejscu [można edytować kod języka Python](editing-python-code-in-visual-studio.md), poruszać się w strukturze kodu i ustawić punkty przerwania podczas sesji debugowania. Za pomocą języka Python można również wybrać kod i nacisnąć klawisze Ctrl+Enter, aby uruchomić ten kod w [interaktywnym oknie REPL](python-interactive-repl-in-visual-studio.md).

- [Okno Dane wyjściowe](../ide/reference/output-window.md) (centrum dolnego rogu) to miejsce, w którym program Visual Studio wysyła powiadomienia, takie jak debugowanie i komunikaty o błędach, ostrzeżenia, komunikaty o stanie publikowania i inne. Każde źródło wiadomości ma własną kartę.
  - [Okno Interaktywne ZAWKLI](python-interactive-repl-in-visual-studio.md) W języku Python pojawia się w tym samym obszarze co okno Dane wyjściowe.

- [Team Explorer](/azure/devops/user-guide/work-team-explorer?view=vsts) (w prawym dolnym rogu) umożliwia śledzenie elementów roboczych i udostępnianie kodu innym osobom przy użyciu technologii kontroli wersji, takich jak [Git](https://git-scm.com/) i [Team Foundation Version Control (TFVC).](/azure/devops/repos/tfvc/overview?view=vsts)

## <a name="editions"></a>Wersje

Program Visual Studio jest dostępny dla systemów Windows i Mac; Jednak obsługa języka Python jest dostępna tylko w programie Visual Studio dla systemu Windows.

Istnieją trzy wersje programu Visual Studio w systemie Windows: Community, Professional i Enterprise. Zobacz [Porównanie identyfikatorów IDE programu Visual Studio,](https://visualstudio.microsoft.com/vs/compare/) aby dowiedzieć się, które funkcje są obsługiwane w każdej wersji.

## <a name="popular-productivity-features"></a>Popularne funkcje zwiększające produktywność

Niektóre z popularnych funkcji w programie Visual Studio, które pomagają być bardziej wydajne w miarę tworzenia oprogramowania obejmują:

- [IntelliSense](editing-python-code-in-visual-studio.md#intellisense)

   IntelliSense to termin dla zestawu funkcji, który wyświetla informacje o kodzie bezpośrednio w edytorze i, w niektórych przypadkach, zapis małych fragmentów kodu dla Ciebie. To tak, jakby mieć podstawową dokumentację w edytorze, co pozwala zaoszczędzić od konieczności wyszukiwania informacji o typie w innym miejscu. Funkcje IntelliSense różnią się w zależności od języka, a artykuł [o kodzie Edyting Python](editing-python-code-in-visual-studio.md#intellisense) zawiera szczegółowe informacje dotyczące języka Python. Na poniższej ilustracji pokazano, jak intellisense wyświetla listę członków dla danego typu:

   ![Ukończenie członkostwa za pomocą programu Visual Studio IntelliSense](media/code-editing-completions-simple.png)

- [Refaktoryzacja](refactoring-python-code.md)

   Klikając prawym przyciskiem myszy fragment kodu i wybierając **szybkie akcje i refaktoryzowania,** program Visual Studio zapewnia operacje, takie jak inteligentna zmiana nazwy zmiennych, wyodrębnianie jednego lub więcej wierszy kodu do nowej metody, zmiana kolejności parametrów metody i inne.

   ![Refaktoryzacja w programie Visual Studio](media/tour-ide-refactor-extract-method.png)

- [Zaznaczanie błędów](refactoring-python-code.md)

   Linting sprawdza błędy i typowe problemy w kodzie Pythona, zachęcając do dobrych wzorców kodowania Pythona.

   ![Polecenie PyLint w menu kontekstowym dla projektów języka Python](media/code-pylint-command.png)

- Pole wyszukiwania

   Visual Studio może wydawać się przytłaczające czasami z tak wielu menu, opcje i właściwości. Pole wyszukiwania to świetny sposób na szybkie znalezienie potrzebnych w programie Visual Studio. Po rozpoczęciu wpisywania nazwy czegoś, czego szukasz, Visual Studio wyświetla wyniki, które zajmą Cię dokładnie tam, gdzie musisz się udać. Jeśli chcesz dodać funkcje do programu Visual Studio, na przykład, aby dodać obsługę dodatkowego języka programowania, pole wyszukiwania zawiera wyniki, które otwierają Instalatora programu Visual Studio, aby zainstalować obciążenie lub pojedynczy składnik.

   ![Pole wyszukiwania w programie Visual Studio](media/tour-ide-quick-launch.png)

- Squiggles i [szybkie akcje](../ide/quick-actions.md)

   Squiggles są faliste podkreśla, że alerty o błędach lub potencjalnych problemów w kodzie podczas pisania. Te wskazówki wizualne umożliwiają natychmiastowe rozwiązywanie problemów bez oczekiwania na wykrycie błędu podczas kompilacji lub po uruchomieniu programu. Po umieszczeniu wskaźnika myszy na fali, zostaną wyświetlene dodatkowe informacje o błędzie. Żarówka może również pojawić się na lewym marginesie z akcjami, znanymi jako Szybkie akcje, aby naprawić błąd.

   ![Squiggles w programie Visual Studio](media/tour-ide-squiggles.png)

- [Przejdź do i zajrzyj do definicji](../ide/go-to-and-peek-definition.md)

   Funkcja **Przejdź do definicji** prowadzi bezpośrednio do lokalizacji, w której zdefiniowano funkcję lub typ. Polecenie **Definicje wglądu** wyświetla definicję w oknie bez otwierania oddzielnego pliku. Polecenie **Znajdź wszystkie odwołania** zapewnia również pomocny sposób odnalezienia, gdzie dany identyfikator jest zdefiniowany i używany.

   ![Polecenia nawigacji kodu](media/tour-ide-navigation-commands.png)

## <a name="powerful-features-for-python"></a>Zaawansowane funkcje dla Pythona

::: moniker range=">=vs-2019"
- [Uruchamianie kodu bez projektu](quickstart-05-python-visual-studio-open-folder.md)

    Począwszy od programu Visual Studio 2019, można otworzyć folder zawierający kod języka Python, aby korzystać z funkcji, takich jak IntelliSense i debugowania bez konieczności tworzenia projektu programu Visual Studio dla kodu.
::: moniker-end

- [Współpraca przy użyciu programu Visual Studio](/visualstudio/liveshare/)
  
    Visual Studio Live Share umożliwia wspólne edytowanie i debugowanie z innymi osobami w czasie rzeczywistym, niezależnie od języka programowania, którego używasz lub typów aplikacji, które budujesz. 

- [Interaktywny REPL Języka Python](python-interactive-repl-in-visual-studio.md)

    Visual Studio udostępnia interaktywne okno pętli odczytu i oceny i drukowania (REPL) dla każdego środowiska języka Python, co poprawia po REPL można uzyskać z *python.exe* w wierszu polecenia. W oknie **Interaktywna** można wprowadzić dowolny kod Języka Python i zobaczyć natychmiastowe wyniki.

    ![Okno interaktywne języka Python](media/interactive-window.png)

- [Debugging](debugging-python-in-visual-studio.md)

    Visual Studio zapewnia kompleksowe środowisko debugowania dla języka Python, w tym dołączanie do uruchomionych procesów, oceny wyrażeń w **oknach Czujka** i **Natychmiastowe,** sprawdzanie zmiennych lokalnych, punktów przerwania, instrukcji step in/out/over, **Ustaw następną instrukcję**i inne. Można również debugować zdalny kod Pythona uruchomiony na komputerach z systemem Linux.

    ![Debugowanie języka Python w programie Visual Studio](media/remote-debugging-breakpoint-hit.png)

- [Interakcja z językiem C++](working-with-c-cpp-python-in-visual-studio.md)

    Wiele bibliotek utworzonych dla języka Python są zapisywane w języku C++ dla optymalnej wydajności. Program Visual Studio zapewnia bogate możliwości tworzenia rozszerzeń języka C++, w tym [debugowania w trybie mieszanym.](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)

    ![Debugowanie w trybie mieszanym języka Python i C++ razem](media/mixed-mode-debugging.png)

- [Profilowania](profiling-python-code-in-visual-studio.md)

    Korzystając z interpretera opartego na CPython, można ocenić wydajność kodu języka Python w programie Visual Studio.

    ![Profilowanie raportu o skuteczności](media/profiling-results.png)

- [Testowanie jednostkowe](unit-testing-python-in-visual-studio.md)

    Visual Studio zapewnia zintegrowaną obsługę wykrywania, uruchamiania i debugowania testów jednostkowych w kontekście IDE.

    ![Testy jednostkowe pokazujące stan testu nie powiodło się](media/unit-test-A-fail.png)

## <a name="next-steps"></a>Następne kroki

Zapoznaj się z programem Python w programie Visual Studio, wykonując jeden z następujących przewodników Szybki start lub samouczków:

> [!div class="nextstepaction"]
> [Szybki start: tworzenie aplikacji internetowej za pomocą flask](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json)

> [!div class="nextstepaction"]
> [Praca z pythonem w programie Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

> [!div class="nextstepaction"]
> [Wprowadzenie do struktury sieci Web Django w programie Visual Studio](learn-django-in-visual-studio-step-01-project-and-solution.md)

> [!div class="nextstepaction"]
> [Wprowadzenie do struktury sieci Web Flask w programie Visual Studio](learn-flask-visual-studio-step-01-project-solution.md)

## <a name="see-also"></a>Zobacz też

- Odkryj [więcej funkcji programu Visual Studio](../ide/advanced-feature-overview.md)
- Odwiedź [visualstudio.microsoft.com](https://visualstudio.microsoft.com/vs/)
- Przeczytaj [blog programu Visual Studio](https://devblogs.microsoft.com/visualstudio/)

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
ms.openlocfilehash: 91f80d648450447a6ba0e80f10e5c39764445cef
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189309"
---
# <a name="welcome-to-the-visual-studio-ide--python"></a>Witamy w programie Visual Studio IDE | Python

*Zintegrowane środowisko programistyczne* programu Visual Studio to twórczy pad do uruchamiania dla języka Python (i innych języków), którego można użyć do edytowania, debugowania i testowania kodu, a następnie publikowania aplikacji. Zintegrowane środowisko programistyczne (IDE) to program bogaty w funkcje, który może być używany w wielu aspektach tworzenia oprogramowania. Poza standardowym edytorem i debugerem, który zapewnia większość środowisk IDE, program Visual Studio zawiera narzędzia do uzupełniania kodu, interaktywne środowiska REPL i inne funkcje ułatwiające proces tworzenia oprogramowania.

[![Visual Studio z projektem języka Python](media/tour-ide-overview.png)](media/tour-ide-overview.png#lightbox)

Ten obraz przedstawia program Visual Studio z otwartym projektem języka Python i kilkoma oknami narzędzi kluczowych, których prawdopodobnie używasz:

- [**Eksplorator rozwiązań**](../ide/solutions-and-projects-in-visual-studio.md) (prawy górny) umożliwia wyświetlanie plików kodu i nawigowanie w nich oraz zarządzanie nimi. **Eksplorator rozwiązań** może pomóc organizować kod przez zgrupowanie plików na [rozwiązania i projekty](../get-started/tutorial-projects-solutions.md).
  - Obok **Eksplorator rozwiązań** to [**środowiska Python**](managing-python-environments-in-visual-studio.md), w których są zarządzane różne interpretery języka Python, które są zainstalowane na komputerze.

  ::: moniker range=">=vs-2019"
  - Możesz również otworzyć i uruchomić kod Python w folderze bez tworzenia plików projektu i rozwiązania programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Szybki Start: otwieranie i uruchamianie kodu w języku Python w folderze](quickstart-05-python-visual-studio-open-folder.md).
  ::: moniker-end

- [Okno edytora](../ide/writing-code-in-the-code-and-text-editor.md) (środkowe), w którym najprawdopodobniej będzie można spędzać większość czasu, zostanie wyświetlona zawartość pliku. W tym miejscu można [edytować kod języka Python](editing-python-code-in-visual-studio.md), nawigować w strukturze kodu i ustawiać punkty przerwania podczas debugowania sesji. W języku Python można również wybrać kod i nacisnąć klawisze CTRL + ENTER, aby uruchomić ten kod w [interaktywnym oknie REPL](python-interactive-repl-in-visual-studio.md).

- W [oknie danych wyjściowych](../ide/reference/output-window.md) (u dołu) jest miejsce, gdzie program Visual Studio wysyła powiadomienia, takie jak debugowanie i komunikaty o błędach, ostrzeżenia, publikowanie komunikatów o stanie itd. Każde źródło wiadomości ma własną kartę.
  - [Okno interaktywnej REPL](python-interactive-repl-in-visual-studio.md) w języku Python pojawia się w tym samym obszarze co okno dane wyjściowe.

- [Team Explorer](/azure/devops/user-guide/work-team-explorer?view=vsts) (prawy dolny) umożliwia śledzenie elementów roboczych i udostępnianie kodu innym osobom korzystającym z technologii kontroli wersji, takich jak [git](https://git-scm.com/) i [Kontrola wersji serwera Team Foundation (TFVC)](/azure/devops/repos/tfvc/overview?view=vsts).

## <a name="editions"></a>Wersje

Program Visual Studio jest dostępny dla systemów Windows i Mac. jednak obsługa języka Python jest dostępna tylko w programie Visual Studio dla systemu Windows.

Istnieją trzy wersje programu Visual Studio w systemie Windows: Community, Professional i Enterprise. Zobacz [porównanie programu Visual Studio środowisk IDE](https://visualstudio.microsoft.com/vs/compare/) , aby dowiedzieć się, jakie funkcje są obsługiwane w poszczególnych wersjach.

## <a name="popular-productivity-features"></a>Popularne funkcje produktywności

Niektóre popularne funkcje programu Visual Studio, które ułatwiają wydajniejszą pracę podczas opracowywania oprogramowania, obejmują:

- [Funkcja IntelliSense](editing-python-code-in-visual-studio.md#intellisense)

   Technologia IntelliSense to termin dla zestawu funkcji, który wyświetla informacje o kodzie bezpośrednio w edytorze, a w niektórych przypadkach zapisuje małe bity kodu. Jest tak jak w przypadku, gdy podstawowa dokumentacja jest wbudowana w edytorze, co umożliwia zaoszczędzenie informacji o typie w innym miejscu. Funkcje IntelliSense różnią się w zależności od języka, a [Edycja artykułu kodu](editing-python-code-in-visual-studio.md#intellisense) w języku Python zawiera szczegółowe informacje dotyczące środowiska Python. Na poniższej ilustracji przedstawiono, w jaki sposób technologia IntelliSense wyświetla listę elementów członkowskich typu:

   ![Uzupełnianie elementu członkowskiego za pomocą funkcji IntelliSense programu Visual Studio](media/code-editing-completions-simple.png)

- [Refaktoryzacja](refactoring-python-code.md)

   Klikając prawym przyciskiem myszy fragment kodu i wybierając **szybkie akcje i refaktoryzacje**, program Visual Studio udostępnia operacje, takie jak inteligentne Zmienianie nazw zmiennych, wyodrębnianie jednego lub kilku wierszy kodu do nowej metody, zmiana kolejności metod parametry i nie tylko.

   ![Refaktoryzacja w programie Visual Studio](media/tour-ide-refactor-extract-method.png)

- [Zaznaczanie błędów](refactoring-python-code.md)

   Zaznaczanie błędów sprawdza, czy występują błędy i typowe problemy w kodzie w języku Python, zachęcając Cię do tworzenia dobrych wzorców kodowania języka Python.

   ![Polecenie PyLint w menu kontekstowym dla projektów języka Python](media/code-pylint-command.png)

- Pole wyszukiwania

   Program Visual Studio może pozornie przeciążać, tak jak wiele menu, opcji i właściwości. Pole wyszukiwania to doskonały sposób na szybkie znajdowanie potrzebnych informacji w programie Visual Studio. Po rozpoczęciu wpisywania nazwy szukanego elementu program Visual Studio Wyświetla listę wyników, które dokładnie zapoznają się z tym, co należy zrobić. Aby dodać funkcję do programu Visual Studio, na przykład w celu dodania obsługi dodatkowego języka programowania, w polu wyszukiwania znajdują się wyniki otwierające Instalator programu Visual Studio w celu zainstalowania obciążenia lub pojedynczego składnika.

   ![Pole wyszukiwania w programie Visual Studio](media/tour-ide-quick-launch.png)

- Zygzaki i [szybkie akcje](../ide/quick-actions.md)

   Zygzaki to faliste podkreślenia, które wysyłają alerty do błędów lub potencjalnych problemów w kodzie podczas wpisywania. Te wizualne wskazówki umożliwiają natychmiastowe Rozwiązywanie problemów bez oczekiwania na odnalezienie błędu podczas kompilacji lub podczas uruchamiania programu. Po umieszczeniu wskaźnika myszy na zygzaku pojawią się dodatkowe informacje o błędzie. Żarówka może również pojawić się na lewym marginesie z akcjami, znanymi jako szybkie akcje, aby naprawić błąd.

   ![Zygzaky w programie Visual Studio](media/tour-ide-squiggles.png)

- [Przejdź do definicji i wglądu](../ide/go-to-and-peek-definition.md)

   Funkcja **Przejdź do definicji** przenosi bezpośrednio do lokalizacji, w której zdefiniowana jest funkcja lub typ. Polecenie **wgląd do definicji** wyświetla definicję w oknie bez otwierania osobnego pliku. Polecenie **Znajdź wszystkie odwołania** zapewnia również przydatny sposób odnajdywania i używania danego identyfikatora.

   ![Polecenia nawigacji kodu](media/tour-ide-navigation-commands.png)

## <a name="powerful-features-for-python"></a>Zaawansowane funkcje języka Python

::: moniker range=">=vs-2019"
- [Uruchom kod bez projektu](quickstart-05-python-visual-studio-open-folder.md)

    Począwszy od programu Visual Studio 2019, można otworzyć folder zawierający kod języka Python, aby korzystać z funkcji, takich jak IntelliSense i debugowanie, bez konieczności tworzenia projektu programu Visual Studio dla kodu.
::: moniker-end

- [Współpraca przy użyciu programu Visual Studio](/visualstudio/liveshare/use/vs)
  
    Visual Studio Live Share umożliwia zespołowe edytowanie i debugowanie z innymi osobami w czasie rzeczywistym, niezależnie od używanego języka programowania lub typów aplikacji, które tworzysz. 

- [Interaktywny REPL języka Python](python-interactive-repl-in-visual-studio.md)

    Program Visual Studio udostępnia interaktywne okno pętle Read-Test-Print (REPL) dla każdego środowiska języka Python, które usprawnia REPL uzyskiwany z poziomu języka *Python. exe* w wierszu polecenia. W oknie **interaktywnym** możesz wprowadzić dowolny kod w języku Python i zobaczyć natychmiastowe wyniki.

    ![Okno interaktywne języka Python](media/interactive-window.png)

- [Debugowanie](debugging-python-in-visual-studio.md)

    Program Visual Studio oferuje kompleksowe środowisko debugowania dla języka Python, w tym dołączanie do uruchomionych procesów, ocenianie wyrażeń w oknach **czujka** i **natychmiastowe** , inspekcja zmiennych lokalnych, punktów przerwania, przechodzenie do trybu/out/over instrukcje, **Ustawianie następnej instrukcji**i innych. Można także debugować kod zdalnego kodu Python uruchomiony na komputerach z systemem Linux.

    ![Debugowanie języka Python w programie Visual Studio](media/remote-debugging-breakpoint-hit.png)

- [Korzystanie zC++](working-with-c-cpp-python-in-visual-studio.md)

    Wiele bibliotek utworzonych dla języka Python jest pisanych C++ w celu uzyskania optymalnej wydajności. Program Visual Studio oferuje bogate możliwości tworzenia C++ rozszerzeń, w tym [debugowania w trybie mieszanym](debugging-mixed-mode-c-cpp-python-in-visual-studio.md).

    ![Debugowanie w trybie mieszanym w języku C++ Python i razem](media/mixed-mode-debugging.png)

- [Profilowanie](profiling-python-code-in-visual-studio.md)

    W przypadku korzystania z interpretera opartego na CPython można oszacować wydajność kodu w języku Python w programie Visual Studio.

    ![Raport dotyczący wydajności profilowania](media/profiling-results.png)

- [Testowanie jednostek](unit-testing-python-in-visual-studio.md)

    Program Visual Studio zapewnia zintegrowaną obsługę odnajdywania, uruchamiania i debugowania testów jednostkowych w kontekście IDE.

    ![Testowanie jednostkowe pokazujące stan niepowodzenia testu](media/unit-test-A-fail.png)

## <a name="next-steps"></a>Następne kroki

Poznaj środowisko Python w programie Visual Studio, wykonując jedną z następujących przewodników Szybki Start i samouczków:

> [!div class="nextstepaction"]
> [Szybki Start: Tworzenie aplikacji internetowej za pomocą kolby](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json)

> [!div class="nextstepaction"]
> [Współpraca z językiem Python w programie Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

> [!div class="nextstepaction"]
> [Wprowadzenie do platformy sieci Web Django w programie Visual Studio](learn-django-in-visual-studio-step-01-project-and-solution.md)

> [!div class="nextstepaction"]
> [Rozpocznij pracę z platformą sieci Web w programie Visual Studio](learn-flask-visual-studio-step-01-project-solution.md)

## <a name="see-also"></a>Zobacz także

- Odkryj [więcej funkcji programu Visual Studio](../ide/advanced-feature-overview.md)
- Odwiedź witrynę [VisualStudio.Microsoft.com](https://visualstudio.microsoft.com/vs/)
- Przeczytaj [Blog programu Visual Studio](https://devblogs.microsoft.com/visualstudio/)

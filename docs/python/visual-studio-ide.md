---
title: Omówienie programu Visual Studio dla programistów używających języka Python
titleSuffix: ''
ms.date: 12/14/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
dev_langs:
- Python
ms.workload:
- python
- data-science
ms.openlocfilehash: 5c7e8c81b52744d62dbdc60259462e7dedc1388e
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/27/2018
ms.locfileid: "53804906"
---
# <a name="welcome-to-the-visual-studio-ide--python"></a>Witamy w środowisku IDE programu Visual Studio | Python

Visual Studio *zintegrowanego środowiska programistycznego* to twórczych uruchamianie konsola dla języka Python (i inne języki) służąca do służy do edytowania, debugowania i testować kod, a następnie opublikować aplikację. Zintegrowanym środowisku programistycznym (IDE) to program bogate, który może służyć do wielu aspektów programowania. Podniesienia standardowy edytor i debuger, większości środowisk IDE podać, program Visual Studio obejmuje uzupełnianie kodu narzędzi, interaktywnego środowiska REPL, i innych funkcji, do jej obsługi ułatwiają realizację procesu tworzenia oprogramowania.

[![Program Visual Studio z projektu języka Python](media/tour-ide-overview.png)](media/tour-ide-overview.png#lightbox)

Ten obraz pokazuje programu Visual Studio Otwórz projekt języka Python i kilkoma oknami narzędzi kluczy, które będą prawdopodobnie używane:

- [**Eksplorator rozwiązań** ](../ide/solutions-and-projects-in-visual-studio.md) (prawym górnym rogu) umożliwia wyświetlanie, przejść i zarządzanie plikami kodu. **Eksplorator rozwiązań** ułatwiają organizowanie kodu za pomocą tych plików do grupowania [rozwiązania i projekty](/visualstudio/get-started/tutorial-projects-solutions).
    - Wraz z **Eksploratora rozwiązań** jest [ **środowiska Python**](managing-python-environments-in-visual-studio.md), gdzie zarządzać różnych interpreterów języka Python, które są zainstalowane na tym komputerze.

- [Okna edytora](../ide/writing-code-in-the-code-and-text-editor.md) (center), gdzie prawdopodobnie spędzisz większość czasu, wyświetla zawartość pliku. To jest, gdy użytkownik [edycji kodu w języku Python](editing-python-code-in-visual-studio.md)nawigować do kodu struktury i ustawiać punkty przerwania podczas debugowania sesji. Za pomocą języka Python, możesz również wybrać kod i naciśnij klawisze Ctrl + Enter, aby uruchomić ten kod w [okna interaktywnego REPL](python-interactive-repl-in-visual-studio.md).

- [Okno danych wyjściowych](../ide/reference/output-window.md) (na dole na środku) jest, gdzie program Visual Studio wysyła powiadomienia, takich jak debugowanie i komunikaty o błędach, ostrzeżenia, komunikaty o stanie publikowania i. Każde źródło komunikatu ma osobnej karcie.
    - A [okna interaktywnego REPL języka Python](python-interactive-repl-in-visual-studio.md) pojawia się w tym samym regionie co okno danych wyjściowych.

- [Team Explorer](/azure/devops/user-guide/work-team-explorer?view=vsts) (prawy dolny róg) umożliwia śledzenie elementów roboczych i udostępnianie kodu z innymi osobami przy użyciu technologii kontroli wersji, takich jak [Git](https://git-scm.com/) i [Team Foundation Version Control (TFVC)](/azure/devops/repos/tfvc/overview?view=vsts).

## <a name="editions"></a>Wersje

Program Visual Studio jest dostępna dla Windows i Mac; jednak obsługa w języku Python jest dostępna tylko w programie Visual Studio for Windows.

Istnieją trzy wersje programu Visual Studio 2017 na Windows: Community, Professional i Enterprise. Zobacz [porównanie programu Visual Studio 2017 IDE](https://visualstudio.microsoft.com/vs/compare/) Aby dowiedzieć się więcej o funkcji, które są obsługiwane w poszczególnych wydaniach.

## <a name="popular-productivity-features"></a>Funkcje zwiększające produktywność popularne funkcje

Oto niektóre z najpopularniejszych funkcji w programie Visual Studio, które ułatwiają mu bardziej wydajnej pracy, podczas opracowywania oprogramowania:

- [Funkcja IntelliSense](editing-python-code-in-visual-studio.md#intellisense)

   Funkcja IntelliSense jest okres zestaw funkcji, który wyświetla informacje o kodzie bezpośrednio w edytorze, a w niektórych przypadkach zapisu małe fragmenty kodu dla Ciebie. To, jak podstawowa dokumentacja wbudowanego w edytorze, co pozwala uniknąć konieczności wyszukiwania informacji o typie w innym miejscu. Funkcje IntelliSense zależy od języka, a [kod Python edycji](editing-python-code-in-visual-studio.md#intellisense) artykuł zawiera szczegółowe informacje dla języka Python. Na poniższej ilustracji przedstawiono, jak technologia IntelliSense wyświetla listę elementu członkowskiego dla typu:

   ![Uzupełnianie składowych za pomocą funkcji IntelliSense Visual Studio](media/code-editing-completions-simple.png)

- [Refaktoryzacja](refactoring-python-code.md)

   Klikając prawym przyciskiem myszy na elemencie kodu i wybierając **szybkie akcje i Refaktoryzacje**, Visual Studio umożliwia operacje, takie jak inteligentne zmiana nazwy zmiennych, wyodrębnianie jeden lub więcej wierszy kodu do nowej metody, zmiana kolejność parametrów metod i inne.

   ![Refaktoryzacja w programie Visual Studio](media/tour-ide-refactor-extract-method.png)

- [Zaznaczanie błędów](refactoring-python-code.md)

   Zaznaczanie błędów sprawdza, czy błędy i często spotykanych problemów z kodu w języku Python, co ułatwia zachowanie za pomocą języka Python dobre, wzorców.

   ![Polecenie PyLint w menu kontekstowym dla projektów języka Python](media/code-pylint-command.png)

- [Szybkie uruchamianie](../ide/reference/quick-launch-environment-options-dialog-box.md)

   Program Visual Studio może wydawać się trudne w czasie za pomocą menu tak wiele, opcje i właściwości. **Szybkie uruchamianie** pole wyszukiwania jest doskonałym sposobem na szybkie znajdowanie potrzebnej w programie Visual Studio. Po uruchomieniu, wpisując nazwę coś, czego szukasz, program Visual Studio wyświetla wyniki, które przyjmują dokładnie miejscu należy przejść. Jeśli chcesz dodać funkcje do programu Visual Studio, na przykład aby dodać obsługę dodatkowych języka programowania, **Szybkie uruchamianie** zapewnia wyniki, które Otwórz Instalator programu Visual Studio do zainstalowania obciążeń lub poszczególnych składników.

   ![Szybkie uruchamianie pola wyszukiwania w programie Visual Studio](media/tour-ide-quick-launch.png)

- Zygzaki i [szybkie akcje](../ide/quick-actions.md)

   Zygzaki są faliste linie, które alertów dotyczących błędów lub potencjalnych problemów w kodzie podczas wpisywania. Te wskazówki visual umożliwiają rozwiązywanie problemów z natychmiast bez oczekiwania na błąd, które mają zostać odnalezione, podczas kompilacji lub po uruchomieniu programu. Po umieszczeniu wskaźnika myszy nad wężyk, zobaczysz dodatkowe informacje o tym błędzie. Żarówka może również wystąpić na lewym marginesie z akcjami, znane jako szybkich akcji, aby naprawić błąd.

   ![Faliste linie w programie Visual Studio](media/tour-ide-squiggles.png)

- [Przejdź do, a następnie zobacz definicję](../ide/go-to-and-peek-definition.md)

   **Przejdź do definicji** funkcji spowoduje przejście bezpośrednio do lokalizacji, w którym funkcja lub typ jest zdefiniowany. **Wgląd w definicje** polecenie wyświetla definicję w oknie bez konieczności otwierania pliku. **Znajdź wszystkie odwołania** polecenie dostarcza również pomocny sposób, aby dowiedzieć się, gdzie wszystkie danym identyfikatorem jest zdefiniowane i używane.

   ![Polecenia nawigacji kodu](media/tour-ide-navigation-commands.png)

## <a name="powerful-features-for-python"></a>Zaawansowane funkcje dla języka Python

- [Interaktywna pętla REPL języka Python](python-interactive-repl-in-visual-studio.md)

    Program Visual Studio udostępnia okno interaktywne odczytu oceny — Drukuj pętli (REPL) dla każdego środowiska Python, które poprawia REPL, możesz uzyskać za pomocą *python.exe* w wierszu polecenia. W **Interactive** okna można wprowadzić dowolny kod języka Python oraz zobaczyć wyniki wprowadzenia.

    ![Okno interaktywne języka Python](media/interactive-window.png)

- [Debugowanie](debugging-python-in-visual-studio.md)

    Program Visual Studio udostępnia kompleksowe środowisko debugowania dla języka Python, dołączanie do uruchomionego procesu, w tym oceny wyrażenia w **Obejrzyj** i **bezpośrednie** systemu windows, inspekcja lokalne zmienne, punkty przerwania, krok instrukcji w/out/over **Ustaw następną instrukcję**i nie tylko. Można również debugować kod Python zdalnego uruchomionych na komputerach z systemem Linux.

    ![Debugowanie języka Python w programie Visual Studio](media/remote-debugging-breakpoint-hit.png)

- [Interakcja z językiem C++](working-with-c-cpp-python-in-visual-studio.md)

    Wiele bibliotek utworzone dla języka Python są zapisywane w języku C++ pod kątem optymalnej wydajności. Program Visual Studio zapewnia zaawansowane funkcje służące do tworzenia rozszerzenia języka C++, w tym [debugowanie w trybie mieszanym](debugging-mixed-mode-c-cpp-python-in-visual-studio.md).

    ![Debugowanie w trybie mieszanym, Python i C++ razem](media/mixed-mode-debugging.png)

- [Profilowanie](profiling-python-code-in-visual-studio.md)

    Korzystając z interpreterem na podstawie języka CPython, będziesz w stanie ocenić wydajność kodu w języku Python w programie Visual Studio.

    ![Raport profilowania wydajności](media/profiling-results.png)

- [Testowanie jednostek](unit-testing-python-in-visual-studio.md)

    Program Visual Studio obsługuje zintegrowane odnajdywania, uruchomiona, i testów jednostkowych debugowania w kontekście IDE.

    ![Testowania przedstawiająca stan nieudanego testu jednostkowego](media/unit-test-A-fail.png)

## <a name="next-steps"></a>Następne kroki

Poznaj języka Python w programie Visual Studio w dalszej, wykonując jedną z następujących przewodników Szybki Start lub samouczki:

> [!div class="nextstepaction"]
> [Szybki Start: Tworzenie aplikacji sieci web za pomocą Flask](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json)

> [!div class="nextstepaction"]
> [Praca z językiem Python w programie Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

> [!div class="nextstepaction"]
> [Wprowadzenie do struktury sieci web Django w programie Visual Studio](learn-django-in-visual-studio-step-01-project-and-solution.md)

> [!div class="nextstepaction"]
> [Rozpoczynanie pracy z usługą Flask struktury sieci web w programie Visual Studio](learn-flask-visual-studio-step-01-project-solution.md)

## <a name="see-also"></a>Zobacz także

- Odkryj [więcej funkcji programu Visual Studio](../ide/advanced-feature-overview.md)
- Odwiedź stronę [visualstudio.microsoft.com](https://visualstudio.microsoft.com/vs/)
- Odczyt [blog Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/)
- Zapoznaj się z bezpłatnym kursom programu Visual Studio na [Microsoft Virtual Academy](https://mva.microsoft.com/product-training/visual-studio-courses#!index=2&lang=1033)

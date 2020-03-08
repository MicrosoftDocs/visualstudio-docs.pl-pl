---
title: Poznaj samouczek Flask w programie Visual Studio w kroku 1, podstawy Flask
titleSuffix: ''
description: Przewodnik po podstawy Flask w kontekście projektów programu Visual Studio, w tym wymagania wstępne, Git i środowisk wirtualnych.
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 7707d993ac5fb6f73060d0f862c828e67c833872
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409831"
---
# <a name="tutorial-get-started-with-the-flask-web-framework-in-visual-studio"></a>Samouczek: Rozpoczynanie pracy z usługą Flask struktury sieci web w programie Visual Studio

[Kolba](https://palletsprojects.com/p/flask/) to lekka struktura języka Python dla aplikacji sieci Web, która zapewnia podstawowe informacje na temat routingu URL i renderowania stron.

Flask jest nazywany framework "micro", ponieważ nie bezpośrednio udostępnia funkcje, takie jak formularz weryfikacji, abstrakcję bazy danych, uwierzytelniania i tak dalej. Takie funkcje są udostępniane przez specjalne pakiety języka Python nazywane *rozszerzeniami*kolb. Rozszerzenia bezproblemowo integrować z Flask, tak aby wyglądały tak, jakby są one częścią Flask sam. Na przykład Flask, sama nie zapewnia aparat szablonów strony. Tworzenie szablonów jest zapewniana przez rozszerzenia, takie jak Jinja i Jade, jak pokazano w tym samouczku.

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:

> [!div class="checklist"]
> - Tworzenie podstawowego projektu Flask w repozytorium Git przy użyciu szablonu "Pusty projekt sieci Web Flask" (krok 1)
> - Tworzenie aplikacji Flask za pomocą jednej strony i renderowania tej strony, przy użyciu szablonu (krok 2)
> - Obsługa plików statycznych, dodawanie stron i użyć szablonu dziedziczenia (krok 3)
> - Szablon projektu sieci Web Flask służy do tworzenia aplikacji z wieloma stronami i elastyczne środowisko (krok 4)
> - Szablon projektu sieci Web Flask sond służy do tworzenia aplikacji sondowania, która korzysta z rozmaitych rodzajów magazynów (magazynu platformy Azure, bazy danych MongoDB lub pamięć).

W miarę upływu następujące kroki, utworzysz jedno rozwiązanie Visual Studio, który zawiera trzy osobne projekty. Utwórz projekt za pomocą różnych szablonów projektu Flask, które są dołączone do programu Visual Studio. Przechowując projektów w tym samym rozwiązaniu, można łatwo przełączać i z powrotem między różnych plików do porównania.

> [!Note]
> Ten samouczek różni się od [przewodnika Szybki Start](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json) w tym samouczku, aby dowiedzieć się więcej o kolbie, a także jak korzystać z różnych szablonów projektu kolb, które zapewniają bardziej obszerny punkt wyjścia dla własnych projektów. Na przykład szablony projektu automatycznie zainstalować pakiet Flask podczas tworzenia projektu, nie trzeba już ręcznie, jak pokazano w opcji szybkiego startu instalacji pakietu.

## <a name="prerequisites"></a>Wymagania wstępne

- Program Visual Studio 2017 lub nowszy w systemie Windows z następującymi opcjami:
  - Obciążenie **programowanie** w języku Python (karta**obciążenie** w instalatorze). Aby uzyskać instrukcje, zobacz [Instalowanie obsługi języka Python w programie Visual Studio](installing-python-support-in-visual-studio.md).
  - Rozszerzenie **git dla systemu Windows** i usługi **GitHub dla programu Visual Studio** na karcie **poszczególne składniki** w obszarze **Narzędzia kodu**.

Szablony projektu Flask są dołączane do wcześniejszych wersjach narzędzi Python Tools for Visual Studio, chociaż szczegóły mogą się różnić od co zostało omówione w tym samouczku.

Programowanie w języku Python nie jest obecnie obsługiwana w programie Visual Studio dla komputerów Mac. Na komputerach Mac i Linux Użyj [rozszerzenia Python w Visual Studio Code](https://code.visualstudio.com/docs/python/python-tutorial).

## <a name="step-1-1-create-a-visual-studio-project-and-solution"></a>Krok 1-1: Tworzenie projektu programu Visual Studio i rozwiązania

1. W programie Visual Studio wybierz pozycję **plik** > **Nowy** > **projekt**, wyszukaj ciąg "Kolba" i wybierz szablon **projektu sieci Web o pustej kolbie** . (Szablon znajduje się również w obszarze > **Python** w **sieci Web** na liście po lewej stronie).

    ![Okno dialogowe nowego projektu w programie Visual Studio dla pustego projektu sieci Web Flask](media/flask/step01-new-blank-project.png)

1. W polach w dolnej części okna dialogowego wprowadź następujące informacje (jak pokazano na poprzedniej ilustracji), a następnie wybierz **przycisk OK**:

    - **Nazwa**: Ustaw nazwę projektu programu Visual Studio na **BasicProject**. Ta nazwa jest także używana dla projektu Flask.
    - **Lokalizacja**: Określ lokalizację, w której ma zostać utworzone rozwiązanie i projekt programu Visual Studio.
    - **Nazwa rozwiązania**: Ustaw wartość **LearningFlask**, która jest odpowiednia dla rozwiązania jako kontener dla wielu projektów w tym samouczku.
    - **Utwórz katalog dla rozwiązania**: pozostaw ustawiony (domyślnie).
    - **Utwórz nowe repozytorium git**: zaznacz tę opcję (która jest domyślnie wyczyszczona), aby program Visual Studio tworzył lokalne repozytorium git podczas tworzenia rozwiązania. Jeśli ta opcja nie jest widoczna, uruchom Instalatora programu Visual Studio i Dodaj rozszerzenie **git dla systemu Windows** i usługi **GitHub dla programu Visual Studio** na karcie **poszczególne składniki** w obszarze **Narzędzia kodu**.

1. Po chwili program Visual Studio wyświetli okno dialogowe z informacją o tym, że **ten projekt wymaga zewnętrznych pakietów** (pokazanych poniżej). To okno dialogowe jest wyświetlane, ponieważ szablon zawiera plik *Requirements. txt* odwołujący się do najnowszej wersji pakietu 1. x. (Wybierz pozycję **Pokaż wymagane pakiety** , aby zobaczyć dokładne zależności).

    ![Monituj powiedzenie, że projekt wymaga pakiety zewnętrzne](media/tutorials-common/step01-requirements-prompt-install-myself.png)

1. Wybierz opcję **zainstaluję je samodzielnie**. Utworzysz środowisko wirtualne wkrótce, aby upewnić się, że jest ona wykluczana z kontroli źródła. (Środowisko zawsze można utworzyć na podstawie *wymagań. txt*).

## <a name="step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository"></a>Krok 1 – 2: Sprawdź kontrolki Git i opublikować w repozytorium zdalnym

Ponieważ wybrano opcję **Utwórz nowe repozytorium git** w oknie dialogowym **Nowy projekt** , projekt jest już zatwierdzony do lokalnej kontroli źródła zaraz po zakończeniu procesu tworzenia. Ten krok umożliwia zapoznanie się z kontrolkami git programu Visual Studio i oknem **Team Explorer** , w którym pracujesz z kontrolą źródła.

1. Sprawdź formanty Git na dolnym rogu okna głównego programu Visual Studio. Od lewej do prawej te kontrolki wyświetlają niewypchniętych zatwierdzeń, niezatwierdzone zmiany, nazwę repozytorium i gałąź bieżącą:

    ![Git formantów w oknie programu Visual Studio](media/flask/step01-git-controls.png)

    > [!Note]
    > Jeśli nie zaznaczysz **nowego repozytorium git** w oknie dialogowym **Nowy projekt** , w kontrolkach Git będzie widoczne tylko polecenie **Dodaj do kontroli źródła** , które tworzy lokalne repozytorium.
    >
    > ![Dodaj do kontroli źródła jest wyświetlany w programie Visual Studio, jeśli nie utworzono repozytorium](media/tutorials-common/step01-git-add-to-source-control.png)

1. Wybierz przycisk zmiany, a program Visual Studio otworzy okno **Team Explorer** na stronie **zmiany** . Ponieważ nowo utworzonego projektu jest już zatwierdzone do kontroli źródła automatycznie, nie widać wszystkie oczekujące zmiany.

    ![Okno Eksploratora zespołu na stronie zmiany](media/flask/step01-team-explorer-changes.png)

1. Na pasku stanu programu Visual Studio wybierz przycisk niewypchnięte zatwierdzeń (Strzałka w górę z **2**), aby otworzyć stronę **Synchronizacja** w **Team Explorer**. Ponieważ lokalne repozytorium, na stronie jest prostych opcji, aby opublikować repozytorium w różnych repozytoria zdalne.

    ![Team Explorer okna pokazujący dostępne Git opcji repozytorium dla kontroli źródła](media/flask/step01-team-explorer.png)

    Możesz niezależnie od usługi, w której ma we własnych projektach. W tym samouczku przedstawiono użycie usługi GitHub, w której ukończony przykładowy kod samouczka jest przechowywany w repozytorium [Microsoft/Python-Sample-vs-Learning-Kolba](https://github.com/Microsoft/python-sample-vs-learning-flask) .

1. Po wybraniu dowolnego z formantów **publikowania** **Team Explorer** poprosi o dodatkowe informacje. Na przykład podczas publikowania przykładu dla tego samouczka należy najpierw utworzyć repozytorium, w którym wystąpiła opcja **wypchnij do zdalnego repozytorium** z adresem URL repozytorium.

    ![Okno Eksploratora zespołu do wypychania do istniejącego repozytorium zdalnego](media/flask/step01-push-to-github.png)

    Jeśli nie masz istniejącego repozytorium, opcje **Publikuj w** serwisie GitHub i **wypchnij do usługi Azure DevOps** umożliwiają utworzenie jednego bezpośrednio z poziomu programu Visual Studio.

1. Podczas pracy z tym samouczkiem Uzyskaj w celu przejrzenia okresowo za pomocą formantów w programie Visual Studio można zatwierdzać i wypychać zmiany. W tym samouczku przypomina o tym, w odpowiednich miejscach.

> [!Tip]
> Aby szybko poruszać się w **Team Explorer**, zaznacz nagłówek (który odczytuje **zmiany** lub **wypchnij** obrazy powyżej), aby wyświetlić menu rozwijane dostępne strony.

### <a name="question-what-are-some-advantages-of-using-source-control-from-the-beginning-of-a-project"></a>Pytanie: Jakie są niektóre korzyści wynikające z używania kontroli źródła, od początku projektu?

Odpowiedź: Przede wszystkim przy użyciu kontroli źródła od samego początku, zwłaszcza, jeśli używasz zdalnego repozytorium zawiera kopię zapasową regularne poza siedzibą firmy, projektu. W przeciwieństwie do obsługi projektu tylko na lokalny system plików, kontroli źródła także zmienić pełną historię zmian i łatwe możliwość przywracania pojedynczego pliku lub całego projektu do poprzedniego stanu. Aby zmian historii pomaga ustalić przyczynę regresji (niepowodzeń testów). Ponadto kontroli źródła jest pracy wielu osób na projekt, która zarządza zastępuje i zapewnia Rozwiązywanie konfliktów. Na koniec kontroli źródła, która jest całkowicie formę automatyzacji, konfiguruje możesz również do automatyzacji kompilacji, testowania i rozwiązania release management. Tak naprawdę jest pierwszym krokiem przy użyciu metodyki DevOps dla projektu, a ponieważ barier wejścia znajdują się więc niski, to naprawdę bez powodu, aby nie używać kontroli źródła, od początku.

Aby uzyskać dodatkową dyskusję na temat kontroli źródła jako Automatyzacja, zobacz [Źródło prawdy: rola repozytoriów w DevOps](https://msdn.microsoft.com/magazine/mt763232), artykuł w witrynie MSDN Magazine przeznaczony dla aplikacji mobilnych, które dotyczą również usługi Web Apps.

### <a name="question-can-i-prevent-visual-studio-from-auto-committing-a-new-project"></a>Pytanie: Można zapobiec programu Visual Studio automatyczne zatwierdzanie nowego projektu?

Odpowiedź: tak. Aby wyłączyć automatyczne zatwierdzanie, przejdź do strony **Ustawienia** w obszarze **Team Explorer**, wybierz pozycję **git** > **Ustawienia globalne**, usuń zaznaczenie pola wyboru **Zatwierdź zmiany po scaleniu domyślnie**, a następnie wybierz pozycję **Aktualizuj**.

## <a name="step-1-3-create-the-virtual-environment-and-exclude-it-from-source-control"></a>Krok 1-3: Utwórz środowisko wirtualne i wykluczenie go z kontroli źródła

Teraz, gdy skonfigurowano kontroli źródła dla projektu, można utworzyć środowisko wirtualne niezbędne pakiety Flask, których wymaga projekt. Następnie można użyć **Team Explorer** do wykluczenia folderu środowiska z kontroli źródła.

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł **środowiska Python** i wybierz polecenie **Dodaj środowisko wirtualne**.

    ![Dodaj polecenie środowisko wirtualne w Eksploratorze rozwiązań](media/flask/step01-add-virtual-environment-command.png)

1. Zostanie wyświetlone okno dialogowe **Dodawanie środowiska wirtualnego** z komunikatem informującym, **że znaleźliśmy plik Requirements. txt.** Ten komunikat oznacza, że program Visual Studio używa tego pliku do skonfigurowania środowiska wirtualnego.

    ![Dodaj okno środowiska wirtualnego z komunikatem w pliku requirements.txt](media/tutorials-common/step01-add-virtual-environment-found-requirements.png)

1. Wybierz pozycję **Utwórz** , aby zaakceptować wartości domyślne. (Możesz zmienić nazwę środowiska wirtualnego, jeśli chcesz, co tylko zmieni nazwę jego podfolderu, ale `env` jest konwencją standardową).

1. Wyrazić zgodę na uprawnienia administratora, jeśli zostanie wyświetlony monit, następnie o cierpliwość przez kilka minut, podczas gdy program Visual Studio pobiera i instaluje pakiety, oznacza to, Flask i jego zależności rozwijanie o tysięcy plików w podfolderach ponad 100. Postęp można zobaczyć w oknie **danych wyjściowych** programu Visual Studio. Czekając, spędzać w kolejnych sekcjach pytanie. Można także zobaczyć opis zależności kolb na stronie [instalacji kolby](https://flask.palletsprojects.com/en/1.0.x/installation/#installation) (Flask.pcocoo.org).

1. W kontrolkach git programu Visual Studio (na pasku stanu) wybierz wskaźnik zmiany (pokazujący **&#42;99**), w którym zostanie otwarta strona **zmiany** w **Team Explorer**.

    Tworzenie środowiska wirtualnego zostało wprowadzone w setkach zmian, ale nie musisz zawierać żadnego z nich w kontroli źródła, ponieważ użytkownik (lub każda inna osoba klonuje projekt) zawsze może odtworzyć środowisko z *wymagań. txt*.

    Aby wykluczyć środowisko wirtualne, kliknij prawym przyciskiem myszy folder **ENV** i wybierz polecenie **Ignoruj te elementy lokalne**.

    ![Ignorowanie środowiska wirtualnego w zmian kontroli źródła](media/flask/step01-ignore-local-items.png)

1. Po wykluczeniu środowiska wirtualnego tylko pozostałe zmiany są w pliku projektu i *. gitignore*. Plik *. gitignore* zawiera dodany wpis dla folderu środowiska wirtualnego. Możesz kliknąć dwukrotnie plik, aby zobaczyć diff.

1. Wprowadź wiadomość dotyczącą zatwierdzenia i wybierz przycisk **Zatwierdź wszystko** , a następnie wypchnij zatwierdzenia do repozytorium zdalnego, jeśli chcesz.

### <a name="question-why-do-i-want-to-create-a-virtual-environment"></a>Pytanie: Dlaczego czy chcesz utworzyć środowisko wirtualne?

Odpowiedź: Środowisko wirtualne jest doskonałym sposobem na izolowanie dokładnie zależności aplikacji. Tej izolacji pozwala uniknąć konfliktów w środowisku Python globalnym i ułatwia testowanie i współpracy. Wraz z upływem czasu podczas opracowywania aplikacji, niezmiennie wprowadzanych wiele pomocnych pakiety języka Python. Utrzymując pakiety w środowisku wirtualnym specyficznym dla projektu, można łatwo zaktualizować plik *Requirements. txt* projektu, który opisuje to środowisko, które jest zawarte w kontroli źródła. Po skopiowaniu projektu na inne komputery, w tym serwery kompilacji, serwery wdrażania i inne komputery deweloperskie, można łatwo odtworzyć środowisko tylko przy użyciu programu *Requirements. txt* (co oznacza, że to środowisko nie musi znajdować się w kontroli źródła). Aby uzyskać więcej informacji, zobacz [Korzystanie z środowisk wirtualnych](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

### <a name="question-how-do-i-remove-a-virtual-environment-thats-already-committed-to-source-control"></a>Pytanie: Jak usunąć środowisko wirtualne jest została już przydzielona do kontroli źródła?

Odpowiedź: najpierw Edytuj plik *. gitignore* , aby wykluczyć folder: Znajdź sekcję na końcu z komentarzem `# Python Tools for Visual Studio (PTVS)` i Dodaj nowy wiersz do folderu środowiska wirtualnego, takiego jak `/BasicProject/env`. (Ponieważ program Visual Studio nie wyświetla pliku w **Eksplorator rozwiązań**, otwórz go bezpośrednio przy użyciu **pliku** > **Otwórz** **plik > pliku** . Możesz również otworzyć plik z **Team Explorer**: na stronie **Ustawienia** wybierz pozycję **Ustawienia repozytorium**, przejdź do sekcji **Ignorowanie atrybutów & plików** , a następnie wybierz łącze **Edytuj** obok **. gitignore**.)

Następnie otwórz okno polecenia, przejdź do folderu, takiego jak *BasicProject* , który zawiera folder środowiska wirtualnego, taki jak *ENV*, i uruchom `git rm -r env`. Następnie zatwierdź te zmiany w wierszu polecenia (`git commit -m 'Remove venv'`) lub Zatwierdź ze strony **zmiany** **Team Explorer**.

## <a name="step-1-4-examine-the-boilerplate-code"></a>Krok 1-4: sprawdzenie kodu standardowy

1. Po zakończeniu tworzenia projektu zobaczysz rozwiązanie i projekt w **Eksplorator rozwiązań**, gdzie projekt zawiera tylko dwa pliki, *App.py* i *Requirements. txt*:

    ![Puste pliki projektu Flask w Eksploratorze rozwiązań](media/flask/step01-blank-flask-project-in-solution-explorer.png)

1. Jak wspomniano wcześniej, plik *Requirements. txt* określa zależność pakietu do kolby. Obecność tego pliku to, co zachęca do tworzenia środowiska wirtualnego, tworząc po raz pierwszy projekt.

1. Pojedynczy plik *App.py* zawiera trzy części. Pierwszy jest instrukcją `import` dla kolby, tworząc wystąpienie klasy `Flask`, która jest przypisana do zmiennej `app`, a następnie przypisując zmienną `wsgi_app`, która jest przydatna w przypadku wdrażania na hoście sieci Web, ale nie w obecnym miejscu):

    ```python
    from flask import Flask
    app = Flask(__name__)

    # Make the WSGI interface available at the top level so wfastcgi can get it.
    wsgi_app = app.wsgi_app
    ```

1. Druga część, na końcu pliku, to bit opcjonalne kodu, który zaczyna się od serwera wdrożeniowego programu Flask konkretnego hosta i wartości portów podjęte ze zmiennych środowiskowych (przyjęto wartość domyślną localhost:5555):

    ```python
    if __name__ == '__main__':
        import os
        HOST = os.environ.get('SERVER_HOST', 'localhost')
        try:
            PORT = int(os.environ.get('SERVER_PORT', '5555'))
        except ValueError:
            PORT = 5555
        app.run(HOST, PORT)
    ```

1. Trzeci jest kierować krótki bitowego kodu, który przypisuje adres URL funkcji, co oznacza, że funkcja udostępnia zasobów według adresu URL. Można definiować trasy przy użyciu `@app.route` dekoratora, którego argument jest względnym adresem URL z katalogu głównego witryny. Jak widać w kodzie, w tym miejscu funkcja zwraca tylko ciąg tekstowy i jest wystarczająco dużo, w przeglądarce do renderowania. W opisanych poniżej renderowania są bardziej rozbudowane stron HTML.

    ```python
    @app.route('/')
    def hello():
        """Renders a sample page."""
        return "Hello World!"
    ```

### <a name="question-what-is-the-purpose-of-the-__name__-argument-to-the-flask-class"></a>Pytanie: Jakie jest przeznaczenie argumentu __name__ w klasie kolb?

Odpowiedź: Argument jest nazwa modułu lub pakietu aplikacji i informuje Flask, gdzie szukać szablonów, pliki statyczne i innych zasobów, które należą do aplikacji. W przypadku aplikacji znajdujących się w jednym module `__name__` jest zawsze poprawną wartością. Jest również ważne w przypadku rozszerzeń, które wymagają informacji o debugowaniu. Aby uzyskać więcej informacji i dodatkowych argumentów, zobacz [dokumentację klasy kolb](https://flask.palletsprojects.com/en/1.0.x/api/#flask.Flask) (Flask.pocoo.org).

### <a name="question-can-a-function-have-more-than-one-route-decorator"></a>Pytanie: Czy funkcja mieć więcej niż jeden dekorator trasy?

Odpowiedź: Tak, można użyć tylu dekoratory dowolną Jeśli taką samą funkcję obsługuje wiele tras. Na przykład, aby użyć funkcji `hello` dla obu "/" i "/Hello", należy użyć następującego kodu:

```python
@app.route('/')
@app.route('/hello')
def hello():
    """Renders a sample page."""
    return "Hello World!"
```

<a name="qa-url-variables"></a>

### <a name="question-how-does-flask-work-with-variable-url-routes-and-query-parameters"></a>Pytanie: Jak Flask działa przy użyciu zmiennej trasy adresu URL i parametry zapytania?

Odpowiedź: w trasie Oznacz każdą zmienną `<variable_name>`, a Kolba przekazuje zmienną do funkcji przy użyciu argumentu nazwanego. Zmienna może być częścią ze ścieżką URL lub w parametrze zapytania. Na przykład trasa w formie `'/hello/<name>` generuje argument ciągu o nazwie `name` do funkcji i użycie `?message=<msg>` w marszrucie analizuje wartość podaną dla parametru zapytania "Message =" i przekazuje go do funkcji jako `msg`:

```python
@app.route('/hello/<name>?message=<msg>')
def hello(name, msg):
    return "Hello " + name + "! Message is " + msg + "."
```

Aby zmienić typ, należy poprzedzić zmienną `int`, `float`, `path` (która akceptuje ukośniki do nazw folderów odróżnić) i `uuid`. Aby uzyskać szczegółowe informacje, zobacz [reguły zmiennych](https://flask.palletsprojects.com/en/1.0.x/quickstart/#variable-rules) w dokumentacji dotyczącej kolb.

Parametry zapytania są również dostępne za pomocą właściwości `request.args`, w odróżnieniu od metody `request.args.get`. Więcej informacji można znaleźć w dokumentacji dotyczącej [obiektu request](https://flask.palletsprojects.com/en/1.0.x/quickstart/#the-request-object) w kolbie.

### <a name="question-can-visual-studio-generate-a-requirementstxt-file-from-a-virtual-environment-after-i-install-other-packages"></a>Pytanie: Visual Studio wygenerować plik Requirements.txt znajduje się w środowisku wirtualnym po zainstalowaniu innych pakietów?

Odpowiedź: tak. Rozwiń węzeł **środowiska Python** , kliknij prawym przyciskiem myszy środowisko wirtualne i wybierz polecenie **Generuj wymagania. txt** . Dobrym sposobem jest użycie tego polecenia okresowo podczas modyfikowania środowiska i zatwierdzić zmiany w parametrach *Requirements. txt* w kontroli źródła wraz ze wszystkimi innymi zmianami kodu, które są zależne od tego środowiska. Jeśli ustawisz ciągłej integracji na serwerze kompilacji, możesz wygenerować plik oraz zatwierdzić zmiany, przy każdej modyfikacji środowiska.

## <a name="step-1-5-run-the-project"></a>Krok 1-5: Uruchom projekt

1. W programie Visual Studio wybierz pozycję **debuguj** > **Rozpocznij debugowanie** (**F5**) lub przycisk **serwer sieci Web** na pasku narzędzi (widoczna przeglądarka może się różnić):

    ![Uruchamianie serwera sieci web przycisku paska narzędzi w programie Visual Studio](media/tutorials-common/run-web-server-toolbar-button.png)

1. Każde polecenie przypisuje losowy numer portu do zmiennej środowiskowej portu, a następnie uruchamia `python app.py`. Zaczyna się kod aplikacji przy użyciu tego portu w ramach serwera rozwoju firmy Flask. Jeśli program Visual Studio **nie może uruchomić debugera** z komunikatem o braku pliku startowego, kliknij prawym przyciskiem myszy pozycję **App.py** w **Eksplorator rozwiązań** i wybierz polecenie **Ustaw jako plik startowy**.

1. Po uruchomieniu serwera, zobaczysz okno konsoli otwórz ten wyświetla dziennik serwera. Program Visual Studio automatycznie otworzy w przeglądarce `http://localhost:<port>`, gdzie powinien zostać wyświetlony komunikat renderowany przez funkcję `hello`:

    ![Widok domyślny projektu Flask](media/flask/step01-first-run-success.png)

1. Gdy wszystko będzie gotowe, Zatrzymaj serwer, zamykając okno konsoli lub korzystając z polecenia **debuguj** > **Zatrzymaj debugowanie** w programie Visual Studio.

### <a name="question-whats-the-difference-between-using-the-debug-menu-commands-and-the-server-commands-on-the-projects-python-submenu"></a>Pytanie: Jaka jest różnica między za pomocą poleceń menu Debugowanie i polecenia serwera w podmenu Python projektu?

Odpowiedź: oprócz poleceń menu **Debuguj** i przycisków paska narzędzi można również uruchomić serwer przy użyciu języka **Python** > **Uruchom serwer** lub **Python** > **Uruchom serwer debugowania** polecenia w menu kontekstowym projektu. Oba polecenia, Otwórz okno konsoli zawiera adres URL lokalnego (localhost:port) dla uruchomionego serwera. Jednak należy ręcznie otworzyć przeglądarkę z tego adresu URL i uruchomienie serwera debugowania nie zostanie uruchomiona automatycznie debugera programu Visual Studio. Możesz dołączyć debuger do uruchomionego procesu później, jeśli chcesz, przy użyciu > **debugowania** **Dołącz do procesu** .

## <a name="next-steps"></a>Następne kroki

W tym momencie podstawowego projektu Flask zawiera kod uruchamiający i kodu strony, w tym samym pliku. Zaleca się, aby rozdzielić te dwa problemy i również rozdzielić HTML i danych przy użyciu szablonów.

> [!div class="nextstepaction"]
> [Tworzenie aplikacji do kolby z widokami i szablonami stron](learn-flask-visual-studio-step-02-create-app.md)

## <a name="go-deeper"></a>Przejdź dalej

- [Kolba szybkiego startu](https://flask.palletsprojects.com/en/1.0.x/quickstart/) (Flask.pocoo.org)
- Kod źródłowy samouczka w witrynie GitHub: [Microsoft/Python-Sample-vs-Learning-Kolba](https://github.com/Microsoft/python-sample-vs-learning-flask)

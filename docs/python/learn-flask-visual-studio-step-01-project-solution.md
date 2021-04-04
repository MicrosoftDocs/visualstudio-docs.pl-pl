---
title: Samouczek z informacjami o kolbie w programie Visual Studio krok 1. podstawowe informacje o kolbie
titleSuffix: ''
description: Przewodnik po języku zawierającym podstawowe informacje w kontekście projektów programu Visual Studio, w tym wymagania wstępne, Git i środowiska wirtualne.
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 89a84198256657ae7f94d0a923780163bee73e48
ms.sourcegitcommit: 5c0e20fc6005bc1f8ca38f4122378c4ac21ba89a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2021
ms.locfileid: "106110613"
---
# <a name="tutorial-get-started-with-the-flask-web-framework-in-visual-studio"></a>Samouczek: Rozpoczynanie pracy z platformą sieci Web w programie Visual Studio

[Kolba](https://palletsprojects.com/p/flask/) to lekka struktura języka Python dla aplikacji sieci Web, która zapewnia podstawowe informacje na temat routingu URL i renderowania stron.

Kolba jest nazywana strukturą "mikro", ponieważ nie udostępnia bezpośrednio funkcji, takich jak Walidacja formularza, Abstrakcja bazy danych, uwierzytelnianie i tak dalej. Takie funkcje są udostępniane przez specjalne pakiety języka Python nazywane *rozszerzeniami* kolb. Rozszerzenia integrują się bezproblemowo z kolbą, tak aby pojawiły się tak, jakby znajdowały się one częścią kolby. Na przykład sama Kolba nie zapewnia aparatu szablonu strony. Tworzenia szablonów jest udostępniana przez rozszerzenia, takie jak Jinja i jade, jak pokazano w tym samouczku.

::: moniker range="vs-2017"
Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
- Tworzenie projektu kolby podstawowej w repozytorium git przy użyciu szablonu "pusty Kolba" projekt sieci Web (krok 1)
- Tworzenie aplikacji do kolby z jedną stroną i renderowanie tej strony przy użyciu szablonu (krok 2)
- Obsługiwanie plików statycznych, dodawanie stron i używanie dziedziczenia szablonów (krok 3)
- Użyj szablonu projektu sieci Web w celu utworzenia aplikacji z wieloma stronami i rozbudowanym projektem (krok 4)
- Użyj szablonu projektu sieci Web kolby sondy do utworzenia aplikacji sondowania korzystającej z różnych opcji magazynu (Azure Storage, MongoDB lub pamięci).

W trakcie wykonywania tych kroków utworzysz pojedyncze rozwiązanie programu Visual Studio, które zawiera trzy oddzielne projekty. Projekt można utworzyć przy użyciu różnych szablonów projektów kolb, które są dołączone do programu Visual Studio. Utrzymując projekty w tym samym rozwiązaniu, można łatwo przełączać się między różnymi plikami do porównania.
::: moniker-end

::: moniker range=">=vs-2019"

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
- Tworzenie projektu kolby podstawowej w repozytorium git przy użyciu szablonu "pusty Kolba" projekt sieci Web (krok 1)
- Tworzenie aplikacji do kolby z jedną stroną i renderowanie tej strony przy użyciu szablonu (krok 2)
- Obsługiwanie plików statycznych, dodawanie stron i używanie dziedziczenia szablonów (krok 3)
- Użyj szablonu projektu sieci Web w celu utworzenia aplikacji z wieloma stronami i rozbudowanym projektem (krok 4)

W trakcie wykonywania tych kroków utworzysz pojedyncze rozwiązanie programu Visual Studio, które zawiera dwa oddzielne projekty. Projekt można utworzyć przy użyciu różnych szablonów projektów kolb, które są dołączone do programu Visual Studio. Utrzymując projekty w tym samym rozwiązaniu, można łatwo przełączać się między różnymi plikami do porównania.
::: moniker-end

> [!Note]
> Ten samouczek różni się od [przewodnika Szybki Start](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json) w tym samouczku, aby dowiedzieć się więcej o kolbie, a także jak korzystać z różnych szablonów projektu kolb, które zapewniają bardziej obszerny punkt wyjścia dla własnych projektów. Na przykład szablony projektu automatycznie instalują pakiet do kolby podczas tworzenia projektu, a nie wymagają ręcznego instalowania pakietu, jak pokazano w przewodniku Szybki Start.

## <a name="prerequisites"></a>Wymagania wstępne

- Program Visual Studio 2017 lub nowszy w systemie Windows z następującymi opcjami:
  - Obciążenie **programowanie** w języku Python (karta **obciążenie** w instalatorze). Aby uzyskać instrukcje, zobacz [Instalowanie obsługi języka Python w programie Visual Studio](installing-python-support-in-visual-studio.md).
  - Rozszerzenie **git dla systemu Windows** i usługi **GitHub dla programu Visual Studio** na karcie **poszczególne składniki** w obszarze **Narzędzia kodu**.

Do wszystkich wcześniejszych wersji Python Tools for Visual Studio dołączone są szablony projektu kolby, ale szczegółowe informacje mogą się różnić od tego, co zostało omówione w tym samouczku.

Programowanie w języku Python nie jest obecnie obsługiwane w Visual Studio dla komputerów Mac. Na komputerach Mac i Linux Użyj [rozszerzenia Python w Visual Studio Code](https://code.visualstudio.com/docs/python/python-tutorial).

## <a name="step-1-1-create-a-visual-studio-project-and-solution"></a>Krok 1-1: Tworzenie projektu i rozwiązania programu Visual Studio

1. W programie Visual Studio wybierz pozycję **plik**  >  **Nowy**  >  **projekt**, wyszukaj ciąg "Kolba" i wybierz szablon **projektu sieci Web pustej kolby** . (Szablon znajduje się również w języku **Python**  >  **Sieć Web** na liście po lewej stronie).

    ![Okno dialogowe nowego projektu w programie Visual Studio dla projektu sieci Web pustej kolby](media/flask/step01-new-blank-project.png)

1. W polach w dolnej części okna dialogowego wprowadź następujące informacje (jak pokazano na poprzedniej ilustracji), a następnie wybierz **przycisk OK**:

    - **Nazwa**: Ustaw nazwę projektu programu Visual Studio na **BasicProject**. Ta nazwa jest również używana dla projektu kolby.
    - **Lokalizacja**: Określ lokalizację, w której ma zostać utworzone rozwiązanie i projekt programu Visual Studio.
    - **Nazwa rozwiązania**: Ustaw wartość **LearningFlask**, która jest odpowiednia dla rozwiązania jako kontener dla wielu projektów w tym samouczku.
    - **Utwórz katalog dla rozwiązania**: pozostaw ustawiony (domyślnie).
    - **Utwórz nowe repozytorium git**: zaznacz tę opcję (która jest domyślnie wyczyszczona), aby program Visual Studio tworzył lokalne repozytorium git podczas tworzenia rozwiązania. Jeśli ta opcja nie jest widoczna, uruchom Instalatora programu Visual Studio i Dodaj rozszerzenie **git dla systemu Windows** i usługi **GitHub dla programu Visual Studio** na karcie **poszczególne składniki** w obszarze **Narzędzia kodu**.

1. Po chwili program Visual Studio wyświetli okno dialogowe z informacją o tym, że **ten projekt wymaga zewnętrznych pakietów** (pokazanych poniżej). To okno dialogowe jest wyświetlane, ponieważ szablon zawiera plik *requirements.txt* , odwołujący się do najnowszego pakietu z kolbą 1. x. (Wybierz pozycję **Pokaż wymagane pakiety** , aby zobaczyć dokładne zależności).

    ![Monituj o to, że projekt wymaga pakietów zewnętrznych](media/tutorials-common/step01-requirements-prompt-install-myself.png)

1. Wybierz opcję **zainstaluję je samodzielnie**. Wkrótce utworzysz środowisko wirtualne, aby upewnić się, że jest ono wykluczone z kontroli źródła. (Środowisko można zawsze utworzyć na podstawie *requirements.txt*).

## <a name="step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository"></a>Krok 1-2: sprawdzanie formantów git i publikowanie w repozytorium zdalnym

Ponieważ wybrano opcję **Utwórz nowe repozytorium git** w oknie dialogowym **Nowy projekt** , projekt jest już zatwierdzony do lokalnej kontroli źródła zaraz po zakończeniu procesu tworzenia. Ten krok umożliwia zapoznanie się z kontrolkami git programu Visual Studio i oknem **Team Explorer** , w którym pracujesz z kontrolą źródła.

1. Przejrzyj kontrolki Git w dolnym rogu okna głównego programu Visual Studio. Od lewej do prawej te kontrolki wyświetlają niewypychane zatwierdzenia, Niezatwierdzone zmiany, nazwę repozytorium i bieżącą gałąź:

    ![Kontrolki Git w oknie programu Visual Studio](media/flask/step01-git-controls.png)

    > [!Note]
    > Jeśli nie zaznaczysz **nowego repozytorium git** w oknie dialogowym **Nowy projekt** , w kontrolkach Git będzie widoczne tylko polecenie **Dodaj do kontroli źródła** , które tworzy lokalne repozytorium.
    >
    > ![Jeśli repozytorium nie zostało utworzone, w programie Visual Studio pojawi się wartość Dodaj do kontroli źródła](media/tutorials-common/step01-git-add-to-source-control.png)

1. Wybierz przycisk zmiany, a program Visual Studio otworzy okno **Team Explorer** na stronie **zmiany** . Ze względu na to, że nowo utworzony projekt jest już automatycznie zatwierdzony do kontroli źródła, nie zobaczysz żadnych oczekujących zmian.

    ![Okno Team Explorer na stronie zmiany](media/flask/step01-team-explorer-changes.png)

1. Na pasku stanu programu Visual Studio wybierz przycisk niewypchnięte zatwierdzeń (Strzałka w górę z **2**), aby otworzyć stronę **Synchronizacja** w **Team Explorer**. Ponieważ masz tylko lokalne repozytorium, Strona zawiera proste opcje publikowania repozytorium w różnych repozytoriach zdalnych.

    ![Okno Team Explorer pokazujące dostępne opcje repozytorium git dotyczące kontroli źródła](media/flask/step01-team-explorer.png)

    Możesz wybrać niezależną usługę dla własnych projektów. W tym samouczku przedstawiono użycie usługi GitHub, w której ukończony przykładowy kod samouczka jest przechowywany w repozytorium [Microsoft/Python-Sample-vs-Learning-Kolba](https://github.com/Microsoft/python-sample-vs-learning-flask) .

1. Po wybraniu dowolnego z formantów **publikowania** **Team Explorer** poprosi o dodatkowe informacje. Na przykład podczas publikowania przykładu dla tego samouczka należy najpierw utworzyć repozytorium, w którym wystąpiła opcja **wypchnij do zdalnego repozytorium** z adresem URL repozytorium.

    ![Okno Team Explorer do wypychania do istniejącego repozytorium zdalnego](media/flask/step01-push-to-github.png)

    Jeśli nie masz istniejącego repozytorium, opcje **Publikuj w** serwisie GitHub i **wypchnij do usługi Azure DevOps** umożliwiają utworzenie jednego bezpośrednio z poziomu programu Visual Studio.

1. Podczas pracy w ramach tego samouczka wykonywać się okresowo, korzystając z formantów w programie Visual Studio, aby zatwierdzić i wypchnąć zmiany. Ten samouczek przypomina użytkownika w odpowiednich punktach.

> [!Tip]
> Aby szybko poruszać się w **Team Explorer**, zaznacz nagłówek (który odczytuje **zmiany** lub **wypchnij** obrazy powyżej), aby wyświetlić menu rozwijane dostępne strony.

### <a name="question-what-are-some-advantages-of-using-source-control-from-the-beginning-of-a-project"></a>Pytanie: Jakie są korzyści z używania kontroli źródła na początku projektu?

Odpowiedź: pierwszy z, przy użyciu kontroli źródła od początku, szczególnie jeśli korzystasz również z repozytorium zdalnego, zapewnia regularne kopie zapasowe projektu. W przeciwieństwie do konserwowania projektu tylko w lokalnym systemie plików kontrola źródła zapewnia również kompletną historię zmian oraz łatwą możliwość przywrócenia pojedynczego pliku lub całego projektu do poprzedniego stanu. Historia zmian pomaga określić przyczynę regresji (niepowodzenia testów). Ponadto kontrola źródła jest niezwykle ważna, jeśli wiele osób pracuje nad projektem, ponieważ zarządza zastępowaniem i zapewnia Rozwiązywanie konfliktów. Na koniec kontrola źródła, która jest zasadniczo formą automatyzacji, pozwala dobrze zautomatyzować kompilacje, testowanie i zarządzanie wydaniami. Jest to naprawdę pierwszy krok przy użyciu DevOps dla projektu i ponieważ przeszkody do wprowadzenia są tak niskie, dlatego nie ma powodów, aby nie używać kontroli źródła od początku.

Aby uzyskać dodatkową dyskusję na temat kontroli źródła jako Automatyzacja, zobacz [Źródło prawdy: rola repozytoriów w DevOps](/archive/msdn-magazine/2016/september/mobile-devops-the-source-of-truth-the-role-of-repositories-in-devops), artykuł w witrynie MSDN Magazine przeznaczony dla aplikacji mobilnych, które dotyczą również usługi Web Apps.

### <a name="question-can-i-prevent-visual-studio-from-auto-committing-a-new-project"></a>Pytanie: czy program Visual Studio może uniemożliwić autozatwierdzanie nowego projektu?

Odpowiedź: Tak. Aby wyłączyć automatyczne zatwierdzanie, przejdź do strony **Ustawienia** w obszarze **Team Explorer**, wybierz pozycję  >  **Ustawienia globalne** git, usuń zaznaczenie pola wyboru **Zatwierdź zmiany po scaleniu domyślnie**, a następnie wybierz pozycję **Aktualizuj**.

## <a name="step-1-3-create-the-virtual-environment-and-exclude-it-from-source-control"></a>Krok 1-3: Tworzenie środowiska wirtualnego i wykluczenie go z kontroli źródła

Teraz, po skonfigurowaniu kontroli źródła dla projektu, można utworzyć środowisko wirtualne wymagane pakiety kolb wymagane przez projekt. Następnie można użyć **Team Explorer** do wykluczenia folderu środowiska z kontroli źródła.

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy węzeł **środowiska Python** i wybierz polecenie **Dodaj środowisko wirtualne**.

    ![Dodaj polecenie środowiska wirtualnego w Eksplorator rozwiązań](media/flask/step01-add-virtual-environment-command.png)

1. Zostanie wyświetlone okno dialogowe **Dodawanie środowiska wirtualnego** z komunikatem informującym o **znalezieniu pliku requirements.txt.** Ten komunikat oznacza, że program Visual Studio używa tego pliku do skonfigurowania środowiska wirtualnego.

    ![Okno dialogowe Dodawanie środowiska wirtualnego z komunikatem o requirements.txt](media/tutorials-common/step01-add-virtual-environment-found-requirements.png)

1. Wybierz pozycję **Utwórz** , aby zaakceptować wartości domyślne. (Możesz zmienić nazwę środowiska wirtualnego, jeśli chcesz, co tylko zmieni nazwę jego podfolderu, ale `env` jest standardową Konwencją).

1. Jeśli zostanie wyświetlony monit, wyrażasz zgodę na uprawnienia administratora, a następnie poczekaj kilka minut, gdy program Visual Studio pobierze i zainstaluje pakiety, które w przypadku kolby i jej zależności oznaczają rozwinięcie tysięcy plików w ponad 100 podfolderach. Postęp można zobaczyć w oknie **danych wyjściowych** programu Visual Studio. Gdy oczekujesz, spędzać poniższe sekcje pytań. Można także zobaczyć opis zależności kolb na stronie [instalacji kolby](https://flask.palletsprojects.com/en/1.0.x/installation/#installation) (Flask.pcocoo.org).

1. W kontrolkach git programu Visual Studio (na pasku stanu) wybierz wskaźnik zmiany (który pokazuje **99&#42;**), co spowoduje otwarcie strony **zmiany** w **Team Explorer**.

    Tworzenie środowiska wirtualnego zostało wprowadzone w setkach zmian, ale nie musisz zawierać żadnego z nich w kontroli źródła, ponieważ użytkownik (lub każda inna osoba klonuje projekt) zawsze może odtworzyć środowisko z *requirements.txt*.

    Aby wykluczyć środowisko wirtualne, kliknij prawym przyciskiem myszy folder **ENV** i wybierz polecenie **Ignoruj te elementy lokalne**.

    ![Ignorowanie środowiska wirtualnego w zmianach kontroli źródła](media/flask/step01-ignore-local-items.png)

1. Po wykluczeniu środowiska wirtualnego tylko pozostałe zmiany są w pliku projektu i *. gitignore*. Plik *. gitignore* zawiera dodany wpis dla folderu środowiska wirtualnego. Możesz kliknąć dwukrotnie plik, aby zobaczyć różnicę.

1. Wprowadź wiadomość dotyczącą zatwierdzenia i wybierz przycisk **Zatwierdź wszystko** , a następnie wypchnij zatwierdzenia do repozytorium zdalnego, jeśli chcesz.

### <a name="question-why-do-i-want-to-create-a-virtual-environment"></a>Pytanie: Dlaczego chcę utworzyć środowisko wirtualne?

Odpowiedź: środowisko wirtualne to świetny sposób izolowania dokładnych zależności aplikacji. Taka Izolacja pozwala uniknąć konfliktów w globalnym środowisku języka Python i pomaga w testowaniu i współpracy. W miarę upływu czasu podczas opracowywania aplikacji niezmiennie się w wielu przydatnych pakietach języka Python. Utrzymując pakiety w środowisku wirtualnym specyficznym dla projektu, można łatwo zaktualizować plik *requirements.txt* projektu, który opisuje to środowisko, które jest zawarte w kontroli źródła. Gdy projekt jest kopiowany na inne komputery, w tym serwery kompilacji, serwery wdrażania i inne komputery deweloperskie, można łatwo odtworzyć środowisko tylko *requirements.txt* (co oznacza, że środowisko nie musi znajdować się w kontroli źródła). Aby uzyskać więcej informacji, zobacz [Korzystanie z środowisk wirtualnych](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

### <a name="question-how-do-i-remove-a-virtual-environment-thats-already-committed-to-source-control"></a>Pytanie: Jak mogę usunąć środowisko wirtualne, które zostało już zatwierdzone do kontroli źródła?

Odpowiedź: najpierw Edytuj plik *. gitignore* , aby wykluczyć folder: Znajdź sekcję na końcu z komentarzem `# Python Tools for Visual Studio (PTVS)` i Dodaj nowy wiersz do folderu środowiska wirtualnego, takiego jak `/BasicProject/env` . (Ponieważ program Visual Studio nie wyświetla pliku w **Eksplorator rozwiązań**, otwórz go bezpośrednio przy użyciu **pliku**  >  **Otwórz**  >  Polecenie menu **plik** . Możesz również otworzyć plik z **Team Explorer**: na stronie **Ustawienia** wybierz pozycję **Ustawienia repozytorium**, przejdź do sekcji **Ignorowanie atrybutów & plików** , a następnie wybierz łącze **Edytuj** obok **. gitignore**.)

Następnie otwórz okno polecenia, przejdź do folderu, takiego jak *BasicProject* , który zawiera folder środowiska wirtualnego, taki jak *ENV* i Run `git rm -r env` . Następnie zatwierdź te zmiany z wiersza polecenia ( `git commit -m 'Remove venv'` ) lub Zatwierdź ze strony **zmiany** w **Team Explorer**.

## <a name="step-1-4-examine-the-boilerplate-code"></a>Krok 1-4: badanie kodu standardowego

1. Po zakończeniu tworzenia projektu zobaczysz rozwiązanie i projekt w **Eksplorator rozwiązań**, gdzie projekt zawiera tylko dwa pliki, *App.py* i *requirements.txt*:

    ![Puste pliki projektu kolby w Eksplorator rozwiązań](media/flask/step01-blank-flask-project-in-solution-explorer.png)

1. Jak wspomniano wcześniej, plik *requirements.txt* określa zależność pakietu do kolby. Obecność tego pliku polega na tym, co zaprasza do utworzenia środowiska wirtualnego podczas pierwszego tworzenia projektu.

1. Pojedynczy plik *App.py* zawiera trzy części. Pierwsza jest `import` instrukcją dla kolby, tworząc wystąpienie `Flask` klasy, która jest przypisana do zmiennej `app` , a następnie przypisując `wsgi_app` zmienną (która jest przydatna w przypadku wdrażania na hoście sieci Web, ale nie w obecnym czasie):

    ```python
    from flask import Flask
    app = Flask(__name__)

    # Make the WSGI interface available at the top level so wfastcgi can get it.
    wsgi_app = app.wsgi_app
    ```

1. Druga część, na końcu pliku, to Bit opcjonalnego kodu, który rozpoczyna się na serwerze deweloperskim z określonym wartościami hosta i portów pobranymi ze zmiennych środowiskowych (domyślnie: 5555):

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

1. Trzeci to krótki bit kodu, który przypisuje funkcję do trasy URL, co oznacza, że funkcja udostępnia zasób identyfikowany przez adres URL. Można definiować trasy przy użyciu dekoratora kolby `@app.route` , którego argument jest względnym adresem URL z katalogu głównego witryny. Jak widać w kodzie, funkcja tutaj zwraca tylko ciąg tekstowy, który wystarcza do renderowania przeglądarki. W krokach, które obserwuję, możesz renderować bogatsze strony za pomocą języka HTML.

    ```python
    @app.route('/')
    def hello():
        """Renders a sample page."""
        return "Hello World!"
    ```

### <a name="question-what-is-the-purpose-of-the-__name__-argument-to-the-flask-class"></a>Pytanie: Jakie jest przeznaczenie argumentu __name__ w klasie kolb?

Odpowiedź: argument jest nazwą modułu lub pakietu aplikacji i zawiera informacje o kolbie, gdzie szukać szablonów, plików statycznych i innych zasobów należących do aplikacji. W przypadku aplikacji znajdujących się w jednym module `__name__` zawsze jest to właściwa wartość. Jest ona również ważna dla rozszerzeń, które wymagają informacji debugowania. Aby uzyskać więcej informacji i dodatkowych argumentów, zobacz [dokumentację klasy kolb](https://flask.palletsprojects.com/en/1.0.x/api/#flask.Flask) (Flask.pocoo.org).

### <a name="question-can-a-function-have-more-than-one-route-decorator"></a>Pytanie: czy funkcja może mieć więcej niż jedną trasę Dekoratora?

Odpowiedź: tak, możesz użyć dowolną liczbę dekoratory, jeśli ta sama funkcja obsługuje wiele tras. Na przykład, aby użyć `hello` funkcji dla obu "/" i "/Hello", należy użyć następującego kodu:

```python
@app.route('/')
@app.route('/hello')
def hello():
    """Renders a sample page."""
    return "Hello World!"
```

<a name="qa-url-variables"></a>

### <a name="question-how-does-flask-work-with-variable-url-routes-and-query-parameters"></a>Pytanie: jak działa Kolba ze zmiennymi adresami URL i parametrami zapytania?

Odpowiedź: w trasie Oznacz każdą zmienną za pomocą `<variable_name>` , a Kolba przekazuje zmienną do funkcji przy użyciu nazwanego argumentu w ścieżce URL. Na przykład trasa w formie `/hello/<name>` generuje argument ciągu wywoływany `name` do funkcji. Parametry zapytania są dostępne za pomocą właściwości, w odróżnieniu `request.args` od `request.args.get` metody. Więcej informacji można znaleźć w dokumentacji dotyczącej [obiektu request](https://flask.palletsprojects.com/en/1.1.x/quickstart/#the-request-object) w kolbie.

```python
# URL: /hello/<name>?message=Have%20a%20nice%20day
@app.route('/hello/<name>')
def hello(name):
    msg = request.args.get('message','')
    return "Hello " + name + "! "+ msg + "."
```

Aby zmienić typ, należy prefiksować zmienną z `int` , `float` , `path` (która akceptuje ukośniki do nazw folderów odróżnić) i `uuid` . Aby uzyskać szczegółowe informacje, zobacz [reguły zmiennych](https://flask.palletsprojects.com/en/1.0.x/quickstart/#variable-rules) w dokumentacji dotyczącej kolb.

### <a name="question-can-visual-studio-generate-a-requirementstxt-file-from-a-virtual-environment-after-i-install-other-packages"></a>Pytanie: czy program Visual Studio może generować plik requirements.txt ze środowiska wirtualnego po zainstalowaniu innych pakietów?

Odpowiedź: Tak. Rozwiń węzeł **środowiska Python** , kliknij prawym przyciskiem myszy środowisko wirtualne i wybierz polecenie **Generuj requirements.txt** . Dobrym sposobem jest użycie tego polecenia okresowo podczas modyfikowania środowiska i zatwierdzić zmiany *requirements.txt* do kontroli źródła wraz ze wszystkimi innymi zmianami kodu, które są zależne od tego środowiska. W przypadku skonfigurowania ciągłej integracji na serwerze kompilacji należy wygenerować plik i zatwierdzić zmiany przy każdej modyfikacji środowiska.

## <a name="step-1-5-run-the-project"></a>Krok 1-5: uruchamianie projektu

1. W programie Visual Studio wybierz pozycję **Debuguj**  >  **Rozpocznij debugowanie** (**F5**) lub przycisk **serwer sieci Web** na pasku narzędzi (widoczna przeglądarka może się różnić):

    ![Przycisk paska narzędzi uruchamiania serwera sieci Web w programie Visual Studio](media/tutorials-common/run-web-server-toolbar-button.png)

1. Każde polecenie przypisuje losowy numer portu do zmiennej środowiskowej portu, a następnie uruchamia polecenie `python app.py` . Kod uruchamia aplikację przy użyciu tego portu w ramach serwera projektowego kolby. Jeśli program Visual Studio **nie może uruchomić debugera** z komunikatem o braku pliku startowego, kliknij prawym przyciskiem myszy pozycję **App.py** w **Eksplorator rozwiązań** i wybierz polecenie **Ustaw jako plik startowy**.

1. Po uruchomieniu serwera zostanie wyświetlone okno konsoli z otwartym dziennikiem serwera. Program Visual Studio automatycznie otwiera przeglądarkę do `http://localhost:<port>` , gdzie powinien zostać wyświetlony komunikat renderowany przez `hello` funkcję:

    ![Widok domyślny projektu kolby](media/flask/step01-first-run-success.png)

1. Gdy wszystko będzie gotowe, Zatrzymaj serwer, zamykając okno konsoli lub korzystając z polecenia **Debuguj**  >  **zatrzymywanie debugowania** w programie Visual Studio.

### <a name="question-whats-the-difference-between-using-the-debug-menu-commands-and-the-server-commands-on-the-projects-python-submenu"></a>Pytanie: Jaka jest różnica między użyciem poleceń menu Debuguj i poleceń serwera w podmenu środowiska Python projektu?

Odpowiedź: oprócz poleceń menu **Debuguj** i przycisków paska narzędzi można również uruchomić serwer przy użyciu   >  polecenia **Uruchom serwer uruchomieniowy** Python lub **Python**  >  **Uruchom serwer debugowania** w menu kontekstowym projektu. Oba polecenia otwierają okno konsoli, w którym widoczny jest lokalny adres URL (localhost: Port) dla uruchomionego serwera. Należy jednak ręcznie otworzyć przeglądarkę z tym adresem URL i uruchomić serwer debugowania nie uruchamia automatycznie debugera programu Visual Studio. Możesz dołączyć debuger do uruchomionego procesu później, jeśli chcesz, przy użyciu polecenia **Debuguj**  >  **Dołącz do procesu** .

## <a name="next-steps"></a>Następne kroki

W tym momencie projekt kolby podstawowej zawiera kod uruchomienia i kod strony w tym samym pliku. Najlepiej oddzielić te dwa kwestie, a także oddzielić kod HTML i dane przy użyciu szablonów.

> [!div class="nextstepaction"]
> [Tworzenie aplikacji do kolby z widokami i szablonami stron](learn-flask-visual-studio-step-02-create-app.md)

## <a name="go-deeper"></a>Przejdź głębiej

- [Kolba szybkiego startu](https://flask.palletsprojects.com/en/1.0.x/quickstart/) (Flask.pocoo.org)
- Kod źródłowy samouczka w witrynie GitHub: [Microsoft/Python-Sample-vs-Learning-Kolba](https://github.com/Microsoft/python-sample-vs-learning-flask)
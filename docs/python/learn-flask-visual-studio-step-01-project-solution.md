---
title: Dowiedz się samouczek Kolby w programie Visual Studio krok 1, podstawy kolby
titleSuffix: ''
description: Przewodnik podstawowych Flask w kontekście projektów programu Visual Studio, w tym wymagania wstępne, Git i środowisk wirtualnych.
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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "79302848"
---
# <a name="tutorial-get-started-with-the-flask-web-framework-in-visual-studio"></a>Samouczek: Wprowadzenie do struktury sieci Web Flask w programie Visual Studio

[Flask](https://palletsprojects.com/p/flask/) to lekka struktura języka Python dla aplikacji sieci web, która zawiera podstawy routingu adresów URL i renderowania stron.

Flask jest nazywany "mikro" framework, ponieważ nie bezpośrednio zapewniają funkcje, takie jak sprawdzanie poprawności formularza, abstrakcji bazy danych, uwierzytelniania i tak dalej. Takie funkcje są zamiast tego dostarczane przez specjalne pakiety Pythona o nazwie *rozszerzenia Flask*. Rozszerzenia bezproblemowo integrują się z kolbą, tak aby wyglądały tak, jakby były częścią samej kolby. Na przykład flask sam nie zapewnia aparat szablonu strony. Templowanie jest dostarczane przez rozszerzenia, takie jak Jinja i Jade, jak pokazano w tym samouczku.

Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:

> [!div class="checklist"]
> - Tworzenie podstawowego projektu kolby w repozytorium Git przy użyciu szablonu "Pusty projekt sieci Web kolby" (krok 1)
> - Tworzenie aplikacji Flask z jedną stroną i renderowanie tej strony przy użyciu szablonu (krok 2)
> - Obsługa plików statycznych, dodawanie stron i używanie dziedziczenia szablonów (krok 3)
> - Użyj szablonu Flask Web Project, aby utworzyć aplikację z wieloma stronami i responsywnym projektem (krok 4)
> - Szablon projektu sieci Web Sondy Flask służy do tworzenia aplikacji sondowania, która używa różnych opcji magazynu (magazynu platformy Azure, mongodb lub pamięci).

W trakcie tych kroków można utworzyć jedno rozwiązanie programu Visual Studio, który zawiera trzy oddzielne projekty. Projekt można utworzyć przy użyciu różnych szablonów projektu Flask, które są dołączone do programu Visual Studio. Utrzymując projekty w tym samym rozwiązaniu, można łatwo przełączać się między różnymi plikami do porównania.

> [!Note]
> Ten samouczek różni się od [przewodnika Szybki start dla kolb,](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json) tym, że dowiesz się więcej o Flask, a także o tym, jak korzystać z różnych szablonów projektów Flask, które zapewniają bardziej rozbudowany punkt wyjścia dla własnych projektów. Na przykład szablony projektów automatycznie instalują pakiet Flask podczas tworzenia projektu, zamiast konieczności ręcznego instalowania pakietu, jak pokazano w przewodniku Szybki start.

## <a name="prerequisites"></a>Wymagania wstępne

- Visual Studio 2017 lub nowsze w systemie Windows z następującymi opcjami:
  - Obciążenie **programistyczne języka Python** **(obciążenie karty** w instalatorze). Aby uzyskać instrukcje, zobacz [Instalowanie obsługi języka Python w programie Visual Studio](installing-python-support-in-visual-studio.md).
  - **Git dla systemu Windows** i **rozszerzenie GitHub dla programu Visual Studio** na karcie Poszczególne **składniki** w obszarze **Narzędzia kodu**.

Szablony projektów flask są dołączone do wszystkich wcześniejszych wersji narzędzi Python Tools for Visual Studio, choć szczegóły mogą się różnić od tego, co zostało omówione w tym samouczku.

Programowanie języka Python nie jest obecnie obsługiwane w programie Visual Studio dla komputerów Mac. Na komputerach Mac i Linux użyj [rozszerzenia Python w programie Visual Studio Code](https://code.visualstudio.com/docs/python/python-tutorial).

## <a name="step-1-1-create-a-visual-studio-project-and-solution"></a>Krok 1-1: Tworzenie projektu i rozwiązania programu Visual Studio

1. W programie Visual Studio wybierz pozycję **Plik** > **nowego** > **projektu**, wyszukaj hasło "Kolby" i wybierz szablon Pusty projekt sieci **Web kolby.** (Szablon znajduje się również w obszarze **Python** > **Web** na liście po lewej stronie).

    ![Nowe okno dialogowe projektu w programie Visual Studio dla pustego projektu sieci Web kolby](media/flask/step01-new-blank-project.png)

1. W polach u dołu okna dialogowego wprowadź następujące informacje (jak pokazano na poprzedniej grafice), a następnie wybierz **przycisk OK:**

    - **Nazwa**: ustaw nazwę projektu programu Visual Studio na **BasicProject**. Ta nazwa jest również używana dla projektu Flask.
    - **Lokalizacja**: określ lokalizację, w której ma być utworzone rozwiązanie i projekt programu Visual Studio.
    - **Nazwa rozwiązania:** zestaw **LearningFlask**, który jest odpowiedni dla rozwiązania jako kontener dla wielu projektów w tym samouczku.
    - **Tworzenie katalogu dla rozwiązania**: Pozostaw zestaw (domyślny).
    - **Utwórz nowe repozytorium Git:** Wybierz tę opcję (która jest domyślnie wyczyszczona), aby program Visual Studio utworzył lokalne repozytorium Git podczas tworzenia rozwiązania. Jeśli nie widzisz tej opcji, uruchom instalator programu Visual Studio i dodaj rozszerzenie **Git dla systemu Windows** i **GitHub dla programu Visual Studio** na karcie Poszczególne **składniki** w obszarze **Narzędzia kodu**.

1. Po chwili visual studio monituje o okno dialogowe z informacją **Ten projekt wymaga pakietów zewnętrznych** (pokazano poniżej). To okno dialogowe jest wyświetlane, ponieważ szablon zawiera plik *requirements.txt* odwołujący się do najnowszego pakietu Flask 1.x. (Wybierz **pokaż wymagane pakiety,** aby zobaczyć dokładne zależności).

    ![Monit mówiąc, że projekt wymaga pakietów zewnętrznych](media/tutorials-common/step01-requirements-prompt-install-myself.png)

1. Wybierz opcję **zainstaluję je samodzielnie**. Wkrótce utworzysz środowisko wirtualne, aby upewnić się, że jest wykluczone z kontroli źródła. (Środowisko zawsze można utworzyć na podstawie *pliku requirements.txt).*

## <a name="step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository"></a>Krok 1-2: Zbadaj kontrolki Git i opublikuj w zdalnym repozytorium

Ponieważ w oknie dialogowym **Nowy projekt** **wybrano repozytorium Utwórz nowy Git,** projekt jest już zatwierdzony do kontroli źródła lokalnego zaraz po zakończeniu procesu tworzenia. W tym kroku zapoznajesz się z formantami Git programu Visual Studio i oknem **Eksploratora zespołu,** w którym pracujesz z kontrolą źródła.

1. Sprawdź kontrolki Git w dolnym rogu okna głównego programu Visual Studio. Od lewej do prawej te formanty pokazują nieuprawione zatwierdzenia, niezatwierdzone zmiany, nazwę repozytorium i bieżącą gałąź:

    ![Formanty git w oknie programu Visual Studio](media/flask/step01-git-controls.png)

    > [!Note]
    > Jeśli nie wybierzesz **repozytorium Utwórz nowy Git** w oknie dialogowym **Nowy projekt,** formanty Git pokażą tylko polecenie **dodaj do źródła,** które tworzy lokalne repozytorium.
    >
    > ![Dodaj do kontroli źródła pojawia się w programie Visual Studio, jeśli nie utworzono repozytorium](media/tutorials-common/step01-git-add-to-source-control.png)

1. Wybierz przycisk zmiany, a program Visual Studio otworzy okno **Eksploratora zespołu** na stronie **Zmiany.** Ponieważ nowo utworzony projekt jest już zobowiązana do kontroli źródła automatycznie, nie widać żadnych oczekujących zmian.

    ![Okno Eksploratora zespołu na stronie Zmiany](media/flask/step01-team-explorer-changes.png)

1. Na pasku stanu programu Visual Studio wybierz przycisk unpushed commits (strzałka w górę z **2**), aby otworzyć stronę **Synchronizacja** w **Eksploratorze zespołu**. Ponieważ masz tylko repozytorium lokalne, strona udostępnia łatwe opcje publikowania repozytorium w różnych repozytoriach zdalnych.

    ![Okno Eksploratora zespołu z dostępnymi opcjami repozytorium Git dla kontroli źródła](media/flask/step01-team-explorer.png)

    Możesz wybrać dowolną usługę dla własnych projektów. W tym samouczku pokazano użycie usługi GitHub, w której wypełniony przykładowy kod samouczka jest obsługiwany w repozytorium [Microsoft/python-sample-vs-learning-flask.](https://github.com/Microsoft/python-sample-vs-learning-flask)

1. Po wybraniu dowolnego z **formantów Publikowania,** **Team Explorer** monituje o więcej informacji. Na przykład podczas publikowania próbki dla tego samouczka, repozytorium trzeba było utworzyć najpierw, w którym to przypadku opcja **Wypychanie do repozytorium zdalnego** została użyta z adresem URL repozytorium.

    ![Okno Eksploratora zespołu do wypychania do istniejącego repozytorium zdalnego](media/flask/step01-push-to-github.png)

    Jeśli nie masz istniejącego repozytorium, **opcje publikowania w usłudze GitHub** i **wypychania do usługi Azure DevOps** umożliwiają utworzenie go bezpośrednio z poziomu programu Visual Studio.

1. Podczas pracy nad tym samouczkiem, dostać się do nawyku okresowego używania formantów w programie Visual Studio do zatwierdzania i wypychania zmian. Ten samouczek przypomina w odpowiednich punktach.

> [!Tip]
> Aby szybko poruszać się w **Eksploratorze zespołu,** wybierz nagłówek (który **odczytuje zmiany** lub **Wypychaj** powyższe obrazy), aby wyświetlić wyskakujące menu dostępnych stron.

### <a name="question-what-are-some-advantages-of-using-source-control-from-the-beginning-of-a-project"></a>Pytanie: Jakie są pewne zalety korzystania z kontroli źródła od początku projektu?

Odpowiedź: Przede wszystkim przy użyciu kontroli źródła od początku, zwłaszcza jeśli używasz również zdalnego repozytorium, zapewnia regularne tworzenie kopii zapasowych poza witryną projektu. W przeciwieństwie do utrzymania projektu tylko w lokalnym systemie plików, kontrola źródła zapewnia również pełną historię zmian i łatwą możliwość ponownego ponownego pojedynczego pliku lub całego projektu do poprzedniego stanu. Ta historia zmian pomaga określić przyczynę regresji (błędy testu). Ponadto kontrola źródła jest niezbędna, jeśli wiele osób pracuje nad projektem, ponieważ zarządza nadpisywami i zapewnia rozwiązywanie konfliktów. Na koniec kontrola źródła, która jest zasadniczo formą automatyzacji, ustawia cię dobrze do automatyzacji kompilacji, testowania i zarządzania wydaniami. To naprawdę pierwszy krok w użyciu DevOps dla projektu, a ponieważ bariery wejścia są tak niskie, naprawdę nie ma powodu, aby nie używać kontroli źródła od początku.

Aby uzyskać dalsze dyskusje na temat kontroli źródła jako automatyzacji, zobacz [Źródło prawdy: Rola repozytoriów w DevOps](https://msdn.microsoft.com/magazine/mt763232), artykuł w MSDN Magazine napisany dla aplikacji mobilnych, który dotyczy również aplikacji internetowych.

### <a name="question-can-i-prevent-visual-studio-from-auto-committing-a-new-project"></a>Pytanie: Czy mogę uniemożliwić programowi Visual Studio automatyczne zatwierdzanie nowego projektu?

Odpowiedź: Tak. Aby wyłączyć automatyczne zatwierdzanie, przejdź do strony **Ustawienia** w **Eksploratorze zespołu**, wybierz pozycję**Ustawienia globalne** **Git** > , wyczyść opcję z etykietą **Zatwierdzanie zmian po domyślnym scaleniu**, a następnie wybierz pozycję **Aktualizuj**.

## <a name="step-1-3-create-the-virtual-environment-and-exclude-it-from-source-control"></a>Krok 1-3: Tworzenie środowiska wirtualnego i wykluczanie go z kontroli źródła

Teraz, po skonfigurowaniu kontroli źródła dla projektu, można utworzyć środowisko wirtualne niezbędne pakiety Flask, które wymaga projektu. Następnie można użyć **Eksploratora zespołu,** aby wykluczyć folder środowiska z kontroli źródła.

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy węzeł **Środowiska języka Python** i wybierz polecenie Dodaj środowisko **wirtualne**.

    ![Polecenie Dodaj środowisko wirtualne w Eksploratorze rozwiązań](media/flask/step01-add-virtual-environment-command.png)

1. Zostanie wyświetlone okno dialogowe **Dodaj środowisko wirtualne** z komunikatem **"Znaleźliśmy plik requirements.txt".** Ten komunikat wskazuje, że program Visual Studio używa tego pliku do skonfigurowania środowiska wirtualnego.

    ![Dodawanie okna dialogowego środowiska wirtualnego z komunikatem requirements.txt](media/tutorials-common/step01-add-virtual-environment-found-requirements.png)

1. Wybierz **pozycję Utwórz,** aby zaakceptować wartości domyślne. (Można zmienić nazwę środowiska wirtualnego, jeśli chcesz, który po prostu zmienia `env` nazwę jego podfolder, ale jest standardową konwencją.)

1. Zgoda na uprawnienia administratora, jeśli zostanie wyświetlony monit, a następnie ciągnij za cierpliwość przez kilka minut, podczas gdy program Visual Studio pobiera i instaluje pakiety, co dla Flask i jego zależności oznacza rozszerzenie około tysiąca plików w ponad 100 podfolderach. Postęp można zobaczyć w oknie **Dane wyjściowe** programu Visual Studio. Podczas oczekiwania zastanów się nad sekcjami Pytania, które następują po tym. Możesz również zobaczyć opis zależności Flask na stronie [instalacji kolby](https://flask.palletsprojects.com/en/1.0.x/installation/#installation) (flask.pcocoo.org).

1. W formancie Git programu Visual Studio (na pasku stanu) wybierz wskaźnik zmian (który pokazuje **99&#42;), **który otwiera stronę **Zmiany** w **Eksploratorze zespołu.**

    Tworzenie środowiska wirtualnego przyniosło setki zmian, ale nie trzeba uwzględniać żadnego z nich w kontroli źródła, ponieważ użytkownik (lub ktokolwiek inny klonuje projekt) zawsze może odtworzyć środowisko z *pliku requirements.txt*.

    Aby wykluczyć środowisko wirtualne, kliknij prawym przyciskiem myszy folder **env** i wybierz polecenie **Ignoruj te elementy lokalne**.

    ![Ignorowanie środowiska wirtualnego w zmianach kontroli źródła](media/flask/step01-ignore-local-items.png)

1. Po wyłączeniu środowiska wirtualnego jedynymi pozostałymi zmianami są plik projektu i *.gitignore*. Plik *.gitignore* zawiera dodany wpis dla folderu środowiska wirtualnego. Możesz kliknąć dwukrotnie plik, aby wyświetlić różnice.

1. Wprowadź komunikat o zatwierdzeniu i wybierz przycisk **Zatwierdz wszystko,** a następnie naciśnij zatwierdzenia do zdalnego repozytorium, jeśli chcesz.

### <a name="question-why-do-i-want-to-create-a-virtual-environment"></a>Pytanie: Dlaczego chcę utworzyć środowisko wirtualne?

Odpowiedź: Środowisko wirtualne to świetny sposób na wyizolowanie dokładnych zależności aplikacji. Taka izolacja pozwala uniknąć konfliktów w globalnym środowisku Języka Python i ułatwia zarówno testowanie, jak i współpracę. Z biegiem czasu, podczas tworzenia aplikacji, niezmiennie przynosisz wiele przydatnych pakietów Pythona. Przechowując pakiety w środowisku wirtualnym specyficznym dla projektu, można łatwo zaktualizować plik *requirements.txt* projektu, który opisuje to środowisko, które jest zawarte w kontroli źródła. Gdy projekt jest kopiowany do innych komputerów, w tym serwerów kompilacji, serwerów wdrożeniowych i innych komputerów deweloperskich, można łatwo odtworzyć środowisko przy użyciu tylko *pliku requirements.txt* (dlatego środowisko nie musi znajdować się pod kontrolą źródła). Aby uzyskać więcej informacji, zobacz [Używanie środowisk wirtualnych](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

### <a name="question-how-do-i-remove-a-virtual-environment-thats-already-committed-to-source-control"></a>Pytanie: Jak usunąć środowisko wirtualne, które jest już zaangażowane w kontrolę źródła?

Odpowiedź: Najpierw edytuj plik *.gitignore,* aby wykluczyć folder: znajdź sekcję na końcu z komentarzem `# Python Tools for Visual Studio (PTVS)` i `/BasicProject/env`dodaj nowy wiersz dla folderu środowiska wirtualnego, na przykład . (Ponieważ program Visual Studio nie pokazuje pliku w **Eksploratorze rozwiązań,** otwórz go bezpośrednio za pomocą polecenia menu > **Otwórz** > **File** **plik.** Możesz również otworzyć plik z **Eksploratora zespołu**: na stronie **Ustawienia** wybierz **pozycję Ustawienia repozytorium**, przejdź do sekcji **Ignoruj & atrybuty,** a następnie wybierz łącze **Edytuj** obok **.gitignore**.)

Po drugie, otwórz okno polecenia, przejdź do folderu takiego jak *BasicProject,* `git rm -r env`który zawiera folder środowiska wirtualnego, taki jak *env,* i uruchom . Następnie zaobenduj te`git commit -m 'Remove venv'`zmiany z wiersza polecenia ( ) lub zaobenduj na stronie **Zmiany** **Eksploratora zespołu**.

## <a name="step-1-4-examine-the-boilerplate-code"></a>Krok 1-4: Zbadaj kod płyty kotłowej

1. Po zakończeniu tworzenia projektu zostanie wyświetlonego rozwiązanie i projekt w **Eksploratorze rozwiązań,** gdzie projekt zawiera tylko dwa pliki, *app.py* i *requirements.txt:*

    ![Puste pliki projektu kolby w Eksploratorze rozwiązań](media/flask/step01-blank-flask-project-in-solution-explorer.png)

1. Jak wspomniano wcześniej, plik *requirements.txt* określa zależność pakietu Flask. Obecność tego pliku jest tym, co zachęca do tworzenia środowiska wirtualnego podczas pierwszego tworzenia projektu.

1. Pojedynczy plik *app.py* zawiera trzy części. Najpierw jest `import` instrukcja dla Flask, tworzenie `Flask` wystąpienia klasy, który jest `app`przypisany do `wsgi_app` zmiennej , a następnie przypisanie zmiennej (co jest przydatne podczas wdrażania do hosta sieci web, ale nie jest używany w chwili obecnej):

    ```python
    from flask import Flask
    app = Flask(__name__)

    # Make the WSGI interface available at the top level so wfastcgi can get it.
    wsgi_app = app.wsgi_app
    ```

1. Druga część, na końcu pliku, jest trochę opcjonalny kod, który uruchamia serwer programistyczny Flask z określonych wartości hosta i portu pobranych ze zmiennych środowiskowych (domyślnie localhost:5555):

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

1. Trzeci to krótki fragment kodu, który przypisuje funkcję do trasy adresu URL, co oznacza, że funkcja zapewnia zasób identyfikowany przez adres URL. Trasy można zdefiniować za `@app.route` pomocą dekoratora Flask, którego argument jest względny adres URL z katalogu głównego witryny. Jak widać w kodzie, funkcja zwraca tylko ciąg tekstowy, który jest wystarczający do renderowania przeglądarki. W kolejnych krokach renderujesz bogatsze strony za pomocą kodu HTML.

    ```python
    @app.route('/')
    def hello():
        """Renders a sample page."""
        return "Hello World!"
    ```

### <a name="question-what-is-the-purpose-of-the-__name__-argument-to-the-flask-class"></a>Pytanie: Jaki jest cel argumentu __nazwa__ do klasy Flask?

Odpowiedź: Argument jest nazwą modułu lub pakietu aplikacji i informuje Flask, gdzie szukać szablonów, plików statycznych i innych zasobów, które należą do aplikacji. W przypadku aplikacji zawartych `__name__` w jednym module jest zawsze właściwą wartością. Jest również ważne dla rozszerzeń, które wymagają informacji debugowania. Aby uzyskać więcej informacji i dodatkowe argumenty, zobacz [dokumentację klasy Flask](https://flask.palletsprojects.com/en/1.0.x/api/#flask.Flask) (flask.pocoo.org).

### <a name="question-can-a-function-have-more-than-one-route-decorator"></a>Pytanie: Czy funkcja może mieć więcej niż jeden dekorator trasy?

Odpowiedź: Tak, możesz użyć tylu dekoratorów, jeśli ta sama funkcja obsługuje wiele tras. Na przykład, aby `hello` użyć funkcji dla "/" i "/hello", użyj następującego kodu:

```python
@app.route('/')
@app.route('/hello')
def hello():
    """Renders a sample page."""
    return "Hello World!"
```

<a name="qa-url-variables"></a>

### <a name="question-how-does-flask-work-with-variable-url-routes-and-query-parameters"></a>Pytanie: Jak kolby działają ze zmiennymi trasami adresów URL i parametrami zapytania?

Odpowiedź: W trasie oznaczasz dowolną `<variable_name>`zmienną za pomocą , a Flask przekazuje zmienną do funkcji przy użyciu nazwanego argumentu. Zmienna może być częścią ścieżki adresu URL lub parametru zapytania. Na przykład trasa w formie `'/hello/<name>` generuje argument ciągu `name` wywoływany do `?message=<msg>` funkcji, a użycie w marszdzie analizuje wartość podana dla parametru `msg`zapytania "message=" i przekazuje ją do funkcji jako:

```python
@app.route('/hello/<name>?message=<msg>')
def hello(name, msg):
    return "Hello " + name + "! Message is " + msg + "."
```

Aby zmienić typ, przedrostek `float` `path` zmiennej z `int`, , (który akceptuje `uuid`ukośnie, aby nakreślić nazwy folderów) i . Aby uzyskać szczegółowe informacje, zobacz [Reguły zmienne](https://flask.palletsprojects.com/en/1.0.x/quickstart/#variable-rules) w dokumentacji kolby.

Parametry kwerendy są `request.args` również dostępne za `request.args.get` pośrednictwem właściwości, w szczególności za pośrednictwem metody. Aby uzyskać więcej informacji, zobacz [Request obiektu](https://flask.palletsprojects.com/en/1.0.x/quickstart/#the-request-object) w dokumentacji Flask.

### <a name="question-can-visual-studio-generate-a-requirementstxt-file-from-a-virtual-environment-after-i-install-other-packages"></a>Pytanie: Czy program Visual Studio może generować plik requirements.txt ze środowiska wirtualnego po zainstalowaniu innych pakietów?

Odpowiedź: Tak. Rozwiń węzeł **Środowiska języka Python,** kliknij prawym przyciskiem myszy środowisko wirtualne i wybierz polecenie **Generuj polecenie requirements.txt.** Dobrze jest używać tego polecenia okresowo podczas modyfikowania środowiska i zatwierdzania zmian *w requirements.txt* do kontroli źródła wraz z innymi zmianami kodu, które zależą od tego środowiska. Jeśli konfigurujesz ciągłą integrację na serwerze kompilacji, należy wygenerować plik i zatwierdzić zmiany przy każdym modyfikowaniu środowiska.

## <a name="step-1-5-run-the-project"></a>Krok 1-5: Uruchom projekt

1. W programie Visual Studio wybierz opcję **Debugowanie** > **start debugowania** **(F5)** lub użyj przycisku **Serwera sieci Web** na pasku narzędzi (widoczna przeglądarka może się różnić):

    ![Uruchamianie przycisku paska narzędzi serwera sieci Web w programie Visual Studio](media/tutorials-common/run-web-server-toolbar-button.png)

1. Albo polecenie przypisuje losowy numer portu do zmiennej `python app.py`środowiskowej PORT, a następnie uruchamia . Kod uruchamia aplikację przy użyciu tego portu w serwerze deweloperskim Flask. Jeśli program Visual Studio **mówi, że nie można uruchomić debugera** z komunikatem o braku pliku startowego, kliknij prawym przyciskiem myszy **app.py** w **Eksploratorze rozwiązań** i wybierz pozycję **Ustaw jako plik startowy**.

1. Po uruchomieniu serwera zostanie wyświetlone otwarte okno konsoli, w którym jest wyświetlany dziennik serwera. Visual Studio następnie automatycznie otwiera `http://localhost:<port>`przeglądarkę do , gdzie powinien `hello` zostać wyświetlony komunikat renderowany przez funkcję:

    ![Domyślny widok projektu kolby](media/flask/step01-first-run-success.png)

1. Po zakończeniu zatrzymaj serwer, zamykając okno konsoli lub używając polecenia **Debugowania** > **zatrzymaj debugowanie** w programie Visual Studio.

### <a name="question-whats-the-difference-between-using-the-debug-menu-commands-and-the-server-commands-on-the-projects-python-submenu"></a>Pytanie: Jaka jest różnica między używaniem poleceń menu debugowania a poleceniami serwera w podmenu Python projektu?

Odpowiedź: Oprócz poleceń menu **debugowania** i przycisków paska narzędzi można również **Python** > uruchomić serwer za pomocą poleceń**serwera uruchamiania** **języka Python** > lub Python**Run** w menu kontekstowym projektu. Oba polecenia otwierają okno konsoli, w którym jest widoczny lokalny adres URL (localhost:port) dla uruchomionego serwera. Należy jednak ręcznie otworzyć przeglądarkę z tym adresem URL, a uruchomienie serwera debugowania nie uruchamia automatycznie debugera programu Visual Studio. Debugera można dołączyć do uruchomionego procesu później, jeśli chcesz, za pomocą polecenia > **Debugowanie dołączania do procesu.** **Debug**

## <a name="next-steps"></a>Następne kroki

W tym momencie podstawowy projekt Flask zawiera kod startowy i kod strony w tym samym pliku. Najlepiej jest oddzielić te dwie kwestie, a także oddzielić kod HTML i dane za pomocą szablonów.

> [!div class="nextstepaction"]
> [Tworzenie aplikacji Flask z widokami i szablonami stron](learn-flask-visual-studio-step-02-create-app.md)

## <a name="go-deeper"></a>Głębiej

- [Szybki start kolby](https://flask.palletsprojects.com/en/1.0.x/quickstart/) (flask.pocoo.org)
- Kod źródłowy samouczka w usłudze GitHub: [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask)

---
title: Dowiedz się samouczek Flask w programie Visual Studio krok 2, widoki i szablony
titleSuffix: ''
description: Przewodnik podstawowych Flask w kontekście projektów programu Visual Studio, w szczególności kroki tworzenia aplikacji i przy użyciu widoków i szablonów.
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 03a0eb6808b2298e0727492978d9beb7cfaf2216
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "79302841"
---
# <a name="step-2-create-a-flask-app-with-views-and-page-templates"></a>Krok 2: Tworzenie aplikacji Flask z widokami i szablonami stron

**Poprzedni krok: [Tworzenie projektu i rozwiązania programu Visual Studio](learn-flask-visual-studio-step-01-project-solution.md)**

Co masz z kroku 1 tego samouczka jest aplikacja Flask z jednej strony i cały kod w jednym pliku. Aby umożliwić przyszłe opracowywanie, najlepiej refaktoryzować kod i utworzyć strukturę szablonów stron. W szczególności chcesz oddzielić kod dla widoków aplikacji od innych aspektów, takich jak kod startowy.

W tym kroku dowiesz się, jak:

> [!div class="checklist"]
> - Refaktoryzuje kod aplikacji, aby oddzielić widoki od kodu startowego (krok 2-1)
> - Renderowanie widoku przy użyciu szablonu strony (krok 2-2)

## <a name="step-2-1-refactor-the-project-to-support-further-development"></a>Krok 2-1: Refaktoryzator projektu wspierającego dalszy rozwój

W kodzie utworzonym przez szablon "Pusty projekt sieci Web flask" masz jeden plik *app.py,* który zawiera kod startowy obok jednego widoku. Aby umożliwić dalszy rozwój aplikacji z wieloma widokami i szablonami, najlepiej oddzielić te problemy.

1. W folderze projektu utwórz `HelloFlask` folder aplikacji o nazwie (kliknij prawym przyciskiem myszy projekt w **Eksploratorze rozwiązań** i wybierz pozycję **Dodaj** > **nowy folder).**

2. W folderze *HelloFlask* utwórz plik o nazwie * \_ \_\_\_init .py* z następującą zawartością, która tworzy `Flask` wystąpienie i ładuje widoki aplikacji (utworzone w następnym kroku):

    ```python
    from flask import Flask
    app = Flask(__name__)

    import HelloFlask.views
    ```

3. W folderze *HelloFlask* utwórz plik o nazwie *views.py* z następującą zawartością. Nazwa *views.py* jest ważna, ponieważ `import HelloFlask.views` używane * \_ \_w\_\_init .py*; jeśli nazwy nie są zgodne, zostanie wyświetlony błąd w czasie wykonywania.

    ```python
    from flask import Flask
    from HelloFlask import app

    @app.route('/')
    @app.route('/home')
    def home():
        return "Hello Flask!"
    ```

    Oprócz zmiany nazwy funkcji i `home`trasy do , ten kod zawiera kod renderowania strony `app` z *app.py* i importuje obiekt, który jest zadeklarowany * \_ \_w init\_\_.py*.

4. Utwórz podfolder w *HelloFlask* o nazwie *szablony*, który pozostaje pusty na razie.

5. W folderze głównym projektu zmień nazwę *app.py* na *runserver.py*i upewnij się, że zawartość jest zgodna z następującym kodem:

    ```python
    import os
    from HelloFlask import app    # Imports the code from HelloFlask/__init__.py

    if __name__ == '__main__':
        HOST = os.environ.get('SERVER_HOST', 'localhost')

        try:
            PORT = int(os.environ.get('SERVER_PORT', '5555'))
        except ValueError:
            PORT = 5555

        app.run(HOST, PORT)
    ```

6. Struktura projektu powinna wyglądać następująco:

    ![Struktura projektu po refaktoryzacji kodu](media/flask/step02-project-structure.png)

7. Wybierz **debugowanie** > **rozpocznij debugowanie** **(F5)** lub użyj przycisku Serwera sieci **Web** na pasku narzędzi (przeglądarka, która może się różnić), aby uruchomić aplikację i otworzyć przeglądarkę. Wypróbuj trasy adresu URL / i /home.

8. Można również ustawić punkty przerwania w różnych częściach kodu i ponownie uruchomić aplikację, aby wykonać sekwencję uruchamiania. Na przykład ustaw punkt przerwania w pierwszych wierszach *runserver.py* i *\_HelloFlask*init_*.py*, a w wierszu `return "Hello Flask!"` w *views.py*. Następnie uruchom ponownie aplikację **(Debug** > **Restart**, **Ctrl**+**F5**, lub przycisk paska narzędzi pokazanego poniżej) i krok po kroku (**F10**) kod lub uruchom z każdego punktu przerwania za pomocą **F5**.

    ![Przycisk Uruchom ponownie na pasku narzędzi debugowania w programie Visual Studio](media/debugging-restart-toolbar-button.png)

9. Zatrzymaj aplikację po zakończeniu.

### <a name="commit-to-source-control"></a>Zatwierdzanie do kontroli źródła

Ponieważ wprowadzono zmiany w kodzie i przetestowano je pomyślnie, teraz jest świetny czas, aby przejrzeć i zatwierdzić zmiany do kontroli źródła. Dalsze kroki w tym samouczku przypominają o odpowiednich czasach, aby ponownie zobowiązać się do kontroli źródła i odesłać do tej sekcji.

1. Wybierz przycisk zmiany u dołu programu Visual Studio (zakreślony poniżej), który przechodzi do **Eksploratora zespołu**.

    ![Przycisk Zmiany formantu źródła na pasku stanu programu Visual Studio](media/flask/step02-source-control-changes-button.png)

1. W **Eksploratorze zespołu**wprowadź komunikat o zatwierdzeniu, taki jak "Kod refaktoryzatora" i wybierz pozycję **Zatwierdź wszystkie**. Po zakończeniu zatwierdzania zostanie wyświetlony komunikat **Commit \<hash> utworzony lokalnie. Synchronizacja w celu udostępnienia zmian na serwerze.** Jeśli chcesz wypchnąć zmiany do zdalnego repozytorium, wybierz pozycję **Synchronizuj**, a następnie wybierz **pozycję Wypychaj** w obszarze **Zatwierdzeń wychodzących**. Można również gromadzić wiele lokalnych zatwierdzeń przed wypchnięciem do zdalnego.

    ![Wypychanie zatwierdzeń do zdalnego w Eksploratorze zespołu](media/flask/step02-source-control-push-to-remote.png)

### <a name="question-how-frequently-should-one-commit-to-source-control"></a>Pytanie: Jak często należy zobowiązać się do kontroli źródła?

Odpowiedź: Zatwierdzanie zmian w formancie źródłowym tworzy rekord w dzienniku zmian i punkt, do którego można przywrócić repozytorium, jeśli to konieczne. Każde zatwierdzenie można również zbadać pod kątem jego konkretnych zmian. Ponieważ zatwierdzenia w Git są niedrogie, lepiej wykonywać częste zatwierdzanie niż gromadzić większą liczbę zmian w jednym zatwierdzeniu. Oczywiście nie trzeba zatwierdzać każdej małej zmiany w poszczególnych plikach. Zazwyczaj należy zatwierdzić podczas dodawania funkcji, zmiana struktury, jak to zrobić w tym kroku lub zrobić kilka refaktoryzacji kodu. Również skontaktować się z innymi w zespole ziarnistość zatwierdzeń, które działają najlepiej dla wszystkich.

Jak często zatwierdzasz i jak często wypychasz zatwierdzenia do zdalnego repozytorium są dwa różne problemy. Przed wypchnięciem ich do repozytorium zdalnego można zgromadzić wiele zatwierdzeń w lokalnym repozytorium. Ponownie, jak często zatwierdzasz zależy od tego, jak zespół chce zarządzać repozytorium.

## <a name="step-2-2-use-a-template-to-render-a-page"></a>Krok 2-2: Renderowanie strony za pomocą szablonu

Funkcja, `home` która masz do tej pory w *views.py* generuje nic więcej niż zwykły tekst odpowiedzi HTTP dla strony. Jednak większość rzeczywistych stron internetowych odpowiada bogatymi stronami HTML, które często zawierają dane na żywo. Istotnie głównym powodem do definiowania widoku za pomocą funkcji jest dynamiczne generowanie zawartości.

Ponieważ zwracana wartość widoku jest tylko ciągiem, można utworzyć dowolny kod HTML w ciągu, używając zawartości dynamicznej. Jednak ponieważ najlepiej jest oddzielić znaczniki od danych, znacznie lepiej jest umieścić znaczników w szablonie i zachować dane w kodzie.

1. Na początek edytuj *views.py,* aby zawierała następujący kod, który używa wbudowanego kodu HTML dla strony z zawartością dynamiczną:

    ```python
    from datetime import datetime
    from flask import render_template
    from HelloFlask import app

    @app.route('/')
    @app.route('/home')
    def home():
        now = datetime.now()
        formatted_now = now.strftime("%A, %d %B, %Y at %X")

        html_content = "<html><head><title>Hello Flask</title></head><body>"
        html_content += "<strong>Hello Flask!</strong> on " + formatted_now
        html_content += "</body></html>"

        return html_content
    ```

1. Uruchom aplikację i odśwież stronę kilka razy, aby zobaczyć, że data/godzina jest aktualizowana. Zatrzymaj aplikację po zakończeniu.

1. Aby przekonwertować renderowanie strony na szablon, utwórz plik o nazwie *index.html* w folderze *szablonów* z następującą zawartością, gdzie `{{ content }}` jest symbol zastępczy lub token zastępczy (nazywany również *zmienną szablonu),* dla którego podajesz wartość w kodzie:

    ```html
    <html>
        <head><title>Hello Flask</title></head>

        <body>
            {{ content }}
        </body>
    </html>
    ```

1. Zmodyfikuj `home` funkcję, aby załadować `render_template` szablon i podać wartość dla "zawartości", która odbywa się przy użyciu nazwanego argumentu pasującego do nazwy symbolu zastępczego. Flask automatycznie wyszukuje szablony w folderze *szablonów,* więc ścieżka do szablonu jest względem tego folderu:

    ```python
    def home():
        now = datetime.now()
        formatted_now = now.strftime("%A, %d %B, %Y at %X")

        return render_template(
            "index.html",
            content = "<strong>Hello, Flask!</strong> on " + formatted_now)
    ```

1. Uruchom aplikację zobacz wyniki i obserwować, że wbudowany `content` kod HTML w wartości nie jest renderowany *jako* HTML, ponieważ aparat szablonów (Jinja) automatycznie ucieka zawartości HTML. Automatyczne ucieczki zapobiega przypadkowym lukom w zabezpieczeniach ataków iniekcji: deweloperzy często zbierają dane wejściowe z jednej strony i używają ich jako wartości w innej za pośrednictwem symbolu zastępczego szablonu. Ucieczka służy również jako przypomnienie, że znowu najlepiej jest zachować HTML z kodu.

    W związku z tym *szablony przeglądu\index.html* zawierają różne symbole zastępcze dla każdego fragmentu danych w znacznikach:

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
        </head>
        <body>
            <strong>{{ message }}</strong>{{ content }}
        </body>
    </html>
    ```

    Następnie zaktualizuj funkcję, `home` aby podać wartości dla wszystkich symboli zastępczych:

    ```python
    def home():
        now = datetime.now()
        formatted_now = now.strftime("%A, %d %B, %Y at %X")

        return render_template(
            "index.html",
            title = "Hello Flask",
            message = "Hello, Flask!",
            content = " on " + formatted_now)
    ```

1. Uruchom aplikację ponownie, aby zobaczyć poprawnie renderowane dane wyjściowe.

    ![Uruchamianie aplikacji przy użyciu szablonu](media/flask/step02-result.png)

1. Zaajmuj zmiany w kontroli źródła i aktualizuj zdalne repozytorium, w razie potrzeby, zgodnie z opisem w [kroku 2-1](#commit-to-source-control).

### <a name="question-do-page-templates-have-to-be-in-a-separate-file"></a>Pytanie: Czy szablony stron muszą znajdować się w osobnym pliku?

Odpowiedź: Chociaż szablony są zwykle przechowywane w oddzielnych plikach HTML, można również użyć szablonu wbudowanego. Zaleca się jednak użycie oddzielnego pliku w celu zachowania czystej separacji między znacznikami a kodem.

### <a name="question-must-templates-use-the-html-file-extension"></a>Pytanie: Czy szablony muszą używać rozszerzenia pliku .html?

Odpowiedź: Rozszerzenie *.html* dla plików szablonów stron jest całkowicie opcjonalne, ponieważ zawsze identyfikujesz `render_template` dokładną ścieżkę względną do pliku w pierwszym argumentie do funkcji. Jednak visual studio (i innych edytorów) zazwyczaj daje funkcje, takie jak uzupełnianie kodu i zabarwienie składni z plikami *.html,* co przewyższa fakt, że szablony stron nie są ściśle HTML.

W rzeczywistości podczas pracy z projektem Flask program Visual Studio automatycznie wykrywa, kiedy edytowany plik HTML jest w rzeczywistości szablonem Flask i zapewnia pewne funkcje autouzupełniania. Na przykład po rozpoczęciu wpisywania komentarza szablonu strony flask, `{#` `#}` program Visual Studio automatycznie udostępnia znaki zamykające. Polecenia **Wybór komentarza** i **Odkomentowanie (w** menu **Edytuj** > **zaawansowane** i na pasku narzędzi) używają również komentarzy szablonów zamiast komentarzy HTML.

### <a name="question-can-templates-be-organized-into-further-subfolders"></a>Pytanie: Czy szablony można organizować w kolejne podfoldery?

Odpowiedź: Tak, można użyć podfolderów, a następnie odwołać `render_template`się do ścieżki względnej w obszarze szablony w *wywołaniach* do . Jest to świetny sposób na skuteczne tworzenie obszarów nazw dla szablonów.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Obsługa plików statycznych, dodawanie stron i używanie dziedziczenia szablonów](learn-flask-visual-studio-step-03-serve-static-files-add-pages.md)

## <a name="go-deeper"></a>Głębiej

- [Szybki start kolby — szablony renderowania](https://flask.palletsprojects.com/en/1.0.x/quickstart/#rendering-templates) (flask.pocoo.org)
- Kod źródłowy samouczka w usłudze GitHub: [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask)

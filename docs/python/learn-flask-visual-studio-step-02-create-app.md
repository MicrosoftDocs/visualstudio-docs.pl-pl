---
title: Poznaj samouczek Flask w programie Visual Studio w kroku 2, widoki i szablony
titleSuffix: ''
description: Przewodnik po podstawy Flask w kontekście projektów programu Visual Studio, w szczególności kroki tworzenia aplikacji i korzystanie z widoków i szablonów.
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 2526a6bcf6dc03379c22e38fb646acba450a9ec5
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59366604"
---
# <a name="step-2-create-a-flask-app-with-views-and-page-templates"></a>Krok 2. Tworzenie aplikacji Flask za pomocą widoków i szablonów stron

**Poprzedniego kroku: [Tworzenie projektu programu Visual Studio i rozwiązania](learn-flask-visual-studio-step-01-project-solution.md)**

Co znajduje się w kroku 1 w tym samouczku jest aplikacji Flask za pomocą jednej stronie, a cały kod w jednym pliku. Aby umożliwić do przyszłego rozwoju, najlepiej jest Refaktoryzacja kodu i tworzenia struktury szablony stron. W szczególności chcesz oddzielić kodu dla widoków aplikacji od innych aspektów, takich jak kod startowy.

W tym kroku teraz dowiesz się, jak:

> [!div class="checklist"]
> - Refaktoryzacja kodu aplikacji do oddzielania widoków z uruchamiania kodu (krok 2 - 1)
> - Renderowanie widoku, używając szablonu strony (krok 2 z 2)

## <a name="step-2-1-refactor-the-project-to-support-further-development"></a>Krok 1 z 2 Refaktoryzuj projektu dalszych obsługi opracowywania aplikacji

W kodzie, utworzona przez szablon "Pusty projekt sieci Web Flask", możesz mieć pojedynczy *app.py* pliku, który zawiera kod uruchamiający wraz z jednego widoku. Aby zezwolić na dalszy rozwój aplikacji za pomocą wielu widoków i szablonów, najlepiej jest do oddzielania tych problemów.

1. W folderze projektu, należy utworzyć folder aplikacji o nazwie `HelloFlask` (kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierz **Dodaj** > **nowy Folder** .)

2. W *HelloFlask* folderze utwórz plik o nazwie  *\_ \_init\_\_.py* z następującą zawartością, które tworzy `Flask` wystąpienia i ładuje widoków aplikacji (utworzonym w następnym kroku):

    ```python
    from flask import Flask
    app = Flask(__name__)

    import HelloFlask.views
    ```

3. W *HelloFlask* folderze utwórz plik o nazwie *views.py* z następującą zawartością. Nazwa *views.py* jest ważne, ponieważ użyto `import HelloFlask.views` w ramach  *\_ \_init\_\_PY*; Jeśli zostanie wyświetlony błąd w czasie wykonywania nazwy nie są zgodne.

    ```python
    from flask import Flask
    from HelloFlask import app

    @app.route('/')
    @app.route('/home')
    def home():
        return "Hello Flask!"
    ```

    Oprócz zmiana nazwy funkcji i wyznaczać trasy do `home`, ten kod zawiera kod renderowania strony z *app.py* , a następnie importuje `app` obiekt, który jest zadeklarowany w  *\_ \_init\_\_.py*.

4. Utwórz podfolder w *HelloFlask* o nazwie *szablony*, pozostaną puste teraz.

5. W folderze głównym projektu, Zmień nazwę *app.py* do *runserver.py*i ich zawartości, które są zgodne z poniższym kodem:

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
6. Do struktury projektu powinna wyglądać podobnie do następującego:

    ![Struktura projektu po refaktoryzacji kodu](media/flask/step02-project-structure.png)

7. Wybierz **debugowania** > **Rozpocznij debugowanie** (**F5**) lub użyj **serwera sieci Web** przycisk na pasku narzędzi (przeglądarka zostanie wyświetlony maja różnią się w) do uruchamiania aplikacji i Otwórz w przeglądarce. Wypróbuj oba / a/home tras adresów URL.

8. Możesz również ustawić punkty przerwania w różnych części kodu i ponownie aplikację, aby stosować się do uruchomienia sekwencji. Na przykład Ustawianie punktu przerwania w pierwszym wierszu *runserver.py* i *HelloFlask\_* init_*.py*, a następnie na `return "Hello Flask!"` wiersza w *views.py*. Następnie ponownie uruchom aplikację (**debugowania** > **ponowne uruchomienie**, **Ctrl**+**F5**, lub przycisk paska narzędzi, pokazano poniżej) i krok po kroku (**F10**) kodu lub uruchamiania z punktu przerwania, w których używane jest **F5**.

    ![Uruchom ponownie przycisk na pasku narzędzi debugowania w programie Visual Studio](media/debugging-restart-toolbar-button.png)

9. Gdy skończysz, Zatrzymaj aplikację.

### <a name="commit-to-source-control"></a>Zapewnij kontrole źródła

Ponieważ wprowadzono zmiany w kodzie, a następnie zostały one przetestowane pomyślnie, teraz jest to doskonały moment, aby przejrzeć i zatwierdzić zmiany do kontroli źródła. Wykonania kolejnych kroków tego samouczka przypomnienia o odpowiedniej razy, aby ponownie zatwierdzić do kontroli źródła, a następnie wrócić do tej sekcji.

1. Wybierz przycisk zmiany wzdłuż dolnej części programu Visual Studio (w kółkach poniżej), która przechodzi do **Team Explorer**.

    ![Przycisk zmiany kontroli źródła na pasku stanu programu Visual Studio](media/flask/step02-source-control-changes-button.png)

1. W **Team Explorer**, wprowadź wiadomość dotyczącą zatwierdzenia, takich jak "Zrefaktoryzuj kod" i wybierz **Zatwierdź wszystko**. Po zakończeniu zatwierdzenie, zostanie wyświetlony komunikat **zatwierdzenia \<skrótu > utworzone lokalnie. Synchronizacji, aby udostępnić zmiany na serwerze.** Aby wypchnąć zmiany do repozytorium zdalnego, należy zaznaczyć **synchronizacji**, a następnie wybierz **wypychania** w obszarze **zatwierdzeń wychodzących**. Wiele lokalnych zatwierdzeń, przed wypchnięciem do zdalnego również może wzrosnąć.

    ![Wypychanie zatwierdzeń do zdalnego w programie Team Explorer](media/flask/step02-source-control-push-to-remote.png)

### <a name="question-how-frequently-should-one-commit-to-source-control"></a>Pytanie: Jak często należy jednego zatwierdzenia do kontroli źródła?

Odpowiedź: Zatwierdzanie zmian do kontroli źródła tworzy rekord w dzienniku zmian i punkt do której można przywrócić repozytorium, jeśli to konieczne. Każde zatwierdzenie może również sprawdzić w jego określonych zmian. Ponieważ niedrogie zatwierdzenia w usłudze Git, lepiej jest do częstych zatwierdzeń, niż się gromadzenie większej liczby zmian w jednym zatwierdzeniu. Wyraźnie widać nie trzeba przekazać co niewielką zmianę do pojedynczych plików. Zazwyczaj należy zatwierdzenie podczas dodawania funkcji, zmiana struktury, takich jak zostało wykonane w tym kroku lub wykonać niektóre refaktoryzacji kodu. Również zapoznać się z innymi osobami w swoim zespole podczas stopień szczegółowości zatwierdzeń, najlepiej sprawdzające się dla wszystkich użytkowników.

Jak często zdecydujesz się i jak często wypychanie zatwierdzeń do repozytorium zdalnego są dwa różne problemy. Może wzrosnąć wiele zatwierdzeń w lokalnym repozytorium, przed wypchnięciem ich do repozytorium zdalnego. Ponownie jak często zatwierdzenia jest zależna od jak zespół chce zarządzać repozytorium.

## <a name="step-2-2-use-a-template-to-render-a-page"></a>Krok 2 z 2 Użyj szablonu do renderowania strony

`home` Funkcja, która należy do tej pory w *views.py* nie więcej niż odpowiedzi HTTP zwykłego tekstu dla strony. Jednak większość rzeczywistych stron sieci web, elastyczniejsze sformatowanego strony HTML, które często obejmują dane na żywo. W rzeczywistości głównym powodem, aby zdefiniować widoku, używając funkcji jest do generowania zawartości dynamicznej.

Ponieważ wartość zwracana dla widoku jest po prostu określonym ciągiem, możesz tworzyć się jak w ciągu przy użyciu zawartości dynamicznej kod HTML. Jednak ponieważ najlepiej oddzielić znaczników, od danych jest znacznie lepiej jest umieścić znaczniki w szablonie i przechowywać dane w kodzie.

1. Po pierwsze, Edytuj *views.py* zawiera następujący kod, który używa wbudowanego kodu HTML dla strony z niektórych zawartości dynamicznej:

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

1. Uruchom aplikację, a następnie odśwież stronę za kilka razy, aby zobaczyć, że data/godzina jest aktualizowana. Gdy skończysz, Zatrzymaj aplikację.

1. Aby przekonwertować renderowanie strony, aby użyć szablonu, Utwórz plik o nazwie *index.html* w *szablony* folderu o następującej zawartości gdzie `{{ content }}` jest symbolu zastępczego lub wymiany tokenu (również wywołuje się *zmiennej szablonu*) dla której należy podać wartość w kodzie:

    ```html
    <html>
        <head><title>Hello Flask</title></head>

        <body>
            {{ content }}
        </body>
    </html>
    ```

1. Modyfikowanie `home` funkcja do użycia `render_template` można załadować szablonu i podać wartość "zawartość", która jest wykonywane przy użyciu argumentu nazwanego pasujące do nazwy symbolu zastępczego. Flask automatycznie wyszuka szablonów w *szablony* folderu, dzięki czemu ścieżkę do szablonu jest określana względem tego folderu:

    ```python
    def home():
        now = datetime.now()
        formatted_now = now.strftime("%A, %d %B, %Y at %X")

        return render_template(
            "index.html",
            content = "<strong>Hello, Flask!</strong> on " + formatted_now)
    ```

1. Uruchamianie aplikacji, zobacz wyniki i Zauważ, że wbudowane HTML w `content` wartości nie renderuje *jako* HTML, ponieważ automatycznie aparatu tworzenia szablonów (Jinja) specjalne zawartość HTML. Automatycznego anulowania zapewnianego element zapobiega przypadkowemu luk w zabezpieczeniach na ataki przez iniekcję kodu: deweloperzy często zbierania danych wejściowych z jednej strony i użyć jej jako wartości w drugiej za pomocą symbolu zastępczego szablonu. Anulowanie służy również jako przypomnienie, że ponownie jest zalecana z kodu HTML.

    W związku z tym Przejrzyj *templates\index.html* mogą zawierać różne symbole zastępcze dla każdego elementu danych w ramach znaczników:

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

    Następnie zaktualizuj `home` funkcję, aby podać wartości dla symboli zastępczych:

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

1. Uruchom aplikację ponownie, aby wyświetlić dane wyjściowe poprawnie renderowany.

    ![Uruchamianie aplikacji przy użyciu szablonu](media/flask/step02-result.png)

1. Zatwierdź zmiany do kontroli źródła i zaktualizować repozytorium zdalnego, jeśli to konieczne, zgodnie z opisem w [krok 1 z 2](#commit-to-source-control).

### <a name="question-do-page-templates-have-to-be-in-a-separate-file"></a>Pytanie: Szablony stron mają znajdować się w oddzielnym pliku?

Odpowiedź: Mimo że szablony są zazwyczaj obsługiwane w oddzielnych plikach HTML, można też użyć szablonu wbudowanego. Przy użyciu oddzielnych plików jest zalecane, jednak do obsługi czystą separacji między znaczników i kodu.

### <a name="question-must-templates-use-the-html-file-extension"></a>Pytanie: Szablony korzystać tylko z rozszerzeniem pliku HTML?

Odpowiedź: *.Html* rozszerzenie dla plików szablonów strony jest opcjonalne, ponieważ zawsze zidentyfikować dokładną ścieżkę względną do pliku w pierwszym argumencie `render_template` funkcji. Jednak program Visual Studio (i innych edytorów) zazwyczaj zapewnia funkcje, takie jak kod zakończenia i składnia barwy z *.html* pliki, które przewyższa fakt, że stronie Szablony nie są ściśle HTML.

W rzeczywistości podczas pracy z projektem Flask programu Visual Studio automatycznie wykrywa, gdy plik HTML, który jest edytowany jest faktycznie szablonem Flask i zapewnia niektórych funkcji autouzupełniania. Na przykład, po rozpoczęciu wpisywania Flask komentarz szablon strony `{#`, Visual Studio automatycznie umożliwia zamknięcie `#}` znaków. **Dodaj komentarz do zaznaczenia** i **Usuń komentarz zaznaczenia** poleceń (na **Edytuj** > **zaawansowane** menu i na pasku narzędzi) komentarze szablonu można także użyć zamiast komentarze HTML.

### <a name="question-when-i-run-the-project-i-see-an-error-that-the-template-cannot-be-found-whats-wrong"></a>Pytanie: Uruchomienie projektu, widzę błąd, którego nie można odnaleźć szablonu. Co jest nie tak?

Odpowiedź: Jeśli widzisz błędy, których nie można znaleźć szablonu, upewnij się, aplikacja może zostać dodana do projektu Flask *settings.py* w `INSTALLED_APPS` listy. Bez tego wpisu Flask nie będzie wiedzieć, aby zobaczyć w aplikacji *szablony* folderu.

### <a name="question-can-templates-be-organized-into-further-subfolders"></a>Pytanie: Szablony można podzielić na dalsze podfoldery?

Odpowiedź: Tak, można użyć podfoldery i odwoływać się do ścieżki względnej w obszarze *szablony* w wywołaniach `render_template`. Ten sposób jest doskonałym sposobem na efektywne tworzenie przestrzeni nazw dla szablonów.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Obsługa plików statycznych, dodawanie stron i użyć szablonu dziedziczenia](learn-flask-visual-studio-step-03-serve-static-files-add-pages.md)

## <a name="go-deeper"></a>Przejdź dalej

- [Przewodnik Szybki Start Flask — renderowanie szablony](http://flask.pocoo.org/docs/1.0/quickstart/#rendering-templates) (flask.pocoo.org)
- Kod źródłowy samouczek w witrynie GitHub: [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask)

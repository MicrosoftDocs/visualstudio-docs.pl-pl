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
ms.openlocfilehash: 03a0eb6808b2298e0727492978d9beb7cfaf2216
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409772"
---
# <a name="step-2-create-a-flask-app-with-views-and-page-templates"></a>Krok 2: Tworzenie aplikacji Flask za pomocą widoków i szablonów stron

**Poprzedni krok: [Tworzenie projektu i rozwiązania programu Visual Studio](learn-flask-visual-studio-step-01-project-solution.md)**

Co znajduje się w kroku 1 w tym samouczku jest aplikacji Flask za pomocą jednej stronie, a cały kod w jednym pliku. Aby umożliwić do przyszłego rozwoju, najlepiej jest Refaktoryzacja kodu i tworzenia struktury szablony stron. W szczególności chcesz oddzielić kodu dla widoków aplikacji od innych aspektów, takich jak kod startowy.

W tym kroku teraz dowiesz się, jak:

> [!div class="checklist"]
> - Refaktoryzacja kodu aplikacji do oddzielania widoków z uruchamiania kodu (krok 2 - 1)
> - Renderowanie widoku, używając szablonu strony (krok 2 z 2)

## <a name="step-2-1-refactor-the-project-to-support-further-development"></a>Krok 1 z 2: Refaktoryzacja projektu dalszych obsługi opracowywania aplikacji

W kodzie utworzonym przez szablon "pusty kolby projekt sieci Web" istnieje pojedynczy plik *App.py* , który zawiera kod uruchomienia obok jednego widoku. Aby zezwolić na dalszy rozwój aplikacji za pomocą wielu widoków i szablonów, najlepiej jest do oddzielania tych problemów.

1. W folderze projektu Utwórz folder aplikacji o nazwie `HelloFlask` (kliknij prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj** > **Nowy folder**).

2. W folderze *HelloFlask* Utwórz plik o nazwie *\_\_init\_\_. PR* z następującą zawartością, która tworzy wystąpienie `Flask` i ładuje widoki aplikacji (utworzone w następnym kroku):

    ```python
    from flask import Flask
    app = Flask(__name__)

    import HelloFlask.views
    ```

3. W folderze *HelloFlask* Utwórz plik o nazwie *views.py* z następującą zawartością. Nazwa *views.py* jest ważna, ponieważ użyto `import HelloFlask.views` w *\_\_init\_\_. PR*; Jeśli nazwy nie są zgodne, zobaczysz błąd w czasie wykonywania.

    ```python
    from flask import Flask
    from HelloFlask import app

    @app.route('/')
    @app.route('/home')
    def home():
        return "Hello Flask!"
    ```

    Oprócz zmiany nazwy funkcji i trasy do `home`, ten kod zawiera kod renderowania stron z *App.py* i importuje obiekt `app`, który jest zadeklarowany w *\_\_init\_\_.* str.

4. Utwórz podfolder w programie *HelloFlask* o nazwie *templates*, który pozostanie pusty dla tej pory.

5. W folderze głównym projektu Zmień nazwę *App.py* na *runserver.py*i Oznacz zawartość jako zgodną z poniższym kodem:

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

7. Wybierz pozycję **debuguj** > **Rozpocznij debugowanie** (**F5**) lub przycisk **serwera sieci Web** na pasku narzędzi (widoczna przeglądarka może się różnić), aby uruchomić aplikację i otworzyć przeglądarkę. Wypróbuj oba / a/home tras adresów URL.

8. Możesz również ustawić punkty przerwania w różnych części kodu i ponownie aplikację, aby stosować się do uruchomienia sekwencji. Na przykład ustaw punkt przerwania w pierwszych wierszach *runserver.py* i *HelloFlask\_* init_ *. PR*i w wierszu `return "Hello Flask!"` w *views.py*. Następnie uruchom ponownie aplikację (**debuguj** > **Uruchom ponownie**, **Ctrl**+**F5**lub przycisk paska narzędzi poniżej), a następnie przeprowadź krok przez (**F10**) kod lub Uruchom z każdego punktu przerwania za pomocą klawisza **F5**.

    ![Uruchom ponownie przycisk na pasku narzędzi debugowania w programie Visual Studio](media/debugging-restart-toolbar-button.png)

9. Gdy skończysz, Zatrzymaj aplikację.

### <a name="commit-to-source-control"></a>Zapewnij kontrole źródła

Ponieważ wprowadzono zmiany w kodzie, a następnie zostały one przetestowane pomyślnie, teraz jest to doskonały moment, aby przejrzeć i zatwierdzić zmiany do kontroli źródła. Wykonania kolejnych kroków tego samouczka przypomnienia o odpowiedniej razy, aby ponownie zatwierdzić do kontroli źródła, a następnie wrócić do tej sekcji.

1. Wybierz przycisk zmiany w dolnej części programu Visual Studio (kółko poniżej), które przechodzi do **Team Explorer**.

    ![Przycisk zmiany kontroli źródła na pasku stanu programu Visual Studio](media/flask/step02-source-control-changes-button.png)

1. W **Team Explorer**wprowadź komunikat dotyczący zatwierdzenia, taki jak "kod refaktoryzacji", i wybierz pozycję **Zatwierdź wszystko**. Po zakończeniu zatwierdzania zostanie wyświetlony komunikat **zatwierdzenie \<> utworzone lokalnie. Synchronizuj, aby udostępnić zmiany na serwerze.** Jeśli chcesz wypchnąć zmiany do zdalnego repozytorium, wybierz pozycję **Synchronizuj**, a następnie wybierz pozycję **wypychanie** w obszarze **zatwierdzenia wychodzące**. Wiele lokalnych zatwierdzeń, przed wypchnięciem do zdalnego również może wzrosnąć.

    ![Wypychanie zatwierdzeń do zdalnego w programie Team Explorer](media/flask/step02-source-control-push-to-remote.png)

### <a name="question-how-frequently-should-one-commit-to-source-control"></a>Pytanie: Jak często należy jednego zatwierdzenia do kontroli źródła?

Odpowiedź: Zatwierdzanie zmian do kontroli źródła tworzy rekord w dzienniku zmian i punkt do której można przywrócić repozytorium, jeśli to konieczne. Każde zatwierdzenie może również sprawdzić w jego określonych zmian. Ponieważ niedrogie zatwierdzenia w usłudze Git, lepiej jest do częstych zatwierdzeń, niż się gromadzenie większej liczby zmian w jednym zatwierdzeniu. Wyraźnie widać nie trzeba przekazać co niewielką zmianę do pojedynczych plików. Zazwyczaj należy zatwierdzenie podczas dodawania funkcji, zmiana struktury, takich jak zostało wykonane w tym kroku lub wykonać niektóre refaktoryzacji kodu. Również zapoznać się z innymi osobami w swoim zespole podczas stopień szczegółowości zatwierdzeń, najlepiej sprawdzające się dla wszystkich użytkowników.

Jak często zdecydujesz się i jak często wypychanie zatwierdzeń do repozytorium zdalnego są dwa różne problemy. Może wzrosnąć wiele zatwierdzeń w lokalnym repozytorium, przed wypchnięciem ich do repozytorium zdalnego. Ponownie jak często zatwierdzenia jest zależna od jak zespół chce zarządzać repozytorium.

## <a name="step-2-2-use-a-template-to-render-a-page"></a>Krok 2 z 2: renderowanie strony za pomocą szablonu

Funkcja `home`, która jest dotąd w *views.py* , nie generuje więcej niż zwykły tekst odpowiedzi HTTP dla strony. Jednak większość rzeczywistych stron sieci web, elastyczniejsze sformatowanego strony HTML, które często obejmują dane na żywo. W rzeczywistości głównym powodem, aby zdefiniować widoku, używając funkcji jest do generowania zawartości dynamicznej.

Ponieważ wartość zwracana dla widoku jest po prostu określonym ciągiem, możesz tworzyć się jak w ciągu przy użyciu zawartości dynamicznej kod HTML. Jednak ponieważ najlepiej oddzielić znaczników, od danych jest znacznie lepiej jest umieścić znaczniki w szablonie i przechowywać dane w kodzie.

1. W przypadku elementów uruchamiających należy edytować *views.py* tak, aby zawierał następujący kod, który używa wbudowanego kodu HTML dla strony z niepewną zawartością dynamiczną:

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

1. Aby skonwertować Render strony w celu użycia szablonu, Utwórz plik o nazwie *index. html* w folderze *templates* o następującej zawartości, gdzie `{{ content }}` jest symbolem zastępczym lub tokenem zastępczym (nazywanym również *zmienną szablonu*), dla której podasz wartość w kodzie:

    ```html
    <html>
        <head><title>Hello Flask</title></head>

        <body>
            {{ content }}
        </body>
    </html>
    ```

1. Zmodyfikuj funkcję `home`, aby użyć `render_template` do załadowania szablonu i podania wartości dla "Content", która jest wykonywana przy użyciu nazwanego argumentu pasującego do nazwy symbolu zastępczego. Kolba automatycznie szuka szablonów w folderze *templates* , więc ścieżka do szablonu jest określana względem tego folderu:

    ```python
    def home():
        now = datetime.now()
        formatted_now = now.strftime("%A, %d %B, %Y at %X")

        return render_template(
            "index.html",
            content = "<strong>Hello, Flask!</strong> on " + formatted_now)
    ```

1. Uruchom aplikację i sprawdź wyniki, a następnie zaobserwuj, że wbudowany kod HTML w wartości `content` nie jest renderowany *jako* HTML, ponieważ aparat tworzenia szablonów (jinja) automatycznie WYPROWADZA zawartość HTML. Automatycznego anulowania zapewnianego element zapobiega przypadkowemu luk w zabezpieczeniach na ataki przez iniekcję kodu: deweloperzy często zbierania danych wejściowych z jednej strony i użyć jej jako wartości w drugiej za pomocą symbolu zastępczego szablonu. Anulowanie służy również jako przypomnienie, że ponownie jest zalecana z kodu HTML.

    W związku z tym Przejrzyj *templates\index.html* , aby zawierały odrębne symbole zastępcze dla każdego fragmentu danych w znaczniku:

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

    Następnie zaktualizuj funkcję `home`, aby zapewnić wartości dla wszystkich symboli zastępczych:

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

1. Zatwierdź zmiany w kontroli źródła i zaktualizuj zdalne repozytorium, jeśli to konieczne, zgodnie z opisem w [kroku 2-1](#commit-to-source-control).

### <a name="question-do-page-templates-have-to-be-in-a-separate-file"></a>Pytanie: Czy szablony stron muszą znajdować się w oddzielnym pliku?

Odpowiedź: Mimo że szablony są zazwyczaj obsługiwane w oddzielnych plikach HTML, umożliwia także szablonem wbudowanego. Przy użyciu oddzielnych plików jest zalecane, jednak do obsługi czystą separacji między znaczników i kodu.

### <a name="question-must-templates-use-the-html-file-extension"></a>Pytanie: Szablony korzystać tylko z rozszerzeniem pliku HTML?

Odpowiedź: rozszerzenie *HTML* dla plików szablonów stron jest całkowicie opcjonalne, ponieważ zawsze identyfikujesz dokładną ścieżkę względną do pliku w pierwszym argumencie funkcji `render_template`. Jednak program Visual Studio (i inne redaktorzy) zwykle udostępnia funkcje, takie jak uzupełnianie kodu i zabarwienie składni z plikami *. html* , co pozwala na przeważenie faktu, że szablony stron nie są wyłącznie w formacie HTML.

W rzeczywistości podczas pracy z projektem Flask programu Visual Studio automatycznie wykrywa, gdy plik HTML, który jest edytowany jest faktycznie szablonem Flask i zapewnia niektórych funkcji autouzupełniania. Na przykład po rozpoczęciu wpisywania komentarza do szablonu strony, `{#`, program Visual Studio automatycznie poda zamykane znaki `#}`. Polecenia **zaznaczania komentarza** i usuwania **komentarzy** (w menu **Edytuj** > **Zaawansowane** i na pasku narzędzi) również używają komentarzy szablonu zamiast komentarzy HTML.

### <a name="question-can-templates-be-organized-into-further-subfolders"></a>Pytanie: Szablony można podzielić na dalsze podfoldery?

Odpowiedź: tak, możesz użyć podfolderów, a następnie odwołać się do ścieżki względnej w obszarze *Szablony* w wywołaniach do `render_template`. Ten sposób jest doskonałym sposobem na efektywne tworzenie przestrzeni nazw dla szablonów.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Korzystanie z plików statycznych, dodawanie stron i dziedziczenie szablonów](learn-flask-visual-studio-step-03-serve-static-files-add-pages.md)

## <a name="go-deeper"></a>Przejdź dalej

- Samouczek [Szybki Start — szablony renderowania](https://flask.palletsprojects.com/en/1.0.x/quickstart/#rendering-templates) (Flask.pocoo.org)
- Kod źródłowy samouczka w witrynie GitHub: [Microsoft/Python-Sample-vs-Learning-Kolba](https://github.com/Microsoft/python-sample-vs-learning-flask)

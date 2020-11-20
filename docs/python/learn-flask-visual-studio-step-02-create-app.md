---
title: Samouczek z samouczkiem zawierającym więcej informacji w programie Visual Studio krok 2, widoki i szablony
titleSuffix: ''
description: Wskazówki dotyczące kolb w kontekście projektów programu Visual Studio, w tym kroki tworzenia aplikacji i korzystania z widoków i szablonów.
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: a06c6dbacf21cb2ce00539af901c24c77aaf9ef5
ms.sourcegitcommit: 5027eb5c95e1d2da6d08d208fd6883819ef52d05
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2020
ms.locfileid: "94974086"
---
# <a name="step-2-create-a-flask-app-with-views-and-page-templates"></a>Krok 2. Tworzenie aplikacji do kolby z widokami i szablonami stron

**Poprzedni krok: [Tworzenie projektu i rozwiązania programu Visual Studio](learn-flask-visual-studio-step-01-project-solution.md)**

Zawartość z kroku 1 tego samouczka to aplikacja do kolby z jedną stroną i cały kod w jednym pliku. Aby pozwolić na przyszłe programowanie, najlepiej wykonać refaktoryzację kodu i utworzyć strukturę szablonów stron. W szczególności chcesz oddzielić kod dla widoków aplikacji z innych aspektów, takich jak kod uruchomienia.

W tym kroku dowiesz się, jak:

> [!div class="checklist"]
> - Refaktoryzacja kodu aplikacji w celu oddzielenia widoków od kodu startowego (krok 2-1)
> - Renderowanie widoku przy użyciu szablonu strony (krok 2-2)

## <a name="step-2-1-refactor-the-project-to-support-further-development"></a>Krok 2-1: Refaktoryzacja projektu do obsługi dalszych wdrożeń

W kodzie utworzonym przez szablon "pusty kolby projekt sieci Web" istnieje pojedynczy plik *App.py* , który zawiera kod uruchomienia obok jednego widoku. Aby umożliwić dalsze Programowanie aplikacji z wieloma widokami i szablonami, najlepiej oddzielić te problemy.

1. W folderze projektu Utwórz folder aplikacji o nazwie `HelloFlask` (kliknij prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** a następnie wybierz pozycję **Dodaj**  >  **Nowy folder**).

2. W folderze *HelloFlask* Utwórz plik o nazwie *\_ \_ init \_ \_ . PR* z następującą zawartością, która tworzy `Flask` wystąpienie i ładuje widoki aplikacji (utworzone w następnym kroku):

    ```python
    from flask import Flask
    app = Flask(__name__)

    import HelloFlask.views
    ```

3. W folderze *HelloFlask* Utwórz plik o nazwie *views.py* z następującą zawartością. Nazwa *views.py* jest ważna, ponieważ została użyta `import HelloFlask.views` w *\_ \_ init \_ \_ . PR*; Jeśli nazwy nie są zgodne, zobaczysz błąd w czasie wykonywania.

    ```python
    from flask import Flask
    from HelloFlask import app

    @app.route('/')
    @app.route('/home')
    def home():
        return "Hello Flask!"
    ```

    Oprócz zmiany nazwy funkcji i trasy do programu `home` ten kod zawiera kod renderowania stron z *App.py* i importuje `app` obiekt zadeklarowany w *\_ \_ init \_ \_ . PR*.

4. Utwórz podfolder w programie *HelloFlask* o nazwie *templates*, który pozostanie pusty dla tej pory.

5. W folderze głównym projektu Zmień nazwę *App.py* na *runserver.py* i Oznacz zawartość jako zgodną z poniższym kodem:

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

6. Struktura projektu powinna wyglądać jak na poniższej ilustracji:

    ![Struktura projektu po refaktoryzacji kodu](media/flask/step02-project-structure.png)

7. Wybierz kolejno opcje **Debuguj**  >  **Rozpocznij debugowanie** (**F5**) lub przycisk **serwer sieci Web** na pasku narzędzi (widoczna przeglądarka może się różnić), aby uruchomić aplikację i otworzyć przeglądarkę. Wypróbuj trasy URL/i/Home.

8. Możesz również ustawić punkty przerwania w różnych częściach kodu i ponownie uruchomić aplikację, aby postępować zgodnie z sekwencją uruchamiania. Na przykład ustaw punkt przerwania w pierwszych wierszach *runserver.py* i *HelloFlask \_* init_ *. PR* i w `return "Hello Flask!"` wierszu w *views.py*. Następnie uruchom ponownie aplikację (**Debug**  >  **ponownie uruchom** polecenie Debug, **naciśnij klawisz Ctrl** + **SHIFT** + **F5** lub przycisk paska narzędzi poniżej), a następnie przejdź do kroku (**F10**) kod lub Uruchom z każdego punktu przerwania przy użyciu klawisza **F5**.

    ![Przycisk Uruchom ponownie na pasku narzędzi debugowania w programie Visual Studio](media/debugging-restart-toolbar-button.png)

9. Zatrzymaj aplikację po zakończeniu.

### <a name="commit-to-source-control"></a>Zatwierdzenie do kontroli źródła

Ponieważ wprowadzono zmiany w kodzie i przetestowano je pomyślnie, to teraz świetny czas na przejrzenie i zatwierdzenie zmian w kontroli źródła. W kolejnych krokach w tym samouczku dowiesz się, jak chcesz ponownie przekazać kontrolę źródła, i zapoznaj się z powrotem z tą sekcją.

1. Wybierz przycisk zmiany w dolnej części programu Visual Studio (kółko poniżej), które przechodzi do **Team Explorer**.

    ![Przycisk zmiany kontroli źródła na pasku stanu programu Visual Studio](media/flask/step02-source-control-changes-button.png)

1. W **Team Explorer** wprowadź komunikat dotyczący zatwierdzenia, taki jak "kod refaktoryzacji", i wybierz pozycję **Zatwierdź wszystko**. Po zakończeniu zatwierdzania zostanie wyświetlone **zatwierdzenie wiadomości \<hash> utworzone lokalnie. Synchronizuj, aby udostępnić zmiany na serwerze.** Jeśli chcesz wypchnąć zmiany do zdalnego repozytorium, wybierz pozycję **Synchronizuj**, a następnie wybierz pozycję **wypychanie** w obszarze **zatwierdzenia wychodzące**. Możesz również zbierać wiele lokalnych zatwierdzeń przed wypchnięciem do zdalnego.

    ![Zatwierdzeń wypychania do zdalnego w Team Explorer](media/flask/step02-source-control-push-to-remote.png)

### <a name="question-how-frequently-should-one-commit-to-source-control"></a>Pytanie: jak często powinno być jedno zatwierdzenie w kontroli źródła?

Odpowiedź: zatwierdzanie zmian w kontroli źródła powoduje utworzenie rekordu w dzienniku zmian i punktu, w którym można przywrócić repozytorium, w razie potrzeby. Każde zatwierdzenie może być również zbadane pod kątem jego konkretnych zmian. Ponieważ zatwierdzeń w usłudze git są niedrogie, lepiej jest wykonywać częste zatwierdzenia niż w celu zebrania większej liczby zmian w jednym zatwierdzeniu. Jasno nie trzeba zatwierdzać każdej drobnej zmiany do poszczególnych plików. Zazwyczaj zatwierdza się podczas dodawania funkcji, zmieniania struktury, takiej jak w tym kroku, lub wykonania niektórych operacji refaktoryzacji kodu. Skontaktuj się również z innymi osobami w zespole, aby uzyskać szczegółowy stopień zatwierdzeń, które najlepiej sprawdzają się dla wszystkich użytkowników.

Częstotliwość zatwierdzania i częstotliwości wypychania zatwierdzeń do repozytorium zdalnego są dwa różne zagadnienia. Przed przekazaniem ich do zdalnego repozytorium można zbierać wiele zatwierdzeń w lokalnym repozytorium. W zależności od tego, jak często zatwierdzasz, zależy od tego, jak zespół chce zarządzać repozytorium.

## <a name="step-2-2-use-a-template-to-render-a-page"></a>Krok 2-2: użycie szablonu do renderowania strony

`home`Funkcja, która jest dotąd w *views.py* , nie generuje więcej niż zwykły tekst odpowiedzi HTTP dla strony. Jednak większość rzeczywistych stron sieci Web reaguje na Zaawansowane strony HTML, które często zawierają dane na żywo. W rzeczywistości podstawowym powodem definiowania widoku przy użyciu funkcji jest dynamiczne generowanie zawartości.

Ponieważ wartość zwracana dla widoku jest tylko ciągiem, można utworzyć dowolny kod HTML, który lubisz w ciągu, przy użyciu zawartości dynamicznej. Jednak ze względu na to, że najlepiej oddzielić znaczniki od danych, lepiej jest umieścić znaczniki w szablonie i zachować dane w kodzie.

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

1. Uruchom aplikację i Odśwież stronę kilka razy, aby zobaczyć, że data/godzina jest aktualizowana. Zatrzymaj aplikację po zakończeniu.

1. Aby skonwertować Render strony w celu użycia szablonu, Utwórz plik o nazwie *index.html* w folderze *templates* o następującej zawartości, gdzie `{{ content }}` jest symbolem zastępczym lub tokenem zastępczym (nazywanym również *zmienną szablonu*), dla której podasz wartość w kodzie:

    ```html
    <html>
        <head><title>Hello Flask</title></head>

        <body>
            {{ content }}
        </body>
    </html>
    ```

1. Zmodyfikuj `home` funkcję, która ma być używana `render_template` do ładowania szablonu i podaj wartość dla "Content", która jest wykonywana przy użyciu nazwanego argumentu pasującego do nazwy symbolu zastępczego. Kolba automatycznie szuka szablonów w folderze *templates* , więc ścieżka do szablonu jest określana względem tego folderu:

    ```python
    def home():
        now = datetime.now()
        formatted_now = now.strftime("%A, %d %B, %Y at %X")

        return render_template(
            "index.html",
            content = "<strong>Hello, Flask!</strong> on " + formatted_now)
    ```

1. Uruchom aplikację, zobacz wyniki i sprawdź, czy wbudowany kod HTML w `content` wartości nie jest renderowany *jako* HTML, ponieważ aparat tworzenia szablonów (jinja) automatycznie wyprowadza zawartość HTML. Automatyczne ucieczki uniemożliwia przypadkowe luki w zabezpieczeniach przed iniekcją: deweloperzy często zbierają dane wejściowe z jednej strony i używają jej jako wartości w innym za pośrednictwem symbolu zastępczego szablonu. Ucieczki również służy jako przypomnienie, że jest ponownie najlepiej zachować kod HTML z kodu.

    Należy odpowiednio przejrzeć *templates\index.html* , aby zawierały odrębne symbole zastępcze dla każdego fragmentu danych w znaczniku:

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

    Następnie zaktualizuj `home` funkcję, aby zapewnić wartości dla wszystkich symboli zastępczych:

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

1. Ponownie uruchom aplikację, aby zobaczyć prawidłowo renderowane dane wyjściowe.

    ![Uruchamianie aplikacji przy użyciu szablonu](media/flask/step02-result.png)

1. Zatwierdź zmiany w kontroli źródła i zaktualizuj zdalne repozytorium, jeśli to konieczne, zgodnie z opisem w [kroku 2-1](#commit-to-source-control).

### <a name="question-do-page-templates-have-to-be-in-a-separate-file"></a>Pytanie: czy szablony stron muszą znajdować się w osobnym pliku?

Odpowiedź: Chociaż szablony są zwykle utrzymywane w oddzielnych plikach HTML, można również użyć szablonu wbudowanego. Zaleca się jednak używanie oddzielnego pliku w celu utrzymania czystego rozdzielenia między adiustacją i kodem.

### <a name="question-must-templates-use-the-html-file-extension"></a>Pytanie: czy szablony muszą używać rozszerzenia pliku HTML?

Odpowiedź: rozszerzenie *HTML* dla plików szablonów stron jest całkowicie opcjonalne, ponieważ zawsze identyfikujesz dokładną ścieżkę względną do pliku w pierwszym argumencie `render_template` funkcji. Jednak program Visual Studio (i inne redaktorzy) zwykle udostępnia funkcje, takie jak uzupełnianie kodu i zabarwienie składni z plikami *. html* , co pozwala na przeważenie faktu, że szablony stron nie są wyłącznie w formacie HTML.

W rzeczywistości podczas pracy z projektem kolby program Visual Studio automatycznie wykrywa, kiedy edytowany plik HTML jest w rzeczywistości szablonem kolby i udostępnia niektóre funkcje autouzupełniania. Na przykład po rozpoczęciu wpisywania komentarza do szablonu strony, program `{#` Visual Studio automatycznie podaje znaki zamykające `#}` . Polecenia **zaznaczania komentarza** i usuwania **komentarzy** (w menu **Edytuj**  >  **Zaawansowane** i na pasku narzędzi) również używają komentarzy szablonu zamiast komentarzy HTML.

### <a name="question-can-templates-be-organized-into-further-subfolders"></a>Pytanie: czy szablony mogą być zorganizowane w dalsze podfoldery?

Odpowiedź: tak, możesz użyć podfolderów, a następnie odwołać się do ścieżki względnej w obszarze *Szablony* w programie wywołania do `render_template` . To świetny sposób na efektywne tworzenie obszarów nazw dla szablonów.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Korzystanie z plików statycznych, dodawanie stron i dziedziczenie szablonów](learn-flask-visual-studio-step-03-serve-static-files-add-pages.md)

## <a name="go-deeper"></a>Przejdź głębiej

- Samouczek [Szybki Start — szablony renderowania](https://flask.palletsprojects.com/en/1.0.x/quickstart/#rendering-templates) (Flask.pocoo.org)
- Kod źródłowy samouczka w witrynie GitHub: [Microsoft/Python-Sample-vs-Learning-Kolba](https://github.com/Microsoft/python-sample-vs-learning-flask)

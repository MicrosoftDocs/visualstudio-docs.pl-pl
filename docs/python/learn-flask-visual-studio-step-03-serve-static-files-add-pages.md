---
title: Dowiedz się samouczek Flask w programie Visual Studio krok 3, pliki statyczne i strony
titleSuffix: ''
description: Przewodnik po podstawach flask w kontekście projektów programu Visual Studio, w szczególności pokazując, jak obsługiwać pliki statyczne, dodawać strony do aplikacji i używać dziedziczenia szablonów
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 5aa952a00075cdad262803140ab4c0360f0c62a0
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "72985185"
---
# <a name="step-3-serve-static-files-add-pages-and-use-template-inheritance"></a>Krok 3: Obsługa plików statycznych, dodawanie stron i używanie dziedziczenia szablonów

**Poprzedni krok: [Tworzenie aplikacji Flask z widokami i szablonami stron](learn-flask-visual-studio-step-02-create-app.md)**

W poprzednich krokach tego samouczka dowiesz się, jak utworzyć minimalną aplikację Flask z pojedynczą stroną samodzielnego kodu HTML. Nowoczesne aplikacje internetowe składają się jednak zazwyczaj z wielu stron i korzystają z zasobów udostępnionych, takich jak pliki CSS i JavaScript, aby zapewnić spójne stylizacje i zachowanie.

W tym kroku dowiesz się, jak:

> [!div class="checklist"]
> - Za pomocą szablonów elementów programu Visual Studio można szybko dodawać nowe pliki różnych typów za pomocą wygodnego kodu standardowego (krok 3-1)
> - Obsługa plików statycznych z kodu (krok 3-2, opcjonalnie)
> - Dodawanie dodatkowych stron do aplikacji (krok 3-3)
> - Tworzenie nagłówka i paska nawigacyjnych używanego na różnych stronach za pomocą dziedziczenia szablonów

## <a name="step-3-1-become-familiar-with-item-templates"></a>Krok 3-1: Zapoznaj się z szablonami przedmiotów

Podczas tworzenia aplikacji Flask zazwyczaj dodajesz o wiele więcej plików Python, HTML, CSS i JavaScript. Dla każdego typu pliku (a także innych plików, takich jak *web.config,* które mogą być potrzebne do wdrożenia), visual studio zapewnia wygodne [szablony elementów,](python-item-templates.md) aby rozpocząć.

Aby wyświetlić dostępne szablony, przejdź do **Programu Solution Explorer**, kliknij prawym przyciskiem myszy folder, w którym chcesz utworzyć element, wybierz pozycję **Dodaj** > **nowy element:**

![Dodawanie nowego okna dialogowego elementu w programie Visual Studio](media/flask/step03-add-new-item-dialog.png)

Aby użyć szablonu, wybierz żądany szablon, określ nazwę pliku i wybierz **przycisk OK**. Dodawanie elementu w ten sposób automatycznie dodaje plik do projektu programu Visual Studio i oznacza zmiany dla kontroli źródła.

### <a name="question-how-does-visual-studio-know-which-item-templates-to-offer"></a>Pytanie: Skąd program Visual Studio wie, które szablony elementów do zaoferowania?

Odpowiedź: Plik projektu programu Visual Studio (*.pyproj*) zawiera identyfikator typu projektu, który oznacza go jako projekt języka Python. Visual Studio używa tego identyfikatora typu, aby wyświetlić tylko te szablony elementów, które są odpowiednie dla typu projektu. W ten sposób visual studio może dostarczyć bogaty zestaw szablonów elementów dla wielu typów projektów bez pytania, aby sortować je za każdym razem.

## <a name="step-3-2-serve-static-files-from-your-app"></a>Krok 3-2: Obsługa plików statycznych z aplikacji

W aplikacji internetowej utworzonej za pomocą języka Python (przy użyciu dowolnej struktury) pliki Języka Python są zawsze uruchamiane na serwerze hosta internetowego i nigdy nie są przesyłane do komputera użytkownika. Inne pliki, takie jak CSS i JavaScript, są używane wyłącznie przez przeglądarkę, więc serwer hosta po prostu dostarcza je w stanie takim, w jakim są wymagane. Takie pliki są określane jako "statyczne" pliki, a Flask może dostarczyć je automatycznie bez konieczności pisania kodu. W plikach HTML, na przykład, można po prostu odwołać się do plików statycznych przy użyciu ścieżki względnej w projekcie. Pierwsza sekcja w tym kroku dodaje plik CSS do istniejącego szablonu strony.

Gdy trzeba dostarczyć plik statyczny z kodu, takich jak za pośrednictwem implementacji punktu końcowego interfejsu API, Flask zapewnia wygodną metodę, która pozwala odwoływać się do plików przy użyciu ścieżek względnych w folderze o nazwie *statyczne* (w katalogu głównym projektu). Druga sekcja w tym kroku pokazuje tę metodę przy użyciu prostego statycznego pliku danych.

W obu przypadkach można organizować pliki w *stanie statycznym,* jak chcesz.

### <a name="use-a-static-file-in-a-template"></a>Używanie pliku statycznego w szablonie

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy folder **HelloFlask** w `static`projekcie programu Visual Studio, wybierz pozycję **Dodaj** > nowy**folder**i nazwij folder .

1. Kliknij prawym przyciskiem myszy folder **statyczny** i wybierz polecenie **Dodaj** > **nowy element**. W wyświetlonym oknie dialogowym zaznacz szablon **arkusza stylów,** nazwij plik `site.css`i wybierz przycisk **OK**. Plik **site.css** pojawi się w projekcie i zostanie otwarty w edytorze. Struktura folderów powinna wyglądać podobnie do następującej ilustracji:

    ![Statyczna struktura plików, jak pokazano w Eksploratorze rozwiązań](media/flask/step03-static-file-structure.png)

1. Zastąp zawartość *witryny site.css* następującym kodem i zapisz plik:

    ```css
    .message {
        font-weight: 600;
        color: blue;
    }
    ```

1. Zastąp zawartość pliku *templates/index.html* aplikacji następującym kodem, który `<strong>` zastępuje element używany w `<span>` kroku 2, który odwołuje się do klasy `message` stylu. Korzystanie z klasy stylu w ten sposób zapewnia znacznie większą elastyczność w stylizacji elementu.

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
            <link rel="stylesheet" type="text/css" href="/static/site.css" />
        </head>
        <body>
            <span class="message">{{ message }}</span>{{ content }}
        </body>
    </html>
    ```

1. Uruchom projekt, aby obserwować wyniki. Zatrzymaj aplikację po zakończeniu i zaobewaj zmiany do kontroli źródła, jeśli chcesz (jak wyjaśniono w [kroku 2](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control)).

### <a name="serve-a-static-file-from-code"></a>Obsługa pliku statycznego z kodu

Flask zapewnia funkcję `serve_static_file` wywoływaną z kodu, aby odwołać się do dowolnego pliku w folderze *statycznym* projektu. Poniższy proces tworzy prosty punkt końcowy interfejsu API, który zwraca statyczny plik danych.

1. Jeśli jeszcze tego nie zrobiono, utwórz folder *statyczny:* w **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy folder **HelloFlask** w projekcie programu Visual Studio, wybierz pozycję **Dodaj** > **nowy folder**i nazwij folder `static`.

1. W folderze *statycznym* utwórz statyczny plik danych JSON o nazwie *data.json* z następującą zawartością (które są bezsensownymi danymi próbki):

    ```json
    {
        "01": {
            "note" : "Data is very simple because we're demonstrating only the mechanism."
        }
    }
    ```

1. W *views.py*, dodaj funkcję z marszrutą /api/data, która zwraca `send_static_file` statyczny plik danych przy użyciu metody:

    ```python
    @app.route('/api/data')
    def get_data():
      return app.send_static_file('data.json')
    ```

1. Uruchom aplikację i przejdź do punktu końcowego /api/data, aby zobaczyć, że zwracany jest plik statyczny. Zatrzymaj aplikację po zakończeniu.

### <a name="question-are-there-any-conventions-for-organizing-static-files"></a>Pytanie: Czy istnieją jakieś konwencje organizowania plików statycznych?

Odpowiedź: W folderze *statycznym* możesz dodawać inne pliki CSS, JavaScript i HTML. Typowym sposobem organizowania plików statycznych jest tworzenie podfolderów o nazwie *czcionki,* *skrypty*i *zawartość* (dla arkuszy stylów i innych plików).

### <a name="question-how-do-i-handle-url-variables-and-query-parameters-in-an-api"></a>Pytanie: Jak obsługiwać zmienne adresu URL i parametry kwerend w interfejsie API?

Odpowiedź: Zobacz odpowiedź w kroku 1-4 na [pytanie: Jak flask działa ze zmiennymi trasami adresów URL i parametrami zapytania?](learn-flask-visual-studio-step-01-project-solution.md#qa-url-variables)

## <a name="step-3-3-add-a-page-to-the-app"></a>Krok 3-3: Dodawanie strony do aplikacji

Dodanie kolejnej strony do aplikacji oznacza, że:

- Dodaj funkcję Języka Python, która definiuje widok.
- Dodaj szablon znaczników strony.
- Dodaj niezbędną routing do pliku *urls.py* projektu Flask.

Następujące kroki dodają stronę "Informacje" do projektu "HelloFlask" i łącza do tej strony ze strony głównej:

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy folder **szablonów,** wybierz `about.html`polecenie **Dodaj** > nowy**element,** zaznacz szablon elementu strony **HTML,** nazwij plik i wybierz przycisk **OK**.

    > [!Tip]
    > Jeśli polecenie **Nowy element** nie jest wyświetlane w menu **Dodaj,** upewnij się, że aplikacja została zatrzymana, aby program Visual Studio zakończył działanie trybu debugowania.

1. Zastąp zawartość *about.html* następującym znacznikiem (łącze jawne do strony głównej zastępujesz prostym paskiem nawigacyjnym w kroku 3-4):

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
            <link rel="stylesheet" type="text/css" href="/static/site.css" />
        </head>
        <body>
            <div><a href="home">Home</a></div>
            {{ content }}
        </body>
    </html>
    ```

1. Otwórz plik *views.py* aplikacji i dodaj funkcję `about` o nazwie, która używa szablonu:

    ```python
    @app.route('/about')
    def about():
        return render_template(
            "about.html",
            title = "About HelloFlask",
            content = "Example app page for Flask.")
    ```

1. Otwórz plik *templates/index.html* i natychmiast dodaj następujący wiersz `<body>` w elemencie, aby utworzyć łącze do strony Informacje (ponownie zastąp to łącze paskiem nawigacyjnym w kroku 3-4):

    ```html
    <div><a href="about">About</a></div>
    ```

1. Zapisz wszystkie pliki za pomocą polecenia menu **Zapisz** > **wszystko** lub po prostu naciśnij **klawisze Ctrl**+**Shift**+**S**. (Technicznie ten krok nie jest potrzebny, ponieważ uruchomienie projektu w programie Visual Studio automatycznie zapisuje pliki. Niemniej jednak, jest to dobra komenda, aby wiedzieć o!)

1. Uruchom projekt, aby obserwować wyniki i sprawdzić nawigację między stronami. Zatrzymaj aplikację po zakończeniu.

### <a name="question-does-the-name-of-a-page-function-matter-to-flask"></a>Pytanie: Czy nazwa funkcji strony ma znaczenie dla Flask?

Odpowiedź: Nie, ponieważ to `@app.route` dekorator określa adresy URL, dla których Flask wywołuje funkcję, aby wygenerować odpowiedź. Deweloperzy zazwyczaj pasują do nazwy funkcji do trasy, ale takie dopasowanie nie jest wymagane.

## <a name="step-3-4-use-template-inheritance-to-create-a-header-and-nav-bar"></a>Krok 3-4: Tworzenie nagłówka i paska nawigacyjnych za pomocą dziedziczenia szablonu

Zamiast jawnych łączy nawigacyjnych na każdej stronie, nowoczesne aplikacje internetowe zazwyczaj używają nagłówka znakowania i paska nawigacyjnego, który zawiera najważniejsze łącza stron, menu podręczne i tak dalej. Aby upewnić się, że nagłówek i pasek nawigacyjny są takie same na wszystkich stronach, nie chcesz jednak powtarzać tego samego kodu w każdym szablonie strony. Zamiast tego chcesz zdefiniować wspólne części wszystkich stron w jednym miejscu.

System tworzenia szablonów flask (Domyślnie Jinja) zapewnia dwa środki do ponownego użytku określonych elementów w wielu szablonach: zawiera i dziedziczenia.

- *Zawiera* inne szablony stron wstawiane w określonym miejscu w szablonie odsyłający przy użyciu składni `{% include <template_path> %}`. Można również użyć zmiennej, jeśli chcesz dynamicznie zmienić ścieżkę w kodzie. Obejmuje są zazwyczaj używane w treści strony do ściągania w szablonie udostępnionym w określonej lokalizacji na stronie.

- *Dziedziczenie* używa `{% extends <template_path> %}` na początku szablonu strony, aby określić udostępniony szablon podstawowy, który następnie opiera się na szablonie odsyłający. Dziedziczenie jest powszechnie używane do definiowania układu udostępnionego, paska nawigacyjnyego i innych struktur dla stron aplikacji, w ten sposób, że szablony odwołujące się muszą tylko dodawać lub modyfikować określone obszary szablonu podstawowego o nazwie *bloki*.

W obu `<template_path>` przypadkach jest względem folderu *szablonów* aplikacji (`../` lub `./` są również dozwolone).

Szablon podstawowy wyznacza *bloki* `{% block <block_name> %}` przy `{% endblock %}` użyciu i tagi. Jeśli szablon odsyłający używa tagów o tej samej nazwie bloku, jego zawartość bloku zastępuje zawartość szablonu podstawowego.

Następujące kroki pokazują dziedziczenie:

1. W folderze *szablony* aplikacji utwórz nowy plik HTML (za pomocą menu**kontekstowego** **Dodaj** > nowy element lub **Dodaj** > **stronę HTML**) o nazwie *layout.html*i zastąp jego zawartość poniższymi znacznikami. Widać, że ten szablon zawiera blok o nazwie "zawartość", który jest wszystkim, co strony odsyłający muszą zastąpić:

    ```html
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="utf-8" />
        <title>{{ title }}</title>
        <link rel="stylesheet" type="text/css" href="/static/site.css" />
    </head>

    <body>
        <div class="navbar">
            <a href="/" class="navbar-brand">Hello Flask</a>
            <a href="{{ url_for('home') }}" class="navbar-item">Home</a>
            <a href="{{ url_for('about') }}" class="navbar-item">About</a>
        </div>

        <div class="body-content">
            {% block content %}
            {% endblock %}
            <hr/>
            <footer>
                <p>&copy; 2018</p>
            </footer>
        </div>
    </body>
    </html>
    ```

1. Dodaj następujące style do pliku *statycznego/site.css* aplikacji (w tym instruktażu nie próbuje się tutaj zademonstrować responsywnego projektu; te style są po prostu generują interesujące wyniki):

    ```css
    .navbar {
        background-color: lightslategray;
        font-size: 1em;
        font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
        color: white;
        padding: 8px 5px 8px 5px;
    }

    .navbar a {
        text-decoration: none;
        color: inherit;
    }

    .navbar-brand {
        font-size: 1.2em;
        font-weight: 600;
    }

    .navbar-item {
        font-variant: small-caps;
        margin-left: 30px;
    }

    .body-content {
        padding: 5px;
        font-family:'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }
    ```

1. Zmodyfikuj *templates/index.html,* aby odwoływać się do szablonu podstawowego i zastąpić blok zawartości. Widać, że za pomocą dziedziczenia ten szablon staje się prosty:

    ```html
    {% extends "layout.html" %}
    {% block content %}
    <span class="message">{{ message }}</span>{{ content }}
    {% endblock %}
    ```

1. Zmodyfikuj *templates/about.html,* aby również odwoływać się do szablonu podstawowego i zastępować blok zawartości:

    ```html
    {% extends "layout.html" %}
    {% block content %}
    {{ content }}
    {% endblock %}
    ```

1. Uruchom serwer, aby obserwować wyniki. Zamknij serwer po zakończeniu.

    ![Uruchamianie aplikacji z pasem nawigacyjnym](media/flask/step03-nav-bar.png)

1. Ponieważ wprowadzono istotne zmiany w aplikacji, to znowu dobry moment, aby [zatwierdzić zmiany do kontroli źródła](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control).

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Użyj pełnego szablonu projektu flask Web Project](learn-flask-visual-studio-step-04-full-flask-project-template.md)

## <a name="go-deeper"></a>Głębiej

- [Wdrażanie aplikacji sieci Web w usłudze Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
- Aby uzyskać więcej możliwości szablonów Jinja, takich jak przepływ sterowania, zobacz [Dokumentacja projektanta szablonów Jinja](http://jinja.palletsprojects.com/en/2.10.x/templates/) (jinja.pocoo.org)
- Szczegółowe informacje `url_for`na temat używania , patrz [url_for](https://flask.palletsprojects.com/en/1.0.x/api/#flask.url_for) w dokumentacji obiektu aplikacji kolby (flask.pocoo.org)
- Kod źródłowy samouczka w usłudze GitHub: [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask)

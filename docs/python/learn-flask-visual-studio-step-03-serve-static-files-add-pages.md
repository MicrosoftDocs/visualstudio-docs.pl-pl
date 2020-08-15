---
title: Samouczek dotyczący kolby w programie Visual Studio krok 3, pliki statyczne i strony
titleSuffix: ''
description: Przewodnik dotyczący części kolb w kontekście projektów programu Visual Studio, w tym szczegółowe informacje o sposobie obsługi plików statycznych, dodawaniu stron do aplikacji i używania dziedziczenia szablonów
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 69fd704976ee941cb053d75040a3d3ec7871a380
ms.sourcegitcommit: d8609a78b460d4783f5d59c0c89454910a4dbd21
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2020
ms.locfileid: "88238745"
---
# <a name="step-3-serve-static-files-add-pages-and-use-template-inheritance-with-flask-app"></a>Krok 3. Korzystanie z plików statycznych, dodawanie stron i dziedziczenie szablonów przy użyciu aplikacji do kolby

**Poprzedni krok: [Tworzenie aplikacji do kolby z widokami i szablonami stron](learn-flask-visual-studio-step-02-create-app.md)**

W poprzednich krokach tego samouczka wiesz już, jak utworzyć aplikację minimalnej kolby za pomocą pojedynczej strony z niezależnym kodem HTML. Nowoczesne aplikacje sieci Web, jednak zwykle składają się z wielu stron i używają zasobów udostępnionych, takich jak pliki CSS i JavaScript, do zapewnienia spójnego stylu i zachowania.

W tym kroku dowiesz się, jak:

> [!div class="checklist"]
> - Użyj szablonów elementów programu Visual Studio, aby szybko dodawać nowe pliki różnych typów przy użyciu wygodnego kodu standardowego (krok 3-1)
> - Obsługuj pliki statyczne z kodu (krok 3-2, opcjonalnie)
> - Dodawanie dodatkowych stron do aplikacji (krok 3-3)
> - Użyj dziedziczenia szablonów, aby utworzyć nagłówek i pasek nawigacyjny, który jest używany na stronach (krok 3-4)

## <a name="step-3-1-become-familiar-with-item-templates"></a>Krok 3-1: Zapoznaj się z szablonami elementów

Podczas tworzenia aplikacji do kolby zazwyczaj dodawane są pliki języka Python, HTML, CSS i JavaScript. Dla każdego typu pliku (a także innych plików, takich jak *web.config* , które mogą być potrzebne do wdrożenia), program Visual Studio udostępnia wygodne [Szablony elementów](python-item-templates.md) umożliwiające rozpoczęcie pracy.

Aby wyświetlić dostępne szablony, przejdź do **Eksplorator rozwiązań**, kliknij prawym przyciskiem myszy folder, w którym chcesz utworzyć element, wybierz pozycję **Dodaj**  >  **nowy element**:

![Okno dialogowe Dodawanie nowego elementu w programie Visual Studio](media/flask/step03-add-new-item-dialog.png)

Aby użyć szablonu, wybierz odpowiedni szablon, określ nazwę pliku, a następnie wybierz **przycisk OK**. Dodanie elementu w ten sposób powoduje automatyczne dodanie pliku do projektu programu Visual Studio i oznaczenie zmian w kontroli źródła.

### <a name="question-how-does-visual-studio-know-which-item-templates-to-offer"></a>Pytanie: w jaki sposób program Visual Studio wie, które szablony elementów mają być oferowane?

Odpowiedź: plik projektu programu Visual Studio (*. pyproj*) zawiera identyfikator typu projektu, który oznacza go jako projekt języka Python. Program Visual Studio używa tego identyfikatora typu do wyświetlania tylko szablonów elementów, które są odpowiednie dla typu projektu. Dzięki temu program Visual Studio może dostarczyć bogaty zestaw szablonów elementów dla wielu typów projektów bez monitowania o sortowanie za każdym razem.

## <a name="step-3-2-serve-static-files-from-your-app"></a>Krok 3-2: obchodzenie plików statycznych z aplikacji

W aplikacji sieci Web skompilowanej za pomocą języka Python (przy użyciu dowolnej platformy) pliki języka Python są zawsze uruchamiane na serwerze hosta sieci Web i nigdy nie są przesyłane do komputera użytkownika. Inne pliki, takie jak CSS i JavaScript, są używane wyłącznie przez przeglądarkę, więc serwer hosta po prostu dostarcza je w miarę ich żądania. Takie pliki są określane jako pliki "static", a kolby mogą być dostarczane automatycznie bez konieczności pisania kodu. Na przykład w plikach HTML można odwoływać się tylko do plików statycznych przy użyciu ścieżki względnej w projekcie. Pierwsza sekcja w tym kroku dodaje plik CSS do istniejącego szablonu strony.

Gdy konieczne jest dostarczenie pliku statycznego z kodu, na przykład przez implementację punktu końcowego interfejsu API, kolba zapewnia wygodną metodę, która umożliwia odwoływanie się do plików przy użyciu ścieżek względnych w folderze o nazwie *static* (w katalogu głównym projektu). Druga sekcja w tym kroku pokazuje, że metoda korzysta z prostego pliku danych statycznych.

W obu przypadkach można organizować pliki w sposób *statyczny* .

### <a name="use-a-static-file-in-a-template"></a>Używanie pliku statycznego w szablonie

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy folder **HelloFlask** w projekcie programu Visual Studio, wybierz polecenie **Dodaj**  >  **Nowy folder**i Nazwij folder `static` .

1. Kliknij prawym przyciskiem myszy folder **statyczny** i wybierz polecenie **Dodaj**  >  **nowy element**. W wyświetlonym oknie dialogowym wybierz szablon **arkusza stylów** , Nazwij plik `site.css` , a następnie wybierz **przycisk OK**. Plik **site. css** zostanie wyświetlony w projekcie i otwarty w edytorze. Struktura folderów powinna wyglądać podobnie do poniższej ilustracji:

    ![Struktura pliku statycznego, jak pokazano w Eksplorator rozwiązań](media/flask/step03-static-file-structure.png)

1. Zastąp zawartość pliku *site. css* następującym kodem i Zapisz plik:

    ```css
    .message {
        font-weight: 600;
        color: blue;
    }
    ```

1. Zastąp zawartość pliku *templates/index.html* aplikacji następującym kodem, który zastępuje `<strong>` element użyty w kroku 2, `<span>` który odwołuje się do `message` klasy style. Użycie klasy stylu w ten sposób zapewnia znacznie większą elastyczność w stylu elementu.

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

1. Uruchom projekt, aby obserwować wyniki. Zatrzymaj aplikację po zakończeniu i zatwierdź zmiany w kontroli źródła, jeśli chcesz (zgodnie z opisem w [kroku 2](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control)).

### <a name="serve-a-static-file-from-code"></a>Obsługiwanie pliku statycznego z kodu

Kolba zawiera funkcję o nazwie `serve_static_file` , którą można wywołać z kodu, aby odwołać się do dowolnego pliku w folderze *statycznym* projektu. Poniższy proces tworzy prosty punkt końcowy interfejsu API, który zwraca plik danych statycznych.

1. Jeśli jeszcze tego nie zrobiono, Utwórz folder *statyczny* : w **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy folder **HelloFlask** w projekcie programu Visual Studio, wybierz pozycję **Dodaj**  >  **Nowy folder**i nadaj nazwę folderowi `static` .

1. W folderze *statycznym* Utwórz statyczny plik danych JSON o nazwie *data.jsprzy* użyciu następującej zawartości (które mają znaczenie przykładowe dane):

    ```json
    {
        "01": {
            "note" : "Data is very simple because we're demonstrating only the mechanism."
        }
    }
    ```

1. W *views.py*Dodaj funkcję z/API/Data trasy, która zwraca plik danych statycznych przy użyciu `send_static_file` metody:

    ```python
    @app.route('/api/data')
    def get_data():
      return app.send_static_file('data.json')
    ```

1. Uruchom aplikację i przejdź do punktu końcowego/API/Data, aby zobaczyć, że plik statyczny jest zwracany. Zatrzymaj aplikację po zakończeniu.

### <a name="question-are-there-any-conventions-for-organizing-static-files"></a>Pytanie: czy istnieją konwencje do organizowania plików statycznych?

Odpowiedź: możesz jednak dodać inne pliki CSS, JavaScript i HTML do folderu *statycznego* . Typowym sposobem organizowania plików statycznych jest tworzenie podfolderów o nazwach *Fonts*, *scripts*i *Content* (dla arkuszy stylów i innych plików).

### <a name="question-how-do-i-handle-url-variables-and-query-parameters-in-an-api"></a>Pytanie: Jak mogę obsługiwać zmienne adresów URL i parametrów zapytania w interfejsie API?

Odpowiedź: Zobacz odpowiedź w kroku 1-4 dla [pytania: jak działa Kolba z zmiennymi adresami URL i parametrami zapytania?](learn-flask-visual-studio-step-01-project-solution.md#qa-url-variables)

## <a name="step-3-3-add-a-page-to-the-app"></a>Krok 3-3: Dodawanie strony do aplikacji

Dodanie innej strony do aplikacji oznacza następujące kwestie:

- Dodaj funkcję języka Python, która definiuje widok.
- Dodaj szablon dla znacznika strony.
- Dodaj wymagane Routing do pliku *URLs.py* projektu kolby.

Poniższe kroki umożliwiają dodanie strony "informacje" do projektu "HelloFlask" i linków do tej strony ze strony głównej:

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy folder **Szablony** , wybierz polecenie **Dodaj**  >  **nowy element**, wybierz szablon elementu **strony HTML** , Nazwij plik `about.html` , a następnie wybierz **przycisk OK**.

    > [!Tip]
    > Jeśli polecenie **nowy element** nie pojawia się w menu **Dodaj** , upewnij się, że aplikacja została zatrzymana, aby program Visual Studio opuszcza tryb debugowania.

1. Zastąp zawartość *about.html* następującym znacznikiem (w kroku 3-4 zostanie zastąpione łącze bezpośrednie do strony głównej z prostym paskiem nawigacyjnym):

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

1. Otwórz plik *views.py* aplikacji i Dodaj funkcję o nazwie `about` , która używa szablonu:

    ```python
    @app.route('/about')
    def about():
        return render_template(
            "about.html",
            title = "About HelloFlask",
            content = "Example app page for Flask.")
    ```

1. Otwórz plik *templates/index.html* i Dodaj następujący wiersz bezpośrednio w elemencie, `<body>` Aby połączyć się ze stroną informacje (ponownie, zastępując ten link paskiem nawigacyjnym w kroku 3-4):

    ```html
    <div><a href="about">About</a></div>
    ```

1. **Zapisz wszystkie**pliki przy użyciu  >  polecenia**Zapisz wszystko** menu lub po prostu naciśnij klawisz **Ctrl** + **SHIFT** + **S**. (Technicznie ten krok nie jest wymagany, ponieważ uruchomienie projektu w programie Visual Studio powoduje automatyczne zapisanie plików. Jednak dobrym poleceniem jest poznanie!)

1. Uruchom projekt, aby obserwować wyniki i sprawdzić nawigację między stronami. Zatrzymaj aplikację po zakończeniu.

### <a name="question-does-the-name-of-a-page-function-matter-to-flask"></a>Pytanie: czy nazwa funkcji strony ma być poddana kolbie?

Odpowiedź: nie, ponieważ jest to `@app.route` dekoratora, który określa adresy URL, dla których Kolba wywołuje funkcję w celu wygenerowania odpowiedzi. Deweloperzy zwykle pasują do nazwy funkcji do trasy, ale takie dopasowanie nie jest wymagane.

## <a name="step-3-4-use-template-inheritance-to-create-a-header-and-nav-bar"></a>Krok 3-4: Użyj dziedziczenia szablonu, aby utworzyć nagłówek i pasek nawigacyjny

Zamiast mieć jawne linki nawigacyjne na każdej stronie, nowoczesne aplikacje sieci Web zwykle używają nagłówka znakowania i paska nawigacyjnego, który zawiera najważniejsze linki stron, menu podręczne i tak dalej. Aby upewnić się, że nagłówek i pasek nawigacyjny są takie same na wszystkich stronach, ale nie chcesz powtarzać tego samego kodu w każdym szablonie strony. Zamiast tego chcesz zdefiniować wspólne części wszystkich stron w jednym miejscu.

System tworzenia szablonów kolby (domyślnie jinja) zapewnia dwa sposoby wielokrotnego używania określonych elementów w wielu szablonach: zawiera i dziedziczenie.

- *Obejmuje* inne szablony stron, które są wstawiane w konkretnym miejscu w szablonie odwołującym przy użyciu składni `{% include <template_path> %}` . Możesz również użyć zmiennej, jeśli chcesz zmienić ścieżkę dynamicznie w kodzie. Dołączenia są zwykle używane w treści strony do ściągania szablonu udostępnionego w określonej lokalizacji na stronie.

- *Dziedziczenie* używa na `{% extends <template_path> %}` początku szablonu strony, aby określić współużytkowany szablon podstawowy, na którym zostanie utworzony szablon odwołujący się. Dziedziczenie jest często używane do definiowania współużytkowanego układu, paska nawigacyjnego i innych struktur dla stron aplikacji, takich jak szablony odwołujące się potrzebują tylko dodawania lub modyfikowania określonych obszarów szablonu podstawowego o nazwie *Blocks*.

W obu przypadkach `<template_path>` jest względna w stosunku do folderu *szablonów* aplikacji ( `../` lub `./` są również dozwolone).

Wyznacza szablonu podstawowego *blokuje* używanie `{% block <block_name> %}` tagów i `{% endblock %}` . Jeśli szablon odwołujący używa tagów o tej samej nazwie bloku, jego zawartość bloku zastępuje szablon podstawowy.

W poniższych krokach przedstawiono dziedziczenie:

1. W folderze *Szablony* aplikacji Utwórz nowy plik HTML (za pomocą **Add**  >  menu kontekstowego Dodaj**nowy element** lub **Dodaj**  >  **stronę HTML**) o nazwie *layout.html*i Zastąp jego zawartość następującym znacznikiem:. Można zobaczyć, że ten szablon zawiera blok o nazwie "Content", który ma zostać zastąpiony przez strony odwołujące:

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

1. Dodaj następujące style do pliku *CSS, statycznego/witryny* aplikacji (w tym instruktażu nie jest podejmowana próba pokazania w tym miejscu odpowiedzi na projekt; te style mają po prostu generowanie interesującego wyniku):

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

1. Zmodyfikuj szablon */index.html* , aby odwołać się do szablonu bazowego i zastąpić blok zawartości. Można zobaczyć, że za pomocą dziedziczenia, ten szablon stanie się prosty:

    ```html
    {% extends "layout.html" %}
    {% block content %}
    <span class="message">{{ message }}</span>{{ content }}
    {% endblock %}
    ```

1. Zmodyfikuj *Szablony/about.html* , aby odwoływać się również do szablonu podstawowego i zastąpić blok zawartości:

    ```html
    {% extends "layout.html" %}
    {% block content %}
    {{ content }}
    {% endblock %}
    ```

1. Uruchom serwer, aby obserwować wyniki. Po zakończeniu zamknij serwer.

    ![Uruchomiona aplikacja wyświetlająca pasek nawigacyjny](media/flask/step03-nav-bar.png)

1. Ze względu na to, że wprowadzono znaczące zmiany w aplikacji, jest to dobry moment na [zatwierdzenie zmian w kontroli źródła](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control).

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Użyj szablonu projektu sieci Web pełnej kolby](learn-flask-visual-studio-step-04-full-flask-project-template.md)

## <a name="go-deeper"></a>Przejdź głębiej

- [Wdróż aplikację sieci Web w usłudze Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
- Aby uzyskać więcej możliwości szablonów Jinja, takich jak przepływ sterowania, zobacz [Dokumentacja projektanta szablonów jinja](http://jinja.palletsprojects.com/en/2.10.x/templates/) (jinja.pocoo.org)
- Aby uzyskać szczegółowe informacje na temat korzystania z programu `url_for` , zobacz [url_for](https://flask.palletsprojects.com/en/1.0.x/api/#flask.url_for) w dokumentacji dotyczącej obiektu aplikacji w kolbie (Flask.pocoo.org).
- Kod źródłowy samouczka w witrynie GitHub: [Microsoft/Python-Sample-vs-Learning-Kolba](https://github.com/Microsoft/python-sample-vs-learning-flask)

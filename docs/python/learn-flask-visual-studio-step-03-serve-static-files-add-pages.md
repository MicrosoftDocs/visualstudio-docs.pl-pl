---
title: Dowiedz się, samouczek Flask w programie Visual Studio w kroku 3, pliki statyczne i strony
titleSuffix: ''
description: Przewodnik po podstawy Flask w kontekście projektów programu Visual Studio, w szczególności pokazująca, jak obsługa plików statycznych, dodawanie stron do aplikacji i użyć szablonu dziedziczenia
ms.date: 09/04/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 906c44ca3b1d0771202e78910870d38f9d4fb995
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065028"
---
# <a name="step-3-serve-static-files-add-pages-and-use-template-inheritance"></a>Krok 3: Obsługa plików statycznych, dodawanie stron i użyć szablonu dziedziczenia

**Poprzedni krok: [tworzenie aplikacji Flask za pomocą widoków i stron szablonów](learn-flask-visual-studio-step-02-create-app.md)**

W poprzednich krokach w tym samouczku wyjaśniono sposób tworzenia minimalną aplikację Flask za pomocą pojedynczej strony HTML niezależna. Nowoczesne aplikacje sieci web, jednak zwykle składają się z wielu stron i wprowadzić korzystanie z zasobów udostępnionych, takich jak pliki CSS i JavaScript, aby zapewnić spójne stylów i zachowanie.

W tym kroku dowiesz się, jak:

> [!div class="checklist"]
> - Użyj szablony elementów Visual Studio, aby szybko dodać nowe pliki o różnych typach wygodne schematyczny kod (krok 3 - 1)
> - Obsługa plików statycznych z kodu (krok 3-2, opcjonalnie)
> - Dodawanie dodatkowych stron do aplikacji (krok 3 z 3)
> - Użyj szablonu dziedziczenia, aby utworzyć pasek nagłówka, jak i nawigacji, który jest używany na stronach (krok 3 – 4)

## <a name="step-3-1-become-familiar-with-item-templates"></a>Krok 1 z 3: zapoznanie się z szablonów elementów

Podczas opracowywania aplikacji Flask, zazwyczaj należy dodać wiele plików więcej języka Python, HTML, CSS i JavaScript. Dla każdego typu pliku (oraz innych plików, takich jak *web.config* potrzebne do wdrożenia), program Visual Studio zapewnia wygodne [elementu szablony](python-item-templates.md) ułatwią Ci rozpoczęcie pracy.

Aby wyświetlić dostępne szablony, przejdź do **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy folder, w którym chcesz utworzyć element i wybierz pozycję **Dodaj** > **nowy element**:

![Dodaj okno dialogowe nowego elementu w programie Visual Studio](media/flask/step03-add-new-item-dialog.png)

Aby użyć szablonu, wybrania odpowiedniego szablonu, określ nazwę pliku i wybierz **OK**. Dodanie elementu w ten sposób automatycznie dodaje plik do projektu programu Visual Studio i oznaczy zmiany do kontroli źródła.

### <a name="question-how-does-visual-studio-know-which-item-templates-to-offer"></a>Pytanie: Jak Visual Studio wiesz, które element szablonów do oferty?

Odpowiedź: Visual Studio pliku projektu (*.pyproj*) zawiera identyfikator typu projektu, który oznacza je jako projektu języka Python. Visual Studio używa tego identyfikatora typu, aby pokazać tylko te szablony elementów, które są odpowiednie dla typu projektu. W ten sposób programu Visual Studio można podać bogatego zestawu szablonów elementów, dla typów bez konieczności sortowanie je każdym razem, gdy wiele projektów.

## <a name="step-3-2-serve-static-files-from-your-app"></a>Krok 2 z 3: Obsługa plików statycznych z aplikacji

W aplikacji sieci web utworzonych za pomocą języka Python (za pomocą dowolnej platformy) pliki języka Python zawsze uruchamiane na serwerze hosta sieci web i nigdy nie są przekazywane do komputera użytkownika. Inne pliki, takie jak CSS i JavaScript, są używane wyłącznie przez przeglądarki, więc serwer hosta po prostu dostarcza je jako — jest zawsze wtedy, gdy są one wymagane. Takie pliki są określane jako "statyczne" pliki i Flask może dostarczyć ją automatycznie bez konieczności pisania kodu. W plikach HTML na przykład, można po prostu odwołasz się do plików statycznych przy użyciu ścieżki względnej w projekcie. Pierwsza sekcja w tym kroku dodaje plik CSS do istniejącego szablonu strony.

Gdy potrzebne do dostarczania plików statycznych z kodu, takich jak za pośrednictwem implementacji punktu końcowego interfejsu API, Flask stanowi wygodną metodę umożliwiającą odwołują się do plików za pomocą ścieżek względnych w folderze o nazwie *statyczne* (w katalogu głównym projektu). Druga sekcja w tym kroku przedstawiono tę metodę, przy użyciu pliku prostego danych statycznych.

W obu przypadkach można organizować pliki objęte *statyczne* dowolny sposób.

### <a name="use-a-static-file-in-a-template"></a>Użyj pliku statycznego w szablonie

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **HelloFlask** folderu w projekcie programu Visual Studio, wybierz opcję **Dodaj** > **nowy folder**i nadaj folderowi `static`.

1. Kliknij prawym przyciskiem myszy **statyczne** i wybierz polecenie **Dodaj** > **nowy element**. W wyświetlonym oknie dialogowym wybierz **arkusza stylów** szablonu, nazwij plik `site.css`i wybierz **OK**. **Site.css** pliku pojawia się w projekcie i jest otwarty w edytorze. Twoja struktura folderów powinny wyglądać podobnie do poniższej ilustracji:

    ![Struktura plików statycznych, jak pokazano w Eksploratorze rozwiązań](media/flask/step03-static-file-structure.png)

1. Zastąp zawartość *site.css* następującym kodem i Zapisz plik:

    ```css
    .message {
        font-weight: 600;
        color: blue;
    }
    ```

1. Zastąp zawartość aplikacji *templates/index.html* pliku następującym kodem, który zastępuje `<strong>` element używany w kroku 2 z `<span>` odwołujący się `message` stylu klasy. Za pomocą klasy stylu w ten sposób zapewnia większą elastyczność w style elementu.

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

1. Uruchom projekt, aby obserwować wyniki. Zatrzymaj aplikację po zakończeniu, a następnie Zatwierdź zmiany do kontroli źródła, jeśli chcesz (jak wyjaśniono w [kroku 2](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control)).

### <a name="serve-a-static-file-from-code"></a>Obsługi plików statycznych z kodu

Flask udostępnia funkcję o nazwie `serve_static_file` , którą można wywołać z kodu do odwoływania się do każdego pliku w projekcie *statyczne* folderu. Poniższa procedura tworzy prosty punkt końcowy interfejsu API, który zwraca plik danych statycznych.

1. Jeśli użytkownik jeszcze tego nie zrobiono, Utwórz *statyczne* folder: w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **HelloFlask** folderu w projekcie programu Visual Studio, wybierz opcję **Dodaj** > **nowy folder**i nadaj folderowi `static`.

1. W *statyczne* folderu, Utwórz statyczny plik danych JSON o nazwie *data.json* z następującą zawartością, (które są bez znaczenia przykładowe dane):

    ```json
    {
        "01": {
            "note" : "Data is very simple because we're demonstrating only the mechanism."
        }
    }
    ```

1. W *views.py*, dodawanie funkcji za pomocą tras/api/danych zwracanych przy użyciu pliku danych statycznych `send_static_file` metody:

    ```python
    @app.route('/api/data')
    def get_data():
      return app.send_static_file('data.json')
    ```

1. Uruchom aplikację i przejdź do endpoint danych/api/aby zobaczyć, że zwracany jest plików statycznych. Gdy skończysz, Zatrzymaj aplikację.

### <a name="question-are-there-any-conventions-for-organizing-static-files"></a>Pytanie: Czy istnieją wszystkie konwencje służący do organizowania plików statycznych?

Odpowiedź: Możesz dodać inne pliki CSS, JavaScript i HTML w swojej *statyczne* folderu dowolny sposób. Typowy sposób organizowania plików statycznych jest utworzenie podfoldery o nazwach odpowiadających *czcionki*, *skrypty*, i *zawartości* (dla arkuszy stylów i inne pliki).

### <a name="question-how-do-i-handle-url-variables-and-query-parameters-in-an-api"></a>Pytanie: Jak obsługiwać adresu URL zmienne i parametry zapytania w interfejsie API?

Odpowiedź: Zobacz odpowiedź w kroku 1 – 4 dla [pytanie: jak Flask pracować zmiennej tras adresów URL i parametry zapytania?](learn-flask-visual-studio-step-01-project-solution.md#qa-url-variables)

## <a name="step-3-3-add-a-page-to-the-app"></a>Krok 3 z 3: Dodaj stronę aplikacji

Dodawanie innej strony w aplikacji oznacza, że następujące czynności:

- Dodaj funkcję języka Python, definiujący widok.
- Dodaj szablon dla strony kodu znaczników.
- Dodaj routingiem niezbędnych do projektu Flask *urls.py* pliku.

Poniższe kroki Dodawanie strony "About" do projektu "HelloFlask" i łącza do tej strony ze strony głównej:

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **szablony** folderu, wybierz **Dodaj** > **nowy element**, wybierz **Strony HTML** szablonu elementu, określ nazwę pliku `about.html`i wybierz **OK**.

    > [!Tip]
    > Jeśli **nowy element** polecenie nie pojawi się na **Dodaj** menu, upewnij się, zostało zatrzymane aplikację tak, aby program Visual Studio opuszcza tryb debugowania.

1. Zastąp zawartość *about.html* następującym kodem (Zastąp jawne łącze do strony głównej z paska nawigacyjnego proste w kroku 3 – 4):

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

1. Otwórz aplikację *views.py* pliku i Dodaj funkcję o nazwie `about` , który używa szablonu:

    ```python
    @app.route('/about')
    def about():
        return render_template(
            "about.html",
            title = "About HelloFlask",
            content = "Example app page for Flask.")
    ```

1. Otwórz *templates/index.html* pliku i Dodaj następujący wiersz bezpośrednio w ramach `<body>` elementu, aby utworzyć łącze do strony informacje (ponownie, należy zamienić ten link paska nawigacji, w kroku 3 – 4):

    ```html
    <div><a href="about">About</a></div>
    ```

1. Zapisz wszystkie pliki przy użyciu **pliku** > **Zapisz wszystko** polecenie menu lub po prostu naciśnij **Ctrl**+**Shift** + **S**. (Z technicznego punktu widzenia, ten krok nie jest wymagany, ponieważ uruchamiania projektu w programie Visual Studio automatycznie zapisuje pliki. Niemniej jednak to pozwala dowiedzieć!)

1. Uruchom projekt, aby obserwować wyniki i sprawdź Nawigacja między stronami. Zatrzymaj aplikację po zakończeniu.

### <a name="question-does-the-name-of-a-page-function-matter-to-flask"></a>Pytanie: Czy nazwa funkcji strony ma znaczenie do Flask?

Odpowiedź: Brak, ponieważ jest on `@app.route` dekoratora, który określa adresy URL, dla których Flask wywołuje funkcję do generowania odpowiedzi. Deweloperzy zazwyczaj jest zgodna z nazwą funkcji, do trasy, ale takie dopasowania nie jest wymagane.

## <a name="step-3-4-use-template-inheritance-to-create-a-header-and-nav-bar"></a>Krok 3 – 4: Użyj dziedziczenie w szablonie, aby utworzyć pasku nagłówka, jak i nav

Zamiast łącza nawigacji jawne na każdej stronie, nowoczesne aplikacje internetowe zazwyczaj korzystają ze znakowaniem nagłówek i pasek nawigacyjny, który zawiera najważniejsze łączy strony, menu podręczne i tak dalej. Aby upewnić się, że nagłówek i na pasku nawigacyjnym są takie same na wszystkich stronach, jednak nie chcesz powtórzyć ten sam kod w każdym szablonie strony. Zamiast tego chcesz zdefiniować typowych części wszystkich stron w jednym miejscu.

System szablonów firmy Flask (Jinja domyślnie) zapewnia dwa oznacza, że ponowne użycie określonych elementów w różnych szablonach: obejmuje i dziedziczenie.

- *Obejmuje* są inne szablony stron, wstawiające w określonym miejscu w szablonie odwołujący się przy użyciu składni `{% include <template_path> %}`. Można również użyć zmiennej, jeśli chcesz zmienić ścieżkę dynamicznie w kodzie. Obejmuje są zazwyczaj używane w treści strony Aby pobrać szablon z określonej lokalizacji, na stronie.

- *Dziedziczenie* używa `{% extends <template_path> %}` na początku szablon strony, aby określić szablon podstawowy udostępnionego odwołujący się szablon tworzy następnie na podstawie. Dziedziczenie jest najczęściej używany do definiowania układu udostępnionego, pasek nawigacji, a inne struktury dla stron aplikacji tak, aby przywołujący szablony muszą tylko dodać lub zmodyfikować określonych obszarach szablon podstawowy o nazwie *bloków*.

W obu przypadkach `<template_path>` względem aplikacji *szablony* folder (`../` lub `./` są również dozwolone).

Szablon podstawowy wyznacza *bloki* przy użyciu `{% block <block_name> %}` i `{% endblock %}` tagów. Jeśli szablon odwołujący się następnie używa tagi o takiej samej nazwie bloku, jego zawartość bloku zastępuje z szablonu podstawowego.

Poniższe kroki prezentują dziedziczenia:

1. W aplikacji *szablony* folderu, Utwórz nowy plik HTML (przy użyciu **Dodaj** > **nowy element** menu kontekstowego lub **Dodaj**  >  **Strony HTML**) o nazwie *layout.html*i zastąp jego zawartość ze znacznikami poniżej. Aby zobaczyć, że ten szablon zawiera bloku o nazwie "zawartość", to wszystko to Zastąp odwołujący się potrzeba strony:

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

1. Dodaj następujące style w aplikacji *static/site.css* pliku (w tym przewodniku nie podjęto próbę pokazują, w tym miejscu elastyczne; te style są po prostu wygenerować wynik interesujące):

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

1. Modyfikowanie *templates/index.html* do odwoływania się do szablon podstawowy i Zastąp blok zawartości. Aby zobaczyć, że za pomocą dziedziczenia, ten szablon staje się proste:

    ```html
    {% extends "layout.html" %}
    {% block content %}
    <span class="message">{{ message }}</span>{{ content }}
    {% endblock %}
    ```

1. Modyfikowanie *templates/about.html* także odwoływać się do szablonu podstawowego i zastępowania bloku zawartości:

    ```html
    {% extends "layout.html" %}
    {% block content %}
    {{ content }}
    {% endblock %}
    ```

1. Uruchom serwer, aby obserwować wyniki. Zamknij serwer po zakończeniu.

    ![Uruchomiona aplikacja wyświetlane na pasku nawigacyjnym](media/flask/step03-nav-bar.png)

1. Ponieważ wprowadzono istotne zmiany w aplikacji, ponownie to dobry moment, aby [Zatwierdź zmiany do kontroli źródła](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control).

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Pełny szablon projektu sieci Web Flask](learn-flask-visual-studio-step-04-full-flask-project-template.md)

## <a name="go-deeper"></a>Przejdź dalej

- [Wdrażanie aplikacji sieci web w usłudze Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
- Aby uzyskać więcej możliwości Jinja szablonów, takich jak przepływ sterowania, zobacz [Jinja szablon projektanta dokumentacji](http://jinja.pocoo.org/docs/2.10/templates) (jinja.pocoo.org)
- Aby uzyskać szczegółowe informacje na temat korzystania z `url_for`, zobacz [url_for](http://flask.pocoo.org/docs/1.0/api/?highlight=url_for#flask.url_for) w dokumentacji obiekt aplikacji Flask (flask.pocoo.org)
- Kod źródłowy samouczek w witrynie GitHub: [Microsoft/python — przykładowe vs uczenia — platformy flask](https://github.com/Microsoft/python-sample-vs-learning-flask)

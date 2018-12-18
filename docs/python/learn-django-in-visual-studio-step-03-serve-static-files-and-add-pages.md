---
title: Dowiedz się, samouczek Django w programie Visual Studio w kroku 3, pliki statyczne i strony
titleSuffix: ''
description: Przewodnik po podstawy Django w kontekście projektów programu Visual Studio, w szczególności pokazująca, jak obsługa plików statycznych, dodawanie stron do aplikacji i użyć szablonu dziedziczenia
ms.date: 11/19/2018
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
ms.openlocfilehash: cfde21f356e35366cfb80b029f918eed0364a7b5
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066083"
---
# <a name="step-3-serve-static-files-add-pages-and-use-template-inheritance"></a>Krok 3: Obsługa plików statycznych, dodawanie stron i użyć szablonu dziedziczenia

**Poprzedni krok: [tworzenie aplikacji Django przy użyciu widoków i stron szablonów](learn-django-in-visual-studio-step-02-create-an-app.md)**

W poprzednich krokach w tym samouczku wyjaśniono sposób tworzenia minimalną aplikację Django z pojedynczej strony HTML niezależna. Nowoczesne aplikacje sieci web, jednak zwykle składają się z wielu stron i wprowadzić korzystanie z zasobów udostępnionych, takich jak pliki CSS i JavaScript, aby zapewnić spójne stylów i zachowanie.

W tym kroku dowiesz się, jak:

> [!div class="checklist"]
> - Użyj szablony elementów Visual Studio, aby szybko dodać nowe pliki o różnych typach wygodne schematyczny kod (krok 3 - 1)
> - Konfigurowanie projektu Django do obsługi plików statycznych (krok 2 z 3)
> - Dodawanie dodatkowych stron do aplikacji (krok 3 z 3)
> - Użyj szablonu dziedziczenia, aby utworzyć pasek nagłówka, jak i nawigacji, który jest używany na stronach (krok 3 – 4)

## <a name="step-3-1-become-familiar-with-item-templates"></a>Krok 1 z 3: zapoznanie się z szablonów elementów

Podczas opracowywania aplikacji Django, zazwyczaj należy dodać wiele plików więcej języka Python, HTML, CSS i JavaScript. Dla każdego typu pliku (oraz innych plików, takich jak *web.config* potrzebne do wdrożenia), program Visual Studio zapewnia wygodne [elementu szablony](python-item-templates.md) ułatwią Ci rozpoczęcie pracy.

Aby wyświetlić dostępne szablony, przejdź do **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy folder, w którym chcesz utworzyć element i wybierz pozycję **Dodaj** > **nowy element**:

![Dodaj okno dialogowe nowego elementu w programie Visual Studio](media/django/step03-add-new-item-dialog.png)

Aby użyć szablonu, wybrania odpowiedniego szablonu, określ nazwę pliku i wybierz **OK**. Dodanie elementu w ten sposób automatycznie dodaje plik do projektu programu Visual Studio i oznaczy zmiany do kontroli źródła.

### <a name="question-how-does-visual-studio-know-which-item-templates-to-offer"></a>Pytanie: Jak Visual Studio wiesz, które element szablonów do oferty?

Odpowiedź: Visual Studio pliku projektu (*.pyproj*) zawiera identyfikator typu projektu, który oznacza je jako projektu języka Python. Visual Studio używa tego identyfikatora typu, aby pokazać tylko te szablony elementów, które są odpowiednie dla typu projektu. W ten sposób programu Visual Studio można podać bogatego zestawu szablonów elementów, dla typów bez konieczności sortowanie je każdym razem, gdy wiele projektów.

## <a name="step-3-2-serve-static-files-from-your-app"></a>Krok 2 z 3: Obsługa plików statycznych z aplikacji

W aplikacji sieci web utworzonych za pomocą języka Python (za pomocą dowolnej platformy) pliki języka Python zawsze uruchamiane na serwerze hosta sieci web i nigdy nie są przekazywane do komputera użytkownika. Inne pliki, takie jak CSS i JavaScript, są używane wyłącznie przez przeglądarki, więc serwer hosta po prostu dostarcza je jako — jest zawsze wtedy, gdy są one wymagane. Takie pliki są określane jako "statyczne" pliki i Django może dostarczyć ją automatycznie bez konieczności pisania kodu.

Projektu Django jest domyślnie skonfigurowany do obsługi plików statycznych z poziomu aplikacji *statyczne* folderu dzięki te wiersze w projekcie Django *settings.py*:

```python
# Static files (CSS, JavaScript, Images)
# https://docs.djangoproject.com/en/1.9/howto/static-files/

STATIC_URL = '/static/'

STATIC_ROOT = posixpath.join(*(BASE_DIR.split(os.path.sep) + ['static']))
```

Można organizować pliki przy użyciu dowolnej struktury folderów w ramach *statyczne* , a następnie użyć ścieżek względnych w tym folderze, do odwoływania się do plików. Aby zademonstrować ten proces, poniższe kroki Dodawanie pliku CSS do aplikacji, a następnie użyj tego arkusza stylów w *index.html* szablonu:

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **HelloDjangoApp** folderu w projekcie programu Visual Studio, wybierz opcję **Dodaj** > **nowy folder**i nadaj folderowi `static`.

1. Kliknij prawym przyciskiem myszy **statyczne** i wybierz polecenie **Dodaj** > **nowy element**. W wyświetlonym oknie dialogowym wybierz **arkusza stylów** szablonu, nazwij plik `site.css`i wybierz **OK**. **Site.css** pliku pojawia się w projekcie i jest otwarty w edytorze. Twoja struktura folderów powinny wyglądać podobnie do poniższej ilustracji:

    ![Struktura plików statycznych, jak pokazano w Eksploratorze rozwiązań](media/django/step03-static-file-structure.png)

1. Zastąp zawartość *site.css* następującym kodem i Zapisz plik:

    ```css
    .message {
        font-weight: 600;
        color: blue;
    }
    ```

1. Zastąp zawartość aplikacji *templates/HelloDjangoApp/index.html* pliku następującym kodem, który zastępuje `<strong>` element używany w kroku 2 z `<span>` odwołujący się `message` stylu klasy. Za pomocą klasy stylu w ten sposób zapewnia większą elastyczność w style elementu. (Jeśli jeszcze nie został przeniesiony *index.html* do podfolderu w *szablony* podczas korzystania z programu VS 2017 w wersji 15.7 wcześniej, można znaleźć [namespacing szablonu](learn-django-in-visual-studio-step-02-create-an-app.md#template-namespacing) w kroku 2 – 4.)

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
            {% load staticfiles %} <!-- Instruct Django to load static files -->
            <link rel="stylesheet" type="text/css" href="{% static 'site.css' %}" />
        </head>
        <body>
            <span class="message">{{ message }}</span>{{ content }}
        </body>
    </html>
    ```

1. Uruchom projekt, aby obserwować wyniki. Zatrzymaj serwer po zakończeniu, a następnie Zatwierdź zmiany do kontroli źródła, jeśli chcesz (jak wyjaśniono w [kroku 2](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control)).

### <a name="question-what-is-the-purpose-of-the--load-staticfiles--tag"></a>Pytanie: Co to jest celem {% obciążenia, jakiego staticfiles %} tag?

Odpowiedź: `{% load staticfiles %}` wiersza jest wymagane, aby odwołujące się do plików statycznych w elementach, takich jak `<head>` i `<body>`. W przykładzie przedstawionym w tej sekcji, "staticfiles" odnosi się do niestandardowego Django szablonu tag zestaw, który jest, co pozwala na używanie `{% static %}` składni do odwoływania się do plików statycznych.  Bez `{% load staticfiles %}`, zobaczysz wyjątek po uruchomieniu aplikacji.

### <a name="question-are-there-any-conventions-for-organizing-static-files"></a>Pytanie: Czy istnieją wszystkie konwencje służący do organizowania plików statycznych?

Odpowiedź: Możesz dodać inne pliki CSS, JavaScript i HTML w swojej *statyczne* folderu dowolny sposób. Typowy sposób organizowania plików statycznych jest utworzenie podfoldery o nazwach odpowiadających *czcionki*, *skrypty*, i *zawartości* (dla arkuszy stylów i inne pliki). W każdym przypadku Pamiętaj, aby uwzględnić te foldery w ścieżce względnej do pliku w `{% static %}` odwołania.

## <a name="step-3-3-add-a-page-to-the-app"></a>Krok 3 z 3: Dodaj stronę aplikacji

Dodawanie innej strony w aplikacji oznacza, że następujące czynności:

- Dodaj funkcję języka Python, definiujący widok.
- Dodaj szablon dla strony kodu znaczników.
- Dodaj wymagane routingu do projektu Django *urls.py* pliku.

Poniższe kroki Dodawanie strony "About" do projektu "HelloDjangoApp" i łącza do tej strony ze strony głównej:

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **szablony/HelloDjangoApp** folderu, wybierz **Dodaj** > **nowy element**, wybierz opcję **strony HTML** szablonu elementu, określ nazwę pliku `about.html`i wybierz **OK**.

    > [!Tip]
    > Jeśli **nowy element** polecenie nie pojawi się na **Dodaj** menu, upewnij się, zostało zatrzymane serwer tak, aby program Visual Studio opuszcza tryb debugowania.

1. Zastąp zawartość *about.html* następującym kodem (Zastąp jawne łącze do strony głównej z paska nawigacyjnego proste w kroku 3 – 4):

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
            {% load staticfiles %}
            <link rel="stylesheet" type="text/css" href="{% static 'site.css' %}" />
        </head>
        <body>
            <div><a href="home">Home</a></div>
            {{ content }}
        </body>
    </html>
    ```

1. Otwórz aplikację *views.py* pliku i Dodaj funkcję o nazwie `about` , który używa szablonu:

    ```python
    def about(request):
        return render(
            request,
            "HelloDjangoApp/about.html",
            {
                'title' : "About HelloDjangoApp",
                'content' : "Example app page for Django."
            }
        )
    ```

1. Otwórz projekt Django *urls.py* pliku i Dodaj następujący wiersz do `urlPatterns` tablicy:

    ```python
    url(r'^about$', HelloDjangoApp.views.about, name='about'),
    ```

1. Otwórz *templates/HelloDjangoApp/index.html* pliku i Dodaj następujący wiersz poniżej `<body>` elementu, aby utworzyć łącze do strony informacje (ponownie, należy zamienić ten link paska nawigacji, w kroku 3 – 4):

    ```html
    <div><a href="about">About</a></div>
    ```

1. Zapisz wszystkie pliki przy użyciu **pliku** > **Zapisz wszystko** polecenie menu lub po prostu naciśnij **Ctrl**+**Shift** + **S**. (Z technicznego punktu widzenia, ten krok nie jest wymagany, ponieważ uruchamiania projektu w programie Visual Studio automatycznie zapisuje pliki. Niemniej jednak to pozwala dowiedzieć!)

1. Uruchom projekt, aby obserwować wyniki i sprawdź Nawigacja między stronami. Zamknij serwer po zakończeniu.

### <a name="question-i-tried-using-index-for-the-link-to-the-home-page-but-it-didnt-work-why"></a>Pytanie: czy mogę próbowano przy użyciu "index", aby uzyskać link do strony głównej, ale nie sprawdził się. Dlaczego?

Odpowiedź: mimo że widoku działa w programach *views.py* nosi nazwę `index`, adresu URL routingu wzorców w projekcie Django *urls.py* plik nie zawiera wyrażenia regularnego, który pasuje do ciągu " Indeks". Aby dopasować te parametry, należy dodać inny wpis dla wzorca `^index$`.

Jak pokazano w następnej sekcji, to lepiej używać `{% url '<pattern_name>' %}` tagu w szablonie strony do odwoływania się do *nazwa* wzorca, w którym wielkość Django tworzy prawidłowego adresu URL. Na przykład Zastąp ciąg `<div><a href="home">Home</a></div>` w *about.html* z `<div><a href="{% url 'index' %}">Home</a></div>`. Użycie "index" działa, w tym miejscu, ponieważ pierwszy adres URL wzorca w *urls.py* w rzeczywistości o nazwie "index" (na mocy niniejszej `name='index'` argument). Umożliwia także "home" do odwoływania się do drugi wzorzec.

## <a name="step-3-4-use-template-inheritance-to-create-a-header-and-nav-bar"></a>Krok 3 – 4: Użyj dziedziczenie w szablonie, aby utworzyć pasku nagłówka, jak i nav

Zamiast łącza nawigacji jawne na każdej stronie, nowoczesne aplikacje internetowe zazwyczaj korzystają ze znakowaniem nagłówek i pasek nawigacyjny, który zawiera najważniejsze łączy strony, menu podręczne i tak dalej. Aby upewnić się, że nagłówek i na pasku nawigacyjnym są takie same na wszystkich stronach, jednak nie chcesz powtórzyć ten sam kod w każdym szablonie strony. Zamiast tego chcesz zdefiniować typowych części wszystkich stron w jednym miejscu.

System szablonów firmy Django zapewnia dwa oznacza, że ponowne użycie określonych elementów w różnych szablonach: obejmuje i dziedziczenie.

- *Obejmuje* są inne szablony stron, wstawiające w określonym miejscu w szablonie odwołujący się przy użyciu składni `{% include <template_path> %}`. Można również użyć zmiennej, jeśli chcesz zmienić ścieżkę dynamicznie w kodzie. Obejmuje są zazwyczaj używane w treści strony Aby pobrać szablon z określonej lokalizacji, na stronie.

- *Dziedziczenie* używa `{% extends <template_path> %}` na początku szablon strony, aby określić szablon podstawowy udostępnionego odwołujący się szablon tworzy następnie na podstawie. Dziedziczenie jest najczęściej używany do definiowania układu udostępnionego, pasek nawigacji, a inne struktury dla stron aplikacji tak, aby przywołujący szablony muszą tylko dodać lub zmodyfikować określonych obszarach szablon podstawowy o nazwie *bloków*.

W obu przypadkach `<template_path>` względem aplikacji *szablony* folder (`../` lub `./` są również dozwolone).

Szablon podstawowy wyznacza blokach, używając `{% block <block_name> %}` i `{% endblock %}` tagów. Jeśli szablon odwołujący się następnie używa tagi o takiej samej nazwie bloku, jego zawartość bloku przesłonięcia podstawowego szablonu.

Poniższe kroki prezentują dziedziczenia:

1. W aplikacji *szablony/HelloDjangoApp* folderu, Utwórz nowy plik HTML (przy użyciu **Dodaj** > **nowy element** menu kontekstowego lub **Dodaj**  >  **Strony HTML**) o nazwie *layout.html*i zastąp jego zawartość ze znacznikami poniżej. Aby zobaczyć, że ten szablon zawiera bloku o nazwie "zawartość", to wszystko to Zastąp odwołujący się potrzeba strony:

    ```html
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="utf-8" />
        <title>{{ title }}</title>
        {% load staticfiles %}
        <link rel="stylesheet" type="text/css" href="{% static 'site.css' %}" />
    </head>

    <body>
        <div class="navbar">
           <a href="/" class="navbar-brand">Hello Django</a>
           <a href="{% url 'home' %}" class="navbar-item">Home</a>
           <a href="{% url 'about' %}" class="navbar-item">About</a>
        </div>

        <div class="body-content">
    {% block content %}{% endblock %}
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

1. Modyfikowanie *templates/HelloDjangoApp/index.html* do odwoływania się do szablon podstawowy i Zastąp blok zawartości. Aby zobaczyć, że za pomocą dziedziczenia, ten szablon staje się proste:

    ```html
    {% extends "HelloDjangoApp/layout.html" %}
    {% block content %}
    <span class="message">{{ message }}</span>{{ content }}
    {% endblock %}
    ```

1. Modyfikowanie *templates/HelloDjangoApp/about.html* także odwoływać się do szablonu podstawowego i zastępowania bloku zawartości:

    ```html
    {% extends "HelloDjangoApp/layout.html" %}
    {% block content %}
    {{ content }}
    {% endblock %}
    ```

1. Uruchom serwer, aby obserwować wyniki. Zamknij serwer po zakończeniu.

    ![Uruchomiona aplikacja wyświetlane na pasku nawigacyjnym](media/django/step03-nav-bar.png)

1. Ponieważ miał wprowadzone istotnych zmian do aplikacji, ponownie to dobry moment, aby [Zatwierdź zmiany do kontroli źródła](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control).

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Użyj pełnego szablonów projektów internetowych Django](learn-django-in-visual-studio-step-04-full-django-project-template.md)

## <a name="go-deeper"></a>Przejdź dalej

- [Wdrażanie aplikacji sieci web w usłudze Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [Zapisywanie swoją pierwszą aplikację Django, część 3 (widoki)](https://docs.djangoproject.com/en/2.0/intro/tutorial03/) (docs.djangoproject.com)
- Aby uzyskać więcej możliwości szablonach Django, takich jak przepływ sterowania, zobacz [język szablonu Django](https://docs.djangoproject.com/en/2.0/ref/templates/language/) (docs.djangoproject.com)
- Aby uzyskać szczegółowe informacje na temat korzystania z `{% url %}` tagów, zobacz [adresu url](https://docs.djangoproject.com/en/2.0/ref/templates/builtins/#url) w ramach [tagi wbudowany szablon i filtry dla odwołania szablonów Django](https://docs.djangoproject.com/en/2.0/ref/templates/builtins/) (docs.djangoproject.com)
- Kod źródłowy samouczek w witrynie GitHub: [Microsoft/python — przykładowe vs uczenia — django](https://github.com/Microsoft/python-sample-vs-learning-django)

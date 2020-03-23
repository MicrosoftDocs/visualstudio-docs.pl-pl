---
title: Dowiedz się samouczek Django w programie Visual Studio krok 3, pliki statyczne i strony
titleSuffix: ''
description: Przewodnik po podstawach Django w kontekście projektów programu Visual Studio, w szczególności pokazujący, jak obsługiwać pliki statyczne, dodawać strony do aplikacji i używać dziedziczenia szablonów
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 54a80ef606a553846ef5be7a86ed4183f3ffde57
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "62958255"
---
# <a name="step-3-serve-static-files-add-pages-and-use-template-inheritance"></a>Krok 3: Obsługa plików statycznych, dodawanie stron i używanie dziedziczenia szablonów

**Poprzedni krok: [Tworzenie aplikacji Django z widokami i szablonami stron](learn-django-in-visual-studio-step-02-create-an-app.md)**

W poprzednich krokach tego samouczka dowiesz się, jak utworzyć minimalną aplikację Django z pojedynczą stroną samodzielnego kodu HTML. Nowoczesne aplikacje internetowe składają się jednak zazwyczaj z wielu stron i korzystają z zasobów udostępnionych, takich jak pliki CSS i JavaScript, aby zapewnić spójne stylizacje i zachowanie.

W tym kroku dowiesz się, jak:

> [!div class="checklist"]
> - Za pomocą szablonów elementów programu Visual Studio można szybko dodawać nowe pliki różnych typów za pomocą wygodnego kodu standardowego (krok 3-1)
> - Konfigurowanie projektu Django do obsługi plików statycznych (krok 3-2)
> - Dodawanie dodatkowych stron do aplikacji (krok 3-3)
> - Tworzenie nagłówka i paska nawigacyjnych używanego na różnych stronach za pomocą dziedziczenia szablonów

## <a name="step-3-1-become-familiar-with-item-templates"></a>Krok 3-1: Zapoznaj się z szablonami przedmiotów

Podczas tworzenia aplikacji Django zazwyczaj dodajesz o wiele więcej plików Python, HTML, CSS i JavaScript. Dla każdego typu pliku (a także innych plików, takich jak *web.config,* które mogą być potrzebne do wdrożenia), visual studio zapewnia wygodne [szablony elementów,](python-item-templates.md) aby rozpocząć.

Aby wyświetlić dostępne szablony, przejdź do **Programu Solution Explorer**, kliknij prawym przyciskiem myszy folder, w którym chcesz utworzyć element, wybierz pozycję **Dodaj** > **nowy element:**

![Dodawanie nowego okna dialogowego elementu w programie Visual Studio](media/django/step03-add-new-item-dialog.png)

Aby użyć szablonu, wybierz żądany szablon, określ nazwę pliku i wybierz **przycisk OK**. Dodawanie elementu w ten sposób automatycznie dodaje plik do projektu programu Visual Studio i oznacza zmiany dla kontroli źródła.

### <a name="question-how-does-visual-studio-know-which-item-templates-to-offer"></a>Pytanie: Skąd program Visual Studio wie, które szablony elementów do zaoferowania?

Odpowiedź: Plik projektu programu Visual Studio (*.pyproj*) zawiera identyfikator typu projektu, który oznacza go jako projekt języka Python. Visual Studio używa tego identyfikatora typu, aby wyświetlić tylko te szablony elementów, które są odpowiednie dla typu projektu. W ten sposób visual studio może dostarczyć bogaty zestaw szablonów elementów dla wielu typów projektów bez pytania, aby sortować je za każdym razem.

## <a name="step-3-2-serve-static-files-from-your-app"></a>Krok 3-2: Obsługa plików statycznych z aplikacji

W aplikacji internetowej utworzonej za pomocą języka Python (przy użyciu dowolnej struktury) pliki Języka Python są zawsze uruchamiane na serwerze hosta internetowego i nigdy nie są przesyłane do komputera użytkownika. Inne pliki, takie jak CSS i JavaScript, są używane wyłącznie przez przeglądarkę, więc serwer hosta po prostu dostarcza je w stanie takim, w jakim są wymagane. Takie pliki są określane jako "statyczne" pliki, a Django może dostarczyć je automatycznie bez konieczności pisania kodu.

Projekt Django jest domyślnie skonfigurowany do obsługi plików statycznych z folderu *statycznego* aplikacji, dzięki tym liniom w *settings.py*projektu Django:

```python
# Static files (CSS, JavaScript, Images)
# https://docs.djangoproject.com/en/1.9/howto/static-files/

STATIC_URL = '/static/'

STATIC_ROOT = posixpath.join(*(BASE_DIR.split(os.path.sep) + ['static']))
```

Można organizować pliki przy użyciu dowolnej struktury folderów w *obrębie statycznej,* która ci się podoba, a następnie używać ścieżek względnych w tym folderze, aby odwoływać się do plików. Aby zademonstrować ten proces, następujące kroki dodają plik CSS do aplikacji, a następnie użyj tego arkusza stylów w szablonie *index.html:*

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy folder **HelloDjangoApp** w `static`projekcie programu Visual Studio, wybierz pozycję **Dodaj** > nowy**folder**i nazwij folder .

1. Kliknij prawym przyciskiem myszy folder **statyczny** i wybierz polecenie **Dodaj** > **nowy element**. W wyświetlonym oknie dialogowym zaznacz szablon **arkusza stylów,** nazwij plik `site.css`i wybierz przycisk **OK**. Plik **site.css** pojawi się w projekcie i zostanie otwarty w edytorze. Struktura folderów powinna wyglądać podobnie do następującej ilustracji:

    ![Statyczna struktura plików, jak pokazano w Eksploratorze rozwiązań](media/django/step03-static-file-structure.png)

1. Zastąp zawartość *witryny site.css* następującym kodem i zapisz plik:

    ```css
    .message {
        font-weight: 600;
        color: blue;
    }
    ```

1. Zastąp zawartość pliku *templates/HelloDjangoApp/index.html* aplikacji następującym kodem, który `<strong>` zastępuje element używany w `<span>` kroku 2, który odwołuje się do klasy `message` stylu. Korzystanie z klasy stylu w ten sposób zapewnia znacznie większą elastyczność w stylizacji elementu. (Jeśli *index.html* nie został przeniesiony do podfolderu w *szablonach* podczas korzystania z programu VS 2017 15.7 lub wcześniejszych, zapoznaj się [z nazwami szablonów](learn-django-in-visual-studio-step-02-create-an-app.md#template-namespacing) w kroku 2-4).

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

1. Uruchom projekt, aby obserwować wyniki. Zatrzymaj serwer po zakończeniu i zaobewuj zmiany do kontroli źródła, jeśli chcesz (jak wyjaśniono w [kroku 2](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control)).

### <a name="question-what-is-the-purpose-of-the--load-staticfiles--tag"></a>Pytanie: Jaki jest cel tagu {% load staticfiles %}?

Odpowiedź: `{% load staticfiles %}` Linia jest wymagana przed odwoływaniem się do `<head>` `<body>`plików statycznych w elementach takich jak i . W przykładzie pokazanym w tej sekcji "staticfiles" odnosi się do niestandardowego zestawu tagów `{% static %}` szablonu Django, który umożliwia użycie składni w odniesieniu do plików statycznych.  Bez `{% load staticfiles %}`, zobaczysz wyjątek po uruchomieniu aplikacji.

### <a name="question-are-there-any-conventions-for-organizing-static-files"></a>Pytanie: Czy istnieją jakieś konwencje organizowania plików statycznych?

Odpowiedź: W folderze *statycznym* możesz dodawać inne pliki CSS, JavaScript i HTML. Typowym sposobem organizowania plików statycznych jest tworzenie podfolderów o nazwie *czcionki,* *skrypty*i *zawartość* (dla arkuszy stylów i innych plików). W każdym przypadku należy pamiętać o uwzględnienie tych folderów w ścieżce względnej do pliku w `{% static %}` odwołaniach.

## <a name="step-3-3-add-a-page-to-the-app"></a>Krok 3-3: Dodawanie strony do aplikacji

Dodanie kolejnej strony do aplikacji oznacza, że:

- Dodaj funkcję Języka Python, która definiuje widok.
- Dodaj szablon znaczników strony.
- Dodaj niezbędną routing do pliku *urls.py* projektu Django.

Następujące kroki dodają stronę "Informacje" do projektu "HelloDjangoApp" i linki do tej strony ze strony głównej:

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy **folder templates/HelloDjangoApp,** wybierz `about.html`pozycję **Dodaj** > nowy**element**, wybierz szablon elementu strony **HTML,** nazwij plik i wybierz przycisk **OK**.

    > [!Tip]
    > Jeśli polecenie **Nowy element** nie jest wyświetlane w menu **Dodaj,** upewnij się, że serwer został zatrzymany, aby program Visual Studio zakończył działanie trybu debugowania.

1. Zastąp zawartość *about.html* następującym znacznikiem (łącze jawne do strony głównej zastępujesz prostym paskiem nawigacyjnym w kroku 3-4):

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

1. Otwórz plik *views.py* aplikacji i dodaj funkcję `about` o nazwie, która używa szablonu:

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

1. Otwórz plik *urls.py* projektu Django i dodaj następujący wiersz `urlPatterns` do tablicy:

    ```python
    url(r'^about$', HelloDjangoApp.views.about, name='about'),
    ```

1. Otwórz plik *templates/HelloDjangoApp/index.html* i dodaj następujący wiersz `<body>` poniżej elementu, aby utworzyć łącze do strony Informacje (ponownie zastąp ten link paskiem nawigacyjnym w kroku 3-4):

    ```html
    <div><a href="about">About</a></div>
    ```

1. Zapisz wszystkie pliki za pomocą polecenia menu **Zapisz** > **wszystko** lub po prostu naciśnij **klawisze Ctrl**+**Shift**+**S**. (Technicznie ten krok nie jest potrzebny, ponieważ uruchomienie projektu w programie Visual Studio automatycznie zapisuje pliki. Niemniej jednak, jest to dobra komenda, aby wiedzieć o!)

1. Uruchom projekt, aby obserwować wyniki i sprawdzić nawigację między stronami. Zamknij serwer po zakończeniu.

### <a name="question-i-tried-using-index-for-the-link-to-the-home-page-but-it-didnt-work-why"></a>Pytanie: Próbowałem użyć "indeks" dla linku do strony głównej, ale to nie zadziałało. Dlaczego?

Odpowiedź: Mimo że funkcja *views.py* widoku w views.py `index`jest nazwana, wzorce routingu adresów URL w pliku *urls.py* projektu Django nie zawierają wyrażenia regularnego, które pasuje do ciągu "index". Aby dopasować ten ciąg, należy dodać `^index$`kolejny wpis dla wzorca .

Jak pokazano w następnej sekcji, o wiele `{% url '<pattern_name>' %}` lepiej jest użyć tagu w szablonie strony, aby odwołać się do *nazwy* wzoru, w którym to przypadku Django tworzy odpowiedni adres URL dla Ciebie. Na przykład `<div><a href="home">Home</a></div>` zastąp `<div><a href="{% url 'index' %}">Home</a></div>`w *pliku about.html* . Użycie "index" działa tutaj, ponieważ pierwszy wzorzec adresu URL w *urls.py* jest w rzeczywistości `name='index'` nazwany "index" (na podstawie argumentu). Możesz również użyć "home", aby odwołać się do drugiego wzoru.

## <a name="step-3-4-use-template-inheritance-to-create-a-header-and-nav-bar"></a>Krok 3-4: Tworzenie nagłówka i paska nawigacyjnych za pomocą dziedziczenia szablonu

Zamiast jawnych łączy nawigacyjnych na każdej stronie, nowoczesne aplikacje internetowe zazwyczaj używają nagłówka znakowania i paska nawigacyjnego, który zawiera najważniejsze łącza stron, menu podręczne i tak dalej. Aby upewnić się, że nagłówek i pasek nawigacyjny są takie same na wszystkich stronach, nie chcesz jednak powtarzać tego samego kodu w każdym szablonie strony. Zamiast tego chcesz zdefiniować wspólne części wszystkich stron w jednym miejscu.

System szablonów Django zapewnia dwa sposoby ponownego użytku określonych elementów w wielu szablonach: zawiera i dziedziczenie.

- *Zawiera* inne szablony stron wstawiane w określonym miejscu w szablonie odsyłający przy użyciu składni `{% include <template_path> %}`. Można również użyć zmiennej, jeśli chcesz dynamicznie zmienić ścieżkę w kodzie. Obejmuje są zazwyczaj używane w treści strony do ściągania w szablonie udostępnionym w określonej lokalizacji na stronie.

- *Dziedziczenie* używa `{% extends <template_path> %}` na początku szablonu strony, aby określić udostępniony szablon podstawowy, który następnie opiera się na szablonie odsyłający. Dziedziczenie jest powszechnie używane do definiowania układu udostępnionego, paska nawigacyjnyego i innych struktur dla stron aplikacji, w ten sposób, że szablony odwołujące się muszą tylko dodawać lub modyfikować określone obszary szablonu podstawowego o nazwie *bloki*.

W obu `<template_path>` przypadkach jest względem folderu *szablonów* aplikacji (`../` lub `./` są również dozwolone).

Szablon podstawowy wyznacza bloki `{% block <block_name> %}` przy `{% endblock %}` użyciu i tagi. Jeśli szablon odsyłający używa tagów o tej samej nazwie bloku, jego zawartość bloku zastępuje zawartość szablonu podstawowego.

Następujące kroki pokazują dziedziczenie:

1. W *folderze aplikacji templates/HelloDjangoApp* utwórz nowy plik HTML (za pomocą menu**kontekstowego** **Dodaj** > nowy element lub **Dodaj** > **stronę HTML**) o nazwie *layout.html*i zastąp jego zawartość znacznikami poniżej. Widać, że ten szablon zawiera blok o nazwie "zawartość", który jest wszystkim, co strony odsyłający muszą zastąpić:

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

1. Zmodyfikuj *templates/HelloDjangoApp/index.html,* aby odwoływać się do szablonu podstawowego i zastąpić blok zawartości. Widać, że za pomocą dziedziczenia ten szablon staje się prosty:

    ```html
    {% extends "HelloDjangoApp/layout.html" %}
    {% block content %}
    <span class="message">{{ message }}</span>{{ content }}
    {% endblock %}
    ```

1. Zmodyfikuj *templates/HelloDjangoApp/about.html,* aby również odwoływać się do szablonu podstawowego i zastępować blok zawartości:

    ```html
    {% extends "HelloDjangoApp/layout.html" %}
    {% block content %}
    {{ content }}
    {% endblock %}
    ```

1. Uruchom serwer, aby obserwować wyniki. Zamknij serwer po zakończeniu.

    ![Uruchamianie aplikacji z pasem nawigacyjnym](media/django/step03-nav-bar.png)

1. Ponieważ wprowadzono istotne zmiany w aplikacji, znowu jest to dobry moment, aby [zatwierdzić zmiany w kontroli źródła.](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control)

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Użyj pełnego szablonu django Web Project](learn-django-in-visual-studio-step-04-full-django-project-template.md)

## <a name="go-deeper"></a>Głębiej

- [Wdrażanie aplikacji sieci Web w usłudze Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [Pisanie pierwszej aplikacji Django, część 3 (widoki)](https://docs.djangoproject.com/en/2.0/intro/tutorial03/) (docs.djangoproject.com)
- Aby uzyskać więcej możliwości szablonów Django, takich jak przepływ sterowania, zobacz [język szablonu Django](https://docs.djangoproject.com/en/2.0/ref/templates/language/) (docs.djangoproject.com)
- Aby uzyskać szczegółowe `{% url %}` informacje na temat używania tagu, zobacz [adres URL](https://docs.djangoproject.com/en/2.0/ref/templates/builtins/#url) [wbudowanych tagów szablonów i filtrów dla szablonów Django (docs.djangoproject.com)](https://docs.djangoproject.com/en/2.0/ref/templates/builtins/)
- Kod źródłowy samouczka na GitHub: [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)

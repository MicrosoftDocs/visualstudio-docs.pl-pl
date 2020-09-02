---
title: Poznaj samouczek Django w programie Visual Studio krok 3, pliki statyczne i strony
titleSuffix: ''
description: Przewodnik po Django podstawy w kontekście projektów programu Visual Studio, w tym szczegółowe informacje o sposobie obsługi plików statycznych, dodawaniu stron do aplikacji i używania dziedziczenia szablonów
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 748f941d5a8f257b3765b06651ff3244793e0123
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "88238533"
---
# <a name="step-3-serve-static-files-add-pages-and-use-template-inheritance-with-django-app"></a>Krok 3. obsługiwanie plików statycznych, dodawanie stron i używanie dziedziczenia szablonów z aplikacją Django

**Poprzedni krok: [Tworzenie aplikacji Django za pomocą widoków i szablonów stron](learn-django-in-visual-studio-step-02-create-an-app.md)**

W poprzednich krokach tego samouczka wiesz już, jak utworzyć aplikację minimalną Django za pomocą pojedynczej strony kodu HTML zawartej w dowolnym miejscu. Nowoczesne aplikacje sieci Web, jednak zwykle składają się z wielu stron i używają zasobów udostępnionych, takich jak pliki CSS i JavaScript, do zapewnienia spójnego stylu i zachowania.

W tym kroku dowiesz się, jak:

> [!div class="checklist"]
> - Użyj szablonów elementów programu Visual Studio, aby szybko dodawać nowe pliki różnych typów przy użyciu wygodnego kodu standardowego (krok 3-1)
> - Konfigurowanie projektu Django do obsługiwania plików statycznych (krok 3-2)
> - Dodawanie dodatkowych stron do aplikacji (krok 3-3)
> - Użyj dziedziczenia szablonów, aby utworzyć nagłówek i pasek nawigacyjny, który jest używany na stronach (krok 3-4)

## <a name="step-3-1-become-familiar-with-item-templates"></a>Krok 3-1: Zapoznaj się z szablonami elementów

Podczas opracowywania aplikacji Django zazwyczaj dodawane są pliki języka Python, HTML, CSS i JavaScript. Dla każdego typu pliku (a także innych plików, takich jak *web.config* , które mogą być potrzebne do wdrożenia), program Visual Studio udostępnia wygodne [Szablony elementów](python-item-templates.md) umożliwiające rozpoczęcie pracy.

Aby wyświetlić dostępne szablony, przejdź do **Eksplorator rozwiązań**, kliknij prawym przyciskiem myszy folder, w którym chcesz utworzyć element, wybierz pozycję **Dodaj**  >  **nowy element**:

![Okno dialogowe Dodawanie nowego elementu w programie Visual Studio](media/django/step03-add-new-item-dialog.png)

Aby użyć szablonu, wybierz odpowiedni szablon, określ nazwę pliku, a następnie wybierz **przycisk OK**. Dodanie elementu w ten sposób powoduje automatyczne dodanie pliku do projektu programu Visual Studio i oznaczenie zmian w kontroli źródła.

### <a name="question-how-does-visual-studio-know-which-item-templates-to-offer"></a>Pytanie: w jaki sposób program Visual Studio wie, które szablony elementów mają być oferowane?

Odpowiedź: plik projektu programu Visual Studio (*. pyproj*) zawiera identyfikator typu projektu, który oznacza go jako projekt języka Python. Program Visual Studio używa tego identyfikatora typu do wyświetlania tylko szablonów elementów, które są odpowiednie dla typu projektu. Dzięki temu program Visual Studio może dostarczyć bogaty zestaw szablonów elementów dla wielu typów projektów bez monitowania o sortowanie za każdym razem.

## <a name="step-3-2-serve-static-files-from-your-app"></a>Krok 3-2: obchodzenie plików statycznych z aplikacji

W aplikacji sieci Web skompilowanej za pomocą języka Python (przy użyciu dowolnej platformy) pliki języka Python są zawsze uruchamiane na serwerze hosta sieci Web i nigdy nie są przesyłane do komputera użytkownika. Inne pliki, takie jak CSS i JavaScript, są używane wyłącznie przez przeglądarkę, więc serwer hosta po prostu dostarcza je w miarę ich żądania. Takie pliki są określane jako pliki "static", a Django mogą dostarczać je automatycznie bez konieczności pisania kodu.

Projekt Django jest domyślnie skonfigurowany do obsłużenia plików statycznych z folderu *statycznego* aplikacji, dzięki czemu są one zgodne z tymi wierszami w *Settings.py*projektu Django:

```python
# Static files (CSS, JavaScript, Images)
# https://docs.djangoproject.com/en/1.9/howto/static-files/

STATIC_URL = '/static/'

STATIC_ROOT = posixpath.join(*(BASE_DIR.split(os.path.sep) + ['static']))
```

Pliki można organizować przy użyciu dowolnej struktury folderów w obszarze *statyczny* , a następnie użyć ścieżek względnych w tym folderze, aby odwołać się do plików. Aby zademonstrować ten proces, następujące kroki umożliwiają dodanie pliku CSS do aplikacji, a następnie użycie tego arkusza stylów w szablonie *index.html* :

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy folder **HelloDjangoApp** w projekcie programu Visual Studio, wybierz polecenie **Dodaj**  >  **Nowy folder**i Nazwij folder `static` .

1. Kliknij prawym przyciskiem myszy folder **statyczny** i wybierz polecenie **Dodaj**  >  **nowy element**. W wyświetlonym oknie dialogowym wybierz szablon **arkusza stylów** , Nazwij plik `site.css` , a następnie wybierz **przycisk OK**. Plik **site. css** zostanie wyświetlony w projekcie i otwarty w edytorze. Struktura folderów powinna wyglądać podobnie do poniższej ilustracji:

    ![Struktura pliku statycznego, jak pokazano w Eksplorator rozwiązań](media/django/step03-static-file-structure.png)

1. Zastąp zawartość pliku *site. css* następującym kodem i Zapisz plik:

    ```css
    .message {
        font-weight: 600;
        color: blue;
    }
    ```

1. Zamień zawartość pliku *templates/HelloDjangoApp/index.html* aplikacji na następujący kod, który zastępuje `<strong>` element użyty w kroku 2, `<span>` który odwołuje się do `message` klasy style. Użycie klasy stylu w ten sposób zapewnia znacznie większą elastyczność w stylu elementu. (Jeśli nie przeniesiono *index.html* do podfolderu w *szablonach* przy użyciu programu vs 2017 15,7 i wcześniejszych, zapoznaj się z tematem [Template namespacing](learn-django-in-visual-studio-step-02-create-an-app.md#template-namespacing) (krok 2-4).

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

1. Uruchom projekt, aby obserwować wyniki. Zatrzymaj serwer po zakończeniu i zatwierdź zmiany w kontroli źródła, jeśli chcesz (zgodnie z opisem w [kroku 2](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control)).

### <a name="question-what-is-the-purpose-of-the--load-staticfiles--tag"></a>Pytanie: jaki jest cel tagu {% Load staticfiles%}?

Odpowiedź: `{% load staticfiles %}` wiersz jest wymagany przed odwołaniem do plików statycznych w elementach takich jak `<head>` i `<body>` . W przykładzie przedstawionym w tej sekcji "staticfiles" odwołuje się do niestandardowego zestawu tagów szablonu Django, co umożliwia użycie `{% static %}` składni w celu odwoływania się do plików statycznych.  Bez `{% load staticfiles %}` , podczas uruchamiania aplikacji zobaczysz wyjątek.

### <a name="question-are-there-any-conventions-for-organizing-static-files"></a>Pytanie: czy istnieją konwencje do organizowania plików statycznych?

Odpowiedź: możesz jednak dodać inne pliki CSS, JavaScript i HTML do folderu *statycznego* . Typowym sposobem organizowania plików statycznych jest tworzenie podfolderów o nazwach *Fonts*, *scripts*i *Content* (dla arkuszy stylów i innych plików). W każdym przypadku Pamiętaj o uwzględnieniu tych folderów w ścieżce względnej do pliku w `{% static %}` odwołaniach.

### <a name="question-can-i-complete-the-same-task-without-using-the--load-staticfiles--tag"></a>Pytanie: Czy można wykonać to samo zadanie bez użycia tagu {% Load staticfiles%}?

Odpowiedź: tak, możesz.

```html
<html>
    <head>
        <title>{{ title }}</title>
        <link rel="stylesheet" type="text/css" href="../../static/site.css" />
    </head>
    <body>
        <span class="message">{{ message }}</span>{{ content }}
    </body>
</html>
```

## <a name="step-3-3-add-a-page-to-the-app"></a>Krok 3-3: Dodawanie strony do aplikacji

Dodanie innej strony do aplikacji oznacza następujące kwestie:

- Dodaj funkcję języka Python, która definiuje widok.
- Dodaj szablon dla znacznika strony.
- Dodaj wymagane Routing do pliku *URLs.py* projektu Django.

Poniższe kroki umożliwiają dodanie strony "informacje" do projektu "HelloDjangoApp" i linków do tej strony ze strony głównej:

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy folder **templates/HelloDjangoApp** , wybierz polecenie **Dodaj**  >  **nowy element**, wybierz szablon elementu **strony HTML** , Nazwij plik `about.html` , a następnie wybierz **przycisk OK**.

    > [!Tip]
    > Jeśli polecenie **nowy element** nie pojawia się w menu **Dodaj** , upewnij się, że serwer został zatrzymany, aby program Visual Studio wyzamykał tryb debugowania.

1. Zastąp zawartość *about.html* następującym znacznikiem (w kroku 3-4 zostanie zastąpione łącze bezpośrednie do strony głównej z prostym paskiem nawigacyjnym):

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

1. Otwórz plik *views.py* aplikacji i Dodaj funkcję o nazwie `about` , która używa szablonu:

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

1. Otwórz plik *URLs.py* projektu Django i Dodaj następujący wiersz do `urlPatterns` tablicy:

    ```python
    url(r'^about$', HelloDjangoApp.views.about, name='about'),
    ```

1. Otwórz plik *templates/HelloDjangoApp/index.html* i Dodaj następujący wiersz poniżej `<body>` elementu, aby utworzyć link do strony informacje (ponownie Zastąp ten link paskiem nawigacyjnym w kroku 3-4):

    ```html
    <div><a href="about">About</a></div>
    ```

1. **Zapisz wszystkie**pliki przy użyciu  >  polecenia**Zapisz wszystko** menu lub po prostu naciśnij klawisz **Ctrl** + **SHIFT** + **S**. (Technicznie ten krok nie jest wymagany, ponieważ uruchomienie projektu w programie Visual Studio powoduje automatyczne zapisanie plików. Jednak dobrym poleceniem jest poznanie!)

1. Uruchom projekt, aby obserwować wyniki i sprawdzić nawigację między stronami. Po zakończeniu zamknij serwer.

### <a name="question-i-tried-using-index-for-the-link-to-the-home-page-but-it-didnt-work-why"></a>Pytanie: podjęto próbę użycia "index" linku do strony głównej, ale nie zadziałało. Dlaczego?

Odpowiedź: Mimo że funkcja widoku w *views.py* ma nazwę `index` , wzorce routingu adresów URL w pliku *URLs.py* projektu Django nie zawierają wyrażenia regularnego zgodnego z ciągiem "index". Aby dopasować ten ciąg, należy dodać kolejny wpis do wzorca `^index$` .

Jak pokazano w następnej sekcji, lepiej jest użyć `{% url '<pattern_name>' %}` znacznika w szablonie strony, aby odwołać się do *nazwy* wzorca. w takim przypadku Django tworzy prawidłowy adres URL. Na przykład Zastąp ciąg `<div><a href="home">Home</a></div>` w *about.html* `<div><a href="{% url 'index' %}">Home</a></div>` . Użycie "index" działa tutaj, ponieważ pierwszy wzorzec adresu URL w *URLs.py* to, w rzeczywistości, o nazwie "index" (na mocy `name='index'` argumentu). Możesz również użyć "Home", aby odwołać się do drugiego wzorca.

## <a name="step-3-4-use-template-inheritance-to-create-a-header-and-nav-bar"></a>Krok 3-4: Użyj dziedziczenia szablonu, aby utworzyć nagłówek i pasek nawigacyjny

Zamiast mieć jawne linki nawigacyjne na każdej stronie, nowoczesne aplikacje sieci Web zwykle używają nagłówka znakowania i paska nawigacyjnego, który zawiera najważniejsze linki stron, menu podręczne i tak dalej. Aby upewnić się, że nagłówek i pasek nawigacyjny są takie same na wszystkich stronach, ale nie chcesz powtarzać tego samego kodu w każdym szablonie strony. Zamiast tego chcesz zdefiniować wspólne części wszystkich stron w jednym miejscu.

System tworzenia szablonów Django zapewnia dwa środki do wielokrotnego użycia określonych elementów w wielu szablonach: obejmuje i dziedziczenie.

- *Obejmuje* inne szablony stron, które są wstawiane w konkretnym miejscu w szablonie odwołującym przy użyciu składni `{% include <template_path> %}` . Możesz również użyć zmiennej, jeśli chcesz zmienić ścieżkę dynamicznie w kodzie. Dołączenia są zwykle używane w treści strony do ściągania szablonu udostępnionego w określonej lokalizacji na stronie.

- *Dziedziczenie* używa na `{% extends <template_path> %}` początku szablonu strony, aby określić współużytkowany szablon podstawowy, na którym zostanie utworzony szablon odwołujący się. Dziedziczenie jest często używane do definiowania współużytkowanego układu, paska nawigacyjnego i innych struktur dla stron aplikacji, takich jak szablony odwołujące się potrzebują tylko dodawania lub modyfikowania określonych obszarów szablonu podstawowego o nazwie *Blocks*.

W obu przypadkach `<template_path>` jest względna w stosunku do folderu *szablonów* aplikacji ( `../` lub `./` są również dozwolone).

Wyznacza szablonu podstawowego blokuje używanie `{% block <block_name> %}` tagów i `{% endblock %}` . Jeśli szablon, który odwołuje się, używa tagów o tej samej nazwie bloku, jego zawartość bloku przesłania element szablonu podstawowego.

W poniższych krokach przedstawiono dziedziczenie:

1. W folderze *Szablony/HelloDjangoApp* aplikacji Utwórz nowy plik HTML (za pomocą **Add**  >  menu kontekstowego Dodaj**nowy element** lub **Dodaj**  >  **stronę HTML**) o nazwie *layout.html*i Zastąp jego zawartość następującym znacznikiem:. Można zobaczyć, że ten szablon zawiera blok o nazwie "Content", który ma zostać zastąpiony przez strony odwołujące:

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

1. Zmodyfikuj szablon */HelloDjangoApp/index.html* , aby odwołać się do szablonu bazowego i zastąpić blok zawartości. Można zobaczyć, że za pomocą dziedziczenia, ten szablon stanie się prosty:

    ```html
    {% extends "HelloDjangoApp/layout.html" %}
    {% block content %}
    <span class="message">{{ message }}</span>{{ content }}
    {% endblock %}
    ```

1. Zmodyfikuj szablon */HelloDjangoApp/about.html* , aby odwoływać się również do szablonu podstawowego i zastąpić blok zawartości:

    ```html
    {% extends "HelloDjangoApp/layout.html" %}
    {% block content %}
    {{ content }}
    {% endblock %}
    ```

1. Uruchom serwer, aby obserwować wyniki. Po zakończeniu zamknij serwer.

    ![Uruchomiona aplikacja wyświetlająca pasek nawigacyjny](media/django/step03-nav-bar.png)

1. Ze względu na to, że wprowadzono znaczące zmiany w aplikacji, jest to dobry moment na [zatwierdzenie zmian w kontroli źródła](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control).

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Użyj szablonu projektu sieci Web w pełnym Django](learn-django-in-visual-studio-step-04-full-django-project-template.md)

## <a name="go-deeper"></a>Przejdź głębiej

- [Wdróż aplikację sieci Web w usłudze Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [Pisanie pierwszej aplikacji Django, część 3 (widoki)](https://docs.djangoproject.com/en/2.0/intro/tutorial03/) (docs.djangoproject.com)
- Aby uzyskać więcej możliwości szablonów Django, takich jak przepływ sterowania, zobacz [Django Template Language](https://docs.djangoproject.com/en/2.0/ref/templates/language/) (docs.djangoproject.com)
- Aby uzyskać szczegółowe informacje na temat używania `{% url %}` znacznika, zobacz [adres URL](https://docs.djangoproject.com/en/2.0/ref/templates/builtins/#url) w [wbudowanych tagach szablonu i filtry dla Django szablonów](https://docs.djangoproject.com/en/2.0/ref/templates/builtins/) (docs.djangoproject.com).
- Kod źródłowy samouczka w witrynie GitHub: [Microsoft/Python-Sample-vs-Learning-Django](https://github.com/Microsoft/python-sample-vs-learning-django)

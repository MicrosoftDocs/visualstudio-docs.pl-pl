---
title: Samouczek Django w programie Visual Studio krok 4, szablon projektu sieci Web
titleSuffix: ''
description: Przewodnik po Django podstawy w kontekście projektów programu Visual Studio, w tym funkcje udostępniane przez szablon projektu sieci Web Django.
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 3c0a0f0f4e009d689a69e840b31281e65bc5a0e2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942558"
---
# <a name="step-4-use-the-full-django-web-project-template"></a>Krok 4. Korzystanie z szablonu pełnego projektu sieci Web Django

**Poprzedni krok: [Obsługiwanie plików statycznych, dodawanie stron i używanie dziedziczenia szablonów](learn-django-in-visual-studio-step-03-serve-static-files-and-add-pages.md)**

Teraz, gdy znasz podstawowe informacje o usłudze Django, tworząc aplikację w szablonie "pusty Django projekt sieci Web" w programie Visual Studio, można łatwo zrozumieć aplikację, która jest tworzona przez szablon "Django Web Project".

W tym kroku:

> [!div class="checklist"]
> - Utwórz kompletną aplikację sieci Web Django przy użyciu szablonu "Django Project Web" i Przeanalizuj strukturę projektu (krok 4-1)
> - Zapoznaj się z widokami i szablonami stron utworzonymi przez szablon projektu, które składają się z trzech stron, które dziedziczą z szablonu strony podstawowej i które wykorzystują statyczne biblioteki JavaScript, takie jak jQuery i Bootstrap (krok 4-2).
> - Opis routingu URL dostarczonego przez szablon (krok 4-3)

Szablon zawiera również podstawowe uwierzytelnianie, które jest omówione w kroku 5.

## <a name="step-4-1-create-a-project-from-the-template"></a>Krok 4-1: Tworzenie projektu na podstawie szablonu

1. W programie Visual Studio przejdź do **Eksplorator rozwiązań**, kliknij prawym przyciskiem myszy rozwiązanie **LearningDjango** utworzone wcześniej w tym samouczku, a następnie wybierz pozycję **Dodaj**  >  **Nowy projekt**. (Alternatywnie, jeśli chcesz użyć nowego rozwiązania, wybierz pozycję **plik**  >  **Nowe**  >  W zamian **projekt** ).

1. W oknie dialogowym Nowy projekt Wyszukaj i wybierz szablon **projektu sieci Web Django** , wywołaj projekt "DjangoWeb", a następnie wybierz **przycisk OK**.

1. Ponieważ szablon ponownie zawiera plik *requirements.txt* , program Visual Studio pyta, gdzie zainstalować te zależności. Wybierz opcję, **Zainstaluj w środowisku wirtualnym**, a następnie w oknie dialogowym **Dodawanie środowiska wirtualnego** wybierz pozycję **Utwórz** , aby zaakceptować ustawienia domyślne.

1. Po zakończeniu konfigurowania środowiska wirtualnego przez program Visual Studio postępuj zgodnie z instrukcjami wyświetlanymi w *readme.html* , aby utworzyć Django administratora (czyli administratora). Po prostu kliknij prawym przyciskiem myszy projekt programu Visual Studio i wybierz polecenie **Python**  >  **Django Create administratora** , a następnie postępuj zgodnie z instrukcjami. Upewnij się, że nazwa użytkownika i hasło są rejestrowane podczas korzystania z funkcji uwierzytelniania aplikacji.

1. Ustaw projekt **DjangoWeb** jako domyślny dla rozwiązania Visual Studio, klikając prawym przyciskiem myszy ten projekt w **Eksplorator rozwiązań** i wybierając pozycję **Ustaw jako projekt startowy**. Projekt startowy, który jest wyświetlany pogrubiony, jest uruchamiany po uruchomieniu debugera.

    ![Eksplorator rozwiązań pokazujący projekt DjangoWeb jako projekt startowy](media/django/step04-second-project-in-solution-set-as-startup-project.png)

1. Wybierz pozycję **Debuguj**  >  **Rozpocznij debugowanie** (**F5**) lub użyj przycisku **serwer sieci Web** na pasku narzędzi, aby uruchomić serwer:

    ![Przycisk paska narzędzi uruchamiania serwera sieci Web w programie Visual Studio](media/django/run-web-server-toolbar-button.png)

1. Aplikacja utworzona przez szablon ma trzy strony, Strona główna, informacje i kontakt, które są przełączane między przy użyciu paska nawigacyjnego. Poświęć minutę lub dwie, aby przeanalizować różne części aplikacji. Aby uwierzytelnić się w aplikacji za pomocą polecenia **Zaloguj** , użyj wcześniej utworzonych poświadczeń administratora.

    ![Pełny widok przeglądarki aplikacji sieci Web Django](media/django/step04-full-app-desktop-view.png)

1. Aplikacja utworzona przez szablon "Django Web Project" używa narzędzia Bootstrap do dynamicznego układu, który obsługuje czynniki formularzy mobilnych. Aby wyświetlić ten czas odpowiedzi, Zmień rozmiar przeglądarki na wąski widok, aby zawartość była renderowana w pionie, a na pasku nawigacyjnym zostanie wyświetlona ikona menu:

    ![Widok Mobile (wąski) aplikacji projektu sieci Web Django](media/django/step04-full-app-mobile-view.png)

1. Możesz pozostawić aplikację działającą dla następujących sekcji.

    Jeśli chcesz zatrzymać aplikację i [zatwierdzić zmiany w kontroli źródła](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control), najpierw Otwórz stronę **zmiany** w **Team Explorer**, kliknij prawym przyciskiem myszy folder dla środowiska wirtualnego (prawdopodobnie **ENV**), a następnie wybierz polecenie **Ignoruj te elementy lokalne**.

### <a name="examine-what-the-template-creates"></a>Sprawdzanie, co tworzy szablon

Na najszerszym poziomie szablon "projekt sieci Web Django" tworzy następującą strukturę:

- Pliki w folderze głównym projektu:
  - *manage.py*, Django narzędzia administracyjne.
  - *DB. sqlite3*— domyślna baza danych programu SQLite.
  - *requirements.txt* zawierający zależność od Django 1. x.
  - *readme.html*, plik, który jest wyświetlany w programie Visual Studio po utworzeniu projektu. Jak wskazano w poprzedniej sekcji, postępuj zgodnie z instrukcjami w tym miejscu, aby utworzyć konto administratora aplikacji.
- Folder *App* zawiera wszystkie pliki aplikacji, w tym widoki, modele, testy, formularze, szablony i pliki statyczne (zobacz krok 4-2). Zwykle nazwę tego folderu można zmienić, aby użyć bardziej charakterystycznej nazwy aplikacji.
- Folder *DjangoWeb* (Django Project) zawiera typowe pliki projektu Django: *\_ \_ init \_ \_ . PR*, *Settings.py*, *URLs.py* i *WSGI.py*. Przy użyciu szablonu projektu *Settings.py* jest już skonfigurowany dla aplikacji i pliku bazy danych, a *URLs.py* jest już skonfigurowana za pomocą tras do wszystkich stron aplikacji, w tym formularza logowania.

### <a name="question-is-it-possible-to-share-a-virtual-environment-between-visual-studio-projects"></a>Pytanie: czy jest możliwe udostępnianie środowiska wirtualnego między projektami programu Visual Studio?

Odpowiedź: tak, ale należy to zrobić, korzystając z świadomości, że różne projekty mogą korzystać z różnych pakietów w miarę upływu czasu, dlatego udostępnione środowisko wirtualne musi zawierać wszystkie pakiety dla wszystkich projektów, które go używają.

Niemniej jednak, aby użyć istniejącego środowiska wirtualnego, wykonaj następujące czynności:

1. Po wyświetleniu monitu o zainstalowanie zależności w programie Visual Studio wybierz opcję **zainstaluję je samodzielnie** .
1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy węzeł **środowiska Python** i wybierz polecenie **Dodaj istniejące środowisko wirtualne**.
1. Przejdź do folderu zawierającego środowisko wirtualne i wybierz go, a następnie wybierz **przycisk OK**.

## <a name="step-4-2-understand-the-views-and-page-templates-created-by-the-project-template"></a>Krok 4-2: informacje o widokach i szablonach stron utworzonych przez szablon projektu

Po uruchomieniu projektu aplikacja zawiera trzy widoki: Home, about i Contact. Kod dla tych widoków można znaleźć w folderze *aplikacji/widoków* . Każda funkcja widoku po prostu wywołuje `django.shortcuts.render` ścieżkę do szablonu i obiektu prostego słownika. Na przykład strona informacje jest obsługiwana przez `about` funkcję:

```python
def about(request):
    """Renders the about page."""
    assert isinstance(request, HttpRequest)
    return render(
        request,
        'app/about.html',
        {
            'title':'About',
            'message':'Your application description page.',
            'year':datetime.now().year,
        }
    )
```

Szablony znajdują się w folderze *Szablony/aplikacje* aplikacji (a zazwyczaj chcesz zmienić nazwę *aplikacji* na nazwa aplikacji rzeczywistej). Szablon podstawowy, *layout.html*, jest najbardziej obszerny. Odnosi się do wszystkich niezbędnych plików statycznych (JavaScript i CSS), definiuje blok o nazwie "Content", który przesłonił inne strony i udostępnia inny blok o nazwie "Scripts" (skrypty). Następujące fragmenty z adnotacjami z *layout.html* pokazują następujące obszary:

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />

    <!-- Define a viewport for Bootstrap's responsive rendering -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{{ title }} - My Django Application</title>

    {% load staticfiles %}
    <link rel="stylesheet" type="text/css" href="{% static 'app/content/bootstrap.min.css' %}" />
    <link rel="stylesheet" type="text/css" href="{% static 'app/content/site.css' %}" />
    <script src="{% static 'app/scripts/modernizr-2.6.2.js' %}"></script>
</head>
<body>
    <!-- Navbar omitted -->

    <div class="container body-content">

<!-- "content" block that pages are expected to override -->
{% block content %}{% endblock %}
        <hr/>
        <footer>
            <p>&copy; {{ year }} - My Django Application</p>
        </footer>
    </div>

<!-- Additional scripts; use the "scripts" block to add page-specific scripts.  -->
    <script src="{% static 'app/scripts/jquery-1.10.2.js' %}"></script>
    <script src="{% static 'app/scripts/bootstrap.js' %}"></script>
    <script src="{% static 'app/scripts/respond.js' %}"></script>
{% block scripts %}{% endblock %}

</body>
</html>
```

Szablony poszczególnych stron, *about.html*, *contact.html* i *index.html*, każdy rozszerzy szablon podstawowy *layout.html*. *about.html* jest najprostszym i zawierającym `{% extends %}` `{% block content %}` znaczniki i:

```html
{% extends "app/layout.html" %}

{% block content %}

<h2>{{ title }}.</h2>
<h3>{{ message }}</h3>

<p>Use this area to provide additional information.</p>

{% endblock %}
```

*index.html* i *contact.html* używają tej samej struktury i udostępniają zawartość dłuższa w bloku "Content" (zawartość).

W folderze *templates/App* jest również czwarta strona *login.html*, wraz z *loginpartial.html* , które zostały wprowadzone do *layout.html* przy użyciu `{% include %}` . Te pliki szablonów są omówione w kroku 5 podczas uwierzytelniania.

### <a name="question-can--block--and--endblock--be-indented-in-the-django-page-template"></a>Pytanie: może {% Block%} i {% endblock%} mieć wcięcia w szablonie strony Django?

Odpowiedź: tak, szablony stron Django działają prawidłowo w przypadku wcięć tagów bloków, które mogą być wyrównane do ich odpowiednich elementów nadrzędnych. Nie są to wcięcia w szablonach stron wygenerowanych przez szablon projektu programu Visual Studio, dzięki czemu można jasno zobaczyć, gdzie są umieszczone.

## <a name="step-4-3-understand-the-url-routing-created-by-the-template"></a>Krok 4-3: Omówienie routingu URL utworzonego przez szablon

Plik *URLs.py* projektu Django utworzony przez szablon "Django Web Project" zawiera następujący kod:

```python
from datetime import datetime
from django.conf.urls import url
import django.contrib.auth.views

import app.forms
import app.views

urlpatterns = [
    url(r'^$', app.views.home, name='home'),
    url(r'^contact$', app.views.contact, name='contact'),
    url(r'^about$', app.views.about, name='about'),
    url(r'^login/$',
        django.contrib.auth.views.login,
        {
            'template_name': 'app/login.html',
            'authentication_form': app.forms.BootstrapAuthenticationForm,
            'extra_context':
            {
                'title': 'Log in',
                'year': datetime.now().year,
            }
        },
        name='login'),
    url(r'^logout$',
        django.contrib.auth.views.logout,
        {
            'next_page': '/',
        },
        name='logout'),
]
```

Pierwsze trzy wzorce URL są mapowane bezpośrednio do `home` widoków, `contact` i `about` w pliku *views.py* aplikacji. Wzorce `^login/$` i `^logout$` , z drugiej strony, używają wbudowanych widoków Django zamiast widoków zdefiniowanych przez aplikację. Wywołania `url` metody zawierają również dodatkowe dane umożliwiające dostosowanie widoku. Krok 5 eksploruje te wywołania.

### <a name="question-in-the-project-i-created-why-does-the-about-url-pattern-uses-about-instead-of-about-as-shown-here"></a>Pytanie: w utworzonym przez siebie projekcie, dlaczego wzorzec adresu URL "informacje" używa "^ about" zamiast "^ about $", jak pokazano tutaj?

Odpowiedź: brak końcowego elementu "$" w wyrażeniu regularnym był prostym nadzorem w wielu wersjach szablonu projektu. Wzorzec adresu URL doskonale sprawdza się w przypadku strony o nazwie "informacje", ale bez końcowego "$" wzorzec adresu URL jest również zgodny z adresami URL, takimi jak "about = Django", "about09876", "aboutoflaughter" i tak dalej. Na końcu przedstawiono znak "$", aby utworzyć wzorzec adresu URL, który jest zgodny *tylko* z "informacjami".

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Uwierzytelnianie użytkowników w Django](learn-django-in-visual-studio-step-05-django-authentication.md)

## <a name="go-deeper"></a>Przejdź głębiej

- [Wdróż aplikację sieci Web w usłudze Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [Pisanie pierwszej aplikacji Django, część 4 — formularze i widoki ogólne](https://docs.djangoproject.com/en/2.0/intro/tutorial04/) (docs.djangoproject.com)
- Kod źródłowy samouczka w witrynie GitHub: [Microsoft/Python-Sample-vs-Learning-Django](https://github.com/Microsoft/python-sample-vs-learning-django)

---
title: Dowiedz się samouczek Django w programie Visual Studio krok 4, szablon projektu sieci Web
titleSuffix: ''
description: Przewodnik po podstawach Django w kontekście projektów programu Visual Studio, w szczególności funkcje dostarczone przez szablon Django Web Project.
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: c778d830b20797962306700a5af938eb3a3bb142
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "62961700"
---
# <a name="step-4-use-the-full-django-web-project-template"></a>Krok 4: Użyj pełnego szablonu Django Web Project

**Poprzedni krok: [Obsługa plików statycznych, dodawanie stron i używanie dziedziczenia szablonów](learn-django-in-visual-studio-step-03-serve-static-files-and-add-pages.md)**

Teraz, gdy już zbadać podstawy Django, tworząc aplikację na "Blank Django Web Project" szablon w Programie Visual Studio, można łatwo zrozumieć pełniejszą aplikację, która jest produkowana przez szablon "Django Web Project".

W tym kroku teraz:

> [!div class="checklist"]
> - Tworzenie pełniejszej aplikacji internetowej Django przy użyciu szablonu "Django Web Project" i badanie struktury projektu (krok 4-1)
> - Zrozumienie widoków i szablonów stron utworzonych przez szablon projektu, które składają się z trzech stron, które dziedziczą z szablonu strony podstawowej i które wykorzystują statyczne biblioteki JavaScript, takie jak jQuery i Bootstrap (krok 4-2)
> - Opis routingu adresów URL dostarczonych przez szablon (krok 4-3)

Szablon zapewnia również uwierzytelnianie podstawowe, które jest omówione w kroku 5.

## <a name="step-4-1-create-a-project-from-the-template"></a>Krok 4-1: Tworzenie projektu na podstawie szablonu

1. W programie Visual Studio przejdź do **programu Solution Explorer**, kliknij prawym przyciskiem myszy rozwiązanie **LearningDjango** utworzone wcześniej w tym samouczku i wybierz pozycję **Dodaj** > **nowy projekt**. (Alternatywnie, jeśli chcesz użyć nowego rozwiązania, wybierz **pozycję Plik** > **nowego** > **projektu).**

1. W nowym oknie dialogowym projektu wyszukaj i wybierz szablon **Django Web Project,** zadzwoń do projektu "DjangoWeb" i wybierz **PRZYCISK OK**.

1. Ponieważ szablon ponownie zawiera plik *requirements.txt,* visual studio pyta, gdzie zainstalować te zależności. Wybierz opcję **Zainstaluj w środowisku wirtualnym,** a następnie w oknie dialogowym **Dodaj środowisko wirtualne** wybierz pozycję **Utwórz,** aby zaakceptować wartości domyślne.

1. Po zakończeniu konfigurowania środowiska wirtualnego w programie Visual Studio postępuj zgodnie z instrukcjami wyświetlanymi w pliku *readme.html,* aby utworzyć superużytnika Django (czyli administratora). Wystarczy kliknąć prawym przyciskiem myszy projekt programu Visual Studio i wybrać polecenie **Python** > **Django Create Superuser,** a następnie postępuj zgodnie z instrukcjami. Pamiętaj, aby rejestrować swoją nazwę użytkownika i hasło podczas korzystania z funkcji uwierzytelniania aplikacji.

1. Ustaw projekt **DjangoWeb** jako domyślny dla rozwiązania programu Visual Studio, klikając prawym przyciskiem myszy ten projekt w **Eksploratorze rozwiązań** i wybierając **pozycję Ustaw jako projekt startowy.** Projekt uruchamiania, który jest wyświetlany pogrubioną czcionką, jest tym, co jest uruchamiane po uruchomieniu debugera.

    ![Eksplorator rozwiązań przedstawiający projekt DjangoWeb jako projekt startowy](media/django/step04-second-project-in-solution-set-as-startup-project.png)

1. Wybierz **debugowanie** > **rozpocznij debugowanie** **(F5)** lub użyj przycisku Serwera sieci **Web** na pasku narzędzi, aby uruchomić serwer:

    ![Uruchamianie przycisku paska narzędzi serwera sieci Web w programie Visual Studio](media/django/run-web-server-toolbar-button.png)

1. Aplikacja utworzona przez szablon ma trzy strony: Strona główna, Informacje i Kontakt, które można nawigować między za pomocą paska nawigacji. Poświęć minutę lub dwie, aby zbadać różne części aplikacji. Aby uwierzytelnić się za pomocą aplikacji za pomocą polecenia **Zaloguj,** użyj poświadczeń administratora utworzonych wcześniej.

    ![Pełny widok przeglądarki aplikacji Django Web Project](media/django/step04-full-app-desktop-view.png)

1. Aplikacja stworzona przez szablon "Django Web Project" używa Bootstrap do elastycznego układu, który pasuje do mobilnych rozmiarów. Aby zobaczyć tę responsywność, zmienić rozmiar przeglądarki na wąski widok, tak aby zawartość była renderowana w pionie, a pasek nawigacyjny zamienia się w ikonę menu:

    ![Mobilny (wąski) widok aplikacji Django Web Project](media/django/step04-full-app-mobile-view.png)

1. Możesz pozostawić aplikację z uruchomiona dla sekcji, które należy wykonać.

    Jeśli chcesz zatrzymać aplikację i [zatwierdzić zmiany w formancie źródłowym,](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control)najpierw otwórz stronę **Zmiany** w **Eksploratorze zespołu,** kliknij prawym przyciskiem myszy folder środowiska wirtualnego (prawdopodobnie **env)** i wybierz pozycję **Ignoruj te elementy lokalne**.

### <a name="examine-what-the-template-creates"></a>Sprawdzanie, co tworzy szablon

Na najszerszym poziomie szablon "Django Web Project" tworzy następującą strukturę:

- Pliki w katalogu głównym projektu:
  - *manage.py*, narzędzie administracyjne Django.
  - *db.sqlite3*, domyślna baza danych SQLite.
  - *requirements.txt* zawierający zależność od Django 1.x.
  - *readme.html*, plik, który jest wyświetlany w programie Visual Studio po utworzeniu projektu. Jak wspomniano w poprzedniej sekcji, postępuj zgodnie z instrukcjami tutaj, aby utworzyć konto superużyt (administrator) dla aplikacji.
- Folder *aplikacji* zawiera wszystkie pliki aplikacji, w tym widoki, modele, testy, formularze, szablony i pliki statyczne (patrz krok 4-2). Zazwyczaj zmieniasz nazwę tego folderu, aby użyć bardziej charakterystycznej nazwy aplikacji.
- Folder *DjangoWeb* (projekt Django) zawiera typowe pliki projektu Django: * \_ \_\_\_init .py*, *settings.py*, *urls.py*i *wsgi.py*. Korzystając z szablonu projektu, *settings.py* jest już skonfigurowany dla aplikacji i pliku bazy danych, a *urls.py* jest już skonfigurowany z trasami do wszystkich stron aplikacji, w tym formularza logowania.

### <a name="question-is-it-possible-to-share-a-virtual-environment-between-visual-studio-projects"></a>Pytanie: Czy można udostępniać środowisko wirtualne między projektami programu Visual Studio?

Odpowiedź: Tak, ale zrób to ze świadomością, że różne projekty mogą używać różnych pakietów w czasie, a zatem udostępnione środowisko wirtualne musi zawierać wszystkie pakiety dla wszystkich projektów, które go używają.

Niemniej jednak, aby użyć istniejącego środowiska wirtualnego, wykonaj następujące czynności:

1. Po wyświetleniu monitu o zainstalowanie zależności w programie Visual Studio wybierz opcję **Zainstaluję je samodzielnie.**
1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy węzeł **Środowiska języka Python** i wybierz polecenie Dodaj istniejące środowisko **wirtualne**.
1. Przejdź do folderu zawierającego środowisko wirtualne i wybierz go, a następnie wybierz przycisk **OK**.

## <a name="step-4-2-understand-the-views-and-page-templates-created-by-the-project-template"></a>Krok 4-2: Zrozumienie widoków i szablonów stron utworzonych przez szablon projektu

Jak obserwować po uruchomieniu projektu, aplikacja zawiera trzy widoki: Strona główna, Informacje i Kontakt. Kod tych widoków znajduje się w folderze *aplikacja/widoki.* Każda funkcja widoku `django.shortcuts.render` po prostu wywołuje ze ścieżką do szablonu i prostego obiektu słownika. Na przykład strona Informacje jest obsługiwana przez `about` funkcję:

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

Szablony znajdują się w *folderze szablonów/aplikacji* aplikacji (zazwyczaj chcesz zmienić nazwę *aplikacji* na nazwę prawdziwej aplikacji). Szablon podstawowy, *layout.html*, jest najbardziej obszerny. Odnosi się do wszystkich niezbędnych plików statycznych (JavaScript i CSS), definiuje blok o nazwie "zawartość", który inne strony zastępują, i udostępnia inny blok o nazwie "skrypty". Następujące fragmenty z adnotacjami z *layout.html* przedstawiają następujące konkretne obszary:

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

Poszczególne szablony stron, *about.html*, *contact.html*i *index.html*, każdy rozszerza szablon podstawowy *layout.html*. *about.html* jest najprostszy i `{% extends %}` `{% block content %}` pokazuje i tagi:

```html
{% extends "app/layout.html" %}

{% block content %}

<h2>{{ title }}.</h2>
<h3>{{ message }}</h3>

<p>Use this area to provide additional information.</p>

{% endblock %}
```

*index.html* i *contact.html* używają tej samej struktury i zapewniają dłuższą zawartość w bloku "content".

W *szablonach /* folderze aplikacji jest również czwarta strona *login.html*, wraz z *loginpartial.html,* który jest wniesiona do *layout.html* za pomocą `{% include %}`. Te pliki szablonów są omówione w kroku 5 na uwierzytelnianie.

### <a name="question-can--block--and--endblock--be-indented-in-the-django-page-template"></a>Pytanie: Czy {% bloku %} i {% bloku końcowego %} może być wcięty w szablonie strony Django?

Odpowiedź: Tak, szablony stron Django działają dobrze, jeśli wcięcie tagów blokowych, być może, aby wyrównać je w odpowiednich elementach nadrzędnych. Nie są one wcięci w szablonach stron generowanych przez szablon projektu programu Visual Studio, dzięki czemu można wyraźnie zobaczyć, gdzie są one umieszczone.

## <a name="step-4-3-understand-the-url-routing-created-by-the-template"></a>Krok 4-3: Zrozumienie routingu adresów URL utworzonego przez szablon

Plik *urls.py* projektu Django utworzony przez szablon "Django Web Project" zawiera następujący kod:

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

Pierwsze trzy wzorce adresów URL `home` `contact`są `about` mapowane bezpośrednio do pliku , i widoków w pliku *views.py* aplikacji. Wzorce `^login/$` i `^logout$`, z drugiej strony, używają wbudowanych widoków Django zamiast widoków zdefiniowanych przez aplikację. Wywołania `url` metody zawierają również dodatkowe dane, aby dostosować widok. Krok 5 eksploruje te połączenia.

### <a name="question-in-the-project-i-created-why-does-the-about-url-pattern-uses-about-instead-of-about-as-shown-here"></a>Pytanie: W projekcie, który stworzyłem, dlaczego wzorzec adresu URL "o" używa '^about' zamiast '^about$', jak pokazano tutaj?

Odpowiedź: Brak końcowego "$" w wyrażeniu regularnym był prostym niedopatrzeniem w wielu wersjach szablonu projektu. Wzorzec adresu URL działa idealnie dla strony o nazwie "o", ale bez końcowego "$" wzorzec adresu URL pasuje również do adresów URL takich jak "about=django", "about09876", "aboutoflaughter" i tak dalej. Końcowe "$" jest wyświetlane w tym miejscu, aby utworzyć wzorzec adresu URL, który pasuje *tylko* "o".

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Uwierzytelnianie użytkowników w Django](learn-django-in-visual-studio-step-05-django-authentication.md)

## <a name="go-deeper"></a>Głębiej

- [Wdrażanie aplikacji sieci Web w usłudze Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [Pisanie pierwszej aplikacji Django, część 4 - formularze i ogólne widoki](https://docs.djangoproject.com/en/2.0/intro/tutorial04/) (docs.djangoproject.com)
- Kod źródłowy samouczka na GitHub: [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)

---
title: Poznaj samouczek Django w programie Visual Studio w kroku 4, szablon projektów internetowych
titleSuffix: ''
description: Przewodnik po podstawy Django w kontekście projektów programu Visual Studio, w szczególności funkcji oferowanych przez szablon projektu sieci Web Django.
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
ms.sourcegitcommit: 0e22ead8234b2c4467bcd0dc047b4ac5fb39b977
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59366201"
---
# <a name="step-4-use-the-full-django-web-project-template"></a>Krok 4. Użyj pełnego szablonów projektów internetowych Django

**Poprzedniego kroku: [Obsługa plików statycznych, dodawanie stron i użyć szablonu dziedziczenia](learn-django-in-visual-studio-step-03-serve-static-files-and-add-pages.md)**

Teraz, gdy zostały zbadane podstawy Django, tworząc aplikację od szablonu "Pusty projekt sieci Web Django" w programie Visual Studio, może łatwo zrozumieć pełniejszego aplikacji, który jest wytwarzany przez szablon "Projekt sieci Web Django".

W tym kroku możesz teraz:

> [!div class="checklist"]
> - Tworzenie pełniejszego aplikacji sieci web Django przy użyciu szablonu "Projekt sieci Web Django" i sprawdź struktury projektu (krok 4 - 1)
> - Zapoznać się z widoków i szablonów strony utworzone przez szablon projektu, które składają się z trzech stron, które dziedziczą z szablonem strony podstawowej i że stosuje statycznej biblioteki JavaScript, takich jak jQuery i Bootstrap (krok 2 z 4)
> - Omówienie routingu adresów URL podany przez szablon (krok 4-3)

Szablon zawiera również uwierzytelnianie podstawowe, co zostało omówione w kroku 5.

## <a name="step-4-1-create-a-project-from-the-template"></a>Krok 1 z 4 Tworzenie projektu z szablonu

1. W programie Visual Studio, przejdź do **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **LearningDjango** rozwiązanie utworzone we wcześniejszej części tego samouczka, a następnie wybierz pozycję **Dodaj**  >   **Nowy projekt**. (, Jeśli chcesz użyć nowego rozwiązania, wybierz **pliku** > **New** > **projektu** zamiast.)

1. W oknie dialogowym Nowy projekt wyszukiwanie i wybieranie **projektu sieci Web Django** szablonu, wywołaj projektu "DjangoWeb", a następnie wybierz pozycję **OK**.

1. Ponieważ szablon ponownie zawiera *requirements.txt* plików, programu Visual Studio pyta, gdzie zainstalować te zależności. Wybierz opcję, **zainstalować w środowisku wirtualnym**, a następnie w **Dodawanie środowiska wirtualnego** okna dialogowego wybierz **Utwórz** aby zaakceptować wartości domyślne.

1. Gdy program Visual Studio zakończy się skonfigurowanie środowiska wirtualnego, postępuj zgodnie z instrukcjami wyświetlonych *readme.html* utworzyć Django użytkownika administratora (administrator). Po prostu kliknij prawym przyciskiem myszy projekt programu Visual Studio i wybierz **Python** > **Django — Tworzenie administratora** polecenia, a następnie postępuj zgodnie z monitami. Upewnij się zarejestrować nazwę użytkownika i hasło, ponieważ używane podczas wykonywania funkcji uwierzytelniania aplikacji.

1. Ustaw **DjangoWeb** projektu jako domyślny dla rozwiązania Visual Studio przez kliknięcie prawym przyciskiem myszy tego projektu w **Eksploratora rozwiązań** i wybierając polecenie **Ustaw jako projekt startowy** . Projekt startowy, który jest pokazany w pogrubienie, to co program jest uruchamiany w przypadku, gdy uruchamiasz debuger.

    ![Eksploratora rozwiązań przedstawiający DjangoWeb projekt jako projekt startowy](media/django/step04-second-project-in-solution-set-as-startup-project.png)

1. Wybierz **debugowania** > **Rozpocznij debugowanie** (**F5**) lub użyj **serwera sieci Web** przycisk na pasku narzędzi, aby uruchomić serwer:

    ![Uruchamianie serwera sieci web przycisku paska narzędzi w programie Visual Studio](media/django/run-web-server-toolbar-button.png)

1. Aplikacja utworzona przez szablon ma trzy strony Strona główna o i skontaktuj się z pomocą, której możesz przechodzić między za pomocą paska nawigacji. Zająć minutę lub dwie zbadać różne części aplikacji. Do uwierzytelniania za pomocą aplikacji za pomocą **Zaloguj** poleceń, użyj utworzonych wcześniej poświadczeń administratora.

    ![Widok pełnej przeglądarki aplikacji projektu sieci Web Django](media/django/step04-full-app-desktop-view.png)

1. Aplikacja utworzona przez szablon "Projekt sieci Web Django" używa ładowania początkowego dla układem dynamicznym, który obsługuje urządzeń przenośnych. Aby wyświetlić ten czas reakcji, zmiana rozmiaru przeglądarki, aby wąskie tak, aby zawartość renderuje w pionie i na pasku nawigacyjnym jest przekształcany ikonę menu:

    ![Mobile (wąskie) widok aplikacji Django Web Project](media/django/step04-full-app-mobile-view.png)

1. Możesz pozostawić aplikacja uruchomiona w kolejnych sekcjach.

    Jeśli chcesz zatrzymać aplikację i [Zatwierdź zmiany do kontroli źródła](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control), najpierw otwórz **zmiany** strony w **Team Explorer**, kliknij prawym przyciskiem myszy folder (środowiska wirtualnego prawdopodobnie **env**) i wybierz **ignorować te elementy lokalne**.

### <a name="examine-what-the-template-creates"></a>Sprawdź ten szablon tworzy

Na poziomie największą szablonu "Projektów internetowych Django" tworzy następującą strukturę:

- Pliki w katalogu głównym projektu:
  - *manage.PY*, narzędzia administracyjnego Django.
  - *DB.sqlite3*, domyślna baza danych SQLite.
  - *Plik Requirements.txt* zawierający zależności Django 1.x.
  - *Readme.HTML*, pliku, który jest wyświetlany w programie Visual Studio po utworzeniu projektu. Jak wspomniano w poprzedniej sekcji, wykonaj poniższe instrukcje, aby utworzyć konto administratora (administrator) dla aplikacji.
- *Aplikacji* folder zawiera wszystkie pliki aplikacji, łącznie z widoków, modele, testy, formularze, szablony i pliki statyczne (zobacz krok 4-2). Zazwyczaj zmiana nazwy tego folderu, aby użyć bardziej wyróżniające nazwy aplikacji.
- *DjangoWeb* folder (Django projekt) zawiera typowe pliki projektu Django:  *\_ \_init\_\_.py*,  *Settings.PY*, *urls.py*, i *wsgi.py*. Za pomocą szablonu projektu *settings.py* została już skonfigurowana dla aplikacji i plik bazy danych i *urls.py* ma już skonfigurowaną trasy do wszystkich stron aplikacji, w tym formularz logowania.

### <a name="question-is-it-possible-to-share-a-virtual-environment-between-visual-studio-projects"></a>Pytanie: Czy jest możliwe udostępnianie środowisku wirtualnym między projektami Visual Studio?

Odpowiedź: Tak, ale to zrobić za pomocą świadomości, że różnych projektów, które mogą używać różnych pakietach wraz z upływem czasu, a w związku z tym udostępnione środowisko wirtualne musi zawierać wszystkie pakiety dla wszystkich projektów, które go używają.

Niemniej jednak aby użyć istniejącego środowiska wirtualnego, należy wykonać następujące czynności:

1. Po wyświetleniu monitu, aby zainstalować zależności w programie Visual Studio, wybierz **I zainstaluje je samodzielnie** opcji.
1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **środowiska Python** a następnie wybierz węzeł **Dodawanie istniejącego środowiska wirtualnego**.
1. Przejdź do i wybierz folder zawierający środowiska wirtualnego, a następnie wybierz **OK**.

## <a name="step-4-2-understand-the-views-and-page-templates-created-by-the-project-template"></a>Krok 2 z 4 Widoki i szablony strony utworzone przez szablon projektu

Jak można zaobserwować, gdy uruchamiasz projekt, ta aplikacja zawiera trzy widoki: Strona główna i skontaktuj się z pomocą. Kod dla tych widoków znajduje się w *aplikacji/widoki* folderu. Każda funkcja widoku po prostu wywołuje widok `django.shortcuts.render` na ścieżkę do szablonu i obiekt słownika prostego. Na przykład na stronie informacje jest obsługiwany przez `about` funkcji:

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

Szablony znajdują się w aplikacji *szablony/aplikacji* folder (i zazwyczaj chcesz zmienić nazwę *aplikacji* do nazwy rzeczywistych aplikacji). Szablon podstawowy *layout.html*, jest najbardziej rozbudowanych. On odnosi się do wszystkich niezbędnych plików statycznych (JavaScript i CSS), definiuje bloku o nazwie "treści" innych stron zastąpienie i udostępnia innego bloku o nazwie "skrypty". Następujące fragmenty z z adnotacjami *layout.html* te określone obszary:

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

Szablony pojedynczej strony *about.html*, *contact.html*, i *index.html*, Rozszerz każdy szablon podstawowy *layout.html*. *About.HTML* to najprostszy i pokazuje `{% extends %}` i `{% block content %}` tagi:

```html
{% extends "app/layout.html" %}

{% block content %}

<h2>{{ title }}.</h2>
<h3>{{ message }}</h3>

<p>Use this area to provide additional information.</p>

{% endblock %}
```

*index.HTML* i *contact.html* Użyj tej samej struktury i podaj dłuższy zawartości w bloku "treści".

W *szablony/aplikacji* folder jest również czwartej stronie *login.html*, wraz z *loginpartial.html* przenoszona do *layout.html*przy użyciu `{% include %}`. Te pliki szablonu są omówione w kroku 5 uwierzytelniania.

### <a name="question-can--block--and--endblock--be-indented-in-the-django-page-template"></a>Pytanie: Może {% block %} i {% endblock %} wcięcia w szablonie strony Django?

Odpowiedź: Szablony stron Django działają tak, prawidłowo, gdy wcięcie znaczników bloku, prawdopodobnie po to, aby dopasować je w ramach ich elementy nadrzędne odpowiednie. Są one wcięty szablony stron wygenerowanych przez szablon projektu Visual Studio, aby wyraźnie zobaczyć, gdzie są umieszczone.

## <a name="step-4-3-understand-the-url-routing-created-by-the-template"></a>Krok 3 z 4 Omówienie routingu adresów URL utworzonej przez szablon

Projekt Django *urls.py* pliku utworzona przez szablon "Projekt sieci Web Django" zawiera następujący kod:

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

Pierwsze trzy wzorce adresów URL mapować bezpośrednio do `home`, `contact`, i `about` widoków w aplikacji *views.py* pliku. Wzorce `^login/$` i `^logout$`, z drugiej strony, zamiast widoki zdefiniowane w aplikacji za pomocą wbudowanych widoków Django. Wywołania `url` metoda również zawierać dodatkowe dane w celu dostosowania wyświetlania. Krok 5 odkrywa te wywołania.

### <a name="question-in-the-project-i-created-why-does-the-about-url-pattern-uses-about-instead-of-about-as-shown-here"></a>Pytanie: W projekcie, utworzono, dlaczego "about" wzorzec adresu URL korzysta z "^ o" zamiast "^ o$" pokazane tutaj?

Odpowiedź: Brak końcowe "$" w wyrażeniu regularnym jest proste nadzoru w wielu wersjach szablonu projektu. Wzorzec adresu URL działa dobrze dla strony o nazwie "about", ale bez końcowych "$" wzorzec adresu URL dopasowuje również adresy URL takich jak "około = django", "about09876", "aboutoflaughter", a tym samym na. Końcowe "$" jest wyświetlany w tym miejscu utworzyć wzorzec adresu URL, który jest zgodny *tylko* "about".

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Uwierzytelnianie użytkowników w Django](learn-django-in-visual-studio-step-05-django-authentication.md)

## <a name="go-deeper"></a>Przejdź dalej

- [Wdrażanie aplikacji sieci web w usłudze Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [Zapisywanie swoją pierwszą aplikację Django, część 4 — formularzy i widoków ogólny](https://docs.djangoproject.com/en/2.0/intro/tutorial04/) (docs.djangoproject.com)
- Kod źródłowy samouczek w witrynie GitHub: [Microsoft/python — przykładowe vs uczenia — django](https://github.com/Microsoft/python-sample-vs-learning-django)

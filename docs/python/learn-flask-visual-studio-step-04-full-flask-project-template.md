---
title: Poznaj samouczek Flask w programie Visual Studio w kroku 4, szablony projektów internetowych
titleSuffix: ''
description: Przewodnik po podstawy Flask w kontekście projektów programu Visual Studio, w szczególności funkcji oferowanych przez Szablony projektu sieci Web Flask i Flask/Jade projektu sieci Web.
ms.date: 01/07/2019
ms.prod: visual-studio-dev15
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 6a179dc2dc8f3851b1b75ca840b55e07e1ff6a30
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54927519"
---
# <a name="step-4-use-the-full-flask-web-project-template"></a>Krok 4. Pełny szablon projektu sieci Web Flask

**Poprzedniego kroku: [Obsługa plików statycznych, dodawanie stron i użyć szablonu dziedziczenia](learn-flask-visual-studio-step-03-serve-static-files-add-pages.md)**

Teraz, gdy zostały zbadane podstawy Flask, tworząc aplikację od szablonu "Pusty projekt aplikacji Flask" w programie Visual Studio, może łatwo zrozumieć pełniejszego aplikacji, które są generowane przez szablon "Projekt sieci Web Flask".

W tym kroku możesz teraz:

> [!div class="checklist"]
> - Tworzenie pełniejszego aplikacji internetowej Flask za pomocą szablonu "Projekt sieci Web Flask" i sprawdź struktury projektu (krok 4 - 1)
> - Zapoznać się z widoków i szablonów strony utworzone przez szablon projektu, które składają się z trzech stron, które dziedziczą z szablonem strony podstawowej i że stosuje statycznej biblioteki JavaScript, takich jak jQuery i Bootstrap (krok 2 z 4)
> - Omówienie routingu adresów URL podany przez szablon (krok 4-3)

Ten artykuł dotyczy również szablon "Projekt sieci Web Flask/Jade", który tworzy aplikację, która jest identyczna jak "Projektu sieci Web Flask" przy użyciu aparatu Jade szablonów zamiast Jinja. Dodatkowe szczegóły są umieszczane na końcu tego artykułu.

## <a name="step-4-1-create-a-project-from-the-template"></a>Krok 1 z 4 Tworzenie projektu z szablonu

1. W programie Visual Studio, przejdź do **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **LearningFlask** rozwiązanie utworzone we wcześniejszej części tego samouczka, a następnie wybierz pozycję **Dodaj**  >   **Nowy projekt**. (, Jeśli chcesz użyć nowego rozwiązania, wybierz **pliku** > **New** > **projektu** zamiast.)

1. W oknie dialogowym Nowy projekt wyszukiwanie i wybieranie **projektu sieci Web Flask** szablonu, wywołaj projektu "FlaskWeb", a następnie wybierz pozycję **OK**.

1. Ponieważ szablon ponownie zawiera *requirements.txt* plików, programu Visual Studio pyta, gdzie zainstalować te zależności. Wybierz opcję, **zainstalować w środowisku wirtualnym**, a następnie w **Dodawanie środowiska wirtualnego** okna dialogowego wybierz **Utwórz** aby zaakceptować wartości domyślne.

1. Gdy program Visual Studio zakończy się skonfigurowanie środowiska wirtualnego, ustaw **FlaskWeb** projektu jako domyślny dla rozwiązania Visual Studio przez kliknięcie prawym przyciskiem myszy tego projektu w **Eksploratora rozwiązań** i Wybieranie **Ustaw jako projekt startowy**. Projekt startowy, który jest pokazany w pogrubienie, to co program jest uruchamiany w przypadku, gdy uruchamiasz debuger.

    ![Eksploratora rozwiązań przedstawiający FlaskWeb projekt jako projekt startowy](media/flask/step04-second-project-in-solution-set-as-startup-project.png)

1. Wybierz **debugowania** > **Rozpocznij debugowanie** (**F5**) lub użyj **serwera sieci Web** przycisk na pasku narzędzi, aby uruchomić serwer:

    ![Uruchamianie serwera sieci web przycisku paska narzędzi w programie Visual Studio](media/flask/run-web-server-toolbar-button.png)

1. Aplikacja utworzona przez szablon ma trzy strony Strona główna o i skontaktuj się z pomocą, której możesz przechodzić między za pomocą paska nawigacji. Zająć minutę lub dwie zbadać różne części aplikacji. Do uwierzytelniania za pomocą aplikacji za pomocą **Zaloguj** poleceń, użyj utworzonych wcześniej poświadczeń administratora.

    ![Wyświetlany w przeglądarce pełny widok aplikacji Flask Web Project](media/flask/step04-full-app-desktop-view.png)

1. Aplikacja utworzona przez szablon "Projekt sieci Web Flask" używa ładowania początkowego dla układem dynamicznym, który obsługuje urządzeń przenośnych. Aby wyświetlić ten czas reakcji, zmiana rozmiaru przeglądarki, aby wąskie tak, aby zawartość renderuje w pionie i na pasku nawigacyjnym jest przekształcany ikonę menu:

    ![Widok aplikacji Flask Web Project Mobile (wąskie)](media/flask/step04-full-app-mobile-view.png)

1. Możesz pozostawić aplikacja uruchomiona w kolejnych sekcjach.

    Jeśli chcesz zatrzymać aplikację i [Zatwierdź zmiany do kontroli źródła](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control), najpierw otwórz **zmiany** strony w **Team Explorer**, kliknij prawym przyciskiem myszy folder (środowiska wirtualnego prawdopodobnie **env**) i wybierz **ignorować te elementy lokalne**.

### <a name="examine-what-the-template-creates"></a>Sprawdź ten szablon tworzy

Szablon "Projekt sieci Web Flask" tworzy strukturę poniżej. Zawartość jest bardzo podobne do utworzonego w poprzednich krokach. Różnica polega na to, że szablon "Projekt sieci Web Flask" zawiera więcej strukturze *statyczne* folderu, ponieważ zawiera jQuery i Bootstrap uzyskać elastyczne środowisko. Szablon dodaje również strony kontaktu. Ogólne po wykonaniu poprzednich kroków w ramach tego samouczka, wszystko — od szablonu powinna być znane.

- Pliki w katalogu głównym projektu:
  - *runserver.PY*, skrypt do uruchomienia aplikacji na serwerze rozwoju.
  - *Plik Requirements.txt* zawierający zależności Flask postaci 0.x.
- *FlaskWeb* folder zawiera wszystkie pliki aplikacji:
  - *\_\_init.PY\_ \_*  oznacza kod aplikacji jako moduł języka Python, tworzy obiekt Flask i importuje widoków aplikacji.
  - *Views.PY* zawiera kod w celu renderowania stron.
  - *Statyczne* folder zawiera podfoldery o nazwach odpowiadających *zawartości* (pliki CSS), *czcionki* (pliki czcionek) i *skrypty* (plików JavaScript).
  - *Szablony* folder zawiera *layout.html* szablon podstawowy wraz z *about.html*, *contact.html*, i  *index.HTML* dla określonych stron każdy rozszerzyć *layout.html*.

### <a name="question-is-it-possible-to-share-a-virtual-environment-between-visual-studio-projects"></a>Pytanie: Czy jest możliwe udostępnianie środowisku wirtualnym między projektami Visual Studio?

Odpowiedź: Tak, ale to zrobić za pomocą świadomości, że różnych projektów, które mogą używać różnych pakietach wraz z upływem czasu, a w związku z tym udostępnione środowisko wirtualne musi zawierać wszystkie pakiety dla wszystkich projektów, które go używają.

Niemniej jednak aby użyć istniejącego środowiska wirtualnego, należy wykonać następujące czynności:

1. Po wyświetleniu monitu, aby zainstalować zależności w programie Visual Studio, wybierz **I zainstaluje je samodzielnie** opcji.
1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **środowiska Python** a następnie wybierz węzeł **Dodawanie istniejącego środowiska wirtualnego**.
1. Przejdź do i wybierz folder zawierający środowiska wirtualnego, a następnie wybierz **OK**.

## <a name="step-4-2-understand-the-views-and-page-templates-created-by-the-project-template"></a>Krok 2 z 4 Widoki i szablony strony utworzone przez szablon projektu

Jak można zaobserwować, gdy uruchamiasz projekt, ta aplikacja zawiera trzy widoki: Strona główna i skontaktuj się z pomocą. Kod dla tych widoków znajduje się w *FlaskWeb/views.py*. Każda funkcja widoku po prostu wywołuje widok `flask.render_template` na ścieżkę do szablonu oraz listy zmiennych argumentów dla wartości, aby zapewnić do szablonu. Na przykład na stronie informacje jest obsługiwany przez `about` — funkcja (których dekoratora zapewnia routing adresów URL):

```python
@app.route('/about')
def about():
    """Renders the about page."""
    return render_template(
        'about.html',
        title='About',
        year=datetime.now().year,
        message='Your application description page.'
    )
```

`home` i `contact` funkcji są niemal identyczne, z podobnych dekoratory i nieco inne argumenty.

Szablony znajdują się w aplikacji *szablony* folderu. Szablon podstawowy *layout.html*, jest najbardziej rozbudowanych. On odnosi się do wszystkich niezbędnych plików statycznych (JavaScript i CSS), definiuje bloku o nazwie "treści" innych stron zastąpienie i udostępnia innego bloku o nazwie "skrypty". Następujące fragmenty z z adnotacjami *layout.html* te określone obszary:

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />

    <!-- Define a viewport for Bootstrap's responsive rendering -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{{ title }} - My Flask Application</title>

    <link rel="stylesheet" type="text/css" href="/static/content/bootstrap.min.css" />
    <link rel="stylesheet" type="text/css" href="/static/content/site.css" />
    <script src="/static/scripts/modernizr-2.6.2.js"></script>
</head>

<body>
    <!-- Navbar omitted -->

    <div class="container body-content">
        <!-- "content" block that pages are expected to override -->
        {% block content %}{% endblock %}
        <hr />
        <footer>
            <p>&copy; {{ year }} - My Flask Application</p>
        </footer>
    </div>

    <!-- Additional scripts; use the "scripts" block to add page-specific scripts.  -->
    <script src="/static/scripts/jquery-1.10.2.js"></script>
    <script src="/static/scripts/bootstrap.js"></script>
    <script src="/static/scripts/respond.js"></script>
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

## <a name="the-flaskjade-web-project-template"></a>Szablon projektu sieci Web Flask/Jade

Jak wspomniano na początku tego artykułu, programu Visual Studio udostępniają szablon "Projekt sieci Web Flask/Jade", która tworzy aplikację, która jest wizualnie taka sama, jak co to jest generowany przez "Projekt sieci Web Flask". Podstawowa różnica polega na tym, że używa on aparat Jade szablonów, który jest rozszerzeniem Jinja, która implementuje te same pojęcia z bardziej zwięzłą języka. W szczególności Jade używa słowa kluczowe zamiast tagi ujęty w znaki {filtr ograniczników, na przykład i umożliwia dotyczą stylów CSS oraz elementów HTML za pomocą słów kluczowych.

Aby włączyć Jade, szablon projektu najpierw zawiera pakiet pyjade w *requirements.txt*.

Aplikacja  *\_ \_init\_\_PY* pliku zawiera wiersz do

```python
app.jinja_env.add_extension('pyjade.ext.jinja.PyJadeExtension')
```
W *szablony* folderów, zobacz *jade* plików zamiast *.html* szablonów i widoków w *views.py* odnoszą się do tych plików w ich wywołania `flask.render_template`. W przeciwnym razie kod widoków jest taki sam.

Otwarcie jednej z *jade* pliki, możesz zobaczyć bardziej zwięzłą wyrażenie szablonu. Na przykład poniżej przedstawiono zawartość *templates/layout.jade* utworzona przez szablon "Projekt sieci Web Flask/Jade":

```jade
doctype html
html
  head
    meta(charset='utf-8')
    meta(name='viewport', content='width=device-width, initial-scale=1.0')
    title #{title} - My Flask/Jade Application
    link(rel='stylesheet', type='text/css', href='/static/content/bootstrap.min.css')
    link(rel='stylesheet', type='text/css', href='/static/content/site.css')
    script(src='/static/scripts/modernizr-2.6.2.js')
  body
    .navbar.navbar-inverse.navbar-fixed-top
      .container
        .navbar-header
          button.navbar-toggle(type='button', data-toggle='collapse', data-target='.navbar-collapse')
            span.icon-bar
            span.icon-bar
            span.icon-bar
          a.navbar-brand(href='/') Application name
        .navbar-collapse.collapse
          ul.nav.navbar-nav
            li
              a(href='/') Home
            li
              a(href='/about') About
            li
              a(href='/contact') Contact
    .container.body-content
      block content
      hr
      footer
        p &copy; #{year} - My Flask/Jade Application

    script(src='/static/scripts/jquery-1.10.2.js')
    script(src='/static/scripts/bootstrap.js')
    script(src='/static/scripts/respond.js')

    block scripts
```

A Oto zawartość *templates/about.jade*, przedstawiający zastosowanie `#{ <name>}` dla symboli zastępczych:

```jade
extends layout

block content
  h2 #{title}.
  h3 #{message}
  p Use this area to provide additional information.
```

Możesz eksperymentować z zarówno Jinja i Jade składni, aby zobaczyć, który z nich działa najlepiej dla Ciebie.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Szablon projektu sieci Web Flask sond](learn-flask-visual-studio-step-05-polls-flask-web-project-template.md)

## <a name="go-deeper"></a>Przejdź dalej

- [Zapisywanie swoją pierwszą aplikację Flask, część 4 — formularzy i widoków ogólny](https://docs.djangoproject.com/en/2.0/intro/tutorial04/) (docs.djangoproject.com)
- [Jade na GitHib (dokumentacja)](https://github.com/liuliqiang/pyjade) (github.com)
- Kod źródłowy samouczek w witrynie GitHub: [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask)

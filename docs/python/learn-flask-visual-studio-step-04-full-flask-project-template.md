---
title: Samouczek dotyczący kolby w programie Visual Studio krok 4, szablony projektów sieci Web
titleSuffix: ''
description: Wskazówki dotyczące kolb w kontekście projektów programu Visual Studio, w tym funkcje udostępniane przez projekt sieci Web, kolby/Jade.
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: ef9154a34ddd08e7e0a4b9434f7f748b2603aef4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882872"
---
# <a name="step-4-use-the-full-flask-web-project-template"></a>Krok 4. Korzystanie z szablonu projektu sieci Web pełnej kolby

**Poprzedni krok: [Obsługiwanie plików statycznych, dodawanie stron i używanie dziedziczenia szablonów](learn-flask-visual-studio-step-03-serve-static-files-add-pages.md)**

Teraz, gdy znasz już podstawowe informacje o kolbie, tworząc aplikację na podstawie szablonu "pustej kolby projektu aplikacji" w programie Visual Studio, można łatwo zrozumieć aplikację, która jest tworzona przez szablon "Przeanalizuj projekt sieci Web".

W tym kroku:

> [!div class="checklist"]
> - Utwórz kompletną aplikację sieci Web przy użyciu szablonu "Analizuj projekt sieci Web" i przejrzyj strukturę projektu (krok 4-1)
> - Zapoznaj się z widokami i szablonami stron utworzonymi przez szablon projektu, które składają się z trzech stron, które dziedziczą z szablonu strony podstawowej i które wykorzystują statyczne biblioteki JavaScript, takie jak jQuery i Bootstrap (krok 4-2).
> - Opis routingu URL dostarczonego przez szablon (krok 4-3)

Ten artykuł dotyczy również szablonu "Kolba/Jade projektu sieci Web", który tworzy aplikację, która jest identyczna z "projektem w sieci Web" przy użyciu aparatu tworzenia szablonów Jade zamiast jinja. Dodatkowe szczegóły znajdują się na końcu tego artykułu.

## <a name="step-4-1-create-a-project-from-the-template"></a>Krok 4-1: Tworzenie projektu na podstawie szablonu

1. W programie Visual Studio przejdź do **Eksplorator rozwiązań**, kliknij prawym przyciskiem myszy rozwiązanie **LearningFlask** utworzone wcześniej w tym samouczku, a następnie wybierz pozycję **Dodaj**  >  **Nowy projekt**. (Alternatywnie, jeśli chcesz użyć nowego rozwiązania, wybierz pozycję **plik**  >  **Nowe**  >  W zamian **projekt** ).

1. W oknie dialogowym Nowy projekt Wyszukaj i wybierz szablon **projektu sieci Web z kolbą** , wywołaj projekt "FlaskWeb" i wybierz **przycisk OK**.

1. Ponieważ szablon ponownie zawiera plik *requirements.txt* , program Visual Studio pyta, gdzie zainstalować te zależności. Wybierz opcję, **Zainstaluj w środowisku wirtualnym**, a następnie w oknie dialogowym **Dodawanie środowiska wirtualnego** wybierz pozycję **Utwórz** , aby zaakceptować ustawienia domyślne.

1. Gdy program Visual Studio zakończy Konfigurowanie środowiska wirtualnego, ustaw projekt **FlaskWeb** jako domyślny dla rozwiązania Visual Studio, klikając prawym przyciskiem myszy ten projekt w **Eksplorator rozwiązań** i wybierając pozycję **Ustaw jako projekt startowy**. Projekt startowy, który jest wyświetlany pogrubiony, jest uruchamiany po uruchomieniu debugera.

    ![Eksplorator rozwiązań pokazujący projekt FlaskWeb jako projekt startowy](media/flask/step04-second-project-in-solution-set-as-startup-project.png)

1. Wybierz pozycję **Debuguj**  >  **Rozpocznij debugowanie** (**F5**) lub użyj przycisku **serwer sieci Web** na pasku narzędzi, aby uruchomić serwer:

    ![Przycisk paska narzędzi uruchamiania serwera sieci Web w programie Visual Studio](media/flask/run-web-server-toolbar-button.png)

1. Aplikacja utworzona przez szablon ma trzy strony, Strona główna, informacje i kontakt, które są przełączane między przy użyciu paska nawigacyjnego. Poświęć minutę lub dwie, aby przeanalizować różne części aplikacji. Aby uwierzytelnić się w aplikacji za pomocą polecenia **Zaloguj** , użyj wcześniej utworzonych poświadczeń administratora.

    ![Pełny widok przeglądarki dla aplikacji projektu sieci Web](media/flask/step04-full-app-desktop-view.png)

1. Aplikacja utworzona za pomocą szablonu "Kolba w sieci Web" używa programu Bootstrap do dynamicznego układu, który jest zgodny ze współczynnikiem formularza przenośnego. Aby wyświetlić ten czas odpowiedzi, Zmień rozmiar przeglądarki na wąski widok, aby zawartość była renderowana w pionie, a na pasku nawigacyjnym zostanie wyświetlona ikona menu:

    ![Widok Mobile (wąski) dla aplikacji projektu sieci Web](media/flask/step04-full-app-mobile-view.png)

1. Możesz pozostawić aplikację działającą dla następujących sekcji.

    Jeśli chcesz zatrzymać aplikację i [zatwierdzić zmiany w kontroli źródła](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control), najpierw Otwórz stronę **zmiany** w **Team Explorer**, kliknij prawym przyciskiem myszy folder dla środowiska wirtualnego (prawdopodobnie **ENV**), a następnie wybierz polecenie **Ignoruj te elementy lokalne**.

### <a name="examine-what-the-template-creates"></a>Sprawdzanie, co tworzy szablon

Szablon "Kolba" projektu sieci Web "tworzy strukturę poniżej. Zawartość jest bardzo podobna do utworzonych w poprzednich krokach. Różnica polega na tym, że szablon "projekt sieci Web" zawiera więcej struktur w folderze *statycznym* , ponieważ zawiera jQuery i Bootstrap na potrzeby projektowania. Szablon dodaje również stronę kontaktu. Ogólnie, jeśli wykonano poprzednie kroki w tym samouczku, wszystkie elementy z szablonu powinny być znane.

- Pliki w folderze głównym projektu:
  - *runserver.py* skrypt służący do uruchamiania aplikacji na serwerze deweloperskim.
  - *requirements.txt* zawierający zależność od kolby 0. x.
- Folder *FlaskWeb* zawiera wszystkie pliki aplikacji:
  - init.py oznacza kod aplikacji jako moduł języka Python, tworzy obiekt kolby i importuje widoki aplikacji. *\_ \_ \_ \_*
  - *views.py* zawiera kod do renderowania stron.
  - Folder *statyczny* zawiera podfoldery o nazwie *zawartość* (pliki CSS), *czcionki* (pliki czcionek) i *skrypty* (pliki JavaScript).
  - Folder *templates* zawiera szablon podstawowy *layout.html* wraz z *about.html*, *contact.html* i *index.html* dla określonych stron, które zostały rozszerzone *layout.html*.

### <a name="question-is-it-possible-to-share-a-virtual-environment-between-visual-studio-projects"></a>Pytanie: czy jest możliwe udostępnianie środowiska wirtualnego między projektami programu Visual Studio?

Odpowiedź: tak, ale należy to zrobić, korzystając z świadomości, że różne projekty mogą korzystać z różnych pakietów w miarę upływu czasu, dlatego udostępnione środowisko wirtualne musi zawierać wszystkie pakiety dla wszystkich projektów, które go używają.

Niemniej jednak, aby użyć istniejącego środowiska wirtualnego, wykonaj następujące czynności:

1. Po wyświetleniu monitu o zainstalowanie zależności w programie Visual Studio wybierz opcję **zainstaluję je samodzielnie** .
1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy węzeł **środowiska Python** i wybierz polecenie **Dodaj istniejące środowisko wirtualne**.
1. Przejdź do folderu zawierającego środowisko wirtualne i wybierz go, a następnie wybierz **przycisk OK**.

## <a name="step-4-2-understand-the-views-and-page-templates-created-by-the-project-template"></a>Krok 4-2: informacje o widokach i szablonach stron utworzonych przez szablon projektu

Po uruchomieniu projektu aplikacja zawiera trzy widoki: Home, about i Contact. Kod dla tych widoków znajduje się w *FlaskWeb/views. PR*. Każda funkcja widoku po prostu wywołuje `flask.render_template` ze ścieżką do szablonu i zmienną listę argumentów dla wartości, które mają zostać przekazane do szablonu. Na przykład strona informacje jest obsługiwana przez `about` funkcję (której dekoratora zapewnia Routing adresów URL):

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

`home`Funkcje i `contact` są niemal identyczne, z podobnymi dekoratoryami i nieco różnymi argumentami.

Szablony znajdują się w folderze *Szablony* aplikacji. Szablon podstawowy, *layout.html*, jest najbardziej obszerny. Odnosi się do wszystkich niezbędnych plików statycznych (JavaScript i CSS), definiuje blok o nazwie "Content", który przesłonił inne strony i udostępnia inny blok o nazwie "Scripts" (skrypty). Następujące fragmenty z adnotacjami z *layout.html* pokazują następujące obszary:

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

## <a name="the-flaskjade-web-project-template"></a>Szablon projektu sieci Web kolby/Jade

Jak wspomniano na początku tego artykułu, program Visual Studio udostępnia szablon "kolby/Jade projektu sieci Web", który tworzy aplikację, która jest wizualnie identyczna z tym, co zostało utworzone przez "projekt sieci Web". Podstawowa różnica polega na tym, że używa aparatu Jade tworzenia szablonów, który jest rozszerzeniem Jinja, które implementuje te same koncepcje z bardziej zwięzłym językiem. W odniesieniu do Jade używa słów kluczowych zamiast tagów ujętych w ograniczniki {%%}, na przykład, i umożliwia odwoływanie się do stylów CSS i elementów HTML przy użyciu słów kluczowych.

Aby włączyć Jade, szablon projektu najpierw zawiera pakiet pyjade w *requirements.txt*.

Plik *\_ \_ init \_ \_ . PR* aplikacji zawiera wiersz do

```python
app.jinja_env.add_extension('pyjade.ext.jinja.PyJadeExtension')
```

W folderze *Szablony* widoczne są pliki *Jade* zamiast szablonów *html* , a widoki w *views.py* odnoszą się do tych plików w ramach wywołań do programu `flask.render_template` . W przeciwnym razie kod widoków jest taki sam.

Otwarcie jednego z plików *. Jade* można zobaczyć bardziej zwięzłe wyrażenie szablonu. Załóżmy na przykład, że zawartość *szablonów/Layout. Jade* została utworzona przez szablon "Kolba/Jade projekt sieci Web":

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

A Oto zawartość *szablonów/about. Jade*, które pokazują użycie `#{ <name>}` dla symboli zastępczych:

```jade
extends layout

block content
  h2 #{title}.
  h3 #{message}
  p Use this area to provide additional information.
```

Śmiało, aby eksperymentować ze składnią jinja i jade, aby zobaczyć, która z nich najlepiej sprawdza się.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Szablon projektu sieci Web kolby sondy](learn-flask-visual-studio-step-05-polls-flask-web-project-template.md)

## <a name="go-deeper"></a>Przejdź głębiej

- [Pisanie pierwszej kolby, część 4 — formularze i widoki ogólne](https://docs.djangoproject.com/en/2.0/intro/tutorial04/) (docs.djangoproject.com)
- [Jade w witrynie GitHub (dokumentacja)](https://github.com/liuliqiang/pyjade) (GitHub.com)
- Kod źródłowy samouczka w witrynie GitHub: [Microsoft/Python-Sample-vs-Learning-Kolba](https://github.com/Microsoft/python-sample-vs-learning-flask)

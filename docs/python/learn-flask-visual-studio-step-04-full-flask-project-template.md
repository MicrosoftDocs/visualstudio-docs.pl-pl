---
title: Dowiedz się samouczek Kolby w programie Visual Studio krok 4, szablony projektów sieci Web
titleSuffix: ''
description: Przewodnik po podstawach flask w kontekście projektów programu Visual Studio, w szczególności funkcje dostarczone przez flask Web Project i Flask/Jade Web Project szablonów.
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 9f4c165f3e882cea71ee4aaff9f2358c27ce6a2b
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "62957319"
---
# <a name="step-4-use-the-full-flask-web-project-template"></a>Krok 4: Użyj pełnego szablonu projektu Flask Web Project

**Poprzedni krok: [Obsługa plików statycznych, dodawanie stron i używanie dziedziczenia szablonów](learn-flask-visual-studio-step-03-serve-static-files-add-pages.md)**

Teraz, gdy zostały zbadane podstawy Flask przez tworzenie aplikacji na "Blank Flask App Project" szablon w programie Visual Studio, można łatwo zrozumieć pełniejszą aplikację, która jest produkowana przez szablon "Flask Web Project".

W tym kroku teraz:

> [!div class="checklist"]
> - Tworzenie pełniejszej aplikacji internetowej Flask przy użyciu szablonu "Flask Web Project" i badanie struktury projektu (krok 4-1)
> - Zrozumienie widoków i szablonów stron utworzonych przez szablon projektu, które składają się z trzech stron, które dziedziczą z szablonu strony podstawowej i które wykorzystują statyczne biblioteki JavaScript, takie jak jQuery i Bootstrap (krok 4-2)
> - Opis routingu adresów URL dostarczonych przez szablon (krok 4-3)

Ten artykuł dotyczy również szablonu "Flask/Jade Web Project", który tworzy aplikację identyczną z aplikacją "Flask Web Project" przy użyciu silnika szablonów Jade zamiast Jinja. Dodatkowe szczegóły znajdują się na końcu tego artykułu.

## <a name="step-4-1-create-a-project-from-the-template"></a>Krok 4-1: Tworzenie projektu na podstawie szablonu

1. W programie Visual Studio przejdź do **programu Solution Explorer**, kliknij prawym przyciskiem myszy rozwiązanie **LearningFlask** utworzone wcześniej w tym samouczku i wybierz pozycję **Dodaj** > **nowy projekt**. (Alternatywnie, jeśli chcesz użyć nowego rozwiązania, wybierz **pozycję Plik** > **nowego** > **projektu).**

1. W oknie dialogowym nowego projektu wyszukaj i wybierz szablon **Flask Web Project,** zadzwoń do projektu "FlaskWeb" i wybierz **przycisk OK**.

1. Ponieważ szablon ponownie zawiera plik *requirements.txt,* visual studio pyta, gdzie zainstalować te zależności. Wybierz opcję **Zainstaluj w środowisku wirtualnym,** a następnie w oknie dialogowym **Dodaj środowisko wirtualne** wybierz pozycję **Utwórz,** aby zaakceptować wartości domyślne.

1. Po zakończeniu konfigurowania środowiska wirtualnego w programie Visual Studio ustaw projekt **FlaskWeb** jako domyślny dla rozwiązania programu Visual Studio, klikając prawym przyciskiem myszy ten projekt w **Eksploratorze rozwiązań** i wybierając **pozycję Ustaw jako projekt uruchamiania.** Projekt uruchamiania, który jest wyświetlany pogrubioną czcionką, jest tym, co jest uruchamiane po uruchomieniu debugera.

    ![Eksplorator rozwiązań przedstawiający projekt FlaskWeb jako projekt startowy](media/flask/step04-second-project-in-solution-set-as-startup-project.png)

1. Wybierz **debugowanie** > **rozpocznij debugowanie** **(F5)** lub użyj przycisku Serwera sieci **Web** na pasku narzędzi, aby uruchomić serwer:

    ![Uruchamianie przycisku paska narzędzi serwera sieci Web w programie Visual Studio](media/flask/run-web-server-toolbar-button.png)

1. Aplikacja utworzona przez szablon ma trzy strony: Strona główna, Informacje i Kontakt, które można nawigować między za pomocą paska nawigacji. Poświęć minutę lub dwie, aby zbadać różne części aplikacji. Aby uwierzytelnić się za pomocą aplikacji za pomocą polecenia **Zaloguj,** użyj poświadczeń administratora utworzonych wcześniej.

    ![Pełny widok przeglądarki aplikacji Flask Web Project](media/flask/step04-full-app-desktop-view.png)

1. Aplikacja stworzona przez szablon "Flask Web Project" używa Bootstrap do elastycznego układu, który pasuje do mobilnych rozmiarów. Aby zobaczyć tę responsywność, zmienić rozmiar przeglądarki na wąski widok, tak aby zawartość była renderowana w pionie, a pasek nawigacyjny zamienia się w ikonę menu:

    ![Mobilny (wąski) widok aplikacji Flask Web Project](media/flask/step04-full-app-mobile-view.png)

1. Możesz pozostawić aplikację z uruchomiona dla sekcji, które należy wykonać.

    Jeśli chcesz zatrzymać aplikację i [zatwierdzić zmiany w formancie źródłowym,](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control)najpierw otwórz stronę **Zmiany** w **Eksploratorze zespołu,** kliknij prawym przyciskiem myszy folder środowiska wirtualnego (prawdopodobnie **env)** i wybierz pozycję **Ignoruj te elementy lokalne**.

### <a name="examine-what-the-template-creates"></a>Sprawdzanie, co tworzy szablon

Szablon "Flask Web Project" tworzy strukturę poniżej. Zawartość jest bardzo podobna do zawartości utworzonej w poprzednich krokach. Różnica polega na tym, że szablon "Flask Web Project" zawiera więcej struktury w folderze *statycznym,* ponieważ zawiera jQuery i Bootstrap do responsywnego projektowania. Szablon dodaje również stronę kontaktową. Ogólnie rzecz biorąc, jeśli po poprzednich krokach w tym samouczku wszystko z szablonu powinno być znane.

- Pliki w katalogu głównym projektu:
  - *runserver.py*, skrypt do uruchamiania aplikacji na serwerze deweloperów.
  - *requirements.txt* zawierający zależność od Flask 0.x.
- Folder *FlaskWeb* zawiera wszystkie pliki aplikacji:
  - init.py oznacza kod aplikacji jako moduł Języka Python, tworzy obiekt Flask i importuje widoki aplikacji. * \_ \_\_ *
  - *views.py* zawiera kod do renderowania stron.
  - Folder *statyczny* zawiera podfoldery o nazwie *content* (pliki CSS), *czcionki* (pliki czcionek) i *skrypty* (pliki JavaScript).
  - Folder *szablonów* zawiera szablon podstawowy *layout.html* wraz z *plikem about.html*, *contact.html*i *index.html* dla określonych stron, które rozszerzają *layout.html*.

### <a name="question-is-it-possible-to-share-a-virtual-environment-between-visual-studio-projects"></a>Pytanie: Czy można udostępniać środowisko wirtualne między projektami programu Visual Studio?

Odpowiedź: Tak, ale zrób to ze świadomością, że różne projekty mogą używać różnych pakietów w czasie, a zatem udostępnione środowisko wirtualne musi zawierać wszystkie pakiety dla wszystkich projektów, które go używają.

Niemniej jednak, aby użyć istniejącego środowiska wirtualnego, wykonaj następujące czynności:

1. Po wyświetleniu monitu o zainstalowanie zależności w programie Visual Studio wybierz opcję **Zainstaluję je samodzielnie.**
1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy węzeł **Środowiska języka Python** i wybierz polecenie Dodaj istniejące środowisko **wirtualne**.
1. Przejdź do folderu zawierającego środowisko wirtualne i wybierz go, a następnie wybierz przycisk **OK**.

## <a name="step-4-2-understand-the-views-and-page-templates-created-by-the-project-template"></a>Krok 4-2: Zrozumienie widoków i szablonów stron utworzonych przez szablon projektu

Jak obserwować po uruchomieniu projektu, aplikacja zawiera trzy widoki: Strona główna, Informacje i Kontakt. Kod tych widoków znajduje się w *flaskWeb/views.py*. Każda funkcja widoku `flask.render_template` po prostu wywołuje ze ścieżką do szablonu i zmienną listę argumentów dla wartości, które mają być podane do szablonu. Na przykład strona Informacje jest obsługiwana przez `about` funkcję (której dekorator udostępnia routing adresu URL):

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

`home` Funkcje `contact` i funkcje są prawie identyczne, z podobnymi dekoratorami i nieco innymi argumentami.

Szablony znajdują się w folderze *szablonów* aplikacji. Szablon podstawowy, *layout.html*, jest najbardziej obszerny. Odnosi się do wszystkich niezbędnych plików statycznych (JavaScript i CSS), definiuje blok o nazwie "zawartość", który inne strony zastępują, i udostępnia inny blok o nazwie "skrypty". Następujące fragmenty z adnotacjami z *layout.html* przedstawiają następujące konkretne obszary:

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

## <a name="the-flaskjade-web-project-template"></a>Szablon projektu sieci Web Flask/Jade

Jak wspomniano na początku tego artykułu, Visual Studio zapewniają "Flask/Jade Web Project" szablon, który tworzy aplikację, która jest wizualnie identyczne z tym, co jest produkowane przez "Flask Web Project". Podstawową różnicą jest to, że używa jadeitowego silnika szablonów, który jest rozszerzeniem do Jinja, który implementuje te same pojęcia z bardziej zwięzłym językiem. W szczególności Jade używa słów kluczowych zamiast tagów ujętych w ogranicznikach {% %} i umożliwia odwoływanie się do stylów CSS i elementów HTML przy użyciu słów kluczowych.

Aby włączyć Jade, szablon projektu najpierw zawiera pakiet pyjade w *pliku requirements.txt*.

Plik * \_ \_.py\_\_init* aplikacji zawiera wiersz

```python
app.jinja_env.add_extension('pyjade.ext.jinja.PyJadeExtension')
```

W folderze *szablony* są widoczne pliki *.jade* zamiast szablonów *.html,* a widoki w *views.py* odnoszą `flask.render_template`się do tych plików w ich połączeniach do . W przeciwnym razie kod widoków jest taka sama.

Otwierając jeden z plików *.jade,* możesz zobaczyć bardziej zwięzłe wyrażenie szablonu. Na przykład, oto zawartość *templates/layout.jade,* utworzona przez szablon "Flask/Jade Web Project":

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

A oto zawartość *szablonów / about.jade*, pokazując `#{ <name>}` wykorzystanie dla symboli zastępczych:

```jade
extends layout

block content
  h2 #{title}.
  h3 #{message}
  p Use this area to provide additional information.
```

Zachęcamy do eksperymentowania zarówno z jinja i jade składni, aby zobaczyć, który z nich działa najlepiej dla Ciebie.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Szablon projektu sieci Web Sondy Kolby](learn-flask-visual-studio-step-05-polls-flask-web-project-template.md)

## <a name="go-deeper"></a>Głębiej

- [Pisanie pierwszej aplikacji Flask, część 4 - formularze i widoki ogólne](https://docs.djangoproject.com/en/2.0/intro/tutorial04/) (docs.djangoproject.com)
- [Jade na GitHib (Dokumentacja)](https://github.com/liuliqiang/pyjade) (github.com)
- Kod źródłowy samouczka w usłudze GitHub: [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask)

---
title: Poznaj samouczek Django w programie Visual Studio, w kroku 5, uwierzytelnianie
titleSuffix: ''
description: Przewodnik po podstawy Django w kontekście projektów programu Visual Studio, w szczególności funkcje uwierzytelniania określone szablony projektów internetowych Django.
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: bdc76b0a7b9d3f74da77b317faf31dae83706f04
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62957888"
---
# <a name="step-5-authenticate-users-in-django"></a>Krok 5. Uwierzytelnianie użytkowników w Django

**Poprzedniego kroku: [Użyj pełnego szablonów projektów internetowych Django](learn-django-in-visual-studio-step-04-full-django-project-template.md)**

Ponieważ uwierzytelnianie jest typowe potrzeby aplikacji sieci web, szablon "Projekt sieci Web Django" obejmuje przepływ uwierzytelniania podstawowego. (Szablon "Projekt sieci Web Django sond" omówiono w kroku 6 procedury w tym samouczku także sam przepływ.) W przypadku stosowania Django szablony projektu Visual Studio zawiera wszystkie moduły niezbędne do uwierzytelniania w projekcie Django *settings.py*.

W tym kroku dowiesz się:

> [!div class="checklist"]
> - Jak korzystać z tego przepływu uwierzytelniania podany w szablonach programu Visual Studio (krok 5 - 1)

## <a name="step-5-1-use-the-authentication-flow"></a>Krok 1 z 5 Przepływ uwierzytelniania

Poniższe kroki wykonuje przepływ uwierzytelniania i opisano części projektu, które są zaangażowane:

1. Jeśli jeszcze nie wykonano instrukcje *readme.html* plik w folderze głównym projektu, aby utworzyć konta administratora (administrator), zrób to teraz.

1. Uruchamianie aplikacji z programu Visual Studio przy użyciu **debugowania** > **Rozpocznij debugowanie** (**F5**). Gdy aplikacja zostanie wyświetlona w przeglądarce, Zauważ, że **Zaloguj** pojawia się w prawym górnym rogu paska nawigacyjnego.

    ![Kontrolka Login na stronie aplikacji projektu sieci Web Django](media/django/step05-login-control.png)

1. Otwórz *templates/app/layout.html* i Zauważ, że `<div class="navbar ...>` element zawiera tag `{% include app/loginpartial.html %}`. `{% include %}` Tag powoduje, że firmy Django szablonów systemu, aby ściągnąć zawartość pliku uwzględnione w tym momencie w szablonie zawierającego.

1. Otwórz *templates/app/loginpartial.html* i obserwuj, jak używa tagu warunkowego `{% if user.is_authenticated %}` wraz z `{% else %}` tag do różnych elementów interfejsu użytkownika, w zależności od tego, czy użytkownik został uwierzytelniony renderowania:

    ```html
    {% if user.is_authenticated %}
    <form id="logoutForm" action="/logout" method="post" class="navbar-right">
        {% csrf_token %}
        <ul class="nav navbar-nav navbar-right">
            <li><span class="navbar-brand">Hello {{ user.username }}!</span></li>
            <li><a href="javascript:document.getElementById('logoutForm').submit()">Log off</a></li>
        </ul>
    </form>

    {% else %}

    <ul class="nav navbar-nav navbar-right">
        <li><a href="{% url 'login' %}">Log in</a></li>
    </ul>

    {% endif %}
    ```

1. Ponieważ żaden użytkownik nie jest uwierzytelniony, przy pierwszym uruchomieniu aplikacji, ten kod szablonu powoduje wyświetlenie tylko "Zaloguj" linku do ścieżki względnej "Logowanie". Jak określono w *urls.py* (jak pokazano w poprzedniej sekcji), tej trasy jest mapowany na `django.contrib.auth.views.login` widoku. Ten widok otrzymuje następujące dane:

    ```python
    {
        'template_name': 'app/login.html',
        'authentication_form': app.forms.BootstrapAuthenticationForm,
        'extra_context':
        {
            'title': 'Log in',
            'year': datetime.now().year,
        }
    }
    ```

    W tym miejscu `template_name` identyfikuje szablon do strony logowania, w tym przypadku *templates/app/login.html*. `extra_context` Właściwość została dodana do domyślny kontekst danych, do szablonu. Na koniec `authentication_form` Określa klasę formularza za pomocą identyfikatora logowania; w szablonie będzie ono wyświetlane jako `form` obiektu. Wartość domyślna to `AuthenticationForm` (z `django.contrib.auth.views`); szablon projektu Visual Studio zamiast tego używa formularz zdefiniowany w aplikacji *forms.py* pliku:

    ```python
    from django import forms
    from django.contrib.auth.forms import AuthenticationForm
    from django.utils.translation import ugettext_lazy as _

    class BootstrapAuthenticationForm(AuthenticationForm):
        """Authentication form which uses boostrap CSS."""
        username = forms.CharField(max_length=254,
                                   widget=forms.TextInput({
                                       'class': 'form-control',
                                       'placeholder': 'User name'}))
        password = forms.CharField(label=_("Password"),
                                   widget=forms.PasswordInput({
                                       'class': 'form-control',
                                       'placeholder':'Password'}))
    ```

    Jak widać, pochodzi ta klasa formularza `AuthenticationForm` i zastąpi pól nazwy użytkownika i hasła w celu dodania tekst symbolu zastępczego. Szablon programu Visual Studio zawiera ten kod jawne przy założeniu, że prawdopodobnie zechcesz dostosować formularz, takie jak dodawanie sprawdzania siły haseł.

1. Po przejściu do strony logowania, następnie renderuje aplikacji *login.html* szablonu. Zmienne `{{ form.username }}` i `{{ form.password }}` renderowania `CharField` formularzy z `BootstrapAuthenticationForm`. Istnieje również wbudowane sekcję, aby wyświetlić błędy sprawdzania poprawności, a element gotowych do użycia dla społecznościowych nazw logowania, jeśli zdecydujesz się dodać tych usług.

    ```html
    {% extends "app/layout.html" %}

    {% block content %}

    <h2>{{ title }}</h2>
    <div class="row">
        <div class="col-md-8">
            <section id="loginForm">
                <form action="." method="post" class="form-horizontal">
                    {% csrf_token %}
                    <h4>Use a local account to log in.</h4>
                    <hr />
                    <div class="form-group">
                        <label for="id_username" class="col-md-2 control-label">User name</label>
                        <div class="col-md-10">
                            {{ form.username }}
                        </div>
                    </div>
                    <div class="form-group">
                        <label for="id_password" class="col-md-2 control-label">Password</label>
                        <div class="col-md-10">
                            {{ form.password }}
                        </div>
                    </div>
                    <div class="form-group">
                        <div class="col-md-offset-2 col-md-10">
                            <input type="hidden" name="next" value="/" />
                            <input type="submit" value="Log in" class="btn btn-default" />
                        </div>
                    </div>
                    {% if form.errors %}
                    <p class="validation-summary-errors">Please enter a correct user name and password.</p>
                    {% endif %}
                </form>
            </section>
        </div>
        <div class="col-md-4">
            <section id="socialLoginForm"></section>
        </div>
    </div>

    {% endblock %}
    ```

1. Gdy prześlesz formularz, Django próbuje uwierzytelnienia poświadczeń użytkownika (na przykład poświadczenia użytkownika administratora). W przypadku niepowodzenia uwierzytelniania, możesz pozostać na bieżącej stronie, ale `form.errors` ma wartość true. Jeśli uwierzytelnianie się powiedzie, Django, przechodzi do względnym adresem URL w polu "dalej" `<input type="hidden" name="next" value="/" />`, czyli w tym przypadku na stronie głównej (`/`).

1. Teraz, gdy strona główna jest renderowany ponownie `user.is_authenticated` właściwość ma wartość true, gdy *loginpartial.html* szablonu jest renderowany. W rezultacie, zobacz **Hello (nazwa użytkownika)** wiadomości i **wylogować**. Możesz użyć `user.is_authenticated` w innych częściach aplikacji przeprowadzenie sprawdzenia uwierzytelniania.

    ![Witaj wiadomości i wylogowywania formantu na stronie aplikacja projektu sieci Web Django](media/django/step05-logoff-control.png)

1. Aby sprawdzić, czy uwierzytelniony użytkownik jest autoryzowany do dostępu do określonych zasobów, musisz pobrać uprawnienia specyficzne dla użytkowników ze swojej bazy danych. Aby uzyskać więcej informacji, zobacz [przy użyciu uwierzytelniania systemu Django](https://docs.djangoproject.com/en/2.0/topics/auth/default/#permissions-and-authorization) (Django docs).

1. Administrator lub administrator, w szczególności jest autoryzowany do dostępu do wbudowanych interfejsów administratora Django przy użyciu względnych adresów URL "/admin/" i "/ admin/docs /". Aby włączyć te interfejsy, wykonaj następujące czynności:

    1. Zainstaluj pakiet języka Python docutils do własnego środowiska. Jest doskonały sposób, w tym celu można dodać "docutils" Twoje *requirements.txt* pliku, a następnie w obszarze **Eksploratora rozwiązań**, rozwiń węzeł projektu, rozwiń węzeł **środowiska Python** węzła, a następnie Kliknij prawym przyciskiem myszy środowiska używasz wybierz **Zainstaluj z pliku requirements.txt**.

    1. Otwórz projekt Django *urls.py* i usuwanie komentarzy domyślne z następujących pozycji:

        ```python
        from django.conf.urls import include
        from django.contrib import admin
        admin.autodiscover()

        # ...
        urlpatterns = [
            # ...
            url(r'^admin/doc/', include('django.contrib.admindocs.urls')),
            url(r'^admin/', include(admin.site.urls)),
        ]
        ```

    1. W projekcie Django *settings.py* pliku, przejdź do folderu `INSTALLED_APPS` kolekcji i Dodaj `'django.contrib.admindocs'`.

    1. Po ponownym uruchomieniu aplikacji, możesz przejść do "/admin/" i "/ admin/docs /" i wykonywać zadania, takie jak utworzenie dodatkowych kont użytkowników.

        ![Django Administratorze](media/django/step05-administrator-interface.png)

1. Wylogowanie końcowe część z przepływem uwierzytelniania. Jak widać w *loginpartial.html*, **wylogować** łącze jest po prostu WPIS względny adres URL "/ logowania", który jest obsługiwany przez wbudowany view `django.contrib.auth.views.logout`. Ten widok nie wyświetla żadnych interfejsów użytkownika i po prostu powoduje przejście do strony głównej (jak pokazano na *urls.py* dla "^ wylogowania$" wzorca). Jeśli chcesz wyświetlić stronę wylogowywania, należy najpierw zmienić wzorzec adresu URL w następujący sposób, aby dodać właściwość "template_name" i Usuń właściwość "next_page":

    ```python
    url(r'^logout$',
        django.contrib.auth.views.logout,
        {
            'template_name': 'app/loggedoff.html',
            # 'next_page': '/',
        },
        name='logout')
    ```

    Następnie utwórz *templates/app/loggedoff.html* z następującą zawartością (minimalny):

    ```html
    {% extends "app/layout.html" %}
    {% block content %}
    <h3>You have been logged off</h3>
    {% endblock %}
    ```

    Wynik jest wyświetlany w następujący sposób:

    ![Dodano wylogowany strony](media/django/step05-logged-off-page.png)

1. Gdy wszystko będzie gotowe, zatrzymać serwer ponownie zmianami i zatwierdzanie ich do kontroli źródła.

### <a name="question-what-is-the-purpose-of-the--csrftoken--tag-that-appears-in-the-form-elements"></a>Pytanie: Co to jest celem {% csrf_token %} tagów, które pojawia się w \<formularza\> elementy?

Odpowiedź: `{% csrf_token %}` Znacznik obejmuje wbudowane w Django [fałszerstwo żądania międzywitrynowego (csrf) ochrony](https://docs.djangoproject.com/en/2.0/ref/csrf/) (Django docs). Zazwyczaj Dodaj ten tag do dowolnego elementu, która obejmuje metody żądania POST, PUT lub DELETE, takie jak formularz. Funkcja renderowania szablonu (`render`) wstawia na potrzeby ochrony.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Użyj szablonu projektu sieci Web Django sond](learn-django-in-visual-studio-step-06-polls-django-web-project-template.md)

## <a name="go-deeper"></a>Przejdź dalej

- [Uwierzytelnianie użytkownika w Django](https://docs.djangoproject.com/en/2.0/topics/auth/) (docs.djangoproject.com)
- Kod źródłowy samouczek w witrynie GitHub: [Microsoft/python — przykładowe vs uczenia — django](https://github.com/Microsoft/python-sample-vs-learning-django)

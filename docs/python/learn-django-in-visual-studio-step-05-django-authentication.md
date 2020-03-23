---
title: Dowiedz się samouczek Django w programie Visual Studio, krok 5, uwierzytelnianie
titleSuffix: ''
description: Przewodnik po podstawach Django w kontekście projektów programu Visual Studio, w szczególności funkcji uwierzytelniania dostarczonych przez szablony django Web Project.
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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "62957888"
---
# <a name="step-5-authenticate-users-in-django"></a>Krok 5: Uwierzytelnianie użytkowników w Django

**Poprzedni krok: [Użyj pełnego szablonu Django Web Project](learn-django-in-visual-studio-step-04-full-django-project-template.md)**

Ponieważ uwierzytelnianie jest częstą potrzebą aplikacji internetowych, szablon "Django Web Project" zawiera podstawowy przepływ uwierzytelniania. (Szablon "Sondy Django Web Project" omówione w kroku 6 tego samouczka również zawiera ten sam przepływ.) Podczas korzystania z dowolnego z szablonów projektu Django, Visual Studio zawiera wszystkie niezbędne moduły do uwierzytelniania w *settings.py*projektu Django .

W tym kroku dowiesz się:

> [!div class="checklist"]
> - Jak korzystać z przepływu uwierzytelniania dostępnego w szablonach programu Visual Studio (krok 5-1)

## <a name="step-5-1-use-the-authentication-flow"></a>Krok 5-1: Użyj przepływu uwierzytelniania

Następujące kroki wykonują przepływ uwierzytelniania i opisują części projektu, które są zaangażowane:

1. Jeśli nie postosujesz się jeszcze do instrukcji w pliku *readme.html* w katalogu głównym projektu, aby utworzyć konto superużytnika (administratora), zrób to teraz.

1. Uruchom aplikację z programu Visual Studio przy użyciu **debugowania** > **debugowania** **(F5).** Gdy aplikacja pojawi się w przeglądarce, należy zauważyć, że **logowanie** pojawia się w prawym górnym rogu paska nawigacyjnym.

    ![Kontrola logowania na stronie aplikacji Django Web Project](media/django/step05-login-control.png)

1. Otwórz *templates/app/layout.html* i obserwuj, `<div class="navbar ...>` że element `{% include app/loginpartial.html %}`zawiera znacznik . Tag `{% include %}` nakazuje systemowi szablonów Django, aby w tym momencie w szablonie zawierającym wciągnął zawartość dołączonego pliku.

1. Otwórz *templates/app/loginpartial.html* i obserwuj, jak używa tagu `{% if user.is_authenticated %}` warunkowego wraz z tagiem do renderowania `{% else %}` różnych elementów interfejsu użytkownika w zależności od tego, czy użytkownik uwierzytelnił się:

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

1. Ponieważ żaden użytkownik nie jest uwierzytelniony przy pierwszym uruchomieniu aplikacji, ten kod szablonu renderuje tylko łącze "Zaloguj się" do ścieżki względnej "login". Jak określono w *urls.py* (jak pokazano w poprzedniej sekcji), trasa `django.contrib.auth.views.login` ta jest mapowana do widoku. Widok ten otrzymuje następujące dane:

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

    W `template_name` tym miejscu identyfikuje szablon strony logowania, w tym przypadku *templates/app/login.html*. Właściwość `extra_context` jest dodawana do domyślnych danych kontekstowych podanych do szablonu. Na koniec `authentication_form` określa klasę formularza do użycia z logowaniem; w szablonie pojawia `form` się jako obiekt. Wartością domyślną `AuthenticationForm` `django.contrib.auth.views`jest (od ); Szablon projektu programu Visual Studio zamiast tego używa formularza zdefiniowanego w pliku *forms.py* aplikacji:

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

    Jak widać, ta klasa formularza `AuthenticationForm` pochodzi od i w szczególności zastępuje pola nazwy użytkownika i hasła, aby dodać tekst zastępczy. Szablon programu Visual Studio zawiera ten jawny kod przy założeniu, że prawdopodobnie chcesz dostosować formularz, takich jak dodawanie sprawdzania poprawności siły hasła.

1. Po przejściu do strony logowania aplikacja renderuje szablon *login.html.* Zmienne `{{ form.username }}` i `{{ form.password }}` renderuj formularze `CharField` z `BootstrapAuthenticationForm`programu . Istnieje również wbudowana sekcja, aby wyświetlić błędy sprawdzania poprawności i gotowy element logowania społecznościowego, jeśli zdecydujesz się dodać te usługi.

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

1. Po przesłaniu formularza Django próbuje uwierzytelnić twoje poświadczenia (takie jak poświadczenia superużytnika). Jeśli uwierzytelnianie nie powiedzie się, pozostaniesz na bieżącej stronie, ale `form.errors` ustawiona na true. Jeśli uwierzytelnianie zakończy się pomyślnie, Django przechodzi do względnego adresu URL w polu `<input type="hidden" name="next" value="/" />``/`"następny", który w tym przypadku jest stroną główną ( ).

1. Teraz, gdy strona główna jest renderowana ponownie, `user.is_authenticated` właściwość jest true, gdy *loginpartial.html* szablon jest renderowany. W rezultacie zostanie wyświetlony komunikat **Hello (nazwa użytkownika)** i **wyloguj się**. Można użyć `user.is_authenticated` w innych częściach aplikacji, aby sprawdzić uwierzytelnianie.

    ![Hello message and logoff control on the Django Web Project app page Hello message and logoff control on the Django Web Project app page Hello message and logoff control on the Django Web Project app page Hello message](media/django/step05-logoff-control.png)

1. Aby sprawdzić, czy uwierzytelniony użytkownik jest upoważniony do uzyskiwania dostępu do określonych zasobów, należy pobrać uprawnienia specyficzne dla użytkownika z bazy danych. Aby uzyskać więcej informacji, zobacz [Korzystanie z systemu uwierzytelniania Django](https://docs.djangoproject.com/en/2.0/topics/auth/default/#permissions-and-authorization) (dokumenty Django).

1. W szczególności superużytnik lub administrator jest upoważniony do dostępu do wbudowanych interfejsów administratora Django przy użyciu względnych adresów URL "/admin/" i "/admin/doc/". Aby włączyć te interfejsy, wykonaj następujące czynności:

    1. Zainstaluj pakiet docutils Python w swoim środowisku. Doskonałym sposobem, aby to zrobić, jest dodanie "docutils" do pliku *requirements.txt,* a następnie w **Eksploratorze rozwiązań**, rozwiń projekt, rozwiń węzeł **Środowiska Pythona,** a następnie kliknij prawym przyciskiem myszy środowisko, którego używasz, wybierz **zainstaluj z pliku requirements.txt**.

    1. Otwórz *urls.py* projektu Django i usuń domyślne komentarze z następujących wpisów:

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

    1. W pliku *settings.py* projektu Django przejdź do `INSTALLED_APPS` kolekcji `'django.contrib.admindocs'`i dodaj .

    1. Po ponownym uruchomieniu aplikacji można przejść do "/admin/" i "/admin/doc/" i wykonywać zadania, takie jak tworzenie dodatkowych kont użytkowników.

        ![Interfejs administratora Django](media/django/step05-administrator-interface.png)

1. Ostatnią częścią przepływu uwierzytelniania jest wylogowanie. Jak widać w *loginpartial.html*, link **Wyloguj** się po prostu nie POST do względnego `django.contrib.auth.views.logout`adresu URL "/ login", który jest obsługiwany przez wbudowany widok . Ten widok nie wyświetla żadnego interfejsu użytkownika i po prostu przechodzi do strony głównej (jak pokazano w *urls.py* dla wzorca "^wyloguj się$"). Jeśli chcesz wyświetlić stronę wylogowywania, najpierw zmień wzorzec adresu URL w następujący sposób, aby dodać właściwość "template_name" i usuń właściwość "next_page":

    ```python
    url(r'^logout$',
        django.contrib.auth.views.logout,
        {
            'template_name': 'app/loggedoff.html',
            # 'next_page': '/',
        },
        name='logout')
    ```

    Następnie utwórz *templates/app/loggedoff.html* z następującą (minimalną) zawartością:

    ```html
    {% extends "app/layout.html" %}
    {% block content %}
    <h3>You have been logged off</h3>
    {% endblock %}
    ```

    Wynik jest wyświetlany w następujący sposób:

    ![Dodano stronę wylogowany](media/django/step05-logged-off-page.png)

1. Gdy wszystko po zakończeniu, zatrzymaj serwer i ponownie zaobżą zmiany do kontroli źródła.

### <a name="question-what-is-the-purpose-of-the--csrf_token--tag-that-appears-in-the-form-elements"></a>Pytanie: Jaki jest cel tagu {% csrf_token %}, \<który\> pojawia się w elementach formularza?

Odpowiedź: `{% csrf_token %}` Tag zawiera wbudowaną ochronę przed [fałszerszem żądań międzygiełdowych (csrf) (dokumenty](https://docs.djangoproject.com/en/2.0/ref/csrf/) Django). Zazwyczaj ten tag jest dodawany do dowolnego elementu, który obejmuje metody żądania POST, PUT lub DELETE, takie jak formularz. Funkcja renderowania szablonu (`render`), a następnie wstawia niezbędną ochronę.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Użyj szablonu projektu sieci Web Ankiety Django](learn-django-in-visual-studio-step-06-polls-django-web-project-template.md)

## <a name="go-deeper"></a>Głębiej

- [Uwierzytelnianie użytkownika w Django](https://docs.djangoproject.com/en/2.0/topics/auth/) (docs.djangoproject.com)
- Kod źródłowy samouczka na GitHub: [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)

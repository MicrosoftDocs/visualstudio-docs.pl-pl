---
title: Poznaj samouczek Django w programie Visual Studio, krok 5, uwierzytelnianie
titleSuffix: ''
description: Przewodnik po Django podstawy w kontekście projektów programu Visual Studio, w tym funkcje uwierzytelniania udostępniane przez szablony projektu sieci Web Django.
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: ea708c1721d85468d99a0ccc327f378042579f85
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942493"
---
# <a name="step-5-authenticate-users-in-django"></a>Krok 5. uwierzytelnianie użytkowników w Django

**Poprzedni krok: [Użyj szablonu projektu sieci Web Full Django](learn-django-in-visual-studio-step-04-full-django-project-template.md)**

Ponieważ uwierzytelnianie jest powszechną potrzebą dla aplikacji sieci Web, szablon "projekt sieci Web Django" obejmuje podstawowy przepływ uwierzytelniania. (Szablon "ankiety Django Web projekt" omówiony w kroku 6 tego samouczka zawiera również ten sam przepływ). W przypadku używania któregokolwiek z szablonów projektów Django program Visual Studio zawiera wszystkie moduły niezbędne do uwierzytelniania w *Settings.py* projektu Django.

W tym kroku dowiesz się:

> [!div class="checklist"]
> - Jak używać przepływu uwierzytelniania dostępnego w szablonach programu Visual Studio (krok 5-1)

## <a name="step-5-1-use-the-authentication-flow"></a>Krok 5-1: korzystanie z przepływu uwierzytelniania

Poniższe kroki służą do wykonywania przepływu uwierzytelniania i opisywania części projektu, które są związane z:

1. Jeśli nie wykonano jeszcze instrukcji w pliku *readme.html* w katalogu głównym projektu w celu utworzenia konta administratora, zrób to teraz.

1. Uruchom aplikację **z programu Visual Studio przy użyciu debugowania**  >  **Rozpocznij debugowanie** (**F5**). Gdy aplikacja zostanie wyświetlona w przeglądarce, zwróć uwagę, że **Logowanie** pojawia się w prawym górnym rogu paska nawigacyjnego.

    ![Kontrolka logowania na stronie aplikacji Project Web Django](media/django/step05-login-control.png)

1. Otwórz *szablon/App/layout.html* i sprawdź, czy `<div class="navbar ...>` element zawiera tag `{% include app/loginpartial.html %}` . Ten `{% include %}` tag instruuje system tworzenia szablonów Django, aby ściągał zawartość dołączonego pliku w tym momencie w szablonie zawierającym.

1. Otwórz plik *templates/App/loginpartial.html* i obserwuj, w jaki sposób używa znacznika warunkowego `{% if user.is_authenticated %}` wraz ze `{% else %}` znacznikiem, aby renderować różne elementy interfejsu użytkownika w zależności od tego, czy użytkownik został uwierzytelniony:

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

1. Ponieważ żaden użytkownik nie jest uwierzytelniany podczas pierwszego uruchomienia aplikacji, ten kod szablonu renderuje tylko łącze "Logowanie do" do ścieżki względnej "login". Zgodnie z definicją w *URLs.py* (jak pokazano w poprzedniej sekcji) ta trasa jest mapowana do `django.contrib.auth.views.login` widoku. Ten widok otrzymuje następujące dane:

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

    W tym miejscu można `template_name` zidentyfikować szablon strony logowania, w tym przypadku *Szablony/aplikacje/login.html*. `extra_context`Właściwość jest dodawana do domyślnych danych kontekstowych przyznanych szablonowi. Na koniec `authentication_form` Określa klasę formularza do użycia z identyfikatorem logowania; w szablonie, który jest wyświetlany jako `form` obiekt. Wartość domyślna to `AuthenticationForm` (od `django.contrib.auth.views` ); szablon projektu programu Visual Studio używa zamiast tego formularza zdefiniowanego w pliku *Forms.py* aplikacji:

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

    Jak widać, Klasa formularza pochodzi z i w tym przypadku `AuthenticationForm` zastępuje pola Nazwa użytkownika i hasło, aby dodać tekst zastępczy. Szablon programu Visual Studio zawiera ten jawny kod na założeniu, że najkorzystniej chcesz dostosować formularz, taki jak dodanie walidacji siły hasła.

1. Po przejściu do strony logowania aplikacja renderuje szablon *login.html* . Zmienne `{{ form.username }}` i `{{ form.password }}` renderuje `CharField` formularze z `BootstrapAuthenticationForm` . Istnieje również wbudowana sekcja umożliwiająca wyświetlanie błędów walidacji, a także gotowy element do logowania społecznościowego, jeśli użytkownik zdecyduje się dodać te usługi.

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

1. Po przesłaniu formularza Django próbuje uwierzytelnić poświadczenia (na przykład poświadczenia administratora). Jeśli uwierzytelnianie nie powiedzie się, pozostanie na bieżącej stronie, ale `form.errors` ustawiono wartość true. Jeśli uwierzytelnianie zakończyło się pomyślnie, Django przechodzi do względnego adresu URL w polu "dalej", `<input type="hidden" name="next" value="/" />` w tym przypadku jest to Strona główna ( `/` ).

1. Teraz po ponownym wyrenderowaniu strony głównej `user.is_authenticated` Właściwość ma wartość true, gdy zostanie renderowany szablon *loginpartial.html* . W związku z tym zobaczysz komunikat **powitalny (username)** i **Wyloguj** się. `user.is_authenticated`Aby sprawdzić uwierzytelnianie, można użyć innych części aplikacji.

    ![Komunikat powitalny i kontrola wylogowania na stronie aplikacji Django Web Project](media/django/step05-logoff-control.png)

1. Aby sprawdzić, czy uwierzytelniony użytkownik ma autoryzację dostępu do określonych zasobów, musisz pobrać uprawnienia specyficzne dla użytkownika z bazy danych. Aby uzyskać więcej informacji, zobacz [Korzystanie z systemu uwierzytelniania Django](https://docs.djangoproject.com/en/2.0/topics/auth/default/#permissions-and-authorization) (dokumentacja Django).

1. Administrator, w szczególności, ma uprawnienia dostępu do wbudowanych interfejsów administratora Django przy użyciu względnych adresów URL "/admin/" i "/admin/doc/". Aby włączyć te interfejsy, wykonaj następujące czynności:

    1. Zainstaluj pakiet docutils Python w Twoim środowisku. Aby to zrobić, należy dodać "docutils" do pliku *requirements.txt* , a następnie w **Eksplorator rozwiązań**, rozwinąć projekt, rozwinąć węzeł **środowiska Python** , a następnie kliknąć prawym przyciskiem myszy środowisko, w którym jest używana opcja **Zainstaluj z requirements.txt**.

    1. Otwórz *URLs.py* projektu Django i usuń domyślne Komentarze z następujących wpisów:

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

    1. W pliku *Settings.py* projektu Django przejdź do `INSTALLED_APPS` kolekcji i Dodaj `'django.contrib.admindocs'` .

    1. Po ponownym uruchomieniu aplikacji można przejść do "/admin/" i "/admin/doc/" oraz wykonywać zadania, takie jak tworzenie dodatkowych kont użytkowników.

        ![Interfejs administratora Django](media/django/step05-administrator-interface.png)

1. Ostatnia część przepływu uwierzytelniania jest wylogowanie. Jak widać w *loginpartial.html* **, link Wyloguj** wystarczy po prostu wpis do względnego adresu URL "/login", który jest obsługiwany przez wbudowany widok `django.contrib.auth.views.logout` . Ten widok nie wyświetla żadnego interfejsu użytkownika i po prostu przechodzi do strony głównej (jak pokazano w *URLs.py* dla wzorca "^ Wyloguj $"). Jeśli chcesz wyświetlić stronę wylogowywania, najpierw zmień wzorzec adresu URL w następujący sposób, aby dodać właściwość "template_name" i usunąć Właściwość "next_page":

    ```python
    url(r'^logout$',
        django.contrib.auth.views.logout,
        {
            'template_name': 'app/loggedoff.html',
            # 'next_page': '/',
        },
        name='logout')
    ```

    Następnie Utwórz *szablon/aplikację/loggedoff.html* przy użyciu następującej (minimalnej) zawartości:

    ```html
    {% extends "app/layout.html" %}
    {% block content %}
    <h3>You have been logged off</h3>
    {% endblock %}
    ```

    Wynik jest wyświetlany w następujący sposób:

    ![Dodano zalogowaną stronę](media/django/step05-logged-off-page.png)

1. Gdy wszystko będzie gotowe, Zatrzymaj serwer i ponownie Zatwierdź zmiany w kontroli źródła.

### <a name="question-what-is-the-purpose-of-the--csrf_token--tag-that-appears-in-the-form-elements"></a>Pytanie: jaki jest cel tagu {% csrf_token%}, który pojawia się w \<form\> elementach?

Odpowiedź: `{% csrf_token %}` tag zawiera wbudowaną [ochronę Django (CSRF) żądania międzywitrynowego](https://docs.djangoproject.com/en/2.0/ref/csrf/) . Zazwyczaj ten tag jest dodawany do dowolnego elementu, który obejmuje metody POST, PUT lub DELETE, takie jak formularz. Funkcja renderowania szablonu ( `render` ) następnie wstawia wymaganą ochronę.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Korzystanie z szablonu projektu sieci Web Django sondy](learn-django-in-visual-studio-step-06-polls-django-web-project-template.md)

## <a name="go-deeper"></a>Przejdź głębiej

- [Uwierzytelnianie użytkownika w Django](https://docs.djangoproject.com/en/2.0/topics/auth/) (docs.djangoproject.com)
- Kod źródłowy samouczka w witrynie GitHub: [Microsoft/Python-Sample-vs-Learning-Django](https://github.com/Microsoft/python-sample-vs-learning-django)

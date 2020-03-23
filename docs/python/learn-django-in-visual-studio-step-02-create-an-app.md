---
title: Dowiedz się samouczek Django w programie Visual Studio krok 2, widoki i szablony stron
titleSuffix: ''
description: Przewodnik owy elementów Django w kontekście projektów programu Visual Studio, w szczególności kroki tworzenia aplikacji i przy użyciu widoków i szablonów.
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 5befdfb5f6974ff7b042319121a27c3628757b6e
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "79302862"
---
# <a name="step-2-create-a-django-app-with-views-and-page-templates"></a>Krok 2: Tworzenie aplikacji Django z widokami i szablonami stron

**Poprzedni krok: [Tworzenie projektu i rozwiązania programu Visual Studio](learn-django-in-visual-studio-step-01-project-and-solution.md)**

To, co masz do tej pory w projekcie Visual Studio, to tylko składniki *projektu*Django na poziomie lokacji, które mogą uruchamiać jedną lub więcej *aplikacji*Django. Następnym krokiem jest utworzenie pierwszej aplikacji za pomocą jednej strony.

W tym kroku dowiesz się, jak:

> [!div class="checklist"]
> - Tworzenie aplikacji Django za pomocą jednej strony (krok 2-1)
> - Uruchom aplikację z projektu Django (krok 2-2)
> - Renderowanie widoku przy użyciu kodu HTML (krok 2-3)
> - Renderowanie widoku przy użyciu szablonu strony Django (krok 2-4)

## <a name="step-2-1-create-an-app-with-a-default-structure"></a>Krok 2-1: Tworzenie aplikacji o domyślnej strukturze

Aplikacja Django to oddzielny pakiet Pythona, który zawiera zestaw powiązanych plików w określonym celu. Projekt Django może zawierać dowolną liczbę aplikacji, co odzwierciedla fakt, że host internetowy może obsługiwać dowolną liczbę oddzielnych punktów wejścia z jednej nazwy domeny. Na przykład projekt Django dla domeny, takiej jak contoso.com, może zawierać jedną aplikację dla, `www.contoso.com`drugą aplikację dla support.contoso.com i trzecią aplikację dla docs.contoso.com. W takim przypadku projekt Django obsługuje routing adresów URL na poziomie witryny i ustawienia (w *urls.py* i *settings.py* plików), podczas gdy każda aplikacja ma swój własny, odrębny styl i zachowanie poprzez wewnętrzną routing, widoki, modele, pliki statyczne i interfejs administracyjny.

Aplikacja Django zazwyczaj zaczyna się od standardowego zestawu plików. Visual Studio udostępnia szablony elementów do inicjowania aplikacji Django w projekcie Django, wraz ze zintegrowanym poleceniem menu, które służy temu sameu celowi:

- Szablony: W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Dodaj** > **nowy element**. W oknie dialogowym **Dodawanie nowego elementu** wybierz szablon aplikacji **Django 1.9,** określ nazwę aplikacji w polu **Nazwa** i wybierz **przycisk OK**.

- Zintegrowane polecenie: W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz pozycję **Dodaj** > **aplikację Django**. To polecenie monituje o nazwę i tworzy aplikację Django 1.9.

    ![Polecenie Menu do dodawania aplikacji Django](media/django/step02-add-django-app-command.png)

Korzystając z jednej z tych metod, utwórz aplikację o nazwie "HelloDjangoApp". Wynikiem jest folder w projekcie o tej nazwie, który zawiera elementy opisane w poniższej tabeli.

![Pliki aplikacji Django w Eksploratorze rozwiązań](media/django/step02-django-app-in-solution-explorer.png)

| Element | Opis |
| --- | --- |
| **\_\_init\_\_.py** | Plik, który identyfikuje aplikację jako pakiet. |
| **Migracji** | Folder, w którym Django przechowuje skrypty, które aktualizują bazę danych, aby wyrównać ze zmianami w modelach. Narzędzia migracji Django następnie zastosować niezbędne zmiany do poprzedniej wersji bazy danych, tak aby dopasować bieżące modele. Korzystając z migracji, kładziesz nacisk na modele i pozwalasz Django obsługiwać podstawowy schemat bazy danych. Migracje są omówione w kroku 6; na razie folder po prostu zawiera * \_ \_plik .py init\_\_* (wskazujący, że folder definiuje własny pakiet Pythona). |
| **szablonów** | Folder szablonów stron Django zawierający pojedynczy plik *index.html* w folderze pasującym do nazwy aplikacji. (W programie Visual Studio 2017 15.7 i wcześniejszych, plik znajduje się bezpośrednio w *szablonach* i krok 2-4 nakazuje utworzenie podfolderu.) Szablony to bloki HTML, do których widoki mogą dodawać informacje do dynamicznego renderowania strony. Szablon strony "zmienne", `{{ content }}` takie jak w *index.html,* są symbolami zastępczymi dla wartości dynamicznych, jak wyjaśniono w dalszej części tego artykułu (krok 2). Zazwyczaj aplikacje Django tworzą obszar nazw dla swoich szablonów, umieszczając je w podfolderze, który pasuje do nazwy aplikacji. |
| **admin.py** | Plik Języka Python, w którym można rozszerzyć interfejs administracyjny aplikacji (patrz krok 6), który jest używany do wysiewu i edycji danych w bazie danych. Początkowo ten plik zawiera tylko `from django.contrib import admin`instrukcję , . Domyślnie Django zawiera standardowy interfejs administracyjny za pośrednictwem wpisów w pliku *settings.py* projektu Django, który można włączyć, odkomentowywanie istniejących wpisów w *urls.py*. |
| **apps.py** | Plik języka Python, który definiuje klasę konfiguracji dla aplikacji (zobacz poniżej, po tej tabeli). |
| **models.py** | Modele są obiektami danych identyfikowane przez funkcje, za pomocą których widoki współdziałają z podstawową bazą danych aplikacji (zobacz krok 6). Django udostępnia warstwę połączenia bazy danych, dzięki czemu aplikacje nie muszą zajmować się tymi szczegółami. Plik *models.py* jest domyślnym miejscem do tworzenia modeli i początkowo zawiera tylko `from django.db import models`instrukcję , . |
| **tests.py** | Plik języka Python, który zawiera podstawową strukturę testów jednostkowych. |
| **views.py** | Widoki są zazwyczaj uważane za strony sieci web, które przyjmują żądanie HTTP i zwracają odpowiedź HTTP. Widoki są zazwyczaj renderowane w formacie HTML, który przeglądarki internetowe wiedzą, jak wyświetlać, ale widok niekoniecznie musi być widoczny (np. forma pośrednia). Widok jest zdefiniowany przez funkcję Języka Python, której obowiązkiem jest renderowanie kodu HTML do wysłania do przeglądarki. Views.py *views.py* plik jest domyślnym miejscem do tworzenia widoków i początkowo zawiera `from django.shortcuts import render`tylko instrukcję , . |

Zawartość *apps.py* pojawia się w następujący sposób podczas używania nazwy "HelloDjangoApp":

```python
from django.apps import AppConfig

class HelloDjangoAppConfig(AppConfig):
    name = 'HelloDjango'
```

### <a name="question-is-creating-a-django-app-in-visual-studio-any-different-from-creating-an-app-on-the-command-line"></a>Pytanie: Czy tworzenie aplikacji Django w programie Visual Studio różni się od tworzenia aplikacji w wierszu polecenia?

Odpowiedź: Uruchomienie polecenia **Dodaj** > **aplikację Django** lub użycie **polecenia Dodaj** > **nowy element** z szablonem aplikacji `manage.py startapp <app_name>`Django tworzy te same pliki, co polecenie Django. Zaletą tworzenia aplikacji w programie Visual Studio jest to, że folder aplikacji i wszystkie jego pliki są automatycznie zintegrowane z projektem. Za pomocą tego samego polecenia programu Visual Studio można utworzyć dowolną liczbę aplikacji w projekcie.

## <a name="step-2-2-run-the-app-from-the-django-project"></a>Krok 2-2: Uruchom aplikację z projektu Django

W tym momencie po ponownym uruchomieniu projektu w programie Visual Studio (za pomocą przycisku paska narzędzi lub **debugowania** > **rozpocznij debugowanie),** nadal jest widoczna strona domyślna. Nie ma zawartości aplikacji, ponieważ musisz zdefiniować stronę specyficzną dla aplikacji i dodać aplikację do projektu Django:

1. W folderze *HelloDjangoApp* zmodyfikuj *views.py,* aby dopasować poniższy kod, który definiuje widok o nazwie "indeks":

    ```python
    from django.shortcuts import render
    from django.http import HttpResponse

    def index(request):
        return HttpResponse("Hello, Django!")
    ```

1. W folderze *BasicProject* (utworzonym w kroku 1) zmodyfikuj *urls.py,* aby co najmniej odpowiadał poniższemu kodowi (możesz zachować komentarze pouczające, jeśli chcesz):

    ```python
    from django.conf.urls import include, url
    import HelloDjangoApp.views

    # Django processes URL patterns in the order they appear in the array
    urlpatterns = [
        url(r'^$', HelloDjangoApp.views.index, name='index'),
        url(r'^home$', HelloDjangoApp.views.index, name='home'),
    ]
    ```

    Każdy wzorzec adresu URL opisuje widoki, do których Django kieruje określone `https://www.domain.com/`adresy URL względne witryny (czyli część, która następuje). Pierwszy wpis `urlPatterns` rozpoczynający się od `^$` wyrażenia regularnego jest routingiem dla katalogu głównego witryny "/". Drugi wpis, `^home$` w szczególności trasy "/home". Można mieć dowolną liczbę marszrut do tego samego widoku.

1. Uruchom projekt ponownie, aby zobaczyć wiadomość **Hello, Django!** zgodnie z definicją w widoku. Zatrzymaj serwer po zakończeniu.

### <a name="commit-to-source-control"></a>Zatwierdzanie do kontroli źródła

Ponieważ wprowadzono zmiany w kodzie i przetestowano je pomyślnie, teraz jest świetny czas, aby przejrzeć i zatwierdzić zmiany do kontroli źródła. Dalsze kroki w tym samouczku przypominają o odpowiednich czasach, aby ponownie zobowiązać się do kontroli źródła i odesłać do tej sekcji.

1. Wybierz przycisk zmiany u dołu programu Visual Studio (zakreślony poniżej), który przechodzi do **Eksploratora zespołu**.

    ![Przycisk Zmiany formantu źródła na pasku stanu programu Visual Studio](media/django/step02-source-control-changes-button.png)

1. W **Eksploratorze zespołu**wprowadź komunikat o zatwierdzeniu, taki jak "Utwórz początkową aplikację Django" i wybierz pozycję **Zaprzyjmij wszystko**. Po zakończeniu zatwierdzania zostanie wyświetlony komunikat **Commit \<hash> utworzony lokalnie. Synchronizacja w celu udostępnienia zmian na serwerze.** Jeśli chcesz wypchnąć zmiany do zdalnego repozytorium, wybierz pozycję **Synchronizuj**, a następnie wybierz **pozycję Wypychaj** w obszarze **Zatwierdzeń wychodzących**. Można również gromadzić wiele lokalnych zatwierdzeń przed wypchnięciem do zdalnego.

    ![Wypychanie zatwierdzeń do zdalnego w Eksploratorze zespołu](media/django/step02-source-control-push-to-remote.png)

### <a name="question-what-is-the-r-prefix-before-the-routing-strings-for"></a>Pytanie: Co to jest prefiks "r" przed ciągami routingu?

Odpowiedź: Prefiks "r" na ciągu w języku Python oznacza "raw", który nakazuje Pythonowi, aby nie unikał żadnych znaków w ciągu. Ponieważ wyrażenia regularne używają wielu znaków specjalnych, użycie prefiksu "r" sprawia, że ciągi\\te są znacznie łatwiejsze do odczytania niż w przypadku, gdy zawierają one wiele znaków ucieczki.

### <a name="question-what-do-the--and--characters-mean-in-the-url-routing-entries"></a>Pytanie: Co oznaczają znaki ^ i $ we wpisach routingu adresów URL?

Odpowiedź: W wyrażeniach regularnych definiujących wzorce adresów URL ^ oznacza "początek wiersza", a $ oznacza "koniec wiersza", gdzie ponownie adresy URL są względem katalogu głównego witryny (następująca po nim `https://www.domain.com/`część ). Wyrażenie regularne `^$` skutecznie oznacza "puste" i dlatego `https://www.domain.com/` pasuje do pełnego adresu URL (nic nie dodane do katalogu głównego witryny). Wzór `^home$` pasuje dokładnie `https://www.domain.com/home/`. (Django nie używa trailing / w dopasowywaniu wzoru.)

Jeśli nie używasz końcowego $ w wyrażeniu regularnym, jak w `^home`przypadku , wzorzec adresu URL pasuje do *dowolnego* adresu URL, który zaczyna się od "home", "home", "homework", "homestead" i "home192837".

Aby eksperymentować z różnymi wyrażeniami regularnymi, wypróbuj narzędzia online, takie jak [regex101.com](https://regex101.com) w [pythex.org](https://www.pythex.org).

## <a name="step-2-3-render-a-view-using-html"></a>Krok 2-3: Renderowanie widoku przy użyciu kodu HTML

Funkcja, `index` która masz do tej pory w *views.py* generuje nic więcej niż zwykły tekst odpowiedzi HTTP dla strony. Większość rzeczywistych stron internetowych, oczywiście, odpowiada bogatymi stronami HTML, które często zawierają dane na żywo. Istotnie głównym powodem, aby zdefiniować widok za pomocą funkcji jest, dzięki czemu można wygenerować tę zawartość dynamicznie.

Ponieważ argument `HttpResponse` jest tylko ciągiem, można zbudować dowolny kod HTML, który ci się podoba w ciągu. Na prostym przykładzie `index` zastąp funkcję następującym `from` kodem (zachowanie istniejących instrukcji), który generuje odpowiedź HTML przy użyciu zawartości dynamicznej, która jest aktualizowana przy każdym odświeżaniu strony:

```python
from datetime import datetime

def index(request):
    now = datetime.now()

    html_content = "<html><head><title>Hello, Django</title></head><body>"
    html_content += "<strong>Hello Django!</strong> on " + now.strftime("%A, %d %B, %Y at %X")
    html_content += "</body></html>"

    return HttpResponse(html_content)
```

Uruchom projekt ponownie, aby zobaczyć komunikat w stylu "**Hello Django!** poniedziałek, 16 kwietnia 2018 o 16:28:10". Odśwież stronę, aby zaktualizować czas i potwierdzić, że zawartość jest generowana przy każdym żądaniu. Zatrzymaj serwer po zakończeniu.

> [!Tip]
> Skrótem do zatrzymania i ponownego uruchomienia projektu jest użycie polecenia menu > **Debugowania ponownie** **Debug****(Ctrl**+**Shift**+**F5)** lub przycisku Uruchom **ponownie** na pasku narzędzi debugowania:
>
> ![Przycisk Uruchom ponownie na pasku narzędzi debugowania w programie Visual Studio](media/debugging-restart-toolbar-button.png)

## <a name="step-2-4-render-a-view-using-a-page-template"></a>Krok 2-4: Renderowanie widoku przy użyciu szablonu strony

Generowanie HTML w kodzie działa dobrze dla bardzo małych stron, ale jak strony stają się bardziej wyrafinowane zazwyczaj chcesz zachować statyczne części HTML strony (wraz z odniesieniami do plików CSS i JavaScript) jako "szablony stron", do których następnie wstawić dynamiczne, treści generowanych przez kod. W poprzedniej sekcji tylko data i `now.strftime` godzina połączenia jest dynamiczna, co oznacza, że cała inna zawartość może być umieszczona w szablonie strony.

Szablon strony Django to blok HTML, który może zawierać dowolną liczbę tokenów zastępczych `{{` zwanych "zmiennymi", które są nakreślone przez i `}}`, jak w `{{ content }}`. Moduł szablonów Django zastępuje zmienne zawartością dynamiczną, którą podajesz w kodzie.

Poniższe kroki pokazują użycie szablonów stron:

1. W folderze *BasicProject,* który zawiera projekt Django, otwórz plik *settings.py* i dodaj nazwę aplikacji `INSTALLED_APPS` "HelloDjangoApp" do listy. Dodanie aplikacji do listy informuje projekt Django, że istnieje folder o tej nazwie zawierający aplikację:

    ```python
    INSTALLED_APPS = [
        'HelloDjangoApp',
        # Other entries...
    ]
    ```

1. Również w *settings.py,* upewnij się, że `TEMPLATES` obiekt zawiera następujący wiersz (domyślnie dołączony), który nakazuje Django szukać szablonów w folderze *szablonów* zainstalowanej aplikacji:

    ```json
    'APP_DIRS': True,
    ```

1. W folderze *HelloDjangoApp* otwórz plik szablonu *strony templates/HelloDjangoApp/index.html* (lub *templates/index.html* w programie VS 2017 15.7 lub `{{ content }}`starszym), aby zauważyć, że zawiera jedną zmienną:

    ```html
    <html>
    <head><title></title></head>

    <body>

    {{ content }}

    </body>
    </html>
    ```

1. W folderze *HelloDjangoApp* otwórz *views.py* i `index` zastąp funkcję następującym `django.shortcuts.render` kodem, który używa funkcji pomocnika. Pomocnik `render` zapewnia uproszczony interfejs do pracy z szablonami stron. Pamiętaj, aby zachować wszystkie istniejące `from` instrukcje.

    ```python
    from django.shortcuts import render   # Added for this step

    def index(request):
        now = datetime.now()

        return render(
            request,
            "HelloDjangoApp/index.html",  # Relative path from the 'templates' folder to the template file
            # "index.html", # Use this code for VS 2017 15.7 and earlier
            {
                'content': "<strong>Hello Django!</strong> on " + now.strftime("%A, %d %B, %Y at %X")
            }
        )
    ```

    Pierwszym argumentem `render`, jak widać, jest obiekt żądania, a następnie względna ścieżka do pliku szablonu w folderze *szablonów* aplikacji. Plik szablonu jest nazwany dla widoku, który obsługuje, w stosownych przypadkach. Trzeci argument `render` jest następnie słownik zmiennych, które odwołuje się do szablonu. W słowniku można dołączać obiekty, w którym to przypadku `{{ object.property }}`zmienna w szablonie może odnosić się do programu .

1. Uruchom projekt i obserwuj dane wyjściowe. Powinien zostać wyświetlony komunikat podobny do tego, który jest widoczny w kroku 2-2, wskazujący, że szablon działa.

    Należy jednak zauważyć, że kod `content` HTML użyty we właściwości `render` renderuje tylko jako zwykły tekst, ponieważ funkcja automatycznie unika tego kodu HTML. Automatyczne ucieczki zapobiegają przypadkowym lukom w zabezpieczeniach ataków iniekcji: deweloperzy często zbierają dane wejściowe z jednej strony i używają ich jako wartości w innej za pośrednictwem symbolu zastępczego szablonu. Ucieczka służy również jako przypomnienie, że znowu najlepiej jest zachować HTML w szablonie strony i poza kodem. Na szczęście jest to prosta sprawa, aby utworzyć dodatkowe zmienne w razie potrzeby. Na przykład zmień *index.html* z szablonami, aby dopasować następujące *znaczniki,* które dodaje tytuł strony i zachowuje całe formatowanie w szablonie strony:

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
        </head>
        <body>
            <strong>{{ message }}</strong>{{ content }}
        </body>
    </html>
    ```

    Następnie zapisz `index` funkcję widoku w następujący sposób, aby podać wartości dla wszystkich zmiennych w szablonie strony:

    ```python
    def index(request):
        now = datetime.now()

        return render(
            request,
            "HelloDjangoApp/index.html",  # Relative path from the 'templates' folder to the template file
            # "index.html", # Use this code for VS 2017 15.7 and earlier
            {
                'title' : "Hello Django",
                'message' : "Hello Django!",
                'content' : " on " + now.strftime("%A, %d %B, %Y at %X")
            }
        )
    ```

1. Zatrzymaj serwer i uruchom ponownie projekt i obserwuj, że strona jest teraz renderowana poprawnie:

    ![Uruchamianie aplikacji przy użyciu szablonu](media/django/step02-result.png)

1. <a name="template-namespacing"></a>Visual Studio 2017 w wersji 15.7 i wcześniejszych: W końcowym kroku przenieś szablony do podfolderu o nazwie taka sama jak aplikacja, która tworzy obszar nazw i pozwala uniknąć potencjalnych konfliktów z innymi aplikacjami, które można dodać do projektu. (Szablony w programie VS 2017 15.8+ robią to automatycznie). Oznacza to, że utwórz podfolder w *szablonach* o nazwie *HelloDjangoApp*, `index` przenieś *index.html* do tego podfolderu i zmodyfikuj funkcję widoku, aby odwoływać się do nowej ścieżki szablonu, *HelloDjangoApp/index.html*. Następnie uruchom projekt, sprawdź, czy strona jest renderowana poprawnie, i zatrzymaj serwer.

1. Zaajmuj zmiany w kontroli źródła i aktualizuj zdalne repozytorium, w razie potrzeby, zgodnie z opisem w [kroku 2-2](#commit-to-source-control).

### <a name="question-do-page-templates-have-to-be-in-a-separate-file"></a>Pytanie: Czy szablony stron muszą znajdować się w osobnym pliku?

Odpowiedź: Chociaż szablony są zwykle przechowywane w oddzielnych plikach HTML, można również użyć szablonu wbudowanego. Zaleca się jednak użycie oddzielnego pliku w celu zachowania czystej separacji między znacznikami a kodem.

### <a name="question-must-templates-use-the-html-file-extension"></a>Pytanie: Czy szablony muszą używać rozszerzenia pliku .html?

Odpowiedź: Rozszerzenie *.html* dla plików szablonów stron jest całkowicie opcjonalne, ponieważ zawsze identyfikujesz `render` dokładną ścieżkę względną do pliku w drugim argumie do funkcji. Jednak visual studio (i innych edytorów) zazwyczaj daje funkcje, takie jak uzupełnianie kodu i zabarwienie składni z plikami *.html,* co przewyższa fakt, że szablony stron nie są ściśle HTML.

W rzeczywistości podczas pracy z projektem Django program Visual Studio automatycznie wykrywa, kiedy edytowany plik HTML jest w rzeczywistości szablonem Django i zapewnia pewne funkcje automatycznego uzupełniania. Na przykład po rozpoczęciu wpisywania komentarza szablonu strony Django `{#`program `#}` Visual Studio automatycznie udostępnia znaki zamykające. Polecenia **Wybór komentarza** i **Odkomentowanie (w** menu **Edytuj** > **zaawansowane** i na pasku narzędzi) używają również komentarzy szablonów zamiast komentarzy HTML.

### <a name="question-when-i-run-the-project-i-see-an-error-that-the-template-cannot-be-found-whats-wrong"></a>Pytanie: Po uruchomieniu projektu pojawia się błąd, że nie można odnaleźć szablonu. Co jest nie tak?

Odpowiedź: Jeśli widzisz błędy, których nie można znaleźć szablonu, upewnij się, że aplikacja została dodana do *settings.py* projektu Django na `INSTALLED_APPS` liście. Bez tego wpisu Django nie będzie wiedział, aby szukać w folderze *szablonów* aplikacji.

### <a name="question-why-is-template-namespacing-important"></a>Pytanie: Dlaczego nazwa szablonu jest ważna?

Odpowiedź: Gdy Django szuka szablonu, `render` o którym mowa w funkcji, używa dowolnego pliku, który znajdzie najpierw, który pasuje do ścieżki względnej. Jeśli masz wiele aplikacji Django w tym samym projekcie, które używają tych samych struktur folderów dla szablonów, prawdopodobnie jedna aplikacja nieumyślnie użyje szablonu z innej aplikacji. Aby uniknąć takich błędów, należy zawsze utworzyć podfolder w folderze *szablonów* aplikacji, który pasuje do nazwy aplikacji, aby uniknąć powielania.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Obsługa plików statycznych, dodawanie stron i używanie dziedziczenia szablonów](learn-django-in-visual-studio-step-03-serve-static-files-and-add-pages.md)

## <a name="go-deeper"></a>Głębiej

- [Pisanie pierwszej aplikacji Django, część 1 - widoki](https://docs.djangoproject.com/en/2.0/intro/tutorial01/#write-your-first-view) (docs.djangoproject.com)
- Aby uzyskać więcej możliwości szablonów Django, takich jak zawiera i dziedziczenie, zobacz [Język szablonu Django](https://docs.djangoproject.com/en/2.0/ref/templates/language/) (docs.djangoproject.com)
- [Szkolenie z wyrażeń regularnych na inLearning](https://www.linkedin.com/learning/topics/regular-expressions) (LinkedIn)
- Kod źródłowy samouczka na GitHub: [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)

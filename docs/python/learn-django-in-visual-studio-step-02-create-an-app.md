---
title: Poznaj samouczek Django w programie Visual Studio w kroku 2, widoki i szablony stron
titleSuffix: ''
description: Przewodnik po podstawy Django w kontekście projektów programu Visual Studio, w szczególności kroki tworzenia aplikacji i korzystanie z widoków i szablonów.
ms.date: 11/19/2018
ms.prod: visual-studio-dev15
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: ce819f5d0a7167c4fce2871894df7c6edd26e6a6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53871706"
---
# <a name="step-2-create-a-django-app-with-views-and-page-templates"></a>Krok 2. Tworzenie aplikacji Django przy użyciu widoków i szablonów stron

**Poprzedniego kroku: [Tworzenie projektu programu Visual Studio i rozwiązania](learn-django-in-visual-studio-step-01-project-and-solution.md)**

Posiadane przez Ciebie do tej pory w projekt programu Visual Studio są tylko składniki poziomie witryny Django *projektu*, które można uruchomić co najmniej jeden Django *aplikacji*. Następnym krokiem jest, aby utworzyć swoją pierwszą aplikację za pomocą pojedynczej strony.

W tym kroku teraz dowiesz się, jak:

> [!div class="checklist"]
> - Tworzenie aplikacji Django z jednej strony (krok 2 - 1)
> - Uruchom aplikację z projektu Django (krok 2 z 2)
> - Renderowania widoku przy użyciu języka HTML (krok 2 – 3)
> - Renderowanie widoku, używając szablonu strony Django (krok 2 – 4)

## <a name="step-2-1-create-an-app-with-a-default-structure"></a>Krok 1 z 2 Tworzenie aplikacji z domyślnej struktury

Aplikacja Django jest oddzielny pakiet języka Python, który zawiera zestaw powiązanych plików w określonym celu. Projekt Django może zawierać dowolną liczbę aplikacji, która odzwierciedla fakt, że host sieci web może obsługiwać dowolną liczbę punktów oddzielny wpis z pojedynczą nazwę domeny. Na przykład projekt Django dla domeny, np. contoso.com może zawierać jedną aplikację www.contoso.com, drugą aplikację dla support.contoso.com i trzeci aplikację dla docs.contoso.com. W tym przypadku projekt Django obsługuje routing adresów URL i ustawień poziomie witryny (w jego *urls.py* i *settings.py* plików), a każda aplikacja ma swoją własną odrębnych stylów i działanie za pomocą wewnętrznej Routing, widoki, modele, pliki statyczne i interfejsu administracyjnego.

Aplikacja Django zwykle zaczyna się od standardowego zestawu plików. Program Visual Studio udostępnia szablony elementów, aby zainicjować aplikację Django, w ramach projektu Django, wraz z zintegrowanym polecenie, który służy do tego samego celu:

- Szablony: W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz **Dodaj** > **nowy element**. W **Dodaj nowy element** okno dialogowe, wybierz opcję **Django 1.9 aplikacji** szablonu, należy określić nazwę aplikacji w **nazwa** i wybierz przycisk **OK**.

- Polecenie zintegrowane: W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz **Dodaj** > **aplikacji Django**. To polecenie wyświetli monit o podanie nazwy i tworzy aplikację Django 1.9.

    ![Polecenia menu dodawania aplikacji Django](media/django/step02-add-django-app-command.png)

Przy użyciu jednej z metod, tworzenie aplikacji o nazwie "HelloDjangoApp". Wynik jest folderem w projekcie przy użyciu tej nazwy, która zawiera elementy, zgodnie z opisem w tabeli znajdującej się poniżej.

![Pliki aplikacji Django w Eksploratorze rozwiązań](media/django/step02-django-app-in-solution-explorer.png)

| Element | Opis |
| --- | --- |
| **\_\_init\_\_.py** | Plik, który identyfikuje aplikację jako pakiet. |
| **Migracje** | Folder, w którym Django przechowuje skrypty, które aktualizują bazę danych, aby wyrównać ze zmianami do modeli. Narzędzia migracji w Django następnie zastosować wymagane zmiany do poprzednich wersji bazy danych, aby był zgodny z bieżącym modeli. Za pomocą migracji, nadal możesz skoncentrować się na swoje modele i pozwól Django obsługi podstawowy schemat bazy danych. Migracje zostały omówione w kroku 6. teraz, po prostu zawiera folder  *\_ \_init\_\_PY* pliku (co oznacza, że folder definiuje swój własny pakiet języka Python). |
| **Szablony** | Folder zawierający pojedynczy plik szablony stron Django *index.html* w folderze pasujące do nazwy aplikacji. (W programie Visual Studio 2017 w wersji 15.7 i starszych plik znajduje się bezpośrednio pod *szablony* kroku 2 – 4 obydwa te elementy do tworzenia tego podfolderu.) Szablony są bloki kodu HTML, do którego widoki mogą dodawać informacje, aby powodować dynamiczne renderowanie strony. Takie jak strona "zmienne szablonu," `{{ content }}` w *index.html*, jest symboli zastępczych dla wartości dynamicznych, zgodnie z opisem w dalszej części tego artykułu (krok 2). Zazwyczaj aplikacje Django utworzenia przestrzeni nazw swoje szablony, umieszczając je w podfolderze, która jest zgodna z nazwą aplikacji. |
| **Admin.PY** | Plik języka Python, w którym możesz rozszerzyć aplikację użytkownika administracyjnego interfejsu (zobacz krok 6), używany do umieszczenia i edytować dane w bazie danych. Początkowo ten plik zawiera tylko instrukcja `from django.contrib import admin`. Domyślnie Django zawiera standardowy interfejs administracyjny za pośrednictwem wpisów w projekcie Django *settings.py* pliku, który można włączyć, trwa usuwanie komentarza do istniejących wpisów *urls.py*. |
| **Apps.PY** | Plik języka Python, który definiuje klasę konfiguracji dla aplikacji (zobacz poniżej pod tą tabelą). |
| **models.PY** | Modele są obiekty danych, identyfikowany przez funkcje, za pomocą których widoki interakcji z podstawowej bazy danych aplikacji (zobacz krok 6). Django zapewnia warstwę połączenia bazy danych, dzięki czemu nie trzeba zajmować się te szczegóły aplikacji. *Models.py* plików jest miejscem domyślna, w której chcesz utworzyć swoje modele i początkowo zawiera tylko instrukcja `from django.db import models`. |
| **Tests.PY** | Plik języka Python, który zawiera podstawowej struktury testów jednostkowych. |
| **Views.PY** | Widoki są na tym, co zwykle sądzisz o jako strony sieci web, które przyjmują żądania HTTP i zwracają odpowiedź HTTP. Widoki zwykle renderowane jako HTML, który sposób wyświetlania przeglądarki sieci web, ale widoku nie zawsze musi być widoczny (na przykład formularz pośredniego). Widok jest definiowany przez funkcję języka Python, którego zadaniem jest do renderowania elementów HTML do wysłania do przeglądarki. *Views.py* plik jest miejsce domyślny, w którym można tworzyć widoki i początkowo zawiera tylko instrukcja `from django.shortcuts import render`. |

Zawartość *app.py* pojawia się w następujący sposób, gdy przy użyciu nazwy "HelloDjangoApp":

```python
from django.apps import AppConfig

class HelloDjangoAppConfig(AppConfig):
    name = 'HelloDjango'
```

### <a name="question-is-creating-a-django-app-in-visual-studio-any-different-from-creating-an-app-on-the-command-line"></a>Pytanie: Tworzy aplikację Django w programie Visual Studio inaczej niż Tworzenie aplikacji w wierszu polecenia?

Odpowiedź: Uruchamianie **Dodaj** > **aplikacji Django** polecenia lub przy użyciu **Dodaj** > **nowy element** za pomocą szablonu aplikacji Django Tworzy tych samych plików w ramach polecenia Django `manage.py startapp <app_name>`. Do tworzenia aplikacji w programie Visual Studio ma folderu aplikacji i wszystkie jego pliki są automatycznie zintegrowane do projektu. Można użyć tego samego polecenia programu Visual Studio, można utworzyć dowolną liczbę aplikacji w projekcie.

## <a name="step-2-2-run-the-app-from-the-django-project"></a>Krok 2 z 2 Uruchom aplikację z projektu Django

Jeśli na tym etapie, ponownie uruchom projekt w programie Visual Studio (przy użyciu przycisku paska narzędzi lub **debugowania** > **Rozpocznij debugowanie**), nadal wyświetlić domyślną stronę. Brak zawartości aplikacji pojawia się, ponieważ musisz zdefiniowana strona specyficzny dla aplikacji i dodać ją do projektu Django:

1. W *HelloDjangoApp* folder, Modyfikuj *views.py* do dopasowania poniższego kodu, który definiuje widoku o nazwie "index":

    ```python
    from django.shortcuts import render
    from django.http import HttpResponse

    def index(request):
        return HttpResponse("Hello, Django!")
    ```

1. W *BasicProject* folder (utworzonego w kroku 1), zmodyfikuj *urls.py* do co najmniej odpowiadać następujący kod (można zachować instruktażowy komentarze, jeśli chcesz):

    ```python
    from django.conf.urls import include, url
    import HelloDjangoApp.views

    # Django processes URL patterns in the order they appear in the array
    urlpatterns = [
        url(r'^$', HelloDjangoApp.views.index, name='index'),
        url(r'^home$', HelloDjangoApp.views.index, name='home'),
    ]
    ```

    Każdy wzorzec adresu URL w tym artykule opisano widoki, do których Django kieruje określone adresy URL określony względem witryny (oznacza to, że fragment, który następuje po `https://www.domain.com/`). Pierwszy wpis `urlPatterns` który zaczyna się od wyrażenia regularnego `^$` jest routingu dla katalogu głównego witryny, "/". Drugi wpis `^home$` specjalnie kieruje "/ home". Może mieć dowolną liczbę marszrut do tego samego widoku.

1. Uruchom projekt ponownie, aby zobaczyć komunikat **Witaj, Django!** zgodnie z definicją widoku. Gdy skończysz, Zatrzymaj serwer.

### <a name="commit-to-source-control"></a>Zapewnij kontrole źródła

Ponieważ wprowadzono zmiany w kodzie, a następnie zostały one przetestowane pomyślnie, teraz jest to doskonały moment, aby przejrzeć i zatwierdzić zmiany do kontroli źródła. Wykonania kolejnych kroków tego samouczka przypomnienia o odpowiedniej razy, aby ponownie zatwierdzić do kontroli źródła, a następnie wrócić do tej sekcji.

1. Wybierz przycisk zmiany wzdłuż dolnej części programu Visual Studio (w kółkach poniżej), która przechodzi do **Team Explorer**.

    ![Przycisk zmiany kontroli źródła na pasku stanu programu Visual Studio](media/django/step02-source-control-changes-button.png)

1. W **Team Explorer**, wprowadź wiadomość dotyczącą zatwierdzenia, takie jak "Tworzenie aplikacji Django początkowej" i wybierz **Zatwierdź wszystko**. Po zakończeniu zatwierdzenie, zostanie wyświetlony komunikat **zatwierdzenia \<skrótu > utworzone lokalnie. Synchronizacji, aby udostępnić zmiany na serwerze.** Aby wypchnąć zmiany do repozytorium zdalnego, należy zaznaczyć **synchronizacji**, a następnie wybierz **wypychania** w obszarze **zatwierdzeń wychodzących**. Wiele lokalnych zatwierdzeń, przed wypchnięciem do zdalnego również może wzrosnąć.

    ![Wypychanie zatwierdzeń do zdalnego w programie Team Explorer](media/django/step02-source-control-push-to-remote.png)

### <a name="question-what-is-the-r-prefix-before-the-routing-strings-for"></a>Pytanie: Co to jest prefiks "r" przed routingu ciągi dla?

Odpowiedź: Prefiks "r" w ciągu w języku Python oznacza "pierwotne", który powoduje, że Python wyprowadza znaków w ciągu. Ponieważ wyrażenia regularne mogą używać wielu znaków specjalnych, przy użyciu prefiksu "r" sprawia, że te ciągi znacznie łatwiejsze do odczytania niż, jeśli ich zawierała kilka "\\" znaki ucieczki.

### <a name="question-what-do-the--and--characters-mean-in-the-url-routing-entries"></a>Pytanie: Co zrobić, ^ znaków $ oznaczają we wpisach routingu adresów URL i?

Odpowiedź: W wyrażeniach regularnych, które definiują wzorce adresów URL ^ oznacza "start wiersza" i oznacza, że $ "koniec wiersza," gdzie ponownie adresy URL są względem katalogu głównego witryny (part, który następuje po `https://www.domain.com/`). Wyrażenie regularne `^$` skutecznie oznacza, że "blank" i w związku z tym pasuje pełnego adresu URL `https://www.domain.com/` (niczego nie dodane do katalogu głównego witryny). Wzorzec `^home$` dopasowuje dokładnie `https://www.domain.com/home/`. (Django nie używają końcowych / w dopasowywanie do wzorców).

Jeśli nie używasz końcowe $ w wyrażeniu regularnym, podobnie jak w przypadku `^home`, a następnie dopasowuje wzorzec adresu URL *wszelkie* adresu URL, który rozpoczyna się od "home", takich jak "domowy", "przydzielaj", "homestead" i "home192837".

Aby eksperymentować z różnych wyrażeń regularnych, spróbuj online narzędzia takie jak [regex101.com](https://regex101.com) na [pythex.org](https://www.pythex.org).

## <a name="step-2-3-render-a-view-using-html"></a>Krok 2-3: Renderowania widoku przy użyciu języka HTML

`index` Funkcja, która należy do tej pory w *views.py* nie więcej niż odpowiedzi HTTP zwykłego tekstu dla strony. Większość rzeczywistych stron sieci web, oczywiście, odpowiedź z rozbudowanych strony HTML, które często obejmują dane na żywo. W rzeczywistości głównym powodem, aby zdefiniować widoku, używając funkcji jest więc można dynamicznie wygenerować tę zawartość.

Ponieważ argument `HttpResponse` jest po prostu określonym ciągiem utworzenia wewnątrz ciągu, takich jak kod HTML. Prosty przykład zastąpić `index` funkcji następującym kodem (utrzymywanie istniejących `from` instrukcji), która generuje odpowiedzi HTML przy użyciu zawartości dynamicznej, która jest aktualizowana przy każdym odświeżeniu strony:

```python
from datetime import datetime

def index(request):
    now = datetime.now()

    html_content = "<html><head><title>Hello, Django</title></head><body>"
    html_content += "<strong>Hello Django!</strong> on " + now.strftime("%A, %d %B, %Y at %X")
    html_content += "</body></html>"

    return HttpResponse(html_content)
```

Uruchom projekt ponownie, aby wyświetlić komunikat podobny do "**Django Hello!** w każdy poniedziałek, 16 kwietnia 2018 r. o 16:28:10 ". Odśwież stronę Aby zaktualizować czasu i upewnij się, że zawartość jest generowany z każdym żądaniem. Gdy skończysz, Zatrzymaj serwer.

> [!Tip]
> Skrót do zatrzymywania i ponownego uruchamiania projektu jest użycie **debugowania** > **ponowne uruchomienie** polecenia menu (**Ctrl**+**Shift**  + **F5**) lub **ponowne uruchomienie** przycisk na pasku narzędzi debugowania:
>
> ![Uruchom ponownie przycisk na pasku narzędzi debugowania w programie Visual Studio](media/debugging-restart-toolbar-button.png)

## <a name="step-2-4-render-a-view-using-a-page-template"></a>Krok 2 – 4: Renderowanie widoku, używając szablonu strony

Generowanie kodu HTML w kodzie działa prawidłowo dla stron bardzo małe, ale jak strony Pobierz bardziej zaawansowane zazwyczaj chcesz zachować statycznych elementów kodu HTML na stronie (wraz z odwołania do plików CSS i JavaScript) jako "strony templates", do których należy następnie Wstaw dynamiczny, wygenerowany kod zawartość. W poprzedniej sekcji, tylko datę i godzinę z `now.strftime` wywołanie jest dynamiczny, co oznacza, wszelką inną zawartością można umieścić w szablonie strony.

Szablon strony Django to blok kodu HTML, który może zawierać dowolną liczbę tokenów zastąpienia o nazwie "zmienne" które są rozdzielone przez `{{` i `}}`, jak w `{{ content }}`. Moduł szablonów firmy Django następnie zamienia zmienne zawartości dynamicznej, która zapewnia w kodzie.

Poniższe kroki pokazują użycie szablonów stron:

1. W obszarze *BasicProject* Otwórz folder zawierający projekt Django *settings.py* pliku i Dodaj do nazwy aplikacji "HelloDjangoApp" `INSTALLED_APPS` listy. Dodawanie aplikacji do listy informuje aplikację Django, że są folder o takiej nazwie zawierającego aplikację:

    ```python
    INSTALLED_APPS = [
        'HelloDjangoApp',
        # Other entries...
    ]
    ```

1. Również w *settings.py*, upewnij się, że `TEMPLATES` obiekt zawiera następujący wiersz (domyślnie), który powoduje, że Django, aby wyszukać szablony w zainstalowanej aplikacji *szablony* folderu:

    ```json
    'APP_DIRS': True,
    ```

1. W *HelloDjangoApp* folder, otwórz *templates/HelloDjangoApp/index.html* plik szablonu strony (lub *templates/index.html* w wersji 15.7 programu VS 2017 i starszych), Sprawdź, czy zawiera on jedną zmienną `{{ content }}`:

    ```html
    <html>
    <head><title></title></head>

    <body>

    {{ content }}

    </body>
    </html>
    ```

1. W *HelloDjangoApp* folder, otwórz *views.py* i Zastąp `index` funkcji następującym kodem, który używa `django.shortcuts.render` funkcji pomocnika. `render` Pomocnika oferuje uproszczony interfejs do pracy z szablonami strony. Pamiętaj zachować wszystkie istniejące `from` instrukcji.

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

    Pierwszy argument `render`, jak widać, to obiekt żądania, następuje względną ścieżkę do pliku szablonu w ramach aplikacji *szablony* folderu. Plik szablonu nosi nazwę dla widoku, który ją obsługuje, jeśli to stosowne. Trzeci argument `render` jest następnie słownika zmiennych, które szablon, który odwołuje się do. Mogą znajdować się obiekty w słowniku, w którym to przypadku zmienna w szablonie mogą odwoływać się do `{{ object.property }}`.

1. Uruchom projekt i sprawdzanie danych wyjściowych. Wyświetlony podobny komunikat, jak pokazano w kroku 2-2, wskazujący, że szablon działa.

    Sprawdź, że kod HTML, możesz użyć w `content` właściwości powoduje wyświetlenie tylko jako zwykły tekst, ponieważ `render` funkcja automatycznie specjalne tego HTML. Automatyczne anulowania zapewnianego element zapobiec przypadkowemu luk w zabezpieczeniach na ataki przez iniekcję kodu: deweloperzy często zbierania danych wejściowych z jednej strony i użyć jej jako wartości w drugiej za pomocą symbolu zastępczego szablonu. Anulowanie służy również jako przypomnienie, że ponownie jest najlepiej trzymać HTML w szablonie strony i z kodu. Na szczęście go polega po prostu utworzyć dodatkowe zmienne w razie potrzeby. Na przykład zmienić *index.html* z *szablony* aby dopasować następujący kod, który dodaje tytuł strony i przechowuje wszystkie formatowania w szablonie strony:

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

    Następnie zapisywać `index` widok, funkcji w następujący sposób, podaj wartości dla wszystkich zmiennych z szablonu strony:

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

1. Zatrzymaj serwer ponownego uruchomienia projektu i sprawdź, czy strona teraz renderuje prawidłowo:

    ![Uruchamianie aplikacji przy użyciu szablonu](media/django/step02-result.png)

1. <a name="template-namespacing"></a>Visual Studio 2017 w wersji 15.7 i starszych: W ostatnim kroku należy przenieść szablonów do podfolderu o nazwie taka sama jak aplikację, która tworzy przestrzeń nazw i pozwala uniknąć potencjalnych konfliktów z innymi aplikacjami, które można dodać do projektu. (Szablony w programie VS 2017 15.8 + zrobić to dla Ciebie automatycznie.) Oznacza to, utwórz podfolder w *szablony* o nazwie *HelloDjangoApp*, Przenieś *index.html* do tego podfolderu i modyfikować `index` funkcji do odwoływania się do wyświetlenia Nowa ścieżka tego szablonu, *HelloDjangoApp/index.html*. Uruchom projekt, Sprawdź poprawnie renderuje stronę i zatrzymać serwer.

1. Zatwierdź zmiany do kontroli źródła i zaktualizować repozytorium zdalnego, jeśli to konieczne, zgodnie z opisem w [krok 2 z 2](#commit-to-source-control).

### <a name="question-do-page-templates-have-to-be-in-a-separate-file"></a>Pytanie: Szablony stron mają znajdować się w oddzielnym pliku?

Odpowiedź: Mimo że szablony są zazwyczaj obsługiwane w oddzielnych plikach HTML, można też użyć szablonu wbudowanego. Przy użyciu oddzielnych plików jest zalecane, jednak do obsługi czystą separacji między znaczników i kodu.

### <a name="question-must-templates-use-the-html-file-extension"></a>Pytanie: Szablony korzystać tylko z rozszerzeniem pliku HTML?

Odpowiedź: *.Html* rozszerzenie dla plików szablonów strony jest opcjonalne, ponieważ zawsze zidentyfikować dokładną ścieżkę względną do pliku w drugi argument `render` funkcji. Jednak program Visual Studio (i innych edytorów) zazwyczaj zapewnia funkcje, takie jak kod zakończenia i składnia barwy z *.html* pliki, które przewyższa fakt, że stronie Szablony nie są ściśle HTML.

W rzeczywistości podczas pracy z projektem Django, Visual Studio automatycznie wykrywa, gdy plik HTML, który jest edytowany jest faktycznie szablonem Django i zapewnia niektórych funkcji autouzupełniania. Na przykład, po rozpoczęciu wpisywania Django komentarz szablon strony `{#`, Visual Studio automatycznie umożliwia zamknięcie `#}` znaków. **Dodaj komentarz do zaznaczenia** i **Usuń komentarz zaznaczenia** poleceń (na **Edytuj** > **zaawansowane** menu i na pasku narzędzi) komentarze szablonu można także użyć zamiast komentarze HTML.

### <a name="question-when-i-run-the-project-i-see-an-error-that-the-template-cannot-be-found-whats-wrong"></a>Pytanie: Uruchomienie projektu, widzę błąd, którego nie można odnaleźć szablonu. Co jest nie tak?

Odpowiedź: Jeśli widzisz błędy, których nie można znaleźć szablonu, upewnij się, aplikacja może zostać dodana do projektu Django *settings.py* w `INSTALLED_APPS` listy. Bez tego wpisu Django nie będzie wiedzieć, aby zobaczyć w aplikacji *szablony* folderu.

### <a name="question-why-is-template-namespacing-important"></a>Pytanie: Dlaczego ważne jest, namespacing szablonu?

Odpowiedź: Gdy Django szuka szablonu, określone w `render` funkcji używa niezależnie od znajdzie pierwszy plik, zgodna ze ścieżką względną. Jeśli masz wiele aplikacji Django w tym samym projekcie, które używają tej samej struktury folderów dla szablonów, prawdopodobnie, co aplikacja użyje przypadkowo szablonu z innej aplikacji. Aby uniknąć takich błędów, zawsze Utwórz podfolder w aplikacji *szablony* folder, który jest zgodna z nazwą aplikacji, aby uniknąć jego duplikowania wszystkie.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Obsługa plików statycznych, dodawanie stron i użyć szablonu dziedziczenia](learn-django-in-visual-studio-step-03-serve-static-files-and-add-pages.md)

## <a name="go-deeper"></a>Przejdź dalej

- [Zapisywanie swoją pierwszą aplikację Django, część 1 — widoki](https://docs.djangoproject.com/en/2.0/intro/tutorial01/#write-your-first-view) (docs.djangoproject.com)
- Aby uzyskać więcej możliwości Django szablony, takie jak obejmuje i dziedziczenie, zobacz [język szablonu Django](https://docs.djangoproject.com/en/2.0/ref/templates/language/) (docs.djangoproject.com)
- [Wyrażenie regularne szkolenie dotyczące inLearning](https://www.linkedin.com/learning/topics/regular-expressions) (LinkedIn)
- Kod źródłowy samouczek w witrynie GitHub: [Microsoft/python — przykładowe vs uczenia — django](https://github.com/Microsoft/python-sample-vs-learning-django)

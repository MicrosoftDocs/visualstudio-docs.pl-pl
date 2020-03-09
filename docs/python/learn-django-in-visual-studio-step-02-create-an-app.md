---
title: Poznaj samouczek Django w programie Visual Studio w kroku 2, widoki i szablony stron
titleSuffix: ''
description: Przewodnik po podstawy Django w kontekście projektów programu Visual Studio, w szczególności kroki tworzenia aplikacji i korzystanie z widoków i szablonów.
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
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409422"
---
# <a name="step-2-create-a-django-app-with-views-and-page-templates"></a>Krok 2: Tworzenie aplikacji Django z widoków i szablonów stron

**Poprzedni krok: [Tworzenie projektu i rozwiązania programu Visual Studio](learn-django-in-visual-studio-step-01-project-and-solution.md)**

W projekcie programu Visual Studio to wszystko, co jest dotąd dostępne tylko dla składników na poziomie witryny *projektu*Django, które mogą uruchamiać jedną lub więcej *aplikacji*Django. Następnym krokiem jest, aby utworzyć swoją pierwszą aplikację za pomocą pojedynczej strony.

W tym kroku teraz dowiesz się, jak:

> [!div class="checklist"]
> - Tworzenie aplikacji Django z jednej strony (krok 2 - 1)
> - Uruchom aplikację z projektu Django (krok 2 z 2)
> - Renderowania widoku przy użyciu języka HTML (krok 2 – 3)
> - Renderowanie widoku, używając szablonu strony Django (krok 2 – 4)

## <a name="step-2-1-create-an-app-with-a-default-structure"></a>Krok 1 z 2: tworzenie aplikacji z domyślnej struktury

Aplikacja Django jest oddzielny pakiet języka Python, który zawiera zestaw powiązanych plików w określonym celu. Projekt Django może zawierać dowolną liczbę aplikacji, która odzwierciedla fakt, że host sieci web może obsługiwać dowolną liczbę punktów oddzielny wpis z pojedynczą nazwę domeny. Na przykład projekt Django dla domeny, takiej jak contoso.com, może zawierać jedną aplikację do `www.contoso.com`, drugą aplikację dla support.contoso.com i trzecią aplikację dla docs.contoso.com. W takim przypadku projekt Django obsługuje Routing i ustawienia adresów URL na poziomie witryny (w plikach *URLs.py* i *Settings.py* ), natomiast każda aplikacja ma własne odrębne style i zachowanie za pomocą wewnętrznych routingu, widoków, modeli, plików statycznych i interfejsu administracyjnego.

Aplikacja Django zwykle zaczyna się od standardowego zestawu plików. Program Visual Studio udostępnia szablony elementów, aby zainicjować aplikację Django, w ramach projektu Django, wraz z zintegrowanym polecenie, który służy do tego samego celu:

- Szablony: w **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz pozycję **Dodaj** > **nowy element**. W oknie dialogowym **Dodaj nowy element** wybierz szablon **aplikacji Django 1,9** , określ nazwę aplikacji w polu **Nazwa** , a następnie wybierz **przycisk OK**.

- Zintegrowane polecenie: w **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Dodaj** > **Django aplikację**. To polecenie wyświetli monit o podanie nazwy i tworzy aplikację Django 1.9.

    ![Polecenia menu dodawania aplikacji Django](media/django/step02-add-django-app-command.png)

Przy użyciu jednej z metod, tworzenie aplikacji o nazwie "HelloDjangoApp". Wynik jest folderem w projekcie przy użyciu tej nazwy, która zawiera elementy, zgodnie z opisem w tabeli znajdującej się poniżej.

![Pliki aplikacji Django w Eksploratorze rozwiązań](media/django/step02-django-app-in-solution-explorer.png)

| Element | Opis |
| --- | --- |
| **\_\_init\_\_. PR** | Plik, który identyfikuje aplikację jako pakiet. |
| **Migracje** | Folder, w którym Django przechowuje skrypty, które aktualizują bazę danych, aby wyrównać ze zmianami do modeli. Narzędzia migracji w Django następnie zastosować wymagane zmiany do poprzednich wersji bazy danych, aby był zgodny z bieżącym modeli. Za pomocą migracji, nadal możesz skoncentrować się na swoje modele i pozwól Django obsługi podstawowy schemat bazy danych. Migracje zostały omówione w kroku 6. na razie folder po prostu zawiera *\_\_init\_\_. PR* (wskazuje, że folder definiuje własny pakiet języka Python). |
| **templates** | Folder dla szablonów stron Django zawierający pojedynczy plik *index. html* w folderze zgodnym z nazwą aplikacji. (W programie Visual Studio 2017 15,7 i starszych) plik jest zawarty bezpośrednio w *szablonach* i krok 2-4 instruuje o utworzeniu podfolderu. Szablony są blokami HTML, w których widoki mogą dodawać informacje do dynamicznego renderowania strony. Szablon strony "zmienne", takie jak `{{ content }}` w *pliku index. html*, są symbolami zastępczymi dla wartości dynamicznych, jak wyjaśniono w dalszej części tego artykułu (krok 2). Zazwyczaj aplikacje Django utworzenia przestrzeni nazw swoje szablony, umieszczając je w podfolderze, która jest zgodna z nazwą aplikacji. |
| **admin.py** | Plik języka Python, w którym możesz rozszerzyć aplikację użytkownika administracyjnego interfejsu (zobacz krok 6), używany do umieszczenia i edytować dane w bazie danych. Początkowo ten plik zawiera tylko instrukcję, `from django.contrib import admin`. Domyślnie Django zawiera standardowy interfejs administracyjny za pomocą wpisów w pliku *Settings.py* projektu Django, który można włączyć przez usunięcie komentarza istniejących wpisów w *URLs.py*. |
| **apps.py** | Plik języka Python, który definiuje klasę konfiguracji dla aplikacji (zobacz poniżej pod tą tabelą). |
| **models.py** | Modele są obiekty danych, identyfikowany przez funkcje, za pomocą których widoki interakcji z podstawowej bazy danych aplikacji (zobacz krok 6). Django zapewnia warstwę połączenia bazy danych, dzięki czemu nie trzeba zajmować się te szczegóły aplikacji. Plik *models.py* jest domyślnym miejscem, w którym można tworzyć modele i początkowo zawiera tylko te instrukcje, `from django.db import models`. |
| **tests.py** | Plik języka Python, który zawiera podstawowej struktury testów jednostkowych. |
| **views.py** | Widoki są na tym, co zwykle sądzisz o jako strony sieci web, które przyjmują żądania HTTP i zwracają odpowiedź HTTP. Widoki zwykle renderowane jako HTML, który sposób wyświetlania przeglądarki sieci web, ale widoku nie zawsze musi być widoczny (na przykład formularz pośredniego). Widok jest definiowany przez funkcję języka Python, którego zadaniem jest do renderowania elementów HTML do wysłania do przeglądarki. Plik *views.py* jest domyślnym miejscem, w którym można tworzyć widoki, a początkowo zawiera tylko instrukcję, `from django.shortcuts import render`. |

Zawartość *Apps.py* pojawia się w następujący sposób przy użyciu nazwy "HelloDjangoApp":

```python
from django.apps import AppConfig

class HelloDjangoAppConfig(AppConfig):
    name = 'HelloDjango'
```

### <a name="question-is-creating-a-django-app-in-visual-studio-any-different-from-creating-an-app-on-the-command-line"></a>Pytanie: Tworzy aplikację Django w programie Visual Studio inaczej niż Tworzenie aplikacji w wierszu polecenia?

Odpowiedź: uruchomienie polecenia **add** > **Django App** lub użycie opcji **Dodaj** > **nowy element** z szablonem aplikacji Django powoduje te same pliki co `manage.py startapp <app_name>`polecenia Django. Do tworzenia aplikacji w programie Visual Studio ma folderu aplikacji i wszystkie jego pliki są automatycznie zintegrowane do projektu. Można użyć tego samego polecenia programu Visual Studio, można utworzyć dowolną liczbę aplikacji w projekcie.

## <a name="step-2-2-run-the-app-from-the-django-project"></a>Krok 2 z 2: uruchamianie aplikacji z projektu Django

W tym momencie, jeśli ponownie uruchomisz projekt w programie Visual Studio (za pomocą przycisku paska narzędzi lub **debugowania** > **Rozpocznij debugowanie**), nadal zobaczysz stronę domyślną. Brak zawartości aplikacji pojawia się, ponieważ musisz zdefiniowana strona specyficzny dla aplikacji i dodać ją do projektu Django:

1. W folderze *HelloDjangoApp* zmodyfikuj *views.py* w taki sposób, aby pasował do poniższego kodu, który definiuje widok o nazwie "index":

    ```python
    from django.shortcuts import render
    from django.http import HttpResponse

    def index(request):
        return HttpResponse("Hello, Django!")
    ```

1. W folderze *BasicProject* (utworzonym w kroku 1) zmodyfikuj *URLs.py* do co najmniej zgodnego z poniższym kodem (możesz zachować Komentarze z instrukcjami, jeśli chcesz):

    ```python
    from django.conf.urls import include, url
    import HelloDjangoApp.views

    # Django processes URL patterns in the order they appear in the array
    urlpatterns = [
        url(r'^$', HelloDjangoApp.views.index, name='index'),
        url(r'^home$', HelloDjangoApp.views.index, name='home'),
    ]
    ```

    Każdy wzorzec adresów URL opisuje widoki, do których Django kieruje konkretne adresy URL względne względem witryny (to jest część, która następuje po `https://www.domain.com/`). Pierwszy wpis w `urlPatterns`, który rozpoczyna się od wyrażenia regularnego, `^$` jest trasą dla katalogu głównego witryny "/". Drugi wpis `^home$`, a w przypadku trasy "/Home". Może mieć dowolną liczbę marszrut do tego samego widoku.

1. Uruchom ponownie projekt, aby zobaczyć komunikat **Hello, Django!** zgodnie z definicją widoku. Gdy skończysz, Zatrzymaj serwer.

### <a name="commit-to-source-control"></a>Zapewnij kontrole źródła

Ponieważ wprowadzono zmiany w kodzie, a następnie zostały one przetestowane pomyślnie, teraz jest to doskonały moment, aby przejrzeć i zatwierdzić zmiany do kontroli źródła. Wykonania kolejnych kroków tego samouczka przypomnienia o odpowiedniej razy, aby ponownie zatwierdzić do kontroli źródła, a następnie wrócić do tej sekcji.

1. Wybierz przycisk zmiany w dolnej części programu Visual Studio (kółko poniżej), które przechodzi do **Team Explorer**.

    ![Przycisk zmiany kontroli źródła na pasku stanu programu Visual Studio](media/django/step02-source-control-changes-button.png)

1. W **Team Explorer**wprowadź komunikat dotyczący zatwierdzenia, taki jak "Tworzenie początkowej aplikacji Django", i wybierz pozycję **Zatwierdź wszystko**. Po zakończeniu zatwierdzania zostanie wyświetlony komunikat **zatwierdzenie \<> utworzone lokalnie. Synchronizuj, aby udostępnić zmiany na serwerze.** Jeśli chcesz wypchnąć zmiany do zdalnego repozytorium, wybierz pozycję **Synchronizuj**, a następnie wybierz pozycję **wypychanie** w obszarze **zatwierdzenia wychodzące**. Wiele lokalnych zatwierdzeń, przed wypchnięciem do zdalnego również może wzrosnąć.

    ![Wypychanie zatwierdzeń do zdalnego w programie Team Explorer](media/django/step02-source-control-push-to-remote.png)

### <a name="question-what-is-the-r-prefix-before-the-routing-strings-for"></a>Pytanie: Co to jest prefiks "r" przed routingu ciągi dla?

Odpowiedź: Prefiks "r" w ciągu w języku Python oznacza "pierwotne" który powoduje, że języka Python, aby nie wprowadzić dowolne znaki ciągu. Ponieważ wyrażenia regularne używają wielu znaków specjalnych, użycie prefiksu "r" sprawia, że te ciągi są znacznie łatwiejsze do odczytu, niż w przypadku, gdy zawierają liczbę znaków ucieczki "\\".

### <a name="question-what-do-the--and--characters-mean-in-the-url-routing-entries"></a>Pytanie: Co zrobić, ^ znaków $ oznaczają we wpisach routingu adresów URL i?

Odpowiedź: w wyrażeniach regularnych definiujących wzorce adresów URL ^ oznacza "początek wiersza" i $ oznacza "koniec wiersza", gdzie ponownie adresy URL są względne dla katalogu głównego witryny (część, która następuje po `https://www.domain.com/`). Wyrażenie regularne `^$` efektywnie oznacza "puste" i w związku z tym dopasowuje pełny adres URL `https://www.domain.com/` (nic nie dodano do katalogu głównego witryny). Wzorzec `^home$` dopasowuje dokładnie `https://www.domain.com/home/`. (Django nie używają końcowych / w dopasowywanie do wzorców).

Jeśli nie używasz końcowej $ w wyrażeniu regularnym, podobnie jak w przypadku `^home`, wzorzec adresu URL *pasuje do* adresu URL zaczynającego się od "Home" ("Home", "HomeGroup", "Homestead" i "home192837").

Aby eksperymentować z różnymi wyrażeniami regularnymi, wypróbuj narzędzia online, takie jak [regex101.com](https://regex101.com) na [pythex.org](https://www.pythex.org).

## <a name="step-2-3-render-a-view-using-html"></a>Krok 2-3: renderowania widoku przy użyciu języka HTML

Funkcja `index`, która jest dotąd w *views.py* , nie generuje więcej niż zwykły tekst odpowiedzi HTTP dla strony. Większość rzeczywistych stron sieci web, oczywiście, odpowiedź z rozbudowanych strony HTML, które często obejmują dane na żywo. W rzeczywistości głównym powodem, aby zdefiniować widoku, używając funkcji jest więc można dynamicznie wygenerować tę zawartość.

Ponieważ argument `HttpResponse` jest tylko ciągiem, można utworzyć dowolny kod HTML, który lubisz w ciągu. W prostym przykładzie Zastąp funkcję `index` poniższym kodem (utrzymując istniejące instrukcje `from`), które generuje odpowiedź HTML przy użyciu zawartości dynamicznej, która jest aktualizowana za każdym razem, gdy odświeżasz stronę:

```python
from datetime import datetime

def index(request):
    now = datetime.now()

    html_content = "<html><head><title>Hello, Django</title></head><body>"
    html_content += "<strong>Hello Django!</strong> on " + now.strftime("%A, %d %B, %Y at %X")
    html_content += "</body></html>"

    return HttpResponse(html_content)
```

Uruchom ponownie projekt, aby zobaczyć komunikat podobny do "**Hello Django!** w każdy poniedziałek, 16 kwietnia 2018 r. o 16:28:10 ". Odśwież stronę Aby zaktualizować czasu i upewnij się, że zawartość jest generowany z każdym żądaniem. Gdy skończysz, Zatrzymaj serwer.

> [!Tip]
> Skrót do zatrzymywania i ponownego uruchamiania projektu to użycie polecenia **debuguj** > **restart** menu (**Ctrl**+**SHIFT**+**F5**) lub przycisk **Uruchom ponownie** na pasku narzędzi debugowania:
>
> ![Uruchom ponownie przycisk na pasku narzędzi debugowania w programie Visual Studio](media/debugging-restart-toolbar-button.png)

## <a name="step-2-4-render-a-view-using-a-page-template"></a>Krok 2 – 4: renderowania widoku, używając szablonu strony

Generowanie kodu HTML w kodzie działa prawidłowo dla stron bardzo małe, ale jak strony Pobierz bardziej zaawansowane zazwyczaj chcesz zachować statycznych elementów kodu HTML na stronie (wraz z odwołania do plików CSS i JavaScript) jako "strony templates", do których należy następnie Wstaw dynamiczny, wygenerowany kod zawartość. W poprzedniej sekcji tylko data i godzina wywołania `now.strftime` jest dynamiczna, co oznacza, że cała zawartość może zostać umieszczona w szablonie strony.

Szablon strony Django jest blokiem HTML, który może zawierać dowolną liczbę tokenów zastępczych o nazwie "zmienne", które są nakreślone przez `{{` i `}}`, jak w `{{ content }}`. Moduł szablonów firmy Django następnie zamienia zmienne zawartości dynamicznej, która zapewnia w kodzie.

Poniższe kroki pokazują użycie szablonów stron:

1. W folderze *BasicProject* , który zawiera projekt Django, otwórz plik *Settings.py* i Dodaj nazwę aplikacji "HelloDjangoApp" do listy `INSTALLED_APPS`. Dodawanie aplikacji do listy informuje aplikację Django, że są folder o takiej nazwie zawierającego aplikację:

    ```python
    INSTALLED_APPS = [
        'HelloDjangoApp',
        # Other entries...
    ]
    ```

1. W programie *Settings.py*upewnij się, że obiekt `TEMPLATES` zawiera następujący wiersz (domyślnie włączony), który instruuje Django, aby wyszukać szablony w folderze *szablonów* zainstalowanej aplikacji:

    ```json
    'APP_DIRS': True,
    ```

1. W folderze *HelloDjangoApp* Otwórz plik szablonu strony *templates/HelloDjangoApp/index.html* (lub *templates/index.html* w programie vs 2017 15,7 i starsze), aby sprawdzić, czy zawiera on jedną zmienną, `{{ content }}`:

    ```html
    <html>
    <head><title></title></head>

    <body>

    {{ content }}

    </body>
    </html>
    ```

1. W folderze *HelloDjangoApp* Otwórz *views.py* i Zastąp funkcję `index` poniższym kodem, który używa funkcji pomocnika `django.shortcuts.render`. Pomocnik `render` udostępnia uproszczony interfejs do pracy z szablonami stron. Pamiętaj, aby zachować wszystkie istniejące `from` instrukcji.

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

    Pierwszy argument do `render`, jak widać, jest obiektem żądania, a następnie ścieżką względną do pliku szablonu w folderze *szablonów* aplikacji. Plik szablonu nosi nazwę dla widoku, który ją obsługuje, jeśli to stosowne. Trzeci argument `render` jest następnie słownik zmiennych, do których odwołuje się szablon. Można uwzględnić obiekty w słowniku, w którym to przypadku zmienna w szablonie może odwoływać się do `{{ object.property }}`.

1. Uruchom projekt i sprawdzanie danych wyjściowych. Wyświetlony podobny komunikat, jak pokazano w kroku 2-2, wskazujący, że szablon działa.

    Należy jednak zauważyć, że kod HTML użyty we właściwości `content` renderuje tylko jako zwykły tekst, ponieważ funkcja `render` automatycznie wyprowadza ten kod HTML. Automatyczne anulowania zapewnianego element zapobiec przypadkowemu luk w zabezpieczeniach na ataki przez iniekcję kodu: deweloperzy często zbierania danych wejściowych z jednej strony i użyć jej jako wartości w drugiej za pomocą symbolu zastępczego szablonu. Anulowanie służy również jako przypomnienie, że ponownie jest najlepiej trzymać HTML w szablonie strony i z kodu. Na szczęście go polega po prostu utworzyć dodatkowe zmienne w razie potrzeby. Na przykład zmień *plik index. html* z *szablonami* , aby pasował do poniższego znacznika, co spowoduje dodanie tytułu strony i zachowanie całego formatowania w szablonie strony:

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

    Następnie napisz `index` funkcję widoku w następujący sposób, aby podać wartości dla wszystkich zmiennych w szablonie strony:

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

1. <a name="template-namespacing"></a>Visual Studio 2017 w wersji 15,7 i starszej: w ostatnim kroku Przenieś szablony do podfolderu o nazwie takiej samej jak aplikacja, która tworzy przestrzeń nazw i pozwala uniknąć potencjalnych konfliktów z innymi aplikacjami, które mogą zostać dodane do projektu. (Szablony w programie VS 2017 15.8 + zrób to automatycznie). Oznacza to, że należy utworzyć podfolder w *szablonach* o nazwie *HelloDjangoApp*, przenieść *index. html* do tego podfolderu i zmodyfikować funkcję widoku `index`, aby odwołać się do nowej ścieżki szablonu, *HelloDjangoApp/index.html*. Uruchom projekt, Sprawdź poprawnie renderuje stronę i zatrzymać serwer.

1. Zatwierdź zmiany w kontroli źródła i zaktualizuj zdalne repozytorium, jeśli to konieczne, zgodnie z opisem w [kroku 2-2](#commit-to-source-control).

### <a name="question-do-page-templates-have-to-be-in-a-separate-file"></a>Pytanie: Czy szablony stron muszą znajdować się w oddzielnym pliku?

Odpowiedź: Mimo że szablony są zazwyczaj obsługiwane w oddzielnych plikach HTML, umożliwia także szablonem wbudowanego. Przy użyciu oddzielnych plików jest zalecane, jednak do obsługi czystą separacji między znaczników i kodu.

### <a name="question-must-templates-use-the-html-file-extension"></a>Pytanie: Szablony korzystać tylko z rozszerzeniem pliku HTML?

Odpowiedź: rozszerzenie *. html* dla plików szablonów stron jest całkowicie opcjonalne, ponieważ należy zawsze identyfikować dokładną ścieżkę względną do pliku w drugim argumencie funkcji `render`. Jednak program Visual Studio (i inne redaktorzy) zwykle udostępnia funkcje, takie jak uzupełnianie kodu i zabarwienie składni z plikami *. html* , co pozwala na przeważenie faktu, że szablony stron nie są wyłącznie w formacie HTML.

W rzeczywistości podczas pracy z projektem Django, Visual Studio automatycznie wykrywa, gdy plik HTML, który jest edytowany jest faktycznie szablonem Django i zapewnia niektórych funkcji autouzupełniania. Na przykład po rozpoczęciu wpisywania komentarza do szablonu strony Django `{#`program Visual Studio automatycznie poda zamykane znaki `#}`. Polecenia **zaznaczania komentarza** i usuwania **komentarzy** (w menu **Edytuj** > **Zaawansowane** i na pasku narzędzi) również używają komentarzy szablonu zamiast komentarzy HTML.

### <a name="question-when-i-run-the-project-i-see-an-error-that-the-template-cannot-be-found-whats-wrong"></a>Pytanie: Uruchamiania projektu, I może zostać wyświetlony komunikat nie można odnaleźć szablonu. Co jest nie tak?

Odpowiedź: Jeśli widzisz błędy, których szablon nie można znaleźć, upewnij się, że aplikacja została dodana do *Settings.py* projektu Django na liście `INSTALLED_APPS`. Bez tego wpisu Django nie będzie wiadomo, aby szukać w folderze *szablonów* aplikacji.

### <a name="question-why-is-template-namespacing-important"></a>Pytanie: Dlaczego jest szablon namespacing istotne?

Odpowiedź: gdy Django szuka szablonu, do którego odwołuje się w funkcji `render`, używa dowolnego pliku, który znajduje się w pierwszej kolejności zgodnej ze ścieżką względną. Jeśli masz wiele aplikacji Django w tym samym projekcie, które używają tej samej struktury folderów dla szablonów, prawdopodobnie, co aplikacja użyje przypadkowo szablonu z innej aplikacji. Aby uniknąć takich błędów, należy zawsze utworzyć podfolder w folderze *szablonów* aplikacji, który jest zgodny z nazwą aplikacji, aby uniknąć wszystkich duplikacji.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Korzystanie z plików statycznych, dodawanie stron i dziedziczenie szablonów](learn-django-in-visual-studio-step-03-serve-static-files-and-add-pages.md)

## <a name="go-deeper"></a>Przejdź dalej

- [Pisanie pierwszej aplikacji Django, część 1 — widoki](https://docs.djangoproject.com/en/2.0/intro/tutorial01/#write-your-first-view) (docs.djangoproject.com)
- Aby uzyskać więcej możliwości szablonów Django, takich jak Dołączanie i dziedziczenie, zobacz [Django Template Language](https://docs.djangoproject.com/en/2.0/ref/templates/language/) (docs.djangoproject.com).
- [Szkolenie dotyczące wyrażenia regularnego w trakcie zdobywania informacji](https://www.linkedin.com/learning/topics/regular-expressions) (LinkedIn)
- Kod źródłowy samouczka w witrynie GitHub: [Microsoft/Python-Sample-vs-Learning-Django](https://github.com/Microsoft/python-sample-vs-learning-django)

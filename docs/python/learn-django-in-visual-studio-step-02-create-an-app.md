---
title: Poznaj samouczek Django w programie Visual Studio krok 2, widoki i szablony stron
titleSuffix: ''
description: Przewodnik po Django podstawy w kontekście projektów programu Visual Studio, w tym w tym kroki tworzenia aplikacji i korzystania z widoków i szablonów.
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "89314176"
---
# <a name="step-2-create-a-django-app-with-views-and-page-templates"></a>Krok 2. Tworzenie aplikacji Django za pomocą widoków i szablonów stron

**Poprzedni krok: [Tworzenie projektu i rozwiązania programu Visual Studio](learn-django-in-visual-studio-step-01-project-and-solution.md)**

W projekcie programu Visual Studio to wszystko, co jest dotąd dostępne tylko dla składników na poziomie witryny *projektu*Django, które mogą uruchamiać jedną lub więcej *aplikacji*Django. Następnym krokiem jest utworzenie pierwszej aplikacji przy użyciu jednej strony.

W tym kroku dowiesz się, jak:

> [!div class="checklist"]
> - Tworzenie aplikacji Django za pomocą pojedynczej strony (krok 2-1)
> - Uruchamianie aplikacji z projektu Django (krok 2-2)
> - Renderowanie widoku przy użyciu języka HTML (krok 2-3)
> - Renderowanie widoku przy użyciu szablonu strony Django (krok 2-4)

## <a name="step-2-1-create-an-app-with-a-default-structure"></a>Krok 2-1: Tworzenie aplikacji z domyślną strukturą

Aplikacja Django to oddzielny pakiet języka Python, który zawiera zestaw powiązanych plików do określonego celu. Projekt Django może zawierać dowolną liczbę aplikacji, co odzwierciedla fakt, że host sieci Web może obsługiwać dowolną liczbę oddzielnych punktów wejścia z pojedynczej nazwy domeny. Na przykład projekt Django dla domeny, takiej jak contoso.com, może zawierać jedną aplikację dla aplikacji `www.contoso.com` , drugą aplikację dla support.contoso.com i trzecią aplikację dla docs.contoso.com. W takim przypadku projekt Django obsługuje Routing i ustawienia adresów URL na poziomie witryny (w plikach *URLs.py* i *Settings.py* ), natomiast każda aplikacja ma własne odrębne style i zachowanie za pomocą wewnętrznych routingu, widoków, modeli, plików statycznych i interfejsu administracyjnego.

Aplikacja Django zazwyczaj rozpoczyna się od standardowego zestawu plików. Program Visual Studio udostępnia szablony elementów umożliwiające zainicjowanie aplikacji Django w projekcie Django oraz zintegrowane polecenie menu, które służy do tego samego celu:

- Szablony: w **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Dodaj**  >  **nowy element**. W oknie dialogowym **Dodaj nowy element** wybierz szablon **aplikacji Django 1,9** , określ nazwę aplikacji w polu **Nazwa** , a następnie wybierz **przycisk OK**.

- Zintegrowane polecenie: w **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Dodaj**  >  **aplikację Django**. To polecenie poprosi o nazwę i utworzy aplikację Django 1,9.

    ![Polecenie menu do dodawania aplikacji Django](media/django/step02-add-django-app-command.png)

Przy użyciu jednej z metod Utwórz aplikację o nazwie "HelloDjangoApp". Wynik jest folderem w projekcie o tej nazwie, która zawiera elementy, zgodnie z opisem w poniższej tabeli.

![Pliki aplikacji Django w Eksplorator rozwiązań](media/django/step02-django-app-in-solution-explorer.png)

| Element | Opis |
| --- | --- |
| **\_\_init \_ \_ . PR** | Plik, który identyfikuje aplikację jako pakiet. |
| **Migracje** | Folder, w którym Django przechowuje skrypty, które aktualizują bazę danych, aby były wyrównane ze zmianami modeli. Narzędzia migracji Django następnie stosują niezbędne zmiany do dowolnej starszej wersji bazy danych, aby były zgodne z bieżącymi modelami. Korzystając z migracji, możesz zachować fokus na modelach i Django obsłużyć bazowy schemat bazy danych. Migracje zostały omówione w kroku 6. na razie folder po prostu zawiera plik * \_ \_ init \_ \_ . PR* (wskazujący, że folder definiuje własny pakiet w języku Python). |
| **templates** | Folder szablonów stron Django zawierający pojedynczy plik *index.html* w folderze zgodnym z nazwą aplikacji. (W programie Visual Studio 2017 15,7 i starszych) plik jest zawarty bezpośrednio w *szablonach* i krok 2-4 instruuje o utworzeniu podfolderu. Szablony są blokami HTML, w których widoki mogą dodawać informacje do dynamicznego renderowania strony. Szablon strony "zmienne", takie jak `{{ content }}` w *index.html*, są symbolami zastępczymi dla wartości dynamicznych, jak wyjaśniono w dalszej części tego artykułu (krok 2). Zazwyczaj aplikacje Django tworzą przestrzeń nazw dla swoich szablonów, umieszczając je w podfolderze zgodnym z nazwą aplikacji. |
| **admin.py** | Plik języka Python, w którym można zwiększyć interfejs administracyjny aplikacji (zobacz krok 6), który jest używany do wypełniania i edytowania danych w bazie danych. Początkowo ten plik zawiera tylko instrukcję, `from django.contrib import admin` . Domyślnie Django zawiera standardowy interfejs administracyjny za pomocą wpisów w pliku *Settings.py* projektu Django, który można włączyć przez usunięcie komentarza istniejących wpisów w *URLs.py*. |
| **apps.py** | Plik języka Python, który definiuje klasę konfiguracyjną dla aplikacji (patrz poniżej, po tej tabeli). |
| **models.py** | Modele to obiekty danych identyfikowane przez funkcje, za pomocą których widoki współdziałają z podstawową bazą danych aplikacji (zobacz krok 6). Django zapewnia warstwę połączenia bazy danych, dzięki czemu aplikacje nie muszą zachodzić o te szczegóły. Plik *models.py* jest domyślnym miejscem, w którym można tworzyć modele i początkowo zawiera tylko te instrukcje `from django.db import models` . |
| **tests.py** | Plik języka Python, który zawiera podstawową strukturę testów jednostkowych. |
| **views.py** | Widoki są zwykle uznawane za strony sieci Web, które przyjmują żądanie HTTP i zwracają odpowiedź HTTP. Widoki są zwykle renderowane jako HTML, ponieważ przeglądarki sieci Web wiedzą, jak są wyświetlane, ale widok nie musi być widoczny (na przykład w postaci pośredniej). Widok jest definiowany przez funkcję języka Python, której odpowiedzialność jest renderowanie HTML w celu wysłania do przeglądarki. Plik *views.py* jest domyślnym miejscem, w którym można tworzyć widoki, a początkowo zawiera tylko te instrukcje `from django.shortcuts import render` . |

Zawartość *Apps.py* pojawia się w następujący sposób przy użyciu nazwy "HelloDjangoApp":

```python
from django.apps import AppConfig

class HelloDjangoAppConfig(AppConfig):
    name = 'HelloDjango'
```

### <a name="question-is-creating-a-django-app-in-visual-studio-any-different-from-creating-an-app-on-the-command-line"></a>Pytanie: czy tworzysz aplikację Django w programie Visual Studio, która różni się od tworzenia aplikacji w wierszu polecenia?

Odpowiedź: uruchomienie polecenia **Add**  >  **Django App** lub użycie opcji **Dodaj**  >  **nowy element** z szablonem aplikacji Django powoduje te same pliki co polecenie Django `manage.py startapp <app_name>` . Zaletą tworzenia aplikacji w programie Visual Studio jest to, że folder aplikacji i wszystkie jego pliki są automatycznie integrowane z projektem. Możesz użyć tego samego polecenia programu Visual Studio, aby utworzyć dowolną liczbę aplikacji w projekcie.

## <a name="step-2-2-run-the-app-from-the-django-project"></a>Krok 2-2: uruchamianie aplikacji z projektu Django

W tym momencie, jeśli ponownie uruchomisz projekt w programie Visual Studio (za pomocą przycisku paska narzędzi **Debug**lub  >  **debugowania rozpoczęcia**debugowania), nadal zobaczysz stronę domyślną. Nie zostanie wyświetlona żadna zawartość aplikacji, ponieważ musisz zdefiniować stronę specyficzną dla aplikacji i dodać aplikację do projektu Django:

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

    Każdy wzorzec adresów URL opisuje widoki, do których Django kieruje konkretne adresy URL względne względem witryny (czyli część, która znajduje się poniżej `https://www.domain.com/` ). Pierwszym wpisem `urlPatterns` rozpoczynającym się od wyrażenia regularnego `^$` jest Routing dla katalogu głównego witryny "/". Drugi wpis, w tym `^home$` trasy "/Home". Możesz mieć dowolną liczbę routingu do tego samego widoku.

1. Uruchom ponownie projekt, aby zobaczyć komunikat **Hello, Django!** zgodnie z definicją w widoku. Zatrzymaj serwer po zakończeniu.

### <a name="commit-to-source-control"></a>Zatwierdzenie do kontroli źródła

Ponieważ wprowadzono zmiany w kodzie i przetestowano je pomyślnie, to teraz świetny czas na przejrzenie i zatwierdzenie zmian w kontroli źródła. W kolejnych krokach w tym samouczku dowiesz się, jak chcesz ponownie przekazać kontrolę źródła, i zapoznaj się z powrotem z tą sekcją.

1. Wybierz przycisk zmiany w dolnej części programu Visual Studio (kółko poniżej), które przechodzi do **Team Explorer**.

    ![Przycisk zmiany kontroli źródła na pasku stanu programu Visual Studio](media/django/step02-source-control-changes-button.png)

1. W **Team Explorer**wprowadź komunikat dotyczący zatwierdzenia, taki jak "Tworzenie początkowej aplikacji Django", i wybierz pozycję **Zatwierdź wszystko**. Po zakończeniu zatwierdzania zostanie wyświetlone **zatwierdzenie wiadomości \<hash> utworzone lokalnie. Synchronizuj, aby udostępnić zmiany na serwerze.** Jeśli chcesz wypchnąć zmiany do zdalnego repozytorium, wybierz pozycję **Synchronizuj**, a następnie wybierz pozycję **wypychanie** w obszarze **zatwierdzenia wychodzące**. Możesz również zbierać wiele lokalnych zatwierdzeń przed wypchnięciem do zdalnego.

    ![Zatwierdzeń wypychania do zdalnego w Team Explorer](media/django/step02-source-control-push-to-remote.png)

### <a name="question-what-is-the-r-prefix-before-the-routing-strings-for"></a>Pytanie: co to jest prefiks "r" przed ciągami routingu?

Odpowiedź: prefiks "r" w ciągu w języku Python oznacza "RAW", który powoduje, że język Python nie zwraca żadnych znaków w ciągu. Ponieważ wyrażenia regularne używają wielu znaków specjalnych, użycie prefiksu "r" sprawia, że te ciągi są znacznie łatwiejsze do odczytu, niż w przypadku, gdy zawierają liczbę \\ znaków ucieczki "".

### <a name="question-what-do-the--and--characters-mean-in-the-url-routing-entries"></a>Pytanie: co oznaczają znaki ^ i $ w wpisach routingu URL?

Odpowiedź: w wyrażeniach regularnych, które definiują wzorce adresów URL, ^ oznacza "początek wiersza" i $ oznacza "koniec wiersza", gdzie ponownie adresy URL są względne w stosunku do katalogu głównego witryny (w poniższej części `https://www.domain.com/` ). Wyrażenie regularne `^$` efektywnie oznacza "puste" i w związku z tym dopasowuje pełny adres URL `https://www.domain.com/` (nic nie zostało dodane do katalogu głównego witryny). Wzorzec `^home$` pasuje dokładnie `https://www.domain.com/home/` . (Django nie używa wzorca końcowego/w dopasowaniu).

Jeśli nie używasz końcowej $ w wyrażeniu regularnym, podobnie jak w przypadku `^home` , wzorzec adresu URL dopasowuje *dowolny* adres URL zaczynający się od "Home" ("Home", "HomeGroup", "Homestead" i "home192837").

Aby eksperymentować z różnymi wyrażeniami regularnymi, wypróbuj narzędzia online, takie jak [regex101.com](https://regex101.com) na [pythex.org](https://www.pythex.org).

## <a name="step-2-3-render-a-view-using-html"></a>Krok 2-3: renderowanie widoku przy użyciu języka HTML

`index`Funkcja, która jest dotąd w *views.py* , nie generuje więcej niż zwykły tekst odpowiedzi HTTP dla strony. W przypadku większości rzeczywistych stron sieci Web należy odpowiedzieć na Zaawansowane strony HTML, które często zawierają dane na żywo. W związku z tym podstawową przyczyną zdefiniowania widoku przy użyciu funkcji jest to, że można wygenerować tę zawartość dynamicznie.

Ponieważ argumentem `HttpResponse` jest tylko ciąg, można utworzyć dowolny kod HTML, który lubisz w ciągu. Jako prosty przykład Zastąp `index` funkcję następującym kodem (utrzymując istniejące `from` instrukcje), który GENERUJE odpowiedź HTML przy użyciu zawartości dynamicznej, która jest aktualizowana za każdym razem, gdy odświeżasz stronę:

```python
from datetime import datetime

def index(request):
    now = datetime.now()

    html_content = "<html><head><title>Hello, Django</title></head><body>"
    html_content += "<strong>Hello Django!</strong> on " + now.strftime("%A, %d %B, %Y at %X")
    html_content += "</body></html>"

    return HttpResponse(html_content)
```

Uruchom ponownie projekt, aby zobaczyć komunikat podobny do "**Hello Django!** w poniedziałek, 16 kwietnia, 2018 o 16:28:10 ". Odśwież stronę, aby zaktualizować czas i potwierdzić, że zawartość jest generowana przy użyciu każdego żądania. Zatrzymaj serwer po zakończeniu.

> [!Tip]
> Skrót do zatrzymywania i ponownego uruchamiania projektu to użycie polecenia **Debuguj**  >  **ponowne uruchomienie** menu (**Ctrl** + **SHIFT** + **F5**) lub przycisk **Uruchom ponownie** na pasku narzędzi debugowania:
>
> ![Przycisk Uruchom ponownie na pasku narzędzi debugowania w programie Visual Studio](media/debugging-restart-toolbar-button.png)

## <a name="step-2-4-render-a-view-using-a-page-template"></a>Krok 2-4: renderowanie widoku przy użyciu szablonu strony

Generowanie kodu HTML w kodzie działa prawidłowo w przypadku bardzo małych stron, ale w miarę jak strony są bardziej zaawansowane, zazwyczaj należy zachować statyczne składniki HTML strony (wraz z odwołaniami do plików CSS i JavaScript) jako "szablony stron", w których następnie wstawić dynamiczną, wygenerowaną w kodzie zawartość. W poprzedniej sekcji tylko data i godzina `now.strftime` wywołania jest dynamiczna, co oznacza, że cała zawartość może zostać umieszczona w szablonie strony.

Szablon strony Django jest blokiem HTML, który może zawierać dowolną liczbę tokenów zastępczych o nazwie "zmienne", które są rozdzielone przez `{{` i `}}` , jak w `{{ content }}` . Moduł tworzenia szablonów Django następnie zastępuje zmienne z zawartością dynamiczną dostarczaną w kodzie.

Poniższe kroki pokazują, jak korzystać z szablonów stron:

1. W folderze *BasicProject* , który zawiera projekt Django, otwórz plik *Settings.py* i Dodaj do listy nazwę aplikacji "HelloDjangoApp" `INSTALLED_APPS` . Dodanie aplikacji do listy informuje projekt Django o nazwie zawierającej aplikację:

    ```python
    INSTALLED_APPS = [
        'HelloDjangoApp',
        # Other entries...
    ]
    ```

1. W programie *Settings.py*upewnij się, że `TEMPLATES` obiekt zawiera następujący wiersz (domyślnie włączony), który instruuje Django, aby wyszukać szablony w folderze *szablonów* zainstalowanej aplikacji:

    ```json
    'APP_DIRS': True,
    ```

1. W folderze *HelloDjangoApp* Otwórz plik szablonu strony *Szablony/HelloDjangoApp/index.html* (lub *Szablony/index.html* w programie vs 2017 15,7 i starsze), aby sprawdzić, czy zawiera on jedną zmienną `{{ content }}` :

    ```html
    <html>
    <head><title></title></head>

    <body>

    {{ content }}

    </body>
    </html>
    ```

1. W folderze *HelloDjangoApp* Otwórz *views.py* i Zastąp `index` funkcję następującym kodem, który używa `django.shortcuts.render` funkcji pomocnika. `render`Pomocnik udostępnia uproszczony interfejs do pracy z szablonami stron. Upewnij się, że wszystkie istniejące instrukcje są zachowywane `from` .

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

    Pierwszy argument do `render` , jak widać, jest obiektem żądania, a następnie ścieżką względną do pliku szablonu w folderze *szablonów* aplikacji. Plik szablonu jest nazwany dla widoku, który obsługuje, w razie potrzeby. Trzeci argument jest to `render` słownik zmiennych, do których odwołuje się szablon. Można uwzględnić obiekty w słowniku, w którym to przypadku zmienna w szablonie może odwoływać się do `{{ object.property }}` .

1. Uruchom projekt i obserwuj dane wyjściowe. Powinien zostać wyświetlony podobny komunikat do tego, który pojawił się w kroku 2-2, co oznacza, że szablon działa.

    Należy jednak zauważyć, że kod HTML użyty we `content` Właściwości renderuje tylko jako zwykły tekst, ponieważ `render` funkcja automatycznie wyprowadza ten kod HTML. Automatyczne ucieczki Zapobiegaj przypadkowym atakom na ataki: deweloperzy często zbierają dane wejściowe z jednej strony i używają jej jako wartości w innym za pośrednictwem symbolu zastępczego szablonu. Ucieczki również służy jako przypomnienie, że najlepiej jest zachować kod HTML w szablonie strony i poza kodem. Na szczęście warto utworzyć dodatkowe zmienne, w razie potrzeby. Na przykład zmień *index.html* z *szablonami* , aby dopasować następujące znaczniki, co spowoduje dodanie tytułu strony i zachowanie całego formatowania w szablonie strony:

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

    Następnie napisz `index` funkcję View w następujący sposób, aby podać wartości dla wszystkich zmiennych w szablonie strony:

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

1. Zatrzymaj serwer i ponownie uruchom projekt i sprawdź, czy strona jest teraz renderowana prawidłowo:

    ![Uruchamianie aplikacji przy użyciu szablonu](media/django/step02-result.png)

1. <a name="template-namespacing"></a>Visual Studio 2017 w wersji 15,7 i starszej: w ostatnim kroku Przenieś szablony do podfolderu o nazwie takiej samej jak aplikacja, która tworzy przestrzeń nazw i pozwala uniknąć potencjalnych konfliktów z innymi aplikacjami, które mogą zostać dodane do projektu. (Szablony w programie VS 2017 15.8 + zrób to automatycznie). Oznacza to, że należy utworzyć podfolder w *szablonach* o nazwie *HelloDjangoApp*, przenieść *index.html* do tego podfolderu i zmodyfikować `index` funkcję widoku, aby odwołać się do nowej ścieżki szablonu, *HelloDjangoApp/index.html*. Następnie Uruchom projekt, sprawdź, czy strona jest renderowana prawidłowo i Zatrzymaj serwer.

1. Zatwierdź zmiany w kontroli źródła i zaktualizuj zdalne repozytorium, jeśli to konieczne, zgodnie z opisem w [kroku 2-2](#commit-to-source-control).

### <a name="question-do-page-templates-have-to-be-in-a-separate-file"></a>Pytanie: czy szablony stron muszą znajdować się w osobnym pliku?

Odpowiedź: Chociaż szablony są zwykle utrzymywane w oddzielnych plikach HTML, można również użyć szablonu wbudowanego. Zaleca się jednak używanie oddzielnego pliku w celu utrzymania czystego rozdzielenia między adiustacją i kodem.

### <a name="question-must-templates-use-the-html-file-extension"></a>Pytanie: czy szablony muszą używać rozszerzenia pliku HTML?

Odpowiedź: rozszerzenie *HTML* dla plików szablonów stron jest całkowicie opcjonalne, ponieważ zawsze identyfikujesz dokładną ścieżkę względną do pliku w drugim argumencie `render` funkcji. Jednak program Visual Studio (i inne redaktorzy) zwykle udostępnia funkcje, takie jak uzupełnianie kodu i zabarwienie składni z plikami *. html* , co pozwala na przeważenie faktu, że szablony stron nie są wyłącznie w formacie HTML.

W rzeczywistości podczas pracy z projektem Django program Visual Studio automatycznie wykrywa, kiedy edytowany plik HTML jest w rzeczywistości szablonem Django i udostępnia niektóre funkcje autouzupełniania. Na przykład po rozpoczęciu wpisywania komentarza do szablonu strony Django program `{#` Visual Studio automatycznie poda znaki zamykające `#}` . Polecenia **zaznaczania komentarza** i usuwania **komentarzy** (w menu **Edytuj**  >  **Zaawansowane** i na pasku narzędzi) również używają komentarzy szablonu zamiast komentarzy HTML.

### <a name="question-when-i-run-the-project-i-see-an-error-that-the-template-cannot-be-found-whats-wrong"></a>Pytanie: po uruchomieniu projektu pojawia się błąd, że nie można znaleźć szablonu. Co jest nie tak?

Odpowiedź: Jeśli widzisz błędy, których szablon nie można znaleźć, upewnij się, że aplikacja została dodana do *Settings.py* projektu Django na `INSTALLED_APPS` liście. Bez tego wpisu Django nie będzie wiadomo, aby szukać w folderze *szablonów* aplikacji.

### <a name="question-why-is-template-namespacing-important"></a>Pytanie: Dlaczego szablon namespacing ważne?

Odpowiedź: gdy Django szuka szablonu, do którego odwołuje się `render` Funkcja, używa dowolnego pliku, który znajduje się najpierw, który jest zgodny ze ścieżką względną. Jeśli masz wiele aplikacji Django w tym samym projekcie, które używają tych samych struktur folderów dla szablonów, prawdopodobnie jedna aplikacja będzie przypadkowo używać szablonu z innej aplikacji. Aby uniknąć takich błędów, należy zawsze utworzyć podfolder w folderze *szablonów* aplikacji, który jest zgodny z nazwą aplikacji, aby uniknąć wszystkich duplikacji.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Korzystanie z plików statycznych, dodawanie stron i dziedziczenie szablonów](learn-django-in-visual-studio-step-03-serve-static-files-and-add-pages.md)

## <a name="go-deeper"></a>Przejdź głębiej

- [Pisanie pierwszej aplikacji Django, część 1 — widoki](https://docs.djangoproject.com/en/2.0/intro/tutorial01/#write-your-first-view) (docs.djangoproject.com)
- Aby uzyskać więcej możliwości szablonów Django, takich jak Dołączanie i dziedziczenie, zobacz [Django Template Language](https://docs.djangoproject.com/en/2.0/ref/templates/language/) (docs.djangoproject.com).
- [Szkolenie dotyczące wyrażenia regularnego w trakcie zdobywania informacji](https://www.linkedin.com/learning/topics/regular-expressions) (LinkedIn)
- Kod źródłowy samouczka w witrynie GitHub: [Microsoft/Python-Sample-vs-Learning-Django](https://github.com/Microsoft/python-sample-vs-learning-django)

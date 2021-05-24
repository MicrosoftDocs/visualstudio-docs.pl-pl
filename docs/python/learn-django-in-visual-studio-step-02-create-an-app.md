---
title: Zapoznaj się z samouczkiem django Visual Studio kroku 2, widoków i szablonu strony
titleSuffix: ''
description: Przewodnik po podstawach django w kontekście projektów Visual Studio, w szczególności kroków tworzenia aplikacji oraz korzystania z widoków i szablonów.
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18, SEO-VS-2020
ms.workload:
- python
- data-science
ms.openlocfilehash: 196b15dff25681a23c05118a02f19109e09e3959
ms.sourcegitcommit: 5fe2462ffc33c7ece9cf3a179fb598354c916e1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2021
ms.locfileid: "110320475"
---
# <a name="step-2-create-a-django-app-with-views-and-page-templates"></a>Krok 2. Tworzenie aplikacji Django z widokami i szablonami stron

**Poprzedni krok: [Tworzenie Visual Studio projektu i rozwiązania](learn-django-in-visual-studio-step-01-project-and-solution.md)**

Do tej pory w projekcie django Visual Studio tylko składniki na poziomie witryny projektu *Django,* które mogą uruchamiać co najmniej jedną *aplikacje* Django. Następnym krokiem jest utworzenie pierwszej aplikacji z jedną stroną.

W tym kroku dowiesz się, jak:

> [!div class="checklist"]
> - Tworzenie aplikacji Django z jedną stroną (krok 2–1)
> - Uruchamianie aplikacji z projektu Django (krok 2–2)
> - Renderowanie widoku przy użyciu kodu HTML (krok 2–3)
> - Renderowanie widoku przy użyciu szablonu strony Django (krok 2–4)

## <a name="step-2-1-create-an-app-with-a-default-structure"></a>Krok 2–1. Tworzenie aplikacji o domyślnej strukturze

Aplikacja Django to oddzielny pakiet języka Python, który zawiera zestaw powiązanych plików do określonego celu. Projekt Django może zawierać dowolną liczbę aplikacji, co odzwierciedla fakt, że host internetowy może obsługiwać dowolną liczbę oddzielnych punktów wejścia od pojedynczej nazwy domeny. Na przykład projekt Django dla domeny takiej jak contoso.com może zawierać jedną aplikację dla , drugą aplikację dla usługi support.contoso.com i trzecią aplikację dla `www.contoso.com` docs.contoso.com. W tym przypadku projekt Django obsługuje routing i ustawienia adresów URL na poziomie witryny (w plikach urls.py *i settings.py),* *podczas* gdy każda aplikacja ma własne odrębne style i zachowanie dzięki routingowi wewnętrznemu, widokom, modelom, plikom statycznym i interfejsowi administracyjnemu.

Aplikacja Django zwykle rozpoczyna się od standardowego zestawu plików. Visual Studio szablony elementów do inicjowania aplikacji Django w projekcie Django wraz ze zintegrowanym poleceniem menu, które służy do tego samego celu:

- Szablony: w **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy projekt i wybierz **polecenie Dodaj**  >  **nowy element**. W **oknie dialogowym Dodawanie nowego** elementu wybierz szablon **Aplikacja Django 1.9,** określ nazwę aplikacji w polu **Nazwa** i wybierz przycisk **OK.**

- Zintegrowane polecenie: w **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Dodaj aplikację**  >  **Django.** To polecenie wyświetla monit o nazwę i tworzy aplikację Django 1.9.

    ![Polecenie Menu do dodawania aplikacji Django](media/django/step02-add-django-app-command.png)

Przy użyciu jednej z tych metod utwórz aplikację o nazwie "HelloDjangoApp". Wynikiem jest folder w projekcie o tej nazwie, który zawiera elementy zgodnie z opisem w poniższej tabeli.

![Pliki aplikacji Django w programie Eksplorator rozwiązań](media/django/step02-django-app-in-solution-explorer.png)

::: moniker range="vs-2017"
| Element | Opis |
| --- | --- |
| **\_\_init \_ \_ .py** | Plik, który identyfikuje aplikację jako pakiet. |
| **Migracji** | Folder, w którym Django przechowuje skrypty aktualizujące bazę danych w celu dostosowania do zmian w modelach. Narzędzia do migracji django następnie stosują niezbędne zmiany do każdej poprzedniej wersji bazy danych, tak aby była ona dopasowana do bieżących modeli. Korzystając z migracji, możesz skupić się na modelach i pozwolić, aby django obsługiło bazowy schemat bazy danych. Migracje zostały omówione w kroku 6; Na razie folder po prostu zawiera plik *\_ \_ init \_ \_ .py* (wskazujący, że folder definiuje własny pakiet języka Python). |
| **templates** | Folder szablonów stron Django zawierający pojedynczy plikindex.htm *l* w folderze pasujący do nazwy aplikacji. (W Visual Studio 2017 15.7 i starszych plik jest  zawarty bezpośrednio w szablonach, a krok 2–4 powoduje utworzenie podfolderu. Szablony to bloki kodu HTML, do których widoki mogą dodawać informacje w celu dynamicznego renderowania strony. "Zmienne" szablonu strony, takie jakindex.html , są symbolami zastępczymi wartości dynamicznych, jak wyjaśniono w dalszej części tego artykułu `{{ content }}` (krok 2).  Zazwyczaj aplikacje Django tworzą przestrzeń nazw dla swoich szablonów, umieszczając je w podfolderze, który odpowiada nazwie aplikacji. |
| **admin.py** | Plik języka Python, w którym rozszerzasz interfejs administracyjny aplikacji (zobacz krok 6), który jest używany do iniekcjonować i edytować dane w bazie danych. Początkowo ten plik zawiera tylko instrukcje `from django.contrib import admin` . Domyślnie django zawiera standardowy interfejs administracyjny za pośrednictwem wpisów w pliku *settings.py* Django, który można włączyć, odkomentując istniejące wpisy w *urls.py*. |
| **apps.py** | Plik w języku Python, który definiuje klasę konfiguracji dla aplikacji (zobacz poniżej, po tej tabeli). |
| **models.py** | Modele to obiekty danych identyfikowane przez funkcje, za pomocą których widoki wchodzą w interakcję z bazą danych aplikacji (zobacz krok 6). Django udostępnia warstwę połączenia bazy danych, dzięki czemu aplikacje nie muszą się martwić tymi szczegółami. Plik *models.py* jest domyślnym miejscem, w którym można tworzyć modele, i początkowo zawiera tylko instrukcje `from django.db import models` . |
| **tests.py** | Plik języka Python zawierający podstawową strukturę testów jednostkowych. |
| **views.py** | Widoki są zwykle stronami internetowymi, które przyjmą żądanie HTTP i zwracają odpowiedź HTTP. Wyświetlenia są zwykle renderowane jako kod HTML, które przeglądarki internetowe wiedzą, jak je wyświetlać, ale widok nie musi być widoczny (na przykład formularz pośredni). Widok jest definiowany przez funkcję języka Python, której zadaniem jest renderowanie kodu HTML w celu wysłania do przeglądarki. Plik *views.py* jest domyślnym miejscem do tworzenia widoków i początkowo zawiera tylko instrukcje `from django.shortcuts import render` . |
::: moniker-end

::: moniker range=">=vs-2019"
| Element | Opis |
| --- | --- |
| **\_\_init \_ \_ .py** | Plik, który identyfikuje aplikację jako pakiet. |
| **Migracji** | Folder, w którym Django przechowuje skrypty, które aktualizują bazę danych w celu dostosowania do zmian w modelach. Narzędzia migracji django następnie stosują niezbędne zmiany do każdej poprzedniej wersji bazy danych, tak aby była ona dopasowana do bieżących modeli. Korzystając z migracji, możesz skupić się na modelach i pozwolić, aby django obsługiło bazowy schemat bazy danych. Migracje zostały omówione w dokumentacji [django;](https://docs.djangoproject.com/en/3.2/topics/migrations/) Na razie folder po prostu zawiera plik *\_ \_ init \_ \_ .py* (wskazujący, że folder definiuje własny pakiet języka Python). |
| **templates** | Folder szablonów stron Django zawierający pojedynczy plikindex.htm *l* w folderze pasujący do nazwy aplikacji. (W Visual Studio 2017 15.7 i starszych plik jest  zawarty bezpośrednio w szablonach, a krok 2–4 powoduje utworzenie podfolderu. Szablony to bloki kodu HTML, do których widoki mogą dodawać informacje w celu dynamicznego renderowania strony. "Zmienne" szablonu strony, takie jakindex.html , są symbolami zastępczymi wartości dynamicznych, jak wyjaśniono w dalszej części tego artykułu `{{ content }}` (krok 2).  Zazwyczaj aplikacje Django tworzą przestrzeń nazw dla swoich szablonów, umieszczając je w podfolderze, który odpowiada nazwie aplikacji. |
| **admin.py** | Plik w języku Python, w którym rozszerzasz interfejs administracyjny aplikacji, który służy do iniekcjonować i edytować dane w bazie danych. Początkowo ten plik zawiera tylko instrukcje `from django.contrib import admin` . Domyślnie django zawiera standardowy interfejs administracyjny za pośrednictwem  wpisów w pliku settings.py projektu Django, który można włączyć, odkomentując istniejące wpisy w urls.py *.* |
| **apps.py** | Plik w języku Python, który definiuje klasę konfiguracji dla aplikacji (zobacz poniżej, po tej tabeli). |
| **models.py** | Modele to obiekty danych identyfikowane przez funkcje, za pomocą których widoki wchodzą w interakcję z bazą danych aplikacji. Django udostępnia warstwę połączenia bazy danych, dzięki czemu aplikacje nie muszą się martwić o te szczegóły. Plik *models.py* jest domyślnym miejscem, w którym można tworzyć modele, i początkowo zawiera tylko instrukcje `from django.db import models` . |
| **tests.py** | Plik języka Python zawierający podstawową strukturę testów jednostkowych. |
| **views.py** | Widoki są zwykle stronami internetowymi, które przyjmą żądanie HTTP i zwracają odpowiedź HTTP. Wyświetlenia są zwykle renderowane jako kod HTML, które przeglądarki internetowe wiedzą, jak je wyświetlać, ale widok nie musi być widoczny (na przykład formularz pośredni). Widok jest definiowany przez funkcję języka Python, której zadaniem jest renderowanie kodu HTML w celu wysłania do przeglądarki. Plik *views.py* jest domyślnym miejscem do tworzenia widoków i początkowo zawiera tylko instrukcje `from django.shortcuts import render` . |
::: moniker-end

Zawartość pliku *apps.py* w następujący sposób w przypadku używania nazwy "HelloDjangoApp":

```python
from django.apps import AppConfig

class HelloDjangoAppConfig(AppConfig):
    name = 'HelloDjango'
```

### <a name="question-is-creating-a-django-app-in-visual-studio-any-different-from-creating-an-app-on-the-command-line"></a>Pytanie: Czy tworzenie aplikacji Django w Visual Studio różni się od tworzenia aplikacji w wierszu polecenia?

Odpowiedź: Uruchomienie polecenia **Add**  >  Django app (Dodaj aplikację **Django)** lub użycie polecenia **Add**  >  **New Item** (Dodaj nowy element) za pomocą szablonu aplikacji Django powoduje uzyskanie tych samych plików, co polecenie `manage.py startapp <app_name>` Django. Zaletą tworzenia aplikacji w Visual Studio jest to, że folder aplikacji i wszystkie jego pliki są automatycznie integrowane w projekcie. Możesz użyć tego samego Visual Studio, aby utworzyć dowolną liczbę aplikacji w projekcie.

## <a name="step-2-2-run-the-app-from-the-django-project"></a>Krok 2–2. Uruchamianie aplikacji z projektu Django

W tym momencie, jeśli ponownie uruchamiasz projekt w programie Visual Studio (przy użyciu przycisku paska narzędzi lub opcji **Debuguj** rozpocznij debugowanie), nadal będzie widać  >  stronę domyślną. Zawartość aplikacji nie jest wyświetlana, ponieważ musisz zdefiniować stronę specyficzną dla aplikacji i dodać aplikację do projektu Django:

1. W *folderze HelloDjangoApp* zmodyfikuj plik *views.py* do poniższego kodu, który definiuje widok o nazwie "index":

    ```python
    from django.shortcuts import render
    from django.http import HttpResponse

    def index(request):
        return HttpResponse("Hello, Django!")
    ```

1. W *folderze BasicProject* (utworzonym w kroku 1) zmodyfikuj plik *urls.py,* aby był co najmniej pasować do następującego kodu (jeśli chcesz, możesz zachować komentarze z poinstrukcją):

    ```python
    from django.conf.urls import include, url
    import HelloDjangoApp.views

    # Django processes URL patterns in the order they appear in the array
    urlpatterns = [
        url(r'^$', HelloDjangoApp.views.index, name='index'),
        url(r'^home$', HelloDjangoApp.views.index, name='home'),
    ]
    ```

    Każdy wzorzec adresu URL opisuje widoki, do których django kieruje określone adresy URL względne dla witryny (czyli część, która następuje po pliku `https://www.domain.com/` ). Pierwszym wpisem w programie, który rozpoczyna się od wyrażenia regularnego, jest routing dla katalogu `urlPatterns` `^$` głównego lokacji "/". Drugi wpis, `^home$` w szczególności trasy "/home". Możesz mieć dowolną liczbę routingów do tego samego widoku.

1. Uruchom ponownie projekt, aby zobaczyć komunikat **Hello, Django!** zgodnie z definicją w widoku. Gdy wszystko będzie gotowe, zatrzymaj serwer.

### <a name="commit-to-source-control"></a>Zatwierdzanie do kontroli źródła

Ponieważ w kodzie zostały wprowadzone zmiany i zostały one pomyślnie przetestowane, jest to doskonały czas na przejrzenie i zatwierdzenie zmian w kontroli źródła. W kolejnych krokach tego samouczka przypomnisz o odpowiednich godzinach, aby ponownie zatwierdzić kontrolę źródła, i wróć do tej sekcji.

1. Wybierz przycisk zmiany u dołu okna Visual Studio (w okręgu poniżej), który umożliwia przejście do **Team Explorer**.

    ![Przycisk Zmiany kontroli źródła na Visual Studio stanu](media/django/step02-source-control-changes-button.png)

1. W **Team Explorer** wprowadź komunikat o zatwierdzeniu, taki jak "Utwórz początkową aplikację Django", a następnie wybierz **pozycję Zateń wszystko.** Po zakończeniu zatwierdzania zostanie wyświetlony komunikat Zatwierdzenie **\<hash> utworzone lokalnie. Synchronizuj, aby udostępnić zmiany serwerowi.** Jeśli chcesz wypchnąć zmiany do repozytorium zdalnego, wybierz pozycję **Synchronizuj,** a następnie wybierz pozycję **Wypchń** w obszarze **Wychodzące zatwierdzenia.** Można również gromadzić wiele zatwierdzeń lokalnych przed wypchnięciem do zdalnego.

    ![Wypychanie zatwierdzeń do zdalnego Team Explorer](media/django/step02-source-control-push-to-remote.png)

### <a name="question-what-is-the-r-prefix-before-the-routing-strings-for"></a>Pytanie: Jaki jest prefiks "r" przed ciągami routingu?

Odpowiedź: Prefiks "r" w ciągu w języku Python oznacza "nieprzetworzony", który nakazuje językowi Python, aby nie poprzedzał znakiem ucieczki w ciągu. Ponieważ wyrażenia regularne używają wielu znaków specjalnych, użycie prefiksu "r" sprawia, że ciągi te są znacznie łatwiejsze do odczytania niż gdyby zawierały liczbę znaków ucieczki \\ "".

### <a name="question-what-do-the--and--characters-mean-in-the-url-routing-entries"></a>Pytanie: Co oznaczają znaki ^ i $ we wpisach routingu adresów URL?

Odpowiedź: W wyrażeniach regularnych, które definiują wzorce adresów URL, ^ oznacza "początek wiersza", a $ oznacza "koniec wiersza", gdzie ponownie adresy URL są względne względem katalogu głównego witryny (część poniżej `https://www.domain.com/` ). Wyrażenie regularne w praktyce oznacza "puste" i w związku z tym pasuje `^$` do pełnego adresu URL (nic nie jest dodawane do katalogu głównego `https://www.domain.com/` witryny). Wzorzec `^home$` jest dokładnie taki sam jak `https://www.domain.com/home/` . (Django nie używa końcowego /w dopasowywaniu wzorca).

Jeśli nie używasz końcowego $w wyrażeniu regularnym, tak jak w przypadku , wzorzec adresu URL pasuje do dowolnego adresu URL, który zaczyna się od "home", takiego jak `^home` "home", "homework", "home192837". 

Aby poeksperymentować z różnymi wyrażeniami regularnymi, wypróbuj narzędzia online, takie [jak regex101.com](https://regex101.com) na [pythex.org](https://www.pythex.org).

## <a name="step-2-3-render-a-view-using-html"></a>Krok 2–3. Renderowanie widoku przy użyciu kodu HTML

Funkcja, która jest do tej pory views.py generuje niczym więcej niż tylko odpowiedź HTTP w postaci `index` zwykłego tekstu dla strony.  Oczywiście większość rzeczywistych stron internetowych odpowiada za pomocą rozbudowanych stron HTML, które często zawierają dane na żywo. W rzeczywistości głównym powodem definiowania widoku przy użyciu funkcji jest możliwość dynamicznego generowania tej zawartości.

Ponieważ argument funkcji jest tylko ciągiem, możesz utworzyć dowolny `HttpResponse` kod HTML w ciągu. W prostym przykładzie zastąp funkcję następującym kodem (zachowując istniejące instrukcje), który generuje odpowiedź HTML przy użyciu zawartości dynamicznej, która jest aktualizowana przy każdym `index` `from` odświeżeniu strony:

```python
from datetime import datetime

def index(request):
    now = datetime.now()

    html_content = "<html><head><title>Hello, Django</title></head><body>"
    html_content += "<strong>Hello Django!</strong> on " + now.strftime("%A, %d %B, %Y at %X")
    html_content += "</body></html>"

    return HttpResponse(html_content)
```

Uruchom ponownie projekt, aby wyświetlić komunikat podobny do **"Hello Django!** w poniedziałek 16 kwietnia 2018 r. o 16:28:10". Odśwież stronę, aby zaktualizować czas i potwierdzić, że zawartość jest generowana przy każdym żądaniu. Gdy wszystko będzie gotowe, zatrzymaj serwer.

> [!Tip]
> Skrótem do zatrzymywania i ponownego uruchamiania projektu jest użycie polecenia menu  >  **Debuguj** ponownie **(Ctrl** + **Shift** + **F5)** lub **przycisku Uruchom** ponownie na pasku narzędzi debugowania:
>
> ![Przycisk Uruchom ponownie na pasku narzędzi debugowania w Visual Studio](media/debugging-restart-toolbar-button.png)

## <a name="step-2-4-render-a-view-using-a-page-template"></a>Krok 2–4. Renderowanie widoku przy użyciu szablonu strony

Generowanie kodu HTML w kodzie działa dobrze w przypadku bardzo małych stron, ale w związku z tym, że strony są bardziej zaawansowane, zwykle chcesz zachować statyczne części HTML strony (wraz z odwołaniami do plików CSS i JavaScript) jako "szablony stron", do których następnie wstawianie dynamicznej zawartości generowanej przez kod. W poprzedniej sekcji tylko data i godzina wywołania są dynamiczne, co oznacza, że całą inną zawartość można umieścić `now.strftime` w szablonie strony.

Szablon strony Django to blok kodu HTML, który może zawierać dowolną liczbę tokenów zastępczych nazywanych "zmiennymi", które są rozsyłane za pomocą elementów `{{` i , jak w pliku `}}` `{{ content }}` . Następnie moduł szablonów django zastępuje zmienne zawartością dynamiczną podaną w kodzie.

W poniższych krokach pokazano, jak używać szablonów stron:

1. W *folderze BasicProject,* który zawiera projekt Django, otwórz plik *settings.py* i dodaj nazwę aplikacji "HelloDjangoApp" do `INSTALLED_APPS` listy. Dodanie aplikacji do listy informuje projekt Django, że istnieje folder o tej nazwie zawierający aplikację:

    ```python
    INSTALLED_APPS = [
        'HelloDjangoApp',
        # Other entries...
    ]
    ```

1. W *programie settings.py* upewnij się, że obiekt zawiera następujący wiersz (dołączony domyślnie), który instruuje platformę Django, aby szukać szablonów w folderze `TEMPLATES` templates *zainstalowanej* aplikacji:

    ```json
    'APP_DIRS': True,
    ```

1. W *folderze HelloDjangoApp* otwórz plik szablonu strony *templates/HelloDjangoApp/index.html* (lub *templates/index.html* w programie VS 2017 15.7 i starszych), aby zaobserwować, że zawiera on jedną zmienną: `{{ content }}` :

    ```html
    <html>
    <head><title></title></head>

    <body>

    {{ content }}

    </body>
    </html>
    ```

1. W *folderze HelloDjangoApp* otwórz plik *views.py* i zastąp funkcję następującym kodem, który używa `index` funkcji `django.shortcuts.render` pomocnika . Pomocnik `render` udostępnia uproszczony interfejs do pracy z szablonami stron. Pamiętaj, aby zachować wszystkie istniejące `from` instrukcje.

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

    Pierwszym argumentem funkcji , jak widać, jest obiekt żądania, po którym następuje ścieżka względna do pliku szablonu w `render` folderze *templates* aplikacji. Plik szablonu jest nazwany dla widoku, który obsługuje, jeśli jest to konieczne. Trzecim argumentem funkcji jest następnie słownik zmiennych, do `render` których odwołuje się szablon. Obiekty można uwzględnić w słowniku. W takim przypadku zmienna w szablonie może odwoływać się `{{ object.property }}` do .

1. Uruchom projekt i obserwuj dane wyjściowe. Powinien zostać wyświetlony komunikat podobny do widocznego w kroku 2–2, wskazujący, że szablon działa.

    Zauważ jednak, że kod HTML użyty we właściwości jest renderowany tylko jako zwykły tekst, ponieważ `content` `render` funkcja automatycznie unika kodu HTML. Automatyczne ucieczki zapobiegają przypadkowym lukom w zabezpieczeniach w celu iniekcji ataków: deweloperzy często zbierają dane wejściowe z jednej strony i używają ich jako wartości w innej za pośrednictwem symbolu zastępczego szablonu. Ucieczka służy również jako przypomnienie, że najlepiej jest zachować kod HTML w szablonie strony i poza kodem. Na szczęście tworzenie dodatkowych zmiennych w razie potrzeby jest proste. Na przykład zmieńindex.htmna  *szablony,* aby dopasować je do następującego narzutu, który dodaje tytuł strony i zachowuje całe formatowanie w szablonie strony:

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

    Następnie napisz funkcję view w następujący sposób, aby podać wartości dla `index` wszystkich zmiennych w szablonie strony:

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

1. Zatrzymaj serwer i uruchom ponownie projekt, a następnie sprawdź, czy strona jest teraz poprawnie renderowana:

    ![Uruchamianie aplikacji przy użyciu szablonu](media/django/step02-result.png)

1. <a name="template-namespacing"></a>Visual Studio 2017 w wersji 15.7 lub starszej: w ostatnim kroku przenieś szablony do podfolderu o nazwie takiej samej jak aplikacja, co powoduje utworzenie przestrzeni nazw i uniknięcie potencjalnych konfliktów z innymi aplikacjami, które można dodać do projektu. (Szablony w programie VS 2017 15.8+ robią to automatycznie). Oznacza *to,* że utwórz  podfolder w szablonach o nazwie *HelloDjangoApp,* przenieśindex.html do tego podfolderu i zmodyfikuj funkcję view, aby odwoływała się do nowej ścieżki szablonu `index` *HelloDjangoApp/index.html*. Następnie uruchom projekt, sprawdź, czy strona jest prawidłowo renderowana, i zatrzymaj serwer.

1. W razie potrzeby zat zatwierdzanie zmian w kontroli źródła i aktualizowanie repozytorium zdalnego zgodnie z opisem w [kroku 2–2.](#commit-to-source-control)

### <a name="question-do-page-templates-have-to-be-in-a-separate-file"></a>Pytanie: Czy szablony stron muszą być w oddzielnym pliku?

Odpowiedź: Chociaż szablony są zwykle utrzymywane w oddzielnych plikach HTML, można również użyć szablonu wbudowanego. Zaleca się jednak używanie oddzielnego pliku w celu zachowania czystego oddzielenia znaczników od kodu.

### <a name="question-must-templates-use-the-html-file-extension"></a>Pytanie: Czy szablony muszą używać rozszerzenia pliku HTML?

Odpowiedź: *Rozszerzenie html* dla plików szablonów stron jest całkowicie opcjonalne, ponieważ zawsze identyfikujesz dokładną ścieżkę względną do pliku w drugim argumentze `render` funkcji. Jednak Visual Studio (i inne edytory) zazwyczaj zapewniają funkcje takie jak uzupełnianie kodu i kolorowanie składni za pomocą plików *HTML,* co przeważa nad tym, że szablony stron nie są wyłącznie html.

W rzeczywistości podczas pracy z projektem Django program Visual Studio automatycznie wykrywa, kiedy edytowany plik HTML jest w rzeczywistości szablonem Django i udostępnia pewne funkcje autouzupełnienia. Na przykład po rozpoczęciu wpisywania komentarza szablonu strony Django `{#` , Visual Studio automatycznie podaje znaki `#}` zamykające. Polecenia **Wybór komentarza** i **Zaznaczenie** komentarza (w menu Edytuj zaawansowane i na pasku narzędzi) również używają komentarzy szablonu   >   zamiast komentarzy HTML.

### <a name="question-when-i-run-the-project-i-see-an-error-that-the-template-cannot-be-found-whats-wrong"></a>Pytanie: Po uruchomieniu projektu widzę komunikat o błędzie, że nie można odnaleźć szablonu. Co jest nie tak?

Odpowiedź: Jeśli widzisz błędy, których nie można znaleźć w szablonie,  upewnij się, że aplikacja została dodana do listy settings.py `INSTALLED_APPS` Django. Bez tego wpisu django nie będzie wiedzieć, jak szukać w folderze *szablonów* aplikacji.

### <a name="question-why-is-template-namespacing-important"></a>Pytanie: Dlaczego nazwy szablonów są istotne?

Odpowiedź: Gdy django wyszukuje szablon, do którym odnosi się funkcja, używa najpierw dowolnego znalezionego pliku, `render` który pasuje do ścieżki względnej. Jeśli masz wiele aplikacji Django w tym samym projekcie, które używają tych samych struktur folderów dla szablonów, prawdopodobnie jedna aplikacja będzie w sposób niezamierzony używać szablonu z innej aplikacji. Aby uniknąć takich błędów, należy zawsze utworzyć podfolder w folderze *templates* aplikacji, który jest taki, który odpowiada nazwie aplikacji, aby uniknąć duplikowania wszystkich błędów.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Obsługiwać pliki statyczne, dodawać strony i używać dziedziczenia szablonu](learn-django-in-visual-studio-step-03-serve-static-files-and-add-pages.md)

## <a name="go-deeper"></a>Głębiej

- [Pisanie pierwszej aplikacji Django, część 1 — widoki](https://docs.djangoproject.com/en/2.0/intro/tutorial01/#write-your-first-view) (docs.djangoproject.com)
- Aby uzyskać więcej możliwości szablonów Django, takich jak uwzględnianie i dziedziczenie, zobacz Język szablonów [Django](https://docs.djangoproject.com/en/2.0/ref/templates/language/) (docs.djangoproject.com)
- [Trenowanie wyrażeń regularnych na stronie inLearning](https://www.linkedin.com/learning/topics/regular-expressions) (LinkedIn)
- Kod źródłowy samouczka w witrynie GitHub: [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)

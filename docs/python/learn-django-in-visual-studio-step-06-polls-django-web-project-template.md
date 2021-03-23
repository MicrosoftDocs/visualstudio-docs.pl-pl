---
title: Poznaj samouczek Django w programie Visual Studio krok 6, szablon projektu sondowań
titleSuffix: ''
description: Przewodnik po Django podstawy w kontekście projektów programu Visual Studio, w tym w pełni funkcje szablonu projektu sieci Web Django, takiego jak dostosowanie administracyjne.
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
monikerRange: vs-2017
ms.workload:
- python
- data-science
ms.openlocfilehash: b52cc9615eb4829aede06ae65c152e47b3ff3844
ms.sourcegitcommit: f1dff6c4532c43b0444aa12ea57e90bb7dba6fba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2021
ms.locfileid: "104806033"
---
# <a name="step-6-use-the-polls-django-web-project-template"></a>Krok 6. użycie szablonu projektu sieci Web Django sondy

**Poprzedni krok: [uwierzytelnianie użytkowników w Django](learn-django-in-visual-studio-step-05-django-authentication.md)**

Po zrozumieniu szablonu "Django Web Project" programu Visual Studio można teraz przeglądać trzeci szablon Django, "Sondowas Django Web Project", który jest oparty na tej samej bazie kodu i demonstruje pracę z bazą danych.

W tym kroku dowiesz się, jak:

> [!div class="checklist"]
> - Utwórz projekt na podstawie szablonu i zainicjuj bazę danych (krok 6-1)
> - Zrozumienie modeli danych (krok 6-2)
> - Zastosuj migracje (krok 6-3)
> - Informacje o widokach i szablonach stron utworzonych przez szablon projektu (krok 6-4)
> - Tworzenie niestandardowego interfejsu administracyjnego (krok 6-5)

Projekt utworzony przy użyciu tego szablonu jest podobny do tego, co uzyskasz, postępując zgodnie z samouczkiem [pisanie pierwszej aplikacji Django](https://docs.djangoproject.com/en/2.0/intro/tutorial01/) w dokumentacji Django. Aplikacja internetowa składa się z publicznej witryny, która umożliwia osobom przeglądanie i głosowanie w nich, a także niestandardowy interfejs administracyjny, za pomocą którego można zarządzać sondowaniem. Używa tego samego systemu uwierzytelniania co szablon "Django Web Project" i zwiększa użycie bazy danych przez implementację modeli Django, jak przedstawiono w poniższych sekcjach.

## <a name="step-6-1-create-the-project-and-initialize-the-database"></a>Krok 6-1: Tworzenie projektu i Inicjowanie bazy danych

1. W programie Visual Studio przejdź do **Eksplorator rozwiązań**, kliknij prawym przyciskiem myszy rozwiązanie **LearningDjango** utworzone wcześniej w tym samouczku, a następnie wybierz pozycję **Dodaj**  >  **Nowy projekt**. (Alternatywnie, jeśli chcesz użyć nowego rozwiązania, wybierz pozycję **plik**  >  **Nowe**  >  W zamian **projekt** ).

1. W oknie dialogowym Nowy projekt Wyszukaj i wybierz szablon **projektu sieci Web sondowania Django** , wywołaj projekt "DjangoPolls", a następnie wybierz **przycisk OK**.

1. Podobnie jak w przypadku innych szablonów projektu w programie Visual Studio, szablon "Django" projektu sieci Web "sondy" zawiera plik *requirements.txt* , program Visual Studio monituje o lokalizację instalacji tych zależności. Wybierz opcję, **Zainstaluj w środowisku wirtualnym**, a następnie w oknie dialogowym **Dodawanie środowiska wirtualnego** wybierz pozycję **Utwórz** , aby zaakceptować ustawienia domyślne.

1. Gdy środowisko Python zakończy Konfigurowanie środowiska wirtualnego, postępuj zgodnie z instrukcjami wyświetlanymi w *readme.html* , aby zainicjować bazę danych i utworzyć Django administratora (czyli administratora). Kroki należy najpierw kliknąć prawym przyciskiem myszy projekt **DjangoPolls** w **Eksplorator rozwiązań**, wybrać polecenie **Python**  >  **Django zmigrować** , a następnie ponownie kliknąć prawym przyciskiem myszy projekt, wybrać polecenie **Python**  >  **Django Create administratora** i postępować zgodnie z instrukcjami. (Jeśli spróbujesz najpierw utworzyć administratora, zobaczysz błąd, ponieważ baza danych nie została zainicjowana.)

1. Ustaw projekt **DjangoPolls** jako domyślny dla rozwiązania Visual Studio, klikając prawym przyciskiem myszy ten projekt w **Eksplorator rozwiązań** i wybierając pozycję **Ustaw jako projekt startowy**. Projekt startowy, który jest wyświetlany pogrubiony, jest uruchamiany po uruchomieniu debugera.

1. Wybierz pozycję **Debuguj**  >  **Rozpocznij debugowanie** (**F5**) lub użyj przycisku **serwer sieci Web** na pasku narzędzi, aby uruchomić serwer:

    ![Przycisk paska narzędzi uruchamiania serwera sieci Web w programie Visual Studio](media/django/run-web-server-toolbar-button.png)

1. Aplikacja utworzona przez szablon ma trzy strony, Strona główna, informacje i kontakt, które są przechodzenie między górnym paskiem nawigacyjnym. Poświęć minutę lub dwie, aby przeanalizować różne części aplikacji (strony informacje i kontakty są bardzo podobne do "projektu sieci Web Django" i nie są jeszcze omówione w dalszej części).

    ![Pełny widok przeglądarki aplikacji sieci Web Django](media/django/step06-full-app-view.png)

1. Na pasku nawigacyjnym wybierz również link **Administracja** , który wyświetla ekran logowania, aby zademonstrować, że interfejs administracyjny jest autoryzowany tylko dla uwierzytelnionych administratorów. Użyj poświadczeń administratora i nastąpi kierowanie do strony "/admin", która jest domyślnie włączona podczas korzystania z tego szablonu projektu.

    ![Widok administracyjny aplikacji Project Web Django dla ankiet](media/django/step06-polls-administrative-interface.png)

1. Możesz pozostawić aplikację działającą dla następujących sekcji.

    Jeśli chcesz zatrzymać aplikację i [zatwierdzić zmiany w kontroli źródła](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control), najpierw Otwórz stronę **zmiany** w **Team Explorer**, kliknij prawym przyciskiem myszy folder dla środowiska wirtualnego (prawdopodobnie **ENV**), a następnie wybierz polecenie **Ignoruj te elementy lokalne**.

### <a name="examine-the-project-contents"></a>Sprawdzanie zawartości projektu

Jak wspomniano wcześniej. Większość elementów projektu utworzonych na podstawie szablonu "ankiety Django Web Project" powinien być znany, jeśli eksplorujesz inne szablony projektu w programie Visual Studio. Dodatkowe kroki opisane w tym artykule podsumowują bardziej znaczące zmiany i dodatki, czyli modele danych i dodatkowe widoki.

### <a name="question-what-does-the-django-migrate-command-do"></a>Pytanie: co to jest polecenie Django Migrowanie?

Odpowiedź: polecenie **Django** Migration w specjalny sposób uruchamia `manage.py migrate` polecenie, które uruchamia wszelkie skrypty w folderze *aplikacji/migracji* , który nie został wcześniej uruchomiony. W takim przypadku polecenie uruchamia skrypt *0001_initial. PR* w tym folderze, aby skonfigurować wymagany schemat w bazie danych.

Sam skrypt migracji jest tworzony przez `manage.py makemigrations` polecenie, które skanuje plik *models.py* aplikacji, porównuje go z bieżącym stanem bazy danych, a następnie generuje niezbędne skrypty do migracji schematu bazy danych w celu dopasowania do bieżących modeli. Ta funkcja programu Django jest bardzo wydajna, gdy aktualizujesz i modyfikujesz modele w miarę upływu czasu. Dzięki generowaniu i uruchamianiu migracji modele i bazy danych są synchronizowane z niewielkim trudnością.

Pracujesz z migracją w kroku 6-3 w dalszej części tego artykułu.

## <a name="step-6-2-understand-data-models"></a>Krok 6-2: zrozumienie modeli danych

Modele aplikacji o nazwie sondowanie i wybór są zdefiniowane w *App/models. PR*. Każda z nich jest klasą języka Python, która pochodzi z `django.db.models.Model` i używa metod `models` klasy, takich jak `CharField` i `IntegerField` do definiowania pól w modelu, które mapują do kolumn bazy danych.

```python
from django.db import models
from django.db.models import Sum

class Poll(models.Model):
    """A poll object for use in the application views and repository."""
    text = models.CharField(max_length=200)
    pub_date = models.DateTimeField('date published')

    def total_votes(self):
        """Calculates the total number of votes for this poll."""
        return self.choice_set.aggregate(Sum('votes'))['votes__sum']

    def __unicode__(self):
        """Returns a string representation of a poll."""
        return self.text

class Choice(models.Model):
    """A poll choice object for use in the application views and repository."""
    poll = models.ForeignKey(Poll)
    text = models.CharField(max_length=200)
    votes = models.IntegerField(default=0)

    def votes_percentage(self):
        """Calculates the percentage of votes for this choice."""
        total = self.poll.total_votes()
        return self.votes / float(total) * 100 if total > 0 else 0

    def __unicode__(self):
        """Returns a string representation of a choice."""
        return self.text
```

Jak widać, sonda zachowuje opis w jego `text` polu i datę publikacji w `pub_date` . Te pola są jedynymi tymi, które istnieją dla sondowania w bazie danych programu; `total_votes` pole jest obliczane w czasie wykonywania.

Wybór jest powiązany z sondowaniem za pomocą `poll` pola, zawiera opis w `text` i utrzymuje liczbę dla tego wyboru w `votes` . `votes_percentage`Pole jest obliczane w czasie wykonywania i nie można go znaleźć w bazie danych.

Pełną listę typów pól jest `CharField` (ograniczony tekst) `TextField` (nieograniczony tekst),,,,,,, `EmailField` `URLField` `DateTimeField` `IntegerField` `DecimalField` `BooleanField` `ForeignKey` , i `ManyToMany` . Każde pole przyjmuje pewne atrybuty, takie jak `max_length` . Ten `blank=True` atrybut oznacza, że pole jest opcjonalne; `null=true` oznacza, że wartość jest opcjonalna. Występuje również `choices` atrybut, który ogranicza wartości do wartości w tablicy wartości danych/Wyświetl krotek wartości. (Zobacz [odwołanie do pola modelu](https://docs.djangoproject.com/en/2.0/ref/models/fields/) w dokumentacji Django).

Można potwierdzić, co jest przechowywane w bazie danych, badając plik *DB. sqlite3* w projekcie przy użyciu narzędzia, takiego jak [przeglądarka SQLite](https://sqlitebrowser.org/). W bazie danych zobaczysz, że pole klucza obcego takie jak `poll` w modelu wyboru jest przechowywane jako `poll_id` ; Django obsługuje mapowanie automatycznie.

Ogólnie rzecz biorąc, praca z bazą danych w programie Django oznacza, że działa wyłącznie za pośrednictwem modeli, dzięki czemu Django może zarządzać podstawową bazą danych w Twoim imieniu.

### <a name="seed-the-database-from-samplesjson"></a>Wypełnianie bazy danych z samples.jsna

Początkowo baza danych nie zawiera żadnych sondowań. Możesz użyć interfejsu administracyjnego w adresie URL "/admin", aby dodać sondy ręcznie i można także odwiedzić stronę "/Seed" w uruchomionej witrynie, aby dodać inicjator bazy danych z sondowami zdefiniowanymi w *samples.jsaplikacji w* pliku.

*URLs.py* projektu Django ma dodany wzorzec adresu URL `url(r'^seed$', app.views.seed, name='seed'),` . `seed`Widok w *aplikacji/widokach. pr* ładuje *samples.jsw* pliku i tworzy niezbędne obiekty modelu. Django następnie automatycznie tworzy pasujące rekordy w źródłowej bazie danych.

Zwróć uwagę na użycie `@login_required` dekoratora, aby wskazać poziom autoryzacji dla widoku.

```python
@login_required
def seed(request):
    """Seeds the database with sample polls."""
    samples_path = path.join(path.dirname(__file__), 'samples.json')
    with open(samples_path, 'r') as samples_file:
        samples_polls = json.load(samples_file)

    for sample_poll in samples_polls:
        poll = Poll()
        poll.text = sample_poll['text']
        poll.pub_date = timezone.now()
        poll.save()

        for sample_choice in sample_poll['choices']:
            choice = Choice()
            choice.poll = poll
            choice.text = sample_choice
            choice.votes = 0
            choice.save()

    return HttpResponseRedirect(reverse('app:home'))
```

Aby zobaczyć efekt, najpierw uruchom aplikację, aby zobaczyć, że żadne sondy jeszcze nie istnieją. Następnie przejdź do adresu URL "/Seed" i po powrocie aplikacji do strony głównej powinieneś zobaczyć, że sondy staną się dostępne. Ponownie możesz przeanalizować plik RAW *DB. sqlite3* za pomocą narzędzia, takiego jak [przeglądarka SQLite](https://sqlitebrowser.org/).

![Sondowanie aplikacji sieci Web Django za pomocą inicjatora bazy danych](media/django/step06-app-with-seeded-database.png)

### <a name="question-is-it-possible-to-initialize-the-database-using-the-django-administrative-utility"></a>Pytanie: czy jest możliwe zainicjowanie bazy danych za pomocą narzędzia administracyjnego Django?

Odpowiedź: tak, możesz użyć [polecenia Django-admin loaddata](https://docs.djangoproject.com/en/2.0/ref/django-admin/#loaddata) , aby wykonać to samo zadanie co strona inicjatora w aplikacji. Podczas pracy nad pełną aplikacją internetową możesz użyć kombinacji dwóch metod: zainicjuj bazę danych z wiersza polecenia, a następnie przekonwertuj stronę inicjatora tutaj na interfejs API, do którego można wysłać dowolne inne dane JSON, zamiast polegać na zakodowanym pliku.

## <a name="step-6-3-use-migrations"></a>Krok 6-3: Użyj migracji

Po uruchomieniu `manage.py makemigrations` polecenia (za pomocą menu kontekstowego w programie Visual Studio) po utworzeniu projektu Django utworzył plik *App/migrations/0001_initial. PR* . Ten plik zawiera skrypt służący do tworzenia początkowych tabel bazy danych.

Ze względu na to, że w miarę upływu czasu zmienisz zmiany w modelach, Django ułatwiają aktualny schemat bazy danych z tymi modelami. Ogólny przepływ pracy jest następujący:

1. Wprowadź zmiany w modelach w pliku *models.py* .
1. W programie Visual Studio kliknij prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** i wybierz polecenie **Python**  >  **Django Utwórz migracje** . Jak opisano wcześniej, to polecenie generuje skrypty w *aplikacji/migracji* w celu migrowania bazy danych z jej bieżącego stanu do nowego stanu.
1. Aby zastosować skrypty do rzeczywistej bazy danych, ponownie kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Python**  >  **Django Migruj**.

Django śledzi, które migracje zostały zastosowane do każdej bazy danych, na przykład po uruchomieniu polecenia migracji, Django stosuje się niezależnie od tego, czy są potrzebne. Jeśli utworzysz nową, pustą bazę danych, na przykład uruchomienie polecenia migracji spowoduje jego aktualność przy użyciu bieżących modeli, stosując każdy skrypt migracji. Podobnie w przypadku zmiany wielu modeli i wygenerowania migracji na komputerze deweloperskim można zastosować migracje zbiorcze do produkcyjnej bazy danych, uruchamiając polecenie migracji na serwerze produkcyjnym. Django ponownie stosuje tylko te skrypty migracji, które zostały wygenerowane od czasu ostatniej migracji produkcyjnej bazy danych.

Aby zobaczyć efekt zmiany modelu, spróbuj wykonać następujące czynności:

1. Dodaj opcjonalne pole Author do modelu sondowania w *App/models. PR* , dodając następujący wiersz po `pub_date` polu, aby dodać pole opcjonalne `author` :

    ```python
    author = models.CharField(max_length=100, blank=True)
    ```

1. Zapisz plik, a następnie kliknij prawym przyciskiem myszy projekt **DjangoPolls** w **Eksplorator rozwiązań** i wybierz polecenie **Python**  >  **Django wykonaj migracje** .
1. Wybierz polecenie **projekt**  >  **Pokaż wszystkie pliki** , aby wyświetlić nowo wygenerowany skrypt w folderze **migracji** , którego nazwa rozpoczyna się od **002_auto_**. Kliknij prawym przyciskiem myszy ten plik i wybierz pozycję **Dołącz do projektu**. Następnie można wybrać pozycję **projekt**  >  ponownie **Pokaż wszystkie pliki** , aby przywrócić oryginalny widok. (Zobacz drugie pytanie poniżej, aby uzyskać szczegółowe informacje na temat tego kroku).
1. W razie potrzeby Otwórz ten plik, aby poznać, w jaki sposób program Django skryptuje zmianę stanu poprzedniego modelu z nowym stanem.
1. Kliknij prawym przyciskiem myszy projekt programu Visual Studio, a następnie wybierz pozycję **Python**  >  **Django Migruj** , aby zastosować zmiany do bazy danych.
1. W razie potrzeby Otwórz bazę danych w odpowiedniej przeglądarce, aby potwierdzić zmianę.

Ogólna funkcja migracji Django oznacza, że nie jest konieczne ręczne Zarządzanie schematem bazy danych. Po prostu wprowadź zmiany w modelach, wygeneruj skrypty migracji i zastosuj je za pomocą polecenia migracji.

### <a name="question-what-happens-if-i-forget-to-run-the-migrate-command-after-making-changes-to-models"></a>Pytanie: co się stanie, jeśli zapomnię uruchomić polecenie migracji po wprowadzeniu zmian w modelach?

Odpowiedź: Jeśli modele nie są zgodne z informacjami znajdującymi się w bazie danych, Django nie powiedzie się w czasie wykonywania z odpowiednimi wyjątkami. Na przykład jeśli zapomnisz zmigrować zmiany modelu pokazanej w poprzedniej sekcji, zobaczysz błąd **nie w takiej kolumnie: app_poll. Author**:

![Błąd wyświetlany, gdy zmiana modelu nie została zmigrowana](media/django/step06-exception-when-forgetting-to-migrate.png).

### <a name="question-why-doesnt-solution-explorer-show-newly-generated-scripts-after-running-django-make-migrations"></a>Pytanie: Dlaczego nie Eksplorator rozwiązań pokazać nowo generowanych skryptów po uruchomieniu Django dokonać migracji?

Odpowiedź: Mimo że nowo wygenerowane skrypty istnieją w folderze *aplikacji/migracji* i są stosowane podczas uruchamiania polecenia **migracji Django** , nie pojawiają się automatycznie w **Eksplorator rozwiązań** ponieważ nie zostały dodane do projektu programu Visual Studio. Aby je wyświetlić, najpierw wybierz polecenie **projekt**  >  **Pokaż wszystkie pliki** lub przycisk paska narzędzi przedstawiony na poniższej ilustracji. To polecenie powoduje, że **Eksplorator rozwiązań** pokazać wszystkie pliki w folderze projektu przy użyciu ikony konturu kropkowanego dla elementów, które nie zostały dodane do samego projektu. Kliknij prawym przyciskiem myszy pliki, które chcesz dodać, a następnie wybierz opcję **Dołącz do projektu**, która również obejmuje je w kontroli źródła przy następnym zatwierdzeniu.

![Polecenie include w projekcie w Eksplorator rozwiązań](media/django/step06-include-migrations-script-in-project.png)

### <a name="question-can-i-see-what-migrations-would-be-applied-before-running-the-migrate-command"></a>Pytanie: Czy można zobaczyć, jakie migracje zostaną zastosowane przed uruchomieniem polecenia migracji?

Odpowiedź: tak, użyj [polecenia Django-admin showmigrations](https://docs.djangoproject.com/en/2.0/ref/django-admin/#showmigrations).

## <a name="step-6-4-understand-the-views-and-page-templates-created-by-the-project-template"></a>Krok 6-4: informacje o widokach i szablonach stron utworzonych przez szablon projektu

Większość widoków wygenerowanych przez szablon "sondy Django Web projektu", takich jak widoki stron informacje i kontakty, jest bardzo podobna do widoków utworzonych przez szablon "Django projekt sieci Web", który pracował wcześniej w tym samouczku. Podobnie jak w przypadku aplikacji sondy jest to, że Strona główna korzysta z modeli, tak jak kilka dodanych stron do głosowania i wyświetlania wyników sondowania.

Aby rozpocząć od, pierwszy wiersz tablicy projektu Django `urlpatterns` w pliku *URLs.py* jest więcej niż tylko prosty Routing do widoku aplikacji. W zamian pobierany jest plik *URLs.py* aplikacji:

```python
from django.conf.urls import url, include
import app.views

urlpatterns = [
    url(r'^', include('app.urls', namespace="app")),
    # ..
]
```

Plik *App/URL. PR* zawiera bardziej interesujący kod routingu (dodane komentarze objaśniające):

```python
urlpatterns = [
    # Home page routing
    url(r'^$',
        app.views.PollListView.as_view(
            queryset=Poll.objects.order_by('-pub_date')[:5],
            context_object_name='latest_poll_list',
            template_name='app/index.html',),
        name='home'),

    # Routing for a poll page, which use URLs in the form <poll_id>/,
    # where the id number is captured as a group named "pk".
    url(r'^(?P<pk>\d+)/$',
        app.views.PollDetailView.as_view(
            template_name='app/details.html'),
        name='detail'),

    # Routing for <poll_id>/results pages, again using a capture group
    # named pk.
    url(r'^(?P<pk>\d+)/results/$',
        app.views.PollResultsView.as_view(
            template_name='app/results.html'),
        name='results'),

    # Routing for <poll_id>/vote pages, with the capture group named
    # poll_id this time, which becomes an argument passed to the view.
    url(r'^(?P<poll_id>\d+)/vote/$', app.views.vote, name='vote'),
]
```

Jeśli nie znasz bardziej złożonych wyrażeń regularnych, można wkleić wyrażenie do [regex101.com](https://regex101.com/) w celu wyjaśnienia w zwykłym języku. (Aby przejść do następnego ukośnika `/` , należy dodać ukośnik odwrotny, `\` przed nimi; Ucieczka nie jest konieczna w języku Python ze względu `r` na prefiks ciągu, co oznacza "RAW").

W Django, składnia `?P<name>pattern` tworzy grupę o nazwie `name` , która jest przenoszona jako argumenty do widoków w kolejności, w jakiej się znajdują. W pokazanym wcześniej kodzie `PollsDetailView` i `PollsResultsView` odebranie argumentu o nazwie `pk` i `app.views.vote` odebranie argumentu o nazwie `poll_id` .

Możesz również zobaczyć, że większość widoków nie tylko kieruje odwołania do funkcji widoku w *aplikacji/widokach. PR*. Zamiast tego, najlepiej odwoływać się do klasy w tym samym pliku, który pochodzi z `django.views.generic.ListView` lub `django.views.generic.DetailView` . Klasy bazowe zapewniają `as_view` metody, które przyjmują `template_name` argument do identyfikowania szablonu. `ListView`Klasa bazowa, jak używana dla strony głównej, oczekuje również `queryset` Właściwości zawierającej dane i `context_object_name` Właściwość o nazwie zmiennej, która ma być odwołująca się do danych w szablonie, w tym przypadku `latest_poll_list` .

Teraz można przeanalizować `PollListView` stronę główną, która jest zdefiniowana w następujący sposób w temacie *App/views. PR*:

```python
class PollListView(ListView):
    """Renders the home page, with a list of all polls."""
    model = Poll

    def get_context_data(self, **kwargs):
        context = super(PollListView, self).get_context_data(**kwargs)
        context['title'] = 'Polls'
        context['year'] = datetime.now().year
        return context
```

Wszystko gotowe do zidentyfikowania modelu, z którym działa widok (sondowanie), i przesłania `get_context_data` metodę w celu dodania `title` i `year` wartości do kontekstu.

Rdzeń szablonu (*templates/App/index.html*) jest następujący:

```html
{% if latest_poll_list %}
<table class="table table-hover">
    <tbody>
        {% for poll in latest_poll_list %}
        <tr>
            <td>
                <a href="{% url 'app:detail' poll.id %}">{{poll.text}}</a>
            </td>
        </tr>
        {% endfor %}
    </tbody>
</table>
{% else %}
<!-- ... other content omitted ... -->
{% endif %}
```

Po prostu, szablon odbiera listę obiektów sondowania w `latest_poll_list` , a następnie wykonuje iterację na tej liście, aby utworzyć wiersz tabeli zawierający link do każdej sondy przy użyciu wartości sondy `text` . W `{% url %}` tagu "App: Detail" odnosi się do wzorca adresu URL w polu *App/URL. PR* o nazwie "Detail", używając `poll.id` jako argumentu. Ten efekt polega na tym, że Django tworzy adres URL przy użyciu odpowiedniego wzorca i używa go dla linku. Ten bit w przyszłości oznacza, że w dowolnym momencie można zmienić ten wzorzec adresu URL, a wygenerowane linki są automatycznie aktualizowane.

`PollDetailView`Klasy i `PollResultsView` w *aplikacji/widoków. PR* (nie pokazano tutaj) wyglądają niemal identycznie z `PollListView` wyjątkiem tego, że pochodzą od `DetailView` zamiast tego. Ich odpowiednie szablony, *aplikacje/szablony/details.html* i *App/templates/results.html* następnie umieszczają odpowiednie pola z modeli wewnątrz różnych kontrolek HTML. Jednym unikatowym elementem w *details.html* jest to, że opcje sondy są zawarte w formularzu HTML, który po przesłaniu wysyła wpis do adresu URL/vote. Jak widać wcześniej, ten wzorzec adresu URL jest kierowany do `app.views.vote` , który jest implementowany w następujący sposób (należy zwrócić uwagę na `poll_id` argument, który jest ponownie nazwaną grupą w wyrażeniu regularnym używanym w routingu dla tego widoku):

```python
def vote(request, poll_id):
    """Handles voting. Validates input and updates the repository."""
    poll = get_object_or_404(Poll, pk=poll_id)
    try:
        selected_choice = poll.choice_set.get(pk=request.POST['choice'])
    except (KeyError, Choice.DoesNotExist):
        return render(request, 'app/details.html', {
            'title': 'Poll',
            'year': datetime.now().year,
            'poll': poll,
            'error_message': "Please make a selection.",
    })
    else:
        selected_choice.votes += 1
        selected_choice.save()
        return HttpResponseRedirect(reverse('app:results', args=(poll.id,)))
```

W tym miejscu widok nie ma odpowiadającego mu szablonu, takiego jak inne strony. Zamiast tego sprawdza poprawność wybranej sondy, pokazując 404, jeśli Sonda nie istnieje (tylko w przypadku, gdy ktoś wprowadzi adres URL, na przykład "głosowania/1a2b3c"). Następnie sprawdza, czy wybrany głos jest prawidłowy dla sondy. W przeciwnym razie `except` blok po prostu renderuje ponownie stronę szczegółów z komunikatem o błędzie. Jeśli wybór jest prawidłowy, wyświetli się powiększanie głosu i przekierowania na stronie wyników.

## <a name="step-6-5-create-a-custom-administration-interface"></a>Krok 6-5: Tworzenie niestandardowego interfejsu administracyjnego

Ostatnie fragmenty szablonu "Django" projektu sieci Web "sonds" są rozszerzeniami niestandardowymi domyślnego interfejsu administracyjnego Django, jak pokazano wcześniej w tym artykule w kroku 6-1. Domyślny interfejs zapewnia zarządzanie użytkownikami i grupami, ale nic więcej. Szablon projektu sondowania dodaje funkcje, które umożliwiają również zarządzanie sondowaniem.

Po pierwsze, wzorce URL w *URLs.py* projektu Django są `url(r'^admin/', include(admin.site.urls)),` domyślnie włączone. wzór "admin/doc" jest również dołączony do komentarza.

Następnie aplikacja zawiera plik *admin.py*, który Django automatycznie uruchamiany podczas odwiedzania interfejsu administracyjnego, dzięki czemu można dołączać do `django.contrib.admin` `INSTALLED_APPS` tablicy *Settings.py*. Kod w tym pliku, zgodnie z szablonem projektu, jest następujący:

```python
from django.contrib import admin
from app.models import Choice, Poll

class ChoiceInline(admin.TabularInline):
    """Choice objects can be edited inline in the Poll editor."""
    model = Choice
    extra = 3

class PollAdmin(admin.ModelAdmin):
    """Definition of the Poll editor."""
    fieldsets = [
        (None, {'fields': ['text']}),
        ('Date information', {'fields': ['pub_date']}),
    ]
    inlines = [ChoiceInline]
    list_display = ('text', 'pub_date')
    list_filter = ['pub_date']
    search_fields = ['text']
    date_hierarchy = 'pub_date'

admin.site.register(Poll, PollAdmin)
```

Jak widać, `PollAdmin` Klasa dziedziczy z `django.contrib.admin.ModelAdmin` i dostosowuje liczbę pól przy użyciu nazw z `Poll` modelu, którymi zarządza. Te pola są opisane na stronie [Opcje ModelAdmin](https://docs.djangoproject.com/en/2.0/ref/contrib/admin/#modeladmin-options) w dokumentacji Django.

Wywołanie w celu `admin.site.register` połączenia tej klasy z modelem ( `Poll` ) i zawiera je w interfejsie administratora. Ogólny wynik jest przedstawiony poniżej:

![Widok administracyjny aplikacji Project Web Django dla ankiet](media/django/step06-polls-administrative-interface.png)

## <a name="next-steps"></a>Następne kroki

> [!Note]
> Jeśli Twoje rozwiązanie programu Visual Studio zostało zatwierdzone do kontroli źródła w trakcie tego samouczka, teraz jest dobrym terminem do wykonania kolejnego zatwierdzenia. Twoje rozwiązanie powinno być zgodne z kodem źródłowym samouczka w witrynie GitHub: [Microsoft/Python-Sample-vs-Learning-Django](https://github.com/Microsoft/python-sample-vs-learning-django).

Teraz udało Ci się przeanalizować w całości szablon "pusty projekt sieci Web Django", "projekt sieci Web" Django "i" sondy projektu sieci Web Django "w programie Visual Studio. Znasz już wszystkie podstawowe informacje o Django, takie jak Używanie widoków i szablonów oraz Eksplorowanie routingu, uwierzytelniania i korzystania z modeli baz danych. Teraz powinno być możliwe tworzenie aplikacji sieci Web z własnymi widokami i modelami, które są potrzebne.

Uruchamianie aplikacji sieci Web na komputerze deweloperskim to tylko jeden krok w udostępnieniu aplikacji klientom. Następne kroki mogą obejmować następujące zadania:

- Wdróż aplikację sieci Web na serwerze produkcyjnym, takim jak Azure App Service. Zobacz [Publikowanie w Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md).

- Dostosuj stronę 404, tworząc szablon o nazwie *templates/404.html*. Gdy jest obecny, Django używa tego szablonu zamiast domyślnego. Aby uzyskać więcej informacji, zobacz [widoki błędów](https://docs.djangoproject.com/en/2.0/ref/views/#error-views) w dokumentacji Django.

- Zapisz testy jednostkowe w *tests.py*; Szablony projektów programu Visual Studio zawierają punkty początkowe, a więcej informacji można znaleźć na stronie [Tworzenie pierwszej aplikacji Django, część 5 — testowanie](https://docs.djangoproject.com/en/2.0/intro/tutorial05/) i [testowanie w Django](https://docs.djangoproject.com/en/2.0/topics/testing/) w dokumentacji Django.

- Zmień aplikację z oprogramowania SQLite na magazyn danych na poziomie produkcyjnym, taki jak PostgreSQL, MySQL i SQL Server (wszystkie mogą być hostowane na platformie Azure). Zgodnie z opisem w [przypadku korzystania z oprogramowania SQLite](https://www.sqlite.org/whentouse.html) (SQLite.org), program SQLite działa prawidłowo w przypadku witryn o niskiej i średnim ruchu z mniej niż 100 000 trafień/dzień, ale nie jest to zalecane w przypadku wyższych woluminów. Jest on również ograniczony do jednego komputera, dlatego nie można go używać w żadnym scenariuszu obejmującym wiele serwerów, takim jak równoważenie obciążenia i replikacja geograficzna. Aby uzyskać informacje na temat pomocy technicznej Django dla innych baz danych, zobacz [Konfiguracja bazy danych](https://docs.djangoproject.com/en/2.0/intro/tutorial02/#database-setup). Możesz również użyć [zestawu Azure SDK dla języka Python](/azure/python/) do pracy z usługami Azure Storage, takimi jak tabele i obiekty blob.

- Skonfiguruj potok ciągłej integracji/ciągłego wdrażania w usłudze, takiej jak Azure DevOps. Oprócz pracy z kontrolą źródła (za pośrednictwem Azure Repos lub GitHub lub w innym miejscu) można skonfigurować projekt platformy Azure DevOps, aby automatycznie uruchamiał testy jednostkowe jako wstępnie wymagane dla wydania, a także skonfigurować potok do wdrożenia na serwerze przejściowym w celu przeprowadzenia dodatkowych testów przed wdrożeniem w środowisku produkcyjnym. Ponadto platforma Azure DevOps integruje się z rozwiązaniami do monitorowania, takimi jak App Insights i zamyka cały cykl dzięki narzędziom do planowania Agile. Aby uzyskać więcej informacji, zobacz Tworzenie potoku ciągłej integracji/ciągłego wdrażania [dla języka Python za pomocą projektu DevOps platformy Azure](/azure/devops-project/azure-devops-project-python?view=vsts&preserve-view=true) , a także ogólnej [dokumentacji usługi Azure DevOps](/azure/devops/?view=vsts&preserve-view=true).

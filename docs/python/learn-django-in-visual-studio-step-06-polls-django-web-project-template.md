---
title: Dowiedz się samouczek Django w programie Visual Studio krok 6, Szablon projektu Ankiety
titleSuffix: ''
description: Przewodnik po podstawach Django w kontekście projektów programu Visual Studio, w szczególności funkcje szablonu projektu sieci Web Usługi Polls Django, takie jak dostosowanie administracyjne.
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: c1fe3db702508267e96dc79f2f789a17a7edf98b
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "75755575"
---
# <a name="step-6-use-the-polls-django-web-project-template"></a>Krok 6: Użyj szablonu projektu internetowego Ankiety Django

**Poprzedni krok: [Uwierzytelnianie użytkowników w Django](learn-django-in-visual-studio-step-05-django-authentication.md)**

Po zrozumieniu szablonu "Django Web Project" programu Visual Studio, możesz teraz przyjrzeć się trzeciemu szablonowi Django, "Polls Django Web Project", który opiera się na tej samej podstawie kodu i demonstruje pracę z bazą danych.

W tym kroku dowiesz się, jak:

> [!div class="checklist"]
> - Tworzenie projektu na podstawie szablonu i inicjowanie bazy danych (krok 6-1)
> - Opis modeli danych (krok 6-2)
> - Stosowanie migracji (krok 6-3)
> - Opis widoków i szablonów stron utworzonych przez szablon projektu (krok 6-4)
> - Tworzenie niestandardowego interfejsu administracyjnego (krok 6-5)

Projekt stworzony przy użyciu tego szablonu jest podobny do tego, co otrzymujesz, wykonując samouczek [Pisanie pierwszej aplikacji Django](https://docs.djangoproject.com/en/2.0/intro/tutorial01/) w dokumentach Django. Aplikacja internetowa składa się z witryny publicznej, która umożliwia użytkownikom wyświetlanie ankiet i głosowanie w nich, wraz z niestandardowym interfejsem administracyjnym, za pomocą którego można zarządzać ankietami. Używa tego samego systemu uwierzytelniania co szablon "Django Web Project" i w większym zakresie wykorzystuje bazę danych, implementując modele Django, jak zostały zbadane w poniższych sekcjach.

## <a name="step-6-1-create-the-project-and-initialize-the-database"></a>Krok 6-1: Tworzenie projektu i inicjowanie bazy danych

1. W programie Visual Studio przejdź do **programu Solution Explorer**, kliknij prawym przyciskiem myszy rozwiązanie **LearningDjango** utworzone wcześniej w tym samouczku i wybierz pozycję **Dodaj** > **nowy projekt**. (Alternatywnie, jeśli chcesz użyć nowego rozwiązania, wybierz **pozycję Plik** > **nowego** > **projektu).**

1. W nowym oknie dialogowym projektu wyszukaj i wybierz szablon **Ankiety Django Web Project,** zadzwoń do projektu "DjangoPolls" i wybierz **PRZYCISK OK**.

1. Podobnie jak inne szablony projektów w programie Visual Studio, szablon "Sonduje django Web Project" zawiera plik *requirements.txt,* program Visual Studio monituje o zainstalowanie tych zależności. Wybierz opcję **Zainstaluj w środowisku wirtualnym,** a następnie w oknie dialogowym **Dodaj środowisko wirtualne** wybierz pozycję **Utwórz,** aby zaakceptować wartości domyślne.

1. Po zakończeniu konfigurowania środowiska wirtualnego w Pythonie postępuj zgodnie z instrukcjami wyświetlanymi w *wyświetlonym readme.html,* aby zainicjować bazę danych i utworzyć superużytkownika Django (czyli administratora). Kroki te mają polegać na pierwszym kliknięciu prawym przyciskiem myszy projektu **DjangoPolls** w **Eksploratorze rozwiązań**, wybraniu polecenia **Python** > **Django Migrate,** a następnie ponownego kliknięcia projektu prawym przyciskiem myszy, wybrania polecenia **Python** > **Django Create Superuser** i postępuj zgodnie z instrukcjami. (Jeśli spróbujesz najpierw utworzyć superużytnika, zostanie wyświetlony błąd, ponieważ baza danych nie została zainicjowana).

1. Ustaw projekt **DjangoPolls** jako domyślny dla rozwiązania programu Visual Studio, klikając prawym przyciskiem myszy ten projekt w **Eksploratorze rozwiązań** i wybierając **pozycję Ustaw jako projekt startowy.** Projekt uruchamiania, który jest wyświetlany pogrubioną czcionką, jest tym, co jest uruchamiane po uruchomieniu debugera.

1. Wybierz **debugowanie** > **rozpocznij debugowanie** **(F5)** lub użyj przycisku Serwera sieci **Web** na pasku narzędzi, aby uruchomić serwer:

    ![Uruchamianie przycisku paska narzędzi serwera sieci Web w programie Visual Studio](media/django/run-web-server-toolbar-button.png)

1. Aplikacja utworzona przez szablon ma trzy strony: Strona główna, Informacje i Kontakt, które można nawigować między za pomocą górnego paska nawigacji. Poświęć minutę lub dwie, aby zbadać różne części aplikacji (strony Informacje i Kontakty są bardzo podobne do "Django Web Project" i nie są dalej omawiane).

    ![Pełny widok przeglądarki aplikacji Polls Django Web Project](media/django/step06-full-app-view.png)

1. Wybierz również **łącze Administracja** na pasku nawigacyjnym, na którym jest wyświetlany ekran logowania, aby wykazać, że interfejs administracyjny jest autoryzowany tylko dla uwierzytelnionych administratorów. Użyj poświadczeń superużytów i zostaniesz przekierowany do strony "/admin", która jest domyślnie włączona podczas korzystania z tego szablonu projektu.

    ![Widok administracyjny aplikacji Polls Django Web Project](media/django/step06-polls-administrative-interface.png)

1. Możesz pozostawić aplikację z uruchomiona dla sekcji, które należy wykonać.

    Jeśli chcesz zatrzymać aplikację i [zatwierdzić zmiany w formancie źródłowym,](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control)najpierw otwórz stronę **Zmiany** w **Eksploratorze zespołu,** kliknij prawym przyciskiem myszy folder środowiska wirtualnego (prawdopodobnie **env)** i wybierz pozycję **Ignoruj te elementy lokalne**.

### <a name="examine-the-project-contents"></a>Sprawdzanie zawartości projektu

Jak wspomniano wcześniej. wiele z tego, co znajduje się w projekcie utworzonym na podstawie szablonu "Ankiety Django Web Project" powinno być znane, jeśli eksplorujesz inne szablony projektów w programie Visual Studio. Dodatkowe kroki w tym artykule podsumować bardziej znaczące zmiany i uzupełnienia, a mianowicie modeli danych i dodatkowych widoków.

### <a name="question-what-does-the-django-migrate-command-do"></a>Pytanie: Do czego działa polecenie Django Migrate?

Odpowiedź: polecenie **Django Migrate** uruchamia `manage.py migrate` specjalnie polecenie, które uruchamia wszystkie skrypty w folderze *app/migrations,* które nie zostały wcześniej uruchomione. W takim przypadku polecenie uruchamia skrypt *0001_initial.py* w tym folderze, aby skonfigurować niezbędny schemat w bazie danych.

Sam skrypt migracji jest `manage.py makemigrations` tworzony przez polecenie, które skanuje plik *models.py* aplikacji, porównuje go z bieżącym stanem bazy danych, a następnie generuje skrypty niezbędne do migracji schematu bazy danych w celu dopasowania do bieżących modeli. Ta funkcja Django jest bardzo potężna, gdy aktualizujesz i modyfikujesz swoje modele w czasie. Generując i uruchamiając migracje, modele i baza danych są zsynchronizowane z niewielkimi trudnościami.

Z migracją pracujesz w kroku 6-3 w dalszej części tego artykułu.

## <a name="step-6-2-understand-data-models"></a>Krok 6-2: Zrozumienie modeli danych

Modele aplikacji o nazwie Sonda i Wybór są zdefiniowane w *aplikacji/models.py*. Każda z nich jest klasą Języka Python, która wywodzi się z `django.db.models.Model` i używa metod `models` klasy, takich jak `CharField` i `IntegerField` do definiowania pól w modelu, które mapują do kolumn bazy danych.

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

Jak widać, ankieta zachowuje opis w `text` swoim polu i `pub_date`datę publikacji w . Te pola są jedynymi, które istnieją dla ankiety w bazie danych; `total_votes` pole jest obliczane w czasie wykonywania.

Wybór jest powiązany z `poll` ankietą za pośrednictwem `text`pola, zawiera opis w `votes`polu i zachowuje liczbę dla tego wyboru w . Pole `votes_percentage` jest obliczane w czasie wykonywania i nie znajduje się w bazie danych.

Pełna lista typów pól `CharField` to `TextField` (tekst ograniczony) `EmailField` `URLField`(tekst nieograniczony), , , `DateTimeField`, `IntegerField`, `DecimalField`, `BooleanField`, `ForeignKey`, i `ManyToMany`. Każde pole ma pewne `max_length`atrybuty, takie jak . Atrybut `blank=True` oznacza, że pole jest opcjonalne; `null=true` oznacza, że wartość jest opcjonalna. Istnieje również `choices` atrybut, który ogranicza wartości do wartości w tablicy krotek wartości danych/wartości wyświetlania. (Zobacz [odwołanie do pola Model](https://docs.djangoproject.com/en/2.0/ref/models/fields/) w dokumentacji Django).

Możesz potwierdzić dokładnie to, co jest przechowywane w bazie danych, badając plik *db.sqlite3* w projekcie za pomocą narzędzia takiego jak [przeglądarka SQLite](https://sqlitebrowser.org/). W bazie danych widać, że pole `poll` klucza obcego, `poll_id`takie jak w modelu Wyboru, jest przechowywane jako ; Django automatycznie obsługuje mapowanie.

Ogólnie rzecz biorąc, praca z bazą danych w Django oznacza pracę wyłącznie za pośrednictwem modeli, dzięki czemu Django może zarządzać podstawową bazą danych w Twoim imieniu.

### <a name="seed-the-database-from-samplesjson"></a>Materiał siewny bazy danych z pliku samples.json

Początkowo baza danych nie zawiera żadnych ankiet. Za pomocą interfejsu administracyjnego w adresie URL "/admin" można ręcznie dodawać ankiety, a także odwiedzić stronę "/seed" w uruchomionej witrynie, aby dodać bazę danych źródłową z ankietami zdefiniowanymi w pliku *samples.json* aplikacji.

*urls.py* projektu Django ma dodatkowy wzorzec `url(r'^seed$', app.views.seed, name='seed'),`adresu URL, . Widok `seed` w *aplikacji/views.py* ładuje plik *samples.json* i tworzy niezbędne obiekty modelu. Django następnie automatycznie tworzy pasujące rekordy w podstawowej bazie danych.

Należy zwrócić uwagę `@login_required` na użycie dekoratora, aby wskazać poziom autoryzacji dla widoku.

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

Aby zobaczyć efekt, uruchom aplikację najpierw, aby zobaczyć, że nie ma jeszcze żadnych ankiet. Następnie odwiedź adres URL "/seed", a gdy aplikacja powróci do strony głównej, zobaczysz, że ankiety stały się dostępne. Ponownie, zapraszam do zbadania surowego pliku *db.sqlite3* za pomocą narzędzia, takiego jak [przeglądarka SQLite](https://sqlitebrowser.org/).

![Sonduje aplikację Django Web Project z rozstawioną bazą danych](media/django/step06-app-with-seeded-database.png)

### <a name="question-is-it-possible-to-initialize-the-database-using-the-django-administrative-utility"></a>Pytanie: Czy możliwe jest zainicjowanie bazy danych za pomocą narzędzia administracyjnego Django?

Odpowiedź: Tak, możesz użyć [polecenia django-admin loaddata,](https://docs.djangoproject.com/en/2.0/ref/django-admin/#loaddata) aby wykonać to samo zadanie, co strona wysiewu w aplikacji. Podczas pracy z pełną aplikacją sieci web można użyć kombinacji dwóch metod: zainicjować bazę danych z wiersza polecenia, a następnie przekonwertować stronę źródłową tutaj do interfejsu API, do którego można wysłać inne dowolnego dowolnego dowolnego JSON zamiast polegać na pliku zakodowane.

## <a name="step-6-3-use-migrations"></a>Krok 6-3: Użyj migracji

Po uruchomieniu `manage.py makemigrations` polecenia (przy użyciu menu kontekstowego w programie Visual Studio) po utworzeniu projektu, Django utworzył *plik aplikacji/migracji/0001_initial.py.* Ten plik zawiera skrypt, który tworzy początkowe tabele bazy danych.

Ponieważ nieuchronnie będziesz wprowadzać zmiany w modelach w czasie, Django ułatwia śledzenie schematu podstawowej bazy danych z tymi modelami. Ogólny przepływ pracy jest następujący:

1. Wprowadzanie zmian w modelach w pliku *models.py.*
1. W programie Visual Studio kliknij prawym przyciskiem myszy projekt w **Eksploratorze rozwiązań** i wybierz polecenie **Sterowanie** > migracjami języka Python**Django.** Jak opisano wcześniej, to polecenie generuje skrypty w *aplikacji/migracji* do migracji bazy danych z bieżącego stanu do nowego stanu.
1. Aby zastosować skrypty do rzeczywistej bazy danych, kliknij prawym przyciskiem myszy projekt ponownie i wybierz **python** > **Django Migrate**.

Django śledzi, które migracje zostały zastosowane do dowolnej bazy danych, tak że po uruchomieniu polecenia migracji, Django stosuje niezależnie od migracji są potrzebne. Jeśli na przykład utworzysz nową, pustą bazę danych, polecenie migracji spowoduje jej uaktualnienie w bieżących modelach, stosując każdy skrypt migracji. Podobnie, jeśli dokonasz wielu zmian modelu i wygenerujesz migracje na komputerze deweloperskim, możesz zastosować skumulowane migracje do produkcyjnej bazy danych, uruchamiając polecenie migracji na serwerze produkcyjnym. Django ponownie stosuje tylko te skrypty migracji, które zostały wygenerowane od ostatniej migracji produkcyjnej bazy danych.

Aby zobaczyć efekt zmiany modelu, spróbuj wykonać następujące czynności:

1. Dodaj opcjonalne pole autora do modelu Sondowanie w *aplikacji/models.py,* dodając następujący wiersz po polu, `pub_date` aby dodać pole opcjonalne: `author`

    ```python
    author = models.CharField(max_length=100, blank=True)
    ```

1. Zapisz plik, a następnie kliknij prawym przyciskiem myszy projekt **DjangoPolls** w **Eksploratorze rozwiązań** i wybierz polecenie **Python** > **Django Make Migrations.**
1. Wybierz polecenie **Project** > **Show All Files,** aby wyświetlić nowo wygenerowany skrypt w folderze **migracji,** którego nazwa zaczyna się od **002_auto_**. Kliknij prawym przyciskiem myszy ten plik i wybierz pozycję **Uwzględnij w programie Project**. Następnie można ponownie wybrać opcję**Pokaż wszystkie pliki** w programie **Project,** > aby przywrócić oryginalny widok. (Szczegółowe informacje na temat tego kroku można znaleźć w drugim pytaniu poniżej).
1. W razie potrzeby otwórz ten plik, aby sprawdzić, jak Django skrypty zmiany z poprzedniego stanu modelu do nowego stanu.
1. Kliknij prawym przyciskiem myszy projekt programu Visual Studio ponownie i **wybierz** > python**Django Migrate,** aby zastosować zmiany do bazy danych.
1. W razie potrzeby otwórz bazę danych w odpowiedniej przeglądarce, aby potwierdzić zmianę.

Ogólnie rzecz biorąc, funkcja migracji Django oznacza, że nigdy nie musisz ręcznie zarządzać schematem bazy danych. Wystarczy wprowadzić zmiany w modelach, wygenerować skrypty migracji i zastosować je za pomocą polecenia migracji.

### <a name="question-what-happens-if-i-forget-to-run-the-migrate-command-after-making-changes-to-models"></a>Pytanie: Co się stanie, jeśli zapomnę uruchomić polecenie migracji po wszedniu zmian w modelach?

Odpowiedź: Jeśli modele nie pasują do tego, co jest w bazie danych, Django kończy się niepowodzeniem w czasie wykonywania z odpowiednimi wyjątkami. Na przykład, jeśli zapomnisz przeprowadzić migrację zmiany modelu pokazanej w poprzedniej sekcji, zostanie wyświetlony błąd **bez takiej kolumny: app_poll.author**:

![Błąd wyświetlany, gdy zmiana modelu nie została zmigrowana](media/django/step06-exception-when-forgetting-to-migrate.png).

### <a name="question-why-doesnt-solution-explorer-show-newly-generated-scripts-after-running-django-make-migrations"></a>Pytanie: Dlaczego Eksplorator rozwiązań nie pokazuje nowo wygenerowanych skryptów po uruchomieniu Django Make Migrations?

Odpowiedź: Chociaż nowo wygenerowane skrypty istnieją w folderze *aplikacji/migracji* i są stosowane podczas uruchamiania polecenia **Django Migrate,** nie pojawiają się one automatycznie w **Eksploratorze rozwiązań,** ponieważ nie zostały dodane do projektu programu Visual Studio. Aby były widoczne, należy najpierw zaznaczyć polecenie menu **Project** > **Show All Files** lub przycisk paska narzędzi opisany na poniższej ilustracji. To polecenie powoduje, że **Eksplorator rozwiązań** wyświetla wszystkie pliki w folderze projektu, używając kropkowanej ikony konspektu dla elementów, które nie zostały dodane do samego projektu. Kliknij prawym przyciskiem myszy pliki, które chcesz dodać, i wybierz pozycję **Uwzględnij w programie Project,** która również uwzględnia je w formancie źródłowym z następnym zatwierdzeniem.

![Polecenie Dołącz do projektu w Eksploratorze rozwiązań](media/django/step06-include-migrations-script-in-project.png)

### <a name="question-can-i-see-what-migrations-would-be-applied-before-running-the-migrate-command"></a>Pytanie: Czy mogę zobaczyć, jakie migracje zostaną zastosowane przed uruchomieniem polecenia migracji?

Odpowiedź: Tak, użyj [polecenia django-admin showmigrations](https://docs.djangoproject.com/en/2.0/ref/django-admin/#showmigrations).

## <a name="step-6-4-understand-the-views-and-page-templates-created-by-the-project-template"></a>Krok 6-4: Zrozumienie widoków i szablonów stron utworzonych przez szablon projektu

Większość widoków generowanych przez szablon "Polls Django Web Project", takich jak widoki na stronach Informacje i Kontakt, są bardzo podobne do widoków utworzonych przez szablon "Django Web Project", z którymi pracowałeś wcześniej w tym samouczku. Co innego w aplikacji Ankiety jest to, że jego strona główna korzysta z modeli, podobnie jak kilka dodanych stron do głosowania i wyświetlania wyników ankiety.

Na początek pierwszy wiersz w `urlpatterns` tablicy projektu Django w *urls.py* pliku jest czymś więcej niż tylko prostym routingiem do widoku aplikacji. Zamiast tego pobiera w aplikacji własny plik *urls.py:*

```python
from django.conf.urls import url, include
import app.views

urlpatterns = [
    url(r'^', include('app.urls', namespace="app")),
    # ..
]
```

Plik *app/urls.py* zawiera kilka bardziej interesujących kodów routingu (dodano komentarze wyjaśniające):

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

Jeśli nie znasz bardziej złożonych wyrażeń regularnych używanych w tym miejscu, możesz wkleić wyrażenie do [regex101.com,](https://regex101.com/) aby uzyskać wyjaśnienie w prostym języku. (Musisz uciec do przodu `/` ukośniki, dodając `\` ukośnik wstecz, przed nimi; ucieczka nie jest konieczne w Pythonie ze względu na `r` prefiks na ciąg, co oznacza "raw").

W Django składnia `?P<name>pattern` tworzy grupę `name`o nazwie , która jest przekazywana jako argumenty do widoków w kolejności, w jakiej się pojawiają. W `PollsDetailView` kodzie pokazanym `PollsResultsView` wcześniej i `pk` `app.views.vote` otrzymać argument `poll_id`o nazwie i odbiera argument o nazwie .

Widać również, że większość widoków to nie tylko bezpośrednie odwołania do funkcji widoku w *aplikacji/views.py*. Zamiast tego większość z nich odnosi się do `django.views.generic.ListView` klasy `django.views.generic.DetailView`w tym samym pliku, która pochodzi od lub . Klasy podstawowe zapewniają `as_view` metody, które `template_name` przyjmują argument do identyfikowania szablonu. Klasa `ListView` podstawowa, używana dla strony głównej, `queryset` oczekuje również właściwości zawierającej dane i właściwości o nazwie zmiennej, `context_object_name` za pomocą której `latest_poll_list`chcesz odwołać się do danych w szablonie, w tym przypadku .

Teraz możesz sprawdzić `PollListView` stronę główną, która jest zdefiniowana w *aplikacji / views.py:*

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

Wszystko, co jest zrobione w tym miejscu jest zidentyfikowanie modelu, `get_context_data` który działa `title` `year` z widoku (Ankieta) i zastępuje metodę dodawania i wartości do kontekstu.

Rdzeń szablonu (*templates/app/index.html*) jest następujący:

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

Mówiąc prościej, szablon odbiera listę `latest_poll_list`Poll obiektów w , a następnie iteruje za pośrednictwem tej listy, `text` aby utworzyć wiersz tabeli, który zawiera łącze do każdej ankiety przy użyciu wartości ankiety. W `{% url %}` tagu "app:detail" odnosi się do wzorca adresu URL w *aplikacji/urls.py* o nazwie "detail", używając `poll.id` jako argumentu. Efektem tego jest to, że Django tworzy adres URL przy użyciu odpowiedniego wzorca i używa go do linku. Ten bit przyszłości korekty oznacza, że można zmienić ten wzorzec adresu URL w dowolnym momencie i wygenerowane linki automatycznie zaktualizować do dopasowania.

I `PollDetailView` `PollResultsView` klasy w *app/views.py* (nie pokazano tutaj) wyglądają prawie `PollListView` `DetailView` identycznie, z wyjątkiem tego, że pochodzą one od zamiast. Ich odpowiednie szablony, *app/templates/details.html* i *app/templates/results.html* następnie umieszczają odpowiednie pola z modeli w różnych formantach HTML. Jednym z unikalnych elementów w *details.html* jest to, że wybory dla ankiety są zawarte w formularzu HTML, który po przesłaniu ma POST do /vote URL. Jak widać wcześniej, ten wzorzec adresu URL jest kierowany `app.views.vote` `poll_id` do , który jest implementowany w następujący sposób (zwróć uwagę na argument, który jest ponownie nazwaną grupą w wyrażeniu regularnym używanym w routingu dla tego widoku):

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

W tym miejscu widok nie ma własnego odpowiedniego szablonu, podobnie jak inne strony. Zamiast tego sprawdza poprawność wybranej ankiety, pokazując 404, jeśli ankieta nie istnieje (tylko w przypadku, gdy ktoś wpisze adres URL, taki jak "głosuj/1a2b3c"). Następnie upewnia się, że wybrany wybór jest ważny dla ankiety. Jeśli nie, `except` blok po prostu renderuje stronę szczegółów ponownie z komunikatem o błędzie. Jeśli wybór jest prawidłowy, widok zlicza głos i przekierowuje do strony wyników.

## <a name="step-6-5-create-a-custom-administration-interface"></a>Krok 6-5: Tworzenie niestandardowego interfejsu administracyjnego

Ostatnie fragmenty szablonu "Polls Django Web Project" to niestandardowe rozszerzenia domyślnego interfejsu administracyjnego Django, jak pokazano wcześniej w tym artykule w kroku 6-1. Domyślny interfejs zapewnia zarządzanie użytkownikami i grupami, ale nic więcej. Szablon projektu Ankiety dodaje funkcje, które umożliwiają również zarządzanie ankietami.

Po pierwsze, wzorce adresów URL w *urls.py* `url(r'^admin/', include(admin.site.urls)),` projektu Django zostały uwzględnione domyślnie; "admin / doc" wzór jest również wliczone, ale skomentował.

Aplikacja następnie zawiera *plik admin.py*, który Django automatycznie działa podczas odwiedzania interfejsu `django.contrib.admin` administracyjnego dzięki włączeniu do `INSTALLED_APPS` tablicy *settings.py*. Kod w tym pliku, zgodnie z szablonem projektu, jest następujący:

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

Jak widać, `PollAdmin` klasa pochodzi z `django.contrib.admin.ModelAdmin` i dostosowuje liczbę swoich pól przy `Poll` użyciu nazw z modelu, który zarządza. Pola te są opisane w [opcjach ModelAdmin](https://docs.djangoproject.com/en/2.0/ref/contrib/admin/#modeladmin-options) w dokumentacji Django.

Wywołanie `admin.site.register` następnie łączy tę klasę z`Poll`modelem ( ) i zawiera ją w interfejsie administratora. Ogólny wynik jest pokazany poniżej:

![Widok administracyjny aplikacji Polls Django Web Project](media/django/step06-polls-administrative-interface.png)

## <a name="next-steps"></a>Następne kroki

> [!Note]
> Jeśli zostały popełnienia rozwiązania programu Visual Studio do kontroli źródła w trakcie tego samouczka, teraz jest dobry czas, aby wykonać inne zatwierdzenie. Twoje rozwiązanie powinno być zgodne z kodem źródłowym samouczka na GitHub: [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django).

Teraz zbadałeś całość szablonów "Blank Django Web Project", "Django Web Project" i "Polls Django Web Project" w programie Visual Studio. Nauczyłeś się wszystkich podstaw Django, takich jak korzystanie z widoków i szablonów, i zbadałeś routing, uwierzytelnianie i używanie modeli baz danych. Teraz powinieneś mieć możliwość tworzenia własnej aplikacji sieci web z dowolnymi widokami i modelami, których potrzebujesz.

Uruchamianie aplikacji sieci web na komputerze deweloperskim to tylko jeden krok w udostępnianiu aplikacji klientom. Następne kroki mogą obejmować następujące zadania:

- Wdrażanie aplikacji sieci web na serwerze produkcyjnym, takim jak usługa Azure App Service. Zobacz [Publikowanie w usłudze Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md).

- Dostosuj stronę 404, tworząc szablon o nazwie *templates/404.html*. Gdy jest obecny, Django używa tego szablonu zamiast domyślnego. Aby uzyskać więcej informacji, zobacz [Widoki błędów](https://docs.djangoproject.com/en/2.0/ref/views/#error-views) w dokumentacji Django.

- Napisz testy jednostkowe w *tests.py*; Szablony projektów programu Visual Studio zapewniają punkty wyjścia dla tych, a więcej informacji można znaleźć na [Pisanie pierwszej aplikacji Django, część 5 - testowanie](https://docs.djangoproject.com/en/2.0/intro/tutorial05/) i [testowanie w Django](https://docs.djangoproject.com/en/2.0/topics/testing/) w dokumentacji Django.

- Zmień aplikację z SQLite do magazynu danych na poziomie produkcji, takich jak PostgreSQL, MySQL i SQL Server (z których wszystkie mogą być hostowane na platformie Azure). Zgodnie z [opisem kiedy używać SQLite](https://www.sqlite.org/whentouse.html) (sqlite.org), SQLite działa dobrze w przypadku miejsc o niskim i średnim natężeniu ruchu z mniej niż 100K odsłon / dzień, ale nie jest zalecane dla większych woluminów. Jest również ograniczona do jednego komputera, więc nie może być używany w żadnym scenariuszu wieloserwerowym, takim jak równoważenie obciążenia i replikacja geograficzna. Aby uzyskać informacje na temat obsługi innych baz danych przez Django, zobacz [Konfiguracja bazy danych](https://docs.djangoproject.com/en/2.0/intro/tutorial02/#database-setup). Można również użyć [narzędzia Azure SDK dla języka Python](/azure/python/) do pracy z usługami magazynu platformy Azure, takich jak tabele i obiekty blob.

- Konfigurowanie potoku ciągłej integracji/ciągłego wdrażania w usłudze takiej jak Azure DevOps. Oprócz pracy z kontrolą źródła (za pośrednictwem usługi Azure Repos lub GitHub lub w innym miejscu), można skonfigurować projekt DevOps platformy Azure tak, aby automatycznie uruchamiał testy jednostkowe jako warunek wstępny wydania, a także skonfigurował potok do wdrożenia na serwerze przejściowym dodatkowe testy przed wdrożeniem w produkcji. Ponadto usługa Azure DevOps integruje się z rozwiązaniami do monitorowania, takimi jak usługa App Insights, i zamyka cały cykl za pomocą narzędzi do elastycznego planowania. Aby uzyskać więcej informacji, zobacz [Tworzenie potoku ciągłej integracji/ciągłego wdrażania dla języka Python za pomocą projektu Azure DevOps,](/azure/devops-project/azure-devops-project-python?view=vsts) a także ogólnej [dokumentacji programu Azure DevOps.](/azure/devops/?view=vsts)

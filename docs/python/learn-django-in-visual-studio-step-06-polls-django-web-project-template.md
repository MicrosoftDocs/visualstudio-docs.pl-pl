---
title: Poznaj samouczek Django w Visual Studio w kroku 6, szablon projektu sond
titleSuffix: ''
description: Przewodnik po podstawy Django w kontekście projektów programu Visual Studio, w szczególności funkcje szablonu projektu sieci Web Django sond, takich jak administracyjne dostosowywania.
ms.date: 11/19/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: ecc0637495b484ae06cb0f18e45ba329c7fa3407
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062499"
---
# <a name="step-6-use-the-polls-django-web-project-template"></a>Krok 6: Należy użyć szablonu projektu sieci Web Django sond

**Poprzedni krok: [uwierzytelniać użytkowników w Django](learn-django-in-visual-studio-step-05-django-authentication.md)**

Po zrozumieniu szablon "Projekt sieci Web Django" Visual Studio teraz zapoznanie się z trzeciego szablonu Django "Sond Django projektu sieci Web", która opiera się na tej samej bazy kodu i pokazuje pracy z bazą danych.

W tym kroku dowiesz się, jak:

> [!div class="checklist"]
> - Tworzenie projektu z szablonu i zainicjować bazy danych (krok 6 - 1)
> - Zrozumienie modeli danych (krok 6-2)
> - Zastosuj migracji (krok 6-3)
> - Widoki i szablony strony utworzone przez szablon projektu (krok 6-4)
> - Utwórz interfejs administracyjny niestandardowych (krok 5 z 6)

Projekt, który został utworzony za pomocą tego szablonu jest podobny do co można uzyskać, wykonując [pisania pierwszej aplikacji Django](https://docs.djangoproject.com/en/2.0/intro/tutorial01/) samouczek w witrynie docs Django. Aplikacja sieci web składa się z publicznej witryny, umożliwiający użytkownikom wyświetlanie ankiety i oddawać głosy, wraz z niestandardowego interfejsu administracyjnego za pomocą którego można zarządzać ankiety. Używa tego samego systemu uwierzytelniania jako szablon "Projekt sieci Web Django" i sprawia, że więcej, użyj bazy danych, wdrażając modele Django jako zbadany w poniższych sekcjach.

## <a name="step-6-1-create-the-project-and-initialize-the-database"></a>Krok 1 z 6: Tworzenie projektu i zainicjować bazy danych

1. W programie Visual Studio, przejdź do **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **LearningDjango** rozwiązanie utworzone we wcześniejszej części tego samouczka, a następnie wybierz pozycję **Dodaj**  >   **Nowy projekt**. (, Jeśli chcesz użyć nowego rozwiązania, wybierz **pliku** > **New** > **projektu** zamiast.)

1. W oknie dialogowym Nowy projekt wyszukiwanie i wybieranie **projektu sieci Web Django sond** szablonu, wywołaj projektu "DjangoPolls", a następnie wybierz pozycję **OK**.

1. Podobnie jak inne szablony projektów w programie Visual Studio zawiera szablon "Projekt sieci Web Django sond" *requirements.txt* pliku monitów w programie Visual Studio pyta, gdzie zainstalować te zależności. Wybierz opcję, **zainstalować w środowisku wirtualnym**, a następnie w **Dodawanie środowiska wirtualnego** okna dialogowego wybierz **Utwórz** aby zaakceptować wartości domyślne.

1. Gdy Python zakończy się skonfigurowanie środowiska wirtualnego, postępuj zgodnie z instrukcjami wyświetlonych *readme.html* do inicjowania bazy danych i utworzyć Django użytkownika administratora (administrator). Kroki są najpierw kliknij prawym przyciskiem myszy **DjangoPolls** projektu w **Eksploratora rozwiązań**, wybierz opcję **Python** > **Django migracji** ponownie, wybierz polecenie, a następnie kliknij prawym przyciskiem myszy projekt **Python** > **Django — Tworzenie administratora** poleceń i postępuj zgodnie z monitami. (Jeśli zostanie podjęta próba najpierw utworzyć użytkownika nadrzędnego, zobaczysz błąd, ponieważ baza danych nie została zainicjowana.)

1. Ustaw **DjangoPolls** projektu jako domyślny dla rozwiązania Visual Studio przez kliknięcie prawym przyciskiem myszy tego projektu w **Eksploratora rozwiązań** i wybierając polecenie **Ustaw jako projekt startowy**. Projekt startowy, który jest pokazany w pogrubienie, to co program jest uruchamiany w przypadku, gdy uruchamiasz debuger.

1. Wybierz **debugowania** > **Rozpocznij debugowanie** (**F5**) lub użyj **serwera sieci Web** przycisk na pasku narzędzi, aby uruchomić serwer:

    ![Uruchamianie serwera sieci web przycisku paska narzędzi w programie Visual Studio](media/django/run-web-server-toolbar-button.png)

1. Aplikacja utworzona przez szablon ma trzy strony Strona główna o i skontaktuj się z pomocą, której możesz przechodzić między za pomocą paska nawigacji górnej. Zająć minutę lub dwie zbadać różne części aplikacji (informacje i skontaktuj się z strony są bardzo podobne do "Projekt sieci Web Django" i nie są omówione w dalszych).

    ![Widok pełnej przeglądarki aplikacji projektu sieci Web Django sond](media/django/step06-full-app-view.png)

1. Również wybrać **administracji** łączy na pasku nawigacyjnym, która wyświetla ekran logowania, aby zademonstrować, że interfejs administracyjny jest uprawnienia tylko do uwierzytelnienia administratorów. Użyj poświadczeń administratora i są kierowane do "/ admin" strony, która jest domyślnie włączona, korzystając z tego szablonu projektu.

    ![Administracyjne widok aplikacji projektu sieci Web Django sond](media/django/step06-polls-administrative-interface.png)

1. Możesz pozostawić aplikacja uruchomiona w kolejnych sekcjach.

    Jeśli chcesz zatrzymać aplikację i [Zatwierdź zmiany do kontroli źródła](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control), najpierw otwórz **zmiany** strony w **Team Explorer**, kliknij prawym przyciskiem myszy folder (środowiska wirtualnego prawdopodobnie **env**) i wybierz **ignorować te elementy lokalne**.

### <a name="examine-the-project-contents"></a>Sprawdź zawartość projektu

Wspomniane wcześniej. Większość co to jest projekt utworzony z szablonu "Projekt sieci Web Django sond" należy się zapoznać, jeśli zostały przedstawione z szablonów projektów w programie Visual Studio. Dodatkowe kroki w tym artykule podsumowanie bardziej znaczące zmiany i uzupełnienia, a mianowicie modeli danych i dodatkowe widoki.

### <a name="question-what-does-the-django-migrate-command-do"></a>Pytanie: do czego służy polecenie Django migracji?

Odpowiedź: **migracji Django** polecenia specjalnie `manage.py migrate` polecenia, które uruchamia wszystkie skrypty w *aplikacji/migrations* folder, który jeszcze nie zostały wcześniej uruchomione. W takim przypadku polecenie jest uruchamiane *0001_initial.py* skryptu w tym folderze, aby skonfigurować wymagane schematu w bazie danych.

Sam skrypt migracji jest tworzony przez `manage.py makemigrations` polecenia, które skanuje aplikacji *models.py* pliku, porównuje go do bieżącego stanu bazy danych, a następnie generuje wymaganymi skryptami migrować schemat bazy danych do Dopasowuje bieżący modeli. Ta funkcja Django są ogromne jako aktualizacji i modyfikowania modeli wraz z upływem czasu. Generowanie i uruchamianie migracji, należy dysponować modele i bazę danych zsynchronizowany z niewielkim nakładem pracy.

Możesz pracować z funkcją migracji w kroku 6-3 w dalszej części tego artykułu.

## <a name="step-6-2-understand-data-models"></a>Krok 2 z 6: zrozumienie modeli danych

Modele dla aplikacji o nazwie sondowania i wybór, są definiowane w *app/models.py*. Każdy z nich jest klasą języka Python, która pochodzi od klasy `django.db.models.Model` i używa metody `models` klasy takie jak `CharField` i `IntegerField` do zdefiniowania pola w modelu i mapowania kolumny bazy danych.

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

Jak widać, Sondowaniu przechowuje opis w jego `text` pola i publikacji Data w `pub_date`. Te pola są jedynymi osobami, które istnieją dla sondowania w bazie danych. `total_votes` pola jest obliczane w czasie wykonywania.

Wybór jest powiązany z sondowania za pośrednictwem `poll` pola, zawiera opis w `text`i przechowuje licznik tego wyboru tych elementów w `votes`. `votes_percentage` Pola jest obliczane w czasie wykonywania i nie znajduje się w bazie danych.

Pełna lista typów pól jest `CharField` (ograniczoną tekstu) `TextField` (nieograniczona liczba tekst), `EmailField`, `URLField`, `DateTimeField`, `IntegerField`, `DecimalField`, `BooleanField`, `ForeignKey`, i `ManyToMany`. Każde pole ma niektórych atrybutów, takich jak `max_length`. `blank=True` Atrybut oznacza, że pole jest opcjonalne; `null=true` oznacza, że wartość jest opcjonalna. Istnieje również `choices` atrybut, który ogranicza wartości do wartości w tablicy krotki wartości wartość/wyświetlania danych. (Zobacz [modelu odwołania do pól](https://docs.djangoproject.com/en/2.0/ref/models/fields/) w dokumentacji Django.)

Możesz potwierdzić dokładnie co to jest przechowywany w bazie danych, sprawdzając *db.sqlite3* pliku w projekcie przy użyciu narzędzia, takiego jak [przeglądarki SQLite](https://sqlitebrowser.org/). W bazie danych, zobaczysz, że pola klucza obcego, takich jak `poll` w wyborze modelu są przechowywane jako `poll_id`; Django obsługuje mapowanie automatycznie.

Ogólnie rzecz biorąc pracy z bazą danych w Django oznacza, że działa wyłącznie w ramach modeli tak, aby zarządzać Django podstawowej bazy danych w Twoim imieniu.

### <a name="seed-the-database-from-samplesjson"></a>Inicjowanie bazy danych z samples.json

Początkowo baza danych zawiera nie ankiety. Można użyć interfejsu administracyjnego w "/ admin" adres URL, aby dodać sonduje ręcznie, a możesz również odwiedzić stronę "/ materiału siewnego" w witrynie uruchomiona, można dodać inicjatora bazy danych z sond zdefiniowanych w aplikacji *samples.json* pliku.

Projekt Django *urls.py* ma dodano wzorzec adresu URL, `url(r'^seed$', app.views.seed, name='seed'),`. `seed` Wyświetlać w *app/views.py* ładuje *samples.json* pliku i tworzy obiekty niezbędne modelu. Django automatycznie utworzy pasujące rekordy w bazie danych.

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

Aby zobaczyć efekt, uruchom aplikację, aby dowiedzieć się, że nie ankiety, ale istnieje. Następnie skorzystaj z adresu URL "/ materiału siewnego", a zwrócona do strony głównej aplikacji powinien zostać wyświetlony, sond, są dostępne. Ponownie, możesz sprawdzić nieprzetworzonych *db.sqlite3* pliku przy użyciu narzędzia, takiego jak [przeglądarki SQLite](https://sqlitebrowser.org/).

![Aplikacja projektu sieci Web Django ankiety z wypełnionych bazy danych](media/django/step06-app-with-seeded-database.png)

### <a name="question-is-it-possible-to-initialize-the-database-using-the-django-administrative-utility"></a>Pytanie: Czy można zainicjować bazy danych wykorzystuje narzędzia administracyjnego Django?

Odpowiedź: Tak, możesz użyć [polecenia loaddata administracyjnego django](https://docs.djangoproject.com/en/1.9/ref/django-admin/#loaddata) do wykonania tych samych zadań rozmieszczania strony w aplikacji. Podczas pracy w aplikacji sieci web pełną, można użyć z kombinacją dwóch metod: Zainicjuj bazę danych z poziomu wiersza polecenia, a następnie przekonwertować na stronie inicjatora do interfejsu API, do którego można wysyłać żadnych dowolnego JSON, a nie jednostki uzależnionej w pliku zakodowane.

## <a name="step-6-3-use-migrations"></a>Krok 3 z 6: użyć migracje

Po uruchomieniu `manage.py makemigrations` polecenia (przy użyciu menu kontekstowego w programie Visual Studio) po utworzeniu projektu, Django utworzyła plik *app/migrations/0001_initial.py* pliku. Ten plik zawiera skrypt, który tworzy tabele początkowej bazy danych.

Ponieważ natychmiastową wprowadzisz zmiany do Twoich modeli wraz z upływem czasu, Django ułatwia podstawowy schemat bazy danych na bieżąco z tych modeli. Ogólny przepływ pracy jest w następujący sposób:

1. Wprowadź zmiany do modeli w swojej *models.py* pliku.
1. W programie Visual Studio, kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierz **Python** > **migracji należy Django** polecenia. Jak opisano wcześniej, to polecenie spowoduje wygenerowanie skryptów w *aplikacji/migrations* przeprowadzić migrację bazy danych z jego bieżącym stanie Nowy stan.
1. Aby zastosować skryptów do rzeczywistej bazy danych, ponownie kliknij prawym przyciskiem myszy projekt i wybierz **Python** > **migracji Django**.

Django śledzi migracji, które zostały zastosowane do dowolnej danej bazy danych tak, aby podczas uruchamiania polecenia migracji ma zastosowanie Django, niezależnie od migracji są potrzebne. Jeśli tworzysz nową, pustą bazę danych, na przykład uruchomienie polecenia migracji udostępnia ją na bieżąco ze swoimi modelami bieżącej, stosując każdego skryptu migracji. Podobnie jeśli wprowadzasz wiele zmian w modelu i generowanie migracje na komputerze deweloperskim, można użyć migracje zbiorczą do produkcyjnej bazy danych, uruchamiając polecenie migracji na serwerze produkcyjnym. Django ponownie dotyczy tylko tych skryptów migracji, które zostały wygenerowane od czasu ostatniego migracja produkcyjnej bazy danych.

Aby zobaczyć efekt zmiany modelu, spróbuj wykonać następujące kroki:

1. Dodaj pole opcjonalne author do modelu sondowania w *app/models.py* , dodając następujący wiersz po `pub_date` pola, aby dodać opcjonalny `author` pola:

    ```python
    author = models.CharField(max_length=100, blank=True)
    ```

1. Zapisz plik, a następnie kliknij prawym przyciskiem myszy **DjangoPolls** projektu w **Eksploratora rozwiązań** i wybierz **Python** > **migracji należy Django**  polecenia.
1. Wybierz **projektu** > **Pokaż wszystkie pliki** polecenie, aby wyświetlić nowo wygenerowane skryptu w **migracje** folder, którego nazwa zaczyna się od  **002_auto_**. Kliknij prawym przyciskiem myszy, plik, a następnie zaznacz **załącz do projektu**. Następnie możesz wybrać **projektu** > **Pokaż wszystkie pliki** ponownie, aby przywrócić oryginalnego widoku. (W tym kroku, zobacz drugie pytanie poniżej, aby uzyskać szczegółowe informacje).
1. Jeśli to konieczne, należy otworzyć ten plik, aby sprawdzić, jak Django skrypty zmian z poprzedniego stanu modelu do nowego stanu.
1. Ponownie kliknij prawym przyciskiem myszy projekt programu Visual Studio i wybierz **Python** > **migracji Django** Aby zastosować zmiany do bazy danych.
1. Jeśli to konieczne, można otworzyć bazy danych w odpowiedniej podglądu, aby potwierdzić zmianę.

Ogólne Django w funkcji migracji oznacza, że użytkownik należy nigdy nie zarządzać schemat bazy danych ręcznie. Wystarczy wprowadzić zmiany do Twoich modeli, generowania skryptów migracji i zastosowanie ich przy użyciu polecenia migracji.

### <a name="question-what-happens-if-i-forget-to-run-the-migrate-command-after-making-changes-to-models"></a>Pytanie: Co się stanie, jeśli zapomnę wykonywanie polecenia migracji po wprowadzeniu zmian do modeli?

Odpowiedź: Jeśli modele nie są zgodne, co znajduje się w bazie danych, Django zakończy się niepowodzeniem w czasie wykonywania za pomocą odpowiednich wyjątków. Na przykład, Jeśli zapomnisz do migrowania zmiana modelu pokazano w poprzedniej sekcji, zostanie wyświetlony błąd **takich kolumn: app_poll.author**:

![Błąd pokazany, gdy zmiana modelu ma nie została poddana migracji](media/django/step06-exception-when-forgetting-to-migrate.png).

### <a name="question-why-doesnt-solution-explorer-show-newly-generated-scripts-after-running-django-make-migrations"></a>Pytanie: Dlaczego nie skrypty show nowo wygenerowane Eksplorator rozwiązań po zakończeniu migracji należy Django?

Odpowiedź: Mimo że nowo wygenerowanych skryptów istnieje w *aplikacji/migrations* folder i są stosowane podczas uruchamiania **migracji Django** polecenia, nie pojawiają się automatycznie w **rozwiązania Eksplorator** , ponieważ nie zostały one dodane do projektu programu Visual Studio. Aby stały się widoczne, najpierw wybierz **projektu** > **Pokaż wszystkie pliki** polecenie menu lub przycisku paska narzędzi, przedstawione na poniższej ilustracji. To polecenie powoduje **Eksploratora rozwiązań** Aby wyświetlić wszystkie pliki w folderze projektu dla elementów, które nie zostały dodane do poziomu projektu za pomocą ikony konspektu notacji. Kliknij prawym przyciskiem myszy pliki, które chcesz dodać, a następnie wybierz pozycję **załącz do projektu**, który zawiera również je w kontroli źródła z następnym zatwierdzeniu.

![Objęte polecenia Projekt w Eksploratorze rozwiązań](media/django/step06-include-migrations-script-in-project.png)

### <a name="question-can-i-see-what-migrations-would-be-applied-before-running-the-migrate-command"></a>Pytanie: Czy można wyświetlić migracji, które mają zostać zastosowane przed uruchomieniem polecenia migracji?

Odpowiedź: Tak, użyj [polecenia showmigrations administracyjnego django](https://docs.djangoproject.com/en/2.0/ref/django-admin/#showmigrations).

## <a name="step-6-4-understand-the-views-and-page-templates-created-by-the-project-template"></a>Krok 6-4: Omówienie widoków i stron szablony utworzone przez szablon projektu

Większość widoków generowane przez szablon "Projekt sieci Web Django sond", takie jak widoki informacje i skontaktuj się z stron, są bardzo podobne do widoków tworzone przez szablon "Projekt sieci Web Django" doświadczenie w pracy z wcześniej w tym samouczku. Co to są inne w przypadku sond, aplikacja jest, że jego strony głównej korzysta z modeli, jak wiele dodaje strony do głosowania i wyświetlania wyników ankiety.

Na początek z pierwszego wiersza w projekcie Django `urlpatterns` tablicy w *urls.py* plik jest więcej niż tylko prosty routing do widoku aplikacji. Zamiast tego ściąga własnych aplikacji *urls.py* pliku:

```python
from django.conf.urls import url, include
import app.views

urlpatterns = [
    url(r'^', include('app.urls', namespace="app")),
    # ..
]
```

*App/urls.py* następnie zawierający bardziej interesujące kodu routingu (komentarze wyjaśniające, dodane):

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

Jeśli nie jesteś zaznajomiony z bardziej złożonych wyrażeń regularnych, w tym miejscu użyć, możesz wkleić wyrażenia w [regex101.com](https://regex101.com/) objaśnienia dotyczące przy użyciu prostego języka. (Należy jako znak ucieczki ukośnika `/` , dodając ukośnika, `\` przed nimi; anulowania zapewnianego element nie jest konieczne w języku Python z powodu `r` prefiks ciągu, co oznacza "pierwotne").

W Django, składnia `?P<name>pattern` tworzy grupę o nazwie `name`, która pobiera przekazywane jako argumenty do widoków w kolejności, są wyświetlane. W kodzie, przedstawionej wcześniej `PollsDetailView` i `PollsResultsView` otrzymywać argument o nazwie `pk` i `app.views.vote` odbiera argument o nazwie `poll_id`.

Możesz też sprawdzić, czy większość widoków nie są po prostu bezpośrednimi odwołaniami do widoku funkcji w *app/views.py*. Zamiast tego większość odnoszą się do klasy, w tym samym pliku, pochodzącą z `django.views.generic.ListView` lub `django.views.generic.DetailView`. Podaj klas bazowych `as_view` metody, które zająć `template_name` argumentu szablon. `ListView` Klasy bazowej, ponieważ używany dla strony głównej oczekuje również `queryset` właściwości zawierającej dane i `context_object_name` właściwość o nazwie zmiennej, według której ma się do danych w szablonie, w tym przypadku `latest_poll_list`.

Teraz można sprawdzić `PollListView` dla strony głównej, która została zdefiniowana w następujący sposób w *app/views.py*:

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

Wszystkie opcje, które ma wykonać w tym miejscu jest zidentyfikowanie model, widok współpracuje z (sondowania), która zastępuje `get_context_data` metody w celu dodania `title` i `year` wartości do kontekstu.

Podstawowy szablon (*templates/app/index.html*) jest w następujący sposób:

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

Najprościej mówiąc, szablon otrzymuje listę obiektów sondowania w `latest_poll_list`, a następnie wykonuje iterację przez tę listę, aby utworzyć wiersza tabeli, która zawiera link do każdego sondowania przy użyciu sondowania `text` wartość. W `{% url %}` tagu "app:detail" odnosi się do wzorca adresu url w *app/urls.py* o nazwie "szczegóły", przy użyciu `poll.id` jako argument. To powoduje czy Django tworzy adres URL przy użyciu odpowiednich wzorca i użyty dla tego połączenia. Ten bit sprawdzające przyszłość oznacza, że, można zmienić ten wzorzec adresu URL w każdej chwili łącza wygenerowany automatycznie zaktualizować do dopasowania.

`PollDetailView` i `PollResultsView` klas w *app/views.py* (nie pokazane tutaj) Szukaj prawie identyczne `PollListView` z tą różnicą, że pochodzą one od `DetailView` zamiast tego. Ich odpowiednich szablonów, *app/templates/details.html* i *app/templates/results.html* umieścić odpowiednie pola z modeli w ramach różnych kontrolek HTML. Jeden unikatowy zestaw w *details.html* jest, że opcje dla sondowania, znajdują się w formularz HTML, który po przesłaniu jest POST na adres URL /vote. Jak pokazano wcześniej, że wzorzec adresu URL jest kierowany do `app.views.vote`, która jest zaimplementowana w następujący sposób (Uwaga `poll_id` argumentu, który jest ponownie nazwanej grupy w wyrażeniu regularnym, używane w routingu dla tego widoku):

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

W tym miejscu widoku nie ma swój własny odpowiedniego szablonu, takie jak innych stron. Zamiast tego weryfikuje wybrane sondowania, przedstawiający 404, jeśli sondowania nie istnieje (tylko w przypadku, gdy ktoś wpisze adres URL np. "głos/1a2b3c"). Następnie daje to pewność, że wybór oddanym głosem jest prawidłowy dla sondowania. Jeśli nie, `except` blok po prostu renderuje stronę szczegółów, ponownie komunikatu o błędzie. Jeśli wybrany jest prawidłowy, widok zlicza głosu i wykonuje przekierowanie do strony wyników.

## <a name="step-6-5-create-a-custom-administration-interface"></a>Krok 5 z 6: Utworzenie interfejsu niestandardowego administracji

Ostatnie elementy szablonu "Projekt sieci Web Django sond" są niestandardowych rozszerzeń domyślne Django interfejs administracyjny, jak pokazano wcześniej w tym artykule w kroku 6-1. Udostępnia domyślny interfejs dla użytkowników i grupy zarządzania, ale nic więcej. Szablon projektu sond dodaje funkcje, które umożliwiają zarządzanie także ankiety.

Po pierwsze, adres URL wzorców w projekcie Django *urls.py* ma `url(r'^admin/', include(admin.site.urls)),` Domyślnie; wzorzec "admin/doc" również jest uwzględniony, ale oznaczone jako komentarz.

Ta aplikacja zawiera następnie plik *admin.py*, Django uruchamiane automatycznie, gdy użytkownik odwiedza interfejs administracyjny dzięki gotowej do włączenia `django.contrib.admin` w `INSTALLED_APPS` tablicę *settings.py*. Kod w tym pliku, dostarczone przez szablon projektu jest następujący:

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

Jak widać, `PollAdmin` klasa pochodzi od `django.contrib.admin.ModelAdmin` i dostosowuje liczbę jej pola przy użyciu nazwy z `Poll` modelu, który zarządza. Te pola są opisane na [opcje ModelAdmin](https://docs.djangoproject.com/en/2.0/ref/contrib/admin/#modeladmin-options) w dokumentacji Django.

Wywołanie `admin.site.register` tej klasy łączy się następnie z modelu (`Poll`) i dołączenia go na interfejs administracyjny. Poniżej przedstawiono ogólny wynik:

![Administracyjne widok aplikacji projektu sieci Web Django sond](media/django/step06-polls-administrative-interface.png)

## <a name="next-steps"></a>Następne kroki

> [!Note]
> Jeśli do kontroli źródła w toku w tym samouczku został zostały zatwierdzanie rozwiązania programu Visual Studio, teraz jest dobry moment, aby wykonać inną zatwierdzenia. Rozwiązanie powinno pasuje do kodu źródłowego samouczek, w witrynie GitHub: [Microsoft/python — przykładowe vs uczenia — django](https://github.com/Microsoft/python-sample-vs-learning-django).

Teraz zostały zbadane całości "Pusty projekt sieci Web Django", "Projekt sieci Web Django" i "Projekt sieci Web Django sond" szablonów w programie Visual Studio. Wyjaśniono podstawy Django, takie jak korzystanie z widoków i szablonów, a następnie zostały przedstawione routingu, uwierzytelniania i używania modeli bazy danych. Teraz można utworzyć własną aplikację internetową z wszystkie widoki i modele, które są potrzebne.

Uruchamianie aplikacji sieci web na komputerze deweloperskim jest tylko jeden krok w zakresie udostępniania aplikacji dla klientów. Kolejne kroki mogą obejmować następujące zadania:

- Wdrażanie aplikacji sieci web na serwerze produkcyjnym, takich jak usługa Azure App Service. Zobacz [publikowanie w usłudze Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md).

- Dostosowywanie strony 404, tworząc szablon o nazwie *templates/404.html*. Jeśli jest obecny, ten szablon jest używany w Django zamiast domyślnej, jeden. Aby uzyskać więcej informacji, zobacz [widoków błąd](https://docs.djangoproject.com/en/2.0/ref/views/#error-views) w dokumentacji Django.

- Pisanie testów jednostkowych *tests.py*; szablony projektu Visual Studio stanowią punkt wyjścia dla tych i więcej informacji znajduje się na [pisania pierwszej aplikacji Django, część 5 — testowanie](https://docs.djangoproject.com/en/2.0/intro/tutorial05/) i [Testowania w Django](https://docs.djangoproject.com/en/2.0/topics/testing/) w dokumentacji Django.

- Należy zmodyfikować aplikację tak, z bazy danych SQLite w magazynie danych na poziomie produkcyjnym, takich jak PostgreSQL, MySQL i SQL Server (które mogą być hostowane na platformie Azure). Zgodnie z opisem na [kiedy należy używać bazy danych SQLite](https://www.sqlite.org/whentouse.html) (sqlite.org) działa prawidłowo dla witryn o średnim ruchu z mniej niż 100 tysięcy trafień/dzień działania niskiej SQLite, ale nie jest zalecany do większej ilości. Jest także ograniczona do jednego komputera, więc nie można używać w każdym scenariuszu wielu serwerów, takich jak Równoważenie obciążenia i replikację geograficzną. Aby uzyskać informacje na temat obsługi Django w innych bazach danych, zobacz [Konfiguracja bazy danych](https://docs.djangoproject.com/en/2.0/intro/tutorial02/#database-setup). Można również użyć [zestawu Azure SDK dla języka Python](azure-sdk-for-python.md) do pracy z usług Azure storage, takich jak tabele i obiektów blob.

- Konfigurowanie potoku ciągłej integracji/ciągłego wdrażania usługi, takie jak DevOps platformy Azure. Oprócz Praca z kontrolą źródła (przy użyciu Azure repozytoriów GitHub i/lub gdzie indziej), można skonfigurować projekt DevOps platformy Azure do automatycznego uruchamiania testów jednostkowych jako warunek wstępny dla wersji i także skonfigurować potok do wdrażania na serwerze tymczasowym dla dodatkowe testy przed wdrożeniem w środowisku produkcyjnym. Azure DevOps, ponadto integruje się z usługą monitorowania rozwiązań, takich jak usługi App Insights i zamknięcie całego cyklu za pomocą narzędzi planowania agile. Aby uzyskać więcej informacji, zobacz [utworzyć potok ciągłej integracji/ciągłego Dostarczania dla języka Python za pomocą projektu DevOps platformy Azure](/azure/devops-project/azure-devops-project-python?view=vsts) i również ogólne [dokumentacji usługi Azure DevOps](/azure/devops/?view=vsts).

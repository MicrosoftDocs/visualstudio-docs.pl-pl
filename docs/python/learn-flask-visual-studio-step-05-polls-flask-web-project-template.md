---
title: Samouczek do uczenia o kolbie w programie Visual Studio krok 5, szablon projektu sondowania
titleSuffix: ''
description: Wskazówki dotyczące kolb w kontekście projektów programu Visual Studio, w tym w odniesieniu do funkcji projektu sieci Web kolby sondowania i sondowania/Jade szablonu projektu sieci Web.
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
monikerRange: vs-2017
ms.workload:
- python
- data-science
ms.openlocfilehash: fd67e527ccf62de17dc15a5415f573c9622a51e9
ms.sourcegitcommit: f1dff6c4532c43b0444aa12ea57e90bb7dba6fba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805981"
---
# <a name="step-5-use-the-polls-flask-web-project-template"></a>Krok 5. użycie szablonu projektu sieci Web w kolbie sond

**Poprzedni krok: [Użyj szablonu projektu sieci Web pełnej kolby](learn-flask-visual-studio-step-04-full-flask-project-template.md)**

Po zrozumieniu szablonu "projekt sieci Web" w programie Visual Studio można teraz przyjrzeć się szablonowi trzeciej kolbie "projekt sieci Web" sondy, który jest oparty na tej samej bazie kodu.

W tym kroku dowiesz się, jak:

> [!div class="checklist"]
> - Utwórz projekt na podstawie szablonu i zainicjuj bazę danych (krok 5-1)
> - Zrozumienie modeli danych (krok 5-2)
> - Zrozumienie magazynów danych zapasowych (krok 5-3)
> - Omówienie widoków szczegółów i wyników sondowania (krok 5-4)

Program Visual Studio udostępnia również szablon "sondy/projekt sieci Web Jade", który tworzy identyczną aplikację, ale używa rozszerzenia Jade dla aparatu jinja tworzenia szablonów. Aby uzyskać szczegółowe informacje, zobacz [krok 4 — szablon projektu sieci Web w kolbie/Jade](learn-flask-visual-studio-step-04-full-flask-project-template.md#the-flaskjade-web-project-template).

## <a name="step-5-1-create-the-project"></a>Krok 5-1: Tworzenie projektu

1. W programie Visual Studio przejdź do **Eksplorator rozwiązań**, kliknij prawym przyciskiem myszy rozwiązanie **LearningFlask** utworzone wcześniej w tym samouczku, a następnie wybierz pozycję **Dodaj**  >  **Nowy projekt**. (Alternatywnie, jeśli chcesz użyć nowego rozwiązania, wybierz pozycję **plik**  >  **Nowe**  >  W zamian **projekt** ).

1. W oknie dialogowym Nowy projekt Wyszukaj i wybierz szablon **projektu sieci Web dla kolby sondy** , wywołaj projekt "FlaskPolls" i wybierz **przycisk OK**.

1. Podobnie jak w przypadku innych szablonów projektu w programie Visual Studio, szablon "projekt sieci Web" sondy "zawiera plik *requirements.txt* , Visual Studio pyta, gdzie zainstalować te zależności. Wybierz opcję, **Zainstaluj w środowisku wirtualnym**, a następnie w oknie dialogowym **Dodawanie środowiska wirtualnego** wybierz pozycję **Utwórz** , aby zaakceptować ustawienia domyślne. (Ten szablon wymaga odpowiedniej kolby, a także pakietów Azure-Storage i pymongo). projekt sieci Web "sondy/Jade", a także wymaga pyjade.

1. Ustaw projekt **FlaskPolls** jako domyślny dla rozwiązania Visual Studio, klikając prawym przyciskiem myszy ten projekt w **Eksplorator rozwiązań** i wybierając pozycję **Ustaw jako projekt startowy**. Projekt startowy, który jest wyświetlany pogrubiony, jest uruchamiany po uruchomieniu debugera.

1. Wybierz pozycję **Debuguj**  >  **Rozpocznij debugowanie** (**F5**) lub użyj przycisku **serwer sieci Web** na pasku narzędzi, aby uruchomić serwer:

    ![Przycisk paska narzędzi uruchamiania serwera sieci Web w programie Visual Studio](media/django/run-web-server-toolbar-button.png)

1. Aplikacja utworzona przez szablon ma trzy strony, Strona główna, informacje i kontakt, które są przechodzenie między górnym paskiem nawigacyjnym. Poświęć minutę lub dwie, aby przeanalizować różne części aplikacji (strony informacje i kontakty są bardzo podobne do "projektu kolby internetowej" i nie są jeszcze omówione w dalszej części).

    ![Pełny widok aplikacji internetowej projektu sieci Web](media/flask/step06-full-app-view.png)

1. Na stronie głównej przycisk **Utwórz przykładowe sondy** inicjuje magazyn danych aplikacji z trzema różnymi sondowami opisanymi w artykule *modele/samples.jsna* stronie. Domyślnie aplikacja używa bazy danych w pamięci (jak pokazano na stronie informacje), która jest resetowana za każdym razem, gdy aplikacja zostanie uruchomiona ponownie. Aplikacja zawiera również kod do pracy z usługą Azure Storage i Mongo DB, zgodnie z opisem w dalszej części tego artykułu.

1. Po zainicjowaniu magazynu danych można głosować w różnych sondach, jak pokazano na stronie głównej (pasek nawigacyjny i stopka są pomijane dla zwięzłości):

    ![Widok aplikacji sondy po zainicjowaniu magazynu danych](media/flask/step06-polls-initialized.png)

1. Wybranie sondy powoduje wyświetlenie określonych opcji:

    ![Interfejs głosowania dla sondy](media/flask/step06-polls-voting-interface.png)

1. Po głosowaniu aplikacja wyświetli stronę wyników i umożliwi ponowne zagłosowanie:

    ![widok wyników po głosowaniu](media/flask/step06-polls-results.png)

1. Możesz pozostawić aplikację działającą dla następujących sekcji.

    Jeśli chcesz zatrzymać aplikację i [zatwierdzić zmiany w kontroli źródła](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control), najpierw Otwórz stronę **zmiany** w **Team Explorer**, kliknij prawym przyciskiem myszy folder dla środowiska wirtualnego (prawdopodobnie **ENV**), a następnie wybierz polecenie **Ignoruj te elementy lokalne**.

### <a name="examine-the-project-contents"></a>Sprawdzanie zawartości projektu

Jak wspomniano wcześniej. Większość elementów projektu utworzonych na podstawie szablonu "projekt sieci Web przestawek sond" (oraz szablon "Jade sond/projekt sieci Web") powinien znać, czy zostały zbadane inne szablony projektu w programie Visual Studio. Dodatkowe kroki opisane w tym artykule podsumowują bardziej znaczące zmiany i dodatki, czyli modele danych i dodatkowe widoki.

## <a name="step-5-2-understand-the-data-models"></a>Krok 5-2: zrozumienie modeli danych

Modele danych dla aplikacji to klasy języka Python o nazwach sondowania i wyboru, które są zdefiniowane w *modelach/ \_ \_ init \_ \_ . PR*. Ankieta reprezentuje pytanie, dla którego kolekcja wystąpień wyboru reprezentuje dostępne odpowiedzi. Sonda utrzymuje również łączną liczbę głosów (dla dowolnej opcji) i metodę obliczania statystyk, które są używane do generowania widoków:

```python
class Poll(object):
    """A poll object for use in the application views and repository."""
    def __init__(self, key=u'', text=u''):
        """Initializes the poll."""
        self.key = key
        self.text = text
        self.choices = []
        self.total_votes = None

    def calculate_stats(self):
        """Calculates some statistics for use in the application views."""
        total = 0
        for choice in self.choices:
            total += choice.votes
        for choice in self.choices:
            choice.votes_percentage = choice.votes / float(total) * 100 \
                if total > 0 else 0
        self.total_votes = total

class Choice(object):
    """A poll choice object for use in the application views and repository."""
    def __init__(self, key=u'', text=u'', votes=0):
        """Initializes the poll choice."""
        self.key = key
        self.text = text
        self.votes = votes
        self.votes_percentage = None
```

Te modele danych są ogólnymi abstrakcyjnymi, które pozwalają widokom aplikacji korzystać z różnych typów magazynów danych zapasowych, które są opisane w następnym kroku.

## <a name="step-5-3-understand-the-backing-data-stores"></a>Krok 5-3: Omówienie magazynów danych zapasowych

Aplikacja utworzona przez szablon "projekt sieci Web" z przestawem sondy "może być uruchamiana w odniesieniu do magazynu danych w pamięci, w usłudze Azure Table Storage lub w bazie danych Mongo DB.

Mechanizm magazynowania danych działa w następujący sposób:

1. Typ repozytorium jest określany za pomocą `REPOSITORY_NAME` zmiennej środowiskowej, która może być ustawiona na wartość "Memory", "azuretablestore" lub "MongoDB". Bit kodu w *Settings.py* Pobiera nazwę przy użyciu "pamięć" jako domyślną. Jeśli chcesz zmienić magazyn zapasowy, musisz ustawić zmienną środowiskową i ponownie uruchomić aplikację.

    ```python
    from os import environ
    REPOSITORY_NAME = environ.get('REPOSITORY_NAME', 'memory')
    ```

1. Kod *Settings.py* inicjuje `REPOSITORY_SETTINGS` obiekt. Jeśli chcesz korzystać z usługi Azure Table Store lub Mondo DB, musisz najpierw zainicjować te magazyny danych w innym miejscu, a następnie ustawić wymagane zmienne środowiskowe, które poinformują aplikację, jak nawiązać połączenie ze sklepem:

    ```python
    if REPOSITORY_NAME == 'azuretablestorage':
        REPOSITORY_SETTINGS = {
            'STORAGE_NAME': environ.get('STORAGE_NAME', ''),
            'STORAGE_KEY': environ.get('STORAGE_KEY', ''),
            'STORAGE_TABLE_POLL': environ.get('STORAGE_TABLE_POLL', 'polls'),
            'STORAGE_TABLE_CHOICE': environ.get('STORAGE_TABLE_CHOICE', 'choices'),
        }
    elif REPOSITORY_NAME == 'mongodb':
        REPOSITORY_SETTINGS = {
            'MONGODB_HOST': environ.get('MONGODB_HOST', None),
            'MONGODB_DATABASE': environ.get('MONGODB_DATABASE', 'polls'),
            'MONGODB_COLLECTION': environ.get('MONGODB_COLLECTION', 'polls'),
        }
    elif REPOSITORY_NAME == 'memory':
        REPOSITORY_SETTINGS = {}
    else:
        raise ValueError('Unknown repository.')
    ```

1. W programie *views.py* aplikacja wywołuje metodę fabryki w celu zainicjowania `Repository` obiektu przy użyciu nazwy i ustawień magazynu danych:

    ```python
    from FlaskPolls.models import PollNotFound
    from FlaskPolls.models.factory import create_repository
    from FlaskPolls.settings import REPOSITORY_NAME, REPOSITORY_SETTINGS

    repository = create_repository(REPOSITORY_NAME, REPOSITORY_SETTINGS)
    ```

1. `factory.create_repository`Metoda znajduje się w *models\factory.py*, która po prostu importuje odpowiedni moduł repozytorium, a następnie tworzy `Repository` wystąpienie:

    ```python
    def create_repository(name, settings):
        """Creates a repository from its name and settings. The settings
        is a dictionary where the keys are different for every type of repository.
        See each repository for details on the required settings."""
        if name == 'azuretablestorage':
            from .azuretablestorage import Repository
        elif name == 'mongodb':
            from .mongodb import Repository
        elif name == 'memory':
            from .memory import Repository
        else:
            raise ValueError('Unknown repository.')

        return Repository(settings)
    ```

1. Implementacje `Repository` klasy specyficzne dla każdego magazynu danych można znaleźć w *models\azuretablestorage.py*, *models\mongodb.py* i *models\memory.py*. Implementacja usługi Azure Storage używa pakietu Azure-Storage. Implementacja Mongo DB używa pakietu pymongo. Zgodnie z opisem w kroku 5-1, oba pakiety są zawarte w pliku *requirements.txt* szablonu projektu. Eksplorowanie szczegółów jest pozostawione jako ćwiczenie dla czytnika.

W skrócie, `Repository` Klasa stanowi streszczenie określonych magazynów danych, a aplikacja używa zmiennych środowiskowych w czasie wykonywania, aby wybrać i skonfigurować, które z trzech implementacji mają być używane.

Poniższe kroki umożliwiają dodanie obsługi innego magazynu danych niż trzy udostępnione przez szablon projektu, w razie potrzeby:

1. Skopiuj *Memory.py* do nowego pliku, aby mieć podstawowy interfejs dla `Repository` klasy.
1. Zmodyfikuj implementację klasy jako pasującą do używanego magazynu danych.
1. Zmodyfikuj *Factory.py* , aby dodać inny `elif` przypadek, który rozpoznaje nazwę dodanego magazynu danych i importuje odpowiedni moduł.
1. Zmodyfikuj *Settings.py* , aby rozpoznawał inną nazwę w `REPOSITORY_NAME` zmiennej środowiskowej i odpowiednio ją zainicjuj `REPOSITORY_SETTINGS` .

### <a name="seed-the-data-store-from-samplesjson"></a>Wypełnianie magazynu danych z samples.jsna

Początkowo wybrany magazyn danych nie zawiera żadnych sondowań, więc na stronie głównej aplikacji jest wyświetlany komunikat **Brak dostępnych sondowań** wraz z przyciskiem **Utwórz przykładowe sondy** . Po wybraniu przycisku widok zostanie zmieniony w celu wyświetlenia dostępnych sondowań. Ten przełącznik odbywa się za poorednictwem tagów warunkowych w *templates\index.html* (niektóre puste wiersze pominięte dla zwięzłości):

```html
{% extends "layout.html" %}
{% block content %}
<h2>{{title}}.</h2>

{% if polls %}
<table class="table table-hover">
    <tbody>
        {% for poll in polls %}
        <tr>
            <td>
                <a href="/poll/{{poll.key}}">{{poll.text}}</a>
            </td>
        </tr>
        {% endfor %}
    </tbody>
</table>
{% else %}
<p>No polls available.</p>
<br />
<form action="/seed" method="post">
    <button class="btn btn-primary" type="submit">Create Sample Polls</button>
</form>
{% endif %}
{% endblock %}
```

`polls`Zmienna w szablonie pochodzi od wywołania do `repository.get_polls` , która zwraca wartość Nothing do momentu zainicjowania magazynu danych.

Kliknięcie przycisku **Utwórz przykładowe sondy** powoduje przejście do adresu URL/Seed. Program obsługi dla tej trasy został zdefiniowany w  *views.py*:

```python
@app.route('/seed', methods=['POST'])
def seed():
    """Seeds the database with sample polls."""
    repository.add_sample_polls()
    return redirect('/')
```

Wywołanie `repository.add_sample_polls()` zakończyło się w jednej z określonych `Repository` implementacji dla wybranego magazynu danych. Każda implementacja wywołuje `_load_samples_json` metodę znalezioną w *modelach \_ \_ init \_ \_ . PR* w celu załadowania *models\samples.jsw* pliku do pamięci, a następnie iteruje dane w celu utworzenia niezbędnych `Poll` i `Choice` obiektów w magazynie danych.

Po zakończeniu tego procesu `redirect('/')` instrukcja w `seed` metodzie przechodzi z powrotem do strony głównej. Ponieważ `repository.get_polls` zwraca teraz obiekt danych, znaczniki warunkowe w *templates\index.html* teraz renderuje tabelę zawierającą sondy.

### <a name="question-how-does-one-add-new-polls-to-the-app"></a>Pytanie: jak jeden z nich dodaje nowe sondy do aplikacji?

Odpowiedź: aplikacja określona za pomocą szablonu projektu nie zawiera funkcji do dodawania lub edytowania sondowań. models\samples.jsmożna modyfikować *w* celu tworzenia nowych danych inicjujących, ale spowodowałoby to zresetowanie magazynu danych. Aby zaimplementować funkcje edycji, należy wdrożyć `Repository` interfejs klasy przy użyciu metod, aby utworzyć niezbędne `Choice` i niepotrzebne `Poll` wystąpienia, a następnie zaimplementować interfejs użytkownika na dodatkowych stronach, które używają tych metod.

## <a name="step-5-4-understand-the-poll-detail-and-results-views"></a>Krok 5-4: Omówienie widoków szczegółów i wyników sondowania

Większość widoków wygenerowanych przez szablon "sondy" projektu sieci Web "i" sondy/Jade projektu sieci Web ", takich jak widoki stron informacje i kontakt, są bardzo podobne do widoków utworzonych w ramach" kolby projektu sieci Web "(lub" projektu sieci Web "*"), który pracował wcześniej w tym samouczku. W poprzedniej sekcji przedstawiono również sposób implementacji strony głównej, aby wyświetlić przycisk inicjowania lub listę sondowań.

Pozostało tutaj, aby sprawdzić informacje o głosowaniu (szczegółach) i wynikach poszczególnych sondowań.

Po wybraniu ankiety ze strony głównej aplikacja przechodzi do adresu URL/Poll/, \<key\> gdzie *klucz* jest unikatowym identyfikatorem dla sondowania. W *views.py* można zobaczyć, że `details` Funkcja jest przypisana do obsługi tego routingu adresów URL dla żądań GET i. Można także zobaczyć, że użycie `<key>` w marszrucie adresu URL mapuje dowolną trasę tego formularza do tej samej funkcji i generuje argument dla funkcji o tej samej nazwie:

```python
@app.route('/poll/<key>', methods=['GET', 'POST'])
def details(key):
    """Renders the poll details page."""
    error_message = ''
    if request.method == 'POST':
        try:
            choice_key = request.form['choice']
            repository.increment_vote(key, choice_key)
            return redirect('/results/{0}'.format(key))
        except KeyError:
            error_message = 'Please make a selection.'

    return render_template(
        'details.html',
        title='Poll',
        year=datetime.now().year,
        poll=repository.get_poll(key),
        error_message=error_message,
    )
```

Aby wyświetlić sondę (GET Requests), ta funkcja po prostu wywołuje *templates\details.html*, która iteruje `choices` tablicę sondy, tworząc przycisk radiowy dla każdego z nich.

```html
{% extends "layout.html" %}

{% block content %}

<h2>{{poll.text}}</h2>
<br />

{% if error_message %}
<p class="text-danger">{{error_message}}</p>
{% endif %}

<form action="/poll/{{poll.key}}" method="post">
    {% for choice in poll.choices %}
    <div class="radio">
        <label>
            <input type="radio" name="choice" id="choice{{choice.key}}" value="{{choice.key}}" />
            {{ choice.text }}
        </label>
    </div>
    {% endfor %}
    <br />
    <button class="btn btn-primary" type="submit">Vote</button>
</form>

{% endblock %}
```

Ponieważ przycisk **głosowania** ma `type="submit"` , wybranie tej opcji spowoduje WYgenerowanie żądania post z powrotem do tego samego adresu URL, który jest kierowany do `details` funkcji jeszcze raz. Jednak ten czas wyodrębnia wybór z danych formularza i przekierowuje do/Results/ \<choice\> .

\<key\>Adres URL/Results/jest następnie kierowany do `results` funkcji w *views.py*, która następnie wywołuje metodę sondowania `calculate_stats` i wykorzystuje *templates\results.html* do renderowania:

```python
@app.route('/results/<key>')
def results(key):
    """Renders the results page."""
    poll = repository.get_poll(key)
    poll.calculate_stats()
    return render_template(
        'results.html',
        title='Results',
        year=datetime.now().year,
        poll=poll,
    )
```

Szablon *results.html* , dla części, po prostu wykonuje iterację w wyborach sond i generuje pasek postępu dla każdego:

```html
{% extends "layout.html" %}

{% block content %}

<h2>{{poll.text}}</h2>
<br />

{% for choice in poll.choices %}
<div class="row">
    <div class="col-sm-5">{{choice.text}}</div>
    <div class="col-sm-5">
        <div class="progress">
            <div class="progress-bar" role="progressbar" aria-valuenow="{{choice.votes}}" aria-valuemin="0" aria-valuemax="{{poll.total_votes}}" style="width: {{choice.votes_percentage}}%;">
                {{choice.votes}}
            </div>
        </div>
    </div>
</div>
{% endfor %}

<br />
<a class="btn btn-primary" href="/poll/{{poll.key}}">Vote again?</a>

{% endblock %}
```

## <a name="next-steps"></a>Następne kroki

> [!Note]
> Jeśli Twoje rozwiązanie programu Visual Studio zostało zatwierdzone do kontroli źródła w trakcie tego samouczka, teraz jest dobrym terminem do wykonania kolejnego zatwierdzenia. Twoje rozwiązanie powinno być zgodne z kodem źródłowym samouczka w witrynie GitHub: [Microsoft/Python-Sample-vs-Learning-Kolba](https://github.com/Microsoft/python-sample-vs-learning-flask).

Teraz udało Ci się zapoznać się z całością projektu sieci Web "pustej kolby", "/Jade] projektu sieci Web" i "przegląd * * * * [/Jade] projektu sieci Web" w programie Visual Studio. Wiesz już, jak używać widoków, szablonów i routingu oraz jak korzystać z kopii zapasowych magazynów danych. Teraz możesz zacząć korzystać z własnej aplikacji internetowej z dowolnym widokiem i modelami, które są potrzebne.

Uruchamianie aplikacji sieci Web na komputerze deweloperskim to tylko jeden krok w udostępnieniu aplikacji klientom. Następne kroki mogą obejmować następujące zadania:

- Wdróż aplikację sieci Web na serwerze produkcyjnym, takim jak Azure App Service. Zobacz [Publikowanie w Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md).

- Dodaj implementację repozytorium, która używa innego magazynu danych na poziomie produkcyjnym, takiego jak PostgreSQL, MySQL i SQL Server (wszystkie mogą być hostowane na platformie Azure). Możesz również użyć [zestawu Azure SDK dla języka Python](/azure/python/) do pracy z usługami magazynu platformy Azure, takimi jak tabele i obiekty blob, a także Cosmos DB.

- Skonfiguruj potok ciągłej integracji/ciągłego wdrażania w usłudze, takiej jak Azure DevOps. Oprócz pracy z kontrolą źródła (za pośrednictwem Azure Repos lub GitHub lub w innym miejscu) można skonfigurować projekt platformy Azure DevOps, aby automatycznie uruchamiał testy jednostkowe jako wstępnie wymagane dla wydania, a także skonfigurować potok do wdrożenia na serwerze przejściowym w celu przeprowadzenia dodatkowych testów przed wdrożeniem w środowisku produkcyjnym. Ponadto platforma Azure DevOps integruje się z rozwiązaniami do monitorowania, takimi jak App Insights i zamyka cały cykl dzięki narzędziom do planowania Agile. Aby uzyskać więcej informacji, zobacz Tworzenie potoku ciągłej integracji/ciągłego wdrażania [dla języka Python za pomocą Azure DevOps projects](/azure/devops-project/azure-devops-project-python?view=vsts&preserve-view=true) a także ogólnej [dokumentacji usługi Azure DevOps](/azure/devops/?view=vsts&preserve-view=true).

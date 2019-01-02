---
title: Poznaj samouczek Flask w Visual Studio w kroku 5, szablon projektu sond
titleSuffix: ''
description: Przewodnik po podstawy Flask w kontekście projektów programu Visual Studio, w szczególności funkcje szablonów projektu sieci Web Flask ankiety i projektu sieci Web Flask/Jade ankiety.
ms.date: 09/04/2018
ms.prod: visual-studio-dev15
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 5938bceeb3dc7393437f44102c21d1ef16c45b63
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53923799"
---
# <a name="step-5-use-the-polls-flask-web-project-template"></a>Krok 5. Użyj szablonu projektu sieci Web Flask sond

**Poprzedniego kroku: [Pełny szablon projektu sieci Web Flask](learn-flask-visual-studio-step-04-full-flask-project-template.md)**

Po zrozumieniu szablon "Projekt sieci Web Flask" Visual Studio teraz zapoznanie się z trzeciej szablonu Flask "Sond Flask projektu sieci Web", która opiera się na tej samej bazy kodu.

W tym kroku dowiesz się, jak:

> [!div class="checklist"]
> - Tworzenie projektu z szablonu i zainicjować bazy danych (krok 5 - 1)
> - Zrozumienie modeli danych (krok 5-2)
> - Zrozumienie tworzenie kopii zapasowych magazynów danych (krok 5-3)
> - Omówienie widoków szczegółów i wyniki sondowania (krok 5-4)

Visual Studio udostępnia również szablon "Projekt sieci Web Flask/Jade sond", która wytwarza identyczną aplikację, ale używa aparatu tworzenia szablonów Jinja Jade rozszerzenia. Aby uzyskać więcej informacji, zobacz [krok 4 — szablon projektu sieci Web Flask/Jade](learn-flask-visual-studio-step-04-full-flask-project-template.md#the-flaskjade-web-project-template).

## <a name="step-5-1-create-the-project"></a>Krok 1 z 5 Utwórz projekt

1. W programie Visual Studio, przejdź do **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **LearningFlask** rozwiązanie utworzone we wcześniejszej części tego samouczka, a następnie wybierz pozycję **Dodaj**  >   **Nowy projekt**. (, Jeśli chcesz użyć nowego rozwiązania, wybierz **pliku** > **New** > **projektu** zamiast.)

1. W oknie dialogowym Nowy projekt wyszukiwanie i wybieranie **projektu sieci Web Flask sond** szablonu, wywołaj projektu "FlaskPolls", a następnie wybierz pozycję **OK**.

1. Podobnie jak inne szablony projektów w programie Visual Studio zawiera szablon "Projekt sieci Web Flask sond" *requirements.txt* plików, programu Visual Studio pyta, gdzie zainstalować te zależności. Wybierz opcję, **zainstalować w środowisku wirtualnym**, a następnie w **Dodawanie środowiska wirtualnego** okna dialogowego wybierz **Utwórz** aby zaakceptować wartości domyślne. (Ten szablon wymaga Flask, a także pakietów usługi azure storage i pymongo; pyjade wymaga również "Sond Flask/Jade projektu sieci Web").

1. Ustaw **FlaskPolls** projektu jako domyślny dla rozwiązania Visual Studio przez kliknięcie prawym przyciskiem myszy tego projektu w **Eksploratora rozwiązań** i wybierając polecenie **Ustaw jako projekt startowy**. Projekt startowy, który jest pokazany w pogrubienie, to co program jest uruchamiany w przypadku, gdy uruchamiasz debuger.

1. Wybierz **debugowania** > **Rozpocznij debugowanie** (**F5**) lub użyj **serwera sieci Web** przycisk na pasku narzędzi, aby uruchomić serwer:

    ![Uruchamianie serwera sieci web przycisku paska narzędzi w programie Visual Studio](media/django/run-web-server-toolbar-button.png)

1. Aplikacja utworzona przez szablon ma trzy strony Strona główna o i skontaktuj się z pomocą, której możesz przechodzić między za pomocą paska nawigacji górnej. Zająć minutę lub dwie zbadać różne części aplikacji (informacje i skontaktuj się z strony są bardzo podobne do "Projekt sieci Web Flask" i nie są omówione w dalszych).

    ![Pełen przegląd aplikacja projektu sieci Web Flask sond](media/flask/step06-full-app-view.png)

1. Na stronie głównej **tworzenie przykładowej ankiety** przycisk inicjuje magazynu danych aplikacji przy użyciu trzech różnych sond, które są opisane w *models/samples.json* strony. Domyślnie aplikacja używa w pamięci bazy danych (jak pokazano na stronie informacje), który jest resetowany każdorazowo, gdy aplikacja zostanie ponownie uruchomiony. Aplikacja również zawiera kod, aby pracować z usługi Azure Storage i bazą danych Mongo, zgodnie z opisem w dalszej części tego artykułu.

1. Po został zainicjowany magazyn danych, możesz głosować w różnych sond pokazany na stronie głównej (paska nawigacji i stopki są pomijane dla zwięzłości):

    ![Widok aplikacji ankiety, gdy magazyn danych jest inicjowany](media/flask/step06-polls-initialized.png)

1. Wybieranie sondowania Wyświetla określone dane:

    ![Interfejs głosowanie w ankiecie](media/flask/step06-polls-voting-interface.png)

1. Po głosowania, aplikacja wyświetlający stronę wyników i umożliwia głosowanie ponownie:

    ![Widok wyników po głosowania](media/flask/step06-polls-results.png)

1. Możesz pozostawić aplikacja uruchomiona w kolejnych sekcjach.

    Jeśli chcesz zatrzymać aplikację i [Zatwierdź zmiany do kontroli źródła](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control), najpierw otwórz **zmiany** strony w **Team Explorer**, kliknij prawym przyciskiem myszy folder (środowiska wirtualnego prawdopodobnie **env**) i wybierz **ignorować te elementy lokalne**.

### <a name="examine-the-project-contents"></a>Sprawdź zawartość projektu

Wspomniane wcześniej. Większość co to jest projekt utworzony z szablonu "Projekt sieci Web Flask sond" (i szablonów "Projekt sieci Web Flask/Jade sond") należy się zapoznać, jeśli zostały przedstawione z szablonów projektów w programie Visual Studio. Dodatkowe kroki w tym artykule podsumowanie bardziej znaczące zmiany i uzupełnienia, a mianowicie modeli danych i dodatkowe widoki.

## <a name="step-5-2-understand-the-data-models"></a>Krok 2 z 5 Zrozumienie modeli danych

Modele danych dla aplikacji są klasy języka Python o nazwie sondowania i wyboru, które są zdefiniowane w *modeli /\_\_init\_\_.py*. Sondowaniu reprezentuje zapytania, dla którego kolekcję wystąpień wyboru reprezentują dostępne odpowiedzi. Sondowaniu przechowuje także całkowita liczba głosów (dla dowolnej), a metoda, aby obliczyć statystyki, które są używane do generowania widoków:

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

Te modele danych są ogólne elementy abstrakcji, umożliwiające widoków aplikacji, aby pracować z różnego rodzaju kopii magazyny danych, które są opisane w następnym kroku.

## <a name="step-5-3-understand-the-backing-data-stores"></a>Krok 3 z 5 Zrozumienie tworzenie kopii zapasowych magazynów danych

Aplikacja utworzona przez szablon "Projekt sieci Web Flask sond" można uruchomić względem magazynu danych w pamięci, usługa Azure table storage lub bazie danych Mongo DB.

Mechanizm magazynu danych działa w następujący sposób:

1. Typ repozytorium jest określony za pomocą `REPOSITORY_NAME` zmiennej środowiskowej, która może być równa "pamięć", "azuretablestore" lub "bazy danych mongodb". Ilość kodu w *settings.py* pobiera nazwę, za pomocą "pamięć" jako domyślny. Aby zmienić magazyn zapasowy, musisz ustawić zmienną środowiskową i uruchom ponownie aplikację.

    ```python
    from os import environ
    REPOSITORY_NAME = environ.get('REPOSITORY_NAME', 'memory')
    ```

1. *Settings.py* kodzie następnie inicjuje `REPOSITORY_SETTINGS` obiektu. Jeśli chcesz używać magazynu tabel platformy Azure lub Mondo bazy danych, należy najpierw zainicjować te magazyny danych w innym miejscu, a następnie ustaw zmienne środowiskowe wymagane, określające aplikacji, jak połączyć się z magazynem:

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

1. W *views.py*, aplikacja wywołuje metodę fabryki, aby zainicjować `Repository` przy użyciu nazwy i ustawienia magazynu danych:

    ```python
    from FlaskPolls.models import PollNotFound
    from FlaskPolls.models.factory import create_repository
    from FlaskPolls.settings import REPOSITORY_NAME, REPOSITORY_SETTINGS

    repository = create_repository(REPOSITORY_NAME, REPOSITORY_SETTINGS)
    ```

1. `factory.create_repository` Metoda znajduje się w *models\factory.py*, który po prostu importuje moduł odpowiedniego repozytorium, a następnie tworzy `Repository` wystąpienie:

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

1. Implementacje `Repository` klasy, które są specyficzne dla każdego magazynu danych można znaleźć w *models\azuretablestorage.py*, *models\mongodb.py*, i *models\memory.py* . Wdrożenia usługi Azure storage korzysta z pakietu usługi azure storage; Implementacja Mongo DB używa pakietu pymongo. Jak wspomniano w kroku 5-1, oba pakiety znajdują się w szablonie projektu *requirements.txt* pliku. Eksplorowanie szczegóły pozostanie w charakterze ćwiczenia dla czytnika.

Krótko mówiąc `Repository` klasa przenosi szczegółowe informacje na temat magazynu danych, a aplikacja używa zmiennych środowiskowych w czasie wykonywania można wybrać i skonfigurować, do których trzy implementacji w celu użycia.

Poniższe kroki obsługę magazynu danych innego niż trzy dostarczone przez szablon projektu, jeśli zaistnieje taka potrzeba:

1. Kopiuj *memory.py* do nowego pliku, aby mieć podstawowy interfejs dla `Repository` klasy.
1. Zmodyfikuj implementacji klasy jako pasujące do magazynu danych, z którego korzystasz.
1. Modyfikowanie *factory.py* Aby dodać kolejny `elif` przypadek, który rozpoznaje nazwę magazynowi danych dodane, a następnie importuje odpowiedniego modułu.
1. Modyfikowanie *settings.py* rozpoznawanie inną nazwę w `REPOSITORY_NAME` zmiennej środowiskowej i zainicjować `REPOSITORY_SETTINGS` odpowiednio.

### <a name="seed-the-data-store-from-samplesjson"></a>Magazyn danych z samples.json umieszczenia

Początkowo dowolnego magazynu danych w wybranym zawiera nie ankiety, więc strony głównej aplikacji przedstawia komunikat **nie dostępnych sond** wraz z **tworzenie przykładowej ankiety** przycisku. Po wybraniu przycisku, natomiast widok zmiany do wyświetlenia dostępnych sond. Ten przełącznik odbywają się za pośrednictwem warunkowego tagów w *templates\index.html* (niektóre puste wiersze dla zwięzłości pominięto):

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

`polls` Zmiennej w szablonie pochodzi z wywołania `repository.get_polls`, która nie zwraca żadnego dopóki magazyn danych jest inicjowany.

Wybieranie **tworzenie przykładowej ankiety** przycisku powoduje przejście do adresu URL /seed. Program obsługi dla tej trasy jest zdefiniowany w *views.py*:

```python
@app.route('/seed', methods=['POST'])
def seed():
    """Seeds the database with sample polls."""
    repository.add_sample_polls()
    return redirect('/')
```

Wywołanie `repository.add_sample_polls()` kończy się w jednym z konkretnym `Repository` implementacje dla magazynu danych wybrany. Każda implementacja wywołuje `_load_samples_json` znaleźć metodę w *modeli\_\_init\_\_.py* załadować *models\samples.json* pliku do pamięci, następnie wykonuje iterację przez te dane, aby utworzyć niezbędne `Poll` i `Choice` obiektów w magazynie danych.

Po zakończeniu tego procesu, `redirect('/')` instrukcji w `seed` metoda wraca do strony głównej. Ponieważ `repository.get_polls` teraz zwraca obiekt danych warunkowego znaczniki *templates\index.html* teraz renderuje tabelę zawierającą ankiety.

### <a name="question-how-does-one-add-new-polls-to-the-app"></a>Pytanie: Jak jeden dodać nowe sonduje usługę do aplikacji?

Odpowiedź: Aplikacja, zgodnie z postanowieniami przy użyciu szablonu projektu nie zawiera funkcji do dodawania lub edytowania ankiety. Możesz zmodyfikować *models\samples.json* Aby utworzyć nowe dane inicjowania, ale oznacza to resetowanie magazynu danych. Aby zaimplementować funkcje edycji, musisz rozszerzyć `Repository` interfejsu klasy za pomocą metod, aby utworzyć niezbędne `Choice` i `Poll` wystąpień, implementować interfejs użytkownika w dodatkowych stron, które korzystają z tych metod.

## <a name="step-5-4-understand-the-poll-detail-and-results-views"></a>Krok 5 — 4: Omówienie widoków szczegółów i wyniki sondowania

Większość widoków generowane przez Szablony "Projekt sieci Web Flask sond" i "Projekt sieci Web Flask/Jade sond", takie jak widoki informacje i skontaktuj się z stron, są bardzo podobne do widoków utworzonej przez szablon "Projekt sieci Web Flask" (lub "Projekt sieci Web Flask/Jade"), nad którą były prowadzone za pomocą wcześniej w tym samouczku. W poprzedniej sekcji także przedstawiono sposób implementacji na stronie głównej do pokazywania przycisku inicjowania lub listę sond.

Co jeszcze pozostało w tym miejscu jest zbadanie głosowania (szczegóły) oraz widok wyników poszczególnych sondowania.

Po wybraniu sondowania ze strony głównej aplikacja przejdzie do /poll/ adresu URL\<klucz\> gdzie *klucza* jest unikatowy identyfikator dla sondowania. W *views.py* widzimy, że `details` funkcji jest przypisany do obsługi tego adresu URL routingu żądań i GET. Możesz też sprawdzić, że używanie `<key>` w adresie URL trasy mapuje wszystkie trasy tworzące do tej samej funkcji i generuje argument funkcji o takiej samej nazwie:

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

Aby wyświetlić sondowania (żądania GET), ta funkcja po prostu wywołuje widok na *templates\details.html*, który iteruje po sondowania `choices` tablicy, tworzenie przycisku radiowego dla każdej.

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

Ponieważ **głos** przycisk ma `type="submit"`, zaznaczając go generuje żądanie POST do tego samego adresu URL, który jest kierowany do `details` funkcji jeszcze raz. Tym razem jednak wyodrębnia wybór z danych formularza i przekierowuje do /results/\<wybór\>.

/Results/\<klucz\> adres URL jest następnie przekierowywane do `results` działa w programach *views.py*, który następnie wywołuje sondowania `calculate_stats` metody i wymaga *templates\results.html* do renderowania:

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

*Results.html* szablonu ze swojej strony, po prostu wykonuje iterację przez opcji sondowania i generuje pasek postępu dla każdego:

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
> Jeśli do kontroli źródła w toku w tym samouczku został zostały zatwierdzanie rozwiązania programu Visual Studio, teraz jest dobry moment, aby wykonać inną zatwierdzenia. Rozwiązania powinny odpowiadać kod źródłowy samouczek w witrynie GitHub: [Microsoft/python — przykładowe vs uczenia — platformy flask](https://github.com/Microsoft/python-sample-vs-learning-flask).

Teraz zostały zbadane materiałami szablony "Pusty projekt sieci Web Flask", "Projekt sieci Web Flask [/Jade]" i "Sond projektu sieci Web Flask [/Jade]" w programie Visual Studio. Wiesz już, podstawy Flask, takich jak routing i korzystanie z widoków i szablonów i zostały już, jak używać tworzenie kopii zapasowych magazynów danych. Teraz można rozpocząć pracę w aplikacji sieci web własne z dowolną widoki i modele, które są potrzebne.

Uruchamianie aplikacji sieci web na komputerze deweloperskim jest tylko jeden krok w zakresie udostępniania aplikacji dla klientów. Kolejne kroki mogą obejmować następujące zadania:

- Wdrażanie aplikacji sieci web na serwerze produkcyjnym, takich jak usługa Azure App Service. Zobacz [publikowanie w usłudze Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md).

- Dodaj implementację repozytorium, która używa innego magazynu danych na poziomie produkcyjnym, takich jak PostgreSQL, MySQL i SQL Server (które mogą być hostowane na platformie Azure). Można również użyć [zestawu Azure SDK dla języka Python](azure-sdk-for-python.md) do pracy z usług Azure storage, takie jak tabele i obiektów blob, a także usługi Cosmos DB.

- Konfigurowanie potoku ciągłej integracji/ciągłego wdrażania usługi, takie jak DevOps platformy Azure. Oprócz Praca z kontrolą źródła (przy użyciu Azure repozytoriów GitHub i/lub gdzie indziej), można skonfigurować projekt DevOps platformy Azure do automatycznego uruchamiania testów jednostkowych jako warunek wstępny dla wersji i także skonfigurować potok do wdrażania na serwerze tymczasowym dla dodatkowe testy przed wdrożeniem w środowisku produkcyjnym. Azure DevOps, ponadto integruje się z usługą monitorowania rozwiązań, takich jak usługi App Insights i zamknięcie całego cyklu za pomocą narzędzi planowania agile. Aby uzyskać więcej informacji, zobacz [utworzyć potok ciągłej integracji/ciągłego Dostarczania dla języka Python za pomocą projektu DevOps platformy Azure](/azure/devops-project/azure-devops-project-python?view=vsts) i również ogólne [dokumentacji usługi Azure DevOps](/azure/devops/?view=vsts).

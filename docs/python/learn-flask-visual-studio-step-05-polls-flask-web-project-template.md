---
title: Dowiedz się samouczek Kolby w programie Visual Studio krok 5, szablon projektu Ankiety
titleSuffix: ''
description: Przewodnik po podstawowych flask w kontekście projektów programu Visual Studio, w szczególności funkcje sondowania Flask Web Project i ankiety Flask/Jade web project szablonów.
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: c540dfef9d2d46bb621432b3e37438e0b6b07298
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "70154893"
---
# <a name="step-5-use-the-polls-flask-web-project-template"></a>Krok 5: Użyj szablonu projektu ankiety Flask Web Project

**Poprzedni krok: [Użyj pełnego szablonu projektu Flask Web Project](learn-flask-visual-studio-step-04-full-flask-project-template.md)**

Po zrozumieniu szablonu "Flask Web Project" programu Visual Studio można teraz przyjrzeć się trzeciemu szablonowi Flask, "Polls Flask Web Project", który opiera się na tej samej podstawie kodu.

W tym kroku dowiesz się, jak:

> [!div class="checklist"]
> - Tworzenie projektu na podstawie szablonu i inicjowanie bazy danych (krok 5-1)
> - Opis modeli danych (krok 5-2)
> - Opis zapasów danych (krok 5-3)
> - Opis szczegółów ankiety i wyświetleń wyników (krok 5-4)

Visual Studio udostępnia również szablon "Sonduje flask/jade web project", który tworzy identyczną aplikację, ale używa rozszerzenia Jade dla aparatu szablonów Jinja. Aby uzyskać szczegółowe informacje, zobacz [Krok 4 - Szablon projektu sieci Web Flask/Jade](learn-flask-visual-studio-step-04-full-flask-project-template.md#the-flaskjade-web-project-template).

## <a name="step-5-1-create-the-project"></a>Krok 5-1: Tworzenie projektu

1. W programie Visual Studio przejdź do **programu Solution Explorer**, kliknij prawym przyciskiem myszy rozwiązanie **LearningFlask** utworzone wcześniej w tym samouczku i wybierz pozycję **Dodaj** > **nowy projekt**. (Alternatywnie, jeśli chcesz użyć nowego rozwiązania, wybierz **pozycję Plik** > **nowego** > **projektu).**

1. W oknie dialogowym nowego projektu wyszukaj i wybierz szablon **projektu sieci Web Sondy Flask** Web, zadzwoń do projektu "FlaskPolls" i wybierz **przycisk OK**.

1. Podobnie jak inne szablony projektów w programie Visual Studio, szablon "Polls Flask Web Project" zawiera plik *requirements.txt,* program Visual Studio pyta, gdzie zainstalować te zależności. Wybierz opcję **Zainstaluj w środowisku wirtualnym,** a następnie w oknie dialogowym **Dodaj środowisko wirtualne** wybierz pozycję **Utwórz,** aby zaakceptować wartości domyślne. (Ten szablon wymaga flask, jak również azure-storage i pymongo pakietów; "Polls Flask/Jade Web Project" wymaga również pyjade.)

1. Ustaw projekt **FlaskPolls** jako domyślny dla rozwiązania programu Visual Studio, klikając prawym przyciskiem myszy ten projekt w **Eksploratorze rozwiązań** i wybierając **pozycję Ustaw jako projekt startowy.** Projekt uruchamiania, który jest wyświetlany pogrubioną czcionką, jest tym, co jest uruchamiane po uruchomieniu debugera.

1. Wybierz **debugowanie** > **rozpocznij debugowanie** **(F5)** lub użyj przycisku Serwera sieci **Web** na pasku narzędzi, aby uruchomić serwer:

    ![Uruchamianie przycisku paska narzędzi serwera sieci Web w programie Visual Studio](media/django/run-web-server-toolbar-button.png)

1. Aplikacja utworzona przez szablon ma trzy strony: Strona główna, Informacje i Kontakt, które można nawigować między za pomocą górnego paska nawigacji. Poświęć minutę lub dwie, aby zbadać różne części aplikacji (strony Informacje i Kontakty są bardzo podobne do "Projektu Flask Web Project" i nie są dalej omawiane).

    ![Pełny widok aplikacji Polls Flask Web Project](media/flask/step06-full-app-view.png)

1. Na stronie głównej przycisk **Utwórz przykładowe ankiety** inicjuje magazyn danych aplikacji z trzema różnymi ankietami, które są opisane na stronie *models/samples.json.* Domyślnie aplikacja używa bazy danych w pamięci (jak pokazano na stronie Informacje), która jest resetowana przy każdym ponownym uruchomieniu aplikacji. Aplikacja zawiera również kod do pracy z usługą Azure Storage i Mongo DB, zgodnie z opisem w dalszej części tego artykułu.

1. Po zainicjowaniu magazynu danych możesz głosować w różnych ankietach, jak pokazano na stronie głównej (pasek nawigacyjny i stopka są pomijane dla zwięzłości):

    ![Widok aplikacji Ankiety po zainicjowaniu magazynu danych](media/flask/step06-polls-initialized.png)

1. Wybranie ankiety powoduje wyświetlenie określonych opcji:

    ![Interfejs głosowania w ankiecie](media/flask/step06-polls-voting-interface.png)

1. Po głosowaniu aplikacja pokazuje stronę wyników i pozwala głosować ponownie:

    ![Widok wyników po głosowaniu](media/flask/step06-polls-results.png)

1. Możesz pozostawić aplikację z uruchomiona dla sekcji, które należy wykonać.

    Jeśli chcesz zatrzymać aplikację i [zatwierdzić zmiany w formancie źródłowym,](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control)najpierw otwórz stronę **Zmiany** w **Eksploratorze zespołu,** kliknij prawym przyciskiem myszy folder środowiska wirtualnego (prawdopodobnie **env)** i wybierz pozycję **Ignoruj te elementy lokalne**.

### <a name="examine-the-project-contents"></a>Sprawdzanie zawartości projektu

Jak wspomniano wcześniej. wiele z tego, co znajduje się w projekcie utworzonym na podstawie szablonu "Polls Flask Web Project" (i szablonu "Polls Flask/Jade Web Project") powinno być znane, jeśli zostały zbadane inne szablony projektów w programie Visual Studio. Dodatkowe kroki w tym artykule podsumować bardziej znaczące zmiany i uzupełnienia, a mianowicie modeli danych i dodatkowych widoków.

## <a name="step-5-2-understand-the-data-models"></a>Krok 5-2: Zrozumienie modeli danych

Modele danych dla aplikacji są python klasy o nazwie Sonda i wybór, które są zdefiniowane w *modelach /\_\_init\_\_.py*. A Poll reprezentuje pytanie, dla których kolekcja Choice wystąpień reprezentują dostępne odpowiedzi. Ankieta zachowuje również całkowitą liczbę głosów (dla dowolnego wyboru) i metodę obliczania statystyk, które są używane do generowania widoków:

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

Te modele danych są ogólne abstrakcje, które umożliwiają widoki aplikacji do pracy z różnych typów zapasów danych, które są opisane w następnym kroku.

## <a name="step-5-3-understand-the-backing-data-stores"></a>Krok 5-3: Zrozumienie zapasowych magazynów danych

Aplikacja utworzona przez szablon "Polls Flask Web Project" można uruchomić względem magazynu danych w pamięci, w magazynie tabel platformy Azure lub w bazie danych Mongo DB.

Mechanizm przechowywania danych działa w następujący sposób:

1. Typ repozytorium jest określony `REPOSITORY_NAME` za pomocą zmiennej środowiskowej, która może być ustawiona na "memory", "azuretablestore" lub "mongodb". Trochę kodu w *settings.py* pobiera nazwę, używając "pamięci" jako domyślnej. Jeśli chcesz zmienić magazyn kopii zapasowej, musisz ustawić zmienną środowiskową i ponownie uruchomić aplikację.

    ```python
    from os import environ
    REPOSITORY_NAME = environ.get('REPOSITORY_NAME', 'memory')
    ```

1. Kod *settings.py* następnie inicjuje `REPOSITORY_SETTINGS` obiekt. Jeśli chcesz użyć magazynu tabel platformy Azure lub mondo DB, należy najpierw zainicjować te magazyny danych w innym miejscu, a następnie ustawić niezbędne zmienne środowiskowe, które informują aplikację, jak połączyć się ze sklepem:

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

1. W *views.py*aplikacja wywołuje metodę fabryczną w celu `Repository` zainicjowania obiektu przy użyciu nazwy i ustawień magazynu danych:

    ```python
    from FlaskPolls.models import PollNotFound
    from FlaskPolls.models.factory import create_repository
    from FlaskPolls.settings import REPOSITORY_NAME, REPOSITORY_SETTINGS

    repository = create_repository(REPOSITORY_NAME, REPOSITORY_SETTINGS)
    ```

1. Metoda `factory.create_repository` znajduje się w *models\factory.py*, który po prostu importuje odpowiedni `Repository` moduł repozytorium, a następnie tworzy wystąpienie:

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

1. `Repository` Implementacje klasy, które są specyficzne dla każdego magazynu danych można znaleźć w *models\azuretablestorage.py*, *models\mongodb.py*i *models\memory.py*. Implementacja usługi Azure storage używa pakietu magazynu azure; implementacja Mongo DB wykorzystuje pakiet pymongo. Jak wspomniano w kroku 5-1, oba pakiety są zawarte w pliku *requirements.txt* szablonu projektu. Odkrywanie szczegółów pozostaje jako ćwiczenie dla czytelnika.

Krótko mówiąc, `Repository` klasa abstrakcji specyfiki magazynu danych, a aplikacja używa zmiennych środowiskowych w czasie wykonywania, aby wybrać i skonfigurować, które z trzech implementacji do użycia.

W razie potrzeby w następujących krokach dodano obsługę innego magazynu danych niż trzy dostarczone przez szablon projektu:

1. Kopiuj *memory.py* do nowego pliku, dzięki czemu `Repository` masz podstawowy interfejs dla klasy.
1. Zmodyfikuj implementację klasy, aby odpowiadała magazynowi danych, którego używasz.
1. Zmodyfikuj *factory.py,* aby dodać inną `elif` sprawę, która rozpoznaje nazwę dodanego magazynu danych i importuje odpowiedni moduł.
1. Zmodyfikuj *settings.py* rozpoznać inną nazwę w zmiennej środowiskowej `REPOSITORY_NAME` i `REPOSITORY_SETTINGS` odpowiednio zainicjować.

### <a name="seed-the-data-store-from-samplesjson"></a>Seed magazynu danych z samples.json

Początkowo każdy wybrany magazyn danych nie zawiera żadnych ankiet, więc strona główna aplikacji wyświetla komunikat **Brak ankiet dostępnych** wraz z przyciskiem **Utwórz przykładowe ankiety.** Po wybraniu przycisku widok zmienia się jednak, aby wyświetlić dostępne ankiety. Ten przełącznik odbywa się za pomocą tagów warunkowych w *templates\index.html* (niektóre puste wiersze pominięte dla zwięzłości):

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

Zmienna `polls` w szablonie pochodzi `repository.get_polls`z wywołania do , który zwraca nic, dopóki magazyn danych jest inicjowany.

Wybranie przycisku **Utwórz przykładowe ankiety** przechodzi do /seed URL. Program obsługi dla tej trasy jest zdefiniowany w *views.py:*

```python
@app.route('/seed', methods=['POST'])
def seed():
    """Seeds the database with sample polls."""
    repository.add_sample_polls()
    return redirect('/')
```

Wywołanie `repository.add_sample_polls()` kończy się w jednej `Repository` z określonych implementacji dla wybranego magazynu danych. Każda implementacja `_load_samples_json` wywołuje metodę znalezioną w *\_\_\_\_modelach init .py,* aby załadować plik *models\samples.json* do pamięci, a następnie iteruje za pośrednictwem tych danych, aby utworzyć niezbędne `Poll` i `Choice` obiekty w magazynie danych.

Po zakończeniu tego procesu `redirect('/')` instrukcja `seed` w metodzie przechodzi z powrotem do strony głównej. Ponieważ `repository.get_polls` teraz zwraca obiekt danych, tagi warunkowe w *templates\index.html* renderuje teraz tabelę zawierającą ankiety.

### <a name="question-how-does-one-add-new-polls-to-the-app"></a>Pytanie: Jak dodać nowe ankiety do aplikacji?

Odpowiedź: aplikacja udostępniana za pośrednictwem szablonu projektu nie zawiera możliwości dodawania lub edytowania ankiet. Można zmodyfikować *models\samples.json,* aby utworzyć nowe dane inicjowania, ale oznaczałoby to zresetowanie magazynu danych. Aby zaimplementować funkcje `Repository` edycji, należy rozszerzyć `Choice` interfejs `Poll` klasy o metody, aby utworzyć niezbędne i wystąpienia, a następnie zaimplementować interfejs użytkownika w dodatkowych stronach, które używają tych metod.

## <a name="step-5-4-understand-the-poll-detail-and-results-views"></a>Krok 5-4: Poznaj szczegóły ankiety i wyświetlenia wyników

Większość widoków generowanych przez szablony "Polls Flask Web Project" i "Polls Flask/Jade Web Project", takie jak widoki stron Informacje i Kontakt, są bardzo podobne do widoków utworzonych przez szablon "Flask Web Project" (lub "Flask/Jade Web Project"), z którymi pracowałeś wcześniej w tym samouczku. W poprzedniej sekcji dowiesz się również, jak strona główna jest implementowana, aby wyświetlić przycisk inicjowania lub listę ankiet.

Pozostaje tu zbadać głosowanie (szczegóły) i wyniki poszczególnych ankiet.

Po wybraniu ankiety ze strony głównej aplikacja przechodzi do\<adresu\> URL /poll/ klucz, gdzie *klucz* jest unikatowy identyfikator dla ankiety. W *views.py* widać, że `details` funkcja jest przypisana do obsługi tego routingu adresu URL dla get i żądań. Widać również, że `<key>` użycie w routiscie adresu URL zarówno mapuje dowolną trasę tego formularza do tej samej funkcji, jak i generuje argument do funkcji o tej samej nazwie:

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

Aby wyświetlić ankietę (żądania GET), ta funkcja po prostu wywołuje *templates\details.html*, który iteruje za pomocą tablicy ankiety, `choices` tworząc przycisk opcji dla każdego.

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

Ponieważ **Vote** przycisk Głosowanie `type="submit"`ma , wybierając go generuje żądanie POST z powrotem do `details` tego samego adresu URL, który jest ponownie kierowany do funkcji. Tym razem jednak wyodrębnia wybór z danych formularza i przekierowuje do /results/\<choice\>.

\</results/ key\> URL jest następnie `results` kierowane do funkcji w *views.py*, który `calculate_stats` następnie wywołuje metodę ankiety i wykorzystuje *templates\results.html* do renderowania:

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

Szablon *results.html,* ze swojej strony, po prostu iteruje przez wybory ankiety i generuje pasek postępu dla każdego:

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
> Jeśli zostały popełnienia rozwiązania programu Visual Studio do kontroli źródła w trakcie tego samouczka, teraz jest dobry czas, aby wykonać inne zatwierdzenie. Twoje rozwiązanie powinno być zgodne z kodem źródłowym samouczka w witrynie GitHub: [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask).

Teraz zbadano całość szablonów "Pusty projekt sieci Web Flask", "Flask[/Jade] Web Project" i "Polls Flask[/Jade] Web Project" w programie Visual Studio. Poznaliśmy wszystkie podstawowe informacje dotyczące flask, takie jak używanie widoków, szablonów i routingu, i widziałeś, jak używać zapasowych magazynów danych. Teraz powinieneś być w stanie rozpocząć pracę w aplikacji internetowej z dowolnymi widokami i modelami, których potrzebujesz.

Uruchamianie aplikacji sieci web na komputerze deweloperskim to tylko jeden krok w udostępnianiu aplikacji klientom. Następne kroki mogą obejmować następujące zadania:

- Wdrażanie aplikacji sieci web na serwerze produkcyjnym, takim jak usługa Azure App Service. Zobacz [Publikowanie w usłudze Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md).

- Dodaj implementację repozytorium, która używa innego magazynu danych na poziomie produkcji, takiego jak PostgreSQL, MySQL i SQL Server (wszystkie z nich mogą być hostowane na platformie Azure). Można również użyć [narzędzia Azure SDK for Python](/azure/python/) do pracy z usługami magazynu platformy Azure, takimi jak tabele i obiekty blob, a także usługa Cosmos DB.

- Konfigurowanie potoku ciągłej integracji/ciągłego wdrażania w usłudze takiej jak Azure DevOps. Oprócz pracy z kontrolą źródła (za pośrednictwem usługi Azure Repos lub GitHub lub w innym miejscu), można skonfigurować projekt DevOps platformy Azure tak, aby automatycznie uruchamiał testy jednostkowe jako warunek wstępny wydania, a także skonfigurował potok do wdrożenia na serwerze przejściowym dodatkowe testy przed wdrożeniem w produkcji. Ponadto usługa Azure DevOps integruje się z rozwiązaniami do monitorowania, takimi jak usługa App Insights, i zamyka cały cykl za pomocą narzędzi do elastycznego planowania. Aby uzyskać więcej informacji, zobacz [Tworzenie potoku ciągłej integracji/ciągłego wdrażania dla języka Python za pomocą projektów usługi Azure DevOps,](/azure/devops-project/azure-devops-project-python?view=vsts) a także ogólnej [dokumentacji usługi Azure DevOps.](/azure/devops/?view=vsts)

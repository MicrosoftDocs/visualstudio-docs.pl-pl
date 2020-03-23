---
title: Dowiedz się samouczek Django w programie Visual Studio, krok 1, podstawy Django
titleSuffix: ''
description: Przewodnik podstawowych Django w kontekście projektów programu Visual Studio, demonstrując wsparcie Visual Studio zapewnia rozwoju Django.
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: b41ed3901cd4ad18a1b52ddbdc7ee6fd82cb5380
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "62962261"
---
# <a name="tutorial-get-started-with-the-django-web-framework-in-visual-studio"></a>Samouczek: Wprowadzenie do struktury sieci Web Django w programie Visual Studio

[Django](https://www.djangoproject.com/) to wysokiej klasy struktura Pythona zaprojektowana z myślą o szybkim, bezpiecznym i skalowalnym tworzeniu stron internetowych. W tym samouczku eksploruje platformę Django w kontekście szablonów projektu, które program Visual Studio zapewnia usprawnienie tworzenia aplikacji sieci web opartych na Django.

Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:

> [!div class="checklist"]
> - Utwórz podstawowy projekt Django w repozytorium Git za pomocą szablonu "Blank Django Web Project" (krok 1)
> - Utwórz aplikację Django za pomocą jednej strony i twórz tę stronę za pomocą szablonu (krok 2)
> - Obsługa plików statycznych, dodawanie stron i używanie dziedziczenia szablonów (krok 3)
> - Użyj szablonu Django Web Project, aby utworzyć aplikację z wieloma stronami i responsywnym projektem (krok 4)
> - Uwierzytelnij użytkowników (krok 5)
> - Szablon Usługi Polls Django Web Project służy do tworzenia aplikacji, która używa modeli, migracji baz danych i dostosowań do interfejsu administracyjnego (krok 6)

## <a name="prerequisites"></a>Wymagania wstępne

- Visual Studio 2017 lub nowsze w systemie Windows z następującymi opcjami:
  - Obciążenie **programistyczne języka Python** **(obciążenie karty** w instalatorze). Aby uzyskać instrukcje, zobacz [Instalowanie obsługi języka Python w programie Visual Studio](installing-python-support-in-visual-studio.md).
  - **Git dla systemu Windows** i **rozszerzenie GitHub dla programu Visual Studio** na karcie Poszczególne **składniki** w obszarze **Narzędzia kodu**.

Szablony projektów Django są również dołączone do wszystkich wcześniejszych wersji narzędzi Python Tools for Visual Studio, chociaż szczegóły mogą różnić się od tego, co zostało omówione w tym samouczku (szczególnie różne we wcześniejszych wersjach struktury Django).

Programowanie języka Python nie jest obecnie obsługiwane w programie Visual Studio dla komputerów Mac. Na komputerach Mac i Linux użyj [rozszerzenia Python w programie Visual Studio Code](https://code.visualstudio.com/docs/python/python-tutorial).

### <a name="visual-studio-projects-and-django-projects"></a>"Projekty Visual Studio" i "Projekty Django"

W terminologii Django "projekt Django" składa się z kilku plików konfiguracyjnych na poziomie witryny wraz z jedną lub kilkoma "aplikacjami", które wdrażasz na hoście internetowym w celu utworzenia pełnej aplikacji internetowej. Projekt Django może zawierać wiele aplikacji, a ta sama aplikacja może być w wielu projektach Django.

Projekt programu Visual Studio, ze swojej strony, może zawierać projekt Django wraz z wieloma aplikacjami. Ze względu na prostotę, gdy ten samouczek odnosi się tylko do "projektu", odnosi się do projektu programu Visual Studio. Gdy odnosi się do "Projektu Django" część aplikacji internetowej, używa "Projekt Django" specjalnie.

W trakcie tego samouczka utworzysz jedno rozwiązanie programu Visual Studio, które zawiera trzy oddzielne projekty Django, z których każdy zawiera jedną aplikację Django. Utrzymując projekty w tym samym rozwiązaniu, można łatwo przełączać się między różnymi plikami do porównania.

## <a name="step-1-1-create-a-visual-studio-project-and-solution"></a>Krok 1-1: Tworzenie projektu i rozwiązania programu Visual Studio

Podczas pracy z Django z wiersza polecenia, zazwyczaj `django-admin startproject <project_name>` należy rozpocząć projekt, uruchamiając polecenie. W programie Visual Studio przy użyciu szablonu "Blank Django Web Project" zapewnia taką samą strukturę w projekcie i rozwiązaniu programu Visual Studio.

1. W programie Visual Studio wybierz **pozycję Plik** > **nowego** > **projektu**, wyszukaj hasło "Django" i wybierz szablon Pusty projekt **internetowy Django.** (Szablon znajduje się również w obszarze **Python** > **Web** na liście po lewej stronie).

    ![Nowe okno dialogowe projektu w programie Visual Studio dla pustego projektu sieci Web Django](media/django/step01-new-blank-project.png)

1. W polach u dołu okna dialogowego wprowadź następujące informacje (jak pokazano na poprzedniej grafice), a następnie wybierz **przycisk OK:**

    - **Nazwa**: ustaw nazwę projektu programu Visual Studio na **BasicProject**. Ta nazwa jest również używana dla projektu Django.
    - **Lokalizacja**: określ lokalizację, w której ma być utworzone rozwiązanie i projekt programu Visual Studio.
    - **Rozwiązanie:** pozostaw tę formant jako domyślną **Opcję Utwórz nowe rozwiązanie.**
    - **Nazwa rozwiązania:** zestaw **LearningDjango**, który jest odpowiedni dla rozwiązania jako kontener dla wielu projektów w tym samouczku.
    - **Tworzenie katalogu dla rozwiązania**: Pozostaw zestaw (domyślny).
    - **Utwórz nowe repozytorium Git:** Wybierz tę opcję (która jest domyślnie wyczyszczona), aby program Visual Studio utworzył lokalne repozytorium Git podczas tworzenia rozwiązania. Jeśli nie widzisz tej opcji, uruchom instalator programu Visual Studio i dodaj rozszerzenie **Git dla systemu Windows** i **GitHub dla programu Visual Studio** na karcie Poszczególne **składniki** w obszarze **Narzędzia kodu**.

1. Po chwili visual studio monituje o okno dialogowe z informacją **Ten projekt wymaga pakietów zewnętrznych** (pokazano poniżej). To okno dialogowe pojawia się, ponieważ szablon zawiera plik *requirements.txt* odwołujący się do najnowszego pakietu Django 1.x. (Wybierz **pokaż wymagane pakiety,** aby zobaczyć dokładne zależności).

    ![Monit mówiąc, że projekt wymaga pakietów zewnętrznych](media/django/step01-requirements-prompt-install-myself.png)

1. Wybierz opcję **zainstaluję je samodzielnie**. Wkrótce utworzysz środowisko wirtualne, aby upewnić się, że jest wykluczone z kontroli źródła. (Środowisko zawsze można utworzyć na podstawie *pliku requirements.txt).*

## <a name="step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository"></a>Krok 1-2: Zbadaj kontrolki Git i opublikuj w zdalnym repozytorium

Ponieważ w oknie dialogowym **Nowy projekt** **wybrano repozytorium Utwórz nowy Git,** projekt jest już zatwierdzony do kontroli źródła lokalnego zaraz po zakończeniu procesu tworzenia. W tym kroku zapoznajesz się z formantami Git programu Visual Studio i oknem **Eksploratora zespołu,** w którym pracujesz z kontrolą źródła.

1. Sprawdź kontrolki Git w dolnym rogu okna głównego programu Visual Studio. Od lewej do prawej te formanty pokazują nieuprawione zatwierdzenia, niezatwierdzone zmiany, nazwę repozytorium i bieżącą gałąź:

    ![Formanty git w oknie programu Visual Studio](media/django/step01-git-controls.png)

    > [!Note]
    > Jeśli nie wybierzesz **repozytorium Utwórz nowy Git** w oknie dialogowym **Nowy projekt,** formanty Git pokażą tylko polecenie **dodaj do źródła,** które tworzy lokalne repozytorium.
    >
    > ![Dodaj do kontroli źródła pojawia się w programie Visual Studio, jeśli nie utworzono repozytorium](media/django/step01-git-add-to-source-control.png)

1. Wybierz przycisk zmiany, a program Visual Studio otworzy okno **Eksploratora zespołu** na stronie **Zmiany.** Ponieważ nowo utworzony projekt jest już zobowiązana do kontroli źródła automatycznie, nie widać żadnych oczekujących zmian.

    ![Okno Eksploratora zespołu na stronie Zmiany](media/django/step01-team-explorer-changes.png)

1. Na pasku stanu programu Visual Studio wybierz przycisk unpushed commits (strzałka w górę z **2**), aby otworzyć stronę **Synchronizacja** w **Eksploratorze zespołu**. Ponieważ masz tylko repozytorium lokalne, strona udostępnia łatwe opcje publikowania repozytorium w różnych repozytoriach zdalnych.

    ![Okno Eksploratora zespołu z dostępnymi opcjami repozytorium Git dla kontroli źródła](media/django/step01-team-explorer.png)

    Możesz wybrać dowolną usługę dla własnych projektów. W tym samouczku pokazano użycie usługi GitHub, w której wypełniony przykładowy kod samouczka jest obsługiwany w repozytorium [Microsoft/python-sample-vs-learning-django.](https://github.com/Microsoft/python-sample-vs-learning-django)

1. Po wybraniu dowolnego z **formantów Publikowania,** **Team Explorer** monituje o więcej informacji. Na przykład podczas publikowania próbki dla tego samouczka, repozytorium trzeba było utworzyć najpierw, w którym to przypadku opcja **Wypychanie do repozytorium zdalnego** została użyta z adresem URL repozytorium.

    ![Okno Eksploratora zespołu do wypychania do istniejącego repozytorium zdalnego](media/django/step01-push-to-github.png)

    Jeśli nie masz istniejącego repozytorium, **opcje publikowania w usłudze GitHub** i **wypychania do usługi Azure DevOps** umożliwiają utworzenie go bezpośrednio z poziomu programu Visual Studio.

1. Podczas pracy nad tym samouczkiem, dostać się do nawyku okresowego używania formantów w programie Visual Studio do zatwierdzania i wypychania zmian. Ten samouczek przypomina w odpowiednich punktach.

> [!Tip]
> Aby szybko poruszać się w **Eksploratorze zespołu,** wybierz nagłówek (który **odczytuje zmiany** lub **Wypychaj** powyższe obrazy), aby wyświetlić wyskakujące menu dostępnych stron.

### <a name="question-what-are-some-advantages-of-using-source-control-from-the-beginning-of-a-project"></a>Pytanie: Jakie są pewne zalety korzystania z kontroli źródła od początku projektu?

Odpowiedź: Przede wszystkim przy użyciu kontroli źródła od początku, zwłaszcza jeśli używasz również zdalnego repozytorium, zapewnia regularne tworzenie kopii zapasowych poza witryną projektu. W przeciwieństwie do utrzymania projektu tylko w lokalnym systemie plików, kontrola źródła zapewnia również pełną historię zmian i łatwą możliwość ponownego ponownego pojedynczego pliku lub całego projektu do poprzedniego stanu. Ta historia zmian pomaga określić przyczynę regresji (błędy testu). Ponadto kontrola źródła jest niezbędna, jeśli wiele osób pracuje nad projektem, ponieważ zarządza nadpisywami i zapewnia rozwiązywanie konfliktów. Na koniec kontrola źródła, która jest zasadniczo formą automatyzacji, ustawia cię dobrze do automatyzacji kompilacji, testowania i zarządzania wydaniami. To naprawdę pierwszy krok w użyciu DevOps dla projektu, a ponieważ bariery wejścia są tak niskie, naprawdę nie ma powodu, aby nie używać kontroli źródła od początku.

Aby uzyskać dalsze dyskusje na temat kontroli źródła jako automatyzacji, zobacz [Źródło prawdy: Rola repozytoriów w DevOps](https://msdn.microsoft.com/magazine/mt763232), artykuł w MSDN Magazine napisany dla aplikacji mobilnych, który dotyczy również aplikacji internetowych.

### <a name="question-can-i-prevent-visual-studio-from-auto-committing-a-new-project"></a>Pytanie: Czy mogę uniemożliwić programowi Visual Studio automatyczne zatwierdzanie nowego projektu?

Odpowiedź: Tak. Aby wyłączyć automatyczne zatwierdzanie, przejdź do strony **Ustawienia** w **Eksploratorze zespołu**, wybierz pozycję**Ustawienia globalne** **Git** > , wyczyść opcję z etykietą **Zatwierdzanie zmian po domyślnym scaleniu**, a następnie wybierz pozycję **Aktualizuj**.

## <a name="step-1-3-create-the-virtual-environment-and-exclude-it-from-source-control"></a>Krok 1-3: Tworzenie środowiska wirtualnego i wykluczanie go z kontroli źródła

Teraz, po skonfigurowaniu kontroli źródła dla projektu, można utworzyć środowisko wirtualne, które zawiera niezbędne pakiety Django dla projektu. Następnie można użyć **Eksploratora zespołu,** aby wykluczyć folder środowiska z kontroli źródła.

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy węzeł **Środowiska języka Python** i wybierz polecenie Dodaj środowisko **wirtualne**.

    ![Polecenie Dodaj środowisko wirtualne w Eksploratorze rozwiązań](media/django/step01-add-virtual-environment-command.png)

1. Zostanie wyświetlone okno dialogowe **Dodaj środowisko wirtualne** z komunikatem **"Znaleźliśmy plik requirements.txt".** Ten komunikat wskazuje, że program Visual Studio używa tego pliku do skonfigurowania środowiska wirtualnego.

    ![Dodawanie okna dialogowego środowiska wirtualnego z komunikatem requirements.txt](media/django/step01-add-virtual-environment-found-requirements.png)

1. Wybierz **pozycję Utwórz,** aby zaakceptować wartości domyślne. (Można zmienić nazwę środowiska wirtualnego, jeśli chcesz, który po prostu zmienia `env` nazwę jego podfolder, ale jest standardową konwencją.)

1. Zgoda na uprawnienia administratora, jeśli zostanie wyświetlony monit, a następnie ciągnij przez kilka minut, podczas gdy Visual Studio pobiera i instaluje pakiety, co dla Django oznacza rozszerzenie kilku tysięcy plików w około tylu podfolderach! Postęp można zobaczyć w oknie **Dane wyjściowe** programu Visual Studio. Podczas oczekiwania zastanów się nad sekcjami Pytania, które następują po tym.

1. W formancie Git programu Visual Studio (na pasku stanu) wybierz wskaźnik zmian (który pokazuje **99&#42;), **który otwiera stronę **Zmiany** w **Eksploratorze zespołu.**

    Tworzenie środowiska wirtualnego przyniosło tysiące zmian, ale nie trzeba uwzględniać żadnego z nich w kontroli źródła, ponieważ użytkownik (lub ktokolwiek inny klonuje projekt) zawsze może odtworzyć środowisko z *pliku requirements.txt*.

    Aby wykluczyć środowisko wirtualne, kliknij prawym przyciskiem myszy folder **env** i wybierz polecenie **Ignoruj te elementy lokalne**.

    ![Ignorowanie środowiska wirtualnego w zmianach kontroli źródła](media/django/step01-ignore-local-items.png)

1. Po wyłączeniu środowiska wirtualnego jedynymi pozostałymi zmianami są plik projektu i *.gitignore*. Plik *.gitignore* zawiera dodany wpis dla folderu środowiska wirtualnego. Możesz kliknąć dwukrotnie plik, aby wyświetlić różnice.

1. Wprowadź komunikat o zatwierdzeniu i wybierz przycisk **Zatwierdz wszystko,** a następnie naciśnij zatwierdzenia do zdalnego repozytorium, jeśli chcesz.

### <a name="question-why-do-i-want-to-create-a-virtual-environment"></a>Pytanie: Dlaczego chcę utworzyć środowisko wirtualne?

Odpowiedź: Środowisko wirtualne to świetny sposób na wyizolowanie dokładnych zależności aplikacji. Taka izolacja pozwala uniknąć konfliktów w globalnym środowisku Języka Python i ułatwia zarówno testowanie, jak i współpracę. Z biegiem czasu, podczas tworzenia aplikacji, niezmiennie przynosisz wiele przydatnych pakietów Pythona. Przechowując pakiety w środowisku wirtualnym specyficznym dla projektu, można łatwo zaktualizować plik *requirements.txt* projektu, który opisuje to środowisko, które jest zawarte w kontroli źródła. Gdy projekt jest kopiowany do innych komputerów, w tym serwerów kompilacji, serwerów wdrożeniowych i innych komputerów deweloperskich, można łatwo odtworzyć środowisko przy użyciu tylko *pliku requirements.txt* (dlatego środowisko nie musi znajdować się pod kontrolą źródła). Aby uzyskać więcej informacji, zobacz [Używanie środowisk wirtualnych](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

### <a name="question-how-do-i-remove-a-virtual-environment-thats-already-committed-to-source-control"></a>Pytanie: Jak usunąć środowisko wirtualne, które jest już zaangażowane w kontrolę źródła?

Odpowiedź: Najpierw edytuj plik *.gitignore,* aby wykluczyć folder: znajdź sekcję na końcu z komentarzem `# Python Tools for Visual Studio (PTVS)` i `/BasicProject/env`dodaj nowy wiersz dla folderu środowiska wirtualnego, na przykład . (Ponieważ program Visual Studio nie pokazuje pliku w **Eksploratorze rozwiązań,** otwórz go bezpośrednio za pomocą polecenia menu > **Otwórz** > **File** **plik.** Możesz również otworzyć plik z **Eksploratora zespołu**: na stronie **Ustawienia** wybierz **pozycję Ustawienia repozytorium**, przejdź do sekcji **Ignoruj & atrybuty,** a następnie wybierz łącze **Edytuj** obok **.gitignore**.)

Po drugie, otwórz okno polecenia, przejdź do folderu takiego jak *BasicProject,* `git rm -r env`który zawiera folder środowiska wirtualnego, taki jak *env,* i uruchom . Następnie zaobenduj te`git commit -m 'Remove venv'`zmiany z wiersza polecenia ( ) lub zaobenduj na stronie **Zmiany** **Eksploratora zespołu**.

## <a name="step-1-4-examine-the-boilerplate-code"></a>Krok 1-4: Zbadaj kod płyty kotłowej

Po zakończeniu tworzenia projektu należy sprawdzić kod projektu Django (który jest ponownie taki `django-admin startproject <project_name>`sam, jak generowany przez polecenie CLI).

1. W katalogu głównym projektu jest *manage.py*, narzędzie administracyjne wiersza polecenia Django, które visual studio automatycznie ustawia jako plik startowy projektu. Narzędzie jest uruchamiane w `python manage.py <command> [options]`wierszu polecenia za pomocą programu . W przypadku typowych zadań Django program Visual Studio udostępnia wygodne polecenia menu. Kliknij prawym przyciskiem myszy projekt w **Eksploratorze rozwiązań** i wybierz **pozycję Python,** aby wyświetlić listę. Niektóre z tych poleceń można napotkać w trakcie tego samouczka.

    ![Polecenia Django w menu kontekstowym projektu Pythona](media/django/step01-django-commands-menu.png)

2. W projekcie jest folder o nazwie taki sam jak projekt. Zawiera podstawowe pliki projektu Django:

   - *__init.py*: pusty plik, który informuje Pythona, że ten folder jest pakietem Pythona.
   - *wsgi.py*: punkt wejścia dla serwerów sieci web zgodnych z WSGI do obsługi projektu. Zazwyczaj pozostawiasz ten plik w stanie takim, w jakim udostępnia on haki dla produkcyjnych serwerów sieci web.
   - *settings.py*: zawiera ustawienia projektu Django, które modyfikujesz w trakcie tworzenia aplikacji internetowej.
   - *urls.py*: zawiera spis treści projektu Django, który również modyfikujesz w trakcie rozwoju.

     ![Pliki projektu Django w Eksploratorze rozwiązań](media/django/step01-django-project-in-solution-explorer.png)

3. Jak wspomniano wcześniej, szablon programu Visual Studio dodaje również plik *requirements.txt* do projektu, określając zależność pakietu Django. Obecność tego pliku jest tym, co zachęca do tworzenia środowiska wirtualnego podczas pierwszego tworzenia projektu.

### <a name="question-can-visual-studio-generate-a-requirementstxt-file-from-a-virtual-environment-after-i-install-other-packages"></a>Pytanie: Czy program Visual Studio może generować plik requirements.txt ze środowiska wirtualnego po zainstalowaniu innych pakietów?

Odpowiedź: Tak. Rozwiń węzeł **Środowiska języka Python,** kliknij prawym przyciskiem myszy środowisko wirtualne i wybierz polecenie **Generuj polecenie requirements.txt.** Dobrze jest używać tego polecenia okresowo podczas modyfikowania środowiska i zatwierdzania zmian *w requirements.txt* do kontroli źródła wraz z innymi zmianami kodu, które zależą od tego środowiska. Jeśli konfigurujesz ciągłą integrację na serwerze kompilacji, należy wygenerować plik i zatwierdzić zmiany przy każdym modyfikowaniu środowiska.

## <a name="step-1-5-run-the-empty-django-project"></a>Krok 1-5: Uruchom pusty projekt Django

1. W programie Visual Studio wybierz opcję **Debugowanie** > **start debugowania** **(F5)** lub użyj przycisku **Serwera sieci Web** na pasku narzędzi (widoczna przeglądarka może się różnić):

    ![Uruchamianie przycisku paska narzędzi serwera sieci Web w programie Visual Studio](media/django/run-web-server-toolbar-button.png)

1. Uruchomienie serwera oznacza uruchomienie `manage.py runserver <port>`polecenia , które uruchamia wbudowany serwer deweloperski Django. Jeśli program Visual Studio **mówi, że nie można uruchomić debugera** z komunikatem o braku pliku startowego, kliknij prawym przyciskiem myszy **manage.py** w **Eksploratorze rozwiązań** i wybierz pozycję **Ustaw jako plik startowy**.

1. Po uruchomieniu serwera zostanie wyświetlone otwarte okno konsoli, w którym również jest wyświetlany dziennik serwera. Program Visual Studio automatycznie `http://localhost:<port>`otwiera przeglądarkę na program . Ponieważ projekt Django nie ma aplikacji, Django pokazuje tylko domyślną stronę, aby potwierdzić, że to, co masz do tej pory, działa dobrze:

    ![Domyślny widok projektu Django](media/django/step01-first-run-success.png)

1. Po zakończeniu zatrzymaj serwer, zamykając okno konsoli lub używając polecenia **Debugowania** > **zatrzymaj debugowanie** w programie Visual Studio.

### <a name="question-is-django-a-web-server-as-well-as-a-framework"></a>Pytanie: Czy Django jest serwerem www, a także platformą?

Odpowiedź: Tak i nie. Django ma wbudowany serwer www, który jest używany do celów programisty. Ten serwer sieci web jest to, co pobiera używane podczas uruchamiania aplikacji sieci web lokalnie, takich jak podczas debugowania w programie Visual Studio. Jednak po wdrożeniu na hoście Django używa serwera sieci web hosta. Moduł *wsgi.py* w projekcie Django zajmuje się podłączaniem do serwerów produkcyjnych.

### <a name="question-whats-the-difference-between-using-the-debug-menu-commands-and-the-server-commands-on-the-projects-python-submenu"></a>Pytanie: Jaka jest różnica między używaniem poleceń menu debugowania a poleceniami serwera w podmenu Python projektu?

Odpowiedź: Oprócz poleceń menu **debugowania** i przycisków paska narzędzi można również **Python** > uruchomić serwer za pomocą poleceń**serwera uruchamiania** **języka Python** > lub Python**Run** w menu kontekstowym projektu. Oba polecenia otwierają okno konsoli, w którym jest widoczny lokalny adres URL (localhost:port) dla uruchomionego serwera. Należy jednak ręcznie otworzyć przeglądarkę z tym adresem URL, a uruchomienie serwera debugowania nie uruchamia automatycznie debugera programu Visual Studio. Debugera można dołączyć do uruchomionego procesu później, jeśli chcesz, za pomocą polecenia > **Debugowanie dołączania do procesu.** **Debug**

## <a name="next-steps"></a>Następne kroki

W tym momencie podstawowy projekt Django nie zawiera żadnych aplikacji. Utwórz aplikację w następnym kroku. Ponieważ zazwyczaj pracujesz z aplikacjami Django bardziej niż projekt Django, nie musisz wiedzieć o tym więcej o plikach z kotłem.

> [!div class="nextstepaction"]
> [Tworzenie aplikacji Django z widokami i szablonami stron](learn-django-in-visual-studio-step-02-create-an-app.md)

## <a name="go-deeper"></a>Głębiej

- Kod projektu Django: [Pisanie pierwszej aplikacji Django, część 1](https://docs.djangoproject.com/en/2.0/intro/tutorial01/) (docs.djangoproject.com)
- Narzędzie administracyjne: [django-admin i manage.py](https://docs.djangoproject.com/en/2.0/ref/django-admin/) (docs.djangoproject.com)
- Kod źródłowy samouczka na GitHub: [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)

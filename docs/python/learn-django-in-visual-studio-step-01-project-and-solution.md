---
title: Poznaj samouczek Django w programie Visual Studio, krok 1, podstawy Django
titleSuffix: ''
description: Przewodnik podstawy Django w kontekście projektów programu Visual Studio, demonstrując pomocy technicznej programu Visual Studio udostępnia do tworzenia aplikacji Django.
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62962261"
---
# <a name="tutorial-get-started-with-the-django-web-framework-in-visual-studio"></a>Samouczek: Wprowadzenie do struktury sieci web Django w programie Visual Studio

[Django](https://www.djangoproject.com/) jest przeznaczony do tworzenia aplikacji internetowych szybki, bezpieczny i skalowalny struktura języka Python wysokiego poziomu. W tym samouczku przedstawiono framework Django w kontekście szablonów projektu, które program Visual Studio udostępnia uprościć tworzenie aplikacji sieci web opartych na Django.

W tym samouczku dowiesz się, jak:

> [!div class="checklist"]
> - Tworzenie podstawowego projektu Django w repozytorium Git przy użyciu szablonu "Pusty projekt sieci Web Django" (krok 1)
> - Tworzenie aplikacji Django z jednej strony i renderowania tej strony, przy użyciu szablonu (krok 2)
> - Obsługa plików statycznych, dodawanie stron i użyć szablonu dziedziczenia (krok 3)
> - Szablon projektu sieci Web Django służy do tworzenia aplikacji z wieloma stronami i elastyczne środowisko (krok 4)
> - Uwierzytelnianie użytkowników (krok 5)
> - Szablon projektu sieci Web Django sond służy do tworzenia aplikacji używającej modeli, migracje baz danych i dostosowania interfejsu administracyjnego (krok 6)

## <a name="prerequisites"></a>Wymagania wstępne

- Visual Studio 2017 lub później na Windows przy użyciu następujących opcji:
  - **Programowania w języku Python** obciążenia (**obciążenia** karty w oknie Instalatora). Aby uzyskać instrukcje, zobacz [Instalowanie obsługi języka Python w programie Visual Studio](installing-python-support-in-visual-studio.md).
  - **Git dla Windows** i **rozszerzeniu GitHub Extension for Visual Studio** na **poszczególne składniki** karcie **kodu narzędzia**.

Szablony projektów Django są również dołączone do wszystkich wcześniejszych wersjach narzędzi Python Tools for Visual Studio, chociaż szczegóły mogą się różnić od co zostało omówione w tym samouczku (szczególnie różni się ze starszymi wersjami struktury Django).

Programowanie w języku Python nie jest obecnie obsługiwana w programie Visual Studio dla komputerów Mac. Na komputerach Mac i Linux, należy użyć [rozszerzenie języka Python w programie Visual Studio Code](https://code.visualstudio.com/docs/python/python-tutorial).

### <a name="visual-studio-projects-and-django-projects"></a>"Visual Studio" i "Django projektów"

W terminologii Django "Projekt Django" składa się z kilku plików konfiguracji na poziomie witryny, wraz z co najmniej jeden "aplikacje" wdrażane w ramach hosta sieci web, aby utworzyć aplikację sieci web o pełny. Projekt Django może zawierać wiele aplikacji, a ta sama aplikacja może znajdować się w wielu projektach Django.

Projekt programu Visual Studio ze swojej strony może zawierać projekt Django wraz z wieloma aplikacjami. Dla uproszczenia, należy zawsze wtedy, gdy w tym samouczku odnosi się do właśnie to "Projekt" odwołuje się do projektu programu Visual Studio. Gdy odwołuje się do części "Django projektu" aplikacja sieci web, używa "Django projektu" specjalnie.

W trakcie tego samouczka utworzysz jedno rozwiązanie Visual Studio zawierający trzy oddzielne projekty Django, z których każdy zawiera pojedynczą aplikację Django. Przechowując projektów w tym samym rozwiązaniu, można łatwo przełączać i z powrotem między różnych plików do porównania.

## <a name="step-1-1-create-a-visual-studio-project-and-solution"></a>Krok 1-1: Tworzenie projektu programu Visual Studio i rozwiązania

Podczas pracy z Django z wiersza polecenia, zwykle Uruchom projekt, uruchamiając `django-admin startproject <project_name>` polecenia. W programie Visual Studio przy użyciu szablonu "Pusty projekt sieci Web Django" zawiera tę samą strukturę, w ramach projektu programu Visual Studio i rozwiązania.

1. W programie Visual Studio, wybierz **pliku** > **New** > **projektu**, wyszukaj frazę "Django" i wybierz **pusty projekt sieci Web Django**  szablonu. (Szablon znajduje się również w obszarze **Python** > **Web** na liście po lewej stronie.)

    ![Okno dialogowe nowego projektu w programie Visual Studio dla pustego projektu sieci Web Django](media/django/step01-new-blank-project.png)

1. W polach w dolnej części okna dialogowego wprowadź następujące informacje (jak pokazano na poprzednim rysunku), a następnie wybierz **OK**:

    - **Nazwa**: Ustaw nazwę projektu programu Visual Studio, aby **BasicProject**. Ta nazwa jest także używana dla projektu Django.
    - **Lokalizacja**: Określ lokalizację, w której chcesz utworzyć rozwiązanie programu Visual Studio i projektu.
    - **Rozwiązanie**: pozostaw ten formant ustawioną wartość domyślną **Utwórz nowe rozwiązanie** opcji.
    - **Nazwa rozwiązania**: Ustaw **LearningDjango**, który jest odpowiedni do rozwiązania jako kontener dla wielu projektów w ramach tego samouczka.
    - **Utwórz katalog dla rozwiązania**: Pozostaw zestawu (ustawienie domyślne).
    - **Utwórz nowe repozytorium Git**: Wybierz tę opcję, (czyli wyczyść domyślnie), tak aby program Visual Studio tworzy lokalne repozytorium Git, podczas tworzenia rozwiązania. Jeśli nie widzisz tej opcji, uruchom Instalatora programu Visual Studio i Dodaj **Git dla Windows** i **rozszerzeniu GitHub Extension for Visual Studio** na **poszczególne składniki** kartę w obszarze **kodu narzędzia**.

1. Po chwili Visual Studio wyświetli monit z informacją o tym okna dialogowego **ten projekt wymaga pakiety zewnętrzne** (pokazana poniżej). To okno dialogowe pojawia się, ponieważ szablon zawiera *requirements.txt* plik odwołuje się do najnowszego pakietu 1.x Django. (Wybierz **Pokaż wymagane pakiety** Aby wyświetlić zależności dokładną.)

    ![Monituj powiedzenie, że projekt wymaga pakiety zewnętrzne](media/django/step01-requirements-prompt-install-myself.png)

1. Wybierz opcję **I zainstaluje je samodzielnie**. Utworzysz środowisko wirtualne wkrótce, aby upewnić się, że jest ona wykluczana z kontroli źródła. (Zawsze można tworzyć środowiska na podstawie *requirements.txt*.)

## <a name="step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository"></a>Krok 1 – 2: Sprawdź kontrolki Git i opublikuj do zdalnego repozytorium

Ponieważ wybrano **Utwórz nowe repozytorium Git** w **nowy projekt** okno dialogowe, projekt jest już zaangażowana w lokalnej kontroli źródła zaraz po zakończeniu procesu tworzenia. W tym kroku należy zapoznać się z kontrolek Git programu Visual Studio i **Team Explorer** okna, w którym pracujesz z kontrolą źródła.

1. Sprawdź formanty Git na dolnym rogu okna głównego programu Visual Studio. Od lewej do prawej te kontrolki wyświetlają niewypchniętych zatwierdzeń, niezatwierdzone zmiany, nazwę repozytorium i gałąź bieżącą:

    ![Git formantów w oknie programu Visual Studio](media/django/step01-git-controls.png)

    > [!Note]
    > Jeśli nie zaznaczysz **Utwórz nowe repozytorium Git** w **nowy projekt** oknie dialogowym usługi Git kontrolek zostaną wyświetlone tylko **Dodaj do kontroli źródła** polecenia, który tworzy lokalną repozytorium.
    >
    > ![Dodaj do kontroli źródła jest wyświetlany w programie Visual Studio, jeśli nie utworzono repozytorium](media/django/step01-git-add-to-source-control.png)

1. Wybierz przycisk zmiany, a Visual Studio otwiera jego **Team Explorer** okno na **zmiany** strony. Ponieważ nowo utworzonego projektu jest już zatwierdzone do kontroli źródła automatycznie, nie widać wszystkie oczekujące zmiany.

    ![Okno Eksploratora zespołu na stronie zmiany](media/django/step01-team-explorer-changes.png)

1. Na pasku stanu programu Visual Studio, wybierz przycisk niewypchniętych zatwierdzeń (strzałkę w górę o **2**) aby otworzyć **synchronizacji** strony w **Team Explorer**. Ponieważ lokalne repozytorium, na stronie jest prostych opcji, aby opublikować repozytorium w różnych repozytoria zdalne.

    ![Team Explorer okna pokazujący dostępne Git opcji repozytorium dla kontroli źródła](media/django/step01-team-explorer.png)

    Możesz niezależnie od usługi, w której ma we własnych projektach. W tym samouczku pokazano sposób użycia usługi GitHub, w której ukończone przykładowego kodu na potrzeby tego samouczka jest zachowywany w [Microsoft/python — przykładowe vs uczenia — django](https://github.com/Microsoft/python-sample-vs-learning-django) repozytorium.

1. Po wybraniu dowolnego z **Publikuj** kontrolek **Team Explorer** wyświetli monit o podanie informacji. Na przykład podczas publikowania próbki na potrzeby tego samouczka, samo repozytorium musieli najpierw należy utworzyć, w którym to przypadku **wypychania do repozytorium zdalnego** użyto opcji za pomocą adresu URL repozytorium.

    ![Okno Eksploratora zespołu do wypychania do istniejącego repozytorium zdalnego](media/django/step01-push-to-github.png)

    Jeśli masz istniejące repozytorium, **publikowanie w usłudze GitHub** i **Wypychanie do usługi Azure DevOps** opcje pozwalają utworzyć bezpośrednio z poziomu programu Visual Studio.

1. Podczas pracy z tym samouczkiem Uzyskaj w celu przejrzenia okresowo za pomocą formantów w programie Visual Studio można zatwierdzać i wypychać zmiany. W tym samouczku przypomina o tym, w odpowiednich miejscach.

> [!Tip]
> Szybko poruszać się po **Team Explorer**, wybierz nagłówek (który odczytuje **zmiany** lub **wypychania** w obrazach powyżej) aby wyświetlić menu podręcznego dostępnych stron.

### <a name="question-what-are-some-advantages-of-using-source-control-from-the-beginning-of-a-project"></a>Pytanie: Jakie są niektóre korzyści wynikające z używania kontroli źródła, od początku projektu?

Odpowiedź: Przede wszystkim przy użyciu kontroli źródła od samego początku, zwłaszcza, jeśli używasz zdalnego repozytorium zawiera kopię zapasową regularne poza siedzibą firmy, projektu. W przeciwieństwie do obsługi projektu tylko na lokalny system plików, kontroli źródła także zmienić pełną historię zmian i łatwe możliwość przywracania pojedynczego pliku lub całego projektu do poprzedniego stanu. Aby zmian historii pomaga ustalić przyczynę regresji (niepowodzeń testów). Ponadto kontroli źródła jest pracy wielu osób na projekt, która zarządza zastępuje i zapewnia Rozwiązywanie konfliktów. Na koniec kontroli źródła, która jest całkowicie formę automatyzacji, konfiguruje możesz również do automatyzacji kompilacji, testowania i rozwiązania release management. Tak naprawdę jest pierwszym krokiem przy użyciu metodyki DevOps dla projektu, a ponieważ barier wejścia znajdują się więc niski, to naprawdę bez powodu, aby nie używać kontroli źródła, od początku.

Aby uzyskać dalsze dyskusji na temat kontroli źródła jako usługi automation, zobacz [źródło prawdziwych danych: Rola repozytoriów w infrastrukturze DevOps](https://msdn.microsoft.com/magazine/mt763232), artykuł w MSDN Magazine przeznaczony dla aplikacji mobilnych, który ma również zastosowanie do aplikacji sieci web.

### <a name="question-can-i-prevent-visual-studio-from-auto-committing-a-new-project"></a>Pytanie: Można zapobiec programu Visual Studio automatyczne zatwierdzanie nowego projektu?

Odpowiedź: Tak. Aby wyłączyć automatyczne zatwierdzenie, przejdź do **ustawienia** strony w **Team Explorer**, wybierz opcję **Git** > **ustawienia globalne**, wyczyść Opcja etykietą **Zatwierdź zmiany po scaleniu domyślnie**, a następnie wybierz **aktualizacji**.

## <a name="step-1-3-create-the-virtual-environment-and-exclude-it-from-source-control"></a>Krok 1-3: Utwórz środowisko wirtualne i wykluczenie go z kontroli źródła

Teraz, gdy skonfigurowano kontroli źródła dla projektu, można utworzyć środowiska wirtualnego, który zawiera niezbędne pakiety Django dla projektu. Następnie można użyć **Team Explorer** Aby wykluczyć folder środowiska z poziomu kontroli źródła.

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **środowiska Python** a następnie wybierz węzeł **Dodawanie środowiska wirtualnego**.

    ![Dodaj polecenie środowisko wirtualne w Eksploratorze rozwiązań](media/django/step01-add-virtual-environment-command.png)

1. **Dodawanie środowiska wirtualnego** zostanie wyświetlone okno dialogowe z komunikat **znaleźliśmy pliku requirements.txt.** Ten komunikat oznacza, że program Visual Studio używa tego pliku do skonfigurowania środowiska wirtualnego.

    ![Dodaj okno środowiska wirtualnego z komunikatem w pliku requirements.txt](media/django/step01-add-virtual-environment-found-requirements.png)

1. Wybierz **Utwórz** aby zaakceptować wartości domyślne. (Można zmienić nazwę środowiska wirtualnego, jeśli chcesz, który po prostu zmienia nazwę jej podfolder, ale `env` jest standardowej konwencji.)

1. Wyrazić zgodę na uprawnienia administratora, jeśli zostanie wyświetlony monit, a następnie o cierpliwość przez kilka minut, podczas gdy program Visual Studio pobiera i instaluje pakiety, oznacza to, aby uzyskać Django rozwijanie kilka tysięcy plików o tyle podfoldery! Możesz zobaczyć postępy w programie Visual Studio **dane wyjściowe** okna. Czekając, spędzać w kolejnych sekcjach pytanie.

1. Dla kontrolek repozytorium Git usługi Visual Studio (na pasku stanu), wybierz wskaźnik zmian (pokazujący **99&#42;**) co spowoduje otwarcie **zmiany** strony w **Team Explorer**.

    Tworzenie środowiska wirtualnego odwoływanych tysięcy zmian, ale nie trzeba uwzględnić któryś z nich w kontroli źródła, ponieważ użytkownik (lub każdy w przeciwnym razie klonowanie projektu) zawsze można odtworzyć środowisko z *requirements.txt* .

    Aby wykluczyć środowiska wirtualnego, kliknij prawym przyciskiem myszy **env** i wybierz polecenie **ignorować te elementy lokalne**.

    ![Ignorowanie środowiska wirtualnego w zmian kontroli źródła](media/django/step01-ignore-local-items.png)

1. Po wykluczeniu środowiska wirtualnego, tylko pozostałe zmiany są w pliku projektu i *.gitignore*. *.Gitignore* zawierający dodano wpis dla folderu środowiska wirtualnego. Możesz kliknąć dwukrotnie plik, aby zobaczyć diff.

1. Wprowadź wiadomość dotyczącą zatwierdzenia, a następnie wybierz pozycję **Zatwierdź wszystko** przycisk, a następnie, jeśli chcesz wypychanie zatwierdzeń do repozytorium zdalnego.

### <a name="question-why-do-i-want-to-create-a-virtual-environment"></a>Pytanie: Dlaczego chcesz utworzyć środowisko wirtualne?

Odpowiedź: Środowisko wirtualne jest doskonałym sposobem na izolowanie dokładnie zależności aplikacji. Tej izolacji pozwala uniknąć konfliktów w środowisku Python globalnym i ułatwia testowanie i współpracy. Wraz z upływem czasu podczas opracowywania aplikacji, niezmiennie wprowadzanych wiele pomocnych pakiety języka Python. Przechowując pakietów w środowisku wirtualnym specyficzne dla projektu, można łatwo zaktualizować projektu *requirements.txt* pliku, który opisuje środowisku, w którym znajduje się w kontroli źródła. Gdy projekt jest kopiowana do innych komputerów, serwerów kompilacji, wdrażania serwerów i innych komputerach rozwoju, w tym jest łatwo odtworzyć środowiskiem za pomocą tylko *requirements.txt* (co jest dlaczego środowiska nie musi znajdować się w kontroli źródła). Aby uzyskać więcej informacji, zobacz [korzystanie ze środowisk wirtualnych](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

### <a name="question-how-do-i-remove-a-virtual-environment-thats-already-committed-to-source-control"></a>Pytanie: Jak usunąć środowisko wirtualne jest została już przydzielona do kontroli źródła?

Odpowiedź: Po pierwsze Przeprowadź edycję swoje *.gitignore* plik, aby wykluczyć folder: Znajdź sekcję na końcu z komentarzem `# Python Tools for Visual Studio (PTVS)` i Dodaj nowy wiersz do folderu, w środowisku wirtualnym, takie jak `/BasicProject/env`. (Ponieważ program Visual Studio nie wyświetla plik w **Eksploratora rozwiązań**, otwórz je bezpośrednio przy użyciu **pliku** > **Otwórz**  >   **Plik** polecenia menu. Możesz również otworzyć plik z **Team Explorer**: na **ustawienia** wybierz opcję **ustawienia repozytorium**, przejdź do **Ignoruj & atrybutów plików** sekcji, a następnie wybierz **Edytuj** łącze obok **.gitignore**.)

Po drugie, Otwórz okno polecenia, przejdź do folderu, takich jak *BasicProject* zawierający takie jak folder w środowisku wirtualnym *env*i uruchom `git rm -r env`. Następnie należy zatwierdzić te zmiany z wiersza polecenia (`git commit -m 'Remove venv'`) lub czy zatwierdzić z **zmiany** strony **Team Explorer**.

## <a name="step-1-4-examine-the-boilerplate-code"></a>Krok 1-4: Badanie kodu standardowy

Po zakończeniu tworzenia projektu, należy zbadać standardowy kod projektu Django (czyli ponownie, taka sama jak wartość generowanych przez polecenia interfejsu wiersza polecenia `django-admin startproject <project_name>`).

1. W projekcie jest głównym *manage.py*, Django narzędzie wiersza polecenia administracyjne programu Visual Studio automatycznie ustawia jako plik startowy projektu. Uruchom narzędzie przy użyciu wiersza polecenia `python manage.py <command> [options]`. Do wykonywania typowych zadań Django Visual Studio zapewnia wygodne poleceń. Kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierz **Python** Aby wyświetlić listę. Niektóre z tych poleceń w ramach tego samouczka wystąpią.

    ![Polecenia Django w języku Python projektu menu kontekstowe](media/django/step01-django-commands-menu.png)

2. W projekcie jest folder o nazwie taka sama jak projekt. Zawiera podstawowe pliki projektu Django:

   - *__init.PY*: pusty plik Python informuje, czy ten folder jest pakiet języka Python.
   - *wsgi.PY*: punkt wejścia dla zgodnego z WSGI serwerów sieci web do obsługi projektu. Zazwyczaj pozostaw ten plik jako — jest jak udostępnia punkty zaczepienia do produkcyjnych serwerów sieci web.
   - *Settings.PY*: zawiera ustawienia dla projektu Django, co możesz zmodyfikować w trakcie opracowywania aplikacji sieci web.
   - *URLs.PY*: zawiera spis treści dla projektu Django, która jest modyfikowana w trakcie opracowywania.

     ![Django pliki projektu w Eksploratorze rozwiązań](media/django/step01-django-project-in-solution-explorer.png)

3. Jak wspomniano wcześniej, szablon programu Visual Studio dodaje również *requirements.txt* plik do projektu określenie Django zależności pakietów. Obecność tego pliku to, co zachęca do tworzenia środowiska wirtualnego, tworząc po raz pierwszy projekt.

### <a name="question-can-visual-studio-generate-a-requirementstxt-file-from-a-virtual-environment-after-i-install-other-packages"></a>Pytanie: Visual Studio wygenerować plik Requirements.txt znajduje się w środowisku wirtualnym po zainstalowaniu innych pakietów?

Odpowiedź: Tak. Rozwiń **środowiska Python** węzła, kliknij prawym przyciskiem myszy środowiska wirtualnego, a następnie wybierz pozycję **Generovat requirements.txt** polecenia. Dobre okresowo użycia tego polecenia podczas modyfikowania środowiska i zatwierdzania zmian do *requirements.txt* do kontroli źródła oraz innych zmian kodu, które są zależne od danego środowiska. Jeśli ustawisz ciągłej integracji na serwerze kompilacji, możesz wygenerować plik oraz zatwierdzić zmiany, przy każdej modyfikacji środowiska.

## <a name="step-1-5-run-the-empty-django-project"></a>Krok 1-5: Uruchom pusty projekt Django

1. W programie Visual Studio, wybierz **debugowania** > **Rozpocznij debugowanie** (**F5**) lub użyj **serwera sieci Web** przycisk na pasku narzędzi ( Przeglądarka widocznej mogą się różnić):

    ![Uruchamianie serwera sieci web przycisku paska narzędzi w programie Visual Studio](media/django/run-web-server-toolbar-button.png)

1. Uruchomienie serwera oznacza, że uruchomienie polecenia `manage.py runserver <port>`, co spowoduje włączenie serwera wdrożeniowego wbudowanych w Django. Jeśli program Visual Studio twierdzi **nie można uruchomić debugera** z komunikatem o konieczności nie plik startowy, kliknij prawym przyciskiem myszy **manage.py** w **Eksploratora rozwiązań** i wybierz **Ustaw jako plik startowy**.

1. Po uruchomieniu serwera, zobaczysz okno konsoli otwórz oznacza również Wyświetla dziennik serwera. Program Visual Studio automatycznie otworzy w przeglądarce `http://localhost:<port>`. Ponieważ projekt Django nie ma żadnych aplikacji, jednak Django pokazuje tylko strony domyślnej można potwierdzić, że posiadane przez Ciebie do tej pory działa prawidłowo:

    ![Widok domyślny projekt Django](media/django/step01-first-run-success.png)

1. Gdy skończysz, Zatrzymaj serwer zamknięcie okna konsoli lub za pomocą **debugowania** > **Zatrzymaj debugowanie** polecenia w programie Visual Studio.

### <a name="question-is-django-a-web-server-as-well-as-a-framework"></a>Pytanie: Jest Django, serwer sieci web, a także platformę?

Odpowiedź: Tak i nie. Django ma serwera sieci web wbudowane, który służy do celów programistycznych. Ten serwer sieci web jest, co zostanie wykorzystany podczas uruchamiania aplikacji sieci web w środowisku lokalnym, takie jak czas debugowania w programie Visual Studio. Podczas wdrażania hosta sieci web, jednak Django użyje hosta serwera sieci web. *Wsgi.py* modułu w projekcie Django dba o przechwytywanie na serwerach produkcyjnych.

### <a name="question-whats-the-difference-between-using-the-debug-menu-commands-and-the-server-commands-on-the-projects-python-submenu"></a>Pytanie: Jaka jest różnica między za pomocą poleceń menu Debugowanie i polecenia serwera w podmenu Python projektu?

Odpowiedź: Oprócz **debugowania** poleceń menu i przycisków paska narzędzi można również uruchomić serwera za pomocą **Python** > **uruchom serwer** lub  **Python** > **serwera debugowania Uruchom** polecenia menu kontekstowego projektu. Oba polecenia, Otwórz okno konsoli zawiera adres URL lokalnego (localhost:port) dla uruchomionego serwera. Jednak należy ręcznie otworzyć przeglądarkę z tego adresu URL i uruchomienie serwera debugowania nie zostanie uruchomiona automatycznie debugera programu Visual Studio. Możesz dołączyć debugera do uruchomionego procesu później, jeśli chcesz, za pomocą **debugowania** > **dołączyć do procesu** polecenia.

## <a name="next-steps"></a>Następne kroki

W tym momencie podstawowego projektu Django nie zawiera żadnych aplikacji. Możesz utworzyć aplikację w następnym kroku. Ponieważ zazwyczaj pracować z więcej niż projekt Django aplikacje Django, nie musisz wiedzieć znacznie bardziej, informacje o plikach standardowy w chwili obecnej.

> [!div class="nextstepaction"]
> [Tworzenie aplikacji Django przy użyciu widoków i szablonów stron](learn-django-in-visual-studio-step-02-create-an-app.md)

## <a name="go-deeper"></a>Przejdź dalej

- Kod projektu Django: [Zapisywanie swoją pierwszą aplikację Django, część 1](https://docs.djangoproject.com/en/2.0/intro/tutorial01/) (docs.djangoproject.com)
- Narzędzie administracyjne: [administracyjnego django i manage.py](https://docs.djangoproject.com/en/2.0/ref/django-admin/) (docs.djangoproject.com)
- Kod źródłowy samouczek w witrynie GitHub: [Microsoft/python — przykładowe vs uczenia — django](https://github.com/Microsoft/python-sample-vs-learning-django)

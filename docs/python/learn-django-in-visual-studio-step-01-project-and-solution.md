---
title: Poznaj samouczek Django w programie Visual Studio, krok 1, podstawowe informacje o Django
titleSuffix: ''
description: Przewodnik po Django podstawy w kontekście projektów programu Visual Studio, ukazujący pomoc techniczną dla programu Visual Studio, umożliwia tworzenie aplikacji Django.
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: afde24347237ed3fc87d7a00ebdf21787d78909c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942664"
---
# <a name="tutorial-get-started-with-the-django-web-framework-in-visual-studio"></a>Samouczek: Rozpoczynanie pracy z platformą internetową Django w programie Visual Studio

[Django](https://www.djangoproject.com/) to struktura języka Python wysokiego poziomu przeznaczona do szybkiego, bezpiecznego i skalowalnego programowania w sieci Web. Ten samouczek Eksplorowanie struktury Django w kontekście szablonów projektu, które program Visual Studio zapewnia, aby usprawnić Tworzenie aplikacji sieci Web opartych na Django.

Z tego samouczka dowiesz się, jak wykonywać następujące czynności:

> [!div class="checklist"]
> - Tworzenie podstawowego projektu Django w repozytorium git przy użyciu szablonu "Blank Django Web Project" (krok 1)
> - Tworzenie aplikacji Django z jedną stroną i renderowanie tej strony przy użyciu szablonu (krok 2)
> - Obsługiwanie plików statycznych, dodawanie stron i używanie dziedziczenia szablonów (krok 3)
> - Korzystanie z szablonu projektu sieci Web Django w celu utworzenia aplikacji z wieloma stronami i wyglądem (krok 4)
> - Uwierzytelnianie użytkowników (krok 5)
> - Użyj szablonu projektu sieci Web Django sondy, aby utworzyć aplikację korzystającą z modeli, migracji baz danych i dostosowań do interfejsu administracyjnego (krok 6)

## <a name="prerequisites"></a>Wymagania wstępne

- Program Visual Studio 2017 lub nowszy w systemie Windows z następującymi opcjami:
  - Obciążenie **programowanie** w języku Python (karta **obciążenie** w instalatorze). Aby uzyskać instrukcje, zobacz [Instalowanie obsługi języka Python w programie Visual Studio](installing-python-support-in-visual-studio.md).
  - Rozszerzenie **git dla systemu Windows** i usługi **GitHub dla programu Visual Studio** na karcie **poszczególne składniki** w obszarze **Narzędzia kodu**.

Szablony projektów Django są również dołączone do wszystkich wcześniejszych wersji Python Tools for Visual Studio, ale szczegółowe informacje mogą się różnić od tego, co zostało omówione w tym samouczku (zwłaszcza w przypadku wcześniejszych wersji środowiska Django Framework).

Programowanie w języku Python nie jest obecnie obsługiwane w Visual Studio dla komputerów Mac. Na komputerach Mac i Linux Użyj [rozszerzenia Python w Visual Studio Code](https://code.visualstudio.com/docs/python/python-tutorial).

### <a name="visual-studio-projects-and-django-projects"></a>"Projekty programu Visual Studio" i "projekty Django"

W terminologii Django "projekt Django" składa się z kilku plików konfiguracyjnych na poziomie witryny oraz co najmniej jednej "aplikacji" wdrażanej na hoście sieci Web w celu utworzenia kompletnej aplikacji sieci Web. Projekt Django może zawierać wiele aplikacji, a ta sama aplikacja może znajdować się w wielu projektach Django.

Projekt programu Visual Studio, dla którego część, może zawierać projekt Django wraz z wieloma aplikacjami. Ze względu na prostotę, gdy ten samouczek odnosi się tylko do projektu, odwołuje się do projektu programu Visual Studio. Gdy odwołuje się do części "Django Project" aplikacji sieci Web, w tym celu jest stosowana "Django Project".

W ramach tego samouczka utworzysz pojedyncze rozwiązanie programu Visual Studio, które zawiera trzy oddzielne projekty Django, z których każdy zawiera jedną aplikację Django. Utrzymując projekty w tym samym rozwiązaniu, można łatwo przełączać się między różnymi plikami do porównania.

## <a name="step-1-1-create-a-visual-studio-project-and-solution"></a>Krok 1-1: Tworzenie projektu i rozwiązania programu Visual Studio

Podczas pracy z Django z poziomu wiersza polecenia, zazwyczaj uruchamiasz projekt, uruchamiając `django-admin startproject <project_name>` polecenie. W programie Visual Studio Użycie szablonu "pusty projekt sieci Web Django" zapewnia taką samą strukturę w ramach projektu i rozwiązania programu Visual Studio.

1. W programie Visual Studio wybierz pozycję **plik**  >  **Nowy**  >  **projekt**, wyszukaj ciąg "Django" i wybierz szablon **projektu sieci Web pustej Django** . (Szablon znajduje się również w języku **Python**  >  **Sieć Web** na liście po lewej stronie).

    ![Okno dialogowe nowego projektu w programie Visual Studio dla pustego projektu sieci Web Django](media/django/step01-new-blank-project.png)

1. W polach w dolnej części okna dialogowego wprowadź następujące informacje (jak pokazano na poprzedniej ilustracji), a następnie wybierz **przycisk OK**:

    - **Nazwa**: Ustaw nazwę projektu programu Visual Studio na **BasicProject**. Ta nazwa jest również używana dla projektu Django.
    - **Lokalizacja**: Określ lokalizację, w której ma zostać utworzone rozwiązanie i projekt programu Visual Studio.
    - **Rozwiązanie**: Pozostaw ten zestaw kontrolek jako domyślną opcję **Utwórz nowe rozwiązanie** .
    - **Nazwa rozwiązania**: Ustaw wartość **LearningDjango**, która jest odpowiednia dla rozwiązania jako kontener dla wielu projektów w tym samouczku.
    - **Utwórz katalog dla rozwiązania**: pozostaw ustawiony (domyślnie).
    - **Utwórz nowe repozytorium git**: zaznacz tę opcję (która jest domyślnie wyczyszczona), aby program Visual Studio tworzył lokalne repozytorium git podczas tworzenia rozwiązania. Jeśli ta opcja nie jest widoczna, uruchom Instalatora programu Visual Studio i Dodaj rozszerzenie **git dla systemu Windows** i usługi **GitHub dla programu Visual Studio** na karcie **poszczególne składniki** w obszarze **Narzędzia kodu**.

1. Po chwili program Visual Studio wyświetli okno dialogowe z informacją o tym, że **ten projekt wymaga zewnętrznych pakietów** (pokazanych poniżej). To okno dialogowe jest wyświetlane, ponieważ szablon zawiera plik *requirements.txt* , odwołujący się do najnowszego pakietu Django 1. x. (Wybierz pozycję **Pokaż wymagane pakiety** , aby zobaczyć dokładne zależności).

    ![Monituj o to, że projekt wymaga pakietów zewnętrznych](media/django/step01-requirements-prompt-install-myself.png)

1. Wybierz opcję **zainstaluję je samodzielnie**. Wkrótce utworzysz środowisko wirtualne, aby upewnić się, że jest ono wykluczone z kontroli źródła. (Środowisko można zawsze utworzyć na podstawie *requirements.txt*).

## <a name="step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository"></a>Krok 1-2: sprawdzanie formantów git i publikowanie w repozytorium zdalnym

Ponieważ wybrano opcję **Utwórz nowe repozytorium git** w oknie dialogowym **Nowy projekt** , projekt jest już zatwierdzony do lokalnej kontroli źródła zaraz po zakończeniu procesu tworzenia. Ten krok umożliwia zapoznanie się z kontrolkami git programu Visual Studio i oknem **Team Explorer** , w którym pracujesz z kontrolą źródła.

1. Przejrzyj kontrolki Git w dolnym rogu okna głównego programu Visual Studio. Od lewej do prawej te kontrolki wyświetlają niewypychane zatwierdzenia, Niezatwierdzone zmiany, nazwę repozytorium i bieżącą gałąź:

    ![Kontrolki Git w oknie programu Visual Studio](media/django/step01-git-controls.png)

    > [!Note]
    > Jeśli nie zaznaczysz **nowego repozytorium git** w oknie dialogowym **Nowy projekt** , w kontrolkach Git będzie widoczne tylko polecenie **Dodaj do kontroli źródła** , które tworzy lokalne repozytorium.
    >
    > ![Jeśli repozytorium nie zostało utworzone, w programie Visual Studio pojawi się wartość Dodaj do kontroli źródła](media/django/step01-git-add-to-source-control.png)

1. Wybierz przycisk zmiany, a program Visual Studio otworzy okno **Team Explorer** na stronie **zmiany** . Ze względu na to, że nowo utworzony projekt jest już automatycznie zatwierdzony do kontroli źródła, nie zobaczysz żadnych oczekujących zmian.

    ![Okno Team Explorer na stronie zmiany](media/django/step01-team-explorer-changes.png)

1. Na pasku stanu programu Visual Studio wybierz przycisk niewypchnięte zatwierdzeń (Strzałka w górę z **2**), aby otworzyć stronę **Synchronizacja** w **Team Explorer**. Ponieważ masz tylko lokalne repozytorium, Strona zawiera proste opcje publikowania repozytorium w różnych repozytoriach zdalnych.

    ![Okno Team Explorer pokazujące dostępne opcje repozytorium git dotyczące kontroli źródła](media/django/step01-team-explorer.png)

    Możesz wybrać niezależną usługę dla własnych projektów. W tym samouczku przedstawiono użycie usługi GitHub, w której ukończony przykładowy kod samouczka jest przechowywany w repozytorium [Microsoft/Python-Sample-vs-Learning-Django](https://github.com/Microsoft/python-sample-vs-learning-django) .

1. Po wybraniu dowolnego z formantów **publikowania** **Team Explorer** poprosi o dodatkowe informacje. Na przykład podczas publikowania przykładu dla tego samouczka należy najpierw utworzyć repozytorium, w którym wystąpiła opcja **wypchnij do zdalnego repozytorium** z adresem URL repozytorium.

    ![Okno Team Explorer do wypychania do istniejącego repozytorium zdalnego](media/django/step01-push-to-github.png)

    Jeśli nie masz istniejącego repozytorium, opcje **Publikuj w** serwisie GitHub i **wypchnij do usługi Azure DevOps** umożliwiają utworzenie jednego bezpośrednio z poziomu programu Visual Studio.

1. Podczas pracy w ramach tego samouczka wykonywać się okresowo, korzystając z formantów w programie Visual Studio, aby zatwierdzić i wypchnąć zmiany. Ten samouczek przypomina użytkownika w odpowiednich punktach.

> [!Tip]
> Aby szybko poruszać się w **Team Explorer**, zaznacz nagłówek (który odczytuje **zmiany** lub **wypchnij** obrazy powyżej), aby wyświetlić menu rozwijane dostępne strony.

### <a name="question-what-are-some-advantages-of-using-source-control-from-the-beginning-of-a-project"></a>Pytanie: Jakie są korzyści z używania kontroli źródła na początku projektu?

Odpowiedź: pierwszy z, przy użyciu kontroli źródła od początku, szczególnie jeśli korzystasz również z repozytorium zdalnego, zapewnia regularne kopie zapasowe projektu. W przeciwieństwie do konserwowania projektu tylko w lokalnym systemie plików kontrola źródła zapewnia również kompletną historię zmian oraz łatwą możliwość przywrócenia pojedynczego pliku lub całego projektu do poprzedniego stanu. Historia zmian pomaga określić przyczynę regresji (niepowodzenia testów). Ponadto kontrola źródła jest niezwykle ważna, jeśli wiele osób pracuje nad projektem, ponieważ zarządza zastępowaniem i zapewnia Rozwiązywanie konfliktów. Na koniec kontrola źródła, która jest zasadniczo formą automatyzacji, pozwala dobrze zautomatyzować kompilacje, testowanie i zarządzanie wydaniami. Jest to naprawdę pierwszy krok przy użyciu DevOps dla projektu i ponieważ przeszkody do wprowadzenia są tak niskie, dlatego nie ma powodów, aby nie używać kontroli źródła od początku.

Aby uzyskać dodatkową dyskusję na temat kontroli źródła jako Automatyzacja, zobacz [Źródło prawdy: rola repozytoriów w DevOps](/archive/msdn-magazine/2016/september/mobile-devops-the-source-of-truth-the-role-of-repositories-in-devops), artykuł w witrynie MSDN Magazine przeznaczony dla aplikacji mobilnych, które dotyczą również usługi Web Apps.

### <a name="question-can-i-prevent-visual-studio-from-auto-committing-a-new-project"></a>Pytanie: czy program Visual Studio może uniemożliwić autozatwierdzanie nowego projektu?

Odpowiedź: Tak. Aby wyłączyć automatyczne zatwierdzanie, przejdź do strony **Ustawienia** w obszarze **Team Explorer**, wybierz pozycję  >  **Ustawienia globalne** git, usuń zaznaczenie pola wyboru **Zatwierdź zmiany po scaleniu domyślnie**, a następnie wybierz pozycję **Aktualizuj**.

## <a name="step-1-3-create-the-virtual-environment-and-exclude-it-from-source-control"></a>Krok 1-3: Tworzenie środowiska wirtualnego i wykluczenie go z kontroli źródła

Teraz, po skonfigurowaniu kontroli źródła dla projektu, można utworzyć środowisko wirtualne, które zawiera niezbędne pakiety Django dla projektu. Następnie można użyć **Team Explorer** do wykluczenia folderu środowiska z kontroli źródła.

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy węzeł **środowiska Python** i wybierz polecenie **Dodaj środowisko wirtualne**.

    ![Dodaj polecenie środowiska wirtualnego w Eksplorator rozwiązań](media/django/step01-add-virtual-environment-command.png)

1. Zostanie wyświetlone okno dialogowe **Dodawanie środowiska wirtualnego** z komunikatem informującym o **znalezieniu pliku requirements.txt.** Ten komunikat oznacza, że program Visual Studio używa tego pliku do skonfigurowania środowiska wirtualnego.

    ![Okno dialogowe Dodawanie środowiska wirtualnego z komunikatem o requirements.txt](media/django/step01-add-virtual-environment-found-requirements.png)

1. Wybierz pozycję **Utwórz** , aby zaakceptować wartości domyślne. (Możesz zmienić nazwę środowiska wirtualnego, jeśli chcesz, co tylko zmieni nazwę jego podfolderu, ale `env` jest standardową Konwencją).

1. Jeśli zostanie wyświetlony monit, wyrażasz zgodę na uprawnienia administratora, a następnie poczekaj kilka minut, gdy program Visual Studio pobierze i zainstaluje pakiety, które dla Django oznaczają rozwinięcie kilku tysięcy plików w dowolnej liczbie podfolderów. Postęp można zobaczyć w oknie **danych wyjściowych** programu Visual Studio. Gdy oczekujesz, spędzać poniższe sekcje pytań.

1. W kontrolkach git programu Visual Studio (na pasku stanu) wybierz wskaźnik zmiany (który pokazuje **99&#42;**), co spowoduje otwarcie strony **zmiany** w **Team Explorer**.

    Tworzenie środowiska wirtualnego wprowadzonego w tysiącach zmian, ale nie trzeba uwzględniać żadnego z nich w kontroli źródła, ponieważ użytkownik (lub każda inna osoba klonuje projekt) zawsze może odtworzyć środowisko z *requirements.txt*.

    Aby wykluczyć środowisko wirtualne, kliknij prawym przyciskiem myszy folder **ENV** i wybierz polecenie **Ignoruj te elementy lokalne**.

    ![Ignorowanie środowiska wirtualnego w zmianach kontroli źródła](media/django/step01-ignore-local-items.png)

1. Po wykluczeniu środowiska wirtualnego tylko pozostałe zmiany są w pliku projektu i *. gitignore*. Plik *. gitignore* zawiera dodany wpis dla folderu środowiska wirtualnego. Możesz kliknąć dwukrotnie plik, aby zobaczyć różnicę.

1. Wprowadź wiadomość dotyczącą zatwierdzenia i wybierz przycisk **Zatwierdź wszystko** , a następnie wypchnij zatwierdzenia do repozytorium zdalnego, jeśli chcesz.

### <a name="question-why-do-i-want-to-create-a-virtual-environment"></a>Pytanie: Dlaczego chcę utworzyć środowisko wirtualne?

Odpowiedź: środowisko wirtualne to świetny sposób izolowania dokładnych zależności aplikacji. Taka Izolacja pozwala uniknąć konfliktów w globalnym środowisku języka Python i pomaga w testowaniu i współpracy. W miarę upływu czasu podczas opracowywania aplikacji niezmiennie się w wielu przydatnych pakietach języka Python. Utrzymując pakiety w środowisku wirtualnym specyficznym dla projektu, można łatwo zaktualizować plik *requirements.txt* projektu, który opisuje to środowisko, które jest zawarte w kontroli źródła. Gdy projekt jest kopiowany na inne komputery, w tym serwery kompilacji, serwery wdrażania i inne komputery deweloperskie, można łatwo odtworzyć środowisko tylko *requirements.txt* (co oznacza, że środowisko nie musi znajdować się w kontroli źródła). Aby uzyskać więcej informacji, zobacz [Korzystanie z środowisk wirtualnych](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

### <a name="question-how-do-i-remove-a-virtual-environment-thats-already-committed-to-source-control"></a>Pytanie: Jak mogę usunąć środowisko wirtualne, które zostało już zatwierdzone do kontroli źródła?

Odpowiedź: najpierw Edytuj plik *. gitignore* , aby wykluczyć folder: Znajdź sekcję na końcu z komentarzem `# Python Tools for Visual Studio (PTVS)` i Dodaj nowy wiersz do folderu środowiska wirtualnego, takiego jak `/BasicProject/env` . (Ponieważ program Visual Studio nie wyświetla pliku w **Eksplorator rozwiązań**, otwórz go bezpośrednio przy użyciu **pliku**  >  **Otwórz**  >  Polecenie menu **plik** . Możesz również otworzyć plik z **Team Explorer**: na stronie **Ustawienia** wybierz pozycję **Ustawienia repozytorium**, przejdź do sekcji **Ignorowanie atrybutów & plików** , a następnie wybierz łącze **Edytuj** obok **. gitignore**.)

Następnie otwórz okno polecenia, przejdź do folderu, takiego jak *BasicProject* , który zawiera folder środowiska wirtualnego, taki jak *ENV* i Run `git rm -r env` . Następnie zatwierdź te zmiany z wiersza polecenia ( `git commit -m 'Remove venv'` ) lub Zatwierdź ze strony **zmiany** w **Team Explorer**.

## <a name="step-1-4-examine-the-boilerplate-code"></a>Krok 1-4: badanie kodu standardowego

Po zakończeniu tworzenia projektu Przejrzyj kod standardowego projektu Django (który jest ponownie taki sam jak wygenerowany przez polecenie CLI `django-admin startproject <project_name>` ).

1. W katalogu głównym projektu jest *manage.py*, narzędzie administracyjne wiersza polecenia Django, które program Visual Studio automatycznie ustawia jako plik startowy projektu. Narzędzie jest uruchamiane w wierszu polecenia przy użyciu `python manage.py <command> [options]` . W przypadku typowych zadań Django program Visual Studio udostępnia wygodne polecenia menu. Kliknij prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** i wybierz pozycję **Python** , aby wyświetlić listę. Niektóre z tych poleceń są spotykane w ramach tego samouczka.

    ![Polecenia Django w menu kontekstowym projektu języka Python](media/django/step01-django-commands-menu.png)

2. W projekcie jest folder o nazwie takiej samej jak projekt. Zawiera podstawowe pliki projektu Django:

   - *__init. PR*: pusty plik, który informuje Python, że ten folder jest pakietem języka Python.
   - *WSGI.py*: punkt wejścia dla serwerów sieci Web zgodnych z WSGI, aby zapewnić obsługę Twojego projektu. Zazwyczaj ten plik jest opuszczany, ponieważ udostępnia punkty zaczepienia dla produkcyjnych serwerów sieci Web.
   - *Settings.py*: zawiera ustawienia dla projektu Django, które można modyfikować w trakcie opracowywania aplikacji sieci Web.
   - *URLs.py*: zawiera spis treści projektu Django, który można także zmodyfikować w trakcie opracowywania.

     ![Pliki projektu Django w Eksplorator rozwiązań](media/django/step01-django-project-in-solution-explorer.png)

3. Jak wspomniano wcześniej, szablon programu Visual Studio dodaje również plik *requirements.txt* do projektu, określając zależność pakietu Django. Obecność tego pliku polega na tym, co zaprasza do utworzenia środowiska wirtualnego podczas pierwszego tworzenia projektu.

### <a name="question-can-visual-studio-generate-a-requirementstxt-file-from-a-virtual-environment-after-i-install-other-packages"></a>Pytanie: czy program Visual Studio może generować plik requirements.txt ze środowiska wirtualnego po zainstalowaniu innych pakietów?

Odpowiedź: Tak. Rozwiń węzeł **środowiska Python** , kliknij prawym przyciskiem myszy środowisko wirtualne i wybierz polecenie **Generuj requirements.txt** . Dobrym sposobem jest użycie tego polecenia okresowo podczas modyfikowania środowiska i zatwierdzić zmiany *requirements.txt* do kontroli źródła wraz ze wszystkimi innymi zmianami kodu, które są zależne od tego środowiska. W przypadku skonfigurowania ciągłej integracji na serwerze kompilacji należy wygenerować plik i zatwierdzić zmiany przy każdej modyfikacji środowiska.

## <a name="step-1-5-run-the-empty-django-project"></a>Krok 1-5: uruchamianie pustego projektu Django

1. W programie Visual Studio wybierz pozycję **Debuguj**  >  **Rozpocznij debugowanie** (**F5**) lub przycisk **serwer sieci Web** na pasku narzędzi (widoczna przeglądarka może się różnić):

    ![Przycisk paska narzędzi uruchamiania serwera sieci Web w programie Visual Studio](media/django/run-web-server-toolbar-button.png)

1. Uruchomienie serwera oznacza uruchomienie polecenia `manage.py runserver <port>` , które uruchamia wbudowany serwer programistyczny Django. Jeśli program Visual Studio **nie może uruchomić debugera** z komunikatem o braku pliku startowego, kliknij prawym przyciskiem myszy pozycję **manage.py** w **Eksplorator rozwiązań** i wybierz polecenie **Ustaw jako plik startowy**.

1. Po uruchomieniu serwera zostanie wyświetlone okno konsoli, które również wyświetla dziennik serwera. Program Visual Studio automatycznie otwiera przeglądarkę do programu `http://localhost:<port>` . Ponieważ projekt Django nie ma żadnych aplikacji, w Django jest wyświetlana tylko strona domyślna, która pozwala potwierdzić, że to dotychczas działa prawidłowo:

    ![Widok domyślny projektu Django](media/django/step01-first-run-success.png)

1. Gdy wszystko będzie gotowe, Zatrzymaj serwer, zamykając okno konsoli lub korzystając z polecenia **Debuguj**  >  **zatrzymywanie debugowania** w programie Visual Studio.

### <a name="question-is-django-a-web-server-as-well-as-a-framework"></a>Pytanie: czy Django serwer sieci Web, a także strukturę?

Odpowiedź: tak i nie. Django ma wbudowany serwer sieci Web, który jest używany do celów deweloperskich. Ten serwer sieci Web jest używany podczas lokalnego uruchamiania aplikacji sieci Web, na przykład podczas debugowania w programie Visual Studio. Po wdrożeniu na hoście sieci Web Django używa zamiast tego serwera sieci Web hosta. Moduł *WSGI.py* w projekcie Django zajmuje się przełączaniem do serwerów produkcyjnych.

### <a name="question-whats-the-difference-between-using-the-debug-menu-commands-and-the-server-commands-on-the-projects-python-submenu"></a>Pytanie: Jaka jest różnica między użyciem poleceń menu Debuguj i poleceń serwera w podmenu środowiska Python projektu?

Odpowiedź: oprócz poleceń menu **Debuguj** i przycisków paska narzędzi można również uruchomić serwer przy użyciu   >  polecenia **Uruchom serwer uruchomieniowy** Python lub **Python**  >  **Uruchom serwer debugowania** w menu kontekstowym projektu. Oba polecenia otwierają okno konsoli, w którym widoczny jest lokalny adres URL (localhost: Port) dla uruchomionego serwera. Należy jednak ręcznie otworzyć przeglądarkę z tym adresem URL i uruchomić serwer debugowania nie uruchamia automatycznie debugera programu Visual Studio. Możesz dołączyć debuger do uruchomionego procesu później, jeśli chcesz, przy użyciu polecenia **Debuguj**  >  **Dołącz do procesu** .

## <a name="next-steps"></a>Następne kroki

W tym momencie projekt Basic Django nie zawiera żadnych aplikacji. W następnym kroku utworzysz aplikację. Ponieważ zazwyczaj pracujesz z aplikacjami Django więcej niż w projekcie Django, nie musisz już wiedzieć więcej na temat plików standardowych.

> [!div class="nextstepaction"]
> [Tworzenie aplikacji Django za pomocą widoków i szablonów stron](learn-django-in-visual-studio-step-02-create-an-app.md)

## <a name="go-deeper"></a>Przejdź głębiej

- Kod projektu Django: [pisanie pierwszej aplikacji Django, część 1](https://docs.djangoproject.com/en/2.0/intro/tutorial01/) (docs.djangoproject.com)
- Narzędzie administracyjne: [Django-admin i manage.py](https://docs.djangoproject.com/en/2.0/ref/django-admin/) (docs.djangoproject.com)
- Kod źródłowy samouczka w witrynie GitHub: [Microsoft/Python-Sample-vs-Learning-Django](https://github.com/Microsoft/python-sample-vs-learning-django)
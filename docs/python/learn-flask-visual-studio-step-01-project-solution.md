---
title: Poznaj samouczek Flask w programie Visual Studio w kroku 1, podstawy Flask
titleSuffix: ''
description: Przewodnik po podstawy Flask w kontekście projektów programu Visual Studio, w tym wymagania wstępne, Git i środowisk wirtualnych.
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: d0ad3ac3c4efa6be136fa85ee0c8abbe3632e53f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62958805"
---
# <a name="tutorial-get-started-with-the-flask-web-framework-in-visual-studio"></a>Samouczek: Rozpoczynanie pracy z usługą Flask struktury sieci web w programie Visual Studio

[Flask](http://flask.pocoo.org/) to lekki struktura języka Python dla aplikacji sieci web, która zapewnia podstawowe informacje dotyczące routingu adresów URL i renderowania stron.

Flask jest nazywany framework "micro", ponieważ nie bezpośrednio udostępnia funkcje, takie jak formularz weryfikacji, abstrakcję bazy danych, uwierzytelniania i tak dalej. Takie funkcje, zamiast tego są dostarczane przez specjalnych pakietów języka Python o nazwie Flask *rozszerzenia*. Rozszerzenia bezproblemowo integrować z Flask, tak aby wyglądały tak, jakby są one częścią Flask sam. Na przykład Flask, sama nie zapewnia aparat szablonów strony. Tworzenie szablonów jest zapewniana przez rozszerzenia, takie jak Jinja i Jade, jak pokazano w tym samouczku.

W tym samouczku dowiesz się, jak:

> [!div class="checklist"]
> - Tworzenie podstawowego projektu Flask w repozytorium Git przy użyciu szablonu "Pusty projekt sieci Web Flask" (krok 1)
> - Tworzenie aplikacji Flask za pomocą jednej strony i renderowania tej strony, przy użyciu szablonu (krok 2)
> - Obsługa plików statycznych, dodawanie stron i użyć szablonu dziedziczenia (krok 3)
> - Szablon projektu sieci Web Flask służy do tworzenia aplikacji z wieloma stronami i elastyczne środowisko (krok 4)
> - Szablon projektu sieci Web Flask sond służy do tworzenia aplikacji sondowania, która korzysta z rozmaitych rodzajów magazynów (magazynu platformy Azure, bazy danych MongoDB lub pamięć).

W miarę upływu następujące kroki, utworzysz jedno rozwiązanie Visual Studio, który zawiera trzy osobne projekty. Utwórz projekt za pomocą różnych szablonów projektu Flask, które są dołączone do programu Visual Studio. Przechowując projektów w tym samym rozwiązaniu, można łatwo przełączać i z powrotem między różnych plików do porównania.

> [!Note]
> W tym samouczku różni się od [Szybki Start Flask](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json) , możesz dowiedzieć się więcej o Flask oraz jak używać różnych Flask szablonów projektu, które zapewnia bardziej rozległe począwszy od punktu we własnych projektach. Na przykład szablony projektu automatycznie zainstalować pakiet Flask podczas tworzenia projektu, nie trzeba już ręcznie, jak pokazano w opcji szybkiego startu instalacji pakietu.

## <a name="prerequisites"></a>Wymagania wstępne

- Visual Studio 2017 lub później na Windows przy użyciu następujących opcji:
  - **Programowania w języku Python** obciążenia (**obciążenia** karty w oknie Instalatora). Aby uzyskać instrukcje, zobacz [Instalowanie obsługi języka Python w programie Visual Studio](installing-python-support-in-visual-studio.md).
  - **Git dla Windows** i **rozszerzeniu GitHub Extension for Visual Studio** na **poszczególne składniki** karcie **kodu narzędzia**.

Szablony projektu Flask są dołączane do wcześniejszych wersjach narzędzi Python Tools for Visual Studio, chociaż szczegóły mogą się różnić od co zostało omówione w tym samouczku.

Programowanie w języku Python nie jest obecnie obsługiwana w programie Visual Studio dla komputerów Mac. Na komputerach Mac i Linux, należy użyć [rozszerzenie języka Python w programie Visual Studio Code](https://code.visualstudio.com/docs/python/python-tutorial).

## <a name="step-1-1-create-a-visual-studio-project-and-solution"></a>Krok 1-1: Tworzenie projektu programu Visual Studio i rozwiązania

1. W programie Visual Studio, wybierz **pliku** > **New** > **projektu**, wyszukaj frazę "Flask" i wybierz **pusty projekt sieci Web Flask**  szablonu. (Szablon znajduje się również w obszarze **Python** > **Web** na liście po lewej stronie.)

    ![Okno dialogowe nowego projektu w programie Visual Studio dla pustego projektu sieci Web Flask](media/flask/step01-new-blank-project.png)

1. W polach w dolnej części okna dialogowego wprowadź następujące informacje (jak pokazano na poprzednim rysunku), a następnie wybierz **OK**:

    - **Nazwa**: Ustaw nazwę projektu programu Visual Studio, aby **BasicProject**. Ta nazwa jest także używana dla projektu Flask.
    - **Lokalizacja**: Określ lokalizację, w której chcesz utworzyć rozwiązanie programu Visual Studio i projektu.
    - **Nazwa rozwiązania**: Ustaw **LearningFlask**, który jest odpowiedni do rozwiązania jako kontener dla wielu projektów w ramach tego samouczka.
    - **Utwórz katalog dla rozwiązania**: Pozostaw zestawu (ustawienie domyślne).
    - **Utwórz nowe repozytorium Git**: Wybierz tę opcję, (czyli wyczyść domyślnie), tak aby program Visual Studio tworzy lokalne repozytorium Git, podczas tworzenia rozwiązania. Jeśli nie widzisz tej opcji, uruchom Instalatora programu Visual Studio i Dodaj **Git dla Windows** i **rozszerzeniu GitHub Extension for Visual Studio** na **poszczególne składniki** kartę w obszarze **kodu narzędzia**.

1. Po chwili Visual Studio wyświetli monit z informacją o tym okna dialogowego **ten projekt wymaga pakiety zewnętrzne** (pokazana poniżej). To okno dialogowe pojawia się, ponieważ szablon zawiera *requirements.txt* plik odwołuje się do najnowszego pakietu 1.x Flask. (Wybierz **Pokaż wymagane pakiety** Aby wyświetlić zależności dokładną.)

    ![Monituj powiedzenie, że projekt wymaga pakiety zewnętrzne](media/tutorials-common/step01-requirements-prompt-install-myself.png)

1. Wybierz opcję **I zainstaluje je samodzielnie**. Utworzysz środowisko wirtualne wkrótce, aby upewnić się, że jest ona wykluczana z kontroli źródła. (Zawsze można tworzyć środowiska na podstawie *requirements.txt*.)

## <a name="step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository"></a>Krok 1 – 2: Sprawdź kontrolki Git i opublikuj do zdalnego repozytorium

Ponieważ wybrano **Utwórz nowe repozytorium Git** w **nowy projekt** okno dialogowe, projekt jest już zaangażowana w lokalnej kontroli źródła zaraz po zakończeniu procesu tworzenia. W tym kroku należy zapoznać się z kontrolek Git programu Visual Studio i **Team Explorer** okna, w którym pracujesz z kontrolą źródła.

1. Sprawdź formanty Git na dolnym rogu okna głównego programu Visual Studio. Od lewej do prawej te kontrolki wyświetlają niewypchniętych zatwierdzeń, niezatwierdzone zmiany, nazwę repozytorium i gałąź bieżącą:

    ![Git formantów w oknie programu Visual Studio](media/flask/step01-git-controls.png)

    > [!Note]
    > Jeśli nie zaznaczysz **Utwórz nowe repozytorium Git** w **nowy projekt** oknie dialogowym usługi Git kontrolek zostaną wyświetlone tylko **Dodaj do kontroli źródła** polecenia, który tworzy lokalną repozytorium.
    >
    > ![Dodaj do kontroli źródła jest wyświetlany w programie Visual Studio, jeśli nie utworzono repozytorium](media/tutorials-common/step01-git-add-to-source-control.png)

1. Wybierz przycisk zmiany, a Visual Studio otwiera jego **Team Explorer** okno na **zmiany** strony. Ponieważ nowo utworzonego projektu jest już zatwierdzone do kontroli źródła automatycznie, nie widać wszystkie oczekujące zmiany.

    ![Okno Eksploratora zespołu na stronie zmiany](media/flask/step01-team-explorer-changes.png)

1. Na pasku stanu programu Visual Studio, wybierz przycisk niewypchniętych zatwierdzeń (strzałkę w górę o **2**) aby otworzyć **synchronizacji** strony w **Team Explorer**. Ponieważ lokalne repozytorium, na stronie jest prostych opcji, aby opublikować repozytorium w różnych repozytoria zdalne.

    ![Team Explorer okna pokazujący dostępne Git opcji repozytorium dla kontroli źródła](media/flask/step01-team-explorer.png)

    Możesz niezależnie od usługi, w której ma we własnych projektach. W tym samouczku pokazano sposób użycia usługi GitHub, w której ukończone przykładowego kodu na potrzeby tego samouczka jest zachowywany w [Microsoft/python — przykładowe vs uczenia — platformy flask](https://github.com/Microsoft/python-sample-vs-learning-flask) repozytorium.

1. Po wybraniu dowolnego z **Publikuj** kontrolek **Team Explorer** wyświetli monit o podanie informacji. Na przykład podczas publikowania próbki na potrzeby tego samouczka, samo repozytorium musieli najpierw należy utworzyć, w którym to przypadku **wypychania do repozytorium zdalnego** użyto opcji za pomocą adresu URL repozytorium.

    ![Okno Eksploratora zespołu do wypychania do istniejącego repozytorium zdalnego](media/flask/step01-push-to-github.png)

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

Teraz, gdy skonfigurowano kontroli źródła dla projektu, można utworzyć środowisko wirtualne niezbędne pakiety Flask, których wymaga projekt. Następnie można użyć **Team Explorer** Aby wykluczyć folder środowiska z poziomu kontroli źródła.

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **środowiska Python** a następnie wybierz węzeł **Dodawanie środowiska wirtualnego**.

    ![Dodaj polecenie środowisko wirtualne w Eksploratorze rozwiązań](media/flask/step01-add-virtual-environment-command.png)

1. **Dodawanie środowiska wirtualnego** zostanie wyświetlone okno dialogowe z komunikat **znaleźliśmy pliku requirements.txt.** Ten komunikat oznacza, że program Visual Studio używa tego pliku do skonfigurowania środowiska wirtualnego.

    ![Dodaj okno środowiska wirtualnego z komunikatem w pliku requirements.txt](media/tutorials-common/step01-add-virtual-environment-found-requirements.png)

1. Wybierz **Utwórz** aby zaakceptować wartości domyślne. (Można zmienić nazwę środowiska wirtualnego, jeśli chcesz, który po prostu zmienia nazwę jej podfolder, ale `env` jest standardowej konwencji.)

1. Wyrazić zgodę na uprawnienia administratora, jeśli zostanie wyświetlony monit, następnie o cierpliwość przez kilka minut, podczas gdy program Visual Studio pobiera i instaluje pakiety, oznacza to, Flask i jego zależności rozwijanie o tysięcy plików w podfolderach ponad 100. Możesz zobaczyć postępy w programie Visual Studio **dane wyjściowe** okna. Czekając, spędzać w kolejnych sekcjach pytanie. Widać również opis zależności firmy Flask na [instalacji Flask](http://flask.pocoo.org/docs/1.0/installation/#installation) strony (flask.pcocoo.org).

1. Dla kontrolek repozytorium Git usługi Visual Studio (na pasku stanu), wybierz wskaźnik zmian (pokazujący **99&#42;**) co spowoduje otwarcie **zmiany** strony w **Team Explorer**.

    Tworzenie środowiska wirtualnego odwoływanych setki zmiany, ale nie trzeba uwzględnić któryś z nich w kontroli źródła, ponieważ użytkownik (lub każdy w przeciwnym razie klonowanie projektu) zawsze można odtworzyć środowisko z *requirements.txt*.

    Aby wykluczyć środowiska wirtualnego, kliknij prawym przyciskiem myszy **env** i wybierz polecenie **ignorować te elementy lokalne**.

    ![Ignorowanie środowiska wirtualnego w zmian kontroli źródła](media/flask/step01-ignore-local-items.png)

1. Po wykluczeniu środowiska wirtualnego, tylko pozostałe zmiany są w pliku projektu i *.gitignore*. *.Gitignore* zawierający dodano wpis dla folderu środowiska wirtualnego. Możesz kliknąć dwukrotnie plik, aby zobaczyć diff.

1. Wprowadź wiadomość dotyczącą zatwierdzenia, a następnie wybierz pozycję **Zatwierdź wszystko** przycisk, a następnie, jeśli chcesz wypychanie zatwierdzeń do repozytorium zdalnego.

### <a name="question-why-do-i-want-to-create-a-virtual-environment"></a>Pytanie: Dlaczego chcesz utworzyć środowisko wirtualne?

Odpowiedź: Środowisko wirtualne jest doskonałym sposobem na izolowanie dokładnie zależności aplikacji. Tej izolacji pozwala uniknąć konfliktów w środowisku Python globalnym i ułatwia testowanie i współpracy. Wraz z upływem czasu podczas opracowywania aplikacji, niezmiennie wprowadzanych wiele pomocnych pakiety języka Python. Przechowując pakietów w środowisku wirtualnym specyficzne dla projektu, można łatwo zaktualizować projektu *requirements.txt* pliku, który opisuje środowisku, w którym znajduje się w kontroli źródła. Gdy projekt jest kopiowana do innych komputerów, serwerów kompilacji, wdrażania serwerów i innych komputerach rozwoju, w tym jest łatwo odtworzyć środowiskiem za pomocą tylko *requirements.txt* (co jest dlaczego środowiska nie musi znajdować się w kontroli źródła). Aby uzyskać więcej informacji, zobacz [korzystanie ze środowisk wirtualnych](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

### <a name="question-how-do-i-remove-a-virtual-environment-thats-already-committed-to-source-control"></a>Pytanie: Jak usunąć środowisko wirtualne jest została już przydzielona do kontroli źródła?

Odpowiedź: Po pierwsze Przeprowadź edycję swoje *.gitignore* plik, aby wykluczyć folder: Znajdź sekcję na końcu z komentarzem `# Python Tools for Visual Studio (PTVS)` i Dodaj nowy wiersz do folderu, w środowisku wirtualnym, takie jak `/BasicProject/env`. (Ponieważ program Visual Studio nie wyświetla plik w **Eksploratora rozwiązań**, otwórz je bezpośrednio przy użyciu **pliku** > **Otwórz**  >   **Plik** polecenia menu. Możesz również otworzyć plik z **Team Explorer**: na **ustawienia** wybierz opcję **ustawienia repozytorium**, przejdź do **Ignoruj & atrybutów plików** sekcji, a następnie wybierz **Edytuj** łącze obok **.gitignore**.)

Po drugie, Otwórz okno polecenia, przejdź do folderu, takich jak *BasicProject* zawierający takie jak folder w środowisku wirtualnym *env*i uruchom `git rm -r env`. Następnie należy zatwierdzić te zmiany z wiersza polecenia (`git commit -m 'Remove venv'`) lub czy zatwierdzić z **zmiany** strony **Team Explorer**.

## <a name="step-1-4-examine-the-boilerplate-code"></a>Krok 1-4: Badanie kodu standardowy

1. Po zakończeniu tworzenia projektu, zobacz rozwiązania i projektu w **Eksploratora rozwiązań**, w którym projekt zawiera tylko dwa pliki *app.py* i *requirements.txt*:

    ![Puste pliki projektu Flask w Eksploratorze rozwiązań](media/flask/step01-blank-flask-project-in-solution-explorer.png)

1. Jak wspomniano wcześniej, *requirements.txt* plik określa zależność pakietu Flask. Obecność tego pliku to, co zachęca do tworzenia środowiska wirtualnego, tworząc po raz pierwszy projekt.

1. Pojedynczy *app.py* plik zawiera trzy części. Najpierw jest `import` poufności informacji dotyczące Flask, tworzenia wystąpienia obiektu `Flask` klasy, która jest przypisana do zmiennej `app`, a następnie przypisując `wsgi_app` zmiennej (co jest przydatne podczas wdrażania hosta sieci web, ale nie są używane w chwili obecnej):

    ```python
    from flask import Flask
    app = Flask(__name__)

    # Make the WSGI interface available at the top level so wfastcgi can get it.
    wsgi_app = app.wsgi_app
    ```

1. Druga część, na końcu pliku, to bit opcjonalne kodu, który zaczyna się od serwera wdrożeniowego programu Flask konkretnego hosta i wartości portów podjęte ze zmiennych środowiskowych (przyjęto wartość domyślną localhost:5555):

    ```python
    if __name__ == '__main__':
        import os
        HOST = os.environ.get('SERVER_HOST', 'localhost')
        try:
            PORT = int(os.environ.get('SERVER_PORT', '5555'))
        except ValueError:
            PORT = 5555
        app.run(HOST, PORT)
    ```

1. Trzeci jest kierować krótki bitowego kodu, który przypisuje adres URL funkcji, co oznacza, że funkcja udostępnia zasobów według adresu URL. Definiowanie tras przy użyciu firmy Flask `@app.route` dekoratora, którego argument jest względny adres URL z katalogu głównego witryny. Jak widać w kodzie, w tym miejscu funkcja zwraca tylko ciąg tekstowy i jest wystarczająco dużo, w przeglądarce do renderowania. W opisanych poniżej renderowania są bardziej rozbudowane stron HTML.

    ```python
    @app.route('/')
    def hello():
        """Renders a sample page."""
        return "Hello World!"
    ```

### <a name="question-what-is-the-purpose-of-the-name-argument-to-the-flask-class"></a>Pytanie: Co to jest celem __nazwa__ argument klasy Flask?

Odpowiedź: Argument jest nazwa modułu lub pakietu aplikacji i informuje Flask, gdzie szukać szablonów, pliki statyczne i innych zasobów, które należą do aplikacji. W przypadku aplikacji znajdujących się w pojedynczym module `__name__` jest zawsze poprawnej wartości. Jest również ważne w przypadku rozszerzeń, które wymagają informacji o debugowaniu. Aby uzyskać więcej informacji i dodatkowe argumenty, zobacz [dokumentacji klasy Flask](http://flask.pocoo.org/docs/1.0/api/#flask.Flask) (flask.pocoo.org).

### <a name="question-can-a-function-have-more-than-one-route-decorator"></a>Pytanie: Czy funkcja może mieć więcej niż jeden dekorator trasy?

Odpowiedź: Tak, można użyć tylu dekoratory dowolną Jeśli taką samą funkcję obsługuje wiele tras. Na przykład, aby użyć `hello` funkcji dla obu "/" i "/ hello", użyj następującego kodu:

```python
@app.route('/')
@app.route('/hello')
def hello():
    """Renders a sample page."""
    return "Hello World!"
```

<a name="qa-url-variables"></a>

### <a name="question-how-does-flask-work-with-variable-url-routes-and-query-parameters"></a>Pytanie: Jak działa Flask za pomocą zmiennej trasy adresu URL i parametry zapytania

Odpowiedź: W trasie, oznaczenie dowolnej zmiennej za pomocą `<variable_name>`, i Flask przekazuje zmienną do funkcji za pomocą argumentu nazwanego. Zmienna może być częścią ze ścieżką URL lub w parametrze zapytania. Na przykład trasy w formie `'/hello/<name>` generuje argumentu ciągu o nazwie `name` funkcji i za pomocą `?message=<msg>` w trasie analizuje wartości podanej dla "komunikat =" parametr zapytania i przekazuje je do działania jako `msg`:

```python
@app.route('/hello/<name>?message=<msg>')
def hello(name, msg):
    return "Hello " + name + "! Message is " + msg + "."
```

Aby zmienić typ, należy poprzedzić zmienną nazwą `int`, `float`, `path` (który akceptuje ukośniki, aby odróżnić nazwy folderów), a `uuid`. Aby uzyskać więcej informacji, zobacz [reguły zmiennych](http://flask.pocoo.org/docs/1.0/quickstart/#variable-rules) w dokumentacji Flask.

Parametry zapytania są również dostępne za pośrednictwem `request.args` właściwości, w szczególności za pomocą `request.args.get` metody. Aby uzyskać więcej informacji, zobacz [żądanie obiektu](http://flask.pocoo.org/docs/1.0/quickstart/#the-request-object) w dokumentacji Flask.

### <a name="question-can-visual-studio-generate-a-requirementstxt-file-from-a-virtual-environment-after-i-install-other-packages"></a>Pytanie: Visual Studio wygenerować plik Requirements.txt znajduje się w środowisku wirtualnym po zainstalowaniu innych pakietów?

Odpowiedź: Tak. Rozwiń **środowiska Python** węzła, kliknij prawym przyciskiem myszy środowiska wirtualnego, a następnie wybierz pozycję **Generovat requirements.txt** polecenia. Dobre okresowo użycia tego polecenia podczas modyfikowania środowiska i zatwierdzania zmian do *requirements.txt* do kontroli źródła oraz innych zmian kodu, które są zależne od danego środowiska. Jeśli ustawisz ciągłej integracji na serwerze kompilacji, możesz wygenerować plik oraz zatwierdzić zmiany, przy każdej modyfikacji środowiska.

## <a name="step-1-5-run-the-project"></a>Krok 1-5: Uruchom projekt

1. W programie Visual Studio, wybierz **debugowania** > **Rozpocznij debugowanie** (**F5**) lub użyj **serwera sieci Web** przycisk na pasku narzędzi ( Przeglądarka widocznej mogą się różnić):

    ![Uruchamianie serwera sieci web przycisku paska narzędzi w programie Visual Studio](media/tutorials-common/run-web-server-toolbar-button.png)

1. Albo polecenie przypisuje numer portu losowego do zmiennej środowiskowej portu, a następnie uruchamia `python app.py`. Zaczyna się kod aplikacji przy użyciu tego portu w ramach serwera rozwoju firmy Flask. Jeśli program Visual Studio twierdzi **nie można uruchomić debugera** z komunikatem o konieczności nie plik startowy, kliknij prawym przyciskiem myszy **app.py** w **Eksploratora rozwiązań** i wybierz  **Ustaw jako plik startowy**.

1. Po uruchomieniu serwera, zobaczysz okno konsoli otwórz ten wyświetla dziennik serwera. Program Visual Studio następnie automatycznie otworzy w przeglądarce `http://localhost:<port>`, w którym powinien zostać wyświetlony komunikat renderowany przez `hello` funkcji:

    ![Widok domyślny projektu Flask](media/flask/step01-first-run-success.png)

1. Gdy skończysz, Zatrzymaj serwer zamknięcie okna konsoli lub za pomocą **debugowania** > **Zatrzymaj debugowanie** polecenia w programie Visual Studio.

### <a name="question-whats-the-difference-between-using-the-debug-menu-commands-and-the-server-commands-on-the-projects-python-submenu"></a>Pytanie: Jaka jest różnica między za pomocą poleceń menu Debugowanie i polecenia serwera w podmenu Python projektu?

Odpowiedź: Oprócz **debugowania** poleceń menu i przycisków paska narzędzi można również uruchomić serwera za pomocą **Python** > **uruchom serwer** lub  **Python** > **serwera debugowania Uruchom** polecenia menu kontekstowego projektu. Oba polecenia, Otwórz okno konsoli zawiera adres URL lokalnego (localhost:port) dla uruchomionego serwera. Jednak należy ręcznie otworzyć przeglądarkę z tego adresu URL i uruchomienie serwera debugowania nie zostanie uruchomiona automatycznie debugera programu Visual Studio. Możesz dołączyć debugera do uruchomionego procesu później, jeśli chcesz, za pomocą **debugowania** > **dołączyć do procesu** polecenia.

## <a name="next-steps"></a>Następne kroki

W tym momencie podstawowego projektu Flask zawiera kod uruchamiający i kodu strony, w tym samym pliku. Zaleca się, aby rozdzielić te dwa problemy i również rozdzielić HTML i danych przy użyciu szablonów.

> [!div class="nextstepaction"]
> [Tworzenie aplikacji Flask za pomocą widoków i szablonów stron](learn-flask-visual-studio-step-02-create-app.md)

## <a name="go-deeper"></a>Przejdź dalej

- [Przewodnik Szybki Start Flask](http://flask.pocoo.org/docs/1.0/quickstart/) (flask.pocoo.org)
- Kod źródłowy samouczek w witrynie GitHub: [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask)

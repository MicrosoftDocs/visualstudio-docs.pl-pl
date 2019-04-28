---
title: 'Szybki Start: Użyj programu Visual Studio do tworzenia aplikacji sieci web w języku Python'
description: W tym przewodniku Szybki Start używasz programu Visual Studio i platforma Flask do tworzenia prostej aplikacji sieci web w języku Python.
ms.date: 03/07/2019
ms.technology: vs-python
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- python
- data-science
ms.openlocfilehash: f81ca0d5c41f08174adfc891055939414e1bfe6f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62953962"
---
# <a name="quickstart-create-your-first-python-web-app-using-visual-studio"></a>Szybki start: Tworzenie pierwszej aplikacji sieci web języka Python za pomocą programu Visual Studio

W ramach tego wprowadzenia do programu Visual Studio jako środowiskiem Python IDE 5 – 10 minut utworzysz prostą aplikację sieci web języka Python w ramach struktury Flask. Tworzenie projektu za pomocą dyskretnych kroki, które ułatwiają Dowiedz się więcej o podstawowych funkcji programu Visual Studio.

::: moniker range="vs-2017"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) strony, aby zainstalować go za darmo. W oknie Instalatora upewnij się wybrać **programowania w języku Python** obciążenia.

::: moniker-end

::: moniker range=">=vs-2019"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) strony, aby zainstalować go za darmo. W oknie Instalatora upewnij się wybrać **programowania w języku Python** obciążenia.

::: moniker-end

## <a name="create-the-project"></a>Utwórz projekt

Poniższe kroki umożliwiają utworzenie pustego projektu, który służy jako kontener dla aplikacji:

::: moniker range="vs-2017"
1. Otwórz program Visual Studio 2017.

2. Na pasku menu u góry wybierz **Plik > Nowy > Projekt**.

3. W **nowy projekt** okna dialogowego pole, wprowadź "Projekt sieci Web języka Python" w polu wyszukiwania w prawym górnym rogu, wybierz pozycję **projektu sieci Web** w środkową listę, należy nadać projektowi nazwę, takich jak "HelloPython", a następnie wybierz **OK**.

    ![Okno dialogowe nowego projektu z projektu sieci Web w języku Python wybrane](media/quickstart-python-00-web-project.png)

    Jeśli nie widzisz szablony projektów języka Python, uruchom **Instalatora programu Visual Studio**, wybierz opcję **więcej** > **Modyfikuj**, wybierz opcję **języka Python Programowanie** obciążenia, wybierz **Modyfikuj**.

    ![Obciążenie programowania języka Python w Instalatorze programu Visual Studio](../python/media/installation-python-workload.png)

4. Nowy projekt zostanie otwarty w **Eksploratora rozwiązań** w okienku po prawej stronie. Projekt jest pusta, w tym momencie ponieważ nie zawiera on innych plików.

    ![Nowo utworzony projekt pusty Eksplorator rozwiązań](media/quickstart-python-01-empty-project.png)
::: moniker-end

::: moniker range=">=vs-2019"
1. Open Visual Studio 2019.
2. Na ekranie startowym wybierz **Utwórz nowy projekt**.
3. W **Utwórz nowy projekt** okna dialogowego pole, wprowadź "Internetowego języka Python" w polu wyszukiwania u góry wybierz **projektu sieci Web** w środkową listę, a następnie zaznacz **dalej**:

    ![Tworzenie nowego ekranu projektu za pomocą wybrany projekt sieci Web języka Python](media/quickstart-python-00-web-project-2019a.png)

    Jeśli nie widzisz szablony projektów języka Python, uruchom **Instalatora programu Visual Studio**, wybierz opcję **więcej** > **Modyfikuj**, wybierz opcję **języka Python Programowanie** obciążenia, wybierz **Modyfikuj**.

    ![Obciążenie programowania języka Python w Instalatorze programu Visual Studio](../python/media/installation-python-workload.png)

4. W **konfigurowania nowego projektu** poniżej, oknie dialogowym wprowadź "HelloPython" **Nazwa projektu**, określ lokalizację i wybierz **Utwórz**. ( **Nazwa rozwiązania** automatycznie jest ustawiony na zgodny **Nazwa projektu**.)

    ![Konfigurowanie okna dialogowego Nowy projekt](media/quickstart-python-00-web-project-2019b.png)

5. Nowy projekt zostanie otwarty w **Eksploratora rozwiązań** w okienku po prawej stronie. Projekt jest pusta, w tym momencie ponieważ nie zawiera on innych plików.

    ![Nowo utworzony projekt pusty Eksplorator rozwiązań](media/quickstart-python-01-empty-project-2019.png)
::: moniker-end

**Pytanie: Jakie są zalety tworzenia projektu w programie Visual Studio dla aplikacji w języku Python?**

**Odpowiedź**: Aplikacje Python są zazwyczaj definiowane przy użyciu tylko pliki i foldery, ale ta struktura prostych może stać się uciążliwe jako aplikacji wydają się większe i być może obejmować automatycznego generowania plików JavaScript dla aplikacji sieci web i tak dalej. Projekt programu Visual Studio pomaga zarządzać taką złożonością. Projekt ( *.pyproj* pliku) identyfikuje źródła i plikami zawartości skojarzonymi z projektem, zawiera informacje o kompilacji dla każdego pliku, zachowuje informacje o integracji z systemami kontroli źródła i pomoże Ci organizowanie aplikacji do składników logicznych.

**Pytanie: Co to jest "Rozwiązanie" wyświetlane w Eksploratorze rozwiązań?**

**Odpowiedź**: Rozwiązania programu Visual Studio jest kontenerem, który pomaga w zarządzaniu dla jednego lub więcej powiązanych projektów jako grupą i przechowuje ustawienia konfiguracji, które nie są specyficzne dla projektu. Projekty w rozwiązaniu można także odwoływać się do siebie nawzajem, w taki sposób, że uruchomiony jeden projekt (aplikacji w języku Python) automatycznie tworzy drugi projekt (np. rozszerzenia C++ używanych w aplikacji języka Python).

## <a name="install-the-flask-library"></a>Zainstaluj bibliotekę Flask

Aplikacje sieci Web w języku Python prawie zawsze użyj jednej z wielu dostępnych bibliotek języka Python do obsługi szczegóły niskiego poziomu, takie jak routing żądań sieci web i kształtowania odpowiedzi. W tym celu program Visual Studio udostępnia różne szablony dla aplikacji sieci web, z których jedna użyjesz w dalszej części tego przewodnika Szybki Start.

W tym miejscu skorzystaj z poniższych wskazówek, celu zainstalować bibliotekę Flask do domyślnego "globalne środowiska" używający programu Visual Studio dla tego projektu.

::: moniker range="vs-2017"
1. Rozwiń **środowiska Python** węzeł w projekcie, aby wyświetlić domyślne środowisko dla projektu.

    ![Środowisko domyślne Eksplorator rozwiązań](media/quickstart-python-02-default-environment.png)

2. Kliknij prawym przyciskiem myszy środowiska, a następnie wybierz pozycję **zainstaluj pakiet języka Python**. To polecenie otwiera **środowiska Python** okno na **pakietów** kartę.

3. W polu wyszukiwania wprowadź "flask", a następnie wybierz pozycję **polecenia pip install flask z PyPI**. Zaakceptuj wszystkie monity o uprawnienia administratora i obserwuj **dane wyjściowe** okna w programie Visual Studio, uzyskać informacje o postępie. (Monit o podniesienie uprawnień się dzieje, gdy folder packages globalne środowiska znajduje się w obszarze chronionym jak *C:\Program Files*.)

    ![Zainstalowanie biblioteki Flask za pomocą instalacji narzędzia pip](media/quickstart-python-03-install-package.png)
::: moniker-end
::: moniker range=">=vs-2019"
1. Rozwiń **środowiska Python** węzeł w projekcie, aby wyświetlić domyślne środowisko dla projektu.

    ![Środowisko domyślne Eksplorator rozwiązań](media/quickstart-python-02-default-environment-2019.png)

2. Kliknij prawym przyciskiem myszy środowiska, a następnie wybierz pozycję **Zarządzanie pakietami języka Python...** . To polecenie otwiera **środowiska Python** okno na **pakietów (PyPI)** kartę.

3. Wprowadź "flask" w polu wyszukiwania. Jeśli **Flask** pojawia się poniżej pola wyszukiwania, możesz pominąć ten krok. W przeciwnym razie wybierz **Uruchom polecenie: polecenia pip install, flask**. Zaakceptuj wszystkie monity o uprawnienia administratora i obserwuj **dane wyjściowe** okna w programie Visual Studio, uzyskać informacje o postępie. (Monit o podniesienie uprawnień się dzieje, gdy folder packages globalne środowiska znajduje się w obszarze chronionym jak *C:\Program Files*.)

    ![Zainstalowanie biblioteki Flask za pomocą instalacji narzędzia pip](media/quickstart-python-03-install-package-2019.png)
::: moniker-end

4. Po zainstalowaniu biblioteki jest wyświetlana w środowisku w **Eksploratora rozwiązań**, co oznacza, że można wprowadzać z niego korzystać w kodzie języka Python.

    ::: moniker range="vs-2017"
    ![Wyświetlanie i zainstalowanie biblioteki Flask w Eksploratorze rozwiązań](media/quickstart-python-04-package-installed.png)
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    ![Wyświetlanie i zainstalowanie biblioteki Flask w Eksploratorze rozwiązań](media/quickstart-python-04-package-installed-2019.png)
    ::: moniker-end

> [!Note]
> Zamiast instalowania bibliotek w środowisku globalnym, deweloperzy zazwyczaj utworzyć "środowisko wirtualne" w którym chcesz zainstalować biblioteki dla określonego projektu. Szablony programu Visual Studio oferują zazwyczaj tej opcji, zgodnie z opisem w [Szybki Start — Tworzenie projektu języka Python za pomocą szablonu](../python/quickstart-02-python-in-visual-studio-project-from-template.md).

**Pytanie: Gdzie dowiedzieć się więcej na temat innych dostępnych pakietów języka Python?**

**Odpowiedź**: Odwiedź stronę [indeksu pakietami języka Python](https://pypi.org/).

## <a name="add-a-code-file"></a>Dodaj plik kodu

Teraz możesz dodać ilość kodu języka Python do wdrożenia aplikacji sieci web minimalny.

1. Kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierz **Dodaj > Nowy element**.

1. W wyświetlonym oknie dialogowym wybierz **pusty plik Python**, nadaj jej nazwę *app.py*i wybierz **Dodaj**. Program Visual Studio automatycznie otwiera plik w oknie edytora.

1. Skopiuj poniższy kod i wklej go w *app.py*:

    ```python
    from flask import Flask

    # Create an instance of the Flask class that is the WSGI application.
    # The first argument is the name of the application module or package,
    # typically __name__ when using a single module.
    app = Flask(__name__)

    # Flask route decorators map / and /hello to the hello function.
    # To add other resources, create functions that generate the page contents
    # and add decorators to define the appropriate resource locators for them.

    @app.route('/')
    @app.route('/hello')
    def hello():
        # Render the page
        return "Hello Python!"

    if __name__ == '__main__':
        # Run the app server on localhost:4449
        app.run('localhost', 4449)
    ```

1. Być może zauważono, że **Dodaj > Nowy element** wyświetlone okno dialogowe wiele innych typów plików, które można dodać do projektu języka Python, łącznie z klasy języka Python, pakiet języka Python, test jednotky Pythonu *web.config* pliki i inne. Ogólnie rzecz biorąc te szablony elementu są nazywane, są doskonały sposób, aby szybko utworzyć pliki przydatne schematyczny kod.

**Pytanie: Gdzie można dowiedzieć się więcej na temat Flask?**

**Odpowiedź**: Zapoznaj się z dokumentacją Flask, począwszy od [Szybki Start Flask](http://flask.pocoo.org/docs/0.12/quickstart/#quickstart).

## <a name="run-the-application"></a>Uruchamianie aplikacji

1. Kliknij prawym przyciskiem myszy *app.py* w **Eksploratora rozwiązań** i wybierz **Ustaw jako plik startowy**. To polecenie Określa plik kodu, można uruchomić w języku Python, podczas uruchamiania aplikacji.

    ::: moniker range="vs-2017"
    ![Ustawienie plik startowy dla projektu w Eksploratorze rozwiązań](media/quickstart-python-05-set-as-startup-file.png)
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    ![Ustawienie plik startowy dla projektu w Eksploratorze rozwiązań](media/quickstart-python-05-set-as-startup-file-2019.png)
    ::: moniker-end

1. Kliknij prawym przyciskiem myszy *app.py* w **Eksploratora rozwiązań** i wybierz **Ustaw jako plik startowy**. To polecenie Określa plik kodu, można uruchomić w języku Python, podczas uruchamiania aplikacji.

2. Kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierz **właściwości**. Następnie wybierz pozycję **debugowania** kartę i ustawić **numer portu** właściwość `4449`. Ten krok zapewnia, że program Visual Studio otworzy w przeglądarce za pomocą `localhost:4449` do dopasowania `app.run` argumentów w kodzie.

3. Wybierz **Debuguj > Uruchom bez debugowania** (**Ctrl**+**F5**), która zapisuje zmiany w plikach i uruchamia aplikację.

4. Okno polecenia pojawi się komunikat o "* działające w <https://localhost:4449/>", i w przeglądarce powinna zostać otwarta `localhost:4449` w przypadku, gdy zostanie wyświetlony komunikat "Hello, języka Python!" Żądanie GET pojawia się również w oknie wiersza polecenia, jego stan 200.

    Jeśli przeglądarka nie jest otwierany automatycznie, uruchom wybranej przeglądarki i przejdź do `localhost:4449`.

    Jeśli zostanie wyświetlony tylko Python interaktywnej powłoki w oknie wiersza polecenia lub tego okna pojawi się na ekranie krótko, upewnij się, że możesz *app.py* jako plik startowy w kroku 1 powyżej.

5. Przejdź do `localhost:4449/hello` do przetestowania, czy dekorator dla `/hello` działa również zasobów. Ponownie żądanie GET pojawia się w oknie wiersza polecenia, jego stan 200. Możesz spróbować niektóre inne również adres URL pokazują kodów stanu 404 w oknie wiersza polecenia.

6. Zamknij okno polecenia, aby zatrzymać aplikację, a następnie zamknij okno przeglądarki.

**Pytanie: Jaka jest różnica między polecenia Uruchom bez debugowania i Rozpocznij debugowanie?**

**Odpowiedź**: Możesz użyć **Rozpocznij debugowanie** do uruchomienia aplikacji w kontekście [debugera programu Visual Studio](../python/debugging-python-in-visual-studio.md), co umożliwia ustawianie punktów przerwania, Sprawdź zmienne i przejść przez kod wiersz po wierszu. Aplikacje mogą działać wolniej w debugerze, ze względu na różne punkty zaczepienia, które umożliwiają profilowanie. **Rozpocznij bez debugowania**, natomiast bezpośrednio uruchamia aplikację tak, jakby uruchomieniu w wierszu polecenia z Brak kontekstu debugowania i automatycznie otworzy w przeglądarce i powoduje przejście do adresu URL określonego we właściwościach projektu  **Debugowanie** kartę.

## <a name="next-steps"></a>Następne kroki

Gratulujemy systemem swoją pierwszą aplikację języka Python w programie Visual Studio, w których wyjaśniono nieco o korzystaniu z programu Visual Studio jako IDE języka Python!

> [!div class="nextstepaction"]
> [Wdrażanie aplikacji w usłudze Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md)

Ponieważ kroki, które zostały wykonane w tym przewodniku Szybki Start są dość ogólny, został prawdopodobnie odgadnięcia może i powinno zostać zautomatyzowane. Takie usługi automation jest rola szablony projektu Visual Studio. Zapoznaj się z artykułem [Szybki Start — Tworzenie projektu języka Python za pomocą szablonu](../python/quickstart-02-python-in-visual-studio-project-from-template.md) demonstracyjne, który służy do tworzenia aplikacji sieci web podobny do przedstawionego utworzony w tym artykule, ale mniejszej liczby czynności.

Kontynuuj pełniejszego samouczek dotyczący języka Python w programie Visual Studio, w tym użycie okna interaktywnego, debugowania i wizualizacji danych i pracę z usługą Git, przechodzą przez [samouczka: Rozpoczynanie pracy z językiem Python w programie Visual Studio](../python/tutorial-working-with-python-in-visual-studio-step-01-create-project.md).

Chcesz dowiedzieć się więcej, że program Visual Studio ma do zaoferowania, zaznacz poniższe linki.

- Dowiedz się więcej o [szablonów aplikacji w programie Visual Studio internetowa w języku Python](../python/python-web-application-project-templates.md).
- Dowiedz się więcej o [debugowania języka Python](../python/debugging-python-in-visual-studio.md)
- Dowiedz się więcej o [środowiska IDE programu Visual Studio](../get-started/visual-studio-ide.md) ogólnie rzecz biorąc.

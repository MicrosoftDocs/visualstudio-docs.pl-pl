---
title: 'Szybki start: tworzenie aplikacji internetowej w języku Python przy użyciu Visual Studio'
titleSuffix: ''
description: W tym przewodniku Szybki start użyjemy struktury Visual Studio Flask, aby utworzyć prostą aplikację internetową w języku Python.
ms.date: 03/07/2019
ms.technology: vs-python
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom:
- acquisition
- SEO-VS-2020
ms.workload:
- python
- data-science
ms.openlocfilehash: 1cefae42025407e0252b5aedc28e979e0d86debc
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2021
ms.locfileid: "112113177"
---
# <a name="quickstart-create-your-first-python-web-app-using-visual-studio"></a>Szybki start: tworzenie pierwszej aplikacji internetowej w języku Python przy użyciu Visual Studio

W tym 5–10-minutowym wprowadzeniu do środowiska IDE języka Python Visual Studio jako prostą aplikację internetową w języku Python opartą na platformie Flask. Projekt można utworzyć za pomocą dyskretnych kroków, które ułatwiają Visual Studio podstawowych funkcji aplikacji.

::: moniker range="vs-2017"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [pobierania](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) Visual Studio, aby zainstalować ją bezpłatnie. W instalatorze wybierz obciążenie Programowanie w **języku Python.**

::: moniker-end

::: moniker range=">=vs-2019"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [pobierania](https://visualstudio.microsoft.com/downloads) Visual Studio, aby zainstalować ją bezpłatnie. W instalatorze wybierz obciążenie Programowanie w **języku Python.**

::: moniker-end

## <a name="create-the-project"></a>Tworzenie projektu

Poniższe kroki tworzą pusty projekt, który służy jako kontener dla aplikacji:

::: moniker range="vs-2017"
1. Otwórz program Visual Studio 2017.

2. Na górnym pasku menu wybierz pozycję File > New > Project (Nowy **> Project).**

3. W **oknie dialogowym** Nowy projekt wprowadź tekst "Python Web Project"  w polu wyszukiwania w prawym górnym rogu, wybierz pozycję Projekt internetowy na środkowej liście, nadaj projektowi nazwę, na przykład "HelloPython", a następnie wybierz **przycisk OK**.

    ![Okno dialogowe Nowy projekt z wybranym projektem internetowym języka Python](media/quickstart-python-00-web-project.png)

    Jeśli nie widzisz szablonów projektów języka Python, uruchom polecenie  Instalator programu Visual Studio, wybierz **pozycję** Więcej modyfikacji, wybierz obciążenie Programowanie w języku >  **Python,** a następnie wybierz **pozycję Modyfikuj**.

    ![Obciążenie programowania w języku Python w Visual Studio instalatora](../python/media/installation-python-workload.png)

4. Nowy projekt zostanie otwarty w **Eksplorator rozwiązań** okienku po prawej stronie. Projekt jest w tym momencie pusty, ponieważ nie zawiera żadnych innych plików.

    ![Eksplorator rozwiązań przedstawiający nowo utworzony pusty projekt](media/quickstart-python-01-empty-project.png)
::: moniker-end

::: moniker range=">=vs-2019"
1. Otwórz Visual Studio 2019 r.
2. Na ekranie startowym wybierz **pozycję Utwórz nowy projekt.**
3. W **oknie dialogowym** Tworzenie nowego projektu wprowadź tekst "Python web" w polu wyszukiwania u góry, wybierz pozycję **Projekt** internetowy na środkowej liście, a następnie wybierz pozycję **Dalej:**

    ![Ekran tworzenia nowego projektu z wybranym projektem internetowym języka Python](media/quickstart-python-00-web-project-2019a.png)

    Jeśli nie widzisz szablonów projektów języka Python, uruchom polecenie  Instalator programu Visual Studio, wybierz **pozycję** Więcej modyfikacji, wybierz obciążenie Programowanie w języku >  **Python,** a następnie wybierz **pozycję Modyfikuj**.

    ![Obciążenie programowania w języku Python w Visual Studio instalatora](../python/media/installation-python-workload.png)

4. W **oknie dialogowym** Configure your new project (Konfigurowanie nowego projektu) wprowadź wartość "HelloPython" w pozycji **Project name**(Nazwa projektu), określ lokalizację i wybierz pozycję **Create (Utwórz).** (Nazwa **rozwiązania jest** automatycznie ustawiana tak, aby odpowiadała nazwie **projektu).**

    ![Okno dialogowe Konfigurowania nowego projektu](media/quickstart-python-00-web-project-2019b.png)

5. Nowy projekt zostanie otwarty w **Eksplorator rozwiązań** okienku po prawej stronie. Projekt jest w tym momencie pusty, ponieważ nie zawiera żadnych innych plików.

    ![Eksplorator rozwiązań przedstawiający nowo utworzony pusty projekt](media/quickstart-python-01-empty-project-2019.png)
::: moniker-end

**Pytanie: Jakie są zalety tworzenia projektu w środowisku Visual Studio dla aplikacji w języku Python?**

**Odpowiedź:** Aplikacje w języku Python są zwykle definiowane przy użyciu tylko folderów i plików, ale ta prosta struktura może być uciążliwa, gdy aplikacje stają się większe i mogą obejmować automatycznie generowane pliki, język JavaScript dla aplikacji internetowych i tak dalej. Projekt Visual Studio pomaga zarządzać tą złożonością. Projekt (plik *pyproj)* identyfikuje wszystkie pliki źródłowe i pliki zawartości skojarzone z projektem, zawiera informacje o kompilacji dla każdego pliku, przechowuje informacje w celu integracji z systemami kontroli źródła i ułatwia organizowanie aplikacji w składniki logiczne.

**Pytanie: Co to jest "rozwiązanie" wyświetlane w Eksplorator rozwiązań?**

**Odpowiedź:** Rozwiązanie Visual Studio to kontener, który ułatwia zarządzanie co najmniej jednym powiązanym projektem jako grupą i przechowuje ustawienia konfiguracji, które nie są specyficzne dla projektu. Projekty w rozwiązaniu mogą również odwoływać się do siebie nawzajem, tak aby uruchamianie jednego projektu (aplikacji w języku Python) automatycznie tworzyło drugi projekt (na przykład rozszerzenie C++ używane w aplikacji języka Python).

## <a name="install-the-flask-library"></a>Instalowanie biblioteki flask

Aplikacje internetowe w języku Python prawie zawsze używają jednej z wielu dostępnych bibliotek języka Python do obsługi szczegółów niskiego poziomu, takich jak routing żądań internetowych i kształtowanie odpowiedzi. W tym celu Visual Studio różne szablony dla aplikacji internetowych, z których jeden będzie dostępny w dalszej części tego przewodnika Szybki start.

W tym miejscu użyjesz poniższych kroków, aby zainstalować bibliotekę Flask w domyślnym "środowisku globalnym", które Visual Studio używane w tym projekcie.

::: moniker range="vs-2017"
1. Rozwiń **węzeł Środowiska języka Python** w projekcie, aby wyświetlić domyślne środowisko dla projektu.

    ![Eksplorator rozwiązań przedstawiający środowisko domyślne](media/quickstart-python-02-default-environment.png)

2. Kliknij prawym przyciskiem myszy środowisko i wybierz polecenie **Zainstaluj pakiet języka Python.** To polecenie otwiera okno **Środowiska języka Python** na karcie **Pakiety.**

3. Wprowadź wartość "flask" w polu wyszukiwania i wybierz **pozycję pip install flask z pakietu PyPI**. Zaakceptuj wszelkie monity o uprawnienia  administratora i obserwuj postęp w oknie dane Visual Studio danych wyjściowych. (Monit o podniesienie uprawnień występuje, gdy folder packages środowiska globalnego znajduje się w chronionym obszarze, takim *jak C:\Program Files).*

    ![Instalowanie biblioteki Flask przy użyciu instalacji narzędzia pip](media/quickstart-python-03-install-package.png)
::: moniker-end
::: moniker range=">=vs-2019"
1. Rozwiń **węzeł Środowiska języka Python** w projekcie, aby wyświetlić domyślne środowisko dla projektu.

    ![Eksplorator rozwiązań przedstawiający środowisko domyślne](media/quickstart-python-02-default-environment-2019.png)

2. Kliknij prawym przyciskiem myszy środowisko i wybierz polecenie **Zarządzaj pakietami języka Python...**. To polecenie otwiera okno **Środowiska języka Python** na karcie Pakiety **(PyPI).**

3. Wprowadź "flask" w polu wyszukiwania. Jeśli **pod polem** wyszukiwania pojawi się komunikat Flask, możesz pominąć ten krok. W przeciwnym razie **wybierz polecenie Uruchom: pip install flask**. Zaakceptuj wszelkie monity o uprawnienia  administratora i obserwuj postęp w oknie dane Visual Studio danych wyjściowych. (Monit o podniesienie uprawnień występuje, gdy folder packages środowiska globalnego znajduje się w chronionym obszarze, takim *jak C:\Program Files).*

    ![Instalowanie biblioteki Flask przy użyciu instalacji narzędzia pip](media/quickstart-python-03-install-package-2019.png)
::: moniker-end

4. Po zainstalowaniu biblioteka zostanie wyświetlona w środowisku w **języku Eksplorator rozwiązań**, co oznacza, że można z niego korzystać w kodzie języka Python.

    ::: moniker range="vs-2017"
    ![Biblioteka Flask zainstalowana i wyświetlona w Eksplorator rozwiązań](media/quickstart-python-04-package-installed.png)
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    ![Biblioteka Flask zainstalowana i wyświetlona w Eksplorator rozwiązań](media/quickstart-python-04-package-installed-2019.png)
    ::: moniker-end

> [!Note]
> Zamiast instalować biblioteki w środowisku globalnym, deweloperzy zwykle tworzą "środowisko wirtualne", w którym mają być zainstalowane biblioteki dla określonego projektu. Visual Studio szablony zwykle oferują tę opcję, jak omówiono w przewodniku Szybki start — Tworzenie projektu [języka Python przy użyciu szablonu](../python/quickstart-02-python-in-visual-studio-project-from-template.md).

**Pytanie: Gdzie mogę dowiedzieć się więcej o innych dostępnych pakietach języka Python?**

**Odpowiedź:** Odwiedź stronę indeksu [pakietów języka Python](https://pypi.org/).

## <a name="add-a-code-file"></a>Dodawanie pliku kodu

Teraz możesz dodać trochę kodu w języku Python, aby zaimplementować minimalną aplikację internetową.

1. Kliknij prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** i wybierz **polecenie Dodaj > nowy element.**

1. W wyświetlonym oknie dialogowym wybierz pozycję Pusty plik **Python,** nadaj jej *nazwę app.py*, a następnie wybierz pozycję **Dodaj**. Visual Studio automatycznie otwiera plik w oknie edytora.

1. Skopiuj następujący kod i wklej go do *pliku app.py*:

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

1. Możesz zauważyć, że w oknie dialogowym Dodawanie nowego elementu w języku **>** jest wyświetlanych wiele innych typów plików, które można dodać do projektu języka Python, w tym klasę języka Python, pakiet języka Python, test jednostkowy języka *Python,* plikiweb.configjęzyka Python i inne. Ogólnie rzecz biorąc, te szablony elementów, jak są wywoływane, są doskonałym sposobem na szybkie tworzenie plików za pomocą przydatnego, standstandatowego kodu.

**Pytanie: Gdzie mogę dowiedzieć się więcej o flaskie?**

**Odpowiedź:** Zapoznaj się z dokumentacją flask, zaczynając od przewodnika [Szybki start flask.](https://flask.palletsprojects.com/en/1.1.x/quickstart/#quickstart)

## <a name="run-the-application"></a>Uruchamianie aplikacji

1. Kliknij prawym przyciskiem *myszy app.py* w **Eksplorator rozwiązań** i wybierz polecenie Ustaw jako **plik startowy.** To polecenie identyfikuje plik kodu do uruchomienia w języku Python podczas uruchamiania aplikacji.

    ::: moniker range="vs-2017"
    ![Ustawianie pliku startowego projektu w programie Eksplorator rozwiązań](media/quickstart-python-05-set-as-startup-file.png)
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    ![Ustawianie pliku startowego projektu w programie Eksplorator rozwiązań](media/quickstart-python-05-set-as-startup-file-2019.png)
    ::: moniker-end

2. Kliknij prawym przyciskiem myszy projekt w oknie **Eksplorator rozwiązań** a następnie wybierz **pozycję Właściwości**. Następnie wybierz **kartę Debugowanie** i ustaw właściwość **Numer portu** na wartość `4449` . Ten krok zapewnia, że Visual Studio przeglądarki z , `localhost:4449` aby `app.run` dopasować argumenty w kodzie.

3. Wybierz **pozycję > uruchom bez** debugowania **(Ctrl** F5), aby zapisywać zmiany w + plikach i uruchamiać aplikację.

4. Zostanie wyświetlone okno polecenia z komunikatem Running **in https: /localhost:4449 (Uruchomione w lokalizacji https: \/ /localhost:4449).** Powinno zostać otwarte okno przeglądarki z wyświetlonym komunikatem `localhost:4449` "Hello, Python!" Żądanie GET jest również wyświetlane w oknie polecenia ze stanem 200.

    Jeśli przeglądarka nie zostanie otwarta automatycznie, uruchom przeglądarkę i przejdź do `localhost:4449` .

    Jeśli w oknie polecenia jest dostępna tylko interaktywna powłoka języka Python lub jeśli  okno jest krótko migane na ekranie, upewnij się, że ustawiono app.py jako plik startowy w kroku 1 powyżej.

5. Przejdź do `localhost:4449/hello` , aby sprawdzić, czy dekorator `/hello` zasobu również działa. Ponownie żądanie GET zostanie wyświetlone w oknie polecenia ze stanem 200. Możesz również wypróbować inny adres URL, aby zobaczyć, że w oknie polecenia są wyświetlane kody stanu 404.

6. Zamknij okno polecenia, aby zatrzymać aplikację, a następnie zamknij okno przeglądarki.

**Pytanie: Jaka jest różnica między poleceniem Rozpocznij bez debugowania i rozpocznij debugowanie?**

**Odpowiedź:** Możesz użyć polecenia **Rozpocznij** debugowanie, aby uruchomić aplikację w kontekście debugera programu [Visual Studio,](../python/debugging-python-in-visual-studio.md)co umożliwia ustawianie punktów przerwania, badanie zmiennych i krok po wierszu kodu. Aplikacje mogą działać wolniej w debugerze ze względu na różne wpięcie, które umożliwia debugowanie. Z kolei polecenie Uruchom bez debugowania uruchamia aplikację bezpośrednio tak, jakby była uruchamiana z wiersza polecenia, bez kontekstu debugowania, a także automatycznie uruchamia przeglądarkę i przechodzi do adresu URL określonego na karcie **Debugowanie** właściwości projektu.

## <a name="next-steps"></a>Następne kroki

Gratulujemy uruchomienia pierwszej aplikacji w języku Python z Visual Studio, w której wiesz już nieco o używaniu języka Visual Studio jako środowiska IDE języka Python!

> [!div class="nextstepaction"]
> [Wdrażanie aplikacji w Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md)

Ponieważ kroki, które zostały opisane w tym przewodniku Szybki start, są dość ogólne, prawdopodobnie zgadywano, że mogą i powinny być zautomatyzowane. Taka automatyzacja jest rolą Visual Studio szablonów projektów. Przejdź przez [przewodnik Szybki start —](../python/quickstart-02-python-in-visual-studio-project-from-template.md) tworzenie projektu w języku Python przy użyciu szablonu demonstracyjnego, który tworzy aplikację internetową podobną do tej utworzonej w tym artykule, ale z mniejszą liczbą kroków.

Aby kontynuować pracę z pełniejszego samouczka na temat języka Python w usłudze Visual Studio, w tym korzystania z okna interaktywnego, debugowania, wizualizacji danych i pracy z usługą Git, przejdź do tematu Samouczek: wprowadzenie do języka Python w [usłudze Visual Studio](../python/tutorial-working-with-python-in-visual-studio-step-01-create-project.md).

Aby dowiedzieć się więcej Visual Studio do zaoferowania, wybierz poniższe linki.

- Dowiedz się więcej [o szablonach aplikacji internetowych w języku Python Visual Studio](../python/python-web-application-project-templates.md).
- Dowiedz się więcej o [debugowaniu języka Python](../python/debugging-python-in-visual-studio.md)
- Dowiedz się więcej o [Visual Studio IDE.](../get-started/visual-studio-ide.md)

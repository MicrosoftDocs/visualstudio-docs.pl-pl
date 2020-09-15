---
title: 'Szybki Start: Tworzenie aplikacji sieci Web w języku Python za pomocą programu Visual Studio'
titleSuffix: ''
description: W tym przewodniku szybki start użyjesz programu Visual Studio i platformy do tworzenia prostej aplikacji sieci Web w języku Python.
ms.date: 03/07/2019
ms.technology: vs-python
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: SEO-VS-2020
ms.workload:
- python
- data-science
ms.openlocfilehash: 4318cd98de166210a8e8744840967942006b8ea6
ms.sourcegitcommit: a18c7e9b367c2f92f6e54c3eaef442775d457667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/15/2020
ms.locfileid: "90100516"
---
# <a name="quickstart-create-your-first-python-web-app-using-visual-studio"></a>Szybki Start: Tworzenie pierwszej aplikacji sieci Web w języku Python przy użyciu programu Visual Studio

W tym 5-10-minutowym wprowadzeniu do programu Visual Studio jako środowiska IDE języka Python utworzysz prostą aplikację sieci Web w języku Python opartą na strukturze kolb. Projekt można utworzyć za pomocą odrębnych kroków, które ułatwiają zapoznanie się z podstawowymi funkcjami programu Visual Studio.

::: moniker range="vs-2017"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) , aby zainstalować ją bezpłatnie. W instalatorze upewnij się, że wybrano obciążenie programowanie w języku **Python** .

::: moniker-end

::: moniker range=">=vs-2019"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads) , aby zainstalować ją bezpłatnie. W instalatorze upewnij się, że wybrano obciążenie programowanie w języku **Python** .

::: moniker-end

## <a name="create-the-project"></a>Tworzenie projektu

Poniższe kroki tworzą pusty projekt, który służy jako kontener dla aplikacji:

::: moniker range="vs-2017"
1. Otwórz program Visual Studio 2017.

2. Na górnym pasku menu wybierz kolejno pozycje **plik > nowy > projekt**.

3. W oknie dialogowym **Nowy projekt** wprowadź "projekt sieci Web w języku Python" w polu wyszukiwania w prawym górnym rogu, wybierz **Projekt sieci Web** na liście środkowej, Nadaj projektowi nazwę, taką jak "HelloPython", a następnie wybierz **przycisk OK**.

    ![Okno dialogowe Nowy projekt z wybranym projektem sieci Web w języku Python](media/quickstart-python-00-web-project.png)

    Jeśli nie widzisz szablonów projektu w języku Python, uruchom **Instalator programu Visual Studio**, wybierz opcję **więcej** > **modyfikacji**, wybierz obciążenie programowanie w języku **Python** , a następnie wybierz **Modyfikuj**.

    ![Obciążenie programowanie w języku Python w Instalatorze programu Visual Studio](../python/media/installation-python-workload.png)

4. Nowy projekt zostanie otwarty w **Eksplorator rozwiązań** w okienku po prawej stronie. Projekt jest pusty w tym momencie, ponieważ nie zawiera żadnych innych plików.

    ![Eksplorator rozwiązań pokazujący nowo utworzony pusty projekt](media/quickstart-python-01-empty-project.png)
::: moniker-end

::: moniker range=">=vs-2019"
1. Otwórz program Visual Studio 2019.
2. Na ekranie startowym wybierz pozycję **Utwórz nowy projekt**.
3. W oknie dialogowym **Utwórz nowy projekt** w polu wyszukiwania u góry wpisz "sieć Web języka Python", wybierz **Projekt sieci Web** na liście środkowej, a następnie wybierz pozycję **dalej**:

    ![Utwórz nowy ekran projektu z wybranym projektem sieci Web w języku Python](media/quickstart-python-00-web-project-2019a.png)

    Jeśli nie widzisz szablonów projektu w języku Python, uruchom **Instalator programu Visual Studio**, wybierz opcję **więcej** > **modyfikacji**, wybierz obciążenie programowanie w języku **Python** , a następnie wybierz **Modyfikuj**.

    ![Obciążenie programowanie w języku Python w Instalatorze programu Visual Studio](../python/media/installation-python-workload.png)

4. W poniższym oknie dialogowym **Konfigurowanie nowego projektu** wprowadź wartość "HelloPython" dla pozycji **Nazwa projektu**, określ lokalizację, a następnie wybierz pozycję **Utwórz**. ( **Nazwa rozwiązania** jest automatycznie ustawiana tak, aby odpowiadała **nazwie projektu**).

    ![Skonfiguruj okno dialogowe nowego projektu](media/quickstart-python-00-web-project-2019b.png)

5. Nowy projekt zostanie otwarty w **Eksplorator rozwiązań** w okienku po prawej stronie. Projekt jest pusty w tym momencie, ponieważ nie zawiera żadnych innych plików.

    ![Eksplorator rozwiązań pokazujący nowo utworzony pusty projekt](media/quickstart-python-01-empty-project-2019.png)
::: moniker-end

**Pytanie: Jakie jest zalety tworzenia projektu w programie Visual Studio dla aplikacji w języku Python?**

**Odpowiedź**: aplikacje języka Python są zwykle definiowane przy użyciu tylko folderów i plików, ale prosta struktura może stać się uciążliwa, gdy aplikacje stają się większe i prawdopodobnie wymagają automatycznie generowanych plików, języka JavaScript dla aplikacji sieci Web i tak dalej. Projekt programu Visual Studio ułatwia zarządzanie tą złożonością. Projekt (plik *. pyproj* ) identyfikuje wszystkie pliki źródłowe i zawartości skojarzone z projektem, zawiera informacje o kompilacji każdego pliku, utrzymuje informacje do integracji z systemami kontroli źródła i pomaga organizować aplikację w składniki logiczne.

**Pytanie: co to jest "rozwiązanie" widoczne w Eksplorator rozwiązań?**

**Odpowiedź**: rozwiązanie Visual Studio jest kontenerem, który ułatwia zarządzanie dla co najmniej jednego powiązanego projektu jako grupy, a także przechowuje ustawienia konfiguracji, które nie są specyficzne dla projektu. Projekty w rozwiązaniu mogą również odwoływać się do siebie nawzajem, takich jak uruchomienie jednego projektu (aplikacja w języku Python) automatycznie kompiluje drugi projekt (na przykład rozszerzenie C++ używane w aplikacji Python).

## <a name="install-the-flask-library"></a>Zainstaluj bibliotekę kolb

Aplikacje sieci Web w języku Python prawie zawsze używają jednej z wielu dostępnych bibliotek języka Python do obsługi szczegółowych informacji, takich jak kierowanie żądań sieci Web i kształtowanie odpowiedzi. W tym celu program Visual Studio udostępnia różne szablony dla aplikacji sieci Web, z których jedna jest używana w dalszej części tego przewodnika Szybki Start.

W tym celu należy wykonać poniższe kroki, aby zainstalować bibliotekę kolb w domyślnym środowisku globalnym, którego program Visual Studio używa dla tego projektu.

::: moniker range="vs-2017"
1. Rozwiń węzeł **środowiska Python** w projekcie, aby zobaczyć domyślne środowisko dla projektu.

    ![Eksplorator rozwiązań przedstawiający środowisko domyślne](media/quickstart-python-02-default-environment.png)

2. Kliknij prawym przyciskiem myszy środowisko i wybierz polecenie **Zainstaluj pakiet języka Python**. To polecenie otwiera okno **środowiska języka Python** na karcie **pakiety** .

3. Wprowadź "kolbę" w polu wyszukiwania i wybierz pozycję **pip install Installation from PyPI**. Zaakceptuj wszelkie zapytanie dotyczące uprawnień administratora i postępuj zgodnie z oknem **danych wyjściowych** w programie Visual Studio. (Monit o podniesienie uprawnień występuje, gdy folder pakiety dla środowiska globalnego znajduje się w chronionym obszarze, takim jak *C:\Program Files*).

    ![Instalowanie biblioteki kolb przy użyciu narzędzia pip install](media/quickstart-python-03-install-package.png)
::: moniker-end
::: moniker range=">=vs-2019"
1. Rozwiń węzeł **środowiska Python** w projekcie, aby zobaczyć domyślne środowisko dla projektu.

    ![Eksplorator rozwiązań przedstawiający środowisko domyślne](media/quickstart-python-02-default-environment-2019.png)

2. Kliknij prawym przyciskiem myszy środowisko i wybierz polecenie **Zarządzaj pakietami Python..**.. To polecenie otwiera okno **środowiska Python** na karcie **pakiety (PyPI)** .

3. Wprowadź "kolbę" w polu wyszukiwania. Jeśli **zostanie** wyświetlona poniżej pola wyszukiwania, możesz pominąć ten krok. W przeciwnym razie wybierz pozycję **Uruchom polecenie: Kolba instalacyjna PIP**. Zaakceptuj wszelkie zapytanie dotyczące uprawnień administratora i postępuj zgodnie z oknem **danych wyjściowych** w programie Visual Studio. (Monit o podniesienie uprawnień występuje, gdy folder pakiety dla środowiska globalnego znajduje się w chronionym obszarze, takim jak *C:\Program Files*).

    ![Instalowanie biblioteki kolb przy użyciu narzędzia pip install](media/quickstart-python-03-install-package-2019.png)
::: moniker-end

4. Po zainstalowaniu Biblioteka pojawia się w środowisku w **Eksplorator rozwiązań**, co oznacza, że można z niej korzystać w kodzie języka Python.

    ::: moniker range="vs-2017"
    ![Biblioteka kolb zainstalowana i wyświetlana w Eksplorator rozwiązań](media/quickstart-python-04-package-installed.png)
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    ![Biblioteka kolb zainstalowana i wyświetlana w Eksplorator rozwiązań](media/quickstart-python-04-package-installed-2019.png)
    ::: moniker-end

> [!Note]
> Zamiast instalować biblioteki w środowisku globalnym, deweloperzy zwykle tworzą "środowisko wirtualne", w którym można zainstalować biblioteki dla określonego projektu. Szablony programu Visual Studio zazwyczaj oferują tę opcję, zgodnie z opisem w [przewodniku szybki start — Tworzenie projektu w języku Python przy użyciu szablonu](../python/quickstart-02-python-in-visual-studio-project-from-template.md).

**Pytanie: gdzie mogę dowiedzieć się więcej o innych dostępnych pakietach języka Python?**

**Odpowiedź**: Przejdź do [indeksu pakietu języka Python](https://pypi.org/).

## <a name="add-a-code-file"></a>Dodaj plik kodu

Teraz możesz dodać bit kodu języka Python, aby zaimplementować minimalną aplikację sieci Web.

1. Kliknij prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** a następnie wybierz pozycję **Dodaj > nowy element**.

1. W wyświetlonym oknie dialogowym wybierz pozycję **pusty plik**w języku Python, nadaj jej nazwę *App.py*i wybierz pozycję **Dodaj**. Program Visual Studio automatycznie otwiera plik w oknie edytora.

1. Skopiuj następujący kod i wklej go do *App.py*:

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

1. Być może zauważono, że okno dialogowe **dodawanie > nowego elementu** wyświetla wiele innych typów plików, które można dodać do projektu języka Python, w tym klasy języka Python, pakietu języka Python, testu jednostkowego języka Python, plików *web.config* i innych. Ogólnie rzecz biorąc, te szablony elementów, gdy są one wywoływane, to doskonały sposób na szybkie tworzenie plików przy użyciu użytecznego kodu standardowego.

**Pytanie: gdzie mogę dowiedzieć się więcej o kolbie?**

**Odpowiedź**: Zapoznaj się z dokumentacją kolby, rozpoczynając od [kolby szybkiego startu](https://flask.palletsprojects.com/en/1.1.x/quickstart/#quickstart).

## <a name="run-the-application"></a>Uruchamianie aplikacji

1. Kliknij prawym przyciskiem myszy pozycję *App.py* w **Eksplorator rozwiązań** i wybierz pozycję **Ustaw jako plik startowy**. To polecenie identyfikuje plik kodu do uruchomienia w języku Python podczas uruchamiania aplikacji.

    ::: moniker range="vs-2017"
    ![Ustawianie pliku startowego dla projektu w Eksplorator rozwiązań](media/quickstart-python-05-set-as-startup-file.png)
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    ![Ustawianie pliku startowego dla projektu w Eksplorator rozwiązań](media/quickstart-python-05-set-as-startup-file-2019.png)
    ::: moniker-end

2. Kliknij prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** i wybierz polecenie **Właściwości**. Następnie wybierz kartę **debugowanie** i ustaw właściwość **numer portu** na `4449` . Ten krok zapewnia, że program Visual Studio uruchamia przeglądarkę w `localhost:4449` celu dopasowania `app.run` argumentów w kodzie.

3. Wybierz pozycję **Debuguj > Uruchom bez debugowania** (**Ctrl** + **F5**), co spowoduje zapisanie zmian w plikach i uruchomienie aplikacji.

4. Zostanie wyświetlone okno polecenia z komunikatem **uruchomionym w protokole https: \/ /localhost: 4449**, a okno przeglądarki powinno być otwarte w `localhost:4449` miejscu, w którym jest wyświetlany komunikat "Hello, Python!" Żądanie GET jest również wyświetlane w oknie wiersza polecenia o stanie 200.

    Jeśli przeglądarka nie zostanie otwarta automatycznie, Uruchom wybraną przeglądarkę i przejdź do `localhost:4449` .

    Jeśli widzisz tylko interaktywną powłokę języka Python w oknie polecenia lub jeśli okno zostanie krótko przebłyskowe, upewnij się, że ustawiono *App.py* jako plik startowy w kroku 1 powyżej.

5. Przejdź do `localhost:4449/hello` , aby sprawdzić, czy dekoratora dla `/hello` zasobu również działa. Ponownie żądanie GET zostanie wyświetlone w oknie polecenia o stanie 200. Wypróbuj bezpłatny adres URL, aby sprawdzić, czy w oknie polecenia są wyświetlane kody stanu 404.

6. Zamknij okno wiersza polecenia, aby zatrzymać aplikację, a następnie zamknij okno przeglądarki.

**Pytanie: Jaka jest różnica między poleceniem Start bez debugowania a rozpoczęciem debugowania?**

**Odpowiedź**: Użyj opcji **Rozpocznij debugowanie** , aby uruchomić aplikację w kontekście [debugera programu Visual Studio](../python/debugging-python-in-visual-studio.md), co pozwala na ustawianie punktów przerwania, badanie zmiennych i przechodzenie krok po kroku przez wiersz kodu. Aplikacje mogą działać wolniej w debugerze z powodu różnych punktów zaczepienia, które umożliwiają debugowanie. **Uruchom bez debugowania**, w przeciwieństwie, uruchamia aplikację bezpośrednio tak jak wtedy, gdy uruchomiono ją z wiersza polecenia, bez kontekstu debugowania, a także automatycznie uruchamia przeglądarkę i przechodzi do adresu URL określonego na karcie **debugowanie** właściwości projektu.

## <a name="next-steps"></a>Następne kroki

Gratulujemy uruchomienia pierwszej aplikacji w języku Python w programie Visual Studio, w której wiesz już, jak używać programu Visual Studio jako środowiska IDE języka Python.

> [!div class="nextstepaction"]
> [Wdróż aplikację w Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md)

Ze względu na to, że kroki wykonywane w tym przewodniku Szybki Start są dość ogólne, prawdopodobnie zostało to spowodowane tym, że mogą one być zautomatyzowane. Takie Automatyzacja jest rolą szablonów projektów programu Visual Studio. Przejdź do [przewodnika Szybki Start — Tworzenie projektu w języku Python przy użyciu szablonu](../python/quickstart-02-python-in-visual-studio-project-from-template.md) pokazu, który tworzy aplikację sieci Web podobną do tej, która została utworzona w tym artykule, ale z mniejszą liczbą kroków.

Aby kontynuować pełen samouczek dotyczący języka Python w programie Visual Studio, w tym używanie interaktywnego okna, debugowania, wizualizacji danych i pracy z usługą git, przejdź przez [Samouczek: wprowadzenie do języka Python w programie Visual Studio](../python/tutorial-working-with-python-in-visual-studio-step-01-create-project.md).

Aby dowiedzieć się więcej o tym, że program Visual Studio jest oferowany, wybierz poniższe linki.

- Dowiedz się więcej [na temat szablonów aplikacji sieci Web w języku Python w programie Visual Studio](../python/python-web-application-project-templates.md).
- Informacje o [debugowaniu języka Python](../python/debugging-python-in-visual-studio.md)
- Więcej informacji na temat [środowiska IDE programu Visual Studio](../get-started/visual-studio-ide.md) jest ogólnie dostępne.

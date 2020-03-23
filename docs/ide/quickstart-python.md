---
title: 'Szybki start: tworzenie aplikacji internetowej języka Python za pomocą programu Visual Studio'
description: W tym przewodniku Szybki start można użyć visual studio i struktury Flask do tworzenia prostej aplikacji sieci web w języku Python.
ms.date: 03/07/2019
ms.technology: vs-python
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- python
- data-science
ms.openlocfilehash: cbb06ac800fd21e2354b04fb2e7e46306da7ed72
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "70180344"
---
# <a name="quickstart-create-your-first-python-web-app-using-visual-studio"></a>Szybki start: tworzenie pierwszej aplikacji internetowej języka Python przy użyciu programu Visual Studio

W tym 5-10 minut wprowadzenie do programu Visual Studio jako ide języka Python, należy utworzyć prostą aplikację sieci web języka Python na podstawie struktury Flask. Projekt można utworzyć za pomocą dyskretnych kroków, które ułatwiają zapoznanie się z podstawowymi funkcjami programu Visual Studio.

::: moniker range="vs-2017"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [pobierania programu Visual Studio,](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) aby zainstalować ją bezpłatnie. W instalatorze upewnij się, że wybierz obciążenie **deweloperów języka Python.**

::: moniker-end

::: moniker range=">=vs-2019"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [pobierania programu Visual Studio,](https://visualstudio.microsoft.com/downloads) aby zainstalować ją bezpłatnie. W instalatorze upewnij się, że wybierz obciążenie **deweloperów języka Python.**

::: moniker-end

## <a name="create-the-project"></a>Tworzenie projektu

Następujące kroki tworzą pusty projekt, który służy jako kontener dla aplikacji:

::: moniker range="vs-2017"
1. Otwórz program Visual Studio 2017.

2. Na górnym pasku menu wybierz **pozycję Plik > Nowy projekt >**.

3. W oknie dialogowym **Nowy projekt** wpisz "Projekt python Web Project" w polu wyszukiwania w prawym górnym rogu, wybierz pozycję Projekt **sieci Web** na liście środkowej, nadaj projektowi nazwę w stylu "HelloPython", a następnie wybierz przycisk **OK**.

    ![Nowe okno dialogowe projektu z wybraną wybraną po wybraniem programu Python Web Project](media/quickstart-python-00-web-project.png)

    Jeśli nie widzisz szablonów projektu języka Python, uruchom **Instalator programu Visual Studio**, wybierz pozycję **Więcej** > **modyfikuj**, wybierz obciążenie **deweloperskie języka Python,** a następnie wybierz pozycję **Modyfikuj**.

    ![Obciążenie programistyczne języka Python w instalatorze programu Visual Studio](../python/media/installation-python-workload.png)

4. Nowy projekt zostanie otwarty w **Eksploratorze rozwiązań** w prawym okienku. Projekt jest pusty w tym momencie, ponieważ nie zawiera żadnych innych plików.

    ![Eksplorator rozwiązań przedstawiający nowo utworzony pusty projekt](media/quickstart-python-01-empty-project.png)
::: moniker-end

::: moniker range=">=vs-2019"
1. Otwórz program Visual Studio 2019.
2. Na ekranie startowym wybierz pozycję **Utwórz nowy projekt**.
3. W oknie **dialogowym Tworzenie nowego projektu** wprowadź "Python web" w polu wyszukiwania u góry, wybierz pozycję **Web Project** na liście środkowej, a następnie wybierz pozycję **Dalej:**

    ![Tworzenie nowego ekranu projektu z wybraną wybraną pozycją Python Web Project](media/quickstart-python-00-web-project-2019a.png)

    Jeśli nie widzisz szablonów projektu języka Python, uruchom **Instalator programu Visual Studio**, wybierz pozycję **Więcej** > **modyfikuj**, wybierz obciążenie **deweloperskie języka Python,** a następnie wybierz pozycję **Modyfikuj**.

    ![Obciążenie programistyczne języka Python w instalatorze programu Visual Studio](../python/media/installation-python-workload.png)

4. W wyświetlonym oknie dialogowym **Konfigurowanie nowego projektu** wprowadź "HelloPython" dla **nazwy projektu**, określ lokalizację i wybierz pozycję **Utwórz**. (Nazwa **rozwiązania** jest automatycznie ustawiona tak, aby odpowiadała **nazwie projektu).**

    ![Konfigurowanie nowego okna dialogowego projektu](media/quickstart-python-00-web-project-2019b.png)

5. Nowy projekt zostanie otwarty w **Eksploratorze rozwiązań** w prawym okienku. Projekt jest pusty w tym momencie, ponieważ nie zawiera żadnych innych plików.

    ![Eksplorator rozwiązań przedstawiający nowo utworzony pusty projekt](media/quickstart-python-01-empty-project-2019.png)
::: moniker-end

**Pytanie: Jakie są zalety tworzenia projektu w programie Visual Studio dla aplikacji Języka Python?**

**Odpowiedź**: Aplikacje Python są zazwyczaj definiowane przy użyciu tylko folderów i plików, ale ta prosta struktura może stać się uciążliwa, ponieważ aplikacje stają się większe i być może obejmują automatycznie generowane pliki, JavaScript dla aplikacji internetowych i tak dalej. Projekt programu Visual Studio pomaga zarządzać tą złożonością. Projekt (plik *pyproj)* identyfikuje wszystkie pliki źródłowe i zawartości skojarzone z projektem, zawiera informacje o kompilacji dla każdego pliku, przechowuje informacje do integracji z systemami kontroli źródła i pomaga zorganizować aplikację w składniki logiczne.

**Pytanie: Co to jest "rozwiązanie" pokazane w Eksploratorze rozwiązań?**

**Odpowiedź:** Rozwiązanie programu Visual Studio to kontener, który pomaga zarządzać dla jednego lub więcej powiązanych projektów jako grupa i przechowuje ustawienia konfiguracji, które nie są specyficzne dla projektu. Projekty w rozwiązaniu mogą również odwoływać się do siebie nawzajem, tak że uruchomienie jednego projektu (aplikacja Języka Python) automatycznie tworzy drugi projekt (na przykład rozszerzenie C++ używane w aplikacji Języka Python).

## <a name="install-the-flask-library"></a>Zainstaluj bibliotekę Kolby

Aplikacje sieci Web w języku Python prawie zawsze używają jednej z wielu dostępnych bibliotek Języka Python do obsługi szczegółów niskiego poziomu, takich jak routing żądań sieci web i kształtowanie odpowiedzi. W tym celu program Visual Studio udostępnia wiele szablonów dla aplikacji sieci web, z których jeden jest używany w dalszej części tego przewodnika Szybki start.

W tym miejscu należy użyć następujących kroków, aby zainstalować bibliotekę Flask w domyślnym "środowisku globalnym", które program Visual Studio używa dla tego projektu.

::: moniker range="vs-2017"
1. Rozwiń węzeł **Środowiska języka Python** w projekcie, aby wyświetlić domyślne środowisko dla projektu.

    ![Eksplorator rozwiązań przedstawiający środowisko domyślne](media/quickstart-python-02-default-environment.png)

2. Kliknij prawym przyciskiem myszy środowisko i wybierz polecenie **Zainstaluj pakiet Python**. To polecenie otwiera okno **Środowiska języka Python** na karcie **Pakiety.**

3. Wprowadź "kolbę" w polu wyszukiwania i wybierz **pip install kolby z PyPI**. Zaakceptuj wszystkie monity o uprawnienia administratora i obserwuj okno **Dane wyjściowe** w programie Visual Studio dla postępu. (Monit o podniesienie uprawnień ma miejsce, gdy folder pakietów dla środowiska globalnego znajduje się w obszarze chronionym, takim jak *C:\Program Files).(* Monit o podniesienie uprawnień dzieje się, gdy folder pakietów dla środowiska globalnego znajduje się w obszarze chronionym, takich jak C:\Program Files ).)

    ![Instalacja biblioteki kolby za pomocą instalacji pip](media/quickstart-python-03-install-package.png)
::: moniker-end
::: moniker range=">=vs-2019"
1. Rozwiń węzeł **Środowiska języka Python** w projekcie, aby wyświetlić domyślne środowisko dla projektu.

    ![Eksplorator rozwiązań przedstawiający środowisko domyślne](media/quickstart-python-02-default-environment-2019.png)

2. Kliknij prawym przyciskiem myszy środowisko i wybierz pozycję **Zarządzaj pakietami Pythona...**. To polecenie otwiera okno **Środowiska języka Python** na karcie **Pakiety (PyPI).**

3. W polu wyszukiwania wpisz "kolbyę". Jeśli pod polem wyszukiwania pojawi się **Flask,** możesz pominąć ten krok. W przeciwnym razie wybierz **polecenie Uruchom: pip install flask**. Zaakceptuj wszystkie monity o uprawnienia administratora i obserwuj okno **Dane wyjściowe** w programie Visual Studio dla postępu. (Monit o podniesienie uprawnień ma miejsce, gdy folder pakietów dla środowiska globalnego znajduje się w obszarze chronionym, takim jak *C:\Program Files).(* Monit o podniesienie uprawnień dzieje się, gdy folder pakietów dla środowiska globalnego znajduje się w obszarze chronionym, takich jak C:\Program Files ).)

    ![Instalacja biblioteki kolby za pomocą instalacji pip](media/quickstart-python-03-install-package-2019.png)
::: moniker-end

4. Po zainstalowaniu biblioteka pojawia się w środowisku w **Eksploratorze rozwiązań,** co oznacza, że można z niej korzystać w kodzie Pythona.

    ::: moniker range="vs-2017"
    ![Biblioteka kolby zainstalowana i pokazowana w Eksploratorze rozwiązań](media/quickstart-python-04-package-installed.png)
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    ![Biblioteka kolby zainstalowana i pokazowana w Eksploratorze rozwiązań](media/quickstart-python-04-package-installed-2019.png)
    ::: moniker-end

> [!Note]
> Zamiast instalować biblioteki w środowisku globalnym, deweloperzy zazwyczaj tworzą "środowisko wirtualne", w którym mają być instalowane biblioteki dla określonego projektu. Szablony programu Visual Studio zazwyczaj oferują tę opcję, jak omówiono w [przewodnikach Szybki start — tworzenie projektu języka Python przy użyciu szablonu](../python/quickstart-02-python-in-visual-studio-project-from-template.md).

**Pytanie: Gdzie mogę dowiedzieć się więcej o innych dostępnych pakietach Pythona?**

**Odpowiedź**: Odwiedź [indeks pakietów Pythona](https://pypi.org/).

## <a name="add-a-code-file"></a>Dodawanie pliku kodu

Teraz możesz dodać trochę kodu Języka Python, aby zaimplementować minimalną aplikację internetową.

1. Kliknij prawym przyciskiem myszy projekt w **Eksploratorze rozwiązań** i wybierz polecenie **Dodaj > nowy element**.

1. W wyświetlonym oknie dialogowym wybierz pozycję **Pusty plik języka Python**, *nazwij*go app.py , a następnie wybierz pozycję **Dodaj**. Program Visual Studio automatycznie otwiera plik w oknie edytora.

1. Skopiuj następujący kod i wklej go do *app.py:*

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

1. Być może zauważyłeś, że okno dialogowe **Dodaj > Nowy element** wyświetla wiele innych typów plików, które można dodać do projektu Języka Python, w tym klasę Języka Python, pakiet Pythona, test jednostkowy języka Python, pliki *web.config* i inne. Ogólnie rzecz biorąc, te szablony elementów, jak są one nazywane, to świetny sposób, aby szybko tworzyć pliki z przydatnym kodem standardowego.

**Pytanie: Gdzie mogę dowiedzieć się więcej o Flask?**

**Odpowiedź**: Zapoznaj się z dokumentacją kolby, zaczynając od [szybkiego startu kolby](https://flask.palletsprojects.com/en/1.1.x/quickstart/#quickstart).

## <a name="run-the-application"></a>Uruchamianie aplikacji

1. Kliknij prawym przyciskiem myszy *app.py* w **Eksploratorze rozwiązań** i wybierz polecenie **Ustaw jako plik startowy**. To polecenie identyfikuje plik kodu do uruchomienia w języku Python podczas uruchamiania aplikacji.

    ::: moniker range="vs-2017"
    ![Ustawianie pliku startowego dla projektu w Eksploratorze rozwiązań](media/quickstart-python-05-set-as-startup-file.png)
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    ![Ustawianie pliku startowego dla projektu w Eksploratorze rozwiązań](media/quickstart-python-05-set-as-startup-file-2019.png)
    ::: moniker-end

2. Kliknij prawym przyciskiem myszy projekt w **Eksploratorze rozwiązań** i wybierz polecenie **Właściwości**. Następnie wybierz kartę **Debugowanie** i ustaw `4449`właściwość Numer **portu** na . Ten krok gwarantuje, że visual `localhost:4449` studio uruchamia `app.run` przeglądarkę, aby dopasować argumenty w kodzie.

3. Wybierz **opcję Debugowanie > Start Without Debugging** **(Ctrl**+**F5),** która zapisuje zmiany w plikach i uruchamia aplikację.

4. Pojawi się okno polecenia z komunikatem "* Uruchomiony w `localhost:4449` ", a okno przeglądarki powinno zostać otwarte w miejscu, w <https://localhost:4449/>którym zostanie wyświetlony komunikat "Hello, Python!" Żądanie GET pojawia się również w oknie polecenia o stanie 200.

    Jeśli przeglądarka nie otwiera się automatycznie, uruchom wybraną przeglądarkę i przejdź do `localhost:4449`.

    Jeśli w oknie polecenia jest widoczna tylko interaktywna powłoka Języka Python lub jeśli to okno miga na ekranie na krótko, upewnij się, że ustawisz *app.py* jako plik startowy w kroku 1 powyżej.

5. Przejdź `localhost:4449/hello` do, aby przetestować, `/hello` że dekorator dla zasobu również działa. Ponownie żądanie GET pojawia się w oknie polecenia o stanie 200. Możesz wypróbować inny adres URL, aby zobaczyć, że wyświetlają one 404 kody stanu w oknie polecenia.

6. Zamknij okno polecenia, aby zatrzymać aplikację, a następnie zamknij okno przeglądarki.

**Pytanie: Jaka jest różnica między poleceniem Start bez debugowania a rozpocznij debugowanie?**

**Odpowiedź:** Użyj **rozpocznij debugowania,** aby uruchomić aplikację w kontekście [debugera programu Visual Studio,](../python/debugging-python-in-visual-studio.md)co pozwala na ustawienie punktów przerwania, badanie zmiennych i krok po wierszu. Aplikacje mogą działać wolniej w debugerze ze względu na różne haki, które umożliwiają debugowanie. **Start Bez debugowania**, w przeciwieństwie, uruchamia aplikację bezpośrednio, tak jakby uruchomiono go z wiersza polecenia, bez kontekstu debugowania, a także automatycznie uruchamia przeglądarkę i przechodzi do adresu URL określonego w karcie **debugowania** właściwości projektu.

## <a name="next-steps"></a>Następne kroki

Gratulujemy uruchamiania pierwszej aplikacji Języka Python z programu Visual Studio, w której dowiedziałeś się trochę o używaniu programu Visual Studio jako ide pythona!

> [!div class="nextstepaction"]
> [Wdrażanie aplikacji w usłudze Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md)

Ponieważ kroki, które zostały opisane w tym Przewodniku Szybki start, są dość ogólne, prawdopodobnie zgadłeś, że mogą i powinny być zautomatyzowane. Taka automatyzacja jest rolą szablonów projektu programu Visual Studio. Przejdź przez [przewodnik Szybki start — utwórz projekt języka Python przy użyciu szablonu](../python/quickstart-02-python-in-visual-studio-project-from-template.md) dla demonstracji, która tworzy aplikację internetową podobną do tej utworzonej w tym artykule, ale z mniejszą liczbą kroków.

Aby kontynuować pełniejsze samouczek na temat języka Python w programie Visual Studio, w tym przy użyciu interaktywnego okna, debugowania, wizualizacji danych i pracy z gitem, przejdź przez [samouczek: Wprowadzenie do języka Python w programie Visual Studio](../python/tutorial-working-with-python-in-visual-studio-step-01-create-project.md).

Aby dowiedzieć się więcej, że visual studio ma do zaoferowania, wybierz łącza poniżej.

- Dowiedz się więcej o [szablonach aplikacji sieci Web języka Python w programie Visual Studio](../python/python-web-application-project-templates.md).
- Dowiedz się więcej o [debugowaniu języka Python](../python/debugging-python-in-visual-studio.md)
- Dowiedz się więcej o [ide programu Visual Studio](../get-started/visual-studio-ide.md) w ogóle.

---
title: Publikowanie aplikacji języka Python w usłudze Azure App Service w systemie Windows
description: Jak opublikować aplikację sieci Web języka Python bezpośrednio w usłudze Azure App Service w systemie Windows z programu Visual Studio, w tym niezbędną zawartość pliku web.config.
ms.date: 01/07/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: cf9125476a4fdc369cc22034e081f2151020f064
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62784664"
---
# <a name="publishing-to-azure-app-service-on-windows"></a>Publikowanie w usłudze Azure App Service w systemie Windows

> [!Note]
> Ta zawartość i opisane funkcje są przestarzałe, ale nadal działają. Deweloperzy języka Python są zachęcani do migracji do [usługi App Service w systemie Linux,](publishing-python-web-applications-to-azure-from-visual-studio.md) jeśli to możliwe.

Visual Studio udostępnia możliwość publikowania aplikacji sieci Web Języka Python bezpośrednio do usługi Azure App Service w systemie Windows. Publikowanie w usłudze Azure App Service w systemie Windows oznacza `web.config` kopiowanie niezbędnych plików na serwer i konfigurowanie odpowiedniego pliku, który instruuje serwer sieci web, jak uruchomić aplikację.

Proces publikowania różni się między programem Visual Studio 2017 i nowszym a programem Visual Studio 2015. W szczególności visual studio 2015 automatyzuje niektóre `web.config`kroki, w tym tworzenie , ale ta automatyzacja ogranicza długoterminową elastyczność i kontrolę. Visual Studio 2017 i nowsze wymaga więcej ręcznych kroków, ale zapewnia bardziej dokładną kontrolę nad środowiskiem Python. Obie opcje są opisane tutaj.

> [!Note]
> Aby uzyskać informacje na temat zmian między programami Visual Studio 2015 i Visual Studio 2017 i nowszymi, zobacz wpis w blogu [Publikowania na platformie Azure w programie Visual Studio 2017.](https://devblogs.microsoft.com/python/publish-to-azure-in-vs-2017/)

## <a name="prerequisites"></a>Wymagania wstępne

W tym instruktażu potrzebny jest projekt aplikacji sieci web oparty na strukturach Bottle, Flask lub Django. Jeśli nie masz jeszcze projektu i chcesz wypróbować proces publikowania, utwórz prosty projekt testowy w następujący sposób:

1. W programie Visual Studio wybierz **pozycję Plik > Nowy projekt >**, wyszukaj hasło "Butelka", wybierz projekt Bottle Web **Project**, określ i nazwij i ścieżkę projektu, kliknij przycisk **OK**. (Szablon Butelka jest dołączony do obciążenia deweloperskiego języka Python; zobacz [Instalacja](installing-python-support-in-visual-studio.md).)

1. Postępuj zgodnie z instrukcjami, aby zainstalować pakiety zewnętrzne, wybierając **pozycję Zainstaluj w środowisku wirtualnym** i preferowany tłumacz podstawowy dla środowiska wirtualnego. Zazwyczaj można dopasować ten wybór do wersji języka Python zainstalowany w usłudze App Service.

1. Przetestuj projekt lokalnie, naciskając klawisz F5 lub wybierając **debugowanie > Rozpocznij debugowanie**.

## <a name="create-an-azure-app-service"></a>Tworzenie usługi Azure App Service

Publikowanie na platformie Azure wymaga docelowej usługi aplikacji. W tym celu można utworzyć usługę app service przy użyciu subskrypcji platformy Azure lub można użyć witryny tymczasowej.

Jeśli nie masz jeszcze subskrypcji, zacznij od [bezpłatnego pełnego konta platformy Azure,](https://azure.microsoft.com/free/)które obejmuje hojne kredyty na usługi platformy Azure. Rozważ również zarejestrowanie się w [programie Visual Studio Dev Essentials,](https://azure.microsoft.com/pricing/member-offers/vs-dev-essentials/)który daje 25 USD kredytu co miesiąc przez cały rok.

> [!Tip]
> Mimo że platforma Azure prosi o kartę kredytową w celu zweryfikowania konta, karta nie jest obciążona. Możesz również ustawić [limit wydatków](/azure/billing/billing-spending-limit) równy darmowym kredytom, aby zagwarantować, że nie pojawią się żadne dodatkowe opłaty. Ponadto platforma Azure udostępnia bezpłatną warstwę planu usługi app service, która jest idealna dla prostych aplikacji testowych, zgodnie z opisem w następnej sekcji.

### <a name="using-a-subscription"></a>Korzystanie z subskrypcji

Dzięki aktywnej subskrypcji platformy Azure utwórz usługę app service z pustą aplikacją sieci Web w następujący sposób:

1. Zaloguj się na [portal.azure.com](https://portal.azure.com).
1. Wybierz **+Nowy**, a następnie wybierz pozycję **Web + Mobile,** a następnie aplikację Web **App**.
1. Określ nazwę aplikacji sieci web, pozostaw **grupę zasobów** na "Utwórz nowy" i wybierz pozycję **Windows** jako system operacyjny.
1. Wybierz **plan/lokalizację usługi aplikacji**, wybierz pozycję **Utwórz nowe**i określ nazwę i lokalizację. Następnie wybierz **pozycję Warstwa cenowa**, przewiń w dół do i wybierz plan **Wolny F1,** naciśnij **klawisz Select**, a następnie przycisk **OK,** a następnie **utwórz**.
1. (Opcjonalnie) Po utworzeniu usługi App Service przejdź do niej, wybierz pozycję **Pobierz profil publikowania**i zapisz plik lokalnie.

### <a name="using-a-temporary-app-service"></a>Korzystanie z tymczasowej usługi aplikacji

Utwórz tymczasową usługę aplikacji bez konieczności subskrypcji platformy Azure w następujący sposób:

1. Otwórz przeglądarkę, aby [try.azurewebsites.net](https://try.azurewebsites.net).
1. Wybierz **aplikację Web App** dla typu aplikacji, a następnie wybierz pozycję **Dalej**.
1. Wybierz **pozycję Pusta witryna,** a następnie **polecenie Utwórz**.
1. Zaloguj się za pomocą wybranego loginu społecznościowego, a po krótkim czasie twoja witryna jest gotowa pod wyświetlonym adresem URL.
1. Wybierz pozycję Pobierz profil `.publishsettings` **publikowania** i zapisz plik, którego używasz później.

## <a name="configure-python-on-azure-app-service"></a>Konfigurowanie usługi Python w usłudze Azure App Service

Po uruchomieniu usługi App Service z pustą aplikacją sieci Web (w ramach subskrypcji lub w bezpłatnej witrynie) zainstaluj wybraną wersję języka Python zgodnie z [opisem Zarządzanie pythonem w usłudze Azure App Service.](managing-python-on-azure-app-service.md) Aby opublikować z programu Visual Studio 2017 i nowszych, należy zarejestrować dokładną ścieżkę do interpretera języka Python zainstalowanego z rozszerzeniem lokacji, zgodnie z opisem w tym artykule.

W razie potrzeby można `bottle` również zainstalować pakiet przy użyciu procesu w tych instrukcjach, ponieważ ten pakiet jest zainstalowany jako część innych kroków w tym instruktażu.

## <a name="publish-to-app-service---visual-studio-2017-and-later"></a>Publikowanie w usłudze App Service — Visual Studio 2017 i nowsze

Publikowanie w usłudze Azure App Service z programu Visual Studio 2017 i później kopiuje tylko pliki w projekcie na serwerze. W związku z tym konieczne jest utworzenie plików niezbędnych do skonfigurowania środowiska serwera.

1. W **Eksploratorze rozwiązań**programu Visual Studio kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Dodaj > Nowy element...**. W wyświetlonym oknie dialogowym wybierz szablon "Azure web.config (Fast CGI)" i wybierz przycisk OK. Spowoduje to utworzenie pliku `web.config` w katalogu głównym projektu.

1. Zmodyfikuj `PythonHandler` wpis, `web.config` aby ścieżka była zgodna z instalacją języka Python na serwerze (szczegółowe informacje można znaleźć w [odwołaniu do konfiguracji usług IIS](https://www.iis.net/configreference) (iis.net). Na przykład dla języka Python 3.6.1 x64 wpis powinien być wyświetlany w następujący sposób:

    ```xml
    <system.webServer>
      <handlers>
        <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule"
            scriptProcessor="D:\home\Python361x64\python.exe|D:\home\Python361x64\wfastcgi.py"
            resourceType="Unspecified" requireAccess="Script"/>
      </handlers>
    </system.webServer>
    ```

1. Ustaw `WSGI_HANDLER` wpis `web.config` w odpowiednim dla używanej struktury:

    - **Butelka**: dodać nawiasy `app.wsgi_app` po jak pokazano poniżej. Jest to konieczne, ponieważ ten `app.py`obiekt jest funkcją (patrz ) a nie zmienną:

        ```xml
        <!-- Bottle apps only -->
        <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
        ```

    - **Kolba**: Zmień `WSGI_HANDLER` wartość `<project_name>.app` `<project_name>` na miejsce odpowiadające nazwie projektu. Możesz znaleźć dokładny identifer, patrząc `from <project_name> import app` na `runserver.py`oświadczenie w . Na przykład jeśli projekt nosi nazwę "FlaskAzurePublishExample", wpis będzie wyświetlany w następujący sposób:

        ```xml
        <!-- Flask apps only: change the project name to match your app -->
        <add key="WSGI_HANDLER" value="FlaskAzurePublishExample.app"/>
        ```

    - **Django**: Potrzebne są `web.config` dwie zmiany w projektach Django. Najpierw zmień `WSGI_HANDLER` wartość `django.core.wsgi.get_wsgi_application()` na (obiekt znajduje `wsgi.py` się w pliku):

        ```xml
        <!-- Django apps only -->
        <add key="WSGI_HANDLER" value="django.core.wsgi.get_wsgi_application()"/>
        ```

        Po drugie, dodaj następujący wpis `WSGI_HANDLER`poniżej tego, który ma zastąpić `DjangoAzurePublishExample` nazwą projektu:

        ```xml
        <add key="DJANGO_SETTINGS_MODULE" value="DjangoAzurePublishExample.settings" />
        ```

1. **Tylko aplikacje Django**: W `settings.py` pliku projektu Django dodaj `ALLOWED_HOSTS` domenę adresu URL witryny, jak pokazano poniżej, zastępując "vspython-test-02.azurewebsites.net" adresem URL, oczywiście:

    ```python
    # Change the URL to your specific site
    ALLOWED_HOSTS = ['vspython-test-02.azurewebsites.net']
    ```

    Nie można dodać adresu URL do tablicy powoduje błąd "DisallowedHost at\</\>Invalid HTTP_HOST header: ' adres URL witryny '. Do ALLOWED_HOSTS może\<być\>konieczne dodanie adresu URL witryny."

    Zauważ, że gdy tablica jest pusta, Django automatycznie zezwala na "localhost", ale dodanie produkcyjnego adresu URL powoduje usunięcie tych możliwości. Z tego powodu można zachować oddzielne kopie `settings.py`rozwoju i produkcji , lub użyć zmiennych środowiskowych do kontrolowania wartości czasu wykonywania.

1. W **Eksploratorze rozwiązań**rozwiń folder o takiej `static` samej nazwie jak projekt, kliknij prawym przyciskiem myszy folder, wybierz polecenie **Dodaj > Nowy element...**, wybierz szablon "Azure static files web.config" i wybierz przycisk **OK**. Ta akcja spowoduje utworzenie kolejnego pliku `web.config` w folderze `static`, co z kolei spowoduje wyłączenie przetwarzania języka Python dla tego folderu. Ta konfiguracja wysyła żądania dotyczące plików statycznych do domyślnego serwera internetowego, zamiast korzystać z aplikacji Python.

1. Zapisz projekt, a następnie w **Eksploratorze rozwiązań**programu Visual Studio kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Publikuj**.

    ![Polecenie Publikowania w menu kontekstowym projektu](media/template-web-publish-command.png)

1. Na wyświetlej kartę **Publikowanie** wybierz miejsce docelowe publikowania:

    a. Twoja własna subskrypcja platformy Azure: wybierz usługę **Microsoft Azure App Service**, a następnie wybierz pozycję **Istniejąca,** a następnie **pozycję Publikuj**. Zostanie wyświetlone okno dialogowe, w którym można wybrać odpowiednią subskrypcję i usługę aplikacji. Jeśli usługa App Service nie jest wyświetlana, użyj pobranego profilu publikowania, jak opisano poniżej, dla tymczasowej usługi APp.

    ![Publikowanie w usłudze Azure krok 1, Visual Studio 2017 i nowsze, istniejące subskrypcje](media/tutorials-common-publish-1a-2017.png)

    b. Jeśli używasz tymczasowej usługi app service na try.azurewebsites.net lub w inny sposób **>** musisz użyć profilu publikowania, wybierz formant, aby znaleźć **profil importu**, wybierz tę opcję, a następnie wybierz pozycję **Publikuj**. Spowoduje to wyświetlenie monitu o lokalizację pobranego `.publishsettings` wcześniej pliku.

    ![Publikowanie w usłudze Azure krok 1, Visual Studio 2017 i nowszych, tymczasowa usługa aplikacji](media/tutorials-common-publish-1b-2017.png)

1. Program Visual Studio wyświetla stan publikowania w oknie "Aktywność publikowania w sieci Web" i w oknie Publikowania. Po zakończeniu publikowania domyślna przeglądarka zostanie otwarta w adresie URL witryny. Adres URL jest również wyświetlany w oknie Publikowanie.

1. Po otwarciu przeglądarki może zostać wyświetlony komunikat "Strona nie może być wyświetlana, ponieważ wystąpił błąd serwera wewnętrznego". Ten komunikat wskazuje, że środowisko Języka Python na serwerze nie jest w pełni skonfigurowane, w którym to przypadku wykonaj następujące czynności:

    a. Zapoznaj się ponownie [z zarządzaniem programem Python w usłudze Azure App Service,](managing-python-on-azure-app-service.md)upewniając się, że masz zainstalowane odpowiednie rozszerzenie witryny Języka Python.

    b. Sprawdź dokładnie ścieżkę do interpretera `web.config` języka Python w pliku. Ścieżka musi dokładnie odpowiadać lokalizacji instalacji wybranego rozszerzenia lokacji.

    d. Użyj konsoli Kudu, aby uaktualnić wszystkie `requirements.txt` pakiety wymienione w pliku aplikacji: przejdź `web.config`do `/home/python361x64`tego samego folderu Języka Python, który jest używany w , na przykład , i uruchom następujące polecenie, jak opisano w sekcji [Konsoli Kudu:](managing-python-on-azure-app-service.md#azure-app-service-kudu-console)

    ```command
    python -m pip install --upgrade -r /home/site/wwwroot/requirements.txt
    ```

    Jeśli podczas uruchamiania tego polecenia są widoczne błędy uprawnień, sprawdź, czy jest uruchamiane polecenie w folderze rozszerzenia lokacji, a *nie* w folderze jednej z domyślnych instalacji języka Python usługi App Service. Ponieważ nie można zmodyfikować tych środowisk domyślnych, próba zainstalowania pakietów z pewnością nie powiedzie się.

    d. Aby uzyskać szczegółowe dane wyjściowe `web.config` błędu, dodaj następujący wiersz do `<system.webServer>` węźle, który zapewnia bardziej szczegółowe dane wyjściowe błędu:

    ```xml
    <httpErrors errorMode="Detailed"></httpErrors>
    ```

    e. Spróbuj ponownie uruchomić usługę App Service po zainstalowaniu nowych pakietów. Ponowne uruchomienie nie jest `web.config`konieczne podczas zmiany, ponieważ `web.config` usługa App Service uruchamia automatyczne ponowne uruchamianie za każdym razem, gdy się zmieni.

    > [!Tip]
    > Jeśli wprowadzisz jakiekolwiek zmiany w pliku `requirements.txt` aplikacji, zainstaluj ponownie wszystkie pakiety wymienione w tym pliku, używając konsoli Kudu.

1. Po całkowitym skonfigurowaniu środowiska serwera odśwież stronę w przeglądarce. Powinna zostać wyświetlona aplikacja internetowa.

    ![Wyniki publikowania aplikacji Bottle, Flask i Django w usłudze App Service](media/azure-publish-results.png)

## <a name="publishing-to-app-service---visual-studio-2015"></a>Publikowanie w usłudze app service — Visual Studio 2015

> [!Note]
> Krótki film wideo z tego procesu można znaleźć w [programie Visual Studio Python Samouczek: Tworzenie witryny sieci Web](https://www.youtube.com/watch?v=FJx5mutt1uk&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=6) (youtube.com, 3m10s).

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt, wybierz pozycję **Publikuj**.

1. W oknie dialogowym **Publikowanie** wybierz pozycję **Microsoft Azure App Service**:

  ![Publikowanie w usłudze Azure krok 1](media/tutorials-common-publish-1.png)

1. Wybierz cel:

    - Jeśli masz subskrypcję platformy Azure, wybierz microsoft **azure app service** jako miejsce docelowe publikowania, a następnie w poniższym oknie dialogowym wybierz istniejącą usługę app service lub wybierz **nowy,** aby utworzyć nowy.
    - Jeśli używasz witryny tymczasowej z try.azurewebsites.net, wybierz **pozycję Importuj** jako `.publishsettings` miejsce docelowe publikowania, a następnie wyszukaj plik pobrany z witryny i wybierz **przycisk OK**.

1. Szczegóły usługi app service są wyświetlane **na** karcie **Połączenie** okna publikowania poniżej.

  ![Publikowanie w kroku 2 platformy Azure](media/tutorials-common-publish-2.png)

1. **Wybierz następną >** w razie potrzeby, aby przejrzeć dodatkowe ustawienia.

1. Wybierz pozycję **Publikuj**. Po wdrożeniu aplikacji na platformie Azure domyślna przeglądarka zostanie otwarta w tej witrynie.

W ramach tego procesu program Visual Studio wykonuje również następujące kroki:

- Utwórz `web.config` plik na serwerze, który zawiera odpowiednie `wsgi_app` wskaźniki do funkcji aplikacji i do domyślnego interpretera języka Python 3.4 usługi App Service.
- Wyłącz przetwarzanie plików w `static` folderze projektu (reguły `web.config`dla tego są w ).
- Opublikuj środowisko wirtualne na serwerze.
- Dodaj `web.debug.config` plik i narzędzia debugowania ptvsd, aby włączyć zdalne debugowanie.

Jak wspomniano wcześniej, te automatyczne kroki upraszczają proces publikowania, ale utrudniają kontrolowanie środowiska Języka Python. Na przykład `web.config` plik jest tworzony tylko na serwerze, ale nie jest dodawany do projektu. Proces publikowania trwa również dłużej, ponieważ jest kopiowanie całego środowiska wirtualnego z komputera deweloperskiego, a nie poleganie na konfiguracji serwera.

Ostatecznie można zachować własny `web.config` plik i `requirements.txt` używać do obsługi pakietów na serwerze bezpośrednio. Korzystanie `requirements.txt`, w szczególności, gwarantuje, że środowiska deweloperów i serwerów zawsze pasują.

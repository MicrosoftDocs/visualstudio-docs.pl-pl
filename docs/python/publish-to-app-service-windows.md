---
title: Publikowanie aplikacji w języku Python w celu Azure App Service w systemie Windows
description: Jak opublikować aplikację sieci Web w języku Python bezpośrednio do Azure App Service w systemie Windows z programu Visual Studio, w tym z niezbędną zawartością pliku web.config.
ms.date: 01/07/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: af3e7c2d74a9d7b3a95ae24bba37981822247728
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912557"
---
# <a name="publishing-to-azure-app-service-on-windows"></a>Publikowanie w usłudze Azure App Service w systemie Windows

> [!Note]
> Ta zawartość i opisane funkcje są przestarzałe, ale nadal działają. Deweloperzy języka Python zachęcamy do migracji do [App Service w systemie Linux](publishing-python-web-applications-to-azure-from-visual-studio.md) , jeśli jest to możliwe.

Program Visual Studio oferuje możliwość publikowania aplikacji sieci Web w języku Python bezpośrednio do Azure App Service w systemie Windows. Publikowanie w Azure App Service w systemie Windows oznacza skopiowanie niezbędnych plików na serwer i skonfigurowanie odpowiedniego `web.config` pliku, który instruuje serwer sieci Web, jak uruchomić aplikację.

Proces publikowania różni się od programu Visual Studio 2017 lub nowszego oraz programu Visual Studio 2015. W szczególności program Visual Studio 2015 automatyzuje niektóre kroki, w tym tworzenie `web.config` , ale ta Automatyzacja ogranicza długoterminową elastyczność i kontrolę. Program Visual Studio 2017 i nowsze wymagają dalszych czynności ręcznych, ale zapewnia bardziej dokładną kontrolę nad środowiskiem Python. Obie opcje zostały opisane tutaj.

> [!Note]
> Aby uzyskać ogólne zmiany między programem Visual Studio 2015 i programem Visual Studio 2017 lub nowszym, zobacz wpis w blogu [Publikowanie na platformie Azure w programie Visual Studio 2017](https://devblogs.microsoft.com/python/publish-to-azure-in-vs-2017/).

## <a name="prerequisites"></a>Wymagania wstępne

W tym instruktażu potrzebny jest projekt aplikacji sieci Web oparty na strukturze butelek, kolb lub Django. Jeśli nie masz jeszcze projektu i chcesz wypróbować proces publikowania, Utwórz prosty projekt testowy w następujący sposób:

1. W programie Visual Studio wybierz kolejno pozycje **plik > nowy > projekt**, wyszukaj ciąg "butelka", wybierz **Projekt sieci Web**, podaj nazwę i ścieżkę do projektu, a następnie wybierz **przycisk OK**. (Szablon butelki jest dołączony do obciążenia programowania w języku Python; zobacz [Instalacja](installing-python-support-in-visual-studio.md)).

1. Postępuj zgodnie z monitami, aby zainstalować pakiety zewnętrzne, wybierając opcję **Zainstaluj w środowisku wirtualnym** i preferowanym interpreterem podstawowym dla środowiska wirtualnego. Ten wybór jest zazwyczaj zgodny z wersją języka Python zainstalowaną na App Service.

1. Przetestuj projekt lokalnie, naciskając klawisz F5 lub wybierając pozycję **debuguj > Rozpocznij debugowanie**.

## <a name="create-an-azure-app-service"></a>Tworzenie usługi Azure App Service

Publikowanie na platformie Azure wymaga App Service docelowej. W tym celu można utworzyć App Service przy użyciu subskrypcji platformy Azure lub lokacji tymczasowej.

Jeśli nie masz jeszcze subskrypcji, Zacznij od [bezpłatnego pełnego konta platformy Azure](https://azure.microsoft.com/free/), które obejmuje kredyty Generous dla usług platformy Azure. Rozważ także zarejestrowanie się w usłudze [Visual Studio Dev Essentials](https://azure.microsoft.com/pricing/member-offers/vs-dev-essentials/), co oznacza, że w każdym miesiącu zostanie $25 za każdy miesiąc.

> [!Tip]
> Mimo że platforma Azure prosi o podanie karty kredytowej do zweryfikowania Twojego konta, karta nie jest naliczana. Możesz również ustawić [limit wydatków](/azure/billing/billing-spending-limit) równy bezpłatnym środkom, aby zagwarantować, że nie nastąpią żadne dodatkowe opłaty. Ponadto platforma Azure udostępnia bezpłatną warstwę planu App Service, która jest idealnym rozwiązaniem dla prostych aplikacji testowych, zgodnie z opisem w następnej sekcji.

### <a name="using-a-subscription"></a>Korzystanie z subskrypcji

Korzystając z aktywnej subskrypcji platformy Azure, Utwórz App Service z pustą aplikacją sieci Web w następujący sposób:

1. Zaloguj się pod adresem [Portal.Azure.com](https://portal.azure.com).
1. Wybierz pozycję **+ Nowy**, a następnie wybierz pozycję **Sieć Web + aplikacje mobilne** po której następuje **aplikacja internetowa**.
1. Określ nazwę aplikacji sieci Web, pozostaw **grupę zasobów** na "Utwórz nową" i wybierz **system Windows** jako system operacyjny.
1. Wybierz pozycję **Plan/Lokalizacja usługi App Service**, wybierz pozycję **Utwórz nową**, a następnie określ nazwę i lokalizację. Następnie wybierz pozycję **warstwa cenowa**, przewiń w dół do, a następnie wybierz pozycję **F1 bezpłatnie** , naciśnij **pozycję Wybierz**, a następnie przycisk **OK** , a następnie **Utwórz**.
1. Obowiązkowe Po utworzeniu App Service przejdź do niego, wybierz pozycję **Pobierz profil publikowania** i Zapisz plik lokalnie.

### <a name="using-a-temporary-app-service"></a>Używanie tymczasowego App Service

Utwórz tymczasową App Service bez potrzeby subskrypcji platformy Azure w następujący sposób:

1. Otwórz przeglądarkę w programie [https://azure.microsoft.com/try/app-service/web/](https://azure.microsoft.com/try/app-service/web/) .
1. Wybierz pozycję **aplikacja sieci Web** dla typu aplikacji, a następnie wybierz pozycję **dalej**.
1. Wybierz **pustą lokację**, a następnie pozycję **Utwórz**.
1. Zaloguj się przy użyciu dowolnie wybranego konta i po krótkim czasie, gdy witryna będzie gotowa na wyświetlony adres URL.
1. Wybierz pozycję **Pobierz profil publikowania** i Zapisz `.publishsettings` plik, którego używasz później.

## <a name="configure-python-on-azure-app-service"></a>Konfigurowanie języka Python na Azure App Service

Gdy masz App Service z pustą aplikacją internetową działającą w ramach subskrypcji lub w bezpłatnej lokacji), zainstaluj wybraną wersję języka Python, jak opisano w temacie Zarządzanie językiem [Python na platformie Azure App Service](managing-python-on-azure-app-service.md). W przypadku publikowania z programu Visual Studio 2017 i nowszych należy zapisać dokładną ścieżkę do interpretera języka Python zainstalowanego z rozszerzeniem lokacji, zgodnie z opisem w tym artykule.

W razie potrzeby można również zainstalować `bottle` pakiet przy użyciu procesu w tych instrukcjach, ponieważ ten pakiet jest instalowany w ramach innych kroków w tym instruktażu.

## <a name="publish-to-app-service---visual-studio-2017-and-later"></a>Publikowanie w programie App Service — Visual Studio 2017 i nowszych

Publikowanie w Azure App Service z programu Visual Studio 2017 i nowsze kopiuje tylko pliki w projekcie do serwera programu. W związku z tym konieczne jest utworzenie plików niezbędnych do skonfigurowania środowiska serwera.

1. W programie Visual Studio **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy projekt, a następnie wybierz pozycję **Dodaj > nowy element.**... W wyświetlonym oknie dialogowym wybierz szablon "Azure web.config (Fast CGI)", a następnie kliknij przycisk OK. Spowoduje to utworzenie pliku `web.config` w katalogu głównym projektu.

1. Zmodyfikuj `PythonHandler` wpis w `web.config` tak, aby ścieżka była zgodna z instalacją języka Python na serwerze (zobacz [Dokumentacja konfiguracji usług IIS](https://www.iis.net/configreference) (IIS.NET), aby uzyskać dokładne informacje. Na przykład w przypadku języka Python 3.6.1 x64 wpis powinien wyglądać następująco:

    ```xml
    <system.webServer>
      <handlers>
        <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule"
            scriptProcessor="D:\home\Python361x64\python.exe|D:\home\Python361x64\wfastcgi.py"
            resourceType="Unspecified" requireAccess="Script"/>
      </handlers>
    </system.webServer>
    ```

1. Ustaw `WSGI_HANDLER` wpis w `web.config` odpowiednim obszarze dla używanej platformy:

    - **Butelka**: Dodaj nawiasy po `app.wsgi_app` poniższej ilustracji. Jest to konieczne, ponieważ ten obiekt jest funkcją (zobacz `app.py` ), a nie zmienną:

        ```xml
        <!-- Bottle apps only -->
        <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
        ```

    - **Kolba**: Zmień `WSGI_HANDLER` wartość na `<project_name>.app` gdzie `<project_name>` pasuje do nazwy projektu. Dokładne identyfikator można znaleźć, przeglądając `from <project_name> import app` instrukcje w temacie `runserver.py` . Na przykład jeśli projekt ma nazwę "FlaskAzurePublishExample", wpis będzie wyglądać następująco:

        ```xml
        <!-- Flask apps only: change the project name to match your app -->
        <add key="WSGI_HANDLER" value="FlaskAzurePublishExample.app"/>
        ```

    - **Django**: do projektów Django są konieczne dwie zmiany `web.config` . Najpierw Zmień `WSGI_HANDLER` wartość na `django.core.wsgi.get_wsgi_application()` (obiekt znajduje się w `wsgi.py` pliku):

        ```xml
        <!-- Django apps only -->
        <add key="WSGI_HANDLER" value="django.core.wsgi.get_wsgi_application()"/>
        ```

        Następnie Dodaj następujący wpis poniżej tego elementu `WSGI_HANDLER` , zastępując go `DjangoAzurePublishExample` nazwą projektu:

        ```xml
        <add key="DJANGO_SETTINGS_MODULE" value="DjangoAzurePublishExample.settings" />
        ```

1. **Tylko aplikacje Django**: w pliku projektu Django `settings.py` Dodaj domenę adresów URL witryny do `ALLOWED_HOSTS` jak pokazano poniżej, zastępując "vspython-test-02.azurewebsites.NET" adresem URL, oczywiście:

    ```python
    # Change the URL to your specific site
    ALLOWED_HOSTS = ['vspython-test-02.azurewebsites.net']
    ```

    Nie można dodać adresu URL do tablicy spowoduje wystąpienie błędu "DisallowedHost at/nieprawidłowy nagłówek HTTP_HOST:" \<site URL\> ". Może być konieczne dodanie " \<site URL\> " do ALLOWED_HOSTS ".

    Należy pamiętać, że gdy tablica jest pusta, Django automatycznie zezwala na "localhost", ale dodanie produkcyjnego adresu URL spowoduje usunięcie tych możliwości. Z tego powodu warto zachować osobne kopie i tworzenie kopii produkcyjnych `settings.py` lub użyć zmiennych środowiskowych w celu kontrolowania wartości czasu wykonywania.

1. W **Eksplorator rozwiązań** rozwiń folder o nazwie takiej samej jak projekt, kliknij prawym przyciskiem myszy `static` folder, wybierz pozycję **Dodaj > nowy element...**, wybierz szablon "Pliki statyczne platformy Azure web.config" i wybierz polecenie **OK**. Ta akcja spowoduje utworzenie kolejnego pliku `web.config` w folderze `static`, co z kolei spowoduje wyłączenie przetwarzania języka Python dla tego folderu. Ta konfiguracja wysyła żądania dotyczące plików statycznych do domyślnego serwera internetowego, zamiast korzystać z aplikacji Python.

1. Zapisz projekt, a następnie w programie Visual Studio **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Publikuj**.

    ![Polecenie Publikuj w menu kontekstowym projektu](media/template-web-publish-command.png)

1. Na wyświetlonej karcie **Publikowanie** wybierz miejsce docelowe publikowania:

    a. Twoja subskrypcja platformy Azure: wybierz pozycję **Microsoft Azure App Service**, a następnie **Wybierz pozycję istniejący** , po której następuje **Publikowanie**. Zostanie wyświetlone okno dialogowe, w którym można wybrać odpowiednią subskrypcję i usługę App Service. Jeśli App Service nie zostanie wyświetlona, użyj pobranego profilu publikowania zgodnie z poniższym opisem dla tymczasowej usługi APp Service.

    ![Publikowanie na platformie Azure krok 1, Visual Studio 2017 i nowszych, istniejące subskrypcje](media/tutorials-common-publish-1a-2017.png)

    b. Jeśli używasz tymczasowego App Service w try.azurewebsites.net lub w inny sposób chcesz użyć profilu publikowania, wybierz **>** kontrolkę, aby znaleźć pozycję **Importuj profil**, wybierz tę opcję, a następnie wybierz pozycję **Publikuj**. Zostanie wyświetlony komunikat z prośbą o `.publishsettings` pobraną wcześniej lokalizację pliku.

    ![Publikowanie na platformie Azure krok 1, Visual Studio 2017 lub nowszej, tymczasowej usłudze App Service](media/tutorials-common-publish-1b-2017.png)

1. Program Visual Studio Wyświetla stan publikowania w oknie "działanie publikowania w sieci Web" i oknie publikowania. Po zakończeniu publikowania w adresie URL witryny zostanie otwarta przeglądarka domyślna. Adres URL jest również wyświetlany w oknie publikowanie.

1. Po otwarciu przeglądarki może zostać wyświetlony komunikat "nie można wyświetlić strony, ponieważ wystąpił wewnętrzny błąd serwera". Ten komunikat oznacza, że środowisko Python na serwerze nie jest w pełni skonfigurowane, w takim przypadku należy wykonać następujące czynności:

    a. Ponownie zapoznaj się z [tematem zarządzanie językiem Python w Azure App Service](managing-python-on-azure-app-service.md), aby upewnić się, że masz zainstalowane odpowiednie rozszerzenie witryny języka Python.

    b. Sprawdź dwukrotnie ścieżkę do interpretera języka Python w `web.config` pliku. Ścieżka musi być dokładnie zgodna z lokalizacją instalacji wybranego rozszerzenia witryny.

    c. Użyj konsoli kudu, aby uaktualnić wszystkie pakiety wymienione w `requirements.txt` pliku aplikacji: Przejdź do tego samego folderu Python, który jest używany w programie `web.config` , na przykład `/home/python361x64` , i uruchom następujące polecenie zgodnie z opisem w sekcji [konsoli kudu](managing-python-on-azure-app-service.md#azure-app-service-kudu-console) :

    ```command
    python -m pip install --upgrade -r /home/site/wwwroot/requirements.txt
    ```

    Jeśli podczas uruchamiania tego polecenia są widoczne błędy uprawnień, należy sprawdzić, czy uruchomiono polecenie w folderze rozszerzenia witryny, a *nie* w folderze jednej z App Service domyślnych instalacji języka Python. Ponieważ nie można modyfikować tych środowisk domyślnych, próba instalacji pakietów nie powiedzie się.

    d. Aby uzyskać szczegółowe informacje o błędach, Dodaj następujący wiersz do `web.config` `<system.webServer>` węzła, który zawiera bardziej szczegółowe dane wyjściowe błędu:

    ```xml
    <httpErrors errorMode="Detailed"></httpErrors>
    ```

    e. Spróbuj ponownie uruchomić App Service po zainstalowaniu nowych pakietów. Ponowne uruchomienie nie jest konieczne w przypadku zmiany `web.config` , ponieważ App Service Automatyczne ponowne uruchomienie przy każdej `web.config` zmianie.

    > [!Tip]
    > Jeśli wprowadzisz jakiekolwiek zmiany w pliku `requirements.txt` aplikacji, zainstaluj ponownie wszystkie pakiety wymienione w tym pliku, używając konsoli Kudu.

1. Po całkowitym skonfigurowaniu środowiska serwera odśwież stronę w przeglądarce. Powinna zostać wyświetlona aplikacja internetowa.

    ![Wyniki publikowania aplikacji Bottle, Flask i Django w usłudze App Service](media/azure-publish-results.png)

## <a name="publishing-to-app-service---visual-studio-2015"></a>Publikowanie do App Service — Visual Studio 2015

> [!Note]
> Krótkie wideo tego procesu można znaleźć w [samouczku języka Python programu Visual Studio: kompilowanie witryny sieci Web](https://www.youtube.com/watch?v=FJx5mutt1uk&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=6) (YouTube.com, 3m10s).

1. W **Eksploratorze rozwiązań** kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Opublikuj**.

1. W oknie dialogowym **Publikowanie** wybierz pozycję **Microsoft Azure App Service**:

  ![Publikowanie na platformie Azure — krok 1](media/tutorials-common-publish-1.png)

1. Wybierz obiekt docelowy:

    - Jeśli masz subskrypcję platformy Azure, wybierz pozycję **Microsoft Azure App Service** jako element docelowy publikowania, a następnie w następującym oknie dialogowym wybierz istniejący App Service lub wybierz pozycję **Nowy** , aby utworzyć nowy.
    - Jeśli używasz tymczasowej lokacji z try.azurewebsites.net, wybierz pozycję **Importuj** jako element docelowy publikowania, a następnie wyszukaj `.publishsettings` plik pobrany z witryny i wybierz **przycisk OK**.

1. Szczegóły App Service są wyświetlane na karcie **połączenie** okna dialogowego **publikowania** poniżej.

  ![Publikowanie na platformie Azure — krok 2](media/tutorials-common-publish-2.png)

1. Wybierz pozycję **dalej >** w razie potrzeby, aby przejrzeć dodatkowe ustawienia.

1. Kliknij pozycję **Opublikuj**. Po wdrożeniu aplikacji na platformie Azure w tej witrynie zostanie otwarta przeglądarka domyślna.

W ramach tego procesu program Visual Studio wykonuje również następujące czynności:

- Utwórz `web.config` na serwerze plik zawierający odpowiednie wskaźniki do `wsgi_app` funkcji aplikacji oraz App Service domyślnego interpretera języka Python 3,4.
- Wyłącz przetwarzanie plików w `static` folderze projektu (reguły dla tego programu znajdują się w temacie `web.config` ).
- Opublikuj środowisko wirtualne na serwerze programu.
- Dodaj `web.debug.config` plik i narzędzia debugowania, aby włączyć debugowanie zdalne. W przypadku programu Visual Studio 2019 w wersji 16,4 i starszych narzędzia debugowania są ptvsd. W przypadku programu Visual Studio 2019 w wersji 16,5 lub nowszej narzędzia debugowania są debugpy.

Jak wspomniano wcześniej, te automatyczne kroki upraszczają proces publikowania, ale utrudniają kontrolowanie środowiska Python. Na przykład `web.config` plik jest tworzony tylko na serwerze, ale nie został dodany do projektu. Proces publikowania trwa również dłużej, ponieważ polega na kopiowaniu całego środowiska wirtualnego z komputera deweloperskiego, a nie poleganiu na konfiguracji serwera.

Na koniec warto zachować własny `web.config` plik i używać `requirements.txt` go do bezpośredniego przechowywania pakietów na serwerze. `requirements.txt`W szczególności program gwarantuje, że środowiska programistyczne i serwera są zawsze zgodne.

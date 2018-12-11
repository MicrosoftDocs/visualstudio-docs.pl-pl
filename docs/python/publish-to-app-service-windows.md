---
title: Publikowanie aplikacji w języku Python w usłudze Azure App Service na Windows
description: Jak opublikować aplikację sieci web Python bezpośrednio w usłudze Azure App Service na Windows w programie Visual Studio, w tym niezbędną treść w pliku web.config.
ms.date: 10/18/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: 083deb7b836bfae0b0c1352430ffb6ed4080c3dc
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248208"
---
# <a name="publishing-to-azure-app-service-on-windows"></a>Publikowanie w usłudze Azure App Service na Windows

> [!Note]
> Ta zawartość i funkcje opisane są przestarzałe, ale nadal działać. Zachęcamy programistów używających języka Python, aby dokonać migracji do [usługi App Service w systemie Linux](publishing-python-web-applications-to-azure-from-visual-studio.md) gdzie to możliwe.

Program Visual Studio oferuje możliwość publikowania aplikacji sieci web w języku Python bezpośrednio w usłudze Azure App Service na Windows. Publikowanie w usłudze Azure App Service w Windows oznacza kopiowanie wymaganych plików do serwera i konfigurowania odpowiednich `web.config` pliku, który powoduje, że serwer sieci web jak uruchomić aplikację.

Proces publikowania różni się od programu Visual Studio 2017 i Visual Studio 2015. W szczególności program Visual Studio 2015 automatyzuje niektóre kroki, w tym tworzenie `web.config`, ale taką automatyzację ogranicza długoterminowe elastyczność i kontrolę. Program Visual Studio 2017 wymaga dodatkowych ręcznych czynności, ale zapewnia dokładniejszą kontrolę nad środowiska Python. Obie opcje są opisane w tym miejscu.

> [!Note]
> Aby uzyskać podstawowe informacje dotyczące zmian między wersjami programu Visual Studio 2015 i Visual Studio 2017, zobacz w blogu, [Opublikuj na platformie Azure w programie Visual Studio 2017](https://blogs.msdn.microsoft.com/pythonengineering/2016/12/12/publish-to-azure-in-vs-2017/).

## <a name="prerequisites"></a>Wymagania wstępne

W ramach tego przewodnika należy projektu aplikacji sieci web, oparte na platformy Bottle, Flask i Django. Jeśli jeszcze nie masz projektu, aby ponowić proces publikowania, Utwórz projekt prosty test w następujący sposób:

1. W programie Visual Studio, wybierz **Plik > Nowy > Projekt**, wyszukaj "Bottle", wybierz **projektu sieci Web Bottle**, określ, jak i nazwę i ścieżkę do projektu, kliknij przycisk **OK**. (Szablon Bottle jest uwzględniany z pakietem roboczym programowania Python; zobacz [instalacji](installing-python-support-in-visual-studio.md).)

1. Postępuj zgodnie z monitami, aby zainstalować pakiety zewnętrzne, wybierając **zainstalować w środowisku wirtualnym** i preferowaną podstawowy interpreter dla środowiska wirtualnego. Ten wybór wersji języka Python zainstalowane w usłudze App Service jest zazwyczaj odpowiada.

1. Lokalnie przetestować projekt, naciskając klawisz F5 lub wybierając **Debuguj > Rozpocznij debugowanie**.

## <a name="create-an-azure-app-service"></a>Tworzenie usługi Azure App Service

Publikowanie na platformie Azure wymaga docelowej usługi App Service. W tym celu można utworzyć usługi App Service przy użyciu subskrypcji platformy Azure, możesz też tymczasową witrynę.

Jeśli nie masz jeszcze subskrypcji, skorzystaj z [bezpłatne konto Azure pełnej](https://azure.microsoft.com/free/), co obejmuje istnieją małe wymogi dotyczące środków na korzystanie z usług platformy Azure. Należy również rozważyć skorzystania [Visual Studio Dev Essentials](https://azure.microsoft.com/pricing/member-offers/vs-dev-essentials/), które zapewnia 25 USD środków co miesiąc przez cały rok.

> [!Tip]
> Mimo że Azure poprosi o podanie karty kredytowej zweryfikować swoje konto, karta nie jest rozliczane. Można również ustawić [limit wydatków](/azure/billing/billing-spending-limit) równa z bezpłatnych środków, aby zagwarantować, że występują nie dodatkowych opłat. Ponadto platforma Azure oferuje bezpłatne usługi App Service za warstwę planu, która doskonale nadaje się dla aplikacji prosty test, zgodnie z opisem w następnej sekcji.

### <a name="using-a-subscription"></a>Korzystanie z subskrypcji

Z aktywną subskrypcją platformy Azure Utwórz usługę App Service przy użyciu pusta aplikacja internetowa w następujący sposób:

1. Zaloguj się na [portal.azure.com](https://portal.azure.com).
1. Wybierz **+ nowy**, a następnie wybierz **sieci Web i mobilność** następuje **aplikacji sieci Web**.
1. Określ nazwę dla aplikacji sieci web, pozostaw **grupy zasobów** do "Utwórz nowy" i wybierz polecenie **Windows** jako system operacyjny.
1. Wybierz **plan App service/lokalizacja**, wybierz opcję **Utwórz nową**i określ nazwę i lokalizację. Następnie wybierz pozycję **warstwa cenowa**, przewiń w dół i wybierz **bezpłatna F1** planowanie, naciśnij klawisz **wybierz**, a następnie **OK** i następnie **Tworzenie**.
1. (Opcjonalnie) Po utworzeniu usługi App Service, przejdź do niego, wybierz **Pobierz profil publikowania**, a następnie zapisz plik lokalnie.

### <a name="using-a-temporary-app-service"></a>Przy użyciu tymczasowego App Service

Tworzenie tymczasowego usługi App Service bez subskrypcji platformy Azure w następujący sposób:

1. Otwórz przeglądarkę, aby [try.azurewebsites.net](https://try.azurewebsites.net).
1. Wybierz **aplikacji sieci Web** typ aplikacji, następnie wybierz **dalej**.
1. Wybierz **pusta witryna**, a następnie **Utwórz**.
1. Zaloguj się przy użyciu społecznościowych logowania wybranego i po pewnym czasie lokacja jest gotowa na wyświetlany adres URL.
1. Wybierz **Pobierz profil publikowania** i Zapisz `.publishsettings` pliku, który można użyć później.

## <a name="configure-python-on-azure-app-service"></a>Konfigurowanie języka Python w usłudze Azure App Service

Po utworzeniu usługi App Service z pustym uruchamiania aplikacji sieci Web (lub w ramach subskrypcji w bezpłatnej lokacji), zainstaluj wybranej wersji języka Python, zgodnie z opisem [zarządzania z językiem Python w usłudze Azure App Service](managing-python-on-azure-app-service.md). Publikowanie z programu Visual Studio 2017, zarejestruj się w dokładnej ścieżki do interpretera języka Python zainstalowane z rozszerzeniem lokacji zgodnie z opisem w tym artykule.

Jeśli to konieczne, możesz także zainstalować `bottle` pakietu przy użyciu procesu w tych instrukcjach, ponieważ ten pakiet jest zainstalowany jako część druga kroki opisane w tym przewodniku.

## <a name="publish-to-app-service---visual-studio-2017"></a>Publikowanie w usłudze App Service — program Visual Studio 2017

Publikowanie w usłudze Azure App Service z programu Visual Studio 2017 kopiuje tylko pliki w projekcie do serwera. Jest to konieczne, w związku z tym, aby utworzyć pliki niezbędne do skonfigurowania środowiska serwera.

1. W programie Visual Studio **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz **Dodaj > Nowy element...** . W wyświetlonym oknie dialogowym Wybieranie szablonu "Web.config Pro Azure (Fast CGI)" i następnie naciśnij przycisk OK. Spowoduje to utworzenie `web.config` pliku w katalogu głównym projektu.

1. Modyfikowanie `PythonHandler` wpis `web.config` tak, aby ścieżka odpowiada instalację języka Python na serwerze (zobacz [dokumentacja konfiguracji usług IIS](https://www.iis.net/configreference) (iis.net) dla szczegółowymi informacjami na temat). Na przykład w przypadku języka Python 3.6.1 x64 wpis powinna wyglądać następująco:

    ```xml
    <system.webServer>
      <handlers>
        <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule"
            scriptProcessor="D:\home\Python361x64\python.exe|D:\home\Python361x64\wfastcgi.py"
            resourceType="Unspecified" requireAccess="Script"/>
      </handlers>
    </system.webServer>
    ```

1. Ustaw `WSGI_HANDLER` wpis `web.config` odpowiednio dla struktury korzystasz:

    - **Bottle**: Dodawanie nawiasów po `app.wsgi_app` jak pokazano poniżej. Jest to konieczne, ponieważ ten obiekt jest funkcją (zobacz `app.py`) zamiast zmiennej:

        ```xml
        <!-- Bottle apps only -->
        <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
        ```

    - **Flask**: Zmiana `WSGI_HANDLER` wartość `<project_name>.app` gdzie `<project_name>` jest zgodna z nazwą projektu. Możesz znaleźć dokładny identyfikator, analizując `from <project_name> import app` instrukcji w `runserver.py`. Na przykład jeśli projekt ma nazwę "FlaskAzurePublishExample", wpis wyglądałby następująco:

        ```xml
        <!-- Flask apps only: change the project name to match your app -->
        <add key="WSGI_HANDLER" value="FlaskAzurePublishExample.app"/>
        ```

    - **Django**: Dwie zmiany są potrzebne do `web.config` dla projektów Django. Najpierw należy zmienić `WSGI_HANDLER` wartość `django.core.wsgi.get_wsgi_application()` (obiekt jest w `wsgi.py` pliku):

        ```xml
        <!-- Django apps only -->
        <add key="WSGI_HANDLER" value="django.core.wsgi.get_wsgi_application()"/>
        ```

        Po drugie, Dodaj następujący wpis poniżej dla `WSGI_HANDLER`, zastępując `DjangoAzurePublishExample` o nazwie projektu:

        ```xml
        <add key="DJANGO_SETTINGS_MODULE" value="DjangoAzurePublishExample.settings" />
        ```

1. **Tylko aplikacje Django**: W projekcie Django `settings.py` plików, Dodawanie domeny do adresu URL witryny `ALLOWED_HOSTS` jak pokazano poniżej, zastępując "vspython-test-02.azurewebsites .net" adres URL, oczywiście:

    ```python
    # Change the URL to your specific site
    ALLOWED_HOSTS = ['vspython-test-02.azurewebsites.net']
    ```

    Błąd podczas dodawania adresu URL do wyników tablicy w błędzie "DisallowedHost u / nieprawidłowy nagłówek HTTP_HOST:"\<adres URL witryny\>". Może być konieczne dodanie "\<adres URL witryny\>" Aby ALLOWED_HOSTS. "

    Należy pamiętać, że gdy tablica jest pusta, Django automatycznie umożliwia nazwy "Host_lokalny", ale dodanie adresu URL produkcji powoduje usunięcie tej możliwości. Aby z tego powodu należy zachować oddzielne deweloperskich i produkcyjnych kopii `settings.py`, lub użyj zmiennych środowiskowych, aby kontrolować wartości w czasie wykonywania.

1. W **Eksploratora rozwiązań**, rozwiń folder o nazwie taka sama jak projekt, kliknij prawym przyciskiem myszy `static` folderu, wybierz **Dodaj > Nowy element...** , a następnie wybierz szablon "Statycznych w usłudze Azure files web.config" i wybierz **OK**. Ta akcja powoduje utworzenie innego `web.config` w `static` folder, który wyłącza Python przetwarzania dla tego folderu. Ta konfiguracja wysyła żądania dotyczące plików statycznych do domyślnego serwera sieci web, a nie przy użyciu aplikacji języka Python.

1. Następnie zapisać projekt, w programie Visual Studio **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz **Publikuj**.

    ![Polecenia menu kontekstowego projektu publikowania](media/template-web-publish-command.png)

1. W **Publikuj** kartę, która pojawia się, zaznaczyć miejscem docelowym publikowania:

    a. Subskrypcja platformy Azure: Wybierz **Microsoft Azure App Service**, następnie **wybierz istniejącą** następuje **Publikuj**. Zostanie wyświetlone okno dialogowe, w którym można wybrać odpowiednią subskrypcję i usługi app service. Jeśli nie pojawia się usługa App Service, należy użyć pobrany profil publikowania, zgodnie z poniższym opisem dla tymczasowych usługi APp Service.

    ![Publikowanie do usługi Azure kroku 1, Visual Studio 2017, w przypadku istniejących subskrypcji](media/tutorials-common-publish-1a-2017.png)

    b. Jeśli korzystania tymczasowe usługi App Service na try.azurewebsites.net lub w przeciwnym razie należy użyć profilu publikowania, wybierz **>** formantu, aby znaleźć **Importuj profil**, wybierz tę opcję, następnie Wybierz **Publikuj**. Powoduje wyświetlenie monitu o podanie lokalizacji `.publishsettings` wcześniej pobrany plik.

    ![Publikowanie do usługi Azure kroku 1, Visual Studio 2017 tymczasową aplikację usługi](media/tutorials-common-publish-1b-2017.png)

1. Visual Studio Wyświetla stan publikowania w okna "Działanie publikowania w sieci Web" i publikacji. Po zakończeniu publikowania w domyślnej przeglądarce otworzy się adres URL witryny. Adres URL jest również wyświetlany w oknie publikowania.

1. Po otwarciu przeglądarki może zostać wyświetlony komunikat "nie można wyświetlić strony, ponieważ wystąpił błąd wewnętrzny serwera." Ten komunikat oznacza, że środowiska Python na serwerze nie jest w pełni skonfigurowany, w którym to przypadku wykonaj następujące czynności:

    a. Zapoznaj się ponownie do [zarządzania z językiem Python w usłudze Azure App Service](managing-python-on-azure-app-service.md), upewniając się, że masz odpowiednią języka Python zainstalowane rozszerzenie witryny.

    b. Dokładnie sprawdź ścieżkę do interpretera języka Python w swojej `web.config` pliku. Ścieżka musi dokładnie odpowiadać lokalizacji instalacji rozszerzenia wybranej witryny.

    c. Uaktualnij wszystkie pakiety wymienione w swojej aplikacji za pomocą konsoli Kudu `requirements.txt` pliku: Przejdź do tego samego folderu języka Python, który jest używany w `web.config`, takich jak `/home/python361x64`, i uruchom następujące polecenie, zgodnie z opisem w [Kudu konsoli](managing-python-on-azure-app-service.md#azure-app-service-kudu-console)sekcji:

    ```command
    python -m pip install --upgrade -r /home/site/wwwroot/requirements.txt
    ```

    Jeśli widzisz błędy uprawnień podczas uruchamiania tego polecenia, sprawdź, czy używasz polecenia w folderze rozszerzenia witryny i *nie* w folderze instalacji języka Python domyślnej usługi App Service. Ponieważ nie można modyfikować tych środowisk domyślne, bez obaw próby zainstalowania pakietów zakończy się niepowodzeniem.

    d. Dla danych wyjściowych szczegółowy komunikat o błędzie, należy dodać następujący wiersz do `web.config` w ramach `<system.webServer>` węzła, który umożliwia bardziej szczegółowe dane wyjściowe błędu:

    ```xml
    <httpErrors errorMode="Detailed"></httpErrors>
    ```

    e. Spróbuj ponownie uruchomić usługi App Service po zainstalowaniu nowych pakietów. Ponowne uruchomienie komputera nie jest konieczne w przypadku zmiany `web.config`, jak usługa App Service, automatyczne ponowne uruchomienie zawsze, gdy `web.config` zmiany.

    > [!Tip]
    > Jeśli wprowadzisz zmiany do swojej aplikacji `requirements.txt` pliku, pamiętaj ponownie użyć konsoli Kudu, aby zainstalować wszystkie pakiety, które są teraz wymienione w tym pliku.

1. Po skonfigurowaniu w pełni środowisko serwera, Odśwież stronę w przeglądarce i aplikacji sieci web powinna zostać wyświetlona.

    ![Wyniki publikowania aplikacji Bottle, Flask i Django w usłudze App Service](media/azure-publish-results.png)

## <a name="publishing-to-app-service---visual-studio-2015"></a>Publikowanie w usłudze App Service — program Visual Studio 2015

> [!Note]
> Krótki film tego procesu można znaleźć na [samouczek języka Python dla programu Visual Studio: Tworzenie witryny sieci Web](https://www.youtube.com/watch?v=FJx5mutt1uk&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=6) (witrynie youtube.com, 3m10s).

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy, wybierz projekt **Publikuj**.

1. W **Publikuj** okno dialogowe, wybierz opcję **Microsoft Azure App Service**:

  ![Publikowanie do usługi Azure, krok 1](media/tutorials-common-publish-1.png)

1. Wybieranie klasy docelowej:

    - Jeśli masz subskrypcję platformy Azure, wybierz **Microsoft Azure App Service** jako miejscem docelowym publikowania, następnie w oknie dialogowym poniżej wybierz istniejącej usługi App Service lub **New** Aby utworzyć nową.
    - Jeśli używasz tymczasową witrynę z try.azurewebsites.net wybierz **importu** jako miejscem docelowym publikowania, następnie Przeglądaj w poszukiwaniu `.publishsettings` plik pobrany z witryny i wybierz **OK**.

1. Szczegóły usługi App Service są wyświetlane w **Publikuj** okna dialogowego **połączenia** poniższej karcie.

  ![Publikowanie do usługi Azure, krok 2](media/tutorials-common-publish-2.png)

1. Wybierz **Dalej >** zgodnie z potrzebami, aby przejrzeć dodatkowe ustawienia.

1. Wybierz **publikowania**. Gdy aplikacja jest wdrażana na platformie Azure, domyślnej przeglądarki otwiera się w danej lokacji.

W ramach tego procesu Visual Studio wykona następujące czynności:

- Tworzenie `web.config` pliku na serwerze, który zawiera odpowiednie wskaźniki do aplikacji `wsgi_app` działać, a w usłudze App Service domyślnie języka Python 3.4 interpretera.
- Wyłącz przetwarzanie plików w projekcie `static` folder (reguł dla tego znajdują się w `web.config`).
- Opublikuj w środowisku wirtualnym na serwerze.
- Dodaj `web.debug.config` plików i ptvsd narzędzia, aby umożliwić debugowanie zdalne debugowanie.

Jak wspomniano wcześniej, te kroki automatyczne uprościć proces publikowania, ale utrudnić do kontrolowania środowiska Python. Na przykład `web.config` pliku jest tworzony tylko na serwerze, ale nie są dodawane do projektu. Proces publikowania również trwa dłużej, ponieważ ona jest kopiowanie środowiska zupełnie wirtualnego z komputera dewelopera zamiast polegania na konfigurację serwera.

Po pewnym czasie może chcesz zachować swoje własne `web.config` pliku i użyć `requirements.txt` bezpośrednio utrzymanie pakiety na serwerze. Za pomocą `requirements.txt`, w szczególności gwarantuje, że zawsze być zgodna swoje środowiska deweloperskie i serwera.

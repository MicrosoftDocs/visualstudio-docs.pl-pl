---
title: Konfigurowanie aplikacji sieci Web języka Python dla usług IIS
description: Jak skonfigurować aplikacje internetowe języka Python do uruchamiania z internetowymi usługami informacyjnymi z maszyny wirtualnej systemu Windows.
ms.date: 12/06/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: 551cff18849f0e8ad9fcd6f2c1e08561291b177f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62957376"
---
# <a name="configure-python-web-apps-for-iis"></a>Konfigurowanie aplikacji sieci Web języka Python dla usług IIS

Korzystając z internetowych usług informacyjnych (IIS) jako serwera sieci web na komputerze z systemem Windows (w tym [maszyn wirtualnych systemu Windows na platformie Azure,](/azure/architecture/reference-architectures/n-tier/windows-vm)aplikacje języka Python muszą zawierać określone ustawienia w swoich plikach *web.config,* aby usługi IIS mogły prawidłowo przetwarzać kod języka Python. Sam komputer musi mieć również zainstalowany język Python wraz z pakietami, których wymaga aplikacja internetowa.

> [!Note]
> Ten artykuł zawierał wcześniej wskazówki dotyczące konfigurowania języka Python w usłudze Azure App Service w systemie Windows. Rozszerzenia języka Python i hosty systemu Windows używane w tym scenariuszu zostały przestarzałe na rzecz usługi Azure App Service w systemie Linux. Aby uzyskać więcej informacji, zobacz [Publikowanie aplikacji języka Python w usłudze Azure App Service (Linux)](publishing-python-web-applications-to-azure-from-visual-studio.md). Poprzedni artykuł jest jednak nadal dostępny w serwisie [Zarządzanie aplikacjami w systemie Windows z rozszerzeniami Języka Python](managing-python-on-azure-app-service.md).

## <a name="install-python-on-windows"></a>Instalowanie języka Python w systemie Windows

Aby uruchomić aplikację internetową, najpierw zainstaluj wymaganą wersję języka Python bezpośrednio na komputerze-hoście systemu Windows, zgodnie z opisem w [programie Install Python interpreters](installing-python-interpreters.md).

Zapisz lokalizację tłumacza dla `python.exe` późniejszych kroków. Dla wygody można dodać tę lokalizację do zmiennej środowiskowej PATH.

## <a name="install-packages"></a>Instalowanie pakietów

Podczas korzystania z dedykowanego hosta, można użyć globalnego środowiska Python do uruchamiania aplikacji, a nie środowiska wirtualnego. W związku z tym można zainstalować wszystkie wymagania aplikacji w środowisku globalnym po prostu uruchamiając `pip install -r requirements.txt` w wierszu polecenia.

## <a name="set-webconfig-to-point-to-the-python-interpreter"></a>Ustawianie pliku web.config w celu wskazanie interpretera języka Python

Plik *web.config* aplikacji instruuje serwer sieci Web usług IIS (7+) uruchomiony w systemie Windows o tym, jak powinien obsługiwać żądania języka Python za pośrednictwem protokołu HttpPlatform (zalecane) lub FastCGI. Visual Studio w wersjach 2015 i wcześniejszych dokonać tych modyfikacji automatycznie. Korzystając z programu Visual Studio 2017 i nowszych, należy ręcznie zmodyfikować *web.config.*

### <a name="configure-the-httpplatform-handler"></a>Konfigurowanie programu obsługi httpplatform

Moduł HttpPlatform przekazuje połączenia gniazda bezpośrednio do samodzielnego procesu Pythona. Ten przekaz umożliwia uruchomienie dowolnego serwera sieci web, ale wymaga skryptu startowego, który uruchamia lokalny serwer sieci Web. Skrypt można określić `<httpPlatform>` w elemencie *web.config*, gdzie `processPath` atrybut wskazuje na `arguments` interpreter Języka Python rozszerzenia witryny, a atrybut wskazuje skrypt i wszelkie argumenty, które chcesz podać:

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.webServer>
    <handlers>
      <add name="PythonHandler" path="*" verb="*" modules="httpPlatformHandler" resourceType="Unspecified"/>
    </handlers>
    <httpPlatform processPath="c:\python36-32\python.exe"
                  arguments="c:\home\site\wwwroot\runserver.py --port %HTTP_PLATFORM_PORT%"
                  stdoutLogEnabled="true"
                  stdoutLogFile="c:\home\LogFiles\python.log"
                  startupTimeLimit="60"
                  processesPerApplication="16">
      <environmentVariables>
        <environmentVariable name="SERVER_PORT" value="%HTTP_PLATFORM_PORT%" />
      </environmentVariables>
    </httpPlatform>
  </system.webServer>
</configuration>
```

Zmienna środowiskowa `HTTP_PLATFORM_PORT` pokazana w tym miejscu zawiera port, na którym serwer lokalny powinien nasłuchiwał połączeń z localhost. W tym przykładzie pokazano również, jak utworzyć inną `SERVER_PORT`zmienną środowiskową, w razie potrzeby, w tym przypadku .

### <a name="configure-the-fastcgi-handler"></a>Konfigurowanie programu obsługi FastCGI

FastCGI to interfejs, który działa na poziomie żądania. Usługi IIS odbierają połączenia przychodzące i przekierują każde żądanie do aplikacji WSGI działającej w co najmniej jednym trwałym procesie języka Python.

Aby go użyć, najpierw zainstaluj i skonfiguruj pakiet wfastcgi zgodnie z [opisem](https://pypi.io/project/wfastcgi)na pypi.org/project/wfastcgi/ .

Następnie zmodyfikuj plik *web.config* aplikacji, aby uwzględnić pełne ścieżki do `PythonHandler` pliku *python.exe* i *wfastcgi.py* w kluczu. Poniższe kroki zakładają, że Python jest zainstalowany w *c:\python36-32* i że kod aplikacji jest w *c:\home\site\wwwroot;* odpowiednio dostosować do swoich ścieżek:

1. Zmodyfikuj `PythonHandler` wpis w *witrynie web.config,* tak aby ścieżka była zgodna z lokalizacją instalacji języka Python (szczegółowe informacje można znaleźć w [odwołaniu do konfiguracji usług IIS](https://www.iis.net/configreference) (iis.net).

    ```xml
    <system.webServer>
      <handlers>
        <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule"
            scriptProcessor="c:\python36-32\python.exe|c:\python36-32\wfastcgi.py"
            resourceType="Unspecified" requireAccess="Script"/>
      </handlers>
    </system.webServer>
    ```

1. W `<appSettings>` sekcji *web.config*dodaj klucze dla `WSGI_HANDLER`, `WSGI_LOG` (opcjonalnie) i: `PYTHONPATH`

    ```xml
    <appSettings>
      <add key="PYTHONPATH" value="c:\home\site\wwwroot"/>
      <!-- The handler here is specific to Bottle; see the next section. -->
      <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
      <add key="WSGI_LOG" value="c:\home\LogFiles\wfastcgi.log"/>
    </appSettings>
    ```

    Te `<appSettings>` wartości są dostępne dla aplikacji jako zmienne środowiskowe:

    - Wartość `PYTHONPATH` może być swobodnie przedłużony, ale musi zawierać katalog główny aplikacji.
    - `WSGI_HANDLER`musi wskazywać aplikację WSGI możnącą z aplikacji.
    - `WSGI_LOG`jest opcjonalne, ale zalecane do debugowania aplikacji.

1. Ustaw `WSGI_HANDLER` wpis w *web.config* odpowiednio dla struktury, której używasz:

    - **Butelka**: upewnij się, że masz `app.wsgi_app` nawiasy po jak pokazano poniżej. Jest to konieczne, ponieważ ten obiekt jest funkcją (patrz *app.py),* a nie zmienną:

        ```xml
        <!-- Bottle apps only -->
        <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
        ```

    - **Kolba**: Zmień `WSGI_HANDLER` wartość `<project_name>.app` `<project_name>` na miejsce odpowiadające nazwie projektu. Dokładny identyfikator można znaleźć, patrząc `from <project_name> import app` na instrukcję w *runserver.py*. Na przykład jeśli projekt nosi nazwę "FlaskAzurePublishExample", wpis będzie wyświetlany w następujący sposób:

        ```xml
        <!-- Flask apps only: change the project name to match your app -->
        <add key="WSGI_HANDLER" value="flask_iis_example.app"/>
        ```

    - **Django**: Dwie zmiany są potrzebne do *web.config* dla projektów Django. Najpierw zmień `WSGI_HANDLER` wartość `django.core.wsgi.get_wsgi_application()` na (obiekt znajduje się w *pliku wsgi.py):*

        ```xml
        <!-- Django apps only -->
        <add key="WSGI_HANDLER" value="django.core.wsgi.get_wsgi_application()"/>
        ```

        Po drugie, dodaj następujący wpis `WSGI_HANDLER`poniżej tego, który ma zastąpić `DjangoAzurePublishExample` nazwą projektu:

        ```xml
        <add key="DJANGO_SETTINGS_MODULE" value="django_iis_example.settings" />
        ```

1. **Tylko aplikacje Django**: W pliku *settings.py* projektu Django dodaj domenę adresu `ALLOWED_HOSTS` URL witryny lub adres IP, do jak pokazano poniżej, zastępując "1.2.3.4" adresem URL lub adresem IP, oczywiście:

    ```python
    # Change the URL or IP address to your specific site
    ALLOWED_HOSTS = ['1.2.3.4']
    ```

    Nie można dodać adresu URL do tablicy powoduje błąd **DisallowedHost at\</\>Invalid HTTP_HOST header: ' adres URL witryny '. Do ALLOWED_HOSTS może\<być\>konieczne dodanie adresu URL witryny.**

    Zauważ, że gdy tablica jest pusta, Django automatycznie zezwala na "localhost" i "127.0.0.1", ale dodanie produkcyjnego adresu URL usuwa te funkcje. Z tego powodu można zachować oddzielne kopie rozwoju i produkcji *settings.py*lub użyć zmiennych środowiskowych do kontrolowania wartości czasu wykonywania.

## <a name="deploy-to-iis-or-a-windows-vm"></a>Wdrażanie w usłudze IIS lub maszynie wirtualnej systemu Windows

Za pomocą właściwego pliku *web.config* w projekcie można publikować na komputerze z uruchomionymi usługami IIS za pomocą polecenia **Publikuj** w menu kontekstowym projektu w **Eksploratorze rozwiązań**i wybierając opcję, **Usługi IIS, FTP itp.** W takim przypadku visual studio po prostu kopiuje pliki projektu na serwerze; ponosisz odpowiedzialność za całą konfigurację po stronie serwera.

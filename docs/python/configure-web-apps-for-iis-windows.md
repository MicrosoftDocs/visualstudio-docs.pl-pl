---
title: Konfigurowanie aplikacji sieci web języka Python dla programu IIS
description: Jak skonfigurować aplikacje sieci web języka Python do uruchamiania z Internet Information Services z maszyną wirtualną Windows.
ms.date: 12/06/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: f0ea410a75d1fccf93adc18fc987626ccb026f34
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55029976"
---
# <a name="configure-python-web-apps-for-iis"></a>Konfigurowanie aplikacji sieci web języka Python dla programu IIS

Korzystając z usług Internet Information Services (IIS) jako serwera sieci web na komputerze Windows (w tym [maszyn wirtualnych Windows Azure](/azure/architecture/reference-architectures/n-tier/windows-vm), aplikacji w języku Python musi zawierać konkretne ustawienia w ich *web.config* pliki, który program IIS prawidłowo może przetworzyć kodu w języku Python. Sam komputer musi mieć zainstalowane wraz z wszelkich pakietów, których wymaga aplikacja sieci web języka Python.

> [!Note]
> Ten artykuł zawiera wcześniej wskazówki dotyczące konfigurowania środowiska Python w usłudze Azure App Service na Windows. Rozszerzenia języka Python i hostów Windows używane w tym scenariuszu zostały zaniechane i zastąpione w usłudze Azure App Service w systemie Linux. Aby uzyskać więcej informacji, zobacz [publikowania aplikacji w języku Python w usłudze Azure App Service (Linux)](publishing-python-web-applications-to-azure-from-visual-studio.md). Jednak poprzednim artykule, jest nadal dostępne w [zarządzania usługi App Service w Windows za pomocą rozszerzenia języka Python](managing-python-on-azure-app-service.md).

## <a name="install-python-on-windows"></a>Instalowanie języka Python w Windows

Aby uruchomić aplikację sieci web, najpierw zainstalować usługi wymaganą wersję języka Python bezpośrednio na maszynie hosta Windows zgodnie z opisem na [Python Zainstaluj interpretery](installing-python-interpreters.md).

Zapisz lokalizację `python.exe` interpreter do wykonania kolejnych kroków. Dla wygody można dodać tej lokalizacji do zmiennej środowiskowej PATH.

## <a name="install-packages"></a>Instalowanie pakietów

Korzystając z dedykowanego hosta, można użyć globalnego środowisko Python w celu uruchomienia aplikacji, a nie w środowisku wirtualnym. W związku z tym można zainstalować wszystkie wymagania dotyczące Twojej aplikacji w środowisku globalnym, uruchamiając `pip install -r requirements.txt` polecenie w wierszu polecenia.

## <a name="set-webconfig-to-point-to-the-python-interpreter"></a>Ustaw plik web.config, aby wskazać interpreter języka Python

Twoja aplikacja *web.config* pliku powoduje, że serwer sieci web usług IIS (7 +), systemem Windows o jak powinna obsługiwać żądania języka Python za pomocą interfejsu FastCGI lub HttpPlatform. Korzystając z programu Visual Studio 2017, musisz zmodyfikować *web.config* ręcznie. Zgodnie z opisem w dalszej części tego tematu, Visual Studio 2015 sprawia, że modyfikacje

### <a name="configure-the-httpplatform-handler"></a>Konfigurowanie obsługi HttpPlatform

Moduł HttpPlatform przekazuje połączenia z gniazdami bezpośrednio do autonomicznego proces języka Python. Przekazywanego ta umożliwia uruchamianie dowolnego serwera sieci web, ale wymaga skrypt uruchamiania, który uruchamia lokalny serwer internetowy. Określ skrypt w `<httpPlatform>` elementu *web.config*, gdzie `processPath` atrybutu punkty rozszerzenia witryny interpreter języka Python i `arguments` atrybut wskazuje się skrypt i argumenty chcesz udostępnić:

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

`HTTP_PLATFORM_PORT` Zmienna środowiskowa, pokazano poniżej zawiera port lokalny serwer powinien nasłuchiwać połączeń z hostem lokalnym. W tym przykładzie również pokazano, jak utworzyć inną zmienną środowiskową, jeśli to konieczne, w tym przypadku `SERVER_PORT`.

### <a name="configure-the-fastcgi-handler"></a>Konfigurowanie obsługi interfejsu FastCGI

FastCGI jest interfejsem, który działa na poziomie żądania. IIS odbiera połączenia przychodzące i przekazuje poszczególne żądania do aplikacji WSGI uruchomiony w jednej lub więcej trwały Python przetwarza.

Aby go użyć, zainstalować i skonfigurować pakiet wfastcgi zgodnie z opisem na [pypi.org/project/wfastcgi/](https://pypi.io/project/wfastcgi).

Następnie zmodyfikuj aplikacji *web.config* zawierać pełnej ścieżki do pliku *python.exe* i *procedurę wfastcgi.py* w `PythonHandler` klucza. W poniższych krokach przyjęto, że język Python jest instalowany w *c:\python36-32* i który znajduje się w kodzie aplikacji *c:\home\site\wwwroot*; odpowiednio dostosować Twoje ścieżki:

1. Modyfikowanie `PythonHandler` wpis *web.config* aby odpowiadały ścieżkę lokalizacji instalacji języka Python (zobacz [dokumentacja konfiguracji usług IIS](https://www.iis.net/configreference) (iis.net) dla szczegółowymi informacjami na temat).

    ```xml
    <system.webServer>
      <handlers>
        <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule"
            scriptProcessor="c:\python36-32\python.exe|c:\python36-32\wfastcgi.py"
            resourceType="Unspecified" requireAccess="Script"/>
      </handlers>
    </system.webServer>
    ```

1. W ramach `<appSettings>` części *web.config*, Dodaj klucze dla `WSGI_HANDLER`, `WSGI_LOG` (opcjonalnie) i `PYTHONPATH`:

    ```xml
    <appSettings>
      <add key="PYTHONPATH" value="c:\home\site\wwwroot"/>
      <!-- The handler here is specific to Bottle; see the next section. -->
      <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
      <add key="WSGI_LOG" value="c:\home\LogFiles\wfastcgi.log"/>
    </appSettings>
    ```

    Te `<appSettings>` wartości są dostępne dla aplikacji jako zmienne środowiskowe:

    - Wartość `PYTHONPATH` może być swobodnie przedłużony, ale mogą zawierać katalogu głównego aplikacji.
    - `WSGI_HANDLER` musi wskazywać aplikacją WSGI importowane z aplikacji.
    - `WSGI_LOG` jest opcjonalne, ale zalecane do debugowania aplikacji.

1. Ustaw `WSGI_HANDLER` wpisu w *web.config* odpowiednio dla struktury korzystasz:

    - **Bottle**: Upewnij się, że masz nawiasów po `app.wsgi_app` jak pokazano poniżej. Jest to konieczne, ponieważ ten obiekt jest funkcją (zobacz *app.py*) zamiast zmiennej:

        ```xml
        <!-- Bottle apps only -->
        <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
        ```

    - **Flask**: Zmiana `WSGI_HANDLER` wartość `<project_name>.app` gdzie `<project_name>` jest zgodna z nazwą projektu. Możesz znaleźć dokładny identyfikator, analizując `from <project_name> import app` instrukcji w *runserver.py*. Na przykład jeśli projekt ma nazwę "FlaskAzurePublishExample", wpis wyglądałby następująco:

        ```xml
        <!-- Flask apps only: change the project name to match your app -->
        <add key="WSGI_HANDLER" value="flask_iis_example.app"/>
        ```

    - **Django**: Dwie zmiany są potrzebne do *web.config* dla projektów Django. Najpierw należy zmienić `WSGI_HANDLER` wartość `django.core.wsgi.get_wsgi_application()` (obiekt jest w *wsgi.py* plików):

        ```xml
        <!-- Django apps only -->
        <add key="WSGI_HANDLER" value="django.core.wsgi.get_wsgi_application()"/>
        ```

        Po drugie, Dodaj następujący wpis poniżej dla `WSGI_HANDLER`, zastępując `DjangoAzurePublishExample` o nazwie projektu:

        ```xml
        <add key="DJANGO_SETTINGS_MODULE" value="django_iis_example.settings" />
        ```

1. **Tylko aplikacje Django**: W projekcie Django *settings.py* Dodaj lokacji adres URL domeny lub adres IP, który `ALLOWED_HOSTS` jak pokazano poniżej, zastępując "1.2.3.4" adres URL lub IP oczywiście:

    ```python
    # Change the URL or IP address to your specific site
    ALLOWED_HOSTS = ['1.2.3.4']
    ```

    Błąd podczas dodawania adresu URL do wyników tablicy w błędzie **DisallowedHost na / nieprawidłowy nagłówek HTTP_HOST: "\<adres URL witryny\>". Może być konieczne dodanie "\<adres URL witryny\>" do ALLOWED_HOSTS.**

    Należy pamiętać, że gdy tablica jest pusta, Django, automatycznie umożliwia nazwy "Host_lokalny" i "127.0.0.1", ale dodanie adresu URL produkcji powoduje usunięcie tych możliwości. Aby z tego powodu należy zachować oddzielne deweloperskich i produkcyjnych kopii *settings.py*, lub użyj zmiennych środowiskowych, aby kontrolować wartości w czasie wykonywania.

## <a name="deploy-to-iis-or-a-windows-vm"></a>Wdrażanie usług IIS lub Windows maszyny Wirtualnej

Z prawidłowymi *web.config* pliku w projekcie, możesz opublikować komputer z programem IIS za pomocą **Publikuj** polecenia menu kontekstowego projektu w **Eksploratora rozwiązań**i wybierając opcję **usług IIS, FTP, itp.**. W takich przypadkach program Visual Studio po prostu kopiuje pliki projektu na serwerze; Jesteś odpowiedzialny za całą konfigurację po stronie serwera.

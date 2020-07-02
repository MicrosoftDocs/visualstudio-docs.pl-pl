---
title: Konfigurowanie aplikacji sieci Web w języku Python dla usług IIS
description: Jak skonfigurować aplikacje sieci Web w języku Python do uruchamiania z Internet Information Services z maszyny wirtualnej z systemem Windows.
ms.date: 12/06/2018
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: 3c756f3d9a89294ecce054650037be3f7b26c291
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85540936"
---
# <a name="configure-python-web-apps-for-iis"></a>Konfigurowanie aplikacji sieci Web w języku Python dla usług IIS

W przypadku korzystania z Internet Information Services (IIS) jako serwera sieci Web na komputerze z systemem Windows (w tym [maszyn wirtualnych z systemem Windows na platformie Azure](/azure/architecture/reference-architectures/n-tier/windows-vm), aplikacje języka Python muszą zawierać określone ustawienia w plikach *web.config* , dzięki czemu usługi IIS mogą poprawnie przetwarzać kod języka Python. Na komputerze musi być również zainstalowany język Python oraz wszystkie pakiety wymagane przez aplikację sieci Web.

> [!Note]
> Ten artykuł zawiera wcześniej wskazówki dotyczące konfigurowania języka Python na Azure App Service w systemie Windows. Rozszerzenia Python i hosty systemu Windows używane w tym scenariuszu zostały zaniechane na rzecz Azure App Service w systemie Linux. Aby uzyskać więcej informacji, zobacz [publikowanie aplikacji w języku Python do Azure App Service (Linux)](publishing-python-web-applications-to-azure-from-visual-studio.md). Poprzedni artykuł jest jednak nadal dostępny na [zarządzaniu App Service w systemie Windows przy użyciu rozszerzeń języka Python](managing-python-on-azure-app-service.md).

## <a name="install-python-on-windows"></a>Instalowanie języka Python w systemie Windows

Aby uruchomić aplikację sieci Web, najpierw zainstaluj wymaganą wersję środowiska Python bezpośrednio na komputerze hosta z systemem Windows, zgodnie z opisem w artykule [Instalowanie interpreterów języka Python](installing-python-interpreters.md).

Zapisz lokalizację `python.exe` interpretera na potrzeby kolejnych kroków. Dla wygody możesz dodać tę lokalizację do zmiennej środowiskowej PATH.

## <a name="install-packages"></a>Zainstaluj pakiety

Korzystając z dedykowanego hosta, można użyć globalnego środowiska języka Python do uruchamiania aplikacji zamiast środowiska wirtualnego. W związku z tym można zainstalować wszystkie wymagania aplikacji w środowisku globalnym po prostu, uruchamiając `pip install -r requirements.txt` polecenie w wierszu polecenia.

## <a name="set-webconfig-to-point-to-the-python-interpreter"></a>Ustaw web.config tak, aby wskazywał interpreter języka Python

Plik *web.config* aplikacji instruuje serwer sieci Web usług IIS (7 +) uruchomiony w systemie Windows o tym, jak powinien obsługiwać żądania w języku Python za pomocą HttpPlatform (zalecane) lub FastCGI. W programie Visual Studio w wersji 2015 i starszych wprowadzono te modyfikacje automatycznie. W przypadku korzystania z programu Visual Studio 2017 i nowszych należy zmodyfikować *web.config* ręcznie.

### <a name="configure-the-httpplatform-handler"></a>Konfigurowanie procedury obsługi HttpPlatform

Moduł HttpPlatform przekazuje połączenia gniazda bezpośrednio do samodzielnego procesu języka Python. To przekazanie umożliwia uruchomienie dowolnego serwera sieci Web, ale wymaga skryptu uruchamiania, który uruchamia lokalny serwer sieci Web. Należy określić skrypt w `<httpPlatform>` elemencie *web.config*, gdzie `processPath` atrybut wskazuje interpreter języka Python rozszerzenia witryny, a `arguments` atrybut wskazuje na skrypt i wszystkie argumenty, które mają być podane:

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

`HTTP_PLATFORM_PORT`Pokazana tutaj zmienna środowiskowa zawiera port, na którym serwer lokalny powinien nasłuchiwać połączeń z hosta lokalnego. Ten przykład pokazuje również, jak utworzyć inną zmienną środowiskową, w razie potrzeby, w tym przypadku `SERVER_PORT` .

### <a name="configure-the-fastcgi-handler"></a>Konfigurowanie procedury obsługi FastCGI

FastCGI jest interfejsem, który działa na poziomie żądania. Program IIS odbiera połączenia przychodzące i przekazuje każde żądanie do aplikacji WSGI działającej w co najmniej jednym trwałym procesie języka Python.

Aby go użyć, najpierw zainstaluj i skonfiguruj pakiet wfastcgi zgodnie z opisem w [PyPi.org/Project/wfastcgi/](https://pypi.io/project/wfastcgi).

Następnie zmodyfikuj plik *web.config* aplikacji, aby uwzględnić pełne ścieżki do *python.exe* i *wfastcgi.py* w `PythonHandler` kluczu. W poniższych krokach przyjęto założenie, że Python jest zainstalowany w *c:\python36-32* i że kod aplikacji znajduje się w *c:\home\site\wwwroot*; odpowiednio Dopasuj ścieżki:

1. Zmodyfikuj `PythonHandler` wpis w *web.config* tak, aby ścieżka była zgodna z lokalizacją instalacji języka Python (zobacz [Dokumentacja konfiguracji programu IIS](https://www.iis.net/configreference) (IIS.NET), aby uzyskać dokładne informacje).

    ```xml
    <system.webServer>
      <handlers>
        <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule"
            scriptProcessor="c:\python36-32\python.exe|c:\python36-32\wfastcgi.py"
            resourceType="Unspecified" requireAccess="Script"/>
      </handlers>
    </system.webServer>
    ```

1. W `<appSettings>` sekcji *web.config*Dodaj klucze dla `WSGI_HANDLER` `WSGI_LOG` (opcjonalnie) i `PYTHONPATH` :

    ```xml
    <appSettings>
      <add key="PYTHONPATH" value="c:\home\site\wwwroot"/>
      <!-- The handler here is specific to Bottle; see the next section. -->
      <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
      <add key="WSGI_LOG" value="c:\home\LogFiles\wfastcgi.log"/>
    </appSettings>
    ```

    Te `<appSettings>` wartości są dostępne dla aplikacji jako zmienne środowiskowe:

    - Wartość dla `PYTHONPATH` może być swobodnie rozszerzona, ale musi zawierać katalog główny aplikacji.
    - `WSGI_HANDLER`musi wskazywać aplikację WSGI, która nie jest przenośna z poziomu aplikacji.
    - `WSGI_LOG`jest opcjonalne, ale zalecane do debugowania aplikacji.

1. Ustaw `WSGI_HANDLER` wpis w *web.config* stosownie do używanej platformy:

    - **Butelka**: Upewnij się, że masz nawiasy, `app.wsgi_app` jak pokazano poniżej. Jest to konieczne, ponieważ ten obiekt jest funkcją (zobacz *App.py*), a nie zmienną:

        ```xml
        <!-- Bottle apps only -->
        <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
        ```

    - **Kolba**: Zmień `WSGI_HANDLER` wartość na `<project_name>.app` gdzie `<project_name>` pasuje do nazwy projektu. Dokładny identyfikator można znaleźć, przeglądając `from <project_name> import app` instrukcje w *runserver.py*. Na przykład jeśli projekt ma nazwę "FlaskAzurePublishExample", wpis będzie wyglądać następująco:

        ```xml
        <!-- Flask apps only: change the project name to match your app -->
        <add key="WSGI_HANDLER" value="flask_iis_example.app"/>
        ```

    - **Django**: dwa zmiany są konieczne do *web.config* dla projektów Django. Najpierw Zmień `WSGI_HANDLER` wartość na `django.core.wsgi.get_wsgi_application()` (obiekt znajduje się w pliku *WSGI.py* ):

        ```xml
        <!-- Django apps only -->
        <add key="WSGI_HANDLER" value="django.core.wsgi.get_wsgi_application()"/>
        ```

        Następnie Dodaj następujący wpis poniżej tego elementu `WSGI_HANDLER` , zastępując go `DjangoAzurePublishExample` nazwą projektu:

        ```xml
        <add key="DJANGO_SETTINGS_MODULE" value="django_iis_example.settings" />
        ```

1. **Tylko aplikacje Django**: w pliku *Settings.py* projektu Django należy dodać domenę lub adres IP witryny sieci Web, `ALLOWED_HOSTS` tak jak pokazano poniżej, zastępując element "1.2.3.4" adresem URL lub adresem IP, oczywiście:

    ```python
    # Change the URL or IP address to your specific site
    ALLOWED_HOSTS = ['1.2.3.4']
    ```

    Nie można dodać adresu URL do tablicy wyniki w DisallowedHost błędu w **nagłówku/Nieprawidłowym HTTP_HOST: " \<site URL\> ". Może być konieczne dodanie " \<site URL\> " do ALLOWED_HOSTS.**

    Należy pamiętać, że gdy tablica jest pusta, Django automatycznie zezwala na "localhost" i "127.0.0.1", ale dodanie produkcyjnego adresu URL spowoduje usunięcie tych funkcji. Z tego powodu warto zachować osobne kopie i produkcję *Settings.py*lub użyć zmiennych środowiskowych w celu kontrolowania wartości czasu wykonywania.

## <a name="deploy-to-iis-or-a-windows-vm"></a>Wdrażanie w usługach IIS lub maszynie wirtualnej z systemem Windows

Używając poprawnego pliku *web.config* w projekcie, można publikować na komputerze z URUCHOMIONYMI usługami IIS za pomocą polecenia **Publikuj** w menu kontekstowym projektu w **Eksplorator rozwiązań**i wybierając opcję, **IIS, FTP itp.** W takim przypadku Visual Studio po prostu kopiuje pliki projektu na serwer; Użytkownik jest odpowiedzialny za całą konfigurację po stronie serwera.

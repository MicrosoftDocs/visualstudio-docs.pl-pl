---
title: Konfigurowanie języka Python w usłudze Azure App Service (Windows)
description: Jak zainstalować interpreter języka Python i biblioteki w usłudze Azure App Service i konfigurowanie aplikacji sieci web, aby poprawnie odwoływać się do tego interpretera.
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
ms.openlocfilehash: 7ffe0de939eba8af38c132fc3de5c96a9499e3f0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62535992"
---
# <a name="how-to-set-up-a-python-environment-on-azure-app-service-windows"></a>Jak skonfigurować środowisko języka Python w usłudze Azure App Service (Windows)

> [!Important]
> Firma Microsoft przeceniła rozszerzenia języka Python dla usługi App Service w systemie Windows, zgodnie z opisem w tym artykule na rzecz bezpośredniego wdrożenia usługi App Service w [systemie Linux.](publishing-python-web-applications-to-azure-from-visual-studio.md)

[Usługa Azure App Service](https://azure.microsoft.com/services/app-service/) to oferta platformy jako usługi dla aplikacji sieci web, niezależnie od tego, czy są to witryny dostępne za pośrednictwem przeglądarki, interfejsy API REST używane przez własnych klientów, czy przetwarzanie wyzwalane zdarzeniami. Usługa app service w pełni obsługuje za pomocą języka Python do implementowania aplikacji.

Konfigurowalna obsługa języka Python dla usługi Azure App Service jest dostępna jako zestaw *rozszerzeń lokacji* usługi App Service, z których każda zawiera określoną wersję środowiska wykonawczego języka Python. Następnie można zainstalować wszystkie żądane pakiety bezpośrednio w tym środowisku, zgodnie z opisem w tym artykule. Dostosowując środowisko w samej usłudze app service, nie trzeba obsługiwać pakietów w projektach aplikacji sieci web ani przekazywać ich za pomocą kodu aplikacji.

> [!Tip]
> Chociaż usługa App Service domyślnie ma Python 2.7 i Python 3.4 zainstalowany w folderach głównych na serwerze, nie można dostosować lub zainstalować pakiety w tych środowiskach, ani nie należy polegać na ich obecności. Zamiast tego należy polegać na rozszerzenie witryny, które można kontrolować, zgodnie z opisem w tym artykule.

## <a name="choose-a-python-version-through-the-azure-portal"></a>Wybieranie wersji języka Python za pośrednictwem witryny Azure portal

1. Utwórz usługę app dla aplikacji sieci web w witrynie Azure portal.
1. Na stronie Usługi aplikacji przewiń do sekcji **Narzędzia programistyczne,** wybierz pozycję **Rozszerzenia**, a następnie wybierz pozycję **+ Dodaj**.
1. Przewiń w dół na liście do rozszerzenia zawierającego żądaną wersję języka Python:

    ![Portal Azure z rozszerzeniami języka Python](media/python-on-azure-extensions.png)

    > [!Tip]
    > Jeśli potrzebujesz starszej wersji języka Python i nie widzisz jej na liście w rozszerzeniach lokacji, nadal możesz zainstalować ją za pośrednictwem usługi Azure Resource Manager, zgodnie z opisem w następnej sekcji.

1. Wybierz rozszerzenie, zaakceptuj warunki prawne, a następnie wybierz **przycisk OK**.
1. Powiadomienie pojawi się w portalu po zakończeniu instalacji.

## <a name="choose-a-python-version-through-the-azure-resource-manager"></a>Wybieranie wersji języka Python za pośrednictwem usługi Azure Resource Manager

Jeśli wdrażasz usługę app service z szablonem usługi Azure Resource Manager, dodaj rozszerzenie lokacji jako zasób. W szczególności rozszerzenie jest wyświetlane jako zagnieżdżony `resources` zasób (obiekt pod) `resources`o typie `siteextensions` i nazwie z [siteextensions.net](https://www.siteextensions.net/packages?q=Tags%3A%22python%22).

Na przykład po dodaniu `python361x64` odwołania do (Python 3.6.1 x64), szablon może wyglądać następująco (niektóre właściwości pominięte):

```json
"resources": [
  {
    "apiVersion": "2015-08-01",
    "name": "[parameters('siteName')]",
    "type": "Microsoft.Web/sites",

    // ...

    "resources": [
      {
        "apiVersion": "2015-08-01",
        "name": "python361x64",
        "type": "siteextensions",
        "properties": { },
        "dependsOn": [
          "[resourceId('Microsoft.Web/sites', parameters('siteName'))]"
        ]
      },
      // ...
    ]
  }
```

## <a name="set-webconfig-to-point-to-the-python-interpreter"></a>Ustawianie pliku web.config w celu wskazanie interpretera języka Python

Po zainstalowaniu rozszerzenia lokacji (za pośrednictwem portalu lub szablonu usługi Azure Resource Manager) następnie należy skierować plik *web.config* aplikacji do interpretera języka Python. Plik *web.config* instruuje serwer sieci Web usług IIS (7+) uruchomiony w usłudze App Service o tym, jak powinien obsługiwać żądania języka Python za pośrednictwem protokołu HttpPlatform (zalecane) lub FastCGI.

Rozpocznij od znalezienia pełnej ścieżki do *python.exe rozszerzenia witryny,* a następnie utwórz i zmodyfikuj odpowiedni plik *web.config.*

### <a name="find-the-path-to-pythonexe"></a>Znajdź ścieżkę do pliku python.exe

Rozszerzenie witryny Języka Python jest zainstalowane na serwerze w obszarze *d:\home* w folderze odpowiednim dla wersji i architektury języka Python (z wyjątkiem kilku starszych wersji). Na przykład Python 3.6.1 x64 jest zainstalowany w *d:\home\python361x64*. Pełna ścieżka do interpretera języka Python to *d:\home\python361x64\python.exe*.

Aby wyświetlić określoną ścieżkę w usłudze app service, wybierz **rozszerzenia** na stronie Usługi aplikacji, a następnie wybierz rozszerzenie na liście.

![Lista rozszerzeń w usłudze Azure App Service](media/python-on-azure-extension-list.png)

Ta akcja powoduje otwarcie strony opisu rozszerzenia zawierającej ścieżkę:

![Szczegółowe informacje o rozszerzeniu usługi Azure App Service](media/python-on-azure-extension-detail.png)

Jeśli masz problemy z wyświetlaniem ścieżki rozszerzenia, możesz ją znaleźć ręcznie za pomocą konsoli:

1. Na stronie Usługi aplikacji wybierz**konsolę**narzędzi **programistycznych** > .
1. Wprowadź polecenie `ls ../home` `dir ..\home` lub zobacz foldery rozszerzeń najwyższego poziomu, takie jak *Python361x64*.
1. Wprowadź polecenie, `ls ../home/python361x64` `dir ..\home\python361x64` takie jak lub sprawdź, czy zawiera *ono plik python.exe* i inne pliki interpretera.

### <a name="configure-the-httpplatform-handler"></a>Konfigurowanie programu obsługi httpplatform

Moduł HttpPlatform przekazuje połączenia gniazda bezpośrednio do samodzielnego procesu Pythona. Ten przekaz umożliwia uruchomienie dowolnego serwera sieci web, ale wymaga skryptu startowego, który uruchamia lokalny serwer sieci Web. Skrypt można określić `<httpPlatform>` w elemencie *web.config*, gdzie `processPath` atrybut wskazuje na `arguments` interpreter Języka Python rozszerzenia witryny, a atrybut wskazuje skrypt i wszelkie argumenty, które chcesz podać:

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.webServer>
    <handlers>
      <add name="PythonHandler" path="*" verb="*" modules="httpPlatformHandler" resourceType="Unspecified"/>
    </handlers>
    <httpPlatform processPath="D:\home\Python361x64\python.exe"
                  arguments="D:\home\site\wwwroot\runserver.py --port %HTTP_PLATFORM_PORT%"
                  stdoutLogEnabled="true"
                  stdoutLogFile="D:\home\LogFiles\python.log"
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

FastCGI to interfejs, który działa na poziomie żądania. Usługi IIS odbierają połączenia przychodzące i przekierują każde żądanie do aplikacji WSGI działającej w co najmniej jednym trwałym procesie języka Python. [Pakiet wfastcgi](https://pypi.io/project/wfastcgi) jest wstępnie zainstalowany i skonfigurowany z każdym rozszerzeniem witryny Pythona, dzięki czemu można go łatwo włączyć, dołączając kod w *web.config,* jak pokazano poniżej dla aplikacji internetowej opartej na platformie Bottle. Należy zauważyć, że pełne ścieżki do *python.exe* i `PythonHandler` *wfastcgi.py* są umieszczane w kluczu:

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <appSettings>
    <add key="PYTHONPATH" value="D:\home\site\wwwroot"/>
    <!-- The handler here is specific to Bottle; other frameworks vary. -->
    <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
    <add key="WSGI_LOG" value="D:\home\LogFiles\wfastcgi.log"/>
  </appSettings>
  <system.webServer>
    <handlers>
      <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule"
           scriptProcessor="D:\home\Python361x64\python.exe|D:\home\Python361x64\wfastcgi.py"
           resourceType="Unspecified" requireAccess="Script"/>
    </handlers>
  </system.webServer>
</configuration>
```

Zdefiniowane `<appSettings>` w tym miejscu są dostępne dla aplikacji jako zmienne środowiskowe:

- Wartość `PYTHONPATH` może być swobodnie przedłużony, ale musi zawierać katalog główny aplikacji.
- `WSGI_HANDLER`musi wskazywać aplikację WSGI możnącą z aplikacji.
- `WSGI_LOG`jest opcjonalne, ale zalecane do debugowania aplikacji.

Zobacz Publikowanie na [platformie Azure, aby](publishing-python-web-applications-to-azure-from-visual-studio.md) uzyskać dodatkowe informacje na temat zawartości *web.config* dla aplikacji sieci Web Bottle, Flask i Django.

## <a name="install-packages"></a>Instalowanie pakietów

Interpreter języka Python zainstalowany za pośrednictwem rozszerzenia lokacji jest tylko jeden kawałek środowiska Pythona. Prawdopodobnie trzeba zainstalować różne pakiety w tym środowisku, jak również.

Aby zainstalować pakiety bezpośrednio w środowisku serwera, należy użyć jednej z następujących metod:

| Metody | Sposób użycia |
| --- | --- |
| [Konsola Kudu usługi Azure App Service](#azure-app-service-kudu-console) | Instaluje pakiety interaktywnie. Pakiety muszą być czystym Pythonem lub muszą publikować koła. |
| [Kudu REST API](#kudu-rest-api) | Może służyć do automatyzacji instalacji pakietu.  Pakiety muszą być czystym Pythonem lub muszą publikować koła. |
| Pakiet z aplikacją | Zainstaluj pakiety bezpośrednio w projekcie, a następnie wdrożyć je w usłudze App Service tak, jakby były częścią aplikacji. W zależności od liczby posiadanych zależności i częstotliwości ich aktualizowania ta metoda może być najprostszym sposobem uzyskania działającego wdrożenia. Należy pamiętać, że biblioteki muszą być zgodne z wersją języka Python na serwerze, w przeciwnym razie zobaczysz niejasne błędy po wdrożeniu. Mimo to, ponieważ wersje języka Python w rozszerzeniach witryny usługi App Service są dokładnie takie same, jak te wersje wydane na python.org, można łatwo uzyskać zgodną wersję dla rozwoju lokalnego. |
| Środowiska wirtualne | Bez pomocy technicznej. Zamiast tego należy użyć tworzenia `PYTHONPATH` pakietów i ustawić zmienną środowiskową, aby wskazywała lokalizację pakietów. |

### <a name="azure-app-service-kudu-console"></a>Konsola Kudu usługi Azure App Service

Konsola [Kudu](https://github.com/projectkudu/kudu/wiki/Kudu-console) zapewnia bezpośredni, podwyższony poziom dostępu do wiersza polecenia do serwera usługi App Service i jego systemu plików. Jest to zarówno cenne narzędzie debugowania i umożliwia operacje interfejsu wiersza polecenia, takie jak instalowanie pakietów.

1. Otwórz kudu ze strony usługi App Service w witrynie Azure portal, wybierając pozycję **Narzędzia** > **programistyczne Zaawansowane narzędzia,** a następnie wybierając pozycję **Go**. Ta akcja przechodzi do adresu URL, który jest taki sam `.scm` jak podstawowy adres URL usługi App Service, z wyjątkiem wstawiony. Na przykład, jeśli twój `https://vspython-test.azurewebsites.net/` podstawowy adres URL `https://vspython-test.scm.azurewebsites.net/` jest wtedy Kudu jest włączony (co można zakładkę):

    ![Konsola Kudu dla usługi Azure App Service](media/python-on-azure-console01.png)

1. Wybierz **polecenie Dyług konsoli** > **CMD,** aby otworzyć konsolę, w której możesz przejść do instalacji języka Python i zobaczyć, jakie biblioteki już tam są.

1. Aby zainstalować pojedynczy pakiet:

    a. Przejdź do folderu instalacji języka Python, w którym chcesz zainstalować pakiet, na przykład *d:\home\python361x64*.

    b. Służy `python.exe -m pip install <package_name>` do instalowania pakietu.

    ![Przykład instalowania butelki za pośrednictwem konsoli Kudu dla usługi Azure App Service](media/python-on-azure-console02.png)

1. Jeśli wdrożono już na serwerze *plik requirements.txt* dla aplikacji, zainstaluj wszystkie te wymagania w następujący sposób:

    a. Przejdź do folderu instalacji języka Python, w którym chcesz zainstalować pakiet, na przykład *d:\home\python361x64*.

    b. Uruchom polecenie `python.exe -m pip install --upgrade -r d:\home\site\wwwroot\requirements.txt`.

    Używanie *pliku requirements.txt* jest zalecane, ponieważ łatwo jest odtworzyć dokładny zestaw pakietów zarówno lokalnie, jak i na serwerze. Pamiętaj tylko, aby odwiedzić konsolę po wdrożeniu jakichkolwiek zmian *w pliku requirements.txt* i ponownie uruchomić polecenie.

> [!Note]
> Nie ma kompilatora C w usłudze App Service, więc należy zainstalować koło dla wszystkich pakietów z natywnymi modułami rozszerzenia. Wiele popularnych pakietów zapewnia własne koła. W przypadku pakietów, `pip wheel <package_name>` które tego nie robią, użyj na lokalnym komputerze deweloperskim, a następnie prześlij koło do witryny. Na przykład zobacz [Zarządzanie wymaganymi pakietami z plikem requirements.txt](managing-required-packages-with-requirements-txt.md).

### <a name="kudu-rest-api"></a>Kudu REST API

Zamiast używać konsoli Kudu za pośrednictwem witryny Azure Portal, można uruchamiać polecenia zdalnie za `https://yoursite.scm.azurewebsites.net/api/command`pośrednictwem interfejsu API Kudu REST, publikując polecenie w pliku . Na przykład, aby `bottle` zainstalować pakiet, należy `/api/command`zaksięgować następujące JSON na:

```json
{
    "command": 'python.exe -m pip install bottle',
    "dir": '\home\python361x64'
}
```

Aby uzyskać informacje o poleceniach i uwierzytelnianiu, zobacz [dokumentację Kudu](https://github.com/projectkudu/kudu/wiki/REST-API).

Poświadczenia można również zobaczyć `az webapp deployment list-publishing-profiles` za pomocą polecenia za pośrednictwem interfejsu wiersza polecenia platformy Azure (zobacz [wdrożenie az webapp](/cli/azure/webapp/deployment?view=azure-cli-latest#az-webapp-deployment-list-publishing-profiles)). Biblioteka pomocnicza do publikowania poleceń Kudu jest dostępna na [GitHub](https://github.com/lmazuel/azure-webapp-publish/blob/master/azure_webapp_publish/kudu.py#L42).

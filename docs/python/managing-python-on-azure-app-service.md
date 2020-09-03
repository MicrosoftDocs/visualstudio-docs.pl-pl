---
title: Konfigurowanie języka Python w Azure App Service (system Windows)
description: Jak zainstalować interpreter języka Python i biblioteki na Azure App Service i skonfigurować aplikacje sieci Web do prawidłowego odwoływania się do tego interpretera.
ms.date: 01/07/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: 34fd56b37113467b7cbb2dfb8ac6fdba01b79cc6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543757"
---
# <a name="how-to-set-up-a-python-environment-on-azure-app-service-windows"></a>Jak skonfigurować środowisko Python w Azure App Service (system Windows)

> [!Important]
> Firma Microsoft zakończyła działania rozszerzeń języka Python dla App Service w systemie Windows zgodnie z opisem w tym artykule na rzecz bezpośredniego wdrożenia [App Service w systemie Linux](publishing-python-web-applications-to-azure-from-visual-studio.md).

[Azure App Service](https://azure.microsoft.com/services/app-service/) to oferta typu "platforma jako usługa" dla aplikacji sieci Web, niezależnie od tego, czy są one dostępne za pomocą przeglądarki, interfejsów API REST używanych przez własnych klientów lub przetwarzanych zdarzeń. App Service w pełni obsługuje używanie języka Python do implementowania aplikacji.

Dostosowywalna obsługa języka Python dla Azure App Service jest dostępna jako zestaw App Service *rozszerzenia witryny* , które zawierają określoną wersję środowiska uruchomieniowego języka Python. Następnie można zainstalować wszystkie wymagane pakiety bezpośrednio w tym środowisku, zgodnie z opisem w tym artykule. Dostosowując środowisko w App Service samym, nie musisz obsługiwać pakietów w projektach aplikacji sieci Web ani ładować ich z kodem aplikacji.

> [!Tip]
> Mimo że App Service domyślnie ma zainstalowany język Python 2,7 i Python 3,4 w folderach głównych na serwerze, nie można dostosowywać ani instalować pakietów w tych środowiskach ani nie należy zależeć od ich obecności. Zamiast tego należy polegać na rozszerzeniu witryny, które można kontrolować, zgodnie z opisem w tym artykule.

## <a name="choose-a-python-version-through-the-azure-portal"></a>Wybierz wersję języka Python za pomocą Azure Portal

1. Utwórz App Service aplikacji sieci Web na Azure Portal.
1. Na stronie App Service przewiń do sekcji **Narzędzia programistyczne** , wybierz pozycję **rozszerzenia**, a następnie wybierz pozycję **+ Dodaj**.
1. Przewiń w dół listę do rozszerzenia, które zawiera wersję języka Python:

    ![Azure Portal pokazywania rozszerzeń języka Python](media/python-on-azure-extensions.png)

    > [!Tip]
    > Jeśli potrzebujesz starszej wersji środowiska Python i nie widzisz jej w rozszerzeniach lokacji, możesz zainstalować ją za pomocą Azure Resource Manager zgodnie z opisem w następnej sekcji.

1. Wybierz rozszerzenie, zaakceptuj postanowienia prawne, a następnie wybierz **przycisk OK**.
1. Po zakończeniu instalacji zostanie wyświetlone powiadomienie w portalu.

## <a name="choose-a-python-version-through-the-azure-resource-manager"></a>Wybierz wersję języka Python za pomocą Azure Resource Manager

W przypadku wdrażania App Service z szablonem Azure Resource Manager Dodaj rozszerzenie lokacji jako zasób. W odniesieniu do rozszerzenia pojawia się jako zasób zagnieżdżony ( `resources` obiekt w obszarze `resources` ) z typem `siteextensions` i nazwą z [siteextensions.NET](https://www.siteextensions.net/packages?q=Tags%3A%22python%22).

Na przykład po dodaniu odwołania do `python361x64` (Python 3.6.1 x64) szablon może wyglądać następująco (niektóre właściwości zostały pominięte):

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

## <a name="set-webconfig-to-point-to-the-python-interpreter"></a>Ustaw web.config tak, aby wskazywał interpreter języka Python

Po zainstalowaniu rozszerzenia witryny (za pomocą portalu lub szablonu Azure Resource Manager), należy wskazać plik *web.config* aplikacji do interpretera języka Python. Plik *web.config* instruuje serwer sieci Web usług IIS (7 +) uruchomiony na App Service o sposobie obsługi żądań w języku Python za pomocą HttpPlatform (zalecane) lub FastCGI.

Zacznij od znalezienia pełnej ścieżki do *python.exe*rozszerzenia witryny, a następnie utwórz i zmodyfikuj odpowiedni plik *web.config* .

### <a name="find-the-path-to-pythonexe"></a>Znajdź ścieżkę do python.exe

Rozszerzenie witryny języka Python jest zainstalowane na serwerze w obszarze *d:\home* w folderze odpowiednim dla wersji i architektury języka Python (z wyjątkiem kilku starszych wersji). Na przykład środowisko Python 3.6.1 x64 jest zainstalowane w *d:\home\python361x64*. Pełna ścieżka do interpretera języka Python jest następnie *d:\home\python361x64\python.exe*.

Aby wyświetlić określoną ścieżkę do App Service, wybierz pozycję **rozszerzenia** na stronie App Service, a następnie wybierz rozszerzenie na liście.

![Lista rozszerzeń na Azure App Service](media/python-on-azure-extension-list.png)

Ta akcja powoduje otwarcie strony opisu rozszerzenia zawierającej ścieżkę:

![Szczegóły rozszerzenia na Azure App Service](media/python-on-azure-extension-detail.png)

Jeśli masz problemy z wyświetlaniem ścieżki do rozszerzenia, możesz je znaleźć ręcznie przy użyciu konsoli programu:

1. Na stronie App Service Wybierz konsolę **Narzędzia deweloperskie**  >  **Console**.
1. Wprowadź polecenie `ls ../home` lub `dir ..\home` , aby wyświetlić foldery rozszerzeń najwyższego poziomu, takie jak *Python361x64*.
1. Wprowadź polecenie jak `ls ../home/python361x64` lub `dir ..\home\python361x64` , aby sprawdzić, czy zawiera *python.exe* i innych plików interpretera.

### <a name="configure-the-httpplatform-handler"></a>Konfigurowanie procedury obsługi HttpPlatform

Moduł HttpPlatform przekazuje połączenia gniazda bezpośrednio do samodzielnego procesu języka Python. To przekazanie umożliwia uruchomienie dowolnego serwera sieci Web, ale wymaga skryptu uruchamiania, który uruchamia lokalny serwer sieci Web. Należy określić skrypt w `<httpPlatform>` elemencie *web.config*, gdzie `processPath` atrybut wskazuje interpreter języka Python rozszerzenia witryny, a `arguments` atrybut wskazuje na skrypt i wszystkie argumenty, które mają być podane:

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

`HTTP_PLATFORM_PORT`Pokazana tutaj zmienna środowiskowa zawiera port, na którym serwer lokalny powinien nasłuchiwać połączeń z hosta lokalnego. Ten przykład pokazuje również, jak utworzyć inną zmienną środowiskową, w razie potrzeby, w tym przypadku `SERVER_PORT` .

### <a name="configure-the-fastcgi-handler"></a>Konfigurowanie procedury obsługi FastCGI

FastCGI jest interfejsem, który działa na poziomie żądania. Program IIS odbiera połączenia przychodzące i przekazuje każde żądanie do aplikacji WSGI działającej w co najmniej jednym trwałym procesie języka Python. [Pakiet wfastcgi](https://pypi.io/project/wfastcgi) jest wstępnie zainstalowany i skonfigurowany przy użyciu każdego rozszerzenia witryny języka Python, dzięki czemu można łatwo włączyć go, dołączając kod w *web.config* jak pokazano poniżej w przypadku aplikacji sieci Web opartej na strukturze butelek. Należy zauważyć, że pełne ścieżki do *python.exe* i *wfastcgi.py* są umieszczane w `PythonHandler` kluczu:

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

`<appSettings>`Zdefiniowane w tym miejscu są dostępne dla aplikacji jako zmienne środowiskowe:

- Wartość dla `PYTHONPATH` może być swobodnie rozszerzona, ale musi zawierać katalog główny aplikacji.
- `WSGI_HANDLER` musi wskazywać aplikację WSGI, która nie jest przenośna z poziomu aplikacji.
- `WSGI_LOG` jest opcjonalne, ale zalecane do debugowania aplikacji.

Zobacz [Publikowanie na platformie Azure,](publishing-python-web-applications-to-azure-from-visual-studio.md) Aby uzyskać dodatkowe informacje na temat *web.config* zawartości dla aplikacji sieci Web w butelkach, kolbach i Django.

## <a name="install-packages"></a>Zainstaluj pakiety

Interpreter języka Python instalowany za pomocą rozszerzenia witryny jest tylko jednym elementem środowiska Python. Może być również konieczne zainstalowanie różnych pakietów w tym środowisku.

Aby zainstalować pakiety bezpośrednio w środowisku serwera, należy użyć jednej z następujących metod:

| Metody | Użycie |
| --- | --- |
| [Azure App Service konsoli kudu](#azure-app-service-kudu-console) | Instaluje pakiety interaktywnie. Pakiety muszą być czyste w języku Python lub muszą publikować koła. |
| [Interfejs API REST usługi kudu](#kudu-rest-api) | Może służyć do automatyzowania instalacji pakietu.  Pakiety muszą być czyste w języku Python lub muszą publikować koła. |
| Pakiet z aplikacją | Zainstaluj pakiety bezpośrednio w projekcie, a następnie wdróż je w App Service tak, jakby były częścią aplikacji. W zależności od liczby posiadanych zależności i częstotliwości ich aktualizowania ta metoda może być Najprostszym sposobem na rozpoczęcie pracy wdrożenia. Należy sprawdzić, czy biblioteki muszą być zgodne z wersją języka Python na serwerze. w przeciwnym razie po wdrożeniu widoczne są błędy ukrywania. Tak samo, ponieważ wersje języka Python w rozszerzeniach lokacji App Service są dokładnie takie same jak wersje wydane w systemie python.org, można łatwo uzyskać zgodną wersję dla lokalnego tworzenia. |
| Środowiska wirtualne | Nieobsługiwane. Zamiast tego należy użyć funkcji grupowania i ustawić `PYTHONPATH` zmienną środowiskową, aby wskazywała lokalizację pakietów. |

### <a name="azure-app-service-kudu-console"></a>Azure App Service konsoli kudu

[Konsola kudu](https://github.com/projectkudu/kudu/wiki/Kudu-console) zapewnia bezpośredni i podniesiony dostęp do wiersza polecenia do serwera App Service i jego systemu plików. Jest to cenne narzędzie debugowania i pozwala na wykonywanie operacji interfejsu wiersza polecenia, takich jak instalowanie pakietów.

1. Otwórz kudu na stronie App Service na Azure Portal, wybierając pozycję **Narzędzia deweloperskie**  >  **Zaawansowane narzędzia**, a następnie wybierz pozycję **Przejdź**. Ta akcja powoduje przejście do adresu URL, który jest taki sam, jak adres URL podstawowego App Service z wyjątkiem `.scm` wstawiony. Na przykład, jeśli podstawowy adres URL to `https://vspython-test.azurewebsites.net/` kudu, jest on włączony `https://vspython-test.scm.azurewebsites.net/` (można zakładać za zakładką):

    ![Konsola kudu dla Azure App Service](media/python-on-azure-console01.png)

1. Wybierz pozycję **Debuguj konsolę**  >  **cmd** , aby otworzyć konsolę programu, w której można przejść do instalacji języka Python i zobaczyć, jakie biblioteki już istnieją.

1. Aby zainstalować pojedynczy pakiet:

    a. Przejdź do folderu instalacji języka Python, w którym chcesz zainstalować pakiet, taki jak *d:\home\python361x64*.

    b. Użyj `python.exe -m pip install <package_name>` , aby zainstalować pakiet.

    ![Przykład instalacji butelki za pomocą konsoli kudu dla Azure App Service](media/python-on-azure-console02.png)

1. Jeśli wcześniej wdrożono *requirements.txt* aplikacji na serwerze, należy zainstalować wszystkie te wymagania w następujący sposób:

    a. Przejdź do folderu instalacji języka Python, w którym chcesz zainstalować pakiet, taki jak *d:\home\python361x64*.

    b. Uruchom polecenie `python.exe -m pip install --upgrade -r d:\home\site\wwwroot\requirements.txt`.

    Zaleca się używanie *requirements.txt* , ponieważ jest łatwo odtworzenie dokładnego zestawu pakietów zarówno lokalnie, jak i na serwerze. Pamiętaj, aby odwiedzić konsolę programu po wdrożeniu zmian do *requirements.txt* i ponownie uruchomić polecenie.

> [!Note]
> Brak kompilatora C w App Service, więc należy zainstalować koło dla wszystkich pakietów z modułami rozszerzenia macierzystego. Wiele popularnych pakietów zapewnia własne koła. W przypadku pakietów, które nie używają `pip wheel <package_name>` na lokalnym komputerze deweloperskim, a następnie Przekaż kółko do lokacji. Aby zapoznać się z przykładem, zobacz [Zarządzanie wymaganymi pakietami przy użyciu requirements.txt](managing-required-packages-with-requirements-txt.md).

### <a name="kudu-rest-api"></a>Interfejs API REST usługi kudu

Zamiast korzystać z konsoli kudu za pośrednictwem Azure Portal, można uruchomić polecenia zdalnie za pośrednictwem interfejsu API REST kudu, publikując polecenie do `https://yoursite.scm.azurewebsites.net/api/command` . Na przykład aby zainstalować `bottle` pakiet, Opublikuj następujący kod JSON w celu `/api/command` :

```json
{
    "command": 'python.exe -m pip install bottle',
    "dir": '\home\python361x64'
}
```

Informacje o poleceniach i uwierzytelnianiu znajdują się w [dokumentacji kudu](https://github.com/projectkudu/kudu/wiki/REST-API).

Poświadczenia można także wyświetlić za pomocą `az webapp deployment list-publishing-profiles` polecenia za pośrednictwem interfejsu użytkownika platformy Azure (zobacz [AZ webapp Deployment](/cli/azure/webapp/deployment?view=azure-cli-latest#az-webapp-deployment-list-publishing-profiles)). Biblioteka pomocnika do ogłaszania poleceń kudu jest dostępna w witrynie [GitHub](https://github.com/lmazuel/azure-webapp-publish/blob/master/azure_webapp_publish/kudu.py#L42).

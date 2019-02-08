---
title: Konfigurowanie języka Python w usłudze Azure App Service (Windows)
description: Jak zainstalować interpreter języka Python i bibliotek w usłudze Azure App Service i konfigurowanie aplikacji sieci web, aby poprawnie odwołać się do tego interpretera.
ms.date: 01/07/2019
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: f68f12578ea7b5148aa018c21e14c334c33ad9a1
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55918926"
---
# <a name="how-to-set-up-a-python-environment-on-azure-app-service-windows"></a>Jak skonfigurować środowisko Python w usłudze Azure App Service (Windows)

> [!Important]
> Microsoft jest przestarzała rozszerzenia języka Python dla usługi App Service na Windows zgodnie z opisem w tym artykule na rzecz bezpośrednim wdrożeniu do [usługi App Service w systemie Linux](publishing-python-web-applications-to-azure-from-visual-studio.md).

[Usługa Azure App Service](https://azure.microsoft.com/services/app-service/) to oferta platformy jako usługi dla aplikacji sieci web, czy są one dostępne za pośrednictwem przeglądarki, interfejsów API REST używany przez własnych klientów lub wyzwalane przez zdarzenia przetwarzania witryn. Usługa App Service w pełni obsługuje przy użyciu języka Python do wdrożenia aplikacji.

Możliwe do dostosowania obsługi języka Python dla usługi Azure App Service jest przewidziana zbiór usługi App Service *rozszerzeń witryny* czy każdy zawiera określoną wersję środowiska uruchomieniowego Python. Następnie można zainstalować wszystkie odpowiednie pakiety bezpośrednio w środowisku, zgodnie z opisem w tym artykule. Dostosowując środowiska w samej usługi aplikacji, nie trzeba Obsługa pakietów w projektach aplikacji sieci web lub przekazać je za pomocą kodu aplikacji.

> [!Tip]
> Mimo że usługi App Service domyślnie ma środowisko Python 2.7 i języka Python 3.4 zainstalowane w katalogu głównego folderów na serwerze, nie można dostosować lub instalowanie pakietów w tych środowiskach, ani nie powinna zależeć od ich obecności. Zamiast tego należy polegać na rozszerzenie witryny, które możesz kontrolować, zgodnie z opisem w tym artykule.

## <a name="choose-a-python-version-through-the-azure-portal"></a>Wybierz wersję języka Python za pomocą witryny Azure portal

1. Tworzenie usługi App Service dla aplikacji sieci web w witrynie Azure portal.
1. Na stronie usługi App Service, przewiń do **narzędzia programistyczne** zaznacz **rozszerzenia**, a następnie wybierz **+ Dodaj**.
1. Przewiń w dół na liście, aby rozszerzenia, która zawiera wersję środowiska Python, chcesz, aby:

    ![Witryny Azure portal przedstawiający rozszerzenia języka Python](media/python-on-azure-extensions.png)

    > [!Tip]
    > Jeśli potrzebujesz starszej wersji środowiska Python i nie jest widoczna na liście rozszerzeń witryny, można nadal zainstalować go za pomocą usługi Azure Resource Manager zgodnie z opisem w następnej sekcji.

1. Zaznacz rozszerzenie, zaakceptuj postanowienia prawne, a następnie wybierz **OK**.
1. Po zakończeniu instalacji, w portalu pojawi się powiadomienie.

## <a name="choose-a-python-version-through-the-azure-resource-manager"></a>Wybierz wersję języka Python za pomocą usługi Azure Resource Manager

Jeśli wdrażasz usługi App Service przy użyciu szablonu usługi Azure Resource Manager, należy dodać rozszerzenie witryny jako zasób. W szczególności rozszerzenie jest wyświetlane jako zasób zagnieżdżonych ( `resources` obiekt w obszarze `resources`) z typem `siteextensions` i nazwę z [siteextensions.net](https://www.siteextensions.net/packages?q=Tags%3A%22python%22).

Na przykład, po dodaniu odwołania do `python361x64` (Python 3.6.1 x 64), Twój szablon może wyglądać podobnie do następującej (niektóre właściwości pominięcia):

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

## <a name="set-webconfig-to-point-to-the-python-interpreter"></a>Ustaw plik web.config, aby wskazać interpreter języka Python

Po zainstalowaniu rozszerzenia witryny (za pośrednictwem portalu lub szablonu usługi Azure Resource Manager), następnie punktu aplikacji *web.config* pliku do interpretera języka Python. *Web.config* pliku powoduje, że serwer internetowy IIS (7 +), które są uruchomione w usłudze App Service o jak powinna obsługiwać żądania języka Python za pomocą interfejsu FastCGI lub HttpPlatform.

Rozpocznij, wyszukując pełną ścieżkę do rozszerzenia witryny *python.exe*, a następnie utwórz i zmodyfikuj odpowiednie *web.config* pliku.

### <a name="find-the-path-to-pythonexe"></a>Znaleźć ścieżkę do python.exe

Rozszerzenie witryny Python jest zainstalowany na serwerze, w obszarze *d:\home* w folderze odpowiedniej wersji środowiska Python i architektura (z wyjątkiem kilku starszych wersji). Na przykład Python 3.6.1 x64 jest zainstalowany w *d:\home\python361x64*. Pełna ścieżka do interpretera języka Python jest następnie *d:\home\python361x64\python.exe*.

Aby wyświetlić określoną ścieżkę w usłudze App Service, wybierz **rozszerzenia** na stronie usługi App Service, następnie wybierz rozszerzenie na liście.

![Lista rozszerzeń w usłudze Azure App Service](media/python-on-azure-extension-list.png)

Spowoduje to otwarcie strony opis rozszerzenia zawierający ścieżkę:

![Szczegóły rozszerzenia usługi Azure App Service](media/python-on-azure-extension-detail.png)

Jeśli masz problemy z wyświetlaniem ścieżki dla rozszerzenia, można znaleźć je ręcznie przy użyciu konsoli:

1. Na stronie usługi App Service, wybierz **narzędzia programistyczne** > **konsoli**.
1. Wprowadź polecenie `ls ../home` lub `dir ..\home` się foldery najwyższego poziomu rozszerzeń, takich jak *Python361x64*.
1. Wprowadź polecenie, takie jak `ls ../home/python361x64` lub `dir ..\home\python361x64` Aby sprawdzić, czy zawiera on *python.exe* i inne pliki interpretera.

### <a name="configure-the-fastcgi-handler"></a>Konfigurowanie obsługi interfejsu FastCGI

FastCGI jest interfejsem, który działa na poziomie żądania. IIS odbiera połączenia przychodzące i przekazuje poszczególne żądania do aplikacji WSGI uruchomiony w jednej lub więcej trwały Python przetwarza. [Pakietu wfastcgi](https://pypi.io/project/wfastcgi) jest wstępnie zainstalowany i skonfigurowany przy użyciu każdego rozszerzenia witryny języka Python, dzięki czemu możesz go łatwo uaktywnić, dołączając kod w *web.config* , takich jak przedstawione poniżej dla aplikacji sieci web, w oparciu o Struktura Bottle. Należy pamiętać, że pełne ścieżki do *python.exe* i *procedurę wfastcgi.py* są umieszczane w `PythonHandler` klucza:

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

`<appSettings>` Zdefiniowanego w tym miejscu są dostępne dla aplikacji jako zmienne środowiskowe:

- Wartość `PYTHONPATH` może być swobodnie przedłużony, ale mogą zawierać katalogu głównego aplikacji.
- `WSGI_HANDLER` musi wskazywać aplikacją WSGI importowane z aplikacji.
- `WSGI_LOG` jest opcjonalne, ale zalecane do debugowania aplikacji.

Zobacz [Opublikuj na platformie Azure](publishing-python-web-applications-to-azure-from-visual-studio.md) więcej informacji na temat *web.config* aplikacje sieci web Bottle, Flask i Django zawartości.

### <a name="configure-the-httpplatform-handler"></a>Konfigurowanie obsługi HttpPlatform

Moduł HttpPlatform przekazuje połączenia z gniazdami bezpośrednio do autonomicznego proces języka Python. Przekazywanego ta umożliwia uruchamianie dowolnego serwera sieci web, ale wymaga skrypt uruchamiania, który uruchamia lokalny serwer internetowy. Określ skrypt w `<httpPlatform>` elementu *web.config*, gdzie `processPath` atrybutu punkty rozszerzenia witryny interpreter języka Python i `arguments` atrybut wskazuje się skrypt i argumenty chcesz udostępnić:

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

`HTTP_PLATFORM_PORT` Zmienna środowiskowa, pokazano poniżej zawiera port lokalny serwer powinien nasłuchiwać połączeń z hostem lokalnym. W tym przykładzie również pokazano, jak utworzyć inną zmienną środowiskową, jeśli to konieczne, w tym przypadku `SERVER_PORT`.

## <a name="install-packages"></a>Instalowanie pakietów

Interpreter języka Python zainstalowane za pomocą rozszerzenia witryny to tylko jeden fragment środowiska Python. Prawdopodobnie należy zainstalować różne pakiety w tym środowisku, jak również.

Aby zainstalować pakiety bezpośrednio w środowisku serwera, użyj jednej z następujących metod:

| Metody | Użycie |
| --- | --- |
| [Usługa Azure Konsola Kudu usługi App Service](#azure-app-service-kudu-console) | Instaluje pakiety interaktywnie. Pakiet musi być czysty języka Python lub należy opublikować koła. |
| [Interfejs API REST programu kudu](#kudu-rest-api) | Może służyć do automatyzacji instalacji pakietu aktualizacji.  Pakiet musi być czysty języka Python lub należy opublikować koła. |
| Pakietu z aplikacją | Instalowanie pakietów bezpośrednio do projektu, a następnie wdrożyć je w usłudze App Service tak, jakby były częścią Twojej aplikacji. W zależności od liczby zależności są i jak często je zaktualizować, ta metoda jest najprostszym sposobem wdrożenia pracy, przechodząc. Należy pamiętać, że biblioteki musi odpowiadać wersji języka Python na serwerze, w przeciwnym razie zostaną wyświetlone błędy zasłoniętej po wdrożeniu. Inaczej mówiąc, ponieważ wersje języka Python w usłudze App Service, rozszerzenia witryny są dokładnie takie same jak dla tych wersji wydanej w dniu python.org można łatwo uzyskać zgodnej wersji dla wdrożenia lokalnego. |
| Środowiska wirtualne | Nieobsługiwane. Zamiast tego należy użyć, tworzenie pakietów i ustawić `PYTHONPATH` zmiennej środowiskowej, aby wskazać lokalizację pakietów. |

### <a name="azure-app-service-kudu-console"></a>Usługa Azure Konsola Kudu usługi App Service

[Konsoli Kudu](https://github.com/projectkudu/kudu/wiki/Kudu-console) zapewnia dostęp bezpośrednie, z podwyższonym poziomem uprawnień z wiersza polecenia na serwerze usługi App Service i jego systemu plików. To jest zarówno przydatnym narzędziem debugowania i zezwala na operacje interfejsu wiersza polecenia, takie jak instalowanie pakietów.

1. Otwórz Kudu ze strony usługi App Service w witrynie Azure portal, wybierając pozycję **narzędzia programistyczne** > **Narzędzia zaawansowane**, a następnie wybierając pozycję **Przejdź**. Ta akcja powoduje przejście do adresu URL, który jest taka sama jak podstawowa aplikacja adres URL Twojej usługi z wyjątkiem z `.scm` wstawiony. Na przykład, jeśli podstawowy adres URL jest `https://vspython-test.azurewebsites.net/` , a następnie Kudu znajduje się na `https://vspython-test.scm.azurewebsites.net/` (który można dodać do zakładek):

    ![Konsola Kudu dla usługi Azure App Service](media/python-on-azure-console01.png)

1. Wybierz **konsoli debugowania** > **CMD** mogli otwierać konsolę, można nawigować do z instalacją języka Python i zobaczyć, jakie biblioteki już istnieje.

1. Aby zainstalować pojedynczy pakiet:

    a. Przejdź do folderu instalacji języka Python, w którym chcesz zainstalować pakiet, takie jak *d:\home\python361x64*.

    b. Użyj `python.exe -m pip install <package_name>` do zainstalowania pakietu.

    ![Przykład instalowania bottle za pośrednictwem konsoli Kudu dla usługi Azure App Service](media/python-on-azure-console02.png)

1. Jeśli udało Ci się wdrożyć *requirements.txt* dla aplikacji do serwera, zainstalować te wymagania w następujący sposób:

    a. Przejdź do folderu instalacji języka Python, w którym chcesz zainstalować pakiet, takie jak *d:\home\python361x64*.

    b. Uruchom polecenie `python.exe -m pip install --upgrade -r d:\home\site\wwwroot\requirements.txt`.

    Za pomocą *requirements.txt* jest zalecane, ponieważ jest łatwy do odtworzenia dokładnie pakietu ustawić zarówno lokalnie, jak i na serwerze. Po prostu Pamiętaj, aby odwiedzać konsolę po wdrożeniu zmiany *requirements.txt* i ponownie uruchom polecenie.

> [!Note]
> Istnieje nie kompilator języka C w usłudze App Service, więc trzeba zainstalować kółka kątem ewentualnych pakietów, za pomocą modułów macierzystych rozszerzeń. Wiele popularnych pakietów zapewniają własne koła. W przypadku pakietów, które nie należy używać `pip wheel <package_name>` na lokalnym komputerze deweloperskim i przekażesz wheel do witryny. Aby uzyskać przykład, zobacz [zarządzania wymagane pakiety przy użyciu pliku requirements.txt](managing-required-packages-with-requirements-txt.md).

### <a name="kudu-rest-api"></a>Interfejs API REST programu kudu

Zamiast korzystania z konsoli Kudu za pośrednictwem witryny Azure portal możesz zdalnie uruchamiać polecenia przy użyciu interfejsu API REST programu Kudu, publikując polecenie, aby `https://yoursite.scm.azurewebsites.net/api/command`. Na przykład, aby zainstalować `bottle` pakietu, Opublikuj następujące dane JSON do `/api/command`:

```json
{
    "command": 'python.exe -m pip install bottle',
    "dir": '\home\python361x64'
}
```

Aby uzyskać informacje o poleceniach oraz uwierzytelniania, zobacz [dokumentacji Kudu](https://github.com/projectkudu/kudu/wiki/REST-API).

Można również wyświetlić przy użyciu poświadczeń `az webapp deployment list-publishing-profiles` polecenia za pomocą wiersza polecenia platformy Azure (zobacz [az webapp deployment](/cli/azure/webapp/deployment?view=azure-cli-latest#az-webapp-deployment-list-publishing-profiles)). Biblioteka pomocnicza, umożliwiające publikowanie poleceń Kudu dostępnej w [GitHub](https://github.com/lmazuel/azure-webapp-publish/blob/master/azure_webapp_publish/kudu.py#L42).

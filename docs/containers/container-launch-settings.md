---
title: Visual Studio ustawień uruchamiania narzędzi kontenera
author: ghogen
description: Dowiedz się więcej na temat ustawień uruchamiania narzędzi kontenerów, które są powiązane ze Visual Studio aplikacjami konteneryzowanych.
ms.author: ghogen
ms.date: 08/15/2019
ms.technology: vs-azure
ms.topic: reference
ms.openlocfilehash: e50935145913bcd1f3c4457f4704376a0ac0f6ef
ms.sourcegitcommit: 162be102d2c22a1c4ad2c447685abd28e0e85d15
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2021
ms.locfileid: "109973242"
---
# <a name="container-tools-launch-settings"></a>Ustawienia uruchamiania narzędzi kontenerów

W *folderze Właściwości* w projekcie programu ASP.NET Core możesz znaleźć plik launchSettings.js, który zawiera ustawienia kontrolujące sposób, w jaki aplikacja internetowa jest uruchomiona na komputerze dewelopera. Aby uzyskać szczegółowe informacje na temat sposobu używania tego pliku podczas tworzenia ASP.NET, zobacz Use multiple environments in ASP.NET Core (Używanie wielu środowisk w [programie ASP.NET Core).](/aspnet/core/fundamentals/environments?view=aspnetcore-2.2&preserve-view=true) W *launchSettings.jsna* stronie ustawienia w sekcji Platformy **Docker** są powiązane ze Visual Studio konteneryzowanych aplikacji.

::: moniker range="vs-2017"

```json
    "Docker": {
      "commandName": "Docker",
      "launchBrowser": true,
      "launchUrl": "{Scheme}://{ServiceHost}:{ServicePort}"
    }
```

::: moniker-end
::: moniker range=">=vs-2019"

```json
    "Docker": {
      "commandName": "Docker",
      "launchBrowser": true,
      "launchUrl": "{Scheme}://{ServiceHost}:{ServicePort}",
      "environmentVariables": {
        "ASPNETCORE_URLS": "https://+:443;http://+:80",
        "ASPNETCORE_HTTPS_PORT": "44360"
      },
      "httpPort": 51803,
      "useSSL": true,
      "sslPort": 44360
    }
```

::: moniker-end

Ustawienie commandName określa, że ta sekcja dotyczy narzędzi kontenerów. W poniższej tabeli przedstawiono właściwości, które można ustawić w tej sekcji:

::: moniker range="vs-2017"

|Nazwa ustawienia|Wersja|Przykład|Opis|
|------------|-------|-------|---------------|
|launchBrowser|Visual Studio 2017|"launchBrowser": true|Wskazuje, czy uruchomić przeglądarkę po pomyślnym uruchomieniu projektu.|
|launchUrl|Visual Studio 2017|"launchUrl": "{Scheme}://{ServiceHost}:{ServicePort}"|Ten adres URL jest używany podczas uruchamiania przeglądarki.  Obsługiwane tokeny zastępcze dla tego ciągu to:<br>   {Scheme} — zastępowany wartością "http" lub "https" w zależności od tego, czy jest używany protokół SSL.<br>   {ServiceHost} — zwykle zastępowany przez "localhost". Jednak w przypadku określania wartości docelowych dla kontenerów systemu Windows Windows 10 RS3 lub starszej wersji jest on zastępowany adresem IP kontenera.<br>   {ServicePort} — zwykle zastępowany protokołem sslPort lub httpPort, w zależności od tego, czy jest używany protokół SSL.  Jednak w przypadku określania wartości docelowych dla kontenerów systemu Windows w wersji Windows 10 RS3 lub starszej jest ona zastępowana wartością "443" lub "80", w zależności od tego, czy jest używany protokół SSL.|

::: moniker-end

::: moniker range=">=vs-2019"

| Nazwa ustawienia         | Przykład                                               | Opis                                                                                                             |
| -------------------- | ----------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| commandLineArgs      | "commandLineArgs": "--mysetting myvalue"              | Te argumenty wiersza polecenia służące do uruchamiania aplikacji są używane podczas uruchamiania projektu w kontenerze.                                     |
| environmentVariables | "environmentVariables": {                             | Te wartości zmiennych środowiskowych są przekazywane do procesu podczas jego działania w kontenerze.                       |
|                      | "ASPNETCORE_URLS": " https://+:443 ; http://+:80 ",       |                                                                                                                         |
|                      | "ASPNETCORE_HTTPS_PORT": "44381"                      |                                                                                                                         |
|                      | }                                                     |                                                                                                                         |
| httpPort             | "httpPort": 24051                                     | Ten port na hoście jest mapowany na port 80 kontenera podczas uruchamiania kontenera.                                |
|                      |                                                       | Jeśli nie zostanie on nieokreślony, wartość zostanie wzięona z wartości iisSettings.                                                          |
| launchBrowser        | "launchBrowser": true                                 | Wskazuje, czy uruchomić przeglądarkę po pomyślnym uruchomieniu projektu.                                       |
| launchUrl            | "launchUrl": "{Scheme}://{ServiceHost}:{ServicePort}" | Ten adres URL jest używany podczas uruchamiania przeglądarki. Obsługiwane tokeny zastępcze dla tego ciągu to:                          |
|                      |                                                       | -{Scheme} - zastąpione przez "http" lub "https" w zależności od tego, czy jest używany protokół SSL.                                   |
|                      |                                                       | -{ServiceHost} - zwykle zastępowany przez "localhost".                                                                    |
|                      |                                                       | Jednak w przypadku określania wartości docelowych dla kontenerów systemu Windows Windows 10 RS3 lub starszej wersji jest on zastępowany adresem IP kontenera.           |
|                      |                                                       | -{ServicePort} - zwykle zastępowany sslPort lub httpPort, w zależności od tego, czy jest używany protokół SSL.                   |
|                      |                                                       | Jednak w przypadku określania wartości docelowych dla kontenerów systemu Windows na Windows 10 RS3 lub starszej wersji jest on zastępowany wartością "443" lub "80".         |
|                      |                                                       | w zależności od tego, czy jest używany protokół SSL.                                                                                       |
| sslPort              | "sslPort": 44381                                      | Ten port na hoście jest mapowany na port 443 kontenera podczas uruchamiania kontenera.                               |
|                      |                                                       | Jeśli nie zostanie on nieokreślony, wartość zostanie wzięte z wartości iisSettings.                                                          |
| useSSL               | "useSSL": true                                        | Wskazuje, czy używać protokołu SSL podczas uruchamiania projektu. Jeśli nie określono useSSL, ssl jest używany, gdy sslPort > 0. |

::: moniker-end

## <a name="next-steps"></a>Następne kroki

Skonfiguruj projekt, ustawiając właściwości [kompilacji narzędzi kontenera](container-msbuild-properties.md).

## <a name="see-also"></a>Zobacz też

- [Docker Compose właściwości kompilacji](docker-compose-properties.md)
- [Zarządzanie profilami uruchamiania dla Docker Compose](launch-profiles.md)

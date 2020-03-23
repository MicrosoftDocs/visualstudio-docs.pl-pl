---
title: Ustawienia uruchamiania narzędzi kontenerowych programu Visual Studio
author: ghogen
description: Omówienie procesu kompilacji narzędzi kontenerowych
ms.author: ghogen
ms.date: 08/15/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 1c9786c29573da3b0149a9ec6578f2ce58c4de9f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76542597"
---
# <a name="container-tools-launch-settings"></a>Ustawienia uruchamiania narzędzi kontenerowych

W folderze *Właściwości* w projekcie ASP.NET Core można znaleźć plik launchSettings.json, który zawiera ustawienia, które kontrolują sposób uruchamiania aplikacji sieci web na komputerze deweloperskim. Aby uzyskać szczegółowe informacje na temat sposobu używania tego pliku w ASP.NET rozwoju, zobacz [Używanie wielu środowisk w ASP.NET Core](/aspnet/core/fundamentals/environments?view=aspnetcore-2.2). W *launchSettings.json*ustawienia w sekcji **Docker** są związane z tym, jak program Visual Studio obsługuje konteneryzowane aplikacje.

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

CommandName ustawienie identyfikuje, że ta sekcja dotyczy narzędzi kontenera. W poniższej tabeli przedstawiono właściwości, które można ustawić w tej sekcji:

::: moniker range="vs-2017"

|Nazwa ustawienia|Wersja|Przykład|Opis|
|------------|-------|-------|---------------|
|launchBrowser|Visual Studio 2017|"launchBrowser": prawda|Wskazuje, czy uruchomić przeglądarkę po pomyślnym uruchomieniu projektu.|
|launchUrl|Visual Studio 2017|"launchUrl": "{Scheme}://{ServiceHost}:{ServicePort}"|Ten adres URL jest używany podczas uruchamiania przeglądarki.  Obsługiwane tokeny zastępcze dla tego ciągu to:<br>   {Scheme} — zastąpiono "http" lub "https" w zależności od tego, czy używany jest protokół SSL.<br>   {ServiceHost} — zwykle zastępowane "localhost". Podczas kierowania kontenerów systemu Windows w systemie Windows 10 RS3 lub starszych, jednak jest zastępowany ip kontenera.<br>   {ServicePort} — zwykle zastępowane sslPort lub httpPort, w zależności od tego, czy używany jest protokół SSL.  Podczas kierowania na kontenery systemu Windows w systemie Windows 10 RS3 lub starszych, jednak jest on zastąpiony albo "443" lub "80", w zależności od tego, czy jest używany SSL.|

::: moniker-end

::: moniker range=">=vs-2019"

| Nazwa ustawienia         | Przykład                                               | Opis                                                                                                             |
| -------------------- | ----------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| poleceniaLineArgs      | "commandLineArgs": "--mysetting myvalue"              | Te argumenty wiersza polecenia są używane podczas uruchamiania projektu w kontenerze.                                     |
| środowiskoWarzylne | "environmentVariables": {                             | Te wartości zmiennych środowiskowych są przekazywane do procesu, gdy jest uruchamiany w kontenerze.                       |
|                      | "ASPNETCORE_URLS": "https://+:443; http://+:80",       |                                                                                                                         |
|                      | "ASPNETCORE_HTTPS_PORT": "44381"                      |                                                                                                                         |
|                      | }                                                     |                                                                                                                         |
| Port http             | "httpPort": 24051                                     | Ten port na hoście jest mapowany do portu kontenera 80 podczas uruchamiania kontenera.                                |
|                      |                                                       | Jeśli nie określono, wartość jest pobierana z iisSettings wartość.                                                          |
| launchBrowser        | "launchBrowser": prawda                                 | Wskazuje, czy uruchomić przeglądarkę po pomyślnym uruchomieniu projektu.                                       |
| launchUrl            | "launchUrl": "{Scheme}://{ServiceHost}:{ServicePort}" | Ten adres URL jest używany podczas uruchamiania przeglądarki. Obsługiwane tokeny zastępcze dla tego ciągu to:                          |
|                      |                                                       | - {Scheme} - Zastąpiony "http" lub "https" w zależności od tego, czy używany jest protokół SSL.                                   |
|                      |                                                       | - {ServiceHost} - Zwykle zastępowany "localhost".                                                                    |
|                      |                                                       | Podczas kierowania kontenerów systemu Windows w systemie Windows 10 RS3 lub starszych, jednak jest zastępowany ip kontenera.           |
|                      |                                                       | - {ServicePort} - Zwykle zastępowane sslPort lub httpPort, w zależności od tego, czy używany jest protokół SSL.                   |
|                      |                                                       | Podczas kierowania na kontenery systemu Windows w systemie Windows 10 RS3 lub starszych, choć, jest zastępowany albo "443" lub "80",         |
|                      |                                                       | w zależności od tego, czy używany jest SSL.                                                                                       |
| sslPort (port sslport)              | "sslPort": 44381                                      | Ten port na hoście jest mapowany do portu kontenera 443 podczas uruchamiania kontenera.                               |
|                      |                                                       | Jeśli nie określono, wartość jest pobierana z iisSettings wartość.                                                          |
| useSSL               | "useSSL": prawda                                        | Wskazuje, czy podczas uruchamiania projektu ma być używany ssl. Jeśli użycieSSL nie jest określony, a następnie SSL jest używany, gdy sslPort > 0. |

::: moniker-end

## <a name="next-steps"></a>Następne kroki

Skonfiguruj projekt, ustawiając [właściwości kompilacji narzędzi kontenerowych](container-msbuild-properties.md).

## <a name="see-also"></a>Zobacz też

[Właściwości kompilacji docker compose](docker-compose-properties.md)

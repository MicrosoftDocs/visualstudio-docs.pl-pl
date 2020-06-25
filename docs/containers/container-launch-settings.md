---
title: Ustawienia uruchamiania narzędzi kontenera programu Visual Studio
author: ghogen
description: Przegląd procesu kompilacji narzędzi kontenera
ms.author: ghogen
ms.date: 08/15/2019
ms.technology: vs-azure
ms.topic: reference
ms.openlocfilehash: 07dd9dd4c5c61014eecf245719b142cdbaecbc38
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85283336"
---
# <a name="container-tools-launch-settings"></a>Ustawienia uruchamiania narzędzi kontenera

W folderze *Właściwości* w projekcie ASP.NET Core można znaleźć launchSettings.jsw pliku, który zawiera ustawienia kontrolujące sposób uruchamiania aplikacji sieci Web na komputerze deweloperskim. Aby uzyskać szczegółowe informacje na temat sposobu użycia tego pliku w programowaniu ASP.NET, zobacz [Używanie wielu środowisk w ASP.NET Core](/aspnet/core/fundamentals/environments?view=aspnetcore-2.2). W *launchSettings.jsna*, ustawienia w sekcji **Docker** dotyczą sposobu, w jaki program Visual Studio obsługuje aplikacje w kontenerach.

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

Ustawienie CommandName wskazuje, że ta sekcja dotyczy narzędzi kontenerów. W poniższej tabeli przedstawiono właściwości, które można ustawić w tej sekcji:

::: moniker range="vs-2017"

|Nazwa ustawienia|Wersja|Przykład|Opis|
|------------|-------|-------|---------------|
|launchBrowser|Visual Studio 2017|"launchBrowser": true|Wskazuje, czy po pomyślnym uruchomieniu projektu ma być uruchamiana przeglądarka.|
|launchUrl|Visual Studio 2017|"launchUrl": "{Schema}://{ServiceHost}: {serviceport}"|Ten adres URL jest używany podczas uruchamiania przeglądarki.  Obsługiwane tokeny zastępcze dla tego ciągu to:<br>   {Schema} — zamieniono na "http" lub "https" w zależności od tego, czy jest używany protokół SSL.<br>   {ServiceHost} — zazwyczaj zamieniono na "localhost". W przypadku kontenerów systemu Windows w systemie Windows 10 RS3 lub starszym są one zastępowane przez adres IP kontenera.<br>   {Serviceport} — zazwyczaj jest zastępowany sslPort lub httpPort, w zależności od tego, czy jest używany protokół SSL.  W przypadku kontenerów systemu Windows w systemie Windows 10 RS3 lub starszym są one zastępowane "443" lub "80", w zależności od tego, czy jest używany protokół SSL.|

::: moniker-end

::: moniker range=">=vs-2019"

| Nazwa ustawienia         | Przykład                                               | Opis                                                                                                             |
| -------------------- | ----------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| CommandLineArgs —      | "CommandLineArgs —": "--Setting wartość"              | Te argumenty wiersza polecenia służące do uruchamiania aplikacji są używane podczas uruchamiania projektu w kontenerze.                                     |
| environmentVariables | "environmentVariables": {                             | Te wartości zmiennych środowiskowych są przesyłane do procesu, gdy jest on uruchamiany w kontenerze.                       |
|                      | "ASPNETCORE_URLS": " https://+:443 ; http://+:80 ",       |                                                                                                                         |
|                      | "ASPNETCORE_HTTPS_PORT": "44381"                      |                                                                                                                         |
|                      | }                                                     |                                                                                                                         |
| httpPort             | "httpPort": 24051                                     | Ten port na hoście jest mapowany na port 80 kontenera podczas uruchamiania kontenera.                                |
|                      |                                                       | Jeśli nie zostanie określony, wartość jest pobierana z wartości iisSettings.                                                          |
| launchBrowser        | "launchBrowser": true                                 | Wskazuje, czy po pomyślnym uruchomieniu projektu ma być uruchamiana przeglądarka.                                       |
| launchUrl            | "launchUrl": "{Schema}://{ServiceHost}: {serviceport}" | Ten adres URL jest używany podczas uruchamiania przeglądarki. Obsługiwane tokeny zastępcze dla tego ciągu to:                          |
|                      |                                                       | -{Schema} — zastępuje "http" lub "https" w zależności od tego, czy jest używany protokół SSL.                                   |
|                      |                                                       | -{ServiceHost} — zazwyczaj zastępuje się "localhost".                                                                    |
|                      |                                                       | W przypadku kontenerów systemu Windows w systemie Windows 10 RS3 lub starszym są one zastępowane przez adres IP kontenera.           |
|                      |                                                       | -{Serviceport} — zazwyczaj jest zastępowany sslPort lub httpPort, w zależności od tego, czy jest używany protokół SSL.                   |
|                      |                                                       | W przypadku kontenerów systemu Windows w systemie Windows 10 RS3 lub starszym są one zastępowane "443" lub "80".         |
|                      |                                                       | w zależności od tego, czy jest używany protokół SSL.                                                                                       |
| sslPort              | "sslPort": 44381                                      | Ten port na hoście jest mapowany na port 443 kontenera podczas uruchamiania kontenera.                               |
|                      |                                                       | Jeśli nie zostanie określony, wartość jest pobierana z wartości iisSettings.                                                          |
| useSSL               | "useSSL": true                                        | Wskazuje, czy podczas uruchamiania projektu ma być używany protokół SSL. Jeśli nie określono useSSL, protokół SSL jest używany, gdy sslPort > 0. |

::: moniker-end

## <a name="next-steps"></a>Następne kroki

Skonfiguruj projekt, ustawiając [Właściwości kompilacji narzędzia kontenerów](container-msbuild-properties.md).

## <a name="see-also"></a>Zobacz też

[Docker Compose właściwości kompilacji](docker-compose-properties.md)

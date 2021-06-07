---
title: Zarządzanie profilami uruchamiania dla Docker Compose projektów
description: Dowiedz się, jak Docker Compose profilów uruchamiania i kontrolować, które usługi są uruchomione, gdy używasz Docker Compose w Visual Studio.
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.devlang: dotnet
ms.topic: how-to
ms.date: 05/10/2021
ms.author: ghogen
monikerRange: '>=vs-2019'
ms.openlocfilehash: e740ea3b7950c14bf11522c4e438a105b09eb7f6
ms.sourcegitcommit: ab5735d64a6ad7aecabf5d6df159888e3246bff5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111433704"
---
# <a name="manage-launch-profiles-for-docker-compose"></a>Zarządzanie profilami uruchamiania dla Docker Compose

Jeśli masz aplikację, która składa się z wielu usług i używa usługi Docker Compose, możesz skonfigurować, które usługi są uruchamiane i debugowane, tworząc lub edytując istniejący profil uruchamiania w Docker Compose uruchamiania. Profile uruchamiania umożliwiają dynamiczne uruchamianie tylko tych usług, które mają znaczenie dla bieżącego scenariusza. Możesz tworzyć i wybierać profile uruchamiania, aby dostosować środowisko debugowania i ustawić określone akcje uruchamiania, takie jak `Browser Launch URL` . Dostępna będzie również opcja wyboru poszczególnych usług lub profilu usługi Docker Compose, który również będzie wyglądał na plik Compose w celu określenia grupy usług do uruchomienia.

Aby uzyskać informacje o profilach Docker Compose, zobacz Using profiles with Compose (Używanie [profilów za pomocą narzędzia Compose).](https://docs.docker.com/compose/profiles/)
 
## <a name="prerequisites"></a>Wymagania wstępne

- [Visual Studio 2019 w wersji 16.10](https://visualstudio.microsoft.com/vs/) lub nowszej
- Rozwiązanie z [orkiestracji kontenerów z Docker Compose](tutorial-multicontainer.md)

## <a name="manage-launch-settings"></a>Zarządzanie ustawieniami uruchamiania

Rozważmy następujący Docker Compose, w którym *docker-compose.yml* ma pięć usług i trzy profile Compose (sieć Web, web1 i web2).

```yml
version: '3.9'

services:
  webapplication1:
    image: ${DOCKER_REGISTRY-}webapplication1
    profiles: [web, web1]
    build:
      context: .
      dockerfile: WebApplication1/Dockerfile

  webapplication2:
    image: ${DOCKER_REGISTRY-}webapplication2
    profiles: [web, web2]
    build:
      context: .
      dockerfile: WebApplication2/Dockerfile

  webapplication3:
    image: ${DOCKER_REGISTRY-}webapplication3
    profiles: [web]
    build:
      context: .
      dockerfile: WebApplication3/Dockerfile

  external1:
    image: redis

  external2:
    image: redis

```

Istnieje kilka opcji otwierania okna dialogowego Docker Compose uruchamiania:
- W Visual Studio pozycję   >  **Debuguj Zarządzaj Docker Compose uruchamiania:**

    ![Zrzut ekranu przedstawiający element menu Debuguj zarządzaj ustawieniami narzędzia Compose](media/launch-settings/debug-dropdown-manage-compose.png)

- Kliknij prawym przyciskiem myszy projekt aplikacji Visual Studio i wybierz pozycję Zarządzaj Docker Compose `docker-compose` **ustawieniami uruchamiania**

    ![Zrzut ekranu przedstawiający element menu kontekstowego](media/launch-settings/launch-settings-context-menu.png)

- Użyj polecenia Szybkie uruchamianie **(Ctrl** Q) i wyszukaj Docker Compose, aby znaleźć + wyżej wymienione  polecenie.

W poniższym przykładzie wybrano profil Utwórz, który filtruje listę Usługi do tylko trzech z `web1` pięciu uwzględnionych w tym profilu: 

!["Zrzut ekranu przedstawiający okno dialogowe ustawień uruchamiania"](media/launch-settings/launch-settings-create-profile.png)

Sekcja Docker Compose profile jest wyświetlana tylko wtedy, gdy w plikach *docker-compose.yml* są zdefiniowane profile.

W następnym przykładzie pokazano wybieranie między poszczególnymi usługami zamiast filtrowania do usług w profilu redagowania. W tym miejscu pokazujemy, jak wyglądałoby okno dialogowe, jeśli został utworzony nowy profil uruchamiania o nazwie , który uruchamia tylko dwie z pięciu usług, z debugowaniem `test2` `webapplication1` i bez `webapplication2` debugowania.  Ten profil uruchamiania uruchamia również przeglądarkę po uruchomieniu aplikacji i otwiera ją na stronie głównej aplikacji `webapplication1` . 

![Zrzut ekranu przedstawiający okno dialogowe ustawień uruchamiania z wybranymi usługami](media/launch-settings/launch-settings-selected.png)

Te informacje zostaną zapisane na stronie *launchSettings.js, jak* pokazano poniżej

```json
{
    "profiles": {
      "test2": {
        "commandName": "DockerCompose",
        "composeLaunchServiceName": "webapplication1",
        "serviceActions": {
          "external1": "DoNotStart",
          "external2": "DoNotStart",
          "webapplication1": "StartDebugging",
          "webapplication2": "StartWithoutDebugging",
          "webapplication3": "DoNotStart"
        },
        "composeLaunchAction": "LaunchBrowser",
        "commandVersion": "1.0",
        "composeLaunchUrl": "{Scheme}://localhost:{ServicePort}"
      }
   }
}
```

## <a name="create-a-launch-profile-that-uses-a-docker-compose-profile"></a>Tworzenie profilu uruchamiania, który używa Docker Compose profilu

Możesz również dodatkowo dostosować zachowania dotyczące uruchamiania, tworząc Visual Studio uruchamiania, które korzystają z profilów tworzenia.

Aby utworzyć inny profil, który korzysta z profilu Utwórz, wybierz pozycję **Użyj profilów** Docker Compose i wybierz pozycję `web1` . Teraz profil uruchamiania obejmuje trzy usługi — (które należą do `webapplication1` profilów `web` i `web1` Utwórz) `external1` i `external2` . Domyślnie usługi bez kodu źródłowego, takie jak i, mają domyślną akcję `external1`  `external2` Uruchom bez **debugowania**. Aplikacje .NET z kodem źródłowym domyślnie **uruchamiają debugowanie.**

> [!IMPORTANT]
> Jeśli usługa nie określi profilu Utwórz, zostanie on niejawnie uwzględniony we wszystkich profilach compose.

![Zrzut ekranu przedstawiający okno dialogowe ustawień uruchamiania z utworzonym innym profilem](media/launch-settings/launch-settings-create-profile.png)

Te informacje zostaną zapisane, jak pokazano w poniższym kodzie. Konfiguracja usługi i jej domyślna akcja nie są zapisywane, chyba że zmienisz akcję domyślną.

```json
{
  "profiles": {
    "test1": {
      "commandName": "DockerCompose",
      "composeProfile": {
         "includes": [
            "web1"
         ]
      },
      "commandVersion": "1.0"
    }
  }
}
```

Możesz również zmienić akcję webapplication1 na **Start bez debugowania**. Ustawienia w *launchSettings.jsnastępnie* wyglądają jak następujący kod:

```json
{
  "profiles": {
    "test1": {
        "commandName": "DockerCompose",
        "composeProfile": {
          "includes": [
              "web1"
              ],
          "serviceActions": {
              "webapplication1": "StartWithoutDebugging"
          }
        },
    "commandVersion": "1.0"
    }
  }
}
```

## <a name="properties"></a>Właściwości

Poniżej znajduje się opis każdej właściwości wlaunchSettings.js *na*:

|Właściwość| Opis|
| - | - |
|Commandname| Nazwa polecenia. Wartość domyślna to "DockerCompose"|
|CommandVersion| Numer wersji używany do zarządzania schematem profilu uruchamiania dockerCompose.|
|composeProfile| Właściwość nadrzędna definiująca definicję profilu uruchamiania. Jego właściwościami podrzędnmi są `includes` i `serviceActions`|
|composeProfile — obejmuje | Lista nazw profilów redagowania, które tworzą profil uruchamiania.|
|composeProfile — serviceActions | Wyświetla listę wybranych profilów, usług i akcji uruchamiania poszczególnych usług|
|serviceActions | Wyświetla listę wybranych usług i akcję uruchamiania.|
|composeLaunchServiceName| Jeśli określono parametr DockerLaunchAction lub DockerLaunchBrowser, nazwa usługi DockerServiceName jest nazwą usługi, która powinna zostać uruchomiona. Ta właściwość pozwala określić, która usługa w Docker Compose zostanie uruchomiona.|
|composeLaunchAction| Określa akcję uruchamiania do wykonania na **klawiszach F5** lub **Ctrl** + **F5.** Dozwolone wartości to None, LaunchBrowser i LaunchWCFTestClient.|
|composeLaunchUrl| Adres URL do użycia podczas uruchamiania przeglądarki. Prawidłowe tokeny zastępcze to "{ServiceIPAddress}", "{ServicePort}" i "{Scheme}". Na przykład: {Scheme}://{ServiceIPAddress}:{ServicePort}|

## <a name="next-steps"></a>Następne kroki

Dowiedz się więcej o tym, jak działa narzędzie Container Tools, czytając Visual Studio Container Tools build and debug overview (Omówienie kompilowania i [debugowania narzędzi kontenerów).](container-build.md)

## <a name="see-also"></a>Zobacz też

- [Visual Studio ustawień uruchamiania narzędzi kontenera](container-launch-settings.md)

- [Docker Compose ustawień kompilacji](docker-compose-properties.md)

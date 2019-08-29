---
title: Narzędzia kontenera programu Visual Studio Docker Compose ustawienia kompilacji
author: ghogen
description: Przegląd procesu kompilacji narzędzi kontenera
ms.author: ghogen
ms.date: 08/12/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: bdd835effaa691660d6462787bef590c2b985e49
ms.sourcegitcommit: 3cda0d58c5cf1985122b8977b33a171c7359f324
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2019
ms.locfileid: "70158392"
---
# <a name="docker-compose-build-properties"></a>Docker Compose właściwości kompilacji

Oprócz właściwości kontrolujących poszczególne projekty platformy Docker, opisanych we właściwościach [kompilacji narzędzi kontenera](container-msbuild-properties.md), można również dostosować sposób, w jaki program Visual Studio kompiluje projekty Docker Compose przez ustawienie właściwości Docker Compose, które MSBuild używa do kompilowania rozwiązania. Możesz również kontrolować sposób, w jaki debuger programu Visual Studio uruchamia Docker Compose aplikacje przez ustawienie etykiet plików w Docker Compose pliki konfiguracji.

## <a name="how-to-set-the-msbuild-properties"></a>Jak ustawić właściwości programu MSBuild

Aby ustawić wartość właściwości, edytuj plik projektu. W przypadku właściwości Docker Compose jest to plik projektu z rozszerzeniem dcproj, chyba że wskazano inaczej w tabeli w następnej sekcji. Załóżmy na przykład, że chcesz określić uruchamianie przeglądarki po rozpoczęciu debugowania. `DockerLaunchAction` Właściwość w pliku projektu. dcproj można ustawić w następujący sposób.

```xml
<PropertyGroup>
   <DockerLaunchAction>LaunchBrowser</DockerLaunchAction>
</PropertyGroup>
```

Możesz dodać ustawienie właściwości do istniejącego `PropertyGroup` elementu lub jeśli nie istnieje, Utwórz nowy `PropertyGroup` element.


## <a name="docker-compose-msbuild-properties"></a>Docker Compose właściwości programu MSBuild

W poniższej tabeli przedstawiono właściwości programu MSBuild dostępne dla projektów Docker Compose.

| Nazwa właściwości | Lokalizacja | Opis | Wartość domyślna  |
|---------------|----------|-------------|----------------|
|DockerComposeProjectPath|CSPROJ lub vbproj|Ścieżka względna do pliku platformy Docker-redagowanie projektu (dcproj). Ta wartość jest używana podczas publikowania projektu usługi, aby znaleźć odpowiednie ustawienia kompilacji obrazu przechowywane w pliku Docker-Compose. yml.|-|
|DockerLaunchAction| dcproj | Określa akcję uruchamiania do wykonania na F5 lub CTRL + F5.  Dozwolone wartości to None, LaunchBrowser i LaunchWCFTestClient|Brak|
|DockerLaunchBrowser| dcproj | Wskazuje, czy ma zostać uruchomiona przeglądarka. Ignorowany, jeśli określono DockerLaunchAction. | False |
|DockerServiceName| dcproj|Jeśli określono DockerLaunchAction lub DockerLaunchBrowser, DockerServiceName jest nazwą usługi, która powinna zostać uruchomiona.  Służy do określenia, który z potencjalnie wielu projektów, do których może się odwoływać plik platformy Docker, zostanie uruchomiony.|-|
|DockerServiceUrl| dcproj | Adres URL, który ma być używany podczas uruchamiania przeglądarki.  Prawidłowe tokeny zastępcze to "{serviceipaddress}", "{serviceport}" i "{Schema}".  Na przykład: {Schema}://{ServiceIPAddress}: {serviceport}|-|
|DockerTargetOS| dcproj | Docelowy system operacyjny używany podczas kompilowania obrazu platformy Docker.|-|

## <a name="docker-compose-file-labels"></a>Docker Compose etykiety plików

Niektóre ustawienia można również przesłonić, umieszczając plik o nazwie *Docker-Compose. vs. Debug. yml* (dla konfiguracji **debugowania** ) lub *Docker-Compose. vs. release. yml* (dla konfiguracji **wydania** ) w tym samym katalogu, w którym znajduje *się plik Docker-Compose. yml* .  W tym pliku można określić następujące ustawienia:

```yml
services:
  webapplication1:
    labels:
      com.microsoft.visualstudio.debuggee.workingdirectory: "C:\\my_app_folder"
```

Użyj podwójnych cudzysłowów wokół wartości, jak w poprzednim przykładzie, i użyj ukośnika odwrotnego jako znaku ucieczki dla ukośników odwrotnych w ścieżkach.

|Nazwa etykiety|Opis|
|----------|-----------|
|com. Microsoft. VisualStudio. debugowanego obiektu. arguments|Argumenty przekazane do programu podczas uruchamiania debugowania. W przypadku aplikacji platformy .NET Core jest to zwykle zestaw dodatkowych ścieżek wyszukiwania dla pakietów NuGet, po których następuje ścieżka do zestawu wyjściowego projektu.|
|com. Microsoft. VisualStudio. debugowanego obiektu. killprogram|To polecenie służy do zatrzymania programu debugowanego obiektu, który działa wewnątrz kontenera (w razie potrzeby).|
|com. Microsoft. VisualStudio. debugowanego obiektu. program|Program został uruchomiony podczas uruchamiania debugowania. W przypadku aplikacji platformy .NET Core zwykle jest to **dotnet**.|
|com. Microsoft. VisualStudio. debugowanego obiektu. WorkingDirectory|Katalog używany jako katalog początkowy podczas uruchamiania debugowania. Jest to zazwyczaj */App* dla kontenerów systemu Linux lub kontenerów *C:\app* for Windows.|

## <a name="next-steps"></a>Następne kroki

Aby uzyskać ogólne informacje na temat właściwości programu MSBuild, zobacz [Właściwości programu MSBuild](../msbuild/msbuild-properties.md).

## <a name="see-also"></a>Zobacz także

[Właściwości kompilacji narzędzi kontenera](container-msbuild-properties.md)

[Ustawienia uruchamiania narzędzi kontenera](container-launch-settings.md)

[Właściwości zarezerwowane i dobrze znane dla programu MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)

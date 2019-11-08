---
title: Narzędzia kontenera programu Visual Studio Docker Compose ustawienia kompilacji
author: ghogen
description: Przegląd procesu kompilacji narzędzi kontenera
ms.author: ghogen
ms.date: 08/12/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 4ea1a936de215340cc13971e7a70a8d795d36cbb
ms.sourcegitcommit: ba0fef4f5dca576104db9a5b702670a54a0fcced
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73713933"
---
# <a name="docker-compose-build-properties"></a>Docker Compose właściwości kompilacji

Oprócz właściwości kontrolujących poszczególne projekty platformy Docker, opisanych we [właściwościach kompilacji narzędzi kontenera](container-msbuild-properties.md), można również dostosować sposób, w jaki program Visual Studio kompiluje projekty Docker Compose przez ustawienie właściwości Docker Compose, które MSBuild używa do kompilowania rozwiązania. Możesz również kontrolować sposób, w jaki debuger programu Visual Studio uruchamia Docker Compose aplikacje przez ustawienie etykiet plików w Docker Compose pliki konfiguracji.

## <a name="how-to-set-the-msbuild-properties"></a>Jak ustawić właściwości programu MSBuild

Aby ustawić wartość właściwości, edytuj plik projektu. W przypadku właściwości Docker Compose ten plik projektu jest jednym z rozszerzeniem. dcproj, o ile nie wskazano inaczej w tabeli w następnej sekcji. Załóżmy na przykład, że chcesz określić uruchamianie przeglądarki po rozpoczęciu debugowania. Właściwość `DockerLaunchAction` można ustawić w pliku projektu. dcproj w następujący sposób.

```xml
<PropertyGroup>
   <DockerLaunchAction>LaunchBrowser</DockerLaunchAction>
</PropertyGroup>
```

Możesz dodać ustawienie właściwości do istniejącego elementu `PropertyGroup` lub jeśli nie istnieje, Utwórz nowy element `PropertyGroup`.

## <a name="docker-compose-msbuild-properties"></a>Docker Compose właściwości programu MSBuild

W poniższej tabeli przedstawiono właściwości programu MSBuild dostępne dla projektów Docker Compose.

| Nazwa właściwości | Lokalizacja | Opis | Wartość domyślna  |
|---------------|----------|-------------|----------------|
|AdditionalComposeFiles|dcproj|Określa dodatkowe pliki redagowania na liście rozdzielanej średnikami do wysłania do Docker-Compose. exe dla wszystkich poleceń. Ścieżki względne z pliku projektu platformy Docker (dcproj) są dozwolone.|-|
|DockerComposeBaseFilePath|dcproj|Określa pierwszą część nazw plików w plikach do redagowania platformy Docker bez rozszerzenia *. yml* . Na przykład: <br>1. DockerComposeBaseFilePath = null/undefined: Użyj podstawowej ścieżki pliku *Docker-Zredaguj*, a pliki będą nazwane *Docker-Compose. yml* i *Docker-Compose. override. yml*<br>2. DockerComposeBaseFilePath = *mydockercompose*: pliki będą nazwane *mydockercompose. yml* i *mydockercompose. override. yml*<br> 3. DockerComposeBaseFilePath = *.. \mydockercompose*: pliki będą mieć jeden poziom. |Docker-Compose|
|DockerComposeBuildArguments|dcproj|Określa dodatkowe parametry, które mają zostać przekazane do polecenia `docker-compose build`. Na przykład:`--parallel --pull` |
|DockerComposeDownArguments|dcproj|Określa dodatkowe parametry, które mają zostać przekazane do polecenia `docker-compose down`. Na przykład:`--timeout 500`|-|  
|DockerComposeProjectPath|CSPROJ lub vbproj|Ścieżka względna do pliku platformy Docker-redagowanie projektu (dcproj). Ustaw tę właściwość podczas publikowania projektu usługi, aby znaleźć skojarzone ustawienia kompilacji obrazu przechowywane w pliku Docker-Compose. yml.|-|
|DockerComposeUpArguments|dcproj|Określa dodatkowe parametry, które mają zostać przekazane do polecenia `docker-compose up`. Na przykład:`--timeout 500`|-|
|DockerLaunchAction| dcproj | Określa akcję uruchamiania do wykonania na F5 lub CTRL + F5.  Dozwolone wartości to None, LaunchBrowser i LaunchWCFTestClient|Brak|
|DockerLaunchBrowser| dcproj | Wskazuje, czy ma zostać uruchomiona przeglądarka. Ignorowany, jeśli określono DockerLaunchAction. | False |
|DockerServiceName| dcproj|Jeśli określono DockerLaunchAction lub DockerLaunchBrowser, DockerServiceName jest nazwą usługi, która powinna zostać uruchomiona.  Użyj tej właściwości, aby określić, który z potencjalnie wielu projektów, do których może się odwoływać plik platformy Docker, zostanie uruchomiony.|-|
|DockerServiceUrl| dcproj | Adres URL, który ma być używany podczas uruchamiania przeglądarki.  Prawidłowe tokeny zastępcze to "{serviceipaddress}", "{serviceport}" i "{Schema}".  Na przykład: {Schema}://{ServiceIPAddress}: {serviceport}|-|
|DockerTargetOS| dcproj | Docelowy system operacyjny używany podczas kompilowania obrazu platformy Docker.|-|

> [!NOTE]
> DockerComposeBuildArguments, DockerComposeDownArguments i DockerComposeUpArguments są nowe w programie Visual Studio 2019 w wersji 16,3.

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
|com. Microsoft. VisualStudio. debugowanego obiektu. arguments|Argumenty przekazane do programu podczas uruchamiania debugowania. W przypadku aplikacji platformy .NET Core te argumenty są zwykle dodatkowymi ścieżkami wyszukiwania pakietów NuGet, po których następuje ścieżka do zestawu wyjściowego projektu.|
|com. Microsoft. VisualStudio. debugowanego obiektu. killprogram|To polecenie służy do zatrzymania programu debugowanego obiektu, który działa wewnątrz kontenera (w razie potrzeby).|
|com. Microsoft. VisualStudio. debugowanego obiektu. program|Program został uruchomiony podczas uruchamiania debugowania. W przypadku aplikacji .NET Core to ustawienie jest zazwyczaj **dotnet**.|
|com. Microsoft. VisualStudio. debugowanego obiektu. WorkingDirectory|Katalog używany jako katalog początkowy podczas uruchamiania debugowania. To ustawienie jest zwykle */App* dla kontenerów systemu Linux lub kontenerów *C:\app* for Windows.|

## <a name="next-steps"></a>Następne kroki

Aby uzyskać ogólne informacje na temat właściwości programu MSBuild, zobacz [Właściwości programu MSBuild](../msbuild/msbuild-properties.md).

## <a name="see-also"></a>Zobacz także

[Właściwości kompilacji narzędzi kontenera](container-msbuild-properties.md)

[Ustawienia uruchamiania narzędzi kontenera](container-launch-settings.md)

[Właściwości zarezerwowane i dobrze znane dla programu MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)

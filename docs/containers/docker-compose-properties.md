---
title: Ustawienia kompilacji dokomunika do kompozycji narzędzi kontenerowych programu Visual Studio
author: ghogen
description: Omówienie procesu kompilacji narzędzi kontenerowych
ms.author: ghogen
ms.date: 08/12/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 85cb8745a14439cfb09036a1bc96e6bd0fa15ae4
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "79988517"
---
# <a name="docker-compose-build-properties"></a>Właściwości kompilacji docker compose

Oprócz właściwości, które kontrolują poszczególne projekty platformy Docker, opisane w [narzędzia kontenera właściwości kompilacji,](container-msbuild-properties.md)można również dostosować sposób Visual Studio tworzy projektów docker compose, ustawiając właściwości Docker Compose, które MSBuild używa do tworzenia rozwiązania. Można również kontrolować sposób, w jaki debuger programu Visual Studio uruchamia aplikacje docker compose, ustawiając etykiety plików w plikach konfiguracyjnych docker compose.

## <a name="how-to-set-the-msbuild-properties"></a>Jak ustawić właściwości MSBuild

Aby ustawić wartość właściwości, edytuj plik projektu. W przypadku właściwości docker compose ten plik projektu jest plikiem z rozszerzeniem .dcproj, chyba że w tabeli w następnej sekcji wskazano inaczej. Załóżmy na przykład, że chcesz określić, aby uruchomić przeglądarkę po uruchomieniu debugowania. `DockerLaunchAction` Właściwość można ustawić w pliku projektu .dcproj w następujący sposób.

```xml
<PropertyGroup>
   <DockerLaunchAction>LaunchBrowser</DockerLaunchAction>
</PropertyGroup>
```

Można dodać ustawienie właściwości do `PropertyGroup` istniejącego elementu lub jeśli go nie `PropertyGroup` ma, utwórz nowy element.

## <a name="docker-compose-msbuild-properties"></a>Właściwości narzędzia Docker Compose w programie MSBuild

W poniższej tabeli przedstawiono właściwości MSBuild dostępne dla projektów dokceny redagowania.

| Nazwa właściwości | Lokalizacja | Opis | Wartość domyślna  |
|---------------|----------|-------------|----------------|
|Dodatkowe ścieżki pliku plików|dcproj ( dcproj )|Określa dodatkowe pliki redagowania na liście rozdzielanych średnikami, które mają być wysyłane do programu docker-compose.exe dla wszystkich poleceń. Ścieżki względne z pliku projektu docker-compose (dcproj) są dozwolone.|-|
|Ścieżka dockerComposeBaseFilePath|dcproj ( dcproj )|Określa pierwszą część nazwy plików plików docker-compose bez rozszerzenia *.yml.* Przykład: <br>1. DockerComposeBaseFilePath = null/undefined: użyj ścieżki pliku podstawowego *docker-compose*, a pliki będą nazywać się *docker-compose.yml* i *docker-compose.override.yml*<br>2. DockerComposeBaseFilePath = *mydockercompose*: pliki będą nazywać się *mydockercompose.yml* i *mydockercompose.override.yml*<br> 3. DockerComposeBaseFilePath = *.. \mydockercompose*: pliki będą się o jeden poziom. |docker-compose|
|DockerComposeBuildArgument (DockerComposeBuildArgument)|dcproj ( dcproj )|Określa dodatkowe parametry, które `docker-compose build` mają być przedajne do polecenia. Na przykład: `--parallel --pull` |
|DockerComposeDownArgument ( DockerComposeDownArgument )|dcproj ( dcproj )|Określa dodatkowe parametry, które `docker-compose down` mają być przedajne do polecenia. Na przykład: `--timeout 500`|-|  
|Ścieżka dockerComposeProjectPath|csproj lub vbproj|Ścieżka względna do pliku projektu docker-compose (dcproj). Ustaw tę właściwość podczas publikowania projektu usługi, aby znaleźć skojarzone ustawienia kompilacji obrazu przechowywane w pliku docker-compose.yml.|-|
|DockerComposeUpArgument ( DockerComposeUpArgument )|dcproj ( dcproj )|Określa dodatkowe parametry, które `docker-compose up` mają być przedajne do polecenia. Na przykład: `--timeout 500`|-|
|Tryb DockerDevelopmentMode|dcproj ( dcproj )| Określa, czy "build-on-host" optymalizacji ("Fast Mode" debugowania) jest włączona.  Dozwolone wartości są **szybkie** i **regularne**. | Szybko |
|DockerLaunchaction (DockerLaunchAction)| dcproj ( dcproj ) | Określa akcję uruchamiania, która ma być emigatorem F5 lub Ctrl+F5.  Dozwolone wartości to None, LaunchBrowser i LaunchWCFTestClient|Brak|
|DockerLaunchBrowser| dcproj ( dcproj ) | Wskazuje, czy ma zostać uruchomiona przeglądarka. Ignorowane, jeśli DockerLaunchAction jest określony. | False |
|Nazwa usługi Docker| dcproj ( dcproj )|Jeśli DockerLaunchAction lub DockerLaunchBrowser są określone, a następnie DockerServiceName jest nazwą usługi, która powinna zostać uruchomiona.  Ta właściwość służy do określenia, które z potencjalnie wielu projektów, do których można odwoływać się plik docker-compose, zostanie uruchomiony.|-|
|Usługa DockerServiceUrl| dcproj ( dcproj ) | Adres URL, którego ma być używany podczas uruchamiania przeglądarki.  Prawidłowe tokeny zastępcze to "{ServiceIPAddress}", "{ServicePort}" i "{Scheme}".  Na przykład: {Scheme}://{ServiceIPAddress}:{ServicePort}|-|
|DockerTargetOS (DockerTargetOS)| dcproj ( dcproj ) | Docelowy system operacyjny używany podczas tworzenia obrazu platformy Docker.|-|

## <a name="example"></a>Przykład

Jeśli zmienisz lokalizację plików docker compose, `DockerComposeBaseFilePath` ustawiając ścieżkę względną, należy również upewnić się, że kontekst kompilacji zostanie zmieniony, tak aby odwoływał się do folderu rozwiązania. Na przykład jeśli plik redagowania docker jest folder o nazwie *DockerComposeFiles*, następnie docker pliku redagowania należy ustawić kontekst kompilacji na ".." lub ".. /..", w zależności od tego, gdzie jest względem folderu rozwiązania.

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="15.0" Sdk="Microsoft.Docker.Sdk">
  <PropertyGroup Label="Globals">
    <ProjectVersion>2.1</ProjectVersion>
    <DockerTargetOS>Windows</DockerTargetOS>
    <ProjectGuid>154022c1-8014-4e9d-bd78-6ff46670ffa4</ProjectGuid>
    <DockerLaunchAction>LaunchBrowser</DockerLaunchAction>
    <DockerServiceUrl>{Scheme}://{ServiceIPAddress}{ServicePort}</DockerServiceUrl>
    <DockerServiceName>webapplication1</DockerServiceName>
    <DockerComposeBaseFilePath>DockerComposeFiles\mydockercompose</DockerComposeBaseFilePath>
    <AdditionalComposeFilePaths>AdditionalComposeFiles\myadditionalcompose.yml</AdditionalComposeFilePaths>
  </PropertyGroup>
  <ItemGroup>
    <None Include="DockerComposeFiles\mydockercompose.override.yml">
      <DependentUpon>DockerComposeFiles\mydockercompose.yml</DependentUpon>
    </None>
    <None Include="DockerComposeFiles\mydockercompose.yml" />
    <None Include=".dockerignore" />
  </ItemGroup>
</Project>
```

Plik *mydockercompose.yml* powinien wyglądać następująco, z kontekstem kompilacji ustawionym na ścieżkę względną folderu rozwiązania (w tym przypadku `..`).

```yml
version: '3.4'

services:
  webapplication1:
    image: ${DOCKER_REGISTRY-}webapplication1
    build:
      context: ..
      dockerfile: WebApplication1\Dockerfile
```

> [!NOTE]
> DockerComposeBuildArguments, DockerComposeDownArguments i DockerComposeUpArguments są nowe w programie Visual Studio 2019 w wersji 16.3.

## <a name="docker-compose-file-labels"></a>Etykiety plików docker compose

Można również zastąpić niektóre ustawienia, umieszczając plik o nazwie *docker-compose.vs.debug.yml* (dla konfiguracji **debugowania)** lub *docker-compose.vs.release.yml* (dla konfiguracji **wersji)** w tym samym katalogu co plik *docker-compose.yml.*  W tym pliku można określić ustawienia w następujący sposób:

```yml
services:
  webapplication1:
    labels:
      com.microsoft.visualstudio.debuggee.workingdirectory: "C:\\my_app_folder"
```

Użyj cudzysłowów podwójnych wokół wartości, jak w poprzednim przykładzie, i użyj ukośnika odwrotnego jako znaku ucieczki dla ukośnienia w ścieżkach.

|Nazwa etykiety|Opis|
|----------|-----------|
|argumentów witryny com.microsoft.visualstudio.debuggee.arguments|Argumenty przekazywane do programu podczas uruchamiania debugowania. W przypadku aplikacji .NET Core te argumenty są zazwyczaj dodatkowe ścieżki wyszukiwania dla pakietów NuGet, po których następuje ścieżka do zestawu wyjściowego projektu.|
|program com.microsoft.visualstudio.debuggee.killprogram|To polecenie służy do zatrzymania programu debuggee, który działa wewnątrz kontenera (w razie potrzeby).|
|plik com.microsoft.visualstudio.debuggee.program|Program uruchomiony podczas uruchamiania debugowania. W przypadku aplikacji .NET Core to ustawienie jest zazwyczaj **dotnet**.|
|com.microsoft.visualstudio.debuggee.workingdirectory|Katalog używany jako katalog początkowy podczas uruchamiania debugowania. To ustawienie jest zazwyczaj */app* dla kontenerów systemu Linux lub *C:\app* dla kontenerów systemu Windows.|

## <a name="customize-the-app-startup-process"></a>Dostosowywanie procesu uruchamiania aplikacji

Przed uruchomieniem aplikacji można uruchomić polecenie lub `entrypoint` skrypt niestandardowy przy użyciu tego ustawienia i uzależnieniu jej od konfiguracji. Na przykład, jeśli chcesz skonfigurować certyfikat tylko w `update-ca-certificates`trybie **debugowania,** uruchamiając , ale nie w trybie **wydania,** można dodać następujący kod tylko w *docker-compose.vs.debug.yml:*

```yml
services:
  webapplication1:
    entrypoint: "sh -c 'update-ca-certificates && tail -f /dev/null'"
    labels:
      ...
```

Jeśli *pominięto docker-compose.vs.release.yml* lub *docker-compose.vs.debug.yml* następnie Visual Studio generuje jeden na podstawie ustawień domyślnych.

## <a name="next-steps"></a>Następne kroki

Aby uzyskać informacje na temat właściwości MSBuild ogólnie, zobacz [MSBuild Właściwości](../msbuild/msbuild-properties.md).

## <a name="see-also"></a>Zobacz też

[Właściwości kompilacji narzędzi kontenerowych](container-msbuild-properties.md)

[Ustawienia uruchamiania narzędzi kontenerowych](container-launch-settings.md)

[MSBuild zastrzeżone i dobrze znane właściwości](../msbuild/msbuild-reserved-and-well-known-properties.md)

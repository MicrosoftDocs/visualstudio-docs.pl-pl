---
title: Docker Compose ustawień kompilacji
author: ghogen
description: Dowiedz się, jak edytować Docker Compose kompilacji, aby dostosować sposób Visual Studio kompilacji i Docker Compose aplikacji.
ms.custom: SEO-VS-2020
ms.author: ghogen
ms.date: 04/06/2021
ms.technology: vs-azure
ms.topic: reference
ms.openlocfilehash: ed4b2a0dc1dc7a0520bf8e83ab1968a3815196e0
ms.sourcegitcommit: e12d6cdaeb37564f05361965db2ec8ad0d4f21ad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2021
ms.locfileid: "108025868"
---
# <a name="docker-compose-build-properties"></a>Docker Compose właściwości kompilacji

Oprócz właściwości sterujących poszczególnymi projektami platformy Docker, opisanych we właściwościach kompilacji narzędzi [Container Tools,](container-msbuild-properties.md)można również dostosować sposób kompilowania projektów platformy Docker Compose za pomocą programu Visual Studio, ustawiając właściwości platformy Docker Compose używane przez program MSBuild do kompilowania rozwiązania. Możesz również kontrolować sposób, w jaki debuger Visual Studio uruchamia aplikacje Docker Compose, ustawiając etykiety plików w Docker Compose konfiguracji.

## <a name="how-to-set-the-msbuild-properties"></a>Jak ustawić właściwości programu MSBuild

Aby ustawić wartość właściwości, edytuj plik projektu. W Docker Compose tego pliku projektu jest to plik z rozszerzeniem dcproj, chyba że określono inaczej w tabeli w następnej sekcji. Załóżmy na przykład, że chcesz określić, aby przeglądarka uruchamiała się po rozpoczęciu debugowania. Właściwość w pliku projektu dcproj można ustawić `DockerLaunchAction` w następujący sposób.

```xml
<PropertyGroup>
   <DockerLaunchAction>LaunchBrowser</DockerLaunchAction>
</PropertyGroup>
```

Możesz dodać ustawienie właściwości do istniejącego elementu, a jeśli go nie `PropertyGroup` ma, utwórz nowy `PropertyGroup` element.

## <a name="docker-compose-msbuild-properties"></a>Właściwości narzędzia Docker Compose w programie MSBuild

W poniższej tabeli przedstawiono właściwości programu MSBuild dostępne dla Docker Compose projektów.

| Nazwa właściwości | Lokalizacja | Opis | Wartość domyślna  |
|---------------|----------|-------------|----------------|
|AdditionalComposeFilePaths|dcproj|Określa dodatkowe pliki redagowania na liście rozdzielonych średnikami, które mają być wysyłane do docker-compose.exe dla wszystkich poleceń. Ścieżki względne z pliku projektu docker-compose (dcproj) są dozwolone.|-|
|DockerComposeBaseFilePath|dcproj|Określa pierwszą część nazw plików docker-compose bez rozszerzenia *yml.* Na przykład: <br>1. DockerComposeBaseFilePath = null/undefined: użyj ścieżki pliku podstawowego *docker-compose,* a pliki będą mieć nazwy *docker-compose.yml* i *docker-compose.override.yml.*<br>2. DockerComposeBaseFilePath = *mydockercompose*: pliki będą mieć nazwy *mydockercompose.yml* i *mydockercompose.override.yml.*<br> 3. DockerComposeBaseFilePath = *.. \mydockercompose*: pliki będą się o jeden poziom. |docker-compose|
|DockerComposeBuildArguments|dcproj|Określa dodatkowe parametry do przekazania do `docker-compose build` polecenia. Na przykład `--parallel --pull`. |
|DockerComposeDownArguments|dcproj|Określa dodatkowe parametry do przekazania do `docker-compose down` polecenia. Na przykład `--timeout 500`.|-|  
|DockerComposeProjectName| dcproj | Jeśli jest określona, zastępuje nazwę projektu docker-compose. | "dockercompose" + automatycznie generowany skrót |
|DockerComposeProjectPath|csproj lub vbproj|Ścieżka względna do pliku projektu docker-compose (dcproj). Ustaw tę właściwość podczas publikowania projektu usługi, aby znaleźć skojarzone ustawienia kompilacji obrazu przechowywane w pliku docker-compose.yml.|-|
|DockerComposeProjectsToIgnore|dcproj| Określa projekty, które mają być ignorowane przez narzędzia docker-compose podczas debugowania. Tej właściwości można używać dla dowolnego projektu. Ścieżki plików można określić na jeden z dwóch sposobów: <br> 1. Względem dcproj. Na przykład `<DockerComposeProjectsToIgnore>path\to\AngularProject1.csproj</DockerComposeProjectsToIgnore>`. <br> 2. Ścieżki bezwzględne.<br> **Uwaga:** ścieżki powinny być oddzielone znakiem ogranicznika `;` .|-|
|DockerComposeUpArguments|dcproj|Określa dodatkowe parametry do przekazania do `docker-compose up` polecenia. Na przykład `--timeout 500`.|-|
|DockerDevelopmentMode| dcproj | Określa, czy projekt użytkownika jest wbudowany w kontener. Dozwolone wartości szybkiej  lub **regularnej kontrolki,** [które etapy są budowyw](https://aka.ms/containerfastmode) pliku Dockerfile. Konfiguracja debugowania jest domyślnie trybem szybkim, a w przeciwnym razie trybem regularnym. | Duża |
|DockerLaunchAction| dcproj | Określa akcję uruchamiania do wykonania na klawiszach F5 lub Ctrl+F5.  Dozwolone wartości to None, LaunchBrowser i LaunchWCFTestClient. | Brak |
|DockerLaunchBrowser| dcproj | Wskazuje, czy uruchomić przeglądarkę. Ignorowane, jeśli określono dockerLaunchAction. | Fałsz |
|DockerServiceName| dcproj| Jeśli określono parametr DockerLaunchAction lub DockerLaunchBrowser, parametr DockerServiceName określa, która usługa, do której odwołuje się plik docker-compose, zostanie uruchomiona.|-|
|DockerServiceUrl| dcproj | Adres URL do użycia podczas uruchamiania przeglądarki.  Prawidłowe tokeny zastępcze to "{ServiceIPAddress}", "{ServicePort}" i "{Scheme}".  Na przykład: {Scheme}://{ServiceIPAddress}:{ServicePort}|-|
|DockerTargetOS| dcproj | Docelowy system operacyjny używany podczas budowania obrazu platformy Docker.|-|

## <a name="example"></a>Przykład

Jeśli zmienisz lokalizację plików docker compose, ustawiając ścieżkę względną, musisz również upewnić się, że kontekst kompilacji został zmieniony, aby odwołań do folderu `DockerComposeBaseFilePath` rozwiązania. Jeśli na przykład plik docker compose jest folderem o nazwie *DockerComposeFiles, wówczas* plik docker compose powinien ustawić kontekst kompilacji na ".." lub ".. /..", w zależności od tego, gdzie jest względna względem folderu rozwiązania.

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

Plik *mydockercompose.yml* powinien wyglądać tak, a kontekst kompilacji powinien być ustawiony na ścieżkę względną folderu rozwiązania (w tym przypadku `..` ).

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
> DockerComposeBuildArguments, DockerComposeDownArguments i DockerComposeUpArguments są nowościami w wersji 16.3 programu Visual Studio 2019.

## <a name="overriding-visual-studios-docker-compose-configuration"></a>Zastępowanie Visual Studio konfiguracji Docker Compose serwera

Niektóre ustawienia można zastąpić, umieszczając plik o nazwie *docker-compose.vs.debug.yml* (dla trybu szybkiego) lub *docker-compose.vs.release.yml* (dla trybu regularnego) w tym samym katalogu co plik   *docker-compose.yml.* 

>[!TIP] 
>Aby znaleźć wartości domyślne dla dowolnego z tych ustawień, poszukaj w pliku *docker-compose.vs.debug.g.yml* lub *docker-compose.vs.release.g.yml.*

### <a name="docker-compose-file-labels"></a>Docker Compose etykiety plików

 W *pliku docker-compose.vs.debug.yml* lub *docker-compose.vs.release.yml* można zdefiniować etykiety specyficzne dla przesłonięcia w następujący sposób:

```yml
services:
  webapplication1:
    labels:
      com.microsoft.visualstudio.debuggee.workingdirectory: "C:\\my_app_folder"
```

Użyj podwójnego cudzysłowu wokół wartości, jak w poprzednim przykładzie, i użyj ukośnika odwrotnego jako znaku ucieczki dla ukośników odwrotnych w ścieżkach.

|Nazwa etykiety|Opis|
|----------|-----------|
|com.microsoft.visualstudio.debuggee.arguments|Argumenty przekazane do programu podczas uruchamiania debugowania. W przypadku aplikacji .NET Core te argumenty są zazwyczaj dodatkowymi ścieżkami wyszukiwania dla pakietów NuGet, po których następuje ścieżka do zestawu wyjściowego projektu.|
|com.microsoft.visualstudio.debuggee.program|Program został uruchomiony podczas uruchamiania debugowania. W przypadku aplikacji .NET Core to ustawienie jest zwykle **dotnet**.|
|com.microsoft.visualstudio.debuggee.workingdirectory|Katalog używany jako katalog początkowy podczas uruchamiania debugowania. To ustawienie to zazwyczaj */app dla* kontenerów systemu Linux lub *C:\app dla* kontenerów systemu Windows.|
|com.microsoft.visualstudio.debuggee.killprogram|To polecenie służy do zatrzymania programu debugowania, który jest uruchomiony wewnątrz kontenera (w razie potrzeby).|

### <a name="customize-the-docker-build-process"></a>Dostosowywanie procesu kompilacji platformy Docker

Możesz zadeklarować etap kompilacji w pliku Dockerfile przy `target` użyciu ustawienia we właściwości `build` . To przesłonięcie może być używane tylko w pliku *docker-compose.vs.debug.yml* lub *docker-compose.vs.release.yml* 

```yml
services:
  webapplication1:
    build:
      target: customStage
    labels:
      ...
```

### <a name="customize-the-app-startup-process"></a>Dostosowywanie procesu uruchamiania aplikacji

Przed uruchomieniem aplikacji przy użyciu ustawienia możesz uruchomić polecenie lub skrypt niestandardowy, co będzie zależne `entrypoint` od właściwości `DockerDevelopmentMode` . Jeśli na przykład chcesz skonfigurować certyfikat tylko  w trybie szybkim, uruchamiając polecenie , ale nie w trybie regularnym, możesz dodać następujący kod tylko w pliku `update-ca-certificates`  *docker-compose.vs.debug.yml:* 

```yml
services:
  webapplication1:
    entrypoint: "sh -c 'update-ca-certificates && tail -f /dev/null'"
    labels:
      ...
```

## <a name="next-steps"></a>Następne kroki

Aby uzyskać ogólne informacje na temat właściwości programu MSBuild, [zobacz Właściwości programu MSBuild.](../msbuild/msbuild-properties.md)

## <a name="see-also"></a>Zobacz też

[Właściwości kompilacji narzędzi kontenera](container-msbuild-properties.md)

[Ustawienia uruchamiania narzędzi kontenerów](container-launch-settings.md)

[Zarezerwowane i dobrze znane właściwości programu MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)

---
title: Docker Compose ustawienia kompilacji
author: ghogen
description: Przegląd procesu kompilacji narzędzi kontenera
ms.author: ghogen
ms.date: 08/12/2019
ms.technology: vs-azure
ms.topic: reference
ms.openlocfilehash: deed01e2aa719df7ffeb038f022ef9d6d4b8cc71
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2020
ms.locfileid: "89741854"
---
# <a name="docker-compose-build-properties"></a>Docker Compose właściwości kompilacji

Oprócz właściwości kontrolujących poszczególne projekty platformy Docker, opisanych we [właściwościach kompilacji narzędzi kontenera](container-msbuild-properties.md), można również dostosować sposób, w jaki program Visual Studio kompiluje projekty Docker Compose przez ustawienie właściwości Docker Compose używanych przez MSBuild do kompilowania rozwiązania. Możesz również kontrolować sposób, w jaki debuger programu Visual Studio uruchamia Docker Compose aplikacje przez ustawienie etykiet plików w Docker Compose pliki konfiguracji.

## <a name="how-to-set-the-msbuild-properties"></a>Jak ustawić właściwości programu MSBuild

Aby ustawić wartość właściwości, edytuj plik projektu. W przypadku właściwości Docker Compose ten plik projektu jest jednym z rozszerzeniem. dcproj, o ile nie wskazano inaczej w tabeli w następnej sekcji. Załóżmy na przykład, że chcesz określić uruchamianie przeglądarki po rozpoczęciu debugowania. `DockerLaunchAction`Właściwość w pliku projektu. dcproj można ustawić w następujący sposób.

```xml
<PropertyGroup>
   <DockerLaunchAction>LaunchBrowser</DockerLaunchAction>
</PropertyGroup>
```

Możesz dodać ustawienie właściwości do istniejącego `PropertyGroup` elementu lub jeśli nie istnieje, Utwórz nowy `PropertyGroup` element.

## <a name="docker-compose-msbuild-properties"></a>Właściwości narzędzia Docker Compose w programie MSBuild

W poniższej tabeli przedstawiono właściwości programu MSBuild dostępne dla projektów Docker Compose.

| Nazwa właściwości | Lokalizacja | Opis | Wartość domyślna  |
|---------------|----------|-------------|----------------|
|AdditionalComposeFilePaths|dcproj|Określa dodatkowe pliki redagowania na liście rozdzielanej średnikami do wysłania do docker-compose.exe dla wszystkich poleceń. Ścieżki względne z pliku projektu platformy Docker (dcproj) są dozwolone.|-|
|DockerComposeBaseFilePath|dcproj|Określa pierwszą część nazw plików w plikach do redagowania platformy Docker bez rozszerzenia *. yml* . Na przykład: <br>1. DockerComposeBaseFilePath = null/undefined: Użyj podstawowej ścieżki pliku *Docker-Zredaguj*, a pliki będą nazwane *Docker-Compose. yml* i *Docker-Compose. override. yml*<br>2. DockerComposeBaseFilePath = *mydockercompose*: pliki będą nazwane *mydockercompose. yml* i *mydockercompose. override. yml*<br> 3. DockerComposeBaseFilePath = *.. \mydockercompose*: pliki będą mieć jeden poziom. |Docker-Compose|
|DockerComposeBuildArguments|dcproj|Określa dodatkowe parametry, które mają zostać przekazane do `docker-compose build` polecenia. Na przykład `--parallel --pull` |
|DockerComposeDownArguments|dcproj|Określa dodatkowe parametry, które mają zostać przekazane do `docker-compose down` polecenia. Na przykład `--timeout 500`|-|  
|DockerComposeProjectPath|CSPROJ lub vbproj|Ścieżka względna do pliku platformy Docker-redagowanie projektu (dcproj). Ustaw tę właściwość podczas publikowania projektu usługi, aby znaleźć skojarzone ustawienia kompilacji obrazu przechowywane w pliku Docker-Compose. yml.|-|
|DockerComposeUpArguments|dcproj|Określa dodatkowe parametry, które mają zostać przekazane do `docker-compose up` polecenia. Na przykład `--timeout 500`|-|
|DockerDevelopmentMode|dcproj| Kontroluje, czy jest włączona optymalizacja "Kompiluj-on-host" (debugowanie w trybie szybkim).  Dozwolone wartości są **szybkie** i **regularne**. | Duża |
|DockerLaunchAction| dcproj | Określa akcję uruchamiania do wykonania na F5 lub CTRL + F5.  Dozwolone wartości to None, LaunchBrowser i LaunchWCFTestClient|Brak|
|DockerLaunchBrowser| dcproj | Wskazuje, czy ma zostać uruchomiona przeglądarka. Ignorowany, jeśli określono DockerLaunchAction. | Fałsz |
|DockerServiceName| dcproj|Jeśli określono DockerLaunchAction lub DockerLaunchBrowser, DockerServiceName jest nazwą usługi, która powinna zostać uruchomiona.  Użyj tej właściwości, aby określić, który z potencjalnie wielu projektów, do których może się odwoływać plik platformy Docker, zostanie uruchomiony.|-|
|DockerServiceUrl| dcproj | Adres URL, który ma być używany podczas uruchamiania przeglądarki.  Prawidłowe tokeny zastępcze to "{serviceipaddress}", "{serviceport}" i "{Schema}".  Na przykład: {Schema}://{ServiceIPAddress}: {serviceport}|-|
|DockerTargetOS| dcproj | Docelowy system operacyjny używany podczas kompilowania obrazu platformy Docker.|-|

## <a name="example"></a>Przykład

Jeśli zmienisz lokalizację plików redagowania platformy Docker, ustawiając `DockerComposeBaseFilePath` ścieżkę względną, należy również upewnić się, że kontekst kompilacji został zmieniony tak, aby odwoływał się do folderu rozwiązania. Na przykład, jeśli plik redagowania platformy Docker jest folderem o nazwie *DockerComposeFiles*, plik do redagowania platformy Docker powinien ustawić kontekst kompilacji na ".." lub ".. w zależności od tego, gdzie jest względem folderu rozwiązania.

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

Plik *mydockercompose. yml* powinien wyglądać następująco, a kontekst kompilacji ustawił ścieżkę względną folderu rozwiązania (w tym przypadku `..` ).

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
> DockerComposeBuildArguments, DockerComposeDownArguments i DockerComposeUpArguments są nowe w programie Visual Studio 2019 w wersji 16,3.

## <a name="docker-compose-file-labels"></a>Docker Compose etykiety plików

Niektóre ustawienia można również przesłonić, umieszczając plik o nazwie *Docker-Compose. vs. Debug. yml* (dla konfiguracji **debugowania** ) lub *Docker-Compose. vs. release. yml* (dla konfiguracji **wydania** ) w tym samym katalogu, w którym znajduje się plik *Docker-Compose. yml* .  W tym pliku można określić następujące ustawienia:

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

## <a name="customize-the-app-startup-process"></a>Dostosowywanie procesu uruchamiania aplikacji

Można uruchomić polecenie lub skrypt niestandardowy przed uruchomieniem aplikacji przy użyciu `entrypoint` Ustawienia i uzależnić się od konfiguracji. Na przykład, jeśli trzeba skonfigurować certyfikat tylko w trybie **debugowania** przez uruchomienie `update-ca-certificates` , ale nie w trybie **wydania** , można dodać następujący kod tylko w *Docker-Compose. vs. Debug. yml*:

```yml
services:
  webapplication1:
    entrypoint: "sh -c 'update-ca-certificates && tail -f /dev/null'"
    labels:
      ...
```

Jeśli pominięto *Docker-Compose. vs. release. yml* lub *Docker-Compose. vs. Debug. yml* , program Visual Studio generuje je na podstawie ustawień domyślnych.

## <a name="next-steps"></a>Następne kroki

Aby uzyskać ogólne informacje na temat właściwości programu MSBuild, zobacz [Właściwości programu MSBuild](../msbuild/msbuild-properties.md).

## <a name="see-also"></a>Zobacz także

[Właściwości kompilacji narzędzi kontenera](container-msbuild-properties.md)

[Ustawienia uruchamiania narzędzi kontenera](container-launch-settings.md)

[Zarezerwowane i dobrze znane właściwości programu MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)

---
title: Właściwości kompilacji narzędzi kontenera programu Visual Studio
author: ghogen
description: Przegląd procesu kompilacji narzędzi kontenera
ms.author: ghogen
ms.date: 06/06/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 1b23d918621d79756fd77a1dd9b98009b2769ed3
ms.sourcegitcommit: 596f92fcc84e6f4494178863a66aed85afe0bb08
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2020
ms.locfileid: "82189494"
---
# <a name="container-tools-build-properties"></a>Właściwości kompilacji narzędzi kontenera

Możesz dostosować sposób, w jaki program Visual Studio kompiluje projekty kontenerów przez ustawienie właściwości używanych przez MSBuild do kompilowania projektu. Na przykład można zmienić nazwę pliku dockerfile, określić Tagi i etykiety dla obrazów, podać dodatkowe argumenty przekazane do poleceń platformy Docker i kontrolować, czy program Visual Studio wykonuje pewne optymalizacje wydajności, takie jak Kompilowanie poza środowiskiem kontenera. Możesz również ustawić właściwości debugowania, takie jak nazwa pliku wykonywalnego do uruchomienia, i argumenty wiersza polecenia do dostarczenia.

Aby ustawić wartość właściwości, edytuj plik projektu. Załóżmy na przykład, że pliku dockerfile ma nazwę *MyDockerfile*. `DockerfileFile` Właściwość w pliku projektu można ustawić w następujący sposób.

```xml
<PropertyGroup>
   <DockerfileFile>MyDockerfile</DockerfileFile>
</PropertyGroup>
```

Możesz dodać ustawienie właściwości do istniejącego `PropertyGroup` elementu lub jeśli nie istnieje, Utwórz nowy `PropertyGroup` element.

W poniższej tabeli przedstawiono właściwości programu MSBuild dostępne dla projektów kontenerów. Wersja pakietu NuGet ma zastosowanie do [Microsoft. VisualStudio. Azure. Containers. Tools. targets](https://www.nuget.org/packages/Microsoft.VisualStudio.Azure.Containers.Tools.Targets/).

| Nazwa właściwości | Opis | Wartość domyślna  | Wersja pakietu NuGet|
|---------------|-------------|----------------|----------------------|
| ContainerDevelopmentMode | Kontroluje, czy jest włączona optymalizacja "Kompiluj-on-host" (debugowanie w trybie szybkim).  Dozwolone wartości są **szybkie** i **regularne**. | Fast |1.0.1872750 lub nowszy|
| ContainerVsDbgPath | Ścieżka debugera VSDBG. | `%USERPROFILE%\vsdbg\vs2017u5` |1.0.1985401 lub nowszy|
| DockerDebuggeeArguments | Podczas debugowania, w debugerze jest nadawane przekazanie tych argumentów do uruchomionego pliku wykonywalnego. | Nie dotyczy projektów ASP.NET .NET Framework |1.7.8 lub nowszy|
| DockerDebuggeeProgram | Podczas debugowania jest nakazuje debugerowi uruchomienie tego pliku wykonywalnego. | W przypadku projektów platformy .NET Core: dotnet, ASP.NET .NET Framework projekty: nie dotyczy (program IIS jest zawsze używany) |1.7.8 lub nowszy|
| DockerDebuggeeKillProgram | To polecenie służy do kasowania uruchomionego procesu w kontenerze. | Nie dotyczy projektów ASP.NET .NET Framework |1.7.8 lub nowszy|
| DockerDebuggeeWorkingDirectory | Podczas debugowania, w debugerze jest nakazuje użycie tej ścieżki jako katalogu roboczego. | C:\app (Windows) lub/App (Linux) |1.7.8 lub nowszy|
| DockerDefaultTargetOS | Domyślny docelowy system operacyjny używany podczas kompilowania obrazu platformy Docker. | Ustawione przez program Visual Studio. |1.0.1985401 lub nowszy|
| DockerImageLabels | Domyślny zestaw etykiet stosowany do obrazu platformy Docker. | com. Microsoft. Created-by = Visual-Studio; com. Microsoft. Visual-Studio. Project-Name = $ (MSBuildProjectName) |1.5.4 lub nowszy|
| DockerFastModeProjectMountDirectory|W **trybie szybkim**ta właściwość kontroluje, gdzie katalog wyjściowy projektu jest instalowany woluminowo w działającym kontenerze.|C:\app (Windows) lub/App (Linux)|1.9.2 lub nowszy|
| DockerfileBuildArguments | Dodatkowe argumenty przekazane do polecenia [Docker Build](https://docs.docker.com/engine/reference/commandline/build/) . | Nie dotyczy. |1.0.1872750 lub nowszy|
| DockerfileContext | Domyślny kontekst używany podczas kompilowania obrazu platformy Docker jako ścieżki względnej do pliku dockerfile. | Ustawione przez program Visual Studio. |1.0.1872750 lub nowszy|
| DockerfileFastModeStage | Etap pliku dockerfile (czyli element docelowy), który ma być używany podczas kompilowania obrazu w trybie debugowania. | Pierwszy etap znaleziono w pliku dockerfile (podstawowy) |
| DockerfileFile | Opisuje domyślny pliku dockerfile, który będzie używany do kompilowania/uruchamiania kontenera dla projektu. Może to być również ścieżka. | Pliku dockerfile |1.0.1872750 lub nowszy|
| DockerfileRunArguments | Dodatkowe argumenty przekazane do polecenia [Docker Run](https://docs.docker.com/engine/reference/commandline/run/) . | Nie dotyczy. |1.0.1872750 lub nowszy|
| DockerfileRunEnvironmentFiles | Rozdzielana średnikami lista plików środowiska zastosowanych podczas uruchamiania platformy Docker. | Nie dotyczy. |1.0.1872750 lub nowszy|
| DockerfileTag | Tag, który będzie używany podczas kompilowania obrazu platformy Docker. W debugowaniu ":d EV" jest dołączany do znacznika. | Nazwa zestawu po usunięciu znaków innych niż alfanumeryczne z następującymi regułami: <br/> Jeśli wynikowy tag to wszystkie wartości liczbowe, a następnie "Image" jest wstawiany jako prefiks (na przykład image2314) <br/> Jeśli wynikowy tag jest ciągiem pustym, oznacza to, że jako tag użyto elementu "Image". |1.0.1872750 lub nowszy|

## <a name="example"></a>Przykład

W poniższym pliku projektu przedstawiono przykłady niektórych z tych ustawień.

```xml
 <Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
    <UserSecretsId>feae72bf-2368-4487-b6c6-546c19338cb1</UserSecretsId>
    <DockerDefaultTargetOS>Linux</DockerDefaultTargetOS>
    <!-- In CI/CD scenarios, you might need to change the context. By default, Visual Studio uses the
         folder above the Dockerfile. The path is relative to the Dockerfile, so here the context is
         set to the same folder as the Dockerfile. -->
    <DockerfileContext>.</DockerfileContext>
    <!-- Set `docker run` arguments to mount a volume -->
    <DockerfileRunArguments>-v $(pwd)/host-folder:/container-folder:ro</DockerfileRunArguments>
    <!-- Set `docker build` arguments to add a custom tag -->
    <DockerfileBuildArguments>-t contoso/front-end:v2.0</DockerfileBuildArguments>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.VisualStudio.Azure.Containers.Tools.Targets" Version="1.10.6" />
  </ItemGroup>

</Project>
```

## <a name="next-steps"></a>Następne kroki

Aby uzyskać ogólne informacje na temat właściwości programu MSBuild, zobacz [Właściwości programu MSBuild](../msbuild/msbuild-properties.md).

## <a name="see-also"></a>Zobacz także

[Docker Compose właściwości kompilacji](docker-compose-properties.md)

[Ustawienia uruchamiania narzędzi kontenera](container-launch-settings.md)

[Właściwości zarezerwowane i dobrze znane dla programu MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)

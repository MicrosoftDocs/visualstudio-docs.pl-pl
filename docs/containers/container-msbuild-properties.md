---
title: Właściwości kompilacji narzędzi kontenerowych programu Visual Studio
author: ghogen
description: Omówienie procesu kompilacji narzędzi kontenerowych
ms.author: ghogen
ms.date: 06/06/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 987d358abcccadf36d15593722ff55ba4b879d03
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "71950698"
---
# <a name="container-tools-build-properties"></a>Właściwości kompilacji narzędzi kontenerowych

Można dostosować jak Visual Studio tworzy projekty kontenerów, ustawiając właściwości, które MSBuild używa do tworzenia projektu. Na przykład można zmienić nazwę pliku Dockerfile, określić znaczniki i etykiety obrazów, podać dodatkowe argumenty przekazywane do poleceń platformy Docker i kontrolować, czy program Visual Studio wykonuje pewne optymalizacje wydajności, takie jak tworzenie poza środowiska kontenerowego. Można również ustawić właściwości debugowania, takie jak nazwa pliku wykonywalnego do uruchomienia i argumenty wiersza polecenia, aby zapewnić.

Aby ustawić wartość właściwości, edytuj plik projektu. Załóżmy na przykład, że plik dockerfile nosi nazwę *MyDockerfile*. Właściwość w `DockerfileFile` pliku projektu można ustawić w następujący sposób.

```xml
<PropertyGroup>
   <DockerfileFile>MyDockerfile</DockerfileFile>
</PropertyGroup>
```

Można dodać ustawienie właściwości do `PropertyGroup` istniejącego elementu lub jeśli go nie `PropertyGroup` ma, utwórz nowy element.

W poniższej tabeli przedstawiono właściwości MSBuild dostępne dla projektów kontenerów. Wersja pakietu NuGet ma zastosowanie do [witryny Microsoft.VisualStudio.Azure.Containers.Tools.Targets](https://www.nuget.org/packages/Microsoft.VisualStudio.Azure.Containers.Tools.Targets/).

| Nazwa właściwości | Opis | Wartość domyślna  | Wersja pakietu NuGet|
|---------------|-------------|----------------|----------------------|
| Tryb rozwoju kontenera | Określa, czy "build-on-host" optymalizacji ("Fast Mode" debugowania) jest włączona.  Dozwolone wartości są **szybkie** i **regularne**. | Szybko |1.0.1872750 lub nowsza|
| ContainerVsDbgPath | Ścieżka do debugera VSDBG. | `%USERPROFILE%\vsdbg\vs2017u5` |1.0.1985401 lub nowsza|
| DockerDebuggeeArgument (DockerDebuggeeArgument) | Podczas debugowania debuger jest instruowany, aby przekazać te argumenty do uruchomionego pliku wykonywalnego. | Nie dotyczy projektów ASP.NET .NET Framework |1.7.8 lub nowsze|
| Program DockerDebuggee | Podczas debugowania debuger jest instruowany, aby uruchomić ten plik wykonywalny. | W przypadku projektów .NET Core: dotnet, ASP.NET .NET Framework projects: Not applicable (IIS jest zawsze używany) |1.7.8 lub nowsze|
| Program DockerDebuggeeKill | To polecenie służy do zabicia uruchomionego procesu w kontenerze. | Nie dotyczy projektów ASP.NET .NET Framework |1.7.8 lub nowsze|
| DockerDebuggeePracaKataloga | Podczas debugowania debuger jest instruowany, aby użyć tej ścieżki jako katalogu roboczego. | C:\app (Windows) lub /app (Linux) |1.7.8 lub nowsze|
| DockerDefaultTargetOS | Domyślny docelowy system operacyjny używany podczas tworzenia obrazu platformy Docker. | Zestaw przez program Visual Studio. |1.0.1985401 lub nowsza|
| DockerImageLabels (DockerImageLabels) | Domyślny zestaw etykiet zastosowanych do obrazu platformy Docker. | com.microsoft.created-by=visual-studio;com.microsoft.visual-studio.project-name=$(MSBuildProjectName) |1.5.4 lub nowszy|
| DockerFastModeProjectMountDirectory|W **trybie szybkiego**ta właściwość określa, gdzie katalog wyjściowy projektu jest montowany na woluminie w uruchomionym kontenerze.|C:\app (Windows) lub /app (Linux)|1.9.2 lub nowsze|
| DockerfileBuildArguments (DockerfileBuildArguments) | Dodatkowe argumenty przekazywane do polecenia kompilacji platformy Docker. | Nie dotyczy. |1.0.1872750 lub nowsza|
| DockerfileContext (DockerfileContext) | Domyślny kontekst używany podczas tworzenia obrazu platformy Docker. | Zestaw przez program Visual Studio. |1.0.1872750 lub nowsza|
| DockerfileFastModeStage (DockerfileFastModeStage) | Etap Dockerfile (czyli cel) ma być używany podczas tworzenia obrazu w trybie debugowania. | Pierwszy etap znaleziony w pliku dockerfile (baza) |
| Plik dockerfile | W tym artykule opisano domyślny plik dockerfile, który będzie używany do tworzenia/uruchamiania kontenera dla projektu. Może to być również ścieżka. | Plik dockerfile |1.0.1872750 lub nowsza|
| DockerfileRunArgument (DockerfileRunArgument) | Dodatkowe argumenty przekazywane do polecenia uruchamiania platformy Docker. | Nie dotyczy. |1.0.1872750 lub nowsza|
| DockerfileRunEnvironmentFiles | Lista plików środowiska rozdzielanych średnikami zastosowana podczas uruchamiania platformy Docker. | Nie dotyczy. |1.0.1872750 lub nowsza|
| Tag dockerfileTag | Tag, który będzie używany podczas tworzenia obrazu platformy Docker. Podczas debugowania do tagu dołączany jest znak ":dev". | Nazwa zestawu po usunięciu znaków niealnumerycznych z następującymi regułami: <br/> Jeśli wynikowy znacznik jest cały numeryczny, to "obraz" jest wstawiany jako prefiks (na przykład image2314) <br/> Jeśli wynikowy znacznik jest pustym ciągiem, jako znacznika jest używany "image". |1.0.1872750 lub nowsza|

## <a name="next-steps"></a>Następne kroki

Aby uzyskać informacje na temat właściwości MSBuild ogólnie, zobacz [MSBuild Właściwości](../msbuild/msbuild-properties.md).

## <a name="see-also"></a>Zobacz też

[Właściwości kompilacji docker compose](docker-compose-properties.md)

[Ustawienia uruchamiania narzędzi kontenerowych](container-launch-settings.md)

[MSBuild zastrzeżone i dobrze znane właściwości](../msbuild/msbuild-reserved-and-well-known-properties.md)

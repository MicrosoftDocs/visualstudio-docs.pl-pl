---
title: Właściwości kompilacji narzędzi kontenera programu Visual Studio
author: ghogen
description: Przegląd procesu kompilacji narzędzi kontenera
ms.author: ghogen
ms.date: 06/06/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 987d358abcccadf36d15593722ff55ba4b879d03
ms.sourcegitcommit: 6ae0a289f1654dec63b412bfa22035511a2ef5ad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71950698"
---
# <a name="container-tools-build-properties"></a>Właściwości kompilacji narzędzi kontenera

Możesz dostosować sposób, w jaki program Visual Studio kompiluje projekty kontenerów przez ustawienie właściwości używanych przez MSBuild do kompilowania projektu. Na przykład można zmienić nazwę pliku dockerfile, określić Tagi i etykiety dla obrazów, podać dodatkowe argumenty przekazane do poleceń platformy Docker i kontrolować, czy program Visual Studio wykonuje pewne optymalizacje wydajności, takie jak Kompilowanie poza środowisko kontenera. Możesz również ustawić właściwości debugowania, takie jak nazwa pliku wykonywalnego do uruchomienia, i argumenty wiersza polecenia do dostarczenia.

Aby ustawić wartość właściwości, edytuj plik projektu. Załóżmy na przykład, że pliku dockerfile ma nazwę *MyDockerfile*. Właściwość `DockerfileFile` w pliku projektu można ustawić w następujący sposób.

```xml
<PropertyGroup>
   <DockerfileFile>MyDockerfile</DockerfileFile>
</PropertyGroup>
```

Możesz dodać ustawienie właściwości do istniejącego elementu `PropertyGroup` lub jeśli nie istnieje, Utwórz nowy element `PropertyGroup`.

W poniższej tabeli przedstawiono właściwości programu MSBuild dostępne dla projektów kontenerów. Wersja pakietu NuGet ma zastosowanie do [Microsoft. VisualStudio. Azure. Containers. Tools. targets](https://www.nuget.org/packages/Microsoft.VisualStudio.Azure.Containers.Tools.Targets/).

| Nazwa właściwości | Opis | Wartość domyślna  | Wersja pakietu NuGet|
|---------------|-------------|----------------|----------------------|
| ContainerDevelopmentMode | Kontroluje, czy jest włączona optymalizacja "Kompiluj-on-host" (debugowanie w trybie szybkim).  Dozwolone wartości są **szybkie** i **regularne**. | Fast |1.0.1872750 lub nowszy|
| ContainerVsDbgPath | Ścieżka debugera VSDBG. | `%USERPROFILE%\vsdbg\vs2017u5` |1.0.1985401 lub nowszy|
| DockerDebuggeeArguments | Podczas debugowania, w debugerze jest nadawane przekazanie tych argumentów do uruchomionego pliku wykonywalnego. | Nie dotyczy projektów ASP.NET .NET Framework |1.7.8 lub nowszy|
| DockerDebuggeeProgram | Podczas debugowania jest nakazuje debugerowi uruchomienie tego pliku wykonywalnego. | W przypadku projektów platformy .NET Core: dotnet, ASP.NET .NET Framework projekty: Nie dotyczy (program IIS jest zawsze używany) |1.7.8 lub nowszy|
| DockerDebuggeeKillProgram | To polecenie służy do kasowania uruchomionego procesu w kontenerze. | Nie dotyczy projektów ASP.NET .NET Framework |1.7.8 lub nowszy|
| DockerDebuggeeWorkingDirectory | Podczas debugowania, w debugerze jest nakazuje użycie tej ścieżki jako katalogu roboczego. | C:\app (Windows) lub/App (Linux) |1.7.8 lub nowszy|
| DockerDefaultTargetOS | Domyślny docelowy system operacyjny używany podczas kompilowania obrazu platformy Docker. | Ustawione przez program Visual Studio. |1.0.1985401 lub nowszy|
| DockerImageLabels | Domyślny zestaw etykiet stosowany do obrazu platformy Docker. | com.microsoft.created-by=visual-studio;com.microsoft.visual-studio.project-name=$(MSBuildProjectName) |1.5.4 lub nowszy|
| DockerFastModeProjectMountDirectory|W **trybie szybkim**ta właściwość kontroluje, gdzie katalog wyjściowy projektu jest instalowany woluminowo w działającym kontenerze.|C:\app (Windows) lub/App (Linux)|1.9.2 lub nowszy|
| DockerfileBuildArguments | Dodatkowe argumenty przekazane do polecenia Docker Build. | Nie dotyczy. |1.0.1872750 lub nowszy|
| DockerfileContext | Domyślny kontekst używany podczas kompilowania obrazu platformy Docker. | Ustawione przez program Visual Studio. |1.0.1872750 lub nowszy|
| DockerfileFastModeStage | Etap pliku dockerfile (czyli element docelowy), który ma być używany podczas kompilowania obrazu w trybie debugowania. | Pierwszy etap znaleziono w pliku dockerfile (podstawowy) |
| DockerfileFile | Opisuje domyślny pliku dockerfile, który będzie używany do kompilowania/uruchamiania kontenera dla projektu. Może to być również ścieżka. | Pliku dockerfile |1.0.1872750 lub nowszy|
| DockerfileRunArguments | Dodatkowe argumenty przekazane do polecenia Docker Run. | Nie dotyczy. |1.0.1872750 lub nowszy|
| DockerfileRunEnvironmentFiles | Rozdzielana średnikami lista plików środowiska zastosowanych podczas uruchamiania platformy Docker. | Nie dotyczy. |1.0.1872750 lub nowszy|
| DockerfileTag | Tag, który będzie używany podczas kompilowania obrazu platformy Docker. W debugowaniu ":d EV" jest dołączany do znacznika. | Nazwa zestawu po usunięciu znaków innych niż alfanumeryczne z następującymi regułami: <br/> Jeśli wynikowy tag to wszystkie wartości liczbowe, a następnie "Image" jest wstawiany jako prefiks (na przykład image2314) <br/> Jeśli wynikowy tag jest ciągiem pustym, oznacza to, że jako tag użyto elementu "Image". |1.0.1872750 lub nowszy|

## <a name="next-steps"></a>Następne kroki

Aby uzyskać ogólne informacje na temat właściwości programu MSBuild, zobacz [Właściwości programu MSBuild](../msbuild/msbuild-properties.md).

## <a name="see-also"></a>Zobacz także

[Docker Compose właściwości kompilacji](docker-compose-properties.md)

[Ustawienia uruchamiania narzędzi kontenera](container-launch-settings.md)

[Właściwości zarezerwowane i dobrze znane dla programu MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)

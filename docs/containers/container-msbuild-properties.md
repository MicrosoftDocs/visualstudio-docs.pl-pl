---
title: Właściwości kompilacji narzędzi kontenera programu Visual Studio
author: ghogen
description: Przegląd procesu kompilacji narzędzi kontenera
ms.author: ghogen
ms.date: 06/06/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 4bc6cb4221d85bd43b98b2ac36c34c919937960b
ms.sourcegitcommit: 3cda0d58c5cf1985122b8977b33a171c7359f324
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2019
ms.locfileid: "70152532"
---
# <a name="container-tools-build-properties"></a>Właściwości kompilacji narzędzi kontenera

Możesz dostosować sposób, w jaki program Visual Studio kompiluje projekty kontenerów przez ustawienie właściwości używanych przez MSBuild do kompilowania projektu. Na przykład można zmienić nazwę pliku dockerfile, określić Tagi i etykiety dla obrazów, podać dodatkowe argumenty przekazane do poleceń platformy Docker i kontrolować, czy program Visual Studio wykonuje pewne optymalizacje wydajności, takie jak Kompilowanie poza środowisko kontenera. Możesz również ustawić właściwości debugowania, takie jak nazwa pliku wykonywalnego do uruchomienia, i argumenty wiersza polecenia do dostarczenia.

Aby ustawić wartość właściwości, edytuj plik projektu. Załóżmy na przykład, że pliku dockerfile ma nazwę *MyDockerfile*. `DockerfileFile` Właściwość w pliku projektu można ustawić w następujący sposób.

```xml
<PropertyGroup>
   <DockerfileFile>MyDockerfile</DockerfileFile>
</PropertyGroup>
```

Możesz dodać ustawienie właściwości do istniejącego `PropertyGroup` elementu lub jeśli nie istnieje, Utwórz nowy `PropertyGroup` element.

W poniższej tabeli przedstawiono właściwości programu MSBuild dostępne dla projektów kontenerów.

| Nazwa właściwości | Opis | Wartość domyślna  |
|---------------|-------------|----------------|
| DockerfileFile | Opisuje domyślny pliku dockerfile, który będzie używany do kompilowania/uruchamiania kontenera dla projektu. Może to być również ścieżka. | Pliku dockerfile |
| DockerfileTag | Tag, który będzie używany podczas kompilowania obrazu platformy Docker. W debugowaniu ":d EV" jest dołączany do znacznika. | Nazwa zestawu po usunięciu znaków innych niż alfanumeryczne z następującymi regułami: <br/> Jeśli wynikowy tag to wszystkie wartości liczbowe, a następnie "Image" jest wstawiany jako prefiks (na przykład image2314) <br/> Jeśli wynikowy tag jest ciągiem pustym, oznacza to, że jako tag użyto elementu "Image". |
| DockerContext | Domyślny kontekst używany podczas kompilowania obrazu platformy Docker. | Ustawione przez program Visual Studio. |
| ContainerDevelopmentMode | Kontroluje, czy jest włączona optymalizacja "Kompiluj-on-host" (debugowanie w trybie szybkim).  Dozwolone wartości są **szybkie** i **regularne**. | Fast |
| DockerDefaultTargetOS | Domyślny docelowy system operacyjny używany podczas kompilowania obrazu platformy Docker. | Ustawione przez program Visual Studio. |
| DockerImageLabels | Domyślny zestaw etykiet stosowany do obrazu platformy Docker. | com.microsoft.created-by=visual-studio;com.microsoft.visual-studio.project-name=$(MSBuildProjectName) |
| ContainerVsDbgPath | Ścieżka debugera VSDBG. | `%USERPROFILE%\vsdbg\vs2017u5` |
| DockerfileBuildArguments | Dodatkowe argumenty przekazane do polecenia Docker Build. | Nie dotyczy. |
| DockerfileRunArguments | Dodatkowe argumenty przekazane do polecenia Docker Run. | Nie dotyczy. |
| DockerfileRunEnvironmentFiles | Rozdzielana średnikami lista plików środowiska zastosowanych podczas uruchamiania platformy Docker. | Nie dotyczy. |
| DockerfileFastModeStage | Etap pliku dockerfile (czyli element docelowy), który ma być używany podczas kompilowania obrazu w trybie debugowania. | Pierwszy etap znaleziono w pliku dockerfile (podstawowy) |
| DockerDebuggeeProgram | Podczas debugowania jest nakazuje debugerowi uruchomienie tego pliku wykonywalnego. | W przypadku projektów platformy .NET Core: dotnet, ASP.NET .NET Framework projekty: Nie dotyczy (program IIS jest zawsze używany) |
| DockerDebuggeeArguments | Podczas debugowania, w debugerze jest nadawane przekazanie tych argumentów do uruchomionego pliku wykonywalnego. | Nie dotyczy projektów ASP.NET .NET Framework |
| DockerDebuggeeWorkingDirectory | Podczas debugowania, w debugerze jest nakazuje użycie tej ścieżki jako katalogu roboczego. | C:\app (Windows) lub/App (Linux) |
| DockerDebuggeeKillProgram | To polecenie służy do kasowania uruchomionego procesu w kontenerze. | Nie dotyczy projektów ASP.NET .NET Framework |

## <a name="next-steps"></a>Następne kroki

Aby uzyskać ogólne informacje na temat właściwości programu MSBuild, zobacz [Właściwości programu MSBuild](../msbuild/msbuild-properties.md).

## <a name="see-also"></a>Zobacz także

[Docker Compose właściwości kompilacji](docker-compose-properties.md)

[Ustawienia uruchamiania narzędzi kontenera](container-launch-settings.md)

[Właściwości zarezerwowane i dobrze znane dla programu MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)

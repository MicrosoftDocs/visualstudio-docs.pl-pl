---
title: Narzędzia kontenerów programu Visual Studio właściwości kompilacji
author: ghogen
description: Omówienie procesu kompilacji narzędzia kontenerów
ms.author: ghogen
ms.date: 06/06/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: e3ce803f13b8dde82ffe71906e5f7a43a029dbb6
ms.sourcegitcommit: 0cd282a7584b9bfd4df7882f8fdf3ad8a270e219
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2019
ms.locfileid: "67467414"
---
# <a name="container-tools-build-properties"></a>Narzędzia kontenerów właściwości kompilacji

Można dostosować, w jaki sposób program Visual Studio kompiluje projekty kontenera przez ustawienie właściwości, które korzysta z programu MSBuild do kompilowania projektu. Na przykład zmienić nazwę pliku Dockerfile, określ znaczniki i etykiety dla obrazów, należy podać dodatkowe argumenty przekazane do polecenia Docker i kontroli, czy niektóre optymalizacje wydajności, takie jak tworzenie poza program Visual Studio środowiska kontenera. Aby zapewnić, można również ustawić właściwości, takie jak nazwa pliku wykonywalnego do uruchomienia i argumenty wiersza polecenia debugowania.

Aby ustawić wartość właściwości, wyedytuj plik projektu. Załóżmy na przykład, nosi nazwę z pliku Dockerfile *MyDockerfile*. Możesz ustawić `DockerfileFile` właściwość w projekcie plików w następujący sposób.

```xml
<PropertyGroup>
   <DockerfileFile>MyDockerfile</DockerfileFile>
</PropertyGroup>
```

Ustawienie właściwości można dodać do istniejącej `PropertyGroup` elementu, lub jeśli nie istnieje, Utwórz nową `PropertyGroup` elementu.

W poniższej tabeli przedstawiono dostępne dla projektów kontenera właściwości programu MSBuild.

| Nazwa właściwości | Opis | Wartość domyślna  |
|---------------|-------------|----------------|
| DockerfileFile | W tym artykule opisano domyślne pliku Dockerfile, który będzie używany do uruchomienia kompilacji/kontenera dla projektu. Może to być także ścieżkę. | Dockerfile |
| DockerfileTag | Tag, który będzie używany podczas tworzenia obrazu platformy Docker. Podczas debugowania, ": dev" jest dołączany do tagu. | Nazwa zestawu po obcięcie znaki inne niż alfanumeryczne z następującymi regułami: <br/> W przypadku cyfr wynikowe tag "image" jest wstawiony jako prefiksu (na przykład image2314) <br/> Jeśli wynikowe znacznik jest pustym ciągiem, "image" jest używany jako znacznik. |
| DockerContext | Domyślny kontekst używany podczas tworzenia obrazu platformy Docker. | Ustaw przez program Visual Studio. |
| ContainerDevelopmentMode | Określa, czy włączono optymalizacji "kompilacji na host" (debugowanie "Szybkie tryb").  Dozwolone wartości to **Fast** i **regularne**. | Szybka |
| DockerDefaultTargetOS | Docelowy system operacyjny używany podczas tworzenia obrazu platformy Docker. | Ustaw przez program Visual Studio. |
| DockerImageLabels | Domyślny zestaw etykiety zastosowane do obrazu platformy Docker. | com.microsoft.created-by=visual-studio;com.microsoft.visual-studio.project-name=$(MSBuildProjectName) |
| ContainerVsDbgPath | Ścieżka do debugera VSDBG. | `%USERPROFILE%\vsdbg\vs2017u5` |
| DockerfileBuildArguments | Dodatkowe argumenty przekazywane do polecenia kompilacji platformy Docker. | Nie dotyczy. |
| DockerfileRunArguments | Dodatkowe argumenty przekazane do platformy Docker, uruchom polecenie. | Nie dotyczy. |
| DockerfileRunEnvironmentFiles | Rozdzielana średnikami lista plików środowiska stosowane podczas uruchamiania platformy Docker. | Nie dotyczy. |
| DockerfileFastModeStage | Etap pliku Dockerfile (oznacza to, że obiekt docelowy) do użycia podczas tworzenia obrazu w trybie debugowania. | Pierwszy etap, znaleziono w pliku Dockerfile (base) |
| DockerDebuggeeProgram | Podczas debugowania, Debuger jest zobowiązany do uruchomienia tego pliku wykonywalnego. | Dla projektów .NET Core: dotnet, projektów programu .NET Framework dla programu ASP.NET: Nie dotyczy (usługi IIS zawsze są używane) |
| DockerDebuggeeArguments | Podczas debugowania, Debuger jest zobowiązany do te argumenty przekazywane do uruchomionego pliku wykonywalnego. | Nie ma zastosowania do projektów programu .NET Framework dla programu ASP.NET |
| DockerDebuggeeWorkingDirectory | Podczas debugowania, Debuger jest zobowiązany do używania tej ścieżki, jako katalog roboczy. | C:\app (Windows) lub App (Linux) |
| DockerDebuggeeKillProgram | To polecenie jest używane do zatrzymania uruchomionego procesu w kontenerze. | Nie ma zastosowania do projektów programu .NET Framework dla programu ASP.NET |

## <a name="next-steps"></a>Następne kroki

Instrukcje dotyczące programu MSBuild ogólnie rzecz biorąc, zobacz właściwości [właściwości programu MSBuild](../msbuild/msbuild-properties.md).

## <a name="see-also"></a>Zobacz także

[Program MSBuild zarezerwowane i dobrze znane właściwości](../msbuild/msbuild-reserved-and-well-known-properties.md).

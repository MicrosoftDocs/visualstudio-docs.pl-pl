---
title: Narzędzia kontenerów programu Visual Studio kompilacji — omówienie
author: ghogen
description: Omówienie procesu kompilacji narzędzia kontenerów
ms.author: ghogen
ms.date: 06/06/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 26b9bab096c65ff987d4e7c824555544a7e38cd6
ms.sourcegitcommit: 0cd282a7584b9bfd4df7882f8fdf3ad8a270e219
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2019
ms.locfileid: "67467405"
---
# <a name="building-containerized-apps-using-visual-studio-or-the-command-line"></a>Tworzenie kontenerowych nimi aplikacji przy użyciu programu Visual Studio lub wiersza polecenia

W przypadku tworzenia z programu Visual Studio IDE, czy Konfigurowanie kompilacji wiersza polecenia, musisz wiedzieć, jak program Visual Studio tworzy używa pliku Dockerfile do tworzenia projektów.  Ze względu na wydajność programu Visual Studio, następuje specjalny proces konteneryzowanych aplikacji. Zrozumienie, w jaki sposób program Visual Studio kompiluje projekty jest szczególnie ważne w przypadku, gdy możesz dostosować proces kompilacji, modyfikując plik Dockerfile.

Gdy program Visual Studio tworzy projekt, który nie używa kontenerów platformy Docker, wywołuje MSBuild na komputerze lokalnym i generuje pliki wyjściowe w folderze (zazwyczaj `bin`) w folderze rozwiązania lokalnego. Dla projektów konteneryzowanych jednak proces kompilacji uwzględnia instrukcji pliku Dockerfile w celu skompilowania aplikacji konteneryzowanych. Plik Dockerfile, który używa programu Visual Studio jest podzielony na wiele etapów. Ten proces zależy od platformy Docker *wieloetapowych kompilacji* funkcji.

## <a name="multistage-build"></a>Wieloetapowych kompilacji

Funkcja kompilacji wieloetapowych ułatwia proces tworzenia kontenerów bardziej efektywne i sprawia, że kontenery mniejszych, umożliwiając im zawierają tylko bity, które Twoja aplikacja wymaga w czasie wykonywania.

Kompilacja wieloetapowych umożliwia obrazów kontenera do utworzenia w etapach, które tworzą pośrednich obrazów. Na przykład należy rozważyć typowy plik Dockerfile, generowane przez program Visual Studio — to pierwszy etap `base`:

```
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443
```

Wiersze w pliku Dockerfile zaczynają się od obrazu Nanoserver z rejestru kontenerów firmy Microsoft (mcr.microsoft.com) i Utwórz obraz pośrednich `base` udostępnia porty 80 i 443 i ustawia katalog roboczy `/app`.

Następny etap to `build`, która jest wyświetlana w następujący sposób:

```
FROM mcr.microsoft.com/dotnet/core/sdk:2.2-stretch AS build
WORKDIR /src
COPY ["WebApplication43/WebApplication43.csproj", "WebApplication43/"]
RUN dotnet restore "WebApplication43/WebApplication43.csproj"
COPY . .
WORKDIR "/src/WebApplication43"
RUN dotnet build "WebApplication43.csproj" -c Release -o /app
```

Możesz zobaczyć, że `build` etapu zaczyna się od innego oryginalny obraz z rejestru (`sdk` zamiast `aspnet`), zamiast kontynuowanie z podstawowego.  `sdk` Obraz ma wszystkie narzędzia do kompilacji i z tego powodu jest znacznie większa niż obraz aspnet, która zawiera tylko składników środowiska wykonawczego. Przyczyna przy użyciu osobny obraz staną się oczywiste, jeśli przyjrzymy się pozostałej części pliku Dockerfile:

```
FROM build AS publish
RUN dotnet publish "WebApplication43.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "WebApplication43.dll"]
```

Ostatnim krokiem jest uruchamiany ponownie z `base`i zawiera `COPY --from=publish` można skopiować opublikowane dane wyjściowe do finalnego obrazu. Ten proces umożliwia końcowego obraz, który ma być o wiele mniejsza, ponieważ nie trzeba uwzględniać wszystkie narzędzia do kompilacji, które były `sdk` obrazu.

## <a name="faster-builds-for-the-debug-configuration"></a>Szybsze kompilowanie dla konfiguracji debugowania

Ze względu na wydajność procesu kompilacji dla konteneryzowanych aplikacji nie jest tak proste jak po prostu wykonując kroki opisane w pliku Dockerfile. Tworzenie w kontenerze jest znacznie wolniejsze niż opierając się na komputerze lokalnym.  Dlatego podczas kompilowania **debugowania** konfiguracji programu Visual Studio rzeczywiście kompiluje projekty na komputerze lokalnym, a następnie udostępnia folder dane wyjściowe do kontenera przy użyciu zamontowania woluminu. Nosi nazwę kompilacji z użyciem tego rodzaju optymalizacji, włączone *Fast* tryb kompilacji.

W **Fast** tryb, wywołań programu Visual Studio `docker build` z nieprawidłowym argumentem platformy docker do tworzenia tylko `base` etapu.  Visual Studio obsługuje resztą procesu bez względu na zawartość pliku Dockerfile. Tak gdy modyfikujesz z pliku Dockerfile, takie jak dostosować środowisko kontenerów lub zainstalować dodatkowe zależności w pierwszym etapie należy umieszczać modyfikacje.  Wszystkie niestandardowe kroki umieszczone w pliku Dockerfile `build`, `publish`, lub `final` etapów nie zostaną wykonane.

Tego rodzaju optymalizacji wydajności występuje tylko wtedy, gdy tworzysz **debugowania** konfiguracji. W **wersji** konfiguracji kompilacji odbywa się w kontenerze, jak określono w pliku Dockerfile.

Jeśli chcesz wyłączyć optymalizację wydajności i kompilacji jako Określa plik Dockerfile, następnie ustawić **ContainerDevelopmentMode** właściwości **regularne** w pliku projektu w następujący sposób:

```xml
<PropertyGroup>
   <ContainerDevelopmentMode>Regular</ContainerDevelopmentMode>
</PropertyGroup>
```

Aby przywrócić zoptymalizować wydajność, ustaw wartość **Fast**.

## <a name="building-from-the-command-line"></a>Tworzenie z wiersza polecenia

Możesz użyć `docker build` lub `MSBuild` do kompilacji z wiersza polecenia.

### <a name="docker-build"></a>kompilacji platformy docker

Tworzenie konteneryzowanej rozwiązania z wiersza polecenia, zazwyczaj można użyć polecenia `docker build <context>` dla każdego projektu w rozwiązaniu. Należy podać *kompilacji kontekstu* argumentu. *Kompilacji kontekstu* dla pliku Dockerfile jest folder na komputerze lokalnym, który jest używany jako folder roboczy do generowania obrazu. Na przykład jest f'older, które zostały skopiowane pliki przy kopiowaniu do kontenera.  W projektach .NET Core należy użyć folderu zawierającego plik rozwiązania (.sln).  Wyrażony w postaci ścieżki względnej, ten argument jest zazwyczaj ".." dla pliku Dockerfile w folderze projektu i plik rozwiązania w folderze nadrzędnym.  Dla projektów programu .NET Framework kontekstu kompilacji jest folder projektu, a nie w folderze rozwiązania.

> [!NOTE] 
> Dla projektów programu .NET Framework, a także dla projektów .NET Core utworzone za pomocą wersji programu Visual Studio przed Visual Studio 2017 Update 4 plik Dockerfile nie użyto wieloetapowych kompilacji. Gdy program Visual Studio tworzy się przy użyciu tych plików Dockerfile, zamiast tworzenia projektu w pliku Dockerfile i programu Visual Studio tworzy każdego projektu, a następnie kopiuje wyniki do kontenera. Ponieważ kroki kompilacji nie są zawarte w pliku Dockerfile, nie można przeprowadzić kompilacji takich projektów przy użyciu `docker build` z wiersza polecenia. Należy użyć programu MSBuild do kompilowania tych projektów.

### <a name="msbuild"></a>MSBuild

Aby skompilować projekt lub rozwiązanie dla kontenera platformy docker w jednym, można użyć programu MSBuild z `/t:ContainerBuild` opcja polecenia.

```cmd
MSBuild <solution_name>.sln /t:ContainerBuild /p:Configuration=Debug
```

Zostaną wyświetlone dane wyjściowe podobne do wyświetlania w **dane wyjściowe** okna podczas kompilowania rozwiązania z programu Visual Studio IDE.

Podczas **debugowania** określona konfiguracja (i **ContainerDevelopmentMode** właściwość jest ustawiona na **Fast**), program Visual Studio używa optymalizacji kompilacji opisane w w tym artykule, dzięki czemu projektu jest kompilowana szybciej na komputerze lokalnym i są kopiowane do kontenera.  Gdy **wersji** konfiguracji jest określony, kompilacji odbywa się w kontenerze i może być wolniejsze.

Jeśli używasz narzędzia Docker Compose projektu, należy użyć polecenia:

```
msbuild /t:DockerPackageService /p:DockerAppType=AspNet /p:Configuration=Release <project_name>\<project_name>.csproj
msbuild /p:Configuration=Release docker-compose.dcproj
```

## <a name="scripting-a-containerized-build-using-azure-devops"></a>Skrypty kompilacji konteneryzowanych za pomocą DevOps platformy Azure

Potoki usługi Azure służy do tworzenia swoich konteneryzowanych aplikacji i publikowanie w usłudze Azure Container Registry lub Docker Hub. Wykonaj instrukcje dotyczące konfigurowania potoku usługi Azure, w tym artykule: [Tworzenia, testowania i wypychanie aplikacji kontenera aparatu Docker](/azure/devops/pipelines/languages/docker?view=azure-devops). Jednak sposób wdrożyć swoje rozwiązanie, należy dodać zadanie programu MSBuild do potoku. Wewnętrznie, program MSBuild używa `docker build` do tworzenia kontenerów.

Dodaj zadanie programu MSBuild do potoku sieci w następujący sposób:

```
- task: MSBuild@1
  displayName: 'Build Application and main Docker Image'
  inputs:
    solution: '**/*.sln'
    msbuildArguments: '/t:ContainerBuild /p:Configuration=$(buildConfiguration)'
```

Aby uzyskać więcej informacji, zobacz [zadanie MSBuild](/azure/devops/pipelines/tasks/build/msbuild?view=azure-devops).

## <a name="next-steps"></a>Następne kroki

Dowiedz się, jak dostosować kompilacji przez ustawienie dodatkowych właściwości programu MSBuild w plikach projektu. Zobacz [właściwości kompilacji narzędzia kontenerów](container-msbuild-properties.md).

## <a name="see-also"></a>Zobacz także

[Program MSBuild](../msbuild/msbuild.md)
[pliku Dockerfile na Windows](/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
[kontenerów systemu Linux na Windows](/virtualization/windowscontainers/deploy-containers/linux-containers)

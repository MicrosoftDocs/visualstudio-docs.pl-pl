---
title: Omówienie kompilacji narzędzi kontenerów programu Visual Studio
author: ghogen
description: Przegląd procesu kompilacji narzędzi kontenera
ms.author: ghogen
ms.date: 06/06/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: edc4674e2468124ecb46b25a1411043ed4b66a2a
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253118"
---
# <a name="building-containerized-apps-using-visual-studio-or-the-command-line"></a>Tworzenie aplikacji kontenerowych przy użyciu programu Visual Studio lub wiersza polecenia

Niezależnie od tego, czy tworzysz z programu Visual Studio IDE, czy konfigurujesz kompilację w wierszu polecenia, musisz wiedzieć, jak kompilacja Visual Studio używa pliku dockerfile do kompilowania projektów.  Ze względu na wydajność program Visual Studio jest zgodny ze specjalnym procesem dla aplikacji kontenerowych. Zrozumienie sposobu, w jaki program Visual Studio kompiluje projekty, jest szczególnie istotny podczas dostosowywania procesu kompilacji przez zmodyfikowanie pliku dockerfile.

Gdy program Visual Studio kompiluje projekt, który nie używa kontenerów platformy Docker, wywołuje program MSBuild na maszynie lokalnej i generuje pliki wyjściowe w folderze ( `bin`zazwyczaj) w folderze rozwiązania lokalnego. Jednak w przypadku projektu kontenera proces kompilacji bierze pod uwagę instrukcje pliku dockerfile na potrzeby tworzenia kontenera aplikacji. Pliku dockerfile, które są używane przez program Visual Studio, jest podzielony na wiele etapów. Ten proces polega na funkcji *kompilacji potokach wieloetapowych* platformy Docker.

## <a name="multistage-build"></a>Kompilacja potokach wieloetapowych

Funkcja kompilacji potokach wieloetapowych ułatwia proces kompilowania kontenerów bardziej wydajnie i sprawia, że kontenery są mniejsze, dzięki czemu mogą zawierać tylko bity wymagane przez aplikację w czasie wykonywania. Kompilacja potokach wieloetapowych jest używana dla projektów .NET Core, a nie .NET Framework projektów.

Kompilacja potokach wieloetapowych umożliwia tworzenie obrazów kontenerów w etapach, które generują obrazy pośrednie. Przykładowo Rozważmy typowe pliku dockerfile wygenerowane przez program Visual Studio — pierwszy etap to `base`:

```
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443
```

Linie w pliku dockerfile zaczynają się od obrazu Nanoserver z Microsoft Container Registry (MCR.Microsoft.com) i tworzą pośredni obraz `base` , który uwidacznia porty 80 i 443, i ustawia katalog roboczy na. `/app`

Następnym etapem jest `build`, która wygląda następująco:

```
FROM mcr.microsoft.com/dotnet/core/sdk:2.2-stretch AS build
WORKDIR /src
COPY ["WebApplication43/WebApplication43.csproj", "WebApplication43/"]
RUN dotnet restore "WebApplication43/WebApplication43.csproj"
COPY . .
WORKDIR "/src/WebApplication43"
RUN dotnet build "WebApplication43.csproj" -c Release -o /app
```

Możesz zobaczyć, że `build` etap zaczyna się od innego oryginalnego obrazu z rejestru (`sdk` a nie `aspnet`), a nie z bazy.  `sdk` Obraz zawiera wszystkie narzędzia kompilacji i z tego powodu jest dużo większy niż obraz ASPNET, który zawiera tylko składniki środowiska uruchomieniowego. Przyczyna użycia oddzielnego obrazu zostanie wyczyszczona, gdy zobaczysz resztę pliku dockerfile:

```
FROM build AS publish
RUN dotnet publish "WebApplication43.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "WebApplication43.dll"]
```

Końcowy etap zostanie uruchomiony ponownie z `base`i `COPY --from=publish` zawiera kopię publikowanych danych wyjściowych do obrazu końcowego. Dzięki temu obraz końcowy może być dużo mniejszy, ponieważ nie musi zawierać wszystkich narzędzi do kompilacji, które znajdowały się w `sdk` obrazie.

## <a name="faster-builds-for-the-debug-configuration"></a>Szybsze kompilacje dla konfiguracji debugowania

Istnieje kilka optymalizacji, które program Visual Studio pomaga zwiększyć wydajność procesu kompilacji dla projektów kontenerowych. Po rozpoczęciu debugowania (F5) wcześniej skompilowany obraz jest ponownie używany, jeśli jest to możliwe. Jeśli nie chcesz ponownie używać poprzedniego kontenera, możesz użyć polecenia **Kompiluj** lub **Wyczyść** w programie Visual Studio, aby wymusić użycie przez program Visual Studio nowego kontenera.

Ponadto w celu zwiększenia wydajności proces kompilacji dla aplikacji kontenerowych nie jest tak prosty jak po kroku opisanym w pliku dockerfile. Kompilowanie w kontenerze jest znacznie wolniejsze niż kompilowanie na komputerze lokalnym.  Dlatego podczas kompilowania w konfiguracji **debugowania** program Visual Studio rzeczywiście kompiluje projekty na komputerze lokalnym, a następnie udostępnia folder wyjściowy do kontenera przy użyciu funkcji montowania woluminu. Kompilacja z włączoną opcją optymalizacji jest nazywana kompilacją trybu *szybkiego* .

W trybie **szybkim** program Visual Studio `docker build` wywołuje z argumentem, który instruuje platformę Docker, aby kompiluje tylko ten `base` etap.  Program Visual Studio obsługuje resztę procesu bez względu na zawartość pliku dockerfile. Dlatego w przypadku zmodyfikowania pliku dockerfile, na przykład w celu dostosowania środowiska kontenera lub zainstalowania dodatkowych zależności, należy wprowadzić modyfikacje w pierwszym etapie.  Wszelkie niestandardowe kroki umieszczone w pliku dockerfile `build`, `publish`, lub `final` etapy nie będą wykonywane.

Ta optymalizacja wydajności występuje tylko w przypadku kompilowania w konfiguracji **debugowania** . W konfiguracji **wydania** kompilacja odbywa się w kontenerze określonym w pliku dockerfile.

Jeśli chcesz wyłączyć optymalizację wydajności i kompilację jako pliku dockerfile, ustaw właściwość **ContainerDevelopmentMode** na **Regular** w pliku projektu w następujący sposób:

```xml
<PropertyGroup>
   <ContainerDevelopmentMode>Regular</ContainerDevelopmentMode>
</PropertyGroup>
```

Aby przywrócić optymalizację wydajności, Usuń właściwość z pliku projektu.

## <a name="building-from-the-command-line"></a>Kompilowanie z wiersza polecenia

Można użyć `docker build` lub `MSBuild` do kompilowania z wiersza polecenia.

### <a name="docker-build"></a>Kompilacja platformy Docker

Aby skompilować rozwiązanie z kontenerem z wiersza polecenia, można zwykle użyć polecenia `docker build <context>` dla każdego projektu w rozwiązaniu. Podajesz argument *kontekstu kompilacji* . *Kontekst kompilacji* dla pliku dockerfile to folder na komputerze lokalnym, który jest używany jako folder roboczy do generowania obrazu. Na przykład jest to folder, z którego kopiowane są pliki podczas kopiowania do kontenera.  W projektach .NET Core Użyj folderu zawierającego plik rozwiązania (. sln).  W postaci ścieżki względnej ten argument jest zwykle ".." dla pliku dockerfile w folderze projektu i pliku rozwiązania w folderze nadrzędnym.  W przypadku projektów .NET Framework, kontekst kompilacji jest folderem projektu, a nie folderem rozwiązania.

```cmd
docker build -f Dockerfile ..
```

### <a name="msbuild"></a>MSBuild

Wieloetapowe dockerfile utworzone przez program Visual Studio dla projektów .NET Framework (i dla projektów .NET Core utworzonych przy użyciu wersji programu Visual Studio wcześniejszych niż Visual Studio 2017 Update 4) nie są potokach wieloetapowych wieloetapowe dockerfile.  Kroki opisane w tych wieloetapowe dockerfile nie kompilują kodu.  Zamiast tego, gdy program Visual Studio kompiluje .NET Framework pliku dockerfile, najpierw kompiluje projekt przy użyciu programu MSBuild.  Gdy to się powiedzie, program Visual Studio kompiluje pliku dockerfile, który po prostu kopiuje dane wyjściowe kompilacji z programu MSBuild do wynikowego obrazu platformy Docker.  Ponieważ kroki kompilowania kodu nie są uwzględnione w pliku dockerfile, nie można skompilować .NET Framework wieloetapowe dockerfile przy użyciu `docker build` wiersza polecenia. Do kompilowania tych projektów należy używać programu MSBuild.

Aby utworzyć obraz dla pojedynczego projektu kontenera platformy Docker, można użyć programu MSBuild z `/t:ContainerBuild` opcją polecenia. Na przykład:

```cmd
MSBuild MyProject.csproj /t:ContainerBuild /p:Configuration=Release
```

Dane wyjściowe będą wyglądać podobnie jak w oknie **danych wyjściowych** podczas kompilowania rozwiązania z poziomu środowiska IDE programu Visual Studio. Zawsze używaj `/p:Configuration=Release`, ponieważ w przypadkach, gdy program Visual Studio używa optymalizacji kompilacji potokach wieloetapowych, wyniki podczas kompilowania konfiguracji **debugowania** mogą nie być zgodne z oczekiwaniami.

Jeśli używasz projektu Docker Compose, użyj polecenia, aby skompilować obrazy:

```cmd
msbuild /p:SolutionPath=<solution-name>.sln /p:Configuration=Release docker-compose.dcproj
```

## <a name="next-steps"></a>Następne kroki

Dowiedz się, jak dodatkowo dostosować kompilacje przez ustawienie dodatkowych właściwości programu MSBuild w plikach projektu. Zobacz [Właściwości programu MSBuild dla projektów kontenerów](container-msbuild-properties.md).

## <a name="see-also"></a>Zobacz także

[Program MSBuild](../msbuild/msbuild.md)
[pliku dockerfile w kontenerach systemu Windows](/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
[Linux w systemie Windows](/virtualization/windowscontainers/deploy-containers/linux-containers)

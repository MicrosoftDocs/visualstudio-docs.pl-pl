---
title: Omówienie kompilacji i debugowania narzędzi kontenera programu Visual Studio
author: ghogen
description: Przegląd procesu kompilowania i debugowania narzędzi kontenera
ms.author: ghogen
ms.date: 11/20/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 07ecc9a171cf6c0ca254ddbf284f116545ddd0f0
ms.sourcegitcommit: 20f546a0b13b56e7b0da21abab291d42a5ba5928
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2021
ms.locfileid: "104884086"
---
# <a name="how-visual-studio-builds-containerized-apps"></a>Jak program Visual Studio umożliwia tworzenie aplikacji konteneryzowanych

Niezależnie od tego, czy tworzysz z programu Visual Studio IDE, czy konfigurujesz kompilację w wierszu polecenia, musisz wiedzieć, jak program Visual Studio używa pliku dockerfile do kompilowania projektów.  Ze względu na wydajność program Visual Studio jest zgodny ze specjalnym procesem dla aplikacji kontenerowych. Zrozumienie sposobu, w jaki program Visual Studio kompiluje projekty, jest szczególnie istotny podczas dostosowywania procesu kompilacji przez zmodyfikowanie pliku dockerfile.

Gdy program Visual Studio kompiluje projekt, który nie używa kontenerów platformy Docker, wywołuje program MSBuild na maszynie lokalnej i generuje pliki wyjściowe w folderze (zazwyczaj `bin` ) w folderze rozwiązania lokalnego. Jednak w przypadku projektu kontenera proces kompilacji bierze pod uwagę instrukcje pliku dockerfile na potrzeby tworzenia kontenera aplikacji. Pliku dockerfile, które są używane przez program Visual Studio, jest podzielony na wiele etapów. Ten proces polega na funkcji *kompilacji potokach wieloetapowych* platformy Docker.

## <a name="multistage-build"></a>Kompilacja potokach wieloetapowych

Funkcja kompilacji potokach wieloetapowych ułatwia proces kompilowania kontenerów bardziej wydajnie i sprawia, że kontenery są mniejsze, dzięki czemu mogą zawierać tylko bity wymagane przez aplikację w czasie wykonywania. Kompilacja potokach wieloetapowych jest używana dla projektów .NET Core, a nie .NET Framework projektów.

Kompilacja potokach wieloetapowych umożliwia tworzenie obrazów kontenerów w etapach, które generują obrazy pośrednie. Przykładowo Rozważmy typowe pliku dockerfile wygenerowane przez program Visual Studio — pierwszy etap to `base` :

```
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443
```

Linie w pliku dockerfile zaczynają się od obrazu Debian z Microsoft Container Registry (mcr.microsoft.com) i tworzą pośredni obraz `base` , który uwidacznia porty 80 i 443, i ustawia katalog roboczy na `/app` .

Następnym etapem jest `build` , która wygląda następująco:

```
FROM mcr.microsoft.com/dotnet/core/sdk:2.2-stretch AS build
WORKDIR /src
COPY ["WebApplication43/WebApplication43.csproj", "WebApplication43/"]
RUN dotnet restore "WebApplication43/WebApplication43.csproj"
COPY . .
WORKDIR "/src/WebApplication43"
RUN dotnet build "WebApplication43.csproj" -c Release -o /app
```

Możesz zobaczyć, że `build` etap zaczyna się od innego oryginalnego obrazu z rejestru ( `sdk` a nie `aspnet` ), a nie z bazy.  `sdk`Obraz zawiera wszystkie narzędzia kompilacji i z tego powodu jest dużo większy niż obraz ASPNET, który zawiera tylko składniki środowiska uruchomieniowego. Przyczyna użycia oddzielnego obrazu zostanie wyczyszczona, gdy zobaczysz resztę pliku dockerfile:

```
FROM build AS publish
RUN dotnet publish "WebApplication43.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "WebApplication43.dll"]
```

Końcowy etap zostanie uruchomiony ponownie z `base` i zawiera `COPY --from=publish` kopię publikowanych danych wyjściowych do obrazu końcowego. Dzięki temu obraz końcowy może być dużo mniejszy, ponieważ nie musi zawierać wszystkich narzędzi do kompilacji, które znajdowały się w `sdk` obrazie.

## <a name="building-from-the-command-line"></a>Kompilowanie z wiersza polecenia

Jeśli chcesz skompilować poza programem Visual Studio, możesz użyć programu `docker build` lub `MSBuild` do kompilowania z poziomu wiersza polecenia.

### <a name="docker-build"></a>docker build

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

Dane wyjściowe będą wyglądać podobnie jak w oknie **danych wyjściowych** podczas kompilowania rozwiązania z poziomu środowiska IDE programu Visual Studio. Zawsze używaj `/p:Configuration=Release` , ponieważ w przypadkach, gdy program Visual Studio używa optymalizacji kompilacji potokach wieloetapowych, wyniki podczas kompilowania konfiguracji **debugowania** mogą nie być zgodne z oczekiwaniami. Zobacz [debugowanie](#debugging).

Jeśli używasz projektu Docker Compose, użyj tego polecenia, aby skompilować obrazy:

```cmd
msbuild /p:SolutionPath=<solution-name>.sln /p:Configuration=Release docker-compose.dcproj
```

## <a name="project-warmup"></a>Rozgrzewania projektu

*Projekt rozgrzewania* odnosi się do serii kroków, które są wykonywane, gdy wybrano profil platformy Docker dla projektu (to znaczy, gdy projekt jest ładowany lub dodano obsługę platformy Docker), aby zwiększyć wydajność kolejnych uruchomień (**F5** lub **Ctrl** + **F5**). Można to skonfigurować w obszarze **Narzędzia**  >  **Opcje**  >  **kontenerów narzędzia**. Poniżej przedstawiono zadania, które są uruchamiane w tle:

- Sprawdź, czy program Docker Desktop jest zainstalowany i uruchomiony.
- Upewnij się, że na pulpicie platformy Docker jest ustawiony ten sam system operacyjny co projekt.
- Pobierz obrazy z pierwszego etapu pliku dockerfile ( `base` etap w większości wieloetapowe dockerfile).  
- Skompiluj pliku dockerfile i uruchom kontener.

Rozgrzewania będzie działać tylko w trybie **szybkim** , dlatego uruchomiony kontener będzie miał zainstalowany wolumin folderu aplikacji. Oznacza to, że wszelkie zmiany w aplikacji nie będą unieważniać kontenera. Dlatego zwiększa to wydajność debugowania znacznie i skraca czas oczekiwania na długotrwałe zadania, takie jak ściąganie dużych obrazów.

## <a name="volume-mapping"></a>Mapowanie woluminów

Aby debugowanie działało w kontenerach, program Visual Studio używa mapowania woluminów do mapowania debugera i folderów NuGet z komputera hosta. Mapowanie woluminów zostało opisane w dokumentacji platformy Docker [tutaj](https://docs.docker.com/storage/volumes/). Poniżej przedstawiono woluminy, które są zainstalowane w kontenerze:

|Wolumin|Opis|
|-|-|
| **Zdalny debuger** | Zawiera bity wymagane do uruchomienia debugera w kontenerze w zależności od typu projektu. Szczegółowo wyjaśniono w sekcji [debugowanie](#debugging) .|
| **Folder aplikacji** | Zawiera folder projektu, w którym znajduje się pliku dockerfile.|
| **Folder źródłowy** | Zawiera kontekst kompilacji, który jest przesyłany do poleceń platformy Docker.|
| **Foldery pakietów NuGet** | Zawiera pakiety NuGet i foldery rezerwowe, które są odczytywane z pliku *obj \{ }. csproj. NuGet. g. props* w projekcie. |

W przypadku aplikacji sieci Web ASP.NET Core mogą istnieć dwa dodatkowe foldery dla certyfikatu SSL i wpisy tajne użytkownika, które opisano szczegółowo w następnej sekcji.

## <a name="ssl-enabled-aspnet-core-apps"></a>Aplikacje ASP.NET Core obsługujące protokół SSL

Narzędzia kontenerów w programie Visual Studio obsługują debugowanie aplikacji ASP.NET Core z obsługą protokołu SSL przy użyciu certyfikatu deweloperskiego, tak samo jak w przypadku, gdy oczekujesz, że będzie on działał bez kontenerów. W takim przypadku program Visual Studio dodaje kilka kroków w celu wyeksportowania certyfikatu i udostępnienia go dla kontenera. Oto przepływ, którego program Visual Studio obsługuje podczas debugowania w kontenerze:

1. Zapewnia, że lokalny certyfikat programistyczny jest obecny i zaufany na maszynie hosta za pomocą `dev-certs` Narzędzia.
2. Eksportuje certyfikat do%APPDATA%\ASP.NET\Https przy użyciu bezpiecznego hasła przechowywanego w magazynie kluczy tajnych użytkownika dla tej konkretnej aplikacji.
3. Wolumin — instaluje następujące katalogi:

   - *%APPDATA%\Microsoft\UserSecrets*
   - *%APPDATA%\ASP.NET\Https*

ASP.NET Core szuka certyfikatu zgodnego z nazwą zestawu w folderze *https* , co oznacza, że jest on mapowany do kontenera w tej ścieżce. Ścieżkę i hasło certyfikatu można alternatywnie zdefiniować przy użyciu zmiennych środowiskowych (czyli `ASPNETCORE_Kestrel__Certificates__Default__Path` i `ASPNETCORE_Kestrel__Certificates__Default__Password` ) lub w pliku JSON użytkownika, na przykład:

```json
{
  "Kestrel": {
    "Certificates": {
      "Default": {
        "Path": "c:\\app\\mycert.pfx",
        "Password": "strongpassword"
      }
    }
  }
}
```

Jeśli konfiguracja obsługuje zarówno kompilacje kontenerów, jak i niekontenerowe, należy używać zmiennych środowiskowych, ponieważ ścieżki są specyficzne dla środowiska kontenera.

Aby uzyskać więcej informacji na temat używania protokołu SSL z aplikacjami ASP.NET Core w kontenerach, zobacz [hostowanie ASP.NET Core obrazów przy użyciu protokołu Docker over https](/aspnet/core/security/docker-https)).

## <a name="debugging"></a>Debugowanie

Podczas kompilowania w konfiguracji **debugowania** istnieje kilka optymalizacji, które program Visual Studio pomaga w wydajności procesu kompilacji dla projektów kontenerowych. Proces kompilacji dla aplikacji kontenerowych nie jest tak prosty jak po kroku opisanym w pliku dockerfile. Kompilowanie w kontenerze jest znacznie wolniejsze niż kompilowanie na komputerze lokalnym.  Dlatego podczas kompilowania w konfiguracji **debugowania** program Visual Studio rzeczywiście kompiluje projekty na komputerze lokalnym, a następnie udostępnia folder wyjściowy do kontenera przy użyciu funkcji montowania woluminu. Kompilacja z włączoną opcją optymalizacji jest nazywana kompilacją trybu *szybkiego* .

W trybie **szybkim** program Visual Studio wywołuje `docker build` z argumentem, który instruuje platformę Docker, aby kompiluje tylko ten `base` etap.  Program Visual Studio obsługuje resztę procesu bez względu na zawartość pliku dockerfile. Dlatego w przypadku zmodyfikowania pliku dockerfile, na przykład w celu dostosowania środowiska kontenera lub zainstalowania dodatkowych zależności, należy wprowadzić modyfikacje w pierwszym etapie.  Wszelkie niestandardowe kroki umieszczone w pliku dockerfile `build` , `publish` , lub `final` etapy nie będą wykonywane.

Ta optymalizacja wydajności występuje tylko w przypadku kompilowania w konfiguracji **debugowania** . W konfiguracji **wydania** kompilacja odbywa się w kontenerze określonym w pliku dockerfile.

Jeśli chcesz wyłączyć optymalizację wydajności i kompilację jako pliku dockerfile, ustaw właściwość **ContainerDevelopmentMode** na **Regular** w pliku projektu w następujący sposób:

```xml
<PropertyGroup>
   <ContainerDevelopmentMode>Regular</ContainerDevelopmentMode>
</PropertyGroup>
```

Aby przywrócić optymalizację wydajności, Usuń właściwość z pliku projektu.

 Po rozpoczęciu debugowania (**F5**) poprzednio uruchomiony kontener jest ponownie używany, jeśli jest to możliwe. Jeśli nie chcesz ponownie używać poprzedniego kontenera, możesz użyć polecenia **Kompiluj** lub **Wyczyść** w programie Visual Studio, aby wymusić użycie przez program Visual Studio nowego kontenera.

Proces uruchamiania debugera zależy od typu projektu i systemu operacyjnego kontenera:

|Scenariusz|Proces debugera|
|-|-|
| **Aplikacje platformy .NET Core (kontenery systemu Linux)**| Program Visual Studio pobiera `vsdbg` i mapuje go do kontenera, a następnie jest wywoływany z programem i argumentami (czyli `dotnet webapp.dll` ), a następnie debuger dołącza do procesu. |
| **Aplikacje platformy .NET Core (kontenery systemu Windows)**| Program Visual Studio używa `onecoremsvsmon` i mapuje go do kontenera, uruchamia go jako punkt wejścia, a następnie program Visual Studio nawiązuje połączenie z nim i dołącza do programu. Przypomina to jak zwykle skonfigurować zdalne debugowanie na innym komputerze lub maszynie wirtualnej.|
| **Aplikacje .NET Framework** | Program Visual Studio używa `msvsmon` i mapuje go do kontenera, uruchamia go jako część punktu wejścia, gdzie program Visual Studio może się z nim połączyć i dołącza do programu.|

Aby uzyskać więcej informacji na temat `vsdbg.exe` , zobacz [Offroad debugowanie architektury .NET Core w systemie Linux i OSX z programu Visual Studio](https://github.com/Microsoft/MIEngine/wiki/Offroad-Debugging-of-.NET-Core-on-Linux---OSX-from-Visual-Studio).

## <a name="container-entry-point"></a>Punkt wejścia kontenera

Program Visual Studio używa niestandardowego punktu wejścia kontenera w zależności od typu projektu i systemu operacyjnego kontenera, poniżej przedstawiono różne kombinacje:

|Typ kontenera|Punkt wejścia|
|-|-|
| **Kontenery systemu Linux** | Punkt wejścia to `tail -f /dev/null` , czyli nieskończony czas oczekiwania na utrzymanie kontenera. Gdy aplikacja jest uruchamiana za pomocą debugera, jest to debuger, który jest odpowiedzialny za uruchamianie aplikacji (czyli `dotnet webapp.dll` ). Jeśli uruchomiono bez debugowania, narzędzia uruchamiają `docker exec -i {containerId} dotnet webapp.dll` się, aby uruchomić aplikację.|
| **Kontenery systemu Windows**| Punkt wejścia jest podobny do `C:\remote_debugger\x64\msvsmon.exe /noauth /anyuser /silent /nostatus` tego, który uruchamia debuger, więc nasłuchuje połączeń. Ta sama zasada ma zastosowanie w przypadku, gdy debuger uruchamia aplikację i `docker exec` polecenie po uruchomieniu bez debugowania. W przypadku .NET Framework aplikacji sieci Web punkt wejścia jest nieco inny, gdzie `ServiceMonitor` jest dodawany do polecenia.|

Punkt wejścia kontenera można modyfikować tylko w projektach platformy Docker, a nie w projektach z pojedynczym kontenerem.

## <a name="next-steps"></a>Następne kroki

Dowiedz się, jak dodatkowo dostosować kompilacje przez ustawienie dodatkowych właściwości programu MSBuild w plikach projektu. Zobacz [Właściwości programu MSBuild dla projektów kontenerów](container-msbuild-properties.md).

## <a name="see-also"></a>Zobacz też

Program [MSBuild](../msbuild/msbuild.md) 
 [Pliku dockerfile w systemie Windows](/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile) 
 [Kontenery systemu Linux w systemie Windows](/virtualization/windowscontainers/deploy-containers/linux-containers)

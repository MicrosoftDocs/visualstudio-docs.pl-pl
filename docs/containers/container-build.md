---
title: Omówienie kompilacji i debugowania narzędzi kontenerów programu Visual Studio
author: ghogen
description: Omówienie procesu tworzenia i debugowania narzędzi kontenerowych
ms.author: ghogen
ms.date: 11/20/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: d91dd01879ac3bb62b981109463f6762046382ef
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77027261"
---
# <a name="how-visual-studio-builds-containerized-apps"></a>Jak program Visual Studio umożliwia tworzenie aplikacji konteneryzowanych

Niezależnie od tego, czy tworzysz z środowiska IDE programu Visual Studio, czy konfigurujesz kompilację wiersza polecenia, musisz wiedzieć, jak program Visual Studio używa pliku Dockerfile do tworzenia projektów.  Ze względu na wydajność visual studio następuje specjalny proces dla aplikacji konteneryzowanych. Zrozumienie, jak Visual Studio tworzy projekty jest szczególnie ważne podczas dostosowywania procesu kompilacji przez modyfikowanie Dockerfile.

Gdy program Visual Studio tworzy projekt, który nie używa kontenerów platformy Docker, wywołuje MSBuild na komputerze `bin`lokalnym i generuje pliki wyjściowe w folderze (zazwyczaj) w folderze rozwiązania lokalnego. W przypadku projektu konteneryzowanego proces kompilacji uwzględnia jednak instrukcje dockerfile dotyczące tworzenia konteneryzowanej aplikacji. Plik Dockerfile, którego używa program Visual Studio, jest podzielony na wiele etapów. Proces ten opiera się na *wieloetapowej* funkcji kompilacji platformy Docker.

## <a name="multistage-build"></a>Kompilacja wieloetapowa

Funkcja kompilacji wieloetapowej pomaga uczynić proces tworzenia kontenerów bardziej wydajne i sprawia, że kontenery mniejsze, umożliwiając im zawierać tylko bity, które aplikacja potrzebuje w czasie wykonywania. Kompilacja wieloetapowa jest używana dla projektów .NET Core, a nie projektów .NET Framework.

Kompilacja wieloetapowa umożliwia tworzenie obrazów kontenerów w etapach, które generują obrazy pośrednie. Na przykład należy wziąć pod uwagę typowy plik dockerfile `base`generowany przez program Visual Studio — pierwszym etapem jest:

```
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443
```

Linie w pliku Dockerfile zaczynają się od obrazu Debiana z rejestru kontenerów `base` firmy Microsoft (mcr.microsoft.com) i tworzą obraz pośredni, który `/app`udostępnia porty 80 i 443 i ustawia katalog roboczy na .

Kolejnym etapem `build`jest , który wygląda następująco:

```
FROM mcr.microsoft.com/dotnet/core/sdk:2.2-stretch AS build
WORKDIR /src
COPY ["WebApplication43/WebApplication43.csproj", "WebApplication43/"]
RUN dotnet restore "WebApplication43/WebApplication43.csproj"
COPY . .
WORKDIR "/src/WebApplication43"
RUN dotnet build "WebApplication43.csproj" -c Release -o /app
```

Widać, że `build` etap zaczyna się od innego oryginalnego`sdk` obrazu `aspnet`z rejestru ( a nie ), a nie dalej od podstawy.  Obraz `sdk` ma wszystkie narzędzia kompilacji i z tego powodu jest o wiele większy niż obraz aspnet, który zawiera tylko składniki środowiska wykonawczego. Przyczyna użycia oddzielnego obrazu staje się jasna, gdy spojrzysz na pozostałą część pliku Dockerfile:

```
FROM build AS publish
RUN dotnet publish "WebApplication43.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "WebApplication43.dll"]
```

Ostatni etap rozpoczyna się `base`ponownie od `COPY --from=publish` , i zawiera skopiować opublikowane dane wyjściowe do ostatecznego obrazu. Ten proces umożliwia ostateczny obraz jest znacznie mniejszy, ponieważ nie musi zawierać wszystkich narzędzi kompilacji, które były na obrazie. `sdk`

## <a name="building-from-the-command-line"></a>Budowanie z wiersza polecenia

Jeśli chcesz tworzyć poza programem Visual `docker build` Studio, można użyć lub `MSBuild` skompilować z wiersza polecenia.

### <a name="docker-build"></a>docker build

Aby utworzyć rozwiązanie konteneryzowane z wiersza polecenia, `docker build <context>` zwykle można użyć polecenia dla każdego projektu w rozwiązaniu. Podać argument *kontekstu kompilacji.* *Kontekst kompilacji* dla dockerfile jest folder na komputerze lokalnym, który jest używany jako folder roboczy do generowania obrazu. Na przykład jest to folder, z którego kopiujesz pliki podczas kopiowania do kontenera.  W projektach .NET Core użyj folderu zawierającego plik rozwiązania (.sln).  Wyrażony jako ścieżka względna, ten argument jest zazwyczaj ".." dla Dockerfile w folderze projektu i pliku rozwiązania w folderze nadrzędnym.  W przypadku projektów platformy .NET Framework kontekst kompilacji jest folderem projektu, a nie folderem rozwiązania.

```cmd
docker build -f Dockerfile ..
```

### <a name="msbuild"></a>MSBuild

Pliki dockerfiles utworzone przez program Visual Studio dla projektów programu .NET Framework (i dla projektów .NET Core utworzonych za pomocą wersji programu Visual Studio przed aktualizacją programu Visual Studio 2017 Update 4) nie są wieloetapowymi plikami dockerfiles.  Kroki w tych dockerfiles nie skompilować kodu.  Zamiast tego gdy program Visual Studio tworzy plik dockerfile .NET Framework, najpierw kompiluje projekt przy użyciu msbuild.  Gdy to się powiedzie, Visual Studio następnie tworzy Dockerfile, który po prostu kopiuje dane wyjściowe kompilacji z MSBuild do wynikowego obrazu platformy Docker.  Ponieważ kroki do skompilowania kodu nie są uwzględnione w Dockerfile, nie można utworzyć `docker build` .NET Framework Dockerfiles przy użyciu z wiersza polecenia. Do tworzenia tych projektów należy użyć narzędzia MSBuild.

Aby utworzyć obraz dla pojedynczego projektu kontenera platformy docker można użyć MSBuild z opcją `/t:ContainerBuild` polecenia. Przykład:

```cmd
MSBuild MyProject.csproj /t:ContainerBuild /p:Configuration=Release
```

Zobaczysz dane wyjściowe podobne do tego, co widzisz w oknie **dane wyjściowe** podczas tworzenia rozwiązania z ide programu Visual Studio. Zawsze `/p:Configuration=Release`używaj , ponieważ w przypadkach, gdy visual studio używa optymalizacji kompilacji wieloetapowej, wyniki podczas tworzenia konfiguracji **debugowania** może nie być zgodnie z oczekiwaniami. Zobacz [Debugowanie](#debugging).

Jeśli używasz projektu docker compose, użyj tego polecenia do tworzenia obrazów:

```cmd
msbuild /p:SolutionPath=<solution-name>.sln /p:Configuration=Release docker-compose.dcproj
```

## <a name="project-warmup"></a>Rozgrzewka projektu

*Rozgrzewka projektu* odnosi się do serii kroków, które mają miejsce, gdy profil platformy Docker jest wybrany dla projektu (czyli po załadowaniu projektu lub docker wsparcie jest dodawany) w celu zwiększenia wydajności kolejnych przebiegów **(F5** lub **Ctrl**+**F5**). Można to konfigurować w obszarze**Narzędzia kontenerów****opcji** >  **narzędzi narzędzi** > . Oto zadania uruchamiane w tle:

- Sprawdź, czy program Docker Desktop jest zainstalowany i uruchomiony.
- Upewnij się, że program Docker Desktop jest ustawiony na ten sam system operacyjny co projekt.
- Ściągnij obrazy w pierwszym etapie dockerfile `base` (etap w większości Dockerfiles).  
- Skompiluj plik Dockerfile i uruchom kontener.

Rozgrzewka nastąpi tylko w trybie **szybki,** więc uruchomiony kontener będzie miał zainstalowany wolumin folderu aplikacji. Oznacza to, że wszelkie zmiany w aplikacji nie unieważniają kontenera. W związku z tym znacznie zwiększa wydajność debugowania i zmniejsza czas oczekiwania na długo działające zadania, takie jak ciągnięcie dużych obrazów.

## <a name="volume-mapping"></a>Mapowanie woluminów

Do debugowania do pracy w kontenerach, Visual Studio używa mapowania woluminów do mapowania debugera i NuGet folderów z komputera hosta. Mapowanie woluminów jest opisane w dokumentacji platformy Docker [w tym miejscu](https://docs.docker.com/storage/volumes/). Oto woluminy, które są zamontowane w kontenerze:

|||
|-|-|
| **Debuger zdalny** | Zawiera bity wymagane do uruchomienia debugera w kontenerze w zależności od typu projektu. Jest to wyjaśnione w bardziej |szczegóły w sekcji [Debugowanie.](#debugging)
| **Folder aplikacji** | Zawiera folder projektu, w którym znajduje się plik Dockerfile.|
| **Folder źródłowy** | Zawiera kontekst kompilacji, który jest przekazywany do poleceń platformy Docker.|
| **Foldery pakietów NuGet** | Zawiera pakiety NuGet i foldery rezerwowe odczytywane z pliku *\{obj project}.csproj.nuget.g.props* w projekcie. |

W przypadku ASP.NET podstawowych aplikacji sieci web mogą istnieć dwa dodatkowe foldery dla certyfikatu SSL i wpisów tajnych użytkownika, co jest wyjaśnione bardziej szczegółowo w następnej sekcji.

## <a name="ssl-enabled-aspnet-core-apps"></a>Aplikacje ASP.NET Core z obsługą SSL

Narzędzia kontenerów w programie Visual Studio obsługują debugowanie aplikacji ASP.NET rdzenia z obsługą SSL z certyfikatem deweloperskim, w taki sam sposób, w jaki można oczekiwać, że będzie działać bez kontenerów. Aby tak się stało, Visual Studio dodaje kilka kroków, aby wyeksportować certyfikat i udostępnić go do kontenera. Oto przepływ, który visual studio obsługuje dla Ciebie podczas debugowania w kontenerze:

1. Zapewnia obecność certyfikatu lokalnego rozwoju i zaufanie `dev-certs` na komputerze hosta za pośrednictwem narzędzia.
2. Eksportuje certyfikat do %APPDATA%\ASP.NET\Https z bezpiecznym hasłem, które jest przechowywane w magazynie wpisów tajnych użytkownika dla tej konkretnej aplikacji.
3. Wolumin instaluje następujące katalogi:

   - *%APPDATA%\Microsoft\UserSecrets*
   - *%APPDATA%\ASP.NET\Https*

ASP.NET Core wyszukuje certyfikat, który pasuje do nazwy zestawu w obszarze *https* folderu, dlatego jest mapowany do kontenera w tej ścieżce. Ścieżkę certyfikatu i hasło można również zdefiniować przy `ASPNETCORE_Kestrel__Certificates__Default__Path` `ASPNETCORE_Kestrel__Certificates__Default__Password`użyciu zmiennych środowiskowych (czyli i) lub w pliku json wpisów tajnych użytkownika, na przykład:

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

Jeśli konfiguracja obsługuje zarówno konteneryzowanych i nie konteneryzowanych kompilacji, należy użyć zmiennych środowiskowych, ponieważ ścieżki są specyficzne dla środowiska kontenera.

Aby uzyskać więcej informacji na temat używania protokołu SSL z aplikacjami ASP.NET Core w kontenerach, zobacz [Hosting ASP.NET obrazy rdzenia za pomocą platformy Docker za pośrednictwem protokołu HTTPS](/aspnet/core/security/docker-https)).

## <a name="debugging"></a>Debugging

Podczas tworzenia w konfiguracji **debugowania,** istnieje kilka optymalizacji, które visual studio nie, które pomagają w wydajności procesu kompilacji dla projektów konteneryzowanych. Proces kompilacji dla konteneryzowanych aplikacji nie jest tak proste, jak po prostu po kroki opisane w Dockerfile. Budowanie w kontenerze jest znacznie wolniejsze niż budowanie na lokalnej maszynie.  Tak po utworzeniu w konfiguracji **debugowania** Visual Studio faktycznie tworzy projekty na komputerze lokalnym, a następnie udostępnia folder danych wyjściowych do kontenera przy użyciu montażu woluminu. Kompilacja z włączoną optymalizacją jest nazywana kompilacją trybu *szybkiego.*

W trybie **szybki** `docker build` program Visual Studio wywołuje z argumentem, który mówi docker do tworzenia tylko na `base` etapie.  Visual Studio obsługuje resztę procesu bez względu na zawartość Dockerfile. Tak podczas modyfikowania dockerfile, takich jak dostosować środowisko kontenera lub zainstalować dodatkowe zależności, należy umieścić swoje modyfikacje w pierwszym etapie.  Wszystkie niestandardowe kroki umieszczone w pliku `build` `publish`Dockerfile lub `final` etapy nie zostaną wykonane.

Ta optymalizacja wydajności występuje tylko podczas tworzenia w konfiguracji **debugowania.** W konfiguracji **release** kompilacji występuje w kontenerze, jak określono w Dockerfile.

Jeśli chcesz wyłączyć optymalizację wydajności i budować zgodnie z określa Dockerfile, a następnie ustawić **ContainerDevelopmentMode** właściwość **regularna** w pliku projektu w następujący sposób:

```xml
<PropertyGroup>
   <ContainerDevelopmentMode>Regular</ContainerDevelopmentMode>
</PropertyGroup>
```

Aby przywrócić optymalizację wydajności, usuń właściwość z pliku projektu.

 Po uruchomieniu debugowania (**F5**), wcześniej uruchomiony kontener jest ponownie, jeśli to możliwe. Jeśli nie chcesz ponownie użyć poprzedniego kontenera, można użyć **polecenia Odbuduj** lub **Wyczyść** w programie Visual Studio, aby wymusić program Visual Studio do użycia świeżego kontenera.

Proces uruchamiania debugera zależy od typu projektu i systemu operacyjnego kontenera:

|||
|-|-|
| **Aplikacje .NET Core (kontenery systemu Linux)**| Visual Studio `vsdbg` pobiera i mapuje go do kontenera, a następnie zostanie `dotnet webapp.dll`wywołany z programem i argumentów (to znaczy), a następnie debuger dołącza do procesu. |
| **Aplikacje .NET Core (kontenery systemu Windows)**| Visual Studio `onecoremsvsmon` używa i mapuje go do kontenera, uruchamia go jako punkt wejścia, a następnie Visual Studio łączy się z nim i dołącza do programu. Jest to podobne do sposobu konfigurowania zdalnego debugowania na innym komputerze lub maszynie wirtualnej.|
| **Aplikacje programu .NET Framework** | Visual Studio `msvsmon` używa i mapuje go do kontenera, uruchamia go jako część punktu wejścia, gdzie Visual Studio można połączyć się z nim i dołącza do programu.|

Aby uzyskać `vsdbg.exe`informacje na temat , zobacz [Debugowanie offroad .NET Core w systemie Linux i OSX z programu Visual Studio](https://github.com/Microsoft/MIEngine/wiki/Offroad-Debugging-of-.NET-Core-on-Linux---OSX-from-Visual-Studio).

## <a name="container-entry-point"></a>Punkt wejścia kontenera

Visual Studio używa niestandardowego punktu wejścia kontenera w zależności od typu projektu i systemu operacyjnego kontenera, oto różne kombinacje:

|||
|-|-|
| **Kontenery systemu Linux** | Punkt wejścia `tail -f /dev/null`jest , który jest nieskończone czekać, aby zachować kontener uruchomiony. Po uruchomieniu aplikacji za pośrednictwem debugera jest debuger, jest debugerem, który jest odpowiedzialny za uruchomienie aplikacji (czyli `dotnet webapp.dll`). Jeśli zostanie uruchomiony bez debugowania, `docker exec -i {containerId} dotnet webapp.dll` narzędzia uruchamia się do uruchomienia aplikacji.|
| **Kontenery systemu Windows**| Punkt wejścia jest `C:\remote_debugger\x64\msvsmon.exe /noauth /anyuser /silent /nostatus` coś takiego, który uruchamia debugera, więc jest nasłuchiwanie połączeń. To samo dotyczy, że debuger uruchamia `docker exec` aplikację i polecenia po uruchomieniu bez debugowania. W przypadku aplikacji sieci web programu .NET `ServiceMonitor` Framework punkt wejścia jest nieco inny, gdzie jest dodawany do polecenia.|

Punkt wejścia kontenera można modyfikować tylko w projektach docker-compose, a nie w projektach z jednym kontenerem.

## <a name="next-steps"></a>Następne kroki

Dowiedz się, jak dalej dostosowywać kompilacje, ustawiając dodatkowe właściwości MSBuild w plikach projektu. Zobacz [WŁAŚCIWOŚCI MSBuild dla projektów kontenerów](container-msbuild-properties.md).

## <a name="see-also"></a>Zobacz też

[Plik](../msbuild/msbuild.md)
[dockerfile](/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
MSBuild na kontenerach systemu Windows[Linux w systemie Windows](/virtualization/windowscontainers/deploy-containers/linux-containers)

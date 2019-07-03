---
title: Narzędzia kontenerów programu Visual Studio kompilacji — omówienie
author: ghogen
description: Omówienie procesu kompilacji narzędzia kontenerów
ms.author: ghogen
ms.date: 06/06/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 9f2da112bfeebe4e0bce976736eee5696d888105
ms.sourcegitcommit: c7b9ab1bc19d74b635c19b1937e92c590dafd736
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2019
ms.locfileid: "67552823"
---
# <a name="building-containerized-apps-using-visual-studio-or-the-command-line"></a>Tworzenie kontenerowych nimi aplikacji przy użyciu programu Visual Studio lub wiersza polecenia

W przypadku tworzenia z programu Visual Studio IDE, czy Konfigurowanie kompilacji wiersza polecenia, musisz wiedzieć, jak program Visual Studio tworzy używa pliku Dockerfile do tworzenia projektów.  Ze względu na wydajność programu Visual Studio, następuje specjalny proces konteneryzowanych aplikacji. Zrozumienie, w jaki sposób program Visual Studio kompiluje projekty jest szczególnie ważne w przypadku, gdy możesz dostosować proces kompilacji, modyfikując plik Dockerfile.

Gdy program Visual Studio tworzy projekt, który nie używa kontenerów platformy Docker, wywołuje MSBuild na komputerze lokalnym i generuje pliki wyjściowe w folderze (zazwyczaj `bin`) w folderze rozwiązania lokalnego. Dla projektów konteneryzowanych jednak proces kompilacji uwzględnia instrukcji pliku Dockerfile w celu skompilowania aplikacji konteneryzowanych. Plik Dockerfile, który używa programu Visual Studio jest podzielony na wiele etapów. Ten proces zależy od platformy Docker *wieloetapowych kompilacji* funkcji.

## <a name="multistage-build"></a>Wieloetapowych kompilacji

Funkcja kompilacji wieloetapowych ułatwia proces tworzenia kontenerów bardziej efektywne i sprawia, że kontenery mniejszych, umożliwiając im zawierają tylko bity, które Twoja aplikacja wymaga w czasie wykonywania. Wieloetapowych kompilacji jest używany dla projektów .NET Core, nie projektów programu .NET Framework.

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

Istnieje kilka optymalizacji, które pomagają wydajności procesu kompilacji dla projektów konteneryzowanych program Visual Studio. Po rozpoczęciu debugowania (F5), wcześniej utworzony obraz zostanie ponownie użyty, jeśli jest to możliwe. Jeśli nie chcesz ponownie użyć poprzedniej kontenera, możesz użyć **odbudować** lub **czysty** polecenia w programie Visual Studio, aby wymusić programu Visual Studio do używania nowej kontenera.

Ponadto w celu poprawy wydajności procesu kompilacji dla konteneryzowanych aplikacji nie jest tak proste jak po prostu wykonując kroki opisane w pliku Dockerfile. Tworzenie w kontenerze jest znacznie wolniejsze niż opierając się na komputerze lokalnym.  Dlatego podczas kompilowania **debugowania** konfiguracji programu Visual Studio rzeczywiście kompiluje projekty na komputerze lokalnym, a następnie udostępnia folder dane wyjściowe do kontenera przy użyciu zamontowania woluminu. Nosi nazwę kompilacji z użyciem tego rodzaju optymalizacji, włączone *Fast* tryb kompilacji.

W **Fast** tryb, wywołań programu Visual Studio `docker build` z nieprawidłowym argumentem platformy docker do tworzenia tylko `base` etapu.  Visual Studio obsługuje resztą procesu bez względu na zawartość pliku Dockerfile. Tak gdy modyfikujesz z pliku Dockerfile, takie jak dostosować środowisko kontenerów lub zainstalować dodatkowe zależności w pierwszym etapie należy umieszczać modyfikacje.  Wszystkie niestandardowe kroki umieszczone w pliku Dockerfile `build`, `publish`, lub `final` etapów nie zostaną wykonane.

Tego rodzaju optymalizacji wydajności występuje tylko wtedy, gdy tworzysz **debugowania** konfiguracji. W **wersji** konfiguracji kompilacji odbywa się w kontenerze, jak określono w pliku Dockerfile.

Jeśli chcesz wyłączyć optymalizację wydajności i kompilacji jako Określa plik Dockerfile, następnie ustawić **ContainerDevelopmentMode** właściwości **regularne** w pliku projektu w następujący sposób:

```xml
<PropertyGroup>
   <ContainerDevelopmentMode>Regular</ContainerDevelopmentMode>
</PropertyGroup>
```

Aby przywrócić optymalizacji wydajności, należy usunąć właściwość z pliku projektu.

## <a name="building-from-the-command-line"></a>Tworzenie z wiersza polecenia

Możesz użyć `docker build` lub `MSBuild` do kompilacji z wiersza polecenia.

### <a name="docker-build"></a>kompilacji platformy docker

Tworzenie konteneryzowanej rozwiązania z wiersza polecenia, zazwyczaj można użyć polecenia `docker build <context>` dla każdego projektu w rozwiązaniu. Należy podać *kompilacji kontekstu* argumentu. *Kompilacji kontekstu* dla pliku Dockerfile jest folder na komputerze lokalnym, który jest używany jako folder roboczy do generowania obrazu. Na przykład jest folder, który można skopiować pliki z przy kopiowaniu do kontenera.  W projektach .NET Core należy użyć folderu zawierającego plik rozwiązania (.sln).  Wyrażony w postaci ścieżki względnej, ten argument jest zazwyczaj ".." dla pliku Dockerfile w folderze projektu i plik rozwiązania w folderze nadrzędnym.  Dla projektów programu .NET Framework kontekstu kompilacji jest folder projektu, a nie w folderze rozwiązania.

```cmd
docker build -f Dockerfile ..
```

### <a name="msbuild"></a>MSBuild

Pliki Dockerfile utworzone przez program Visual Studio dla projektów programu .NET Framework (i dla projektów .NET Core utworzone za pomocą wersji programu Visual Studio przed Visual Studio 2017 Update 4) nie są wieloetapowych pliki Dockerfile.  Kroki opisane w tych plików Dockerfile nie można skompilować kod.  Zamiast tego gdy program Visual Studio tworzy plik Dockerfile .NET Framework, najpierw kompiluje projekt, korzystając z programu MSBuild.  Jeśli się to powiedzie, program Visual Studio tworzy następnie plik Dockerfile, po prostu kopiuje dane wyjściowe kompilacji z programu MSBuild do Wynikowy obraz platformy Docker.  Ponieważ kroki do kompilowania kodu nie są zawarte w pliku Dockerfile, nie można utworzyć plików Dockerfile Framework .NET przy użyciu `docker build` z wiersza polecenia. Należy użyć programu MSBuild do kompilowania tych projektów.

Do tworzenia obrazu dla pojedynczej platformy docker container projektu można użyć programu MSBuild z `/t:ContainerBuild` opcja polecenia. Na przykład:

```cmd
MSBuild MyProject.csproj /t:ContainerBuild /p:Configuration=Release
```

Zostaną wyświetlone dane wyjściowe podobne do wyświetlania w **dane wyjściowe** okna podczas kompilowania rozwiązania z programu Visual Studio IDE. Zawsze używaj `/p:Configuration=Release`, ponieważ w przypadku, gdy program Visual Studio używa kompilacji wieloetapowych optymalizacji, wyniki podczas kompilowania **debugowania** konfiguracji nie może być zgodnie z oczekiwaniami.

Jeśli używasz narzędzia Docker Compose projektu, użyj polecenia do tworzenia obrazów:

```cmd
msbuild /p:SolutionPath=<solution-name>.sln /p:Configuration=Release docker-compose.dcproj
```

## <a name="next-steps"></a>Następne kroki

Dowiedz się, jak dostosować kompilacji przez ustawienie dodatkowych właściwości programu MSBuild w plikach projektu. Zobacz [właściwości programu MSBuild dla projektów kontenera](container-msbuild-properties.md).

## <a name="see-also"></a>Zobacz także

[Program MSBuild](../msbuild/msbuild.md)
[pliku Dockerfile na Windows](/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
[kontenerów systemu Linux na Windows](/virtualization/windowscontainers/deploy-containers/linux-containers)

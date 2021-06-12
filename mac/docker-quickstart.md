---
title: Wprowadzenie do platformy Docker
description: Dowiedz się, jak dodać program Docker do projektów w programie Visual Studio dla komputerów Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/09/2020
ms.topic: how-to
ms.openlocfilehash: 4ddb15c8bc5bf90663c5431d2379af61b43e73a6
ms.sourcegitcommit: 4b2b6068846425f6964c1fd867370863fc4993ce
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2021
ms.locfileid: "112043097"
---
# <a name="get-started-with-docker-in-visual-studio-for-mac"></a>Wprowadzenie do platformy Docker w programie Visual Studio dla komputerów Mac

Dzięki Visual Studio dla komputerów Mac można łatwo tworzyć, debugować i uruchamiać konteneryzowane aplikacje ASP.NET Core i publikować je na platformie Azure.

## <a name="prerequisites"></a>Wymagania wstępne

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-mac)
* [Visual Studio dla komputerów Mac 2019 r.](https://visualstudio.microsoft.com/vs/mac)

## <a name="installation-and-setup"></a>Instalacja i konfiguracja

W przypadku instalacji platformy Docker przejrzyj i postępuj zgodnie z informacjami w te tematach Install Docker Desktop for Mac (Instalowanie [programu Docker Desktop dla komputerów Mac).](https://docs.docker.com/docker-for-mac/install/)

## <a name="creating-an-aspnet-core-web-application-and-adding-docker-support"></a>Tworzenie aplikacji ASP.NET Core i dodawanie obsługi platformy Docker

1. Utwórz nowe rozwiązanie, przechodząc do > **Nowe rozwiązanie.**
1. W **obszarze Aplikacja > .NET Core** wybierz szablon Aplikacja **internetowa:** ![ Tworzenie nowej ASP.NET aplikacji internetowej](media/docker-quickstart-1.png)
1. Wybierz platformę docelową. W tym przykładzie użyjemy programu .NET Core 2.2: ![ Ustaw platformę docelową](media/docker-quickstart-2.png)
1. Wprowadź szczegóły projektu, takie jak name _(DockerDemo_ w tym przykładzie). Utworzony projekt zawiera wszystkie podstawowe informacje potrzebne do skompilowania i uruchomienia witryny ASP.NET Core.
1. W oknie rozwiązania kliknij prawym przyciskiem myszy projekt DockerDemo i wybierz pozycję Dodaj > Dodaj obsługę **platformy Docker:** ![ Dodaj obsługę platformy Docker](media/docker-quickstart-3.png)

Visual Studio dla komputerów Mac automatycznie doda nowy projekt do rozwiązania o nazwie **docker-compose** i doda plik **Dockerfile** do istniejącego projektu.

![Wygenerowane pliki obsługi platformy Docker](media/docker-quickstart-4.png)

## <a name="dockerfile-overview"></a>Omówienie pliku Dockerfile

Plik Dockerfile to przepis na utworzenie końcowego obrazu platformy Docker. Opis poleceń znajdujących się w tym pliku można znaleźć w [dokumentacji pliku Dockerfile](https://docs.docker.com/engine/reference/builder/).

```
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/core/sdk:2.2-stretch AS build
WORKDIR /src
COPY DockerDemo/DockerDemo.csproj DockerDemo/
RUN dotnet restore "DockerDemo/DockerDemo.csproj"
COPY . .
WORKDIR "/src/DockerDemo"
RUN dotnet build "DockerDemo.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "DockerDemo.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "DockerDemo.dll"]
```

Poprzedni plik *Dockerfile* jest oparty na obrazie [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) i zawiera instrukcje modyfikowania obrazu podstawowego przez sbudowania projektu i dodania go do kontenera.

> [!NOTE]
> Domyślny plik Dockerfile utworzony przez Visual Studio dla komputerów Mac uwidacznia port 80 dla ruchu HTTP. Aby włączyć ruch HTTPS, dodaj `Expose 443` do pliku Dockerfile.

## <a name="debugging"></a>Debugowanie

Wybierz projekt `docker-compose` jako Projekt startowy i rozpocznij debugowanie (Uruchom >**Rozpocznij debugowanie).** Spowoduje to skompilowanie, wdrożenie i ASP.NET projektu w kontenerze.

> [!TIP]
> Przy pierwszym uruchomieniu po zainstalowaniu programu Docker Desktop podczas próby debugowania może zostać wyświetlony następujący błąd: `Cannot start service dockerdemo: Mounts denied`
>
> Dodaj `/usr/local/share/dotnet/sdk/NuGetFallbackFolder` do karty Udostępnianie plików w programie Docker Desktop:
>
> ![Dodawanie folderu NuGetFallbackFolder do udostępniania plików](media/docker-quickstart-5.png)

Po zakończeniu kompilacji aplikacja zostanie uruchomiona w przeglądarce Safari:

![Domyślny projekt platformy Docker uruchomiony w przeglądarce Safari](media/docker-quickstart-6.png)

Należy pamiętać, że kontener będzie nasłuchiwać na porcie, a `http://localhost:32768` ten port może się różnić.

Aby wyświetlić listę uruchomionych kontenerów, użyj `docker ps` polecenia w terminalu.

Zanotuj przekaźnik portów na poniższym zrzucie ekranu (w **obszarze PORTY**). Oznacza to, że kontener nasłuchuje na porcie, który widzieliśmy powyżej w przeglądarce Safari, i przekazuje żądania do wewnętrznego serwera internetowego na porcie 80 (zgodnie z definicją w pliku Dockerfile). Z perspektywy aplikacji nasłuchuje ona na porcie 80:

![Lista kontenerów platformy Docker](media/docker-quickstart-7.png)

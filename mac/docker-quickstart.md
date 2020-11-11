---
title: Wprowadzenie do platformy Docker
description: Dowiedz się, jak dodać platformę Docker do projektów w Visual Studio dla komputerów Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/09/2020
ms.topic: how-to
ms.openlocfilehash: e2bfb78369ae5da389820a318196dd7e9e13e897
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493078"
---
# <a name="get-started-with-docker-in-visual-studio-for-mac"></a>Wprowadzenie do platformy Docker w Visual Studio dla komputerów Mac

Dzięki Visual Studio dla komputerów Mac można łatwo kompilować, debugować i uruchamiać kontenery ASP.NET Core aplikacje i publikować je na platformie Azure.

## <a name="prerequisites"></a>Wymagania wstępne

* [Pulpit Docker](https://hub.docker.com/editions/community/docker-ce-desktop-mac)
* [Visual Studio dla komputerów Mac 2019](https://visualstudio.microsoft.com/vs/mac)

## <a name="installation-and-setup"></a>Instalacja i konfiguracja

W przypadku instalacji platformy Docker Przejrzyj informacje i postępuj zgodnie z informacjami w tematach [Instalowanie programu Docker Desktop dla komputerów Mac](https://docs.docker.com/docker-for-mac/install/).

## <a name="creating-an-aspnet-core-web-application-and-adding-docker-support"></a>Tworzenie aplikacji sieci Web ASP.NET Core i Dodawanie obsługi platformy Docker

1. Utwórz nowe rozwiązanie, przechodząc do **pliku > nowe rozwiązanie**.
1. W obszarze **aplikacja .NET Core >** wybierz szablon **aplikacja sieci Web** : ![ Utwórz nową aplikację ASP.NET](media/docker-quickstart-1.png)
1. Wybierz platformę docelową. W tym przykładzie będziemy używać platformy .NET Core 2,2: ![ Ustaw platformę docelową](media/docker-quickstart-2.png)
1. Wprowadź szczegóły projektu, takie jak nazwa ( _DockerDemo_ w tym przykładzie). Utworzony projekt zawiera wszystkie podstawowe informacje niezbędne do kompilowania i uruchamiania witryny sieci Web ASP.NET Core.
1. W oknie rozwiązanie kliknij prawym przyciskiem myszy projekt DockerDemo i wybierz polecenie **dodaj > Dodaj obsługę platformy Docker** : ![ Dodaj obsługę platformy Docker](media/docker-quickstart-3.png)

Visual Studio dla komputerów Mac automatycznie doda nowy projekt do rozwiązania o nazwie **Docker-Zredaguj** i Dodaj **pliku dockerfile** do istniejącego projektu.

![Wygenerowane pliki obsługi platformy Docker](media/docker-quickstart-4.png)

## <a name="dockerfile-overview"></a>Pliku dockerfile — Omówienie

Pliku dockerfile to przepis dotyczący tworzenia końcowego obrazu platformy Docker. Opis poleceń znajdujących się w tym pliku można znaleźć w [dokumentacji pliku Dockerfile](https://docs.docker.com/engine/reference/builder/).

```
FROM microsoft/dotnet:2.2-aspnetcore-runtime AS base
WORKDIR /app
EXPOSE 80

FROM microsoft/dotnet:2.2-sdk AS build
WORKDIR /src
COPY DockerDemo/DockerDemo.csproj DockerDemo/
RUN dotnet restore DockerDemo/DockerDemo.csproj
COPY . .
WORKDIR /src/DockerDemo
RUN dotnet build DockerDemo.csproj -c Release -o /app

FROM build AS publish
RUN dotnet publish DockerDemo.csproj -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "DockerDemo.dll"]
```

Poprzedni *pliku dockerfile* opiera się na obrazie [Microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) i zawiera instrukcje dotyczące modyfikowania obrazu podstawowego przez skompilowanie projektu i dodanie go do kontenera.

> [!NOTE]
> Domyślny pliku dockerfile utworzony przez Visual Studio dla komputerów Mac uwidacznia port 80 dla ruchu HTTP. Aby włączyć ruch HTTPS, Dodaj `Expose 443` do pliku dockerfile.

## <a name="debugging"></a>Debugowanie

Wybierz `docker-compose` projekt jako projekt startowy i Rozpocznij debugowanie ( **Uruchom > Rozpocznij debugowanie** ). Spowoduje to skompilowanie, wdrożenie i uruchomienie projektu ASP.NET w kontenerze.

> [!TIP]
> Podczas pierwszego uruchomienia po zainstalowaniu programu Docker Desktop podczas próby debugowania może zostać wyświetlony następujący błąd: `Cannot start service dockerdemo: Mounts denied`
>
> Dodaj `/usr/local/share/dotnet/sdk/NuGetFallbackFolder` do karty Udostępnianie plików w programie Docker Desktop:
>
> ![Dodawanie folderu NuGetFallbackFolder do udostępniania plików](media/docker-quickstart-5.png)

Po zakończeniu kompilacji aplikacja zostanie uruchomiona w przeglądarce Safari:

![Domyślny projekt platformy Docker uruchomiony w przeglądarce Safari](media/docker-quickstart-6.png)

Należy zauważyć, że kontener nasłuchuje na porcie, `http://localhost:32768` na przykład, a ten port może się różnić.

Aby wyświetlić listę uruchomionych kontenerów, użyj `docker ps` polecenia w terminalu.

Zwróć uwagę na przekaźnik portów na poniższym zrzucie ekranu (w obszarze **porty** ). Oznacza to, że kontener nasłuchuje na porcie znajdującym się w przeglądarce Safari powyżej i przekazuje żądania do wewnętrznego serwera WebServer przy użyciu portu 80 (zgodnie z definicją w pliku dockerfile). Z perspektywy aplikacji nasłuchuje na porcie 80:

![Lista kontenerów platformy Docker](media/docker-quickstart-7.png)

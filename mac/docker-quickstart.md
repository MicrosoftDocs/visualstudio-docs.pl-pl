---
title: Wprowadzenie do platformy Docker
description: Dowiedz się, jak dodać platformę Docker do projektów w programie Visual Studio dla komputerów Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 06/17/2019
ms.openlocfilehash: 2c6bdd7d0b2c939ed9db9be962e89d9ee423e1d4
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "74984117"
---
# <a name="get-started-with-docker-in-visual-studio-for-mac"></a>Wprowadzenie do platformy Docker w programie Visual Studio dla komputerów Mac

Za pomocą programu Visual Studio dla komputerów Mac można łatwo tworzyć, debugować i uruchamiać konteneryzowane aplikacje ASP.NET Core i publikować je na platformie Azure.

## <a name="prerequisites"></a>Wymagania wstępne

* [Pulpit platformy Docker](https://hub.docker.com/editions/community/docker-ce-desktop-mac)
* [Visual Studio 2019 dla komputerów Mac](https://visualstudio.microsoft.com/vs/mac)

## <a name="installation-and-setup"></a>Instalacja i konfiguracja

Aby uzyskać informacje dotyczące instalacji platformy Docker, zapoznaj się z informacjami zawartymi w [aplikacji Install Docker Desktop dla komputerów Mac](https://docs.docker.com/docker-for-mac/install/).

## <a name="creating-an-aspnet-core-web-application-and-adding-docker-support"></a>Tworzenie ASP.NET podstawowej aplikacji sieci Web i dodawanie obsługi platformy Docker

1. Utwórz nowe rozwiązanie, przechodząc do **file > new solution**.
1. W obszarze **.NET Core > App** wybierz ![szablon aplikacji sieci **Web:** Tworzenie nowej aplikacji ASP.NET](media/docker-quickstart-1.png)
1. Wybierz platformę docelową. W tym przykładzie użyjemy .NET Core ![2.2: Set target framework](media/docker-quickstart-2.png)
1. Wprowadź szczegóły projektu, takie jak nazwa (_DockerDemo_ w tym przykładzie). Utworzony projekt zawiera wszystkie podstawy potrzebne do utworzenia i uruchomienia witryny sieci Web ASP.NET Core.
1. W panelu rozwiązania kliknij prawym przyciskiem myszy projekt DockerDemo i wybierz polecenie **Dodaj > Dodaj obsługę platformy Docker:** ![Dodaj obsługę platformy docker](media/docker-quickstart-3.png)

Visual Studio dla komputerów Mac automatycznie doda nowy projekt do rozwiązania o nazwie **docker-compose** i dodać **Dockerfile** do istniejącego projektu.

![Wygenerowane pliki obsługi platformy docker](media/docker-quickstart-4.png)

## <a name="dockerfile-overview"></a>Omówienie pliku dockerfile

Dockerfile to przepis na tworzenie ostatecznego obrazu platformy Docker. Opis poleceń znajdujących się w tym pliku można znaleźć w [dokumentacji pliku Dockerfile](https://docs.docker.com/engine/reference/builder/).

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

Poprzedni plik *Dockerfile* jest oparty na obrazie [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) i zawiera instrukcje dotyczące modyfikowania obrazu podstawowego przez tworzenie projektu i dodawanie go do kontenera.

> [!NOTE]
> Domyślny plik Dockerfile utworzony przez program Visual Studio dla komputerów Mac udostępnia port 80 dla ruchu HTTP. Aby włączyć ruch HTTPS, dodaj `Expose 443` do pliku dockerfile.

## <a name="debugging"></a>Debugging

Wybierz `docker-compose` projekt jako projekt startowy i rozpocznij debugowanie (**Uruchom > Rozpocznij debugowanie**). Spowoduje to tworzenie, wdrażanie i uruchamianie projektu ASP.NET w kontenerze.

> [!TIP]
> Przy pierwszym uruchomieniu po zainstalowaniu pulpitu platformy Docker podczas próby debugowania może pojawić się następujący błąd:`Cannot start service dockerdemo: Mounts denied`
>
> Dodaj `/usr/local/share/dotnet/sdk/NuGetFallbackFolder` do karty Udostępnianie plików na pulpicie platformy Docker:
>
> ![Dodawanie folderu NuGetFallbackFolder do udostępniania plików](media/docker-quickstart-5.png)

Po zakończeniu kompilacji aplikacja zostanie uruchomiona w przeglądarce Safari:

![Domyślny projekt platformy Docker uruchomiony w przeglądarce Safari](media/docker-quickstart-6.png)

Należy zauważyć, że kontener będzie `http://localhost:32768` nasłuchiwanie na porcie, na przykład i ten port może się różnić.

Aby wyświetlić listę uruchomionych `docker ps` kontenerów, użyj polecenia w terminalu.

Zwróć uwagę na przekaźnik portu na poniższym zrzucie ekranu (w obszarze **PORTY).** Pokazuje to, że kontener nasłuchuje na porcie, który widzieliśmy w safari powyżej i przekazywania żądań do wewnętrznego serwera www na porcie 80 (zgodnie z definicją w Dockerfile). Z punktu widzenia aplikacji nasłuchuje na porcie 80:

![Lista kontenerów platformy Docker](media/docker-quickstart-7.png)

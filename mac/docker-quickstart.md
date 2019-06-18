---
title: Rozpoczynanie pracy z platformą Docker w programie Visual Studio dla komputerów Mac
description: Dowiedz się, jak dodawać platformy Docker do projektów w programie Visual Studio dla komputerów Mac
author: bytesguy
ms.author: adhartle
ms.date: 06/17/2019
ms.openlocfilehash: 8760bd048e23675c72fb7635587ca1c522b14259
ms.sourcegitcommit: fd5a5b057df3d733f5224c305096907989811f85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2019
ms.locfileid: "67196412"
---
# <a name="get-started-with-docker-in-visual-studio-for-mac"></a>Rozpoczynanie pracy z platformą Docker w programie Visual Studio dla komputerów Mac

Z programem Visual Studio dla komputerów Mac można łatwo tworzyć, debugować i uruchamianie konteneryzowanych platformy ASP.NET Core z aplikacji i opublikuj je na platformie Azure.

## <a name="prerequisites"></a>Wymagania wstępne

* [Pulpitu platformy docker](https://hub.docker.com/editions/community/docker-ce-desktop-mac)
* [Visual Studio for Mac 2019](https://visualstudio.microsoft.com/vs/mac)

## <a name="installation-and-setup"></a>Instalacja i konfiguracja

Dla instalacji platformy Docker, przejrzyj i wykonaj odpowiednie informacje zawiera temat [zainstalować pulpitu platformy Docker dla komputerów Mac](https://docs.docker.com/docker-for-mac/install/).

## <a name="creating-an-aspnet-core-web-application-and-adding-docker-support"></a>Tworzenie aplikacji sieci Web platformy ASP.NET Core i dodanie obsługi platformy Docker

1. Utwórz nowe rozwiązanie, przechodząc do **Plik > nowe rozwiązanie**.
1. W obszarze **platformy .NET Core > App** wybierz **aplikacji sieci Web** szablonu: ![Tworzenie nowej aplikacji platformy ASP.NET](media/docker-quickstart-1.png)
1. Wybierz platformę docelową. W tym przykładzie używamy platformy .NET Core 2.2: ![Platforma docelowa zestawu](media/docker-quickstart-2.png)
1. Wprowadź szczegóły projektu, takie jak nazwa (_DockerDemo_ w tym przykładzie). Utworzony projekt zawiera podstawowe, których potrzebujesz, aby skompilować i uruchomić witrynę sieci web platformy ASP.NET Core.
1. W konsoli rozwiązania, kliknij prawym przyciskiem myszy projekt DockerDemo, a następnie wybierz **Dodaj > Dodaj obsługę platformy Docker**: ![Dodaj obsługę platformy docker](media/docker-quickstart-3.png)

Visual Studio dla komputerów Mac automatycznie doda nowy projekt do rozwiązania o nazwie **narzędzia docker compose** i Dodaj **pliku Dockerfile** do istniejącego projektu.

![Pliki obsługi wygenerowanego platformy docker](media/docker-quickstart-4.png)

## <a name="dockerfile-overview"></a>Plik Dockerfile — omówienie

Plik Dockerfile stanowi przepisu tworzenia finalnego obrazu platformy Docker. Zapoznaj się [odwołanie do pliku Dockerfile](https://docs.docker.com/engine/reference/builder/) dla zrozumienia poleceń w nim.

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

Poprzedni *pliku Dockerfile* opiera się na [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) obrazu i zawiera instrukcje dotyczące modyfikowania obraz podstawowy, tworząc projekt i dodanie go do kontenera.

> [!NOTE]
> Domyślny plik Dockerfile utworzone przez program Visual Studio dla komputerów Mac uwidacznia Port 80 dla ruchu HTTP. Aby umożliwić ruch HTTPS, Dodaj `Expose 443` do pliku Dockerfile.

## <a name="debugging"></a>Debugowanie

Wybierz `docker-compose` projekt jako projekt startowy i Rozpocznij debugowanie (**Uruchom > Rozpocznij debugowanie**). Spowoduje to tworzenie, wdrażanie i uruchamianie projektu programu ASP.NET w kontenerze.

> [!TIP]
> Przy pierwszym uruchomieniu po zainstalowaniu platformy Docker komputerów może zostać wyświetlony następujący błąd podczas próby przeprowadzenia debugowania: `Cannot start service dockerdemo: Mounts denied`
> 
> Dodaj `/usr/local/share/dotnet/sdk/NuGetFallbackFolder` kartę udostępniania plików, na pulpicie platformy Docker:
>
> ![Dodawanie folderu NuGetFallbackFolder udostępniania plików](media/docker-quickstart-5.png)

Po zakończeniu kompilacji aplikacji zostanie uruchomiony w przeglądarce Safari:

![Domyślny projekt platformy Docker, uruchomiony w przeglądarce Safari](media/docker-quickstart-6.png)

Należy pamiętać, że kontener będzie nasłuchiwać portu `http://localhost:32768` dla przykładu, a ten port może się różnić.

Aby wyświetlić listę uruchomionych kontenerów, użyj `docker ps` polecenia w terminalu.

Należy pamiętać, przekazywania portu na poniższym zrzucie ekranu (w obszarze **porty**). Pokazuje to, czy kontener nasłuchuje na porcie, którą widzieliśmy w przeglądarkach Safari, powyżej i przekazywania żądań do wewnętrznego serwera sieci Web na porcie 80 (jak określono w pliku Dockerfile). Z perspektywy aplikacji nasłuchuje na porcie 80:

![Lista kontenerów platformy docker](media/docker-quickstart-7.png)

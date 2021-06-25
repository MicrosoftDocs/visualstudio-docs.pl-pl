---
title: Visual Studio Tools for Docker z ASP.NET
author: ghogen
description: Dowiedz się, jak używać narzędzi i Visual Studio 2019 Docker for Windows
ms.author: ghogen
ms.date: 02/22/2021
ms.prod: visual-studio-dev16
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: 35beb1bb67dbfe4d0d1707c499b605f6ff698956
ms.sourcegitcommit: 674d3fafa7c9e0cb0d1338027ef419a49c028c36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2021
ms.locfileid: "112908024"
---
Za pomocą usługi Visual Studio można łatwo kompilować, debugować i uruchamiać konteneryzowane aplikacje .NET, ASP.NET i ASP.NET Core oraz publikować je w usługach Azure Container Registry (ACR), Docker Hub, Azure App Service lub własnym rejestrze kontenerów. W tym artykule opublikujemy aplikację podstawową ASP.NET ACR.

## <a name="prerequisites"></a>Wymagania wstępne

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) r. z zainstalowanym obciążeniem **Tworzenie** aplikacji internetowych, Narzędzia platformy **Azure** i/lub tworzenie aplikacji dla wielu platform na platformie **.NET Core**
* .NET Core Development Tools for development with .NET Core [(Narzędzia deweloperskie na](https://dotnet.microsoft.com/download/dotnet-core/) platformie .NET Core do tworzenia aplikacji na platformie .NET Core)
* Aby opublikować w Azure Container Registry, subskrypcja platformy Azure. [Zarejestruj się, aby uzyskać bezpłatną wersję próbną.](https://azure.microsoft.com/free/dotnet/)

## <a name="installation-and-setup"></a>Instalacja i konfiguracja

W przypadku instalacji platformy Docker zapoznaj się najpierw z informacjami na stronie [Docker Desktop for Windows: What to know before you install (Program Docker Desktop dla](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install)systemu Windows: co należy wiedzieć przed zainstalowaniem programu ). Następnie zainstaluj program [Docker Desktop.](https://hub.docker.com/editions/community/docker-ce-desktop-windows)

## <a name="add-a-project-to-a-docker-container"></a>Dodawanie projektu do kontenera platformy Docker

1. Utwórz nowy projekt przy użyciu szablonu aplikacji internetowej **ASP.NET Core** lub jeśli chcesz użyć aplikacji .NET Framework zamiast .NET Core, wybierz pozycję ASP.NET Web **Application (.NET Framework)**.
1. Na **ekranie Dodatkowe informacje** upewnij się, że pole wyboru Włącz obsługę **platformy Docker** jest zaznaczone.

   ![Pole wyboru Włącz obsługę platformy Docker](../../media/container-tools/vs-2019/webapp-additional-information-31-docker.png)

   Zrzut ekranu przedstawia program .NET Core. Jeśli używasz usługi .NET Framework, wygląda to nieco inaczej.

1. Wybierz typ kontenera (Windows lub Linux), a następnie kliknij pozycję **Utwórz.**

## <a name="dockerfile-overview"></a>Plik Dockerfile — przegląd

Plik *Dockerfile*, przepis na utworzenie końcowego obrazu platformy Docker, jest tworzony w projekcie. Zapoznaj się [z odwołaniem do pliku Dockerfile,](https://docs.docker.com/engine/reference/builder/) aby uzyskać informacje na temat jego poleceń.

```dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
WORKDIR /src
COPY ["WebApplication1/WebApplication1.csproj", "WebApplication1/"]
RUN dotnet restore "WebApplication1/WebApplication1.csproj"
COPY . .
WORKDIR "/src/WebApplication1"
RUN dotnet build "WebApplication1.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "WebApplication1.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "WebApplication1.dll"]
```

Poprzedni plik *Dockerfile* jest oparty na obrazie [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) i zawiera instrukcje modyfikowania obrazu podstawowego przez sbudowania projektu i dodania go do kontenera. Jeśli używasz obrazu .NET Framework, obraz podstawowy będzie inny.

Jeśli w oknie dialogowym nowego projektu zostanie zaznaczone pole wyboru **Konfiguruj dla protokołu HTTPS**, plik *Dockerfile* uwidacznia dwa porty. Jeden port jest używany na potrzeby ruchu HTTP, a drugi na potrzeby protokołu HTTPS. Jeśli to pole wyboru nie zostanie zaznaczone, dla ruchu HTTP zostanie uwidoczniony pojedynczy port (80).

## <a name="debug"></a>Debugowanie

Wybierz pozycję **Docker** z listy rozwijanej debugowania na pasku narzędzi i rozpocznij debugowanie aplikacji. Może zostać wyświetlony komunikat z monitem o zaufanie do certyfikatu. wybierz zaufanie certyfikatowi, aby kontynuować.

Opcja **Narzędzia kontenerów** w **oknie Dane** wyjściowe pokazuje, jakie akcje są podejmowane. Pobieranie obrazu podstawowego może zająć trochę czasu, ale przy kolejnych przebiegach będzie znacznie szybsze.

>[!NOTE]
> Jeśli musisz zmienić porty na potrzeby debugowania, możesz to zrobić wlaunchSettings.js *pliku.* Zobacz [Container Launch Settings (Ustawienia uruchamiania kontenera).](../../container-launch-settings.md)

## <a name="containers-window"></a>Okno kontenerów

Jeśli masz już Visual Studio 2019 w wersji 16.4 lub  nowszej, możesz użyć okna Kontenery, aby wyświetlić uruchomione kontenery na maszynie oraz obrazy, które są dostępne.

Otwórz okno **Kontenery,** używając pola wyszukiwania w ide (naciśnij **klawisze Ctrl** Q, aby go użyć), wpisz i wybierz okno +  `container` **Kontenery** z listy.

Okno Kontenery **można** zainstalować w wygodnym miejscu, na przykład poniżej edytora, przenosząc je i korzystając z przewodników umieszczania okien.

W oknie znajdź kontener i za pomocą poszczególnych kart wyświetl zmienne środowiskowe, mapowania portów, dzienniki i system plików.

![Zrzut ekranu przedstawiający okno Kontenery](../../media/overview/vs-2019/container-tools-window.png)

Aby uzyskać więcej informacji, zobacz [Wyświetlanie i diagnozowanie kontenerów i obrazów w Visual Studio](../../view-and-diagnose-containers.md).

## <a name="publish-docker-images"></a>Publikowanie obrazów platformy Docker

Po zakończeniu cyklu tworzenia i debugowania aplikacji możesz utworzyć obraz produkcyjny aplikacji.

1. Zmień opcję listy rozwijanej konfiguracji na **Wydanie** i skompiluj aplikację.
1. Kliknij prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** i wybierz polecenie **Publikuj.**
1. W **oknie dialogowym** Publikowanie wybierz kartę **Container Registry Docker.**

   ![Zrzut ekranu przedstawiający okno dialogowe Publikowanie — wybierz pozycję Docker Container Registry](../../media/container-tools/vs-2019/docker-container-registry.png)

1. Wybierz **pozycję Create New Azure Container Registry (Utwórz Azure Container Registry).**

   ![Zrzut ekranu przedstawiający okno dialogowe Publikowanie — wybierz pozycję Utwórz nową Azure Container Registry](../../media/container-tools/vs-2019/select-existing-or-create-new-azure-container-registry.png)

1. Wypełnij żądane wartości w create **a new Azure Container Registry**.

    | Ustawienie      | Sugerowana wartość  | Opis                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **Prefiks DNS** | Nazwa unikatowa w skali globalnej | Nazwa, która jednoznacznie identyfikuje rejestr kontenerów. |
    | **Subskrypcja** | Wybierz subskrypcję | Subskrypcja platformy Azure, która ma być używana. |
    | **[Grupa zasobów](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Nazwa grupy zasobów, w której chcesz utworzyć rejestr kontenerów. Wybierz pozycję **Nowa**, aby utworzyć nową grupę zasobów.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Standardowa (Standard) | Warstwa usługi rejestru kontenerów  |
    | **Lokalizacja rejestru** | Lokalizacja w pobliżu | Wybierz lokalizację w [regionie w](https://azure.microsoft.com/regions/) pobliżu ciebie lub w pobliżu innych usług, które będą korzystać z rejestru kontenerów. |

    ![Visual Studio dialogowe Azure Container Registry tworzenia aplikacji][0]

1. Kliknij pozycję **Utwórz**. W **oknie** dialogowym Publikowanie zostanie teraz wyświetlone utworzony rejestr.

   ![Zrzut ekranu przedstawiający okno dialogowe publikowanie Azure Container Registry utworzone](../../media/container-tools/vs-2019/created-azure-container-registry.png)

1. Wybierz **pozycję** Zakończ, aby ukończyć proces publikowania obrazu kontenera w nowo utworzonym rejestrze na platformie Azure.

   ![Zrzut ekranu przedstawiający pomyślną publikację](../../media/container-tools/vs-2019/publish-succeeded.png)

## <a name="next-steps"></a>Następne kroki

Teraz możesz ściągnąć kontener z rejestru do dowolnego hosta, który może uruchamiać obrazy platformy Docker, na [Azure Container Instances](/azure/container-instances/container-instances-tutorial-deploy-app).

[0]:../../media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog-2019.png

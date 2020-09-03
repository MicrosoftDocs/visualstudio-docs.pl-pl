---
title: Visual Studio Tools for Docker z ASP.NET
author: ghogen
description: Dowiedz się, jak korzystać z narzędzi i Docker for Windows programu Visual Studio 2019
ms.author: ghogen
ms.date: 02/01/2019
ms.prod: visual-studio-dev16
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: fc549951e9c6b6d208c478f37126238e91f6f039
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "88186238"
---
Za pomocą programu Visual Studio można łatwo kompilować, debugować i uruchamiać kontenery .NET, ASP.NET i ASP.NET Core aplikacje oraz publikować je w Azure Container Registry (ACR), Docker Hub, Azure App Service lub własnym rejestrze kontenerów. W tym artykule opublikujemy aplikację ASP.NET Core w ACR.

## <a name="prerequisites"></a>Wymagania wstępne

* [Pulpit Docker](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Program Visual Studio 2019](https://visualstudio.microsoft.com/downloads) z zainstalowaną obsługą tworzenia aplikacji dla **sieci Web**, obciążeń **narzędzi platformy Azure** i/lub **oprogramowania .NET Core dla wielu platform**
* [Narzędzia programistyczne platformy .NET Core](https://dotnet.microsoft.com/download/dotnet-core/) do programowania przy użyciu platformy .NET Core
* Do opublikowania w usłudze Azure Container Registry, subskrypcji platformy Azure. [Zarejestruj się, aby skorzystać z bezpłatnej wersji próbnej](https://azure.microsoft.com/free/dotnet/).

## <a name="installation-and-setup"></a>Instalacja i konfiguracja

W przypadku instalacji platformy Docker najpierw przejrzyj informacje na [pulpicie Docker dla systemu Windows: co należy wiedzieć przed zainstalowaniem](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install)programu. Następnie zainstaluj program [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows).

## <a name="add-a-project-to-a-docker-container"></a>Dodawanie projektu do kontenera platformy Docker

1. Utwórz nowy projekt za pomocą szablonu **aplikacji sieci web ASP.NET Core** lub jeśli chcesz użyć .NET Framework zamiast programu .NET Core, wybierz pozycję **ASP.NET Web Application (.NET Framework)**.
1. Wybierz pozycję **aplikacja sieci Web**i upewnij się, że pole wyboru **Włącz obsługę platformy Docker** jest zaznaczone.

   ![Pole wyboru Włącz obsługę platformy Docker](../../media/container-tools/vs-2019/create-new-web-application.PNG)

   Zrzut ekranu przedstawia platformę .NET Core; Jeśli używasz .NET Framework, wygląda to nieco inaczej.

1. Wybierz odpowiedni typ kontenera (system Windows lub Linux), a następnie kliknij przycisk **Utwórz**.

## <a name="dockerfile-overview"></a>Plik Dockerfile — przegląd

*Pliku dockerfile*, przepis dotyczący tworzenia końcowego obrazu platformy Docker, jest tworzony w projekcie. Zapoznaj się z dokumentacją [pliku dockerfile](https://docs.docker.com/engine/reference/builder/) , aby zrozumieć polecenia w nim.:

```dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1-nanoserver-1903 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/core/sdk:3.1-nanoserver-1903 AS build
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

Poprzedni *pliku dockerfile* opiera się na obrazie [Microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) i zawiera instrukcje dotyczące modyfikowania obrazu podstawowego przez skompilowanie projektu i dodanie go do kontenera. Jeśli używasz .NET Framework, obraz podstawowy będzie różny.

Jeśli w oknie dialogowym nowego projektu zostanie zaznaczone pole wyboru **Konfiguruj dla protokołu HTTPS**, plik *Dockerfile* uwidacznia dwa porty. Jeden port jest używany na potrzeby ruchu HTTP, a drugi na potrzeby protokołu HTTPS. Jeśli to pole wyboru nie zostanie zaznaczone, dla ruchu HTTP zostanie uwidoczniony pojedynczy port (80).

## <a name="debug"></a>Debugowanie

Wybierz pozycję **Docker** z listy rozwijanej debugowania na pasku narzędzi i rozpocznij debugowanie aplikacji. Może pojawić się komunikat z monitem o zaufać certyfikatowi; Wybierz relację zaufania certyfikatu, aby kontynuować.

Opcja **Narzędzia kontenera** w oknie **danych wyjściowych** pokazuje, jakie akcje są wykonywane. Po raz pierwszy pobranie obrazu podstawowego może potrwać trochę czasu, ale jest to znacznie szybsze w kolejnych uruchomieniach.

>[!NOTE]
> Jeśli musisz zmienić porty na potrzeby debugowania, możesz to zrobić w *launchSettings.js* pliku. Zobacz [Ustawienia uruchamiania kontenera](../../container-launch-settings.md).

## <a name="containers-window"></a>Okno kontenerów

Jeśli masz program Visual Studio 2019 w wersji 16,4 lub nowszej, możesz użyć okna **kontenery** do wyświetlania uruchomionych kontenerów na swoim komputerze, a także dostępnych obrazów.

Otwórz okno **kontenery** przy użyciu pola wyszukiwania w IDE (naciśnij klawisz **Ctrl** + **Q** , aby go użyć), wpisz w `container` i wybierz z listy okno **kontenery** .

Możesz zainstalować okno **kontenery** w wygodnym miejscu, takim jak poniżej edytora, przenosząc je wokół i postępując zgodnie z przewodnikiem umieszczania okna.

W oknie Znajdź kontener i przejdź na każdą kartę, aby wyświetlić zmienne środowiskowe, mapowania portów, dzienniki i system plików.

![Zrzut ekranu okna kontenerów](../../media/overview/vs-2019/container-tools-window.png)

Aby uzyskać więcej informacji, zobacz [Wyświetlanie i diagnozowanie kontenerów i obrazów w programie Visual Studio](../../view-and-diagnose-containers.md).

## <a name="publish-docker-images"></a>Publikowanie obrazów platformy Docker

Po zakończeniu cyklu opracowywania i debugowania aplikacji można utworzyć obraz produkcyjny aplikacji.

1. Zmień opcję listy rozwijanej konfiguracji na **Wydanie** i skompiluj aplikację.
1. Kliknij prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** i wybierz polecenie **Publikuj**.
1. W oknie dialogowym **Publikowanie** wybierz kartę **Docker Container Registry** .

   ![Zrzut ekranu przedstawiający okno dialogowe publikowania — wybierz Container Registry Docker](../../media/container-tools/vs-2019/docker-container-registry.png)

1. Wybierz pozycję **Utwórz nowe Azure Container Registry**.

   ![Zrzut ekranu przedstawiający okno dialogowe publikowania — wybierz pozycję Utwórz nowy Azure Container Registry](../../media/container-tools/vs-2019/select-existing-or-create-new-azure-container-registry.png)

1. Wypełnij odpowiednie wartości w polu **Utwórz nową Azure Container Registry**.

    | Ustawienie      | Sugerowana wartość  | Opis                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **Prefiks DNS** | Nazwa unikatowa w skali globalnej | Nazwa, która jednoznacznie identyfikuje rejestr kontenerów. |
    | **Subskrypcja** | Wybierz subskrypcję | Subskrypcja platformy Azure, która ma być używana. |
    | **[Grupa zasobów](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Nazwa grupy zasobów, w której ma zostać utworzony rejestr kontenerów. Wybierz pozycję **Nowa**, aby utworzyć nową grupę zasobów.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Standard | Warstwa usług w rejestrze kontenerów  |
    | **Lokalizacja rejestru** | Lokalizacja blisko Ciebie | Wybierz lokalizację w [regionie](https://azure.microsoft.com/regions/) blisko siebie lub w najbliższej innej usłudze, która będzie korzystać z rejestru kontenerów. |

    ![Okno dialogowe tworzenia Azure Container Registry programu Visual Studio][0]

1. Kliknij przycisk **Utwórz**. W oknie dialogowym **publikowania** zostanie wyświetlony utworzony rejestr.

   ![Zrzut ekranu przedstawiający okno dialogowe publikowania z utworzonymi Azure Container Registry](../../media/container-tools/vs-2019/created-azure-container-registry.png)

1. Wybierz przycisk **Zakończ** , aby zakończyć proces publikowania obrazu kontenera do nowo utworzonego rejestru na platformie Azure.

   ![Zrzut ekranu przedstawiający pomyślne publikowanie](../../media/container-tools/vs-2019/publish-succeeded.png)

## <a name="next-steps"></a>Następne kroki

Teraz można ściągnąć kontener z rejestru do dowolnego hosta, który może uruchamiać obrazy platformy Docker, na przykład [Azure Container Instances](/azure/container-instances/container-instances-tutorial-deploy-app).

[0]:../../media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog-2019.png

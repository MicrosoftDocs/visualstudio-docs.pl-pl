---
title: Visual Studio Tools for Docker z ASP.NET Core
author: ghogen
description: Dowiedz się, jak korzystać z narzędzi i Docker for Windows programu Visual Studio 2019
ms.author: ghogen
ms.date: 02/01/2019
ms.prod: visual-studio-dev16
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: 7eae92f7c65208dfeda9cd19e14eaa627e12a22a
ms.sourcegitcommit: bbff780cda82bb64862d77fe8f407f1803beb876
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2019
ms.locfileid: "74142210"
---
Program Visual Studio umożliwia łatwe tworzenie, debugowanie i uruchamianie kontenerów ASP.NET Core aplikacji oraz publikowanie ich w usłudze Azure Container Registry (ACR), Docker Hub, Azure App Service lub własnym rejestrze kontenerów. W tym artykule opublikujemy ACR.

## <a name="prerequisites"></a>Wymagania wstępne

* [Pulpit Docker](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Program Visual Studio 2019](https://visualstudio.microsoft.com/downloads) z zainstalowaną obsługą tworzenia aplikacji dla **sieci Web**, obciążeń **narzędzi platformy Azure** i/lub **oprogramowania .NET Core dla wielu platform**
* [Narzędzia programistyczne programu .net core 2,2](https://dotnet.microsoft.com/download/dotnet-core/2.2) do programowania przy użyciu programu .net Core 2,2
* Do opublikowania w usłudze Azure Container Registry, subskrypcji platformy Azure. [Zarejestruj się, aby skorzystać z bezpłatnej wersji próbnej](https://azure.microsoft.com/offers/ms-azr-0044p/).

## <a name="installation-and-setup"></a>Instalacja i konfiguracja

W przypadku instalacji platformy Docker najpierw przejrzyj informacje na [pulpicie Docker dla systemu Windows: co należy wiedzieć przed zainstalowaniem](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install)programu. Następnie zainstaluj program [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows).

## <a name="add-a-project-to-a-docker-container"></a>Dodawanie projektu do kontenera platformy Docker

1. Utwórz nowy projekt za pomocą szablonu **aplikacji sieci Web ASP.NET Core** .
1. Wybierz pozycję **aplikacja sieci Web**i upewnij się, że pole wyboru **Włącz obsługę platformy Docker** jest zaznaczone.

   ![Włącz obsługę platformy Docker — pole wyboru](../../media/container-tools/vs-2019/create-new-web-application.PNG)

1. Wybierz odpowiedni typ kontenera (system Windows lub Linux), a następnie kliknij przycisk **Utwórz**.

## <a name="dockerfile-overview"></a>Pliku dockerfile — Omówienie

*Pliku dockerfile*, przepis dotyczący tworzenia końcowego obrazu platformy Docker, jest tworzony w projekcie. Zapoznaj się z dokumentacją [pliku dockerfile](https://docs.docker.com/engine/reference/builder/) , aby zrozumieć polecenia w nim.:

```
FROM microsoft/dotnet:2.2-aspnetcore-runtime-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM microsoft/dotnet:2.2-sdk-stretch AS build
WORKDIR /src
COPY ["HelloDockerTools/HelloDockerTools.csproj", "HelloDockerTools/"]
RUN dotnet restore "HelloDockerTools/HelloDockerTools.csproj"
COPY . .
WORKDIR "/src/HelloDockerTools"
RUN dotnet build "HelloDockerTools.csproj" -c Release -o /app

FROM build AS publish
RUN dotnet publish "HelloDockerTools.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "HelloDockerTools.dll"]
```

Poprzedni *pliku dockerfile* opiera się na obrazie [Microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) i zawiera instrukcje dotyczące modyfikowania obrazu podstawowego przez skompilowanie projektu i dodanie go do kontenera.

Gdy pole wyboru Konfiguruj nowy projekt **dla protokołu HTTPS** jest zaznaczone, *pliku dockerfile* uwidacznia dwa porty. Jeden port jest używany na potrzeby ruchu HTTP; drugi port jest używany w przypadku protokołu HTTPS. Jeśli pole wyboru nie jest zaznaczone, pojedynczy port (80) zostanie uwidoczniony dla ruchu HTTP.

## <a name="debug"></a>Debugowanie

Wybierz pozycję **Docker** z listy rozwijanej Debuguj na pasku narzędzi i Rozpocznij debugowanie aplikacji. Może pojawić się komunikat z monitem o zaufać certyfikatowi; Wybierz relację zaufania certyfikatu, aby kontynuować.

Opcja **Narzędzia kontenera** w oknie **danych wyjściowych** pokazuje, jakie akcje są wykonywane.

Otwórz **konsolę Menedżera pakietów** (PMC) z menu **Narzędzia**, > Menedżer pakietów NuGet, **konsola Menedżera pakietów**.

Utworzony obraz platformy Docker aplikacji jest otagowany jako *dev*. Obraz jest oparty na tagu *2,2-aspnetcore-Runtime* obrazu podstawowego *Microsoft/dotnet* . Uruchom `docker images` polecenie w oknie **konsola Menedżera pakietów** (PMC). Wyświetlane są obrazy na komputerze:

```console
REPOSITORY        TAG                     IMAGE ID      CREATED         SIZE
hellodockertools  dev                     d72ce0f1dfe7  30 seconds ago  255MB
microsoft/dotnet  2.2-aspnetcore-runtime  fcc3887985bb  6 days ago      255MB
```

> [!NOTE]
> Obraz **deweloperski** nie zawiera plików binarnych aplikacji i innych zawartości, ponieważ konfiguracje **debugowania** używają funkcji instalacji woluminu, aby zapewnić iteracyjne edytowanie i debugowanie. Aby utworzyć obraz produkcyjny zawierający całą zawartość, użyj konfiguracji **wydania** .

Uruchom `docker ps` polecenie w kryterium PMC. Zauważ, że aplikacja jest uruchomiona przy użyciu kontenera:

```console
CONTAINER ID        IMAGE                  COMMAND               CREATED             STATUS              PORTS                                           NAMES
cf5d2ef5f19a        hellodockertools:dev   "tail -f /dev/null"   2 minutes ago       Up 2 minutes        0.0.0.0:52036->80/tcp, 0.0.0.0:44342->443/tcp   priceless_cartwright
```

## <a name="containers-window"></a>Okno kontenerów

Jeśli masz program Visual Studio 2019 w wersji 16,4 lub nowszej, możesz użyć okna **kontenery** do wyświetlania uruchomionych kontenerów na swoim komputerze, a także dostępnych obrazów.

Otwórz okno **kontenery** przy użyciu pola wyszukiwania w IDE (naciśnij klawisz **Ctrl**+**Q** , aby go użyć), wpisz `container`i wybierz z listy okno **kontenery** .

Możesz zainstalować okno **kontenery** w wygodnym miejscu, takim jak poniżej edytora, przenosząc je wokół i postępując zgodnie z przewodnikiem umieszczania okna.

W oknie Znajdź kontener i przejdź na każdą kartę, aby wyświetlić zmienne środowiskowe, mapowania portów, dzienniki i system plików.

Aby uzyskać więcej informacji, zobacz [Wyświetlanie i diagnozowanie kontenerów i obrazów w programie Visual Studio](../../view-and-diagnose-containers.md).

## <a name="publish-docker-images"></a>Publikowanie obrazów platformy Docker

Po zakończeniu cyklu opracowywania i debugowania aplikacji można utworzyć obraz produkcyjny aplikacji.

1. Zmień listę rozwijaną konfiguracji, aby **zwolnić** i skompilować aplikację.
1. Kliknij prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** i wybierz polecenie **Publikuj**.
1. W oknie dialogowym Publikowanie elementu docelowego wybierz kartę **Container Registry** .
1. Wybierz pozycję **Utwórz nowe Azure Container Registry** a następnie kliknij przycisk **Publikuj**.
1. Wypełnij odpowiednie wartości w polu **Utwórz nową Azure Container Registry**.

    | Ustawienie      | Sugerowana wartość  | Opis                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **Prefiks DNS** | Globalnie unikatowa nazwa | Nazwa, która jednoznacznie identyfikuje rejestr kontenerów. |
    | **Ramach** | Wybierz subskrypcję | Subskrypcja platformy Azure do użycia. |
    | **[Grupa zasobów](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Nazwa grupy zasobów, w której ma zostać utworzony rejestr kontenerów. Wybierz pozycję **Nowy** , aby utworzyć nową grupę zasobów.|
    | **[Magazyn](https://docs.microsoft.com/azure/container-registry/container-registry-skus)** | Standardowa | Warstwa usług w rejestrze kontenerów  |
    | **Lokalizacja rejestru** | Lokalizacja blisko Ciebie | Wybierz lokalizację w [regionie](https://azure.microsoft.com/regions/) blisko siebie lub w najbliższej innej usłudze, która będzie korzystać z rejestru kontenerów. |

    ![Okno dialogowe tworzenia Azure Container Registry programu Visual Studio][0]

1. Kliknij przycisk **Utwórz**

   ![Zrzut ekranu przedstawiający pomyślne publikowanie](../../media/container-tools/publish-succeeded.png)

## <a name="next-steps"></a>Następne kroki

Teraz można ściągnąć kontener z rejestru do dowolnego hosta, który może uruchamiać obrazy platformy Docker, na przykład [Azure Container Instances](/azure/container-instances/container-instances-tutorial-deploy-app).

[0]:../../media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog-2019.png

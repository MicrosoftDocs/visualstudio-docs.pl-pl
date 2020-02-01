---
title: Narzędzia kontenerów programu Visual Studio z platformą ASP.NET Core
author: ghogen
description: Dowiedz się, jak korzystać z narzędzi i Docker for Windows programu Visual Studio 2017
ms.author: ghogen
ms.date: 02/01/2019
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: ae6548892010035564bf29a8eda25b736db97d2a
ms.sourcegitcommit: 4be64917e4224fd1fb27ba527465fca422bc7d62
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2020
ms.locfileid: "76922974"
---
Program Visual Studio umożliwia łatwe tworzenie, debugowanie i uruchamianie kontenerów ASP.NET Core aplikacji oraz publikowanie ich w usłudze Azure Container Registry (ACR), Docker Hub, Azure App Service lub własnym rejestrze kontenerów. W tym artykule opublikujemy ACR.

## <a name="prerequisites"></a>Wymagania wstępne

* [Pulpit Docker](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Program Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) z zainstalowaną obsługą tworzenia aplikacji dla **sieci Web**, obciążeń **narzędzi platformy Azure** i/lub **oprogramowania .NET Core dla wielu platform**
* Do opublikowania w usłudze Azure Container Registry, subskrypcji platformy Azure. [Zamów bezpłatną wersję próbną](https://azure.microsoft.com/offers/ms-azr-0044p/).

## <a name="installation-and-setup"></a>Instalacja i konfiguracja

W przypadku instalacji platformy Docker najpierw przejrzyj informacje na [pulpicie Docker dla systemu Windows: co należy wiedzieć przed zainstalowaniem](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install)programu. Następnie zainstaluj program [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows).

## <a name="add-a-project-to-a-docker-container"></a>Dodawanie projektu do kontenera platformy Docker

1. Z menu programu Visual Studio wybierz pozycję **plik > nowy > projekt**.
1. W sekcji **Szablony** okna dialogowego **Nowy projekt** wybierz pozycję  **C# Visual > Web**.
1. Wybierz **ASP.NET Core aplikację sieci Web** lub jeśli chcesz użyć .NET Framework zamiast programu .NET Core, wybierz pozycję **aplikacja sieci Web ASP.NET**.
1. Nadaj nowej aplikacji nazwę (lub wybierz ją domyślną), a następnie kliknij **przycisk OK**.
1. Wybierz **aplikacji sieci Web**.
1. Zaznacz pole wyboru **Włącz obsługę platformy Docker** .

   ![Pole wyboru Włącz obsługę platformy Docker](../../media/container-tools/enable-docker-support.PNG)

   Zrzut ekranu przedstawia platformę .NET Core; Jeśli używasz .NET Framework, wygląda to nieco inaczej.

1. Wybierz odpowiedni typ kontenera (system Windows lub Linux), a następnie kliknij przycisk **OK**.

## <a name="dockerfile-overview"></a>Plik Dockerfile — przegląd

*Pliku dockerfile*, przepis dotyczący tworzenia końcowego obrazu platformy Docker, jest tworzony w projekcie. Zapoznaj się z dokumentacją [pliku dockerfile](https://docs.docker.com/engine/reference/builder/) , aby zrozumieć polecenia w nim.:

```
FROM microsoft/dotnet:2.1-aspnetcore-runtime AS base
WORKDIR /app
EXPOSE 59518
EXPOSE 44364

FROM microsoft/dotnet:2.1-sdk AS build
WORKDIR /src
COPY HelloDockerTools/HelloDockerTools.csproj HelloDockerTools/
RUN dotnet restore HelloDockerTools/HelloDockerTools.csproj
COPY . .
WORKDIR /src/HelloDockerTools
RUN dotnet build HelloDockerTools.csproj -c Release -o /app

FROM build AS publish
RUN dotnet publish HelloDockerTools.csproj -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "HelloDockerTools.dll"]
```

Poprzedni *pliku dockerfile* opiera się na obrazie [Microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) i zawiera instrukcje dotyczące modyfikowania obrazu podstawowego przez skompilowanie projektu i dodanie go do kontenera. Jeśli używasz .NET Framework, obraz podstawowy będzie różny.

Jeśli w oknie dialogowym nowego projektu zostanie zaznaczone pole wyboru **Konfiguruj dla protokołu HTTPS**, plik *Dockerfile* uwidacznia dwa porty. Jeden port jest używany na potrzeby ruchu HTTP, a drugi na potrzeby protokołu HTTPS. Jeśli to pole wyboru nie zostanie zaznaczone, dla ruchu HTTP zostanie uwidoczniony pojedynczy port (80).

## <a name="debug"></a>Debugowanie

Wybierz pozycję **Docker** z listy rozwijanej debugowania na pasku narzędzi i rozpocznij debugowanie aplikacji. Może pojawić się komunikat z monitem o zaufać certyfikatowi; Wybierz relację zaufania certyfikatu, aby kontynuować.

Okno **dane wyjściowe** pokazuje, jakie akcje są wykonywane.

Otwórz **konsolę Menedżera pakietów** (PMC) z menu **Narzędzia**, > Menedżer pakietów NuGet, **konsola Menedżera pakietów**.

Wynikowy obraz platformy Docker aplikacji jest oznaczony tagiem *dev*. Obraz bazuje na tagu *2.1-aspnetcore-runtime* obrazu podstawowego *microsoft/dotnet*. Uruchom polecenie `docker images` w oknie **konsoli menedżera pakietów** (PMC). Na komputerze są wyświetlane następujące obrazy:

```console
REPOSITORY        TAG                     IMAGE ID      CREATED         SIZE
hellodockertools  dev                     d72ce0f1dfe7  30 seconds ago  255MB
microsoft/dotnet  2.1-aspnetcore-runtime  fcc3887985bb  6 days ago      255MB
```

> [!NOTE]
> Obraz **deweloperski** nie zawiera plików binarnych aplikacji i innych zawartości, ponieważ konfiguracje **debugowania** używają funkcji instalacji woluminu, aby zapewnić iteracyjne edytowanie i debugowanie. Aby utworzyć obraz produkcyjny zawierający całą zawartość, użyj konfiguracji **wydania** .

Uruchom polecenie `docker ps` w konsoli PMC. Zauważ, że aplikacja działa przy użyciu kontenera:

```console
CONTAINER ID        IMAGE                  COMMAND                   CREATED             STATUS              PORTS                   NAMES
baf9a678c88d        hellodockertools:dev   "C:\\remote_debugge..."   21 seconds ago      Up 19 seconds       0.0.0.0:37630->80/tcp   dockercompose4642749010770307127_hellodockertools_1
```

## <a name="publish-docker-images"></a>Publikowanie obrazów platformy Docker

Po zakończeniu cyklu opracowywania i debugowania aplikacji można utworzyć obraz produkcyjny aplikacji.

1. Zmień opcję listy rozwijanej konfiguracji na **Wydanie** i skompiluj aplikację.
1. Kliknij prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** i wybierz polecenie **Publikuj**.
1. W oknie dialogowym Publikowanie elementu docelowego wybierz kartę **Container Registry** .
1. Wybierz pozycję **Utwórz nowe Azure Container Registry** a następnie kliknij przycisk **Publikuj**.
1. Wypełnij odpowiednie wartości w polu **Utwórz nową Azure Container Registry**.

    | Ustawienie      | Sugerowana wartość  | Opis                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **Prefiks DNS** | Globalnie unikatowa nazwa | Nazwa, która jednoznacznie identyfikuje rejestr kontenerów. |
    | **Subskrypcja** | Wybierz subskrypcję | Subskrypcja platformy Azure do użycia. |
    | **[Grupa zasobów](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Nazwa grupy zasobów, w której ma zostać utworzony rejestr kontenerów. Wybierz pozycję **Nowy** , aby utworzyć nową grupę zasobów.|
    | **[Magazyn](/azure/container-registry/container-registry-skus)** | Standardowy | Warstwa usług w rejestrze kontenerów  |
    | **Lokalizacja rejestru** | Lokalizacja blisko Ciebie | Wybierz lokalizację w [regionie](https://azure.microsoft.com/regions/) blisko siebie lub w najbliższej innej usłudze, która będzie korzystać z rejestru kontenerów. |

    ![Okno dialogowe tworzenia Azure Container Registry programu Visual Studio][0]

1. Kliknij przycisk **Utwórz**.

## <a name="next-steps"></a>Następne kroki

Teraz można ściągnąć kontener z rejestru do dowolnego hosta, który może uruchamiać obrazy platformy Docker, na przykład [Azure Container Instances](/azure/container-instances/container-instances-tutorial-deploy-app).

[0]:../../media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png

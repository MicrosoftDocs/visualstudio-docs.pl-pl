---
title: Narzędzia kontenerów programu Visual Studio z platformą ASP.NET Core
author: ghogen
description: Dowiedz się, jak używać Visual Studio 2017 i Docker for Windows
ms.author: ghogen
ms.date: 02/01/2019
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: 53bf0d559d9737494567b079621879b97a403a95
ms.sourcegitcommit: fc05a763b59e212c86350d117a1900a1f2686ec8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2021
ms.locfileid: "111564908"
---
Za Visual Studio można łatwo kompilować, debugować i uruchamiać konteneryzowane aplikacje ASP.NET Core oraz publikować je w usługach Azure Container Registry (ACR), Docker Hub, Azure App Service lub własnym rejestrze kontenerów. W tym artykule opublikujemy dane w uciece ACR.

## <a name="prerequisites"></a>Wymagania wstępne

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) z zainstalowanym obciążeniem **Tworzenie** aplikacji internetowych, Narzędzia platformy **Azure** i/lub tworzenie aplikacji dla wielu platform na platformie **.NET Core**
* Aby opublikować w Azure Container Registry, subskrypcja platformy Azure. [Zarejestruj się, aby uzyskać bezpłatną wersję próbną.](https://azure.microsoft.com/free/dotnet/)

## <a name="installation-and-setup"></a>Instalacja i konfiguracja

W przypadku instalacji platformy Docker zapoznaj się najpierw z informacjami na stronie [Docker Desktop for Windows: What to know before you install (Program Docker Desktop dla](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install)systemu Windows: co należy wiedzieć przed zainstalowaniem programu ). Następnie zainstaluj program [Docker Desktop.](https://hub.docker.com/editions/community/docker-ce-desktop-windows)

## <a name="add-a-project-to-a-docker-container"></a>Dodawanie projektu do kontenera platformy Docker

1. W menu Visual Studio pozycję **File > New > Project**(Nowy > projektu).
1. W sekcji **Szablony** okna dialogowego **Nowy** projekt wybierz pozycję **Visual C# > Web.**
1. Wybierz **ASP.NET Web Application Core** lub jeśli chcesz użyć aplikacji internetowej .NET Framework zamiast .NET Core, wybierz pozycję ASP.NET Web **Application.**
1. Nadaj nowej aplikacji nazwę (lub wybierz wartość domyślną), a następnie wybierz przycisk **OK.**
1. Wybierz **pozycję Aplikacja internetowa.**
1. Zaznacz pole **wyboru Włącz obsługę platformy Docker.**

   ![Pole wyboru Włącz obsługę platformy Docker](../../media/container-tools/enable-docker-support.PNG)

   Zrzut ekranu przedstawia program .NET Core. Jeśli używasz usługi .NET Framework, wygląda to nieco inaczej.

1. Wybierz typ kontenera (Windows lub Linux), a następnie kliknij przycisk **OK.**

## <a name="dockerfile-overview"></a>Plik Dockerfile — przegląd

Plik *Dockerfile*, przepis na utworzenie końcowego obrazu platformy Docker, jest tworzony w projekcie. Zapoznaj się [z odwołaniem do pliku Dockerfile,](https://docs.docker.com/engine/reference/builder/) aby uzyskać informacje na temat jego poleceń.

```
FROM mcr.microsoft.com/dotnet/aspnet:2.1 AS base
WORKDIR /app
EXPOSE 59518
EXPOSE 44364

FROM mcr.microsoft.com/dotnet/sdk:2.1 AS build
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

Poprzedni plik *Dockerfile* jest oparty na obrazie [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) i zawiera instrukcje modyfikowania obrazu podstawowego przez sbudowania projektu i dodania go do kontenera. Jeśli używasz obrazu .NET Framework, obraz podstawowy będzie inny.

Jeśli w oknie dialogowym nowego projektu zostanie zaznaczone pole wyboru **Konfiguruj dla protokołu HTTPS**, plik *Dockerfile* uwidacznia dwa porty. Jeden port jest używany na potrzeby ruchu HTTP, a drugi na potrzeby protokołu HTTPS. Jeśli to pole wyboru nie zostanie zaznaczone, dla ruchu HTTP zostanie uwidoczniony pojedynczy port (80).

## <a name="debug"></a>Debugowanie

Wybierz pozycję **Docker** z listy rozwijanej debugowania na pasku narzędzi i rozpocznij debugowanie aplikacji. Może zostać wyświetlony komunikat z monitem o zaufanie do certyfikatu. wybierz zaufanie certyfikatowi, aby kontynuować.

Okno **Dane** wyjściowe pokazuje, jakie akcje są podejmowane.

Otwórz **konsolę Menedżer pakietów** (PMC) z **menu** Narzędzia> NuGet Menedżer pakietów Menedżer pakietów **Console**.

Wynikowy obraz platformy Docker aplikacji jest oznaczony tagiem *dev*. Obraz bazuje na tagu *2.1-aspnetcore-runtime* obrazu podstawowego *microsoft/dotnet*. Uruchom polecenie `docker images` w oknie **konsoli menedżera pakietów** (PMC). Na komputerze są wyświetlane następujące obrazy:

```console
REPOSITORY        TAG                     IMAGE ID      CREATED         SIZE
hellodockertools  dev                     d72ce0f1dfe7  30 seconds ago  255MB
microsoft/dotnet  2.1-aspnetcore-runtime  fcc3887985bb  6 days ago      255MB
```

> [!NOTE]
> Obraz **dewelopera** nie zawiera plików binarnych aplikacji  ani innej zawartości, ponieważ konfiguracje debugowania używają instalowanie woluminów w celu zapewnienia iteracyjnych możliwości edytowania i debugowania. Aby utworzyć obraz produkcyjny zawierający całą zawartość, użyj **konfiguracji wydania.**

Uruchom polecenie `docker ps` w konsoli PMC. Zauważ, że aplikacja działa przy użyciu kontenera:

```console
CONTAINER ID        IMAGE                  COMMAND                   CREATED             STATUS              PORTS                   NAMES
baf9a678c88d        hellodockertools:dev   "C:\\remote_debugge..."   21 seconds ago      Up 19 seconds       0.0.0.0:37630->80/tcp   dockercompose4642749010770307127_hellodockertools_1
```

## <a name="publish-docker-images"></a>Publikowanie obrazów platformy Docker

Po zakończeniu cyklu tworzenia i debugowania aplikacji możesz utworzyć obraz produkcyjny aplikacji.

1. Zmień opcję listy rozwijanej konfiguracji na **Wydanie** i skompiluj aplikację.
1. Kliknij prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** i wybierz polecenie **Publikuj.**
1. W oknie dialogowym publish target (Miejsce docelowe **publikacji) wybierz Container Registry** oknie dialogowym.
1. Wybierz **pozycję Utwórz nowy Azure Container Registry** a następnie kliknij pozycję **Opublikuj.**
1. Wypełnij żądane wartości w create **a new Azure Container Registry**.

    | Ustawienie      | Sugerowana wartość  | Opis                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **Prefiks DNS** | Nazwa unikatowa w skali globalnej | Nazwa, która jednoznacznie identyfikuje rejestr kontenerów. |
    | **Subskrypcja** | Wybierz subskrypcję | Subskrypcja platformy Azure, która ma być używana. |
    | **[Grupa zasobów](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Nazwa grupy zasobów, w której chcesz utworzyć rejestr kontenerów. Wybierz pozycję **Nowa**, aby utworzyć nową grupę zasobów.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Standardowa (Standard) | Warstwa usługi rejestru kontenerów  |
    | **Lokalizacja rejestru** | Lokalizacja w pobliżu | Wybierz lokalizację w [regionie w](https://azure.microsoft.com/regions/) pobliżu ciebie lub w pobliżu innych usług, które będą korzystać z rejestru kontenerów. |

    ![Visual Studio dialogowe Azure Container Registry tworzenia aplikacji][0]

1. Kliknij pozycję **Utwórz**

## <a name="next-steps"></a>Następne kroki

Teraz możesz ściągnąć kontener z rejestru do dowolnego hosta, który może uruchamiać obrazy platformy Docker, na [przykład Azure Container Instances](/azure/container-instances/container-instances-tutorial-deploy-app).

[0]:../../media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png

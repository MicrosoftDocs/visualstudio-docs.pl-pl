---
title: Narzędzia kontenera programu Visual Studio z ASP.NET Core i React.js
titleSuffix: ''
ms.custom: SEO-VS-2020
author: ghogen
description: Dowiedz się, jak utworzyć kontenery z reagują na aplikacje za pomocą narzędzi kontenera programu Visual Studio i platformy Docker
ms.author: ghogen
ms.date: 05/14/2020
ms.technology: vs-azure
ms.topic: quickstart
ms.openlocfilehash: 783d7a116dbdf530008c3271d38d15f7db3c3c98
ms.sourcegitcommit: 503f82045b9236d457b79712cd71405d4a62a53d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2020
ms.locfileid: "91750761"
---
# <a name="quickstart-use-docker-with-a-react-single-page-app-in-visual-studio"></a>Szybki Start: korzystanie z platformy Docker z aplikacją jednostronicową do reagowania w programie Visual Studio

Za pomocą programu Visual Studio można łatwo kompilować, debugować i uruchamiać kontenery ASP.NET Core aplikacje, w tym za pomocą skryptów JavaScript po stronie klienta, takich jak React.js aplikacji jednostronicowej, i publikować je w Azure Container Registry (ACR), Docker Hub, Azure App Service lub własnym rejestrze kontenerów. W tym artykule opublikujemy ACR.

## <a name="prerequisites"></a>Wymagania wstępne

::: moniker range="vs-2017"
* [Pulpit Docker](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Program Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) z zainstalowaną obsługą tworzenia aplikacji dla **sieci Web**, obciążeń **narzędzi platformy Azure** i/lub **oprogramowania .NET Core dla wielu platform**
* Do opublikowania w usłudze Azure Container Registry, subskrypcji platformy Azure. [Zarejestruj się, aby skorzystać z bezpłatnej wersji próbnej](https://azure.microsoft.com/offers/ms-azr-0044p/).
* [Node.js](https://nodejs.org/en/download/)
* W przypadku kontenerów systemu Windows 10 w wersji 1903 lub nowszej w celu używania obrazów platformy Docker, do których odwołuje się ten artykuł.
::: moniker-end
::: moniker range=">=vs-2019"
* [Pulpit Docker](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Program Visual Studio 2019](https://visualstudio.microsoft.com/downloads) z zainstalowaną obsługą tworzenia aplikacji dla **sieci Web**, obciążeń **narzędzi platformy Azure** i/lub **oprogramowania .NET Core dla wielu platform**
* [Narzędzia programistyczne programu .net core 3,1](https://dotnet.microsoft.com/download/dotnet-core/3.1) do programowania przy użyciu programu .net Core 3,1.
* Do opublikowania w usłudze Azure Container Registry, subskrypcji platformy Azure. [Zarejestruj się, aby skorzystać z bezpłatnej wersji próbnej](https://azure.microsoft.com/offers/ms-azr-0044p/).
* [Node.js](https://nodejs.org/en/download/)
* W przypadku kontenerów systemu Windows 10 w wersji 1903 lub nowszej w celu używania obrazów platformy Docker, do których odwołuje się ten artykuł.
::: moniker-end

## <a name="installation-and-setup"></a>Instalacja i konfiguracja

W przypadku instalacji platformy Docker najpierw przejrzyj informacje na [pulpicie Docker dla systemu Windows: co należy wiedzieć przed zainstalowaniem](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install)programu. Następnie zainstaluj program [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows).

## <a name="create-a-project-and-add-docker-support"></a>Tworzenie projektu i Dodawanie obsługi platformy Docker

::: moniker range="vs-2017"
1. Utwórz nowy projekt za pomocą szablonu **aplikacji sieci Web ASP.NET Core** .
1. Wybierz **React.js**. Nie możesz wybrać opcji **Włącz obsługę platformy Docker**, ale nie martw się, możesz dodać tę obsługę po utworzeniu projektu.

   ![Zrzut ekranu przedstawiający nowy projekt React.js](media/container-tools-react/vs-2017/new-react-project.png)

1. Kliknij prawym przyciskiem myszy węzeł projektu, a następnie wybierz polecenie **Dodaj** > **obsługę platformy Docker** , aby dodać pliku dockerfile do projektu.

   ![Dodawanie obsługi platformy Docker](media/container-tools-react/vs-2017/add-docker-support.png)

1. Wybierz typ kontenera, a następnie kliknij przycisk **OK**.
::: moniker-end
::: moniker range=">=vs-2019"
1. Utwórz nowy projekt za pomocą szablonu **aplikacji sieci Web ASP.NET Core** .
1. Wybierz pozycję **React.js**, a następnie kliknij pozycję **Utwórz**. Nie możesz wybrać opcji **Włącz obsługę platformy Docker**, ale nie martw się, możesz dodać tę obsługę później.

   ![Zrzut ekranu przedstawiający nowy projekt React.js](media/container-tools-react/vs-2019/new-react-project.png)

1. Kliknij prawym przyciskiem myszy węzeł projektu, a następnie wybierz polecenie **Dodaj** > **obsługę platformy Docker** , aby dodać pliku dockerfile do projektu.

   ![Dodawanie obsługi platformy Docker](media/container-tools-react/vs-2017/add-docker-support.png)

1. Wybierz typ kontenera.
::: moniker-end

Następny krok jest różny w zależności od tego, czy używane są kontenery systemu Linux, czy kontenery Windows.

## <a name="modify-the-dockerfile-linux-containers"></a>Modyfikowanie pliku dockerfile (kontenery systemu Linux)

*Pliku dockerfile*, przepis dotyczący tworzenia końcowego obrazu platformy Docker, jest tworzony w projekcie. Opis poleceń znajdujących się w tym pliku można znaleźć w [dokumentacji pliku Dockerfile](https://docs.docker.com/engine/reference/builder/).

Otwórz *pliku dockerfile* w projekcie i Dodaj następujące wiersze, aby zainstalować Node.js 10. x w kontenerze. Pamiętaj, aby dodać te wiersze w pierwszej sekcji, aby dodać instalację Menedżera pakietów węzła *npm.exe* do obrazu podstawowego, a także w `build` sekcji.

```Dockerfile
RUN curl -sL https://deb.nodesource.com/setup_10.x |  bash -
RUN apt-get install -y nodejs
```

*Pliku dockerfile* powinien teraz wyglądać następująco:

```Dockerfile
#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.

FROM mcr.microsoft.com/dotnet/core/aspnet:3.1-buster-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443
RUN curl -sL https://deb.nodesource.com/setup_10.x |  bash -
RUN apt-get install -y nodejs

FROM mcr.microsoft.com/dotnet/core/sdk:3.1-buster AS build
RUN curl -sL https://deb.nodesource.com/setup_10.x |  bash -
RUN apt-get install -y nodejs
WORKDIR /src
COPY ["WebApplication-ReactSPA/WebApplication-ReactSPA.csproj", "WebApplication-ReactSPA/"]
RUN dotnet restore "WebApplication-ReactSPA/WebApplication-ReactSPA.csproj"
COPY . .
WORKDIR "/src/WebApplication-ReactSPA"
RUN dotnet build "WebApplication-ReactSPA.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "WebApplication-ReactSPA.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "WebApplication-ReactSPA.dll"]
```

Poprzedni *pliku dockerfile* opiera się na obrazie [Microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) i zawiera instrukcje dotyczące modyfikowania obrazu podstawowego przez skompilowanie projektu i dodanie go do kontenera.

Jeśli w oknie dialogowym nowego projektu zostanie zaznaczone pole wyboru **Konfiguruj dla protokołu HTTPS**, plik *Dockerfile* uwidacznia dwa porty. Jeden port jest używany na potrzeby ruchu HTTP, a drugi na potrzeby protokołu HTTPS. Jeśli to pole wyboru nie zostanie zaznaczone, dla ruchu HTTP zostanie uwidoczniony pojedynczy port (80).

## <a name="modify-the-dockerfile-windows-containers"></a>Modyfikowanie pliku dockerfile (kontenery systemu Windows)

Otwórz plik projektu przez dwukrotne kliknięcie węzła projektu i zaktualizowanie pliku projektu (*. csproj) przez dodanie następującej właściwości jako elementu podrzędnego `<PropertyGroup>` elementu:

   ```xml
    <DockerfileFastModeStage>base</DockerfileFastModeStage>
   ```

Zaktualizuj pliku dockerfile przez dodanie następujących wierszy. Spowoduje to skopiowanie węzła i npm do kontenera.

   1. Dodaj ``# escape=` `` do pierwszego wiersza pliku dockerfile
   1. Dodaj następujące wiersze przed `FROM … base`

      ```Dockerfile
      FROM mcr.microsoft.com/powershell:nanoserver-1903 AS downloadnodejs
      SHELL ["pwsh", "-Command", "$ErrorActionPreference = 'Stop';$ProgressPreference='silentlyContinue';"]
      RUN Invoke-WebRequest -OutFile nodejs.zip -UseBasicParsing "https://nodejs.org/dist/v10.16.3/node-v10.16.3-win-x64.zip"; `
      Expand-Archive nodejs.zip -DestinationPath C:\; `
      Rename-Item "C:\node-v10.16.3-win-x64" c:\nodejs
      ```

   1. Dodaj następujący wiersz przed i po `FROM … build`

      ```Dockerfile
      COPY --from=downloadnodejs C:\nodejs\ C:\Windows\system32\
      ```

   1. Pełna pliku dockerfile powinna teraz wyglądać następująco:

      ```Dockerfile
      # escape=`
      #Depending on the operating system of the host machines(s) that will build or run the containers, the image specified in the FROM statement may need to be changed.
      #For more information, please see https://aka.ms/containercompat
      FROM mcr.microsoft.com/powershell:nanoserver-1903 AS downloadnodejs
      RUN mkdir -p C:\nodejsfolder
      WORKDIR C:\nodejsfolder
      SHELL ["pwsh", "-Command", "$ErrorActionPreference = 'Stop';$ProgressPreference='silentlyContinue';"]
      RUN Invoke-WebRequest -OutFile nodejs.zip -UseBasicParsing "https://nodejs.org/dist/v10.16.3/node-v10.16.3-win-x64.zip"; `
      Expand-Archive nodejs.zip -DestinationPath C:\; `
      Rename-Item "C:\node-v10.16.3-win-x64" c:\nodejs

      FROM mcr.microsoft.com/dotnet/core/aspnet:3.1-nanoserver-1903 AS base
      WORKDIR /app
      EXPOSE 80
      EXPOSE 443
      COPY --from=downloadnodejs C:\nodejs\ C:\Windows\system32\

      FROM mcr.microsoft.com/dotnet/core/sdk:3.1-nanoserver-1903 AS build
      COPY --from=downloadnodejs C:\nodejs\ C:\Windows\system32\
      WORKDIR /src
      COPY ["WebApplication7/WebApplication37.csproj", "WebApplication37/"]
      RUN dotnet restore "WebApplication7/WebApplication7.csproj"
      COPY . .
      WORKDIR "/src/WebApplication37"
      RUN dotnet build "WebApplication37.csproj" -c Release -o /app/build

      FROM build AS publish
      RUN dotnet publish "WebApplication37.csproj" -c Release -o /app/publish

      FROM base AS final
      WORKDIR /app
      COPY --from=publish /app/publish .
      ENTRYPOINT ["dotnet", "WebApplication37.dll"]
      ```

   1. Zaktualizuj plik dockerignore przez usunięcie `**/bin` .

## <a name="debug"></a>Debugowanie

Wybierz pozycję **Docker** z listy rozwijanej debugowania na pasku narzędzi i rozpocznij debugowanie aplikacji. Może pojawić się komunikat z monitem o zaufać certyfikatowi; Wybierz relację zaufania certyfikatu, aby kontynuować.  Przy pierwszym kompilowaniu program Docker pobiera obrazy podstawowe, dzięki czemu może trwać nieco dłużej.

Opcja **Narzędzia kontenera** w oknie **danych wyjściowych** pokazuje, jakie akcje są wykonywane. Należy zapoznać się z procedurami instalacji skojarzonymi z *npm.exe*.

W przeglądarce zostanie wyświetlona strona główna aplikacji.

::: moniker range="vs-2017"
   ![Zrzut ekranu przedstawiający uruchomioną aplikację](media/container-tools-react/vs-2017/running-app.png)
::: moniker-end
::: moniker range=">=vs-2019"
   ![Zrzut ekranu przedstawiający uruchomioną aplikację](media/container-tools-react/vs-2019/running-app.png)
::: moniker-end

Przejdź do strony *licznika* i przetestuj kod po stronie klienta dla licznika, klikając przycisk **przyrostu** .

Otwórz **konsolę Menedżera pakietów** (PMC) z menu **Narzędzia** ,> Menedżer pakietów NuGet, **konsola Menedżera pakietów**.

Wynikowy obraz platformy Docker aplikacji jest oznaczony tagiem *dev*. Obraz jest oparty na tagu *2,2-aspnetcore-Runtime* obrazu podstawowego *Microsoft/dotnet* . Uruchom polecenie `docker images` w oknie **konsoli menedżera pakietów** (PMC). Na komputerze są wyświetlane następujące obrazy:

```console
REPOSITORY        TAG                     IMAGE ID      CREATED         SIZE
webapplication37  dev                     d72ce0f1dfe7  30 seconds ago  255MB
microsoft/dotnet  2.2-aspnetcore-runtime  fcc3887985bb  6 days ago      255MB
```

> [!NOTE]
> Obraz **deweloperski** nie zawiera plików binarnych aplikacji i innych zawartości, ponieważ konfiguracje **debugowania** używają funkcji instalacji woluminu, aby zapewnić iteracyjne edytowanie i debugowanie. Aby utworzyć obraz produkcyjny zawierający całą zawartość, użyj konfiguracji **wydania** .

Uruchom polecenie `docker ps` w konsoli PMC. Zauważ, że aplikacja działa przy użyciu kontenera:

```console
CONTAINER ID        IMAGE                  COMMAND               CREATED             STATUS              PORTS                                           NAMES
cf5d2ef5f19a        webapplication37:dev   "tail -f /dev/null"   2 minutes ago       Up 2 minutes        0.0.0.0:52036->80/tcp, 0.0.0.0:44342->443/tcp   priceless_cartwright
```

## <a name="publish-docker-images"></a>Publikowanie obrazów platformy Docker

Po zakończeniu cyklu opracowywania i debugowania aplikacji można utworzyć obraz produkcyjny aplikacji.

:::moniker range="vs-2017"

1. Zmień opcję listy rozwijanej konfiguracji na **Wydanie** i skompiluj aplikację.
1. Kliknij prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** i wybierz polecenie **Publikuj**.
1. W oknie dialogowym Publikowanie elementu docelowego wybierz pozycję **Container Registry**.
1. Wybierz pozycję **Utwórz nowe Azure Container Registry** a następnie kliknij przycisk **Publikuj**.
1. Wypełnij odpowiednie wartości w polu **Utwórz nową Azure Container Registry**.

    | Ustawienie      | Sugerowana wartość  | Opis                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **Prefiks DNS** | Nazwa unikatowa w skali globalnej | Nazwa, która jednoznacznie identyfikuje rejestr kontenerów. |
    | **Subskrypcja** | Wybierz subskrypcję | Subskrypcja platformy Azure, która ma być używana. |
    | **[Grupa zasobów](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Nazwa grupy zasobów, w której ma zostać utworzony rejestr kontenerów. Wybierz pozycję **Nowa**, aby utworzyć nową grupę zasobów.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Standardowa | Warstwa usług w rejestrze kontenerów  |
    | **Lokalizacja rejestru** | Lokalizacja blisko Ciebie | Wybierz lokalizację w [regionie](https://azure.microsoft.com/regions/) blisko siebie lub w najbliższej innej usłudze, która będzie korzystać z rejestru kontenerów. |

    ![Okno dialogowe tworzenia Azure Container Registry programu Visual Studio](media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png)

1. Wybierz przycisk **Utwórz**.

   ![Zrzut ekranu przedstawiający pomyślne publikowanie](media/container-tools/publish-succeeded.png)
:::moniker-end

:::moniker range=">=vs-2019"

1. Zmień opcję listy rozwijanej konfiguracji na **Wydanie** i skompiluj aplikację.
1. Kliknij prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** i wybierz polecenie **Publikuj**.
1. W oknie dialogowym Publikowanie elementu docelowego wybierz pozycję **docker Container Registry**.

   ![Wybierz Container Registry platformy Docker](media/container-tools-react/vs-2019/publish-dialog1.png)

1. Następnie wybierz **Azure Container Registry**.

   ![Wybierz Azure Container Registry](media/container-tools-react/vs-2019/publish-dialog-acr.png)

1. Wybierz pozycję **Utwórz nowy Azure Container Registry**.
1. Wypełnij odpowiednie wartości na ekranie **Utwórz nowy Azure Container Registry** .

    | Ustawienie      | Sugerowana wartość  | Opis                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **Prefiks DNS** | Nazwa unikatowa w skali globalnej | Nazwa, która jednoznacznie identyfikuje rejestr kontenerów. |
    | **Subskrypcja** | Wybierz subskrypcję | Subskrypcja platformy Azure, która ma być używana. |
    | **[Grupa zasobów](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Nazwa grupy zasobów, w której ma zostać utworzony rejestr kontenerów. Wybierz pozycję **Nowa**, aby utworzyć nową grupę zasobów.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Standardowa | Warstwa usług w rejestrze kontenerów  |
    | **Lokalizacja rejestru** | Lokalizacja blisko Ciebie | Wybierz lokalizację w [regionie](https://azure.microsoft.com/regions/) blisko siebie lub w najbliższej innej usłudze, która będzie korzystać z rejestru kontenerów. |

    ![Okno dialogowe tworzenia Azure Container Registry programu Visual Studio](media/container-tools-react/vs-2019/azure-container-registry-details.png)

1. Wybierz pozycję **Utwórz**, a następnie wybierz pozycję **Zakończ**.

   ![Wybierz lub Utwórz nowy ACR](media/container-tools-react/vs-2019/publish-dialog2.png)

   Po zakończeniu procesu publikowania można przejrzeć ustawienia publikowania i edytować je, jeśli jest to konieczne, lub opublikować obraz ponownie przy użyciu przycisku **Publikuj** .

   ![Zrzut ekranu przedstawiający pomyślne publikowanie](media/container-tools-react/vs-2019/publish-finished.png)

   Aby ponownie rozpocząć korzystanie z okna dialogowego **publikowania** , Usuń profil publikowania przy użyciu linku **Usuń** na tej stronie, a następnie ponownie wybierz pozycję **Opublikuj** .
:::moniker-end

## <a name="next-steps"></a>Następne kroki

Teraz można ściągnąć kontener z rejestru do dowolnego hosta, który może uruchamiać obrazy platformy Docker, na przykład [Azure Container Instances](/azure/container-instances/container-instances-tutorial-deploy-app).

## <a name="additional-resources"></a>Dodatkowe zasoby

* [Opracowywanie kontenerów w programie Visual Studio](./index.yml)
* [Rozwiązywanie problemów związanych z opracowywaniem zwartości w programie Visual Studio przy użyciu platformy Docker](troubleshooting-docker-errors.md)
* [Repozytorium usługi GitHub dla narzędzi kontenerów programu Visual Studio](https://github.com/Microsoft/DockerTools)


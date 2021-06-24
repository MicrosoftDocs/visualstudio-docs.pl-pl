---
title: Visual Studio Container Tools z ASP.NET Core i React.js
titleSuffix: ''
ms.custom: SEO-VS-2020
author: ghogen
description: Dowiedz się, jak utworzyć konteneryzowana aplikację REACT SPA przy użyciu Visual Studio Container Tools i platformy Docker
ms.author: ghogen
ms.date: 02/21/2021
ms.technology: vs-azure
ms.topic: quickstart
ms.openlocfilehash: 177a44f8af73226d4352c4a48c23c65eadc3e608
ms.sourcegitcommit: 674d3fafa7c9e0cb0d1338027ef419a49c028c36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2021
ms.locfileid: "112602024"
---
# <a name="quickstart-use-docker-with-a-react-single-page-app-in-visual-studio"></a>Szybki start: używanie platformy Docker z jednostronicową aplikacją platformy React w Visual Studio

Za pomocą usługi Visual Studio można łatwo kompilować, debugować i uruchamiać konteneryzowane aplikacje ASP.NET Core, w tym aplikacje z kodem JavaScript po stronie klienta, takie jak jednostronicowa aplikacja usługi React.js, i publikować je w usługach Azure Container Registry (ACR), Docker Hub, Azure App Service lub własnym rejestrze kontenerów. W tym artykule opublikujemy w uciece ACR.

## <a name="prerequisites"></a>Wymagania wstępne

::: moniker range="vs-2017"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) r. z zainstalowanym obciążeniem Tworzenie aplikacji **internetowych,** Narzędzia platformy **Azure** i/lub tworzeniem aplikacji dla wielu platform na platformie **.NET Core**
* Aby opublikować w Azure Container Registry, subskrypcja platformy Azure. [Zarejestruj się, aby uzyskać bezpłatną wersję próbną.](https://azure.microsoft.com/offers/ms-azr-0044p/)
* [Node.js](https://nodejs.org/en/download/)
* W przypadku kontenerów systemu Windows Windows 10 w wersji 1809 lub nowszej, aby użyć obrazów platformy Docker, do których odwołuje się ten artykuł.
::: moniker-end
::: moniker range=">=vs-2019"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) r. z zainstalowanym obciążeniem Tworzenie aplikacji **internetowych,** Narzędzia platformy **Azure** i/lub tworzeniem aplikacji dla wielu platform na platformie **.NET Core**
* [.NET Core 3.1 Development Tools](https://dotnet.microsoft.com/download/dotnet-core/3.1) for development with .NET Core 3.1 (Narzędzia programskie dla platform .NET Core 3.1 na platformie .NET Core 3.1).
* Aby opublikować w Azure Container Registry, subskrypcja platformy Azure. [Zarejestruj się, aby uzyskać bezpłatną wersję próbną.](https://azure.microsoft.com/offers/ms-azr-0044p/)
* [Node.js](https://nodejs.org/en/download/)
* W przypadku kontenerów systemu Windows Windows 10 w wersji 1809 lub nowszej, aby użyć obrazów platformy Docker, do których odwołuje się ten artykuł.
::: moniker-end

## <a name="installation-and-setup"></a>Instalacja i konfiguracja

W przypadku instalacji platformy Docker najpierw zapoznaj się z informacjami na stronie [Docker Desktop for Windows: What to know before you install (Docker Desktop for Windows:](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install)Co należy wiedzieć przed zainstalowaniem programu ). Następnie zainstaluj program [Docker Desktop.](https://hub.docker.com/editions/community/docker-ce-desktop-windows)

## <a name="create-a-project-and-add-docker-support"></a>Tworzenie projektu i dodawanie obsługi platformy Docker

::: moniker range="vs-2017"
1. Utwórz nowy projekt przy użyciu **szablonu ASP.NET Core Web Application.**
1. Wybierz **React.js**. Nie można wybrać opcji Włącz obsługę **platformy Docker,** ale nie martw się— możesz dodać tę obsługę po utworzeniu projektu.

   ![Zrzut ekranu przedstawiający nowy React.js projekt](media/container-tools-react/vs-2017/new-react-project.png)

1. Kliknij prawym przyciskiem myszy węzeł projektu, a następnie wybierz pozycję **Dodaj** obsługę platformy > **Docker,** aby dodać plik Dockerfile do projektu.

   ![Dodawanie obsługi platformy Docker](media/container-tools-react/vs-2017/add-docker-support.png)

1. Wybierz typ kontenera, a następnie kliknij przycisk **OK.**
::: moniker-end

::: moniker range=">=vs-2019"

1. Utwórz nowy projekt przy użyciu szablonu **ASP.NET Core React.js** core.

   ![Zrzut ekranu przedstawiający tworzenie nowego React.js projektowego](media/container-tools-react/vs-2019/create-reactjs-project.png)

1. Na **ekranie Dodatkowe informacje** nie można wybrać opcji Włącz obsługę platformy **Docker,** ale nie martw się— możesz dodać tę obsługę później.

   ![Zrzut ekranu przedstawiający tworzenie nowego React.js projektu — dodatkowe informacje](media/container-tools-react/vs-2019/new-react-project-additional-information.png)

1. Kliknij prawym przyciskiem myszy węzeł projektu, a następnie wybierz pozycję **Dodaj** obsługę platformy > **Docker,** aby dodać plik Dockerfile do projektu.

   ![Dodawanie obsługi platformy Docker](media/container-tools-react/vs-2017/add-docker-support.png)

1. Wybierz typ kontenera.
::: moniker-end

Następny krok różni się w zależności od tego, czy używasz kontenerów systemu Linux, czy kontenerów systemu Windows.

## <a name="modify-the-dockerfile-linux-containers"></a>Modyfikowanie pliku Dockerfile (kontenery systemu Linux)

Plik *Dockerfile*, czyli przepis na utworzenie końcowego obrazu platformy Docker, jest tworzony w projekcie. Opis poleceń znajdujących się w tym pliku można znaleźć w [dokumentacji pliku Dockerfile](https://docs.docker.com/engine/reference/builder/).

Otwórz plik *Dockerfile* w projekcie i dodaj następujące wiersze, aby Node.js 10.x w kontenerze. Pamiętaj, aby dodać te wiersze w pierwszej sekcji, aby dodać instalację menedżera pakietów *node* npm.exedo obrazu podstawowego, a także w `build` sekcji .

```Dockerfile
RUN curl -sL https://deb.nodesource.com/setup_10.x |  bash -
RUN apt-get install -y nodejs
```

Plik *Dockerfile* powinien teraz wyglądać podobnie do tego:

```Dockerfile
#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.

FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443
RUN curl -sL https://deb.nodesource.com/setup_10.x |  bash -
RUN apt-get install -y nodejs

FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
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

Poprzedni plik *Dockerfile* jest oparty na obrazie mcr.microsoft.com/dotnet/core/aspnet [i](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) zawiera instrukcje modyfikowania obrazu podstawowego przez sbudowania projektu i dodania go do kontenera.

Jeśli w oknie dialogowym nowego projektu zostanie zaznaczone pole wyboru **Konfiguruj dla protokołu HTTPS**, plik *Dockerfile* uwidacznia dwa porty. Jeden port jest używany na potrzeby ruchu HTTP, a drugi na potrzeby protokołu HTTPS. Jeśli to pole wyboru nie zostanie zaznaczone, dla ruchu HTTP zostanie uwidoczniony pojedynczy port (80).

## <a name="modify-the-dockerfile-windows-containers"></a>Modyfikowanie pliku Dockerfile (kontenerów systemu Windows)

Otwórz plik projektu, klikając dwukrotnie węzeł projektu i aktualizuj plik projektu (*.csproj), dodając następującą właściwość jako element `<PropertyGroup>` podrzędny elementu :

   ```xml
    <DockerfileFastModeStage>base</DockerfileFastModeStage>
   ```

Zaktualizuj plik Dockerfile, dodając następujące wiersze. Spowoduje to skopiowanie węzła i pliku npm do kontenera.

   1. Dodawanie ``# escape=` `` do pierwszego wiersza pliku Dockerfile
   1. Dodaj następujące wiersze przed `FROM … base`

      ```Dockerfile
      FROM mcr.microsoft.com/powershell AS downloadnodejs
      SHELL ["pwsh", "-Command", "$ErrorActionPreference = 'Stop';$ProgressPreference='silentlyContinue';"]
      RUN Invoke-WebRequest -OutFile nodejs.zip -UseBasicParsing "https://nodejs.org/dist/v10.16.3/node-v10.16.3-win-x64.zip"; `
      Expand-Archive nodejs.zip -DestinationPath C:\; `
      Rename-Item "C:\node-v10.16.3-win-x64" c:\nodejs
      ```

   2. Dodaj następujący wiersz przed i po `FROM … build`

      ```Dockerfile
      COPY --from=downloadnodejs C:\nodejs\ C:\Windows\system32\
      ```

   3. Kompletny plik Dockerfile powinien teraz wyglądać podobnie do tego:

      ```Dockerfile
      # escape=`
      #Depending on the operating system of the host machines(s) that will build or run the containers, the image specified in the FROM statement may need to be changed.
      #For more information, please see https://aka.ms/containercompat
      FROM mcr.microsoft.com/powershell AS downloadnodejs
      RUN mkdir -p C:\nodejsfolder
      WORKDIR C:\nodejsfolder
      SHELL ["pwsh", "-Command", "$ErrorActionPreference = 'Stop';$ProgressPreference='silentlyContinue';"]
      RUN Invoke-WebRequest -OutFile nodejs.zip -UseBasicParsing "https://nodejs.org/dist/v10.16.3/node-v10.16.3-win-x64.zip"; `
      Expand-Archive nodejs.zip -DestinationPath C:\; `
      Rename-Item "C:\node-v10.16.3-win-x64" c:\nodejs

      FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS base
      WORKDIR /app
      EXPOSE 80
      EXPOSE 443
      COPY --from=downloadnodejs C:\nodejs\ C:\Windows\system32\

      FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
      COPY --from=downloadnodejs C:\nodejs\ C:\Windows\system32\
      WORKDIR /src
      COPY ["WebApplicationReact1/WebApplicationReact1.csproj", "WebApplicationReact1/"]
      RUN dotnet restore "WebApplicationReact1/WebApplicationReact1.csproj"
      COPY . .
      WORKDIR "/src/WebApplicationReact1"
      RUN dotnet build "WebApplicationReact1.csproj" -c Release -o /app/build

      FROM build AS publish
      RUN dotnet publish "WebApplicationReact1.csproj" -c Release -o /app/publish

      FROM base AS final
      WORKDIR /app
      COPY --from=publish /app/publish .
      ENTRYPOINT ["dotnet", "WebApplicationReact1.dll"]
      ```

   4. Zaktualizuj plik dockerignore, usuwając plik `**/bin` .

## <a name="debug"></a>Debugowanie

Wybierz pozycję **Docker** z listy rozwijanej debugowania na pasku narzędzi i rozpocznij debugowanie aplikacji. Może zostać wyświetlony komunikat z monitem o zaufanie do certyfikatu; Wybierz ufanie certyfikatowi, aby kontynuować.  Podczas pierwszej kompilacji docker pobiera obrazy podstawowe, więc może to potrwać nieco dłużej.

Opcja **Narzędzia kontenera** w **oknie Dane** wyjściowe pokazuje, jakie akcje są podejmowane. Powinny zostać opisane kroki instalacji skojarzone z *npm.exe*.

W przeglądarce zostanie pokazana strona główna aplikacji.

::: moniker range="vs-2017"
   ![Zrzut ekranu przedstawiający uruchamianie aplikacji](media/container-tools-react/vs-2017/running-app.png)
::: moniker-end
::: moniker range=">=vs-2019"
   ![Zrzut ekranu przedstawiający uruchamianie aplikacji](media/container-tools-react/vs-2019/running-app.png)
::: moniker-end

Spróbuj przejść do strony *Licznik* i przetestować kod licznika po stronie klienta, klikając przycisk **Inkrementacja.**

Otwórz **konsolę Menedżer pakietów** (PMC) z menu **Tools**> NuGet Menedżer pakietów, **Menedżer pakietów Console**.

Wynikowy obraz platformy Docker aplikacji jest oznaczony tagiem *dev*. Obraz jest oparty na *tagu 3.1* obrazu podstawowego *dotnet/core/aspnet.* Uruchom polecenie `docker images` w oknie **konsoli menedżera pakietów** (PMC). Na komputerze są wyświetlane następujące obrazy:

```console
REPOSITORY                             TAG                 IMAGE ID            CREATED             SIZE
webapplicationreact1                   dev                 09be6ec2405d        2 hours ago         352MB
mcr.microsoft.com/dotnet/core/aspnet   3.1                 e3559b2d50bb        10 days ago         207MB
```

> [!NOTE]
> Obraz **dewelopera** nie zawiera plików binarnych aplikacji  ani innej zawartości, ponieważ konfiguracje debugowania używają instalowanie woluminu w celu zapewnienia iteracyjnych możliwości edytowania i debugowania. Aby utworzyć obraz produkcyjny zawierający całą zawartość, użyj **konfiguracji Wydania.**

Uruchom polecenie `docker ps` w konsoli PMC. Zauważ, że aplikacja działa przy użyciu kontenera:

```console
CONTAINER ID        IMAGE                      COMMAND               CREATED             STATUS              PORTS                                           NAMES
56d1b1008c89        webapplicationreact1:dev   "tail -f /dev/null"   2 hours ago         Up 2 hours          0.0.0.0:32771->80/tcp, 0.0.0.0:32770->443/tcp   WebApplication-React1
```

## <a name="publish-docker-images"></a>Publikowanie obrazów platformy Docker

Po zakończeniu cyklu opracowywania i debugowania aplikacji możesz utworzyć obraz produkcyjny aplikacji.

:::moniker range="vs-2017"

1. Zmień opcję listy rozwijanej konfiguracji na **Wydanie** i skompiluj aplikację.
1. Kliknij prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** i wybierz polecenie **Publikuj.**
1. W oknie dialogowym obiektu docelowego publikowania wybierz **pozycję Container Registry**.
1. Wybierz **pozycję Utwórz nowy Azure Container Registry** a następnie kliknij pozycję **Opublikuj.**
1. Wypełnij żądane wartości w **edycie Create a new Azure Container Registry (Tworzenie nowego Azure Container Registry**.

    | Ustawienie      | Sugerowana wartość  | Opis                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **Prefiks DNS** | Nazwa unikatowa w skali globalnej | Nazwa, która jednoznacznie identyfikuje rejestr kontenerów. |
    | **Subskrypcja** | Wybierz subskrypcję | Subskrypcja platformy Azure, która ma być używana. |
    | **[Grupa zasobów](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Nazwa grupy zasobów, w której chcesz utworzyć rejestr kontenerów. Wybierz pozycję **Nowa**, aby utworzyć nową grupę zasobów.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Standardowa (Standard) | Warstwa usługi rejestru kontenerów  |
    | **Lokalizacja rejestru** | Lokalizacja w pobliżu | Wybierz lokalizację w [regionie w](https://azure.microsoft.com/regions/) pobliżu ciebie lub w pobliżu innych usług, które będą korzystać z rejestru kontenerów. |

    ![Visual Studio dialogowe Azure Container Registry tworzenia aplikacji](media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png)

1. Wybierz przycisk **Utwórz**.

   ![Zrzut ekranu przedstawiający pomyślną publikację](media/container-tools/publish-succeeded.png)
:::moniker-end

:::moniker range=">=vs-2019"

1. Zmień opcję listy rozwijanej konfiguracji na **Wydanie** i skompiluj aplikację.
1. Kliknij prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** i wybierz polecenie **Publikuj.**
1. W oknie dialogowym publikowania docelowego wybierz pozycję **Docker Container Registry**.

   ![Wybierz pozycję Docker Container Registry](media/container-tools-react/vs-2019/publish-dialog1.png)

1. Następnie wybierz **pozycję Azure Container Registry**.

   ![Wybierz Azure Container Registry](media/container-tools-react/vs-2019/publish-dialog-acr.png)

1. Wybierz **pozycję Utwórz nowy Azure Container Registry**.
1. Wypełnij żądane wartości na ekranie **Create new Azure Container Registry (Tworzenie Azure Container Registry** aplikacji).

    | Ustawienie      | Sugerowana wartość  | Opis                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **Prefiks DNS** | Nazwa unikatowa w skali globalnej | Nazwa, która jednoznacznie identyfikuje rejestr kontenerów. |
    | **Subskrypcja** | Wybierz subskrypcję | Subskrypcja platformy Azure, która ma być używana. |
    | **[Grupa zasobów](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Nazwa grupy zasobów, w której chcesz utworzyć rejestr kontenerów. Wybierz pozycję **Nowa**, aby utworzyć nową grupę zasobów.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Standardowa (Standard) | Warstwa usługi rejestru kontenerów  |
    | **Lokalizacja rejestru** | Lokalizacja w pobliżu | Wybierz lokalizację w [regionie w](https://azure.microsoft.com/regions/) pobliżu ciebie lub w pobliżu innych usług, które będą korzystać z rejestru kontenerów. |

    ![Visual Studio dialogowe Azure Container Registry tworzenia aplikacji](media/container-tools-react/vs-2019/azure-container-registry-details.png)

1. Wybierz **pozycję Utwórz,** a następnie wybierz **pozycję Zakończ.**

   ![Wybieranie lub tworzenie nowego konta ACR](media/container-tools-react/vs-2019/publish-dialog2.png)

   Po zakończeniu procesu publikowania możesz przejrzeć ustawienia publikowania i edytować je w razie potrzeby lub opublikować obraz ponownie przy użyciu **przycisku Publikuj.**

   ![Zrzut ekranu przedstawiający pomyślną publikację](media/container-tools-react/vs-2019/publish-finished.png)

   Aby ponownie rozpocząć korzystanie z **okna dialogowego** Publikowanie, usuń profil publikowania przy użyciu **linku Usuń** na tej stronie, a następnie ponownie wybierz **pozycję Publikuj.**
:::moniker-end

## <a name="next-steps"></a>Następne kroki

Teraz możesz ściągnąć kontener z rejestru do dowolnego hosta, który może uruchamiać obrazy platformy Docker, na [Azure Container Instances](/azure/container-instances/container-instances-tutorial-deploy-app).

## <a name="additional-resources"></a>Dodatkowe zasoby

* [Opracowywanie kontenerów w programie Visual Studio](./index.yml)
* [Rozwiązywanie problemów związanych z opracowywaniem zwartości w programie Visual Studio przy użyciu platformy Docker](troubleshooting-docker-errors.md)
* [Repozytorium usługi GitHub dla narzędzi kontenerów programu Visual Studio](https://github.com/Microsoft/DockerTools)


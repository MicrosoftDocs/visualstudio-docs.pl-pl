---
title: Narzędzia kontenerów programu Visual Studio z ASP.NET Core i React.js
author: ghogen
description: Dowiedz się, jak korzystać z narzędzi kontenerowych programu Visual Studio i platformy Docker dla systemu Windows
ms.author: ghogen
ms.date: 10/16/2019
ms.technology: vs-azure
ms.topic: quickstart
ms.openlocfilehash: af859c1c06820aa477869f6968e9c652bd525de6
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "75916747"
---
# <a name="quickstart-use-docker-with-a-react-single-page-app-in-visual-studio"></a>Szybki start: używanie platformy Docker z aplikacją React jednostronicową w programie Visual Studio

Za pomocą programu Visual Studio można łatwo tworzyć, debugować i uruchamiać konteneryzowane aplikacje ASP.NET Core, w tym aplikacje javascript po stronie klienta, takie jak aplikacja jednostronicowa React.js, i publikować je w usłudze Azure Container Registry (ACR), Centrum platformy Docker, usłudze Azure App Service lub we własnym rejestru kontenerów. W tym artykule opublikujemy w ACR.

## <a name="prerequisites"></a>Wymagania wstępne

::: moniker range="vs-2017"
* [Pulpit platformy Docker](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) z zainstalowanym **programem Web Development,** **obciążeniem narzędzi platformy Azure** i/lub **międzyplatformowym** obciążeniem programistycznym .NET Core
* Aby opublikować w usłudze Azure Container Registry, subskrypcję platformy Azure. [Zarejestruj się, aby uzyskać bezpłatną wersję próbną](https://azure.microsoft.com/offers/ms-azr-0044p/).
* [Node.js](https://nodejs.org/en/download/)
* W przypadku kontenerów systemu Windows system Windows 10 w wersji 1903 lub nowszej można użyć obrazów platformy Docker, do których odwołują się w tym artykule.
::: moniker-end
::: moniker range=">=vs-2019"
* [Pulpit platformy Docker](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) z zainstalowanym **programem Web Development,** **obciążeniem narzędzi platformy Azure** i/lub **międzyplatformowym** obciążeniem programistycznym .NET Core
* [.NET Core 2.2 Narzędzia programistyczne](https://dotnet.microsoft.com/download/dotnet-core/2.2) do tworzenia z .NET Core 2.2
* Aby opublikować w usłudze Azure Container Registry, subskrypcję platformy Azure. [Zarejestruj się, aby uzyskać bezpłatną wersję próbną](https://azure.microsoft.com/offers/ms-azr-0044p/).
* [Node.js](https://nodejs.org/en/download/)
* W przypadku kontenerów systemu Windows system Windows 10 w wersji 1903 lub nowszej można użyć obrazów platformy Docker, do których odwołują się w tym artykule.
::: moniker-end

## <a name="installation-and-setup"></a>Instalacja i konfiguracja

W przypadku instalacji platformy Docker należy najpierw przejrzeć informacje zawarte w programie [Docker Desktop dla systemu Windows: Co należy wiedzieć przed zainstalowaniem](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install)programu . Następnie zainstaluj program [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows).

## <a name="create-a-project-and-add-docker-support"></a>Tworzenie projektu i dodawanie obsługi platformy Docker

::: moniker range="vs-2017"
1. Utwórz nowy projekt przy użyciu szablonu **ASP.NET Core Web Application.**
1. Wybierz **react.js**. Nie można wybrać **Włącz obsługę platformy Docker**, ale nie martw się, można dodać tej obsługi po utworzeniu projektu.

   ![Zrzut ekranu przedstawiający nowy projekt React.js](media/container-tools-react/vs2017/new-react-project.png)

1. Kliknij prawym przyciskiem myszy węzeł projektu, a następnie wybierz pozycję **Dodaj** > **obsługę platformy Docker,** aby dodać plik dockerfile do projektu.

   ![Dodawanie obsługi platformy Docker](media/container-tools-react/vs2017/add-docker-support.png)

1. Zaznacz typ kontenera i kliknij przycisk **OK**.
::: moniker-end
::: moniker range=">=vs-2019"
1. Utwórz nowy projekt przy użyciu szablonu **ASP.NET Core Web Application.**
1. Wybierz **pozycję React.js**i kliknij przycisk **Utwórz**. Nie możesz wybrać **opcji Włącz obsługę platformy Docker**, ale nie martw się, możesz dodać tę obsługę później.

   ![Zrzut ekranu przedstawiający nowy projekt React.js](media/container-tools-react/vs2019/new-react-project.png)

1. Kliknij prawym przyciskiem myszy węzeł projektu, a następnie wybierz pozycję **Dodaj** > **obsługę platformy Docker,** aby dodać plik dockerfile do projektu.

   ![Dodawanie obsługi platformy Docker](media/container-tools-react/vs2017/add-docker-support.png)

1. Wybierz typ kontenera.
::: moniker-end

Następny krok różni się w zależności od tego, czy używasz kontenerów systemu Linux, czy kontenerów systemu Windows.

## <a name="modify-the-dockerfile-linux-containers"></a>Modyfikowanie pliku dockerfile (kontenery Systemu Linux)

W projekcie tworzony jest plik *dockerfile*, przepis na tworzenie ostatecznego obrazu platformy Docker. Opis poleceń znajdujących się w tym pliku można znaleźć w [dokumentacji pliku Dockerfile](https://docs.docker.com/engine/reference/builder/).

Otwórz plik *Dockerfile* w projekcie i dodaj następujące wiersze, aby zainstalować node.js 10.x w kontenerze. Pamiętaj, aby dodać te wiersze w pierwszej sekcji, aby dodać instalację menedżera pakietu węzła *npm.exe* do obrazu podstawowego, który jest używany w kolejnych krokach.

```
RUN curl -sL https://deb.nodesource.com/setup_10.x |  bash -
RUN apt-get install -y nodejs
```

*Dockerfile* powinien teraz wyglądać mniej więcej tak:

```
FROM microsoft/dotnet:2.2-aspnetcore-runtime-stretch-slim AS base
WORKDIR /app
EXPOSE 80 
EXPOSE 443
RUN curl -sL https://deb.nodesource.com/setup_10.x |  bash -
RUN apt-get install -y nodejs

FROM microsoft/dotnet:2.2-sdk-stretch AS build
WORKDIR /src
COPY ["WebApplication37/WebApplication37.csproj", "WebApplication37/"]
RUN dotnet restore "WebApplication37/WebApplication37.csproj"
COPY . .
WORKDIR "/src/WebApplication37"
RUN dotnet build "WebApplication37.csproj" -c Release -o /app

FROM build AS publish
RUN dotnet publish "WebApplication37.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "WebApplication37.dll"]
```

Poprzedni plik *Dockerfile* jest oparty na obrazie [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) i zawiera instrukcje dotyczące modyfikowania obrazu podstawowego przez tworzenie projektu i dodawanie go do kontenera.

Jeśli w oknie dialogowym nowego projektu zostanie zaznaczone pole wyboru **Konfiguruj dla protokołu HTTPS**, plik *Dockerfile* uwidacznia dwa porty. Jeden port jest używany na potrzeby ruchu HTTP, a drugi na potrzeby protokołu HTTPS. Jeśli to pole wyboru nie zostanie zaznaczone, dla ruchu HTTP zostanie uwidoczniony pojedynczy port (80).

## <a name="modify-the-dockerfile-windows-containers"></a>Modyfikowanie pliku dockerfile (kontenerów systemu Windows)

Otwórz plik projektu, klikając dwukrotnie węzeł projektu i zaktualizuj plik projektu (*.csproj), dodając `<PropertyGroup>` następującą właściwość jako element podrzędny elementu:

   ```xml
    <DockerfileFastModeStage>base</DockerfileFastModeStage>
   ```

Zaktualizuj plik Dockerfile, dodając następujące wiersze. Spowoduje to skopiowanie węzła i npm do kontenera.

   1. Dodaj ``# escape=` `` do pierwszego wiersza pliku dockerfile
   1. Przed dodaniem następujących wierszy`FROM … base`

      ```
      FROM mcr.microsoft.com/powershell:nanoserver-1903 AS downloadnodejs
      SHELL ["pwsh", "-Command", "$ErrorActionPreference = 'Stop';$ProgressPreference='silentlyContinue';"]
      RUN Invoke-WebRequest -OutFile nodejs.zip -UseBasicParsing "https://nodejs.org/dist/v10.16.3/node-v10.16.3-win-x64.zip"; `
      Expand-Archive nodejs.zip -DestinationPath C:\; `
      Rename-Item "C:\node-v10.16.3-win-x64" c:\nodejs
      ```

   1. Dodaj następujący wiersz przed i po`FROM … build`

      ```
      COPY --from=downloadnodejs C:\nodejs\ C:\Windows\system32\
      ```

   1. Kompletny plik dockerfile powinien teraz wyglądać mniej więcej tak:

      ```
      # escape=`
      #Depending on the operating system of the host machines(s) that will build or run the containers, the image specified in the FROM statement may need to be changed.
      #For more information, please see https://aka.ms/containercompat
      FROM mcr.microsoft.com/powershell:nanoserver-1903 AS downloadnodejs
      SHELL ["pwsh", "-Command", "$ErrorActionPreference = 'Stop';$ProgressPreference='silentlyContinue';"]
      RUN Invoke-WebRequest -OutFile nodejs.zip -UseBasicParsing "https://nodejs.org/dist/v10.16.3/node-v10.16.3-win-x64.zip"; `
      RUN Expand-Archive nodejs.zip -DestinationPath C:\; `
      RUN Rename-Item "C:\node-v10.16.3-win-x64" c:\nodejs

      FROM mcr.microsoft.com/dotnet/core/aspnet:2.2-nanoserver-1903 AS base
      WORKDIR /app
      EXPOSE 80
      EXPOSE 443
      COPY --from=downloadnodejs C:\nodejs\ C:\Windows\system32\

      FROM mcr.microsoft.com/dotnet/core/sdk:2.2-nanoserver-1903 AS build
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

1. Zaktualizuj plik .dockerignore, usuwając plik `**/bin`.

## <a name="debug"></a>Debugowanie

Wybierz pozycję **Docker** z listy rozwijanej debugowania na pasku narzędzi i rozpocznij debugowanie aplikacji. Może zostać wyświetlony komunikat z monitem o ufanie certyfikatowi; wybrać, aby zaufać certyfikatowi, aby kontynuować.  Przy pierwszym budowie docker pobiera obrazy podstawowe, więc może to potrwać nieco dłużej.

Opcja **Narzędzia kontenerów** w oknie **Dane wyjściowe** pokazuje, jakie akcje mają miejsce. Powinny być widoczne kroki instalacji skojarzone z *npm.exe*.

Przeglądarka pokazuje stronę główną aplikacji.

::: moniker range="vs-2017"
   ![Zrzut ekranu przedstawiający uruchamianie aplikacji](media/container-tools-react/vs2017/running-app.png)
::: moniker-end
::: moniker range=">=vs-2019"
   ![Zrzut ekranu przedstawiający uruchamianie aplikacji](media/container-tools-react/vs2019/running-app.png)
::: moniker-end

Spróbuj przejść do *counter* strony i przetestować kod po stronie klienta dla licznika, klikając przycisk **Przyrost.**

Otwórz **konsolę Menedżera pakietów** (PMC) z menu **Narzędzia**> Menedżer pakietów NuGet, **Konsola Menedżera pakietów**.

Wynikowy obraz platformy Docker aplikacji jest oznaczony tagiem *dev*. Obraz jest oparty na *2.2-aspnetcore-runtime* tag obrazu podstawowego *microsoft/dotnet.* Uruchom polecenie `docker images` w oknie **konsoli menedżera pakietów** (PMC). Na komputerze są wyświetlane następujące obrazy:

```console
REPOSITORY        TAG                     IMAGE ID      CREATED         SIZE
webapplication37  dev                     d72ce0f1dfe7  30 seconds ago  255MB
microsoft/dotnet  2.2-aspnetcore-runtime  fcc3887985bb  6 days ago      255MB
```

> [!NOTE]
> Obraz **dewelopera** nie zawiera plików binarnych aplikacji i innej zawartości, ponieważ konfiguracje **debugowania** używają montażu woluminów, aby zapewnić iteracyjne środowisko edycji i debugowania. Aby utworzyć obraz produkcyjny zawierający całą zawartość, należy użyć konfiguracji **Wydania.**

Uruchom polecenie `docker ps` w konsoli PMC. Zauważ, że aplikacja działa przy użyciu kontenera:

```console
CONTAINER ID        IMAGE                  COMMAND               CREATED             STATUS              PORTS                                           NAMES
cf5d2ef5f19a        webapplication37:dev   "tail -f /dev/null"   2 minutes ago       Up 2 minutes        0.0.0.0:52036->80/tcp, 0.0.0.0:44342->443/tcp   priceless_cartwright
```

## <a name="publish-docker-images"></a>Publikowanie obrazów platformy Docker

Po zakończeniu cyklu tworzenia i debugowania aplikacji można utworzyć obraz produkcyjny aplikacji.

1. Zmień opcję listy rozwijanej konfiguracji na **Wydanie** i skompiluj aplikację.
1. Kliknij prawym przyciskiem myszy projekt w **Eksploratorze rozwiązań** i wybierz polecenie **Publikuj**.
1. W oknie dialogowym publikowania obiektu docelowego wybierz kartę **Rejestr kontenerów.**
1. Wybierz **pozycję Utwórz nowy rejestr kontenerów platformy Azure** i kliknij pozycję **Publikuj**.
1. Wypełnij żądane wartości w obszarze **Utwórz nowy rejestr kontenerów platformy Azure**.

    | Ustawienie      | Sugerowana wartość  | Opis                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **Prefiks DNS** | Nazwa unikatowa w skali globalnej | Nazwa, która jednoznacznie identyfikuje rejestr kontenerów. |
    | **Subskrypcja** | Wybierz subskrypcję | Subskrypcja platformy Azure, która ma być używana. |
    | **[Grupa zasobów](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Nazwa grupy zasobów, w której ma być utworzony rejestr kontenerów. Wybierz pozycję **Nowa**, aby utworzyć nową grupę zasobów.|
    | **[Numer jednostki magazynowej](/azure/container-registry/container-registry-skus)** | Standardowa | Warstwa usługi rejestru kontenerów  |
    | **Lokalizacja rejestru** | Lokalizacja blisko Ciebie | Wybierz lokalizację w [regionie](https://azure.microsoft.com/regions/) w pobliżu lub w pobliżu innych usług, które będą korzystać z rejestru kontenerów. |

    ![Okno dialogowe tworzenia kontenera usługi Azure w programie Visual Studio][0]

1. Kliknij przycisk **Utwórz**.

   ![Zrzut ekranu przedstawiający pomyślne opublikowanie](media/container-tools/publish-succeeded.png)

## <a name="next-steps"></a>Następne kroki

Teraz można wyciągnąć kontener z rejestru do dowolnego hosta zdolnego do uruchamiania obrazów platformy Docker, na przykład [wystąpienia kontenera platformy Azure.](/azure/container-instances/container-instances-tutorial-deploy-app)

## <a name="additional-resources"></a>Zasoby dodatkowe

* [Opracowywanie kontenerów w programie Visual Studio](/visualstudio/containers)
* [Rozwiązywanie problemów związanych z opracowywaniem zwartości w programie Visual Studio przy użyciu platformy Docker](troubleshooting-docker-errors.md)
* [Repozytorium usługi GitHub dla narzędzi kontenerów programu Visual Studio](https://github.com/Microsoft/DockerTools)

::: moniker range="vs-2017"
[0]:media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png
::: moniker-end
::: moniker range=">=vs-2019"
[0]:media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog-2019.png
::: moniker-end
---
title: Narzędzia kontenerów programu Visual Studio z platformą ASP.NET Core
author: ghogen
description: Dowiedz się, jak korzystać z narzędzi programu Visual Studio 2017 i platformy Docker dla systemu Windows
ms.author: ghogen
ms.date: 02/01/2019
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: ae6548892010035564bf29a8eda25b736db97d2a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76922974"
---
Za pomocą programu Visual Studio można łatwo tworzyć, debugować i uruchamiać konteneryzowane aplikacje ASP.NET Core i publikować je w usłudze Azure Container Registry (ACR), Centrum platformy Docker, usłudze Azure App Service lub własnym rejestrze kontenerów. W tym artykule opublikujemy w ACR.

## <a name="prerequisites"></a>Wymagania wstępne

* [Pulpit platformy Docker](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) z zainstalowanym **programem Web Development,** **obciążeniem narzędzi platformy Azure** i/lub **międzyplatformowym** obciążeniem programistycznym .NET Core
* Aby opublikować w usłudze Azure Container Registry, subskrypcję platformy Azure. [Zarejestruj się, aby uzyskać bezpłatną wersję próbną](https://azure.microsoft.com/offers/ms-azr-0044p/).

## <a name="installation-and-setup"></a>Instalacja i konfiguracja

W przypadku instalacji platformy Docker należy najpierw przejrzeć informacje zawarte w programie [Docker Desktop dla systemu Windows: Co należy wiedzieć przed zainstalowaniem](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install)programu . Następnie zainstaluj program [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows).

## <a name="add-a-project-to-a-docker-container"></a>Dodawanie projektu do kontenera platformy Docker

1. Z menu Visual Studio wybierz polecenie **Plik > Nowy projekt >**.
1. W sekcji **Szablony** w oknie dialogowym **Nowy projekt** wybierz pozycję **Visual C# > Web**.
1. Wybierz **ASP.NET Core Web Application** lub jeśli chcesz użyć programu .NET Framework zamiast programu .NET Core, wybierz opcję ASP.NET aplikacji sieci **Web**.
1. Nadaj nowej aplikacji nazwę (lub zrób wartość domyślną) i wybierz **przycisk OK**.
1. Wybierz **aplikację sieci Web**.
1. Zaznacz pole wyboru **Włącz obsługę platformy Docker.**

   ![Pole wyboru Włącz obsługę platformy Docker](../../media/container-tools/enable-docker-support.PNG)

   Zrzut ekranu pokazuje .NET Core; jeśli używasz programu .NET Framework, wygląda to nieco inaczej.

1. Wybierz odpowiedni typ kontenera (Windows lub Linux) i kliknij przycisk **OK**.

## <a name="dockerfile-overview"></a>Plik Dockerfile — przegląd

W projekcie tworzony jest plik *dockerfile*, przepis na tworzenie ostatecznego obrazu platformy Docker. Zapoznaj się z odwołaniem do [pliku dockerfile,](https://docs.docker.com/engine/reference/builder/) aby zapoznać się z poleceniami w nim.:

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

Poprzedni plik *Dockerfile* jest oparty na obrazie [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) i zawiera instrukcje dotyczące modyfikowania obrazu podstawowego przez tworzenie projektu i dodawanie go do kontenera. Jeśli używasz programu .NET Framework, obraz podstawowy będzie inny.

Jeśli w oknie dialogowym nowego projektu zostanie zaznaczone pole wyboru **Konfiguruj dla protokołu HTTPS**, plik *Dockerfile* uwidacznia dwa porty. Jeden port jest używany na potrzeby ruchu HTTP, a drugi na potrzeby protokołu HTTPS. Jeśli to pole wyboru nie zostanie zaznaczone, dla ruchu HTTP zostanie uwidoczniony pojedynczy port (80).

## <a name="debug"></a>Debugowanie

Wybierz pozycję **Docker** z listy rozwijanej debugowania na pasku narzędzi i rozpocznij debugowanie aplikacji. Może zostać wyświetlony komunikat z monitem o ufanie certyfikatowi; wybrać, aby zaufać certyfikatowi, aby kontynuować.

Okno **Dane wyjściowe** pokazuje, jakie akcje mają miejsce.

Otwórz **konsolę Menedżera pakietów** (PMC) z menu **Narzędzia**> Menedżer pakietów NuGet, **Konsola Menedżera pakietów**.

Wynikowy obraz platformy Docker aplikacji jest oznaczony tagiem *dev*. Obraz bazuje na tagu *2.1-aspnetcore-runtime* obrazu podstawowego *microsoft/dotnet*. Uruchom polecenie `docker images` w oknie **konsoli menedżera pakietów** (PMC). Na komputerze są wyświetlane następujące obrazy:

```console
REPOSITORY        TAG                     IMAGE ID      CREATED         SIZE
hellodockertools  dev                     d72ce0f1dfe7  30 seconds ago  255MB
microsoft/dotnet  2.1-aspnetcore-runtime  fcc3887985bb  6 days ago      255MB
```

> [!NOTE]
> Obraz **dewelopera** nie zawiera plików binarnych aplikacji i innej zawartości, ponieważ konfiguracje **debugowania** używają montażu woluminów, aby zapewnić iteracyjne środowisko edycji i debugowania. Aby utworzyć obraz produkcyjny zawierający całą zawartość, należy użyć konfiguracji **Wydania.**

Uruchom polecenie `docker ps` w konsoli PMC. Zauważ, że aplikacja działa przy użyciu kontenera:

```console
CONTAINER ID        IMAGE                  COMMAND                   CREATED             STATUS              PORTS                   NAMES
baf9a678c88d        hellodockertools:dev   "C:\\remote_debugge..."   21 seconds ago      Up 19 seconds       0.0.0.0:37630->80/tcp   dockercompose4642749010770307127_hellodockertools_1
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

1. Kliknij **przycisk Utwórz**

## <a name="next-steps"></a>Następne kroki

Teraz można wyciągnąć kontener z rejestru do dowolnego hosta zdolnego do uruchamiania obrazów platformy Docker, na przykład [wystąpienia kontenera platformy Azure.](/azure/container-instances/container-instances-tutorial-deploy-app)

[0]:../../media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png

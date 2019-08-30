---
title: Narzędzia kontenera programu Visual Studio z ASP.NET Core
author: ghogen
description: Dowiedz się, jak używać narzędzi kontenera programu Visual Studio i Docker for Windows
ms.author: ghogen
ms.date: 06/06/2019
ms.technology: vs-azure
ms.topic: quickstart
ms.openlocfilehash: bcc30ec13096b37d7540c187d11c846d6c575093
ms.sourcegitcommit: 44e9b1d9230fcbbd081ee81be9d4be8a485d8502
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2019
ms.locfileid: "70179878"
---
# <a name="quickstart-use-docker-with-a-react-single-page-app-in-visual-studio"></a>Szybki start: Korzystanie z platformy Docker z aplikacją jednostronicową do reagowania w programie Visual Studio

Za pomocą programu Visual Studio można łatwo kompilować, debugować i uruchamiać kontenery ASP.NET Core aplikacje, w tym za pomocą skryptów JavaScript po stronie klienta, takich jak aplikacje jednostronicowe z systemem. js, a następnie publikować je w Azure Container Registry (ACR), Docker Hub, Azure App Service lub własnych Rejestr kontenerów. W tym artykule opublikujemy ACR.

## <a name="prerequisites"></a>Wymagania wstępne

::: moniker range="vs-2017"
* [Pulpit Docker](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Program Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) z zainstalowaną obsługą tworzenia aplikacji dla **sieci Web**, obciążeń **narzędzi platformy Azure** i/lub **oprogramowania .NET Core dla wielu platform**
* Do opublikowania w usłudze Azure Container Registry, subskrypcji platformy Azure. [Zamów bezpłatną wersję próbną](https://azure.microsoft.com/offers/ms-azr-0044p/).
::: moniker-end
::: moniker range=">=vs-2019"
* [Pulpit Docker](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Program Visual Studio 2019](https://visualstudio.microsoft.com/downloads) z zainstalowaną obsługą tworzenia aplikacji dla **sieci Web**, obciążeń **narzędzi platformy Azure** i/lub **oprogramowania .NET Core dla wielu platform**
* [Narzędzia programistyczne programu .net core 2,2](https://dotnet.microsoft.com/download/dotnet-core/2.2) do programowania przy użyciu programu .net Core 2,2
* Do opublikowania w usłudze Azure Container Registry, subskrypcji platformy Azure. [Zamów bezpłatną wersję próbną](https://azure.microsoft.com/offers/ms-azr-0044p/).
::: moniker-end

## <a name="installation-and-setup"></a>Instalacja i konfiguracja

Aby zainstalować platformę Docker, najpierw przejrzyj informacje [na pulpicie Docker dla systemu Windows: Co należy wiedzieć przed zainstalowaniem](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install)programu. Następnie zainstaluj program [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows).

## <a name="create-a-project-and-add-docker-support"></a>Tworzenie projektu i Dodawanie obsługi platformy Docker

::: moniker range="vs-2017"
1. Utwórz nowy projekt za pomocą szablonu **aplikacji sieci Web ASP.NET Core** .
1. Wybierz pozycję **reagować. js**. Nie możesz wybrać opcji **Włącz obsługę platformy Docker**, ale nie martw się, możesz dodać tę obsługę po utworzeniu projektu.

   ![Zrzut ekranu przedstawiający nowy projekt reaguje. js](media/container-tools-react/vs2017/new-react-project.png)

1. Kliknij prawym przyciskiem myszy węzeł projektu, a następnie wybierz polecenie **Dodaj** > **obsługę platformy Docker** , aby dodać pliku dockerfile do projektu.

   ![Dodaj obsługę platformy Docker](media/container-tools-react/vs2017/add-docker-support.png)

1. Wybierz typ kontenera systemu Linux, a następnie kliknij przycisk **OK**.
::: moniker-end
::: moniker range=">=vs-2019"
1. Utwórz nowy projekt za pomocą szablonu **aplikacji sieci Web ASP.NET Core** .
1. Wybierz pozycję **reagując. js**, a następnie kliknij pozycję **Utwórz**. Nie możesz wybrać opcji **Włącz obsługę platformy Docker**, ale nie martw się, możesz dodać tę obsługę później.

   ![Zrzut ekranu przedstawiający nowy projekt reaguje. js](media/container-tools-react/vs2019/new-react-project.png)

1. Kliknij prawym przyciskiem myszy węzeł projektu, a następnie wybierz polecenie **Dodaj** > **obsługę platformy Docker** , aby dodać pliku dockerfile do projektu.

   ![Dodaj obsługę platformy Docker](media/container-tools-react/vs2017/add-docker-support.png)

1. Wybierz pozycję Linux jako typ kontenera.
::: moniker-end

## <a name="dockerfile-overview"></a>Pliku dockerfile — Omówienie

*Pliku dockerfile*, przepis dotyczący tworzenia końcowego obrazu platformy Docker, jest tworzony w projekcie. Zapoznaj się z dokumentacją [pliku dockerfile](https://docs.docker.com/engine/reference/builder/) , aby zrozumieć polecenia w nim.

Otwórz *pliku dockerfile* w projekcie i Dodaj następujące wiersze, aby zainstalować Node. js 10. x w kontenerze. Pamiętaj, aby dodać te wiersze w pierwszej sekcji, aby dodać instalację węzła Menedżera pakietów *npm. exe* do obrazu podstawowego używanego w kolejnych krokach.

```
RUN curl -sL https://deb.nodesource.com/setup_10.x |  bash -
RUN apt-get install -y nodejs
```

*Pliku dockerfile* powinien teraz wyglądać następująco:

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

Poprzedni *pliku dockerfile* opiera się na obrazie [Microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) i zawiera instrukcje dotyczące modyfikowania obrazu podstawowego przez skompilowanie projektu i dodanie go do kontenera.

Gdy pole wyboru Konfiguruj nowy projekt **dla protokołu HTTPS** jest zaznaczone, *pliku dockerfile* uwidacznia dwa porty. Jeden port jest używany na potrzeby ruchu HTTP; drugi port jest używany w przypadku protokołu HTTPS. Jeśli pole wyboru nie jest zaznaczone, pojedynczy port (80) zostanie uwidoczniony dla ruchu HTTP.

## <a name="debug"></a>Debugowanie

Wybierz pozycję Docker z listy rozwijanej Debuguj na pasku narzędzi i Rozpocznij debugowanie aplikacji. Może pojawić się komunikat z monitem o zaufać certyfikatowi; Wybierz relację zaufania certyfikatu, aby kontynuować.

Opcja **Narzędzia kontenera** w oknie **danych wyjściowych** pokazuje, jakie akcje są wykonywane. Powinny zostać wyświetlone kroki instalacji skojarzone z *npm. exe*.

W przeglądarce zostanie wyświetlona strona główna aplikacji.

::: moniker range="vs-2017"
   ![Zrzut ekranu przedstawiający uruchomioną aplikację](media/container-tools-react/vs2017/running-app.png)
::: moniker-end
::: moniker range=">=vs-2019"
   ![Zrzut ekranu przedstawiający uruchomioną aplikację](media/container-tools-react/vs2019/running-app.png)
::: moniker-end

Przejdź do strony *licznika* i przetestuj kod po stronie klienta dla licznika, klikając przycisk **przyrostu** .

Otwórz **konsolę Menedżera pakietów** (PMC) z menu **Narzędzia**, > Menedżer pakietów NuGet, **konsola Menedżera pakietów**.

Utworzony obraz platformy Docker aplikacji jest otagowany jako *dev*. Obraz jest oparty na tagu *2,2-aspnetcore-Runtime* obrazu podstawowego *Microsoft/dotnet* . Uruchom polecenie w oknie **konsola Menedżera pakietów** (PMC). `docker images` Wyświetlane są obrazy na komputerze:

```console
REPOSITORY        TAG                     IMAGE ID      CREATED         SIZE
webapplication37  dev                     d72ce0f1dfe7  30 seconds ago  255MB
microsoft/dotnet  2.2-aspnetcore-runtime  fcc3887985bb  6 days ago      255MB
```

> [!NOTE]
> Obraz **deweloperski** nie zawiera plików binarnych aplikacji i innych zawartości, ponieważ konfiguracje **debugowania** używają funkcji instalacji woluminu, aby zapewnić iteracyjne edytowanie i debugowanie. Aby utworzyć obraz produkcyjny zawierający całą zawartość, użyj konfiguracji **wydania** .

`docker ps` Uruchom polecenie w PMC. Zauważ, że aplikacja jest uruchomiona przy użyciu kontenera:

```console
CONTAINER ID        IMAGE                  COMMAND               CREATED             STATUS              PORTS                                           NAMES
cf5d2ef5f19a        webapplication37:dev   "tail -f /dev/null"   2 minutes ago       Up 2 minutes        0.0.0.0:52036->80/tcp, 0.0.0.0:44342->443/tcp   priceless_cartwright
```

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
    | **Subskrypcja** | Wybierz subskrypcję | Subskrypcja platformy Azure do użycia. |
    | **[Grupa zasobów](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Nazwa grupy zasobów, w której ma zostać utworzony rejestr kontenerów. Wybierz pozycję **Nowy** , aby utworzyć nową grupę zasobów.|
    | **[MAGAZYN](https://docs.microsoft.com/azure/container-registry/container-registry-skus)** | Standardowa (Standard) | Warstwa usług w rejestrze kontenerów  |
    | **Lokalizacja rejestru** | Lokalizacja blisko Ciebie | Wybierz lokalizację w [regionie](https://azure.microsoft.com/regions/) blisko siebie lub w najbliższej innej usłudze, która będzie korzystać z rejestru kontenerów. |

    ![Okno dialogowe tworzenia Azure Container Registry programu Visual Studio][0]

1. Kliknij przycisk **Utwórz**.

   ![Zrzut ekranu przedstawiający pomyślne publikowanie](media/container-tools/publish-succeeded.png)

## <a name="next-steps"></a>Następne kroki

Teraz można ściągnąć kontener z rejestru do dowolnego hosta, który może uruchamiać obrazy platformy Docker, na przykład [Azure Container Instances](/azure/container-instances/container-instances-tutorial-deploy-app).

## <a name="additional-resources"></a>Dodatkowe zasoby

* [Programowanie kontenerów za pomocą programu Visual Studio](/visualstudio/containers)
* [Rozwiązywanie problemów z programowaniem programu Visual Studio przy użyciu platformy Docker](troubleshooting-docker-errors.md)
* [Repozytorium usługi GitHub dla narzędzi kontenerów programu Visual Studio](https://github.com/Microsoft/DockerTools)

::: moniker range="vs-2017"
[0]:media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png
::: moniker-end
::: moniker range=">=vs-2019"
[0]:media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog-2019.png
::: moniker-end
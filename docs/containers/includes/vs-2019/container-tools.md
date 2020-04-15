---
title: Narzędzia programu Visual Studio dla platformy Docker z ASP.NET
author: ghogen
description: Dowiedz się, jak korzystać z narzędzi programu Visual Studio 2019 i platformy Docker dla systemu Windows
ms.author: ghogen
ms.date: 02/01/2019
ms.prod: visual-studio-dev16
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: d6d519483b350f2c1086c76bc17522b71a435fe9
ms.sourcegitcommit: cc58ca7ceae783b972ca25af69f17c9f92a29fc2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389956"
---
Za pomocą programu Visual Studio można łatwo tworzyć, debugować i uruchamiać konteneryzowane aplikacje .NET, ASP.NET i ASP.NET Core i publikować je w usłudze Azure Container Registry (ACR), Centrum platformy Docker, usłudze Azure App Service lub własny rejestr kontenerów. W tym artykule opublikujemy aplikację ASP.NET Core do ACR.

## <a name="prerequisites"></a>Wymagania wstępne

* [Pulpit platformy Docker](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) z zainstalowanym **programem Web Development,** **obciążeniem narzędzi platformy Azure** i/lub **międzyplatformowym** obciążeniem programistycznym .NET Core
* [Narzędzia do programowania .NET Core](https://dotnet.microsoft.com/download/dotnet-core/) do tworzenia za pomocą platformy .NET Core
* Aby opublikować w usłudze Azure Container Registry, subskrypcję platformy Azure. [Zarejestruj się, aby uzyskać bezpłatną wersję próbną](https://azure.microsoft.com/free/dotnet/).

## <a name="installation-and-setup"></a>Instalacja i konfiguracja

W przypadku instalacji platformy Docker należy najpierw przejrzeć informacje zawarte w programie [Docker Desktop dla systemu Windows: Co należy wiedzieć przed zainstalowaniem](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install)programu . Następnie zainstaluj program [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows).

## <a name="add-a-project-to-a-docker-container"></a>Dodawanie projektu do kontenera platformy Docker

1. Utwórz nowy projekt przy użyciu szablonu **ASP.NET Core Web Application** lub jeśli chcesz użyć programu .NET Framework zamiast programu .NET Core, wybierz opcję ASP.NET aplikacji sieci Web **(.NET Framework).**
1. Wybierz **opcję Aplikacja sieci Web**i upewnij się, że jest zaznaczone pole wyboru Włącz obsługę platformy **Docker.**

   ![Pole wyboru Włącz obsługę platformy Docker](../../media/container-tools/vs-2019/create-new-web-application.PNG)

   Zrzut ekranu pokazuje .NET Core; jeśli używasz programu .NET Framework, wygląda to nieco inaczej.

1. Wybierz odpowiedni typ kontenera (Windows lub Linux) i kliknij przycisk **Utwórz**.

## <a name="dockerfile-overview"></a>Plik Dockerfile — przegląd

W projekcie tworzony jest plik *dockerfile*, przepis na tworzenie ostatecznego obrazu platformy Docker. Zapoznaj się z odwołaniem do [pliku dockerfile,](https://docs.docker.com/engine/reference/builder/) aby zapoznać się z poleceniami w nim.:

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

Poprzedni plik *Dockerfile* jest oparty na obrazie [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) i zawiera instrukcje dotyczące modyfikowania obrazu podstawowego przez tworzenie projektu i dodawanie go do kontenera. Jeśli używasz programu .NET Framework, obraz podstawowy będzie inny.

Jeśli w oknie dialogowym nowego projektu zostanie zaznaczone pole wyboru **Konfiguruj dla protokołu HTTPS**, plik *Dockerfile* uwidacznia dwa porty. Jeden port jest używany na potrzeby ruchu HTTP, a drugi na potrzeby protokołu HTTPS. Jeśli to pole wyboru nie zostanie zaznaczone, dla ruchu HTTP zostanie uwidoczniony pojedynczy port (80).

## <a name="debug"></a>Debugowanie

Wybierz pozycję **Docker** z listy rozwijanej debugowania na pasku narzędzi i rozpocznij debugowanie aplikacji. Może zostać wyświetlony komunikat z monitem o ufanie certyfikatowi; wybrać, aby zaufać certyfikatowi, aby kontynuować.

Opcja **Narzędzia kontenerów** w oknie **Dane wyjściowe** pokazuje, jakie akcje mają miejsce. Po raz pierwszy pobranie obrazu bazowego może trochę potrwać, ale w kolejnych biegach jest znacznie szybsze.

>[!NOTE]
> Jeśli chcesz zmienić porty do debugowania, możesz to zrobić w pliku *launchSettings.json.* Zobacz [Ustawienia uruchamiania kontenera](../../container-launch-settings.md).

## <a name="containers-window"></a>Okno Kontenery

Jeśli masz visual studio 2019 w wersji 16.4 lub nowszej, można użyć **kontenerów** okna do wyświetlania uruchomionych kontenerów na komputerze, a także obrazy, które są dostępne.

Otwórz okno **Kontenery** przy użyciu pola wyszukiwania w IDE (naciśnij klawisz `container` **Ctrl**+**Q,** aby go użyć), wpisz i wybierz okno **Kontenery** z listy.

Okno **Kontenery** można zamontować w dogodnym miejscu, na przykład pod edytorem, przesuwając je i postępującym zgodnie z prowadnicami umieszczania okien.

W oknie znajdź kontener i przejdź przez każdą kartę, aby wyświetlić zmienne środowiskowe, mapowania portów, dzienniki i system plików.

![Zrzut ekranu przedstawiający okno Kontenery](../../media/overview/vs-2019/container-tools-window.png)

Aby uzyskać więcej informacji, zobacz [Wyświetlanie i diagnozowanie kontenerów i obrazów w programie Visual Studio.](../../view-and-diagnose-containers.md)

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

   ![Zrzut ekranu przedstawiający pomyślne opublikowanie](../../media/container-tools/publish-succeeded.png)

## <a name="next-steps"></a>Następne kroki

Teraz można wyciągnąć kontener z rejestru do dowolnego hosta zdolnego do uruchamiania obrazów platformy Docker, na przykład [wystąpienia kontenera platformy Azure.](/azure/container-instances/container-instances-tutorial-deploy-app)

[0]:../../media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog-2019.png

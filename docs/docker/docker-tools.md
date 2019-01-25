---
title: Visual Studio Tools for Docker z platformą ASP.NET Core
author: ghogen
description: Dowiedz się, jak używać narzędzi Visual Studio 2017 i platformy Docker for Windows
ms.author: ghogen
ms.date: 12/17/2018
ms.prod: visual-studio-dev15
ms.technology: vs-azure
ms.openlocfilehash: 6322c0072a4e9a22e5f3c8521aef9c87c1790175
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54876302"
---
# <a name="quickstart-visual-studio-tools-for-docker"></a>Szybki start: Visual Studio Tools for Docker

Za pomocą programu Visual Studio 2017 można łatwo tworzyć, debugować i uruchamianie konteneryzowanych aplikacji platformy ASP.NET Core i opublikować je w usłudze Azure Container Registry (ACR), usługi Docker Hub, usłudze Azure App Service lub rejestru kontenerów. W tym artykule opublikujemy do usługi ACR.

## <a name="prerequisites"></a>Wymagania wstępne

* [Pulpitu platformy docker](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Program Visual Studio 2017](https://visualstudio.microsoft.com/) z **programowania dla sieci Web**, **narzędzi Azure** obciążenia, i/lub **programowanie dla wielu platform .NET Core** zainstalowanym obciążeniem

## <a name="installation-and-setup"></a>Instalacja i Konfiguracja

Instalacja platformy Docker, najpierw zapoznaj się z informacjami o [pulpitu platformy Docker for Windows: Co należy wiedzieć przed zainstalowaniem](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install). Następnie zainstaluj [pulpitu platformy Docker](https://hub.docker.com/editions/community/docker-ce-desktop-windows).

## <a name="add-a-project-to-a-docker-container"></a>Dodaj projekt do kontenera platformy Docker

1. Wybierz z menu programu Visual Studio **Plik > Nowy > Projekt**.
1. W obszarze **szablony** części **nowy projekt** okno dialogowe, wybierz opcję **Visual C# > sieci Web**.
1. Wybierz **aplikacji sieci Web platformy ASP.NET Core**.
1. Nazwij swoją nową aplikację (lub wykonać domyślnie) i wybierz **OK**.
1. Wybierz **aplikacji sieci Web**.
1. Sprawdź **włączyć obsługę platformy Docker** pole wyboru.

   ![Zaznacz pole wyboru obsługę platformy Docker](media/docker-tools/enable-docker-support.PNG)

1. Wybierz typ kontenera (Windows lub Linux) i kliknij **OK**.

## <a name="dockerfile-overview"></a>Plik Dockerfile — omówienie

A *pliku Dockerfile*, przepisu do utworzenia końcowej obrazu platformy Docker jest tworzony w projekcie. Zapoznaj się [odwołanie do pliku Dockerfile](https://docs.docker.com/engine/reference/builder/) dla zrozumienia poleceń w niej.:

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

Poprzedni *pliku Dockerfile* opiera się na [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) obrazu i zawiera instrukcje dotyczące modyfikowania obraz podstawowy, tworząc projekt i dodanie go do kontenera. 

Gdy okno dialogowe nowego projektu w **Konfigurowanie protokołu HTTPS** pole wyboru jest zaznaczone, *pliku Dockerfile* udostępnia dwa porty. Jeden port jest używany do ruchu HTTP; inne port jest używany do obsługi protokołu HTTPS. Jeśli nie jest zaznaczone pole wyboru, jednego portu (80) jest uwidaczniany dla ruchu HTTP.

## <a name="debug"></a>Debugowanie

Wybierz **Docker** z poziomu pozycji Debuguj listy rozwijanej w pasku narzędzi, a następnie uruchamiania, debugowania aplikacji. Może pojawić się komunikat, wraz z monitem o o ufanie certyfikat; Wybierz zaufać certyfikatowi, aby kontynuować.

**Dane wyjściowe** okno pokazuje, jakie akcje pojawiają się.

Otwórz **Konsola Menedżera pakietów** (PMC) z menu **narzędzia**> Menedżer pakietów NuGet, **Konsola Menedżera pakietów**.

Wynikowy obraz platformy Docker w aplikacji zostanie oznaczony jako *dev*. Obraz, który jest oparty na *2.1 — aspnetcore-środowiska uruchomieniowego* tag *microsoft/dotnet* obrazu podstawowego. Uruchom `docker images` polecenia w pliku **Konsola Menedżera pakietów** okna (PMC). Wyświetlane są obrazy na komputerze:

```console
REPOSITORY        TAG                     IMAGE ID      CREATED         SIZE
hellodockertools  dev                     d72ce0f1dfe7  30 seconds ago  255MB
microsoft/dotnet  2.1-aspnetcore-runtime  fcc3887985bb  6 days ago      255MB
```

> [!NOTE]
> **Dev** obraz nie zawiera plików binarnych aplikacji i innej zawartości jako **debugowania** konfiguracje używają instalowania woluminów iteracji edytowanie i debugowanie. Aby utworzyć obraz produkcji zawierające całą zawartość, należy użyć **wersji** konfiguracji.

Uruchom `docker ps` polecenia w konsoli zarządzania Pakietami. Zwróć uwagę, że aplikacja jest uruchomiona przy użyciu kontenera:

```console
CONTAINER ID        IMAGE                  COMMAND                   CREATED             STATUS              PORTS                   NAMES
baf9a678c88d        hellodockertools:dev   "C:\\remote_debugge..."   21 seconds ago      Up 19 seconds       0.0.0.0:37630->80/tcp   dockercompose4642749010770307127_hellodockertools_1
```

## <a name="publish-docker-images"></a>Publikowanie obrazów platformy Docker

Po zakończeniu cyklu programowanie i debugowanie aplikacji, można utworzyć obraz aplikacji produkcyjnych.

1. Zmień konfigurację menu rozwijane **wersji** i kompilowania aplikacji. 
1. Kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierz polecenie **Publikuj**.
1. W oknie dialogowym docelowej publikowania wybierz **Container Registry** kartę.
1. Wybierz **Tworzenie nowej usługi Azure Container Registry** i kliknij przycisk **Publikuj**.
1. Wprowadź żądane wartości w **Utwórz nowy rejestr Azure Container Registry**.

    | Ustawienie      | Sugerowana wartość  | Opis                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **Prefiks DNS** | Nazwa unikatowa w skali globalnej | Unikatowa nazwa identyfikująca rejestru kontenerów. |
    | **Subskrypcja** | Wybierz subskrypcję | Subskrypcja platformy Azure do użycia. |
    | **[Grupa zasobów](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Nazwa grupy zasobów, w której chcesz utworzyć rejestru kontenerów. Wybierz **New** do tworzenia nowej grupy zasobów.|
    | **[SKU](https://docs.microsoft.com/azure/container-registry/container-registry-skus)** | Standardowa (Standard) | Warstwy usługi container Registry  |
    | **Lokalizacja w rejestrze** | Bliską lokalizację | Wybierz lokalizację w [region](https://azure.microsoft.com/regions/) okolicy lub w pobliżu innych usług używających usługi container registry. |

    ![Visual Studio utworzyć okno dialogowe usługi Azure Container Registry][0]

1. Kliknij przycisk **Utwórz**.

Możesz teraz ściągnąć kontenera z rejestru na dowolnym hoście może uruchamiać obrazy Docker, na przykład [usługi Azure Container Instances](/azure/container-instances/container-instances-tutorial-deploy-app).

## <a name="additional-resources"></a>Dodatkowe zasoby

* [Tworzenie kontenerów za pomocą programu Visual Studio](/visualstudio/containers)
* [Rozwiązywanie problemów z programowania Visual Studio 2017 przy użyciu rozwiązania Docker](vs-azure-tools-docker-troubleshooting-docker-errors.md)
* [Visual Studio Tools dla repozytorium GitHub platformy Docker](https://github.com/Microsoft/DockerTools)

[0]:media/vs-azure-tools-docker-hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png

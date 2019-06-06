---
title: Narzędzia kontenerów programu Visual Studio z platformą ASP.NET Core
author: ghogen
description: Dowiedz się, jak używać narzędzia kontenerów programu Visual Studio i platformy Docker for Windows
ms.author: ghogen
ms.date: 06/06/2019
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: b35a4c8a593129d2bdf72ab9eac2972611c8989f
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2019
ms.locfileid: "66748500"
---
# <a name="quickstart-use-docker-with-a-react-single-page-app-in-visual-studio"></a>Szybki start: Używać platformy Docker za pomocą aplikacji jednostronicowej platformy React w programie Visual Studio

Z programem Visual Studio można łatwo tworzyć, debugować i uruchamianie konteneryzowanych platformy ASP.NET Core aplikacji, łącznie z tymi za pomocą języka JavaScript po stronie klienta, takie jak aplikacja jednostronicowa React.js i publikowania ich w usłudze Azure Container Registry (ACR), usługi Docker Hub, Azure App Service lub własne Rejestr kontenerów. W tym artykule opublikujemy do usługi ACR.

## <a name="prerequisites"></a>Wymagania wstępne

::: moniker range="vs-2017"
* [Pulpitu platformy docker](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Program Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) z **programowania dla sieci Web**, **narzędzi Azure** obciążenia, i/lub **programowanie dla wielu platform .NET Core** zainstalowanym obciążeniem
* Publikowanie w usłudze Azure Container Registry w subskrypcji platformy Azure. [Zamów bezpłatną wersję próbną](https://azure.microsoft.com/offers/ms-azr-0044p/).
::: moniker-end
::: moniker range=">=vs-2019"
* [Pulpitu platformy docker](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) z **programowania dla sieci Web**, **narzędzi Azure** obciążenia, i/lub **programowanie dla wielu platform .NET Core** zainstalowanym obciążeniem
* [Narzędzia programistyczne programu .NET core 2.2](https://dotnet.microsoft.com/download/dotnet-core/2.2) podczas tworzenia aplikacji z platformy .NET Core 2.2
* Publikowanie w usłudze Azure Container Registry w subskrypcji platformy Azure. [Zamów bezpłatną wersję próbną](https://azure.microsoft.com/offers/ms-azr-0044p/).
::: moniker-end

## <a name="installation-and-setup"></a>Instalacja i Konfiguracja

Instalacja platformy Docker, najpierw zapoznaj się z informacjami o [pulpitu platformy Docker for Windows: Co należy wiedzieć przed zainstalowaniem](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install). Następnie zainstaluj [pulpitu platformy Docker](https://hub.docker.com/editions/community/docker-ce-desktop-windows).

## <a name="create-a-project-and-add-docker-support"></a>Utwórz projekt i Dodaj obsługę platformy Docker

::: moniker range="vs-2017"
1. Utwórz nowy projekt za pomocą **aplikacji sieci Web programu ASP.NET Core** szablonu.
1. Wybierz **React.js**. Nie można wybrać **włączyć obsługę platformy Docker**, ale nie martw się — po utworzeniu projektu można dodać obsługę.

   ![Zrzut ekranu przedstawiający nowy projekt z użyciem biblioteki React.js](media/container-tools-react/vs2017/new-react-project.png)

1. Kliknij prawym przyciskiem myszy węzeł projektu, a następnie wybierz **Dodaj** > **obsługę platformy Docker** można dodać pliku Dockerfile do projektu.

   ![Dodaj obsługę platformy Docker](media/container-tools-react/vs2017/add-docker-support.png)

1. Wybierz typ kontenera systemu Linux, a następnie kliknij przycisk **OK**.
::: moniker-end
::: moniker range=">=vs-2019"
1. Utwórz nowy projekt za pomocą **aplikacji sieci Web programu ASP.NET Core** szablonu.
1. Wybierz **React.js**i kliknij przycisk **Utwórz**. Nie można wybrać **włączyć obsługę platformy Docker**, ale nie martw się później możesz dodać obsługę.

   ![Zrzut ekranu przedstawiający nowy projekt z użyciem biblioteki React.js](media/container-tools-react/vs2019/new-react-project.png)

1. Kliknij prawym przyciskiem myszy węzeł projektu, a następnie wybierz **Dodaj** > **obsługę platformy Docker** można dodać pliku Dockerfile do projektu.

   ![Dodaj obsługę platformy Docker](media/container-tools-react/vs2017/add-docker-support.png)

1. Wybierz typ kontenera systemu Linux.
::: moniker-end

## <a name="dockerfile-overview"></a>Plik Dockerfile — omówienie

A *pliku Dockerfile*, przepisu do utworzenia końcowej obrazu platformy Docker jest tworzony w projekcie. Zapoznaj się [odwołanie do pliku Dockerfile](https://docs.docker.com/engine/reference/builder/) dla zrozumienia poleceń w nim.

Otwórz *pliku Dockerfile* w projekcie i dodaj następujące wiersze do instalowania programu Node.js 10.x w kontenerze. Pamiętaj dodać następujące wiersze w pierwszej sekcji, aby dodać instalacji programu Node package manager *npm.exe* na podstawowy obraz, który jest używany w kolejnych krokach.

```
RUN curl -sL https://deb.nodesource.com/setup_10.x |  bash -
RUN apt-get install -y nodejs
```

*Pliku Dockerfile* powinien teraz wyglądać mniej więcej tak:

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

Poprzedni *pliku Dockerfile* opiera się na [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) obrazu i zawiera instrukcje dotyczące modyfikowania obraz podstawowy, tworząc projekt i dodanie go do kontenera.

Gdy okno dialogowe nowego projektu w **Konfigurowanie protokołu HTTPS** pole wyboru jest zaznaczone, *pliku Dockerfile* udostępnia dwa porty. Jeden port jest używany do ruchu HTTP; inne port jest używany do obsługi protokołu HTTPS. Jeśli nie jest zaznaczone pole wyboru, jednego portu (80) jest uwidaczniany dla ruchu HTTP.

## <a name="debug"></a>Debugowanie

Wybierz **Docker** z poziomu pozycji Debuguj listy rozwijanej w pasku narzędzi, a następnie uruchamiania, debugowania aplikacji. Może pojawić się komunikat, wraz z monitem o o ufanie certyfikat; Wybierz zaufać certyfikatowi, aby kontynuować.

**Narzędzia kontenerów** opcji **dane wyjściowe** okno pokazuje, jakie akcje pojawiają się. Powinien zostać wyświetlony kroki instalacji, skojarzone z *npm.exe*.

Przeglądarka pokazuje strony głównej aplikacji.

::: moniker range="vs-2017"
   ![Zrzut ekranu przedstawiający uruchamianie aplikacji](media/container-tools-react/vs2017/running-app.png)
::: moniker-end
::: moniker range=">=vs-2019"
   ![Zrzut ekranu przedstawiający uruchamianie aplikacji](media/container-tools-react/vs2019/running-app.png)
::: moniker-end

Spróbuj przejść do *licznika* strony i przetestuj kod po stronie klienta dla licznika, klikając **przyrostu** przycisku.

Otwórz **Konsola Menedżera pakietów** (PMC) z menu **narzędzia**> Menedżer pakietów NuGet, **Konsola Menedżera pakietów**.

Wynikowy obraz platformy Docker w aplikacji zostanie oznaczony jako *dev*. Obraz, który jest oparty na *2.2-aspnetcore-środowiska uruchomieniowego* tag *microsoft/dotnet* obrazu podstawowego. Uruchom `docker images` polecenia w pliku **Konsola Menedżera pakietów** okna (PMC). Wyświetlane są obrazy na komputerze:

```console
REPOSITORY        TAG                     IMAGE ID      CREATED         SIZE
webapplication37  dev                     d72ce0f1dfe7  30 seconds ago  255MB
microsoft/dotnet  2.2-aspnetcore-runtime  fcc3887985bb  6 days ago      255MB
```

> [!NOTE]
> **Dev** obraz nie zawiera plików binarnych aplikacji i innej zawartości jako **debugowania** konfiguracje używają instalowania woluminów iteracji edytowanie i debugowanie. Aby utworzyć obraz produkcji zawierające całą zawartość, należy użyć **wersji** konfiguracji.

Uruchom `docker ps` polecenia w konsoli zarządzania Pakietami. Zwróć uwagę, że aplikacja jest uruchomiona przy użyciu kontenera:

```console
CONTAINER ID        IMAGE                  COMMAND               CREATED             STATUS              PORTS                                           NAMES
cf5d2ef5f19a        webapplication37:dev   "tail -f /dev/null"   2 minutes ago       Up 2 minutes        0.0.0.0:52036->80/tcp, 0.0.0.0:44342->443/tcp   priceless_cartwright
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

   ![Zrzut ekranu przedstawiający pomyślne publikowanie](media/container-tools/publish-succeeded.png)

## <a name="next-steps"></a>Następne kroki

Możesz teraz ściągnąć kontenera z rejestru na dowolnym hoście może uruchamiać obrazy Docker, na przykład [usługi Azure Container Instances](/azure/container-instances/container-instances-tutorial-deploy-app).

## <a name="additional-resources"></a>Dodatkowe zasoby

* [Tworzenie kontenerów za pomocą programu Visual Studio](/visualstudio/containers)
* [Rozwiązywanie problemów z programowania Visual Studio z platformą Docker](troubleshooting-docker-errors.md)
* [Repozytorium programu Visual Studio kontenera narzędzi w witrynie GitHub](https://github.com/Microsoft/DockerTools)

::: moniker range="vs-2017"
[0]:media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png
::: moniker-end
::: moniker range=">=vs-2019"
[0]:media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog-2019.png
::: moniker-end
---
title: Wdróż kontener platformy Docker ASP.NET w rejestrze ACR
description: Dowiedz się, jak używać narzędzi kontenera programu Visual Studio do wdrażania aplikacji sieci Web ASP.NET lub ASP.NET Core w rejestrze kontenerów
author: ghogen
manager: jillfra
ms.assetid: e5e81c5e-dd18-4d5a-a24d-a932036e78b9
ms.devlang: dotnet
ms.topic: how-to
ms.technology: vs-azure
ms.date: 03/14/2019
ms.author: ghogen
ms.openlocfilehash: 4626b64f5e733fec049d56dfe53407cc0fe31566
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "88168705"
---
# <a name="deploy-an-aspnet-container-to-a-container-registry-using-visual-studio"></a>Wdrażanie kontenera platformy ASP.NET w rejestrze kontenerów przy użyciu programu Visual Studio

## <a name="overview"></a>Omówienie

Docker to lekki aparat kontenerów, podobny na kilka sposobów na maszynę wirtualną, której można używać do hostowania aplikacji i usług.
Ten samouczek przeprowadzi Cię przez program Visual Studio w celu opublikowania aplikacji w kontenerze w [Azure Container Registry](https://azure.microsoft.com/services/container-registry).

Jeśli nie masz subskrypcji platformy Azure, przed rozpoczęciem utwórz [bezpłatne konto](https://azure.microsoft.com/free/dotnet/?utm_source=acr-publish-doc&utm_medium=docs&utm_campaign=docs).

## <a name="prerequisites"></a>Wymagania wstępne

W celu ukończenia tego samouczka:

::: moniker range="vs-2017"
* Zainstaluj najnowszą wersję programu [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)z obciążeniem "ASP.NET and Web Development"
::: moniker-end
::: moniker range=">=vs-2019"
* Zainstaluj najnowszą wersję programu [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) z obciążeniem "ASP.NET and Web Development"
::: moniker-end
* Zainstaluj [Docker for Windows](https://docs.docker.com/docker-for-windows/install/)

## <a name="create-an-aspnet-core-web-app"></a>Tworzenie aplikacji internetowej ASP.NET Core

Poniższe kroki przeprowadzą Cię przez proces tworzenia podstawowej aplikacji ASP.NET Core, która będzie używana w tym samouczku. Jeśli masz już projekt, możesz pominąć tę sekcję.

::: moniker range="vs-2017"
[!INCLUDE [create-aspnet5-app](../azure/includes/create-aspnet5-app.md)]
::: moniker-end
::: moniker range=">=vs-2019"
[!INCLUDE [create-aspnet5-app](../azure/includes/vs-2019/create-aspnet5-app-2019.md)]
::: moniker-end

::: moniker range="vs-2017"

## <a name="publish-your-container-to-azure-container-registry"></a>Publikowanie kontenera do Azure Container Registry

1. Kliknij prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** i wybierz polecenie **Publikuj**.
2. W oknie dialogowym **Publikowanie elementu docelowego** wybierz pozycję **Container Registry**.
3. Wybierz opcję **nowy Azure Container Registry** i kliknij przycisk **Publikuj**.
4. Wypełnij odpowiednie wartości w polu **Utwórz nową Azure Container Registry**.

    | Ustawienie      | Sugerowana wartość  | Opis                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **Prefiks DNS** | Nazwa unikatowa w skali globalnej | Nazwa, która jednoznacznie identyfikuje rejestr kontenerów. |
    | **Subskrypcja** | Wybierz subskrypcję | Subskrypcja platformy Azure, która ma być używana. |
    | **[Grupa zasobów](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Nazwa grupy zasobów, w której ma zostać utworzony rejestr kontenerów. Wybierz pozycję **Nowa**, aby utworzyć nową grupę zasobów.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Standard | Warstwa usług w rejestrze kontenerów  |
    | **Lokalizacja rejestru** | Lokalizacja blisko Ciebie | Wybierz lokalizację w [regionie](https://azure.microsoft.com/regions/) blisko siebie lub w najbliższej innej usłudze, która będzie korzystać z rejestru kontenerów. |

    ![Okno dialogowe tworzenia Azure Container Registry programu Visual Studio](media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png)

5. Kliknij pozycję **Utwórz**
::: moniker-end

::: moniker range=">=vs-2019"
## <a name="publish-your-container-to-azure-container-registry"></a>Publikowanie kontenera do Azure Container Registry
1. Kliknij prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** i wybierz polecenie **Publikuj**.
2. W oknie dialogowym **Publikowanie** wybierz pozycję **Docker Container Registry**.

   ![Zrzut ekranu przedstawiający okno dialogowe publikowania — wybierz Container Registry Docker](media/container-tools/vs-2019/docker-container-registry.png)

3. Wybierz pozycję **Utwórz nowe Azure Container Registry**.
 
   ![Zrzut ekranu przedstawiający okno dialogowe publikowania — wybierz pozycję Utwórz nowe Azure Container Registry](media/container-tools/vs-2019/select-existing-or-create-new-azure-container-registry.png)

4. Wypełnij odpowiednie wartości na ekranie **Azure Container Registry** .

    | Ustawienie      | Sugerowana wartość  | Opis                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **Prefiks DNS** | Nazwa unikatowa w skali globalnej | Nazwa, która jednoznacznie identyfikuje rejestr kontenerów. |
    | **Subskrypcja** | Wybierz subskrypcję | Subskrypcja platformy Azure, która ma być używana. |
    | **[Grupa zasobów](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Nazwa grupy zasobów, w której ma zostać utworzony rejestr kontenerów. Wybierz pozycję **Nowa**, aby utworzyć nową grupę zasobów.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Standard | Warstwa usług w rejestrze kontenerów  |
    | **Lokalizacja rejestru** | Lokalizacja blisko Ciebie | Wybierz lokalizację w [regionie](https://azure.microsoft.com/regions/) blisko siebie lub w najbliższej innej usłudze, która będzie korzystać z rejestru kontenerów. |

    ![Okno dialogowe tworzenia Azure Container Registry programu Visual Studio](media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog-2019.png)

5. Kliknij przycisk **Utwórz**.

6. Wybierz przycisk **Zakończ** , aby ukończyć proces.
::: moniker-end

Teraz można ściągnąć kontener z rejestru do dowolnego hosta, który może uruchamiać obrazy platformy Docker, na przykład [Azure Container Instances](/azure/container-instances/container-instances-tutorial-deploy-app).

## <a name="see-also"></a>Zobacz też

[Szybki Start: Wdrażanie wystąpienia kontenera na platformie Azure przy użyciu interfejsu wiersza polecenia platformy Azure](/azure/container-instances/container-instances-quickstart)

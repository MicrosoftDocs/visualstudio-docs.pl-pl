---
title: Wdrażanie kontenera platformy Docker programu ASP.NET do usługi Azure Container Registry (ACR) | Dokumentacja firmy Microsoft
description: Dowiedz się, jak wdrożyć aplikację sieci web platformy ASP.NET Core do rejestru kontenerów za pomocą programu Visual Studio Tools for Docker
author: ghogen
manager: jillfra
ms.assetid: e5e81c5e-dd18-4d5a-a24d-a932036e78b9
ms.devlang: dotnet
ms.topic: conceptual
ms.technology: vs-azure
ms.date: 03/14/2019
ms.author: ghogen
ms.openlocfilehash: d287d26b9807876d99b4bed871c464a3130e627f
ms.sourcegitcommit: d78821f8c353e0102b1554719f549f32dffac71b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2019
ms.locfileid: "58515173"
---
# <a name="deploy-an-aspnet-container-to-a-container-registry-using-visual-studio"></a>Wdrażanie kontenera platformy ASP.NET w rejestrze kontenerów przy użyciu programu Visual Studio

## <a name="overview"></a>Omówienie

Docker to aparat uproszczone kontenera, podobne pod pewnymi względami na maszynę wirtualną, której można użyć do hostowania aplikacji i usług.
Ten samouczek przeprowadzi Cię przez publikowanie konteneryzowaną aplikację przy użyciu programu Visual Studio [usługi Azure Container Registry](https://azure.microsoft.com/services/container-registry).

Jeśli nie masz subskrypcji platformy Azure, przed rozpoczęciem utwórz [bezpłatne konto](https://azure.microsoft.com/free/dotnet/?utm_source=acr-publish-doc&utm_medium=docs&utm_campaign=docs).

## <a name="prerequisites"></a>Wymagania wstępne

Do ukończenia tego samouczka:

::: moniker range="vs-2017"
* Zainstaluj najnowszą wersję [programu Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)z obciążeniem "programowanie aplikacji platformy ASP.NET i sieci web"
::: moniker-end
::: moniker range=">=vs-2019"
* Zainstaluj najnowszą wersję [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019+rc) z obciążeniem "programowanie aplikacji platformy ASP.NET i sieci web"
::: moniker-end
* Zainstaluj [Docker for Windows](https://docs.docker.com/docker-for-windows/install/)

## <a name="create-an-aspnet-core-web-app"></a>Tworzenie aplikacji internetowej platformy ASP.NET Core
Poniższe kroki prowadzą przez proces tworzenia podstawowej aplikacji platformy ASP.NET Core, który będzie używany w ramach tego samouczka.

::: moniker range="vs-2017"
[!INCLUDE [create-aspnet5-app](../azure/includes/create-aspnet5-app.md)]
::: moniker-end
::: moniker range=">=vs-2019"
[!INCLUDE [create-aspnet5-app](../azure/includes/vs-2019/create-aspnet5-app-2019.md)]
::: moniker-end

## <a name="publish-your-container-to-azure-container-registry"></a>Opublikowany kontener w usłudze Azure Container Registry
1. Kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierz polecenie **Publikuj**.
2. W oknie dialogowym docelowej publikowania wybierz **Container Registry** kartę.
3. Wybierz **nowy rejestr Azure Container Registry** i kliknij przycisk **Publikuj**.
4. Wprowadź żądane wartości w **Utwórz nowy rejestr Azure Container Registry**.

    | Ustawienie      | Sugerowana wartość  | Opis                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **Prefiks DNS** | Nazwa unikatowa w skali globalnej | Unikatowa nazwa identyfikująca rejestru kontenerów. |
    | **Subskrypcja** | Wybierz subskrypcję | Subskrypcja platformy Azure do użycia. |
    | **[Grupa zasobów](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Nazwa grupy zasobów, w której chcesz utworzyć rejestru kontenerów. Wybierz **New** do tworzenia nowej grupy zasobów.|
    | **[SKU](https://docs.microsoft.com/azure/container-registry/container-registry-skus)** | Standardowa (Standard) | Warstwy usługi container Registry  |
    | **Lokalizacja w rejestrze** | Bliską lokalizację | Wybierz lokalizację w [region](https://azure.microsoft.com/regions/) okolicy lub w pobliżu innych usług używających usługi container registry. |

    ![Visual Studio utworzyć okno dialogowe usługi Azure Container Registry](media/vs-azure-tools-docker-hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png)

5. Kliknij przycisk **Utwórz**.

Możesz teraz ściągnąć kontenera z rejestru na dowolnym hoście może uruchamiać obrazy Docker, na przykład [usługi Azure Container Instances](/azure/container-instances/container-instances-tutorial-deploy-app).
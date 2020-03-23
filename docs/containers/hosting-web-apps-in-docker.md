---
title: Wdrażanie kontenera platformy Docker ASP.NET w rejestrze usługi ACR
description: Dowiedz się, jak wdrożyć ASP.NET lub ASP.NET core w rejestrze kontenerów za pomocą narzędzi kontenerowych programu Visual Studio
author: ghogen
manager: jillfra
ms.assetid: e5e81c5e-dd18-4d5a-a24d-a932036e78b9
ms.devlang: dotnet
ms.topic: conceptual
ms.technology: vs-azure
ms.date: 03/14/2019
ms.author: ghogen
ms.openlocfilehash: cfed918633f62700f464ee5f9911fbbfc6463c36
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75916913"
---
# <a name="deploy-an-aspnet-container-to-a-container-registry-using-visual-studio"></a>Wdrażanie kontenera platformy ASP.NET w rejestrze kontenerów przy użyciu programu Visual Studio

## <a name="overview"></a>Omówienie

Docker to lekki aparat kontenera, podobny pod pewnymi względami do maszyny wirtualnej, której można używać do obsługi aplikacji i usług.
W tym samouczku można zapoznać się z publikowaniem aplikacji konteneryzowanych w [usłudze Azure Container Registry](https://azure.microsoft.com/services/container-registry)za pomocą programu Visual Studio.

Jeśli nie masz subskrypcji platformy Azure, utwórz [bezpłatne konto](https://azure.microsoft.com/free/dotnet/?utm_source=acr-publish-doc&utm_medium=docs&utm_campaign=docs) przed rozpoczęciem.

## <a name="prerequisites"></a>Wymagania wstępne

W celu ukończenia tego samouczka:

::: moniker range="vs-2017"
* Instalowanie najnowszej wersji [programu Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)z obciążeniem "ASP.NET i tworzenia sieci Web"
::: moniker-end
::: moniker range=">=vs-2019"
* Instalowanie najnowszej wersji [programu Visual Studio 2019](https://visualstudio.microsoft.com/downloads) z obciążeniem "ASP.NET i tworzenia stron internetowych"
::: moniker-end
* Instalowanie [platformy Docker dla systemu Windows](https://docs.docker.com/docker-for-windows/install/)

## <a name="create-an-aspnet-core-web-app"></a>Tworzenie aplikacji internetowej ASP.NET Core
Poniższe kroki prowadzą użytkownika przez tworzenie podstawowej aplikacji core ASP.NET, która będzie używana w tym samouczku. Jeśli masz już projekt, możesz pominąć tę sekcję.

::: moniker range="vs-2017"
[!INCLUDE [create-aspnet5-app](../azure/includes/create-aspnet5-app.md)]
::: moniker-end
::: moniker range=">=vs-2019"
[!INCLUDE [create-aspnet5-app](../azure/includes/vs-2019/create-aspnet5-app-2019.md)]
::: moniker-end

## <a name="publish-your-container-to-azure-container-registry"></a>Publikowanie kontenera w rejestrze kontenerów platformy Azure
1. Kliknij prawym przyciskiem myszy projekt w **Eksploratorze rozwiązań** i wybierz polecenie **Publikuj**.
2. W oknie dialogowym publikowania obiektu docelowego wybierz kartę **Rejestr kontenerów.**
3. Wybierz **pozycję Nowy rejestr kontenerów platformy Azure** i kliknij pozycję **Publikuj**.
4. Wypełnij żądane wartości w obszarze **Utwórz nowy rejestr kontenerów platformy Azure**.

    | Ustawienie      | Sugerowana wartość  | Opis                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **Prefiks DNS** | Nazwa unikatowa w skali globalnej | Nazwa, która jednoznacznie identyfikuje rejestr kontenerów. |
    | **Subskrypcja** | Wybierz subskrypcję | Subskrypcja platformy Azure, która ma być używana. |
    | **[Grupa zasobów](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Nazwa grupy zasobów, w której ma być utworzony rejestr kontenerów. Wybierz pozycję **Nowa**, aby utworzyć nową grupę zasobów.|
    | **[Numer jednostki magazynowej](/azure/container-registry/container-registry-skus)** | Standardowa | Warstwa usługi rejestru kontenerów  |
    | **Lokalizacja rejestru** | Lokalizacja blisko Ciebie | Wybierz lokalizację w [regionie](https://azure.microsoft.com/regions/) w pobliżu lub w pobliżu innych usług, które będą korzystać z rejestru kontenerów. |

    ![Okno dialogowe tworzenia kontenera usługi Azure w programie Visual Studio](media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png)

5. Kliknij **przycisk Utwórz**

Teraz można wyciągnąć kontener z rejestru do dowolnego hosta zdolnego do uruchamiania obrazów platformy Docker, na przykład [wystąpienia kontenera platformy Azure.](/azure/container-instances/container-instances-tutorial-deploy-app)

## <a name="see-also"></a>Zobacz też

[Szybki start: wdrażanie wystąpienia kontenera na platformie Azure przy użyciu interfejsu wiersza polecenia platformy Azure](/azure/container-instances/container-instances-quickstart)

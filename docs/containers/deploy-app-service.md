---
title: Wdróż kontener Docker ASP.NET Core, aby Azure App Service | Microsoft Docs
description: Dowiedz się, jak używać narzędzi kontenerów programu Visual Studio do wdrażania aplikacji internetowej ASP.NET Core w Azure App Service
author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.devlang: dotnet
ms.topic: article
ms.date: 01/27/2020
ms.author: ghogen
ms.openlocfilehash: 6c1d56f788294826853ad441313597255308bb39
ms.sourcegitcommit: b2fc9ac7d73c847508f6ed082bed026476bb3955
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/05/2020
ms.locfileid: "77027290"
---
# <a name="deploy-an-aspnet-core-container-to-azure-app-service-using-visual-studio"></a>Wdrażanie kontenera ASP.NET Core do Azure App Service przy użyciu programu Visual Studio

Ten samouczek przeprowadzi Cię przez program Visual Studio w celu opublikowania ASP.NET Core aplikacji sieci Web w kontenerze [Azure App Service](/azure/app-service). Azure App Service to odpowiednia usługa dla aplikacji sieci Web o jednym kontenerze hostowanej na platformie Azure.

Jeśli nie masz subskrypcji platformy Azure, przed rozpoczęciem utwórz [bezpłatne konto](https://azure.microsoft.com/free/dotnet/?utm_source=acr-publish-doc&utm_medium=docs&utm_campaign=docs).

## <a name="prerequisites"></a>Wymagania wstępne

W celu ukończenia tego samouczka:

::: moniker range="vs-2017"
- Zainstaluj najnowszą wersję programu [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) z obciążeniem "ASP.NET and Web Development"
::: moniker-end
::: moniker range=">=vs-2019"
- [Program Visual Studio 2019](https://visualstudio.microsoft.com/downloads) z *ASP.NET i programowaniem w sieci Web* .
::: moniker-end
- Zainstaluj program [Docker Desktop](https://docs.docker.com/docker-for-windows/install/)

## <a name="create-an-aspnet-core-web-app"></a>Tworzenie aplikacji internetowej ASP.NET Core

Poniższe kroki przeprowadzą Cię przez proces tworzenia podstawowej aplikacji ASP.NET Core, która będzie używana w tym samouczku.

::: moniker range="vs-2017"
1. Z menu programu Visual Studio wybierz pozycję **plik > nowy > projekt**.
2. W sekcji **Szablony** okna dialogowego **Nowy projekt** wybierz pozycję  **C# Visual > Web**.
3. Wybierz **ASP.NET Core aplikacji sieci Web**.
4. Nadaj nowej aplikacji nazwę (lub wybierz ją domyślną), a następnie kliknij **przycisk OK**.
5. Wybierz pozycję **aplikacja sieci Web**.
6. Zaznacz pole wyboru **Włącz obsługę platformy Docker** .
7. Wybierz typ kontenera systemu **Linux** i kliknij przycisk **OK**. Kontenery systemu Windows nie są obsługiwane do wdrażania w Azure App Service jako kontener.
::: moniker-end
::: moniker range=">= vs-2019"
1. W oknie Start programu Visual Studio wybierz pozycję **Utwórz nowy projekt**.
1. Wybierz **ASP.NET Core aplikacji sieci Web**, a następnie wybierz przycisk **dalej**.
1. Nadaj nowej aplikacji nazwę (lub wybierz ją domyślną), a następnie kliknij pozycję **Utwórz**.
1. Wybierz pozycję **aplikacja sieci Web**.
1. Wybierz, czy ma być obsługiwana obsługa protokołu SSL, przy użyciu pola wyboru **Konfiguruj dla protokołu HTTPS** .
1. Zaznacz pole wyboru **Włącz obsługę platformy Docker** .
1. Wybierz typ kontenera, a następnie kliknij przycisk **Utwórz**. Kontenery systemu Windows nie są obsługiwane do wdrażania w Azure App Service jako kontener.
::: moniker-end

## <a name="deploy-the-container-to-azure"></a>Wdrażanie kontenera na platformie Azure

1. Kliknij prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** i wybierz polecenie **Publikuj**.
1. W oknie dialogowym Publikowanie elementu docelowego wybierz pozycję **App Service Linux** lub **App Service**. Jest to system operacyjny, który będzie obsługiwał serwer sieci Web.
1. Możesz publikować tylko do App Service lub można publikować w App Service i Azure Container Registry (ACR). Aby opublikować kontener w Azure Container Registry (ACR), wybierz opcję **Utwórz nowe App Service dla kontenerów**, a następnie kliknij przycisk **Publikuj**.

   ![Zrzut ekranu okna dialogowego publikowania](media/deploy-app-service/publish-app-service-linux.PNG)

   Aby opublikować tylko Azure App Service bez używania Azure Container Registry, wybierz pozycję **Utwórz nowy**, a następnie kliknij pozycję **Publikuj**.

1. Sprawdź, czy zalogowano się przy użyciu konta skojarzonego z subskrypcją platformy Azure, a następnie wybierz unikatową nazwę, subskrypcję, grupę zasobów, plan hostingu i rejestr kontenerów (jeśli dotyczy) lub zaakceptuj ustawienia domyślne.

   ![Zrzut ekranu przedstawiający ustawienia publikowania](media/deploy-app-service/publish-app-service-linux2.png)

1. Wybierz pozycję **Utwórz**. Kontener zostanie wdrożony na platformie Azure w wybranej grupie zasobów i rejestrze kontenerów. Ten proces trwa nieco czasu. Po zakończeniu karta **Publikowanie** zawiera informacje o tym, co zostało opublikowane, łącznie z adresem URL witryny.

   ![Zrzut ekranu przedstawiający kartę publikowanie](media/deploy-app-service/publish-succeeded.PNG)

1. Kliknij link lokacji, aby sprawdzić, czy aplikacja działa zgodnie z oczekiwaniami na platformie Azure.

   ![Zrzut ekranu aplikacji sieci Web](media/deploy-app-service/web-application-running.png)

1. Profil publikowania jest zapisywany ze wszystkimi wybranymi szczegółami, takimi jak grupa zasobów i rejestr kontenerów.

1. Aby ponownie wykonać wdrożenie z tym samym profilem publikowania, użyj przycisku **Publikuj** , przycisku **Publikuj** w oknie **działanie publikowania w sieci Web** lub kliknij prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** i wybierz polecenie **Publikuj** element w menu kontekstowym.

## <a name="view-container-settings"></a>Wyświetl ustawienia kontenera

W [Azure Portal](https://portal.azure.com)można otworzyć wdrożony App Service.

Ustawienia dla wdrożonego App Service można wyświetlić, otwierając menu **Ustawienia kontenera* (w przypadku korzystania z programu Visual Studio 2019 w wersji 16,4 lub nowszej).

![Zrzut ekranu przedstawiający menu Ustawienia kontenera w Azure Portal](media/deploy-app-service/container-settings-menu.png)

W tym miejscu można wyświetlić informacje o kontenerze, wyświetlić lub pobrać dzienniki albo skonfigurować ciągłe wdrażanie. Zobacz [Azure App Service ciągłej integracji/ciągłego wdrażania](/azure/app-service/containers/app-service-linux-ci-cd).

## <a name="clean-up-resources"></a>Oczyszczanie zasobów

Aby usunąć wszystkie zasoby platformy Azure skojarzone z tym samouczkiem, Usuń grupę zasobów przy użyciu [Azure Portal](https://portal.azure.com). Aby znaleźć grupę zasobów skojarzoną z opublikowaną aplikacją sieci Web, wybierz pozycję **wyświetl** > inne **działanie publikowania w sieci Web** > **Windows** , a następnie wybierz ikonę koła zębatego. Zostanie otwarta karta **Publikowanie** , która zawiera grupę zasobów.

W Azure Portal wybierz pozycję **grupy zasobów**, a następnie wybierz grupę zasobów, aby otworzyć jej stronę szczegółów. Sprawdź, czy jest to poprawna Grupa zasobów, a następnie wybierz pozycję **Usuń grupę zasobów**, wpisz nazwę i wybierz pozycję **Usuń**.

## <a name="next-steps"></a>Następne kroki

Dowiedz się więcej na temat [Azure App Service Linux](/azure/app-service/containers/app-service-linux-intro).

## <a name="see-also"></a>Zobacz też

[Wdróż do Azure Container Registry](hosting-web-apps-in-docker.md)
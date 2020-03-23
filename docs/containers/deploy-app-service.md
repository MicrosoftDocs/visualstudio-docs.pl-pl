---
title: Wdrażanie kontenera ASP.NET Core Docker w usłudze Azure App Service | Dokumenty firmy Microsoft
description: Dowiedz się, jak wdrożyć aplikację internetową ASP.NET Core w usłudze Azure App Service za pomocą narzędzi kontenerowych programu Visual Studio
author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.devlang: dotnet
ms.topic: article
ms.date: 01/27/2020
ms.author: ghogen
ms.openlocfilehash: 6c1d56f788294826853ad441313597255308bb39
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77027290"
---
# <a name="deploy-an-aspnet-core-container-to-azure-app-service-using-visual-studio"></a>Wdrażanie kontenera ASP.NET Core w usłudze Azure App Service przy użyciu programu Visual Studio

W tym samouczku można przejść przez za pomocą programu Visual Studio, aby opublikować konteneryzowany ASP.NET podstawowej aplikacji sieci web do [usługi Azure App Service](/azure/app-service). Usługa Azure App Service to odpowiednia usługa dla aplikacji sieci web z jednym kontenerem hostowanych na platformie Azure.

Jeśli nie masz subskrypcji platformy Azure, utwórz [bezpłatne konto](https://azure.microsoft.com/free/dotnet/?utm_source=acr-publish-doc&utm_medium=docs&utm_campaign=docs) przed rozpoczęciem.

## <a name="prerequisites"></a>Wymagania wstępne

W celu ukończenia tego samouczka:

::: moniker range="vs-2017"
- Instalowanie najnowszej wersji [programu Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) z obciążeniem "ASP.NET i tworzenia sieci Web"
::: moniker-end
::: moniker range=">=vs-2019"
- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) z *obciążeniem ASP.NET i tworzenia sieci Web.*
::: moniker-end
- Instalowanie [pulpitu platformy Docker](https://docs.docker.com/docker-for-windows/install/)

## <a name="create-an-aspnet-core-web-app"></a>Tworzenie aplikacji internetowej ASP.NET Core

Poniższe kroki prowadzą użytkownika przez tworzenie podstawowej aplikacji core ASP.NET, która będzie używana w tym samouczku.

::: moniker range="vs-2017"
1. Z menu Visual Studio wybierz polecenie **Plik > Nowy projekt >**.
2. W sekcji **Szablony** w oknie dialogowym **Nowy projekt** wybierz pozycję **Visual C# > Web**.
3. Wybierz **ASP.NET podstawową aplikację sieci Web**.
4. Nadaj nowej aplikacji nazwę (lub zrób wartość domyślną) i wybierz **przycisk OK**.
5. Wybierz **aplikację sieci Web**.
6. Zaznacz pole wyboru **Włącz obsługę platformy Docker.**
7. Wybierz typ kontenera **systemu Linux** i kliknij przycisk **OK**. Kontenery systemu Windows nie są obsługiwane do wdrożenia w usłudze Azure App Service jako kontener.
::: moniker-end
::: moniker range=">= vs-2019"
1. W oknie startowym programu Visual Studio wybierz pozycję **Utwórz nowy projekt**.
1. Wybierz **ASP.NET Core Web Application**i wybierz pozycję **Dalej**.
1. Nadaj nowej aplikacji nazwę (lub zrób wartość domyślną) i wybierz pozycję **Utwórz**.
1. Wybierz **pozycję Aplikacja sieci Web**.
1. Wybierz, czy chcesz obsługiwać protokół SSL, korzystając z pola wyboru **Konfiguruj dla protokołu HTTPS.**
1. Zaznacz pole wyboru **Włącz obsługę platformy Docker.**
1. Zaznacz typ kontenera i kliknij przycisk **Utwórz**. Kontenery systemu Windows nie są obsługiwane do wdrożenia w usłudze Azure App Service jako kontener.
::: moniker-end

## <a name="deploy-the-container-to-azure"></a>Wdrażanie kontenera na platformie Azure

1. Kliknij prawym przyciskiem myszy projekt w **Eksploratorze rozwiązań** i wybierz polecenie **Publikuj**.
1. W oknie dialogowym publikowania docelowego wybierz pozycję **App Service Linux** lub App **Service**. Jest to system operacyjny, który będzie obsługiwał serwer www.
1. Można publikować tylko w usłudze App Service lub można publikować zarówno w usłudze App Service, jak i w usłudze Azure Container Registry (ACR). Aby opublikować kontener w rejestrze kontenerów platformy Azure (ACR), wybierz pozycję **Utwórz nową usługę app service dla kontenerów**i kliknij przycisk **Publikuj**.

   ![Zrzut ekranu przedstawiający okno dialogowe publikowania](media/deploy-app-service/publish-app-service-linux.PNG)

   Aby publikować tylko w usłudze Azure App Service bez korzystania z rejestru kontenerów platformy Azure, wybierz pozycję **Utwórz nowe**i kliknij pozycję **Publikuj**.

1. Sprawdź, czy zalogowano się przy za pomocą konta skojarzonego z subskrypcją platformy Azure, i wybierz unikatową nazwę, subskrypcję, grupę zasobów, plan hostingowy i rejestr kontenerów (jeśli dotyczy) lub zaakceptuj ustawienia domyślne.

   ![Zrzut ekranu przedstawiający ustawienia publikowania](media/deploy-app-service/publish-app-service-linux2.png)

1. Wybierz pozycję **Utwórz**. Kontener jest wdrażany na platformie Azure w wybranej grupie zasobów i rejestrze kontenerów. Ten proces zajmuje trochę czasu. Po zakończeniu na karcie **Publikowanie** są wyświetlane informacje o tym, co zostało opublikowane, w tym adres URL witryny.

   ![Zrzut ekranu przedstawiający kartę publikowania](media/deploy-app-service/publish-succeeded.PNG)

1. Kliknij łącze witryny, aby sprawdzić, czy aplikacja działa zgodnie z oczekiwaniami na platformie Azure.

   ![Zrzut ekranu przedstawiający aplikację internetową](media/deploy-app-service/web-application-running.png)

1. Profil publikowania jest zapisywany ze wszystkimi wybranymi szczegółami, takimi jak grupa zasobów i rejestr kontenerów.

1. Aby ponownie wdrożyć go przy użyciu tego samego profilu publikowania, użyj przycisku **Publikuj,** przycisku **Publikuj** w oknie **Aktywność publikowania** w sieci Web lub kliknij prawym przyciskiem myszy projekt w **Eksploratorze rozwiązań** i wybierz element **Publikowania** w menu kontekstowym.

## <a name="view-container-settings"></a>Wyświetlanie ustawień kontenera

W [witrynie Azure portal](https://portal.azure.com)można otworzyć wdrożoną usługę app service.

Ustawienia wdrożonej usługi App Service można wyświetlić, otwierając menu ** Ustawienia kontenera* (podczas korzystania z programu Visual Studio 2019 w wersji 16.4 lub nowszej).

![Zrzut ekranu przedstawiający menu Ustawienia kontenerów w witrynie Azure portal](media/deploy-app-service/container-settings-menu.png)

W tym miejscu można wyświetlić informacje o kontenerze, wyświetlić lub pobrać dzienniki lub skonfigurować ciągłe wdrażanie. Zobacz [ciągłe wdrażanie ciągłego wdrażania usługi Azure App Service,2/CD](/azure/app-service/containers/app-service-linux-ci-cd).

## <a name="clean-up-resources"></a>Oczyszczanie zasobów

Aby usunąć wszystkie zasoby platformy Azure skojarzone z tym samouczkiem, usuń grupę zasobów za pomocą [witryny Azure portal](https://portal.azure.com). Aby znaleźć grupę zasobów skojarzoną z opublikowaną aplikacją sieci Web, wybierz pozycję **Wyświetl** > inne**działanie publikowania w sieci Web**systemu**Windows,** > a następnie wybierz ikonę koła zębatego. Zostanie otwarta karta **Publikowanie** zawierająca grupę zasobów.

W witrynie Azure Portal wybierz pozycję **Grupy zasobów**, wybierz grupę zasobów, aby otworzyć jej stronę szczegółów. Sprawdź, czy jest to poprawna grupa zasobów, a następnie wybierz pozycję **Usuń grupę zasobów**, wpisz nazwę i wybierz pozycję **Usuń**.

## <a name="next-steps"></a>Następne kroki

Dowiedz się więcej o [usłudze Azure App Service Linux](/azure/app-service/containers/app-service-linux-intro).

## <a name="see-also"></a>Zobacz też

[Wdrażanie w rejestrze kontenerów platformy Azure](hosting-web-apps-in-docker.md)
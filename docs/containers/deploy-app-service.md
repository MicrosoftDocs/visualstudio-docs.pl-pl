---
title: Wdrażanie kontenera platformy Docker programu ASP.NET Core w usłudze Azure App Service | Dokumentacja firmy Microsoft
description: Dowiedz się, jak wdrożyć aplikację internetową platformy ASP.NET Core w usłudze Azure App Service za pomocą narzędzia kontenerów programu Visual Studio
author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.devlang: dotnet
ms.topic: article
ms.date: 03/08/2019
ms.author: ghogen
ms.openlocfilehash: 8dfb41e9e5e24c01b2973c3d743897329a3a115e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62825059"
---
# <a name="deploy-an-aspnet-core-container-to-azure-app-service-using-visual-studio"></a>Wdrażanie kontenera platformy ASP.NET Core w usłudze Azure App Service przy użyciu programu Visual Studio

Ten samouczek przeprowadzi Cię przy użyciu programu Visual Studio do publikowania konteneryzowanych aplikacji internetowej platformy ASP.NET Core z programem [usługi Azure App Service](/azure/app-service). Usługa Azure App Service jest usługą odpowiednie dla aplikacji sieci web jednym kontenerze, w hostowanych na platformie Azure.

Jeśli nie masz subskrypcji platformy Azure, przed rozpoczęciem utwórz [bezpłatne konto](https://azure.microsoft.com/free/dotnet/?utm_source=acr-publish-doc&utm_medium=docs&utm_campaign=docs).

## <a name="prerequisites"></a>Wymagania wstępne

Do ukończenia tego samouczka:

::: moniker range="vs-2017"
- Zainstaluj najnowszą wersję [programu Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) z obciążeniem "programowanie aplikacji platformy ASP.NET i sieci web"
::: moniker-end
::: moniker range=">=vs-2019"
- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) z *ASP.NET i tworzenie aplikacji internetowych* obciążenia.
::: moniker-end
- Zainstaluj [pulpitu platformy Docker](https://docs.docker.com/docker-for-windows/install/)

## <a name="create-an-aspnet-core-web-app"></a>Tworzenie aplikacji internetowej platformy ASP.NET Core

Poniższe kroki prowadzą przez proces tworzenia podstawowej aplikacji platformy ASP.NET Core, który będzie używany w ramach tego samouczka.

::: moniker range="vs-2017"
1. Wybierz z menu programu Visual Studio **Plik > Nowy > Projekt**.
2. W obszarze **szablony** części **nowy projekt** okno dialogowe, wybierz opcję **Visual C# > sieci Web**.
3. Wybierz **aplikacji sieci Web platformy ASP.NET Core**.
4. Nazwij swoją nową aplikację (lub wykonać domyślnie) i wybierz **OK**.
5. Wybierz **aplikacji sieci Web**.
6. Sprawdź **włączyć obsługę platformy Docker** pole wyboru.
7. Wybierz **Linux** typu kontenera i kliknij przycisk **OK**. Kontenery Windows nie są obsługiwane do wdrożenia w usłudze Azure App Service jako kontener.
::: moniker-end
::: moniker range=">= vs-2019"
1. W oknie uruchamiania programu Visual Studio, wybierz **Utwórz nowy projekt**.
1. Wybierz **aplikacji sieci Web programu ASP.NET Core**i wybierz polecenie **dalej**.
1. Nazwij swoją nową aplikację (lub wykonać domyślnie) i wybierz polecenie **Utwórz**.
1. Wybierz **aplikacji sieci Web**.
1. Wybierz, czy chcesz, aby obsługa protokołu SSL przy użyciu **Konfigurowanie protokołu HTTPS** pola wyboru.
1. Sprawdź **włączyć obsługę platformy Docker** pole wyboru.
1. Wybierz **Linux** typu kontenera, a następnie kliknij przycisk **Utwórz**. Kontenery Windows nie są obsługiwane do wdrożenia w usłudze Azure App Service jako kontener.
::: moniker-end

## <a name="deploy-the-container-to-azure"></a>Wdrażanie kontenera na platformie Azure

1. Kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierz polecenie **Publikuj**.
1. W oknie dialogowym docelowej publikowania wybierz **App Service Linux**.
1. Można publikować tylko w usłudze App Service lub można publikować w usłudze App Service i Azure Container Registry (ACR). Aby opublikować kontenera w usłudze Azure Container Registry (ACR), wybierz opcję **Tworzenie nowej usługi App Service dla kontenerów**i kliknij przycisk **Publikuj**.

   ![Zrzut ekranu przedstawiający okno dialogowe publikowania](media/deploy-app-service/publish-app-service-linux.PNG)

   Aby opublikować tylko usługi Azure App Service bez korzystania z usługi Azure Container Registry, wybierz **Utwórz nową**i kliknij przycisk **Publikuj**.

1. Sprawdź, czy po zarejestrowaniu się przy użyciu konta, która jest skojarzona z subskrypcją platformy Azure i wybierz unikatową nazwę, subskrypcji, grupy zasobów, plan hostingu i rejestru kontenerów (jeśli dotyczy) lub zaakceptuj wartości domyślne.

   ![Zrzut ekranu przedstawiający ustawienia publikowania](media/deploy-app-service/publish-app-service-linux2.png)

1. Wybierz pozycję **Utwórz**. Kontener jest wdrażana na platformie Azure w rejestrze zasobów grupy i kontener, wybrane. Ten proces trwa trochę czasu. Po jej zakończeniu **Publikuj** karta przedstawia informacje o jakie opublikowano, łącznie z adresem URL witryny.

   ![Zrzut ekranu przedstawiający kartę Publikowanie](media/deploy-app-service/publish-succeeded.PNG)

1. Kliknij łącze lokacji, aby sprawdzić Twoja aplikacja będzie działać zgodnie z oczekiwaniami na platformie Azure.

   ![Zrzut ekranu przedstawiający aplikację sieci web](media/deploy-app-service/web-application-running.png)

1. Profil publikowania zostanie zapisany z wszystkie szczegóły, które wybrano, takich jak grupy i kontener rejestru zasobu.
1. Ponownie wdrażać przy użyciu tego samego profilu publikowania, użyj **publikowania** przycisku **Publikuj** znajdujący się na **działania publikowania internetowego** okna lub kliknij prawym przyciskiem myszy nad projektem w **Eksploratora rozwiązań** i wybierz polecenie **Publikuj** elementu menu kontekstowego.

## <a name="clean-up-resources"></a>Oczyszczanie zasobów

Aby usunąć wszystkie zasoby platformy Azure skojarzone z tym samouczkiem, Usuń grupy zasobów za pomocą [witryny Azure portal](https://portal.azure.com). Aby znaleźć grupy zasobów skojarzonych z opublikowanej aplikacji sieci web, wybierz **widoku** > **Windows inne** > **działania publikowania internetowego**, a następnie wybierz ikonę koła zębatego. **Publikuj** karcie zostanie otwarta, który zawiera grupy zasobów.

W witrynie Azure portal wybierz **grup zasobów**, wybierz grupę zasobów, aby otworzyć ich strony szczegółów. Sprawdź, czy jest to grupa zasobu jest prawidłowy, a następnie wybierz **Usuwanie grupy zasobów**, wpisz nazwę i wybierz **Usuń**.

## <a name="next-steps"></a>Następne kroki

Konfigurowanie ciągłej integracji i ciągłego dostarczania (CI/CD) przy użyciu [potoki Azure](/azure/devops/pipelines/?view=azure-devops).

## <a name="see-also"></a>Zobacz także

[Wdrażanie w usłudze Azure Container Registry](vs-azure-tools-docker-hosting-web-apps-in-docker.md)
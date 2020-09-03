---
title: Wdrażanie kontenera Docker ASP.NET Core w usłudze Docker Hub | Microsoft Docs
description: Dowiedz się, jak używać narzędzi kontenera programu Visual Studio do wdrażania aplikacji internetowej ASP.NET Core w usłudze Docker Hub
author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.devlang: dotnet
ms.topic: how-to
ms.date: 07/23/2019
ms.author: ghogen
monikerRange: '>=vs-2019'
ms.openlocfilehash: cd17726d5ba09dcb901fd529e6bdfd97dee52f31
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "88168658"
---
# <a name="deploy-to-docker-hub"></a>Wdrażanie w usłudze Docker Hub

Usługa Docker Hub udostępnia wygodną usługę hostingu dla repozytoriów obrazów. Możesz łatwo wdrożyć usługę Docker Hub ręcznie z poziomu programu Visual Studio.

## <a name="create-a-docker-account-and-docker-hub-repository"></a>Tworzenie konta platformy Docker i repozytorium centrum Docker

[Utwórz](https://hub.docker.com/signup) konto platformy Docker, jeśli jeszcze go nie masz.

Jeśli nie masz repozytorium centrum platformy Docker, utwórz je za pomocą narzędzia [Docker Hub](https://hub.docker.com/).

## <a name="publish-the-image-for-a-single-project-to-docker-hub"></a>Publikowanie obrazu dla pojedynczego projektu w usłudze Docker Hub

1. Kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Publikuj...**. Zostanie wyświetlony ekran z opcjami wdrażania.

   ![Zrzut ekranu przedstawiający opcje wdrażania](media/container-tools/vs-2019/docker-container-registry.png)

1. Wybierz **Container Registry Docker**, a następnie wybierz pozycję **Docker Hub**.

   ![Zrzut ekranu przedstawiający okno dialogowe publikowania — Wybieranie narzędzia Docker Hub](media/deploy-docker-hub/container-tools-docker-hub-deploy.png)

1. Wprowadź swoje poświadczenia platformy Docker.

   ![Zrzut ekranu przedstawiający okno dialogowe centrum platformy Docker](media/deploy-docker-hub/container-tools-docker-hub-credentials.png)

1. Jeśli łączysz się z własnym repozytorium (nie częścią organizacji), pozostaw zaznaczone pole wyboru **Publikuj w repozytorium osobistym** . Jeśli repozytorium należy do organizacji, wyczyść pole wyboru i wprowadź nazwę organizacji. Wprowadź nazwę użytkownika platformy Docker i hasło do konta platformy Docker, które ma uprawnienia dostępu do repozytorium, z którym nawiązujesz połączenie, a następnie wybierz pozycję **Zapisz**.  

   Program Visual Studio podejmie próbę wdrożenia obrazu w usłudze Docker Hub.  Jeśli to się powiedzie, zostanie wyświetlony ekran **Publikowanie** z adresem URL obrazu repozytorium, tagiem obrazu, repozytorium i konfiguracją kompilacji (na przykład **Release**).

   ![Zrzut ekranu przedstawiający ekran publikowanie](media/deploy-docker-hub/container-tools-docker-hub-finished.png)

1. Możesz zaktualizować obraz w dowolnym momencie, klikając przycisk **Publikuj** na tej stronie.  Możesz również zmodyfikować lub usunąć profil, używając linków znajdujących się pod adresem URL.

## <a name="next-steps"></a>Następne kroki

Opublikuj w [Azure Container Registry](/azure/container-registry/) , wykonując kroki opisane w sekcji [wdrażanie do Azure Container Registry](hosting-web-apps-in-docker.md).

Skonfiguruj ciągłą integrację i dostarczanie (CI/CD) za pomocą [Azure Pipelines](/azure/devops/pipelines/?view=azure-devops).

## <a name="see-also"></a>Zobacz też

[Wdróż do Azure App Service](deploy-app-service.md) 
 [Narzędzia kontenerów programu Visual Studio](/visualstudio/containers/).
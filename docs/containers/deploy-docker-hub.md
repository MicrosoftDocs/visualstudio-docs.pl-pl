---
title: Wdrażanie kontenera platformy Docker ASP.NET w centrum platformy Docker | Dokumenty firmy Microsoft
description: Dowiedz się, jak wdrożyć aplikację sieci Web ASP.NET Core w centrum docker za pomocą narzędzi programu Visual Studio Container Tools
author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.devlang: dotnet
ms.topic: article
ms.date: 07/23/2019
ms.author: ghogen
ms.openlocfilehash: b033825bbe8facbeae3dcdee6a5b563461921522
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "73188747"
---
# <a name="deploy-to-docker-hub"></a>Wdrażanie w usłudze Docker Hub

Docker Hub zapewnia wygodną usługę hostingu dla repozytoriów obrazów. W programie Visual Studio można łatwo wdrożyć w centrum platformy Docker Hub ręcznie.

## <a name="create-a-docker-account-and-docker-hub-repository"></a>Tworzenie konta platformy Docker i repozytorium Usługi Docker Hub

[Zarejestruj konto](https://hub.docker.com/signup) Platformy Docker, jeśli jeszcze go nie masz.

Jeśli nie masz repozytorium Centrum platformy Docker, utwórz je w centrum [platformy Docker](https://hub.docker.com/)Hub .

## <a name="publish-the-image-for-a-single-project-to-docker-hub"></a>Publikowanie obrazu pojedynczego projektu w centrum docker

1. Kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Publikuj...**. Zostanie wyświetlony ekran z opcjami wdrażania.

   ![](media/deploy-docker-hub/container-tools-docker-hub-deploy.png)

1. W obszarze **Wybierz miejsce docelowe publikowania**wybierz pozycję Rejestr **kontenerów**, a następnie wybierz pozycję **Centrum platformy Docker**. Zostanie wyświetlone okno dialogowe **Centrum platformy Docker.**

   ![](media/deploy-docker-hub/container-tools-docker-hub-credentials.png)

1. Jeśli łączysz się z własnym repozytorium (nie jest częścią organizacji), pozostaw to pole wyboru **Publikuj w repozytorium osobistym.** Jeśli repozytorium jest własnością organizacji, wyczyść to pole wyboru i wprowadź nazwę organizacji. Wprowadź nazwę użytkownika i hasło platformy Docker dla swojego konta platformy Docker, które ma uprawnienia dostępu do repozytorium, z którego się łączysz, a następnie wybierz pozycję **Zapisz**.  

   Visual Studio próbuje wdrożyć obraz w Centrum platformy Docker.  Jeśli to się powiedzie, zostanie wyświetlony ekran **Publikowania** z adresem URL obrazu repozytorium, znacznikiem obrazu, repozytorium i konfiguracją kompilacji** (na przykład **Zwolnij).**

   ![](media/deploy-docker-hub/container-tools-docker-hub-finished.png)

1. Obraz można zaktualizować w dowolnym momencie, klikając przycisk **Publikuj** na tej stronie.  Możesz też zmodyfikować lub usunąć profil, korzystając z linków pod adresem URL.

## <a name="next-steps"></a>Następne kroki

Publikuj w [rejestrze kontenerów platformy Azure,](/azure/container-registry/) wykonując kroki opisane w [usłudze Wdrażanie w rejestrze kontenerów platformy Azure.](hosting-web-apps-in-docker.md)

Skonfiguruj ciągłą integrację i dostarczanie (CI/CD) za pomocą [usługi Azure Pipelines](/azure/devops/pipelines/?view=azure-devops).

## <a name="see-also"></a>Zobacz też

[Wdrażanie w narzędziach](deploy-app-service.md)
[kontenerów](/visualstudio/containers/)programu Azure App Service Visual Studio .
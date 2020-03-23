---
title: Publikowanie w usłudze Azure App Service
ms.date: 04/02/2019
helpviewer_keywords:
- deployment, website
ms.assetid: 8524a4c5-97a9-41ac-a2a0-034efb9bfc57
author: sayedihashimi
ms.author: sayedha
manager: unniravindranathan
ms.prod: visual-studio-mac
ms.custom: video
ms.workload:
- azure
ms.openlocfilehash: e4ce4273b72a57a2b9456974a108809dcd73b4e0
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "70222732"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio-for-mac"></a>Publikowanie aplikacji sieci Web w usłudze Azure App Service przy użyciu programu Visual Studio dla komputerów Mac

Za pomocą narzędzia Publikowania można publikować aplikacje ASP.NET Core w usłudze Azure App Service.

## <a name="prerequisites"></a>Wymagania wstępne

- [Visual Studio 2019 dla komputerów Mac](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs4mac2019) zainstalowany z włączoną funkcją ASP.NET Core.
- Subskrypcja platformy Azure. Jeśli nie masz jeszcze subskrypcji, [zarejestruj się za darmo,](https://azure.microsoft.com/free/dotnet/)co obejmuje 200 usd na kredyt na 30 dni i 12 miesięcy popularnych bezpłatnych usług.
- Projekt ASP.NET Core. Jeśli nie masz jeszcze projektu, możesz [utworzyć nowy](~/create-new-projects.md).

## <a name="publish-to-azure-app-service"></a>Publikowanie w usłudze Azure App Service

 1. W panelu rozwiązania kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Publikuj**.

    ![Menu kontekstowe Publikowania](media/publish-context-menu.png)

 2. Jeśli wcześniej opublikowano ten projekt w usłudze Azure App Service, zobaczysz profil publikowania w menu. Wybierz profil publikowania, aby rozpocząć proces publikowania.

 3. Aby opublikować ten projekt w usłudze App Service po raz pierwszy, wybierz pozycję **Publikuj na platformie Azure**

    ![Menu kontekstowe Publikowania w usłudze App Service](media/publish-to-azure-context-menu.png)

 4. Zostanie wyświetlone okno dialogowe **Publikowania w usłudze Azure App Service** i zostaną wyświetlone wszystkie istniejące usługi app services. Aby opublikować w istniejącej usłudze app service, wybierz usługę App Service na liście, a następnie kliknij pozycję **Publikuj**.

    ![Okno dialogowe Publikowania w usłudze Azure App Service](media/publish-to-app-service-dialog.png)

 5. Aby utworzyć nową usługę app service, kliknij przycisk **Nowy.**

    ![Okno dialogowe Publikowania w usłudze aplikacji](media/publish-to-app-service-dialog-new-selected.png)

 6. Zostanie wyświetlone okno dialogowe **Nowa usługa aplikacji.** W tym oknie dialogowym można skonfigurować ustawienia nowej usługi App Service.

    ![Okno dialogowe Nowa usługa aplikacji](media/publish-new-app-service.png)

    Istnieje kilka opcji, aby rozważyć dostosowanie tutaj. Nazwa usługi App Service będzie domyślnie nazwa projektu. Jeśli nazwa nie jest dostępna, po prawej stronie pola wejściowego pojawi się znak ostrzegawczy. Nazwa usługi app service będzie używana w adresie URL witryny, więc nazwa musi być prawidłowa, aby była używana w adresie URL.

    Można zmienić subskrypcję, z którą usługa App Service będzie skojarzona przy użyciu listy rozwijanej **Subskrypcja.**

    Można wybrać istniejącą **grupę zasobów** za pomocą listy rozwijanej **+** lub utworzyć nową za pomocą przycisku.

    W przypadku planu usługi aplikacji wybierz istniejący lub utwórz nowy, wybierając przycisk opcji **Niestandardowe.**

    Aby utworzyć nową usługę App Service i opublikować w niej projekt, kliknij przycisk **Utwórz**.

    Po kliknięciu **przycisku Utwórz** nowe okno **dialogowe usługi app service** zostanie odrzucona, a powinien zostać wyświetlony następujący komunikat wskazujący, że rozpoczęto tworzenie usługi App Service.

      ![Utwórz komunikat usługi aplikacji](media/publish-create-app-service-message.png)

    Po kliknięciu **przycisku OK** wiadomość zostanie odrzucona i możesz kontynuować pracę nad projektem. Stan procesu publikowania można obserwować za pomocą paska stanu u góry ide. Po pomyślnym opublikowaniu aplikacji internetowej witryna jest otwierana za pomocą domyślnej przeglądarki.

## <a name="related-video"></a>Podobne wideo

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Publish-to-Azure/player]

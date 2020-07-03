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
ms.topic: how-to
ms.workload:
- azure
ms.openlocfilehash: 81ae8c8dde91655a4b9b3b8dcb4d0033af34e4d5
ms.sourcegitcommit: 5335a9864d5747bc917ed28d4ebeade3076b10e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2020
ms.locfileid: "85950515"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio-for-mac"></a>Publikowanie aplikacji sieci Web w celu Azure App Service przy użyciu Visual Studio dla komputerów Mac

Za pomocą narzędzia do publikowania można publikować ASP.NET Core aplikacje do Azure App Service.

## <a name="prerequisites"></a>Wymagania wstępne

- [Program Visual Studio 2019 dla komputerów Mac](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs4mac2019) został zainstalowany z włączonym ASP.NET Core.
- Subskrypcja platformy Azure. Jeśli nie masz jeszcze subskrypcji, [zarejestruj się bezpłatnie](https://azure.microsoft.com/free/dotnet/), co obejmuje $200 USD za 30 dni i 12 miesięcy za popularne bezpłatne usługi.
- Projekt ASP.NET Core. Jeśli nie masz jeszcze projektu, możesz [utworzyć nowy](~/create-new-projects.md).

## <a name="publish-to-azure-app-service"></a>Publikowanie w usłudze Azure App Service

 1. W okienko rozwiązania kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Publikuj**.

    ![Menu kontekstowe publikowania](media/publish-context-menu.png)

 2. Jeśli projekt został wcześniej opublikowany do Azure App Service, w menu zostanie wyświetlony profil publikowania. Wybierz ten profil publikowania, aby rozpocząć proces publikowania.

 3. Aby opublikować ten projekt do App Service po raz pierwszy, wybierz pozycję **Publikuj na platformie Azure**

    ![Menu kontekstowe publikowania w App Service](media/publish-to-azure-context-menu.png)

 4. Zostanie wyświetlone okno dialogowe **Publikowanie do Azure App Service** i wszystkie istniejące App Services są wyświetlane. Aby opublikować istniejące App Service, wybierz App Service z listy, a następnie kliknij przycisk **Publikuj**.

    ![Okno dialogowe publikowanie w Azure App Service](media/publish-to-app-service-dialog.png)

 5. Aby utworzyć nowy App Service, kliknij przycisk **Nowy** .

    ![Okno dialogowe publikowanie w App Service](media/publish-to-app-service-dialog-new-selected.png)

 6. Zostanie wyświetlone okno dialogowe **nowe App Service** . W tym oknie dialogowym można skonfigurować ustawienia dla nowego App Service.

    ![Nowe okno dialogowe App Service](media/publish-new-app-service.png)

    Istnieje kilka opcji, które należy rozważyć w tym miejscu. Nazwa App Service będzie domyślnie nazwą projektu. Jeśli nazwa jest niedostępna, po prawej stronie pola wejściowego zostanie wyświetlone ostrzeżenie. Nazwa App Service zostanie użyta w adresie URL witryny sieci Web, więc nazwa musi być prawidłowa, aby można jej było używać w adresie URL.

    Możesz zmienić subskrypcję, z którą zostanie skojarzona App Service za pomocą listy rozwijanej **subskrypcji** .

    Możesz wybrać istniejącą **grupę zasobów** przy użyciu listy rozwijanej lub utworzyć nową z **+** przyciskiem.

    W przypadku planu App Service wybierz istniejący lub Utwórz nowy, wybierając przycisk radiowy **niestandardowe** .

    Aby utworzyć nowy App Service i opublikować w nim projekt, kliknij przycisk **Utwórz**.

    Po kliknięciu przycisku **Utwórz** nowe okno dialogowe **App Service** zostanie odrzucone i powinien zostać wyświetlony następujący komunikat informujący o tym, że tworzenie App Service zostało rozpoczęte.

      ![Utwórz komunikat App Service](media/publish-create-app-service-message.png)

    Po kliknięciu przycisku **OK** komunikat zostanie odrzucony i można kontynuować pracę nad projektem. Stan procesu publikowania można obejrzeć z paskiem stanu w górnej części IDE. Po pomyślnym opublikowaniu aplikacji internetowej lokacja zostanie otwarta w domyślnej przeglądarce.

## <a name="related-video"></a>Pokrewne wideo

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Publish-to-Azure/player]

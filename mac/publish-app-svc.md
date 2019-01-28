---
title: Publikowanie w usłudze Azure App Service — Visual Studio dla komputerów Mac
ms.date: 01/17/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: 8524a4c5-97a9-41ac-a2a0-034efb9bfc57
author: sayedihashimi
ms.author: sayedha
manager: unniravindranathan
ms.prod: visual-studio-mac-dev15
ms.workload:
- azure
ms.openlocfilehash: 41eda3bf79b60e7d0a07b41fdd50bbf588240c3d
ms.sourcegitcommit: 447f2174bdecdd471d8a8e11c19554977db620a0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2019
ms.locfileid: "55090182"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio-for-mac"></a>Publikowanie aplikacji sieci Web w usłudze Azure App Service przy użyciu programu Visual Studio dla komputerów Mac

Narzędzie publikowania do publikowania aplikacji platformy ASP.NET Core w usłudze Azure App Service.

## <a name="prerequisites"></a>Wymagania wstępne

 - [Visual Studio 2017 for Mac](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs4mac2017) zainstalowane za pomocą programu ASP.NET Core włączone.
 - Subskrypcja platformy Azure. Jeśli nie masz już subskrypcję, [Utwórz bezpłatne konto](https://azure.microsoft.com/free/dotnet/), zawierający środki w wysokości 200 USD na 30 dni i 12 miesięcy z popularnych bezpłatnych usług.
 - Projekt platformy ASP.NET Core. Jeśli nie masz jeszcze projektu, możesz to zrobić [Utwórz nową](https://docs.microsoft.com/visualstudio/mac/create-new-projects?view=vsmac-2017).

## <a name="publish-to-azure-app-service"></a>Publikowanie w usłudze Azure App Service

 1. W konsoli rozwiązania, kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Publikuj**.

    ![Menu kontekstowe Opublikuj](media/publish-context-menu.png)

 2. Jeśli została wcześniej opublikowana tego projektu w usłudze Azure App Service, zobaczysz profil publikowania, w menu. Wybierz ten profil publikowania, aby rozpocząć proces publikowania.

 3. Aby opublikować ten projekt w usłudze App Service po raz pierwszy, zaznacz **Opublikuj na platformie Azure**

    ![Publikowanie w menu kontekstowym usługi App Service](media/publish-to-azure-context-menu.png)

 4. **Publikuj w usłudze Azure App Service** zostanie wyświetlone okno dialogowe, i nie są wyświetlane wszystkie istniejące usługi aplikacji. Aby opublikować istniejącej usługi App Service, wybierz z listy usługi App Service, a następnie kliknij przycisk **Publikuj**.

    ![Publikowanie w usłudze Azure App Service w oknie dialogowym](media/publish-to-app-service-dialog.png)

 5. Aby utworzyć nową usługę App Service, kliknij przycisk **New** przycisku. 

    ![Publikowanie w oknie dialogowym App Service](media/publish-to-app-service-dialog-new-selected.png)

 6. **Nowej usługi App Service** zostanie wyświetlone okno dialogowe. W tym oknie dialogowym można skonfigurować ustawienia dla nowej usługi App Service.

    ![Okno dialogowe Nowy usługi App Service](media/publish-new-app-service.png)

    Istnieje kilka możliwości, które należy rozważyć w tym miejscu. Nazwa usługi App Service będą domyślnie nazwa projektu. Jeśli nazwa nie jest dostępna na po prawej stronie pola wejściowego pojawi się oznaczeniem ostrzeżenia. Nazwa usługi App Service będzie służyć w adresie URL witryny sieci Web, więc nazwa musi być prawidłową ma być używany w adresie URL.

    Możesz zmienić subskrypcję usługi App Service będą skojarzone z za pomocą **subskrypcji** listy rozwijanej.

    Możesz wybrać istniejące **grupy zasobów** za pomocą listy rozwijanej lub możesz utworzyć nową grupę za pomocą **+** przycisku.

    Dla planu usługi App Service, wybierz istniejącą lub Utwórz nową, wybierając **niestandardowe** przycisku radiowego.

    Kliknij, aby utworzyć nową usługę App Service i opublikować projekt **Utwórz**.

    Po kliknięciu przycisku **Utwórz** **nowej usługi App Service** okna dialogowego zostanie zamknięty i powinien zostać wyświetlony następujący komunikat informujący, że rozpoczęto Tworzenie usługi App Service.

      ![Utwórz wiadomość usługi App Service](media/publish-create-app-service-message.png)

    Po kliknięciu przycisku **OK** wiadomości jest odrzucane i można kontynuować pracę nad projektem. Możesz obserwować stan procesu publikowania za pomocą paska stanu w górnej części IDE. Po pomyślnym opublikowaniu aplikacji sieci web, witryny jest otwierany przy użyciu domyślnej przeglądarki.
---
title: Publikowanie na platformie Azure przez importowanie ustawień publikowania
description: Tworzenie i importowanie profilu publikowania w celu wdrożenia aplikacji z programu Visual Studio do usługi Azure App Service
ms.date: 05/07/2018
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bd040b613a5b982050d651f341456c5fafc2954b
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "65679191"
---
# <a name="publish-an-application-to-azure-app-service-by-importing-publish-settings-in-visual-studio"></a>Publikowanie aplikacji w usłudze Azure App Service przez importowanie ustawień publikowania w programie Visual Studio

Za pomocą narzędzia **Publikowanie** można zaimportować ustawienia publikowania, a następnie wdrożyć aplikację. W tym artykule używamy ustawień publikowania dla usługi Azure App Service, ale można użyć podobnych kroków, aby zaimportować ustawienia publikowania z [usług IIS](../deployment/tutorial-import-publish-settings-iis.md). W niektórych scenariuszach użycie profilu ustawień publikowania może być szybsze niż ręczne konfigurowanie wdrożenia usługi dla każdej instalacji programu Visual Studio.

Te kroki dotyczą aplikacji ASP.NET, ASP.NET Core i .NET Core w programie Visual Studio. Można również zaimportować ustawienia publikowania dla aplikacji [Python.](../python/publishing-python-web-applications-to-azure-from-visual-studio.md)

W tym samouczku zostaną wykonane następujące czynności:

> [!div class="checklist"]
> * Generowanie pliku ustawień publikowania z usługi Azure App Service
> * Importowanie pliku ustawień publikowania do programu Visual Studio
> * Wdrażanie aplikacji w usłudze Azure App Service

Plik ustawień publikowania (*\*.publishsettings*) różni się od profilu publikowania (*\*pubxml*) utworzonego w programie Visual Studio. Plik ustawień publikowania jest tworzony przez usługę Azure App Service, a następnie można go zaimportować do programu Visual Studio.

> [!NOTE]
> Jeśli wystarczy skopiować profil publikowania programu Visual Studio (plik*\*pubxml)* z jednej instalacji programu Visual Studio do innej, można znaleźć profil publikowania , * \<nazwa\>_pubxml*, w * \\<projectname\>\Properties\PublishProfiles* folder dla zarządzanych typów projektów. W przypadku witryn sieci Web zajrzyj w obszarze *folderu \App_Data.* Profile publikowania są plikami XML MSBuild.

## <a name="prerequisites"></a>Wymagania wstępne

::: moniker range=">=vs-2019"

* Musi być zainstalowany program Visual Studio 2019 i ASP.NET i obciążenia **tworzenia sieci Web.**

    Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony pobierania programu Visual [Studio,](https://visualstudio.microsoft.com/downloads/)aby zainstalować ją bezpłatnie.
::: moniker-end

::: moniker range="vs-2017"

* Musi być zainstalowany program Visual Studio 2017 i ASP.NET i obciążenia **tworzenia sieci Web.**

    Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony pobierania programu Visual [Studio,](https://visualstudio.microsoft.com/downloads/)aby zainstalować ją bezpłatnie.
::: moniker-end

* Utwórz usługę Azure App Service. Aby uzyskać szczegółowe instrukcje, zobacz [Wdrażanie aplikacji sieci Web ASP.NET Core na platformie Azure przy użyciu programu Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Tworzenie nowego projektu ASP.NET w programie Visual Studio

1. Na komputerze z programem Visual Studio utwórz nowy projekt.

    Wybierz poprawny szablon. W tym przykładzie wybierz **opcję ASP.NET aplikacji sieci Web (.NET Framework)** lub (tylko dla języka C#) ASP.NET **podstawowej aplikacji sieci Web,** a następnie kliknij przycisk **OK**.

    Jeśli nie widzisz określonych szablonów projektów, kliknij łącze **Otwórz instalator programu Visual Studio** w lewym okienku okna dialogowego Nowy **projekt.** Uruchamia instalator programu Visual Studio. Zainstaluj **obciążenie ASP.NET i tworzenia stron internetowych.**

    Wybranego szablonu projektu (ASP.NET lub ASP.NET Core) musi odpowiadać wersji ASP.NET zainstalowanej na serwerze sieci Web.

1. Wybierz opcję **MVC** (.NET Framework) lub **Web Application (Model-View-Controller)** (dla .NET Core) i upewnij się, że nie jest **zaznaczone żadne uwierzytelnianie,** a następnie kliknij przycisk **OK**.

1. Wpisz nazwę, taką jak **MyWebApp** i kliknij **przycisk OK**.

    Visual Studio tworzy projekt.

1. Wybierz **build** > **build solution,** aby utworzyć projekt.

## <a name="create-the-publish-settings-file-in-azure-app-service"></a>Tworzenie pliku ustawień publikowania w usłudze Azure App Service

1. W witrynie Azure portal otwórz usługę Azure App Service.

1. Kliknij **pozycję Pobierz profil publikowania** i zapisz profil lokalnie.

    ![Pobierz profil publikowania](../deployment/media/tutorial-azure-app-service-get-publish-profile.png)

    Plik z rozszerzeniem pliku *.publishsettings* został wygenerowany w miejscu, w którym został zapisany. Poniższy kod przedstawia częściowy przykład pliku (w bardziej czytelnym formatowaniu).

    ```xml
    <publishData>
      <publishProfile
        profileName="DeployASPDotNetCore - Web Deploy"
        publishMethod="MSDeploy"
        publishUrl="deployaspdotnetcore.scm.azurewebsites.net:443"
        msdeploySite="DeployASPDotNetCore"
        userName="$DeployASPDotNetCore"
        userPWD="abcdefghijklmnopqrstuzwxyz"
        destinationAppUrl="http://deployaspdotnetcore20180508031824.azurewebsites.net"
        SQLServerDBConnectionString=""
        mySQLDBConnectionString=""
        hostingProviderForumLink=""
        controlPanelLink="http://windows.azure.com"
        webSystem="WebSites">
        <databases />
      </publishProfile>
    </publishData>
    ```

    Zazwyczaj poprzedni plik *.publishsettings zawiera dwa profile publikowania, których można użyć w programie Visual Studio, jeden do wdrożenia przy użyciu wdrożenia w sieci Web, a drugi do wdrożenia przy użyciu protokołu FTP. Poprzedni kod przedstawia profil wdrażania w sieci Web. Oba profile zostaną zaimportowane później podczas importowania profilu.

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importowanie ustawień publikowania w programie Visual Studio i wdrażanie

[!INCLUDE [import publish settings](../deployment/includes/import-publish-settings-vs.md)]

## <a name="next-steps"></a>Następne kroki

W tym samouczku utworzono plik ustawień publikowania, zaimportowano go do programu Visual Studio i wdrożono aplikację ASP.NET w usłudze Azure App Service. Przegląd opcji publikowania w programie Visual Studio może być omówienie.

> [!div class="nextstepaction"]
> [Pierwsze spojrzenie na wdrażanie](../deployment/deploying-applications-services-and-components.md)

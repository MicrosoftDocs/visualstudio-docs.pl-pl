---
title: Publikowanie na platformie Azure przez zaimportowanie ustawień publikowania
description: Utwórz i zaimportuj profil publikowania, aby wdrożyć aplikację z programu Visual Studio w celu Azure App Service
ms.date: 05/06/2020
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6d2c52d6db6ca3001712a692a1de059834c975ae
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88801714"
---
# <a name="publish-an-application-to-azure-app-service-by-importing-publish-settings-in-visual-studio"></a>Publikowanie aplikacji do Azure App Service przez zaimportowanie ustawień publikowania w programie Visual Studio

Możesz użyć narzędzia do **publikowania** , aby zaimportować ustawienia publikowania, a następnie wdrożyć aplikację. W tym artykule używamy ustawień publikowania dla Azure App Service, ale możesz użyć podobnych kroków, aby zaimportować ustawienia publikowania z [usług IIS](../deployment/tutorial-import-publish-settings-iis.md). W niektórych scenariuszach korzystanie z profilu ustawień publikowania może być szybsze niż ręczne konfigurowanie wdrożenia w usłudze dla każdej instalacji programu Visual Studio.

Te kroki dotyczą aplikacji ASP.NET, ASP.NET Core i .NET Core w programie Visual Studio. Możesz również zaimportować ustawienia publikowania dla aplikacji języka [Python](../python/publishing-python-web-applications-to-azure-from-visual-studio.md) .

W tym samouczku wykonasz następujące czynności:

> [!div class="checklist"]
> * Generuj plik ustawień publikowania na podstawie Azure App Service
> * Importowanie pliku ustawień publikowania do programu Visual Studio
> * Wdróż aplikację w Azure App Service

Plik ustawień publikowania (* \* . publishsettings*) jest inny niż profil publikacji (* \* . pubxml*) utworzony w programie Visual Studio. Plik ustawień publikowania jest tworzony przez Azure App Service, a następnie można go zaimportować do programu Visual Studio.

> [!NOTE]
> Jeśli wystarczy skopiować profil publikacji programu Visual Studio (plik* \* . pubxml* ) z jednej instalacji programu Visual Studio do innej, można znaleźć profil publikowania, * \<profilename\> . pubxml*, w folderze * \\<ProjectName \> \Properties\PublishProfiles* dla typów projektów zarządzanych. W przypadku witryn sieci Web zapoznaj się z folderem *\ App_Data* . Profile publikowania są plikami XML programu MSBuild.

## <a name="prerequisites"></a>Wymagania wstępne

::: moniker range=">=vs-2019"

* Musisz mieć zainstalowany program Visual Studio 2019 i obciążenie **programowaniem ASP.NET i sieci Web** .

    Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads/),   Aby zainstalować ją bezpłatnie.
::: moniker-end

::: moniker range="vs-2017"

* Musisz mieć zainstalowany program Visual Studio 2017 i obciążenie **programowaniem ASP.NET i sieci Web** .

    Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads/),   Aby zainstalować ją bezpłatnie.
::: moniker-end

* Utwórz Azure App Service. Aby uzyskać szczegółowe instrukcje, zobacz [wdrażanie aplikacji sieci web ASP.NET Core na platformie Azure przy użyciu programu Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Tworzenie nowego projektu ASP.NET w programie Visual Studio

1. Na komputerze z uruchomionym programem Visual Studio Utwórz nowy projekt.

    Wybierz odpowiedni szablon. W tym przykładzie wybierz pozycję **aplikacja sieci web ASP.NET (.NET Framework)** lub (tylko w przypadku języka C#) **ASP.NET Core aplikacja internetowa**, a następnie wybierz przycisk **OK**.

    Jeśli nie widzisz określonych szablonów projektu, przejdź do linku **otwórz Instalator programu Visual Studio** w lewym okienku okna dialogowego **Nowy projekt** . Zostanie uruchomiona Instalator programu Visual Studio. Zainstaluj **ASP.NET i programowanie aplikacji sieci Web** .

    Wybrany szablon projektu (ASP.NET lub ASP.NET Core) musi odpowiadać wersji ASP.NET zainstalowanej na serwerze sieci Web.

1. Wybierz opcję **MVC** (.NET Framework) lub **aplikacja sieci Web (Model-View-Controller)** (dla platformy .NET Core) i upewnij się, że nie wybrano **żadnego uwierzytelniania** , a następnie wybierz przycisk **OK**.

1. Wpisz nazwę, taką jak **MyWebApp** , i wybierz **przycisk OK**.

    Program Visual Studio tworzy projekt.

1. Wybierz pozycję **Kompiluj**  >  **kompilację rozwiązania** , aby skompilować projekt.

## <a name="create-the-publish-settings-file-in-azure-app-service"></a>Utwórz plik ustawień publikowania w Azure App Service

1. W Azure Portal Otwórz Azure App Service.

1. Przejdź do pozycji **Pobierz profil publikowania** i Zapisz profil lokalnie.

    ![Pobieranie profilu publikowania](../deployment/media/tutorial-azure-app-service-get-publish-profile.png)

    Plik z rozszerzeniem *. publishsettings* został wygenerowany w lokalizacji, w której został zapisany. Poniższy kod przedstawia częściowy przykład pliku (w bardziej czytelny sposób formatowania).

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

    Zazwyczaj poprzedni plik *. publishsettings zawiera dwa profile publikowania, których można użyć w programie Visual Studio, jeden do wdrożenia przy użyciu Web Deploy i jeden do wdrożenia przy użyciu protokołu FTP. Powyższy kod przedstawia profil Web Deploy. Oba profile zostaną zaimportowane później podczas importowania profilu.

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importowanie ustawień publikowania w programie Visual Studio i wdrażanie

[!INCLUDE [import publish settings](../deployment/includes/import-publish-settings-vs.md)]

## <a name="next-steps"></a>Następne kroki

W tym samouczku utworzono plik ustawień publikowania, zaimportowano go do programu Visual Studio i wdrożono aplikację ASP.NET do Azure App Service. Warto zapoznać się z omówieniem opcji publikowania w programie Visual Studio.

> [!div class="nextstepaction"]
> [Pierwsze spojrzenie na wdrażanie](../deployment/deploying-applications-services-and-components.md)

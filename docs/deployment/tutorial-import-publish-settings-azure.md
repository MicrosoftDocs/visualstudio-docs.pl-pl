---
title: Publikowanie na platformie Azure przez importowanie ustawień publikowania
description: Tworzenie i importowanie profilu publikowania, aby wdrożyć aplikację z programu Visual Studio w usłudze Azure App Service
ms.date: 05/07/2018
ms.technology: vs-ide-deployment
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 804965df5142ddb18c1857a2540c5c69c08c4f9a
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53058503"
---
# <a name="publish-an-application-to-azure-app-service-by-importing-publish-settings-in-visual-studio"></a>Publikowanie aplikacji w usłudze Azure App Service przez importowanie ustawień publikowania w programie Visual Studio

Możesz użyć **Publikuj** narzędzie ma zaimportować ustawienia publikowania, a następnie wdrożyć aplikację. W tym artykule używamy ustawień publikowania dla usługi Azure App Service, ale można użyć podobne kroki w celu importowania publikowania ustawienia z [IIS](../deployment/tutorial-import-publish-settings-iis.md). W niektórych scenariuszach Użyj publikowania profilu ustawień może być szybsze niż ręcznie konfigurować wdrożenia do usługi w przypadku każdej instalacji programu Visual Studio.

Te kroki mają zastosowanie do aplikacji platformy ASP.NET, ASP.NET Core i .NET Core w programie Visual Studio. Możesz również zaimportować ustawienia publikowania dla [Python](../python/publishing-python-web-applications-to-azure-from-visual-studio.md) aplikacji. Kroki odnoszą się do programu Visual Studio 2017 w wersji 15.6.

W tym samouczku wykonasz następujące czynności:

> [!div class="checklist"]
> * Generuj plik ustawień publikowania z usługi Azure App Service
> * Importuj plik ustawień publikowania w programie Visual Studio
> * Wdrażanie aplikacji w usłudze Azure App Service

Plik ustawień publikowania (*\*.publishsettings*) różni się od profilu publikowania (*\*.pubxml*) utworzone w programie Visual Studio. Plik ustawień publikowania jest tworzony przez usługę Azure App Service, a następnie mogą być importowane do programu Visual Studio.

> [!NOTE]
> Jeśli chcesz tylko do kopiowania programu Visual Studio profil publikowania (*\*.pubxml* plik) z jednej instalacji programu Visual Studio do innego, można znaleźć profilu publikowania  *\<profilename\>.pubxml*w  *\\< nazwa_projektu\>\Properties\PublishProfiles* folder typami projektów zarządzanych. Dla witryn sieci Web, sprawdź w obszarze *\App_Data* folderu. Profile publikowania są plikami XML programu MSBuild.

## <a name="prerequisites"></a>Wymagania wstępne

* Konieczne jest posiadanie programu Visual Studio 2017 i **ASP.NET** i. **NET Framework** pakiet roboczy programowania. Dla aplikacji platformy .NET Core, należy również. **.NET Core** obciążenia.

    Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) strony, aby zainstalować go za darmo.

* Tworzenie usługi Azure App Service. Aby uzyskać szczegółowe instrukcje, zobacz [wdrażanie aplikacji sieci web platformy ASP.NET Core na platformie Azure przy użyciu programu Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Utwórz nowy projekt ASP.NET w programie Visual Studio

1. Na komputerze z programem Visual Studio wybierz **pliku** > **nowy projekt**.

1. W obszarze **Visual C#**  lub **języka Visual Basic**, wybierz **Web**, a następnie w środkowym okienku wybierz **aplikacji sieci Web platformy ASP.NET (.NET Framework)** lub (C# tylko) **aplikacji sieci Web programu ASP.NET Core**, a następnie kliknij przycisk **OK**.

    Jeśli nie widzisz szablony określonego projektu, kliknij przycisk **Otwórz Instalator programu Visual Studio** łącze w okienku po lewej stronie **nowy projekt** okno dialogowe. Uruchamia Instalatora programu Visual Studio. Zobacz wymagania wstępne w tym artykule, aby zidentyfikować wymagane obciążeń programu Visual Studio, które trzeba zainstalować.

1. Wybierz opcję **MVC** (.NET Framework) lub **aplikacji sieci Web (Model-View-Controller)** (dla platformy .NET Core) i upewnij się, że **bez uwierzytelniania** jest zaznaczone, a następnie kliknij przycisk **OK**.

1. Wpisz nazwę, takich jak **MyWebApp** i kliknij przycisk **OK**.

    Program Visual Studio tworzy projekt.

1. Wybierz **kompilacji** > **Kompiluj rozwiązanie** do skompilowania projektu.

## <a name="create-the-publish-settings-file-in-azure-app-service"></a>Utwórz plik ustawień publikowania w usłudze Azure App Service

1. W witrynie Azure portal Otwórz w usłudze Azure App Service.

1. Kliknij przycisk **Pobierz profil publikowania** profilu i zapisz go lokalnie.

    ![Pobierz profil publikowania](../deployment/media/tutorial-azure-app-service-get-publish-profile.png)

    Plik o *.publishsettings* rozszerzenie pliku został wygenerowany w lokalizacji, w którym został zapisany. Poniższy kod przedstawia częściowe przykład pliku (w bardziej czytelnym formatowanie).

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
    Zazwyczaj poprzedni plik *.publishsettings zawiera dwa profile publikowania, których można używać w programie Visual Studio do wdrażania za pomocą narzędzia Web Deploy i jeden do wdrożenia przy użyciu protokołu FTP. Poprzedni kod Pokazuje profil narzędzia Web Deploy. Oba profile zostaną zaimportowane później podczas importowania profilu.

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importowanie ustawień publikowania w programie Visual Studio i wdrażanie

[!INCLUDE [import publish settings](../deployment/includes/import-publish-settings-vs.md)]

## <a name="next-steps"></a>Następne kroki

W tym samouczku utworzony plik ustawień publikowania, zaimportowany do programu Visual Studio i wdrożyć aplikację ASP.NET w usłudze Azure App Service. Możesz się z omówieniem opcji publikowania w programie Visual Studio.

> [!div class="nextstepaction"]
> [Pierwsze spojrzenie na wdrażanie](../deployment/deploying-applications-services-and-components.md)

---
title: Publikowanie w usługach IIS przez zaimportowanie ustawień publikowania
description: Tworzenie i importowanie profilu publikowania w celu wdrożenia aplikacji z Visual Studio do usług IIS
ms.date: 05/06/2020
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: aeaaff68ab0abe85838456e8c8b69e2520295689
ms.sourcegitcommit: a0f5e7188838c5989c9cc78d99fb29bb2813501e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/11/2021
ms.locfileid: "109729276"
---
# <a name="publish-an-application-to-iis-by-importing-publish-settings-in-visual-studio"></a>Publikowanie aplikacji w usługach IIS przez zaimportowanie ustawień publikowania w programie Visual Studio

Za pomocą narzędzia **publikowanie** możesz zaimportować ustawienia publikowania, a następnie wdrożyć aplikację. W tym artykule używamy ustawień publikowania dla usług IIS, ale podobne kroki można wykonać, aby zaimportować ustawienia publikowania dla [Azure App Service](../deployment/tutorial-import-publish-settings-azure.md). W niektórych scenariuszach użycie profilu ustawień publikowania może być szybsze niż ręczne skonfigurowanie wdrożenia w usługach IIS dla każdej instalacji Visual Studio.

Te kroki dotyczą aplikacji ASP.NET, ASP.NET Core i .NET Core w Visual Studio.

W tym samouczku wykonasz następujące czynności:

> [!div class="checklist"]
> * Konfigurowanie usług IIS w celu wygenerowania pliku ustawień publikowania
> * Tworzenie pliku ustawień publikowania
> * Zaimportuj plik ustawień publikowania do Visual Studio
> * Wdrażanie aplikacji w usługach IIS

Plik ustawień publikowania (*\* .publishsettings*) różni się od profilu publikowania *\* (pubxml)* utworzonego w Visual Studio. Plik ustawień publikowania jest tworzony przez usługę IIS lub Azure App Service lub można go utworzyć ręcznie, a następnie zaimportować do Visual Studio.

> [!NOTE]
> Jeśli musisz skopiować profil publikowania programu Visual Studio (plik pubxml) z jednej instalacji programu Visual Studio do innej, możesz znaleźć profil publikowania \* *\<profilename\> pubxml* w folderze *\\ projectname \> \Properties\PublishProfiles* programu<dla zarządzanych typów projektów. W przypadku witryn internetowych zajmij się *folderem \App_Data.* Profile publikowania to pliki XML programu MSBuild.

## <a name="prerequisites"></a>Wymagania wstępne

::: moniker range=">=vs-2019"

* Musisz mieć zainstalowany program Visual Studio 2019 oraz **ASP.NET tworzenia aplikacji internetowych.**

    Jeśli nie masz jeszcze zainstalowanego Visual Studio, przejdź do strony [pobierania](https://visualstudio.microsoft.com/downloads/) Visual Studio, aby zainstalować ją bezpłatnie.
::: moniker-end

::: moniker range="vs-2017"

* Musisz mieć zainstalowany program Visual Studio 2017 oraz **ASP.NET i tworzenie aplikacji internetowych.**

    Jeśli nie masz jeszcze zainstalowanego Visual Studio, przejdź do strony [pobierania](https://visualstudio.microsoft.com/downloads/) Visual Studio, aby zainstalować ją bezpłatnie.
::: moniker-end

* Na serwerze musi być uruchomiony system Windows Server 2012, Windows Server 2016 lub Windows Server 2019 oraz musi być poprawnie zainstalowana rola serwera sieci Web usług [IIS](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) (wymagana do wygenerowania pliku ustawień publikowania (*\* .publishsettings*)). Na ASP.NET musi być również zainstalowana ASP.NET Core w ASP.NET 4.5 lub 4.5 Core. Aby skonfigurować usługę ASP.NET 4.5, zobacz [IIS 8.0 Using ASP.NET 3.5 and ASP.NET 4.5 (Usługi IIS 8.0 w ASP.NET 3.5 i ASP.NET 4.5).](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) Aby skonfigurować program ASP.NET Core, zobacz [Host ASP.NET Core w systemie Windows przy użyciu usług IIS.](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration) W ASP.NET Core upewnij się, że pula aplikacji została skonfigurowana do używania ustawienia Brak kodu zarządzanego, zgodnie z opisem w artykule.

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Tworzenie nowego projektu ASP.NET w programie Visual Studio

1. Na komputerze z Visual Studio utwórz nowy projekt.

    Wybierz odpowiedni szablon. W tym przykładzie wybierz pozycję **ASP.NET Web Application (.NET Framework)** lub (tylko w przypadku języka C#) **ASP.NET Core Web Application**, a następnie wybierz przycisk **OK.**

    Jeśli nie widzisz określonych szablonów projektów, przejdź  do linku Otwórz Instalator programu Visual Studio w lewym okienku okna **dialogowego Nowy** projekt. Ta Instalator programu Visual Studio uruchamia się. Zainstaluj pakiet **ASP.NET tworzenia aplikacji internetowych.**

    Wybierany szablon projektu (ASP.NET lub ASP.NET Core) musi odpowiadać wersji programu ASP.NET zainstalowanej na serwerze sieci Web.

1. Wybierz opcję **MVC** (.NET Framework) lub Aplikacja internetowa **(Model-View-Controller)** (dla platformy .NET Core) i upewnij się, że wybrano pozycję Bez **uwierzytelniania,** a następnie wybierz przycisk **OK.**

1. Wpisz nazwę, na przykład **MyWebApp,** i wybierz **przycisk OK.**

    Visual Studio tworzy projekt.

1. Wybierz **pozycję Build** Build Solution (Skompilowanie rozwiązania)  >   (lub naciśnij **klawisze Ctrl**  +  **Shift**  +  **B),** aby skompilować projekt.

## <a name="install-and-configure-web-deploy-on-windows-server"></a>Instalowanie i konfigurowanie Web Deploy systemie Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

## <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Tworzenie pliku ustawień publikowania w usługach IIS w systemie Windows Server

[!INCLUDE [create-publish-settings-iis](../deployment/includes/create-publish-settings-iis.md)]

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importowanie ustawień publikowania w Visual Studio wdrożenia

[!INCLUDE [import-publish-settings](../deployment/includes/import-publish-settings-vs.md)]

Po pomyślnym wdrożeniu aplikacja powinna zostać automatycznie uruchamiana. Jeśli nie rozpoczyna się od Visual Studio, uruchom aplikację w usługach IIS. W ASP.NET Core należy upewnić się, że pole Pula aplikacji dla puli **DefaultAppPool** ma wartość **Brak kodu zarządzanego.**

## <a name="next-steps"></a>Następne kroki

W tym samouczku utworzono plik ustawień publikowania, zaimportowano go do usługi Visual Studio i wdrożono aplikację ASP.NET w usługach IIS. Możesz chcieć uzyskać przegląd innych opcji publikowania w Visual Studio.

> [!div class="nextstepaction"]
> [Pierwsze spojrzenie na wdrażanie](../deployment/deploying-applications-services-and-components.md)

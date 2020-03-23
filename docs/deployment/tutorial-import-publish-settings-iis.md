---
title: Publikowanie w uiś.
description: Tworzenie i importowanie profilu publikowania w celu wdrożenia aplikacji z programu Visual Studio do usług IIS
ms.date: 01/31/2019
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8e0c7309f52fbc8056f09e5a59afcfdefaa8d0bf
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "65680139"
---
# <a name="publish-an-application-to-iis-by-importing-publish-settings-in-visual-studio"></a>Publikowanie aplikacji w usługach IIS przez importowanie ustawień publikowania w programie Visual Studio

Za pomocą narzędzia **Publikowanie** można zaimportować ustawienia publikowania, a następnie wdrożyć aplikację. W tym artykule używamy ustawień publikowania dla usług IIS, ale można użyć podobnych kroków, aby zaimportować ustawienia publikowania dla [usługi Azure App Service](../deployment/tutorial-import-publish-settings-azure.md). W niektórych scenariuszach użycie profilu ustawień publikowania może być szybsze niż ręczne konfigurowanie wdrażania do usług IIS dla każdej instalacji programu Visual Studio.

Te kroki dotyczą aplikacji ASP.NET, ASP.NET Core i .NET Core w programie Visual Studio.

W tym samouczku zostaną wykonane następujące czynności:

> [!div class="checklist"]
> * Konfigurowanie plików IIS w celu wygenerowania pliku ustawień publikowania
> * Tworzenie pliku ustawień publikowania
> * Importowanie pliku ustawień publikowania do programu Visual Studio
> * Wdrażanie aplikacji w uiświadach iis

Plik ustawień publikowania (*\*.publishsettings*) różni się od profilu publikowania (*\*pubxml*) utworzonego w programie Visual Studio. Plik ustawień publikowania jest tworzony przez usługi IIS lub usługi Azure App Service lub można go utworzyć ręcznie, a następnie można go zaimportować do programu Visual Studio.

> [!NOTE]
> Jeśli wystarczy skopiować profil publikowania programu\*Visual Studio (plik pubxml) z jednej instalacji programu Visual Studio do innej, można znaleźć profil publikowania , * \<nazwa\>_pubxml*, w * \\<projectname\>\Properties\PublishProfiles* folder dla zarządzanych typów projektów. W przypadku witryn sieci Web zajrzyj w obszarze *folderu \App_Data.* Profile publikowania są plikami XML MSBuild.

## <a name="prerequisites"></a>Wymagania wstępne

::: moniker range=">=vs-2019"

* Musi być zainstalowany program Visual Studio 2019 i ASP.NET i obciążenia **tworzenia sieci Web.**

    Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony pobierania programu Visual [Studio,](https://visualstudio.microsoft.com/downloads/)aby zainstalować ją bezpłatnie.
::: moniker-end

::: moniker range="vs-2017"

* Musi być zainstalowany program Visual Studio 2017 i ASP.NET i obciążenia **tworzenia sieci Web.**

    Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony pobierania programu Visual [Studio,](https://visualstudio.microsoft.com/downloads/)aby zainstalować ją bezpłatnie.
::: moniker-end

* Na serwerze musi być uruchomiony system Windows Server 2012 lub Windows Server 2016 i musi być poprawnie [zainstalowana rola serwera sieci Web usług IIS](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) (wymagana do wygenerowania pliku ustawień publikowania (*\*.publishsettings*)). Na serwerze należy również zainstalować ASP.NET 4.5 lub ASP.NET Core. Aby skonfigurować ASP.NET 4.5, zobacz [IIS 8.0 Korzystanie z ASP.NET 3.5 i ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45). Aby skonfigurować ASP.NET Core, zobacz [Host ASP.NET Core w systemie Windows z iis](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Tworzenie nowego projektu ASP.NET w programie Visual Studio

1. Na komputerze z programem Visual Studio utwórz nowy projekt.

    Wybierz poprawny szablon. W tym przykładzie wybierz **opcję ASP.NET aplikacji sieci Web (.NET Framework)** lub (tylko dla języka C#) ASP.NET **podstawowej aplikacji sieci Web,** a następnie kliknij przycisk **OK**.

    Jeśli nie widzisz określonych szablonów projektów, kliknij łącze **Otwórz instalator programu Visual Studio** w lewym okienku okna dialogowego Nowy **projekt.** Uruchamia instalator programu Visual Studio. Zainstaluj **obciążenie ASP.NET i tworzenia stron internetowych.**

    Wybranego szablonu projektu (ASP.NET lub ASP.NET Core) musi odpowiadać wersji ASP.NET zainstalowanej na serwerze sieci Web.

1. Wybierz opcję **MVC** (.NET Framework) lub **Web Application (Model-View-Controller)** (dla .NET Core) i upewnij się, że nie jest **zaznaczone żadne uwierzytelnianie,** a następnie kliknij przycisk **OK**.

1. Wpisz nazwę, taką jak **MyWebApp** i kliknij **przycisk OK**.

    Visual Studio tworzy projekt.

1. Wybierz **build** > **build solution,** aby utworzyć projekt.

## <a name="install-and-configure-web-deploy-on-windows-server"></a>Instalowanie i konfigurowanie wdrażania sieci Web w systemie Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

## <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Tworzenie pliku ustawień publikowania w serwisach IIS w systemie Windows Server

[!INCLUDE [create-publish-settings-iis](../deployment/includes/create-publish-settings-iis.md)]

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importowanie ustawień publikowania w programie Visual Studio i wdrażanie

[!INCLUDE [import-publish-settings](../deployment/includes/import-publish-settings-vs.md)]

Po pomyślnym wdrożeniu aplikacji należy uruchomić automatycznie. Jeśli nie rozpocznie się od programu Visual Studio, uruchom aplikację w iis. W przypadku ASP.NET Core należy upewnić się, że pole Puli aplikacji dla **puli DefaultAppPool** jest ustawione na **Brak kodu zarządzanego**.

## <a name="next-steps"></a>Następne kroki

W tym samouczku utworzono plik ustawień publikowania, zaimportowano go do programu Visual Studio i wdrożono aplikację ASP.NET do aplikacji IIS. Przegląd innych opcji publikowania w programie Visual Studio może być omówienie.

> [!div class="nextstepaction"]
> [Pierwsze spojrzenie na wdrażanie](../deployment/deploying-applications-services-and-components.md)

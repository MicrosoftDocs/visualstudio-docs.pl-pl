---
title: Publikowanie usług IIS przez importowanie ustawień publikowania
description: Tworzenie i importowanie profilu publikowania, aby wdrożyć aplikację w programie Visual Studio w usługach IIS
ms.date: 01/31/2019
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b6b0c4f870de455238c02f5dbecbc0c5d56dfbc9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62927187"
---
# <a name="publish-an-application-to-iis-by-importing-publish-settings-in-visual-studio"></a>Publikowanie aplikacji w usługach IIS przez importowanie ustawień publikowania w programie Visual Studio

Możesz użyć **Publikuj** narzędzie ma zaimportować ustawienia publikowania, a następnie wdrożyć aplikację. W tym artykule używamy ustawień publikowania dla usług IIS, ale możesz użyć podobnych kroków, aby zaimportować ustawienia publikowania dla [usługi Azure App Service](../deployment/tutorial-import-publish-settings-azure.md). W niektórych scenariuszach Użyj publikowania profilu ustawień może być szybsze niż ręcznie konfigurować wdrożenia w usługach IIS dla każdej instalacji programu Visual Studio.

Te kroki mają zastosowanie do aplikacji platformy ASP.NET, ASP.NET Core i .NET Core w programie Visual Studio.

W tym samouczku wykonasz następujące czynności:

> [!div class="checklist"]
> * Konfigurowanie usług IIS tak, aby wygenerować plik ustawień publikowania
> * Utwórz plik ustawień publikowania
> * Importuj plik ustawień publikowania w programie Visual Studio
> * Wdrażanie aplikacji w usługach IIS

Plik ustawień publikowania (*\*.publishsettings*) różni się od profilu publikowania (*\*.pubxml*) utworzone w programie Visual Studio. Plik ustawień publikowania jest tworzony przez usługi IIS lub usługi Azure App Service, lub można utworzyć ręcznie, a następnie mogą być importowane do programu Visual Studio.

> [!NOTE]
> Jeśli chcesz tylko do kopiowania programu Visual Studio profil publikowania (\*pliku .pubxml) z jednej instalacji programu Visual Studio do innego, można znaleźć profilu publikowania  *\<profilename\>.pubxml*, w  *\\< nazwa_projektu\>\Properties\PublishProfiles* folder typami projektów zarządzanych. Dla witryn sieci Web, sprawdź w obszarze *\App_Data* folderu. Profile publikowania są plikami XML programu MSBuild.

## <a name="prerequisites"></a>Wymagania wstępne

::: moniker range=">=vs-2019"

* Konieczne jest posiadanie programu Visual Studio 2019 r zainstalowane i **ASP.NET i tworzenie aplikacji internetowych** obciążenia.

    Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/) strony, aby zainstalować go za darmo.
::: moniker-end

::: moniker range="vs-2017"

* Konieczne jest posiadanie programu Visual Studio 2017 i **ASP.NET i tworzenie aplikacji internetowych** obciążenia.

    Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/) strony, aby zainstalować go za darmo.
::: moniker-end

* Na serwerze, musi zostać uruchomiony system Windows Server 2012 lub Windows Server 2016, a musi mieć [roli serwera sieci Web usług IIS](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) poprawnie zainstalowana (wymagane, aby wygenerować plik ustawień publikowania (*\*. publishsettings*)). ASP.NET 4.5 lub ASP.NET Core należy także zainstalować na serwerze. Aby skonfigurować ASP.NET 4.5, zobacz [3.5 przy użyciu platformy ASP.NET w programie IIS 8.0 i program ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45). Aby skonfigurować platformy ASP.NET Core, zobacz [hosta ASP.NET Core na Windows z programem IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Utwórz nowy projekt ASP.NET w programie Visual Studio

1. Na komputerze z programem Visual Studio Utwórz nowy projekt.

    Wybierz prawidłowy szablon. W tym przykładzie wybierz **aplikacji sieci Web platformy ASP.NET (.NET Framework)** lub (dla C# tylko) **aplikacji sieci Web programu ASP.NET Core**, a następnie kliknij przycisk **OK**.

    Jeśli nie widzisz szablony określonego projektu, kliknij przycisk **Otwórz Instalator programu Visual Studio** łącze w okienku po lewej stronie **nowy projekt** okno dialogowe. Uruchamia Instalatora programu Visual Studio. Zainstaluj **ASP.NET i tworzenie aplikacji internetowych** obciążenia.

    Szablon projektu, wybierz (ASP.NET lub ASP.NET Core) musi odpowiadać wersji zainstalowanych na serwerze sieci web platformy ASP.NET.

1. Wybierz opcję **MVC** (.NET Framework) lub **aplikacji sieci Web (Model-View-Controller)** (dla platformy .NET Core) i upewnij się, że **bez uwierzytelniania** jest zaznaczone, a następnie kliknij przycisk **OK**.

1. Wpisz nazwę, takich jak **MyWebApp** i kliknij przycisk **OK**.

    Program Visual Studio tworzy projekt.

1. Wybierz **kompilacji** > **Kompiluj rozwiązanie** do skompilowania projektu.

## <a name="install-and-configure-web-deploy-on-windows-server"></a>Instalowanie i Konfigurowanie narzędzia Web Deploy w systemie Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

## <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Utwórz plik ustawień publikowania w usługach IIS w systemie Windows Server

[!INCLUDE [create-publish-settings-iis](../deployment/includes/create-publish-settings-iis.md)]

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importowanie ustawień publikowania w programie Visual Studio i wdrażanie

[!INCLUDE [import-publish-settings](../deployment/includes/import-publish-settings-vs.md)]

Po pomyślnym wdrożeniu aplikacji powinna być uruchamiana automatycznie. Jeśli nie zostanie uruchomiony z programu Visual Studio, należy uruchomić aplikację w usługach IIS. Dla platformy ASP.NET Core, należy się upewnić, że pula aplikacji pole **DefaultAppPool** ustawiono **bez kodu zarządzanego**.

## <a name="next-steps"></a>Następne kroki

W tym samouczku utworzono plik ustawień publikowania, zaimportowany do programu Visual Studio i wdrożoną aplikację ASP.NET w usługach IIS. Możesz się z omówieniem inne opcje publikowania w programie Visual Studio.

> [!div class="nextstepaction"]
> [Pierwsze spojrzenie na wdrażanie](../deployment/deploying-applications-services-and-components.md)

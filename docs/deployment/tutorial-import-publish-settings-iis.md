---
title: Publikowanie w usługach IIS przez zaimportowanie ustawień publikowania
description: Tworzenie i importowanie profilu publikowania w celu wdrożenia aplikacji z programu Visual Studio w usługach IIS
ms.date: 05/06/2020
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fff3ded8607f7faf534e6e61a27bd4d3e38d9e38
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "88247563"
---
# <a name="publish-an-application-to-iis-by-importing-publish-settings-in-visual-studio"></a>Publikowanie aplikacji w usługach IIS przez zaimportowanie ustawień publikowania w programie Visual Studio

Możesz użyć narzędzia do **publikowania** , aby zaimportować ustawienia publikowania, a następnie wdrożyć aplikację. W tym artykule używamy ustawień publikowania dla usług IIS, ale możesz użyć podobnych kroków, aby zaimportować ustawienia publikowania dla [Azure App Service](../deployment/tutorial-import-publish-settings-azure.md). W niektórych scenariuszach korzystanie z profilu ustawień publikowania może być szybsze niż ręczne konfigurowanie wdrożenia w usługach IIS dla każdej instalacji programu Visual Studio.

Te kroki dotyczą aplikacji ASP.NET, ASP.NET Core i .NET Core w programie Visual Studio.

W tym samouczku wykonasz następujące czynności:

> [!div class="checklist"]
> * Skonfiguruj usługi IIS, aby można było generować plik ustawień publikowania
> * Tworzenie pliku ustawień publikowania
> * Importowanie pliku ustawień publikowania do programu Visual Studio
> * Wdrażanie aplikacji w usługach IIS

Plik ustawień publikowania (* \* . publishsettings*) jest inny niż profil publikacji (* \* . pubxml*) utworzony w programie Visual Studio. Plik ustawień publikowania jest tworzony przez usługi IIS lub Azure App Service lub można go utworzyć ręcznie, a następnie można go zaimportować do programu Visual Studio.

> [!NOTE]
> Jeśli wystarczy skopiować profil publikacji programu Visual Studio ( \* plik. pubxml) z jednej instalacji programu Visual Studio do innej, można znaleźć profil publikowania, * \<profilename\> . pubxml*, w folderze * \\<ProjectName \> \Properties\PublishProfiles* dla typów projektów zarządzanych. W przypadku witryn sieci Web zapoznaj się z folderem *\ App_Data* . Profile publikowania są plikami XML programu MSBuild.

## <a name="prerequisites"></a>Wymagania wstępne

::: moniker range=">=vs-2019"

* Musisz mieć zainstalowany program Visual Studio 2019 i obciążenie **programowaniem ASP.NET i sieci Web** .

    Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads/),   Aby zainstalować ją bezpłatnie.
::: moniker-end

::: moniker range="vs-2017"

* Musisz mieć zainstalowany program Visual Studio 2017 i obciążenie **programowaniem ASP.NET i sieci Web** .

    Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads/),   Aby zainstalować ją bezpłatnie.
::: moniker-end

* Na serwerze musi być zainstalowany system Windows Server 2012, Windows Server 2016 lub Windows Server 2019 i musi być zainstalowana [rola serwera sieci Web usług IIS](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) (wymagana do wygenerowania pliku ustawień publikowania (* \* . publishsettings*)). Na serwerze należy również zainstalować ASP.NET 4,5 lub ASP.NET Core. Aby skonfigurować ASP.NET 4,5, zobacz [usługi IIS 8,0 przy użyciu ASP.NET 3,5 i ASP.NET 4,5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45). Aby skonfigurować ASP.NET Core, zobacz [hostowanie ASP.NET Core w systemie Windows za pomocą usług IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration). W przypadku ASP.NET Core upewnij się, że skonfigurowano pulę aplikacji tak, aby korzystała z **kodu zarządzanego**, zgodnie z opisem w artykule.

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Tworzenie nowego projektu ASP.NET w programie Visual Studio

1. Na komputerze z uruchomionym programem Visual Studio Utwórz nowy projekt.

    Wybierz odpowiedni szablon. W tym przykładzie wybierz pozycję **aplikacja sieci web ASP.NET (.NET Framework)** lub (tylko w przypadku języka C#) **ASP.NET Core aplikacja internetowa**, a następnie wybierz przycisk **OK**.

    Jeśli nie widzisz określonych szablonów projektu, przejdź do linku **otwórz Instalator programu Visual Studio** w lewym okienku okna dialogowego **Nowy projekt** . Zostanie uruchomiona Instalator programu Visual Studio. Zainstaluj **ASP.NET i programowanie aplikacji sieci Web** .

    Wybrany szablon projektu (ASP.NET lub ASP.NET Core) musi odpowiadać wersji ASP.NET zainstalowanej na serwerze sieci Web.

1. Wybierz opcję **MVC** (.NET Framework) lub **aplikacja sieci Web (Model-View-Controller)** (dla platformy .NET Core) i upewnij się, że nie wybrano **żadnego uwierzytelniania** , a następnie wybierz przycisk **OK**.

1. Wpisz nazwę, taką jak **MyWebApp** , i wybierz **przycisk OK**.

    Program Visual Studio tworzy projekt.

1. Wybierz pozycję **Kompiluj**  >  **kompilację rozwiązania** , aby skompilować projekt.

## <a name="install-and-configure-web-deploy-on-windows-server"></a>Instalowanie i Konfigurowanie Web Deploy w systemie Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

## <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Tworzenie pliku ustawień publikowania w usługach IIS w systemie Windows Server

[!INCLUDE [create-publish-settings-iis](../deployment/includes/create-publish-settings-iis.md)]

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importowanie ustawień publikowania w programie Visual Studio i wdrażanie

[!INCLUDE [import-publish-settings](../deployment/includes/import-publish-settings-vs.md)]

Po pomyślnym wdrożeniu aplikacji należy uruchomić ją automatycznie. Jeśli nie zostanie uruchomiony z programu Visual Studio, uruchom aplikację w usługach IIS. Aby uzyskać ASP.NET Core, należy upewnić się, że w polu Pula aplikacji dla **tej opcji określono** wartość **Brak kodu zarządzanego**.

## <a name="next-steps"></a>Następne kroki

W tym samouczku utworzono plik ustawień publikowania, zaimportowano go do programu Visual Studio i wdrożono aplikację ASP.NET w usługach IIS. Możesz chcieć zapoznać się z innymi opcjami publikowania w programie Visual Studio.

> [!div class="nextstepaction"]
> [Pierwsze spojrzenie na wdrażanie](../deployment/deploying-applications-services-and-components.md)

---
title: Pierwsze spojrzenie na wdrażanie
description: Dowiedz się więcej na temat opcji wdrażania aplikacji w programie Visual Studio.
ms.custom: mvc
ms.date: 01/29/2019
ms.topic: quickstart
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- .NET applications, deploying
- components [Visual Studio], deploying
- installers
- publishing
- deploying applications [Visual Studio]
- deploying applications [Visual Studio], about deploying applications
- components [.NET Framework], deploying
ms.assetid: 63fcdd5b-2e54-4210-9038-65bc23167725
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3a8301fcca5fd915b130477600ed9fe0b5b90f46
ms.sourcegitcommit: c31815e140f2ec79e00a9a9a19900778ec11e860
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2020
ms.locfileid: "91830777"
---
# <a name="first-look-at-deployment-in-visual-studio"></a>Pierwsze spojrzenie na wdrożenie w programie Visual Studio

Przez wdrożenie aplikacji, usługi lub składnika, należy go rozesłać do instalacji na innych komputerach, urządzeniach lub serwerach lub w chmurze. W programie Visual Studio możesz wybrać odpowiednią metodę w zależności od typu wdrożenia, jakiego potrzebujesz. (Wiele typów aplikacji obsługuje inne narzędzia do wdrażania, takie jak wdrażanie wiersza polecenia lub NuGet, które nie zostały opisane w tym miejscu).

Zapoznaj się z przewodnikami Szybki Start i samouczkami, aby uzyskać instrukcje krok po kroku. Aby zapoznać się z omówieniem opcji wdrożenia, zobacz, [jakie opcje publikowania są odpowiednie dla mnie?](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me).

## <a name="deploy-to-local-folder"></a>Wdróż w folderze lokalnym

Wdrożenie do folderu lokalnego jest zwykle używane do testowania lub do rozpoczęcia wdrożenia etapowego, w którym jest używane inne narzędzie do wdrożenia końcowego.

- **ASP.NET**, **ASP.NET Core**, **Node.js**, **Python**i. **NET Core**: Użyj narzędzia do publikowania do wdrożenia w folderze lokalnym. Dokładne dostępne opcje zależą od typu aplikacji. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Publikuj**. (Jeśli nie skonfigurowano wcześniej żadnych profilów publikowania, należy kliknąć przycisk **Utwórz nowy profil**). Następnie wybierz **folder**. Aby uzyskać więcej informacji, zobacz [wdrażanie w folderze lokalnym](quickstart-deploy-to-local-folder.md).

    ![Wybierz pozycję Publikuj](../deployment/media/quickstart-publish.png)

- **Pulpit systemu Windows** Aplikację klasyczną systemu Windows można opublikować w folderze przy użyciu wdrażania ClickOnce. Użytkownicy mogą następnie zainstalować aplikację za pomocą jednego kliknięcia. Aby uzyskać więcej informacji, zobacz [wdrażanie aplikacji klasycznej przy użyciu technologii ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# i Visual Basic). W przypadku języka C++/CLR zobacz [wdrażanie aplikacji natywnej przy użyciu technologii ClickOnce](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) lub dla języka C/C++, zobacz [wdrażanie aplikacji natywnej przy użyciu projektu instalacji](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="publish-to-azure"></a>Publikowanie na platformie Azure

- **ASP.NET**, **ASP.NET Core**, **Python**i **Node.js**: publikowanie w Azure App Service lub Azure App Service Linux (przy użyciu kontenerów) przy użyciu jednej z poniższych metod.

  - Aby ciągłe (lub zautomatyzowane) wdrażanie aplikacji, użyj platformy Azure DevOps z [Azure Pipelines](/azure/devops/pipelines/get-started-yaml?view=azdevops&preserve-view=true).

  - W przypadku wdrożenia aplikacji jednorazowego (lub ręcznego) Użyj narzędzia do **publikowania** w programie Visual Studio.

  W przypadku wdrażania, które zapewnia bardziej dostosowaną konfigurację serwera, można także użyć narzędzia do **publikowania** do wdrożenia aplikacji na maszynie wirtualnej platformy Azure.

  Aby użyć narzędzia do **publikowania** , kliknij prawym przyciskiem myszy projekt w Eksplorator rozwiązań i wybierz polecenie **Publikuj**. (Jeśli wcześniej skonfigurowano wszystkie profile publikowania, należy kliknąć przycisk **Utwórz nowy profil**). W oknie dialogowym Publikowanie wybierz opcję **App Service** lub **Azure Virtual Machines**, a następnie postępuj zgodnie z procedurami konfiguracji.

  ![Wybierz Azure App Service](../deployment/media/quickstart-publish-azure-new.png "Wybierz Azure App Service")

  Począwszy od programu Visual Studio 2017 w wersji 15,7, można wdrożyć aplikacje ASP.NET Core w **App Service dla systemu Linux**.

  W przypadku aplikacji w języku Python Zobacz również sekcję [Publikowanie w języku Python, aby uzyskać Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json).

  Aby zapoznać się z krótkim wprowadzeniem, zobacz [Publikowanie na platformie Azure](quickstart-deploy-to-azure.md) i [Publikowanie w systemie Linux](quickstart-deploy-to-linux.md). Zobacz też temat [publikowanie aplikacji ASP.NET Core na platformie Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). Aby uzyskać wdrożenie przy użyciu narzędzia Git, zobacz [ciągłe wdrażanie ASP.NET Core na platformie Azure za pomocą narzędzia Git](/aspnet/core/publishing/azure-continuous-deployment).

  Aby uzyskać informacje na temat importowania profilu publikowania z programu Azure App Service do programu Visual Studio, zobacz [Importowanie ustawień publikowania i wdrażanie na platformie Azure](../deployment/tutorial-import-publish-settings-azure.md).

  > [!NOTE]
  > Jeśli nie masz jeszcze konta platformy Azure, możesz [zarejestrować się tutaj](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio).

## <a name="publish-to-web-or-deploy-to-network-share"></a>Publikowanie w Internecie lub wdrażanie w udziale sieciowym

- **ASP.NET**, **ASP.NET Core**, **Node.js**i **Python**: można użyć narzędzia do publikowania do wdrożenia w witrynie sieci Web za pomocą protokołu FTP lub Web Deploy. Aby uzyskać więcej informacji, zobacz [wdrażanie w witrynie sieci Web](quickstart-deploy-to-a-web-site.md).

    W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Publikuj**. (Jeśli wcześniej skonfigurowano wszystkie profile publikowania, należy kliknąć przycisk **Utwórz nowy profil**). W narzędziu do publikowania wybierz żądaną opcję i wykonaj kroki konfiguracji.

    ![Wybieranie usług IIS](../deployment/media/quickstart-publish-iis.png)

    Aby uzyskać informacje na temat importowania profilu publikowania w programie Visual Studio, zobacz [Importowanie ustawień publikowania i wdrażanie w usługach IIS](../deployment/tutorial-import-publish-settings-iis.md).

    Możesz również wdrożyć aplikacje i usługi ASP.NET na wiele innych sposobów. Aby uzyskać więcej informacji, zobacz [wdrażanie aplikacji i usług sieci web ASP.NET](/aspnet/overview/deployment).

- **Pulpit systemu Windows** Można opublikować aplikację klasyczną systemu Windows na serwerze sieci Web lub sieciowym udziale plików przy użyciu wdrażania ClickOnce. Użytkownicy mogą następnie zainstalować aplikację za pomocą jednego kliknięcia. Aby uzyskać więcej informacji, zobacz [wdrażanie aplikacji klasycznej przy użyciu technologii ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# i Visual Basic). W przypadku języka C++/CLR zobacz [wdrażanie aplikacji natywnej przy użyciu technologii ClickOnce](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) lub dla języka C/C++, zobacz [wdrażanie aplikacji natywnej przy użyciu projektu instalacji](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="publish-to-microsoft-store"></a>Publikuj w Microsoft Store

W programie Visual Studio można tworzyć pakiety aplikacji do wdrożenia w Microsoft Store.

- **Platformy UWP**: Możesz spakować aplikację i wdrożyć ją za pomocą elementów menu. Aby uzyskać więcej informacji, zobacz [pakowanie aplikacji platformy UWP przy użyciu programu Visual Studio](/windows/uwp/packaging/packaging-uwp-apps).

    ![Tworzenie pakietu aplikacji](../deployment/media/feature-tour-create-app-package.png)

- **Pulpit systemu Windows**: można wdrożyć do Microsoft Store przy użyciu mostka programu Desktop, począwszy od programu Visual Studio 2017 w wersji 15,4. Aby to zrobić, Zacznij od utworzenia projektu pakietu aplikacji systemu Windows. Aby uzyskać więcej informacji, zobacz [pakowanie aplikacji klasycznych dla Microsoft Store (mostek Desktop)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net).

    ![Mostek Desktop](../deployment/media/feature-tour-desktop-bridge.png)

## <a name="deploy-to-a-device-uwp"></a>Wdrażanie na urządzeniu (platformy UWP)

Jeśli wdrażasz aplikację platformy UWP do testowania na urządzeniu, zobacz [Uruchamianie aplikacji platformy UWP na maszynie zdalnej w programie Visual Studio](../debugger/run-windows-store-apps-on-a-remote-machine.md).

## <a name="create-an-installer-package-windows-desktop"></a>Tworzenie pakietu Instalatora (Windows Desktop)

Jeśli potrzebujesz większej złożonej instalacji aplikacji klasycznej niż zapewnianie technologii [ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) , możesz utworzyć pakiet Instalator Windows (plik instalacyjny MSI lub exe) lub niestandardowy program inicjujący.

- Pakiet Instalatora oparty na instalatorze MSI można utworzyć przy użyciu [rozszerzenia zestawu narzędzi WIX dla programu Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension). Jest to zestaw narzędzi wiersza polecenia.

- Pakiet Instalatora MSI lub EXE można utworzyć przy użyciu narzędzia [InstallShield](https://www.flexerasoftware.com/producer/products/software-installation/installshield-software-installer/tab/requirements) z oprogramowania Flexera. Program InstallShield może być używany z programem Visual Studio 2017 i nowszymi wersjami (wersja Community nie jest obsługiwana).

  > [!NOTE]
  > Program InstallShield Limited Edition nie jest już uwzględniony w programie Visual Studio i nie jest obsługiwany w programie Visual Studio 2017 i nowszych wersjach. Zapoznaj się z [oprogramowaniem Flexera](http://learn.flexerasoftware.com/content/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio) na temat przyszłej dostępności.

- Pakiet Instalatora MSI lub EXE można utworzyć przy użyciu projektu konfiguracji (VDPROJ). Aby użyć tej opcji, zainstaluj [rozszerzenie projekty Instalator programu Visual Studio](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.MicrosoftVisualStudio2017InstallerProjects#overview).

- Wstępnie wymagane składniki dla aplikacji klasycznych można również zainstalować, konfigurując Instalator generyczny, który jest znany jako program inicjujący. Aby uzyskać więcej informacji, zobacz [wymagania wstępne dotyczące wdrażania aplikacji](../deployment/application-deployment-prerequisites.md).

## <a name="deploy-to-test-lab"></a>Wdróż w laboratorium testowym

Możesz włączyć bardziej zaawansowane programowanie i testowanie, wdrażając aplikacje w środowiskach wirtualnych. Aby uzyskać więcej informacji, zobacz [test w środowisku laboratoryjnym](../test/lab-management/using-a-lab-environment-for-your-application-lifecycle.md).

## <a name="continuous-deployment"></a>Ciągłe wdrażanie

Za pomocą Azure Pipelines można włączyć ciągłe wdrażanie aplikacji. Aby uzyskać więcej informacji, zobacz [Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true) i [wdrażania na platformie Azure](/azure/devops/deploy-azure/index?view=vsts&preserve-view=true).

## <a name="deploy-a-sql-database"></a>Wdrażanie bazy danych SQL

- [Zmień platformę docelową i Opublikuj projekt bazy danych (SQL Server Data Tools (SSDT))](/sql/ssdt/how-to-change-target-platform-and-publish-a-database-project)

- [Wdróż projekt Analysis Services (SSAS)](/sql/analysis-services/multidimensional-tutorial/lesson-2-5-deploying-an-analysis-services-project)

- [Wdróż projekty i pakiety usług Integration Services (SSIS)](/sql/integration-services/packages/deploy-integration-services-ssis-projects-and-packages)

- [Kompilowanie i wdrażanie w lokalnej bazie danych](/sql/ssdt/how-to-build-and-deploy-to-a-local-database)

## <a name="deployment-for-other-app-types"></a>Wdrożenie dla innych typów aplikacji

| Typ aplikacji | Scenariusz wdrażania | Łącze |
| --- | --- | --- |
| **Aplikacja pakietu Office** | Dodatek dla pakietu Office można opublikować w programie Visual Studio. | [Wdrażanie i publikowanie dodatku dla pakietu Office](https://dev.office.com/docs/add-ins/publish/publish) |
| **Usługa WCF lub OData** | Inne aplikacje mogą używać usług WCF RIA wdrożonych na serwerze sieci Web. | [Opracowywanie i wdrażanie Usługi danych programu WCF](/dotnet/framework/data/wcf/developing-and-deploying-wcf-data-services) |
| **LightSwitch** | LightSwitch nie jest już obsługiwany w programie Visual Studio 2017, ale nadal można ją wdrożyć z poziomu programu Visual Studio 2015 lub starszej wersji. | [Wdrażanie aplikacji LightSwitch](/previous-versions/ff872288(v=vs.140)) |

## <a name="next-steps"></a>Następne kroki

W tym samouczku zawarto krótkie zapoznaj się z opcjami wdrażania dla różnych aplikacji.

> [!div class="nextstepaction"]
> [Jakie opcje publikowania są odpowiednie dla mnie?](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me)
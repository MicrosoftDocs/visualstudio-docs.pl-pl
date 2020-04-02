---
title: Pierwsze spojrzenie na wdrażanie
description: Dowiedz się więcej o opcjach wdrażania aplikacji z programu Visual Studio.
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
ms.openlocfilehash: 1a45dea4b386be418f078f6947487b42f7d968e7
ms.sourcegitcommit: 054815dc9821c3ea219ae6f31ebd9cd2dc8f6af5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2020
ms.locfileid: "80543957"
---
# <a name="first-look-at-deployment-in-visual-studio"></a>Pierwsze spojrzenie na wdrożenie w programie Visual Studio

Wdrażając aplikację, usługę lub składnik, rozpowszechniasz ją do instalacji na innych komputerach, urządzeniach lub serwerach lub w chmurze. W programie Visual Studio możesz wybrać odpowiednią metodę w zależności od typu wdrożenia, jakiego potrzebujesz. (Wiele typów aplikacji obsługuje inne narzędzia wdrażania, takie jak wdrażanie wiersza polecenia, które nie są opisane w tym miejscu).

Zapoznaj się z przewodnikami Szybki start i samouczkami, aby uzyskać instrukcje wdrażania krok po kroku. Aby uzyskać przegląd opcji wdrażania, zobacz [Jakie opcje publikowania są dla mnie odpowiednie?](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me).

## <a name="deploy-to-local-folder"></a>Wdrażanie w folderze lokalnym

Wdrożenie do folderu lokalnego jest zwykle używane do testowania lub do rozpoczęcia wdrożenia etapowego, w którym inne narzędzie jest używane do ostatecznego wdrożenia.

- **ASP.NET**, **ASP.NET Core**, **Node.js**, **Python**i . **NET Core**: Użyj narzędzia Publikowania, aby wdrożyć je w folderze lokalnym. Dokładne dostępne opcje zależą od typu aplikacji. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Publikuj**. (Jeśli wcześniej nie skonfigurowano żadnych profilów publikowania, należy kliknąć przycisk **Utwórz nowy profil).** Następnie **wybierz**folder . Aby uzyskać więcej informacji, zobacz [Wdrażanie w folderze lokalnym](quickstart-deploy-to-local-folder.md).

    ![Wybierz pozycję Publikuj](../deployment/media/quickstart-publish.png)

- **Pulpit systemu Windows** Aplikację klasyczną systemu Windows można opublikować w folderze przy użyciu wdrożenia ClickOnce. Użytkownicy mogą następnie zainstalować aplikację za pomocą jednego kliknięcia. Aby uzyskać więcej informacji, zobacz [Wdrażanie aplikacji klasycznej przy użyciu ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# i Visual Basic). W przypadku języka C++/CLI zobacz [Wdrażanie aplikacji natywnej przy użyciu funkcji ClickOnce](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) lub w przypadku języka C/C++, zobacz [Wdrażanie aplikacji natywnej przy użyciu projektu instalatora](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="publish-to-azure"></a>Publikowanie na platformie Azure

- **ASP.NET**, **ASP.NET Core**, **Python**i **Node.js:** Publikuj w usłudze Azure App Service lub usłudze Azure App Service Linux (przy użyciu kontenerów) przy użyciu jednej z następujących metod.

  - W przypadku ciągłego (lub zautomatyzowanego) wdrażania aplikacji należy używać usługi Azure DevOps z [usługą Azure Pipelines](/azure/devops/pipelines/get-started-yaml?view=azdevops).

  - W przypadku jednorazowego (lub ręcznego) wdrażania aplikacji użyj narzędzia **Publikowania** w programie Visual Studio.

  W przypadku wdrożenia, które zapewnia bardziej dostosowaną konfigurację serwera, można również użyć narzędzia **Publikowania** do wdrażania aplikacji na maszynie wirtualnej platformy Azure.

  Aby użyć narzędzia **Publikowanie,** kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań i wybierz polecenie **Publikuj**. (Jeśli wcześniej skonfigurowano profile publikowania, należy kliknąć przycisk **Utwórz nowy profil).** W oknie dialogowym Publikowanie wybierz pozycję **App Service** lub Azure **Virtual Machines**, a następnie wykonaj kroki konfiguracji.

  ![Wybieranie usługi aplikacji platformy Azure](../deployment/media/quickstart-publish-azure.png "Wybieranie usługi aplikacji platformy Azure")

  Począwszy od programu Visual Studio 2017 w wersji 15.7, można wdrożyć aplikacje ASP.NET Core do **usługi App Service dla systemu Linux**.

  W przypadku aplikacji języka Python zobacz też [Python — publikowanie w usłudze Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json).

  Aby uzyskać krótkie wprowadzenie, zobacz [Publikowanie na platformie Azure](quickstart-deploy-to-azure.md) i [Publikowanie w systemie Linux](quickstart-deploy-to-linux.md). Zobacz też [Publikowanie aplikacji ASP.NET Core na platformie Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). Aby rozpocząć wdrażanie przy użyciu git, zobacz [Ciągłe wdrażanie ASP.NET Core na platformie Azure za pomocą git](/aspnet/core/publishing/azure-continuous-deployment).

  Aby uzyskać informacje dotyczące importowania profilu publikowania z usługi Azure App Service do programu Visual Studio, zobacz [Importowanie ustawień publikowania i wdrażanie na platformie Azure](../deployment/tutorial-import-publish-settings-azure.md).

  > [!NOTE]
  > Jeśli nie masz jeszcze konta platformy Azure, możesz [zarejestrować się tutaj](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio).

## <a name="publish-to-web-or-deploy-to-network-share"></a>Publikowanie w sieci Web lub wdrażanie w udziale sieciowym

- **ASP.NET** **, ASP.NET Core**, **Node.js**i **Python:** Za pomocą narzędzia Publikowania można wdrożyć w witrynie sieci Web przy użyciu protokołu FTP lub wdrożenia w sieci Web. Aby uzyskać więcej informacji, zobacz [Wdrażanie w witrynie sieci Web](quickstart-deploy-to-a-web-site.md).

    W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Publikuj**. (Jeśli wcześniej skonfigurowano profile publikowania, należy kliknąć przycisk **Utwórz nowy profil).** W narzędziu Publikowanie wybierz odpowiednią opcję i postępuj zgodnie z instrukcjami konfiguracji.

    ![Wybierz iIS, FTP itp.](../deployment/media/quickstart-publish-iis-ftp.png)

    Aby uzyskać informacje dotyczące importowania profilu publikowania w programie Visual Studio, zobacz [Importowanie ustawień publikowania i wdrażanie w serwisach IIS](../deployment/tutorial-import-publish-settings-iis.md).

    Można również wdrożyć ASP.NET aplikacji i usług na wiele innych sposobów. Aby uzyskać więcej informacji, zobacz [Wdrażanie ASP.NET aplikacji sieci Web i usług](/aspnet/mvc/overview/deployment/).

- **Pulpit systemu Windows** Aplikację klasyczną systemu Windows można opublikować na serwerze sieci web lub w sieciowym udziale plików przy użyciu wdrożenia ClickOnce. Użytkownicy mogą następnie zainstalować aplikację za pomocą jednego kliknięcia. Aby uzyskać więcej informacji, zobacz [Wdrażanie aplikacji klasycznej przy użyciu ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# i Visual Basic). W przypadku języka C++/CLI zobacz [Wdrażanie aplikacji natywnej przy użyciu funkcji ClickOnce](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) lub w przypadku języka C/C++, zobacz [Wdrażanie aplikacji natywnej przy użyciu projektu instalatora](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="publish-to-microsoft-store"></a>Publikowanie w sklepie Microsoft Store

W programie Visual Studio można tworzyć pakiety aplikacji do wdrożenia w sklepie Microsoft Store.

- **UwP**: Można spakować aplikację i wdrożyć go przy użyciu elementów menu. Aby uzyskać więcej informacji, zobacz [Pakowanie aplikacji platformy uniwersalnej systemu wyurzcie](/windows/uwp/packaging/packaging-uwp-apps)na platformy uniwersalnej systemu wizowego przy użyciu programu Visual Studio .

    ![Tworzenie pakietu aplikacji](../deployment/media/feature-tour-create-app-package.jpg)

- **Pulpit systemu Windows:** Można wdrożyć w sklepie Microsoft Store, począwszy od programu Visual Studio 2017 w wersji 15.4. Aby to zrobić, zacznij od utworzenia projektu pakowania aplikacji systemu Windows. Aby uzyskać więcej informacji, zobacz [Pakowanie aplikacji klasycznej dla sklepu Microsoft Store](/windows/msix/desktop/desktop-to-uwp-packaging-dot-net).

    ![Pakowanie aplikacji klasycznej](../deployment/media/feature-tour-desktop-bridge.png)

## <a name="deploy-net-packages-to-nugetorg"></a>Wdrażanie pakietów .NET w celu NuGet.org

Aby wdrożyć kod w pakiecie w "pakiety", które zawierają skompilowany kod (jako biblioteki DLL) wraz z inną zawartością potrzebną w projektach, które korzystają z tych pakietów, można użyć programu Visual Studio do utworzenia pakietu NuGet i narzędzia interfejsu wiersza polecenia do wydania polecenia ostatecznego wdrożenia.

- [Tworzenie i publikowanie pakietu .NET Standard](/nuget/quickstart/create-and-publish-a-package-using-visual-studio)
- [Tworzenie i publikowanie pakietu .NET Framework](/nuget/quickstart/create-and-publish-a-package-using-visual-studio-net-framework)

## <a name="deploy-to-a-device-uwp"></a>Wdrażanie na urządzeniu (UWP)

Jeśli wdrażasz aplikację platformy uniwersalnej systemu Windows do testowania na urządzeniu, zobacz [Uruchamianie aplikacji platformy uniwersalnej systemu Windows na komputerze zdalnym w programie Visual Studio](../debugger/run-windows-store-apps-on-a-remote-machine.md).

## <a name="create-an-installer-package-windows-desktop"></a>Tworzenie pakietu instalacyjnego (pulpit systemu Windows)

Jeśli potrzebujesz więcej złożonej instalacji aplikacji klasycznej niż [ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) może zapewnić, można utworzyć pakiet Instalatora Windows (MSI lub EXE plik instalacyjny) lub niestandardowy program uruchamiający.

- Pakiet instalatora oparty na msi można utworzyć za pomocą [rozszerzenia WiX Toolset](https://marketplace.visualstudio.com/items?itemName=WixToolset.WiXToolset). Jest to zestaw narzędzi wiersza polecenia.

   ::: moniker range=">=vs-2019"
   W programie Visual Studio 2019 pobierz [rozszerzenie programu WiX Toolset Visual Studio 2019](https://marketplace.visualstudio.com/items?itemName=WixToolset.WixToolsetVisualStudio2019Extension).
   ::: moniker-end

- Pakiet instalatora MSI lub EXE można utworzyć za pomocą [InstallShield](https://www.flexerasoftware.com/producer/products/software-installation/installshield-software-installer/tab/requirements) firmy Flexera Software. InstallShield może być używany z programem Visual Studio 2017 i nowszymi wersjami (wersja społecznościowa nie jest obsługiwana). Należy zauważyć, że InstallShield Limited Edition nie jest już dołączony do programu Visual Studio i nie jest obsługiwany w programie Visual Studio 2017 i nowszych wersjach; skontaktuj się z [Oprogramowaniem Flexera](https://info.flexerasoftware.com/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio) na temat przyszłej dostępności.

- Pakiet instalatora MSI lub EXE można utworzyć przy użyciu projektu Instalatora (vdproj). Aby użyć tej opcji, należy zainstalować [rozszerzenie Projekty instalatora programu Visual Studio](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.MicrosoftVisualStudio2017InstallerProjects#overview).

- Składniki wymaganego pod warunkiem wstępnego dla aplikacji klasycznych można również zainstalować, konfigurując instalator ogólny, który jest znany jako program uruchamiający. Aby uzyskać więcej informacji, zobacz Wymagania wstępne [dotyczące wdrażania aplikacji](../deployment/application-deployment-prerequisites.md).

## <a name="deploy-to-test-lab"></a>Wdrażanie w laboratorium testowym

Bardziej zaawansowane programowanie i testowanie można włączyć, wdrażając aplikacje w środowiskach wirtualnych. Aby uzyskać więcej informacji, zobacz [Testowanie w środowisku laboratoryjnym](../test/lab-management/using-a-lab-environment-for-your-application-lifecycle.md).

## <a name="continuous-deployment"></a>Ciągłe wdrażanie

Za pomocą usługi Azure Pipelines można włączyć ciągłe wdrażanie aplikacji. Aby uzyskać więcej informacji, zobacz [Potoki platformy Azure](/azure/devops/pipelines/index?view=vsts) i [wdrażanie na platformie Azure](/azure/devops/deploy-azure/index?view=vsts).

## <a name="deploy-a-sql-database"></a>Wdrażanie bazy danych SQL

- [Zmienianie platformy docelowej i publikowanie projektu bazy danych (SQL Server Data Tools (SSDT))](/sql/ssdt/how-to-change-target-platform-and-publish-a-database-project)

- [Wdrażanie projektu usług Analysis Services (SSAS)](/sql/analysis-services/multidimensional-tutorial/lesson-2-5-deploying-an-analysis-services-project)

- [Wdrażanie projektów i pakietów usług integracyjnych (SSIS)](/sql/integration-services/packages/deploy-integration-services-ssis-projects-and-packages)

- [Tworzenie i wdrażanie w lokalnej bazie danych](/sql/ssdt/how-to-build-and-deploy-to-a-local-database)

## <a name="deployment-for-other-app-types"></a>Wdrażanie dla innych typów aplikacji

| Typ aplikacji | Scenariusz wdrażania | Link |
| --- | --- | --- |
| **Aplikacja pakietu Office** | Dodatek dla pakietu Office można opublikować w programie Visual Studio. | [Wdrażanie i publikowanie dodatku pakietu Office](/office/dev/add-ins/publish/publish) |
| **Usługa WCF lub OData** | Inne aplikacje mogą korzystać z usług WCF RIA, które można wdrożyć na serwerze sieci web. | [Tworzenie i wdrażanie usług danych WCF](/dotnet/framework/data/wcf/developing-and-deploying-wcf-data-services) |
| **LightSwitch** | LightSwitch nie jest już obsługiwany począwszy od programu Visual Studio 2017, ale nadal można wdrożyć w programie Visual Studio 2015 i wcześniej. | [Wdrażanie aplikacji LightSwitch](https://msdn.microsoft.com/Library/4818d933-295c-4ecc-9148-7ad9ca28dcdb) |

## <a name="next-steps"></a>Następne kroki

W tym samouczku przyjrzałeś się szybko opcjom wdrażania dla różnych aplikacji.

> [!div class="nextstepaction"]
> [Jakie opcje publikowania są dla mnie odpowiednie?](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me)

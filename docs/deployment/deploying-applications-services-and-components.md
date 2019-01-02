---
title: Przewodnik po funkcjach wdrożenia
description: Poznaj opcje wdrażania aplikacji w programie Visual Studio.
ms.custom: mvc
ms.date: 06/22/2018
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d0db2a9dcd19b2100239a99ec8fc08850432aa80
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53860039"
---
# <a name="quickstart-first-look-at-deployment-in-visual-studio"></a>Szybki start: Pierwsze spojrzenie na wdrażanie w programie Visual Studio

Wdrażanie aplikacji, usług lub składników, rozpowszechnianie ich w celu instalacji na innych komputerach, urządzeniach lub serwerów lub w chmurze. W programie Visual Studio możesz wybrać odpowiednią metodę w zależności od typu wdrożenia, jakiego potrzebujesz. (Wiele typów aplikacji obsługuje inne narzędzia wdrażania takich jak wdrażanie z wiersza polecenia lub NuGet, które nie zostały opisane w tym miejscu).

Zobacz, przewodniki Szybki Start i samouczków, aby uzyskać instrukcje krok po kroku wdrożenia. Aby uzyskać przegląd wszystkich opcji wdrażania, zobacz [jakie opcje publikowania są dla mnie najlepsza?](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me).

## <a name="deploy-to-local-folder"></a>Wdrażanie na folder lokalny

Wdrożenia w lokalnym folderze zazwyczaj służy do testowania lub w celu rozpoczęcia wdrożenia etapowego, w którym inne narzędzie służy do wdrażania końcowego.

- **ASP.NET**, **platformy ASP.NET Core**, **Node.js**, **Python**, i. **.NET Core**: Narzędzie publikowania do wdrożenia w lokalnym folderze. Opcje dostępne są zależne od typu aplikacji. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Publikuj**. (Jeśli zostały wcześniej skonfigurowane wszystkie profile publikowania, musisz kliknąć **Utwórz nowy profil**.) Następnie wybierz pozycję **folderu**. Aby uzyskać więcej informacji, zobacz [wdrażanie w lokalnym folderze](quickstart-deploy-to-local-folder.md).

    ![Wybierz polecenie Publikuj](../deployment/media/quickstart-publish.png)

- **Środowisko uruchomieniowe Visual C++**: Możesz wdrożyć środowisko wykonawcze Visual C++ przy użyciu wdrożenia lokalnego lub łączenia statycznego. Aby uzyskać więcej informacji, zobacz [wdrażanie natywnych aplikacji komputerowych (Visual C++)](/cpp/ide/deploying-native-desktop-applications-visual-cpp).

## <a name="publish-to-azure"></a>Publikowanie na platformie Azure

- **ASP.NET**, **platformy ASP.NET Core**, **Python**, i **Node.js**: Narzędzie publikowania szybko Wdrażaj aplikacje w usłudze Azure App Service lub na maszynie wirtualnej platformy Azure. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Publikuj**. (Jeśli zostały wcześniej skonfigurowane wszystkie profile publikowania, musisz kliknąć **Utwórz nowy profil**.) W oknie dialogowym publikowania wybierz **usługi App Service** lub **maszyn wirtualnych platformy Azure**, a następnie wykonaj kroki konfiguracji.

    ![Usługa Azure App Service wybierz](../deployment/media/quickstart-publish-azure.png "wybierz usługi Azure App Service")

    W programie Visual Studio 2017 wersji 15.7 lub nowszej można wdrażać aplikacje platformy ASP.NET Core **usługi App Service dla systemu Linux**.

    Dla aplikacji w języku Python, zobacz też [językiem Python — publikowanie w usłudze Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json).

    Szybkie wprowadzenie, zobacz [Opublikuj na platformie Azure](quickstart-deploy-to-azure.md) i [publikowania w systemie Linux](quickstart-deploy-to-linux.md). Zobacz też [publikowanie aplikacji platformy ASP.NET Core na platformie Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). Do wdrożenia przy użyciu narzędzia Git, zobacz [ciągłe wdrażanie platformy ASP.NET Core na platformie Azure przy użyciu narzędzia Git](/aspnet/core/publishing/azure-continuous-deployment).

    Aby uzyskać informacje na temat importowania profilu publikowania w usłudze Azure App Service w programie Visual Studio, zobacz [importowanie ustawień publikowania i wdrażanie na platformie Azure](../deployment/tutorial-import-publish-settings-azure.md).

    > [!NOTE]
    > Jeśli nie masz już konto platformy Azure, możesz to zrobić [Zarejestruj się tutaj](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio).

## <a name="publish-to-web-or-deploy-to-network-share"></a>Publikuj w sieci Web lub wdrożyć do udziału sieciowego

- **ASP.NET**, **platformy ASP.NET Core**, **Node.js**, i **Python**: Narzędzie publikowania do wdrożenia w witrynie sieci Web przy użyciu protokołu FTP lub narzędzie Web Deploy. Aby uzyskać więcej informacji, zobacz [Wdrażanie witryny sieci web,](quickstart-deploy-to-a-web-site.md).

    W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Publikuj**. (Jeśli zostały wcześniej skonfigurowane wszystkie profile publikowania, musisz kliknąć **Utwórz nowy profil**.) W narzędziu do publikowania wybierz opcję ma i postępuj zgodnie z instrukcjami konfiguracji.

    ![Choose IIS, FTP, etc.](../deployment/media/quickstart-publish-iis-ftp.png)

    Aby uzyskać informacje na temat importowania profilu publikowania w programie Visual Studio, zobacz [importowanie ustawień publikowania i wdrażanie w usługach IIS](../deployment/tutorial-import-publish-settings-iis.md).

    Można także wdrożyć aplikacji ASP.NET i usług na wiele różnych sposobów. Aby uzyskać więcej informacji, zobacz [usług i aplikacji sieci web ASP.NET wdrażanie](http://www.asp.net/aspnet/overview/deployment).

- **Środowisko uruchomieniowe Visual C++**: Możesz wdrożyć środowisko wykonawcze Visual C++ przy użyciu wdrożenia centralnego. Aby uzyskać więcej informacji, zobacz [wdrażanie natywnych aplikacji komputerowych (Visual C++)](/cpp/ide/deploying-native-desktop-applications-visual-cpp).

- **Windows desktop** możesz opublikować aplikację pulpitu Windows, na serwerze sieci web lub w sieciowym udziale plików za pomocą wdrażania ClickOnce. Użytkownicy mogą następnie zainstalować aplikację za pomocą jednego kliknięcia. Aby uzyskać więcej informacji, zobacz [wdrażanie aplikacji klasycznej przy użyciu aplikacji ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) i [wdrażanie aplikacji natywnej za pomocą technologii ClickOnce](/cpp/ide/clickonce-deployment-for-visual-cpp-applications).

## <a name="publish-to-microsoft-store"></a>Publikowanie Microsoft Store

W programie Visual Studio można utworzyć pakiety aplikacji do wdrożenia w Microsoft Store.

- **PLATFORMY UNIWERSALNEJ SYSTEMU WINDOWS**: Można Tworzenie pakietu dla aplikacji i wdróż je przy użyciu elementów menu. Aby uzyskać więcej informacji, zobacz [pakietu aplikacji platformy uniwersalnej systemu Windows przy użyciu programu Visual Studio](/windows/uwp/packaging/packaging-uwp-apps).

    ![Tworzenie pakietu aplikacji](../deployment/media/feature-tour-create-app-package.jpg)

- **Windows desktop**: Można wdrożyć Microsoft Store przy użyciu Desktop Bridge począwszy od programu Visual Studio 2017 w wersji 15.4. Aby to zrobić, Rozpocznij od utworzenia projekt pakietu aplikacji Windows. Aby uzyskać więcej informacji, zobacz [pakietu aplikacji klasycznej dla Microsoft Store (mostek pulpitu)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net).

    ![Mostek pulpitu](../deployment/media/feature-tour-desktop-bridge.png)

## <a name="deploy-to-a-device-uwp"></a>Wdrażanie na urządzenia z systemem (Windows UWP)

Jeśli wdrażasz aplikacji platformy uniwersalnej systemu Windows na potrzeby testowania na urządzeniu, zobacz [uruchamianie aplikacji platformy UWP na komputerze zdalnym w programie Visual Studio](../debugger/run-windows-store-apps-on-a-remote-machine.md).

## <a name="create-an-installer-package-windows-client"></a>Utwórz pakiet Instalatora (systemu Windows Windows client)

Jeśli potrzebujesz więcej złożonej instalacji aplikacji pulpitu niż [ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) może zapewnić można utworzyć pakiet instalacyjny, projektu Instalatora lub niestandardowego programu inicjującego.

- Instalatora WiX opartym na MSI mogą być tworzone przy użyciu [WiX zestawu narzędzi Visual Studio 2017 Extension](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).

- [InstallShield](https://www.flexerasoftware.com/producer/products/software-installation/installshield-software-installer/tab/requirements) z Flexera oprogramowania może być używany z programu Visual Studio 2017 (Community Edition nie są obsługiwane). Należy pamiętać, że InstallShield Limited Edition nie jest już dołączony do Visual Studio i nie jest obsługiwana w programie Visual Studio 2017; Skontaktuj się z [oprogramowania Flexera](http://learn.flexerasoftware.com/content/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio) o przyszłych dostępności.

- Jeśli chcesz utworzyć projekt Instalatora (vdproj), zainstaluj [rozszerzenia programu Visual Studio 2017 Instalatora projektów](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.MicrosoftVisualStudio2017InstallerProjects#overview).

- Można zainstalować wstępnie wymagane składniki aplikacji komputerowych, konfigurując Instalator ogólny, który jest znany jako program inicjujący. Aby uzyskać więcej informacji, zobacz [wymagania wstępne wdrożenia aplikacji](../deployment/application-deployment-prerequisites.md).

## <a name="deploy-to-test-lab"></a>Wdrażanie laboratorium testowego

Aby umożliwić bardziej wyrafinowane projektowanie i testowanie przez wdrożenie aplikacji w środowiskach wirtualnych. Aby uzyskać więcej informacji, zobacz [testów w środowisku laboratoryjnym](../test/lab-management/using-a-lab-environment-for-your-application-lifecycle.md).

## <a name="devops-deployment"></a>Wdrożenie metodyki DevOps

W środowisku zespołowym potoki Azure służy również do włączyć ciągłe wdrażanie aplikacji. Aby uzyskać więcej informacji, zobacz [potoki Azure](/azure/devops/pipelines/index?view=vsts) i [Wdróż na platformie Azure](/azure/devops/deploy-azure/index?view=vsts).

## <a name="deployment-for-other-app-types"></a>Wdrożenia dla innych typów aplikacji

| Typ aplikacji | Scenariusz wdrażania | Łącze |
| --- | --- | --- |
| **Aplikacja pakietu Office** | Możesz opublikować dodatek dla pakietu Office w programie Visual Studio. | [Wdrażanie i publikowanie dodatku pakietu Office](https://dev.office.com/docs/add-ins/publish/publish) |
| **Usługa WCF lub OData** | Inne aplikacje mogą używać usług WCF RIA, które są wdrażane na serwerze sieci web. | [Tworzenie i wdrażanie usług danych WCF](/dotnet/framework/data/wcf/developing-and-deploying-wcf-data-services) |
| **LightSwitch** | LightSwitch nie jest już obsługiwana w programie Visual Studio 2017, ale nadal można wdrożyć z programu Visual Studio 2015 i starszych wersji. | [Wdrażanie aplikacji LightSwitch](https://msdn.microsoft.com/Library/4818d933-295c-4ecc-9148-7ad9ca28dcdb) |

## <a name="next-steps"></a>Następne kroki

W tym samouczku wykonano krótkie omówienie opcji wdrażania dla różnych aplikacji.

> [!div class="nextstepaction"]
> [Jakie opcje publikowania są dla mnie odpowiednia?](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me)

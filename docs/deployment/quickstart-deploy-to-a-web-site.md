---
title: Publikowanie w witrynie sieci Web
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7ec5ea0b52c5d0708630a30b7d2b80be2275f3a9
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2020
ms.locfileid: "84173701"
---
# <a name="publish-a-web-app-to-a-web-site-using-visual-studio"></a>Publikowanie aplikacji sieci Web w witrynie sieci Web przy użyciu programu Visual Studio

Za pomocą narzędzia do **publikowania** można publikować aplikacje ASP.NET, ASP.NET Core, .NET Core i Python w witrynie sieci Web z poziomu programu Visual Studio. W przypadku środowiska Node. js czynności są obsługiwane, ale interfejs użytkownika jest inny.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

> [!NOTE]
> Jeśli musisz opublikować aplikację klasyczną systemu Windows w sieciowym udziale plików, zobacz [wdrażanie aplikacji klasycznej przy użyciu technologii ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# lub Visual Basic). W przypadku języka C++/CLR zobacz [wdrażanie aplikacji natywnej przy użyciu technologii ClickOnce](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) lub dla języka C/C++, zobacz [wdrażanie aplikacji natywnej przy użyciu projektu instalacji](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="publish-to-a-web-site"></a>Publikowanie w witrynie sieci Web

1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Publikuj** (lub użyj elementu menu **Kompiluj**  >  **publikację** ).

    ![Polecenie Publikuj w menu kontekstowym projektu w Eksplorator rozwiązań](../deployment/media/quickstart-publish.png "Wybierz pozycję Publikuj")

1. Jeśli wszystkie profile publikowania zostały wcześniej skonfigurowane, zostanie wyświetlone okienko **Publikowanie** . Wybierz pozycję **Utwórz nowy profil**.

1. W oknie dialogowym **Publikowanie** wybierz opcję **serwer sieci Web (IIS)**.

    ![Wybieranie elementu docelowego publikowania](../deployment/media/quickstart-publish-iis.png "Wybierz usługi IIS, FTP itp.")

1. Wybierz **Web Deploy** jako metodę wdrażania. Web Deploy upraszcza wdrażanie aplikacji sieci Web i witryn sieci Web na serwerach usług IIS i musi być zainstalowany jako aplikacja na serwerze. Zainstaluj go za pomocą [Instalatora platformy sieci Web](https://www.microsoft.com/web/downloads/platform.aspx) .

    ![Wybierz metodę wdrażania](../deployment/media/quickstart-publish-iis-web-deploy.png "Wybierz usługi IIS, FTP itp.")

1. Skonfiguruj wymagane ustawienia metody Publish i wybierz pozycję **Zakończ**. 

    ![Szczegóły połączenia Web Deploy](../deployment/media/quickstart-publish-iis-web-deploy-connection-details.png)

1. Aby przeprowadzić publikowanie, wybierz pozycję **Publikuj** na stronie Podsumowanie. Okno dane wyjściowe pokazuje postęp wdrażania i wyniki.

## <a name="next-steps"></a>Następne kroki

W tym przewodniku szybki start przedstawiono sposób tworzenia profilu publikowania przy użyciu programu Visual Studio. Możesz również skonfigurować profil publikowania przez zaimportowanie ustawień publikowania.

> [!div class="nextstepaction"]
> [Importowanie ustawień publikowania i wdrażanie w usługach IIS](tutorial-import-publish-settings-iis.md)

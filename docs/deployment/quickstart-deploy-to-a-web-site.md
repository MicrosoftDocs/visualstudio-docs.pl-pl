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
ms.openlocfilehash: 1236c3057cd209bd5c7c81304a2168704927c506
ms.sourcegitcommit: 53bc4c11b82882ab658e34c65ae374060f823531
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71127936"
---
# <a name="publish-a-web-app-to-a-web-site-using-visual-studio"></a>Publikowanie aplikacji sieci Web w witrynie sieci Web przy użyciu programu Visual Studio

Za pomocą narzędzia do **publikowania** można publikować aplikacje ASP.NET, ASP.NET Core, .NET Core i Python w witrynie sieci Web z poziomu programu Visual Studio. W przypadku środowiska Node. js czynności są obsługiwane, ale interfejs użytkownika jest inny.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

> [!NOTE]
> Jeśli musisz opublikować aplikację klasyczną systemu Windows w sieciowym udziale plików, zobacz [wdrażanie aplikacji klasycznej przy użyciu technologii ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# lub Visual Basic). Aby C++uzyskać/CLI, zobacz [wdrażanie aplikacji natywnej przy użyciu technologii ClickOnce](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) lub dlaC++języka C/, zobacz [wdrażanie aplikacji natywnej przy użyciu projektu Instalatora](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="publish-to-a-web-site"></a>Publikowanie w witrynie sieci Web

1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Publikuj** (lub użyj elementu menu **Kompiluj** > **publikację** ).

    ![Polecenie Publikuj w menu kontekstowym projektu w Eksplorator rozwiązań](../deployment/media/quickstart-publish.png "Wybierz pozycję Publikuj")

1. Jeśli wszystkie profile publikowania zostały wcześniej skonfigurowane, zostanie wyświetlone okienko **Publikowanie** . Wybierz pozycję **Utwórz nowy profil**.

1. W oknie dialogowym **Wybieranie elementu docelowego publikowania** wybierz opcję **IIS, FTP itp**.

    ![Wybierz usługi IIS, FTP itp.](../deployment/media/quickstart-publish-iis-ftp.png "Wybierz usługi IIS, FTP itp.")

1. Wybierz **publikowania**. Zostanie otwarte okno dialogowe Ustawienia publikowania profilu.

    ![Wybierz folder](../deployment/media/quickstart-publish-settings-web.png "Wybierz folder")

1. W polu **Publikuj metodę** wybierz metodę, taką jak **Web Deploy** lub **FTP**. Ustawienia, które zobaczysz dalej, odpowiadają za metodę publikacji. Web Deploy upraszcza wdrażanie aplikacji sieci Web i witryn sieci Web na serwerach usług IIS i musi być zainstalowany jako aplikacja na serwerze. Zainstaluj go za pomocą [Instalatora platformy sieci Web](https://www.microsoft.com/web/downloads/platform.aspx) .

1. Skonfiguruj wymagane ustawienia metody Publish i wybierz pozycję **Weryfikuj połączenie**. Jeśli serwer lub cel są dostępne, a ustawienia są poprawne, zostanie wyświetlony komunikat informujący o tym, że połączenie zostało zweryfikowane i wszystko jest gotowe do opublikowania.

    ![Weryfikowanie połączenia](../deployment/media/quickstart-publish-web-deploy.png "Weryfikowanie połączenia")

1. Wybierz pozycję **Ustawienia** , aby skonfigurować inne ustawienia wdrożenia, na przykład czy wdrożyć konfigurację debugowania czy wydania, a następnie wybierz pozycję **Zapisz**. Jeśli debugujesz zdalnie, wymagana jest Konfiguracja debugowania.

1. Aby opublikować, wybierz pozycję **Publikuj**. Okno dane wyjściowe pokazuje postęp wdrażania i wyniki.

## <a name="next-steps"></a>Następne kroki

W tym przewodniku szybki start przedstawiono sposób tworzenia profilu publikowania przy użyciu programu Visual Studio. Możesz również skonfigurować profil publikowania przez zaimportowanie ustawień publikowania.

> [!div class="nextstepaction"]
> [Importowanie ustawień publikowania i wdrażanie w usługach IIS](tutorial-import-publish-settings-iis.md)

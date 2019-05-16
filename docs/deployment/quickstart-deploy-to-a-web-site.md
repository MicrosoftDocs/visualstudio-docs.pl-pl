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
ms.openlocfilehash: ffa1adbecc4114d53f2cdaa9e03296ed7f6144b6
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65679177"
---
# <a name="publish-a-web-app-to-a-web-site-using-visual-studio"></a>Publikowanie aplikacji sieci Web do witryny sieci web przy użyciu programu Visual Studio

Możesz użyć **Publikuj** narzędzie do publikowania aplikacji platformy ASP.NET, ASP.NET Core, .NET Core i języka Python w witrynie sieci Web w programie Visual Studio. Dla środowiska Node.js czynności są obsługiwane, ale interfejs użytkownika jest inny.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

> [!NOTE]
> Jeśli potrzebujesz opublikować aplikację pulpitu Windows sieciowy udział plików, zobacz [wdrażanie aplikacji klasycznej przy użyciu aplikacji ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# lub Visual Basic). Dla C++/CLR, zobacz [wdrażanie aplikacji natywnej za pomocą technologii ClickOnce](/cpp/ide/clickonce-deployment-for-visual-cpp-applications) lub dla języka C /C++, zobacz [wdrażanie aplikacji natywnych przy użyciu projektu instalacji](/cpp/ide/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="publish-to-a-web-site"></a>Publikowanie w witrynie sieci Web

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Publikuj** (lub użyj **kompilacji** > **Publikuj** element menu).

    ![Polecenia Opublikuj w menu kontekstowym projektu w Eksploratorze rozwiązań](../deployment/media/quickstart-publish.png "wybierz polecenie Publikuj")

1. Jeśli wcześniej skonfigurowano żadnych profilów publikowania **Publikuj** zostanie wyświetlone okienko. Wybierz **Utwórz nowy profil**.

1. W **wybierz lokalizację docelową publikowania** okna dialogowego wybierz **usług IIS, FTP, etc**.

    ![Wybierz pozycję IIS, FTP itp.](../deployment/media/quickstart-publish-iis-ftp.png "wybierz usług IIS, FTP itp.")

1. Wybierz **publikowania**. Profil publikowania ustawień, które zostanie otwarte okno dialogowe.

    ![Wybierz Folder](../deployment/media/quickstart-publish-settings-web.png "wybierz Folder")

1. W **metody publikowania** pola, takie jak wybrać metodę **narzędzia Web Deploy** lub **FTP**. Ustawienia, które są wyświetlane obok odnoszą się do metody publikowania. Narzędzie Web Deploy upraszcza wdrażanie aplikacji sieci Web i witryn sieci Web na serwerach usług IIS, a musi być zainstalowany jako aplikację na serwerze. Użyj [Instalatora platformy sieci Web](https://www.microsoft.com/web/downloads/platform.aspx) go zainstalować.

1. Skonfiguruj ustawienia wymagane dla metody publikowania i wybierz **Waliduj połączenie**. Jeśli serwer lub docelowy jest dostępny i ustawienia są prawidłowe, komunikat informujący, połączenie jest weryfikowana, a wszystko jest gotowe do opublikowania.

    ![Weryfikacja połączenia z](../deployment/media/quickstart-publish-web-deploy.png "sprawdzanie poprawności połączenia")

1. Wybierz **ustawienia** skonfigurować inne ustawienia wdrożenia, takie jak czy wdrażanie konfiguracji Debug i Release, a następnie wybierz pozycję **Zapisz**. Jeśli debugujesz zdalnie, konfiguracja debugowania jest wymagana.

1. Aby opublikować, zaznacz **Publikuj**. W oknie danych wyjściowych Pokazuje postęp wdrażania i wyniki.

## <a name="next-steps"></a>Następne kroki

W tym przewodniku Szybki Start przedstawiono sposób tworzenia profilu publikowania przy użyciu programu Visual Studio. Można również skonfigurować publikowanie profilu przez importowanie ustawień publikowania.

> [!div class="nextstepaction"]
> [Importowanie ustawień publikowania i wdrażanie w usługach IIS](tutorial-import-publish-settings-iis.md)

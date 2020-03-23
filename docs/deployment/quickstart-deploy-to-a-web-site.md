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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "71127936"
---
# <a name="publish-a-web-app-to-a-web-site-using-visual-studio"></a>Publikowanie aplikacji sieci Web w witrynie sieci Web przy użyciu programu Visual Studio

Za pomocą narzędzia **Publikowania** można publikować aplikacje ASP.NET, ASP.NET Core, .NET Core i Python w witrynie sieci Web z programu Visual Studio. W przypadku pliku Node.js kroki są obsługiwane, ale interfejs użytkownika jest inny.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

> [!NOTE]
> Jeśli chcesz opublikować aplikację klasyczną systemu Windows w sieciowym udziale plików, zobacz [Wdrażanie aplikacji klasycznej przy użyciu funkcji ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# lub Visual Basic). W przypadku języka C++/CLI zobacz [Wdrażanie aplikacji natywnej przy użyciu funkcji ClickOnce](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) lub w przypadku języka C/C++, zobacz [Wdrażanie aplikacji natywnej przy użyciu projektu instalatora](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="publish-to-a-web-site"></a>Publikowanie w witrynie sieci Web

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Publikuj** (lub użyj elementu menu **Buduj** > **publikowanie).**

    ![Polecenie Publikuj w menu kontekstowym projektu w Eksploratorze rozwiązań](../deployment/media/quickstart-publish.png "Wybierz pozycję Publikuj")

1. Jeśli wcześniej skonfigurowano profile publikowania, zostanie wyświetlone okienko **Publikowania.** Wybierz **pozycję Utwórz nowy profil**.

1. W oknie **dialogowym Wybieranie celu publikowania** wybierz pozycję **IIS, FTP itp.**

    ![Wybierz iIS, FTP itp.](../deployment/media/quickstart-publish-iis-ftp.png "Wybierz iIS, FTP itp.")

1. Wybierz pozycję **Publikuj**. Zostanie otwarte okno dialogowe Ustawienia publikowania profilu.

    ![Wybierz folder](../deployment/media/quickstart-publish-settings-web.png "Wybierz folder")

1. W polu **Metoda publikowania** wybierz metodę, taką jak **Wdrażanie w sieci Web** lub **FTP**. Ustawienia, które widzisz obok odpowiadają metody publikowania. Wdrażanie w sieci Web upraszcza wdrażanie aplikacji sieci Web i witryn sieci Web na serwerach usług IIS i musi być zainstalowane jako aplikacja na serwerze. Użyj [instalatora platformy sieci Web,](https://www.microsoft.com/web/downloads/platform.aspx) aby go zainstalować.

1. Skonfiguruj wymagane ustawienia dla metody publikowania i wybierz **pozycję Sprawdź poprawność połączenia**. Jeśli serwer lub obiekt docelowy jest dostępny, a ustawienia są poprawne, komunikat informujący o weryfikacji połączenia i można go opublikować.

    ![Sprawdzanie poprawności połączenia](../deployment/media/quickstart-publish-web-deploy.png "Sprawdzanie poprawności połączenia")

1. Wybierz **pozycję Ustawienia,** aby skonfigurować inne ustawienia wdrażania, takie jak wdrażanie konfiguracji debugowania lub wydania, a następnie wybierz pozycję **Zapisz**. Jeśli debugowanie jest debugowanie zdalnie, wymagana jest konfiguracja debugowania.

1. Aby opublikować, wybierz pozycję **Publikuj**. Okno Dane wyjściowe zawiera postęp wdrożenia i wyniki.

## <a name="next-steps"></a>Następne kroki

W tym przewodniku Szybki start dowiesz się, jak utworzyć profil publikowania za pomocą programu Visual Studio. Profil publikowania można również skonfigurować, importując ustawienia publikowania.

> [!div class="nextstepaction"]
> [Importowanie ustawień publikowania i wdrażanie w usługach IIS](tutorial-import-publish-settings-iis.md)

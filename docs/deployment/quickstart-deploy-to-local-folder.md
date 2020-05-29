---
title: Wdrażanie w folderze lokalnym
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, local folder
ms.assetid: adb461c4-812a-4b8c-b2ab-96002379f6a9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3355636eba7556a472d8ce272437fb07c30714be
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2020
ms.locfileid: "84184179"
---
# <a name="deploy-an-app-to-a-local-folder-using-visual-studio"></a>Wdrażanie aplikacji w folderze lokalnym przy użyciu programu Visual Studio

Za pomocą narzędzia do **publikowania** można publikować aplikacje ASP.NET, ASP.NET Core, .NET Core i Python do folderu lokalnego z programu Visual Studio. W przypadku środowiska Node. js czynności są obsługiwane, ale interfejs użytkownika jest inny.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

> [!NOTE]
> Jeśli musisz opublikować aplikację klasyczną systemu Windows w folderze lokalnym, zobacz [wdrażanie aplikacji klasycznej przy użyciu technologii ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# lub Visual Basic). W przypadku języka C++/CLR zobacz [wdrażanie aplikacji natywnej przy użyciu technologii ClickOnce](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) lub dla języka C/C++, zobacz [wdrażanie aplikacji natywnej przy użyciu projektu instalacji](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="deploy-to-a-local-folder"></a>Wdrażanie w folderze lokalnym

1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Publikuj** (lub użyj elementu menu **Kompiluj**  >  **publikację** ).

    ![Polecenie Publikuj w menu kontekstowym projektu w Eksplorator rozwiązań](../deployment/media/quickstart-publish.png "Wybierz pozycję Publikuj")

1. W oknie dialogowym **Publikowanie** wybierz pozycję **folder**.

    ![Wybierz folder jako element docelowy publikowania](../deployment/media/quickstart-publish-folder.png "Wybierz folder")

1. Wprowadź ścieżkę lub wybierz pozycję **Przeglądaj** , aby określić folder.

    ![Określ ścieżkę do folderu](../deployment/media/quickstart-publish-folder-path.png "Wybierz folder")

1. Wybierz pozycję **Publikuj**. Program Visual Studio kompiluje projekt i publikuje go w określonym folderze. Zostanie wyświetlone okienko **Publikowanie** właściwości projektu przedstawiające Podsumowanie profilu.

    ![Okienko właściwości publikowania przedstawiające Podsumowanie profilu](../deployment/media/quickstart-publish-folder-summary.png)

1. Aby skonfigurować ustawienia wdrożenia, wybierz opcję **Edytuj** w podsumowaniu profilu publikowania i wybierz kartę **Ustawienia** .

    ![Ustawienia profilu](../deployment/media/quickstart-profile-settings.png "Ustawienia profilu")

1. Skonfiguruj opcje, takie jak czy wdrożyć konfigurację debugowania czy wydania, a następnie wybierz pozycję **Zapisz**.

1. Aby ponownie opublikować, wybierz pozycję **Publikuj**.

Wdróż opublikowane pliki w dowolny sposób. Można na przykład spakować je w pliku *zip* , użyć prostego polecenia copy lub wdrożyć je przy użyciu dowolnego wybranego pakietu instalacyjnego.

## <a name="next-steps"></a>Następne kroki

- [Wdrażanie aplikacji .NET Core za pomocą narzędzia do publikowania](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Tworzenie pakietu aplikacji klasycznej dla sklepu Microsoft Store (mostek dla aplikacji klasycznych)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- Architektury [Wdrażanie .NET Framework i aplikacji](/dotnet/framework/deployment/)

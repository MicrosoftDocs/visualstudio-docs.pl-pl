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
ms.openlocfilehash: 862310c8c763ce366798bfacd4f4759d606bb33c
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "71128212"
---
# <a name="deploy-an-app-to-a-local-folder-using-visual-studio"></a>Wdrażanie aplikacji w folderze lokalnym przy użyciu programu Visual Studio

Za pomocą narzędzia **Publikowania** można publikować aplikacje ASP.NET, ASP.NET Core, .NET Core i Python w folderze lokalnym z programu Visual Studio. W przypadku pliku Node.js kroki są obsługiwane, ale interfejs użytkownika jest inny.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

> [!NOTE]
> Jeśli chcesz opublikować aplikację klasyczną systemu Windows w folderze lokalnym, zobacz [Wdrażanie aplikacji klasycznej przy użyciu funkcji ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# lub Visual Basic). W przypadku języka C++/CLI zobacz [Wdrażanie aplikacji natywnej przy użyciu funkcji ClickOnce](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) lub w przypadku języka C/C++, zobacz [Wdrażanie aplikacji natywnej przy użyciu projektu instalatora](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="deploy-to-a-local-folder"></a>Wdrażanie w folderze lokalnym

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Publikuj** (lub użyj elementu menu **Buduj** > **publikowanie).**

    ![Polecenie Publikuj w menu kontekstowym projektu w Eksploratorze rozwiązań](../deployment/media/quickstart-publish.png "Wybierz pozycję Publikuj")

1. Jeśli wcześniej skonfigurowano profile publikowania, zostanie wyświetlone okienko **Publikowania.** Wybierz **pozycję Utwórz nowy profil**.

1. W oknie **dialogowym Wybieranie celu publikowania** wybierz pozycję **Folder**.

    ![Wybieranie folderu lokalnego jako obiektu docelowego publikowania](../deployment/media/quickstart-publish-folder.png "Wybierz folder")

1. Wprowadź ścieżkę lub wybierz **pozycję Przeglądaj,** aby określić folder lokalny.

1. Wybierz pozycję **Publikuj**. Visual Studio tworzy projekt i publikuje go do określonego folderu. Zostanie wyświetlone okienko **Publikowania** właściwości projektu z podsumowaniem profilu.

    ![Publikowanie okienka właściwości z podsumowaniem profilu](../deployment/media/quickstart-publish-folder-summary.png)

1. Aby skonfigurować ustawienia wdrażania, wybierz pozycję **Konfiguruj** w podsumowaniu profilu i wybierz kartę **Ustawienia.**

    ![Ustawienia profilu](../deployment/media/quickstart-profile-settings.png "Ustawienia profilu")

1. Skonfiguruj opcje, takie jak czy wdrożyć konfigurację debugowania lub wersji, a następnie wybierz pozycję **Zapisz**.

1. Aby ponownie opublikować, wybierz pozycję **Publikuj**.

Wdrażanie opublikowanych plików w dowolny sposób. Na przykład można spakować je w pliku *zip,* użyć polecenia prostego kopiowania lub wdrożyć je z dowolnym pakietem instalacyjnym do wyboru.

## <a name="next-steps"></a>Następne kroki

- [Wdrażanie aplikacji .NET Core za pomocą narzędzia publikowania](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Tworzenie pakietu aplikacji klasycznej dla sklepu Microsoft Store (mostek dla aplikacji klasycznych)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- (.NET) [Wdrażanie programu .NET Framework i aplikacji](/dotnet/framework/deployment/)

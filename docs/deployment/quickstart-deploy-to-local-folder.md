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
ms.openlocfilehash: 5627cd0f5ad37a7f92408e887b87d5eda14706eb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62927655"
---
# <a name="deploy-an-app-to-a-local-folder-using-visual-studio"></a>Wdrażanie aplikacji w lokalnym folderze przy użyciu programu Visual Studio

Możesz użyć **Publikuj** narzędzie do publikowania aplikacji platformy ASP.NET, ASP.NET Core, .NET Core i języka Python do folderu lokalnego z programu Visual Studio. Dla środowiska Node.js czynności są obsługiwane, ale interfejs użytkownika jest inny.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

> [!NOTE]
> Jeśli potrzebujesz opublikować aplikację pulpitu Windows do folderu lokalnego, zobacz [wdrażanie aplikacji klasycznej przy użyciu aplikacji ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# lub Visual Basic). Dla C++/CLR, zobacz [wdrażanie aplikacji natywnej za pomocą technologii ClickOnce](/cpp/ide/clickonce-deployment-for-visual-cpp-applications) lub dla języka C /C++, zobacz [wdrażanie aplikacji natywnych przy użyciu projektu instalacji](/cpp/ide/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="deploy-to-a-local-folder"></a>Wdrażanie w folderze lokalnym

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Publikuj** (lub użyj **kompilacji** > **Publikuj** element menu).

    ![Polecenia Opublikuj w menu kontekstowym projektu w Eksploratorze rozwiązań](../deployment/media/quickstart-publish.png "wybierz polecenie Publikuj")

1. Jeśli wcześniej skonfigurowano żadnych profilów publikowania **Publikuj** zostanie wyświetlone okienko. Wybierz **Utwórz nowy profil**.

1. W **wybierz lokalizację docelową publikowania** okna dialogowego wybierz **folderu**.

    ![Wybierz folder lokalny, jako lokalizację docelową publikowania](../deployment/media/quickstart-publish-folder.png "wybierz Folder")

1. Wprowadź ścieżkę lub wybierz **Przeglądaj** do określenia folderu lokalnego.

1. Wybierz **publikowania**. Visual Studio tworzy projekt i publikuje go do określonego folderu. Właściwości projektu **Publikuj** profil zostanie wyświetlone okienko wyświetlanie podsumowania.

    ![Okienko właściwości wyświetlanie podsumowania profil publikowania](../deployment/media/quickstart-publish-folder-summary.png)

1. Aby skonfigurować ustawienia wdrożenia, wybierz **Konfiguruj** w profilu, summary i wybierz pozycję **ustawienia** kartę.

    ![Ustawienia profili](../deployment/media/quickstart-profile-settings.png "ustawienia profilu")

1. Skonfiguruj opcje, takie jak czy wdrażanie konfiguracji Debug i Release, a następnie wybierz pozycję **Zapisz**.

1. Aby ponownie opublikować, wybierz **Publikuj**.

Wdrażanie plików publikowanych w jakikolwiek sposób, który chcesz. Na przykład, można umieścić je w *zip* pliku, użyj polecenia prostą kopię albo wdrażać je przy użyciu dowolnego pakietu instalacyjnego wybranych przez użytkownika.

## <a name="next-steps"></a>Następne kroki

- [Wdrażanie aplikacji .NET Core za pomocą narzędzia publikowania](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Tworzenie pakietu aplikacji klasycznej dla sklepu Microsoft Store (mostek dla aplikacji klasycznych)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- (.NET) [Wdrażania .NET Framework i aplikacji](/dotnet/framework/deployment/)

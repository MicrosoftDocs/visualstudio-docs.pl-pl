---
title: Wdrażanie w folderze lokalnym
description: Dowiedz się, jak publikować aplikacje ASP.NET, ASP.NET Core, .NET Core i Python w folderze z programu Visual Studio za pomocą narzędzia do publikowania.
ms.custom: SEO-VS-2020
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, local folder
ms.assetid: adb461c4-812a-4b8c-b2ab-96002379f6a9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 23ef2036af7b93ee6eeaaa14cb8733a4e0ced638
ms.sourcegitcommit: 79a6be815244f1cfc7b4123afff29983fce0555c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2021
ms.locfileid: "102249502"
---
# <a name="deploy-an-app-to-a-folder-using-visual-studio"></a>Wdrażanie aplikacji w folderze przy użyciu programu Visual Studio

Za pomocą narzędzia do **publikowania** można publikować aplikacje ASP.NET, ASP.NET Core, .NET Core i Python do folderu z programu Visual Studio. W przypadku Node.js kroki są obsługiwane, ale interfejs użytkownika jest inny.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]
::: moniker range=">=vs-2017"
> [!NOTE]
> Jeśli musisz opublikować aplikację klasyczną systemu Windows w folderze, zobacz [wdrażanie aplikacji klasycznej przy użyciu technologii ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# lub Visual Basic). W przypadku języka C++/CLR zobacz [wdrażanie aplikacji natywnej przy użyciu technologii ClickOnce](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) lub dla języka C/C++, zobacz [wdrażanie aplikacji natywnej przy użyciu projektu instalacji](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

::: moniker-end

::: moniker range=">=vs-2019"
> [!NOTE]
> Jeśli musisz opublikować platformę .NET Core 3,1 lub nowszą, aplikację klasyczną systemu Windows do folderu, zobacz [wdrażanie aplikacji .NET dla systemu Windows przy użyciu technologii ClickOnce](quickstart-deploy-using-clickonce-folder.md).

::: moniker-end

## <a name="deploy-to-a-local-folder"></a>Wdrażanie w folderze lokalnym

1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Publikuj** (lub użyj elementu menu **Kompiluj**  >  **publikację** ).

    ![Polecenie Publikuj w menu kontekstowym projektu w Eksplorator rozwiązań](../deployment/media/quickstart-publish.png "Wybierz pozycję Publikuj")

1. Jeśli wszystkie profile publikowania zostały wcześniej skonfigurowane, zostanie wyświetlone okno **Publikowanie** . Wybierz pozycję **Nowy**.

1. W oknie **Publikowanie** wybierz pozycję **folder**.

   ![Wybierz folder jako element docelowy publikowania](../deployment/media/quickstart-publish-folder-new.png "Wybierz folder")

   ::: moniker range=">=vs-2019"

   Jeśli wdrażasz platformę .NET Core 3,1 lub nowszą, aplikacja systemu Windows może wymagać wybrania **folderu** w oknie **określonego celu** .

   ![Wybierz folder jako określony element docelowy](../deployment/media/quickstart-publish-folder-targets.png "Wybierz konkretny element docelowy")

   Jeśli chcesz opublikować platformę .NET Core 3,1 lub nowszą, aplikację systemu Windows z funkcją ClickOnce, zobacz [wdrażanie aplikacji .NET systemu Windows przy użyciu technologii ClickOnce](quickstart-deploy-using-clickonce-folder.md).
   ::: moniker-end

1. Wprowadź ścieżkę lub wybierz pozycję **Przeglądaj** , aby określić folder.

   ![Określ ścieżkę do folderu](../deployment/media/quickstart-publish-folder-path.png "Wybierz folder")

   ::: moniker range=">=vs-2019"
   Kliknij przycisk **Zakończ** , aby zapisać profil.

   ![Okienko właściwości publikowania przedstawiające Podsumowanie profilu](../deployment/media/quickstart-publish-folder-summary.png)
   ::: moniker-end

1. Kliknij pozycję **Opublikuj**. Program Visual Studio kompiluje projekt i publikuje go w określonym folderze.

   ::: moniker range="vs-2017"
   Zostanie wyświetlone okienko **Publikowanie** właściwości projektu przedstawiające Podsumowanie profilu.

   ![Okienko właściwości publikowania przedstawiające Podsumowanie profilu](../deployment/media/quickstart-publish-folder-summary.png)
   ::: moniker-end

1. Aby skonfigurować ustawienia wdrożenia, wybierz opcję **Edytuj** w podsumowaniu profilu publikowania i wybierz kartę **Ustawienia** .

   Ustawienia, które widzisz, są zależne od typu aplikacji. Na poniższej ilustracji przedstawiono przykładowe ustawienia aplikacji ASP.NET Core.

    ![Ustawienia profilu](../deployment/media/quickstart-profile-settings.png "Ustawienia profilu")

    Aby uzyskać dodatkową pomoc dotyczącą wybierania ustawień w programie .NET, zobacz następujące tematy:

    - [Wdrażanie zależne od platformy a wdrożenie samodzielne](/dotnet/core/deploying/)
    - [Docelowe identyfikatory środowiska uruchomieniowego (Portable RID, et al)](/dotnet/core/rid-catalog)
    - [Konfiguracje debugowania i wydania](../ide/understanding-build-configurations.md)

1. Skonfiguruj opcje, takie jak czy wdrożyć konfigurację debugowania czy wydania, a następnie wybierz pozycję **Zapisz**.

1. Aby ponownie opublikować, wybierz pozycję **Publikuj**.

Wdróż opublikowane pliki w dowolny sposób. Można na przykład spakować je w pliku *zip* , użyć prostego polecenia copy lub wdrożyć je przy użyciu dowolnego wybranego pakietu instalacyjnego.

## <a name="next-steps"></a>Następne kroki

W przypadku aplikacji .NET:

- [Wdrażanie aplikacji .NET Core za pomocą narzędzia do publikowania](/dotnet/core/deploying/deploy-with-vs)
- [Publikowanie aplikacji platformy .NET Core (wdrożenia zależne od platformy a samodzielne)](/dotnet/core/deploying/)
- [Wdrażanie .NET Framework i aplikacji](/dotnet/framework/deployment/)
::: moniker range=">=vs-2019"
- [Wdróż aplikację platformy .NET dla systemu Windows przy użyciu technologii ClickOnce](quickstart-deploy-using-clickonce-folder.md).
 ::: moniker-end

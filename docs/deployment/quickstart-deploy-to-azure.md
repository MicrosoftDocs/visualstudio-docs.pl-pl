---
title: Publikowanie w usłudze Azure App Service
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- azure
ms.openlocfilehash: 5881e1dfb1842e2a6d85efe73534f8db2e2f734e
ms.sourcegitcommit: c31815e140f2ec79e00a9a9a19900778ec11e860
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2020
ms.locfileid: "91830746"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio"></a>Publish a Web app to Azure App Service using Visual Studio (Publikowanie aplikacji internetowej w usłudze Azure App Service przy użyciu programu Visual Studio)

W przypadku aplikacji ASP.NET, ASP.NET Core, Node.js i .NET Core można publikować w Azure App Service lub Azure App Service Linux (przy użyciu kontenerów) przy użyciu jednej z poniższych metod.

* Aby ciągłe (lub zautomatyzowane) wdrażanie aplikacji, użyj platformy Azure DevOps z [Azure Pipelines](/azure/devops/pipelines/get-started-yaml?view=azdevops&preserve-view=true).

* W przypadku wdrożenia aplikacji jednorazowego (lub ręcznego) Użyj narzędzia do **publikowania** w programie Visual Studio, aby wdrożyć aplikacje ASP.NET, ASP.NET Core, Node.js i .NET Core do Azure App Service lub [App Service dla systemu Linux](../deployment/quickstart-deploy-to-linux.md) (przy użyciu kontenerów). W przypadku aplikacji języka Python postępuj zgodnie z instrukcjami w sekcji [Python-Publish, aby Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md).

W tym artykule opisano sposób korzystania z narzędzia do **publikowania** na potrzeby wdrożenia jednorazowego.

[!INCLUDE [quickstart-prereqs-azure](includes/quickstart-prereqs-azure.md)]

## <a name="publish-to-azure-app-service-on-windows"></a>Publikowanie w usłudze Azure App Service w systemie Windows

1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Publikuj** (lub Użyj **Build**  >  elementu menu Kompiluj**publikację** ).

    ![Polecenie Publikuj w menu kontekstowym projektu w Eksplorator rozwiązań](../deployment/media/quickstart-publish.png "Wybierz pozycję Publikuj")

1. Jeśli wszystkie profile publikowania zostały wcześniej skonfigurowane, zostanie wyświetlone okno **Publikowanie** . Wybierz pozycję **Nowy**.

1. W oknie **Publikowanie** wybierz pozycję **Azure**.

    ![Wybieranie elementu docelowego publikowania](../deployment/media/quickstart-publish-azure-new.png)

1. Wybierz **Azure App Service (Windows)** i **dalej**.

    ![Wybierz Azure App Service w systemie Linux](../deployment/media/quickstart-publish-windows-select-azure-service.png)

1. Jeśli to konieczne, zaloguj się przy użyciu konta platformy Azure. Wybierz pozycję **Utwórz nowy Azure App Service...**

    ![Link do tworzenia nowego wystąpienia Azure App Service](../deployment/media/quickstart-publish-windows-create-new-link.png)

1. W oknie dialogowym **tworzenie Azure App Service (Windows)** , **Nazwa aplikacji**, **Grupa zasobów**i pola wprowadzania **planu App Service** są wypełniane. Te nazwy można zachować lub zmienić. Gdy wszystko będzie gotowe, wybierz pozycję **Utwórz**.

    ![Wybierz Azure App Service](../deployment/media/quickstart-publish-windows-create-new-dialog.png)

1. W oknie dialogowym **Publikowanie** nowo utworzone wystąpienie zostało automatycznie zaznaczone. Gdy wszystko będzie gotowe, wybierz pozycję **Zakończ**.

    ![Wybierz Azure App Service](../deployment/media/quickstart-publish-windows-select-instance.png)

1. Kliknij pozycję **Opublikuj**. Program Visual Studio wdraża aplikację w Azure App Service, a aplikacja sieci Web ładuje się w przeglądarce. W okienku **Publikowanie** właściwości projektu wyświetlany jest adres URL witryny i inne szczegóły.

    ![Okienko właściwości publikowania przedstawiające Podsumowanie profilu](../deployment/media/quickstart-publish-windows-summary-page.png)

## <a name="clean-up-resources"></a>Czyszczenie zasobów

W poprzednich krokach utworzono zasoby platformy Azure w grupie zasobów. Jeśli nie będziesz już potrzebować tych zasobów w przyszłości, możesz je usunąć przez usunięcie grupy zasobów.
W menu znajdującym się po lewej stronie w witrynie Azure Portal wybierz pozycję **Grupy zasobów**, a następnie wybierz pozycję **myResourceGroup**.
Na stronie grupy zasobów upewnij się, że zasoby na liście są tymi, które chcesz usunąć.
Wybierz pozycję **Usuń**, wpisz ciąg **myResourceGroup** w polu tekstowym, a następnie wybierz opcję **Usuń**.

## <a name="next-steps"></a>Następne kroki

W tym przewodniku szybki start przedstawiono sposób użycia programu Visual Studio do utworzenia profilu publikowania na potrzeby wdrożenia na platformie Azure. Możesz również skonfigurować profil publikowania, importując ustawienia publikowania z Azure App Service.

> [!div class="nextstepaction"]
> [Importowanie ustawień publikowania i wdrażanie na platformie Azure](tutorial-import-publish-settings-azure.md)

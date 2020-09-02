---
title: Publikowanie w usłudze App Service w systemie Linux
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- azure
ms.openlocfilehash: 5b0b45d586fb6eb89eb458329f611d980d9415e0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85285479"
---
# <a name="publish-an-aspnet-core-app-to-app-service-on-linux-using-visual-studio"></a>Publikowanie aplikacji ASP.NET Core App Service w systemie Linux przy użyciu programu Visual Studio

Począwszy od programu Visual Studio 2017 w wersji 15,7, można publikować ASP.NET Core aplikacje do Azure App Service Linux (przy użyciu kontenerów) przy użyciu jednej z poniższych metod.

* Aby ciągłe (lub zautomatyzowane) wdrażanie aplikacji, użyj platformy Azure DevOps z [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/get-started-yaml?view=azdevops).

* W przypadku wdrożenia aplikacji jednorazowego (lub ręcznego) Użyj narzędzia do **publikowania** w programie Visual Studio, aby opublikować ASP.NET Core aplikacje do App Service dla systemu Linux (przy użyciu kontenerów).

W tym artykule opisano sposób korzystania z narzędzia do **publikowania** na potrzeby wdrożenia jednorazowego.

[!INCLUDE [quickstart-prereqs-azure-linux](includes/quickstart-prereqs-azure-linux.md)]

## <a name="publish-to-azure-app-service-on-linux"></a>Publikowanie w usłudze Azure App Service w systemie Linux

1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Publikuj** (lub użyj elementu menu **Kompiluj**  >  **publikację** ).

    ![Polecenie Publikuj w menu kontekstowym projektu w Eksplorator rozwiązań](../deployment/media/quickstart-publish.png "Wybierz pozycję Publikuj")

1. W oknie dialogowym **Publikowanie** wybierz pozycję **Azure**.

    ![Wybieranie elementu docelowego publikowania](../deployment/media/quickstart-publish-azure-new.png)

1. Wybierz pozycję **Azure App Service (Linux)** i **dalej**.

    ![Wybierz Azure App Service w systemie Linux](../deployment/media/quickstart-publish-linux-select-azure-service.png)

1. Jeśli to konieczne, zaloguj się przy użyciu konta platformy Azure. Wybierz pozycję **Utwórz nowy Azure App Service...**

    ![Link do tworzenia nowego wystąpienia Azure App Service](../deployment/media/quickstart-publish-linux-create-new-link.png)

1. W oknie dialogowym **tworzenie Azure App Service (Linux)** pola **Nazwa aplikacji**, **grupa zasobów**i zapis **planu App Service** są wypełniane. Te nazwy można zachować lub zmienić. Gdy wszystko będzie gotowe, wybierz pozycję **Utwórz**.

    ![Wybierz Azure App Service](../deployment/media/quickstart-publish-linux-create-new-dialog.png)

1. W oknie dialogowym **Publikowanie** nowo utworzone wystąpienie zostało automatycznie zaznaczone. Gdy wszystko będzie gotowe, kliknij przycisk **Zakończ**.

    ![Wybierz Azure App Service](../deployment/media/quickstart-publish-linux-select-instance.png)

1. Wybierz pozycję **Opublikuj**. Program Visual Studio wdraża aplikację w Azure App Service, a aplikacja sieci Web ładuje się w przeglądarce. W okienku **Publikowanie** właściwości projektu wyświetlany jest adres URL witryny i inne szczegóły.

    ![Okienko właściwości publikowania przedstawiające Podsumowanie profilu](../deployment/media/quickstart-publish-linux-summary-page.png)

## <a name="clean-up-resources"></a>Czyszczenie zasobów

W poprzednich krokach utworzono zasoby platformy Azure w grupie zasobów. Jeśli nie będziesz już potrzebować tych zasobów w przyszłości, możesz je usunąć przez usunięcie grupy zasobów.
W menu znajdującym się po lewej stronie w witrynie Azure Portal wybierz pozycję **Grupy zasobów**, a następnie wybierz pozycję **myResourceGroup**.
Na stronie grupy zasobów upewnij się, że zasoby na liście są tymi, które chcesz usunąć.
Wybierz pozycję **Usuń**, wpisz ciąg **myResourceGroup** w polu tekstowym, a następnie wybierz opcję **Usuń**.

## <a name="next-steps"></a>Następne kroki

W tym przewodniku szybki start przedstawiono sposób użycia programu Visual Studio do utworzenia profilu publikowania na potrzeby wdrożenia App Service w systemie Linux. Możesz chcieć uzyskać więcej informacji na temat publikowania w systemie Linux przy użyciu platformy Azure.

> [!div class="nextstepaction"]
> [App Service systemu Linux](/azure/app-service/containers/app-service-linux-intro)

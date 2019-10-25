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
ms.openlocfilehash: 4bbff0c2d149afddc355afe5f6c93e9d0aea54c0
ms.sourcegitcommit: 8589d85cc10710ef87e6363a2effa5ee5610d46a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/23/2019
ms.locfileid: "72806912"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio"></a>Publikowanie aplikacji sieci Web w celu Azure App Service przy użyciu programu Visual Studio

W przypadku aplikacji ASP.NET, ASP.NET Core, Node. js i .NET Core można publikować w Azure App Service lub Azure App Service Linux (przy użyciu kontenerów) przy użyciu jednej z poniższych metod.

* Aby ciągłe (lub zautomatyzowane) wdrażanie aplikacji, użyj platformy Azure DevOps z [Azure Pipelines](/azure/devops/pipelines/get-started-yaml?view=azdevops).

* W przypadku wdrożenia aplikacji jednorazowego (lub ręcznego) Użyj narzędzia do **publikowania** w programie Visual Studio, aby wdrożyć aplikacje ASP.NET, ASP.NET Core, Node. js i .NET Core do Azure App Service lub App Service dla systemu Linux (przy użyciu kontenerów). W przypadku aplikacji języka Python postępuj zgodnie z instrukcjami w sekcji [Python-Publish, aby Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md).

W tym artykule opisano sposób korzystania z narzędzia do **publikowania** na potrzeby wdrożenia jednorazowego.

[!INCLUDE [quickstart-prereqs-azure](includes/quickstart-prereqs-azure.md)]

## <a name="publish-to-azure-app-service"></a>Publikowanie w usłudze Azure App Service

1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Publikuj** (lub użyj elementu menu **Kompiluj** > **Opublikuj** ).

    ![Polecenie Publikuj w menu kontekstowym projektu w Eksplorator rozwiązań](../deployment/media/quickstart-publish.png "Wybierz pozycję Publikuj")

1. Jeśli wszystkie profile publikowania zostały wcześniej skonfigurowane, pojawi się okienko **Publikowanie** , w którym należy wybrać opcję **Utwórz nowy profil**.

1. W oknie dialogowym **Wybieranie elementu docelowego publikowania** wybierz **App Service**.

    ![Wybierz Azure App Service](../deployment/media/quickstart-publish-azure.png "Wybierz Azure App Service")

1. Wybierz pozycję **Publikuj**. Zostanie wyświetlone okno dialogowe **tworzenie App Service** . Zaloguj się przy użyciu konta platformy Azure, jeśli to konieczne, domyślne ustawienia usługi aplikacji wypełniają pola.

    ![Utwórz App Service](../deployment/media/quickstart-publish-settings-app-service.png "Utwórz Azure App Service")

1. Wybierz pozycję **Utwórz**. Program Visual Studio wdraża aplikację w Azure App Service, a aplikacja sieci Web ładuje się w przeglądarce. W okienku **Publikowanie** właściwości projektu wyświetlany jest adres URL witryny i inne szczegóły.

    ![Okienko właściwości publikowania przedstawiające Podsumowanie profilu](../deployment/media/quickstart-publish-app-service-summary.png)

## <a name="clean-up-resources"></a>Czyszczenie zasobów

W poprzednich krokach zostały utworzone zasoby platformy Azure w grupie zasobów. Jeśli nie chcesz potrzebować tych zasobów w przyszłości, możesz je usunąć przez usunięcie grupy zasobów.
Z menu po lewej stronie w obszarze Azure Portal wybierz pozycję **grupy zasobów** , a następnie wybierz pozycję Moja **resourceName**.
Na stronie Grupa zasobów upewnij się, że wymienione zasoby są tymi, które chcesz usunąć.
Wybierz pozycję **Usuń**, wpisz w polu tekstowym pozycję Moja **resourceName** , a następnie wybierz pozycję **Usuń**.

## <a name="next-steps"></a>Następne kroki

W tym przewodniku szybki start przedstawiono sposób użycia programu Visual Studio do utworzenia profilu publikowania na potrzeby wdrożenia na platformie Azure. Możesz również skonfigurować profil publikowania, importując ustawienia publikowania z Azure App Service.

> [!div class="nextstepaction"]
> [Importowanie ustawień publikowania i wdrażanie na platformie Azure](tutorial-import-publish-settings-azure.md)

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
ms.openlocfilehash: 1e05862aa57c24bfa8f17d551762054278dd6e52
ms.sourcegitcommit: 8589d85cc10710ef87e6363a2effa5ee5610d46a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/23/2019
ms.locfileid: "72806874"
---
# <a name="publish-an-aspnet-core-app-to-app-service-on-linux-using-visual-studio"></a>Publikowanie aplikacji ASP.NET Core App Service w systemie Linux przy użyciu programu Visual Studio

Począwszy od programu Visual Studio 2017 w wersji 15,7, można publikować ASP.NET Core aplikacje do Azure App Service Linux (przy użyciu kontenerów) przy użyciu jednej z poniższych metod.

* Aby ciągłe (lub zautomatyzowane) wdrażanie aplikacji, użyj platformy Azure DevOps z [Azure Pipelines](/azure/devops/pipelines/get-started-yaml?view=azdevops).

* W przypadku wdrożenia aplikacji jednorazowego (lub ręcznego) Użyj narzędzia do **publikowania** w programie Visual Studio, aby opublikować ASP.NET Core aplikacje do App Service dla systemu Linux (przy użyciu kontenerów).

W tym artykule opisano sposób korzystania z narzędzia do **publikowania** na potrzeby wdrożenia jednorazowego.

[!INCLUDE [quickstart-prereqs-azure-linux](includes/quickstart-prereqs-azure-linux.md)]

## <a name="publish-to-app-service-on-linux"></a>Publikowanie w usłudze App Service w systemie Linux

1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Publikuj** (lub użyj elementu menu **Kompiluj** > **Opublikuj** ).

    ![Polecenie Publikuj w menu kontekstowym projektu w Eksplorator rozwiązań](../deployment/media/quickstart-publish.png "Wybierz pozycję Publikuj")

1. Jeśli wszystkie profile publikowania zostały wcześniej skonfigurowane, pojawi się okienko **Publikowanie** , w którym należy wybrać opcję **Utwórz nowy profil**.

1. W oknie dialogowym **Wybieranie elementu docelowego publikowania** wybierz pozycję **App Service Linux**.

    ![Wybierz Azure App Service](../deployment/media/quickstart-publish-linux.png "Wybierz Azure App Service")

1. Wybierz pozycję **Publikuj**. Zostanie wyświetlone okno dialogowe **tworzenie App Service** . Zaloguj się przy użyciu konta platformy Azure, jeśli to konieczne, domyślne ustawienia usługi aplikacji wypełniają pola.

    ![Utwórz App Service](../deployment/media/quickstart-publish-settings-app-service-linux.png "Utwórz Azure App Service")

1. Wybierz pozycję **Utwórz**. Program Visual Studio wdraża aplikację w Azure App Service, a aplikacja sieci Web ładuje się w przeglądarce. W okienku **Publikowanie** właściwości projektu wyświetlany jest adres URL witryny i inne szczegóły.

    ![Okienko właściwości publikowania przedstawiające Podsumowanie profilu](../deployment/media/quickstart-publish-app-service-summary.png)

## <a name="clean-up-resources"></a>Czyszczenie zasobów

W poprzednich krokach zostały utworzone zasoby platformy Azure w grupie zasobów. Jeśli nie chcesz potrzebować tych zasobów w przyszłości, możesz je usunąć przez usunięcie grupy zasobów.
Z menu po lewej stronie w obszarze Azure Portal wybierz pozycję **grupy zasobów** , a następnie wybierz pozycję Moja **resourceName**.
Na stronie Grupa zasobów upewnij się, że wymienione zasoby są tymi, które chcesz usunąć.
Wybierz pozycję **Usuń**, wpisz w polu tekstowym pozycję Moja **resourceName** , a następnie wybierz pozycję **Usuń**.

## <a name="next-steps"></a>Następne kroki

W tym przewodniku szybki start przedstawiono sposób użycia programu Visual Studio do utworzenia profilu publikowania na potrzeby wdrożenia App Service w systemie Linux. Możesz chcieć uzyskać więcej informacji na temat publikowania w systemie Linux przy użyciu platformy Azure.

> [!div class="nextstepaction"]
> [App Service systemu Linux](/azure/app-service/containers/app-service-linux-intro)

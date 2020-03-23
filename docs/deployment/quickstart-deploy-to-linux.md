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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "72806874"
---
# <a name="publish-an-aspnet-core-app-to-app-service-on-linux-using-visual-studio"></a>Publikowanie aplikacji ASP.NET Core w usłudze App Service w systemie Linux przy użyciu programu Visual Studio

Począwszy od programu Visual Studio 2017 w wersji 15.7, można publikować ASP.NET podstawowe aplikacje do usługi Azure App Service Linux (przy użyciu kontenerów) przy użyciu jednej z następujących metod.

* W przypadku ciągłego (lub zautomatyzowanego) wdrażania aplikacji należy używać usługi Azure DevOps z [usługą Azure Pipelines](/azure/devops/pipelines/get-started-yaml?view=azdevops).

* W przypadku jednorazowego (lub ręcznego) wdrażania aplikacji użyj narzędzia **Publikowania** w programie Visual Studio, aby opublikować aplikacje ASP.NET Core w usłudze App Service dla systemu Linux (przy użyciu kontenerów).

W tym artykule opisano sposób używania narzędzia **Publikowania** do jednorazowego wdrażania.

[!INCLUDE [quickstart-prereqs-azure-linux](includes/quickstart-prereqs-azure-linux.md)]

## <a name="publish-to-app-service-on-linux"></a>Publikowanie w usłudze App Service w systemie Linux

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Publikuj** (lub użyj elementu menu **Buduj** > **publikowanie).**

    ![Polecenie Publikuj w menu kontekstowym projektu w Eksploratorze rozwiązań](../deployment/media/quickstart-publish.png "Wybierz pozycję Publikuj")

1. Jeśli wcześniej skonfigurowano profile publikowania, zostanie wyświetlone okienko **Publikowania,** w którym to przypadku wybierz pozycję **Utwórz nowy profil**.

1. W oknie **dialogowym Wybieranie celu publikowania** wybierz pozycję **App Service Linux**.

    ![Wybieranie usługi aplikacji platformy Azure](../deployment/media/quickstart-publish-linux.png "Wybieranie usługi aplikacji platformy Azure")

1. Wybierz pozycję **Publikuj**. Zostanie wyświetlone okno dialogowe **Tworzenie usługi app service.** Zaloguj się za pomocą konta platformy Azure, jeśli to konieczne, domyślne ustawienia usługi aplikacji wypełnić pola.

    ![Tworzenie usługi App Service](../deployment/media/quickstart-publish-settings-app-service-linux.png "Tworzenie usługi aplikacji platformy Azure")

1. Wybierz **pozycję Utwórz**. Visual Studio wdraża aplikację do usługi Azure App Service, a aplikacja internetowa ładuje się w przeglądarce. Właściwości projektu W okienku **Publikowanie** jest wyświetlany adres URL witryny i inne szczegóły.

    ![Publikowanie okienka właściwości z podsumowaniem profilu](../deployment/media/quickstart-publish-app-service-summary.png)

## <a name="clean-up-resources"></a>Oczyszczanie zasobów

W poprzednich krokach utworzono zasoby platformy Azure w grupie zasobów. Jeśli nie będziesz już potrzebować tych zasobów w przyszłości, możesz je usunąć przez usunięcie grupy zasobów.
W menu znajdującym się po lewej stronie w witrynie Azure Portal wybierz pozycję **Grupy zasobów**, a następnie wybierz pozycję **myResourceGroup**.
Na stronie grupy zasobów upewnij się, że zasoby na liście są tymi, które chcesz usunąć.
Wybierz pozycję **Usuń**, wpisz ciąg **myResourceGroup** w polu tekstowym, a następnie wybierz opcję **Usuń**.

## <a name="next-steps"></a>Następne kroki

W tym przewodniku Szybki start dowiesz się, jak utworzyć profil publikowania w usłudze App Service w systemie Linux za pomocą programu Visual Studio. Możesz chcieć więcej informacji na temat publikowania w systemie Linux przy użyciu platformy Azure.

> [!div class="nextstepaction"]
> [Usługa aplikacji dla systemu Linux](/azure/app-service/containers/app-service-linux-intro)

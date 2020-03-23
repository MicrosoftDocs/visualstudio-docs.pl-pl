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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "72806912"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio"></a>Publish a Web app to Azure App Service using Visual Studio (Publikowanie aplikacji internetowej w usłudze Azure App Service przy użyciu programu Visual Studio)

W przypadku ASP.NET ASP.NET aplikacje Core, Node.js i .NET Core publikuj w usłudze Azure App Service lub usłudze Azure App Service Linux (przy użyciu kontenerów) przy użyciu jednej z następujących metod.

* W przypadku ciągłego (lub zautomatyzowanego) wdrażania aplikacji należy używać usługi Azure DevOps z [usługą Azure Pipelines](/azure/devops/pipelines/get-started-yaml?view=azdevops).

* W przypadku jednorazowego (lub ręcznego) wdrażania aplikacji użyj narzędzia **Publikowania** w programie Visual Studio, aby wdrożyć ASP.NET, ASP.NET core, node.js i .NET Core w usłudze Azure App Service lub usłudze App Service dla systemu Linux (przy użyciu kontenerów). W przypadku aplikacji języka Python wykonaj kroki dotyczące [języka Python — publikuj w usłudze Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md).

W tym artykule opisano sposób używania narzędzia **Publikowania** do jednorazowego wdrażania.

[!INCLUDE [quickstart-prereqs-azure](includes/quickstart-prereqs-azure.md)]

## <a name="publish-to-azure-app-service"></a>Publikowanie w usłudze Azure App Service

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Publikuj** (lub użyj elementu menu **Buduj** > **publikowanie).**

    ![Polecenie Publikuj w menu kontekstowym projektu w Eksploratorze rozwiązań](../deployment/media/quickstart-publish.png "Wybierz pozycję Publikuj")

1. Jeśli wcześniej skonfigurowano profile publikowania, zostanie wyświetlone okienko **Publikowania,** w którym to przypadku wybierz pozycję **Utwórz nowy profil**.

1. W oknie **dialogowym Wybieranie celu publikowania** wybierz pozycję **App Service**.

    ![Wybieranie usługi aplikacji platformy Azure](../deployment/media/quickstart-publish-azure.png "Wybieranie usługi aplikacji platformy Azure")

1. Wybierz pozycję **Publikuj**. Zostanie wyświetlone okno dialogowe **Tworzenie usługi app service.** Zaloguj się za pomocą konta platformy Azure, jeśli to konieczne, domyślne ustawienia usługi aplikacji wypełnić pola.

    ![Tworzenie usługi App Service](../deployment/media/quickstart-publish-settings-app-service.png "Tworzenie usługi aplikacji platformy Azure")

1. Wybierz **pozycję Utwórz**. Visual Studio wdraża aplikację do usługi Azure App Service, a aplikacja internetowa ładuje się w przeglądarce. Właściwości projektu W okienku **Publikowanie** jest wyświetlany adres URL witryny i inne szczegóły.

    ![Publikowanie okienka właściwości z podsumowaniem profilu](../deployment/media/quickstart-publish-app-service-summary.png)

## <a name="clean-up-resources"></a>Oczyszczanie zasobów

W poprzednich krokach utworzono zasoby platformy Azure w grupie zasobów. Jeśli nie będziesz już potrzebować tych zasobów w przyszłości, możesz je usunąć przez usunięcie grupy zasobów.
W menu znajdującym się po lewej stronie w witrynie Azure Portal wybierz pozycję **Grupy zasobów**, a następnie wybierz pozycję **myResourceGroup**.
Na stronie grupy zasobów upewnij się, że zasoby na liście są tymi, które chcesz usunąć.
Wybierz pozycję **Usuń**, wpisz ciąg **myResourceGroup** w polu tekstowym, a następnie wybierz opcję **Usuń**.

## <a name="next-steps"></a>Następne kroki

W tym przewodniku Szybki start dowiesz się, jak utworzyć profil publikowania na platformie Azure za pomocą programu Visual Studio. Profil publikowania można również skonfigurować, importując ustawienia publikowania z usługi Azure App Service.

> [!div class="nextstepaction"]
> [Importowanie ustawień publikowania i wdrażanie na platformie Azure](tutorial-import-publish-settings-azure.md)

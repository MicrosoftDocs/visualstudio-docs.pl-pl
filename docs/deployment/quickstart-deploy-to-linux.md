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
ms.openlocfilehash: 12d1df3874388f0c113600e20ca2dbd080d15d10
ms.sourcegitcommit: e3d96b20381916bf4772f9db52b22275763bb603
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/31/2019
ms.locfileid: "55483968"
---
# <a name="publish-an-aspnet-core-app-to-app-service-on-linux-using-visual-studio"></a>Publikowanie aplikacji platformy ASP.NET Core w usłudze App Service w systemie Linux przy użyciu programu Visual Studio

Począwszy od programu Visual Studio 2017 w wersji 15.7 można publikować aplikacje platformy ASP.NET Core do usługi Azure App Service dla systemu Linux (przy użyciu kontenerów) przy użyciu jednej z następujących metod.

* Ciągła (lub automatycznych) wdrożenia aplikacji, użyj DevOps platformy Azure za pomocą [potoki Azure](https://docs.microsoft.com/azure/devops/pipelines/get-started-yaml?view=azdevops).

* Jednorazowe (lub ręczne) wdrożenia aplikacji, należy użyć **Publikuj** narzędzia w programie Visual Studio do publikowania aplikacji platformy ASP.NET Core w usłudze App Service dla systemu Linux (przy użyciu kontenerów).

W tym artykule opisano sposób używania **Publikuj** narzędzie jednorazowe wdrożenia.

[!INCLUDE [quickstart-prereqs-azure-linux](includes/quickstart-prereqs-azure-linux.md)]

## <a name="publish-to-app-service-on-linux"></a>Publikowanie w usłudze App Service w systemie Linux

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Publikuj** (lub użyj **kompilacji** > **Publikuj** element menu).

    ![Polecenia Opublikuj w menu kontekstowym projektu w Eksploratorze rozwiązań](../deployment/media/quickstart-publish.png "wybierz polecenie Publikuj")

1. Jeśli wcześniej skonfigurowano żadnych profilów publikowania **Publikuj** zostanie wyświetlone okienko, w których wielkość wybranych **Utwórz nowy profil**.

1. W **wybierz lokalizację docelową publikowania** okna dialogowego wybierz **App Service Linux**.

    ![Usługa Azure App Service wybierz](../deployment/media/quickstart-publish-linux.png "wybierz usługi Azure App Service")

1. Wybierz **publikowania**. **Tworzenie usługi App Service** pojawi się okno dialogowe. Zaloguj się przy użyciu konta platformy Azure możesz, jeśli to konieczne, a następnie domyślnych ustawień usługi app Wypełnij pola.

    ![Utwórz usługę App Service](../deployment/media/quickstart-publish-settings-app-service-linux.png "Tworzenie usługi Azure App Service")

1. Wybierz pozycję **Utwórz**. Program Visual Studio wdroży aplikację do usługi Azure App Service i ładowania aplikacji sieci web w przeglądarce. Właściwości projektu **Publikuj** okienko zawiera adres URL witryny oraz inne szczegóły.

    ![Okienko właściwości wyświetlanie podsumowania profil publikowania](../deployment/media/quickstart-publish-app-service-summary.png)

## <a name="clean-up-resources"></a>Oczyszczanie zasobów

W poprzednich krokach utworzono zasoby platformy Azure w grupie zasobów. Jeśli nie będziesz już potrzebować tych zasobów w przyszłości, możesz je usunąć przez usunięcie grupy zasobów.
Wybierz z menu po lewej stronie w witrynie Azure portal, **grup zasobów** , a następnie wybierz **myResourceGroup**.
Na stronie grupy zasobów upewnij się, że zasoby na liście są tymi, które chcesz usunąć.
Wybierz **Usuń**, typ **myResourceGroup** w polu tekstowym, a następnie wybierz pozycję **Usuń**.

## <a name="next-steps"></a>Następne kroki

W tym przewodniku Szybki Start przedstawiono sposób tworzenia profilu publikowania do wdrożenia usługi App Service w systemie Linux przy użyciu programu Visual Studio. Może być więcej informacji na temat publikowania w systemie Linux przy użyciu platformy Azure.

> [!div class="nextstepaction"]
> [Usługa App Service w systemie Linux](/azure/app-service/containers/app-service-linux-intro)

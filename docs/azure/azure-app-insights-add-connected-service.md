---
title: Dodawanie Application Insights platformy Azure przy użyciu usług połączonych | Microsoft Docs
description: Dodawanie usługi Azure Application Insights do aplikacji przy użyciu programu Visual Studio
author: AngelosP
manager: jillfra
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: c15e7a14052efdab82388a950865557cb4425771
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "88643546"
---
# <a name="add-azure-application-insights-by-using-visual-studio-connected-services"></a>Dodawanie Application Insights platformy Azure przy użyciu usług połączonych programu Visual Studio

Za pomocą programu Visual Studio można połączyć dowolne z następujących elementów z platformą Azure Application Insights przy użyciu funkcji **usługi połączone** :

- Aplikacja konsolowa .NET Framework
- ASP.NET MVC (.NET Framework) 
- ASP.NET Core
- .NET Core (w tym Aplikacja konsolowa, WPF, Windows Forms, Biblioteka klas)
- Rola procesu roboczego platformy .NET Core
- Azure Functions
- Aplikacja platforma uniwersalna systemu Windows
- Xamarin
- Cordova

Funkcja połączonej usługi dodaje wszystkie konieczne odwołania i kod połączenia do projektu i odpowiednio modyfikuje pliki konfiguracyjne.

> [!NOTE]
> Ten temat ma zastosowanie do programu Visual Studio w systemie Windows. Aby uzyskać Visual Studio dla komputerów Mac, zobacz [usługi połączone w programie Visual Studio dla komputerów Mac](/visualstudio/mac/connected-services).
## <a name="prerequisites"></a>Wymagania wstępne

- Program Visual Studio z zainstalowanym obciążeniem platformy Azure.
- Projekt jednego z obsługiwanych typów

## <a name="connect-to-azure-application-insights-using-connected-services"></a>Nawiązywanie połączenia z usługą Azure Application Insights przy użyciu usług połączonych

1. Otwórz projekt w programie Visual Studio.

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł **usługi połączone** , a następnie z menu kontekstowego wybierz polecenie **Dodaj podłączoną usługę**.

1. Na karcie **połączone usługi** wybierz ikonę + dla **zależności usługi**.

    ![Dodaj zależność usługi](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Na stronie **Dodawanie zależności** wybierz pozycję **Azure Application Insights**.

    ![Dodawanie Application Insights platformy Azure](./media/azure-app-insights-add-connected-service/azure-app-insights.png)

    Zaloguj się do konta platformy Azure, jeśli jeszcze nie zalogowano się. Jeśli nie masz konta platformy Azure, możesz zarejestrować się, aby skorzystać z [bezpłatnej wersji próbnej](https://azure.microsoft.com/account/free).

1. Na ekranie **Konfigurowanie usługi azure Application Insights** wybierz istniejący składnik usługi Azure Application Insights, a następnie wybierz przycisk **dalej**.

    Jeśli musisz utworzyć nowy składnik, przejdź do następnego kroku. W przeciwnym razie przejdź do kroku 7.

    ![Połącz z istniejącym składnikiem Application Insights](./media/azure-app-insights-add-connected-service/created-app-insights.png)

1. Aby utworzyć składnik Application Insights:

   1. Wybierz pozycję **Utwórz nowy składnik Application Insights** w dolnej części ekranu.

   1. Wypełnij **Application Insights: Utwórz nowy** ekran, a następnie wybierz pozycję **Utwórz**.

       ![Nowy składnik usługi Azure App Insights](./media/azure-app-insights-add-connected-service/create-new-app-insights.png)

   1. Po wyświetleniu ekranu **konfiguruj Application Insights platformy Azure** nowy składnik zostanie wyświetlony na liście. Wybierz nowy składnik z listy, a następnie wybierz przycisk **dalej**.

1. Wprowadź nazwę klucza Instrumentacji lub wybierz wartość domyślną, a następnie wybierz, czy parametry połączenia mają być przechowywane w lokalnym pliku tajemnicy, czy w [Azure Key Vault](/azure/key-vault).

   ![Określ parametry połączenia](./media/azure-app-insights-add-connected-service/connection-string.png)

1. Na ekranie **Podsumowanie zmian** są wyświetlane wszystkie modyfikacje, które zostaną wprowadzone w projekcie w przypadku ukończenia procesu. Jeśli zmiany wyglądają na OK, wybierz przycisk **Zakończ**.

   ![Podsumowanie zmian](./media/azure-app-insights-add-connected-service/summary-of-changes.png)

1. Połączenie jest wyświetlane w sekcji **zależności usługi** na karcie **podłączone usługi** .

   ![Zależności usługi](./media/azure-app-insights-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Zobacz też

- [Strona produktu Azure Monitor](https://azure.microsoft.com/services/monitor/)
- [Dokumentacja usługi Azure App Insights](/azure/azure-monitor/app/app-insights-overview/)
- [Połączone usługi (Visual Studio dla komputerów Mac)](/visualstudio/mac/connected-services)

---
title: Dodawanie konfiguracji aplikacji platformy Azure przy użyciu usług połączonych | Microsoft Docs
description: Dodawanie zależności usługi konfiguracji platformy Azure do aplikacji przy użyciu usług połączonych programu Visual Studio
author: ghogen
manager: ''
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 12/11/2020
ms.author: ghogen
monikerRange: '>=vs-2019'
ms.openlocfilehash: a0db2f2e4993fcc3c986686322b8915615758e13
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727297"
---
# <a name="adding-azure-app-configuration-by-using-visual-studio-connected-services"></a>Dodawanie konfiguracji aplikacji platformy Azure przy użyciu usług połączonych programu Visual Studio

W tym samouczku dowiesz się, jak łatwo dodać wszystko, czego potrzebujesz, aby rozpocząć korzystanie z usługi Azure App Configuration do zarządzania flagami konfiguracji i funkcji dla projektów sieci Web w programie Visual Studio, niezależnie od tego, czy używasz ASP.NET Core, czy też dowolnego typu projektu ASP.NET. Korzystając z funkcji usługi połączone w programie Visual Studio, można automatycznie dodać wszystkie kod, pakiety NuGet i ustawienia konfiguracji, które są wymagane do nawiązania połączenia z zasobem konfiguracji aplikacji na platformie Azure. Aby użyć tej funkcji, musisz używać programu Visual Studio 2019 w wersji 16,9 lub nowszej.

> [!NOTE]
> Ten temat ma zastosowanie do programu Visual Studio w systemie Windows. Aby uzyskać Visual Studio dla komputerów Mac, zobacz [usługi połączone w programie Visual Studio dla komputerów Mac](/visualstudio/mac/connected-services).

## <a name="prerequisites"></a>Wymagania wstępne

- Program Visual Studio z zainstalowanym obciążeniem platformy Azure.
- Projekt jednego z obsługiwanych typów

## <a name="connect-to-azure-app-configuration-using-connected-services"></a>Łączenie z konfiguracją aplikacji platformy Azure przy użyciu usług połączonych

1. Otwórz projekt w programie Visual Studio.

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy węzeł **usługi połączone** , a następnie z menu kontekstowego wybierz polecenie **Dodaj podłączoną usługę**.

    ![Dodawanie usługi połączonej z platformą Azure](./media/vs-azure-tools-connected-services-storage/vs-2019/add-connected-service.png)

1. Na karcie **połączone usługi** wybierz ikonę + dla **zależności usługi**.

    ![Dodaj zależność usługi](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Na stronie **Dodawanie zależności** wybierz pozycję **Konfiguracja aplikacji platformy Azure**.

    ![Dodaj konfigurację aplikacji](./media/vs-azure-tools-connected-services-app-configuration/add-azure-app-configuration.png)

    Zaloguj się do konta platformy Azure, jeśli jeszcze nie zalogowano się. Jeśli nie masz konta platformy Azure, możesz zarejestrować się, aby skorzystać z [bezpłatnej wersji próbnej](https://azure.microsoft.com/free/dotnet).

1. Na ekranie **Konfigurowanie konfiguracji aplikacji Azure** wybierz swoją subskrypcję i istniejący magazyn konfiguracji. Następnie wybierz przycisk **Dalej**.

    Jeśli musisz utworzyć magazyn konfiguracji aplikacji, przejdź do następnego kroku. W przeciwnym razie przejdź do kroku 6.

    ![Dodaj istniejące konto konfiguracji do projektu](./media/vs-azure-tools-connected-services-app-configuration/select-config-store.png)

1. Aby utworzyć magazyn konfiguracji aplikacji:

   1. Wybierz ikonę + znajdującą się po prawej stronie nagłówka **magazynów konfiguracji aplikacji** . 

   1. Wypełnij pola **Konfiguracja aplikacji platformy Azure: Utwórz nowe** okno dialogowe, a następnie wybierz pozycję **Utwórz**. Należy pamiętać, że pole Nazwa zasobu musi być unikatowe. 

       ![Nowy magazyn konfiguracji aplikacji platformy Azure](./media/vs-azure-tools-connected-services-app-configuration/create-new-config-store.png)

   1. Gdy zostanie wyświetlone okno dialogowe **Konfiguracja aplikacji platformy Azure** , nowy magazyn konfiguracji zostanie wyświetlony na liście. Wybierz ten nowy magazyn, a następnie wybierz pozycję **dalej**.

1. Wprowadź nazwę parametrów połączenia i zdecyduj, czy chcesz, aby parametry połączenia były przechowywane w lokalnym pliku tajemnicy, czy w [Azure Key Vault](/azure/key-vault).

   ![Określ parametry połączenia](./media/vs-azure-tools-connected-services-app-configuration/connection-string-app-config.png)

1. Na ekranie **Podsumowanie zmian** są wyświetlane wszystkie modyfikacje, które zostaną wprowadzone w projekcie w przypadku ukończenia procesu. Jeśli zmiany wyglądają na OK, wybierz przycisk **Zakończ**.

   ![Podsumowanie zmian](./media/vs-azure-tools-connected-services-app-configuration/summary-of-changes-app-config.png)

1. Po zakończeniu **procesu konfiguracji zależności** konfiguracja aplikacji platformy Azure zostanie teraz wyświetlona w węźle **zależności usługi** projektu.

## <a name="next-steps"></a>Następne kroki

Dowiedz się więcej o konfiguracji aplikacji platformy Azure w dokumentacji dotyczącej [konfiguracji aplikacji platformy Azure](/azure/azure-app-configuration/overview).

## <a name="see-also"></a>Zobacz też

- [Samouczek dotyczący używania konfiguracji dynamicznej w konfiguracji aplikacji połączonej ASP.NET Core aplikacji](/azure/azure-app-configuration/enable-dynamic-configuration-aspnet-core)
- [Połączone usługi (Visual Studio dla komputerów Mac)](/visualstudio/mac/connected-services)
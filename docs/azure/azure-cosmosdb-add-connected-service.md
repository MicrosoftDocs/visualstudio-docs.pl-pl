---
title: Dodawanie usługi Azure CosmosDB za pomocą usług połączonych | Microsoft Docs
description: Dodaj obsługę usługi Azure CosmosDB do aplikacji przy użyciu programu Visual Studio, aby dodać podłączoną usługę
author: AngelosP
manager: jmartens
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: 070c1e77559e33ac398730b1bafc5a4a86825cda
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841187"
---
# <a name="add-azure-cosmos-db-to-your-app-by-using-visual-studio-connected-services"></a>Dodawanie Azure Cosmos DB do aplikacji przy użyciu usług połączonych programu Visual Studio

Za pomocą programu Visual Studio można połączyć dowolne z następujących elementów, aby Azure Cosmos DB przy użyciu funkcji **usługi połączone** :

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

## <a name="connect-to-azure-cosmos-db-using-connected-services"></a>Nawiązywanie połączenia z usługą Azure Cosmos DB przy użyciu usług połączonych

1. Otwórz projekt w programie Visual Studio.

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy węzeł **usługi połączone** , a następnie z menu kontekstowego wybierz polecenie **Dodaj podłączoną usługę**.

1. Na karcie **połączone usługi** wybierz ikonę + dla **zależności usługi**.

    ![Dodaj zależność usługi](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Na stronie **Dodawanie zależności** wybierz pozycję **Azure Cosmos DB**.

    ![Dodaj Azure Cosmos DB](./media/azure-cosmosdb-add-connected-service/azure-cosmosdb.png)

    Zaloguj się do konta platformy Azure, jeśli jeszcze nie zalogowano się. Jeśli nie masz konta platformy Azure, możesz zarejestrować się, aby skorzystać z [bezpłatnej wersji próbnej](https://azure.microsoft.com/account/free).

1. Na ekranie **Azure Cosmos DB** wybierz istniejący Azure Cosmos DB i wybierz przycisk **dalej**.

    Jeśli musisz utworzyć bazę danych, przejdź do następnego kroku. W przeciwnym razie przejdź do kroku 7.

    ![Dodaj istniejące Cosmos DB do projektu](./media/azure-cosmosdb-add-connected-service/created-cosmosdb.png)

1. Aby utworzyć Azure Cosmos DB:

   1. Wybierz pozycję **Utwórz nową Azure Cosmos DB** w dolnej części ekranu.

   1. Wypełnij **Azure Cosmos DB: Utwórz nowy** ekran, a następnie wybierz pozycję **Utwórz**.

       ![Nowe Azure Cosmos DB](./media/azure-cosmosdb-add-connected-service/create-new-cosmosdb.png)

   1. Gdy zostanie wyświetlone okno dialogowe **konfigurowanie Azure Cosmos DB** , Nowa baza danych zostanie wyświetlona na liście. Wybierz nową bazę danych z listy, a następnie wybierz pozycję **dalej**.

1. Wprowadź nazwę parametrów połączenia i zdecyduj, czy chcesz, aby parametry połączenia były przechowywane w lokalnym pliku tajemnicy, czy w [Azure Key Vault](/azure/key-vault).

   ![Określ parametry połączenia](./media/azure-cosmosdb-add-connected-service/connection-string.png)

1. Na ekranie **Podsumowanie zmian** są wyświetlane wszystkie modyfikacje, które zostaną wprowadzone w projekcie w przypadku ukończenia procesu. Jeśli zmiany wyglądają na OK, wybierz przycisk **Zakończ**.

   ![Podsumowanie zmian](./media/azure-cosmosdb-add-connected-service/summary-of-changes.png)

1. Połączenie jest wyświetlane w sekcji **zależności usługi** na karcie **podłączone usługi** .

   ![Zależności usługi](./media/azure-cosmosdb-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Zobacz też

- [Strona produktu Azure Cosmos DB](https://azure.microsoft.com/services/cosmos-db/)
- [Dokumentacja usługi Azure Cosmos DB](/azure/cosmos-db/)
- [Połączone usługi (Visual Studio dla komputerów Mac)](/visualstudio/mac/connected-services)

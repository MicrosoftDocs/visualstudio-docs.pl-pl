---
title: Dodaj połączenie do Azure SQL Database | Microsoft Docs
description: Dodawanie połączenia Azure SQL Database do aplikacji przy użyciu usług połączonych programu Visual Studio
author: AngelosP
manager: jillfra
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: 09ae5768e55ae3e08ec2549faeb7cefa70a5edd1
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2020
ms.locfileid: "93399050"
---
# <a name="add-a-connection-to-azure-sql-database"></a>Dodaj połączenie do Azure SQL Database

W programie Visual Studio można połączyć dowolne z następujących elementów w usłudze Azure SQL Database przy użyciu funkcji **usługi połączone** :

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

## <a name="connect-to-azure-sql-database-using-connected-services"></a>Nawiązywanie połączenia z usługą Azure SQL Database przy użyciu usług połączonych

1. Otwórz projekt w programie Visual Studio.

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy węzeł **usługi połączone** , a następnie z menu kontekstowego wybierz polecenie **Dodaj podłączoną usługę**.

1. Na karcie **połączone usługi** wybierz ikonę + dla **zależności usługi**.

    ![Dodaj zależność usługi](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Na stronie **Dodawanie zależności** wybierz pozycję **Azure SQL Database**.

    ![Dodaj usługę Azure SQL Database](./media/azure-sql-database-add-connected-service/azure-sql-database.png)

    Zaloguj się do konta platformy Azure, jeśli jeszcze nie zalogowano się. Jeśli nie masz konta platformy Azure, możesz zarejestrować się, aby skorzystać z [bezpłatnej wersji próbnej](https://azure.microsoft.com/account/free).

1. Na ekranie **konfigurowanie Azure SQL Database** wybierz istniejący Azure SQL Database i wybierz przycisk **dalej**.

    Jeśli musisz utworzyć nowy składnik, przejdź do następnego kroku. W przeciwnym razie przejdź do kroku 7.

    ![Połącz z istniejącym składnikiem Azure SQL Database](./media/azure-sql-database-add-connected-service/created-azure-sql-database.png)

1. Aby utworzyć Azure SQL Database:

   1. Wybierz pozycję **utwórz SQL Database** w dolnej części ekranu.

   1. Wypełnij **Azure SQL Database: Utwórz nowy** ekran, a następnie wybierz pozycję **Utwórz**.

       ![Nowe Azure SQL Database](./media/azure-sql-database-add-connected-service/create-new-azure-sql-database.png)

   1. Po wyświetleniu ekranu **konfigurowania Azure SQL Database** Nowa baza danych zostanie wyświetlona na liście. Wybierz nową bazę danych z listy, a następnie wybierz pozycję **dalej**.

1. Wprowadź nazwę parametrów połączenia lub wybierz wartość domyślną, a następnie wybierz, czy parametry połączenia mają być przechowywane w lokalnym pliku tajemnicy, czy w [Azure Key Vault](/azure/key-vault).

   ![Określ parametry połączenia](./media/azure-sql-database-add-connected-service/connection-string.png)

1. Na ekranie **Podsumowanie zmian** są wyświetlane wszystkie modyfikacje, które zostaną wprowadzone w projekcie w przypadku ukończenia procesu. Jeśli zmiany wyglądają na OK, wybierz przycisk **Zakończ**.

   ![Podsumowanie zmian](./media/azure-sql-database-add-connected-service/summary-of-changes.png)

   Jeśli zostanie wyświetlony monit o ustawienie reguł zapory, wybierz opcję **tak**.

   ![Reguły zapory](./media/azure-sql-database-add-connected-service/firewall-rules.png)

1. Połączenie jest wyświetlane w sekcji **zależności usługi** na karcie **podłączone usługi** .

   ![Zależności usługi](./media/azure-sql-database-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Zobacz też

- [Strona produktu Azure SQL Database](https://azure.microsoft.com/services/sql-database/)
- [Dokumentacja usługi Azure SQL Database](/azure/azure-sql/database/)
- [Połączone usługi (Visual Studio dla komputerów Mac)](/visualstudio/mac/connected-services)

---
title: Dodawanie połączenia do Azure SQL Database | Microsoft Docs
description: Dodawanie Azure SQL Database do aplikacji przy użyciu usługi Visual Studio Połączonych usług
author: AngelosP
manager: jmartens
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: 26a01bfe2a34422f9596710f832a1c4af699fd3b
ms.sourcegitcommit: 3fe04d5b931ae459a802a1b965f84186757cbc08
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2021
ms.locfileid: "111588491"
---
# <a name="add-a-connection-to-azure-sql-database"></a>Dodawanie połączenia do Azure SQL Database

Za Visual Studio można połączyć dowolny z następujących połączeń z usługą Azure SQL Database pomocą funkcji **Usługi** połączone:

- .NET Framework aplikacji konsolowej
- ASP.NET MVC (.NET Framework) 
- ASP.NET Core
- .NET Core (w tym aplikacja konsolowa, WPF, Windows Forms, biblioteka klas)
- Rola procesu roboczego .NET Core
- Azure Functions
- platforma uniwersalna systemu Windows aplikacji
- Xamarin
- Cordova

Funkcja usługi połączonej dodaje wszystkie potrzebne odwołania i kod połączenia do projektu i odpowiednio modyfikuje pliki konfiguracji.

> [!NOTE]
> Ten temat dotyczy Visual Studio w systemie Windows. Aby uzyskać Visual Studio dla komputerów Mac, zobacz [Usługi połączone w Visual Studio dla komputerów Mac](/visualstudio/mac/connected-services).
## <a name="prerequisites"></a>Wymagania wstępne

- Visual Studio z zainstalowanym obciążeniem platformy Azure.
- Projekt jednego z obsługiwanych typów

## <a name="connect-to-azure-sql-database-using-connected-services"></a>Nawiązywanie połączenia z Azure SQL Database przy użyciu usług połączonych

1. Otwórz projekt w programie Visual Studio.

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy węzeł **Usługi** połączone, a następnie z menu kontekstowego wybierz pozycję **Dodaj usługę połączeniową.**

1. Na karcie **Usługi połączone** wybierz ikonę + dla opcji **Zależności usług.**

    ![Dodawanie zależności usługi](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Na stronie **Dodawanie zależności** wybierz pozycję **Azure SQL Database**.

    ![Dodawanie Azure SQL Database service](./media/azure-sql-database-add-connected-service/azure-sql-database.png)

    Jeśli jeszcze nie zalogowano się, zaloguj się do konta platformy Azure. Jeśli nie masz konta platformy Azure, możesz utworzyć konto bezpłatnej [wersji próbnej.](https://azure.microsoft.com/account/free)

1. Na **ekranie Azure SQL Database** wybierz istniejącą aplikację, Azure SQL Database następnie wybierz pozycję **Dalej.**

    Jeśli musisz utworzyć nowy składnik, przejdź do następnego kroku. W przeciwnym razie przejdź do kroku 7.

    ![Nawiązywanie połączenia z istniejącym Azure SQL Database sieciowym](./media/azure-sql-database-add-connected-service/created-azure-sql-database.png)

1. Aby utworzyć Azure SQL Database:

   1. Wybierz **pozycję SQL Database** u dołu ekranu.

   1. Wypełnij pole **Azure SQL Database: Create new screen** (Utwórz nowy ekran), a następnie wybierz pozycję Create **(Utwórz).**

       ![Nowe Azure SQL Database](./media/azure-sql-database-add-connected-service/create-new-azure-sql-database.png)

   1. Gdy zostanie **Azure SQL Database** ekran Azure SQL Database, nowa baza danych zostanie wyświetlona na liście. Wybierz nową bazę danych z listy, a następnie wybierz pozycję **Dalej.**

1. Wprowadź nazwę parametrów połączenia lub wybierz wartość domyślną, a następnie wybierz, czy chcesz przechowywać ciągi połączenia w lokalnym pliku wpisów tajnych, czy w pliku [Azure Key Vault](/azure/key-vault).

   ![Określanie parametrów połączenia](./media/azure-sql-database-add-connected-service/connection-string.png)

1. Ekran **Podsumowanie zmian** zawiera wszystkie modyfikacje, które zostaną wprowadzone w projekcie po zakończeniu procesu. Jeśli zmiany wyglądają dobrze, wybierz pozycję **Zakończ.**

   ![Podsumowanie zmian](./media/azure-sql-database-add-connected-service/summary-of-changes.png)

   Jeśli zostanie wyświetlony monit o ustawienie reguł zapory, wybierz pozycję **Tak.**

   ![Reguły zapory](./media/azure-sql-database-add-connected-service/firewall-rules.png)

1. Połączenie zostanie wyświetlone w sekcji **Zależności usług** na **karcie Usługi** połączone.

   ![Zależności usługi](./media/azure-sql-database-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Zobacz też

- [Azure SQL Database produktu](https://azure.microsoft.com/services/sql-database/)
- [Dokumentacja usługi Azure SQL Database](/azure/azure-sql/database/)
- [Połączone usługi (Visual Studio dla komputerów Mac)](/visualstudio/mac/connected-services)

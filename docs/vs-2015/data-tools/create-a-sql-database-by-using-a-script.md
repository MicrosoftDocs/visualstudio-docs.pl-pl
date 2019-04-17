---
title: Tworzenie bazy danych SQL za pomocą skryptu | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
ms.assetid: 36f913c0-f5a7-4831-83a0-baba721ac95c
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b78e70ae790a39cb761eca34dcdc2b9b32b5bbfd
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59653635"
---
# <a name="create-a-sql-database-by-using-a-script"></a>Tworzenie bazy danych SQL za pomocą skryptu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym przewodniku używasz programu Visual Studio do tworzenia małej bazy danych, który zawiera przykładowy kod dla [Tworzenie prostej aplikacji danych przy użyciu pakietu ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md).  
  
 **W tym temacie**  
  
-   [Utwórz skrypt, który zawiera schemat bazy danych](../data-tools/create-a-sql-database-by-using-a-script.md#CreateScript)  
  
-   [Utwórz projekt bazy danych i importowanie schematu](../data-tools/create-a-sql-database-by-using-a-script.md#CreateProject)  
  
-   [Wdrażanie bazy danych](../data-tools/create-a-sql-database-by-using-a-script.md#DeployDatabase)  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Do przeprowadzenia tego instruktażu, musi mieć programu SQL Server Express LocalDB lub innej bazy danych SQL zainstalowana.  
  
##  <a name="CreateScript"></a> Utwórz skrypt, który zawiera schemat bazy danych  
  
#### <a name="to-create-a-script-from-which-you-can-import-a-schema"></a>Aby utworzyć skrypt, z którego można importować schematy  
  
1.  W [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], na pasku menu wybierz **pliku** > **New** > **pliku**.  
  
     **Nowy plik** pojawi się okno dialogowe.  
  
2.  W **kategorie** listy wybierz **ogólne**.  
  
3.  W **szablony** listy wybierz **plik Sql**, a następnie wybierz pozycję **Otwórz** przycisku.  
  
     Zostanie otwarty Edytor Transact-SQL.  
  
4.  Skopiuj poniższy kod języka Transact-SQL, a następnie wklej go do edytora języka Transact-SQL.  
  
    ```  
    PRINT N'Creating Sales...';  
    GO  
    CREATE SCHEMA [Sales]  
        AUTHORIZATION [dbo];  
    GO  
    PRINT N'Creating Sales.Customer...';  
    GO  
    CREATE TABLE [Sales].[Customer] (  
        [CustomerID]   INT           IDENTITY (1, 1) NOT NULL,  
        [CustomerName] NVARCHAR (40) NOT NULL,  
        [YTDOrders]    INT           NOT NULL,  
        [YTDSales]     INT           NOT NULL  
    );  
    GO  
    PRINT N'Creating Sales.Orders...';  
    GO  
    CREATE TABLE [Sales].[Orders] (  
        [CustomerID] INT      NOT NULL,  
        [OrderID]    INT      IDENTITY (1, 1) NOT NULL,  
        [OrderDate]  DATETIME NOT NULL,  
        [FilledDate] DATETIME NULL,  
        [Status]     CHAR (1) NOT NULL,  
        [Amount]     INT      NOT NULL  
    );  
    GO  
    PRINT N'Creating Sales.Def_Customer_YTDOrders...';  
    GO  
    ALTER TABLE [Sales].[Customer]  
        ADD CONSTRAINT [Def_Customer_YTDOrders] DEFAULT 0 FOR [YTDOrders];  
    GO  
    PRINT N'Creating Sales.Def_Customer_YTDSales...';  
    GO  
    ALTER TABLE [Sales].[Customer]  
        ADD CONSTRAINT [Def_Customer_YTDSales] DEFAULT 0 FOR [YTDSales];  
    GO  
    PRINT N'Creating Sales.Def_Orders_OrderDate...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [Def_Orders_OrderDate] DEFAULT GetDate() FOR [OrderDate];  
    GO  
    PRINT N'Creating Sales.Def_Orders_Status...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [Def_Orders_Status] DEFAULT 'O' FOR [Status];  
    GO  
    PRINT N'Creating Sales.PK_Customer_CustID...';  
    GO  
    ALTER TABLE [Sales].[Customer]  
        ADD CONSTRAINT [PK_Customer_CustID] PRIMARY KEY CLUSTERED ([CustomerID] ASC) WITH (ALLOW_PAGE_LOCKS = ON, ALLOW_ROW_LOCKS = ON, PAD_INDEX = OFF, IGNORE_DUP_KEY = OFF, STATISTICS_NORECOMPUTE = OFF);  
    GO  
    PRINT N'Creating Sales.PK_Orders_OrderID...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [PK_Orders_OrderID] PRIMARY KEY CLUSTERED ([OrderID] ASC) WITH (ALLOW_PAGE_LOCKS = ON, ALLOW_ROW_LOCKS = ON, PAD_INDEX = OFF, IGNORE_DUP_KEY = OFF, STATISTICS_NORECOMPUTE = OFF);  
    GO  
    PRINT N'Creating Sales.FK_Orders_Customer_CustID...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [FK_Orders_Customer_CustID] FOREIGN KEY ([CustomerID]) REFERENCES [Sales].[Customer] ([CustomerID]) ON DELETE NO ACTION ON UPDATE NO ACTION;  
    GO  
    PRINT N'Creating Sales.CK_Orders_FilledDate...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [CK_Orders_FilledDate] CHECK ((FilledDate >= OrderDate) AND (FilledDate < '01/01/2020'));  
    GO  
    PRINT N'Creating Sales.CK_Orders_OrderDate...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [CK_Orders_OrderDate] CHECK ((OrderDate > '01/01/2005') and (OrderDate < '01/01/2020'));  
    GO  
    PRINT N'Creating Sales.uspCancelOrder...';  
    GO  
    CREATE PROCEDURE [Sales].[uspCancelOrder]  
    @OrderID INT  
    AS  
    BEGIN  
    DECLARE @Delta INT, @CustomerID INT  
    BEGIN TRANSACTION  
        SELECT @Delta = [Amount], @CustomerID = [CustomerID]  
         FROM [Sales].[Orders] WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Orders]  
       SET [Status] = 'X'  
    WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Customer]  
       SET  
       YTDOrders = YTDOrders - @Delta  
        WHERE [CustomerID] = @CustomerID  
    COMMIT TRANSACTION  
    END  
    GO  
    PRINT N'Creating Sales.uspFillOrder...';  
    GO  
    CREATE PROCEDURE [Sales].[uspFillOrder]  
    @OrderID INT, @FilledDate DATETIME  
    AS  
    BEGIN  
    DECLARE @Delta INT, @CustomerID INT  
    BEGIN TRANSACTION  
        SELECT @Delta = [Amount], @CustomerID = [CustomerID]  
         FROM [Sales].[Orders] WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Orders]  
       SET [Status] = 'F',  
           [FilledDate] = @FilledDate  
    WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Customer]  
       SET  
       YTDSales = YTDSales + @Delta  
        WHERE [CustomerID] = @CustomerID  
    COMMIT TRANSACTION  
    END  
    GO  
    PRINT N'Creating Sales.uspNewCustomer...';  
    GO  
    CREATE PROCEDURE [Sales].[uspNewCustomer]  
    @CustomerName NVARCHAR (40),  
    @CustomerID INT OUTPUT  
    AS  
    BEGIN  
    INSERT INTO [Sales].[Customer] (CustomerName) VALUES (@CustomerName);  
    SET @CustomerID = SCOPE_IDENTITY();  
    RETURN @@ERROR  
    END  
    GO  
    PRINT N'Creating Sales.uspPlaceNewOrder...';  
    GO  
    CREATE PROCEDURE [Sales].[uspPlaceNewOrder]  
    @CustomerID INT, @Amount INT, @OrderDate DATETIME, @Status CHAR (1)='O'  
    AS  
    BEGIN  
    DECLARE @RC INT  
    BEGIN TRANSACTION  
    INSERT INTO [Sales].[Orders] (CustomerID, OrderDate, FilledDate, Status, Amount)   
         VALUES (@CustomerID, @OrderDate, NULL, @Status, @Amount)  
    SELECT @RC = SCOPE_IDENTITY();  
    UPDATE [Sales].[Customer]  
       SET  
       YTDOrders = YTDOrders + @Amount  
        WHERE [CustomerID] = @CustomerID  
    COMMIT TRANSACTION  
    RETURN @RC  
    END  
    GO  
    CREATE PROCEDURE [Sales].[uspShowOrderDetails]  
    @CustomerID INT=0  
    AS  
    BEGIN  
    SELECT [C].[CustomerName], CONVERT(date, [O].[OrderDate]), CONVERT(date, [O].[FilledDate]), [O].[Status], [O].[Amount]  
      FROM [Sales].[Customer] AS C  
      INNER JOIN [Sales].[Orders] AS O  
         ON [O].[CustomerID] = [C].[CustomerID]  
      WHERE [C].[CustomerID] = @CustomerID  
    END  
    GO  
    ```  
  
5.  Na pasku menu wybierz **pliku** > **Zapisz SqlQuery_1.sql jako**.  
  
     **Zapisz plik jako** pojawi się okno dialogowe.  
  
6.  W **nazwy pliku** wprowadź `SampleImportScript.sql`, zanotuj lokalizację, w którym będzie zapisać plik, a następnie wybierz **Zapisz** przycisku.  
  
7.  Na pasku menu wybierz **pliku** > **Zamknij rozwiązanie**.  
  
     Następnie utwórz projekt bazy danych, a następnie zaimportuj schemat ze skryptu, który został utworzony.  
  
##  <a name="CreateProject"></a> Utwórz projekt bazy danych i importowanie schematu  
  
#### <a name="to-create-a-database-project"></a>Aby utworzyć projekt bazy danych  
  
1.  Na pasku menu wybierz **pliku** > **New** > **projektu**.  
  
     **Nowy projekt** pojawi się okno dialogowe.  
  
2.  W obszarze **zainstalowane**, rozwiń węzeł **szablony** węzła, rozwiń węzeł **inne języki** węzeł **programu SQL Server** kategorii, a następnie Wybierz **projekt bazy danych programu SQL Server** szablonu.  
  
    > [!NOTE]
    >  **Inne języki** węzeł nie jest wyświetlane we wszystkich instalacjach programu Visual Studio.  
  
3.  W **nazwa** wprowadź `Small Database`.  
  
4.  Wybierz **Utwórz katalog rozwiązania** pole wyboru, jeśli nie została jeszcze wybrana.  
  
5.  Wyczyść **Dodaj do kontroli źródła** pole wyboru, jeśli nie jest już wyczyszczone, a następnie wybierz **OK** przycisku.  
  
     Projekt bazy danych jest tworzony i wyświetlany w **Eksploratora rozwiązań**.  
  
     Następnie zaimportuj schemat bazy danych ze skryptu.  
  
#### <a name="to-import-a-database-schema-from-a-script"></a>Aby importować schemat bazy danych ze skryptu  
  
1.  Na pasku menu wybierz **projektu** > **importu** > **skryptu**.  
  
2.  Na **powitalnej** strony, Przejrzyj tekst, a następnie wybierz pozycję **dalej** przycisku.  
  
3.  Wybierz **pojedynczy plik** przycisk opcji, a następnie wybierz **Przeglądaj** przycisku.  
  
     **Importuj skrypt SQL** pojawi się okno dialogowe.  
  
4.  Otwórz folder, w której zapisano plik SampleImportScript.sql, wybierz plik, a następnie wybierz **Otwórz** przycisku.  
  
5.  Wybierz **Zakończ** przycisk, aby zamknąć **Importuj skrypt SQL** okno dialogowe.  
  
     Skrypt jest importowany, a obiekty definiowane przez skrypt są dodane do projektu bazy danych.  
  
6.  Przejrzyj podsumowanie, a następnie kliknij przycisk **Zakończ** przycisk, aby zamknąć **Import pliku skryptu SQL** okno dialogowe.  
  
7.  W **Eksploratora rozwiązań**, rozwiń węzeł sprzedaży, skryptów i zabezpieczeń folderów projektu i sprawdź, czy zawierają one pliki .sql.  
  
8.  W **Eksplorator obiektów SQL Server**, sprawdź, czy baza danych jest wyświetlana w obszarze **projektów** węzła.  
  
     W tym momencie baza danych zawiera tylko obiekty systemowe, takie jak tabele i procedury składowane. Po wdrożeniu bazy danych będzie zawierać tabele użytkownika i procedur składowanych, które definiują skrypty.  
  
##  <a name="DeployDatabase"></a> Wdrażanie bazy danych  
 Po naciśnięciu klawisza **F5** klucza, Wdróż (lub opublikować) bazę danych do bazy danych LocalDB, domyślnie. Można wdrożyć bazy danych do innej lokalizacji otwierając stronę właściwości dla projektu, wybierając **debugowania** kartę, a następnie zmieniając ciąg połączenia.

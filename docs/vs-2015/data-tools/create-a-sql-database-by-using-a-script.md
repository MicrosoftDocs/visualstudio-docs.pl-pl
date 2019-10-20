---
title: Tworzenie bazy danych SQL przy użyciu skryptu | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3bef7c4be2f38d0f50b2a13c7745cb212204769b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670091"
---
# <a name="create-a-sql-database-by-using-a-script"></a>Tworzenie bazy danych SQL za pomocą skryptu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym instruktażu program Visual Studio służy do tworzenia małych baz danych, które zawierają przykładowy kod służący do [tworzenia prostej aplikacji danych za pomocą ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md).

 **W tym temacie**

- [Utwórz skrypt, który zawiera schemat bazy danych](../data-tools/create-a-sql-database-by-using-a-script.md#CreateScript)

- [Tworzenie projektu bazy danych i importowanie schematu](../data-tools/create-a-sql-database-by-using-a-script.md#CreateProject)

- [Wdrażanie bazy danych](../data-tools/create-a-sql-database-by-using-a-script.md#DeployDatabase)

## <a name="prerequisites"></a>Wymagania wstępne
 Aby ukończyć ten przewodnik, musisz mieć zainstalowaną SQL Server Express LocalDB lub inną bazę danych SQL.

## <a name="CreateScript"></a>Utwórz skrypt, który zawiera schemat bazy danych

#### <a name="to-create-a-script-from-which-you-can-import-a-schema"></a>Aby utworzyć skrypt, za pomocą którego można zaimportować schemat

1. W [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] na pasku menu wybierz pozycję **plik**  > **Nowy** **plik** > .

     Pojawi się okno dialogowe **nowy plik** .

2. Na liście **Kategorie** wybierz pozycję **Ogólne**.

3. Na liście **Szablony** wybierz pozycję **plik SQL**, a następnie wybierz przycisk **Otwórz** .

     Zostanie otwarty edytor języka Transact-SQL.

4. Skopiuj następujący kod języka Transact-SQL, a następnie wklej go do edytora Transact-SQL.

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

5. Na pasku menu wybierz pozycję **plik**  > **Zapisz SqlQuery_1. SQL jako**.

     Zostanie wyświetlone okno dialogowe **Zapisywanie pliku jako** .

6. W polu **Nazwa pliku** wprowadź `SampleImportScript.sql`, zanotuj lokalizację, w której chcesz zapisać plik, a następnie wybierz przycisk **Zapisz** .

7. Na pasku menu wybierz pozycję **plik**  > **Zamknij rozwiązanie**.

     Następnie utwórz projekt bazy danych, a następnie zaimportuj schemat ze skryptu, który został utworzony.

## <a name="CreateProject"></a>Tworzenie projektu bazy danych i importowanie schematu

#### <a name="to-create-a-database-project"></a>Aby utworzyć projekt bazy danych

1. Na pasku menu wybierz pozycję **plik**  > **Nowy**  > **projekt**.

     Pojawi się okno dialogowe **Nowy projekt** .

2. W obszarze **zainstalowane**rozwiń węzeł **Szablony** , rozwiń węzeł **inne języki** , wybierz kategorię **SQL Server** , a następnie wybierz szablon **projektu SQL Server Database** .

    > [!NOTE]
    > Węzeł **inne języki** nie pojawia się we wszystkich instalacjach programu Visual Studio.

3. W polu **Nazwa** wprowadź `Small Database`.

4. Zaznacz pole wyboru **Utwórz katalog dla rozwiązania** , jeśli nie zostało jeszcze wybrane.

5. Wyczyść pole wyboru **Dodaj do kontroli źródła** , jeśli nie zostało jeszcze wyczyszczone, a następnie wybierz przycisk **OK** .

     Projekt bazy danych jest tworzony i pojawia się w **Eksplorator rozwiązań**.

     Następnie zaimportuj schemat bazy danych ze skryptu.

#### <a name="to-import-a-database-schema-from-a-script"></a>Aby zaimportować schemat bazy danych ze skryptu

1. Na pasku menu wybierz kolejno pozycje **projekt**  > **Importuj**  > **skrypt**.

2. Na stronie **powitalnej** Przejrzyj tekst, a następnie wybierz przycisk **dalej** .

3. Wybierz przycisk opcji **pojedynczy plik** , a następnie wybierz przycisk **Przeglądaj** .

     Zostanie wyświetlone okno dialogowe **Importuj skrypt SQL** .

4. Otwórz folder, w którym zapisano plik SampleImportScript. SQL, wybierz plik, a następnie wybierz przycisk **Otwórz** .

5. Wybierz przycisk **Zakończ** , aby zamknąć okno dialogowe **Importuj skrypt SQL** .

     Skrypt zostanie zaimportowany, a obiekty zdefiniowane przez skrypt są dodawane do projektu bazy danych.

6. Przejrzyj podsumowanie, a następnie kliknij przycisk **Zakończ** , aby zamknąć okno dialogowe **Importuj plik skryptu SQL** .

7. W **Eksplorator rozwiązań**rozwiń foldery sprzedaż, skrypty i zabezpieczenia projektu i sprawdź, czy zawierają one pliki. SQL.

8. W **Eksplorator obiektów SQL Server**Sprawdź, czy baza danych jest wyświetlana pod węzłem **projekty** .

     W tym momencie baza danych zawiera tylko obiekty systemowe, takie jak tabele i procedury składowane. Po wdrożeniu bazy danych będzie ona zawierać tabele użytkowników i procedury przechowywane zdefiniowane przez skrypty.

## <a name="DeployDatabase"></a>Wdrażanie bazy danych
 Po naciśnięciu klawisza **F5** należy wdrożyć (lub opublikować) bazę danych domyślnie w bazie danych LocalDB. Bazę danych można wdrożyć w innej lokalizacji, otwierając stronę właściwości projektu, wybierając kartę **debugowanie** , a następnie zmieniając parametry połączenia.

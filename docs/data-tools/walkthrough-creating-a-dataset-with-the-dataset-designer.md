---
title: Tworzenie zestawu danych z Projektant obiektów Dataset
description: W tym instruktażu Utwórz zestaw danych przy użyciu Projektant obiektów Dataset. Zapoznaj się z procesem tworzenia nowego projektu i dodawania do niego nowego elementu DataSet.
ms.custom: SEO-VS-2020
ms.date: 09/11/2017
ms.topic: conceptual
helpviewer_keywords:
- datasets [Visual Basic], walkthroughs
- XML schemas, creating datasets
- data [Visual Studio], Dataset Designer
- Dataset Designer, walkthroughs
- datasets [Visual Basic], creating
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: b1fe1d75673dc47f423cf398118230cd1530def0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866232"
---
# <a name="walkthrough-create-a-dataset-with-the-dataset-designer"></a>Przewodnik: Tworzenie zestawu danych za pomocą Projektant obiektów Dataset

W tym instruktażu utworzysz zestaw danych przy użyciu **Projektant obiektów DataSet**. Artykuł przeprowadzi Cię przez proces tworzenia nowego projektu i dodawania do niego nowego elementu **DataSet** . Dowiesz się, jak tworzyć tabele na podstawie tabel w bazie danych bez korzystania z kreatora.

## <a name="prerequisites"></a>Wymagania wstępne

W tym instruktażu jest stosowana SQL Server Express LocalDB i Przykładowa baza danych Northwind.

1. Jeśli nie masz SQL Server Express LocalDB, zainstaluj go na [stronie pobierania SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)lub za pośrednictwem **Instalator programu Visual Studio**. W Instalator programu Visual Studio, SQL Server Express LocalDB można zainstalować w ramach obciążenia **magazynu i przetwarzania danych** albo jako pojedynczy składnik.

2. Zainstaluj przykładową bazę danych Northwind, wykonując następujące kroki:

    1. W programie Visual Studio Otwórz okno **Eksplorator obiektów SQL Server** . (Eksplorator obiektów SQL Server jest instalowany jako część obciążenia **magazynu i przetwarzania danych** w Instalator programu Visual Studio). Rozwiń węzeł **SQL Server** . Kliknij prawym przyciskiem myszy wystąpienie LocalDB i wybierz pozycję **nowe zapytanie**.

       Zostanie otwarte okno edytora zapytań.

    2. Skopiuj [skrypt języka Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do Schowka. Ten skrypt T-SQL tworzy bazę danych Northwind od podstaw i wypełnia ją danymi.

    3. Wklej skrypt T-SQL do edytora zapytań, a następnie wybierz przycisk Execute ( **Wykonaj** ).

       Po krótkim czasie zapytanie kończy wykonywanie i zostanie utworzona baza danych Northwind.

## <a name="create-a-new-windows-forms-application-project"></a>Utwórz nowy projekt aplikacji Windows Forms

1. W programie Visual Studio w menu **plik** wybierz pozycję **Nowy**  >  **projekt**.

2. Rozwiń pozycję **Visual C#** lub **Visual Basic** w okienku po lewej stronie, a następnie wybierz pozycję **Windows Desktop**.

3. W środkowym okienku wybierz typ projektu **aplikacji Windows Forms** .

4. Nazwij projekt **DatasetDesignerWalkthrough**, a następnie wybierz przycisk **OK**.

     Program Visual Studio dodaje projekt do **Eksplorator rozwiązań** i wyświetla nowy formularz w projektancie.

## <a name="add-a-new-dataset-to-the-application"></a>Dodawanie nowego zestawu danych do aplikacji

1. W menu **projekt** wybierz polecenie **Dodaj nowy element**.

     Zostanie wyświetlone okno dialogowe **Dodawanie nowego elementu**.

2. W okienku po lewej stronie wybierz pozycję **dane**, a następnie wybierz pozycję **zestaw danych** w środkowym okienku.

3. Nazwij zestaw danych **NorthwindDataSet**, a następnie wybierz pozycję **Dodaj**.

     Program Visual Studio dodaje plik o nazwie **NorthwindDataSet. xsd** do projektu i otwiera go w **Projektant obiektów DataSet**.

## <a name="create-a-data-connection-in-server-explorer"></a>Tworzenie połączenia danych w Eksplorator serwera

1. W menu **Widok** kliknij **Eksplorator serwera**.

2. W **Eksplorator serwera** kliknij przycisk **Połącz z bazą danych** .

3. Utwórz połączenie z przykładową bazą danych Northwind.

## <a name="create-the-tables-in-the-dataset"></a>Tworzenie tabel w zestawie danych

W tej sekcji wyjaśniono, jak dodać tabele do zestawu danych.

### <a name="to-create-the-customers-table"></a>Aby utworzyć tabelę Customers

1. Rozwiń połączenie danych utworzone w **Eksplorator serwera**, a następnie rozwiń węzeł **tabele** .

2. Przeciągnij tabelę **Customers** z **Eksplorator serwera** na **Projektant obiektów DataSet**.

     Tabela danych **klientów** i **CustomersTableAdapter** są dodawane do zestawu danych.

### <a name="to-create-the-orders-table"></a>Aby utworzyć tabelę Orders

- Przeciągnij tabelę **Orders** z **Eksplorator serwera** na **Projektant obiektów DataSet**.

     Tabela dane **zamówienia** , **OrdersTableAdapter** i relacja danych między tabelami **Customers** i **Orders** są dodawane do zestawu danych.

### <a name="to-create-the-orderdetails-table"></a>Aby utworzyć tabelę OrderDetails

- Przeciągnij tabelę **szczegóły zamówienia** z **Eksplorator serwera** na **Projektant obiektów DataSet**.

     Tabela danych **Order Details** , **OrderDetailsTableAdapter** i relacja danych między tabelami **Orders** i **OrderDetails** są dodawane do zestawu danych.

## <a name="next-steps"></a>Następne kroki

- Zapisz zestaw danych.

- Wybierz pozycję elementy w oknie **źródła danych** i przeciągnij je na formularz. Aby uzyskać więcej informacji, zobacz [Powiązywanie formantów Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).

- Dodaj więcej zapytań do elementów TableAdapter.

- Dodaj logikę walidacji do zdarzeń <xref:System.Data.DataTable.ColumnChanging> lub <xref:System.Data.DataTable.RowChanging> tabel danych w zestawie danych. Aby uzyskać więcej informacji, zobacz [Weryfikowanie danych w zestawach DataSet](../data-tools/validate-data-in-datasets.md).

## <a name="see-also"></a>Zobacz też

- [Tworzenie i konfigurowanie zestawów danych w programie Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [Wiązanie kontrolek Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Wiązanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Sprawdzanie poprawności danych](../data-tools/validate-data-in-datasets.md)

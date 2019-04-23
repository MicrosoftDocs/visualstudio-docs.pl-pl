---
title: 'Przewodnik: Tworzenie zestawu danych w Projektancie obiektów Dataset'
ms.date: 09/11/2017
ms.topic: conceptual
helpviewer_keywords:
- datasets [Visual Basic], walkthroughs
- XML schemas, creating datasets
- data [Visual Studio], Dataset Designer
- Dataset Designer, walkthroughs
- datasets [Visual Basic], creating
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: f91c24885cc6817889671dd7a1a6e7e1686ce93f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60070528"
---
# <a name="walkthrough-create-a-dataset-with-the-dataset-designer"></a>Przewodnik: Tworzenie zestawu danych w Projektancie obiektów Dataset

W tym instruktażu utworzysz zestaw danych przy użyciu **Projektanta obiektów Dataset**. Artykuł przeprowadzi Cię przez proces tworzenia nowego projektu i dodawanie nowej **DataSet** elementu do niego. Dowiesz się, jak tworzyć tabele na podstawie tabel w bazie danych bez użycia kreatora.

## <a name="prerequisites"></a>Wymagania wstępne

Ten przewodnik korzysta z programu SQL Server Express LocalDB i bazie danych Northwind.

1. Jeśli nie masz programu SQL Server Express LocalDB, zainstaluj go z [stronę pobierania programu SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), lub za pomocą **Instalatora programu Visual Studio**. W Instalatorze programu Visual Studio, można zainstalować programu SQL Server Express LocalDB, jako część **przechowywanie i przetwarzanie danych** obciążenie, lub jako poszczególnych składników.

2. Instalowanie przykładowej bazy danych Northwind, wykonaj następujące czynności:

    1. W programie Visual Studio, otwórz **Eksplorator obiektów SQL Server** okna. (Eksplorator obiektów SQL Server jest instalowany jako część **przechowywanie i przetwarzanie danych** obciążenie w Instalatorze programu Visual Studio.) Rozwiń **programu SQL Server** węzła. Kliknij prawym przyciskiem myszy w ramach wystąpienia LocalDB, a następnie wybierz pozycję **nowe zapytanie**.

       Zostanie otwarte okno edytora zapytań.

    2. Kopiuj [skryptów języka Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do Schowka. Ten skrypt języka T-SQL tworzy bazę danych Northwind od podstaw i wypełnia ją z danymi.

    3. Wklej skrypt języka T-SQL do edytora zapytań, a następnie wybierz **Execute** przycisku.

       Po pewnym czasie zapytanie kończy wykonywanie i utworzeniu bazy danych Northwind.

## <a name="create-a-new-windows-forms-application-project"></a>Utwórz nowy projekt aplikacji Windows Forms

1. W programie Visual Studio na **pliku** menu, wybierz opcję **New** > **projektu**.

2. Rozwiń **Visual C#** lub **języka Visual Basic** w okienku po lewej stronie, a następnie zaznacz **pulpitu Windows**.

3. W środkowym okienku wybierz **Windows Forms App** typ projektu.

4. Nadaj projektowi nazwę **DatasetDesignerWalkthrough**, a następnie wybierz **OK**.

     Program Visual Studio dodaje projekt do **Eksploratora rozwiązań** i pojawi się nowy formularz w projektancie.

## <a name="add-a-new-dataset-to-the-application"></a>Dodaj nowy zestaw danych do aplikacji

1. Na **projektu** menu, wybierz opcję **Dodaj nowy element**.

     **Dodaj nowy element** pojawi się okno dialogowe.

2. W okienku po lewej stronie wybierz **danych**, a następnie wybierz **DataSet** w środkowym okienku.

3. Nazwij zestaw danych **NorthwindDataset**, a następnie wybierz **Dodaj**.

     Program Visual Studio dodaje plik o nazwie **NorthwindDataset.xsd** w projekcie i otwiera go w **Projektanta obiektów Dataset**.

## <a name="create-a-data-connection-in-server-explorer"></a>Tworzenie połączenia danych w Eksploratorze serwera

1. Na **widoku** menu, kliknij przycisk **Eksploratora serwera**.

2. W **Eksploratora serwera**, kliknij przycisk **Połącz z bazą danych** przycisku.

3. Utwórz połączenie z przykładową bazą danych Northwind.

## <a name="create-the-tables-in-the-dataset"></a>Tworzenie tabel w zestawie danych

W tej sekcji wyjaśniono, jak dodawać tabele do zestawu danych.

### <a name="to-create-the-customers-table"></a>Aby utworzyć tabelę Customers

1. Rozwiń połączenie danych utworzone w **Eksploratora serwera**, a następnie rozwiń węzeł **tabel** węzła.

2. Przeciągnij **klientów** tabeli **Eksploratora serwera** na **Projektanta obiektów Dataset**.

     A **klientów** tabelę danych i **CustomersTableAdapter** są dodawane do zestawu danych.

### <a name="to-create-the-orders-table"></a>Aby utworzyć tabelę Orders

- Przeciągnij **zamówienia** tabeli **Eksploratora serwera** na **Projektanta obiektów Dataset**.

     **Zamówienia** tabeli danych **OrdersTableAdapter**oraz relacje danych między **klientów** i **zamówienia** tabele są dodawane do zestaw danych.

### <a name="to-create-the-orderdetails-table"></a>Aby utworzyć tabelę OrderDetails

- Przeciągnij **Orderdetails** tabeli **Eksploratora serwera** na **Projektanta obiektów Dataset**.

     **Orderdetails** tabeli danych **OrderDetailsTableAdapter**oraz relacje danych między **zamówienia** i **OrderDetails** tabel zostaną dodane do zestawu danych.

## <a name="next-steps"></a>Następne kroki

- Zapisz zestaw danych.

- Zaznacz elementy w **źródeł danych** okna i przeciągnij je na formularzu. Aby uzyskać więcej informacji, zobacz [formanty powiązania formularzy Windows do danych w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).

- Dodaj więcej zapytań do elementów TableAdapter.

- Dodaj logikę walidacji do zdarzeń <xref:System.Data.DataTable.ColumnChanging> lub <xref:System.Data.DataTable.RowChanging> tabel danych w zestawie danych. Aby uzyskać więcej informacji, zobacz [sprawdzanie poprawności danych w zestawach danych](../data-tools/validate-data-in-datasets.md).

## <a name="see-also"></a>Zobacz także

- [Tworzenie i konfigurowanie zestawów danych w programie Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [Wiązanie kontrolek Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Wiązanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Sprawdzanie poprawności danych](../data-tools/validate-data-in-datasets.md)
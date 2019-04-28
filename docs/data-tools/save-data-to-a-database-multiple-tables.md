---
title: Zapisywanie danych w bazie danych (wiele tabel)
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- updating datasets, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], updating
ms.assetid: 7ebe03da-ce8c-4cbc-bac0-a2fde4ae4d07
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 9e4a30c3aa85969a4cbf712f2f4018c24169ff6d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62565904"
---
# <a name="save-data-to-a-database-multiple-tables"></a>Zapisywanie danych w bazie danych (wiele tabel)

Jedną z najbardziej typowych scenariuszy w tworzeniu aplikacji jest wyświetlenie danych z formularza w aplikacji Windows, edytować dane i wysyłać zaktualizowane dane w bazie danych. Ten poradnik tworzy formularz, który wyświetla dane z dwóch pokrewnych tabel i pokazuje, jak edytować rekordy i zapisać zmiany w bazie danych. W tym przykładzie użyto `Customers` i `Orders` tabel z przykładowej bazy danych Northwind.

Dane można zapisać w aplikacji w bazie danych, wywołując `Update` metody TableAdapter. Podczas przeciągania tabel z **źródeł danych** okna na formularzu, kod, który jest wymagany w celu zapisywania danych jest automatycznie dodawany. Dodatkowe tabele, które są dodawane do formularza wymaga ręcznego dodawania tego kodu. W tym instruktażu pokazano, jak dodać kod, aby zapisać aktualizacje z więcej niż jedną tabelą.

Zadania zilustrowane w tym przewodniku obejmują:

- Tworzenie i konfigurowanie źródła danych w aplikacji za pomocą [Kreatora konfiguracji źródła danych](../data-tools/media/data-source-configuration-wizard.png).

- Określa elementy w [okna źródeł danych](add-new-data-sources.md#data-sources-window). Aby uzyskać więcej informacji, zobacz [Ustawianie formantu do utworzenia podczas przeciągania z okna źródeł danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

- Tworzenie formantów powiązanych z danymi przez przeciąganie elementów z **źródeł danych** okna do formularza.

- Modyfikowanie kilku rekordów w każdej tabeli w zestawie danych.

- Modyfikowanie kodu wysyłać zaktualizowane dane w zestawie danych w bazie danych.

## <a name="prerequisites"></a>Wymagania wstępne

Ten przewodnik korzysta z programu SQL Server Express LocalDB i bazie danych Northwind.

1. Jeśli nie masz programu SQL Server Express LocalDB, zainstaluj go z [stronę pobierania programu SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), lub za pomocą **Instalatora programu Visual Studio**. W **Instalatora programu Visual Studio**, można zainstalować programu SQL Server Express LocalDB, jako część **przechowywanie i przetwarzanie danych** obciążenie, lub jako poszczególnych składników.

2. Instalowanie przykładowej bazy danych Northwind, wykonaj następujące czynności:

    1. W programie Visual Studio, otwórz **Eksplorator obiektów SQL Server** okna. (Eksplorator obiektów SQL Server jest instalowany jako część **przechowywanie i przetwarzanie danych** obciążenie w Instalatorze programu Visual Studio.) Rozwiń **programu SQL Server** węzła. Kliknij prawym przyciskiem myszy w ramach wystąpienia LocalDB, a następnie wybierz pozycję **nowe zapytanie**.

       Zostanie otwarte okno edytora zapytań.

    2. Kopiuj [skryptów języka Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do Schowka. Ten skrypt języka T-SQL tworzy bazę danych Northwind od podstaw i wypełnia ją z danymi.

    3. Wklej skrypt języka T-SQL do edytora zapytań, a następnie wybierz **Execute** przycisku.

       Po pewnym czasie odliczania zapytania i utworzeniu bazy danych Northwind.

## <a name="create-the-windows-forms-application"></a>Tworzenie aplikacji Windows Forms

Utwórz nową **Windows Forms App** projekt albo C# lub Visual Basic. Nadaj projektowi nazwę **UpdateMultipleTablesWalkthrough**.

## <a name="create-the-data-source"></a>Utwórz źródło danych

Spowoduje to utworzenie źródła danych z bazy danych Northwind przy użyciu **Kreatora konfiguracji źródła danych**. Musi mieć dostęp do przykładowej bazy danych Northwind do utworzenia połączenia. Aby uzyskać informacje dotyczące konfigurowania przykładowej bazy danych Northwind, zobacz [jak: Zainstalować przykładowe bazy danych](../data-tools/installing-database-systems-tools-and-samples.md).

1. Na **danych** menu, wybierz opcję **Pokaż źródła danych**.

   **Źródeł danych** zostanie otwarte okno.

2. W **źródeł danych** wybierz **Dodaj nowe źródło danych** można uruchomić **Kreatora konfiguracji źródła danych**.

3. Na **wybierz typ źródła danych** ekranu, wybierz opcję **bazy danych**, a następnie wybierz pozycję **dalej**.

4. Na **wybierz połączenie danych** ekranu, wykonaj jedną z następujących czynności:

    - Jeśli połączenie danych z przykładową bazą danych Northwind jest dostępne na liście rozwijanej, wybierz je.

         —lub—

    - Wybierz **nowe połączenie** otworzyć **Dodawanie/modyfikowanie połączenia** okno dialogowe.

5. Jeśli baza danych wymaga hasła, wybierz opcję dołączenia danych poufnych, a następnie wybierz **dalej**.

6. Na **Zapisz parametry połączenia do pliku konfiguracji aplikacji**, wybierz opcję **dalej**.

7. Na **wybierz obiekty bazy danych** ekranu, a następnie rozwiń **tabel** węzła.

8. Wybierz **klientów** i **zamówienia** tabel, a następnie wybierz **Zakończ**.

     **NorthwindDataSet** zostanie dodany do projektu, a tabele są wyświetlane w **źródeł danych** okna.

## <a name="set-the-controls-to-be-created"></a>Ustawienie kontroli ma zostać utworzony

W tym przewodniku dane w `Customers` tabela znajduje się w **szczegóły** układu, w którym dane są wyświetlane w poszczególnych formantów. Dane z `Orders` tabela znajduje się w **siatki** układ, który jest wyświetlany w <xref:System.Windows.Forms.DataGridView> kontroli.

### <a name="to-set-the-drop-type-for-the-items-in-the-data-sources-window"></a>Aby ustawić upuszczany typ elementów w oknie źródeł danych

1. W **źródeł danych** okna, rozwiń węzeł **klientów** węzła.

2. Na **klientów** węzeł **szczegóły** z listy kontroli, aby zmienić kontrolę nad **klientów** tabeli do poszczególnych formantów. Aby uzyskać więcej informacji, zobacz [Ustawianie formantu do utworzenia podczas przeciągania z okna źródeł danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

## <a name="create-the-data-bound-form"></a>Tworzenie formularza powiązanych z danymi

Można utworzyć formanty powiązane z danymi przez przeciąganie elementów z **źródeł danych** okna do formularza.

1. Przeciągnij główny **klientów** węzła z **źródeł danych** okna na **Form1**.

     Formanty powiązane z danymi z etykietami opisowymi są wyświetlane w formularzu, oraz pasek narzędzi (<xref:System.Windows.Forms.BindingNavigator>) do nawigowania między rekordami. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `CustomersTableAdapter`, <xref:System.Windows.Forms.BindingSource>, i <xref:System.Windows.Forms.BindingNavigator> są wyświetlane w zasobniku składnika.

2. Przeciągnij powiązane **zamówienia** węzła z **źródeł danych** okna na **Form1**.

    > [!NOTE]
    > Powiązane **zamówienia** węzeł znajduje się poniżej **faks** kolumny, a jest elementem podrzędnym **klientów** węzła.

     A <xref:System.Windows.Forms.DataGridView> kontroli i pasek narzędzi (<xref:System.Windows.Forms.BindingNavigator>) do nawigowania między rekordami wyświetlanymi w formularzu. `OrdersTableAdapter` i <xref:System.Windows.Forms.BindingSource> są wyświetlane w zasobniku składnika.

## <a name="add-code-to-update-the-database"></a>Dodaj kod, aby zaktualizować bazę danych

Zaktualizuj bazy danych, wywołując `Update` metody **klientów** i **zamówienia** adapterów TableAdapter. Domyślnie program obsługi zdarzeń dla **Zapisz** przycisk<xref:System.Windows.Forms.BindingNavigator> zostanie dodany do kodu formularza w celu wysyłania aktualizacji do bazy danych. Ta procedura modyfikuje kod, aby wysłać aktualizacje we właściwej kolejności. Pozwala to wyeliminować możliwość zgłaszania błędów więzów integralności. Kod implementuje również dodanymi komentarzami opakowując wywołania aktualizacji w bloku try-catch. Można zmodyfikować kod odpowiednio do potrzeb aplikacji.

> [!NOTE]
> Dla jasności ten przewodnik nie używa transakcji. Jeśli aktualizujesz, dwa lub więcej powiązanych tabel, obejmuje jednak logika aktualizacji w obrębie transakcji. Transakcja jest procesem, który gwarantuje, że wszystkie powiązane zmiany w bazie danych są pomyślnie, zanim wszelkie zmiany zostaną zatwierdzone. Aby uzyskać więcej informacji, zobacz [transakcje i współbieżność](/dotnet/framework/data/adonet/transactions-and-concurrency).

### <a name="to-add-update-logic-to-the-application"></a>Aby dodać logikę aktualizacji do aplikacji

1. Wybierz **Zapisz** znajdujący się na <xref:System.Windows.Forms.BindingNavigator>. Spowoduje to otwarcie edytora kodu, aby `bindingNavigatorSaveItem_Click` programu obsługi zdarzeń.

2. Zastąp kod w obsłudze zdarzeń, aby wywołać `Update` metody powiązanych elementów TableAdapter. Poniższy kod najpierw tworzy trzy tabele dane tymczasowe do przechowywania zaktualizowanych informacji dla każdego <xref:System.Data.DataRowState> (<xref:System.Data.DataRowState.Deleted>, <xref:System.Data.DataRowState.Added>, i <xref:System.Data.DataRowState.Modified>). Aktualizacje są uruchamiane w odpowiedniej kolejności. Kod powinien wyglądać następująco:

     [!code-vb[VbRaddataSaving#10](../data-tools/codesnippet/VisualBasic/save-data-to-a-database-multiple-tables_1.vb)]
     [!code-csharp[VbRaddataSaving#10](../data-tools/codesnippet/CSharp/save-data-to-a-database-multiple-tables_1.cs)]

## <a name="test-the-application"></a>Testowanie aplikacji

1. Naciśnij klawisz **F5**.

2. Należy wprowadzić pewne zmiany do danych z co najmniej jednego rekordu w każdej tabeli.

3. Wybierz ikonę **Zapisz**.

4. Sprawdź wartości w bazie danych, aby sprawdzić, czy zmiany zostały zapisane.

## <a name="see-also"></a>Zobacz także

- [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)
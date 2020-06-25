---
title: Zapisywanie danych w bazie danych (wiele tabel)
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- updating datasets, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], updating
ms.assetid: 7ebe03da-ce8c-4cbc-bac0-a2fde4ae4d07
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b512263cd5d0ca8c83b0ba6848fb16feca1a71f6
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85281646"
---
# <a name="save-data-to-a-database-multiple-tables"></a>Zapisywanie danych w bazie danych (wiele tabel)

Jednym z najczęstszych scenariuszy tworzenia aplikacji jest wyświetlanie danych w formularzu w aplikacji systemu Windows, edytowanie danych i wysyłanie zaktualizowanych danych z powrotem do bazy danych. Ten Instruktaż tworzy formularz, który wyświetla dane z dwóch powiązanych tabel i pokazuje, jak edytować rekordy i zapisywać zmiany z powrotem w bazie danych. Ten przykład używa `Customers` tabel i `Orders` z przykładowej bazy danych Northwind.

Dane w aplikacji można zapisywać z powrotem do bazy danych przez wywołanie `Update` metody TableAdapter. Gdy przeciągniesz tabele z okna **źródła danych** na formularz, zostanie automatycznie dodany kod wymagany do zapisania danych. Wszelkie dodatkowe tabele dodawane do formularza wymagają ręcznego dodania tego kodu. W tym instruktażu pokazano, jak dodać kod, aby zapisać aktualizacje z więcej niż jednej tabeli.

Zadania przedstawione w tym instruktażu obejmują:

- Tworzenie i Konfigurowanie źródła danych w aplikacji za pomocą [Kreatora konfiguracji źródła danych](../data-tools/media/data-source-configuration-wizard.png).

- Ustawianie kontrolek elementów w [oknie źródła danych](add-new-data-sources.md#data-sources-window). Aby uzyskać więcej informacji, zobacz [Ustawianie kontrolki do utworzenia podczas przeciągania z okna źródła danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

- Tworzenie kontrolek powiązanych z danymi przez przeciąganie elementów z okna **źródła danych** na formularz.

- Modyfikowanie kilku rekordów w każdej tabeli w zestawie danych.

- Modyfikowanie kodu w celu wysyłania zaktualizowanych danych z powrotem do bazy danych.

## <a name="prerequisites"></a>Wymagania wstępne

W tym instruktażu jest stosowana SQL Server Express LocalDB i Przykładowa baza danych Northwind.

1. Jeśli nie masz SQL Server Express LocalDB, zainstaluj go na [stronie pobierania SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)lub za pośrednictwem **Instalator programu Visual Studio**. W **Instalator programu Visual Studio**można zainstalować SQL Server Express LocalDB jako część obciążenia **magazynu danych i przetwarzania** lub jako pojedynczy składnik.

2. Zainstaluj przykładową bazę danych Northwind, wykonując następujące kroki:

    1. W programie Visual Studio Otwórz okno **Eksplorator obiektów SQL Server** . (Eksplorator obiektów SQL Server jest instalowany jako część obciążenia **magazynu i przetwarzania danych** w Instalator programu Visual Studio). Rozwiń węzeł **SQL Server** . Kliknij prawym przyciskiem myszy wystąpienie LocalDB i wybierz pozycję **nowe zapytanie**.

       Zostanie otwarte okno edytora zapytań.

    2. Skopiuj [skrypt języka Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do Schowka. Ten skrypt T-SQL tworzy bazę danych Northwind od podstaw i wypełnia ją danymi.

    3. Wklej skrypt T-SQL do edytora zapytań, a następnie wybierz przycisk Execute ( **Wykonaj** ).

       Po krótkim czasie zapytanie kończy działanie i zostanie utworzona baza danych Northwind.

## <a name="create-the-windows-forms-application"></a>Tworzenie aplikacji Windows Forms

Utwórz nowy projekt **aplikacji Windows Forms** dla języka C# lub Visual Basic. Nazwij projekt **UpdateMultipleTablesWalkthrough**.

## <a name="create-the-data-source"></a>Tworzenie źródła danych

Ten krok powoduje utworzenie źródła danych z bazy danych Northwind przy użyciu **Kreatora konfiguracji źródła danych**. Aby utworzyć połączenie, musisz mieć dostęp do przykładowej bazy danych Northwind. Aby uzyskać informacje o konfigurowaniu przykładowej bazy danych Northwind, zobacz [How to: Install Sample Bases](../data-tools/installing-database-systems-tools-and-samples.md).

1. W menu **dane** wybierz pozycję **Pokaż źródła danych**.

   Zostanie otwarte okno **źródła danych** .

2. W oknie **źródła danych** wybierz pozycję **Dodaj nowe źródło danych** , aby uruchomić **Kreatora konfiguracji źródła danych**.

3. Na ekranie **Wybierz typ źródła danych** wybierz pozycję **baza danych**, a następnie wybierz przycisk **dalej**.

4. Na ekranie **Wybierz połączenie danych** wykonaj jedną z następujących czynności:

    - Jeśli połączenie danych z przykładową bazą danych Northwind jest dostępne na liście rozwijanej, wybierz je.

         -lub-

    - Wybierz pozycję **nowe połączenie** , aby otworzyć okno dialogowe **Dodawanie/modyfikowanie połączenia** .

5. Jeśli baza danych wymaga hasła, wybierz opcję dołączenia danych poufnych, a następnie wybierz przycisk **dalej**.

6. Na stronie **Zapisz parametry połączenia do pliku konfiguracji aplikacji**wybierz pozycję **dalej**.

7. Na ekranie **Wybierz obiekty bazy danych** rozwiń węzeł **tabele** .

8. Wybierz tabele **Customers** i **Orders** , a następnie wybierz pozycję **Zakończ**.

     **NorthwindDataSet** jest dodawany do projektu, a tabele są wyświetlane w oknie **źródła danych** .

## <a name="set-the-controls-to-be-created"></a>Ustaw kontrolki do utworzenia

W tym instruktażu dane w `Customers` tabeli znajdują się w układzie **szczegółów** , w którym dane są wyświetlane w poszczególnych kontrolkach. Dane z `Orders` tabeli są w układzie **siatki** , który jest wyświetlany w <xref:System.Windows.Forms.DataGridView> kontrolce.

### <a name="to-set-the-drop-type-for-the-items-in-the-data-sources-window"></a>Aby ustawić typ upuszczenia dla elementów w oknie źródła danych

1. W oknie **źródła danych** rozwiń węzeł **klienci** .

2. W węźle **klienci** wybierz pozycję **szczegóły** z listy kontrolki, aby zmienić formant tabeli **Customers** na poszczególne kontrolki. Aby uzyskać więcej informacji, zobacz [Ustawianie kontrolki do utworzenia podczas przeciągania z okna źródła danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

## <a name="create-the-data-bound-form"></a>Tworzenie formularza powiązanego z danymi

Można utworzyć formanty powiązane z danymi, przeciągając elementy z okna **źródła danych** na formularz.

1. Przeciągnij główny węzeł **Customers** z okna **źródła danych** na **formularz Form1**.

     Formanty powiązane z danymi, które mają opisowe etykiety, są wyświetlane w formularzu wraz z paskiem narzędzi ( <xref:System.Windows.Forms.BindingNavigator> ) na potrzeby nawigowania po rekordach. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `CustomersTableAdapter` , <xref:System.Windows.Forms.BindingSource> i <xref:System.Windows.Forms.BindingNavigator> pojawia się na pasku składnika.

2. Przeciągnij węzeł powiązane **zamówienia** z okna **źródła danych** na **formularz Form1**.

    > [!NOTE]
    > Węzeł powiązane **zamówienia** znajduje się poniżej kolumny **faks** i jest węzłem podrzędnym węzła **Customers** .

     <xref:System.Windows.Forms.DataGridView>Kontrolka i pasek narzędzi ( <xref:System.Windows.Forms.BindingNavigator> ) na potrzeby nawigowania po rekordach pojawiają się w formularzu. `OrdersTableAdapter`I <xref:System.Windows.Forms.BindingSource> pojawia się na pasku składnika.

## <a name="add-code-to-update-the-database"></a>Dodawanie kodu w celu zaktualizowania bazy danych

Bazę danych można zaktualizować, wywołując `Update` metody TableAdapters **klientów** i **zamówień** . Domyślnie program obsługi zdarzeń dla przycisku **Zapisz** <xref:System.Windows.Forms.BindingNavigator> jest dodawany do kodu formularza w celu wysyłania aktualizacji do bazy danych programu. Ta procedura modyfikuje kod w celu wysłania aktualizacji w odpowiedniej kolejności. Eliminuje to możliwość podnoszenia błędów integralności referencyjnej. Kod implementuje również obsługę błędów przez zawijanie wywołania aktualizacji w bloku try-catch. Możesz zmodyfikować kod, aby spełniał wymagania aplikacji.

> [!NOTE]
> Dla jasności ten przewodnik nie korzysta z transakcji. Jeśli jednak aktualizujesz dwie lub więcej powiązanych tabel, Uwzględnij całą logikę aktualizacji w ramach transakcji. Transakcja to proces, który gwarantuje, że wszystkie powiązane zmiany w bazie danych zakończą się pomyślnie przed zatwierdzeniem jakichkolwiek zmian. Aby uzyskać więcej informacji, zobacz [transakcje i współbieżność](/dotnet/framework/data/adonet/transactions-and-concurrency).

### <a name="to-add-update-logic-to-the-application"></a>Aby dodać logikę aktualizacji do aplikacji

1. Wybierz przycisk **Zapisz** na stronie <xref:System.Windows.Forms.BindingNavigator> . Spowoduje to otwarcie edytora kodu w programie `bindingNavigatorSaveItem_Click` obsługi zdarzeń.

2. Zastąp kod w programie obsługi zdarzeń, aby wywołać `Update` metody powiązanej TableAdapters. Poniższy kod najpierw tworzy trzy tymczasowe tabele danych do przechowywania zaktualizowanych informacji dla każdego <xref:System.Data.DataRowState> ( <xref:System.Data.DataRowState.Deleted> , <xref:System.Data.DataRowState.Added> i <xref:System.Data.DataRowState.Modified> ). Aktualizacje są wykonywane w odpowiedniej kolejności. Kod powinien wyglądać następująco:

     [!code-vb[VbRaddataSaving#10](../data-tools/codesnippet/VisualBasic/save-data-to-a-database-multiple-tables_1.vb)]
     [!code-csharp[VbRaddataSaving#10](../data-tools/codesnippet/CSharp/save-data-to-a-database-multiple-tables_1.cs)]

## <a name="test-the-application"></a>Testowanie aplikacji

1. Naciśnij klawisz **F5**.

2. Wprowadź pewne zmiany w danych co najmniej jednego rekordu w każdej tabeli.

3. Wybierz ikonę **Zapisz**.

4. Sprawdź wartości w bazie danych, aby sprawdzić, czy zmiany zostały zapisane.

## <a name="see-also"></a>Zobacz też

- [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)

---
title: Dodawanie walidacji do n-warstwowego zestawu danych
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, validating
- validation [Visual Basic], n-tier data applications
- validating n-tier data applications
ms.assetid: 34ce4db6-09bb-4b46-b435-b2514aac52d3
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 91dbe04c85491a38a221edfb064702085136780f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85283024"
---
# <a name="add-validation-to-an-n-tier-dataset"></a>Dodawanie walidacji do n-warstwowego zestawu danych
Dodawanie walidacji do zestawu danych, który jest podzielony na rozwiązanie n-warstwowe, jest zasadniczo takie samo jak dodanie walidacji do pojedynczego pliku zestawu danych (zestawu danych w jednym projekcie). Sugerowana lokalizacja do wykonywania walidacji danych znajduje się w <xref:System.Data.DataTable.ColumnChanging> zdarzeniach i/lub <xref:System.Data.DataTable.RowChanging> tabeli danych.

Zestaw danych udostępnia funkcje do tworzenia klas częściowych, do których można dodać kod użytkownika do zdarzeń i zmian wierszy w tabelach danych w danych. Aby uzyskać więcej informacji na temat dodawania kodu do zestawu danych w rozwiązaniu n-warstwowym, zobacz [Dodawanie kodu do zestawów DataSet w aplikacjach n-warstwowych](../data-tools/add-code-to-datasets-in-n-tier-applications.md)i [Dodawanie kodu do TableAdapters w aplikacjach n-warstwowych](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md). Aby uzyskać więcej informacji na temat klas częściowych, zobacz [How to: Split a class in klasy częściowej (Projektant klas)](../ide/class-designer/how-to-split-a-class-into-partial-classes.md) lub [częściowe klasy i metody](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).

> [!NOTE]
> Gdy oddzielasz zestawy danych z TableAdapters (ustawiając właściwość **projektu DataSet** ), istniejące częściowe klasy zestawu danych w projekcie nie będą automatycznie przenoszone. Istniejące częściowe klasy DataSet muszą być przenoszone ręcznie do projektu DataSet.

> [!NOTE]
> Projektant zestawu danych nie tworzy automatycznie obsługi zdarzeń w języku C# dla <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.RowChanging> zdarzeń i. Musisz ręcznie utworzyć procedurę obsługi zdarzeń i podłączyć procedurę obsługi zdarzeń do podstawowego zdarzenia. W poniższych procedurach opisano sposób tworzenia wymaganych programów obsługi zdarzeń zarówno w Visual Basic, jak i C#.

## <a name="validate-changes-to-individual-columns"></a>Sprawdzanie poprawności zmian w poszczególnych kolumnach
Sprawdzanie poprawności wartości w poszczególnych kolumnach przez obsługę <xref:System.Data.DataTable.ColumnChanging> zdarzenia. <xref:System.Data.DataTable.ColumnChanging>Zdarzenie jest zgłaszane, gdy wartość w kolumnie zostanie zmodyfikowana. Utwórz procedurę obsługi zdarzeń dla <xref:System.Data.DataTable.ColumnChanging> zdarzenia przez dwukrotne kliknięcie odpowiedniej kolumny w **Projektant obiektów DataSet**.

Po raz pierwszy po dwukrotnym kliknięciu kolumny, Projektant generuje procedurę obsługi zdarzeń dla <xref:System.Data.DataTable.ColumnChanging> zdarzenia. `If...Then`Utworzona zostanie również instrukcja, która sprawdza określoną kolumnę. Na przykład poniższy kod jest generowany po dwukrotnym kliknięciu kolumny **DataDostawy** w tabeli Orders Northwind:

```vb
Private Sub OrdersDataTable_ColumnChanging(ByVal sender As System.Object, ByVal e As System.Data.DataColumnChangeEventArgs) Handles Me.ColumnChanging
    If (e.Column.ColumnName = Me.RequiredDateColumn.ColumnName) Then
        ' Add validation code here.
    End If
End Sub
```

> [!NOTE]
> W projektach C# Projektant obiektów Dataset tworzy tylko klasy częściowe dla zestawu danych i poszczególnych tabel w zestawie danych. Projektant obiektów Dataset nie tworzy automatycznie obsługi zdarzeń dla <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.RowChanging> zdarzeń i w języku C#, podobnie jak w Visual Basic. W projektach C# trzeba ręcznie skonstruować metodę, aby obsłużyć zdarzenie i podłączyć metodę do podstawowego zdarzenia. Poniższa procedura zawiera opis czynności, które należy wykonać w celu utworzenia wymaganych programów obsługi zdarzeń zarówno w Visual Basic, jak i C#.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-add-validation-during-changes-to-individual-column-values"></a>Aby dodać sprawdzanie poprawności podczas zmiany wartości poszczególnych kolumn

1. Otwórz zestaw danych, klikając dwukrotnie plik *XSD* w **Eksplorator rozwiązań**. Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie zestawu danych w Projektant obiektów DataSet](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Kliknij dwukrotnie kolumnę, którą chcesz zweryfikować. Ta akcja powoduje utworzenie <xref:System.Data.DataTable.ColumnChanging> programu obsługi zdarzeń.

    > [!NOTE]
    > Projektant obiektów Dataset nie tworzy automatycznie zdarzenia obsługi dla zdarzenia języka C#. Kod, który jest niezbędny do obsługi zdarzenia w języku C#, jest uwzględniony w następnej sekcji. `SampleColumnChangingEvent` jest tworzony, a następnie podłączany do <xref:System.Data.DataTable.ColumnChanging> zdarzenia w <xref:System.Data.DataTable.EndInit%2A> metodzie.

3. Dodaj kod, aby sprawdzić, czy `e.ProposedValue` zawiera dane, które spełniają wymagania aplikacji. Jeśli proponowana wartość jest nieakceptowalna, ustaw kolumnę, aby wskazać, że zawiera błąd.

     Poniższy przykład kodu sprawdza, czy kolumna **ilość** zawiera wartość większą od 0. Jeśli **ilość** jest mniejsza lub równa 0, kolumna jest ustawiona na błąd. `Else`Klauzula czyści błąd, jeśli **ilość** jest większa niż 0. Kod w obsłudze zdarzeń zmiany kolumny powinien wyglądać następująco:

    ```vb
    If (e.Column.ColumnName = Me.QuantityColumn.ColumnName) Then
        If CType(e.ProposedValue, Short) <= 0 Then
            e.Row.SetColumnError(e.Column, "Quantity must be greater than 0")
        Else
            e.Row.SetColumnError(e.Column, "")
        End If
    End If
    ```

    ```csharp
    // Add this code to the DataTable partial class.

    public override void EndInit()
    {
        base.EndInit();
        // Hook up the ColumnChanging event
        // to call the SampleColumnChangingEvent method.
        ColumnChanging += SampleColumnChangingEvent;
    }

    public void SampleColumnChangingEvent(object sender, System.Data.DataColumnChangeEventArgs e)
    {
        if (e.Column.ColumnName == QuantityColumn.ColumnName)
        {
            if ((short)e.ProposedValue <= 0)
            {
                e.Row.SetColumnError("Quantity", "Quantity must be greater than 0");
            }
            else
            {
                e.Row.SetColumnError("Quantity", "");
            }
        }
    }
    ```

## <a name="validate-changes-to-whole-rows"></a>Weryfikuj zmiany do całych wierszy
Sprawdzanie poprawności wartości w pełnych wierszach przez obsługę <xref:System.Data.DataTable.RowChanging> zdarzenia. <xref:System.Data.DataTable.RowChanging>Zdarzenie jest zgłaszane, gdy wartości we wszystkich kolumnach zostaną zatwierdzone. Należy sprawdzić poprawność w <xref:System.Data.DataTable.RowChanging> zdarzeniu, gdy wartość w jednej kolumnie opiera się na wartości w innej kolumnie. Rozważmy na przykład DataZamówienia i DataDostawy w tabeli Orders na platformie Northwind.

Podczas wprowadzania zamówień Walidacja sprawdza, czy zamówienie nie jest wprowadzane z elementem dostawy, który znajduje się w dniu lub przed DataZamówienia. W tym przykładzie wartości kolumn DataDostawy i DataZamówienia muszą być porównane, więc sprawdzenie poprawności pojedynczej zmiany kolumny nie ma sensu.

Utwórz procedurę obsługi zdarzeń dla <xref:System.Data.DataTable.RowChanging> zdarzenia przez dwukrotne kliknięcie nazwy tabeli na pasku tytułu tabeli na **Projektant obiektów DataSet**.

#### <a name="to-add-validation-during-changes-to-whole-rows"></a>Aby dodać sprawdzanie poprawności podczas zmiany do całych wierszy

1. Otwórz zestaw danych, klikając dwukrotnie plik *XSD* w **Eksplorator rozwiązań**. Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie zestawu danych w Projektant obiektów DataSet](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Kliknij dwukrotnie pasek tytułu tabeli danych w projektancie.

     Klasa częściowa jest tworzona z `RowChanging` obsługą zdarzeń i otwiera się w edytorze kodu.

    > [!NOTE]
    > Projektant obiektów Dataset nie tworzy automatycznie obsługi zdarzeń dla <xref:System.Data.DataTable.RowChanging> zdarzenia w projektach C#. Musisz utworzyć metodę, aby obsłużyć <xref:System.Data.DataTable.RowChanging> zdarzenie i uruchomić kod, a następnie podłączyć zdarzenie do metody inicjacji tabeli.

3. Dodaj kod użytkownika wewnątrz deklaracji klasy częściowej.

4. Poniższy kod pokazuje, gdzie dodać kod użytkownika do walidacji podczas <xref:System.Data.DataTable.RowChanging> zdarzenia. Przykład C# zawiera również kod, aby podłączyć metodę obsługi zdarzeń do `OrdersRowChanging` zdarzenia.

    ```vb
    Partial Class OrdersDataTable
        Private Sub OrdersDataTable_OrdersRowChanging(ByVal sender As System.Object, ByVal e As OrdersRowChangeEvent) Handles Me.OrdersRowChanging
            ' Add logic to validate columns here.
            If e.Row.RequiredDate <= e.Row.OrderDate Then
                ' Set the RowError if validation fails.
                e.Row.RowError = "Required Date cannot be on or before the OrderDate"
            Else
                ' Clear the RowError when validation passes.
                e.Row.RowError = ""
            End If
        End Sub
    End Class
    ```

    ```csharp
    partial class OrdersDataTable
    {
        public override void EndInit()
        {
            base.EndInit();
            // Hook up the event to the
            // RowChangingEvent method.
            OrdersRowChanging += RowChangingEvent;
        }

        public void RowChangingEvent(object sender, OrdersRowChangeEvent e)
        {
            // Perform the validation logic.
            if (e.Row.RequiredDate <= e.Row.OrderDate)
            {
                // Set the row to an error when validation fails.
                e.Row.RowError = "Required Date cannot be on or before the OrderDate";
            }
            else
            {
                // Clear the RowError if validation passes.
                e.Row.RowError = "";
            }
        }
    }
    ```

## <a name="see-also"></a>Zobacz też

- [N-warstwowe aplikacje dotyczące danych — omówienie](../data-tools/n-tier-data-applications-overview.md)
- [Przewodnik: Tworzenie wielowarstwowej aplikacji danych](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Weryfikowanie danych w zestawach danych](../data-tools/validate-data-in-datasets.md)

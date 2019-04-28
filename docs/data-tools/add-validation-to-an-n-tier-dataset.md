---
title: Dodawanie walidacji do n-warstwowego zestawu danych
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, validating
- validation [Visual Basic], n-tier data applications
- validating n-tier data applications
ms.assetid: 34ce4db6-09bb-4b46-b435-b2514aac52d3
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 4fdeef3a21407b4473ed412019e936d7b30389c5
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63402879"
---
# <a name="add-validation-to-an-n-tier-dataset"></a>Dodawanie walidacji do n-warstwowego zestawu danych
Dodawanie walidacji do zestawu danych, który jest podzielony na rozwiązanie n warstwowa zasadniczo jest taka sama, jak dodawanie sprawdzania poprawności do pojedynczego pliku zestawu danych (zestawu danych w jednym projekcie). Proponowana lokalizacja na sprawdzenie poprawności danych jest w trakcie <xref:System.Data.DataTable.ColumnChanging> i/lub <xref:System.Data.DataTable.RowChanging> zdarzenia tabeli danych.

 Zestaw danych zawiera funkcje do tworzenia klas częściowych, do których można dodać kod użytkownika do zmiany kolumny i wiersza zdarzeń tabel danych w zestawie danych. Aby uzyskać więcej informacji na temat dodawania kodu zestawu danych w rozwiązaniu wielowarstwowym, zobacz [Dodawanie kodu do zestawów danych w aplikacjach n warstwowa](../data-tools/add-code-to-datasets-in-n-tier-applications.md), i [Dodawanie kodu do TableAdapters w aplikacjach n warstwowych](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md). Aby uzyskać więcej informacji na temat częściowych klas, zobacz [jak: Podział klasy na klasy częściowe (Projektant klas)](../ide/class-designer/how-to-split-a-class-into-partial-classes.md) lub [klasy częściowe i metody](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).

> [!NOTE]
> Kiedy oddzielisz zestawy danych z TableAdapters (przez ustawienie **projektu DataSet** właściwości), istniejące częściowe klasy zestawu danych w projekcie nie będą przenoszone automatycznie. Istniejące klasy częściowego zestawu danych należy przenieść ręcznie do projektu zestawu danych.

> [!NOTE]
> Projektant zestawu danych nie tworzy automatycznie obsługi zdarzeń w języku C# dla <xref:System.Data.DataTable.ColumnChanging> i <xref:System.Data.DataTable.RowChanging> zdarzenia. Należy ręcznie utworzyć program obsługi zdarzenia i podpiąć procedurę obsługi zdarzeń do zdarzenia bazowego. W poniższych procedurach opisano sposób tworzenia procedury obsługi zdarzeń wymagane zarówno w Visual Basic i C#.

## <a name="validate-changes-to-individual-columns"></a>Sprawdzanie poprawności zmian do poszczególnych kolumn
 Sprawdź poprawność wartości w poszczególnych kolumnach obsługi <xref:System.Data.DataTable.ColumnChanging> zdarzeń. <xref:System.Data.DataTable.ColumnChanging> Zdarzenie jest wywoływane, gdy wartość w kolumnie jest modyfikowana. Utwórz procedurę obsługi zdarzeń dla <xref:System.Data.DataTable.ColumnChanging> zdarzeń, klikając dwukrotnie odpowiednią kolumnę **Projektanta obiektów Dataset**.

 Kliknij dwukrotnie kolumnę, po raz pierwszy projektant generuje moduł obsługi zdarzenia <xref:System.Data.DataTable.ColumnChanging> zdarzeń. `If...Then` Tworzona jest również instrukcja sprawdzająca określone kolumny. Na przykład, poniższy kod jest generowany po dwukrotnym kliknięciu **RequiredDate** kolumny w tabeli Northwind Orders:

```vb
Private Sub OrdersDataTable_ColumnChanging(ByVal sender As System.Object, ByVal e As System.Data.DataColumnChangeEventArgs) Handles Me.ColumnChanging
    If (e.Column.ColumnName = Me.RequiredDateColumn.ColumnName) Then
        ' Add validation code here.
    End If
End Sub
```

> [!NOTE]
> W projektach C# Projektant obiektów Dataset tworzy tylko częściowe klasy dla zestawu danych i poszczególnych tabel w zestawie danych. Projektant zestawu danych nie tworzy automatycznie obsługi zdarzeń dla <xref:System.Data.DataTable.ColumnChanging> i <xref:System.Data.DataTable.RowChanging> zdarzeń w języku C# tak jak to robi w języku Visual Basic. W projektach C# musisz ręcznie utworzyć metodę obsługi zdarzenia i podpiąć metodę do zdarzenia bazowego. Poniższa procedura zawiera kroki, aby utworzyć procedury obsługi zdarzeń wymagane zarówno w Visual Basic i C#.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-add-validation-during-changes-to-individual-column-values"></a>Aby dodać sprawdzanie poprawności podczas zmiany wartości poszczególnych kolumn

1. Otwórz zestaw danych, klikając dwukrotnie *XSD* w pliku **Eksploratora rozwiązań**. Aby uzyskać więcej informacji, zobacz [instruktażu: Tworzenie zestawu danych w Projektancie obiektów Dataset](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Kliknij dwukrotnie kolumnę, którą chcesz zweryfikować. Ta akcja powoduje utworzenie <xref:System.Data.DataTable.ColumnChanging> programu obsługi zdarzeń.

    > [!NOTE]
    > Projektant zestawu danych nie tworzy automatycznie zdarzenia obsługi dla zdarzenia języka C#. Kod, który jest niezbędny do obsługi zdarzeń w języku C# znajduje się w następnej sekcji. `SampleColumnChangingEvent` jest tworzony i następnie podłączone do <xref:System.Data.DataTable.ColumnChanging> zdarzenia w <xref:System.Data.DataTable.EndInit%2A> metody.

3. Dodaj kod, aby sprawdzić, czy `e.ProposedValue` zawiera dane, które spełniają wymagania aplikacji. Jeżeli proponowana wartość jest nieakceptowana, należy ustawić kolumny, aby wskazać, że zawiera błąd.

     Poniższy przykład kodu sprawdza, czy **ilość** kolumna zawiera wartość większą niż 0. Jeśli **ilość** jest mniejszy niż lub równy 0, kolumnę ustawiono jako błąd. `Else` Klauzula czyści ten błąd, jeśli **ilość** jest większa niż 0. Kod w obsłudze zdarzeń zmieniającej się kolumny powinna wyglądać w następujący sposób:

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

## <a name="validate-changes-to-whole-rows"></a>Sprawdzanie poprawności zmiany całych wierszy
 Sprawdź wartości we wszystkich wierszach obsługując <xref:System.Data.DataTable.RowChanging> zdarzeń. <xref:System.Data.DataTable.RowChanging> Zdarzenie jest wywoływane, gdy wartości we wszystkich kolumnach są zatwierdzone. Należy go zweryfikować w <xref:System.Data.DataTable.RowChanging> zdarzenie, kiedy wartość w jednej kolumnie opiera się na wartości w innej kolumnie. Rozważmy na przykład OrderDate i RequiredDate w tabeli zamówienia w bazie danych Northwind.

 Po wprowadzeniu zamówień, sprawdzania poprawności upewnia się, że kolejność nie jest wprowadzone z DataDostawy, który jest w lub przed DataZamówienia. W tym przykładzie wartości dla kolumn RequiredDate i OrderDate muszą być porównane, więc sprawdzanie poprawności zmiany poszczególnych kolumn nie ma sensu.

 Utwórz procedurę obsługi zdarzeń dla <xref:System.Data.DataTable.RowChanging> zdarzeń, klikając dwukrotnie nazwę tabeli, na pasku tytułu tabeli **Projektanta obiektów Dataset**.

#### <a name="to-add-validation-during-changes-to-whole-rows"></a>Aby dodać sprawdzanie poprawności podczas zmiany do całych wierszy

1. Otwórz zestaw danych, klikając dwukrotnie *XSD* w pliku **Eksploratora rozwiązań**. Aby uzyskać więcej informacji, zobacz [instruktażu: Tworzenie zestawu danych w Projektancie obiektów Dataset](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Kliknij dwukrotnie pasek tytułu tabeli danych w projektancie.

     Częściowa klasa jest tworzona przy użyciu `RowChanging` program obsługi zdarzeń i zostanie otwarty w edytorze kodu.

    > [!NOTE]
    > Projektant zestawu danych nie tworzy automatycznie zdarzenia obsługi dla <xref:System.Data.DataTable.RowChanging> zdarzenia w projektach C#. Należy utworzyć metody, aby obsłużyć <xref:System.Data.DataTable.RowChanging> zdarzeń i wykonywania kodu, następnie podpiąć zdarzenie w metodzie inicjalizacji tabeli.

3. Dodaj kod użytkownika wewnątrz deklaracji klasy częściowej.

4. Poniższy kod przedstawia gdzie dodać kod użytkownika do sprawdzania poprawności podczas <xref:System.Data.DataTable.RowChanging> zdarzeń. Przykład C# zawiera również kod do metody obsługi zdarzeń podłączać `OrdersRowChanging` zdarzeń.

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

## <a name="see-also"></a>Zobacz także

- [Omówienie aplikacji N-warstwowa danych](../data-tools/n-tier-data-applications-overview.md)
- [Przewodnik: Tworzenie aplikacji N-warstwowa danych](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Weryfikowanie danych w zestawach danych](../data-tools/validate-data-in-datasets.md)
---
title: Dodawanie walidacji do n-warstwowego zestawu danych | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- n-tier applications, validating
- validation [Visual Basic], n-tier data applications
- validating n-tier data applications
ms.assetid: 34ce4db6-09bb-4b46-b435-b2514aac52d3
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b03f1e85140d62d84ae7c706a9bfee6a7c515abb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72673052"
---
# <a name="add-validation-to-an-n-tier-dataset"></a>Dodawanie walidacji do n-warstwowego zestawu danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dodawanie walidacji do zestawu danych, który jest podzielony na rozwiązanie n-warstwowe, jest zasadniczo takie samo jak dodanie walidacji do pojedynczego pliku zestawu danych (zestawu danych w jednym projekcie). Sugerowana lokalizacja do wykonywania walidacji danych jest w trakcie <xref:System.Data.DataTable.ColumnChanging> i/lub <xref:System.Data.DataTable.RowChanging> zdarzeń tabeli danych.

Projektant zestawu danych udostępnia funkcje do tworzenia klas częściowych, do których można dodać kod użytkownika do zdarzeń w postaci kolumn i zmian wierszy tabel danych w zestawie danych. Aby uzyskać więcej informacji na temat dodawania kodu do zestawu danych w rozwiązaniu n-warstwowym, zobacz [Dodawanie kodu do zestawów DataSet w aplikacjach n-warstwowych](../data-tools/add-code-to-datasets-in-n-tier-applications.md)i [Dodawanie kodu do TableAdapters w aplikacjach n-warstwowych](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md). Aby uzyskać więcej informacji na temat klas częściowych, zobacz [How to: Split a class in klasy częściowej (Projektant klas)](../ide/how-to-split-a-class-into-partial-classes-class-designer.md) lub [częściowe klasy i metody](https://msdn.microsoft.com/library/804cecb7-62db-4f97-a99f-60975bd59fa1).

> [!NOTE]
> Gdy oddzielasz zestawy danych z TableAdapters (ustawiając właściwość **projektu DataSet** ), istniejące częściowe klasy zestawu danych w projekcie nie będą automatycznie przenoszone. Istniejące klasy częściowe zestawu danych muszą być przenoszone ręcznie do projektu DataSet.

> [!NOTE]
> Projektant obiektów Dataset nie tworzy automatycznie programów obsługi zdarzeń w C# przypadku zdarzeń <xref:System.Data.DataTable.ColumnChanging> i <xref:System.Data.DataTable.RowChanging>. Musisz ręcznie utworzyć procedurę obsługi zdarzeń i podłączyć procedurę obsługi zdarzeń do podstawowego zdarzenia. W poniższych procedurach opisano sposób tworzenia wymaganych programów obsługi zdarzeń zarówno w Visual Basic, jak C#i.

## <a name="validatechanges-to-individual-columns"></a>ValidateChanges do poszczególnych kolumn
 Sprawdź poprawność wartości w poszczególnych kolumnach, obsługując zdarzenie <xref:System.Data.DataTable.ColumnChanging>. Zdarzenie <xref:System.Data.DataTable.ColumnChanging> jest zgłaszane, gdy wartość w kolumnie zostanie zmodyfikowana. Utwórz procedurę obsługi zdarzeń dla zdarzenia <xref:System.Data.DataTable.ColumnChanging> przez dwukrotne kliknięcie odpowiedniej kolumny w zestawie danych.

 Po raz pierwszy po dwukrotnym kliknięciu kolumny Projektant generuje procedurę obsługi zdarzeń dla zdarzenia <xref:System.Data.DataTable.ColumnChanging>. Utworzona zostanie również instrukcja `If…Then`, która sprawdza określoną kolumnę. Na przykład poniższy kod jest generowany po dwukrotnym kliknięciu kolumny DataDostawy w tabeli Orders Northwind:

```vb
Private Sub OrdersDataTable_ColumnChanging(ByVal sender As System.Object, ByVal e As System.Data.DataColumnChangeEventArgs) Handles Me.ColumnChanging
    If (e.Column.ColumnName = Me.RequiredDateColumn.ColumnName) Then
        ' Add validation code here.
    End If
End Sub
```

> [!NOTE]
> W C# projektach Projektant obiektów DataSet tworzy tylko klasy częściowe dla zestawu danych i poszczególnych tabel w zestawie danych. Projektant obiektów Dataset nie tworzy automatycznie obsługi zdarzeń dla <xref:System.Data.DataTable.ColumnChanging> i <xref:System.Data.DataTable.RowChanging> zdarzeń, C# tak jak w Visual Basic. W C# projektach należy ręcznie skonstruować metodę, aby obsłużyć zdarzenie i podłączyć metodę do zdarzenia bazowego. Poniższa procedura zawiera opis czynności, które należy wykonać w celu utworzenia wymaganych programów obsługi zdarzeń C#zarówno w Visual Basic, jak i.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-add-validation-during-changes-to-individual-column-values"></a>Aby dodać sprawdzanie poprawności podczas zmiany wartości poszczególnych kolumn

1. Otwórz zestaw danych w projektancie, klikając dwukrotnie plik **XSD** w **Eksplorator rozwiązań**. Aby uzyskać więcej informacji, zobacz [jak: otwieranie zestawu danych w Projektant obiektów DataSet](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).

2. Kliknij dwukrotnie kolumnę, którą chcesz zweryfikować. Ta akcja powoduje utworzenie programu obsługi zdarzeń <xref:System.Data.DataTable.ColumnChanging>.

    > [!NOTE]
    > Projektant obiektów Dataset nie tworzy automatycznie zdarzenia obsługi dla C# zdarzenia. Kod, który jest niezbędny do obsłużenia zdarzenia w programie C# , znajduje się w następnej sekcji. `SampleColumnChangingEvent` jest tworzony, a następnie podłączany do <xref:System.Data.DataTable.ColumnChanging> zdarzenia w metodzie <xref:System.Data.DataTable.EndInit%2A>.

3. Dodaj kod, aby sprawdzić, czy `e.ProposedValue` zawiera dane, które spełniają wymagania aplikacji. Jeśli proponowana wartość jest nieakceptowalna, ustaw kolumnę, aby wskazać, że zawiera błąd.

     Poniższy przykład kodu sprawdza, czy kolumna **ilość** zawiera więcej niż 0. Jeśli **ilość** jest mniejsza lub równa 0, kolumna jest ustawiona na błąd. Klauzula `Else` czyści błąd, jeśli **ilość** jest większa niż 0. Kod w obsłudze zdarzeń zmiany kolumny powinien wyglądać następująco:

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
    // C#
    // Add this code to the DataTable
    // partial class.

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

## <a name="validatechanges-to-whole-rows"></a>ValidateChanges do całych wierszy
 Sprawdź poprawność wartości w pełnych wierszach przez obsługę zdarzenia <xref:System.Data.DataTable.RowChanging>. Zdarzenie <xref:System.Data.DataTable.RowChanging> jest zgłaszane, gdy wartości we wszystkich kolumnach zostaną zatwierdzone. Należy sprawdzić poprawność w zdarzeniu <xref:System.Data.DataTable.RowChanging>, gdy wartość w jednej kolumnie opiera się na wartości w innej kolumnie. Rozważmy na przykład DataZamówienia i DataDostawy w tabeli Orders na platformie Northwind.

 Podczas wprowadzania zamówień Walidacja sprawdza, czy zamówienie nie jest wprowadzane z elementem dostawy, który znajduje się w dniu lub przed DataZamówienia. W tym przykładzie wartości kolumn DataDostawy i DataZamówienia muszą być porównane, więc sprawdzenie poprawności pojedynczej zmiany kolumny nie ma sensu.

 Utwórz procedurę obsługi zdarzeń dla zdarzenia <xref:System.Data.DataTable.RowChanging>, klikając dwukrotnie nazwę tabeli na pasku tytułu tabeli.

#### <a name="to-add-validation-during-changes-to-whole-rows"></a>Aby dodać sprawdzanie poprawności podczas zmiany do całych wierszy

1. Otwórz zestaw danych w projektancie, klikając dwukrotnie plik **XSD** w **Eksplorator rozwiązań**. Aby uzyskać więcej informacji, zobacz [jak: otwieranie zestawu danych w Projektant obiektów DataSet](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).

2. Kliknij dwukrotnie pasek tytułu tabeli danych w projektancie.

     Klasa częściowa jest tworzona z obsługą zdarzeń `RowChanging` i otwiera się w edytorze kodu.

    > [!NOTE]
    > Projektant obiektów Dataset nie tworzy automatycznie obsługi zdarzeń dla zdarzenia <xref:System.Data.DataTable.RowChanging> w C# projektach. Należy utworzyć metodę do obsługi zdarzenia <xref:System.Data.DataTable.RowChanging> i uruchomić kod, aby podłączyć zdarzenie do metody inicjacji tabeli.

3. Dodaj kod użytkownika wewnątrz deklaracji klasy częściowej.

4. Poniższy kod pokazuje, gdzie dodać kod użytkownika do sprawdzania poprawności podczas zdarzenia <xref:System.Data.DataTable.RowChanging> dla Visual Basic:

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

5. Poniższy kod pokazuje, jak utworzyć procedurę obsługi zdarzeń `RowChanging` i gdzie dodać kod użytkownika do sprawdzania poprawności podczas zdarzenia <xref:System.Data.DataTable.RowChanging> dla C#:

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
 [N-warstwowe aplikacje dotyczące danych](../data-tools/n-tier-data-applications-overview.md) — wskazówki [: Tworzenie wielowarstwowej aplikacji](../data-tools/walkthrough-creating-an-n-tier-data-application.md) [do sprawdzania poprawności danych](../data-tools/validate-data-in-datasets.md)

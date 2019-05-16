---
title: Dodawanie walidacji do warstwowego zestawu danych | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4b9b4f77045732bc61fa8aa8e4496eebf86f890a
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65683220"
---
# <a name="add-validation-to-an-n-tier-dataset"></a>Dodawanie walidacji do n-warstwowego zestawu danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dodawanie walidacji do zestawu danych, który jest podzielony na rozwiązanie n warstwowa zasadniczo jest taka sama, jak dodawanie sprawdzania poprawności do pojedynczego pliku zestawu danych (zestawu danych w jednym projekcie). Proponowana lokalizacja na sprawdzenie poprawności danych jest w trakcie <xref:System.Data.DataTable.ColumnChanging> i/lub <xref:System.Data.DataTable.RowChanging> zdarzenia tabeli danych.  
  
Projektant obiektów DataSet oferuje funkcje w celu tworzenia klas częściowych, do których można dodać kod użytkownika do kolumn i wierszy — zmieniający wydarzenia tabel danych w zestawie danych. Aby uzyskać więcej informacji na temat dodawania kodu zestawu danych w rozwiązaniu wielowarstwowym, zobacz [Dodawanie kodu do zestawów danych w aplikacjach n warstwowa](../data-tools/add-code-to-datasets-in-n-tier-applications.md), i [Dodawanie kodu do TableAdapters w aplikacjach n warstwowych](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md). Aby uzyskać więcej informacji na temat częściowych klas, zobacz [jak: Podział klasy na klasy częściowe (Projektant klas)](../ide/how-to-split-a-class-into-partial-classes-class-designer.md) lub [klasy częściowe i metody](https://msdn.microsoft.com/library/804cecb7-62db-4f97-a99f-60975bd59fa1).  
  
> [!NOTE]
> Kiedy oddzielisz zestawy danych z TableAdapters (przez ustawienie **projektu DataSet** właściwości), istniejące częściowe klasy zestawu danych w projekcie nie będą przenoszone automatycznie. Istniejące klasy częściowego zestawu danych należy przenieść ręcznie do projektu zestawu danych.  
  
> [!NOTE]
> Projektant zestawu danych nie tworzy automatycznie obsługi zdarzeń w języku C# dla <xref:System.Data.DataTable.ColumnChanging> i <xref:System.Data.DataTable.RowChanging> zdarzenia. Należy ręcznie utworzyć program obsługi zdarzenia i podpiąć procedurę obsługi zdarzeń do zdarzenia bazowego. W poniższych procedurach opisano sposób tworzenia procedury obsługi zdarzeń wymagane zarówno w Visual Basic i C#.  
  
## <a name="validatechanges-to-individual-columns"></a>Validatechanges do poszczególnych kolumn  
 Sprawdź poprawność wartości w poszczególnych kolumnach obsługi <xref:System.Data.DataTable.ColumnChanging> zdarzeń. <xref:System.Data.DataTable.ColumnChanging> Zdarzenie jest wywoływane, gdy wartość w kolumnie jest modyfikowana. Utwórz procedurę obsługi zdarzeń dla <xref:System.Data.DataTable.ColumnChanging> zdarzeń, klikając dwukrotnie odpowiednią kolumnę w zestawie danych.  
  
 Kliknij dwukrotnie kolumnę, po raz pierwszy projektant generuje moduł obsługi zdarzenia <xref:System.Data.DataTable.ColumnChanging> zdarzeń. `If…Then` Tworzona jest również instrukcja sprawdzająca określone kolumny. Na przykład poniższy kod jest generowany po dwukrotnym kliknięciu kolumna RequiredDate w tabeli Northwind Orders:  
  
```vb  
Private Sub OrdersDataTable_ColumnChanging(ByVal sender As System.Object, ByVal e As System.Data.DataColumnChangeEventArgs) Handles Me.ColumnChanging  
    If (e.Column.ColumnName = Me.RequiredDateColumn.ColumnName) Then  
        ' Add validation code here.  
    End If  
End Sub  
```  
  
> [!NOTE]
> W projektach C# Projektant obiektów Dataset tworzy tylko częściowe klasy dla zestawu danych i poszczególnych tabel w zestawie danych. Projektant zestawu danych nie tworzy automatycznie obsługi zdarzeń dla <xref:System.Data.DataTable.ColumnChanging> i <xref:System.Data.DataTable.RowChanging> zdarzeń w języku C# tak jak to robi w języku Visual Basic. W projektach C# musisz ręcznie utworzyć metodę obsługi zdarzenia i podpiąć metodę do zdarzenia bazowego. Poniższa procedura zawiera kroki, aby utworzyć procedury obsługi zdarzeń wymagane zarówno w Visual Basic i C#.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-add-validation-during-changes-to-individual-column-values"></a>Aby dodać sprawdzanie poprawności podczas zmiany wartości poszczególnych kolumn  
  
1. Otwórz zestaw danych w projektancie, klikając dwukrotnie **XSD** w pliku **Eksploratora rozwiązań**. Aby uzyskać więcej informacji, zobacz [jak: Otwórz zestaw danych w Projektancie obiektów Dataset](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2. Kliknij dwukrotnie kolumnę, którą chcesz zweryfikować. Ta akcja powoduje utworzenie <xref:System.Data.DataTable.ColumnChanging> programu obsługi zdarzeń.  
  
    > [!NOTE]
    > Projektant zestawu danych nie tworzy automatycznie zdarzenia obsługi dla zdarzenia języka C#. Kod, który jest niezbędny do obsługi zdarzeń w języku C# znajduje się w następnej sekcji. `SampleColumnChangingEvent` jest tworzony i następnie podłączone do <xref:System.Data.DataTable.ColumnChanging> zdarzenia w <xref:System.Data.DataTable.EndInit%2A> metody.  
  
3. Dodaj kod, aby sprawdzić, czy `e.ProposedValue` zawiera dane, które spełniają wymagania aplikacji. Jeżeli proponowana wartość jest nieakceptowana, należy ustawić kolumny, aby wskazać, że zawiera błąd.  
  
     Poniższy przykład kodu sprawdza, czy **ilość** kolumna zawiera więcej niż 0. Jeśli **ilość** jest mniejszy niż lub równy 0, kolumnę ustawiono jako błąd. `Else` Klauzula czyści ten błąd, jeśli **ilość** jest większa niż 0. Kod w obsłudze zdarzeń zmieniającej się kolumny powinna wyglądać w następujący sposób:  
  
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
  
## <a name="validatechanges-to-whole-rows"></a>Validatechanges całych wierszy  
 Sprawdź wartości we wszystkich wierszach obsługując <xref:System.Data.DataTable.RowChanging> zdarzeń. <xref:System.Data.DataTable.RowChanging> Zdarzenie jest wywoływane, gdy wartości we wszystkich kolumnach są zatwierdzone. Należy go zweryfikować w <xref:System.Data.DataTable.RowChanging> zdarzenie, kiedy wartość w jednej kolumnie opiera się na wartości w innej kolumnie. Rozważmy na przykład OrderDate i RequiredDate w tabeli zamówienia w bazie danych Northwind.  
  
 Po wprowadzeniu zamówień, sprawdzania poprawności upewnia się, że kolejność nie jest wprowadzone z DataDostawy, który jest w lub przed DataZamówienia. W tym przykładzie wartości dla kolumn RequiredDate i OrderDate muszą być porównane, więc sprawdzanie poprawności zmiany poszczególnych kolumn nie ma sensu.  
  
 Utwórz procedurę obsługi zdarzeń dla <xref:System.Data.DataTable.RowChanging> zdarzeń, klikając dwukrotnie nazwę tabeli, na pasku tytułu tabeli.  
  
#### <a name="to-add-validation-during-changes-to-whole-rows"></a>Aby dodać sprawdzanie poprawności podczas zmiany do całych wierszy  
  
1. Otwórz zestaw danych w projektancie, klikając dwukrotnie **XSD** w pliku **Eksploratora rozwiązań**. Aby uzyskać więcej informacji, zobacz [jak: Otwórz zestaw danych w Projektancie obiektów Dataset](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2. Kliknij dwukrotnie pasek tytułu tabeli danych w projektancie.  
  
     Częściowa klasa jest tworzona przy użyciu `RowChanging` program obsługi zdarzeń i zostanie otwarty w edytorze kodu.  
  
    > [!NOTE]
    > Projektant zestawu danych nie tworzy automatycznie zdarzenia obsługi dla <xref:System.Data.DataTable.RowChanging> zdarzenia w projektach C#. Należy utworzyć metody, aby obsłużyć <xref:System.Data.DataTable.RowChanging> zdarzeń i wykonywania kodu, aby zaczepić zdarzenie w metodzie inicjalizacji tabeli.  
  
3. Dodaj kod użytkownika wewnątrz deklaracji klasy częściowej.  
  
4. Poniższy kod przedstawia gdzie dodać kod użytkownika do sprawdzania poprawności podczas <xref:System.Data.DataTable.RowChanging> zdarzenia dla języka Visual Basic:  
  
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
  
5. Poniższy kod przedstawia sposób tworzenia `RowChanging` program obsługi zdarzeń i gdzie dodać kod użytkownika do sprawdzania poprawności podczas <xref:System.Data.DataTable.RowChanging> zdarzenia dla języka C#:  
  
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
 [Omówienie aplikacji N-warstwowa danych](../data-tools/n-tier-data-applications-overview.md)   
 [Przewodnik: Tworzenie aplikacji warstwowych](../data-tools/walkthrough-creating-an-n-tier-data-application.md)   
 [Weryfikowanie danych w zestawach danych](../data-tools/validate-data-in-datasets.md)

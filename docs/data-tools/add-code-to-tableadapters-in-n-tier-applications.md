---
title: Dodawanie kodu do adapterów TableAdapter w aplikacjach n-warstwowych
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, extending TableAdapters
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: e61b9e35464c4200581f6859b2f394911d266d44
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63402902"
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>Dodawanie kodu do adapterów TableAdapter w aplikacjach n-warstwowych
Możesz rozszerzyć funkcjonalności TableAdapter, tworząc plik częściowe klasy dla TableAdapter i dodając kod do niego (zamiast opcji dodawania kodu *DatasetName.DataSet.Designer* pliku). Klasy częściowe Włącz kod dla określonej klasy do podzielone między wiele plików fizycznych. Aby uzyskać więcej informacji, zobacz [częściowe](/dotnet/visual-basic/language-reference/modifiers/partial) lub [partial (typ)](/dotnet/csharp/language-reference/keywords/partial-type).

Kod, który definiuje obiekt TableAdapter jest generowany za każdym razem, gdy zmiany zostały wprowadzone do elementu TableAdapter w zestawie danych. Ten kod również jest generowany, gdy zostaną wprowadzone zmiany podczas uruchamiania dowolnego kreatora, który modyfikuje konfiguracji TableAdapter. Aby zapobiec usunięciu podczas ponownego generowania TableAdapter w kodzie, należy dodać kod do pliku częściowej klasy TableAdapter.

Domyślnie po oddzielić zestaw danych i kod TableAdapter wynik jest plik klasy dyskretnych w każdym projekcie. Oryginalny projekt zawiera plik o nazwie *DatasetName.Designer.vb* (lub *DatasetName.Designer.cs*) zawierający kod TableAdapter. Projekt, który jest wyznaczone w **projektu Dataset** właściwość ma w pliku o nazwie *DatasetName.DataSet.Designer.vb* (lub *DatasetName.DataSet.Designer.cs*), zawiera kod zestawu danych.

> [!NOTE]
> Kiedy oddzielisz zestawy danych i TableAdapters (przez ustawienie **projektu DataSet** właściwości), istniejące częściowe klasy zestawu danych w projekcie nie zostaną automatycznie przeniesione. Istniejące klasy częściowego zestawu danych należy przenieść ręcznie do projektu zestawu danych.

> [!NOTE]
> Zestaw danych dostarcza funkcje generowania <xref:System.Data.DataTable.ColumnChanging> i <xref:System.Data.DataTable.RowChanging> procedury obsługi zdarzeń, gdy sprawdzanie poprawności jest potrzebny. Aby uzyskać więcej informacji, zobacz [Dodawanie walidacji do warstwowego zestawu danych](../data-tools/add-validation-to-an-n-tier-dataset.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>Aby dodać kod użytkownika do TableAdapter w aplikacji n-warstwowej

1. Znajdź projekt, który zawiera *XSD* pliku.

2. Kliknij dwukrotnie *XSD* plik, aby otworzyć **Projektanta obiektów Dataset**.

3. Kliknij prawym przyciskiem myszy obiekt TableAdapter, który chcesz dodać kod, a następnie wybierz **Wyświetl kod**.

     Klasy częściowe, zostanie utworzona i zostanie otwarty w edytorze kodu.

4. Dodaj kod wewnątrz deklaracji klasy częściowej.

5. Poniższy kod przedstawia gdzie dodać kod do `CustomersTableAdapter` w `NorthwindDataSet`:

    ```vb
    Partial Public Class CustomersTableAdapter
        ' Add code here to add functionality
        ' to the CustomersTableAdapter.
    End Class
    ```

    ```csharp
    public partial class CustomersTableAdapter
    {
        // Add code here to add functionality
        // to the CustomersTableAdapter.
    }
    ```

## <a name="see-also"></a>Zobacz także

- [Omówienie aplikacji N-warstwowa danych](../data-tools/n-tier-data-applications-overview.md)
- [Dodawanie kodu do zestawów danych w aplikacjach n-warstwowych](../data-tools/add-code-to-datasets-in-n-tier-applications.md)
- [Tworzenie i konfigurowanie adapterów TableAdapter](create-and-configure-tableadapters.md)
- [Hierarchiczna aktualizacja — Przegląd](hierarchical-update.md)

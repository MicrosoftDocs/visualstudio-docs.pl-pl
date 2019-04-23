---
title: Dodawanie kodu do zestawów danych w aplikacjach n-warstwowych
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, extending datasets
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: dbd65c5247a82f2a58a57e50402ecde5d330cc9b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60111691"
---
# <a name="add-code-to-datasets-in-n-tier-applications"></a>Dodawanie kodu do zestawów danych w aplikacjach n-warstwowych
Możesz rozszerzyć funkcjonalność zestawu danych, tworzenia pliku częściowej klasy zestawu danych i dodając kod do niego (zamiast opcji dodawania kodu *DatasetName*. Plik Dataset.Designer). Klasy częściowe Włącz kod dla określonej klasy do podzielone między wiele plików fizycznych. Aby uzyskać więcej informacji, zobacz [częściowe](/dotnet/visual-basic/language-reference/modifiers/partial) lub [klasy częściowe i metody](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).

Kod, który definiuje zestaw danych jest generowany za każdym razem, gdy zmiany zostały wprowadzone do definicji zestawu danych (w typizowany zestaw danych). Ten kod zostanie również wygenerowany po wprowadzeniu zmian podczas uruchamiania dowolnego kreatora, który modyfikuje konfigurację zestawu danych. Aby zapobiec usunięciu podczas ponownego generowania zestawu danych w kodzie, należy dodać kod do pliku częściowej klasy zestawu danych.

Domyślnie po oddzielić zestaw danych i kod TableAdapter wynik jest plik klasy dyskretnych w każdym projekcie. Oryginalny projekt zawiera plik o nazwie *DatasetName.Designer.vb* (lub *DatasetName.Designer.cs*) zawierający kod TableAdapter. Projekt, który jest wyznaczone w **projektu Dataset** właściwość zawiera plik o nazwie *DatasetName.DataSet.Designer.vb* (lub *DatasetName.DataSet.Designer.cs*) . Ten plik zawiera kod zestawu danych.

> [!NOTE]
>  Kiedy oddzielisz zestawy danych i TableAdapters (przez ustawienie **projektu DataSet** właściwości), istniejące częściowe klasy zestawu danych w projekcie nie będą przenoszone automatycznie. Istniejące klasy częściowego zestawu danych należy przenieść ręcznie do projektu zestawu danych.

> [!NOTE]
>  Gdy kod sprawdzania poprawności, musi zostać dodany, typizowany zestaw danych zapewnia funkcje do generowania <xref:System.Data.DataTable.ColumnChanging> i <xref:System.Data.DataTable.RowChanging> procedury obsługi zdarzeń. Aby uzyskać więcej informacji, zobacz [Dodawanie walidacji do warstwowego zestawu danych](../data-tools/add-validation-to-an-n-tier-dataset.md).

## <a name="to-add-code-to-datasets-in-n-tier-applications"></a>Dodawanie kodu do zestawów danych w aplikacjach n warstwowej

1. Znajdź projekt, który zawiera *XSD* pliku.

2. Wybierz **XSD** plik, aby otworzyć zestaw danych.

3. Kliknij prawym przyciskiem myszy tabelę danych, do której chcesz dodać kod (nazwa tabeli na pasku tytułu), a następnie wybierz **Wyświetl kod**.

     Klasy częściowe, zostanie utworzona i zostanie otwarty w edytorze kodu.

4. Dodaj kod wewnątrz deklaracji klasy częściowej.

     Poniższy kod przedstawia gdzie dodać kod do CustomersDataTable w NorthwindDataSet:

    ```vb
    Partial Public Class CustomersDataTable
        ' Add code here to add functionality
        ' to the CustomersDataTable.
    End Class
    ```

    ```csharp
    partial class CustomersDataTable
    {
        // Add code here to add functionality
        // to the CustomersDataTable.
    }
    ```

## <a name="see-also"></a>Zobacz także

- [Omówienie aplikacji N-warstwowa danych](../data-tools/n-tier-data-applications-overview.md)
- [Dodawanie kodu do adapterów TableAdapter w aplikacjach n-warstwowych](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [Tworzenie i konfigurowanie adapterów TableAdapter](create-and-configure-tableadapters.md)
- [Hierarchiczna aktualizacja — Przegląd](hierarchical-update.md)
- [Narzędzia zestawów danych w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
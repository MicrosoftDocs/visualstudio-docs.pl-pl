---
title: Dodawanie kodu do zestawów danych w aplikacjach n warstwowa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, extending datasets
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 16b932a316557a64259d10c89613fcca8ff4fead
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53646859"
---
# <a name="add-code-to-datasets-in-n-tier-applications"></a>Dodawanie kodu do zestawów danych w aplikacjach n-warstwowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz rozszerzyć funkcjonalność zestawu danych, tworzenia pliku częściowej klasy zestawu danych i dodając kod do niego (zamiast opcji dodawania kodu *DatasetName*. Plik Dataset.Designer). Klasy częściowe Włącz kod dla określonej klasy do podzielone między wiele plików fizycznych. Aby uzyskać więcej informacji, zobacz [częściowe](http://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) lub [klasy częściowe i metody](http://msdn.microsoft.com/library/804cecb7-62db-4f97-a99f-60975bd59fa1).

Kod, który definiuje zestaw danych jest generowany za każdym razem, gdy zmiany zostały wprowadzone do definicji zestawu danych. Ten kod zostanie również wygenerowany po wprowadzeniu zmian podczas uruchamiania dowolnego kreatora, który modyfikuje konfigurację zestawu danych. Aby zapobiec usunięciu podczas ponownego generowania zestawu danych w kodzie, należy dodać kod do pliku częściowej klasy zestawu danych.

Domyślnie po rozdzielenie zestawu danych i `TableAdapter` kod, wynik jest plik klasy dyskretnych w każdym projekcie. Oryginalny projekt ma filenamed *DatasetName*. Designer.VB (lub *DatasetName*. Designer.cs narzędzie), który zawiera `TableAdapter` kodu. Projekt, który jest wyznaczone w **projektu Dataset** właściwość zawiera plik o nazwie *DatasetName*. DataSet.Designer.vb (lub *DatasetName*. DataSet.Designer.cs). Ten plik zawiera kod zestawu danych.

> [!NOTE]
> Kiedy oddzielisz zestawy danych i `TableAdapter`s (przez ustawienie **projektu DataSet** właściwości), istniejące częściowe klasy zestawu danych w projekcie nie będą przenoszone automatycznie. Istniejące klasy częściowego zestawu danych należy przenieść ręcznie do projektu zestawu danych.

> [!NOTE]
> Gdy kod sprawdzania poprawności, musi zostać dodany, Projektanta obiektów DataSet oferuje funkcję do generowania <xref:System.Data.DataTable.ColumnChanging> i <xref:System.Data.DataTable.RowChanging> procedury obsługi zdarzeń. Aby uzyskać więcej informacji, zobacz [Dodawanie walidacji do warstwowego zestawu danych](../data-tools/add-validation-to-an-n-tier-dataset.md).

## <a name="add-code-to-datasets-in-n-tier-applications"></a>Dodawanie kodu do zestawów danych w aplikacjach n-warstwowych

1.  Znajdź projekt, który zawiera plik XSD (zestaw danych).

2.  Wybierz **XSD** plik, aby otworzyć zestaw danych.

3.  Kliknij prawym przyciskiem myszy tabelę danych, do której chcesz dodać kod (nazwa tabeli na pasku tytułu), a następnie wybierz **Wyświetl kod**.

     Klasy częściowe, zostanie utworzona i zostanie otwarty w edytorze kodu.

4.  Dodaj kod wewnątrz deklaracji klasy częściowej.

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

- [N-warstwowe aplikacje do obsługi danych — omówienie](../data-tools/n-tier-data-applications-overview.md)
- [Dodawanie kodu do adapterów TableAdapter w aplikacjach n-warstwowych](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [TableAdapters](http://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364)
- [TableAdapterManager — Przegląd](http://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650)
- [Hierarchiczna aktualizacja — Przegląd](http://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6)
- [Narzędzia zestawów danych w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
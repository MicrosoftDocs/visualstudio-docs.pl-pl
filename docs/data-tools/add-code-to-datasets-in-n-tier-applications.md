---
title: Dodawanie kodu do zestawów danych w aplikacjach n-warstwowych
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, extending DataSets
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 3e5b3e44e1de085b5389ad0f50aed758f09a2759
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648943"
---
# <a name="add-code-to-datasets-in-n-tier-applications"></a>Dodawanie kodu do zestawów danych w aplikacjach n-warstwowych

Można zwiększyć funkcjonalność zestawu danych, tworząc plik klasy częściowej dla zestawu danych i dodając do niego kod (zamiast dodawać kod do *zestawu danychname*. Plik DataSet. Designer). Klasy częściowe umożliwiają dzielenie kodu dla określonej klasy, aby można je było podzielić między wiele plików fizycznych. Aby uzyskać więcej informacji, zobacz [częściowe](/dotnet/visual-basic/language-reference/modifiers/partial) lub [częściowe klasy i metody](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).

Kod definiujący zestaw danych jest generowany każdorazowo po wprowadzeniu zmian w definicji zestawu danych (w określonym zestawie danych). Ten kod jest również generowany, gdy wprowadzasz zmiany w trakcie działania kreatora, który modyfikuje konfigurację zestawu danych. Aby zapobiec usunięciu kodu podczas ponownej generacji zestawu danych, Dodaj kod do pliku klasy częściowej zestawu danych.

Domyślnie po oddzieleniu zestawu danych i kodu TableAdapter wynik jest dyskretnym plikiem klasy w każdym projekcie. Oryginalny projekt zawiera plik o nazwie *DatasetName. Designer. vb* (lub *DatasetName.Designer.cs*), który zawiera kod TableAdapter. Projekt wskazany we właściwości **projektu DataSet** zawiera plik o nazwie *DatasetName. DataSet. Designer. vb* (lub *DatasetName.DataSet.Designer.cs*). Ten plik zawiera kod zestawu danych.

> [!NOTE]
> Gdy oddzielasz zestawy danych i TableAdapters (ustawiając właściwość **projektu DataSet** ), istniejące częściowe klasy zestawu danych w projekcie nie będą automatycznie przenoszone. Istniejące klasy częściowe zestawu danych muszą być przenoszone ręcznie do projektu DataSet.

> [!NOTE]
> Gdy należy dodać kod sprawdzania poprawności, zestaw danych zawiera funkcje do generowania obsługi zdarzeń <xref:System.Data.DataTable.ColumnChanging> i <xref:System.Data.DataTable.RowChanging>. Aby uzyskać więcej informacji, zobacz [Dodawanie walidacji do wielowarstwowego zestawu danych](../data-tools/add-validation-to-an-n-tier-dataset.md).

## <a name="to-add-code-to-datasets-in-n-tier-applications"></a>Aby dodać kod do zestawów danych w aplikacjach n-warstwowych

1. Znajdź projekt, który zawiera plik *XSD* .

2. Wybierz plik **XSD** , aby otworzyć zestaw danych.

3. Kliknij prawym przyciskiem myszy tabelę danych, do której chcesz dodać kod (nazwę tabeli na pasku tytułu), a następnie wybierz polecenie **Wyświetl kod**.

     Klasa częściowa jest tworzona i otwiera się w edytorze kodu.

4. Dodaj kod wewnątrz deklaracji klasy częściowej.

     Poniższy przykład pokazuje, gdzie dodać kod do CustomersDataTable w NorthwindDataSet:

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

- [N-warstwowe aplikacje dotyczące danych — omówienie](../data-tools/n-tier-data-applications-overview.md)
- [Dodawanie kodu do adapterów TableAdapter w aplikacjach n-warstwowych](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [Tworzenie i konfigurowanie adapterów TableAdapter](create-and-configure-tableadapters.md)
- [Omówienie aktualizacji hierarchicznej](hierarchical-update.md)
- [Narzędzia zestawu danych w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
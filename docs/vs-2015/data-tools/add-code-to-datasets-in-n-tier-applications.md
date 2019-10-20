---
title: Dodawanie kodu do zestawów danych w aplikacjach n-warstwowych | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, extending datasets
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aed37ee9cdd8c221fcfb114db426a6286ee8ad6f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72673120"
---
# <a name="add-code-to-datasets-in-n-tier-applications"></a>Dodawanie kodu do zestawów danych w aplikacjach n-warstwowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można zwiększyć funkcjonalność zestawu danych, tworząc plik klasy częściowej dla zestawu danych i dodając do niego kod (zamiast dodawać kod do *zestawu danychname*. Plik DataSet. Designer). Klasy częściowe umożliwiają dzielenie kodu dla określonej klasy, aby można je było podzielić między wiele plików fizycznych. Aby uzyskać więcej informacji, zobacz [częściowe](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) lub [częściowe klasy i metody](https://msdn.microsoft.com/library/804cecb7-62db-4f97-a99f-60975bd59fa1).

Kod definiujący zestaw danych jest generowany każdorazowo po wprowadzeniu zmian w definicji zestawu danych. Ten kod jest również generowany, gdy wprowadzasz zmiany w trakcie działania kreatora, który modyfikuje konfigurację zestawu danych. Aby zapobiec usunięciu kodu podczas ponownej generacji zestawu danych, Dodaj kod do pliku klasy częściowej zestawu danych.

Domyślnie po rozdzieleniu zestawu danych i kodu `TableAdapter` wynik jest dyskretnym plikiem klasy w każdym projekcie. Oryginalny projekt ma nazwę pliku *DataSetName*. Designer. vb (lub *DataSetName*. Designer.cs), który zawiera kod `TableAdapter`. Projekt, który jest wskazany we właściwości **projektu DataSet** , ma plik o nazwie *DataSetName*. DataSet. Designer. vb (lub *DataSetName*. DataSet.Designer.cs). Ten plik zawiera kod zestawu danych.

> [!NOTE]
> W przypadku rozdzielania zestawów danych i `TableAdapter`s (przez ustawienie właściwości **projektu DataSet** ) istniejące częściowe klasy zestawu danych w projekcie nie będą automatycznie przenoszone. Istniejące klasy częściowe zestawu danych muszą być przenoszone ręcznie do projektu DataSet.

> [!NOTE]
> Gdy należy dodać kod sprawdzania poprawności, Projektant zestawu danych udostępnia funkcje do generowania <xref:System.Data.DataTable.ColumnChanging> i <xref:System.Data.DataTable.RowChanging> obsługi zdarzeń. Aby uzyskać więcej informacji, zobacz [Dodawanie walidacji do wielowarstwowego zestawu danych](../data-tools/add-validation-to-an-n-tier-dataset.md).

## <a name="add-code-to-datasets-in-n-tier-applications"></a>Dodawanie kodu do zestawów danych w aplikacjach n-warstwowych

1. Znajdź projekt, który zawiera plik XSD (DataSet).

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

- [N-warstwowe aplikacje do obsługi danych — omówienie](../data-tools/n-tier-data-applications-overview.md)
- [Dodawanie kodu do adapterów TableAdapter w aplikacjach n-warstwowych](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [TableAdapters](https://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364)
- [TableAdapterManager — Omówienie](https://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650)
- [Omówienie aktualizacji hierarchicznej](https://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6)
- [Narzędzia zestawów danych w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)